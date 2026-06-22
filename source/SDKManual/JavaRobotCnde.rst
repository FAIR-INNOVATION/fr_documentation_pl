CNDE
=====

.. toctree::
    :maxdepth: 5

Konfiguracja sprzężenia zwrotnego stanu robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Konfiguruje sprzężenie zwrotne stanu robota
    * @param state Lista wyliczeniowa stanów robota
    * @param period Okres sprzężenia zwrotnego stanu, zakres 8-1000
    * @return Kod błędu, normalny-0, nieprawidłowy parametr-4, pole stanu nie istnieje-18, całkowita liczba bajtów przekracza 4K-20
    */
    public int SetRobotRealtimeStateConfig(List<RobotState> state, int period)

Dodanie stanu robota do listy konfiguracji CNDE
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Dodaje stan robota do listy konfiguracji
    * @param state Wyliczenie stanu robota
    * @return Kod błędu, normalny-0, stan już istnieje-17, pole stanu nie istnieje-18, przekroczenie 4K-20
    */
    public int AddRobotRealtimeState(RobotState state)

Usunięcie stanu robota z listy konfiguracji CNDE
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Usuwa stan robota z listy konfiguracji
    * @param state Wyliczenie stanu robota
    * @return Kod błędu, normalny-0, stan nie istnieje-18, pozostawienie co najmniej jednego stanu-19
    */
    public int DeleteRobotRealtimeState(RobotState state)

Ustawienie okresu sprzężenia zwrotnego stanu CNDE
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia okres sprzężenia zwrotnego stanu CNDE
    * @param period Okres sprzężenia zwrotnego stanu, zakres 8-1000
    * @return Kod błędu, normalny-0, nieprawidłowy parametr-4
    */
    public int SetRobotRealtimeStatePeriod(int period)

Pobranie wszystkich stanów i okresu bieżącej konfiguracji sprzężenia zwrotnego stanu CNDE
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
     * @brief Pobiera wszystkie stany i okres bieżącej konfiguracji
     * @return Struktura wyniku konfiguracji zawierająca listę stanów i okres
    */
    public StateConfigResult GetRobotRealtimeStateConfig()

Przykład kodu użycia sprzężenia zwrotnego stanu CNDE
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Przykład użycia interfejsu konfiguracji stanu w czasie rzeczywistym CNDE
    */
    public static void TestRealtimeStateConfig(Robot robot)
    {

        // 1. Utworzenie początkowej listy stanów
        List<RobotState> stateList1 = new ArrayList<>();
        stateList1.add(RobotState.ProgramState);
        stateList1.add(RobotState.RobotState);
        stateList1.add(RobotState.JointCurPos);
        stateList1.add(RobotState.ToolCurPos);

        // 2. Pierwsze wywołanie SetRobotRealtimeStateConfig w celu skonfigurowania stanów i okresu
        int period1 = 100;  // okres 100 ms
        int rtn = robot.SetRobotRealtimeStateConfig(stateList1, period1);
        System.out.printf("1. SetRobotRealtimeStateConfig (lista początkowa, okres=%d) rtn: %d%n", period1, rtn);

        if (rtn == 0) {
            // 3. Dodanie dodatkowego stanu
            rtn = robot.AddRobotRealtimeState(RobotState.RobotTime);
            System.out.printf("2. AddRobotRealtimeState (RobotTime) rtn: %d%n", rtn);

            // 4. Ponowne wywołanie SetRobotRealtimeStateConfig w celu ponownej konfiguracji (inna lista stanów)
            List<RobotState> stateList2 = new ArrayList<>();
            stateList2.add(RobotState.ProgramState);
            stateList2.add(RobotState.RobotState);
            stateList2.add(RobotState.MainCode);
            stateList2.add(RobotState.SubCode);
            stateList2.add(RobotState.JointCurPos);
            stateList2.add(RobotState.ToolCurPos);
            stateList2.add(RobotState.ActualJointTorque);

            int period2 = 50;  // okres 50 ms
            rtn = robot.SetRobotRealtimeStateConfig(stateList2, period2);
            System.out.printf("3. SetRobotRealtimeStateConfig (zaktualizowana lista, okres=%d) rtn: %d%n", period2, rtn);

            // 5. Modyfikacja okresu
            int newPeriod = 80;  // okres 80 ms
            rtn = robot.SetRobotRealtimeStatePeriod(newPeriod);
            System.out.printf("4. SetRobotRealtimeStatePeriod (okres=%d) rtn: %d%n", newPeriod, rtn);

            // 6. Pobranie bieżącej konfiguracji i jej wydrukowanie
            Robot.StateConfigResult configResult = robot.GetRobotRealtimeStateConfig();
            System.out.println("5. Wynik GetRobotRealtimeStateConfig:");
            System.out.printf("   - Okres: %d ms%n", configResult.period);
            System.out.println("   - Skonfigurowane stany:");
            for (int i = 0; i < configResult.stateList.size(); i++) {
                System.out.printf("     [%d] %s%n", i, configResult.stateList.get(i));
            }

            rtn = robot.RPC("192.168.58.2");
            if (rtn == 0) {
                System.out.println("rpc połączenie success");
            } else {
                System.out.println("rpc połączenie fail");
                return;
            }
            // Oczekiwanie na nawiązanie połączenia CNDE
            System.out.println("Oczekiwanie na nawiązanie połączenia CNDE...");
            while (robot.CNDEGetStateData() == null) {
                robot.Sleep(100);
            }
            System.out.println("Połączenie CNDE nawiązano, rozpoczęcie odbierania danych...");

            // 7. Cykliczne odczytywanie stanu w czasie rzeczywistym w celu weryfikacji, czy konfiguracja jest aktywna
            System.out.println("6. Odczytywanie stanów w czasie rzeczywistym...");
            while(true) {
                robot.Sleep(1000);
                // Pobieranie danych stanu przez CNDE
                ROBOT_STATE_PKG pkg = robot.CNDEGetStateData();
                if (pkg == null) {
                    System.out.println("Dane stanu są puste, połączenie CNDE przerwane, oczekiwanie na ponowne połączenie");
                    continue;  // Kontynuuj pętlę w przypadku przerwania połączenia, oczekuj na ponowne połączenie
                }
                System.out.println("\n--- Czas robota ---");
                if (pkg.robotTime != null) {
                    System.out.println("robotTime: " + pkg.robotTime.year + "-" + pkg.robotTime.month + "-" + pkg.robotTime.day +
                            " " + pkg.robotTime.hour + ":" + pkg.robotTime.minute + ":" + pkg.robotTime.second +
                            "." + pkg.robotTime.millisecond);
                }

                System.out.println("   --- Informacje o stanie ---");
                System.out.printf("   program_state: %d%n", pkg.program_state);
                System.out.printf("   robot_state: %d%n", pkg.robot_state);
                System.out.printf("   main_code: %d%n", pkg.main_code);
                System.out.printf("   sub_code: %d%n", pkg.sub_code);
                System.out.println("   --- Pozycje stawów (actual_joint_pos) ---");
                System.out.printf("   jt_cur_pos[0-2]: %.2f, %.2f, %.2f%n",
                    pkg.jt_cur_pos[0], pkg.jt_cur_pos[1], pkg.jt_cur_pos[2]);
                System.out.printf("   jt_cur_pos[3-5]: %.2f, %.2f, %.2f%n",
                    pkg.jt_cur_pos[3], pkg.jt_cur_pos[4], pkg.jt_cur_pos[5]);
                System.out.println("   --- Pozycja TCP (actual_TCP_pos) ---");
                System.out.printf("   tl_cur_pos[0-2]: %.2f, %.2f, %.2f%n",
                    pkg.tl_cur_pos[0], pkg.tl_cur_pos[1], pkg.tl_cur_pos[2]);
                System.out.printf("   tl_cur_pos[3-5]: %.2f, %.2f, %.2f%n",
                    pkg.tl_cur_pos[3], pkg.tl_cur_pos[4], pkg.tl_cur_pos[5]);
                System.out.println("   --- Momenty stawów (actual_joint_torque) ---");
                System.out.printf("   jt_cur_tor[0-2]: %.2f, %.2f, %.2f%n",
                    pkg.jt_cur_tor[0], pkg.jt_cur_tor[1], pkg.jt_cur_tor[2]);
                System.out.printf("   jt_cur_tor[3-5]: %.2f, %.2f, %.2f%n",
                    pkg.jt_cur_tor[3], pkg.jt_cur_tor[4], pkg.jt_cur_tor[5]);
                robot.Sleep(500);
            }
        } else {
            System.out.printf("SetRobotRealtimeStateConfig nie powiodło się z błędem: %d%n", rtn);
        }
    }