Wejścia/Wyjścia robota
======================

.. toctree:: 
    :maxdepth: 5

Ustawienie wyjścia cyfrowego skrzynki sterowniczej
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ustawia wyjście cyfrowe skrzynki sterowniczej
    * @param  [in] id  Numer I/O, zakres [0~15]
    * @param  [in] status 0-wył., 1-wł.
    * @param  [in] smooth 0-niewygładzone, 1-wygładzone
    * @param  [in] block  0-blokujące, 1-nieblokujące
    * @return  Kod błędu
    */
    int SetDO(int id, byte status, byte smooth, byte block); 

Ustawienie wyjścia cyfrowego narzędzia
++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ustawia wyjście cyfrowe narzędzia
    * @param  [in] id  Numer I/O, zakres [0~1]
    * @param  [in] status 0-wył., 1-wł.
    * @param  [in] smooth 0-niewygładzone, 1-wygładzone
    * @param  [in] block  0-blokujące, 1-nieblokujące
    * @return  Kod błędu
    */
    int SetToolDO(int id, byte status, byte smooth, byte block); 

Ustawienie wyjścia analogowego skrzynki sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ustawia wyjście analogowe skrzynki sterowniczej
    * @param  [in] id  Numer I/O, zakres [0~1]
    * @param  [in] value Procent wartości prądu lub napięcia, zakres [0~100] odpowiada wartości prądu [0~20mA] lub napięcia [0~10V]
    * @param  [in] block  0-blokujące, 1-nieblokujące
    * @return  Kod błędu
    */
    int SetAO(int id, float value, byte block); 

Ustawienie wyjścia analogowego narzędzia
++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ustawia wyjście analogowe narzędzia
    * @param  [in] id  Numer I/O, zakres [0]
    * @param  [in] value Procent wartości prądu lub napięcia, zakres [0~100] odpowiada wartości prądu [0~20mA] lub napięcia [0~10V]
    * @param  [in] block  0-blokujące, 1-nieblokujące
    * @return  Kod błędu
    */
    int SetToolAO(int id, float value, byte block);

Przykład kodu ustawiania wyjść cyfrowych i analogowych
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos: 

    private void button14_Click(object sender, EventArgs e)
    {
        byte status = 1;
        byte smooth = 0;
        byte block = 0;
        byte di = 0, tool_di = 0;
        float ai = 0.0f, tool_ai = 0.0f;
        float value = 0.0f;


        for (int i = 0; i < 16; i++)
        {
            robot.SetDO(i, status, smooth, block);
            Thread.Sleep(300);
        }

        status = 0;

        for (int i = 0; i < 16; i++)
        {
            robot.SetDO(i, status, smooth, block);
            Thread.Sleep(300);
        }

        status = 1;

        for (int i = 0; i < 2; i++)
        {
            robot.SetToolDO(i, status, smooth, block);
            Thread.Sleep(1000);
        }

        status = 0;

        for (int i = 0; i < 2; i++)
        {
            robot.SetToolDO(i, status, smooth, block);
            Thread.Sleep(1000);
        }

        for (int i = 0; i < 100; i++)
        {
            robot.SetAO(0, i, block);
            Thread.Sleep(30);
        }

        for (int i = 0; i < 100; i++)
        {
            robot.SetToolAO(0, i, block);
            Thread.Sleep(30);
        }

    }

Pobranie wejścia cyfrowego skrzynki sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera wejście cyfrowe skrzynki sterowniczej
    * @param  [in] id  Numer I/O, zakres [0~15]
    * @param  [in] block  0-blokujące, 1-nieblokujące
    * @param  [out] result  0-poziom niski, 1-poziom wysoki
    * @return  Kod błędu
    */   
    int GetDI(int id, byte block, ref byte level);

Pobranie wejścia cyfrowego narzędzia
++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera wejście cyfrowe narzędzia
    * @param  [in] id  Numer I/O, zakres [0~1]
    * @param  [in] block  0-blokujące, 1-nieblokujące
    * @param  [out] result  0-poziom niski, 1-poziom wysoki
    * @return  Kod błędu
    */   
    int GetToolDI(int id, byte block, ref byte level); 

Pobranie wejścia analogowego skrzynki sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera wejście analogowe skrzynki sterowniczej
    * @param  [in] id  Numer I/O, zakres [0~1]
    * @param  [in] block  0-blokujące, 1-nieblokujące
    * @param  [out] result  Procent wejściowej wartości prądu lub napięcia, zakres [0~100] odpowiada wartości prądu [0~20mA] lub napięcia [0~10V]
    * @return  Kod błędu
    */   
    int GetAI(int id, byte block, ref float persent); 

Pobranie wejścia analogowego narzędzia
++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera wejście analogowe narzędzia
    * @param  [in] id  Numer I/O, zakres [0]
    * @param  [in] block  0-blokujące, 1-nieblokujące
    * @param  [out] result  Procent wejściowej wartości prądu lub napięcia, zakres [0~100] odpowiada wartości prądu [0~20mA] lub napięcia [0~10V]
    * @return  Kod błędu
    */   
    int GetToolAI(int id, byte block, ref float persent); 

Pobranie stanu przycisku rejestracji punktu końcowego robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Pobiera stan przycisku rejestracji punktu końcowego robota
    * @param [out] state Stan przycisku, 0-naciśnięty, 1-zwolniony
    * @return Kod błędu 
    */ 
    int GetAxlePointRecordBtnState(ref byte state); 

Pobranie stanu wyjścia DO końcowego robota
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Pobiera stan wyjścia DO końcowego robota 
    * @param [out] do_state Stan wyjścia DO, do0~do1 odpowiadają bit1~bit2, zaczynając od bit0 
    * @return Kod błędu 
    */ 
    int GetToolDO(ref byte do_state);

Pobranie stanu wyjścia DO kontrolera robota
+++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Pobiera stan wyjścia DO kontrolera robota 
    * @param [out] do_state_h Stan wyjścia DO, co0~co7 odpowiadają bit0~bit7 
    * @param [out] do_state_l Stan wyjścia DO, do0~do7 odpowiadają bit0~bit7
    * @return Kod błędu 
    */ 
    int GetDO(ref int do_state_h, ref int do_state_l);   

Przykład kodu pobierania stanu DI, DO robota
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button15_Click(object sender, EventArgs e)
    {
        byte status = 1;
        byte smooth = 0;
        byte block = 0;
        byte di = 0, tool_di = 0;
        float ai = 0.0f, tool_ai = 0.0f;
        float value = 0.0f;

        robot.GetDI(0, block, ref di);
        Console.WriteLine($"di0: {di}");

        tool_di = (byte)robot.GetToolDI(1, block, ref tool_di);
        Console.WriteLine($"tool_di1: {tool_di}");

        robot.GetAI(0, block, ref ai);
        Console.WriteLine($"ai0: {ai}");

        tool_ai = robot.GetToolAI(0, block, ref tool_ai);
        Console.WriteLine($"tool_ai0: {tool_ai}");

        byte _button_state = 0;
        robot.GetAxlePointRecordBtnState(ref _button_state);
        Console.WriteLine($"_button_state is: {_button_state}");

        byte tool_do_state = 0;
        robot.GetToolDO(ref tool_do_state);
        Console.WriteLine($"tool DO state is: {tool_do_state}");

        int do_state_h = 0;
        int do_state_l = 0;
        robot.GetDO(ref do_state_h, ref do_state_l);
        Console.WriteLine($"DO state high is: {do_state_h}\n DO state low is: {do_state_l}");
    }

Oczekiwanie na wejście cyfrowe skrzynki sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Oczekuje na wejście cyfrowe skrzynki sterowniczej
    * @param  [in] id  Numer I/O, zakres [0~15]
    * @param  [in]  status 0-wył., 1-wł.
    * @param  [in]  max_time  Maksymalny czas oczekiwania, jednostka ms
    * @param  [in]  opt  Strategia po przekroczeniu limitu czasu, 0-program zatrzymuje się i informuje o przekroczeniu limitu, 1-ignoruj informację o przekroczeniu limitu i kontynuuj wykonanie programu, 2-czekaj w nieskończoność
    * @return  Kod błędu
    */
    int WaitDI(int id, byte status, int max_time, int opt); 

Oczekiwanie na wielokanałowe wejście cyfrowe skrzynki sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Oczekuje na wielokanałowe wejście cyfrowe skrzynki sterowniczej
    * @param  [in] mode 0-logiczne I dla wielu kanałów, 1-logiczne LUB dla wielu kanałów
    * @param  [in] id  Numer I/O, bit0~bit7 odpowiadają DI0~DI7, bit8~bit15 odpowiadają CI0~CI7
    * @param  [in]  status 0-wył., 1-wł.
    * @param  [in]  max_time  Maksymalny czas oczekiwania, jednostka ms
    * @param  [in]  opt  Strategia po przekroczeniu limitu czasu, 0-program zatrzymuje się i informuje o przekroczeniu limitu, 1-ignoruj informację o przekroczeniu limitu i kontynuuj wykonanie programu, 2-czekaj w nieskończoność
    * @return  Kod błędu
    */
    int WaitMultiDI(int mode, int id, byte status, int max_time, int opt); 

Oczekiwanie na wejście cyfrowe narzędzia
++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Oczekuje na wejście cyfrowe narzędzia
    * @param  [in] id  Numer I/O, zakres [0~1]
    * @param  [in]  status 0-wył., 1-wł.
    * @param  [in]  max_time  Maksymalny czas oczekiwania, jednostka ms
    * @param  [in]  opt  Strategia po przekroczeniu limitu czasu, 0-program zatrzymuje się i informuje o przekroczeniu limitu, 1-ignoruj informację o przekroczeniu limitu i kontynuuj wykonanie programu, 2-czekaj w nieskończoność
    * @return  Kod błędu
    */
    int WaitToolDI(int id, byte status, int max_time, int opt); 

Oczekiwanie na wejście analogowe skrzynki sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Oczekuje na wejście analogowe skrzynki sterowniczej
    * @param  [in] id  Numer I/O, zakres [0~1]
    * @param  [in]  sign 0-większe niż, 1-mniejsze niż
    * @param  [in]  value Procent wejściowej wartości prądu lub napięcia, zakres [0~100] odpowiada wartości prądu [0~20mA] lub napięcia [0~10V]
    * @param  [in]  max_time  Maksymalny czas oczekiwania, jednostka ms
    * @param  [in]  opt  Strategia po przekroczeniu limitu czasu, 0-program zatrzymuje się i informuje o przekroczeniu limitu, 1-ignoruj informację o przekroczeniu limitu i kontynuuj wykonanie programu, 2-czekaj w nieskończoność
    * @return  Kod błędu
    */
    int WaitAI(int id, int sign, float value, int max_time, int opt);   

Oczekiwanie na wejście analogowe narzędzia
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Oczekuje na wejście analogowe narzędzia
    * @param  [in] id  Numer I/O, zakres [0]
    * @param  [in]  sign 0-większe niż, 1-mniejsze niż
    * @param  [in]  value Procent wejściowej wartości prądu lub napięcia, zakres [0~100] odpowiada wartości prądu [0~20mA] lub napięcia [0~10V]
    * @param  [in]  max_time  Maksymalny czas oczekiwania, jednostka ms
    * @param  [in]  opt  Strategia po przekroczeniu limitu czasu, 0-program zatrzymuje się i informuje o przekroczeniu limitu, 1-ignoruj informację o przekroczeniu limitu i kontynuuj wykonanie programu, 2-czekaj w nieskończoność
    * @return  Kod błędu
    */
    int WaitToolAI(int id, int sign, float value, int max_time, int opt); 

Przykład kodu oczekiwania na sygnały wejściowe cyfrowe i analogowe skrzynki sterowniczej
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnIOTest_Click(object sender, EventArgs e)
    {
        byte status = 1;
        byte smooth = 0;
        byte block = 0;
        byte di = 0, tool_di = 0;
        float ai = 0.0f, tool_ai = 0.0f;
        float value = 0.0f;

        int rtn = robot.WaitDI(0, 1, 1000, 1);
        Console.WriteLine("WaitDI over; rtn is: " + rtn);

        robot.WaitMultiDI(1, 3, 3, 1000, 1);
        Console.WriteLine("WaitMultiDI over; rtn is: " + rtn);

        robot.WaitToolDI(1, 1, 1000, 1);
        Console.WriteLine("WaitToolDI over; rtn is: " + rtn);

        robot.WaitAI(0, 0, 50, 1000, 1);
        Console.WriteLine("WaitAI over; rtn is: " + rtn);

        robot.WaitToolAI(0, 0, 50, 1000, 1);
        Console.WriteLine("WaitToolAI over; rtn is: " + rtn);
    }
    
Ustawienie, czy wyjście DO skrzynki sterowniczej ma być resetowane po zatrzymaniu/wstrzymaniu
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia, czy wyjście DO skrzynki sterowniczej ma być resetowane po zatrzymaniu/wstrzymaniu
    * @param [in] resetFlag 0-nie resetuj; 1-resetuj
    * @param [in] reloadFlag Czy przeładować po wznowieniu wstrzymania, 0-nie ładuj; 1-ładuj
    * @return Kod błędu
    */
    public int SetOutputResetCtlBoxDO(int resetFlag, int reloadFlag);

Ustawienie, czy wyjście AO skrzynki sterowniczej ma być resetowane po zatrzymaniu/wstrzymaniu
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia, czy wyjście AO skrzynki sterowniczej ma być resetowane po zatrzymaniu/wstrzymaniu
    * @param [in] resetFlag 0-nie resetuj; 1-resetuj
    * @param [in] reloadFlag Czy przeładować po wznowieniu wstrzymania, 0-nie ładuj; 1-ładuj
    * @return Kod błędu
    */
    public int SetOutputResetCtlBoxAO(int resetFlag, int reloadFlag);

Ustawienie, czy wyjście DO narzędzia końcowego ma być resetowane po zatrzymaniu/wstrzymaniu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia, czy wyjście DO narzędzia końcowego ma być resetowane po zatrzymaniu/wstrzymaniu
    * @param [in] resetFlag 0-nie resetuj; 1-resetuj
    * @param [in] reloadFlag Czy przeładować po wznowieniu wstrzymania, 0-nie ładuj; 1-ładuj
    * @return Kod błędu
    */
    public int SetOutputResetAxleDO(int resetFlag, int reloadFlag);

Ustawienie, czy wyjście AO narzędzia końcowego ma być resetowane po zatrzymaniu/wstrzymaniu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia, czy wyjście AO narzędzia końcowego ma być resetowane po zatrzymaniu/wstrzymaniu
    * @param [in] resetFlag 0-nie resetuj; 1-resetuj
    * @param [in] reloadFlag Czy przeładować po wznowieniu wstrzymania, 0-nie ładuj; 1-ładuj
    * @return Kod błędu
    */
    public int SetOutputResetAxleAO(int resetFlag, int reloadFlag);

Ustawienie, czy wyjście rozszerzone DO ma być resetowane po zatrzymaniu/wstrzymaniu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia, czy wyjście rozszerzone DO ma być resetowane po zatrzymaniu/wstrzymaniu
    * @param [in] resetFlag 0-nie resetuj; 1-resetuj
    * @param [in] reloadFlag Czy przeładować po wznowieniu wstrzymania, 0-nie ładuj; 1-ładuj
    * @return  Kod błędu
    */
    public int SetOutputResetExtDO(int resetFlag, int reloadFlag);

Ustawienie, czy wyjście rozszerzone AO ma być resetowane po zatrzymaniu/wstrzymaniu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia, czy wyjście rozszerzone AO ma być resetowane po zatrzymaniu/wstrzymaniu
    * @param [in] resetFlag 0-nie resetuj; 1-resetuj
    * @param [in] reloadFlag Czy przeładować po wznowieniu wstrzymania, 0-nie ładuj; 1-ładuj
    * @return Kod błędu
    */
    public int SetOutputResetExtAO(int resetFlag, int reloadFlag);

Ustawienie, czy wyjście SmartTool ma być resetowane po zatrzymaniu/wstrzymaniu
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia, czy wyjście SmartTool ma być resetowane po zatrzymaniu/wstrzymaniu
    * @param [in] resetFlag 0-nie resetuj; 1-resetuj
    * @param [in] reloadFlag Czy przeładować po wznowieniu wstrzymania, 0-nie ładuj; 1-ładuj
    * @return Kod błędu
    */
    public int SetOutputResetSmartToolDO(int resetFlag, int reloadFlag);

Przykład kodu resetowania wyjść po zatrzymaniu/wstrzymaniu programu LUA
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public void TestDOReset()
    {
        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();

        for (int i = 0; i < 16; i++)
        {
            robot.SetDO(i, 1, 0, 0);
            Thread.Sleep(200);
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

        robot.ProgramLoad("/fruser/test.lua");
        robot.ProgramRun();

        Thread.Sleep(2000);
        robot.PauseMotion();
        Thread.Sleep(2000);
        robot.ResumeMotion();
        Thread.Sleep(2000);
    }

Ustawienie funkcji konfigurowalnego portu CI skrzynki sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia funkcję konfigurowalnego portu CI skrzynki sterowniczej
    * @param [in] config Kody funkcji CI0-CI7;
    * 0-brak;1-pomyślne zajarzenie łuku;2-gotowość spawarki;3-wykrywanie taśmociągu;4-wstrzymaj;5-wznów;6-uruchom;7-zatrzymaj;
    8-wstrzymaj/wznów;9-uruchom/zatrzymaj;10-przeciąganie nożne;11-przejdź do punktu początkowego zadania;12-przełączanie ręczny/automatyczny;
    13-pomyślne pozycjonowanie drutu spawalniczego;14-przerwanie ruchu;15-uruchom program główny;16-uruchom przewijanie wstecz;17-potwierdzenie uruchomienia;
    18-sygnał wykrywania fotoelektrycznego X;19-sygnał wykrywania fotoelektrycznego Y;20-sygnał wejściowy awaryjnego zatrzymania zewnętrznego 1;21-sygnał wejściowy awaryjnego zatrzymania zewnętrznego 2;
    22-tryb redukcji pierwszego poziomu;23-tryb redukcji drugiego poziomu;24-tryb redukcji trzeciego poziomu (zatrzymanie);25-wznów spawanie;26-zakończ spawanie;
    27-włącz pomocnicze przeciąganie;28-wyłącz pomocnicze przeciąganie;29-włącz/wyłącz pomocnicze przeciąganie;30-wyczyść wszystkie błędy;
    31-przełączanie ręczny/automatyczny (poziom wysoki/niski);32-załącz;33-odłącz;34-załącz/odłącz (zbocze narastające/opadające);35-rozpocznij/zakończ śledzenie punktowe
    * @return Kod błędu
    */
    public int SetDIConfig(int[] config)

Pobranie funkcji konfigurowalnego portu CI skrzynki sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Pobiera funkcję konfigurowalnego portu CI skrzynki sterowniczej
    * @param [in] config Kody funkcji CI0-CI7;
    * 0-brak;1-pomyślne zajarzenie łuku;2-gotowość spawarki;3-wykrywanie taśmociągu;4-wstrzymaj;5-wznów;6-uruchom;7-zatrzymaj;
    8-wstrzymaj/wznów;9-uruchom/zatrzymaj;10-przeciąganie nożne;11-przejdź do punktu początkowego zadania;12-przełączanie ręczny/automatyczny;
    13-pomyślne pozycjonowanie drutu spawalniczego;14-przerwanie ruchu;15-uruchom program główny;16-uruchom przewijanie wstecz;17-potwierdzenie uruchomienia;
    18-sygnał wykrywania fotoelektrycznego X;19-sygnał wykrywania fotoelektrycznego Y;20-sygnał wejściowy awaryjnego zatrzymania zewnętrznego 1;21-sygnał wejściowy awaryjnego zatrzymania zewnętrznego 2;
    22-tryb redukcji pierwszego poziomu;23-tryb redukcji drugiego poziomu;24-tryb redukcji trzeciego poziomu (zatrzymanie);25-wznów spawanie;26-zakończ spawanie;
    27-włącz pomocnicze przeciąganie;28-wyłącz pomocnicze przeciąganie;29-włącz/wyłącz pomocnicze przeciąganie;30-wyczyść wszystkie błędy;
    31-przełączanie ręczny/automatyczny (poziom wysoki/niski);32-załącz;33-odłącz;34-załącz/odłącz (zbocze narastające/opadające);35-rozpocznij/zakończ śledzenie punktowe
    * @return Kod błędu
    */
    public int GetDIConfig(out int[] config)

Ustawienie funkcji konfigurowalnego portu CO skrzynki sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia funkcję konfigurowalnego portu CO skrzynki sterowniczej
    * @param [out] config Kody funkcji CO0-CO7;
    * 0-brak;1-błąd robota;2-robot w ruchu;3-uruchom/zatrzymaj natryskiwanie;4-czyszczenie pistoletu natryskowego;5-sygnał podawania gazu;6-sygnał zajarzenia łuku;7-podawanie drutu punktowe;
    8-podawanie drutu wsteczne;9-wejście JOB 1;10-wejście JOB 2;11-wejście JOB 3;12-sterowanie uruchomieniem/zatrzymaniem taśmociągu;13-robot wstrzymany;14-osiągnięto punkt początkowy zadania;
    15-osiągnięto strefę interferencji;16-sterowanie uruchomieniem/zatrzymaniem pozycjonowania drutu spawalniczego;17-robot zakończył uruchamianie;18-zatrzymanie uruchomienia programu;19-tryb automatyczny/ręczny;20-sygnał wyjściowy awaryjnego zatrzymania 1-bezpieczeństwo;
    21-sygnał wyjściowy awaryjnego zatrzymania 2-bezpieczeństwo;22-zatrzymanie uruchomienia programu skryptowego LUA;23-wyjście stanu bezpieczeństwa-bezpieczeństwo;24-wyjście stanu ochronnego zatrzymania-bezpieczeństwo;
    25-robot w ruchu-bezpieczeństwo;26-tryb redukcji robota-bezpieczeństwo;27-tryb nieredukcji robota-bezpieczeństwo;28-robot niezatrzymany;29-błąd robota-błąd punktu instrukcji;
    30-błąd robota-błąd napędu;31-błąd robota-błąd przekroczenia miękkiego limitu;32-błąd robota-błąd kolizji;33-błąd robota-błąd liczby aktywnych stacji podrzędnych;
    34-błąd robota-błąd stacji podrzędnej;35-błąd robota-błąd I/O;36-błąd robota-błąd chwytaka;37-błąd robota-błąd pliku;38-błąd robota-błąd osobliwej pozycji;
    39-błąd robota-błąd komunikacji napędu;40-błąd robota-błąd parametru;41-błąd robota-błąd przekroczenia miękkiego limitu zewnętrznej osi;42-ostrzeżenie robota-ostrzeżenie;
    43-ostrzeżenie robota-ostrzeżenie drzwi bezpieczeństwa;44-ostrzeżenie robota-ostrzeżenie ruchu;45-ostrzeżenie robota-ostrzeżenie strefy interferencji;46-ostrzeżenie robota-ostrzeżenie ściany bezpieczeństwa;
    47-stan załączenia;48-podnoszenie automatyczne po przerwaniu połączenia;49-ostrzeżenie interferencji sześcianu 1;50-ostrzeżenie interferencji sześcianu 2;51-ostrzeżenie interferencji sześcianu 3;52-ostrzeżenie interferencji sześcianu 4;
    * @return Kod błędu
    */
    public int SetDOConfig(int[] config)

Pobranie funkcji konfigurowalnego portu CO skrzynki sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Pobiera funkcję konfigurowalnego portu CO skrzynki sterowniczej
    * @param [out] config Kody funkcji CO0-CO7;
    * 0-brak;1-błąd robota;2-robot w ruchu;3-uruchom/zatrzymaj natryskiwanie;4-czyszczenie pistoletu natryskowego;5-sygnał podawania gazu;6-sygnał zajarzenia łuku;7-podawanie drutu punktowe;
    8-podawanie drutu wsteczne;9-wejście JOB 1;10-wejście JOB 2;11-wejście JOB 3;12-sterowanie uruchomieniem/zatrzymaniem taśmociągu;13-robot wstrzymany;14-osiągnięto punkt początkowy zadania;
    15-osiągnięto strefę interferencji;16-sterowanie uruchomieniem/zatrzymaniem pozycjonowania drutu spawalniczego;17-robot zakończył uruchamianie;18-zatrzymanie uruchomienia programu;19-tryb automatyczny/ręczny;20-sygnał wyjściowy awaryjnego zatrzymania 1-bezpieczeństwo;
    21-sygnał wyjściowy awaryjnego zatrzymania 2-bezpieczeństwo;22-zatrzymanie uruchomienia programu skryptowego LUA;23-wyjście stanu bezpieczeństwa-bezpieczeństwo;24-wyjście stanu ochronnego zatrzymania-bezpieczeństwo;
    25-robot w ruchu-bezpieczeństwo;26-tryb redukcji robota-bezpieczeństwo;27-tryb nieredukcji robota-bezpieczeństwo;28-robot niezatrzymany;29-błąd robota-błąd punktu instrukcji;
    30-błąd robota-błąd napędu;31-błąd robota-błąd przekroczenia miękkiego limitu;32-błąd robota-błąd kolizji;33-błąd robota-błąd liczby aktywnych stacji podrzędnych;
    34-błąd robota-błąd stacji podrzędnej;35-błąd robota-błąd I/O;36-błąd robota-błąd chwytaka;37-błąd robota-błąd pliku;38-błąd robota-błąd osobliwej pozycji;
    39-błąd robota-błąd komunikacji napędu;40-błąd robota-błąd parametru;41-błąd robota-błąd przekroczenia miękkiego limitu zewnętrznej osi;42-ostrzeżenie robota-ostrzeżenie;
    43-ostrzeżenie robota-ostrzeżenie drzwi bezpieczeństwa;44-ostrzeżenie robota-ostrzeżenie ruchu;45-ostrzeżenie robota-ostrzeżenie strefy interferencji;46-ostrzeżenie robota-ostrzeżenie ściany bezpieczeństwa;
    47-stan załączenia;48-podnoszenie automatyczne po przerwaniu połączenia;49-ostrzeżenie interferencji sześcianu 1;50-ostrzeżenie interferencji sześcianu 2;51-ostrzeżenie interferencji sześcianu 3;52-ostrzeżenie interferencji sześcianu 4;
    * @return Kod błędu
    */
    public int GetDOConfig(out int[] config)

Ustawienie funkcji konfigurowalnego portu End-CI końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia funkcję konfigurowalnego portu End-CI końcowego
    * @param [in] config Kody funkcji End CI0-CI1;
    * 0-brak;1-przełącznik narzędzia przeciągania nauczania;2-sygnał rejestracji punktu;3-przełączanie ręczny/automatyczny (sygnał impulsowy);4-uruchom/zatrzymaj rejestrację TPD;5-wstrzymaj ruch;
    6-wznów ruch;7-uruchom;8-zatrzymaj;9-wstrzymaj/wznów;10-uruchom/zatrzymaj;11-włącz pomocnicze przeciąganie czujnika siły;12-wyłącz pomocnicze przeciąganie czujnika siły;
    13-włącz/wyłącz pomocnicze przeciąganie czujnika siły;14-sygnał wykrywania lasera X;15-sygnał wykrywania lasera Y;16-ruch PTP do punktu początkowego zadania;17-przerwanie ruchu, zatrzymanie bieżącego ruchu zgodnie z sygnałem;
    18-uruchom program główny;19-uruchom przewijanie wstecz;20-potwierdzenie uruchomienia;21-wznów spawanie;22-zakończ spawanie;23-wyczyść błędy;24-przełączanie ręczny/automatyczny (poziom wysoki/niski);
    25-załącz;26-odłącz;27-załącz/odłącz;28-sygnał uruchamiania/zatrzymywania śledzenia serwomechanizmu laserowego;
    * @return Kod błędu
    */
    public int SetToolDIConfig(int[] config)

Pobranie funkcji konfigurowalnego portu End-CI końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Pobiera funkcję konfigurowalnego portu End-CI końcowego
    * @param [out] config Kody funkcji End CI0-CI1;
    * 0-brak;1-przełącznik narzędzia przeciągania nauczania;2-sygnał rejestracji punktu;3-przełączanie ręczny/automatyczny (sygnał impulsowy);4-uruchom/zatrzymaj rejestrację TPD;5-wstrzymaj ruch;
    6-wznów ruch;7-uruchom;8-zatrzymaj;9-wstrzymaj/wznów;10-uruchom/zatrzymaj;11-włącz pomocnicze przeciąganie czujnika siły;12-wyłącz pomocnicze przeciąganie czujnika siły;
    13-włącz/wyłącz pomocnicze przeciąganie czujnika siły;14-sygnał wykrywania lasera X;15-sygnał wykrywania lasera Y;16-ruch PTP do punktu początkowego zadania;17-przerwanie ruchu, zatrzymanie bieżącego ruchu zgodnie z sygnałem;
    18-uruchom program główny;19-uruchom przewijanie wstecz;20-potwierdzenie uruchomienia;21-wznów spawanie;22-zakończ spawanie;23-wyczyść błędy;24-przełączanie ręczny/automatyczny (poziom wysoki/niski);
    25-załącz;26-odłącz;27-załącz/odłącz;28-sygnał uruchamiania/zatrzymywania śledzenia serwomechanizmu laserowego;
    * @return Kod błędu
    */
    public int GetToolDIConfig(out int[] config)
    
Ustawienie stanu aktywnego konfigurowalnego portu CI skrzynki sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia stan aktywny konfigurowalnego portu CI skrzynki sterowniczej
    * @param [in] config Stan aktywny portów CI0-CI7; 0-aktywny wysoki poziom; 1-aktywny niski poziom
    * @return Kod błędu
    */
    public int SetDIConfigLevel(int[] config)
        
Pobranie stanu aktywnego konfigurowalnego portu CI skrzynki sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Pobiera stan aktywny konfigurowalnego portu CI skrzynki sterowniczej
    * @param [out] config Stan aktywny portów CI0-CI7; 0-aktywny wysoki poziom; 1-aktywny niski poziom
    * @return Kod błędu
    */
    public int GetDIConfigLevel(out int[] config)
        
Ustawienie stanu aktywnego konfigurowalnego portu CO skrzynki sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia stan aktywny konfigurowalnego portu CO skrzynki sterowniczej
    * @param [in] config Stan aktywny portów CO0-CO7; 0-aktywny wysoki poziom; 1-aktywny niski poziom
    * @return Kod błędu
    */
    public int SetDOConfigLevel(int[] config)

Pobranie stanu aktywnego konfigurowalnego portu CO skrzynki sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Pobiera stan aktywny konfigurowalnego portu CO skrzynki sterowniczej
    * @param [out] config Stan aktywny portów CO0-CO7; 0-aktywny wysoki poziom; 1-aktywny niski poziom
    * @return Kod błędu
    */
    public int GetDOConfigLevel(out int[] config)
    
Ustawienie stanu aktywnego konfigurowalnego portu CI końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia stan aktywny konfigurowalnego portu CI końcowego
    * @param [in] config Stan aktywny portów CI0-CI1; 0-aktywny wysoki poziom; 1-aktywny niski poziom
    * @return Kod błędu
    */
    public int SetToolDIConfigLevel(int[] config)
    
Pobranie stanu aktywnego konfigurowalnego portu CI końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Pobiera stan aktywny konfigurowalnego portu CI końcowego
    * @param [out] config Stan aktywny portów CI0-CI1; 0-aktywny wysoki poziom; 1-aktywny niski poziom
    * @return Kod błędu
    */
    public int GetToolDIConfigLevel(out int[] config)
    
Ustawienie stanu aktywnego standardowego portu DI skrzynki sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia stan aktywny standardowego portu DI skrzynki sterowniczej
    * @param [in] config Stan aktywny portów DI0-DI7; 0-aktywny wysoki poziom; 1-aktywny niski poziom
    * @return Kod błędu
    */
    public int SetStandardDILevel(int[] config)
    
Pobranie stanu aktywnego standardowego portu DI skrzynki sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Pobiera stan aktywny standardowego portu DI skrzynki sterowniczej
    * @param [out] config Stan aktywny portów DI0-DI7; 0-aktywny wysoki poziom; 1-aktywny niski poziom
    * @return Kod błędu
    */
    public int GetStandardDILevel(out int[] config)

Ustawienie stanu aktywnego standardowego portu DO skrzynki sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia stan aktywny standardowego portu DO skrzynki sterowniczej
    * @param [in] config Stan aktywny portów DO0-DO7; 0-aktywny wysoki poziom; 1-aktywny niski poziom
    * @return Kod błędu
    */
    public int SetStandardDOLevel(int[] config)
    
Pobranie stanu aktywnego standardowego portu DO skrzynki sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Pobiera stan aktywny standardowego portu DO skrzynki sterowniczej
    * @param [out] config Stan aktywny portów DO0-DO7; 0-aktywny wysoki poziom; 1-aktywny niski poziom
    * @return Kod błędu
    */
    public int GetStandardDOLevel(out int[] config)
        
Przykład kodu konfiguracji I/O robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    public void TestIOConfig()
    {
        int rtn = 0;

        // ---------- Test funkcji konfigurowalnego portu CI ----------
        int[] setDIConfig = new int[] { 3, 9, 1, 4, 5, 6, 7, 8 };
        rtn = robot.SetDIConfig(setDIConfig);
        Console.WriteLine($"SetDIConfig rtn is {rtn}");

        // Użycie parametru out do odebrania pobranej tablicy konfiguracyjnej
        int[] getDIConfig;
        rtn = robot.GetDIConfig(out getDIConfig);  
        Console.WriteLine($"GetDIConfig rtn is {rtn}, value is {string.Join(" ", getDIConfig)}");

        // ---------- Test funkcji konfigurowalnego portu CO ----------
        int[] setDOConfig = new int[] { 9, 10, 11, 12, 13, 14, 15, 16 };
        rtn = robot.SetDOConfig(setDOConfig);
        Console.WriteLine($"SetDOConfig rtn is {rtn}");

        int[] getDOConfig;
        rtn = robot.GetDOConfig(out getDOConfig);
        Console.WriteLine($"GetDOConfig rtn is {rtn}, value is {string.Join(" ", getDOConfig)}");

        // ---------- Test funkcji konfigurowalnego portu CI końcowego ----------
        int[] setToolDIConfig = new int[] { 17, 18 };
        rtn = robot.SetToolDIConfig(setToolDIConfig);
        Console.WriteLine($"SetToolDIConfig rtn is {rtn}");

        int[] getToolDIConfig;
        rtn = robot.GetToolDIConfig(out getToolDIConfig);
        Console.WriteLine($"GetToolDIConfig rtn is {rtn}, value is {string.Join(" ", getToolDIConfig)}");

        // ---------- Test stanu aktywnego konfigurowalnego portu CI skrzynki sterowniczej ----------
        int[] setDIConfigLevel = new int[] { 1, 1, 1, 1, 0, 0, 0, 0 };
        rtn = robot.SetDIConfigLevel(setDIConfigLevel);
        Console.WriteLine($"SetDIConfigLevel rtn is {rtn}");

        int[] getDIConfigLevel;
        rtn = robot.GetDIConfigLevel(out getDIConfigLevel);
        Console.WriteLine($"GetDIConfigLevel rtn is {rtn}, value is {string.Join(" ", getDIConfigLevel)}");

        // ---------- Test stanu aktywnego konfigurowalnego portu CO skrzynki sterowniczej ----------
        int[] setDOConfigLevel = new int[] { 0, 0, 0, 0, 1, 1, 1, 1 };
        rtn = robot.SetDIConfigLevel(setDOConfigLevel);
        Console.WriteLine($"SetDOConfigLevel rtn is {rtn}");

        int[] getDOConfigLevel;
        rtn = robot.GetDOConfigLevel(out getDOConfigLevel);
        Console.WriteLine($"GetDOConfigLevel rtn is {rtn}, value is {string.Join(" ", getDOConfigLevel)}");

        // ---------- Test stanu aktywnego konfigurowalnego portu CI końcowego ----------
        int[] setToolDIConfigLevel = new int[] { 1, 0 };
        rtn = robot.SetToolDIConfigLevel(setToolDIConfigLevel);
        Console.WriteLine($"SetToolDIConfigLevel rtn is {rtn}");

        int[] getToolDIConfigLevel;
        rtn = robot.GetToolDIConfigLevel(out getToolDIConfigLevel);
        Console.WriteLine($"GetToolDIConfigLevel rtn is {rtn}, value is {string.Join(" ", getToolDIConfigLevel)}");

        // ---------- Test stanu aktywnego standardowego portu DI skrzynki sterowniczej ----------
        int[] setStandardDILevel = new int[] { 1, 1, 1, 1, 0, 0, 0, 0 };
        rtn = robot.SetStandardDILevel(setStandardDILevel);
        Console.WriteLine($"SetStandardDILevel rtn is {rtn}");

        int[] getStandardDILevel;
        rtn = robot.GetStandardDILevel(out getStandardDILevel);
        Console.WriteLine($"GetStandardDILevel rtn is {rtn}, value is {string.Join(" ", getStandardDILevel)}");

        // ---------- Test stanu aktywnego standardowego portu DO skrzynki sterowniczej ----------
        int[] setStandardDOLevel = new int[] { 0, 0, 0, 0, 1, 1, 1, 1 };
        rtn = robot.SetStandardDOLevel(setStandardDOLevel);
        Console.WriteLine($"SetStandardDOLevel rtn is {rtn}");

        int[] getStandardDOLevel;
        rtn = robot.GetStandardDOLevel(out getStandardDOLevel);
        Console.WriteLine($"GetStandardDOLevel rtn is {rtn}, value is {string.Join(" ", getStandardDOLevel)}");

    }