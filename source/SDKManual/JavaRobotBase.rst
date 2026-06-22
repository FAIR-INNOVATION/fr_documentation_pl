Podstawy robota
===============

.. toctree::
    :maxdepth: 5

Tworzenie instancji robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Konstruktor klasy interfejsu robota
    */
    Robot robot = new Robot();

Nawiązywanie komunikacji ze sterownikiem
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Nawiązuje komunikację ze sterownikiem robota
    * @param  [in] ip  Adres IP sterownika, domyślnie 192.168.58.2
    * @return Kod błędu
    */
    int RPC(String ip);

Zamykanie komunikacji z robotem
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Zamyka komunikację z robotem
    * @return Kod błędu
    */
    int CloseRPC();

Sprawdzanie numeru wersji SDK
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Sprawdza numer wersji SDK
    * @return Numer wersji
    */
    String GetSDKVersion();

Pobieranie adresu IP sterownika
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Pobiera adres IP sterownika
    * @param  [out] ip  Adres IP sterownika
    * @return  Kod błędu
    */
    int GetControllerIP(String[] ip);

Sterowanie wejściem lub wyjściem robota z trybu nauczania przez przeciąganie
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Steruje wejściem lub wyjściem robota z trybu nauczania przez przeciąganie
    * @param  [in] state 0-wyjście z trybu nauczania przez przeciąganie, 1-wejście do trybu nauczania przez przeciąganie
    * @return  Kod błędu
    */
    int DragTeachSwitch(int state);

Sprawdzanie, czy robot jest w trybie nauczania przez przeciąganie
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Sprawdza, czy robot jest w trybie nauczania przez przeciąganie
    * @param  [in] state 0-nie w trybie nauczania przez przeciąganie, 1-w trybie nauczania przez przeciąganie
    * @return  Kod błędu
    */
    int IsInDragTeach(List<Number> state);

Sterowanie włączaniem lub wyłączaniem zasilania robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Steruje włączaniem lub wyłączaniem zasilania robota. Po włączeniu zasilania robot domyślnie jest automatycznie włączany.
    * @param  [in] state  0-wyłącz zasilanie, 1-włącz zasilanie
    * @return  Kod błędu
    */
    int RobotEnable(int state);

Sterowanie przełączaniem trybu ręcznego/automatycznego robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Steruje przełączaniem trybu ręcznego/automatycznego robota
    * @param [in] mode 0-tryb automatyczny, 1-tryb ręczny
    * @return Kod błędu
    */
    int Mode(int mode);

Zamykanie systemu operacyjnego robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.4-3.8.1

.. code-block:: Java
    :linenos:

    /**
    * @brief Zamyka system operacyjny robota
    * @return Kod błędu
    */
    int ShutDownRobotOS();

Ustawianie parametrów ponownego łączenia z robotem
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia parametry ponownego łączenia z robotem
    * @param [in] enable Czy włączyć, true: włącz, false: wyłącz
    * @param [in] times Liczba prób ponownego łączenia
    * @param [in] period Odstęp czasu między próbami ponownego łączenia
    * @return Kod błędu
    */
    int SetReconnectParam(boolean enable, int times, int period);

Inicjalizacja parametrów logowania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Inicjalizuje parametry logowania
    * @param [in] logType Tryb wyjścia, DIRECT-wyjście bezpośrednie; BUFFER-wyjście buforowane; ASYNC-wyjście asynchroniczne
    * @param [in] logLevel Poziom filtrowania logów, ERROR-błąd; WARNING-ostrzeżenie; INFO-informacja; DEBUG-debugowanie
    * @param [in] filePath Ścieżka zapisu pliku, np. "D://Log/"
    * @param [in] saveFileNum Liczba zapisywanych plików, pliki przekraczające zarówno liczbę zapisywanych plików, jak i liczbę dni przechowywania zostaną usunięte
    * @param [in] saveDays Liczba dni przechowywania plików, pliki przekraczające zarówno liczbę zapisywanych plików, jak i liczbę dni przechowywania zostaną usunięte
    * @return Kod błędu
    */
    int LoggerInit(FrLogType logType, FrLogLevel logLevel, String filePath, int saveFileNum, int saveDays)

Ustawianie poziomu filtrowania logów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia poziom filtrowania logów
    * @param [in] logLevel Poziom filtrowania logów, ERROR-błąd; WARNING-ostrzeżenie; INFO-informacja; DEBUG-debugowanie
    * @return Kod błędu
    */
    int SetLoggerLevel(FrLogLevel logLevel)

Przykład kodu podstawowego sterowania robotem
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void main(String[] args)
    {
        Robot robot = new Robot();
        robot.SetReconnectParam(true,20,500);
        robot.LoggerInit(FrLogType.DIRECT, FrLogLevel.INFO, "D://log", 10, 10);
        int rtn = robot.RPC("192.168.58.2");
        if(rtn == 0)
        {
            System.out.println("rpc połączenie success");
        }
        else
        {
            System.out.println("rpc połączenie fail");
            return ;
        }
        String[] ip={""};
        String version = "";
        version=robot.GetSDKVersion();
        System.out.println("SDK version : " + version);
        int rtn = robot.GetControllerIP(ip);
        System.out.println("controller ip : " +  ip[0] + "  " + rtn);
        robot.Mode(1);//1-tryb ręczny  0-tryb automatyczny
        robot.Sleep(1000);
        robot.DragTeachSwitch(1);//wejście w tryb przeciągania
        robot.Sleep(1000);
        ROBOT_STATE_PKG pkg = robot.GetRobotRealTimeState();
        System.out.println("drag state : " + pkg.robot_state);
        robot.Sleep(1000);
        robot.DragTeachSwitch(0);//wyjście z trybu przeciągania
        robot.Sleep(1000);
        pkg = robot.GetRobotRealTimeState();
        System.out.println("drag state : " + pkg.robot_state);

        if (pkg.robot_state ==4){
           System.out.println("tryb przeciągania");
        }else {
           System.out.println("nie w trybie przeciągania");
        }
    }

Pobieranie wersji oprogramowania robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera wersję oprogramowania robota
    * @param [out] robotModel Model robota
    * @param [out] webVersion Wersja web
    * @param [out] controllerVersion Wersja sterownika
    * @return Kod błędu
    */
    int GetSoftwareVersion(String robotModel, String webVersion, String controllerVersion);

Pobieranie wersji sprzętowej robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera wersję sprzętową robota
    * @param [out] ctrlBoxBoardVersion Wersja sprzętowa płyty nośnej szafy sterowniczej
    * @param [out] driver1Version Wersja sprzętowa sterownika 1
    * @param [out] driver1Version Wersja sprzętowa sterownika 2
    * @param [out] driver1Version Wersja sprzętowa sterownika 3
    * @param [out] driver1Version Wersja sprzętowa sterownika 4
    * @param [out] driver1Version Wersja sprzętowa sterownika 5
    * @param [out] driver1Version Wersja sprzętowa sterownika 6
    * @param [out] endBoardVersion Wersja sprzętowa płyty końcowej
    * @return Kod błędu
    */
    int GetHardwareVersion(String ctrlBoxBoardVersion, String driver1Version, String driver2Version, String driver3Version,
                                          String driver4Version, String driver5Version, String driver6Version, String endBoardVersion);

Pobieranie wersji oprogramowania sprzętowego (firmware) robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera wersję oprogramowania sprzętowego (firmware) robota
    * @param [out] ctrlBoxBoardVersion Wersja firmware płyty nośnej szafy sterowniczej
    * @param [out] driver1Version Wersja firmware sterownika 1
    * @param [out] driver1Version Wersja firmware sterownika 2
    * @param [out] driver1Version Wersja firmware sterownika 3
    * @param [out] driver1Version Wersja firmware sterownika 4
    * @param [out] driver1Version Wersja firmware sterownika 5
    * @param [out] driver1Version Wersja firmware sterownika 6
    * @param [out] endBoardVersion Wersja firmware płyty końcowej
    * @return Kod błędu
    */
    int GetFirmwareVersion(String ctrlBoxBoardVersion, String driver1Version, String driver2Version, String driver3Version,
                                          String driver4Version, String driver5Version, String driver6Version, String endBoardVersion);

Przykład kodu pobierania wersji oprogramowania i oprogramowania sprzętowego robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void main(String[] args)
    {
        Robot robot = new Robot();
        robot.SetReconnectParam(true,20,500);//ustawienie liczby prób ponownego łączenia i odstępu
        robot.LoggerInit(FrLogType.DIRECT, FrLogLevel.INFO, "D://log", 10, 10);
        int rtn = robot.RPC("192.168.58.2");
        if(rtn == 0)
        {
            System.out.println("rpc połączenie success");
        }
        else
        {
            System.out.println("rpc połączenie fail");
            return ;
        }
        String ctrlBoxBoardVersion = "";
        String driver1Version = "";
        String driver2Version = "";
        String driver3Version = "";
        String driver4Version = "";
        String driver5Version = "";
        String driver6Version = "";
        String endBoardVersion = "";
        robot.GetHardwareVersion(ctrlBoxBoardVersion ,driver1Version,  driver2Version,  driver3Version,
                 driver4Version,  driver5Version,  driver6Version,  endBoardVersion);

        robot.GetFirmwareVersion(ctrlBoxBoardVersion, driver1Version, driver2Version, driver3Version,
                driver4Version, driver5Version, driver6Version, endBoardVersion);
    }