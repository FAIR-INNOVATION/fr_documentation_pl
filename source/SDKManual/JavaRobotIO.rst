Wejścia/Wyjścia (IO) robota
============================

.. toctree::
    :maxdepth: 5

Ustawianie wyjścia cyfrowego szafy sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Ustawia wyjście cyfrowe szafy sterowniczej
    * @param  [in] id  Numer IO, zakres [0~15]
    * @param  [in] status 0-wył., 1-wł.
    * @param  [in] smooth 0-niewygładzone, 1-wygładzone
    * @param  [in] block  0-blokujące, 1-nieblokujące
    * @return  Kod błędu
    */
    int SetDO(int id, int status, int smooth, int block);

Ustawianie wyjścia cyfrowego narzędzia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Ustawia wyjście cyfrowe narzędzia
    * @param  [in] id  Numer IO, zakres [0~1]
    * @param  [in] status 0-wył., 1-wł.
    * @param  [in] smooth 0-niewygładzone, 1-wygładzone
    * @param  [in] block  0-blokujące, 1-nieblokujące
    * @return  Kod błędu
    */
    int SetToolDO(int id, int status, int smooth, int block);

Ustawianie wyjścia analogowego szafy sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Ustawia wyjście analogowe szafy sterowniczej
    * @param  [in] id  Numer IO, zakres [0~1]
    * @param  [in] value Procent wartości prądu lub napięcia, zakres [0~100] odpowiada wartości prądu [0~20mA] lub napięcia [0~10V]
    * @param  [in] block  0-blokujące, 1-nieblokujące
    * @return  Kod błędu
    */
    int SetAO(int id, double value, int block);

Ustawianie wyjścia analogowego narzędzia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Ustawia wyjście analogowe narzędzia
    * @param  [in] id  Numer IO, zakres [0]
    * @param  [in] value Procent wartości prądu lub napięcia, zakres [0~100] odpowiada wartości prądu [0~20mA] lub napięcia [0~10V]
    * @param  [in] block  0-blokujące, 1-nieblokujące
    * @return  Kod błędu
    */
    int SetToolAO(int id, double value, int block);

Przykład kodu ustawiania wyjść cyfrowych i analogowych
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestAODO(Robot robot)
    {

        int status = 1;
        int smooth = 0;
        int block = 0;

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
            robot.SetAO(0, i, block);
            robot.Sleep(30);
        }

        for (int i = 0; i < 100; i++)
        {
            robot.SetToolAO(0, i, block);
            robot.Sleep(30);
        }

        robot.CloseRPC();
        return 0;
    }

Pobieranie wejścia cyfrowego szafy sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Pobiera wejście cyfrowe szafy sterowniczej
    * @param  [in] id  Numer IO, zakres [0~15]
    * @param  [in] block  0-blokujące, 1-nieblokujące
    * @param  [out] level  0-niski poziom, 1-wysoki poziom
    * @return  Kod błędu
    */
    int GetDI(int id, int block, int[] level);

Pobieranie wejścia cyfrowego narzędzia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Pobiera wejście cyfrowe narzędzia
    * @param  [in] id  Numer IO, zakres [0~1]
    * @param  [in] block  0-blokujące, 1-nieblokujące
    * @param  [out] level 0-niski poziom, 1-wysoki poziom
    * @return  Kod błędu
    */
    int GetToolDI(int id, int block, int[] level);

Pobieranie wejścia analogowego szafy sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Pobiera wejście analogowe szafy sterowniczej
    * @param  [in] id  Numer IO, zakres [0~1]
    * @param  [in] block  0-blokujące, 1-nieblokujące
    * @param  [out] persent Procent wartości prądu lub napięcia wejściowego, zakres [0~100] odpowiada wartości prądu [0~20mA] lub napięcia [0~10V]
    * @return  Kod błędu
    */
    int GetAI(int id, int block, double[] persent)

Pobieranie wejścia analogowego narzędzia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Pobiera wejście analogowe narzędzia
    * @param  [in] id  Numer IO, zakres [0]
    * @param  [in] block  0-blokujące, 1-nieblokujące
    * @param  [out] persent Procent wartości prądu lub napięcia wejściowego, zakres [0~100] odpowiada wartości prądu [0~20mA] lub napięcia [0~10V]
    * @return  Kod błędu
    */
    int GetToolAI(int id, int block, double[] persent)

Pobieranie stanu przycisku rejestracji punktu na końcówce robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Pobiera stan przycisku rejestracji punktu na końcówce robota
    * @param  [out] state Stan przycisku, 0-wciśnięty, 1-zwolniony
    * @return  Kod błędu
    */
    int GetAxlePointRecordBtnState(int[] state)

Pobieranie stanu wyjścia DO na końcówce robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Pobiera stan wyjścia DO na końcówce robota
    * @param  [out] do_state Stan wyjścia DO, do0~do1 odpowiadają bit1~bit2, zaczynając od bit0
    * @return  Kod błędu
    */
    int GetToolDO(int[] do_state)

Pobieranie stanu wyjścia DO sterownika robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Pobiera stan wyjścia DO sterownika robota
    * @param  [out] do_state_h Stan wyjścia DO, co0~co7 odpowiadają bit0~bit7
    * @param  [out] do_state_l Stan wyjścia DO, do0~do7 odpowiadają bit0~bit7
    * @return  Kod błędu
    */
    int GetDO(int[] do_state_h, int[] do_state_l)

Przykład kodu pobierania stanów DI i DO robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestGetDIAI(Robot robot)
    {
        int status = 1;
        int smooth = 0;
        int block = 0;
        int[] di =new int[]{0}, tool_di =new int[] {0};
        double[] ai =new double[] {0}, tool_ai = new double[]{0};
        double value = 0.0;


        robot.GetDI(0, block, di);
        System.out.println("di0:"+di[0]);

        robot.GetToolDI(1, block, tool_di);
        System.out.println("tool_di1:"+ tool_di[0]);

        robot.GetAI(0, block, ai);
        System.out.println("ai0:"+ ai[0]);

        robot.GetToolAI(0, block, tool_ai);
        System.out.println("tool_ai0:"+ tool_ai[0]);

        int[] _button_state=new int[]{0};
        robot.GetAxlePointRecordBtnState(_button_state);
        System.out.println("_button_state is: "+ _button_state[0]);

        int[] tool_do_state=new int[]{0};
        robot.GetToolDO(tool_do_state);
        System.out.println("tool DO state is: "+ tool_do_state[0]);

        int[] do_state_h=new int[]{0};
        int[] do_state_l=new int[]{0};
        robot.GetDO(do_state_h, do_state_l);
        System.out.println("DO state high is: "+do_state_h[0]+", DO state low is: "+ do_state_l[0]);

        return 0;
    }

Oczekiwanie na wejście cyfrowe szafy sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Oczekiwanie na wejście cyfrowe szafy sterowniczej
    * @param  [in] id  Numer IO, zakres [0~15]
    * @param  [in] status 0-wył., 1-wł.
    * @param  [in] max_time  Maksymalny czas oczekiwania, jednostka ms
    * @param  [in] opt  Strategia po przekroczeniu czasu, 0-zatrzymaj program i wyświetl błąd przekroczenia czasu, 1-ignoruj błąd przekroczenia czasu i kontynuuj wykonywanie programu, 2-czekaj w nieskończoność
    * @return  Kod błędu
    */
    int WaitDI(int id, int status, int max_time, int opt);

Oczekiwanie na wiele wejść cyfrowych szafy sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Oczekiwanie na wiele wejść cyfrowych szafy sterowniczej
    * @param  [in] mode 0-logiczne I dla wielu wejść, 1-logiczne LUB dla wielu wejść
    * @param  [in] id  Numer IO, bit0~bit7 odpowiadają DI0~DI7, bit8~bit15 odpowiadają CI0~CI7
    * @param  [in] status 0-wył., 1-wł.
    * @param  [in] max_time  Maksymalny czas oczekiwania, jednostka ms
    * @param  [in] opt  Strategia po przekroczeniu czasu, 0-zatrzymaj program i wyświetl błąd przekroczenia czasu, 1-ignoruj błąd przekroczenia czasu i kontynuuj wykonywanie programu, 2-czekaj w nieskończoność
    * @return  Kod błędu
    */
    int WaitMultiDI(int mode, int id, int status, int max_time, int opt);

Oczekiwanie na wejście cyfrowe narzędzia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Oczekiwanie na wejście cyfrowe narzędzia
    * @param  [in] id  Numer IO, zakres [0~1]
    * @param  [in] status 0-wył., 1-wł.
    * @param  [in] max_time  Maksymalny czas oczekiwania, jednostka ms
    * @param  [in] opt  Strategia po przekroczeniu czasu, 0-zatrzymaj program i wyświetl błąd przekroczenia czasu, 1-ignoruj błąd przekroczenia czasu i kontynuuj wykonywanie programu, 2-czekaj w nieskończoność
    * @return  Kod błędu
    */
    int WaitToolDI(int id, int status, int max_time, int opt);

Oczekiwanie na wejście analogowe szafy sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Oczekiwanie na wejście analogowe szafy sterowniczej
    * @param  [in] id  Numer IO, zakres [0~1]
    * @param  [in] sign 0-większe niż, 1-mniejsze niż
    * @param  [in] value Procent wartości prądu lub napięcia wejściowego, zakres [0~100] odpowiada wartości prądu [0~20mA] lub napięcia [0~10V]
    * @param  [in] max_time  Maksymalny czas oczekiwania, jednostka ms
    * @param  [in] opt  Strategia po przekroczeniu czasu, 0-zatrzymaj program i wyświetl błąd przekroczenia czasu, 1-ignoruj błąd przekroczenia czasu i kontynuuj wykonywanie programu, 2-czekaj w nieskończoność
    * @return  Kod błędu
    */
    int WaitAI(int id, int sign, double value, int max_time, int opt);

Oczekiwanie na wejście analogowe narzędzia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Oczekiwanie na wejście analogowe narzędzia
    * @param  [in] id  Numer IO, zakres [0]
    * @param  [in] sign 0-większe niż, 1-mniejsze niż
    * @param  [in] value Procent wartości prądu lub napięcia wejściowego, zakres [0~100] odpowiada wartości prądu [0~20mA] lub napięcia [0~10V]
    * @param  [in] max_time  Maksymalny czas oczekiwania, jednostka ms
    * @param  [in] opt  Strategia po przekroczeniu czasu, 0-zatrzymaj program i wyświetl błąd przekroczenia czasu, 1-ignoruj błąd przekroczenia czasu i kontynuuj wykonywanie programu, 2-czekaj w nieskończoność
    * @return  Kod błędu
    */
    int WaitToolAI(int id, int sign, double value, int max_time, int opt);

Przykład kodu oczekiwania na sygnały wejściowe cyfrowe i analogowe szafy sterowniczej
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestWaitDIAI(Robot robot)
    {
        int rtn=-1;

        int status = 1;
        int smooth = 0;
        int block = 0;
        int di = 0, tool_di = 0;
        double ai = 0.0, tool_ai = 0.0;
        double value = 0.0;

        rtn = robot.WaitDI(0, 1, 1000, 1);
        System.out.println("WaitDI over; rtn is: "+ rtn);

        robot.WaitMultiDI(1, 3, 3, 1000, 1);
        System.out.println("WaitDI over; rtn is: "+ rtn);

        robot.WaitToolDI(1, 1, 1000, 1);
        System.out.println("WaitDI over; rtn is: " + rtn);

        robot.WaitAI(0, 0, 50, 1000, 1);
        System.out.println("WaitDI over; rtn is: " + rtn);

        robot.WaitToolAI(0, 0, 50, 1000, 1);
        System.out.println("WaitDI over; rtn is: " + rtn);
        return 0;
    }

Ustawianie resetowania wyjścia DO szafy sterowniczej po zatrzymaniu/wstrzymaniu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia resetowanie wyjścia DO szafy sterowniczej po zatrzymaniu/wstrzymaniu
    * @param resetFlag  0-nie resetuj; 1-resetuj
    * @param reloadFlag Czy przeładować po wznowieniu po wstrzymaniu, 0-nie ładuj; 1-ładuj
    * @return Kod błędu
    */
    public int SetOutputResetCtlBoxDO(int resetFlag, int reloadFlag)

Ustawianie resetowania wyjścia AO szafy sterowniczej po zatrzymaniu/wstrzymaniu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia resetowanie wyjścia AO szafy sterowniczej po zatrzymaniu/wstrzymaniu
    * @param resetFlag  0-nie resetuj; 1-resetuj
    * @param reloadFlag Czy przeładować po wznowieniu po wstrzymaniu, 0-nie ładuj; 1-ładuj
    * @return Kod błędu
    */
    public int SetOutputResetCtlBoxAO(int resetFlag, int reloadFlag)

Ustawianie resetowania wyjścia DO narzędzia końcowego po zatrzymaniu/wstrzymaniu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia resetowanie wyjścia DO narzędzia końcowego po zatrzymaniu/wstrzymaniu
    * @param resetFlag  0-nie resetuj; 1-resetuj
    * @param reloadFlag Czy przeładować po wznowieniu po wstrzymaniu, 0-nie ładuj; 1-ładuj
    * @return Kod błędu
    */
    public int SetOutputResetAxleDO(int resetFlag, int reloadFlag)

Ustawianie resetowania wyjścia AO narzędzia końcowego po zatrzymaniu/wstrzymaniu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia resetowanie wyjścia AO narzędzia końcowego po zatrzymaniu/wstrzymaniu
    * @param resetFlag  0-nie resetuj; 1-resetuj
    * @param reloadFlag Czy przeładować po wznowieniu po wstrzymaniu, 0-nie ładuj; 1-ładuj
    * @return Kod błędu
    */
    public int SetOutputResetAxleAO(int resetFlag, int reloadFlag)

Ustawianie resetowania wyjścia rozszerzonego DO po zatrzymaniu/wstrzymaniu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia resetowanie wyjścia rozszerzonego DO po zatrzymaniu/wstrzymaniu
    * @param resetFlag  0-nie resetuj; 1-resetuj
    * @param reloadFlag Czy przeładować po wznowieniu po wstrzymaniu, 0-nie ładuj; 1-ładuj
    * @return Kod błędu
    */
    public int SetOutputResetExtDO(int resetFlag, int reloadFlag)

Ustawianie resetowania wyjścia rozszerzonego AO po zatrzymaniu/wstrzymaniu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia resetowanie wyjścia rozszerzonego AO po zatrzymaniu/wstrzymaniu
    * @param resetFlag  0-nie resetuj; 1-resetuj
    * @param reloadFlag Czy przeładować po wznowieniu po wstrzymaniu, 0-nie ładuj; 1-ładuj
    * @return Kod błędu
    */
    public int SetOutputResetExtAO(int resetFlag, int reloadFlag)

Ustawianie resetowania wyjścia SmartTool po zatrzymaniu/wstrzymaniu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia resetowanie wyjścia SmartTool po zatrzymaniu/wstrzymaniu
    * @param resetFlag  0-nie resetuj; 1-resetuj
    * @param reloadFlag Czy przeładować po wznowieniu po wstrzymaniu, 0-nie ładuj; 1-ładuj
    * @return Kod błędu
    */
    public int SetOutputResetSmartToolDO(int resetFlag, int reloadFlag)

Przykład kodu resetowania wyjść po zatrzymaniu/wstrzymaniu programu LUA
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestDOReset(Robot robot)
    {
        for (int i = 0; i < 16; i++)
        {
            robot.SetDO(i, 1, 0, 0);
            robot.Sleep(200);
        }
        int resetFlag = 1;
        int resumeReloadFlag = 1;
        int rtn = robot.SetOutputResetCtlBoxDO(resetFlag, resumeReloadFlag);
        robot.SetOutputResetCtlBoxAO(resetFlag, resumeReloadFlag);
        robot.SetOutputResetAxleDO(resetFlag, resumeReloadFlag);
        robot.SetOutputResetAxleAO(resetFlag, resumeReloadFlag);
        robot.SetOutputResetExtDO(resetFlag, resumeReloadFlag);
        robot.SetOutputResetExtAO(resetFlag, resumeReloadFlag);
        robot.SetOutputResetSmartToolDO(resetFlag, resumeReloadFlag);
        robot.ProgramLoad("test.lua");
        robot.ProgramRun();
        robot.Sleep(2000);
        robot.PauseMotion();
        robot.Sleep(2000);
        robot.ResumeMotion();
        robot.Sleep(2000);
        robot.CloseRPC();
    }

Ustawianie funkcji konfigurowalnych portów CI szafy sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia funkcje konfigurowalnych portów CI szafy sterowniczej
    * @param config Kody funkcji CI0-CI7;
    * 0-brak;1-sukces rozpoczęcia łuku;2-gotowość spawarki;3-wykrywanie przenośnika;4-wstrzymanie;5-wznowienie;6-uruchomienie;7-zatrzymanie;
    8-wstrzymanie/wznowienie;9-uruchomienie/zatrzymanie;10-przeciąganie nożne;11-przejazd do punktu początkowego zadania;12-przełączanie ręczny/automatyczny;
    13-sukces lokalizacji drutu spawalniczego;14-przerwanie ruchu;15-uruchomienie programu głównego;16-uruchomienie przewijania do tyłu;17-potwierdzenie uruchomienia;
    18-sygnał detekcji fotoelektrycznej X;19-sygnał detekcji fotoelektrycznej Y;20-sygnał zewnętrznego awaryjnego zatrzymania 1;21-sygnał zewnętrznego awaryjnego zatrzymania 2;
    22-tryb redukcji poziomu 1;23-tryb redukcji poziomu 2;24-tryb redukcji poziomu 3 (zatrzymanie);25-wznowienie spawania;26-zakończenie spawania;
    27-włączenie wspomaganego przeciągania;28-wyłączenie wspomaganego przeciągania;29-włączenie/wyłączenie wspomaganego przeciągania;30-wyczyszczenie wszystkich błędów;
    31-przełączanie ręczny/automatyczny (poziom wysoki/niski);32-włączenie;33-wyłączenie;34-włączenie/wyłączenie (zbocze narastające/opadające);35-rozpoczęcie/zakończenie śledzenia punktowego
    * @return Kod błędu
    */
    public int SetDIConfig(int[] config)

Pobieranie funkcji konfigurowalnych portów CI szafy sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera funkcje konfigurowalnych portów CI szafy sterowniczej
    * @param config Kody funkcji CI0-CI7;
    * 0-brak;1-sukces rozpoczęcia łuku;2-gotowość spawarki;3-wykrywanie przenośnika;4-wstrzymanie;5-wznowienie;6-uruchomienie;7-zatrzymanie;
    8-wstrzymanie/wznowienie;9-uruchomienie/zatrzymanie;10-przeciąganie nożne;11-przejazd do punktu początkowego zadania;12-przełączanie ręczny/automatyczny;
    13-sukces lokalizacji drutu spawalniczego;14-przerwanie ruchu;15-uruchomienie programu głównego;16-uruchomienie przewijania do tyłu;17-potwierdzenie uruchomienia;
    18-sygnał detekcji fotoelektrycznej X;19-sygnał detekcji fotoelektrycznej Y;20-sygnał zewnętrznego awaryjnego zatrzymania 1;21-sygnał zewnętrznego awaryjnego zatrzymania 2;
    22-tryb redukcji poziomu 1;23-tryb redukcji poziomu 2;24-tryb redukcji poziomu 3 (zatrzymanie);25-wznowienie spawania;26-zakończenie spawania;
    27-włączenie wspomaganego przeciągania;28-wyłączenie wspomaganego przeciągania;29-włączenie/wyłączenie wspomaganego przeciągania;30-wyczyszczenie wszystkich błędów;
    31-przełączanie ręczny/automatyczny (poziom wysoki/niski);32-włączenie;33-wyłączenie;34-włączenie/wyłączenie (zbocze narastające/opadające);35-rozpoczęcie/zakończenie śledzenia punktowego
    * @return Kod błędu
    */
    public int GetDIConfig(int[] config)

Ustawianie funkcji konfigurowalnych portów CO szafy sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia funkcje konfigurowalnych portów CO szafy sterowniczej
    * @param config Kody funkcji CO0-CO7;
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
    public int SetDOConfig(int[] config)

Pobieranie funkcji konfigurowalnych portów CO szafy sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera funkcje konfigurowalnych portów CO szafy sterowniczej
    * @param config Kody funkcji CO0-CO7;
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
    public int GetDOConfig(int[] config)

Ustawianie funkcji konfigurowalnych portów End-CI końcówki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia funkcje konfigurowalnych portów End-CI końcówki
    * @param config Kody funkcji End CI0-CI1;
    * 0-brak;1-przełącznik narzędzia do przeciągania;2-sygnał rejestracji punktu;3-przełączanie ręczny/automatyczny (sygnał impulsowy);4-uruchamianie/zatrzymywanie rejestracji TPD;5-wstrzymanie ruchu;
    6-wznowienie ruchu;7-uruchomienie;8-zatrzymanie;9-wstrzymanie/wznowienie;10-uruchomienie/zatrzymanie;11-włączenie wspomaganego przeciągania przez czujnik siły;12-wyłączenie wspomaganego przeciągania przez czujnik siły;
    13-włączenie/wyłączenie wspomaganego przeciągania przez czujnik siły;14-sygnał detekcji laserowej X;15-sygnał detekcji laserowej Y;16-ruch PTP do punktu początkowego zadania;17-przerwanie ruchu, zatrzymanie bieżącego ruchu zgodnie z sygnałem;
    18-uruchomienie programu głównego;19-uruchomienie przewijania do tyłu;20-potwierdzenie uruchomienia;21-wznowienie spawania;22-zakończenie spawania;23-wyczyszczenie błędu;24-przełączanie ręczny/automatyczny (poziom wysoki/niski)
    25-włączenie;26-wyłączenie;27-włączenie/wyłączenie;28-sygnał uruchamiania/zatrzymywania śledzenia serwo laserowego;
    * @return Kod błędu
    */
    public int SetToolDIConfig(int[] config)

Pobieranie funkcji konfigurowalnych portów End-CI końcówki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera funkcje konfigurowalnych portów End-CI końcówki
    * @param config Kody funkcji End CI0-CI1;
    * 0-brak;1-przełącznik narzędzia do przeciągania;2-sygnał rejestracji punktu;3-przełączanie ręczny/automatyczny (sygnał impulsowy);4-uruchamianie/zatrzymywanie rejestracji TPD;5-wstrzymanie ruchu;
    6-wznowienie ruchu;7-uruchomienie;8-zatrzymanie;9-wstrzymanie/wznowienie;10-uruchomienie/zatrzymanie;11-włączenie wspomaganego przeciągania przez czujnik siły;12-wyłączenie wspomaganego przeciągania przez czujnik siły;
    13-włączenie/wyłączenie wspomaganego przeciągania przez czujnik siły;14-sygnał detekcji laserowej X;15-sygnał detekcji laserowej Y;16-ruch PTP do punktu początkowego zadania;17-przerwanie ruchu, zatrzymanie bieżącego ruchu zgodnie z sygnałem;
    18-uruchomienie programu głównego;19-uruchomienie przewijania do tyłu;20-potwierdzenie uruchomienia;21-wznowienie spawania;22-zakończenie spawania;23-wyczyszczenie błędu;24-przełączanie ręczny/automatyczny (poziom wysoki/niski)
    25-włączenie;26-wyłączenie;27-włączenie/wyłączenie;28-sygnał uruchamiania/zatrzymywania śledzenia serwo laserowego;
    * @return Kod błędu
    */
    public int GetToolDIConfig(int[] config)

Ustawianie stanu aktywnego konfigurowalnych CI szafy sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia stan aktywny konfigurowalnych CI szafy sterowniczej
    * @param config Stan aktywny portów CI0-CI7; 0-aktywny wysoki poziom; 1-aktywny niski poziom
    * @return Kod błędu
    */
    public int SetDIConfigLevel(int[] config)

Pobieranie stanu aktywnego konfigurowalnych CI szafy sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera stan aktywny konfigurowalnych CI szafy sterowniczej
    * @param config Stan aktywny portów CI0-CI7; 0-aktywny wysoki poziom; 1-aktywny niski poziom
    * @return Kod błędu
    */
    public int GetDIConfigLevel(int[] config)

Ustawianie stanu aktywnego konfigurowalnych CO szafy sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia stan aktywny konfigurowalnych CO szafy sterowniczej
    * @param config Stan aktywny portów CO0-CO7; 0-aktywny wysoki poziom; 1-aktywny niski poziom
    * @return Kod błędu
    */
    public int SetDOConfigLevel(int[] config)

Pobieranie stanu aktywnego konfigurowalnych CO szafy sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera stan aktywny konfigurowalnych CO szafy sterowniczej
    * @param config Stan aktywny portów CO0-CO7; 0-aktywny wysoki poziom; 1-aktywny niski poziom
    * @return Kod błędu
    */
    public int GetDOConfigLevel(int[] config)

Ustawianie stanu aktywnego konfigurowalnych CI końcówki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia stan aktywny konfigurowalnych CI końcówki
    * @param config Stan aktywny portów CI0-CI1; 0-aktywny wysoki poziom; 1-aktywny niski poziom
    * @return Kod błędu
    */
    public int SetToolDIConfigLevel(int[] config)

Pobieranie stanu aktywnego konfigurowalnych CI końcówki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera stan aktywny konfigurowalnych CI końcówki
    * @param config Stan aktywny portów CI0-CI1; 0-aktywny wysoki poziom; 1-aktywny niski poziom
    * @return Kod błędu
    */
    public int GetToolDIConfigLevel(int[] config)

Ustawianie stanu aktywnego standardowych DI szafy sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia stan aktywny standardowych DI szafy sterowniczej
    * @param config Stan aktywny portów DI0-DI7; 0-aktywny wysoki poziom; 1-aktywny niski poziom
    * @return Kod błędu
    */
    public int SetStandardDILevel(int[] config)

Pobieranie stanu aktywnego standardowych DI szafy sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera stan aktywny standardowych DI szafy sterowniczej
    * @param config Stan aktywny portów DI0-DI7; 0-aktywny wysoki poziom; 1-aktywny niski poziom
    * @return Kod błędu
    */
    public int GetStandardDILevel(int[] config)

Ustawianie stanu aktywnego standardowych DO szafy sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia stan aktywny standardowych DO szafy sterowniczej
    * @param config Stan aktywny portów DO0-DO7; 0-aktywny wysoki poziom; 1-aktywny niski poziom
    * @return Kod błędu
    */
    public int SetStandardDOLevel(int[] config)

Pobieranie stanu aktywnego standardowych DO szafy sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera stan aktywny standardowych DO szafy sterowniczej
    * @param config Stan aktywny portów DO0-DO7; 0-aktywny wysoki poziom; 1-aktywny niski poziom
    * @return Kod błędu
    */
    public int GetStandardDOLevel(int[] config)

Przykład kodu konfiguracji IO robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestIOConfig(Robot robot) {
        int[] setDIConfig = new int[]{1, 2, 3, 4, 5, 6, 7, 8};
        int[] getDIConfig = new int[8];
        int rtn = robot.SetDIConfig(setDIConfig);
        System.out.println("SetDIConfig rtn is " + rtn);
        rtn = robot.GetDIConfig(getDIConfig);
        System.out.println("GetDIConfig rtn is " + rtn + ", value is " +
            getDIConfig[0] + " " + getDIConfig[1] + " " + getDIConfig[2] + " " + getDIConfig[3] + " " +
            getDIConfig[4] + " " + getDIConfig[5] + " " + getDIConfig[6] + " " + getDIConfig[7]);

        int[] setDOConfig = new int[]{9, 10, 11, 12, 13, 14, 15, 16};
        int[] getDOConfig = new int[8];
        rtn = robot.SetDOConfig(setDOConfig);
        System.out.println("SetDOConfig rtn is " + rtn);
        rtn = robot.GetDOConfig(getDOConfig);
        System.out.println("GetDOConfig rtn is " + rtn + ", value is " +
            getDOConfig[0] + " " + getDOConfig[1] + " " + getDOConfig[2] + " " + getDOConfig[3] + " " +
            getDOConfig[4] + " " + getDOConfig[5] + " " + getDOConfig[6] + " " + getDOConfig[7]);

        int[] setToolDIConfig = new int[]{17, 18};
        int[] getToolDIConfig = new int[2];
        rtn = robot.SetToolDIConfig(setToolDIConfig);
        System.out.println("SetToolDIConfig rtn is " + rtn);
        rtn = robot.GetToolDIConfig(getToolDIConfig);
        System.out.println("GetToolDIConfig rtn is " + rtn + ", value is " + getToolDIConfig[0] + " " + getToolDIConfig[1]);

        int[] setDIConfigLevel = new int[]{1, 1, 1, 1, 0, 0, 0, 0};
        int[] getDIConfigLevel = new int[8];
        rtn = robot.SetDIConfigLevel(setDIConfigLevel);
        System.out.println("SetDIConfigLevel rtn is " + rtn);
        rtn = robot.GetDIConfigLevel(getDIConfigLevel);
        System.out.println("GetDIConfigLevel rtn is " + rtn + ", value is " +
            getDIConfigLevel[0] + " " + getDIConfigLevel[1] + " " + getDIConfigLevel[2] + " " + getDIConfigLevel[3] + " " +
            getDIConfigLevel[4] + " " + getDIConfigLevel[5] + " " + getDIConfigLevel[6] + " " + getDIConfigLevel[7]);

        int[] setDOConfigLevel = new int[]{0, 0, 0, 0, 1, 1, 1, 1};
        int[] getDOConfigLevel = new int[8];
        rtn = robot.SetDOConfigLevel(setDOConfigLevel);
        System.out.println("SetDOConfigLevel rtn is " + rtn);
        rtn = robot.GetDOConfigLevel(getDOConfigLevel);
        System.out.println("GetDOConfigLevel rtn is " + rtn + ", value is " +
            getDOConfigLevel[0] + " " + getDOConfigLevel[1] + " " + getDOConfigLevel[2] + " " + getDOConfigLevel[3] + " " +
            getDOConfigLevel[4] + " " + getDOConfigLevel[5] + " " + getDOConfigLevel[6] + " " + getDOConfigLevel[7]);

        int[] setToolDIConfigLevel = new int[]{1, 0};
        int[] getToolDIConfigLevel = new int[2];
        rtn = robot.SetToolDIConfigLevel(setToolDIConfigLevel);
        System.out.println("SetToolDIConfigLevel rtn is " + rtn);
        rtn = robot.GetToolDIConfigLevel(getToolDIConfigLevel);
        System.out.println("GetToolDIConfigLevel rtn is " + rtn + ", value is " + getToolDIConfigLevel[0] + " " + getToolDIConfigLevel[1]);

        int[] setStandardDILevel = new int[]{1, 1, 1, 1, 0, 0, 0, 0};
        int[] getStandardDILevel = new int[8];
        rtn = robot.SetStandardDILevel(setStandardDILevel);
        System.out.println("SetStandardDILevel rtn is " + rtn);
        rtn = robot.GetStandardDILevel(getStandardDILevel);
        System.out.println("GetStandardDILevel rtn is " + rtn + ", value is " +
            getStandardDILevel[0] + " " + getStandardDILevel[1] + " " + getStandardDILevel[2] + " " + getStandardDILevel[3] + " " +
            getStandardDILevel[4] + " " + getStandardDILevel[5] + " " + getStandardDILevel[6] + " " + getStandardDILevel[7]);

        int[] setStandardDOLevel = new int[]{0, 0, 0, 0, 1, 1, 1, 1};
        int[] getStandardDOLevel = new int[8];
        rtn = robot.SetStandardDOLevel(setStandardDOLevel);
        System.out.println("SetStandardDOLevel rtn is " + rtn);
        rtn = robot.GetStandardDOLevel(getStandardDOLevel);
        System.out.println("GetStandardDOLevel rtn is " + rtn + ", value is " +
            getStandardDOLevel[0] + " " + getStandardDOLevel[1] + " " + getStandardDOLevel[2] + " " + getStandardDOLevel[3] + " " +
            getStandardDOLevel[4] + " " + getStandardDOLevel[5] + " " + getStandardDOLevel[6] + " " + getStandardDOLevel[7]);

        robot.Sleep(2000);
        return 0;
    }