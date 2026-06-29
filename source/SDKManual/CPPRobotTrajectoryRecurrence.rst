Odtwarzanie trajektorii robota
===============================

.. toctree::
    :maxdepth: 5

Ustawianie parametrów rejestracji trajektorii TPD
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ustawia parametry rejestracji trajektorii TPD
    * @param  [in] type  Typ rejestrowanych danych, 1-pozycja stawów
    * @param  [in] name  Nazwa pliku trajektorii
    * @param  [in] period_ms  Okres próbkowania danych, stałe wartości 2 ms, 4 ms lub 8 ms
    * @param  [in] di_choose  Wybór DI, bity 0~7 odpowiadają DI0~DI7 szafy sterowniczej, bity 8~9 odpowiadają DI0~DI1 końcówki, 0-niewybrany, 1-wybrany
    * @param  [in] do_choose  Wybór DO, bity 0~7 odpowiadają DO0~DO7 szafy sterowniczej, bity 8~9 odpowiadają DO0~DO1 końcówki, 0-niewybrany, 1-wybrany
    * @return  Kod błędu
    */
    errno_t  SetTPDParam(int type, char name[30], int period_ms, uint16_t di_choose, uint16_t do_choose);

Rozpoczęcie rejestracji trajektorii TPD
++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Rozpoczyna rejestrację trajektorii TPD
    * @param  [in] type  Typ rejestrowanych danych, 1-pozycja stawów
    * @param  [in] name  Nazwa pliku trajektorii
    * @param  [in] period_ms  Okres próbkowania danych, stałe wartości 2 ms, 4 ms lub 8 ms
    * @param  [in] di_choose  Wybór DI, bity 0~7 odpowiadają DI0~DI7 szafy sterowniczej, bity 8~9 odpowiadają DI0~DI1 końcówki, 0-niewybrany, 1-wybrany
    * @param  [in] do_choose  Wybór DO, bity 0~7 odpowiadają DO0~DO7 szafy sterowniczej, bity 8~9 odpowiadają DO0~DO1 końcówki, 0-niewybrany, 1-wybrany
    * @return  Kod błędu
    */
    errno_t  SetTPDStart(int type, char name[30], int period_ms, uint16_t di_choose, uint16_t do_choose);

Zatrzymanie rejestracji trajektorii TPD
+++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Zatrzymuje rejestrację trajektorii TPD
    * @return  Kod błędu
    */
    errno_t  SetWebTPDStop();

Usuwanie rejestracji trajektorii TPD
++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Usuwa rejestrację trajektorii TPD
    * @param  [in] name  Nazwa pliku trajektorii
    * @return  Kod błędu
    */
    errno_t  SetTPDDelete(char name[30]);

Wstępne ładowanie trajektorii TPD
+++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Wstępne ładowanie trajektorii TPD
    * @param  [in] name  Nazwa pliku trajektorii
    * @return  Kod błędu
    */
    errno_t  LoadTPD(char name[30]);

Odtwarzanie trajektorii TPD
+++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Odtwarzanie trajektorii TPD
    * @param  [in] name  Nazwa pliku trajektorii
    * @param  [in] blend 0-niewygładzone, 1-wygładzone
    * @param  [in] ovl  Procent skalowania prędkości, zakres [0~100]
    * @return  Kod błędu
    */
    errno_t  MoveTPD(char name[30], uint8_t blend, float ovl);

Pobieranie początkowej pozy i orientacji TPD
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera początkową pozy i orientację TPD
    * @param [in] name Nazwa pliku TPD, bez rozszerzenia
    * @return Kod błędu
    */
    errno_t GetTPDStartPose(char name[30], DescPose *desc_pose);

Ruch do punktu początkowego rejestracji trajektorii TPD
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Ruch do punktu początkowego rejestracji trajektorii TPD
    * @param [in] name Nazwa pliku trajektorii
    * @param [in] moveType Typ ruchu; 0-PTP; 1-LIN
    * @param [in] ovl Procent skalowania prędkości, zakres [0~100]
    * @return Kod błędu
    */
    errno_t MoveToTPDStart(char name[30], uint8_t moveType, float ovl);

Przykład kodu rejestracji trajektorii TPD robota
++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestTPD(void)
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
    int type = 1;
    char name[30] = "tpd2025";
    int period_ms = 4;
    uint16_t di_choose = 0;
    uint16_t do_choose = 0;
    robot.SetTPDParam(type, name, period_ms, di_choose, do_choose);
    robot.Mode(1);
    robot.Sleep(1000);
    robot.DragTeachSwitch(1);
    robot.SetTPDStart(type, name, period_ms, di_choose, do_choose);
    robot.Sleep(3000);
    robot.SetWebTPDStop();
    robot.DragTeachSwitch(0);
    robot.Sleep(1000);
    float ovl = 100.0;
    uint8_t blend = 0;
    DescPose start_pose = {};
    rtn = robot.LoadTPD(name);
    printf("LoadTPD rtn is: %d\n", rtn);
    robot.GetTPDStartPose(name, &start_pose);
    printf("start pose, xyz is: %f %f %f. rpy is: %f %f %f \n", start_pose.tran.x, start_pose.tran.y, start_pose.tran.z, start_pose.rpy.rx, start_pose.rpy.ry, start_pose.rpy.rz);
    rtn = robot.MoveToTPDStart(name, 0, 100);
    printf("MoveToTPDStart rtn is: %d\n", rtn);
    rtn = robot.MoveTPD(name, blend, ovl);
    printf("MoveTPD rtn is: %d\n", rtn);
    std::this_thread::sleep_for(std::chrono::milliseconds(5000));
    robot.SetTPDDelete(name);
    robot.CloseRPC();
    return 0;
    }

Wstępne przetwarzanie trajektorii
+++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Wstępne przetwarzanie trajektorii
    * @param [in] name Nazwa pliku trajektorii
    * @param [in] ovl Procent skalowania prędkości, zakres [0~100]
    * @param [in] opt 1-punkt kontrolny, domyślnie 1
    * @return Kod błędu
    */
    errno_t LoadTrajectoryJ(char name[30], float ovl, int opt);

Odtwarzanie trajektorii
+++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Odtwarzanie trajektorii
    * @return Kod błędu
    */
    errno_t MoveTrajectoryJ();

Pobieranie początkowej pozy i orientacji trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera początkową pozy i orientację trajektorii
    * @param [in] name Nazwa pliku trajektorii
    * @return Kod błędu
    */
    errno_t GetTrajectoryStartPose(char name[30], DescPose *desc_pose);

Pobieranie numeru punktu trajektorii
++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera numer punktu trajektorii
    * @return Kod błędu
    */
    errno_t GetTrajectoryPointNum(int *pnum);

Ustawianie prędkości podczas wykonywania trajektorii
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia prędkość podczas wykonywania trajektorii
    * @param [in] ovl Procent prędkości [0-100.0]
    * @param [in] mode Tryb; 0-tryb zmniejszania prędkości; 1-bezpośrednie przełączenie
    * @return Kod błędu
    */
    errno_t SetTrajectoryJSpeed(float ovl, int mode = 0);

Przykład kodu ustawiania prędkości podczas wykonywania trajektorii robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestSetTrajectoryJSpeed()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        robot.SetReConnectParam(true, 30000, 500);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return -1;
        }

        rtn = robot.TrajectoryJUpLoad("D://zUP/horse.txt");
        printf("Upload TrajectoryJ A %d\n", rtn);
        char traj_file_name[90] = "horse.txt";
        rtn = robot.LoadTrajectoryJ(traj_file_name, 100, 1);
        printf("LoadTrajectoryJ %s, rtn is: %d\n", traj_file_name, rtn);
        DescPose traj_start_pose;
        memset(&traj_start_pose, 0, sizeof(DescPose));
        rtn = robot.GetTrajectoryStartPose(traj_file_name, &traj_start_pose);
        printf("GetTrajectoryStartPose is: %d\n", rtn);
        printf("desc_pos:%f,%f,%f,%f,%f,%f\n", traj_start_pose.tran.x, traj_start_pose.tran.y, traj_start_pose.tran.z, traj_start_pose.rpy.rx, traj_start_pose.rpy.ry, traj_start_pose.rpy.rz);
        std::this_thread::sleep_for(std::chrono::seconds(1));
        robot.SetSpeed(50);
        robot.MoveCart(&traj_start_pose, 0, 0, 100, 100, 100, -1, -1);
        int traj_num = 0;
        rtn = robot.GetTrajectoryPointNum(&traj_num);
        printf("GetTrajectoryStartPose rtn is: %d, traj num is: %d\n", rtn, traj_num);
        rtn = robot.MoveTrajectoryJ();
        printf("MoveTrajectoryJ rtn is: %d\n", rtn);
        robot.Sleep(1000);
        robot.GetRobotRealTimeState(&pkg);
        int trajspeedMode = 1;
        while (pkg.motion_done == 0)
        {
            robot.GetRobotRealTimeState(&pkg);
            rtn = robot.SetTrajectoryJSpeed(10.0, trajspeedMode);
            printf("SetTrajectoryJSpeed is: %d\n", rtn);
            robot.Sleep(1000);
            rtn = robot.SetTrajectoryJSpeed(80.0, trajspeedMode);
            printf("SetTrajectoryJSpeed is: %d\n", rtn);
            robot.Sleep(1000);
        }
        robot.CloseRPC();
        robot.Sleep(1000000);
        return 0;
    }

Ustawianie siły i momentu podczas wykonywania trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia siłę i moment podczas wykonywania trajektorii
    * @param [in] ft Siły i momenty w trzech kierunkach, jednostka N i Nm
    * @return Kod błędu
    */
    errno_t SetTrajectoryJForceTorque(ForceTorque *ft);

Ustawianie siły wzdłuż osi X podczas wykonywania trajektorii
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia siłę wzdłuż osi X podczas wykonywania trajektorii
    * @param [in] fx Siła wzdłuż osi X, jednostka N
    * @return Kod błędu
    */
    errno_t SetTrajectoryJForceFx(double fx);

Ustawianie siły wzdłuż osi Y podczas wykonywania trajektorii
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia siłę wzdłuż osi Y podczas wykonywania trajektorii
    * @param [in] fy Siła wzdłuż osi Y, jednostka N
    * @return Kod błędu
    */
    errno_t SetTrajectoryJForceFy(double fy);

Ustawianie siły wzdłuż osi Z podczas wykonywania trajektorii
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia siłę wzdłuż osi Z podczas wykonywania trajektorii
    * @param [in] fz Siła wzdłuż osi X, jednostka N
    * @return Kod błędu
    */
    errno_t SetTrajectoryJForceFz(double fz);

Ustawianie momentu wokół osi X podczas wykonywania trajektorii
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia moment wokół osi X podczas wykonywania trajektorii
    * @param [in] tx Moment wokół osi X, jednostka Nm
    * @return Kod błędu
    */
    errno_t SetTrajectoryJTorqueTx(double tx);

Ustawianie momentu wokół osi Y podczas wykonywania trajektorii
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia moment wokół osi Y podczas wykonywania trajektorii
    * @param [in] ty Moment wokół osi Y, jednostka Nm
    * @return Kod błędu
    */
    errno_t SetTrajectoryJTorqueTy(double ty);

Ustawianie momentu wokół osi Z podczas wykonywania trajektorii
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia moment wokół osi Z podczas wykonywania trajektorii
    * @param [in] tz Moment wokół osi Z, jednostka Nm
    * @return Kod błędu
    */
    errno_t SetTrajectoryJTorqueTz(double tz);

Przesyłanie pliku trajektorii J
+++++++++++++++++++++++++++++++
.. versionadded:: V3.7.7

.. code-block:: c++
    :linenos:

    /**
     * @brief Przesyła plik trajektorii J
     * @param [in] filePath Pełna ścieżka przesyłanego pliku trajektorii   C://test/testJ.txt
     * @return Kod błędu
     */
    errno_t TrajectoryJUpLoad(const std::string& filePath);

Usuwanie pliku trajektorii J
++++++++++++++++++++++++++++
.. versionadded:: V3.7.7

.. code-block:: c++
    :linenos:

    /**
     * @brief Usuwa plik trajektorii J
     * @param [in] fileName Nazwa pliku testJ.txt
     * @return Kod błędu
     */
    errno_t TrajectoryJDelete(const std::string& fileName);

Przykład kodu odtwarzania pliku trajektorii J robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestTraj(void)
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
      rtn = robot.TrajectoryJUpLoad("D://zUP/traj1.txt");
      printf("Upload TrajectoryJ A %d\n", rtn);
      char traj_file_name[30] = "/fruser/traj/traj1.txt";
      rtn = robot.LoadTrajectoryJ(traj_file_name, 100, 1);
      printf("LoadTrajectoryJ %s, rtn is: %d\n", traj_file_name, rtn);
      DescPose traj_start_pose;
      memset(&traj_start_pose, 0, sizeof(DescPose));
      rtn = robot.GetTrajectoryStartPose(traj_file_name, &traj_start_pose);
      printf("GetTrajectoryStartPose is: %d\n", rtn);
      printf("desc_pos:%f,%f,%f,%f,%f,%f\n", traj_start_pose.tran.x, traj_start_pose.tran.y, traj_start_pose.tran.z, traj_start_pose.rpy.rx, traj_start_pose.rpy.ry, traj_start_pose.rpy.rz);
      std::this_thread::sleep_for(std::chrono::seconds(1));
      robot.SetSpeed(50);
      robot.MoveCart(&traj_start_pose, 0, 0, 100, 100, 100, -1, -1);
      int traj_num = 0;
      rtn = robot.GetTrajectoryPointNum(&traj_num);
      printf("GetTrajectoryStartPose rtn is: %d, traj num is: %d\n", rtn, traj_num);
      rtn = robot.SetTrajectoryJSpeed(50.0);
      printf("SetTrajectoryJSpeed is: %d\n", rtn);
      ForceTorque traj_force;
      memset(&traj_force, 0, sizeof(ForceTorque));
      traj_force.fx = 10;
      rtn = robot.SetTrajectoryJForceTorque(&traj_force);
      printf("SetTrajectoryJForceTorque rtn is: %d\n", rtn);
      rtn = robot.SetTrajectoryJForceFx(10.0);
      printf("SetTrajectoryJForceFx rtn is: %d\n", rtn);
      rtn = robot.SetTrajectoryJForceFy(0.0);
      printf("SetTrajectoryJForceFy rtn is: %d\n", rtn);
      rtn = robot.SetTrajectoryJForceFz(0.0);
      printf("SetTrajectoryJForceFz rtn is: %d\n", rtn);
      rtn = robot.SetTrajectoryJTorqueTx(10.0);
      printf("SetTrajectoryJTorqueTx rtn is: %d\n", rtn);
      rtn = robot.SetTrajectoryJTorqueTy(10.0);
      printf("SetTrajectoryJTorqueTy rtn is: %d\n", rtn);
      rtn = robot.SetTrajectoryJTorqueTz(10.0);
      printf("SetTrajectoryJTorqueTz rtn is: %d\n", rtn);
      rtn = robot.MoveTrajectoryJ();
      printf("MoveTrajectoryJ rtn is: %d\n", rtn);
      robot.CloseRPC();
      return 0;
    }

Wstępne przetwarzanie trajektorii (planowanie trajektorii z wyprzedzeniem)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Wstępne przetwarzanie trajektorii (planowanie trajektorii z wyprzedzeniem)
    * @param [in] name Nazwa pliku trajektorii
    * @param [in] mode Tryb próbkowania, 0-bez próbkowania; 1-próbkowanie w równych odstępach danych; 2-próbkowanie z ograniczeniem błędu
    * @param [in] errorLim Ograniczenie błędu, stosowane przy aproksymacji liniowej
    * @param [in] type Sposób wygładzania, 0-wygładzanie Beziera
    * @param [in] precision Dokładność wygładzania, stosowana przy wygładzaniu Beziera
    * @param [in] vamx Ustawiona maksymalna prędkość, mm/s
    * @param [in] amax Ustawione maksymalne przyspieszenie, mm/s2
    * @param [in] jmax Ustawione maksymalne zryw, mm/s3
    * @param [in] flag Przełącznik włączenia wyprzedzenia z jednostajną prędkością 0-niewłączone; 1-włączone
    * @return Kod błędu
    */
    errno_t LoadTrajectoryLA(char name[30], int mode, double errorLim, int type, double precision, double vamx, double amax, double jmax, int flag = 0);

Odtwarzanie trajektorii (planowanie trajektorii z wyprzedzeniem)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Odtwarzanie trajektorii (planowanie trajektorii z wyprzedzeniem)
    * @return  Kod błędu
    */
    errno_t MoveTrajectoryLA();

Przykład kodu odtwarzania trajektorii (planowanie trajektorii z wyprzedzeniem)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestLoadTrajLA(void)
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
      rtn = robot.TrajectoryJUpLoad("D://zUP/traj.txt");
      printf("Upload TrajectoryJ A %d\n", rtn);
      char traj_file_name[30] = "/fruser/traj/traj.txt";
      rtn = robot.LoadTrajectoryLA(traj_file_name, 1, 2, 0, 2, 100, 200, 1000);
      printf("LoadTrajectoryLA %s, rtn is: %d\n", traj_file_name, rtn);
      DescPose traj_start_pose;
      memset(&traj_start_pose, 0, sizeof(DescPose));
      rtn = robot.GetTrajectoryStartPose(traj_file_name, &traj_start_pose);
      printf("GetTrajectoryStartPose is: %d\n", rtn);
      printf("desc_pos:%f,%f,%f,%f,%f,%f\n", traj_start_pose.tran.x, traj_start_pose.tran.y, traj_start_pose.tran.z, traj_start_pose.rpy.rx, traj_start_pose.rpy.ry, traj_start_pose.rpy.rz);
      std::this_thread::sleep_for(std::chrono::seconds(1));
      robot.SetSpeed(50);
      robot.MoveCart(&traj_start_pose, 0, 0, 100, 100, 100, -1, -1);
      rtn = robot.MoveTrajectoryLA();
      printf("MoveTrajectoryLA rtn is: %d\n", rtn);
      robot.CloseRPC();
      return 0;
    }