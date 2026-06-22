Podstawy robota
===============

.. toctree:: 
    :maxdepth: 5

Instancja robota
++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Konstruktor klasy interfejsu robota
    */
    FRRobot();

Nawiązanie komunikacji z kontrolerem
++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Nawiązuje komunikację z kontrolerem robota
    * @param  [in] ip  Adres IP kontrolera, domyślnie fabrycznie 192.168.58.2
    * @return Kod błędu
    */
    errno_t RPC(const char *ip);

Zerwanie komunikacji z kontrolerem
+++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Zrywa komunikację z kontrolerem robota
     * @return Kod błędu
     */
    errno_t CloseRPC();

Sprawdzenie numeru wersji SDK
+++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Sprawdza numer wersji SDK
    * @param  [out] version   Numer wersji SDK
    * @return  Kod błędu
    */  
    errno_t GetSDKVersion(char *version);

Pobranie adresu IP kontrolera
+++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Pobiera adres IP kontrolera
    * @param  [out] ip  Adres IP kontrolera
    * @return  Kod błędu
    */
    errno_t GetControllerIP(char *ip);

Sterowanie wejściem lub wyjściem robota z trybu przeciągania nauczania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Steruje wejściem lub wyjściem robota z trybu przeciągania nauczania
    * @param  [in] state 0-wyjście z trybu przeciągania nauczania, 1-wejście w tryb przeciągania nauczania
    * @return  Kod błędu
    */
    errno_t DragTeachSwitch(uint8_t state);

Sprawdzenie, czy robot jest w trybie przeciągania
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Sprawdza, czy robot jest w trybie przeciągania nauczania
    * @param  [out] state 0-nie w trybie przeciągania nauczania, 1-w trybie przeciągania nauczania
    * @return  Kod błędu
    */
    errno_t IsInDragTeach(uint8_t *state);

Sterowanie załączeniem lub odłączeniem robota
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Steruje załączeniem lub odłączeniem robota. Po włączeniu zasilania robot domyślnie automatycznie się załącza.
    * @param  [in] state  0-odłączenie, 1-załączenie
    * @return  Kod błędu
    */
    errno_t RobotEnable(uint8_t state);

Sterowanie przełączaniem trybu ręczny/automatyczny robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Steruje przełączaniem trybu ręczny/automatyczny robota
    * @param [in] mode 0-tryb automatyczny, 1-tryb ręczny
    * @return Kod błędu
    */
    errno_t Mode(int mode);

Zamknięcie systemu operacyjnego robota
++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.1-3.8.1

.. code-block:: c++
    :linenos:

    /**
    * @brief Zamyka system operacyjny robota
    * @return Kod błędu
    */
    errno_t ShutDownRobotOS();

Ustawienie parametrów ponownego łączenia komunikacji z robotem
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia parametry ponownego łączenia komunikacji z robotem
    * @param [in] enable Włączenie ponownego łączenia w przypadku awarii sieci true-włączone false-niewłączone
    * @param [in] reconnectTime Czas ponownego połączenia, jednostka ms
    * @param [in] period Okres ponawiania połączenia, jednostka ms
    * @return Kod błędu
    */
    errno_t SetReConnectParam(bool enable, int reconnectTime = 30000, int period = 50);

Zamknięcie systemu operacyjnego robota
++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Zamyka system operacyjny robota
    * @return Kod błędu
    */
    int ShutDownRobotOS();

Inicjalizacja parametrów logowania
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.2.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Inicjalizuje parametry logowania;
    * @param output_model: Tryb wyjścia, 0-wyjście bezpośrednie; 1-wyjście buforowane; 2-wyjście asynchroniczne;
    * @param file_path: Ścieżka zapisu pliku + nazwa, maksymalna długość 256, nazwa musi mieć formę xxx.log, np. /home/fr/linux/fairino.log;
    * @param file_num: Liczba plików do przechowywania rotacyjnego, 1~20. Maksymalny rozmiar pojedynczego pliku 50 MB;
    * @return errno_t Kod błędu;
    */
    errno_t LoggerInit(int output_model = 0, std::string file_path = "", int file_num = 5);

Ustawienie poziomu filtrowania logów
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.2.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia poziom filtrowania logów;
    * @param lvl: Wartość poziomu filtrowania, im mniejsza wartość, tym mniej logów jest wypisywanych. Wartość domyślna to 1. 1-błąd, 2-ostrzeżenie, 3-informacja, 4-debugowanie;
    */
    void SetLoggerLevel(int lvl = 1);

Przykład kodu podstawowego sterowania robotem
+++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestRobotCtrl(void)
    {
            ROBOT_STATE_PKG pkg = {};
            FRRobot robot;
            robot.LoggerInit();
            robot.SetLoggerLevel(1);
            int rtn = robot.RPC("192.168.58.2");
            robot.SetReConnectParam(true, 30000, 500);
            char ip[64] = "";
            char version[64] = "";
            uint8_t state;
            robot.GetSDKVersion(version);
            printf("SDK version:%s\n", version);
            robot.GetControllerIP(ip);
            printf("controller ip:%s\n", ip);
            robot.Mode(1);
            robot.Sleep(1000);
            robot.DragTeachSwitch(1);
            robot.Sleep(1000);
            robot.IsInDragTeach(&state);
            printf("drag state :%u\n", state);
            robot.Sleep(3000);
            robot.DragTeachSwitch(0);
            robot.Sleep(1000);
            robot.IsInDragTeach(&state);
            printf("drag state :%u\n", state);
            robot.Sleep(3000);
            robot.RobotEnable(0);
            robot.Sleep(3000);
            robot.RobotEnable(1);
            robot.Mode(0);
            robot.Sleep(1000);
            robot.Mode(1);
            robot.Sleep(3000);
            robot.ShutDownRobotOS();
            robot.CloseRPC();
            return 0;
    }

Przykład kodu pobierania wersji oprogramowania robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera wersję oprogramowania robota
    * @param[out] robotModel Model robota
    * @param[out] webversion Wersja web
    * @param[out] controllerVersion Wersja kontrolera
    * @return Kod błędu
    */
    errno_t GetSoftwareVersion(char robotModel[64], char webVersion[64], char controllerVersion[64]);

Pobranie wersji sprzętowej robota
+++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera wersję sprzętową robota
    * @param[out] ctrlBoxBoardversion Wersja sprzętowa płyty nośnej skrzynki sterowniczej
    * @param[out] driver1version Wersja sprzętowa napędu 1
    * @param[out] driver2version Wersja sprzętowa napędu 2
    * @param[out] driver3version Wersja sprzętowa napędu 3
    * @param[out] driver4version Wersja sprzętowa napędu 4
    * @param[out] driver5version Wersja sprzętowa napędu 5
    * @param[out] driver6version Wersja sprzętowa napędu 6
    * @param[out] endBoardversion Wersja sprzętowa płyty końcowej
    */
    errno_t GetHardwareVersion(char ctrlBoxBoardversion[128], char driver1version[128], char driver2version[128], char driver3version[128], char driver4version[128], char driver5version[128], char driver6version[128], char endBoardversion[128]);

Pobranie wersji oprogramowania sprzętowego robota
+++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera wersję oprogramowania sprzętowego robota
    * @param[out] ctrlBoxBoardversion Wersja oprogramowania sprzętowego płyty nośnej skrzynki sterowniczej
    * @param[out] driver1version Wersja oprogramowania sprzętowego napędu 1
    * @param[out] driver2version Wersja oprogramowania sprzętowego napędu 2
    * @param[out] driver3version Wersja oprogramowania sprzętowego napędu 3
    * @param[out] driver4version Wersja oprogramowania sprzętowego napędu 4
    * @param[out] driver5version Wersja oprogramowania sprzętowego napędu 5
    * @param[out] driver6version Wersja oprogramowania sprzętowego napędu 6
    * @param[out] endBoardversion Wersja oprogramowania sprzętowego płyty końcowej
    */
    errno_t GetFirmwareVersion(char ctrlBoxBoardversion[128], char driver1version[128], char driver2version[128], char driver3version[128], char driver4version[128], char driver5version[128], char driver6version[128], char endBoardversion[128]);

Przykład kodu pobierania wersji oprogramowania i oprogramowania sprzętowego robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestGetVersions(void)
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
         char robotModel[64] = { 0 };
         char webversion[64] = { 0 };
         char controllerVersion[64] = { 0 };
         char ctrlBoxBoardversion[128] = { 0 };
         char driver1version[128] = { 0 };
         char driver2version[128] = { 0 };
         char driver3version[128] = { 0 };
         char driver4version[128] = { 0 };
         char driver5version[128] = { 0 };
         char driver6version[128] = { 0 };
         char endBoardversion[128] = { 0 };
         rtn = robot.GetSoftwareVersion(robotModel, webversion, controllerVersion);
         printf("Getsoftwareversion rtn is: %d\n", rtn);
         printf("robotmodel is: %s, webversion is: %s, controllerVersion is: %s \n\n", robotModel, webversion, controllerVersion);
         rtn = robot.GetHardwareVersion(ctrlBoxBoardversion, driver1version, driver2version, driver3version, driver4version, driver5version, driver6version, endBoardversion);
         printf("GetHardwareversion rtn is: %d\n", rtn);
         printf("GetHardwareversion get hardware versoin is: %s, %s, %s, %s, %s, %s, %s, %s\n\n", ctrlBoxBoardversion, driver1version, driver2version, driver3version, driver4version, driver5version, driver6version, endBoardversion);
         rtn = robot.GetFirmwareVersion(ctrlBoxBoardversion, driver1version, driver2version, driver3version, driver4version, driver5version, driver6version, endBoardversion);
         printf("GetFirmwareversion rtn is: %d\n", rtn);
         printf("GetHardwareversion get hardware versoin is: %s, %s, %s, %s, %s, %s, %s, %s\n\n", ctrlBoxBoardversion, driver1version, driver2version, driver3version, driver4version, driver5version, driver6version, endBoardversion);
         robot.CloseRPC();
         return 0;
     }