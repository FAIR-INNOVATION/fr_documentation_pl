Podstawy robota
===============

.. toctree:: 
    :maxdepth: 5

Instancja robota
++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Konstruktor klasy interfejsu robota
    */
    Robot(); 

Nawiązanie komunikacji z kontrolerem
+++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Nawiązuje komunikację z kontrolerem robota
    * @param  [in] ip  Adres IP kontrolera, domyślnie fabrycznie 192.168.58.2
    * @return Kod błędu
    */
    int RPC(string ip);

Zerwanie komunikacji z robotem
++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Zrywa komunikację z kontrolerem robota 
    * @return Kod błędu 
    */ 
    int CloseRPC(); 

Sprawdzenie numeru wersji SDK
+++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Sprawdza numer wersji SDK 
    * @param [out] version Numer wersji SDK 
    * @return Kod błędu 
    */  
    int GetSDKVersion(ref string version);

Pobranie adresu IP kontrolera
+++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera adres IP kontrolera
    * @param  [out] ip  Adres IP kontrolera
    * @return  Kod błędu
    */
    int GetControllerIP(ref string ip);

Sterowanie wejściem lub wyjściem robota z trybu przeciągania nauczania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Steruje wejściem lub wyjściem robota z trybu przeciągania nauczania
    * @param  [in] state 0-wyjście z trybu przeciągania nauczania, 1-wejście w tryb przeciągania nauczania
    * @return  Kod błędu
    */
    int DragTeachSwitch(byte state);

Sprawdzenie, czy robot jest w trybie przeciągania
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Sprawdza, czy robot jest w trybie przeciągania nauczania
    * @param  [out] state 0-nie w trybie przeciągania nauczania, 1-w trybie przeciągania nauczania
    * @return  Kod błędu
    */
    int IsInDragTeach(ref byte state); 

Sterowanie załączeniem lub odłączeniem robota
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Steruje załączeniem lub odłączeniem robota. Po włączeniu zasilania robot domyślnie automatycznie się załącza.
    * @param  [in] state  0-odłączenie, 1-załączenie
    * @return  Kod błędu
    */
    int RobotEnable(byte state); 

Sterowanie przełączaniem trybu ręczny/automatyczny robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Steruje przełączaniem trybu ręczny/automatyczny robota
    * @param [in] mode 0-tryb automatyczny, 1-tryb ręczny
    * @return Kod błędu
    */
    int Mode(int mode);

Zamknięcie systemu operacyjnego robota
++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Zamyka system operacyjny robota
    * @return Kod błędu
    */
    int ShutDownRobotOS();

Przykład kodu
+++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button6_Click(object sender, EventArgse)
    {   
        int rtn = robot.ShutDownRobotOS();
        Console.WriteLine($"ShutDownRobotOS rtn is {rtn}");
    }

Ustawienie parametrów ponownego łączenia komunikacji z robotem
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia parametry ponownego łączenia komunikacji z robotem
    * @param [in] enable Czy włączyć true-włączone, false-niewłączone
    * @param [in] times Liczba prób ponownego połączenia
    * @param [in] period Odstęp czasu między próbami ponownego połączenia (milisekundy)
    */
    void SetReconnectParam(bool enable, int times, int period);

Przykład kodu
+++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnStandard_Click(object sender, EventArgs e)
    {
        Robot robot = new Robot();
        robot.SetReconnectParam(true, 100, 20000);//Parametry ponownego łączenia po przerwaniu
        robot.RPC("192.168.58.2"); 

        string ip = "";
        string version = "";
        byte state = 0;

        robot.GetSDKVersion(ref version);
        Console.WriteLine($"SDK version : {version}");
        robot.GetControllerIP(ref ip);
        Console.WriteLine($"controller ip : {ip}");

        robot.Mode(1);
        Thread.Sleep(1000);
        robot.DragTeachSwitch(1);
        int rtn = robot.IsInDragTeach(ref state);
        Console.WriteLine($"drag state : {state}");
        Thread.Sleep(3000);
        robot.DragTeachSwitch(0);
        Thread.Sleep(1000);
        robot.IsInDragTeach(ref state);
        Console.WriteLine($"drag state : {state}");
        Thread.Sleep(3000);
        robot.RobotEnable(0);
        Thread.Sleep(3000);
        robot.RobotEnable(1);

        robot.Mode(0);
        Thread.Sleep(1000);
        robot.Mode(1);
    }

Inicjalizacja parametrów logowania
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Inicjalizuje parametry logowania
    * @param [in] logType: Tryb wyjścia, DIRECT-wyjście bezpośrednie; BUFFER-wyjście buforowane; ASYNC-wyjście asynchroniczne
    * @param [in] logLevel: Poziom filtrowania logów, ERROR-błąd; WARNING-ostrzeżenie; INFO-informacja; DEBUG-debugowanie
    * @param [in] filePath: Ścieżka zapisu pliku, np. "D://Log/"
    * @param [in] saveFileNum: Liczba zapisywanych plików, jednoczesne przekroczenie liczby plików i dni przechowywania spowoduje usunięcie plików
    * @param [in] saveDays: Liczba dni przechowywania plików, jednoczesne przekroczenie liczby plików i dni przechowywania spowoduje usunięcie plików
    * @return Kod błędu
    */
    int LoggerInit(FrLogType logType = FrLogType.DIRECT, FrLogLevel logLevel = FrLogLevel.INFO, string filePath = "", int saveFileNum = 10, int saveDays = 10);

Ustawienie poziomu filtrowania logów
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia poziom filtrowania logów
    * @param [in] logLevel: Poziom filtrowania logów, ERROR-błąd; WARNING-ostrzeżenie; INFO-informacja; DEBUG-debugowanie
    * @return Kod błędu
    */
    int SetLoggerLevel(FrLogLevel logLevel);

Pobranie wersji oprogramowania robota
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Pobiera informacje o wersji oprogramowania robota
    * @param [out] robotModel Model robota
    * @param [out] webVersion Wersja web
    * @param [out] controllerVersion Wersja kontrolera
    * @return Kod błędu 
    */ 
    int GetSoftwareVersion(ref string robotModel, ref string webVersion, ref string controllerVersion);
    
Pobranie wersji sprzętowej robota
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Pobiera informacje o wersji sprzętowej robota
    * @param [out] ctrlBoxBoardVersion Wersja sprzętowa płyty nośnej skrzynki sterowniczej
    * @param [out] driver1Version Wersja sprzętowa napędu 1
    * @param [out] driver2Version Wersja sprzętowa napędu 2
    * @param [out] driver3Version Wersja sprzętowa napędu 3
    * @param [out] driver4Version Wersja sprzętowa napędu 4
    * @param [out] driver5Version Wersja sprzętowa napędu 5
    * @param [out] driver6Version Wersja sprzętowa napędu 6
    * @param [out] endBoardVersion Wersja sprzętowa płyty końcowej
    * @return Kod błędu 
    */ 
    int GetHardwareVersion(ref string ctrlBoxBoardVersion, ref string driver1Version, ref string driver2Version, ref string driver3Version,ref string driver4Version, ref string driver5Version, ref string driver6Version, ref string endBoardVersion);

Pobranie wersji oprogramowania sprzętowego robota
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Pobiera informacje o wersji oprogramowania sprzętowego robota
    * @param [out] ctrlBoxBoardVersion Wersja oprogramowania sprzętowego płyty nośnej skrzynki sterowniczej
    * @param [out] driver1Version Wersja oprogramowania sprzętowego napędu 1
    * @param [out] driver2Version Wersja oprogramowania sprzętowego napędu 2
    * @param [out] driver3Version Wersja oprogramowania sprzętowego napędu 3
    * @param [out] driver4Version Wersja oprogramowania sprzętowego napędu 4
    * @param [out] driver5Version Wersja oprogramowania sprzętowego napędu 5
    * @param [out] driver6Version Wersja oprogramowania sprzętowego napędu 6
    * @param [out] endBoardVersion Wersja oprogramowania sprzętowego płyty końcowej
    * @return Kod błędu 
    */ 
    int GetFirmwareVersion(ref string ctrlBoxBoardVersion, ref string driver1Version, ref string driver2Version, ref string driver3Version,ref string driver4Version, ref string driver5Version, ref string driver6Version, ref string endBoardVersion);

Przykład kodu
++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnGetVersions_Click(object sender, EventArgs e)
    {
        string[] ver = new string[20];
        int rtn = 0;
        rtn = robot.GetSoftwareVersion(ref ver[0], ref ver[1], ref ver[2]);
        rtn = robot.GetHardwareVersion(ref ver[3], ref ver[4], ref ver[5], ref ver[6], ref ver[7], ref ver[8], ref ver[9], ref ver[10]);
        rtn = robot.GetFirmwareVersion(ref ver[11], ref ver[12], ref ver[13], ref ver[14], ref ver[15], ref ver[16], ref ver[17], ref ver[18]);
        Console.WriteLine($"robotmodel  is: {ver[0]}");
        Console.WriteLine($"webVersion  is: {ver[1]}");
        Console.WriteLine($"controllerVersion  is: {ver[2]}");
        Console.WriteLine($"Hard ctrlBox Version  is: {ver[3]}");
        Console.WriteLine($"Hard driver1 Version  is: {ver[4]}");
        Console.WriteLine($"Hard driver2 Version  is: {ver[5]}");
        Console.WriteLine($"Hard driver3 Version  is: {ver[6]}");
        Console.WriteLine($"Hard driver4 Version  is: {ver[7]}");
        Console.WriteLine($"Hard driver5 Version  is: {ver[8]}");
        Console.WriteLine($"Hard driver6 Version  is: {ver[9]}");
        Console.WriteLine($"Hard end Version  is: {ver[10]}");
        Console.WriteLine($"Firm ctrlBox Version  is: {ver[11]}");
        Console.WriteLine($"Firm driver1 Version  is: {ver[12]}");
        Console.WriteLine($"Firm driver2 Version  is: {ver[13]}");
        Console.WriteLine($"Firm driver3 Version  is: {ver[14]}");
        Console.WriteLine($"Firm driver4 Version  is: {ver[15]}");
        Console.WriteLine($"Firm driver5 Version  is: {ver[16]}");
        Console.WriteLine($"Firm driver6 Version  is: {ver[17]}");
        Console.WriteLine($"Firm end Version  is: {ver[18]}");
    }