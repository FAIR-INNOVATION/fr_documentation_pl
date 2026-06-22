CNDE
=====

.. toctree:: 
    :maxdepth: 5

Konfiguracja sprzężenia zwrotnego stanu CNDE robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetRobotRealtimeStateConfig(states: List[RobotState], period: int = 500) -> int:``"
    "Opis", "Ustawia domyślną konfigurację CNDE (wywołaj przed połączeniem RPC)"
    "Parametry wymagane", "
    - ``states``: Lista wyliczeniowa RobotState
    - ``period``: Okres danych (ms), zakres 8-1000, domyślnie 8 ms
    "
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd-errcode"

Dodawanie stanu robota do konfiguracji stanu CNDE
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AddRobotRealtimeState(states: List[RobotState], ip: str = None) -> int:``"
    "Opis", "Dodaje listę stanów CNDE do istniejącej konfiguracji (obsługuje dynamiczną konserwację i izolację IP)"
    "Parametry wymagane", "
    - ``states``: Lista wyliczeniowa RobotState, stany do dodania
    - ``ip``: Opcjonalny, określa IP robota (dla izolacji konfiguracji wielu robotów, jeśli nie podano, modyfikuje konfigurację globalną)
    "
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd-errcode"

Usuwanie stanu robota z konfiguracji stanu CNDE
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``DeleteRobotRealtimeState(states: List[RobotState], ip: str = None) -> int:``"
    "Opis", "Usuwa listę stanów CNDE z istniejącej konfiguracji (obsługuje dynamiczną konserwację i izolację IP)"
    "Parametry wymagane", "
    - ``states``: Lista wyliczeniowa RobotState, stany do usunięcia
    - ``ip``: Opcjonalny, określa IP robota (dla izolacji konfiguracji wielu robotów, jeśli nie podano, modyfikuje konfigurację globalną)
    "
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd-errcode"

Ustawianie okresu sprzężenia zwrotnego stanu CNDE
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetRobotRealtimeStatePeriod(period: int, ip: str = None) -> int:``"
    "Opis", "Ustawia okres sprzężenia zwrotnego stanu CNDE (obsługuje konfigurację globalną lub izolowaną IP)"
    "Parametry wymagane", "
    - ``period``: Okres danych (ms), zakres 8-1000
    - ``ip``: Opcjonalny, określa IP robota (jeśli nie podano, modyfikuje konfigurację globalną)
    "
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd-errcode"

Pobieranie wszystkich bieżących stanów sprzężenia zwrotnego stanu CNDE
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``CNDEGetConfig(self) -> tuple:``"
    "Opis", "Pobiera wszystkie bieżące stany"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd-errcode zawiera strukturę wynikową konfiguracji z listą stanów"

Przykład kodu korzystania ze sprzężenia zwrotnego stanu CNDE
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 

    from fairino import Robot
    from fairino.Robot import RobotState, SetRobotRealtimeStateConfig, DEFAULT_CNDE_STATES, AddRobotRealtimeState, DeleteRobotRealtimeState, SetRobotRealtimeStatePeriod
    import time

    # ==================== Parametry globalne ====================
    ROBOT_IP = '192.168.58.2'       # Adres IP robota
    # ========== Test1: Test konfiguracji CNDE i pobierania danych =============
    # Kroki testu:
    # 1. Ustaw konfigurację CNDE (JointCurPos, ToolCurPos, okres 20 ms)
    # 2. Nawiąż połączenie RPC
    # 3. Wydrukuj dane pozycji przegubów i TCP robota
    # 4. Pobierz znacznik czasu i zweryfikuj okres
    # 5. Zmodyfikuj konfigurację (RobotMode, RbtEnableState, okres 10 ms)
    # 6. Zweryfikuj, czy nowa konfiguracja obowiązuje

    def test1_cnde_config_and_data():
        """Test1: Test konfiguracji CNDE i pobierania danych - weryfikacja ustawień konfiguracji i aktualności danych"""
        print_separator("Test1: Test konfiguracji CNDE i pobierania danych")

        # ===== Krok 1: Ustaw konfigurację CNDE (JointCurPos, ToolCurPos, 20 ms) =====
        print("\n【Krok 1】Ustawianie konfiguracji CNDE...")
        print("  Pola konfiguracji: JointCurPos, ToolCurPos")
        print("  Okres sprzężenia zwrotnego: 20 ms")

        custom_states = [
            RobotState.JointCurPos,   # Bieżąca pozycja przegubów
            RobotState.ToolCurPos,    # Bieżąca pozycja narzędzia (TCP)
        ]

        rtn = SetRobotRealtimeStateConfig(custom_states, 20)
        if rtn != 0:
            print(f"✗ Ustawienie konfiguracji nie powiodło się, kod błędu: {rtn}")
            return None
        print("✓ Konfiguracja CNDE ustawiona pomyślnie")

        # ===== Krok 2: Nawiąż połączenie RPC =====
        print(f"\n【Krok 2】Nawiązywanie połączenia RPC ({ROBOT_IP})...")
        robot = Robot.RPC(ROBOT_IP)
        time.sleep(0.5)  # Oczekiwanie na połączenie i odbiór danych

        # Weryfikacja konfiguracji
        config = robot.CNDEGetConfig()
        if config:
            states, period = config
            print(f"✓ Połączenie udane, bieżąca konfiguracja: {len(states)} pól, okres {period} ms")
        else:
            print("✗ Nie można pobrać konfiguracji CNDE")
            return robot

        # ===== Krok 3: Wydrukuj dane pozycji przegubów i TCP robota =====
        print("\n【Krok 3】Drukowanie danych pozycji przegubów i TCP robota...")
        print("  (Wskazówka: Można przeciągnąć robota, aby zaobserwować zmiany danych)")
        print("  Naciśnij Ctrl+C, aby zatrzymać drukowanie danych")
        print("  (Użyj Wireshark do przechwycenia pakietów w celu weryfikacji rzeczywistego okresu danych)\n")

        sample_count = 0
        try:
            while sample_count < 100:  # Zbierz 100 próbek
                pkg = robot.robot_state_pkg

                # Drukuj co 10 klatek
                if sample_count % 10 == 0:
                    print(f"--- Próbka #{sample_count} ---")
                    print(f"  Pozycja przegubów (deg): [{', '.join([f'{x:.3f}' for x in pkg.jt_cur_pos])}]")
                    print(f"  Pozycja TCP (mm/deg): [{', '.join([f'{x:.3f}' for x in pkg.tl_cur_pos])}]")
                    print(f"  Licznik bieżącej klatki: {pkg.frame_cnt}")
                    print()

                sample_count += 1
                time.sleep(0.02)  # 20 ms

        except KeyboardInterrupt:
            print("\n  Drukowanie danych przerwane przez użytkownika")

        # Zamknięcie połączenia
        robot.CloseRPC()
        time.sleep(1)

        # ===== Krok 4: Zmodyfikuj konfigurację i zweryfikuj =====
        print("\n【Krok 4】Modyfikacja konfiguracji CNDE...")
        print("  Nowe pola konfiguracji: RobotMode, RbtEnableState")
        print("  Nowy okres sprzężenia zwrotnego: 10 ms")

        new_states = [
            RobotState.RobotMode,
            RobotState.RbtEnableState,
        ]

        # Ustaw nową konfigurację
        rtn = SetRobotRealtimeStateConfig(new_states, 10)
        if rtn != 0:
            print(f"✗ Ustawienie nowej konfiguracji nie powiodło się, kod błędu: {rtn}")
            return robot
        print("✓ Nowa konfiguracja ustawiona pomyślnie")

        # Ponowne połączenie
        robot = Robot.RPC(ROBOT_IP)
        time.sleep(0.5)

        # Weryfikacja nowej konfiguracji
        config = robot.CNDEGetConfig()
        if config:
            states, period = config
            print(f"✓ Bieżąca konfiguracja: {[s.name for s in states]}")
            print(f"✓ Bieżący okres: {period} ms")

            if period == 10:
                print("✓ Weryfikacja modyfikacji konfiguracji zakończona pomyślnie (okres zmienił się na 10 ms)")
            else:
                print(f"⚠ Okres nie obowiązuje (oczekiwano 10 ms, faktycznie {period} ms)")

            # Wydrukuj nowe dane
            pkg = robot.robot_state_pkg
            print(f"\n【Dane nowej konfiguracji】")
            print(f"  robot_mode: {pkg.robot_mode}")
            print(f"  rbtEnableState: {pkg.rbtEnableState}")
        else:
            print("✗ Nie można pobrać nowej konfiguracji")

        print("\n✓ Test1 zakończony")
        return robot


    if __name__ == "__main__":
        test1_cnde_config_and_data()


    # ======== Test2: Test pól stanu Add/Delete ====================
    # Funkcja: Testowanie AddRobotRealtimeState() i DeleteRobotRealtimeState()
    # Kroki testu:
    #   1. Użyj AddRobotRealtimeState(), aby dodać SpeedScaleManual i SpeedScaleAuto
    #   2. Połącz się z robotem, wydrukuj prędkość globalną w trybie ręcznym/automatycznym
    #   3. Zmodyfikuj prędkość globalną w WebApp, obserwuj zmiany danych w SDK
    #   4. Użyj DeleteRobotRealtimeState(), aby usunąć dodane pola
    #   5. Połącz się ponownie, sprawdź, czy wartość prędkości wynosi 0 (pola nie są już aktualizowane)


    def test2_add_delete_state():
        """Test2: Test pól stanu Add/Delete - weryfikacja dynamicznego dodawania i usuwania stanów CNDE"""
        print_separator("Test2: Test pól stanu Add/Delete")

        # ===== Krok 1: Dodaj pola SpeedScaleManual i SpeedScaleAuto =====
        print("\n【Krok 1】Używanie AddRobotRealtimeState() do dodania pól współczynnika prędkości...")
        print("  Dodawane pola: SpeedScaleManual, SpeedScaleAuto")

        rtn = AddRobotRealtimeState([
            RobotState.SpeedScaleManual,
            RobotState.SpeedScaleAuto,
        ])

        if rtn != 0:
            print(f"✗ Dodanie pól nie powiodło się, kod błędu: {rtn}")
            return None
        print("✓ Pola dodane pomyślnie")

        # ===== Krok 2: Nawiąż połączenie RPC i wydrukuj prędkość =====
        print(f"\n【Krok 2】Nawiązywanie połączenia RPC ({ROBOT_IP})...")
        robot = Robot.RPC(ROBOT_IP)
        time.sleep(0.5)  # Oczekiwanie na połączenie i odbiór danych

        # Weryfikacja konfiguracji
        config = robot.CNDEGetConfig()
        if config:
            states, period = config
            print(f"✓ Połączenie udane, bieżąca konfiguracja: {len(states)} pól")
            # Sprawdź, czy zawiera dodane pola
            has_manual = RobotState.SpeedScaleManual in states
            has_auto = RobotState.SpeedScaleAuto in states
            if has_manual and has_auto:
                print("✓ Weryfikacja konfiguracji zakończona pomyślnie: SpeedScaleManual i SpeedScaleAuto zostały dodane")
            else:
                print(f"⚠ Ostrzeżenie weryfikacji konfiguracji: Manual={has_manual}, Auto={has_auto}")
        else:
            print("✗ Nie można pobrać konfiguracji CNDE")

        # Wydrukuj dane prędkości
        print("\n【Bieżące dane prędkości】(proszę zmodyfikować prędkość globalną w WebApp i obserwować zmiany)")
        print("  Wskazówka: Przeciągnij robota, włącz zasilanie i przełącz tryb ręczny/automatyczny, obserwuj wartości prędkości")
        print("  Naciśnij Ctrl+C, aby zatrzymać drukowanie danych\n")

        sample_count = 0
        try:
            while sample_count < 100:  # Zbierz 100 próbek (około 10 sekund, co 100 ms)
                pkg = robot.robot_state_pkg
                print(f"  [{sample_count:3d}] SpeedScaleManual: {pkg.speedScaleManual:.2f}, "
                    f"SpeedScaleAuto: {pkg.speedScaleAuto:.2f}, "
                    f"Tryb: {pkg.robot_mode}")
                sample_count += 1
                time.sleep(0.1)  # Odstęp 100 ms
        except KeyboardInterrupt:
            print("\n  Drukowanie danych przerwane przez użytkownika")

        print(f"\n✓ Zbieranie danych zakończone, łącznie {sample_count} próbek")

        # ===== Krok 3: Rozłącz połączenie =====
        print("\n【Krok 3】Zrywanie bieżącego połączenia...")
        robot.CloseRPC()
        time.sleep(1.0)  # Oczekiwanie na całkowite zamknięcie CNDE

        # ===== Krok 4: Usuń dodane pola =====
        print("\n【Krok 4】Używanie DeleteRobotRealtimeState() do usunięcia pól współczynnika prędkości...")
        rtn = DeleteRobotRealtimeState([
            RobotState.SpeedScaleManual,
            RobotState.SpeedScaleAuto,
        ])

        if rtn != 0:
            print(f"✗ Usunięcie pól nie powiodło się, kod błędu: {rtn}")
            return robot
        print("✓ Pola usunięte pomyślnie")

        # ===== Krok 5: Połącz się ponownie i sprawdź, czy wartości pól wynoszą 0 =====
        print(f"\n【Krok 5】Ponowne połączenie i weryfikacja wartości pól po usunięciu...")

        robot = Robot.RPC(ROBOT_IP)
        time.sleep(0.5)

        # Odczytaj wartości prędkości
        pkg = robot.robot_state_pkg
        manual_speed = pkg.speedScaleManual
        auto_speed = pkg.speedScaleAuto

        print(f"\n  SpeedScaleManual po usunięciu: {manual_speed:.2f}")
        print(f"  SpeedScaleAuto po usunięciu: {auto_speed:.2f}")

        # Sprawdź, czy wynosi 0
        if manual_speed == 0 and auto_speed == 0:
            print("\n✓ Weryfikacja Test2 zakończona pomyślnie: wartości prędkości po usunięciu pól wynoszą 0")
        else:
            print(f"\n⚠ Ostrzeżenie Test2: wartości prędkości po usunięciu pól są niezerowe")

        print("\n✓ Test2 zakończony")
        return robot

    if __name__ == "__main__":
        test2_add_delete_state()