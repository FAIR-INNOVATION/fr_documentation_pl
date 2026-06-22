Wejścia/Wyjścia (IO) robota
============================

.. toctree::
    :maxdepth: 5

Ustawianie wyjścia cyfrowego szafy sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ustawia wyjście cyfrowe szafy sterowniczej
    * @param  [in] id  Numer IO, zakres [0~15]
    * @param  [in] status 0-wył., 1-wł.
    * @param  [in] smooth 0-niewygładzone, 1-wygładzone
    * @param  [in] block  0-blokujące, 1-nieblokujące
    * @return  Kod błędu
    */
    errno_t  SetDO(int id, uint8_t status, uint8_t smooth, uint8_t block);

Ustawianie wyjścia cyfrowego narzędzia
++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ustawia wyjście cyfrowe narzędzia
    * @param  [in] id  Numer IO, zakres [0~1]
    * @param  [in] status 0-wył., 1-wł.
    * @param  [in] smooth 0-niewygładzone, 1-wygładzone
    * @param  [in] block  0-blokujące, 1-nieblokujące
    * @return  Kod błędu
    */
    errno_t  SetToolDO(int id, uint8_t status, uint8_t smooth, uint8_t block);

Ustawianie wyjścia analogowego szafy sterowniczej
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ustawia wyjście analogowe szafy sterowniczej
    * @param  [in] id  Numer IO, zakres [0~1]
    * @param  [in] value Procent wartości prądu lub napięcia, zakres [0~100] odpowiada wartości prądu [0~20mA] lub napięcia [0~10V]
    * @param  [in] block  0-blokujące, 1-nieblokujące
    * @return  Kod błędu
    */
    errno_t  SetAO(int id, float value, uint8_t block);

Ustawianie wyjścia analogowego narzędzia
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ustawia wyjście analogowe narzędzia
    * @param  [in] id  Numer IO, zakres [0]
    * @param  [in] value Procent wartości prądu lub napięcia, zakres [0~100] odpowiada wartości prądu [0~20mA] lub napięcia [0~10V]
    * @param  [in] block  0-blokujące, 1-nieblokujące
    * @return  Kod błędu
    */
    errno_t  SetToolAO(int id, float value, uint8_t block);

Przykład kodu ustawiania wyjść cyfrowych i analogowych
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     int TestAODO(void)
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
         uint8_t status = 1;
         uint8_t smooth = 0;
         uint8_t block = 0;
         for (int i = 0; i < 16; i++)
         {
             robot.SetDO(i, status, smooth, block);
             robot.Sleep(300);
         }
         status = 0;
         for (int i = 0; i < 16; i++)
         {
             robot.SetDO(i, status, smooth, block);
             robot.Sleep(300);
         }
         status = 1;
         for (int i = 0; i < 2; i++)
         {
             robot.SetToolDO(i, status, smooth, block);
             robot.Sleep(1000);
         }
         status = 0;
         for (int i = 0; i < 2; i++)
         {
             robot.SetToolDO(i, status, smooth, block);
             robot.Sleep(1000);
         }
         for (int i = 0; i < 100; i++)
         {
             robot.SetAO(0, i * 40.96, block);
             robot.Sleep(30);
         }
         for (int i = 0; i < 100; i++)
         {
             robot.SetToolAO(0, i * 40.96, block);
             robot.Sleep(30);
         }
         robot.CloseRPC();
         return 0;
     }

Pobieranie wejścia cyfrowego szafy sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Pobiera wejście cyfrowe szafy sterowniczej
    * @param  [in] id  Numer IO, zakres [0~15]
    * @param  [in] block  0-blokujące, 1-nieblokujące
    * @param  [out] result  0-niski poziom, 1-wysoki poziom
    * @return  Kod błędu
    */
    errno_t  GetDI(int id, uint8_t block, uint8_t *result);

Pobieranie wejścia cyfrowego narzędzia
++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Pobiera wejście cyfrowe narzędzia
    * @param  [in] id  Numer IO, zakres [0~1]
    * @param  [in] block  0-blokujące, 1-nieblokujące
    * @param  [out] result  0-niski poziom, 1-wysoki poziom
    * @return  Kod błędu
    */
    errno_t  GetToolDI(int id, uint8_t block, uint8_t *result);

Pobieranie wejścia analogowego szafy sterowniczej
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Pobiera wejście analogowe szafy sterowniczej
    * @param  [in] id  Numer IO, zakres [0~1]
    * @param  [in] block  0-blokujące, 1-nieblokujące
    * @param  [out] result  Procent wartości prądu lub napięcia wejściowego, zakres [0~100] odpowiada wartości prądu [0~20mA] lub napięcia [0~10V]
    * @return  Kod błędu
    */
    errno_t  GetAI(int id, uint8_t block, float *result);

Pobieranie wejścia analogowego narzędzia
++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Pobiera wejście analogowe narzędzia
    * @param  [in] id  Numer IO, zakres [0]
    * @param  [in] block  0-blokujące, 1-nieblokujące
    * @param  [out] result  Procent wartości prądu lub napięcia wejściowego, zakres [0~100] odpowiada wartości prądu [0~20mA] lub napięcia [0~10V]
    * @return  Kod błędu
    */
    errno_t  GetToolAI(int id, uint8_t block, float *result);

Pobieranie stanu przycisku rejestracji punktu na końcówce robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Pobiera stan przycisku rejestracji punktu na końcówce robota
     * @param [out] state Stan przycisku, 0-wciśnięty, 1-zwolniony
     * @return Kod błędu
     */
    errno_t  GetAxlePointRecordBtnState(uint8_t *state);

Pobieranie stanu wyjścia DO na końcówce robota
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Pobiera stan wyjścia DO na końcówce robota
     * @param [out] do_state Stan wyjścia DO, do0~do1 odpowiadają bit1~bit2, zaczynając od bit0
     * @return Kod błędu
     */
    errno_t  GetToolDO(uint8_t *do_state);

Pobieranie stanu wyjścia DO sterownika robota
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Pobiera stan wyjścia DO sterownika robota
     * @param [out] do_state_h Stan wyjścia DO, co0~co7 odpowiadają bit0~bit7
     * @param [out] do_state_l Stan wyjścia DO, do0~do7 odpowiadają bit0~bit7
     * @return Kod błędu
     */
    errno_t  GetDO(uint8_t *do_state_h, uint8_t *do_state_l);

Przykład kodu pobierania stanów DI i DO robota
++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     int TestGetDIAI(void)
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
         uint8_t status = 1;
         uint8_t smooth = 0;
         uint8_t block = 0;
         uint8_t di = 0, tool_di = 0;
         float ai = 0.0, tool_ai = 0.0;
         float value = 0.0;
         robot.GetDI(0, block, &di);
         printf("di0:%u\n", di);
         tool_di = robot.GetToolDI(1, block, &tool_di);
         printf("tool_di1:%u\n", tool_di);
         robot.GetAI(0, block, &ai);
         printf("ai0:%f\n", ai);
         tool_ai = robot.GetToolAI(0, block, &tool_ai);
         printf("tool_ai0:%f\n", tool_ai);
         uint8_t _button_state = 0;
         robot.GetAxlePointRecordBtnState(&_button_state);
         printf("_button_state is: %u\n", _button_state);
         uint8_t tool_do_state = 0;
         robot.GetToolDO(&tool_do_state);
         printf("tool DO state is: %u\n", tool_do_state);
         uint8_t do_state_h = 0;
         uint8_t do_state_l = 0;
         robot.GetDO(&do_state_h, &do_state_l);
         printf("DO state high is: %u \n DO state low is: %u\n", do_state_h, do_state_l);
         robot.CloseRPC();
         return 0;
     }

Oczekiwanie na wejście cyfrowe szafy sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Oczekiwanie na wejście cyfrowe szafy sterowniczej
    * @param  [in] id  Numer IO, zakres [0~15]
    * @param  [in]  status 0-wył., 1-wł.
    * @param  [in]  max_time  Maksymalny czas oczekiwania, jednostka ms
    * @param  [in]  opt  Strategia po przekroczeniu czasu, 0-zatrzymaj program i wyświetl błąd przekroczenia czasu, 1-ignoruj błąd przekroczenia czasu i kontynuuj wykonywanie programu, 2-czekaj w nieskończoność
    * @return  Kod błędu
    */
    errno_t  WaitDI(int id, uint8_t status, int max_time, int opt);

Oczekiwanie na wiele wejść cyfrowych szafy sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Oczekiwanie na wiele wejść cyfrowych szafy sterowniczej
    * @param  [in] mode 0-logiczne I dla wielu wejść, 1-logiczne LUB dla wielu wejść
    * @param  [in] id  Numer IO, bit0~bit7 odpowiadają DI0~DI7, bit8~bit15 odpowiadają CI0~CI7
    * @param  [in]  status 0-wył., 1-wł.
    * @param  [in]  max_time  Maksymalny czas oczekiwania, jednostka ms
    * @param  [in]  opt  Strategia po przekroczeniu czasu, 0-zatrzymaj program i wyświetl błąd przekroczenia czasu, 1-ignoruj błąd przekroczenia czasu i kontynuuj wykonywanie programu, 2-czekaj w nieskończoność
    * @return  Kod błędu
    */
    errno_t  WaitMultiDI(int mode, int id, uint8_t status, int max_time, int opt);

Oczekiwanie na wejście cyfrowe narzędzia
++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Oczekiwanie na wejście cyfrowe narzędzia
    * @param  [in] id  Numer IO, zakres [0~1]
    * @param  [in]  status 0-wył., 1-wł.
    * @param  [in]  max_time  Maksymalny czas oczekiwania, jednostka ms
    * @param  [in]  opt  Strategia po przekroczeniu czasu, 0-zatrzymaj program i wyświetl błąd przekroczenia czasu, 1-ignoruj błąd przekroczenia czasu i kontynuuj wykonywanie programu, 2-czekaj w nieskończoność
    * @return  Kod błędu
    */
    errno_t  WaitToolDI(int id, uint8_t status, int max_time, int opt);

Oczekiwanie na wejście analogowe szafy sterowniczej
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Oczekiwanie na wejście analogowe szafy sterowniczej
    * @param  [in] id  Numer IO, zakres [0~1]
    * @param  [in]  sign 0-większe niż, 1-mniejsze niż
    * @param  [in]  value Procent wartości prądu lub napięcia wejściowego, zakres [0~100] odpowiada wartości prądu [0~20mA] lub napięcia [0~10V]
    * @param  [in]  max_time  Maksymalny czas oczekiwania, jednostka ms
    * @param  [in]  opt  Strategia po przekroczeniu czasu, 0-zatrzymaj program i wyświetl błąd przekroczenia czasu, 1-ignoruj błąd przekroczenia czasu i kontynuuj wykonywanie programu, 2-czekaj w nieskończoność
    * @return  Kod błędu
    */
    errno_t  WaitAI(int id, int sign, float value, int max_time, int opt);

Oczekiwanie na wejście analogowe narzędzia
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Oczekiwanie na wejście analogowe narzędzia
    * @param  [in] id  Numer IO, zakres [0]
    * @param  [in]  sign 0-większe niż, 1-mniejsze niż
    * @param  [in]  value Procent wartości prądu lub napięcia wejściowego, zakres [0~100] odpowiada wartości prądu [0~20mA] lub napięcia [0~10V]
    * @param  [in]  max_time  Maksymalny czas oczekiwania, jednostka ms
    * @param  [in]  opt  Strategia po przekroczeniu czasu, 0-zatrzymaj program i wyświetl błąd przekroczenia czasu, 1-ignoruj błąd przekroczenia czasu i kontynuuj wykonywanie programu, 2-czekaj w nieskończoność
    * @return  Kod błędu
    */
    errno_t  WaitToolAI(int id, int sign, float value, int max_time, int opt);

Przykład kodu oczekiwania na sygnały wejściowe cyfrowe i analogowe szafy sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionchanged:: C++SDK-v2.1.2.0

.. code-block:: c++
    :linenos:

     int TestWaitDIAI(void)
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
         uint8_t status = 1;
         uint8_t smooth = 0;
         uint8_t block = 0;
         uint8_t di = 0, tool_di = 0;
         float ai = 0.0, tool_ai = 0.0;
         float value = 0.0;
         rtn = robot.WaitDI(0, 1, 1000, 1);
         cout << "WaitDI over; rtn is: " << rtn << endl;
         robot.WaitMultiDI(1, 3, 3, 1000, 1);
         cout << "WaitDI over; rtn is: " << rtn << endl;
         robot.WaitToolDI(1, 1, 1000, 1);
         cout << "WaitDI over; rtn is: " << rtn << endl;
         robot.WaitAI(0, 0, 50, 1000, 1);
         cout << "WaitDI over; rtn is: " << rtn << endl;
         robot.WaitToolAI(0, 0, 50, 1000, 1);
         cout << "WaitDI over; rtn is: " << rtn << endl;
         robot.CloseRPC();
         return 0;
     }


Ustawianie resetowania wyjścia DO szafy sterowniczej po zatrzymaniu/wstrzymaniu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia resetowanie wyjścia DO szafy sterowniczej po zatrzymaniu/wstrzymaniu
    * @param [in] resetFlag 0-nie resetuj; 1-resetuj
    * @param [in] reloadFlag Czy przeładować po wznowieniu po wstrzymaniu, 0-nie ładuj; 1-ładuj
    * @return Kod błędu
    */
    errno_t SetOutputResetCtlBoxDO(int resetFlag, int reloadFlag = 0);

Ustawianie resetowania wyjścia AO szafy sterowniczej po zatrzymaniu/wstrzymaniu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia resetowanie wyjścia AO szafy sterowniczej po zatrzymaniu/wstrzymaniu
    * @param [in] resetFlag  0-nie resetuj; 1-resetuj
    * @param [in] reloadFlag Czy przeładować po wznowieniu po wstrzymaniu, 0-nie ładuj; 1-ładuj
    * @return Kod błędu
    */
    errno_t SetOutputResetCtlBoxAO(int resetFlag, int reloadFlag = 0);

Ustawianie resetowania wyjścia DO narzędzia końcowego po zatrzymaniu/wstrzymaniu
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia resetowanie wyjścia DO narzędzia końcowego po zatrzymaniu/wstrzymaniu
    * @param [in] resetFlag  0-nie resetuj; 1-resetuj
    * @param [in] reloadFlag Czy przeładować po wznowieniu po wstrzymaniu, 0-nie ładuj; 1-ładuj
    * @return Kod błędu
    */
    errno_t SetOutputResetAxleDO(int resetFlag, int reloadFlag = 0);

Ustawianie resetowania wyjścia AO narzędzia końcowego po zatrzymaniu/wstrzymaniu
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia resetowanie wyjścia AO narzędzia końcowego po zatrzymaniu/wstrzymaniu
    * @param [in] resetFlag  0-nie resetuj; 1-resetuj
    * @param [in] reloadFlag Czy przeładować po wznowieniu po wstrzymaniu, 0-nie ładuj; 1-ładuj
    * @return  Kod błędu
    */
    errno_t SetOutputResetAxleAO(int resetFlag, int reloadFlag = 0);

Ustawianie resetowania wyjścia rozszerzonego DO po zatrzymaniu/wstrzymaniu
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia resetowanie wyjścia rozszerzonego DO po zatrzymaniu/wstrzymaniu
    * @param [in] resetFlag  0-nie resetuj; 1-resetuj
    * @param [in] reloadFlag Czy przeładować po wznowieniu po wstrzymaniu, 0-nie ładuj; 1-ładuj
    * @return  Kod błędu
    */
    errno_t SetOutputResetExtDO(int resetFlag, int reloadFlag = 0);

Ustawianie resetowania wyjścia rozszerzonego AO po zatrzymaniu/wstrzymaniu
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia resetowanie wyjścia rozszerzonego AO po zatrzymaniu/wstrzymaniu
    * @param [in] resetFlag  0-nie resetuj; 1-resetuj
    * @param [in] reloadFlag Czy przeładować po wznowieniu po wstrzymaniu, 0-nie ładuj; 1-ładuj
    * @return  Kod błędu
    */
    errno_t SetOutputResetExtAO(int resetFlag, int reloadFlag = 0);

Ustawianie resetowania wyjścia SmartTool po zatrzymaniu/wstrzymaniu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia resetowanie wyjścia SmartTool po zatrzymaniu/wstrzymaniu
    * @param [in] resetFlag  0-nie resetuj; 1-resetuj
    * @param [in] reloadFlag Czy przeładować po wznowieniu po wstrzymaniu, 0-nie ładuj; 1-ładuj
    * @return  Kod błędu
    */
    errno_t SetOutputResetSmartToolDO(int resetFlag, int reloadFlag = 0);

Przykład kodu resetowania wyjść po zatrzymaniu/wstrzymaniu programu LUA
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    int TestDOReset(void)
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
    for (int i = 0; i < 16; i++)
    {
        robot.SetDO(i, 1, 0, 0);
        robot.Sleep(200);
    }
    int resetFlag = 0;
    int resumeReloadFlag = 0;
    rtn = robot.SetOutputResetCtlBoxDO(resetFlag, resumeReloadFlag);
    robot.SetOutputResetCtlBoxAO(resetFlag, resumeReloadFlag);
    robot.SetOutputResetAxleDO(resetFlag, resumeReloadFlag);
    robot.SetOutputResetAxleAO(resetFlag, resumeReloadFlag);
    robot.SetOutputResetExtDO(resetFlag, resumeReloadFlag);
    robot.SetOutputResetExtAO(resetFlag, resumeReloadFlag);
    robot.SetOutputResetSmartToolDO(resetFlag, resumeReloadFlag);
    robot.ProgramLoad("/fruser/test.lua");
    robot.ProgramRun();
    robot.Sleep(2000);
    robot.PauseMotion();
    robot.Sleep(2000);
    robot.ResumeMotion();
    robot.Sleep(2000);
    robot.CloseRPC();
    return 0;
    }

Ustawianie funkcji konfigurowalnych portów CI szafy sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia funkcje konfigurowalnych portów CI szafy sterowniczej
    * @param [in] config Kody funkcji CI0-CI7;
    * 0-brak;1-sukces rozpoczęcia łuku;2-gotowość spawarki;3-wykrywanie przenośnika;4-wstrzymanie;5-wznowienie;6-uruchomienie;7-zatrzymanie;
    8-wstrzymanie/wznowienie;9-uruchomienie/zatrzymanie;10-przeciąganie nożne;11-przejazd do punktu początkowego zadania;12-przełączanie ręczny/automatyczny;
    13-sukces lokalizacji drutu spawalniczego;14-przerwanie ruchu;15-uruchomienie programu głównego;16-uruchomienie przewijania do tyłu;17-potwierdzenie uruchomienia;
    18-sygnał detekcji fotoelektrycznej X;19-sygnał detekcji fotoelektrycznej Y;20-sygnał zewnętrznego awaryjnego zatrzymania 1;21-sygnał zewnętrznego awaryjnego zatrzymania 2;
    22-tryb redukcji poziomu 1;23-tryb redukcji poziomu 2;24-tryb redukcji poziomu 3 (zatrzymanie);25-wznowienie spawania;26-zakończenie spawania;
    27-włączenie wspomaganego przeciągania;28-wyłączenie wspomaganego przeciągania;29-włączenie/wyłączenie wspomaganego przeciągania;30-wyczyszczenie wszystkich błędów;
    31-przełączanie ręczny/automatyczny (poziom wysoki/niski);32-włączenie;33-wyłączenie;34-włączenie/wyłączenie (zbocze narastające/opadające);35-rozpoczęcie/zakończenie śledzenia punktowego
    * @return Kod błędu
    */
    errno_t SetDIConfig(int config[8]);

Pobieranie funkcji konfigurowalnych portów CI szafy sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera funkcje konfigurowalnych portów CI szafy sterowniczej
    * @param [in] config Kody funkcji CI0-CI7;
    * 0-brak;1-sukces rozpoczęcia łuku;2-gotowość spawarki;3-wykrywanie przenośnika;4-wstrzymanie;5-wznowienie;6-uruchomienie;7-zatrzymanie;
    8-wstrzymanie/wznowienie;9-uruchomienie/zatrzymanie;10-przeciąganie nożne;11-przejazd do punktu początkowego zadania;12-przełączanie ręczny/automatyczny;
    13-sukces lokalizacji drutu spawalniczego;14-przerwanie ruchu;15-uruchomienie programu głównego;16-uruchomienie przewijania do tyłu;17-potwierdzenie uruchomienia;
    18-sygnał detekcji fotoelektrycznej X;19-sygnał detekcji fotoelektrycznej Y;20-sygnał zewnętrznego awaryjnego zatrzymania 1;21-sygnał zewnętrznego awaryjnego zatrzymania 2;
    22-tryb redukcji poziomu 1;23-tryb redukcji poziomu 2;24-tryb redukcji poziomu 3 (zatrzymanie);25-wznowienie spawania;26-zakończenie spawania;
    27-włączenie wspomaganego przeciągania;28-wyłączenie wspomaganego przeciągania;29-włączenie/wyłączenie wspomaganego przeciągania;30-wyczyszczenie wszystkich błędów;
    31-przełączanie ręczny/automatyczny (poziom wysoki/niski);32-włączenie;33-wyłączenie;34-włączenie/wyłączenie (zbocze narastające/opadające);35-rozpoczęcie/zakończenie śledzenia punktowego
    * @return Kod błędu
    */
    errno_t GetDIConfig(int config[8]);

Ustawianie funkcji konfigurowalnych portów CO szafy sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia funkcje konfigurowalnych portów CO szafy sterowniczej
    * @param [out] config Kody funkcji CO0-CO7;
    * 0-brak;1-błąd robota;2-robot w ruchu;3-uruchamianie/zatrzymywanie natryskiwania;4-czyszczenie pistoletu natryskowego;5-sygnał podawania gazu;6-sygnał rozpoczęcia łuku;7-podawanie drutu impulsowe;
    8-podawanie drutu wsteczne;9-port wejściowy JOB 1;10-port wejściowy JOB 2;11-port wejściowy JOB 3;12-sterowanie uruchamianiem/zatrzymywaniem przenośnika;13-robot wstrzymany;14-osiągnięcie punktu początkowego zadania;
    15-osiągnięcie obszaru interferencji;16-sterowanie uruchamianiem/zatrzymywaniem lokalizacji drutu spawalniczego;17-robot zakończył uruchomienie;18-uruchomienie/zatrzymanie programu;19-tryb automatyczny/ręczny;20-sygnał wyjściowy awaryjnego zatrzymania 1-bezpieczeństwo;
    21-sygnał wyjściowy awaryjnego zatrzymania 2-bezpieczeństwo;22-uruchomienie/zatrzymanie programu skryptowego LUA;23-wyjście stanu bezpieczeństwa-bezpieczeństwo;24-wyjście stanu zatrzymania ochronnego-bezpieczeństwo;
    25-robot w ruchu-bezpieczeństwo;26-tryb redukcji robota-bezpieczeństwo;27-tryb nieredukcji robota-bezpieczeństwo;28-robot niezatrzymany;29-błąd robota-błąd punktu instrukcji;
    30-błąd robota-błąd sterownika;31-błąd robota-błąd przekroczenia miękkiego ograniczenia;32-błąd robota-błąd kolizji;33-błąd robota-błąd liczby aktywnych stacji podrzędnych;
    34-błąd robota-błąd stacji podrzędnej;35-błąd robota-błąd IO;36-błąd robota-błąd chwytaka;37-błąd robota-błąd pliku;38-błąd robota-błąd osobliwej pozy i orientacji;
    39-błąd robota-błąd komunikacji ze sterownikiem;40-błąd robota-błąd parametru;41-błąd robota-błąd przekroczenia miękkiego ograniczenia osi zewnętrznej;42-ostrzeżenie robota-ostrzeżenie;
    43-ostrzeżenie robota-ostrzeżenie drzwi bezpieczeństwa;44-ostrzeżenie robota-ostrzeżenie ruchu;45-ostrzeżenie robota-ostrzeżenie obszaru interferencji;46-ostrzeżenie robota-ostrzeżenie ściany bezpieczeństwa;
    47-stan włączenia;48-podnoszenie automatyczne po przerwaniu połączenia;49-ostrzeżenie interferencji prostopadłościan 1;50-ostrzeżenie interferencji prostopadłościan 2;51-ostrzeżenie interferencji prostopadłościan 3;52-ostrzeżenie interferencji prostopadłościan 4;
    * @return Kod błędu
    */
    errno_t SetDOConfig(int config[8]);

Pobieranie funkcji konfigurowalnych portów CO szafy sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera funkcje konfigurowalnych portów CO szafy sterowniczej
    * @param [out] config Kody funkcji CO0-CO7;
    * 0-brak;1-błąd robota;2-robot w ruchu;3-uruchamianie/zatrzymywanie natryskiwania;4-czyszczenie pistoletu natryskowego;5-sygnał podawania gazu;6-sygnał rozpoczęcia łuku;7-podawanie drutu impulsowe;
    8-podawanie drutu wsteczne;9-port wejściowy JOB 1;10-port wejściowy JOB 2;11-port wejściowy JOB 3;12-sterowanie uruchamianiem/zatrzymywaniem przenośnika;13-robot wstrzymany;14-osiągnięcie punktu początkowego zadania;
    15-osiągnięcie obszaru interferencji;16-sterowanie uruchamianiem/zatrzymywaniem lokalizacji drutu spawalniczego;17-robot zakończył uruchomienie;18-uruchomienie/zatrzymanie programu;19-tryb automatyczny/ręczny;20-sygnał wyjściowy awaryjnego zatrzymania 1-bezpieczeństwo;
    21-sygnał wyjściowy awaryjnego zatrzymania 2-bezpieczeństwo;22-uruchomienie/zatrzymanie programu skryptowego LUA;23-wyjście stanu bezpieczeństwa-bezpieczeństwo;24-wyjście stanu zatrzymania ochronnego-bezpieczeństwo;
    25-robot w ruchu-bezpieczeństwo;26-tryb redukcji robota-bezpieczeństwo;27-tryb nieredukcji robota-bezpieczeństwo;28-robot niezatrzymany;29-błąd robota-błąd punktu instrukcji;
    30-błąd robota-błąd sterownika;31-błąd robota-błąd przekroczenia miękkiego ograniczenia;32-błąd robota-błąd kolizji;33-błąd robota-błąd liczby aktywnych stacji podrzędnych;
    34-błąd robota-błąd stacji podrzędnej;35-błąd robota-błąd IO;36-błąd robota-błąd chwytaka;37-błąd robota-błąd pliku;38-błąd robota-błąd osobliwej pozy i orientacji;
    39-błąd robota-błąd komunikacji ze sterownikiem;40-błąd robota-błąd parametru;41-błąd robota-błąd przekroczenia miękkiego ograniczenia osi zewnętrznej;42-ostrzeżenie robota-ostrzeżenie;
    43-ostrzeżenie robota-ostrzeżenie drzwi bezpieczeństwa;44-ostrzeżenie robota-ostrzeżenie ruchu;45-ostrzeżenie robota-ostrzeżenie obszaru interferencji;46-ostrzeżenie robota-ostrzeżenie ściany bezpieczeństwa;
    47-stan włączenia;48-podnoszenie automatyczne po przerwaniu połączenia;49-ostrzeżenie interferencji prostopadłościan 1;50-ostrzeżenie interferencji prostopadłościan 2;51-ostrzeżenie interferencji prostopadłościan 3;52-ostrzeżenie interferencji prostopadłościan 4;
    * @return Kod błędu
    */
    errno_t GetDOConfig(int config[8]);

Ustawianie funkcji konfigurowalnych portów End-CI końcówki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia funkcje konfigurowalnych portów End-CI końcówki
    * @param [in] config Kody funkcji End CI0-CI1;
    * 0-brak;1-przełącznik narzędzia do przeciągania;2-sygnał rejestracji punktu;3-przełączanie ręczny/automatyczny (sygnał impulsowy);4-uruchamianie/zatrzymywanie rejestracji TPD;5-wstrzymanie ruchu;
    6-wznowienie ruchu;7-uruchomienie;8-zatrzymanie;9-wstrzymanie/wznowienie;10-uruchomienie/zatrzymanie;11-włączenie wspomaganego przeciągania przez czujnik siły;12-wyłączenie wspomaganego przeciągania przez czujnik siły;
    13-włączenie/wyłączenie wspomaganego przeciągania przez czujnik siły;14-sygnał detekcji laserowej X;15-sygnał detekcji laserowej Y;16-ruch PTP do punktu początkowego zadania;17-przerwanie ruchu, zatrzymanie bieżącego ruchu zgodnie z sygnałem;
    18-uruchomienie programu głównego;19-uruchomienie przewijania do tyłu;20-potwierdzenie uruchomienia;21-wznowienie spawania;22-zakończenie spawania;23-wyczyszczenie błędu;24-przełączanie ręczny/automatyczny (poziom wysoki/niski)
    25-włączenie;26-wyłączenie;27-włączenie/wyłączenie;28-sygnał uruchamiania/zatrzymywania śledzenia serwo laserowego;
    * @return Kod błędu
    */
    errno_t SetToolDIConfig(int config[2]);

Pobieranie funkcji konfigurowalnych portów End-CI końcówki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera funkcje konfigurowalnych portów End-CI końcówki
    * @param [out] config Kody funkcji End CI0-CI1;
    * 0-brak;1-przełącznik narzędzia do przeciągania;2-sygnał rejestracji punktu;3-przełączanie ręczny/automatyczny (sygnał impulsowy);4-uruchamianie/zatrzymywanie rejestracji TPD;5-wstrzymanie ruchu;
    6-wznowienie ruchu;7-uruchomienie;8-zatrzymanie;9-wstrzymanie/wznowienie;10-uruchomienie/zatrzymanie;11-włączenie wspomaganego przeciągania przez czujnik siły;12-wyłączenie wspomaganego przeciągania przez czujnik siły;
    13-włączenie/wyłączenie wspomaganego przeciągania przez czujnik siły;14-sygnał detekcji laserowej X;15-sygnał detekcji laserowej Y;16-ruch PTP do punktu początkowego zadania;17-przerwanie ruchu, zatrzymanie bieżącego ruchu zgodnie z sygnałem;
    18-uruchomienie programu głównego;19-uruchomienie przewijania do tyłu;20-potwierdzenie uruchomienia;21-wznowienie spawania;22-zakończenie spawania;23-wyczyszczenie błędu;24-przełączanie ręczny/automatyczny (poziom wysoki/niski)
    25-włączenie;26-wyłączenie;27-włączenie/wyłączenie;28-sygnał uruchamiania/zatrzymywania śledzenia serwo laserowego;
    * @return Kod błędu
    */
    errno_t GetToolDIConfig(int config[2]);

Ustawianie stanu aktywnego konfigurowalnych CI szafy sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia stan aktywny konfigurowalnych CI szafy sterowniczej
    * @param [in] config Stan aktywny portów CI0-CI7; 0-aktywny wysoki poziom; 1-aktywny niski poziom
    * @return Kod błędu
    */
    errno_t SetDIConfigLevel(int config[8]);

Pobieranie stanu aktywnego konfigurowalnych CI szafy sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera stan aktywny konfigurowalnych CI szafy sterowniczej
    * @param [out] config Stan aktywny portów CI0-CI7; 0-aktywny wysoki poziom; 1-aktywny niski poziom
    * @return Kod błędu
    */
    errno_t GetDIConfigLevel(int config[8]);

Ustawianie stanu aktywnego konfigurowalnych CO szafy sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia stan aktywny konfigurowalnych CO szafy sterowniczej
    * @param [in] config Stan aktywny portów CO0-CO7; 0-aktywny wysoki poziom; 1-aktywny niski poziom
    * @return Kod błędu
    */
    errno_t SetDOConfigLevel(int config[8]);

Pobieranie stanu aktywnego konfigurowalnych CO szafy sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera stan aktywny konfigurowalnych CO szafy sterowniczej
    * @param [out] config Stan aktywny portów CO0-CO7; 0-aktywny wysoki poziom; 1-aktywny niski poziom
    * @return Kod błędu
    */
    errno_t GetDOConfigLevel(int config[8]);

Ustawianie stanu aktywnego konfigurowalnych CI końcówki
+++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia stan aktywny konfigurowalnych CI końcówki
    * @param [in] config Stan aktywny portów CI0-CI1; 0-aktywny wysoki poziom; 1-aktywny niski poziom
    * @return Kod błędu
    */
    errno_t SetToolDIConfigLevel(int config[2]);

Pobieranie stanu aktywnego konfigurowalnych CI końcówki
+++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera stan aktywny konfigurowalnych CI końcówki
    * @param [out] config Stan aktywny portów CI0-CI1; 0-aktywny wysoki poziom; 1-aktywny niski poziom
    * @return Kod błędu
    */
    errno_t GetToolDIConfigLevel(int config[2]);

Ustawianie stanu aktywnego standardowych DI szafy sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia stan aktywny standardowych DI szafy sterowniczej
    * @param [in] config Stan aktywny portów DI0-DI7; 0-aktywny wysoki poziom; 1-aktywny niski poziom
    * @return Kod błędu
    */
    errno_t SetStandardDILevel(int config[8]);

Pobieranie stanu aktywnego standardowych DI szafy sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera stan aktywny standardowych DI szafy sterowniczej
    * @param [out] config Stan aktywny portów DI0-DI7; 0-aktywny wysoki poziom; 1-aktywny niski poziom
    * @return Kod błędu
    */
    errno_t GetStandardDILevel(int config[8]);

Ustawianie stanu aktywnego standardowych DO szafy sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia stan aktywny standardowych DO szafy sterowniczej
    * @param [in] config Stan aktywny portów DO0-DO7; 0-aktywny wysoki poziom; 1-aktywny niski poziom
    * @return Kod błędu
    */
    errno_t SetStandardDOLevel(int config[8]);

Pobieranie stanu aktywnego standardowych DO szafy sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera stan aktywny standardowych DO szafy sterowniczej
    * @param [out] config Stan aktywny portów DO0-DO7; 0-aktywny wysoki poziom; 1-aktywny niski poziom
    * @return Kod błędu
    */
    errno_t GetStandardDOLevel(int config[8]);

Przykład kodu konfiguracji IO robota
++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestIOConfig()
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
        int setDIConfig[8] = { 1, 2, 3, 4, 5, 6, 7, 8 };
        int getDIConfig[8] = { 0 };
        rtn = robot.SetDIConfig(setDIConfig);
        printf("SetDIConfig rtn is %d\n", rtn);
        rtn = robot.GetDIConfig(getDIConfig);
        printf("GetDIConfig rtn is %d, value is %d %d %d %d %d %d %d %d \n", rtn,
            getDIConfig[0], getDIConfig[1], getDIConfig[2], getDIConfig[3], getDIConfig[4], getDIConfig[5], getDIConfig[6], getDIConfig[7]);
        int setDOConfig[8] = { 9, 10, 11, 12, 13, 14, 15, 16 };
        int getDOConfig[8] = { 0 };
        rtn = robot.SetDOConfig(setDOConfig);
        printf("SetDOConfig rtn is %d\n", rtn);
        rtn = robot.GetDOConfig(getDOConfig);
        printf("GetDOConfig rtn is %d, value is %d %d %d %d %d %d %d %d \n", rtn,
            getDOConfig[0], getDOConfig[1], getDOConfig[2], getDOConfig[3], getDOConfig[4], getDOConfig[5], getDOConfig[6], getDOConfig[7]);
        int setToolDIConfig[2] = { 17, 18 };
        int getToolDIConfig[2] = { 0 };
        rtn = robot.SetToolDIConfig(setToolDIConfig);
        printf("SetToolDIConfig rtn is %d\n", rtn);
        rtn = robot.GetToolDIConfig(getToolDIConfig);
        printf("GetToolDIConfig rtn is %d, value is %d %d \n", rtn, getToolDIConfig[0], getToolDIConfig[1]);
        int setDIConfigLevel[8] = { 1, 1, 1, 1, 0, 0, 0, 0 };
        int getDIConfigLevel[8] = { 0 };
        rtn = robot.SetDIConfigLevel(setDIConfigLevel);
        printf("SetDIConfigLevel rtn is %d\n", rtn);
        rtn = robot.GetDIConfigLevel(getDIConfigLevel);
        printf("GetDIConfigLevel rtn is %d, value is %d %d %d %d %d %d %d %d \n", rtn,
            getDIConfigLevel[0], getDIConfigLevel[1], getDIConfigLevel[2], getDIConfigLevel[3], getDIConfigLevel[4], getDIConfigLevel[5], getDIConfigLevel[6], getDIConfigLevel[7]);
        int setDOConfigLevel[8] = { 0, 0, 0, 0, 1, 1, 1, 1 };
        int getDOConfigLevel[8] = { 0 };
        rtn = robot.SetDOConfigLevel(setDOConfigLevel);
        printf("SetDOConfigLevel rtn is %d\n", rtn);
        rtn = robot.GetDOConfigLevel(getDOConfigLevel);
        printf("GetDOConfigLevel rtn is %d, value is %d %d %d %d %d %d %d %d \n", rtn,
            getDOConfigLevel[0], getDOConfigLevel[1], getDOConfigLevel[2], getDOConfigLevel[3], getDOConfigLevel[4], getDOConfigLevel[5], getDOConfigLevel[6], getDOConfigLevel[7]);
        int setToolDIConfigLevel[2] = { 1, 0 };
        int getToolDIConfigLevel[2] = { 0 };
        rtn = robot.SetToolDIConfigLevel(setToolDIConfigLevel);
        printf("SetToolDIConfigLevel rtn is %d\n", rtn);
        rtn = robot.GetToolDIConfigLevel(getToolDIConfigLevel);
        printf("GetToolDIConfigLevel rtn is %d, value is %d %d \n", rtn, getToolDIConfigLevel[0], getToolDIConfigLevel[1]);
        int setStandardDILevel[8] = { 1, 1, 1, 1, 0, 0, 0, 0 };
        int getStandardDILevel[8] = { 0 };
        rtn = robot.SetStandardDILevel(setStandardDILevel);
        printf("SetStandardDILevel rtn is %d\n", rtn);
        rtn = robot.GetStandardDILevel(getStandardDILevel);
        printf("GetStandardDILevel rtn is %d, value is %d %d %d %d %d %d %d %d \n", rtn,
            getStandardDILevel[0], getStandardDILevel[1], getStandardDILevel[2], getStandardDILevel[3], getStandardDILevel[4], getStandardDILevel[5], getStandardDILevel[6], getStandardDILevel[7]);
        int setStandardDOLevel[8] = { 0, 0, 0, 0, 1, 1, 1, 1 };
        int getStandardDOLevel[8] = { 0 };
        rtn = robot.SetStandardDOLevel(setStandardDOLevel);
        printf("SetStandardDOLevel rtn is %d\n", rtn);
        rtn = robot.GetStandardDOLevel(getStandardDOLevel);
        printf("GetStandsrdDOLevel rtn is %d, value is %d %d %d %d %d %d %d %d \n", rtn,
            getStandardDOLevel[0], getStandardDOLevel[1], getStandardDOLevel[2], getStandardDOLevel[3], getStandardDOLevel[4], getStandardDOLevel[5], getStandardDOLevel[6], getStandardDOLevel[7]);
        robot.Sleep(2000);
        robot.CloseRPC();
        robot.Sleep(1000);
        return 0;
    }