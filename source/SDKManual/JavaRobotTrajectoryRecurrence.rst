Odtwarzanie trajektorii robota
===============================

.. toctree:: 
    :maxdepth: 5

Ustawianie parametrów rejestracji trajektorii TPD
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Ustawianie parametrów rejestracji trajektorii TPD
    * @param  [in] type  Typ rejestrowanych danych, 1-pozycja przegubów
    * @param  [in] name  Nazwa pliku trajektorii
    * @param  [in] period_ms  Okres próbkowania danych, stałe wartości 2ms, 4ms lub 8ms
    * @param  [in] di_choose  Wybór DI, bit0~bit7 odpowiadają DI0~DI7 skrzynki kontrolnej, bit8~bit9 odpowiadają DI0~DI1 końcówki, 0-nie wybieraj, 1-wybierz
    * @param  [in] do_choose  Wybór DO, bit0~bit7 odpowiadają DO0~DO7 skrzynki kontrolnej, bit8~bit9 odpowiadają DO0~DO1 końcówki, 0-nie wybieraj, 1-wybierz
    * @return  Kod błędu
    */
    int SetTPDParam(int type, String name, int period_ms, int di_choose, int do_choose);

Rozpoczęcie rejestracji trajektorii TPD
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Rozpoczęcie rejestracji trajektorii TPD
    * @param  [in] type  Typ rejestrowanych danych, 1-pozycja przegubów
    * @param  [in] name  Nazwa pliku trajektorii
    * @param  [in] period_ms  Okres próbkowania danych, stałe wartości 2ms, 4ms lub 8ms
    * @param  [in] di_choose  Wybór DI, bit0~bit7 odpowiadają DI0~DI7 skrzynki kontrolnej, bit8~bit9 odpowiadają DI0~DI1 końcówki, 0-nie wybieraj, 1-wybierz
    * @param  [in] do_choose  Wybór DO, bit0~bit7 odpowiadają DO0~DO7 skrzynki kontrolnej, bit8~bit9 odpowiadają DO0~DO1 końcówki, 0-nie wybieraj, 1-wybierz
    * @return  Kod błędu
    */
    int SetTPDStart(int type, String name, int period_ms, int di_choose, int do_choose);

Zatrzymanie rejestracji trajektorii TPD
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: java
    :linenos:

    /**
    * @brief  Zatrzymanie rejestracji trajektorii TPD
    * @return  Kod błędu
    */
    int SetWebTPDStop(); 

Usunięcie zarejestrowanej trajektorii TPD
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Usunięcie zarejestrowanej trajektorii TPD
    * @param  [in] name  Nazwa pliku trajektorii
    * @return  Kod błędu
    */   
    int SetTPDDelete(string name); 

Wstępne ładowanie trajektorii TPD
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Wstępne ładowanie trajektorii
    * @param  [in] name  Nazwa pliku trajektorii
    * @return  Kod błędu
    */      
    int LoadTPD(String name);

Odtwarzanie trajektorii TPD
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Odtwarzanie trajektorii
    * @param  [in] name  Nazwa pliku trajektorii
    * @param  [in] blend 0-bez wygładzania, 1-wygładzanie
    * @param  [in] ovl  Procent skalowania prędkości, zakres [0~100]
    * @return  Kod błędu
    */
    int MoveTPD(String name, int blend, double ovl); 

Pobieranie początkowej pozy trajektorii TPD
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Pobieranie początkowej pozy trajektorii 
    * @param [in] name  Nazwa pliku trajektorii, bez rozszerzenia pliku
    * @param [out] desc_pose Pobrana początkowa poza trajektorii
    * @return Kod błędu 
    */ 
    int GetTPDStartPose(String name, DescPose desc_pose); 

Przykład kodu rejestracji trajektorii TPD robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestTPD(Robot robot)
    {
        int type = 1;
        String name = "tpd2025";
        int period_ms = 4;
        int di_choose = 0;
        int do_choose = 0;

        robot.SetTPDParam(type, name, period_ms, di_choose, do_choose);

        robot.Mode(1);
        robot.Sleep(1000);
        robot.DragTeachSwitch(1);
        robot.SetTPDStart(type, name, period_ms, di_choose, do_choose);
        robot.Sleep(10000);
        robot.SetWebTPDStop();
        robot.DragTeachSwitch(0);

        double ovl = 100.0;
        int blend = 0;

        DescPose start_pose =new DescPose() {};

        int rtn = robot.LoadTPD(name);
        System.out.println("LoadTPD rtn is:"+ rtn);

        robot.GetTPDStartPose(name, start_pose);
        robot.MoveCart(start_pose, 0, 0, 100, 100, ovl, -1, -1);
        robot.Sleep(1000);

        rtn = robot.MoveTPD(name, blend, ovl);
        System.out.println("MoveTPD rtn is: "+ rtn);
        robot.Sleep(5000);

        robot.SetTPDDelete(name);
        return 0;
    }

Wstępne przetwarzanie trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Wstępne przetwarzanie zewnętrznego pliku trajektorii 
    * @param [in] name Nazwa pliku trajektorii  
    * @param [in] ovl Procent skalowania prędkości, zakres [0~100]
    * @param [in] opt 1-punkt kontrolny, domyślnie 1 
    * @return Kod błędu 
    */ 
    int LoadTrajectoryJ(String name, double ovl, int opt); 

Odtwarzanie trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Odtwarzanie zewnętrznego pliku trajektorii  
    * @return Kod błędu 
    */
    int MoveTrajectoryJ();

Pobieranie początkowej pozy trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Pobieranie początkowej pozy trajektorii 
    * @param [in] name Nazwa pliku trajektorii  
    * @param [out] desc_pose Pobrana początkowa poza trajektorii
    * @return Kod błędu 
    */ 
    int GetTrajectoryStartPose(String name, DescPose desc_pose);

Pobieranie numeru punktu trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Pobieranie numeru punktu trajektorii
    * @return  Kod błędu
    */
    public int GetTrajectoryPointNum(int pnum)

Ustawianie prędkości podczas odtwarzania trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /*
    * @brief  Ustawianie prędkości podczas odtwarzania trajektorii
    * @param  ovl Procent prędkości
    * @param  mode Tryb; 0-tryb zmniejszania prędkości; 1-bezpośrednie przełączanie
    * @return  Kod błędu
    */
    public int SetTrajectoryJSpeed(double ovl, int mode)

Ustawianie siły i momentu obrotowego podczas odtwarzania trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Ustawianie siły i momentu obrotowego podczas odtwarzania trajektorii
    * @param  [in] ft Siły w trzech kierunkach i momenty obrotowe, jednostka N i Nm
    * @return  Kod błędu
    */
    public int SetTrajectoryJForceTorque(ForceTorque ft)

Ustawianie siły w kierunku X podczas odtwarzania trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Ustawianie siły w kierunku X podczas odtwarzania trajektorii  
    * @param [in] fx Siła w kierunku X, jednostka N
    * @return Kod błędu 
    */
    int SetTrajectoryJForceFx(double fx);

Ustawianie siły w kierunku Y podczas odtwarzania trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Ustawianie siły w kierunku Y podczas odtwarzania trajektorii
    * @param [in] fy Siła w kierunku Y, jednostka N
    * @return Kod błędu 
    */
    int SetTrajectoryJForceFy(double fy);

Ustawianie siły w kierunku Z podczas odtwarzania trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Ustawianie siły w kierunku Z podczas odtwarzania trajektorii  
    * @param [in] fz  Siła w kierunku Z, jednostka N
    * @return Kod błędu 
    */
    int SetTrajectoryJForceFz(double fz);

Ustawianie momentu obrotowego wokół osi X podczas odtwarzania trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Ustawianie momentu obrotowego wokół osi X podczas odtwarzania trajektorii  
    * @param [in] tx Moment obrotowy wokół osi X, jednostka Nm
    * @return Kod błędu 
    */
    int SetTrajectoryJTorqueTx(double tx);

Ustawianie momentu obrotowego wokół osi Y podczas odtwarzania trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Ustawianie momentu obrotowego wokół osi Y podczas odtwarzania trajektorii  
    * @param [in] ty Moment obrotowy wokół osi Y, jednostka Nm
    * @return Kod błędu 
    */
    int SetTrajectoryJTorqueTy(double ty);

Ustawianie momentu obrotowego wokół osi Z podczas odtwarzania trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Ustawianie momentu obrotowego wokół osi Z podczas odtwarzania trajektorii  
    * @param [in] tz Moment obrotowy wokół osi Z, jednostka Nm
    * @return Kod błędu 
    */
    int SetTrajectoryJTorqueTz(double tz);

Przesyłanie pliku trajektorii J
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Przesyłanie pliku trajektorii J  
    * @param [in] filePath Pełna ścieżka przesyłanego pliku trajektorii   C://test/testJ.txt
    * @return Kod błędu 
    */
    int TrajectoryJUpLoad(String filePath);

Usuwanie pliku trajektorii J
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Usuwanie pliku trajektorii J  
    * @param [in] fileName Nazwa pliku testJ.txt
    * @return Kod błędu 
    */
    int TrajectoryJDelete(String fileName);

Przykład kodu odtwarzania pliku trajektorii J robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestTraj(Robot robot)
    {
        int rtn = robot.TrajectoryJUpLoad("D://zUP/horse.txt");
        System.out.println("Upload TrajectoryJ A :"+ rtn);

        String traj_file_name = "horse.txt";
        rtn = robot.LoadTrajectoryJ(traj_file_name, 100, 1);
        System.out.println("LoadTrajectoryJ:"+traj_file_name+", rtn is:"+ rtn);

        DescPose traj_start_pose=new DescPose(0,0,0,0,0,0);
        rtn = robot.GetTrajectoryStartPose(traj_file_name, traj_start_pose);

        robot.Sleep(1000);


        ExaxisPos epos=new ExaxisPos(0,0,0,0);
        DescPose po=new DescPose(0,0,0,0,0,0);
        robot.SetSpeed(50);
        robot.MoveCart(traj_start_pose, 0, 0, 100, 100, 100, -1, -1);

        int traj_num = 0;
        rtn = robot.GetTrajectoryPointNum(traj_num);

        rtn = robot.SetTrajectoryJSpeed(50.0);
        System.out.println("SetTrajectoryJSpeed is:"+ rtn);

        ForceTorque traj_force=new ForceTorque(0,0,0,0,0,0);
        traj_force.fx = 10;
        rtn = robot.SetTrajectoryJForceTorque(traj_force);
        System.out.println("SetTrajectoryJForceTorque rtn is: "+ rtn);

        rtn = robot.SetTrajectoryJForceFx(10.0);
        System.out.println("SetTrajectoryJForceFx rtn is:"+ rtn);

        rtn = robot.SetTrajectoryJForceFy(0.0);
        System.out.println("SetTrajectoryJForceFy rtn is:"+ rtn);

        rtn = robot.SetTrajectoryJForceFz(0.0);
        System.out.println("SetTrajectoryJForceFz rtn is: "+ rtn);

        rtn = robot.SetTrajectoryJTorqueTx(10.0);
        System.out.println("SetTrajectoryJTorqueTx rtn is: "+ rtn);

        rtn = robot.SetTrajectoryJTorqueTy(10.0);
        System.out.println("SetTrajectoryJTorqueTy rtn is:"+ rtn);

        rtn = robot.SetTrajectoryJTorqueTz(10.0);
        System.out.println("SetTrajectoryJTorqueTz rtn is:"+ rtn);

        rtn = robot.MoveTrajectoryJ();
        System.out.println("MoveTrajectoryJ rtn is: "+ rtn);

        return 0;
    }

Przykład kodu ustawiania prędkości podczas odtwarzania trajektorii robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public int TestSetTrajectoryJSpeed(Robot robot) {
        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
        int rtn;

        robot.SetReconnectParam(true, 30000, 500);
        rtn = robot.TrajectoryJUpLoad("D://zUP/horse.txt");
        System.out.printf("Upload TrajectoryJ A %d%n", rtn);
        String trajFileName = "horse.txt";
        rtn = robot.LoadTrajectoryJ(trajFileName, 100, 1);
        System.out.printf("LoadTrajectoryJ %s, rtn is: %d%n", trajFileName, rtn);
        DescPose trajStartPose = new DescPose();
        rtn = robot.GetTrajectoryStartPose(trajFileName, trajStartPose);
        System.out.printf("GetTrajectoryStartPose is: %d%n", rtn);
        System.out.printf("desc_pos:%f,%f,%f,%f,%f,%f%n", trajStartPose.tran.x, trajStartPose.tran.y, trajStartPose.tran.z, trajStartPose.rpy.rx, trajStartPose.rpy.ry, trajStartPose.rpy.rz);
        robot.Sleep(1000);
        robot.SetSpeed(50);
        robot.MoveCart(trajStartPose, 0, 0, 100, 100, 100, -1, -1);
        rtn = robot.GetTrajectoryPointNum(0);
        pkg = robot.GetRobotRealTimeState();
        int trajNum = pkg.trajectory_pnum;
        System.out.printf("GetTrajectoryPointNum rtn is: %d, traj num is: %d%n", rtn, trajNum);

        rtn = robot.MoveTrajectoryJ();
        System.out.printf("MoveTrajectoryJ rtn is: %d%n", rtn);

        robot.Sleep(1000);

        pkg = robot.GetRobotRealTimeState();
        int trajspeedMode = 1;
        while (pkg.motion_done == 0)
        {
            pkg = robot.GetRobotRealTimeState();

            rtn = robot.SetTrajectoryJSpeed(10.0, trajspeedMode);
            System.out.printf("SetTrajectoryJSpeed is: %d%n", rtn);

            robot.Sleep(1000);

            rtn = robot.SetTrajectoryJSpeed(80.0, trajspeedMode);
            System.out.printf("SetTrajectoryJSpeed is: %d%n", rtn);

            robot.Sleep(1000);
        }

        return 0;
    }

Wstępne przetwarzanie trajektorii (Look-Ahead)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.3-3.8.0

.. code-block:: Java
    :linenos:

    /** 
    * @brief Wstępne przetwarzanie trajektorii (Look-Ahead) 
    * @param [in] name  Nazwa pliku trajektorii
    * @param [in] mode Tryb próbkowania, 0-bez próbkowania; 1-równomierne próbkowanie odstępów danych; 2-próbkowanie z ograniczeniem błędu
    * @param [in] errorLim Ograniczenie błędu, obowiązuje przy użyciu aproksymacji liniowej
    * @param [in] type Sposób wygładzania, 0-wygładzanie Beziera
    * @param [in] precision Dokładność wygładzania, obowiązuje przy użyciu wygładzania Beziera
    * @param [in] vamx Ustawiona maksymalna prędkość, mm/s
    * @param [in] amax Ustawione maksymalne przyspieszenie, mm/s2
    * @param [in] jmax Ustawione maksymalne zryw, mm/s3
    * @return Kod błędu 
    */ 
    int LoadTrajectoryLA(String name, int mode, double errorLim, int type, double precision, double vamx, double amax, double jmax); 

Odtwarzanie trajektorii (Look-Ahead)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.3-3.8.0

.. code-block:: Java
    :linenos:

    /** 
    * @brief Odtwarzanie trajektorii (Look-Ahead)  
    * @return Kod błędu 
    */
    int MoveTrajectoryLA();

Przykład kodu odtwarzania trajektorii (Look-Ahead)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestLoadTrajLA(Robot robot)
    {
        int rtn = robot.TrajectoryJUpLoad("D://zUP/traj.txt");

        String traj_file_name = "/fruser/traj/traj.txt";
        rtn = robot.LoadTrajectoryLA(traj_file_name, 1, 2, 0, 2, 100, 200, 1000);

        DescPose traj_start_pose=new DescPose(0,0,0,0,0,0);
        rtn = robot.GetTrajectoryStartPose(traj_file_name, traj_start_pose);

        robot.Sleep(1000);
        robot.SetSpeed(50);
        robot.MoveCart(traj_start_pose, 0, 0, 100, 100, 100, -1, -1);

        rtn = robot.MoveTrajectoryLA();

        robot.CloseRPC();
        return 0;
    }

Ruch do punktu początkowego rejestracji trajektorii TPD
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Ruch do punktu początkowego rejestracji trajektorii TPD
    * @param name Nazwa pliku trajektorii
    * @param moveType Typ ruchu; 0-PTP; 1-LIN
    * @param ovl Procent skalowania prędkości, zakres [0~100]
    * @return Kod błędu
    */
    public int MoveToTPDStart(string name, int moveType, double ovl)

Przykład kodu SDK ruchu do punktu początkowego rejestracji trajektorii TPD
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static void testTPDmove (Robot robot)
    {
        int rtn = 0;
        int type = 1;
        String name = "tpd2025";
        int period_ms = 4;
        int di_choose = 0;
        int do_choose = 0;

        robot.SetTPDParam(type, name, period_ms, di_choose, do_choose);

        robot.Mode(1);
        robot.Sleep(1000);
        robot.DragTeachSwitch(1);
        robot.SetTPDStart(type, name, period_ms, di_choose, do_choose);
        robot.Sleep(3000);
        robot.SetWebTPDStop();
        robot.DragTeachSwitch(0);

        robot.Sleep(1000);
        double ovl = 100.0;
        int blend = 0;
        DescPose start_pose = new DescPose();
        rtn = robot.LoadTPD(name);
        System.out.printf("LoadTPD rtn is: %d\n", rtn);

        robot.GetTPDStartPose(name, start_pose);
        System.out.printf("start pose, xyz is: %f %f %f. rpy is: %f %f %f \n", start_pose.tran.x, start_pose.tran.y, start_pose.tran.z, start_pose.rpy.rx, start_pose.rpy.ry, start_pose.rpy.rz);
        //robot.MoveCart(&start_pose, 0, 0, 100, 100, ovl, -1, -1);
        //robot.Sleep(1000);

        rtn = robot.MoveToTPDStart(name, 0, 100);
        System.out.printf("MoveToTPDStart rtn is: %d\n", rtn);

        rtn = robot.MoveTPD(name, blend, ovl);
        System.out.printf("MoveTPD rtn is: %d\n", rtn);

        robot.Sleep(5000);

        robot.SetTPDDelete(name);

        return ;
    }