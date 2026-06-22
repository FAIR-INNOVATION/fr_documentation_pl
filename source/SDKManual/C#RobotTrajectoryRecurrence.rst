Odtwarzanie trajektorii robota
==============================

.. toctree:: 
    :maxdepth: 5

Ustawienie parametrów rejestracji trajektorii TPD
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ustawia parametry rejestracji trajektorii TPD
    * @param  [in] type  Typ rejestrowanych danych, 1-pozycja stawów
    * @param  [in] name  Nazwa pliku trajektorii
    * @param  [in] period_ms  Okres próbkowania danych, stała wartość 2 ms lub 4 ms lub 8 ms
    * @param  [in] di_choose  Wybór DI, bit0~bit7 odpowiadają DI0~DI7 skrzynki sterowniczej, bit8~bit9 odpowiadają końcowym DI0~DI1, 0-nie wybieraj, 1-wybierz
    * @param  [in] do_choose  Wybór DO, bit0~bit7 odpowiadają DO0~DO7 skrzynki sterowniczej, bit8~bit9 odpowiadają końcowym DO0~DO1, 0-nie wybieraj, 1-wybierz
    * @return  Kod błędu
    */
    int SetTPDParam(int type, string name, int period_ms, UInt16 di_choose, UInt16 do_choose);

Rozpoczęcie rejestracji trajektorii TPD
+++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Rozpoczyna rejestrację trajektorii TPD
    * @param  [in] type  Typ rejestrowanych danych, 1-pozycja stawów
    * @param  [in] name  Nazwa pliku trajektorii
    * @param  [in] period_ms  Okres próbkowania danych, stała wartość 2 ms lub 4 ms lub 8 ms
    * @param  [in] di_choose  Wybór DI, bit0~bit7 odpowiadają DI0~DI7 skrzynki sterowniczej, bit8~bit9 odpowiadają końcowym DI0~DI1, 0-nie wybieraj, 1-wybierz
    * @param  [in] do_choose  Wybór DO, bit0~bit7 odpowiadają DO0~DO7 skrzynki sterowniczej, bit8~bit9 odpowiadają końcowym DO0~DO1, 0-nie wybieraj, 1-wybierz
    * @return  Kod błędu
    */
    int SetTPDStart(int type, string name, int period_ms, UInt16 di_choose, UInt16 do_choose); 

Zatrzymanie rejestracji trajektorii TPD
+++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Zatrzymuje rejestrację trajektorii TPD
    * @return  Kod błędu
    */
    int SetWebTPDStop(); 

Usunięcie rejestracji trajektorii TPD
+++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Usuwa rejestrację trajektorii TPD
    * @param  [in] name  Nazwa pliku trajektorii
    * @return  Kod błędu
    */   
    int SetTPDDelete(string name); 

Wstępne ładowanie trajektorii TPD
++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Wstępne ładowanie trajektorii
    * @param  [in] name  Nazwa pliku trajektorii
    * @return  Kod błędu
    */      
    int LoadTPD(string name);

Pobranie początkowej pozycji i orientacji trajektorii TPD
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Pobiera początkową pozycję i orientację trajektorii 
    * @param [in] name  Nazwa pliku trajektorii
    * @param [out] desc_pose Początkowa pozycja i orientacja trajektorii 
    * @return Kod błędu 
    */ 
    int GetTPDStartPose(string name, ref DescPose desc_pose); 

Odtworzenie trajektorii TPD
++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Odtwarza trajektorię
    * @param  [in] name  Nazwa pliku trajektorii
    * @param  [in] blend 0-niewygładzone, 1-wygładzone
    * @param  [in] ovl  Procent skalowania prędkości, zakres [0~100]
    * @return  Kod błędu
    */
    int MoveTPD(string name, byte blend, float ovl); 

Przykład kodu rejestracji trajektorii TPD robota
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnTPDMove_Click(object sender, EventArgs e)
    {
        int type = 1;
        string name = "tpd2025";
        int period_ms = 4;
        ushort di_choose = 0;
        ushort do_choose = 0;

        robot.SetTPDParam(type, name, period_ms, di_choose, do_choose);

        robot.Mode(1);
        Thread.Sleep(1000);
        robot.DragTeachSwitch(1);
        robot.SetTPDStart(type, name, period_ms, di_choose, do_choose);
        Thread.Sleep(10000);
        robot.SetWebTPDStop();
        robot.DragTeachSwitch(0);

        float ovl = 100.0f;
        byte blend = 0;

        DescPose start_pose = new DescPose();

        int rtn = robot.LoadTPD(name);
        Console.WriteLine("LoadTPD rtn is: {0}\n", rtn);

        robot.GetTPDStartPose(name, ref start_pose);
        Console.WriteLine("start pose, xyz is: {0} {1} {2}. rpy is: {3} {4} {5} \n",
            start_pose.tran.x, start_pose.tran.y, start_pose.tran.z,
            start_pose.rpy.rx, start_pose.rpy.ry, start_pose.rpy.rz);
        robot.MoveCart(start_pose, 0, 0, 100, 100, ovl, -1, -1);
        Thread.Sleep(1000);

        rtn = robot.MoveTPD(name, blend, ovl);
        Console.WriteLine("MoveTPD rtn is: {0}\n", rtn);
        Thread.Sleep(5000);

        robot.SetTPDDelete(name);
    }

Wstępne przetwarzanie zewnętrznego pliku trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Wstępne przetwarzanie zewnętrznego pliku trajektorii 
    * @param [in] name Nazwa pliku trajektorii  
    * @param [in] ovl Procent skalowania prędkości, zakres [0~100] 
    * @param [in] opt 1-punkt sterujący, domyślnie 1 
    * @return Kod błędu 
    */ 
    int LoadTrajectoryJ(string name, float ovl, int opt); 

Odtworzenie trajektorii z zewnętrznego pliku trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Odtwarza trajektorię z zewnętrznego pliku trajektorii  
    * @return Kod błędu 
    */
    int MoveTrajectoryJ();

Pobranie początkowej pozycji trajektorii z pliku trajektorii
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Pobiera początkową pozycję trajektorii z pliku trajektorii 
    * @param [in] name Nazwa pliku trajektorii  
    * @param [out] desc_pose Początkowa pozycja i orientacja trajektorii  
    * @return Kod błędu 
    */ 
    int GetTrajectoryStartPose(string name, ref DescPose desc_pose); 

Pobranie numeru punktu trajektorii z pliku trajektorii
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Pobiera numer punktu trajektorii   
    * @param [out] pnum Numer punktu trajektorii  
    * @return Kod błędu 
    */  
    int GetTrajectoryPointNum(ref int pnum);

Ustawienie prędkości podczas odtwarzania trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ustawia prędkość podczas odtwarzania trajektorii
    * @param  [in] ovl Procent prędkości
    * @param  [in] mode 0-tryb zmniejszania prędkości 1-bezpośrednie przełączanie
    * @return  Kod błędu
    */
    public int SetTrajectoryJSpeed(double ovl, int mode = 0)

Przykład kodu ustawiania prędkości podczas odtwarzania trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public int RunTrajectoryJ(string localFilePath = "D://zUP/trajHelix_aima_1.txt", string remoteFilePath = "/fruser/traj/trajHelix_aima_1.txt",
    int initialSpeedPercent = 50, int trajSpeedMode = 1)
    {
        int rtn;

        // 1. Przesłanie pliku trajektorii J
        rtn = robot.TrajectoryJUpLoad(localFilePath);
        if (rtn != 0)
        {
            Console.WriteLine($"Upload TrajectoryJ failed: {rtn}");
            return rtn;
        }
        Console.WriteLine($"Upload TrajectoryJ success: {localFilePath}");

        // 2. Załadowanie pliku trajektorii
        rtn = robot.LoadTrajectoryJ(remoteFilePath, 100, 1);
        if (rtn != 0)
        {
            Console.WriteLine($"LoadTrajectoryJ failed: {rtn}");
            return rtn;
        }
        Console.WriteLine($"LoadTrajectoryJ success: {remoteFilePath}");

        // 3. Pobranie początkowej pozycji trajektorii
        DescPose trajStartPose = new DescPose(0, 0, 0, 0, 0, 0);
        rtn = robot.GetTrajectoryStartPose(remoteFilePath, ref trajStartPose);
        if (rtn != 0)
        {
            Console.WriteLine($"GetTrajectoryStartPose failed: {rtn}");
            return rtn;
        }
        Console.WriteLine($"Trajectory start pose: ({trajStartPose.tran.x}, {trajStartPose.tran.y}, {trajStartPose.tran.z}, " +
                            $"{trajStartPose.rpy.rx}, {trajStartPose.rpy.ry}, {trajStartPose.rpy.rz})");

        // 4. Przejście do punktu początkowego trajektorii (używając PTP w przestrzeni kartezjańskiej)
        robot.SetSpeed(initialSpeedPercent);
        rtn = robot.MoveCart(trajStartPose, 0, 0, 100, 100, 100, -1, -1);
        if (rtn != 0)
        {
            Console.WriteLine($"MoveCart to start pose failed: {rtn}");
            return rtn;
        }

        // 5. Pobranie liczby punktów trajektorii (opcjonalne, tylko do wyświetlenia)
        int trajPointNum = 0;
        rtn = robot.GetTrajectoryPointNum(ref trajPointNum);
        if (rtn != 0)
        {
            Console.WriteLine($"GetTrajectoryPointNum failed: {rtn}");
            // Nie zwracaj, kontynuuj wykonywanie
        }
        else
        {
            Console.WriteLine($"Trajectory points count: {trajPointNum}");
        }

        // 6. Rozpoczęcie wykonywania ruchu trajektorii (nieblokujące)
        rtn = robot.MoveTrajectoryJ();
        if (rtn != 0)
        {
            Console.WriteLine($"MoveTrajectoryJ failed: {rtn}");
            return rtn;
        }
        Console.WriteLine("MoveTrajectoryJ started.");

        // 7. Dynamiczna zmiana prędkości podczas ruchu (naprzemiennie 10% i 80%)
        // Użyj GetRobotMotionDone do sprawdzenia, czy ruch został zakończony
        byte motionDone = 0;
        robot.GetRobotMotionDone(ref motionDone);

        while (motionDone == 0)
        {
            // Ustaw prędkość na 10%
            rtn = robot.SetTrajectoryJSpeed(10.0, trajSpeedMode);
            Console.WriteLine($"SetTrajectoryJSpeed to 10% returned: {rtn}");
            robot.Sleep(1000);

            // Ponownie sprawdź stan ruchu
            robot.GetRobotMotionDone(ref motionDone);
            if (motionDone != 0) break;

            // Ustaw prędkość na 80%
            rtn = robot.SetTrajectoryJSpeed(80.0, trajSpeedMode);
            Console.WriteLine($"SetTrajectoryJSpeed to 80% returned: {rtn}");
            robot.Sleep(1000);

            // Ponownie sprawdź stan ruchu
            robot.GetRobotMotionDone(ref motionDone);
        }

        Console.WriteLine("Trajectory J motion completed.");
        return 0;
    }

Ustawienie siły i momentu podczas odtwarzania trajektorii
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Ustawia siłę i moment podczas odtwarzania trajektorii  
    * @param [in] ft Siły w trzech kierunkach i momenty obrotowe, jednostka N i Nm
    * @return Kod błędu 
    */
    int SetTrajectoryJForceTorque(ForceTorque ft); 

Ustawienie siły wzdłuż osi X podczas odtwarzania trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Ustawia siłę wzdłuż osi X podczas odtwarzania trajektorii  
    * @param [in] fx  Siła wzdłuż osi X, jednostka N
    * @return Kod błędu 
    */
    int SetTrajectoryJForceFx(double fx);

Ustawienie siły wzdłuż osi Y podczas odtwarzania trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Ustawia siłę wzdłuż osi Y podczas odtwarzania trajektorii  
    * @param [in] fy  Siła wzdłuż osi Y, jednostka N
    * @return Kod błędu 
    */
    int SetTrajectoryJForceFy(double fy);

Ustawienie siły wzdłuż osi Z podczas odtwarzania trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Ustawia siłę wzdłuż osi Z podczas odtwarzania trajektorii  
    * @param [in] fz  Siła wzdłuż osi Z, jednostka N
    * @return Kod błędu 
    */
    int SetTrajectoryJForceFz(double fz);

Ustawienie momentu obrotowego wokół osi X podczas odtwarzania trajektorii
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Ustawia moment obrotowy wokół osi X podczas odtwarzania trajektorii  
    * @param [in] tx  Moment obrotowy wokół osi X, jednostka Nm
    * @return Kod błędu 
    */
    int SetTrajectoryJTorqueTx(double tx);

Ustawienie momentu obrotowego wokół osi Y podczas odtwarzania trajektorii
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Ustawia moment obrotowy wokół osi Y podczas odtwarzania trajektorii  
    * @param [in] ty  Moment obrotowy wokół osi Y, jednostka Nm
    * @return Kod błędu 
    */
    int SetTrajectoryJTorqueTy(double ty);

Ustawienie momentu obrotowego wokół osi Z podczas odtwarzania trajektorii
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Ustawia moment obrotowy wokół osi Z podczas odtwarzania trajektorii  
    * @param [in] tz  Moment obrotowy wokół osi Z, jednostka Nm
    * @return Kod błędu 
    */
    int SetTrajectoryJTorqueTz(double tz);

Przesłanie pliku trajektorii J
++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Przesyła plik trajektorii J
    * @param [in] filePath Pełna ścieżka przesyłanego pliku trajektorii   C://test/testJ.txt
    * @return Kod błędu
    */
    int TrajectoryJUpLoad(string filePath);

Usunięcie pliku trajektorii J
++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Usuwa plik trajektorii J
    * @param [in] fileName Nazwa pliku testJ.txt
    * @return Kod błędu
    */
    int TrajectoryJDelete(string fileName);

Przykład kodu odtwarzania pliku trajektorii J robota
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button33_Click(object sender, EventArgs e)
    {
        int rtn = robot.TrajectoryJUpLoad("D://zUP/spray_traj1.txt");
        Console.WriteLine("Upload TrajectoryJ A {0}\n", rtn);

        string traj_file_name = "/fruser/traj/spray_traj1.txt";
        rtn = robot.LoadTrajectoryJ(traj_file_name, 100, 1);
        Console.WriteLine("LoadTrajectoryJ {0}, rtn is: {1}\n", traj_file_name, rtn);

        DescPose traj_start_pose = new DescPose();
        rtn = robot.GetTrajectoryStartPose(traj_file_name, ref traj_start_pose);
        Console.WriteLine("GetTrajectoryStartPose is: {0}\n", rtn);
        Console.WriteLine("desc_pos:{0},{1},{2},{3},{4},{5}\n",
            traj_start_pose.tran.x, traj_start_pose.tran.y, traj_start_pose.tran.z,
            traj_start_pose.rpy.rx, traj_start_pose.rpy.ry, traj_start_pose.rpy.rz);

        Thread.Sleep(1000);

        robot.SetSpeed(50);
        robot.MoveCart(traj_start_pose, 0, 0, 100, 100, 100, -1, -1);

        int traj_num = 0;
        rtn = robot.GetTrajectoryPointNum(ref traj_num);
        Console.WriteLine("GetTrajectoryStartPose rtn is: {0}, traj num is: {1}\n", rtn, traj_num);

        rtn = robot.SetTrajectoryJSpeed(50.0f);
        Console.WriteLine("SetTrajectoryJSpeed is: {0}\n", rtn);

        ForceTorque traj_force = new ForceTorque();
        traj_force.fx = 10;
        rtn = robot.SetTrajectoryJForceTorque(traj_force);
        Console.WriteLine("SetTrajectoryJForceTorque rtn is: {0}\n", rtn);

        rtn = robot.SetTrajectoryJForceFx(10.0f);
        Console.WriteLine("SetTrajectoryJForceFx rtn is: {0}\n", rtn);

        rtn = robot.SetTrajectoryJForceFy(0.0f);
        Console.WriteLine("SetTrajectoryJForceFy rtn is: {0}\n", rtn);

        rtn = robot.SetTrajectoryJForceFz(0.0f);
        Console.WriteLine("SetTrajectoryJForceFz rtn is: {0}\n", rtn);

        rtn = robot.SetTrajectoryJTorqueTx(10.0f);
        Console.WriteLine("SetTrajectoryJTorqueTx rtn is: {0}\n", rtn);

        rtn = robot.SetTrajectoryJTorqueTy(10.0f);
        Console.WriteLine("SetTrajectoryJTorqueTy rtn is: {0}\n", rtn);

        rtn = robot.SetTrajectoryJTorqueTz(10.0f);
        Console.WriteLine("SetTrajectoryJTorqueTz rtn is: {0}\n", rtn);

        rtn = robot.MoveTrajectoryJ();
        Console.WriteLine("MoveTrajectoryJ rtn is: {0}\n", rtn);
    }

Wstępne przetwarzanie trajektorii (wyprzedzenie trajektorii)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Wstępne przetwarzanie trajektorii (wyprzedzenie trajektorii)
    * @param  [in] name  Nazwa pliku trajektorii
    * @param  [in] mode Tryb próbkowania, 0-brak próbkowania; 1-próbkowanie w równych odstępach danych; 2-próbkowanie z ograniczeniem błędu
    * @param  [in] errorLim Ograniczenie błędu, stosowane przy aproksymacji liniowej
    * @param  [in] type Sposób wygładzania, 0-wygładzanie Beziera
    * @param  [in] precision Dokładność wygładzania, stosowana przy wygładzaniu Beziera
    * @param  [in] vamx Ustawiona maksymalna prędkość, mm/s
    * @param  [in] amax Ustawione maksymalne przyspieszenie, mm/s²
    * @param  [in] jmax Ustawione maksymalne gwałtowność, mm/s³
    * @return  Kod błędu   
    */
    int LoadTrajectoryLA(string name, int mode, double errorLim, int type, double precision, double vamx, double amax, double jmax);

Odtworzenie trajektorii (wyprzedzenie trajektorii)
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Odtwarza trajektorię (wyprzedzenie trajektorii)
    * @return  Kod błędu   
    */
    int MoveTrajectoryLA();

Przykład kodu odtwarzania trajektorii (wyprzedzenie trajektorii)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button8_Click(object sender, EventArgs e)
    {
        int rtn = 0;

        string nameA = "/fruser/traj/A.txt";
        string nameB = "/fruser/traj/B.txt";

        rtn = robot.LoadTrajectoryLA(nameB, 0, 0, 0, 1, 100.0, 100.0, 1000.0);    // Aproksymacja liniowa
        Console.WriteLine($"LoadTrajectoryLA rtn is {rtn}");

        DescPose startPos = new DescPose(0, 0, 0, 0, 0, 0);
        robot.GetTrajectoryStartPose(nameA, ref startPos);

        //
        robot.MoveCart(startPos, 1, 0, (float)100.0, (float)100.0, (float)100.0, -1, -1);

        rtn = robot.MoveTrajectoryLA();
        Console.WriteLine($"MoveTrajectoryLA rtn is {rtn}");
    }

Przejście do punktu początkowego rejestracji trajektorii TPD
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Przejście do punktu początkowego rejestracji trajektorii TPD
    * @param [in] name Nazwa pliku trajektorii
    * @param [in] moveType Typ ruchu; 0-PTP; 1-LIN
    * @param [in] ovl Procent skalowania prędkości, zakres [0~100]
    * @return Kod błędu
    */
    public int MoveToTPDStart(string name, int moveType, double ovl)

Przykład kodu SDK przejścia do punktu początkowego rejestracji trajektorii TPD
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    void testTPDmove()
    {
        string name = "tpd2025";
        int type = 1;
        int period_ms = 4;
        int rtn = 0;
        UInt16 di_choose = 0;
        UInt16 do_choose = 0;

        robot.SetTPDParam(type, name, period_ms, di_choose, do_choose);

        robot.Mode(1);
        Thread.Sleep(3000);
        robot.DragTeachSwitch(1);
        robot.SetTPDStart(type, name, period_ms, di_choose, do_choose);
        Thread.Sleep(3000);
        robot.SetWebTPDStop();
        robot.DragTeachSwitch(0);

        Thread.Sleep(1000);
        float ovl = 100.0f;
        byte blend = 0;
        DescPose start_pose = new DescPose();
        rtn = robot.LoadTPD(name);
        Console.WriteLine($"LoadTPD rtn is:{rtn}\n");

        robot.GetTPDStartPose(name, ref start_pose);
        Console.WriteLine($"start pose, xyz is: %f %f %f. rpy is: {start_pose.tran.x},{start_pose.tran.y}, {start_pose.tran.z}, {start_pose.rpy.rx}, {start_pose.rpy.ry}, {start_pose.rpy.rz}");

        rtn = robot.MoveToTPDStart(name, 0, 100.0);

        rtn = robot.MoveTPD(name, blend, ovl);
        Thread.Sleep(5000*5);

        robot.SetTPDDelete(name);
    }