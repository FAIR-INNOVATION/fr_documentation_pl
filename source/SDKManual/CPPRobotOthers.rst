Inne interfejsy
=================

.. toctree::
    :maxdepth: 5

Pobieranie klucza publicznego SSH
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera klucz publiczny SSH
    * @param [out] keygen Klucz publiczny
    * @return Kod błędu
    */
    errno_t GetSSHKeygen(char keygen[1024]);

Wysyłanie polecenia SCP
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Wysyła polecenie SCP
    * @param [in] mode 0-przesyłanie (komputer nadrzędny -> sterownik), 1-pobieranie (sterownik -> komputer nadrzędny)
    * @param [in] sshname Nazwa użytkownika komputera nadrzędnego
    * @param [in] sship Adres IP komputera nadrzędnego
    * @param [in] usr_file_url Ścieżka pliku na komputerze nadrzędnym
    * @param [in] robot_file_url Ścieżka pliku w sterowniku robota
    * @return Kod błędu
    */
    errno_t SetSSHScpCmd(int mode, char sshname[32], char sship[32], char usr_file_url[128], char robot_file_url[128]);

Obliczanie wartości MD5 pliku w określonej ścieżce
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Oblicza wartość MD5 pliku w określonej ścieżce
    * @param [in] file_path Ścieżka pliku zawierająca nazwę pliku, domyślna ścieżka folderu Traj to: "/fruser/traj/", np. "/fruser/traj/trajHelix_aima_1.txt"
    * @param [out] md5 Wartość MD5 pliku
    * @return Kod błędu
    */
    errno_t ComputeFileMD5(char file_path[256], char md5[256]);

Przykład kodu instrukcji SSH i MD5 robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestSSHMd5(void)
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
      char file_path[256] = "/fruser/airlab.lua";
      char md5[256] = { 0 };
      uint8_t emerg_state = 0;
      uint8_t si0_state = 0;
      uint8_t si1_state = 0;
      int sdk_com_state = 0;
      char ssh_keygen[1024] = { 0 };
      int retval = robot.GetSSHKeygen(ssh_keygen);
      printf("GetSSHKeygen retval is: %d\n", retval);
      printf("ssh key is: %s \n", ssh_keygen);
      char ssh_name[32] = "fr";
      char ssh_ip[32] = "192.168.58.45";
      char ssh_route[128] = "/home/fr";
      char ssh_robot_url[128] = "/root/robot/dhpara.config";
      retval = robot.SetSSHScpCmd(1, ssh_name, ssh_ip, ssh_route, ssh_robot_url);
      printf("SetSSHScpCmd retval is: %d\n", retval);
      printf("robot url is: %s\n", ssh_robot_url);
      robot.ComputeFileMD5(file_path, md5);
      printf("md5 is: %s \n", md5);
      robot.CloseRPC();
      return 0;
    }

Ustawianie okresu sprzężenia zwrotnego portu 20004 robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia okres sprzężenia zwrotnego portu 20004 robota
    * @param [in] period Okres sprzężenia zwrotnego portu 20004 robota (ms)
    * @return Kod błędu
    */
    errno_t SetRobotRealtimeStateSamplePeriod(int period);

Pobieranie okresu sprzężenia zwrotnego portu 20004 robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera okres sprzężenia zwrotnego portu 20004 robota
    * @param [out] period Okres sprzężenia zwrotnego portu 20004 robota (ms)
    * @return Kod błędu
    */
    errno_t GetRobotRealtimeStateSamplePeriod(int& period);

Przykład kodu konfiguracji okresu sprzężenia zwrotnego stanu portu 20004 robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestRealtimePeriod(void)
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
      robot.SetRobotRealtimeStateSamplePeriod(10);
      int getPeriod = 0;
      robot.GetRobotRealtimeStateSamplePeriod(getPeriod);
      cout << "period is " << getPeriod << endl;
      robot.Sleep(1000);
      robot.CloseRPC();
      return 0;
    }

Aktualizacja oprogramowania robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Aktualizacja oprogramowania robota
    * @param [in] filePath Pełna ścieżka pakietu aktualizacyjnego oprogramowania
    * @param [in] block Czy blokować do zakończenia aktualizacji true: blokuj; false: nie blokuj
    * @return Kod błędu
    */
    errno_t SoftwareUpgrade(std::string filePath, bool block);

Pobieranie stanu aktualizacji oprogramowania robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera stan aktualizacji oprogramowania robota
    * @param [out] state Stan aktualizacji pakietu oprogramowania robota (0-bezczynność lub przesyłanie pakietu aktualizacyjnego; 1~100: procent ukończenia aktualizacji; -1: nieudana aktualizacja oprogramowania; -2: nieudana weryfikacja; -3: nieudana weryfikacja wersji; -4: nieudane rozpakowanie; -5: nieudana aktualizacja konfiguracji użytkownika; -6: nieudana aktualizacja konfiguracji urządzeń peryferyjnych; -7: nieudana aktualizacja konfiguracji osi rozszerzonej; -8: nieudana aktualizacja konfiguracji robota; -9: nieudana aktualizacja konfiguracji parametrów DH)
    * @return Kod błędu
    */
    errno_t GetSoftwareUpgradeState(int &state);

Przykład kodu aktualizacji oprogramowania robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestUpgrade(void)
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      robot.LoggerInit();
      robot.SetLoggerLevel(3);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return -1;
      }
      robot.SetReConnectParam(true, 30000, 500);
      robot.SoftwareUpgrade("D://zUP/QNX/software.tar.gz", false);
      while (true)
      {
        int curState = -1;
        robot.GetSoftwareUpgradeState(curState);
        printf("upgrade state is %d\n", curState);
        robot.Sleep(300);
      }
      robot.CloseRPC();
      return 0;
    }

Pobieranie bazy danych tabeli punktów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera bazę danych tabeli punktów
    * @param [in] pointTableName Nazwa tabeli punktów do pobrania    pointTable1.db
    * @param [in] saveFilePath Ścieżka przechowywania pobranej tabeli punktów   C://test/
    * @return Kod błędu
    */
    errno_t PointTableDownLoad(const std::string &pointTableName, const std::string &saveFilePath);

Przesyłanie bazy danych tabeli punktów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Przesyła bazę danych tabeli punktów
    * @param [in] pointTableFilePath Pełna ścieżka przesyłanej tabeli punktów   C://test/pointTable1.db
    * @return Kod błędu
    */
    errno_t PointTableUpLoad(const std::string &pointTableFilePath);

Aktualizacja pliku lua tabeli punktów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Aktualizuje plik lua tabeli punktów
    * @param [in] pointTableName Nazwa tabeli punktów do przełączenia   "pointTable1.db", gdy tabela punktów jest pusta, czyli "", oznacza aktualizację programu lua do programu początkowego bez zastosowanej tabeli punktów
    * @param [in] luaFileName Nazwa pliku lua do aktualizacji   "testPointTable.lua"
    * @param [out] errorStr Informacja o błędzie przełączania tabeli punktów
    * @return Kod błędu
    */
    errno_t PointTableUpdateLua(const std::string &pointTableName, const std::string &luaFileName);

Przykład kodu operacji na tabeli punktów robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestPointTable(void)
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
      string save_path = "D://zDOWN/";
      string point_table_name = "point_table_FR5.db";
      rtn = robot.PointTableDownLoad(point_table_name, save_path);
      cout << "download : " << point_table_name << " fail: " << rtn << endl;
      string upload_path = "D://zUP/point_table_FR5.db";
      rtn = robot.PointTableUpLoad(upload_path);
      cout << "retval is: " << rtn << endl;
      string point_tablename = "point_table_FR5.db";
      string lua_name = "airlab.lua";
      rtn = robot.PointTableUpdateLua(point_tablename, lua_name);
      cout << "retval is: " << rtn << endl;
      robot.CloseRPC();
      return 0;
    }

Pobieranie dziennika sterownika
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.1-3.8.1

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera dziennik sterownika
    * @param [in] savePath Ścieżka zapisu pliku "D://zDown/"
    * @return Kod błędu
    */
    errno_t RbLogDownload(std::string savePath);

Pobieranie wszystkich źródeł danych
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.1-3.8.1

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera wszystkie źródła danych
    * @param [in] savePath Ścieżka zapisu pliku "D://zDown/"
    * @return Kod błędu
    */
    errno_t AllDataSourceDownload(std::string savePath);

Pobieranie pakietu kopii zapasowej danych
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.1-3.8.1

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera pakiet kopii zapasowej danych
    * @param [in] savePath Ścieżka zapisu pliku "D://zDown/"
    * @return Kod błędu
    */
    errno_t DataPackageDownload(std::string savePath);

Przykład kodu pobierania danych sterownika
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestDownLoadRobotData(void)
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
      rtn = robot.RbLogDownload("D://zDOWN/");
      cout << "RbLogDownload rtn is " << rtn << endl;
      rtn = robot.AllDataSourceDownload("D://zDOWN/");
      cout << "AllDataSourceDownload rtn is " << rtn << endl;
      rtn = robot.DataPackageDownload("D://zDOWN/");
      cout << "DataPackageDownload rtn is " << rtn << endl;
      robot.CloseRPC();
      return 0;
    }

Ustawianie aktualizacji oprogramowania sprzętowego stawów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia aktualizację oprogramowania sprzętowego stawów
    * @param [in] type Typ pliku aktualizacyjnego; 1-aktualizacja oprogramowania sprzętowego (przed użyciem należy wprowadzić robota w tryb boot); 2-aktualizacja pliku konfiguracji stacji podrzędnej (przed użyciem należy wyłączyć zasilanie robota)
    * @param [in] path Pełna ścieżka lokalnego pakietu aktualizacyjnego (D://zUP/XXXXX.bin)
    * @return Kod błędu
    */
    errno_t SetJointFirmwareUpgrade(int type, std::string path);

Ustawianie aktualizacji oprogramowania sprzętowego szafy sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia aktualizację oprogramowania sprzętowego szafy sterowniczej
    * @param [in] type Typ pliku aktualizacyjnego; 1-aktualizacja oprogramowania sprzętowego (przed użyciem należy wprowadzić robota w tryb boot); 2-aktualizacja pliku konfiguracji stacji podrzędnej (przed użyciem należy wyłączyć zasilanie robota)
    * @param [in] path Pełna ścieżka lokalnego pakietu aktualizacyjnego (D://zUP/XXXXX.bin)
    * @return Kod błędu
    */
    errno_t SetCtrlFirmwareUpgrade(int type, std::string path);

Ustawianie aktualizacji oprogramowania sprzętowego końcówki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia aktualizację oprogramowania sprzętowego końcówki
    * @param [in] type Typ pliku aktualizacyjnego; 1-aktualizacja oprogramowania sprzętowego (przed użyciem należy wprowadzić robota w tryb boot); 2-aktualizacja pliku konfiguracji stacji podrzędnej (przed użyciem należy wyłączyć zasilanie robota)
    * @param [in] path Pełna ścieżka lokalnego pakietu aktualizacyjnego (D://zUP/XXXXX.bin)
    * @return Kod błędu
    */
    errno_t SetEndFirmwareUpgrade(int type, std::string path);

Aktualizacja pliku konfiguracji pełnych parametrów stawów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Aktualizacja pliku konfiguracji pełnych parametrów stawów (przed użyciem należy wyłączyć zasilanie robota)
    * @param [in] path Pełna ścieżka lokalnego pakietu aktualizacyjnego (D://zUP/XXXXX.bin)
    * @return Kod błędu
    */
    errno_t JointAllParamUpgrade(std::string path);

Przykład kodu aktualizacji oprogramowania sprzętowego stacji podrzędnej robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestFirmWareUpgrade()
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
    robot.RobotEnable(0);
    robot.Sleep(200);
    rtn = robot.JointAllParamUpgrade("D://zUP/upgrade/jointallparameters.db");
    printf("robot JointAllParamUpgrade rtn is %d\n", rtn);
    rtn = robot.SetCtrlFirmwareUpgrade(2, "D://zUP/upgrade/FAIR_Cobot_Cbd_Asix_V2.0.bin");
    printf("robot SetCtrlFirmwareUpgrade config param rtn is %d\n", rtn);
    rtn = robot.SetEndFirmwareUpgrade(2, "D://zUP/upgrade/FAIR_Cobot_Axle_Asix_V2.4.bin");
    printf("robot SetEndFirmwareUpgrade config param rtn is %d\n", rtn);
    robot.SetSysServoBootMode();
    rtn = robot.SetCtrlFirmwareUpgrade(1, "D://zUP/upgrade/FR_CTRL_PRIMCU_FV201212_MAIN_U4_T01_20250428(MT).bin");
    printf("robot SetCtrlFirmwareUpgrade rtn is %d\n", rtn);
    rtn = robot.SetEndFirmwareUpgrade(1, "D://zUP/upgrade/FR_END_FV201009_MAIN_U1_T01_20250428.bin");
    printf("robot SetEndFirmwareUpgrade rtn is %d\n", rtn);
    rtn = robot.SetJointFirmwareUpgrade(1, "D://zUP/upgrade/FR_SERVO_FV504214_MAIN_U7_T07_20250519.bin");
    printf("robot SetJointFirmwareUpgrade rtn is %d\n", rtn);
    robot.CloseRPC();
    return 0;
    }

Aktualizacja systemu operacyjnego robota (szafa sterownicza LA)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
    * @brief Aktualizacja systemu operacyjnego robota (szafa sterownicza LA)
    * @param [in] filePath Pełna ścieżka pakietu aktualizacyjnego systemu operacyjnego
    * @return Kod błędu
    */
    errno_t KernelUpgrade(std::string filePath);

Pobieranie wyniku aktualizacji systemu operacyjnego robota (szafa sterownicza LA)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera wynik aktualizacji systemu operacyjnego robota (szafa sterownicza LA)
    * @param [out] result Wynik aktualizacji: 0: sukces; -1: niepowodzenie
    * @return Kod błędu
    */
    errno_t GetKernelUpgradeResult(int& result);

Generowanie dziennika MCU robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Generuje dziennik MCU robota
    * @return Kod błędu
    */
    errno_t RobotMCULogCollect();

Ustawianie zatrzymania robota po przerwaniu komunikacji portu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia zatrzymanie robota po przerwaniu komunikacji portu
    * @param [in] portID Numer portu 0-8080; 1-8083; 2-20002; 3-20004
    * @param [in] enable 0-wyłącz; 1-włącz
    * @param [in] confirmTime Czas potwierdzenia przerwania komunikacji (ms)[0-5000]
    * @return Kod błędu
    */
    errno_t SetRobotStopOnComDisc(int portID, bool enable, int confirmTime);

Pobieranie parametrów zatrzymania robota po przerwaniu komunikacji portu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera parametry zatrzymania robota po przerwaniu komunikacji portu
    * @param [in] portID Numer portu 0-8080; 1-8083; 2-20002; 3-20004
    * @param [out] enable 0-wyłącz; 1-włącz
    * @param [out] confirmTime Czas potwierdzenia przerwania komunikacji (ms)[0-5000]
    * @return Kod błędu
    */
    errno_t GetRobotStopOnComDisc(int portID, bool &enable, int &confirmTime);

Przykład kodu parametrów zatrzymania robota po przerwaniu komunikacji portu
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestRobotStopOnComDisc()
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
        bool enable = false;
        int confirmTime = 0;
        rtn = robot.SetRobotStopOnComDisc(0, true, 330);
        rtn = robot.SetRobotStopOnComDisc(1, true, 550);
        rtn = robot.SetRobotStopOnComDisc(2, true, 110);
        rtn = robot.SetRobotStopOnComDisc(3, true, 220);
        printf("SetRobotStopOnComDisc %d\n", rtn);
        robot.GetRobotStopOnComDisc(0, enable, confirmTime);
        printf("GetRobotStopOnComDisc 8080 rtn %d; enable is %d; confirm time is %d\n", rtn, enable, confirmTime);
        robot.GetRobotStopOnComDisc(1, enable, confirmTime);
        printf("GetRobotStopOnComDisc 80803 rtn %d; enable is %d; confirm time is %d\n", rtn, enable, confirmTime);
        robot.GetRobotStopOnComDisc(2, enable, confirmTime);
        printf("GetRobotStopOnComDisc 20002 rtn %d; enable is %d; confirm time is %d\n", rtn, enable, confirmTime);
        robot.GetRobotStopOnComDisc(3, enable, confirmTime);
        printf("GetRobotStopOnComDisc 20004 rtn %d; enable is %d; confirm time is %d\n", rtn, enable, confirmTime);
        robot.CloseRPC();
        robot.Sleep(1000);
        return 0;
    }

Wysyłanie ramki instrukcji UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Wysyła ramkę instrukcji UDP
    * @param [in] frame Ciąg ramki danych do wysłania, np.: /f/bIII20III303III7IIIMode(0)III/b/f
    * @return Kod błędu
    */
    errno_t SendUDPFrame(std::string frame);

Ustawianie funkcji zwrotnej wyniku wykonania instrukcji wysłanej przez SDK przez UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia funkcję zwrotną wyniku wykonania instrukcji wysłanej przez SDK przez UDP
    * @param [in] CallBack Funkcja zwrotna; comType-typ odpowiedzi zwrotnej komunikatu instrukcji 0-TCP, 1-UDP; count-licznik ramki odpowiedzi instrukcji; cmdID-numer instrukcji; contentLen-długość danych; content-treść danych
    * @return Kod błędu
    */
    errno_t SetCmdRpyCallback(void (*CallBack)(int comType, int count, int cmdID, int contentLen, std::string content));

Przykład kodu wysyłania instrukcji UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestSendUDPFrame()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.SetCmdRpyCallback(UDPFrameCallBack);
        printf("SetCmdRpyCallback rtn is %d\n", rtn);
        rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return -1;
        }
        robot.SetReConnectParam(true, 30000, 500);
        rtn = robot.SendUDPFrame("/f/bIII20III303III7IIIMode(0)III/b/f");
        printf("SendUDPFrame Mode(0) rtn is %d\n", rtn);
        robot.Sleep(1000);
        rtn = robot.SendUDPFrame("/f/bIII21III303III7IIIMode(1)III/b/f");
        printf("SendUDPFrame Mode(1) rtn is %d\n", rtn);
        robot.Sleep(1000);
        rtn = robot.SendUDPFrame("/f/bIII49III201III184IIIMoveJ(-15.625, -82.680, 101.654, -110.950, -88.290, 0.017, -383.012, -2.325, 242.655, -178.024, 1.710, 74.416, 0, 0, 100, 100, 100, 0.000, 0.000, 0.000, 0.000, -1, 0, 0, 0, 0, 0, 0, 0)III/b/f");
        printf("SendUDPFrame MoveJ(-15.625 rtn is %d\n", rtn);
        robot.Sleep(1000);
        rtn = robot.SendUDPFrame("/f/bIII48III203III199IIIMoveL(-75.622, -82.680, 101.654, -110.950, -88.290, 0.017, -193.537, 330.525, 242.657, -178.024, 1.710, 14.420, 0, 0, 100, 100, 100, -1, 0, 0.000, 0.000, 0.000, 0.000, 0, 0, 0, 0, 0, 0, 0, 0, 100, 0)III/b/f");
        printf("SendUDPFrame MoveL(-75.622 rtn is %d\n", rtn);
        robot.Sleep(1000);
        rtn = robot.SendUDPFrame("/f/bIII4III905III20IIIGetSoftwareVersion()III/b/f");
        printf("SendUDPFrame GetSoftwareVersion() rtn is %d\n", rtn);
        robot.Sleep(1000);
        rtn = robot.SendUDPFrame("/f/bIII20III303III7IIIMode(0)III/b/f");
        printf("SendUDPFrame rtn is %d\n", rtn);
        rtn = robot.SendUDPFrame("III20III303III7IIIMode(0)III/b/f");
        printf("SendUDPFrame rtn is %d\n", rtn);
        rtn = robot.SendUDPFrame("/f/bIII20III303III7IIIMode(0)");
        printf("SendUDPFrame rtn is %d\n", rtn);
        rtn = robot.SendUDPFrame("/f/bIII20III303III6IIIMode(0)III/b/f");
        printf("SendUDPFrame rtn is %d\n", rtn);
        rtn = robot.SendUDPFrame("/f/b|||20|||303|||7|||Mode(0)|||/b/f");
        printf("SendUDPFrame rtn is %d\n", rtn);
        rtn = robot.SendUDPFrame("/f/bII20II303II7IIMode(0)II/b/f");
        printf("SendUDPFrame rtn is %d\n", rtn);
        robot.CloseRPC();
        robot.Sleep(1000);
        return 0;
    }

Ustawianie niestandardowego koloru diody LED końcówki robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia niestandardowy kolor diody LED końcówki robota
    * @param [in] r Sterowanie czerwoną diodą LED końcówki; 0-wył.; 1-wł.
    * @param [in] g Sterowanie zieloną diodą LED końcówki; 0-wył.; 1-wł.
    * @param [in] b Sterowanie niebieską diodą LED końcówki; 0-wył.; 1-wł.
    * @return Kod błędu
    */
    errno_t SetUserLEDColor(bool r, bool g, bool b);

Przykład kodu ustawiania niestandardowego koloru diody LED końcówki robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestUserLedColor()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return 0;
        }
        robot.SetReConnectParam(true, 30000, 500);
        robot.SetUserLEDColor(true, true, true);
        robot.Sleep(1000);
        robot.SetUserLEDColor(false, false, false);
        robot.Sleep(1000);
        robot.SetUserLEDColor(true, false, false);
        robot.Sleep(1000);
        robot.SetUserLEDColor(false, true, false);
        robot.Sleep(1000);
        robot.SetUserLEDColor(false, false, true);
        robot.Sleep(1000);
        robot.CloseRPC();
        robot.Sleep(1000);
        return 0;
    }