Inne interfejsy
===============

.. toctree:: 
    :maxdepth: 5

Pobranie klucza publicznego SSH
++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Pobiera klucz publiczny SSH 
    * @param [out] keygen Klucz publiczny
    * @return Kod błędu 
    */
    int GetSSHKeygen(ref string keygen);

Wysłanie instrukcji SCP
+++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Wysyła instrukcję SCP
    * @param [in] mode 0-przesyłanie (komputer nadrzędny -> kontroler), 1-pobieranie (kontroler -> komputer nadrzędny)
    * @param [in] sshname Nazwa użytkownika komputera nadrzędnego
    * @param [in] sship Adres IP komputera nadrzędnego
    * @param [in] usr_file_url Ścieżka pliku na komputerze nadrzędnym
    * @param [in] robot_file_url Ścieżka pliku w kontrolerze robota
    * @return Kod błędu
    */
    int SetSSHScpCmd(int mode, string sshname, string sship, string usr_file_url, string robot_file_url);

Obliczenie wartości MD5 pliku w określonej ścieżce
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Oblicza wartość MD5 pliku w określonej ścieżce 
    * @param [in] file_path Ścieżka pliku wraz z nazwą pliku, domyślna ścieżka folderu Traj to:"/fruser/traj/", np."/fruser/traj/trajHelix_aima_1.txt"
    * @param [out] md5 Wartość MD5 pliku
    * @return Kod błędu 
    */
    int ComputeFileMD5(string file_path, ref string md5);

Przykład kodu instrukcji SSH i MD5 robota
+++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3
    
.. code-block:: c#
    :linenos:

    private void button46_Click(object sender, EventArgs e)
    {
        string file_path = "/fruser/airlab.lua";
        string md5 = "";
        byte emerg_state = 0;
        byte si0_state = 0;
        byte si1_state = 0;
        int sdk_com_state = 0;

        string ssh_keygen = "";
        int retval = robot.GetSSHKeygen(ref ssh_keygen);
        Console.WriteLine("GetSSHKeygen retval is: {0}", retval);
        Console.WriteLine("ssh key is: {0}", ssh_keygen);

        string ssh_name = "fr";
        string ssh_ip = "192.168.58.45";
        string ssh_route = "/home/fr";
        string ssh_robot_url = "/root/robot/dhpara.config";
        retval = robot.SetSSHScpCmd(1, ssh_name, ssh_ip, ssh_route, ssh_robot_url);
        Console.WriteLine("SetSSHScpCmd retval is: {0}", retval);
        Console.WriteLine("robot url is: {0}", ssh_robot_url);

        robot.ComputeFileMD5(file_path, ref md5);
        Console.WriteLine("md5 is: {0}", md5);
    }

Ustawienie okresu informacji zwrotnej na porcie 20004 robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia okres informacji zwrotnej na porcie 20004 robota
    * @param [in] period Okres informacji zwrotnej na porcie 20004 robota (ms)
    * @return Kod błędu
    */
    int SetRobotRealtimeStateSamplePeriod(int period);

Pobranie okresu informacji zwrotnej na porcie 20004 robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Pobiera okres informacji zwrotnej na porcie 20004 robota
    * @param [out] period Okres informacji zwrotnej na porcie 20004 robota (ms)
    * @return Kod błędu
    */
    int GetRobotRealtimeStateSamplePeriod((ref int period);   

Przykład kodu konfiguracji okresu informacji zwrotnej o stanie na porcie 20004 robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button47_Click(object sender, EventArgs e)
    {
        robot.SetRobotRealtimeStateSamplePeriod(10);
        int getPeriod = 0;
        robot.GetRobotRealtimeStateSamplePeriod(ref getPeriod);
        Console.WriteLine("period is {0}", getPeriod);
        Thread.Sleep(1000);
    }

Aktualizacja oprogramowania robota
++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Aktualizacja oprogramowania robota
    * @param [in] filePath Pełna ścieżka pakietu aktualizacyjnego oprogramowania
    * @param [in] block Czy blokować do zakończenia aktualizacji true: blokujące; false: nieblokujące
    * @return  Kod błędu
    */
    int SoftwareUpgrade(string filePath, bool block);

Pobranie stanu aktualizacji oprogramowania robota
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera stan aktualizacji oprogramowania robota
    * @param [out] state Stan aktualizacji pakietu oprogramowania robota 0-bezczynny lub przesyłanie pakietu aktualizacyjnego; 1~100: procent ukończenia aktualizacji; -1: aktualizacja oprogramowania nieudana; -2: weryfikacja nieudana; -3: weryfikacja wersji nieudana; -4: dekompresja nieudana; -5: aktualizacja konfiguracji użytkownika nieudana; -6: aktualizacja konfiguracji urządzeń peryferyjnych nieudana; -7: aktualizacja konfiguracji osi rozszerzonej nieudana; -8: aktualizacja konfiguracji robota nieudana; -9: aktualizacja konfiguracji parametrów DH nieudana
    * @return  Kod błędu
    */
    int GetSoftwareUpgradeState(ref int state);

Przykład kodu aktualizacji oprogramowania robota
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button48_Click(object sender, EventArgs e)
    {
        robot.SoftwareUpgrade("D://zUP/QNX382/software.tar.gz", false);
        while (true)
        {
            int curState = -1;
            robot.GetSoftwareUpgradeState(ref curState);
            Console.WriteLine("upgrade state is {0}", curState);
            Thread.Sleep(300);
        }
    }

Pobranie tabeli punktów
+++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Pobranie tabeli punktów z kontrolera robota do komputera lokalnego 
    * @param [in] pointTableName Nazwa tabeli punktów w kontrolerze: pointTable1.db
    * @param [in] saveFilePath Ścieżka zapisu tabeli punktów na komputerze C://test/
    * @return Kod błędu 
    */
    int PointTableDownLoad(string pointTableName, string saveFilePath);

Przesłanie tabeli punktów
+++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Przesłanie tabeli punktów z komputera lokalnego do kontrolera robota 
    * @param [in] pointTableFilePath Bezwzględna ścieżka tabeli punktów na komputerze lokalnym C://test/pointTable1.db
    * @return Kod błędu 
    */
    int PointTableUpLoad(string pointTableFilePath);

Aktualizacja programu Lua za pomocą podanej tabeli punktów
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Aktualizacja punktów w programie lua za pomocą podanej tabeli punktów
    * @param [in] pointTableName Nazwa tabeli punktów w kontrolerze: "pointTable1.db", gdy tabela punktów jest pusta, czyli "", oznacza aktualizację programu lua do programu początkowego bez zastosowania tabeli punktów
    * @param [in] luaFileName Nazwa pliku lua do aktualizacji   "test.lua"
    * @param [out] errorStr Informacja o błędzie podczas aktualizacji tabeli punktów w lua  
    * @return Kod błędu 
    */
    int PointTableUpdateLua(string pointTableName, string luaFileName, ref string errorStr);

Przełączenie tabeli punktów i zastosowanie
+++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Przełączenie tabeli punktów i zastosowanie
    * @param [in] pointTableName Nazwa tabeli punktów do przełączenia   "pointTable1.db"
    * @param [out] errorStr Informacja o błędzie podczas przełączania tabeli punktów   
    * @return Kod błędu 
    */
    int PointTableSwitch(string pointTableName, ref string errorStr);

Przykład kodu operacji na tabeli punktów robota
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnUpload_Click(object sender, EventArgs e)
    {
        string save_path = "D://zDOWN/";
        string point_table_name = "test_point_A.db";
        int rtn = robot.PointTableDownLoad(point_table_name, save_path);
        Console.WriteLine("download : {0} fail: {1}", point_table_name, rtn);

        string upload_path = "D://zUP/test_point_A.db";
        rtn = robot.PointTableUpLoad(upload_path);
        Console.WriteLine("retval is: {0}", rtn);

        string point_tablename = "test_point_A.db";
        string lua_name = "Text1.lua";

        string errorStr = "";
        rtn = robot.PointTableUpdateLua(point_tablename, lua_name, ref errorStr);
        Console.WriteLine("retval is: {0}", rtn);
    }

Pobranie dziennika kontrolera
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobranie dziennika kontrolera
    * @param [in] savePath Ścieżka zapisu pliku "D://zDown/"
    * @return  Kod błędu
    */
    int RbLogDownload(string savePath);

Pobranie wszystkich źródeł danych
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Pobranie wszystkich źródeł danych
    * @param [in] savePath Ścieżka zapisu pliku "D://zDown/"
    * @return  Kod błędu
    */
    int AllDataSourceDownload(string savePath);

Pobranie pakietu kopii zapasowej danych
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Pobranie pakietu kopii zapasowej danych
    * @param [in] savePath Ścieżka zapisu pliku "D://zDown/"
    * @return  Kod błędu
    */
    int DataPackageDownload(string savePath);

Przykład kodu pobierania danych kontrolera
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button50_Click(object sender, EventArgs e)
    {
        int rtn = robot.RbLogDownload("D://zDOWN/");
        Console.WriteLine("RbLogDownload rtn is {0}", rtn);

        rtn = robot.AllDataSourceDownload("D://zDOWN/");
        Console.WriteLine("AllDataSourceDownload rtn is {0}", rtn);

        rtn = robot.DataPackageDownload("D://zDOWN/");
        Console.WriteLine("DataPackageDownload rtn is {0}", rtn);
    }

Aktualizacja systemu operacyjnego robota (skrzynka sterownicza LA)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
     * @brief Aktualizacja systemu operacyjnego robota (skrzynka sterownicza LA)
     * @param [in] filePath Pełna ścieżka pakietu aktualizacyjnego systemu operacyjnego
     * @return  Kod błędu
     */
    public int KernelUpgrade(string filePath)

Pobranie wyniku aktualizacji systemu operacyjnego robota (skrzynka sterownicza LA)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
     * @brief Pobranie wyniku aktualizacji systemu operacyjnego robota (skrzynka sterownicza LA)
     * @param [out] result Wynik aktualizacji: 0:sukces; -1:porażka
     * @return  Kod błędu
     */
    public int GetKernelUpgradeResult(ref int[] result)

Ustawienie aktualizacji enkodera
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia aktualizację enkodera
    * @param [in] path Pełna ścieżka lokalnego pakietu aktualizacyjnego (D://zUP/XXXXX.bin)
    * @return Kod błędu
    */
    int SetEncoderUpgrade(string path);

Ustawienie aktualizacji oprogramowania sprzętowego stawu
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia aktualizację oprogramowania sprzętowego stawu
    * @param [in] type Typ pliku aktualizacyjnego; 1-aktualizacja oprogramowania sprzętowego; 2-aktualizacja pliku konfiguracyjnego stacji podrzędnej
    * @param [in] path Pełna ścieżka lokalnego pakietu aktualizacyjnego (D://zUP/XXXXX.bin)
    * @return Kod błędu
    */
    int SetJointFirmwareUpgrade(int type, string path);

Ustawienie aktualizacji oprogramowania sprzętowego skrzynki sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia aktualizację oprogramowania sprzętowego skrzynki sterowniczej
    * @param [in] type Typ pliku aktualizacyjnego; 1-aktualizacja oprogramowania sprzętowego; 2-aktualizacja pliku konfiguracyjnego stacji podrzędnej
    * @param [in] path Pełna ścieżka lokalnego pakietu aktualizacyjnego (D://zUP/XXXXX.bin)
    * @return Kod błędu
    */
    int SetCtrlFirmwareUpgrade(int type, string path);

Ustawienie aktualizacji oprogramowania sprzętowego końcówki
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia aktualizację oprogramowania sprzętowego końcówki
    * @param [in] type Typ pliku aktualizacyjnego; 1-aktualizacja oprogramowania sprzętowego; 2-aktualizacja pliku konfiguracyjnego stacji podrzędnej
    * @param [in] path Pełna ścieżka lokalnego pakietu aktualizacyjnego (D://zUP/XXXXX.bin)
    * @return Kod błędu
    */
    int SetEndFirmwareUpgrade(int type, string path);

Aktualizacja pliku konfiguracyjnego pełnych parametrów stawu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Aktualizacja pliku konfiguracyjnego pełnych parametrów stawu
    * @param [in] path Pełna ścieżka lokalnego pakietu aktualizacyjnego (D://zUP/XXXXX.bin)
    * @return Kod błędu
    */
    int JointAllParamUpgrade(string path);

Przykład kodu aktualizacji oprogramowania sprzętowego stacji podrzędnej robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4
    
.. code-block:: c#
    :linenos:

    private void button83_Click(object sender, EventArgs e)
    {
        robot.RobotEnable(0);
        Thread.Sleep(200);
        int rtn = robot.JointAllParamUpgrade("D://zUP/upgrade/jointallparameters.db");
        Console.WriteLine($"robot JointAllParamUpgrade rtn is{rtn}");
        rtn = robot.SetCtrlFirmwareUpgrade(2, "D://zUP/upgrade/FAIR_Cobot_Cbd_Asix_V2.0.bin");
        Console.WriteLine($"robot SetCtrlFirmwareUpgrade rtn is{rtn}");
        rtn = robot.SetEndFirmwareUpgrade(2, "D://zUP/upgrade/FAIR_Cobot_Axle_Asix_V2.4.bin");
        Console.WriteLine($"robot SetEndFirmwareUpgrade rtn is {rtn}");
        robot.SetSysServoBootMode();
        rtn = robot.SetCtrlFirmwareUpgrade(1, "D://zUP/upgrade/FR_CTRL_PRIMCU_FV201212_MAIN_U4_T01_20250428(MT).bin");
        Console.WriteLine($"robot SetCtrlFirmwareUpgrade rtn is{rtn}");
        rtn = robot.SetEndFirmwareUpgrade(1, "D://zUP/upgrade/FR_END_FV201009_MAIN_U1_T01_20250428.bin");
        Console.WriteLine($"robot SetEndFirmwareUpgrade rtn is {rtn}");
        rtn = robot.SetJointFirmwareUpgrade(1, "D://zUP/upgrade/FR_SERVO_FV504214_MAIN_U7_T07_20250519.bin");
        Console.WriteLine($"robot SetJointFirmwareUpgrade rtn is{rtn}");
    }

Generowanie dziennika MCU robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Generowanie dziennika MCU robota
    * @return Kod błędu
    */
    public int RobotMCULogCollect();

Ustawienie zatrzymania robota po przerwaniu komunikacji portu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:
    
    /**
    * @brief Ustawienie zatrzymania robota po przerwaniu komunikacji portu
    * @param [in] pordID Numer portu 0-8080; 1-8083; 2-20002; 3-20004
    * @param [in] enable 0-wyłączone; 1-włączone
    * @param [in] confirmTime Czas potwierdzenia przerwania komunikacji (ms)[0-5000]
    * @return  Kod błędu
    */
    public int SetRobotStopOnComDisc(int portID, bool enable, int confirmTime)

Pobranie parametrów zatrzymania robota po przerwaniu komunikacji portu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:
    
    /**
    * @brief Pobranie parametrów zatrzymania robota po przerwaniu komunikacji portu
    * @param [in] pordID Numer portu 0-8080; 1-8083; 2-20002; 3-20004
    * @param [out] enable 0-wyłączone; 1-włączone
    * @param [out] confirmTime Czas potwierdzenia przerwania komunikacji (ms)[0-5000]
    * @return  Kod błędu
    */
    public int GetRobotStopOnComDisc(int portID, ref bool enable, ref int confirmTime)
    
Przykład kodu parametrów zatrzymania robota po przerwaniu komunikacji portu
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:
    
    void TestRobotStopOnComDisc()
    {
        int rtn = 0;

        // Ustawienie parametrów dla czterech portów
        rtn = robot.SetRobotStopOnComDisc(0, true, 330);
        rtn = robot.SetRobotStopOnComDisc(1, true, 550);
        rtn = robot.SetRobotStopOnComDisc(2, true, 110);
        rtn = robot.SetRobotStopOnComDisc(3, true, 220);
        Console.WriteLine($"SetRobotStopOnComDisc {rtn}");

        bool enable = false;
        int confirmTime = 0;

        // Pobranie i wydrukowanie ustawień dla każdego portu
        robot.GetRobotStopOnComDisc(0, ref enable, ref confirmTime);
        Console.WriteLine($"GetRobotStopOnComDisc 8080 rtn {rtn}; enable is {(enable ? 1 : 0)}; confirm time is {confirmTime}");

        robot.GetRobotStopOnComDisc(1, ref enable, ref confirmTime);
        Console.WriteLine($"GetRobotStopOnComDisc 8083 rtn {rtn}; enable is {(enable ? 1 : 0)}; confirm time is {confirmTime}");

        robot.GetRobotStopOnComDisc(2, ref enable, ref confirmTime);
        Console.WriteLine($"GetRobotStopOnComDisc 20002 rtn {rtn}; enable is {(enable ? 1 : 0)}; confirm time is {confirmTime}");

        robot.GetRobotStopOnComDisc(3, ref enable, ref confirmTime);
        Console.WriteLine($"GetRobotStopOnComDisc 20004 rtn {rtn}; enable is {(enable ? 1 : 0)}; confirm time is {confirmTime}");

    }

Wysłanie ramki instrukcji UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Wysyła ramkę instrukcji UDP
    * @param [in] Ramka instrukcji
    * @return Kod błędu
    */
    public int SendUDPFrame(string frame)
        
Przykład kodu SDK opartego na komunikacji UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    void TestRobotUDP()
    {
        robot.OnUdpFrameReceived += (comType, frameCount, frameCmdID, contentLen, content) =>
        {
            Console.WriteLine($"[UDP odpowiedź] comType={comType}, count={frameCount}, cmdID={frameCmdID}, content={content}");
        };


        //Wysłanie ramki
        string frameToSend = "/f/bIII52III236III7IIIMode(1)III/b/f";
        robot.SendUDPFrame(frameToSend);
        Thread.Sleep(2000);
        frameToSend = "/f/bIII52III236III7IIIMode(0)III/b/f";
        robot.SendUDPFrame(frameToSend);
        Thread.Sleep(2000);
        frameToSend = "/f/bIII41III201III153IIIMoveJ(53.857,-89.441,119.453,-22.664,61.059,3.369,-54.249,-491.930,375.396,96.474,-6.896,-7.783,0,0,100,100,100,0.000,0.000,0.000,0.000,-1,0,0,0,0,0,0,0)III/b/f";
        robot.SendUDPFrame(frameToSend);
        Thread.Sleep(2000);
        frameToSend = "/f/bIII42III203III163IIIMoveL(81.736,-85.284,114.974,-23.261,88.746,6.799,125.744,-506.570,375.396,96.474,-6.896,-7.783,0,0,100,100,100,-1,0,0.000,0.000,0.000,0.000,0,0,0,0,0,0,0,0,100,0)III/b/f";
        robot.SendUDPFrame(frameToSend);
        Thread.Sleep(2000);
        frameToSend = "/f/bIII47III400III15IIIGetMCVersion(1)III/b/f/f/bIII48III424III21IIIGetSlaveFirmVersion()III/b/f";
        robot.SendUDPFrame(frameToSend);
        Thread.Sleep(2000);

    }
        
Ustawienie niestandardowego koloru lampki końcowej robota przez użytkownika
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawienie niestandardowego koloru lampki końcowej robota przez użytkownika
    * @param [in] r Sterowanie czerwoną lampką końcową; 0-wyłączona; 1-włączona
    * @param [in] g Sterowanie zieloną lampką końcową; 0-wyłączona; 1-włączona
    * @param [in] b Sterowanie niebieską lampką końcową; 0-wyłączona; 1-włączona
    * @return Kod błędu
    */
    public int SetUserLEDColor(bool r, bool g, bool b)
            
Przykład kodu SDK ustawienia niestandardowego koloru lampki końcowej robota przez użytkownika
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    public void testled()
    {
        robot.SetUserLEDColor(true, true, true);
        robot.Sleep(1000);
        robot.SetUserLEDColor(false, false, false);
        robot.Sleep(1000);
        robot.SetUserLEDColor(true, false, false);
        robot.Sleep(1000);
        robot.SetUserLEDColor(false, true, false);
        robot.Sleep(1000);
        robot.SetUserLEDColor(false, false, true);
    }