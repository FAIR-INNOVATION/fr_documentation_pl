CNDE
====

.. toctree:: 
    :maxdepth: 5

Konfiguracja listy danych i okresu aktualizacji CNDE robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Konfiguruje listę danych i okres aktualizacji informacji zwrotnej o stanie robota w czasie rzeczywistym (nadpisuje poprzednią konfigurację)
    * @param [in] states Lista wyliczeń stanów do subskrybowania, kolejność określa porządek w pakiecie danych.
    * @param [in] period Okres aktualizacji danych, jednostka milisekundy, zakres [8, 1000]
    * @return Sukces zwraca 0; błąd zwraca ujemny kod błędu (np. ERR_STATE_INVALID, ERR_PARAM_VALUE itp.)
    */
    public int SetRobotRealtimeStateConfig(List<RobotState> states, int period)

Dodanie elementu stanu do istniejącej listy informacji zwrotnej o stanie
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Dodaje element stanu do istniejącej listy informacji zwrotnej o stanie
    * @param [in] state Wartość wyliczenia stanu do dodania.
    * @return Sukces zwraca 0; błąd zwraca ujemny kod błędu (np. ERR_STATE_ALREADY_EXISTS, ERR_STATE_INVALID itp.)
    */
    public int AddRobotRealtimeState(RobotState state)
    
Usunięcie elementu stanu z istniejącej listy informacji zwrotnej o stanie
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Usuwa element stanu z istniejącej listy informacji zwrotnej o stanie (pozostawia co najmniej jeden stan)
    * @param [in] state Wartość wyliczenia stanu do usunięcia
    * @return Sukces zwraca 0; błąd zwraca ujemny kod błędu (np. ERR_STATE_INVALID, ERR_NEED_AT_LEAST_ONE_STATE)
    */
    public int DeleteRobotRealtimeState(RobotState state)
        
Modyfikacja wyłącznie okresu aktualizacji informacji zwrotnej o stanie
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

     /**
    * @brief Modyfikuje wyłącznie okres aktualizacji informacji zwrotnej o stanie, nie zmieniając listy stanów
    * @param [in] period Nowy okres aktualizacji, jednostka milisekundy, zakres [8, 1000]
    * @return Sukces zwraca 0; błąd zwraca ujemny kod błędu (np. ERR_PARAM_VALUE)
    */
    public int SetRobotRealtimeStatePeriod(int period)
        
Pobranie aktualnie skonfigurowanej listy informacji zwrotnej o stanie i okresu aktualizacji
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Pobiera aktualnie skonfigurowaną listę informacji zwrotnej o stanie i okres aktualizacji
    * @param [out] states Wyjściowa lista wyliczeń stanów subskrybowanych
    * @param [out] period Wyjściowy bieżący okres aktualizacji danych, jednostka milisekundy
    * @return Sukces zwraca 0; błąd zwraca ujemny kod błędu.
    */
    public int GetRobotRealtimeStateConfig(out List<RobotState> states, out int period)

Przykład kodu SDK związany z konfiguracją CNDE
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private async void TestRobotRealtimeStates()
    {
        // 1. Definicja pól stanu do subskrybowania
        List<RobotState> requiredStates = new List<RobotState>
        {
            RobotState.JointCurPos,
            RobotState.ToolCurPos, 
            RobotState.JointDriverTemperature,
            RobotState.RobotTime,
        };

        // 2. Konfiguracja informacji zwrotnej o stanie (okres 8ms)
        int periodMs = 8;
        int ret = robot.SetRobotRealtimeStateConfig(requiredStates, periodMs);
        if (ret != 0)
        {
            Console.WriteLine($"Konfiguracja stanu nie powiodła się, kod błędu: {ret}");
            return;
        }
        Console.WriteLine($"Konfiguracja stanu powiodła się, {requiredStates.Count} pól, okres {periodMs} ms");

        // Weryfikacja, czy konfiguracja jest aktywna
        List<RobotState> actualStates;
        int actualPeriod;
        robot.GetRobotRealtimeStateConfig(out actualStates, out actualPeriod);
        Console.WriteLine($"Rzeczywista liczba stanów: {actualStates.Count}, okres: {actualPeriod} ms");
        Thread.Sleep(3000);
        // 3. Nawiązanie połączenia RPC (wewnętrznie automatycznie wykonuje uzgadnianie CNDE)
        robot.SetReconnectParam(true, 10, 1000);
        ret = robot.RPC("192.168.58.2");  // Proszę zmienić zgodnie z rzeczywistym adresem IP robota
        if (ret != 0)
        {
            Console.WriteLine($"Połączenie RPC nie powiodło się, kod błędu: {ret}");
            return;
        }
        // 4. Cykliczne odczytywanie i drukowanie danych stanu
        DateTime startTime = DateTime.Now;
        const int durationSeconds = 500;

        while ((DateTime.Now - startTime).TotalSeconds < durationSeconds)
        {
            ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
            ret = robot.GetRobotRealTimeState(ref pkg);
            Console.WriteLine($"GetRobotRealTimeState: {ret}");

            // Pozycje stawów (stopnie)
            if (pkg.jt_cur_pos != null && pkg.jt_cur_pos.Length >= 6)
                Console.WriteLine($"Pozycje stawów(°): J1={pkg.jt_cur_pos[0]:F2}, J2={pkg.jt_cur_pos[1]:F2}, J3={pkg.jt_cur_pos[2]:F2}, J4={pkg.jt_cur_pos[3]:F2}, J5={pkg.jt_cur_pos[4]:F2}, J6={pkg.jt_cur_pos[5]:F2}");

            // Pozycja i orientacja TCP (mm /°)
            if (pkg.tl_cur_pos != null && pkg.tl_cur_pos.Length >= 6)
                Console.WriteLine($"Pozycja i orientacja TCP(mm/°): X={pkg.tl_cur_pos[0]:F2}, Y={pkg.tl_cur_pos[1]:F2}, Z={pkg.tl_cur_pos[2]:F2}, RX={pkg.tl_cur_pos[3]:F2}, RY={pkg.tl_cur_pos[4]:F2}, RZ={pkg.tl_cur_pos[5]:F2}");
    
            // Temperatura stawów
            if (pkg.jointDriverTemperature != null && pkg.jointDriverTemperature.Length >= 6)
                Console.WriteLine($"Temperatura stawów(°C): J1={pkg.jointDriverTemperature[0]:F2}, J2={pkg.jointDriverTemperature[1]:F2}, J3={pkg.jointDriverTemperature[2]:F2}, J4={pkg.jointDriverTemperature[3]:F2}, J5={pkg.jointDriverTemperature[4]:F2}, J6={pkg.jointDriverTemperature[5]:F2}");

            // Czas robota
            Console.WriteLine($"Czas robota: {pkg.robotTime.year}-{pkg.robotTime.mouth:D2}-{pkg.robotTime.day:D2} {pkg.robotTime.hour:D2}:{pkg.robotTime.minute:D2}:{pkg.robotTime.second:D2}.{pkg.robotTime.millisecond:D3}");

            await Task.Delay(100);
        }

        // 5. Zerwanie połączenia
        robot.CloseRPC();
    }

Przykład kodu SDK dodawania/usuwania stanów konfiguracji CNDE i ustawiania okresu komunikacji
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private async void TestAddDeleteCNDE()
    {
        List<RobotState> finalStates;
        int finalPeriod;
        // Konfiguracja początkowa: nie żądaj żadnych stanów (konfiguracja domyślna)
        List<RobotState> emptyStates = new List<RobotState>();
        int ret = robot.SetRobotRealtimeStateConfig(emptyStates, 20);

        robot.SetRobotRealtimeStatePeriod(10);
        // Usuń dwa stany
        ret = robot.DeleteRobotRealtimeState(RobotState.JointCurPos);
        Console.WriteLine($"Usunięcie JointCurPos wynik: {ret}");
        ret = robot.DeleteRobotRealtimeState(RobotState.ToolCurPos);
        Console.WriteLine($"Usunięcie ToolCurPos wynik: {ret}");
        // Dodaj jeden stan
        ret = robot.AddRobotRealtimeState(RobotState.CollisionLevel);
        Console.WriteLine($"Dodanie CollisionLevel wynik: {ret}");

        // Pobierz bieżącą listę konfiguracji i wyślij ponownie
        List<RobotState> currentStates;
        int currentPeriod;
        robot.GetRobotRealtimeStateConfig(out currentStates, out currentPeriod);
        Console.WriteLine($"Bieżąca liczba stanów w konfiguracji: {currentStates.Count}");
        ret = robot.SetRobotRealtimeStateConfig(currentStates, currentPeriod);
        Console.WriteLine($"Zastosowanie nowej konfiguracji wynik: {ret}"); Console.WriteLine($"Wynik konfiguracji początkowej: {ret}");
        robot.GetRobotRealtimeStateConfig(out finalStates, out finalPeriod);
        Console.WriteLine($"Liczba stanów w konfiguracji: {finalStates.Count}");
        foreach (var s in finalStates) Console.WriteLine($"  {s}");
        Console.WriteLine($"Okres: {finalPeriod} ms");

        Thread.Sleep(1000);
        //  Nawiązanie połączenia RPC (wewnętrznie automatycznie łączy CNDE)
        robot.SetReconnectParam(true, 100, 1000);
        ret = robot.RPC("192.168.58.2");
        if (ret != 0)
        {
            Console.WriteLine($"Połączenie RPC nie powiodło się: {ret}");
            return;
        }

        // Cykliczne drukowanie usuniętych i dodanych stanów, usunięte stany są drukowane jako 0, dodane stany mogą normalnie pobierać wartości w czasie rzeczywistym
        DateTime lastTime = DateTime.Now;
        int frameCount = 0;
        DateTime startTime = DateTime.Now;
        while ((DateTime.Now - startTime).TotalSeconds < 10)
        {
            ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
            robot.GetRobotRealTimeState(ref pkg);
            DateTime now = DateTime.Now;
            double interval = (now - lastTime).TotalMilliseconds;
            lastTime = now;
            frameCount++;

            if (pkg.jt_cur_pos != null && pkg.jt_cur_pos.Length >= 6)
            {
                Console.WriteLine($"  Pozycje stawów(°): J1={pkg.jt_cur_pos[0]:F2}, J2={pkg.jt_cur_pos[1]:F2}, J3={pkg.jt_cur_pos[2]:F2}, J4={pkg.jt_cur_pos[3]:F2}, J5={pkg.jt_cur_pos[4]:F2}, J6={pkg.jt_cur_pos[5]:F2}");
            }
            if (pkg.tl_cur_pos != null && pkg.tl_cur_pos.Length >= 6)
            {
                Console.WriteLine($"  Pozycja i orientacja TCP(mm/°): X={pkg.tl_cur_pos[0]:F2}, Y={pkg.tl_cur_pos[1]:F2}, Z={pkg.tl_cur_pos[2]:F2}, RX={pkg.tl_cur_pos[3]:F2}, RY={pkg.tl_cur_pos[4]:F2}, RZ={pkg.tl_cur_pos[5]:F2}");
            }
            // Poziom kolizji
            if (pkg.collisionLevel != null && pkg.collisionLevel.Length >= 6)
                Console.WriteLine($"Poziomy kolizji: J1={pkg.collisionLevel[0]}, J2={pkg.collisionLevel[1]}, J3={pkg.collisionLevel[2]}, J4={pkg.collisionLevel[3]}, J5={pkg.collisionLevel[4]}, J6={pkg.collisionLevel[5]}");

            await Task.Delay(50);
        }
        //Zerwanie połączenia
        robot.CloseRPC();
        Console.WriteLine("Test zakończony.");
    }