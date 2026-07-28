Ustawienia bezpieczeństwa robota
================================

.. toctree:: 
    :maxdepth: 5

Ustawienie poziomu kolizji
+++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia poziom kolizji
    * @param  [in]  mode  0-poziom, 1-procent
    * @param  [in]  level Próg kolizji, zakres dla poziomu [], zakres dla procentu [0~1]
    * @param  [in]  config 0-nie aktualizuj pliku konfiguracyjnego, 1-aktualizuj plik konfiguracyjny
    * @return  Kod błędu
    */
    int SetAnticollision(int mode, double[] level, int config); 

Ustawienie strategii po kolizji
++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ustawia strategię po kolizji
    * @param  [in] strategy  0-zatrzymaj z błędem i wstrzymaj; 1-kontynuuj działanie; 2-zatrzymaj z błędem; 3-tryb momentu grawitacyjnego; 4-tryb odpowiedzi oscylacyjnej; 5-tryb odbicia kolizyjnego
    * @param  [in] safeTime  Czas bezpiecznego zatrzymania [1000 - 2000] ms
    * @param  [in] safeDistance  Odległość bezpiecznego zatrzymania [1-150] mm
    * @param  [in] safeVel  Prędkość bezpiecznego zatrzymania TCP [50-250] mm/s
    * @param  [in] safetyMargin  Współczynniki bezpieczeństwa j1-j6 [1-10]
    * @return  Kod błędu
    */
    int SetCollisionStrategy(int strategy, int safeTime, int safeDistance, int safeVel,int[] safetyMargin);

Rozpoczęcie funkcji niestandardowego progu wykrywania kolizji
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Rozpoczęcie funkcji niestandardowego progu wykrywania kolizji, ustawienie progów wykrywania kolizji dla strony stawów i strony TCP
    * @param  [in] flag 1-tylko wykrywanie stawów włączone; 2-tylko wykrywanie TCP włączone; 3-wykrywanie stawów i TCP włączone jednocześnie
    * @param  [in] jointDetectionThreshould Próg wykrywania kolizji stawów j1-j6
    * @param  [in] tcpDetectionThreshould Próg wykrywania kolizji TCP, xyzabc
    * @param  [in] block 0-nieblokujące; 1-blokujące
    * @return  Kod błędu
    */
    int CustomCollisionDetectionStart(int flag, double[] jointDetectionThreshould, double[] tcpDetectionThreshould, int block);

Zakończenie funkcji niestandardowego progu wykrywania kolizji
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Zakończenie funkcji niestandardowego progu wykrywania kolizji
    * @return  Kod błędu
    */
    int CustomCollisionDetectionEnd()

Przykład kodu ustawiania poziomu kolizji robota
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button24_Click(object sender, EventArgs e)
    {
        int mode = 0;
        int config = 1;
        double[] level1 = { 1.0f, 2.0f, 3.0f, 4.0f, 5.0f, 6.0f };
        double[] level2 = { 50.0f, 20.0f, 30.0f, 40.0f, 50.0f, 60.0f };

        int rtn = robot.SetAnticollision(mode, level1, config);
        Console.WriteLine($"SetAnticollision mode 0 rtn is {rtn}");
        mode = 1;
        rtn = robot.SetAnticollision(mode, level2, config);
        Console.WriteLine($"SetAnticollision mode 1 rtn is {rtn}");

        JointPos p1Joint = new JointPos(-11.904f, -99.669f, 117.473f, -108.616f, -91.726f, 74.256f);
        JointPos p2Joint = new JointPos(-45.615f, -106.172f, 124.296f, -107.151f, -91.282f, 74.255f);

        DescPose p1Desc = new DescPose(-419.524f, -13.000f, 351.569f, -178.118f, 0.314f, 3.833f);
        DescPose p2Desc = new DescPose(-321.222f, 185.189f, 335.520f, -179.030f, -1.284f, -29.869f);

        ExaxisPos exaxisPos = new ExaxisPos(0.0f, 0.0f, 0.0f, 0.0f);
        DescPose offdese = new DescPose(0.0f, 0.0f, 0.0f, 0.0f, 0.0f, 0.0f);
        robot.MoveL( p2Joint,  p2Desc, 0, 0, 100, 100, 100, 2,  exaxisPos, 0, 0,  offdese);
        robot.ResetAllError();
        int[] safety = { 5, 5, 5, 5, 5, 5 };
        rtn = robot.SetCollisionStrategy(3, 1000, 150, 250, safety);
        Console.WriteLine($"SetCollisionStrategy rtn is {rtn}");

        double[] jointDetectionThreshould = { 0.1, 0.1, 0.1, 0.1, 0.1, 0.1 };
        double[] tcpDetectionThreshould = { 60, 60, 60, 60, 60, 60 };
        rtn = robot.CustomCollisionDetectionStart(3, jointDetectionThreshould, tcpDetectionThreshould, 0);
        Console.WriteLine($"CustomCollisionDetectionStart rtn is {rtn}");

        robot.MoveL( p1Joint,  p1Desc, 0, 0, 100, 100, 100, -1,  exaxisPos, 0, 0,  offdese);
        robot.MoveL( p2Joint,  p2Desc, 0, 0, 100, 100, 100, -1,  exaxisPos, 0, 0,  offdese);
        rtn = robot.CustomCollisionDetectionEnd();
        Console.WriteLine($"CustomCollisionDetectionEnd rtn is {rtn}");
    }

Ustawienie dodatniego limitu
++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ustawia dodatni limit
    * @param  [in] limit Pozycje sześciu stawów, jednostka deg
    * @return  Kod błędu
    */
    int SetLimitPositive(double[] limit); 

Ustawienie ujemnego limitu
++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ustawia ujemny limit
    * @param  [in] limit Pozycje sześciu stawów, jednostka deg
    * @return  Kod błędu
    */
    int SetLimitNegative(double[] limit); 

Pobranie kąta miękkiego limitu stawu
++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera kąt miękkiego limitu stawu
    * @param  [in] flag 0-blokujący, 1-nieblokujący	 
    * @param  [out] negative  Kąt ujemnego limitu, jednostka deg
    * @param  [out] positive  Kąt dodatniego limitu, jednostka deg
    * @return  Kod błędu
    */
    int GetJointSoftLimitDeg(byte flag, ref double[] negative, ref double[] positive);

Przykład kodu ustawiania limitów robota
+++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnRobotSafetySet_Click(object sender, EventArgs e)
    {
        double[] plimit = { 170.0f, 80.0f, 150.0f, 80.0f, 170.0f, 160.0f };
        robot.SetLimitPositive(plimit);
        double[] nlimit = { -170.0f, -260.0f, -150.0f, -260.0f, -170.0f, -160.0f };
        robot.SetLimitNegative(nlimit);

        double[] neg_deg = new double[6] {0,0,0,0,0,0 };
        double[] pos_deg = new double[6] { 0, 0, 0, 0, 0, 0 };
        robot.GetJointSoftLimitDeg(0, ref neg_deg,ref pos_deg);
        Console.WriteLine($"neg limit deg:{neg_deg[0]},{neg_deg[1]},{neg_deg[2]},{neg_deg[3]},{neg_deg[4]},{neg_deg[5]}");
        Console.WriteLine($"pos limit deg:{pos_deg[0]},{pos_deg[1]},{pos_deg[2]},{pos_deg[3]},{pos_deg[4]},{pos_deg[5]}");
    }

Ustawienie metody wykrywania kolizji robota
+++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia metodę wykrywania kolizji robota
    * @param  [in] method Metoda wykrywania kolizji: 0-tryb prądowy; 1-podwójny enkoder; 2-tryb prądowy i podwójny enkoder włączone jednocześnie
    * @param [in] thresholdMode Sposób progu poziomu kolizji; 0-stały próg poziomu kolizji; 1-niestandardowy próg wykrywania kolizji
    * @return  Kod błędu
    */
    int SetCollisionDetectionMethod(int method,int thresholdMode=0);


Ustawienie włączania/wyłączania wykrywania kolizji w stanie spoczynku
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia włączanie/wyłączanie wykrywania kolizji w stanie spoczynku
    * @param  [in] status 0-wyłączone; 1-włączone
    * @return  Kod błędu
    */
    int SetStaticCollisionOnOff(int status);

Przykład kodu ustawiania metody wykrywania kolizji robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button26_Click(object sender, EventArgs e)
    {
        int rtn = robot.SetCollisionDetectionMethod(0, 0);

        rtn = robot.SetStaticCollisionOnOff(1);
        Console.WriteLine($"SetStaticCollisionOnOff On rtn is {rtn}");
        Thread.Sleep(5000);
        rtn = robot.SetStaticCollisionOnOff(0);
        Console.WriteLine($"SetStaticCollisionOnOff Off rtn is {rtn}");
    }

Wykrywanie momentu obrotowego i mocy stawu
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Wykrywanie momentu obrotowego i mocy stawu
    * @param  [in] status 0-wyłączone; 1-włączone
    * @param  [in] power Ustawiona maksymalna moc (W)
    * @return  Kod błędu
    */
    int SetPowerLimit(int status, double power);

Przykład kodu wykrywania momentu obrotowego i mocy stawu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button26_Click(object sender, EventArgs e)
    {
        robot.DragTeachSwitch(1);
        robot.SetPowerLimit(1, 200);
        double[] torques = { 0, 0, 0, 0, 0, 0 };
        robot.GetJointTorques(1, torques);

        int count = 100;
        robot.ServoJTStart();
        int error = 0;
        while (count > 0)
        {
            error = robot.ServoJT(torques, 0.001f);
            count--;
            Thread.Sleep(1);
        }
        error = robot.ServoJTEnd();
        robot.DragTeachSwitch(0);
    }

Ustawienie parametrów bezpiecznej prędkości
+++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia parametry bezpiecznej prędkości
    * @param [in] enable 0-wył.; 1-włącz w trybie ręcznym; 2-włącz we wszystkich trybach (nie obsługuje automatycznego ograniczenia prędkości)
    * @param [in] maxTCPVel Maksymalna prędkość TCP do ograniczenia; [0-1000] mm/s
    * @param [in] strategy Strategia po przekroczeniu prędkości; 0-zatrzymaj z alarmem; 1-automatyczne ograniczenie prędkości; 2-zatrzymaj z alarmem i odłącz
    * @param [in] maxJointVel Maksymalna prędkość dla 6 stawów (°/s), domyślnie 45°/s
    * @return Kod błędu
    */
    public int SetVelReducePara(int enable, double maxTCPVel, int strategy, double[] maxJointVel = null)
    
Przykład kodu SDK ustawiania parametrów bezpiecznej prędkości
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public int TestSetVelReducePara()
    {
        int rtn = 0;
        JointPos j1 = new JointPos(10.220, -11.121, -118.086, -46.739, 82.036, 131.503);
        JointPos j2 = new JointPos(89.782, -11.122, -118.086, -46.740, 82.036, 131.504);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        double[] maxJointVel = new double[] { 100.0, 100.0, 100.0, 100.0, 100.0, 100.0 };

        robot.SetSpeed(20);
        rtn = robot.SetVelReducePara(0, 200, 0, maxJointVel);
        robot.MoveJ(j2, 1, 2, 100, 100, 100, epos, -1, 0, offset_pos);

        // 1st
        rtn = robot.SetVelReducePara(2, 200, 0, maxJointVel);
        Console.WriteLine($"SetVelReduceParaA param error rtn is {rtn}");
        robot.MoveJ(j1, 1, 2, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.MoveJ(j2, 1, 2, 100, 100, 100, epos, -1, 0, offset_pos);

        // 2rd
        maxJointVel = new double[] { 20.0, 20.0, 20.0, 20.0, 20.0, 20.0 };
        rtn = robot.SetVelReducePara(2, 200, 0, maxJointVel);
        Console.WriteLine($"SetVelReduceParaB reduce vel rtn is {rtn}");
        robot.MoveJ(j1, 1, 2, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.MoveJ(j2, 1, 2, 100, 100, 100, epos, -1, 0, offset_pos);
        return 0; 
    }