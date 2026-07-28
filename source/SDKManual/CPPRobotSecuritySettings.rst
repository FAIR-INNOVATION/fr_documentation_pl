Ustawienia bezpieczeństwa robota
================================

.. toctree::
    :maxdepth: 5

Ustawianie poziomu kolizji
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia poziom kolizji
    * @param  [in]  mode  0-poziom, 1-procent
    * @param  [in]  level Próg kolizji, dla poziomu zakres [], dla procentu zakres [0~1]
    * @param  [in]  config 0-nie aktualizuj pliku konfiguracyjnego, 1-aktualizuj plik konfiguracyjny
    * @return  Kod błędu
    */
    errno_t  SetAnticollision(int mode, float level[6], int config);

Ustawianie strategii po kolizji
+++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief  Ustawia strategię po kolizji
     * @param  [in] strategy  0-zgłoś błąd i wstrzymaj; 1-kontynuuj działanie; 2-zgłoś błąd i zatrzymaj; 3-tryb momentu grawitacyjnego; 4-tryb odpowiedzi oscylacyjnej; 5-tryb odbicia po kolizji
     * @param  [in] safeTime  Czas bezpiecznego zatrzymania [1000 - 2000] ms
     * @param  [in] safeDistance  Odległość bezpiecznego zatrzymania [1-150] mm
     * @param  [in] safetyMargin  Współczynniki bezpieczeństwa dla j1-j6 [1-10]
     * @return  Kod błędu
     */
    errno_t SetCollisionStrategy(int strategy, int safeTime, int safeDistance, int safetyMargin[]);

Rozpoczęcie funkcji niestandardowego progu wykrywania kolizji
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.0-3.8.0

.. code-block:: c++
    :linenos:

     /**
     * @brief  Rozpoczęcie funkcji niestandardowego progu wykrywania kolizji, ustawia progi wykrywania kolizji dla strony stawów i TCP
     * @param  [in] flag 1-włączone tylko wykrywanie stawów; 2-włączone tylko wykrywanie TCP; 3-włączone jednocześnie wykrywanie stawów i TCP
     * @param  [in] jointDetectionThreshould Próg wykrywania kolizji stawów j1-j6
     * @param  [in] tcpDetectionThreshould Próg wykrywania kolizji TCP, xyzabc
     * @param  [in] block 0-nieblokujący; 1-blokujący
     * @return  Kod błędu
     */
    errno_t CustomCollisionDetectionStart(int flag, double jointDetectionThreshould[6], double tcpDetectionThreshould[6], int block);

Zakończenie funkcji niestandardowego progu wykrywania kolizji
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.0-3.8.0

.. code-block:: c++
    :linenos:

    /**
     * @brief  Zakończenie funkcji niestandardowego progu wykrywania kolizji
     * @return  Kod błędu
     */
    errno_t CustomCollisionDetectionEnd();

Przykład kodu ustawiania poziomu kolizji robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestCollision(void)
     {
         ROBOT_STATE_PKG pkg = {};
         FRRobot robot;
         robot.LoggerInit();
         robot.SetLoggerLevel(1);
         int rtn = robot.RPC("192.168.58.2");
         if (rtn != 0)
         {
             return -1;
         }
         robot.SetReConnectParam(true, 30000, 500);
         int mode = 0;
         int config = 1;
         float level1[6] = { 1.0,2.0,3.0,4.0,5.0,6.0 };
         float level2[6] = { 50.0,20.0,30.0,40.0,50.0,60.0 };
         rtn = robot.SetAnticollision(mode, level1, config);
         printf("SetAnticollision mode 0 rtn is %d\n", rtn);
         mode = 1;
         rtn = robot.SetAnticollision(mode, level2, config);
         printf("SetAnticollision mode 1 rtn is %d\n", rtn);
         JointPos p1Joint(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
         JointPos p2Joint(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
         DescPose p1Desc(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
         DescPose p2Desc(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
         ExaxisPos exaxisPos(0.0, 0.0, 0.0, 0.0);
         DescPose offdese(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);
         robot.MoveL(&p2Joint, &p2Desc, 0, 0, 100, 100, 100, 2, &exaxisPos, 0, 0, &offdese);
         robot.ResetAllError();
         int safety[6] = { 5,5,5,5,5,5 };
         rtn = robot.SetCollisionStrategy(3, 1000, 150, 250, safety);
         printf("SetCollisionStrategy rtn is %d\n", rtn);
         double jointDetectionThreshould[6] = { 0.1, 0.1, 0.1, 0.1, 0.1, 0.1 };
         double tcpDetectionThreshould[6] = { 60,60,60,60,60,60 };
         rtn = robot.CustomCollisionDetectionStart(3, jointDetectionThreshould, tcpDetectionThreshould, 0);
         cout << "CustomCollisionDetectionStart rtn is " << rtn << endl;
         robot.MoveL(&p1Joint, &p1Desc, 0, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese);
         robot.MoveL(&p2Joint, &p2Desc, 0, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese);
         rtn = robot.CustomCollisionDetectionEnd();
         cout << "CustomCollisionDetectionEnd rtn is " << rtn << endl;
         robot.CloseRPC();
         return 0;
     }

Ustawianie dodatniego ogranicznika
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ustawia dodatni ogranicznik
    * @param  [in] limit Pozycje sześciu stawów, jednostka deg
    * @return  Kod błędu
    */
    errno_t  SetLimitPositive(float limit[6]);

Ustawianie ujemnego ogranicznika
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ustawia ujemny ogranicznik
    * @param  [in] limit Pozycje sześciu stawów, jednostka deg
    * @return  Kod błędu
    */
    errno_t  SetLimitNegative(float limit[6]);

Pobieranie kątów miękkiego ograniczenia stawów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Pobiera kąty miękkiego ograniczenia stawów
    * @param  [in] flag 0-blokujący, 1-nieblokujący
    * @param  [out] negative  Kąt ujemnego ograniczenia, jednostka deg
    * @param  [out] positive  Kąt dodatniego ograniczenia, jednostka deg
    * @return  Kod błędu
    */
    errno_t  GetJointSoftLimitDeg(uint8_t flag, float negative[6], float positive[6]);

Przykład kodu ustawiania ograniczników robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestLimit(void)
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      robot.LoggerInit();
      robot.SetLoggerLevel(1);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return -1;
      }
      robot.SetReConnectParam(true, 30000, 500);
      float plimit[6] = { 170.0,80.0,150.0,80.0,170.0,160.0 };
      robot.SetLimitPositive(plimit);
      float nlimit[6] = { -170.0,-260.0,-150.0,-260.0,-170.0,-160.0 };
      robot.SetLimitNegative(nlimit);
      float neg_deg[6] = { 0.0 }, pos_deg[6] = { 0.0 };
      robot.GetJointSoftLimitDeg(0, neg_deg, pos_deg);
      printf("neg limit deg:%f,%f,%f,%f,%f,%f\n", neg_deg[0], neg_deg[1], neg_deg[2], neg_deg[3], neg_deg[4], neg_deg[5]);
      printf("pos limit deg:%f,%f,%f,%f,%f,%f\n", pos_deg[0], pos_deg[1], pos_deg[2], pos_deg[3], pos_deg[4], pos_deg[5]);
      robot.CloseRPC();
      return 0;
    }

Ustawianie metody wykrywania kolizji robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia metodę wykrywania kolizji robota
    * @param [in] method Metoda wykrywania kolizji: 0-tryb prądowy; 1-podwójny enkoder; 2-tryb prądowy i podwójny enkoder jednocześnie
    * @param [in] thresholdMode Sposób progu poziomu kolizji; 0-stały próg poziomu kolizji; 1-niestandardowy próg wykrywania kolizji
    * @return  Kod błędu
    */
    errno_t SetCollisionDetectionMethod(int method, int thresholdMode = 0);

Włączanie/wyłączanie wykrywania kolizji w stanie statycznym
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Włącza/wyłącza wykrywanie kolizji w stanie statycznym
     * @param [in] status 0-wyłączone; 1-włączone
     * @return Kod błędu
     */
    errno_t SetStaticCollisionOnOff(int status);

Przykład kodu ustawiania metody wykrywania kolizji robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    int TestCollisionMethod(void)
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      robot.LoggerInit();
      robot.SetLoggerLevel(1);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return -1;
      }
      robot.SetReConnectParam(true, 30000, 500);
      rtn = robot.SetCollisionDetectionMethod(0, 0);
      printf("SetCollisionDetectionMethod rtn is %d\n", rtn);
      rtn = robot.SetStaticCollisionOnOff(1);
      printf("SetStaticCollisionOnOff On rtn is %d\n", rtn);
      rtn = robot.Sleep(5000);
      rtn = robot.SetStaticCollisionOnOff(0);
      printf("SetStaticCollisionOnOff Off rtn is %d\n", rtn);
      robot.CloseRPC();
      return 0;
    }

Detekcja mocy momentu stawów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Detekcja mocy momentu stawów
     * @param [in] status 0-wyłączone; 1-włączone
     * @param [in] power Ustawiona maksymalna moc (W);
     * @return Kod błędu
     */
    errno_t SetPowerLimit(int status, double power);

Przykład kodu detekcji mocy momentu stawów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestPowerLimit(void)
    {
       ROBOT_STATE_PKG pkg = {};
       FRRobot robot;
       robot.LoggerInit();
       robot.SetLoggerLevel(1);
       int rtn = robot.RPC("192.168.58.2");
       if (rtn != 0)
       {
          return -1;
       }
       robot.SetReConnectParam(true, 30000, 500);
       robot.DragTeachSwitch(1);
       robot.SetPowerLimit(1, 200);
       float torques[] = { 0, 0, 0, 0, 0, 0 };
       robot.GetJointTorques(1, torques);
       int count = 100;
       robot.ServoJTStart();
       int error = 0;
       while (count > 0)
       {
          error = robot.ServoJT(torques, 0.001);
          count = count - 1;
          robot.Sleep(1);
       }
       error = robot.ServoJTEnd();
       robot.DragTeachSwitch(0);
       robot.CloseRPC();
       return 0;
    }

Ustawianie parametrów prędkości bezpiecznej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia parametry prędkości bezpieczeństwa
    * @param [in] enable 0-wyłączony; 1-włączony w trybie ręcznym; 2-włączony we wszystkich trybach
    * @param [in] maxTCPVel Maksymalny limit prędkości TCP; [0-1000] mm/s
    * @param [in] strategy Strategia po przekroczeniu prędkości; 0-zatrzymaj i alarm; 1-automatyczne ograniczenie prędkości; 2-zatrzymaj i alarm z wyłączeniem
    * @param [in] maxJointVel Maksymalna prędkość dla 6 stawów (°/s), domyślnie 45°/s
    * @return Kod błędu
    */
    errno_t SetVelReducePara(int enable, double maxTCPVel, int strategy, std::vector<double> maxJointVel = {45.0, 45.0, 45.0, 45.0, 45.0, 45.0});

Przykład kodu SDK ustawiania parametrów prędkości bezpiecznej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestSetVelReducePara()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return -1;
        }
        robot.SetReConnectParam(true, 30000, 500);
        JointPos j1(0, -90, 90, 0, 0, 0);
        JointPos j2(90, -90, 90, 0, 0, 0);
        ExaxisPos epos(0, 0, 0, 0);
        DescPose offset_pos(0, 0, 0, 0, 0, 0);
        robot.SetSpeed(80);
        rtn = robot.SetVelReducePara(2, 30, 1);
        printf("SetVelReducePara param error rtn is %d\n", rtn);
        rtn = robot.SetVelReducePara(0, 30, 1);
        printf("SetVelReducePara disable reduce vel rtn is %d\n", rtn);
        robot.MoveJ(&j1, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.MoveJ(&j2, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        rtn = robot.SetVelReducePara(1, 30, 1);
        printf("SetVelReducePara reduce vel rtn is %d\n", rtn);
        robot.MoveJ(&j1, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.MoveJ(&j2, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        rtn = robot.SetVelReducePara(2, 30, 2);
        printf("SetVelReducePara disable robot rtn is %d\n", rtn);
        robot.MoveJ(&j1, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.MoveJ(&j2, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(2000);
        robot.ResetAllError();
        robot.RobotEnable(1);
        robot.Sleep(1000);
        rtn = robot.SetVelReducePara(2, 30, 0);
        printf("SetVelReducePara report error rtn is %d\n", rtn);
        robot.MoveJ(&j1, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.MoveJ(&j2, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.CloseRPC();
        robot.Sleep(1000);
        return 0;
    }

Przykład Kodu Ustawiania Prędkości Bezpieczeństwa Stawów Robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:    

    int TestSetJointVelReducePara()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return -1;
        }
        robot.SetReConnectParam(true, 30000, 500);
        JointPos j1(10.220, -11.121, -118.086, -46.739, 82.036, 131.503);
        JointPos j2(89.782, -11.122, -118.086, -46.740, 82.036, 131.504);
        ExaxisPos epos(0, 0, 0, 0);
        DescPose offset_pos(0, 0, 0, 0, 0, 0);
        robot.SetSpeed(20);

        std::vector<double> maxJointVelA = {100.0, 100.0, 100.0, 100.0, 100.0, 100.0 };
        rtn = robot.SetVelReducePara(2, 200, 0, maxJointVelA);
        printf("SetVelReducePara param error rtn is %d\n", rtn);
        robot.MoveJ(&j1, 1, 2, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.MoveJ(&j2, 1, 2, 100, 100, 100, &epos, -1, 0, &offset_pos);
        std::vector<double> maxJointVelB = { 20.0, 20.0, 20.0, 20.0, 20.0, 20.0 };
        rtn = robot.SetVelReducePara(2, 200, 0, maxJointVelB);
        printf("SetVelReducePara reduce vel rtn is %d\n", rtn);
        robot.MoveJ(&j1, 1, 2, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.MoveJ(&j2, 1, 2, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(2000);
        robot.CloseRPC();
        return 0;
    }    