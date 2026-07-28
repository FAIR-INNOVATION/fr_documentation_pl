Urządzenia peryferyjne robota
=============================

.. toctree:: 
    :maxdepth: 5

Konfiguracja chwytaka
+++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Konfiguruje chwytak
    * @param  [in] company  Producent chwytaka, do ustalenia
    * @param  [in] device  Numer urządzenia, tymczasowo nieużywane, domyślnie 0
    * @param  [in] softvesion  Numer wersji oprogramowania, tymczasowo nieużywane, domyślnie 0
    * @param  [in] bus Pozycja magistrali, na której zawieszono urządzenie, tymczasowo nieużywane, domyślnie 0
    * @return  Kod błędu
    */
    int SetGripperConfig(int company, int device, int softvesion, int bus);

Pobranie konfiguracji chwytaka
++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera konfigurację chwytaka
    * @param  [in] company  Producent chwytaka, do ustalenia
    * @param  [in] device  Numer urządzenia, tymczasowo nieużywane, domyślnie 0
    * @param  [in] softvesion  Numer wersji oprogramowania, tymczasowo nieużywane, domyślnie 0
    * @param  [in] bus Pozycja magistrali, na której zawieszono urządzenie, tymczasowo nieużywane, domyślnie 0
    * @return  Kod błędu
    */
    int GetGripperConfig(int *company, int *device, int *softvesion, int *bus);

Aktywacja chwytaka
++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Aktywuje chwytak
    * @param  [in] index  Numer chwytaka
    * @param  [in] act  0-reset, 1-aktywacja
    * @return  Kod błędu
    */
    int ActGripper(int index, byte act); 

Sterowanie chwytakiem
+++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Steruje chwytakiem
    * @param  [in] index  Numer chwytaka
    * @param  [in] pos  Procent pozycji, zakres [0~100]
    * @param  [in] vel  Procent prędkości, zakres [0~100]
    * @param  [in] force  Procent momentu, zakres [0~100]
    * @param  [in] max_time  Maksymalny czas oczekiwania, zakres [0~30000], jednostka ms
    * @param  [in] block  0-blokujące, 1-nieblokujące
    * @param  [in] type Typ chwytaka, 0-chwytak równoległy; 1-chwytak obrotowy
    * @param  [in] rotNum Liczba obrotów
    * @param  [in] rotVel Procent prędkości obrotowej [0-100]
    * @param  [in] rotTorque Procent momentu obrotowego [0-100]
    * @return  Kod błędu
    */
    int MoveGripper(int index, int pos, int vel, int force, int max_time, byte block, int type, double rotNum, int rotVel, int rotTorque);

Pobranie stanu ruchu chwytaka
+++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera stan ruchu chwytaka
    * @param  [out] fault  0-brak błędu, 1-wystąpił błąd
    * @param  [out] staus  0-ruch nieukończony, 1-ruch ukończony
    * @return  Kod błędu
    */
    int GetGripperMotionDone(ref int fault, ref int status); 

Pobranie stanu aktywacji chwytaka
+++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera stan aktywacji chwytaka
    * @param  [out] fault  0-brak błędu, 1-wystąpił błąd
    * @param  [out] status  bit0~bit15 odpowiadają numerom chwytaka 0~15, bit=0 oznacza nieaktywny, bit=1 oznacza aktywny
    * @return  Kod błędu
    */
    int GetGripperActivateStatus(ref int fault, ref int status);

Pobranie pozycji chwytaka
+++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera pozycję chwytaka
    * @param  [out] fault  0-brak błędu, 1-wystąpił błąd
    * @param  [out] position  Procent pozycji, zakres 0~100%
    * @return  Kod błędu
    */
    int GetGripperCurPosition(ref int fault, ref int position);

Pobranie prędkości chwytaka
+++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera prędkość chwytaka
    * @param  [out] fault  0-brak błędu, 1-wystąpił błąd
    * @param  [out] speed  Procent prędkości, zakres 0~100%
    * @return  Kod błędu
    */
    int GetGripperCurSpeed(ref int fault, ref int speed);
     
Pobranie prądu chwytaka
+++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera prąd chwytaka
    * @param  [out] fault  0-brak błędu, 1-wystąpił błąd
    * @param  [out] current  Procent prądu, zakres 0~100%
    * @return  Kod błędu
    */
    int GetGripperCurCurrent(ref int fault, ref int current);

Pobranie napięcia chwytaka
++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera napięcie chwytaka
    * @param  [out] fault  0-brak błędu, 1-wystąpił błąd
    * @param  [out] voltage  Napięcie, jednostka 0,1 V
    * @return  Kod błędu
    */
    int GetGripperVoltage(ref int fault, ref int voltage);

Pobranie temperatury chwytaka
+++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera temperaturę chwytaka
    * @param  [out] fault  0-brak błędu, 1-wystąpił błąd
    * @param  [out] temp  Temperatura, jednostka °C
    * @return  Kod błędu
    */
    int GetGripperTemp(ref int fault, ref int temp);

Obliczenie punktu wstępnego chwytania - wizja
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Oblicza punkt wstępnego chwytania - wizja 
    * @param [in] desc_pos Pozycja i orientacja kartezjańska punktu chwytania 
    * @param [in] zlength Przesunięcie w osi Z 
    * @param [in] zangle Przesunięcie kątowe wokół osi Z
    * @param [out] pre_pos Punkt wstępnego chwytania
    * @return Kod błędu 
    */ 
    int ComputePrePick(DescPose desc_pos, double zlength, double zangle, ref DescPose pre_pos);

Obliczenie punktu wycofania - wizja
+++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Oblicza punkt wycofania - wizja 
    * @param [in] desc_pos Pozycja i orientacja kartezjańska punktu wycofania 
    * @param [in] zlength Przesunięcie w osi Z 
    * @param [in] zangle Przesunięcie kątowe wokół osi Z
    * @param [out] post_pos Punkt wycofania
    * @return Kod błędu 
    */ 
    int ComputePostPick(DescPose desc_pos, double zlength, double zangle, ref DescPose post_pos);

Przykład kodu operacji chwytakiem robota
++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button36_Click(object sender, EventArgs e)
    {
        int company = 4;
        int device = 0;
        int softversion = 0;
        int bus = 2;
        int index = 2;
        byte act = 0;
        int max_time = 30000;
        byte block = 0;
        int status=0;
        int fault=0;
        int active_status = 0;
        int current_pos = 0;
        int current = 0;
        int voltage = 0;
        int temp = 0;
        int speed = 0;

        robot.SetGripperConfig(company, device, softversion, bus);
        Thread.Sleep(1000);
        robot.GetGripperConfig(ref company, ref device, ref softversion, ref bus);
        Console.WriteLine("gripper config:{0},{1},{2},{3}\n", company, device, softversion, bus);

        robot.ActGripper(index, act);
        Thread.Sleep(1000);
        act = 1;
        robot.ActGripper(index, act);
        Thread.Sleep(1000);

        robot.MoveGripper(index, 90, 50, 50, max_time, block, 0, 0, 0, 0);
        Thread.Sleep(1000);
        robot.MoveGripper(index, 30, 50, 0, max_time, block, 0, 0, 0, 0);

        robot.GetGripperMotionDone(ref fault, ref status);
        Console.WriteLine("motion status:{0},{1}\n", fault, status);

        robot.GetGripperActivateStatus(ref fault, ref active_status);
        Console.WriteLine("gripper active fault is: {0}, status is: {1}\n", fault, active_status);

        robot.GetGripperCurPosition(ref fault, ref current_pos);
        Console.WriteLine("fault is:{0}, current position is: {1}\n", fault, current_pos);

        robot.GetGripperCurCurrent(ref fault, ref current);
        Console.WriteLine("fault is:{0}, current current is: {1}\n", fault, current);

        robot.GetGripperVoltage(ref fault, ref voltage);
        Console.WriteLine("fault is:{0}, current voltage is: {1} \n", fault, voltage);

        robot.GetGripperTemp(ref fault, ref temp);
        Console.WriteLine("fault is:{0}, current temperature is: {1}\n", fault, temp);

        robot.GetGripperCurSpeed(ref fault, ref speed);
        Console.WriteLine("fault is:{0}, current speed is: {1}\n", fault, speed);

        int retval = 0;
        DescPose prepick_pose = new DescPose();
        DescPose postpick_pose = new DescPose();

        DescPose p1Desc = new DescPose(-419.524f, -13.000f, 351.569f, -178.118f, 0.314f, 3.833f);
        DescPose p2Desc = new DescPose(-321.222f, 185.189f, 335.520f, -179.030f, -1.284f, -29.869f);

        retval = robot.ComputePrePick(p1Desc, 10, 0, ref prepick_pose);
        Console.WriteLine("ComputePrePick retval is: {0}\n", retval);
        Console.WriteLine("xyz is: {0}, {1}, {2}; rpy is: {3}, {4}, {5}\n",
            prepick_pose.tran.x, prepick_pose.tran.y, prepick_pose.tran.z,
            prepick_pose.rpy.rx, prepick_pose.rpy.ry, prepick_pose.rpy.rz);

        retval = robot.ComputePostPick( p2Desc, -10, 0, ref postpick_pose);
        Console.WriteLine("ComputePostPick retval is: {0}\n", retval);
        Console.WriteLine("xyz is: {0}, {1}, {2}; rpy is: {3}, {4}, {5}\n",
            postpick_pose.tran.x, postpick_pose.tran.y, postpick_pose.tran.z,
            postpick_pose.rpy.rx, postpick_pose.rpy.ry, postpick_pose.rpy.rz);

    }

Pobranie liczby obrotów chwytaka obrotowego
+++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera liczbę obrotów chwytaka obrotowego
    * @param  [out] fault  0-brak błędu, 1-wystąpił błąd
    * @param  [out] num  Liczba obrotów
    * @return  Kod błędu
    */
    int GetGripperRotNum(ref UInt16 fault, ref double num);

Pobranie procentu prędkości obrotowej chwytaka obrotowego
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera procent prędkości obrotowej chwytaka obrotowego
    * @param  [out] fault  0-brak błędu, 1-wystąpił błąd
    * @param  [out] speed  Procent prędkości obrotowej
    * @return  Kod błędu
    */
    int GetGripperRotSpeed(ref UInt16 fault, ref int speed);

Pobranie procentu momentu obrotowego chwytaka obrotowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera procent momentu obrotowego chwytaka obrotowego
    * @param  [out] fault  0-brak błędu, 1-wystąpił błąd
    * @param  [out] torque  Procent momentu obrotowego
    * @return  Kod błędu
    */
    int GetGripperRotTorque(ref UInt16 fault, ref int torque);

Przykład kodu pobierania stanu chwytaka obrotowego
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    int MoveRotGripper(int pos, double rotPos)
    {
        robot.ResetAllError();
        robot.ActGripper(1, 1);
        Thread.Sleep(1000);
        int rtn = robot.MoveGripper(1, pos, 50, 50, 5000, 1, 1, rotPos, 50, 100);
        Console.WriteLine($"move gripper rtn is {rtn}" );
        UInt16 fault = 0;
        double rotNum = 0.0;
        int rotSpeed = 0;
        int rotTorque = 0;
        robot.GetGripperRotNum(ref fault, ref rotNum);
        robot.GetGripperRotSpeed(ref fault, ref rotSpeed);
        robot.GetGripperRotTorque(ref fault, ref rotTorque);
        Console.WriteLine($"gripper rot num :{ rotNum}, gripper rotSpeed :{rotSpeed}, gripper rotTorque : { rotTorque}");
        return 0;
    }

Uruchomienie, zatrzymanie taśmociągu
++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Uruchomienie, zatrzymanie taśmociągu 
    * @param [in] status Stan, 1-uruchom, 0-zatrzymaj
    * @return Kod błędu 
    */ 
    int ConveyorStartEnd(byte status); 

Zapis punktu detekcji I/O
+++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Zapis punktu detekcji I/O 
    * @return Kod błędu 
    */ 
    int ConveyorPointIORecord(); 

Zapis punktu A
++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Zapis punktu A 
    * @return Kod błędu 
    */ 
    int ConveyorPointARecord();

Zapis punktu odniesienia
++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Zapis punktu odniesienia 
    * @return Kod błędu 
    */ 
    int ConveyorRefPointRecord(); 

Zapis punktu B
++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Zapis punktu B 
    * @return Kod błędu 
    */ 
    int ConveyorPointBRecord();

Detekcja I/O przedmiotu na taśmociągu
+++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Detekcja I/O przedmiotu na taśmociągu 
    * @param [in] max_t Maksymalny czas detekcji, jednostka ms
    * @return Kod błędu 
    */ 
    int ConveyorIODetect(int max_t);

Pobranie bieżącej pozycji przedmiotu
++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Pobranie bieżącej pozycji przedmiotu 
    * @param [in] mode 1-śledzenie chwytania, 2-śledzenie ruchu, 3-śledzenie TPD
    * @return Kod błędu 
    */ 
    int ConveyorGetTrackData(int mode);

Rozpoczęcie śledzenia taśmociągu
++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Rozpoczęcie śledzenia taśmociągu 
    * @param [in] status Stan, 1-uruchom, 0-zatrzymaj
    * @return Kod błędu 
    */
    int ConveyorTrackStart(byte status);

Zatrzymanie śledzenia taśmociągu
++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Zatrzymanie śledzenia taśmociągu 
    * @return Kod błędu 
    */
    int ConveyorTrackEnd();

Konfiguracja Parametrów Śledzenia w Miejscu na Taśmie Transportowej
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Konfiguruje parametry śledzenia w miejscu na taśmie transportowej
    * @param  [in] trackMode 0-czas; 1-odległość; 2-czas i odległość, dowolny warunek spełniony
    * @param  [in] trackTime Czas śledzenia, jednostka s
    * @param  [in] trackDis Odległość śledzenia
    * @return  Kod błędu
    */
    public int SetStationaryTrackPara(int trackMode, double trackTime, int trackDis)
    
Oczekiwanie na Zakończenie Ruchu Pustego w Miejscu
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Oczekuje na zakończenie ruchu pustego w miejscu
    * @return Kod błędu
    */
    public int WaitStationaryMotionDone()
        
Przykład Kodu Ruchu Śledzenia w Miejscu na Taśmie Transportowej
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public int TestStationaryTrack()
    {
        Console.WriteLine("\n========== Stationary Track Test ==========");

        int rtn;

        JointPos j1 = new JointPos(-35.146, -102.684, 120.805, -100.401, -90.295, 150.105);
        DescPose d1 = new DescPose(-121.814, -348.341, 209.978, -173.152, -3.585, -5.446);

        ExaxisPos ex = new ExaxisPos(0, 0, 0, 0);
        DescPose zeroOff = new DescPose(0, 0, 0, 0, 0, 0);

        int tool = 1;
        int workpiece = 1;

        rtn = robot.ConveyorSetParam(0, 10000, 200, 0, 0, 10);

        robot.MoveJ(j1, d1, tool, workpiece, 100, 100, 100, ex, -1, 0, zeroOff);

        // Step 1: Sygnał sterujący SetDO WŁ.
        Console.WriteLine("--- Step 1: SetDO(6,1) ---");
        rtn = robot.SetDO(6, 1, 0, 0);
        Console.WriteLine("  SetDO(6,1) rtn={0}", rtn);

        // Step 2: Rozpoczęcie śledzenia taśmy
        Console.WriteLine("--- Step 2: ConveyorTrackStart(2) ---");
        rtn = robot.ConveyorTrackStart(2);
        Console.WriteLine("  ConveyorTrackStart(2) rtn={0}", rtn);

        // Step 3: Detekcja IO przedmiotu
        Console.WriteLine("--- Step 3: ConveyorIODetect(10000) ---");
        rtn = robot.ConveyorIODetect(10000);
        Console.WriteLine("  ConveyorIODetect(10000) rtn={0}", rtn);

        // Step 4: Pobierz dane śledzenia
        Console.WriteLine("--- Step 4: ConveyorGetTrackData(2) ---");
        rtn = robot.ConveyorGetTrackData(2);
        Console.WriteLine("  ConveyorGetTrackData(2) rtn={0}", rtn);

        // Step 5: Konfiguracja parametrów śledzenia stacjonarnego (tryb czasu, 200s, odległość 5)
        Console.WriteLine("--- Step 5: SetStationaryTrackPara(0,200,5) ---");
        rtn = robot.SetStationaryTrackPara(0, 5, 5);
        Console.WriteLine("  SetStationaryTrackPara(0,200,5) rtn={0}", rtn);

        // Step 6: Wykonaj ruch stacjonarny
        Console.WriteLine("--- Step 6: MoveStationary() ---");
        rtn = robot.MoveStationary();
        Console.WriteLine("  MoveStationary() rtn={0}", rtn);

        // Step 7: Oczekuj na zakończenie ruchu stacjonarnego
        Console.WriteLine("--- Step 7: WaitStationaryMotionDone() ---");
        rtn = robot.WaitStationaryMotionDone();
        Console.WriteLine("  WaitStationaryMotionDone() rtn={0}", rtn);

        // Step 8: Zakończenie śledzenia taśmy
        Console.WriteLine("--- Step 8: ConveyorTrackEnd() ---");
        rtn = robot.ConveyorTrackEnd();
        Console.WriteLine("  ConveyorTrackEnd() rtn={0}", rtn);

        // Step 9: Sygnał sterujący SetDO WYŁ.
        Console.WriteLine("--- Step 9: SetDO(6,0) ---");
        rtn = robot.SetDO(6, 0, 0, 0);
        Console.WriteLine("  SetDO(6,0) rtn={0}", rtn);

        Console.WriteLine("\n========== Stationary Track Test Complete ==========");
        return 0;
    }    

Konfiguracja parametrów taśmociągu
++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Konfiguracja parametrów taśmociągu
    * @param [in] para[0] Kanał enkodera 1~2
    * @param [in] para[1] Liczba impulsów enkodera na jeden obrót
    * @param [in] para[2] Odległość przebyta przez taśmociąg na jeden obrót enkodera
    * @param [in] para[3] Numer układu współrzędnych przedmiotu dla funkcji śledzenia ruchu, dla śledzenia chwytania i śledzenia TPD ustaw na 0
    * @param [in] para[4] Czy z wizją 0-bez 1-z
    * @param [in] para[5] Współczynnik prędkości dla opcji śledzenia chwytania taśmociągu (1-100) dla innych opcji domyślnie 1 
    * @return Kod błędu
    */
    int ConveyorSetParam(int encChannel, int resolution, double lead, int wpAxis, int vision, double speedRadio, int followType, int startDis=0, int endDis=100);

Ustawienie kompensacji punktu chwytania taśmociągu
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Ustawienie kompensacji punktu chwytania taśmociągu 
    * @param [in] cmp Pozycja kompensacji double[3]{x, y, z}
    * @return Kod błędu 
    */
    int ConveyorCatchPointComp(double[] cmp);

Ruch liniowy śledzenia taśmociągu
+++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Ruch liniowy śledzenia taśmociągu 
    * @param [in] name Nazwa punktu ruchu
    * @param [in] tool Numer układu współrzędnych narzędzia, zakres [0~14] 
    * @param [in] wobj Numer układu współrzędnych przedmiotu, zakres [0~14] 
    * @param [in] vel Procent prędkości, zakres [0~100] 
    * @param [in] acc Procent przyspieszenia, zakres [0~100], tymczasowo nieudostępnione 
    * @param [in] ovl Współczynnik skalowania prędkości, zakres [0~100] 
    * @param [in] blendR [-1.0]-ruch do pozycji (blokujący), [0~1000.0]-promień wygładzenia (nieblokujący), jednostka mm  
    * @return Kod błędu 
    */
    int ConveyorTrackMoveL(string name, int tool, int wobj, float vel, float acc, float ovl, float blendR);

Detekcja wejścia komunikacji taśmociągu
+++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Detekcja wejścia komunikacji taśmociągu
    * @param [in] timeout Czas oczekiwania na przekroczenie limitu ms
    * @return Kod błędu
    */
    public int ConveyorComDetect(int timeout)

Wyzwolenie detekcji wejścia komunikacji taśmociągu
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Wyzwolenie detekcji wejścia komunikacji taśmociągu
    * @return Kod błędu
    */
    int ConveyorComDetectTrigger();

Przykładowy program wyzwalania detekcji wejścia komunikacji taśmociągu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button3_Click(object sender, EventArgs e)
    {

        // Wyłącz przycisk, aby zapobiec wielokrotnemu kliknięciu
        button3.Enabled = false;

        // Wykonaj operację czasochłonną w wątku tła
        Thread conveyorThread = new Thread(ConveyorTest);
        conveyorThread.IsBackground = true;
        conveyorThread.Start();
    }

    private void button4_Click(object sender, EventArgs e)
    {
        // Pobierz dane wejściowe użytkownika
        string input = texBox.Text;
        Console.WriteLine($"please input a number to trigger:{input}");
    
        int rtn = robot.ConveyorComDetectTrigger();
        Console.WriteLine($"ConveyorComDetectTrigger 返回值: {rtn}");
        
    }

    private void ConveyorTest()
    {
        // Użyj Invoke do aktualizacji kontrolek w wątku UI
        this.Invoke((MethodInvoker)delegate {
            Console.WriteLine("开始传送带测试...");
        });

        int retval = 0;
        int index = 1;
        int max_time = 30000;
        bool block = false;
        retval = 0;

        /* Przebieg chwytania taśmociągu */
        DescPose startdescPose = new DescPose(139.176f, 4.717f, 9.088f, -179.999f, -0.004f, -179.990f);
        JointPos startjointPos = new JointPos(-34.129f, -88.062f, 97.839f, -99.780f, -90.003f, -34.140f);

        DescPose homePose = new DescPose(139.177f, 4.717f, 69.084f, -180.000f, -0.004f, -179.989f);
        JointPos homejointPos = new JointPos(-34.129f, -88.618f, 84.039f, -85.423f, -90.003f, -34.140f);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        // Przejdź do bezpiecznej pozycji
        retval = robot.MoveL(homejointPos, homePose, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 1, 1);
        Console.WriteLine($"MoveL 到安全位置返回值: {retval}");

        // Detekcja taśmociągu
        retval = robot.ConveryComDetect(1000 * 10);
        Console.WriteLine($"ConveyorComDetect 返回值: {retval}");

        // Pobierz dane śledzenia
        retval = robot.ConveyorGetTrackData(2);
        Console.WriteLine($"ConveyorGetTrackData 返回值: {retval}");

        // Rozpocznij śledzenie
        retval = robot.ConveyorTrackStart(2);
        Console.WriteLine($"ConveyorTrackStart 返回值: {retval}");

        // Przejdź do pozycji początkowej
        robot.MoveL(startjointPos, startdescPose, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 1, 1);
        robot.MoveL(startjointPos, startdescPose, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 1, 1);

        // Zakończ śledzenie
        retval = robot.ConveyorTrackEnd();
        Console.WriteLine($"ConveyorTrackEnd 返回值: {retval}");

        // Wróć do bezpiecznej pozycji
        robot.MoveL(homejointPos, homePose, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 1, 1);

        this.Invoke((MethodInvoker)delegate {
            Console.WriteLine("传送带测试完成!");
            button3.Enabled = true;
        });
    }

Przykładowy program operacji taśmociągu robota
++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnConvert_Click(object sender, EventArgs e)
    {
        // Conveyor belt tracking
        DescPose pos1 = new DescPose(-354.549, 63.914, 270.176, -179.679, -0.134, 2.468);
        DescPose pos2 = new DescPose(-351.203, -213.393, 351.054, -179.932, -0.508, 2.472);

        double[] cmp = { 0.0, 0.0, 0.0 };
        int rtn = robot.ConveyorCatchPointComp(cmp); // Set conveyor pick-up point compensation
        if (rtn != 0)
        {
            return;
        }
        Console.WriteLine("ConveyorCatchPointComp: rtn  " + rtn);

        rtn = robot.MoveCart(pos1, 1, 0, (float)30.0, (float)180.0, (float)100.0, (float)-1.0, -1);
        Console.WriteLine("MoveCart: rtn  " + rtn);

        rtn = robot.ConveyorIODetect(10000); // Conveyor workpiece I/O detection
        Console.WriteLine("ConveyorIODetect: rtn   " + rtn);

        robot.ConveyorGetTrackData(1); // Configure conveyor tracking for picking
        rtn = robot.ConveyorTrackStart(1); // Start tracking
        Console.WriteLine("ConveyorTrackStart: rtn  " + rtn);

        rtn = robot.ConveyorTrackMoveL("cvrCatchPoint", 1, 0, (float)100.0, (float)0.0, (float)100.0, (float)-1.0, 0, 0);
        Console.WriteLine("ConveyorTrackMoveL: rtn  " + rtn);

        rtn = robot.MoveGripper(2, 30, 60, 30, 30000, 0, 0, 0, 50, 50);
        Console.WriteLine("ConveyorTrackMoveL: rtn  " + rtn);
            

        rtn = robot.ConveyorTrackMoveL("cvrRaisePoint", 1, 0, (float)100.0, (float)0.0, (float)100.0, (float)-1.0, 0, 0);
        Console.WriteLine("ConveyorTrackMoveL: rtn   " + rtn);

        rtn = robot.ConveyorTrackEnd(); // Stop conveyor tracking
        Console.WriteLine("ConveyorTrackEnd: rtn  " + rtn);

        rtn = robot.MoveCart(pos2, 1, 0, (float)30.0, (float)180.0, (float)100.0, (float)-1.0, -1);
        Console.WriteLine("MoveCart: rtn  " + rtn);

        rtn = robot.MoveGripper(2, 100, 60, 30, 30000, 0,0,0,50,50);
        Console.WriteLine("MoveGripper: rtn  " + rtn);

    }

Konfiguracja czujnika końcowego
+++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Konfiguruje czujnik końcowy
    * @param  [in] idCompany Producent, 18-JUNKONG; 25-HUIDE
    * @param  [in] idDevice Typ, 0-JUNKONG/RYR6T.V1.0
    * @param  [in] idSoftware Wersja oprogramowania, 0-J1.0/HuiDe1.0 (tymczasowo nieudostępnione)
    * @param  [in] idBus Miejsce podłączenia, 1-port końcowy 1; 2-port końcowy 2...8-port końcowy 8 (tymczasowo nieudostępnione)
    * @return  Kod błędu
    */
    int AxleSensorConfig(int idCompany, int idDevice, int idSoftware, int idBus);

Pobranie konfiguracji czujnika końcowego
++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera konfigurację czujnika końcowego
    * @param  [out] idCompany Producent, 18-JUNKONG; 25-HUIDE
    * @param  [out] idDevice Typ, 0-JUNKONG/RYR6T.V1.0
    * @return  Kod błędu
    */
    int AxleSensorConfigGet(ref int idCompany, ref int idDevice);

Aktywacja czujnika końcowego
++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Aktywuje czujnik końcowy
    * @param  [in] actFlag 0-reset; 1-aktywacja
    * @return  Kod błędu
    */
    int AxleSensorActivate(int actFlag);

Zapis do rejestru czujnika końcowego
++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Zapis do rejestru czujnika końcowego
    * @param  [in] devAddr  Numer adresu urządzenia 0-255
    * @param  [in] regHAddr Wysoka 8 bitów adresu rejestru
    * @param  [in] regLAddr Niska 8 bitów adresu rejestru
    * @param  [in] regNum  Liczba rejestrów 0-255
    * @param  [in] data1 Wartość 1 zapisywana do rejestru
    * @param  [in] data2 Wartość 2 zapisywana do rejestru
    * @param  [in] isNoBlock 0-blokujące; 1-nieblokujące
    * @return  Kod błędu
    */
     int AxleSensorRegWrite(int devAddr, int regHAddr, int regLAddr, int regNum, int data1, int data2, int isNoBlock);

Przykład kodu czujnika końcowego
++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button2_Click_1(object sender, EventArgs e)
    {
        robot.AxleSensorConfig(18, 0, 0, 1);
        int company = -1;
        int type = -1;
        robot.AxleSensorConfigGet(ref company, ref type);
        Console.WriteLine("company is " + company + ", type is " + type);

        int rtn = robot.AxleSensorActivate(1);
        Console.WriteLine("AxleSensorActivate rtn is " + rtn);

        Thread.Sleep(1000);

        rtn = robot.AxleSensorRegWrite(1, 4, 6, 1, 0, 0, 0);
        Console.WriteLine("AxleSensorRegWrite rtn is " + rtn);   
    }

Pobranie protokołu urządzenia peryferyjnego robota
++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /** 
    * @brief Pobiera protokół urządzenia peryferyjnego robota
    * @param [out] protocol Numer protokołu urządzenia peryferyjnego robota 4096-karta sterująca osią rozszerzoną; 4097-ModbusSlave; 4098-ModbusMaster
    * @return Kod błędu 
    */
    int GetExDevProtocol(ref int protocol);

Ustawienie protokołu urządzenia peryferyjnego robota
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /** 
    * @brief Ustawia protokół urządzenia peryferyjnego robota
    * @param [in] protocol Numer protokołu urządzenia peryferyjnego robota 4096-karta sterująca osią rozszerzoną; 4097-ModbusSlave; 4098-ModbusMaster
    * @return Kod błędu 
    */
    int SetExDevProtocol(int protocol);

Przykładowy program ustawiania protokołu urządzenia peryferyjnego robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnSetProto_Click(object sender, EventArgs e)
    {
      int protocol = 4096;
      int rtn = robot.SetExDevProtocol(protocol);
      Console.WriteLine("SetExDevProtocol rtn " + rtn);
      rtn = robot.GetExDevProtocol(ref protocol);
      Console.WriteLine("GetExDevProtocol rtn " + rtn + " protocol is: " + protocol);
    }

Pobranie parametrów komunikacji końcowej
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Pobiera parametry komunikacji końcowej
    * @param param Parametry komunikacji końcowej
    * @return  Kod błędu
    */
    int GetAxleCommunicationParam(ref AxleComParam getParam);

Ustawienie parametrów komunikacji końcowej
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia parametry komunikacji końcowej
    * @param param  Parametry komunikacji końcowej
    * @return  Kod błędu
    */
    int SetAxleCommunicationParam(AxleComParam param);

Ustawienie typu przesyłania plików końcowych
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia typ przesyłania plików końcowych
    * @param type 1-plik aktualizacji MCU; 2-plik LUA
    * @return  Kod błędu
    */
    int SetAxleFileType(int type);

Ustawienie włączenia wykonania LUA końcowego
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia włączenie wykonania LUA końcowego
    * @param enable 0-nie włączaj; 1-włączaj
    * @return  Kod błędu
    */
    int SetAxleLuaEnable(int enable);

Przywracanie błędu wyjątkowego pliku LUA końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Przywracanie błędu wyjątkowego pliku LUA końcowego
    * @param status 0-nie przywracaj; 1-przywracaj
    * @return  Kod błędu
    */
    int SetRecoverAxleLuaErr(int status);

Pobranie stanu włączenia wykonania LUA końcowego
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Pobiera stan włączenia wykonania LUA końcowego
    * @param [out] status 0-nie włączone; 1-włączone
    * @return  Kod błędu
    */
    int GetAxleLuaEnableStatus(ref int status);

Ustawianie włączonych typów urządzeń końcówki dla LUA
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia włączone typy urządzeń końcówki dla LUA
    * @param [in] forceSensorEnable Stan włączenia czujnika siły, 0-wyłączony; 1-włączony
    * @param [in] gripperEnable Stan włączenia chwytaka, 0-wyłączony; 1-włączony
    * @param [in] IOEnable Stan włączenia urządzenia IO, 0-wyłączony; 1-włączony
    * @param [in] dexhandEnable Stan włączenia dłoni, 0-wyłączony; 1-włączony
    * @return  Kod błędu
    */
    public int SetAxleLuaEnableDeviceType(int forceSensorEnable, int gripperEnable, int IOEnable, int dexhandEnable)

Pobieranie włączonych typów urządzeń końcówki dla LUA
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Pobiera włączone typy urządzeń końcówki dla LUA
    * @param [out] forceSensorEnable Stan włączenia czujnika siły, 0-wyłączony; 1-włączony
    * @param [out] gripperEnable Stan włączenia chwytaka, 0-wyłączony; 1-włączony
    * @param [out] IOEnable Stan włączenia urządzenia IO, 0-wyłączony; 1-włączony
    * @param [out] dexhandEnable Stan włączenia dłoni, 0-wyłączony; 1-włączony
    * @return  Kod błędu
    */
    public int GetAxleLuaEnableDeviceType(ref int forceSensorEnable, ref int gripperEnable, ref int IOEnable, ref int dexhandEnable)

Pobieranie aktualnie skonfigurowanych urządzeń końcówki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Pobiera aktualnie skonfigurowane urządzenia końcówki
    * @param [out] forceSensorEnable Numer włączonego urządzenia czujnika siły, 0-wyłączony; 1-włączony
    * @param [out] gripperEnable Numer włączonego urządzenia chwytaka, 0-wyłączony; 1-włączony
    * @param [out] IODeviceEnable Numer włączonego urządzenia IO, 0-wyłączony; 1-włączony
    * @param [out] decHandEnable Numer włączonego urządzenia dłoni, 0-wyłączony; 1-włączony
    * @return  Kod błędu
    */
    public int GetAxleLuaEnableDevice(ref int[] forceSensorEnable, ref int[] gripperEnable, ref int[] IODeviceEnable, ref int[] decHandEnable)

Ustawianie włączonych funkcji sterowania ruchem chwytaka
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia włączone funkcje sterowania ruchem chwytaka
    * @param [in] id Numer urządzenia chwytaka
    * @param [in] func func[0]-włączenie chwytaka; func[1]-inicjalizacja chwytaka; func[2]-ustawienie pozycji; func[3]-ustawienie prędkości; func[4]-ustawienie momentu obrotowego; func[6]-odczyt stanu chwytaka;
        func[7]-odczyt stanu inicjalizacji; func[8]-odczyt kodu błędu; func[9]-odczyt pozycji; func[10]-odczyt prędkości; func[11]-odczyt momentu obrotowego; func[12]-ustawienie liczby obrotów dla chwytaka obrotowego;
        func[13]-ustawienie prędkości obrotowej dla chwytaka obrotowego; func[14]-ustawienie momentu obrotowego dla chwytaka obrotowego; func[15]-odczyt stanu chwytaka obrotowego; func[16]-odczyt stanu inicjalizacji chwytaka obrotowego;
        func[17]-odczyt liczby obrotów chwytaka obrotowego; func[18]-odczyt prędkości chwytaka obrotowego; func[19]-odczyt momentu obrotowego chwytaka obrotowego; func[20]-ustawienie ruchu synchronicznego wieloosiowego; func[21]-komenda kasowania błędów;
        func[22]-stan pracy pojedynczej osi; func[23]-stan pracy wszystkich osi;
    * @return  Kod błędu
    */
    public int SetAxleLuaGripperFunc(int id, int[] func)

Pobieranie włączonych funkcji sterowania ruchem chwytaka
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Pobiera włączone funkcje sterowania ruchem chwytaka
    * @param [in] id Numer urządzenia chwytaka
    * @param [out] func func[0]-włączenie chwytaka; func[1]-inicjalizacja chwytaka; func[2]-ustawienie pozycji; func[3]-ustawienie prędkości; func[4]-ustawienie momentu obrotowego; func[6]-odczyt stanu chwytaka;
        func[7]-odczyt stanu inicjalizacji; func[8]-odczyt kodu błędu; func[9]-odczyt pozycji; func[10]-odczyt prędkości; func[11]-odczyt momentu obrotowego; func[12]-ustawienie liczby obrotów dla chwytaka obrotowego;
        func[13]-ustawienie prędkości obrotowej dla chwytaka obrotowego; func[14]-ustawienie momentu obrotowego dla chwytaka obrotowego; func[15]-odczyt stanu chwytaka obrotowego; func[16]-odczyt stanu inicjalizacji chwytaka obrotowego;
        func[17]-odczyt liczby obrotów chwytaka obrotowego; func[18]-odczyt prędkości chwytaka obrotowego; func[19]-odczyt momentu obrotowego chwytaka obrotowego; func[20]-ustawienie ruchu synchronicznego wieloosiowego; func[21]-komenda kasowania błędów;
        func[22]-stan pracy pojedynczej osi; func[23]-stan pracy wszystkich osi;
    * @return  Kod błędu
    */
    public int GetAxleLuaGripperFunc(int id, ref int[] func)

Zapis pliku stacji podrzędnej Ethercat robota
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Zapis pliku stacji podrzędnej Ethercat robota
    * @param [in] type Typ pliku stacji podrzędnej, 1-aktualizacja pliku stacji podrzędnej; 2-aktualizacja pliku konfiguracyjnego stacji podrzędnej
    * @param [in] slaveID Numer stacji podrzędnej
    * @param [in] fileName Nazwa przesyłanego pliku
    * @return  Kod błędu
    */
    int SlaveFileWrite(int type, int slaveID, string fileName);

Przesłanie pliku protokołu otwartego LUA końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Przesłanie pliku protokołu otwartego LUA końcowego
    * @param filePath Ścieżka lokalnego pliku lua ".../AXLE_LUA_End_DaHuan.lua"
    * @return Kod błędu 
    */
    int AxleLuaUpload(string filePath);

Wejście stacji podrzędnej Ethercat robota w tryb boot
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Wejście stacji podrzędnej Ethercat robota w tryb boot
    * @return  Kod błędu
    */
    int SetSysServoBootMode();

Przykład kodu operacji na pliku LUA końcowego robota
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button41_Click(object sender, EventArgs e)
    {
        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
        robot.AxleLuaUpload("D://zUP/AXLE_LUA_End_JunDuo_V0.4_20260602.lua");

        AxleComParam param = new AxleComParam(7, 8, 1, 0, 5, 3, 1);
        robot.SetAxleCommunicationParam(param);

        AxleComParam getParam = new AxleComParam();
        robot.GetAxleCommunicationParam(ref getParam);
        Console.WriteLine("GetAxleCommunicationParam param is {0} {1} {2} {3} {4} {5} {6}",
            getParam.baudRate, getParam.dataBit, getParam.stopBit, getParam.verify,
            getParam.timeout, getParam.timeoutTimes, getParam.period);

        robot.SetAxleLuaEnable(1);
        int luaEnableStatus = 0;
        robot.GetAxleLuaEnableStatus(ref luaEnableStatus);
        robot.SetAxleLuaEnableDeviceType(0, 1, 0, 0);

        int forceEnable = 0;
        int gripperEnable = 0;
        int ioEnable = 0;
        int dexhandEnable = 0;
        robot.GetAxleLuaEnableDeviceType(ref forceEnable, ref gripperEnable, ref ioEnable, ref dexhandEnable);
        Console.WriteLine("GetAxleLuaEnableDeviceType param is {0} {1} {2}", forceEnable, gripperEnable, ioEnable);

        int[] func = { 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 };
        robot.SetAxleLuaGripperFunc(1, func);

        int[] getFunc = new int[32];
        robot.GetAxleLuaGripperFunc(1, ref getFunc);
        int[] getforceEnable = new int[16];
        int[] getgripperEnable = new int[16];
        int[] getioEnable = new int[16];
        int[] dexhandEnable1 = new int[16];
        robot.GetAxleLuaEnableDevice(ref getforceEnable, ref getgripperEnable, ref getioEnable,ref dexhandEnable1);
        Console.WriteLine("\ngetforceEnable status : ");
        foreach (int i in getforceEnable)
        {
            Console.Write(i + ",");
        }
        Console.WriteLine("\ngetgripperEnable status : ");
        foreach (int i in getgripperEnable)
        {
            Console.Write(i + ",");
        }
        Console.WriteLine("\ngetioEnable status : ");
        foreach (int i in getioEnable)
        {
            Console.Write(i + ",");
        }
        Console.WriteLine();
        robot.ActGripper(1, 0);
        Thread.Sleep(3000);
        robot.ActGripper(1, 1);
        Thread.Sleep(4000);
        robot.MoveGripper(1, 50, 10, 100, 50000, 0, 0, 0, 0, 0);
        int pos = 0;
        while (true)
        {
            robot.GetRobotRealTimeState(ref pkg);
            Console.WriteLine("gripper pos is " + pkg.gripper_position);
            Thread.Sleep(100);
        }
    } 

Pobranie stanu przycisków SmartTool
++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Pobiera stan przycisków SmartTool
    * @param [out] state Stan przycisków uchwytu SmartTool; (bit0:0-komunikacja normalna; 1-utrata komunikacji; bit1-cofnij operację; bit2-wyczyść program;
        bit3-przycisk A; bit4-przycisk B; bit5-przycisk C; bit6-przycisk D; bit7-przycisk E; bit8-przycisk I/O; bit9-ręczny/automatyczny; bit10-start)
    * @return Kod błędu
    */
    int GetSmarttoolBtnState(ref int state);

Przykład kodu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:

    private void button11_Click(object sender, EventArgs e)
    {

        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
        int state = 0;
        while (true)
        {
            int rtn = robot.GetSmarttoolBtnState(ref state);
            string binaryString = Convert.ToString(state, 2).PadLeft(32, '0');
            Console.WriteLine($"GetSmarttoolBtnState rtn (binary): {binaryString}");
            Thread.Sleep(100);
        }

    }

Przesłanie pliku Lua protokołu otwartego
++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Przesłanie pliku Lua protokołu otwartego
    * @param  filePath Ścieżka lokalnego pliku lua protokołu otwartego
    * @return Kod błędu
    */
    public int OpenLuaUpload(string filePath)


Pobranie parametrów karty stacji podrzędnej
+++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera parametry karty stacji podrzędnej
    * @param  type  0-Ethercat, 1-CClink, 3-Ethercat, 4-EIP
    * @param  version  Wersja protokołu
    * @param  connState  0-odłączony 1-połączony
    * @return  Kod błędu
    */
    public int GetFieldBusConfig(int[] type, int[] version, int[] connState)

Zapis DO stacji podrzędnej
++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Zapis DO stacji podrzędnej
    * @param   DOIndex  Numer DO
    * @param   wirteNum  Liczba zapisywanych
    * @param   status Wartości do zapisania, maksymalnie 8
    * @return  Kod błędu
    */
    public int FieldBusSlaveWriteDO(int DOIndex, int wirteNum, int[] status)

Zapis AO stacji podrzędnej
++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Zapis AO stacji podrzędnej
    * @param [in] AOIndex Numer AO
    * @param [in] wirteNum Liczba zapisywanych
    * @param [in] status Tablica wartości do zapisania (maksymalnie 8), AO0~AO15 są typu całkowitego, AO16~AO31 są typu zmiennoprzecinkowego
    * @return Kod błędu
    */
    public int FieldBusSlaveWriteAO(int AOIndex, int wirteNum, double[] status)

Odczyt DI stacji podrzędnej
+++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Odczyt DI stacji podrzędnej
    * @param  DOIndex  Numer DI
    * @param  readNum  Liczba odczytywanych
    * @param  status Odczytywane wartości, maksymalnie 8
    * @return  Kod błędu
    */
    public int FieldBusSlaveReadDI(int DOIndex, int readNum, int[] status)

Odczyt AI stacji podrzędnej
+++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Odczyt AI stacji podrzędnej
    * @param  AIIndex  Numer AI
    * @param  readNum  Liczba odczytywanych
    * @param  status Odczytywane wartości, maksymalnie 8
    * @return  Kod błędu
    */
    public int FieldBusSlaveReadAI(int AIIndex, int readNum, double[] status)

Oczekiwanie na wejście rozszerzone DI
+++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Oczekiwanie na wejście rozszerzone DI
    * @param  DIIndex Numer DI
    * @param  status 0-poziom niski; 1-poziom wysoki
    * @param  waitMs Maksymalny czas oczekiwania (ms)
    * @return Kod błędu
    */
    public int FieldBusSlaveWaitDI(int DIIndex, int status, int waitMs)

Oczekiwanie na wejście rozszerzone AI
+++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Oczekiwanie na wejście rozszerzone AI
    * @param  AIIndex Numer AI
    * @param  waitType 0-większe niż; 1-mniejsze niż
    * @param  value Wartość AI
    * @param  waitMs Maksymalny czas oczekiwania (ms)
    * @return Kod błędu
    */
    public int FieldBusSlaveWaitAI(int AIIndex, int waitType, double value, int waitMs)

Przykład kodu instrukcji interfejsu trybu stacji podrzędnej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button101_Click(object sender, EventArgs e)
    {
        int rtn = 0;
    
        int type = 0, version = 0, connState = 0;
        int[] ctrl = new int[8];
        double[] ctrlAO = new double[8];
        int[] DI = new int[8];
        double[] AI = new double[8];
        if (rtn != 0)
        {
            return;
        }
        // Upload and load open protocol file
        robot.OpenLuaUpload("E://temp /CtrlDev_field.lua");
        Thread.Sleep(2000);
        robot.SetCtrlOpenLUAName(3, "CtrlDev_field.lua");
        robot.UnloadCtrlOpenLUA(3);
        robot.LoadCtrlOpenLUA(3);
        Thread.Sleep(8000);
    
        // Get protocol type, software version, and connection status with PLC
        robot.GetFieldBusConfig(ref type, ref version, ref connState);
        Console.WriteLine($"type is {type}, version is {version}, connState is {connState}");
    
        // Write DO0 = 1, DO1 = 0, DO2 = 1
        ctrl[0] = 1;
        ctrl[1] = 0;
        ctrl[2] = 1;
        robot.FieldBusSlaveWriteDO(0, 3, ctrl);
    
        // Write AO2 = 0x1000
        ctrlAO[0] = 0x1000;
        robot.FieldBusSlaveWriteAO(2, 1, ctrlAO);

        for (int i = 0; i < 100; i++)
        {
            robot.FieldBusSlaveReadDI(0, 4, ref DI);
            Console.WriteLine($"DI0 is {DI[0]}, DI1 is {DI[1]}, DI2 is {DI[2]}, DI3 is {DI[3]}");
            robot.FieldBusSlaveReadAI(0, 3, ref AI);
            Console.WriteLine($"AI0 is {AI[0]}, AI1 is {AI[1]}, AI2 is {AI[2]}");
            Thread.Sleep(10);
        }
        int ret = robot.FieldBusSlaveWaitDI(0, 1, 100);
        Console.WriteLine($"FieldBusSlaveWaitDI result is {ret}");

        ret = robot.FieldBusSlaveWaitAI(0, 0, 400.00f, 100);
        Console.WriteLine($"FieldBusSlaveWaitAI result is {ret}"); 
    }

Sterowanie macierzową przyssawką
++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Sterowanie macierzową przyssawką
    * @param  slaveID Numer stacji podrzędnej
    * @param  len Długość
    * @param  ctrlValue Wartość sterowania 1-zasysanie z maksymalnym podciśnieniem 2-zasysanie z ustawionym podciśnieniem 3-zatrzymanie zasysania
    * @return Kod błędu
    */
    public int SetSuckerCtrl(int slaveID, int len, int[] ctrlValue)

Pobranie stanu macierzowej przyssawki
+++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Pobranie stanu macierzowej przyssawki
    * @param  slaveID Numer stacji podrzędnej
    * @param  state Stan przyssania 0-uwolnienie przedmiotu 1-wykryto pomyślne przyssanie przedmiotu 2-brak przyssania przedmiotu 3-oderwanie przedmiotu
    * @param  pressValue Bieżące podciśnienie, jednostka kPa
    * @param  error Bieżący kod błędu przyssawki
    * @return Kod błędu
    */
    public int GetSuckerState(int slaveID, int[] state, int[] pressValue, int[] error)

Oczekiwanie na stan przyssawki
++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Oczekiwanie na stan przyssawki
    * @param  slaveID Numer stacji podrzędnej
    * @param  state Stan przyssania 0-uwolnienie przedmiotu 1-wykryto pomyślne przyssanie przedmiotu 2-brak przyssania przedmiotu 3-oderwanie przedmiotu
    * @param  ms Maksymalny czas oczekiwania
    * @return Kod błędu
    */
    public int WaitSuckerState(int slaveID, int state, int ms)

Przykład kodu instrukcji sterowania macierzową przyssawką
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void TestSucker(Robot robot)
    {
    
        int[] ctrl = new int[20];
        int state=0;
        int pressValue=0;
        int error=0;
        int rtn;
    
    
        // Upload and load open protocol file
        robot.OpenLuaUpload(@"C:\SDK\CtrlDev_sucker.lua");
        Thread.Sleep(2000);
        robot.UnloadCtrlOpenLUA(1);
        robot.LoadCtrlOpenLUA(1);
        Thread.Sleep(1000);
    
        // Control sucker in broadcast mode with maximum adsorption capacity
        ctrl[0] = 1;
        robot.SetSuckerCtrl(0, 1, ctrl);
    
        // Monitor states of sucker 1 and sucker 12 in a loop
        for (int i = 0; i < 100; i++)
        {
            robot.GetSuckerState(1, ref state, ref pressValue, ref error);
            Console.WriteLine($"sucker1 state is {state}, pressValue is {pressValue}, error num is {error}");
            robot.GetSuckerState(12, ref state, ref pressValue, ref error);
            Console.WriteLine($"sucker12 state is {state}, pressValue is {pressValue}, error num is {error}");
            Thread.Sleep(100);
        }
        // Wait for sucker 1 to reach adsorbed state, timeout 100ms
        int ret = robot.WaitSuckerState(1, 1, 100);
        Console.WriteLine($"WaitSuckerState result is {ret}");
    
        // Unicast mode to turn off sucker 1 and 12
        ctrl[0] = 3;
        robot.SetSuckerCtrl(1, 1, ctrl);
        robot.SetSuckerCtrl(12, 1, ctrl);
    
        robot.CloseRPC();
    }

Funkcja włączania/wyłączania urządzenia peryferyjnego lasera
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Funkcja włączania/wyłączania urządzenia peryferyjnego lasera
     * @param [in] OnOff 0-wyłącz 1-włącz
     * @param [in] weldId ID spoiny, domyślnie 0
     * @return Kod błędu
     */
    public int LaserTrackingLaserOnOff(int OnOff, int weldId)
    
Funkcja rozpoczęcia/zakończenia śledzenia laserowego
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:

    
    /**
     * @brief Funkcja rozpoczęcia/zakończenia śledzenia laserowego
     * @param [in] OnOff 0-zakończ 1-rozpocznij
     * @param [in] coordId Numer układu współrzędnych narzędzia urządzenia peryferyjnego lasera
     * @return Kod błędu
     */
    public int LaserTrackingTrackOnOff(int OnOff, int coordId)

Pozycjonowanie laserowe - stały kierunek
++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Pozycjonowanie laserowe - stały kierunek
     * @param [in] direction 0-x+ 1-x- 2-y+ 3-y- 4-z+ 5-z-
     * @param [in] vel Prędkość jednostka%
     * @param [in] distance Maksymalna odległość pozycjonowania jednostka mm
     * @param [in] timeout Czas przekroczenia limitu pozycjonowania jednostka ms
     * @param [in] posSensorNum Numer narzędzia skalibrowanego dla lasera
     * @return Kod błędu
     */
    public int LaserTrackingSearchStart_xyz(int direction, int vel, int distance, int timeout, int posSensorNum)
    
Pozycjonowanie laserowe - dowolny kierunek
++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Pozycjonowanie laserowe - dowolny kierunek
     * @param [in] directionPoint Współrzędne xyz punktu wejściowego pozycjonowania
     * @param [in] vel Prędkość jednostka%
     * @param [in] distance Maksymalna odległość pozycjonowania jednostka mm
     * @param [in] timeout Czas przekroczenia limitu pozycjonowania jednostka ms
     * @param [in] posSensorNum Numer narzędzia skalibrowanego dla lasera
     * @return Kod błędu
     */
    public int LaserTrackingSearchStart_point(DescTran directionPoint, int vel, int distance, int timeout, int posSensorNum)
   
Zakończenie pozycjonowania laserowego
+++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
    * @brief  Zakończenie pozycjonowania laserowego
    * @return Kod błędu
    */
    public int LaserTrackingSearchStop()

Konfiguracja adresu IP lasera
+++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Konfiguracja adresu IP lasera
     * @param [in] ip Adres IP urządzenia peryferyjnego lasera
     * @param [in] port Numer portu urządzenia peryferyjnego lasera
     * @return Kod błędu
     */
    public int LaserTrackingSensorConfig(string ip, int port)

Konfiguracja okresu próbkowania urządzenia peryferyjnego lasera
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Konfiguracja okresu próbkowania urządzenia peryferyjnego lasera
     * @param [in] period Okres próbkowania urządzenia peryferyjnego lasera jednostka ms
     * @return Kod błędu
     */
    public int LaserTrackingSensorSamplePeriod(int period)

Ładowanie sterownika urządzenia peryferyjnego lasera
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Ładowanie sterownika urządzenia peryferyjnego lasera
     * @param [in] type Typ protokołu sterownika urządzenia peryferyjnego lasera 101-Ruiniu 102-Chuangxiang 103-Quanshi 104-Tongzhou 105-Aotai
     * @return Kod błędu
     */
    public int LoadPosSensorDriver(int type)

Rozładowanie sterownika urządzenia peryferyjnego lasera
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Rozładowanie sterownika urządzenia peryferyjnego lasera
     * @return Kod błędu
     */
    public int UnLoadPosSensorDriver()

Rejestracja trajektorii spoiny laserowej
++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Rejestracja trajektorii spoiny laserowej
     * @param [in] status 0-zatrzymaj rejestrację 1-śledzenie w czasie rzeczywistym  2-rozpocznij rejestrację
     * @param [in] delayTime Czas opóźnienia jednostka ms
     * @return Kod błędu
     */
    public int LaserSensorRecord1(int status, int delayTime)

Odtworzenie trajektorii spoiny laserowej
++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Odtworzenie trajektorii spoiny laserowej
     * @param [in] delayTime Czas opóźnienia jednostka ms
     * @param [in] speed Prędkość jednostka%
     * @return Kod błędu
     */
    public int LaserSensorReplay(int delayTime, double speed)

Odtworzenie śledzenia laserowego
++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Odtworzenie śledzenia laserowego
     * @return Kod błędu
     */
    public int MoveLTR()

Rejestracja i odtworzenie trajektorii spoiny laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Rejestracja i odtworzenie trajektorii spoiny laserowej
    * @param [in] delayMode Tryb 0-czas opóźnienia 1-odległość opóźnienia
    * @param [in] delayTime Czas opóźnienia jednostka ms
    * @param [in] delayDisExAxisNum Numer osi rozszerzonej
    * @param [in] delayDis Odległość opóźnienia jednostka mm
    * @param [in] sensitivePara Współczynnik czułości kompensacji
    * @param [in] trackMode Typ śledzenia punktowego. 0-ruch asynchroniczny osi rozszerzonej; 1-robot
    * @param [in] triggerMode Sposób wyzwalania śledzenia punktowego. 0-czas śledzenia; 1-I/O
    * @param [in] runTime Czas śledzenia punktowego robota (s)
    * @param [in] speed Prędkość jednostka%
    * @return Kod błędu
    */
    public int LaserSensorRecordandReplay(int delayMode, int delayTime, int delayDisExAxisNum,double delayDis, double sensitivePara, int trackMode, int triggerMode,double runTime, double speed)
    
Przejście do punktu początkowego zarejestrowanej spoiny
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Przejście do punktu początkowego zarejestrowanej spoiny
     * @param [in] moveType 0-PTP 1-LIN
     * @param [in] ovl Prędkość jednostka%
     * @return Kod błędu
     */
    public int MoveToLaserRecordStart(int moveType, double ovl)

Przejście do punktu końcowego zarejestrowanej spoiny
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Przejście do punktu końcowego zarejestrowanej spoiny
     * @param [in] moveType 0-PTP 1-LIN
     * @param [in] ovl Prędkość jednostka%
     * @return Kod błędu
     */
    public int MoveToLaserRecordEnd(int moveType, double ovl)

Przejście do punktu pozycjonowania czujnika laserowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Przejście do punktu pozycjonowania czujnika laserowego
     * @param [in] moveFlag Typ ruchu: 0-PTP; 1-LIN
     * @param [in] ovl Współczynnik skalowania prędkości, 0-100
     * @param [in] dataFlag Wybór danych bufora spoiny: 0-wykonaj dane planowania; 1-wykonaj dane rejestracji
     * @param [in] plateType Typ materiału: 0-blacha falista; 1-blacha trapezowa; 2-blacha ogrodzeniowa; 3-beczka; 4-stal pancerna falista
     * @param [in] trackOffectType Typ przesunięcia czujnika laserowego: 0-brak przesunięcia; 1-przesunięcie w podstawowym układzie współrzędnych; 2-przesunięcie w układzie współrzędnych narzędzia; 3-przesunięcie surowych danych czujnika laserowego
     * @param [in] offset Wartość przesunięcia
     * @return Kod błędu
     */
    public int MoveToLaserSeamPos(int moveFlag, double ovl, int dataFlag, int plateType, int trackOffectType, DescPose offset)
    
Pobranie informacji o współrzędnych punktu pozycjonowania czujnika laserowego
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Pobranie informacji o współrzędnych punktu pozycjonowania czujnika laserowego
     * @param [in] trackOffectType Typ przesunięcia czujnika laserowego: 0-brak przesunięcia; 1-przesunięcie w podstawowym układzie współrzędnych; 2-przesunięcie w układzie współrzędnych narzędzia; 3-przesunięcie surowych danych czujnika laserowego
     * @param [in] offset Wartość przesunięcia
     * @param [out] jPos Pozycja stawów [°]
     * @param [out] descPos Pozycja kartezjańska [mm]
     * @param [out] tool Układ współrzędnych narzędzia
     * @param [out] user Układ współrzędnych przedmiotu
     * @param [out] exaxis Pozycja osi rozszerzonej [mm]
     * @return Kod błędu
     */
    public int GetLaserSeamPos(int trackOffectType, DescPose offset, ref JointPos jPos, ref DescPose descPos, ref int tool, ref int user, ref ExaxisPos exaxis)

Przykład kodu konfiguracji i debugowania parametrów czujnika urządzenia peryferyjnego lasera
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    void testLaserConfig()
    {
        int[] ctrl = new int[20];
        int state;
        int pressValue;
        int error;
        robot.LaserTrackingSensorConfig("192.168.58.20", 5020);
        robot.LaserTrackingSensorSamplePeriod(20);
        robot.LoadPosSensorDriver(101);
        robot.LaserTrackingLaserOnOff(0, 0);
        System.Threading.Thread.Sleep(3000);
        robot.LaserTrackingLaserOnOff(1, 0);
    }

Przykład kodu skanowania trajektorii laserowej i odtwarzania trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    void testLaserRecordAndReplay()
    { 
        int[] ctrl = new int[20];
        int state;
        int pressValue;
        int error;
        robot.OpenLuaUpload("D://zUP/CtrlDev_laser_ruiniu-0117.lua");
        System.Threading.Thread.Sleep(2000);
        robot.SetCtrlOpenLUAName(0, "CtrlDev_laser_ruiniu-0117.lua");
        robot.UnloadCtrlOpenLUA(0);
        robot.LoadCtrlOpenLUA(0);
        System.Threading.Thread.Sleep(8000);
        for (int i=0;i<10;++i)
        {
            JointPos startjointPos = new JointPos(56.205, -117.951, 141.872, -118.149, -94.217, -122.176);
            DescPose startdescPose = new DescPose(-97.552, -282.855, 26.675, 174.182, -1.338, -91.707);
            ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
            DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

            robot.MoveL(startjointPos, startdescPose, 1, 0, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 0);
            robot.LaserSensorRecord1(2, 10);

            JointPos endjointPos = new JointPos(68.809, -87.100, 121.120, -127.233, -95.038, -109.555);
            DescPose enddescPose = new DescPose(-103.555, -464.234, 13.076, 174.179, -1.344, -91.709);
            robot.MoveL(endjointPos, enddescPose, 1, 0, 50, 100, 100, -1, exaxisPos, 0, 0, offdese, 0);

            robot.LaserSensorRecord1(0, 10);
            robot.MoveToLaserRecordStart(1, 30);
            robot.LaserSensorReplay(10, 100);
            robot.MoveLTR();
            robot.LaserSensorRecord1(0, 10);
            Console.WriteLine($"Number of completions : {i+1} ");
        }
                
    }

Przykład kodu pozycjonowania laserowego i śledzenia w czasie rzeczywistym
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    public static void testLasertrack()
    {
        int[] ctrl = new int[20];
        int state;
        int pressValue;
        int error;
        robot.OpenLuaUpload("D://zUP/CtrlDev_laser_ruiniu-0117.lua");
        System.Threading.Thread.Sleep(2000);
        robot.SetCtrlOpenLUAName(0, "CtrlDev_laser_ruiniu-0117.lua");
        robot.UnloadCtrlOpenLUA(0);
        robot.LoadCtrlOpenLUA(0);
        System.Threading.Thread.Sleep(8000);
        for (int i = 0; i < 10; ++i)
        {
            JointPos startjointPos = new JointPos(56.205, -117.951, 141.872, -118.149, -94.217, -122.176);
            DescPose startdescPose = new DescPose(-97.552, -282.855, 26.675, 174.182, -1.338, -91.707);
            ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
            DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);
            DescTran directionPoint = new DescTran();

            robot.MoveL(startjointPos, startdescPose, 1, 0, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 0);
            robot.LaserTrackingSearchStart_xyz(3, 100, 300, 1000, 3);
            robot.LaserTrackingSearchStop();
            robot.MoveToLaserSeamPos(1, 30, 0, 0, 0, offdese);

            robot.LaserTrackingTrackOnOff(1, 3);

            JointPos endjointPos = new JointPos(68.809, -87.100, 121.120, -127.233, -95.038, -109.555);
            DescPose enddescPose = new DescPose(-103.555, -464.234, 13.076, 174.179, -1.344, -91.709);
            robot.MoveL(endjointPos, enddescPose, 1, 0, 20, 100, 100, -1, exaxisPos, 0, 0, offdese, 0);
            robot.LaserTrackingTrackOnOff(0, 3);
            Console.WriteLine($"Number of completions : {i + 1} ");
        }
    }

Przykład kodu śledzenia laserowego z osią rozszerzoną i robotem synchronicznie
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    public void TestLaserTrackAndExitAxis()
    {   
        ExaxisPos startexaxisPos = new ExaxisPos(0, 0, 0, 0);
        ExaxisPos seamexaxisPos = new ExaxisPos(-10, 0, 0, 0);
        ExaxisPos endexaxisPos = new ExaxisPos(-30, 0, 0, 0);      
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);     
        JointPos startjointPos = new JointPos(58.337, -119.628, 146.037, -116.358, -92.224, -117.654);
        DescPose startdescPose = new DescPose(-53.375, -255.363, 0.919, 178.054, 1.077, -94.026);
        for (int i=0;i<10;++i)
        {
            robot.ExtAxisSyncMoveJ(startjointPos, startdescPose, 1, 0, 100, 100, 100, startexaxisPos, -1, 0, offdese);
            Console.WriteLine("11111");
            int ret = robot.LaserTrackingSearchStart_xyz(3, 100, 300, 1000, 2);
            robot.LaserTrackingSearchStop();
            Console.WriteLine("2222");
            int tool = 0;
            int user = 0;
            JointPos seamjointPos = new JointPos();
            DescPose seamdescPose = new DescPose();
            robot.GetLaserSeamPos(0, offdese, ref seamjointPos, ref seamdescPose, ref tool, ref user, ref startexaxisPos);
            Console.WriteLine($"{seamjointPos.jPos[0]}, {seamjointPos.jPos[1]}, {seamjointPos.jPos[2]}, " +
                            $"{seamjointPos.jPos[3]}, {seamjointPos.jPos[4]}, {seamjointPos.jPos[5]}, " +
                            $"{seamdescPose.tran.x}, {seamdescPose.tran.y}, {seamdescPose.tran.z}, " +
                            $"{seamdescPose.rpy.rx}, {seamdescPose.rpy.ry}, {seamdescPose.rpy.rz}");
            if (ret == 0)
            {
                robot.ExtAxisSyncMoveJ(seamjointPos, seamdescPose, 1, 0, 100, 100, 100, seamexaxisPos, -1, 0, offdese);
                Console.WriteLine("3333");
                robot.LaserTrackingTrackOnOff(1, 2);
                JointPos endjointPos = new JointPos(70.580, -90.918, 126.593, -125.154, -92.162, -105.403);
                DescPose enddescPose = new DescPose(-53.375, -419.020, 0.920, 178.054, 1.076, -94.026);
                robot.ExtAxisSyncMoveL(endjointPos, enddescPose, 1, 0, 20, 100, 100, -1, endexaxisPos, 0, offdese);
                robot.LaserTrackingTrackOnOff(0, 2);
            }
            Console.WriteLine($"Number of completions : {i + 1} ");
        }     
    }

Włączanie/wyłączanie funkcji transmisji transparentnej końcowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Włączanie ogólnej funkcji transmisji transparentnej końcowej
    * @param [in] Włączenie, 0-wyłączone, 1-włączone
    * @return Kod błędu
    */
    public int SetAxleGenComEnable(int mode)

Wysyłanie i odbieranie danych nieokresowych funkcji transmisji transparentnej końcowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Wysyłanie danych nieokresowych przez końcówkę i oczekiwanie na odpowiedź
    * @param [in] len_snd, długość wysyłanych danych
    * @param [in] sndBuff[], dane do wysłania
    * @param [in] len_rcv, wybór długości odbieranych danych
    * @param [out] rcvBuff[], odebrane dane odpowiedzi
    * @return Kod błędu
    */
    public int SndRcvAxleGenComCmdData(int len_snd, int[] sndBuff, int len_rcv, ref int[] rcvdata)

Przykład kodu komunikacji danych nieokresowych dla głowicy do moksybustii Beykon w oparciu o funkcję transmisji transparentnej końcowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    void testAxleGenCom()
    {
        int[] led_on = new int[6] { 0xAB, 0xBA, 0x12, 0x01, 0x01, 0x79 };
        int[] led_off = new int[6] { 0xAB, 0xBA, 0x12, 0x01, 0x00, 0x78 };
        int[] version = new int[5]{ 0xAB, 0xBA, 0x11, 0x00, 0x76 };
        int[] state = new int[6] { 0xAB, 0xBA, 0x1B,0x01, 0xAA, 0x2B };
        int[] cycleState = new int[6] { 0xAB, 0xBA, 0x12, 0x01, 0x00, 0x78 };

        int[] rcvdata = new int[16];
        int ret = 0;
        int cnt = 1;

        JointPos p1Joint = new JointPos(88.708, -86.178, 140.989, -141.825, -89.162, -49.879);
        DescPose p1Desc = new DescPose(188.007, -377.850, 260.207, 178.715, 2.823, -131.466);

        JointPos p2Joint = new JointPos(112.131, -75.554, 126.989, -139.027, -88.044, -26.477);
        DescPose p2Desc = new DescPose(368.003, -377.848, 260.211, 178.715, 2.823, -131.465);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        //Włączenie funkcji transmisji transparentnej końcowej
        robot.SetAxleGenComEnable(1);
        robot.SetAxleLuaEnable(1);

        while(cnt<=10)
        { 
            //Odczytanie numeru wersji
            ret = robot.SndRcvAxleGenComCmdData(5, version, 10, ref rcvdata);
            Console.WriteLine($" hard version : {rcvdata[4]},hard code:{rcvdata[5]}, soft version:{rcvdata[6]} {rcvdata[7]}, soft code:{rcvdata[8]}");
            if (ret != 0)
            {
                break;
            }
            Thread.Sleep(1000);
            //Odczytanie stanu obecności głowicy do moksybustii
            ret = robot.SndRcvAxleGenComCmdData(6, state, 6, ref rcvdata);
            Console.WriteLine($" state : {rcvdata[4]}");
            Thread.Sleep(1000);
            //Włączenie lasera głowicy do moksybustii
            ret = robot.SndRcvAxleGenComCmdData(6, led_on, 6, ref rcvdata);
            Console.WriteLine($"led on rcv data is: {rcvdata[0]},{rcvdata[1]}, {rcvdata[2]}, {rcvdata[3]}, {rcvdata[4]}, {rcvdata[5]}");
            robot.MoveJ(p1Joint, p1Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
            Thread.Sleep(4000);
            //Wyłączenie lasera głowicy do moksybustii
            ret = robot.SndRcvAxleGenComCmdData(6, led_off, 6, ref rcvdata);
            Console.WriteLine($"led off rcv data is: {rcvdata[0]},{rcvdata[1]}, {rcvdata[2]}, {rcvdata[3]}, {rcvdata[4]}, {rcvdata[5]}");
            robot.MoveJ(p2Joint, p2Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
            Thread.Sleep(1000);
            Console.WriteLine($"***********************complate No. {cnt}  SDK test*****************************");
            cnt++;
        }

    }

Pobranie pliku Lua protokołu otwartego
++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Pobranie pliku Lua protokołu otwartego
    * @param [in] fileName Nazwa pliku protokołu otwartego "CtrlDev_XXX.lua"
    * @param [in] savePath Ścieżka zapisu pliku protokołu otwartego
    * @return Kod błędu
    */
    public int OpenLuaDownload(string fileName, string savePath)
    
Usunięcie pliku Lua protokołu otwartego
++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Usunięcie pliku Lua protokołu otwartego
    * @param [in] fileName Nazwa pliku lua protokołu otwartego do usunięcia "CtrlDev_XXX.lua"
    * @return Kod błędu
    */
    public int OpenLuaDelete(string fileName)
        
Usunięcie wszystkich plików Lua protokołu otwartego
++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Usunięcie wszystkich plików Lua protokołu otwartego
    * @return Kod błędu
    */
    public int AllOpenLuaDelete()

Przykład kodu SDK operacji na plikach Lua protokołu otwartego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    public int TestCtrlOpenLuaOperate()
    {
        int rtn;

        // Przesłanie pliku Lua do robota
        rtn = robot.OpenLuaUpload("D://zUP/openlua/CtrlDev_WELDING_A.lua");
        Console.WriteLine($"OpenLuaUpload rtn is {rtn}");
        rtn = robot.OpenLuaUpload("D://zUP/openlua/CtrlDev_SWDPOLISH.lua");
        Console.WriteLine($"OpenLuaUpload rtn is {rtn}");

        // Pobranie pliku Lua z robota
        rtn = robot.OpenLuaDownload("CtrlDev_WELDING_A.lua", "D://zDOWN/");
        Console.WriteLine($"OpenLuaDownload rtn is {rtn}");
        rtn = robot.OpenLuaDownload("CtrlDev_SWDPOLISH.lua", "D://zDOWN/");
        Console.WriteLine($"OpenLuaDownload rtn is {rtn}");

        // Ustawienie nazwy Lua protokołu otwartego sterowania
        rtn = robot.SetCtrlOpenLUAName(0, "CtrlDev_WELDING_A.lua");
        Console.WriteLine($"SetCtrlOpenLUAName rtn is {rtn}");
        rtn = robot.SetCtrlOpenLUAName(1, "CtrlDev_SWDPOLISH.lua");
        Console.WriteLine($"SetCtrlOpenLUAName rtn is {rtn}");

        // Pobranie nazwy Lua protokołu otwartego sterowania
        string[] name = new string[4];
        rtn = robot.GetCtrlOpenLUAName(ref name);
        Console.WriteLine($"ctrl open lua names : {name[0]}, {name[1]}, {name[2]}, {name[3]}");

        // Załadowanie i rozładowanie Lua protokołu otwartego
        rtn = robot.LoadCtrlOpenLUA(1);
        Console.WriteLine($"LoadCtrlOpenLUA rtn is {rtn}");
        robot.Sleep(2000);
        rtn = robot.UnloadCtrlOpenLUA(1);
        Console.WriteLine($"UnloadCtrlOpenLUA rtn is {rtn}");

        // Usunięcie określonego pliku Lua i wszystkich plików Lua
        rtn = robot.OpenLuaDelete("CtrlDev_WELDING_A.lua");
        Console.WriteLine($"OpenLuaDelete rtn is {rtn}");
        rtn = robot.AllOpenLuaDelete();
        Console.WriteLine($"AllOpenLuaDelete rtn is {rtn}");

        return 0;
    }

Sterowanie ruchem dłoni
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:    

    /**
    * @brief  Sterowanie ruchem dłoni
    * @param  [in] idstart  Początkowy numer stacji podrzędnej
    * @param  [in] slaveNum  Liczba
    * @param  [in] pos[16]  Pozycja (-360~360) 
    * @param  [in] speed[16]  Procent prędkości, zakres [0~100]
    * @param  [in] force[16]  Procent momentu obrotowego, zakres [0~100]
    * @param  [in] max_time  Maksymalny czas oczekiwania, zakres [0~30000], jednostka ms
    * @return  Kod błędu
    */
    public int SetDexterousHandsMove(int idstart, int slaveNum, double[] pos, int[] speed, int[] force, int max_time)
    
Sterowanie resetem i aktywacją dłoni
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:   

    /**
    * @brief  Sterowanie resetem i aktywacją dłoni
    * @param  [in] id  Numer stacji podrzędnej
    * @param  [in] act  0-reset 1-aktywacja
    * @return  Kod błędu
    */
    public int SetDexterousHandsAct(int id, int act)

Czyszczenie błędu dłoni
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:   

    /**
    * @brief  Czyszczenie błędu dłoni
    * @return  Kod błędu
    */
    public int ClearDexterousHandsError()
    
Ustawianie włączonych funkcji sterowania ruchem dłoni
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:   

    /**
    * @brief Ustawia włączone funkcje sterowania ruchem dłoni
    * @param [in] id Numer stacji podrzędnej dłoni
    * @param [in] func 0-wyzwolenie chwytu, 1-inicjalizacja chwytaka, 2-ustawienie pozycji, 3-ustawienie prędkości, 4-ustawienie momentu obrotowego, 6-odczyt stanu chwytaka, 7-odczyt stanu inicjalizacji, 8-odczyt kodu błędu, 9-odczyt pozycji, 10-odczyt prędkości, 11-odczyt momentu obrotowego, 12-ustawienie liczby obrotów, 13-ustawienie prędkości obrotowej, 14-ustawienie momentu obrotowego obrotu, 15-odczyt stanu chwytaka obrotowego, 16-odczyt stanu inicjalizacji obrotu, 17-odczyt liczby obrotów, 18-odczyt prędkości obrotowej, 19-odczyt momentu obrotowego obrotu, 20-ustawienie ruchu synchronicznego wieloosiowego, 21-komenda kasowania błędów, 22-stan pracy pojedynczej osi, 23-stan pracy wszystkich osi
    * @return  Kod błędu
    */
    public int SetDexterousHandsFunc(int id, int[] func)
    
Pobieranie włączonych funkcji sterowania ruchem dłoni
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:   

    /**
    * @brief Pobiera włączone funkcje sterowania ruchem dłoni
    * @param [in] id Numer urządzenia dłoni
    * @param [out] func 0-wyzwolenie chwytu, 1-inicjalizacja chwytaka, 2-ustawienie pozycji, 3-ustawienie prędkości, 4-ustawienie momentu obrotowego, 6-odczyt stanu chwytaka, 7-odczyt stanu inicjalizacji, 8-odczyt kodu błędu, 9-odczyt pozycji, 10-odczyt prędkości, 11-odczyt momentu obrotowego, 12-ustawienie liczby obrotów, 13-ustawienie prędkości obrotowej, 14-ustawienie momentu obrotowego obrotu, 15-odczyt stanu chwytaka obrotowego, 16-odczyt stanu inicjalizacji obrotu, 17-odczyt liczby obrotów, 18-odczyt prędkości obrotowej, 19-odczyt momentu obrotowego obrotu, 20-ustawienie ruchu synchronicznego wieloosiowego, 21-komenda kasowania błędów, 22-stan pracy pojedynczej osi, 23-stan pracy wszystkich osi
    * @return  Kod błędu
    */
    public int GetDexterousHandsFunc(int id, ref int[] func)

Przykład kodu konfiguracji i ruchu dłoni na końcówce robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:
    
    private void button105_Click(object sender, EventArgs e)
    {
        int id = 1;               // Numer stacji podrzędnej
        int slaveNum = 4;         // Steruje 4 palcami
        int max_time = 8000;      // Maksymalny czas oczekiwania 8 sekund
        int[] speed = new int[16]; // Tablica prędkości, wszystkie 0 oznacza użycie domyślnej prędkości
        int[] force = new int[16]; // Tablica momentu obrotowego

        // Inicjalizacja tablicy momentu: pierwsze 4 palce ustawione na 50%, reszta 0 (wartości wysyłane przez komendę Move)
        for (int i = 0; i < 16; i++)
            force[i] = (i < 4) ? 50 : 0;

        // Funkcja pomocnicza: ustawienie tablicy pozycji (tylko pierwsze 4 palce są skuteczne)
        double[] pos = new double[16];
        void SetPositions(double v1, double v2, double v3, double v4)
        {
            for (int i = 0; i < 16; i++)
                pos[i] = 0;
            pos[0] = v1;
            pos[1] = v2;
            pos[2] = v3;
            pos[3] = v4;
        }

        JointPos j1 = new JointPos(-91.876, -85.920, 109.279, -86.239, -96.664, -28.563);
        JointPos j2 = new JointPos(-40.954, -85.920, 109.279, -86.239, -96.664, -28.563);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);

        Console.WriteLine("===== Rozpoczęto pełny test funkcji dłoni =====");

        // 1. Wyczyść błąd
        int ret = robot.ClearDexterousHandsError();
        Console.WriteLine($"ClearDexterousHandsError -> {ret}");

        // ========== 2. Ustaw przełączniki funkcji ==========
        int[] setFunc = new int[32];
        setFunc[2] = 1;   // Włącz funkcję ustawiania pozycji
        setFunc[4] = 1;   // Włącz funkcję ustawiania momentu obrotowego
        setFunc[9] = 1;   // Odczyt pozycji
        setFunc[10] = 1;  // Odczyt momentu obrotowego
        setFunc[11] = 1;  // Odczyt statusu
        setFunc[22] = 1;  // Status ruchu pojedynczej osi

        ret = robot.SetDexterousHandsFunc(id, setFunc);
        Console.WriteLine($"SetDexterousHandsFunc(włączono init + funkcje pozycji/momentu) -> {ret}");

        // ========== 3. Odczyt statusu funkcji (weryfikacja, czy ustawienia zostały zastosowane) ==========
        int[] getFunc = new int[32];  // GetDexterousHandsFunc zwraca 32 liczby całkowite
        ret = robot.GetDexterousHandsFunc(id, ref getFunc);
        Console.WriteLine($"GetDexterousHandsFunc -> {ret}");
        if (ret == 0)
        {
            // Wyświetl wszystkie 32 wartości
            Console.WriteLine("Wszystkie 32 wartości zwrócone przez GetDexterousHandsFunc:");
            for (int i = 0; i < getFunc.Length; i++)
            {
                Console.Write($"  [{i}]={getFunc[i]}");
                if ((i + 1) % 8 == 0)
                    Console.WriteLine();          // Nowa linia co 8 elementów
                else if (i < getFunc.Length - 1)
                    Console.Write(", ");
            }
            if (getFunc.Length % 8 != 0)
                Console.WriteLine();              // Dodaj nową linię, jeśli ostatnia linia ma mniej niż 8 elementów
        }

        // ========== 4. Aktywuj dłoń ==========
        ret = robot.SetDexterousHandsAct(id, 1);
        Console.WriteLine($"SetDexterousHandsAct(aktywacja) -> {ret}");
        if (ret != 0)
        {
            Console.WriteLine("Aktywacja nie powiodła się, test przerwany");
            return;
        }

        // ========== 5. Początkowy ruch do 20° (wysyłanie wartości pozycji i momentu przez komendę Move) ==========
        SetPositions(20, 20, 20, 20);
        ret = robot.SetDexterousHandsMove(id, slaveNum, pos, speed, force, max_time);
        Console.WriteLine($"Początkowy ruch do 20° -> {ret}");
        robot.Sleep(5000);

        // ========== 6. Ruch wahadłowy 10 razy (10° ↔ 50°) ==========
        Console.WriteLine("Rozpoczynanie 10 ruchów wahadłowych...");
        for (int iteration = 1; iteration <= 10; iteration++)
        {
            robot.MoveJ(j1, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);

            SetPositions(10, 10, 10, 10);
            ret = robot.SetDexterousHandsMove(id, slaveNum, pos, speed, force, max_time);
            Console.WriteLine($"[{iteration}] Ruch do 10° -> {ret}");
            robot.Sleep(1000);

            robot.MoveJ(j2, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);

            SetPositions(50, 50, 50, 50);
            ret = robot.SetDexterousHandsMove(id, slaveNum, pos, speed, force, max_time);
            Console.WriteLine($"[{iteration}] Ruch do 50° -> {ret}");
            robot.Sleep(1000);
        }

        Console.WriteLine("Test zakończony (ustawienie/odczyt przełączników funkcji + aktywacja + 10 ruchów wahadłowych).");
    }