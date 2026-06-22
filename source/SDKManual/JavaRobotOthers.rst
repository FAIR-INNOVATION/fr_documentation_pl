Inne interfejsy
================

.. toctree:: 
    :maxdepth: 5

Pobieranie klucza publicznego SSH
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera klucz publiczny SSH
    * @param [out] keygen Klucz publiczny
    * @return Kod błędu
    */
    int GetSSHKeygen(String[] keygen)

Wysyłanie polecenia SCP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.6-3.8.3

.. code-block:: Java
    :linenos:

    /** 
    * @brief Wysyła polecenie SCP
    * @param [in] mode 0-upload (komputer nadrzędny -> kontroler), 1-pobranie (kontroler -> komputer nadrzędny)
    * @param [in] sshname Nazwa użytkownika komputera nadrzędnego
    * @param [in] sship Adres IP komputera nadrzędnego
    * @param [in] usr_file_url Ścieżka do pliku na komputerze nadrzędnym
    * @param [in] robot_file_url Ścieżka do pliku w kontrolerze robota
    * @return Kod błędu
    */
    int SetSSHScpCmd(int mode, String sshname, String sship, String usr_file_url, String robot_file_url)

Obliczanie wartości MD5 pliku w określonej ścieżce
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Oblicza wartość MD5 pliku w określonej ścieżce
    * @param [in] file_path Ścieżka do pliku wraz z nazwą. Domyślna ścieżka folderu Traj to:"/fruser/traj/", np. "/fruser/traj/trajHelix_aima_1.txt"
    * @param [out] md5 Wartość MD5 pliku
    * @return Kod błędu
    */
    int ComputeFileMD5(String file_path, String[] md5)

Przykład kodu dla poleceń SSH i MD5 robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestSSHMd5(Robot robot)
    {
        String file_path= "/fruser/airlab.lua";
        String[] md5 =new String[]{""};

        String[] ssh_keygen=new String[]{""};
        int retval = robot.GetSSHKeygen(ssh_keygen);
        System.out.println(ssh_keygen[0]);

        String ssh_name = "fr";
        String ssh_ip = "192.168.58.45";
        String ssh_route = "/home/fr";
        String ssh_robot_url = "/root/robot/dhpara.config";
        retval = robot.SetSSHScpCmd(1, ssh_name, ssh_ip, ssh_route, ssh_robot_url);
        System.out.println("SetSSHScpCmd retval is:"+ retval);
        System.out.println("robot url is:"+ ssh_robot_url);

        robot.ComputeFileMD5(file_path, md5);
        System.out.println("md5 is:+"+ md5[0]);
        return 0;
    }

Ustawianie okresu zwrotnego portu 20004 robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia okres zwrotny portu 20004 robota
    * @param [in] period Okres zwrotny portu 20004 robota (ms)
    * @return  Kod błędu
    */
    public int SetRobotRealtimeStateSamplePeriod(int period)

Pobieranie okresu zwrotnego portu 20004 robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Pobiera okres zwrotny portu 20004 robota
    * @return  List[0]:Kod błędu; List[1]:Okres zwrotny portu 20004 robota (ms)
    */
    public List<Integer> GetRobotRealtimeStateSamplePeriod()

Przykład konfiguracji okresu zwrotnego stanu portu 20004 robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestRealtimePeriod(Robot robot)
    {
        robot.SetRobotRealtimeStateSamplePeriod(10);
        List<Integer> getPeriod = new ArrayList<>();
        getPeriod=robot.GetRobotRealtimeStateSamplePeriod();
        robot.Sleep(1000);

        return 0;
    }

Aktualizacja oprogramowania robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
     * @brief Aktualizacja oprogramowania robota
     * @param [in] filePath Pełna ścieżka pakietu aktualizacyjnego oprogramowania
     * @param [in] block Czy blokować do czasu zakończenia aktualizacji: true - blokuj; false - nieblokujący
     * @return  Kod błędu
     */
    public int SoftwareUpgrade(String filePath, boolean block)

Pobieranie statusu aktualizacji oprogramowania robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Pobiera status aktualizacji oprogramowania robota
    * @return  List[0]:Kod błędu; List[1]:Status aktualizacji oprogramowania robota: 0-bezczynność lub przesyłanie pakietu aktualizacyjnego; 1~100:procent ukończenia aktualizacji; -1:niepowodzenie aktualizacji oprogramowania; -2:niepowodzenie weryfikacji; -3:niepowodzenie weryfikacji wersji; -4:niepowodzenie dekompresji; -5:niepowodzenie aktualizacji konfiguracji użytkownika; -6:niepowodzenie aktualizacji konfiguracji urządzeń peryferyjnych; -7:niepowodzenie aktualizacji konfiguracji osi rozszerzenia; -8:niepowodzenie aktualizacji konfiguracji robota; -9:niepowodzenie aktualizacji konfiguracji parametrów DH
    */
    public List<Integer> GetSoftwareUpgradeState()

Przykład kodu aktualizacji oprogramowania robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestUpgrade(Robot robot)
    {
        robot.SoftwareUpgrade("D://zUP/QNX382/software.tar.gz", false);
        while (true)
        {
            List<Integer> inter=new ArrayList<>();
            inter=robot.GetSoftwareUpgradeState();
            System.out.println("upgrade state is:"+ inter.get(1));
            robot.Sleep(300);
        }
    }

Pobieranie bazy danych tabeli punktów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Pobiera bazę danych tabeli punktów 
    * @param [in] pointTableName Nazwa tabeli punktów do pobrania    pointTable1.db
    * @param [in] saveFilePath Ścieżka zapisu pobranej tabeli punktów   C://test/
    * @return Kod błędu 
    */
    int PointTableDownLoad(String pointTableName, String saveFilePath);

Przesyłanie bazy danych tabeli punktów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Przesyła bazę danych tabeli punktów 
    * @param [in] pointTableFilePath Pełna ścieżka przesyłanej tabeli punktów   C://test/pointTable1.db
    * @return Kod błędu 
    */
    int PointTableUpLoad(String pointTableFilePath);

Aktualizacja pliku Lua tabeli punktów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Aktualizuje plik Lua tabeli punktów
    * @param [in] pointTableName Nazwa tabeli punktów do przełączenia   "pointTable1.db". Gdy tabela punktów jest pusta, tzn. "", oznacza to aktualizację programu Lua do programu początkowego bez zastosowanej tabeli punktów
    * @param [in] luaFileName Nazwa pliku Lua do aktualizacji   "testPointTable.lua"
    * @param [out] errorStr Informacja o błędzie przełączania tabeli punktów
    * @return Kod błędu 
    */
    int PointTableUpdateLua(String pointTableName, String luaFileName, String errorStr);

Przykład operacji na tabeli punktów robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestPointTable(Robot robot)
    {
        String save_path = "D://zDOWN/";
        String point_table_name = "point_table_FR5.db";
        int rtn = robot.PointTableDownLoad(point_table_name, save_path);

        String upload_path = "D://zUP/point_table_FR5.db";
        rtn = robot.PointTableUpLoad(upload_path);

        String point_tablename = "point_table_FR5.db";
        String lua_name = "airlab.lua";
        String err="";
        rtn = robot.PointTableUpdateLua(point_tablename, lua_name,err);

        robot.CloseRPC();
        return 0;
    }

Pobieranie logów kontrolera
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.4-3.8.1

.. code-block:: Java
    :linenos:

    /** 
    * @brief Pobiera logi kontrolera
    * @param [in] savePath Ścieżka zapisu pliku "D://zDown/"
    * @return Kod błędu
    */
    int RbLogDownload(String savePath);

Pobieranie wszystkich źródeł danych
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.4-3.8.1

.. code-block:: Java
    :linenos:

    /** 
    * @brief Pobiera wszystkie źródła danych
    * @param [in] savePath Ścieżka zapisu pliku "D://zDown/"
    * @return Kod błędu
    */
    int AllDataSourceDownload(String savePath);

Pobieranie pakietu kopii zapasowej danych
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.4-3.8.1

.. code-block:: Java
    :linenos:

    /** 
    * @brief Pobiera pakiet kopii zapasowej danych
    * @param [in] savePath Ścieżka zapisu pliku "D://zDown/"
    * @return Kod błędu
    */
    int DataPackageDownload(String savePath);

Przykład kodu pobierania danych z kontrolera
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestDownLoadRobotData(Robot robot)
    {
        int rtn = robot.RbLogDownload("D://zDOWN/");

        rtn = robot.AllDataSourceDownload("D://zDOWN/");

        rtn = robot.DataPackageDownload("D://zDOWN/");
        return 0;
    }

Ustawianie aktualizacji enkodera
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia aktualizację enkodera
    * @param [in] path Pełna ścieżka lokalnego pakietu aktualizacyjnego (D://zUP/XXXXX.bin)
    * @return Kod błędu
    */
    int SetEncoderUpgrade(String path)

Ustawianie aktualizacji firmware przegubów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia aktualizację firmware przegubów
    * @param [in] type Typ pliku aktualizacyjnego; 1-aktualizacja firmware; 2-aktualizacja pliku konfiguracyjnego stacji podrzędnej
    * @param [in] path Pełna ścieżka lokalnego pakietu aktualizacyjnego (D://zUP/XXXXX.bin)
    * @return Kod błędu
    */
    public int SetJointFirmwareUpgrade(int type, String path)

Ustawianie aktualizacji firmware skrzynki kontrolnej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia aktualizację firmware skrzynki kontrolnej
    * @param [in] type Typ pliku aktualizacyjnego; 1-aktualizacja firmware; 2-aktualizacja pliku konfiguracyjnego stacji podrzędnej
    * @param [in] path Pełna ścieżka lokalnego pakietu aktualizacyjnego (D://zUP/XXXXX.bin)
    * @return Kod błędu
    */
    public int SetCtrlFirmwareUpgrade(int type, String path)

Ustawianie aktualizacji firmware końcówki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia aktualizację firmware końcówki
    * @param [in] type Typ pliku aktualizacyjnego; 1-aktualizacja firmware; 2-aktualizacja pliku konfiguracyjnego stacji podrzędnej
    * @param [in] path Pełna ścieżka lokalnego pakietu aktualizacyjnego (D://zUP/XXXXX.bin)
    * @return Kod błędu
    */
    public int SetEndFirmwareUpgrade(int type, String path)

Aktualizacja pliku konfiguracji pełnych parametrów przegubu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:

    /**
    * @brief Aktualizacja pliku konfiguracji pełnych parametrów przegubu
    * @param [in] path Pełna ścieżka lokalnego pakietu aktualizacyjnego (D://zUP/XXXXX.bin)
    * @return Kod błędu
    */
    public int JointAllParamUpgrade(String path)

Przykład kodu aktualizacji firmware stacji podrzędnej robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestFirmWareUpgrade(Robot robot)
    {
        robot.RobotEnable(0);
        robot.Sleep(200);
        int rtn = robot.JointAllParamUpgrade("D://zUP/standardQX/jointallparametersFR56.0.db");
        System.out.println("robot JointAllParamUpgrade rtn is:"+ rtn);

        rtn = robot.SetCtrlFirmwareUpgrade(2, "D://zUP/upgrade/FAIR_Cobot_Cbd_Asix_V2.0.bin");
        System.out.println("robot SetCtrlFirmwareUpgrade config param rtn is:"+ rtn);

        rtn = robot.SetEndFirmwareUpgrade(2, "D://zUP/upgrade/FAIR_Cobot_Axle_Asix_V2.4.bin");
        System.out.println("robot SetEndFirmwareUpgrade config param rtn is:"+ rtn);

        robot.SetSysServoBootMode();
        rtn = robot.SetCtrlFirmwareUpgrade(1, "D://zUP/standardQX/FR_CTRL_PRIMCU_FV201010_MAIN_U4_T01_20240529.bin");
        System.out.println("robot SetCtrlFirmwareUpgrade rtn is:"+ rtn);

        rtn = robot.SetEndFirmwareUpgrade(1, "D://zUP/standardQX/FR_END_FV201010_MAIN_U01_T01_20250522.bin");
        System.out.println("robot SetEndFirmwareUpgrade rtn is:"+ rtn);

        rtn = robot.SetJointFirmwareUpgrade(1, "D://zUP/standardQX/FR_SERVO_FV502211_MAIN_U7_T07_20250217.bin");
        System.out.println("robot SetJointFirmwareUpgrade rtn is:"+ rtn);

        robot.CloseRPC();
    }

Aktualizacja systemu operacyjnego robota (skrzynka kontrolna LA)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Aktualizacja systemu operacyjnego robota (skrzynka kontrolna LA)
     * @param [in] filePath Pełna ścieżka pakietu aktualizacyjnego systemu operacyjnego
     * @return  Kod błędu
     */
    public int KernelUpgrade(String filePath)

Pobieranie wyniku aktualizacji systemu operacyjnego robota (skrzynka kontrolna LA)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Pobiera wynik aktualizacji systemu operacyjnego robota (skrzynka kontrolna LA)
     * @param [out] result Wynik aktualizacji: 0:sukces; -1:niepowodzenie
     * @return  Kod błędu
     */
    public int GetKernelUpgradeResult(int[] result)

Generowanie logów MCU robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Generuje logi MCU robota
    * @return Kod błędu
    */
    public int RobotMCULogCollect()

Ustawianie zatrzymania robota po rozłączeniu komunikacji portu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia zatrzymanie robota po rozłączeniu komunikacji portu
    * @param portID Numer portu 0-8080; 1-8083; 2-20002; 3-20004
    * @param enable 0-wyłącz; 1-włącz
    * @param confirmTime Czas potwierdzenia przerwania komunikacji (ms)[0-5000]
    * @return Kod błędu
    */
    public int SetRobotStopOnComDisc(int portID, bool enable, int confirmTime)
    
Pobieranie parametrów zatrzymania robota po rozłączeniu komunikacji portu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera parametry zatrzymania robota po rozłączeniu komunikacji portu
    * @param portID Numer portu 0-8080; 1-8083; 2-20002; 3-20004
    * @param enable Tablica wyników, index 0: 0-wyłącz; 1-włącz
    * @param confirmTime Tablica wyników, index 0: Czas potwierdzenia przerwania komunikacji (ms)[0-5000] 
    * @return Kod błędu
    */
    public int GetRobotStopOnComDisc(int portID, int[] enable, int[] confirmTime)

Przykład kodu parametrów zatrzymania robota po rozłączeniu komunikacji portu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    void TestRobotStopOnComDisc(Robot robot)
    {
        int[] enable = {0};
        int[] confirmTime = {0};
        int rtn = 0;
        rtn = robot.SetRobotStopOnComDisc(0, true, 330);
        rtn = robot.SetRobotStopOnComDisc(1, true, 550);
        rtn = robot.SetRobotStopOnComDisc(2, true, 110);
        rtn = robot.SetRobotStopOnComDisc(3, true, 220);
        System.out.printf("SetRobotStopOnComDisc %d\n", rtn);

        robot.GetRobotStopOnComDisc(0, enable, confirmTime);
        System.out.printf("GetRobotStopOnComDisc 8080 rtn %d; enable is %d; confirm time is %d\n", rtn, enable[0], confirmTime[0]);
        robot.GetRobotStopOnComDisc(1, enable, confirmTime);
        System.out.printf("GetRobotStopOnComDisc 8083 rtn %d; enable is %d; confirm time is %d\n", rtn, enable[0], confirmTime[0]);
        robot.GetRobotStopOnComDisc(2, enable, confirmTime);
        System.out.printf("GetRobotStopOnComDisc 20002 rtn %d; enable is %d; confirm time is %d\n", rtn, enable[0], confirmTime[0]);
        robot.GetRobotStopOnComDisc(3, enable, confirmTime);
        System.out.printf("GetRobotStopOnComDisc 20004 rtn %d; enable is %d; confirm time is %d\n", rtn, enable[0], confirmTime[0]);

        return;
    }

Wysyłanie ramki polecenia UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Wysyła ramkę polecenia UDP
    * @param ramka polecenia
    * @return Kod błędu
    */
    public int SendUDPFrame(String frame)
    
Przykład kodu SDK dla komunikacji UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestRobotUDP (Robot robot) {
        robot.udpCmdClient.SetUDPCmdRpyCallback((srcType, count, cmdID, dataLen, content) -> {
            System.out.println("\n[收到机器人 UDP 回复]");
            System.out.println("srcType: " + srcType);
            System.out.println("count: " + count);
            System.out.println("cmdID: " + cmdID);
            System.out.println("dataLen: " + dataLen);
            System.out.println("内容 (content): " + content);
            return 0;
        });
        // 发送帧
        String frameToSend = "/f/bIII52III236III7IIIMode(1)III/b/f";
        robot.SendUDPFrame(frameToSend);
        robot.Sleep(2000);
        frameToSend = "/f/bIII52III236III7IIIMode(0)III/b/f";
        robot.SendUDPFrame(frameToSend);
        robot.Sleep(2000);
        frameToSend = "/f/bIII41III201III153IIIMoveJ(53.857,-89.441,119.453,-22.664,61.059,3.369,-54.249,-491.930,375.396,96.474,-6.896,-7.783,0,0,100,100,100,0.000,0.000,0.000,0.000,-1,0,0,0,0,0,0,0)III/b/f";
        robot.SendUDPFrame(frameToSend);
        robot.Sleep(2000);
        frameToSend = "/f/bIII42III203III163IIIMoveL(81.736,-85.284,114.974,-23.261,88.746,6.799,125.744,-506.570,375.396,96.474,-6.896,-7.783,0,0,100,100,100,-1,0,0.000,0.000,0.000,0.000,0,0,0,0,0,0,0,0,100,0)III/b/f";
        robot.SendUDPFrame(frameToSend);
        robot.Sleep(2000);
        frameToSend = "/f/bIII47III400III15IIIGetMCVersion(1)III/b/f/f/bIII48III424III21IIIGetSlaveFirmVersion()III/b/f";
        robot.SendUDPFrame(frameToSend);
        robot.Sleep(2000);
    }
        
Ustawianie niestandardowego koloru lampki końcówki robota przez użytkownika
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia niestandardowy kolor lampki końcówki robota przez użytkownika
    * @param r Sterowanie czerwoną lampką końcówki; 0-wyłącz; 1-włącz
    * @param g Sterowanie zieloną lampką końcówki; 0-wyłącz; 1-włącz
    * @param b Sterowanie niebieską lampką końcówki; 0-wyłącz; 1-włącz
    * @return Kod błędu
    */
    public int SetUserLEDColor(bool r, bool g, bool b)
            
Przykład kodu SDK ustawiania niestandardowego koloru lampki końcówki robota przez użytkownika
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public void testled(robot)
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