Wprowadzenie do CNDE
====================

Konfigurowalny protokół wymiany danych sieciowych dla robota współpracującego (zwany dalej CNDE) to sposób, w jaki klient może sterować robotem i uzyskiwać informacje zwrotne o jego stanie za pośrednictwem komunikacji UDP.

Tabela 1-1 przedstawia wszystkie stany robota, które można uzyskać za pośrednictwem CNDE. Klient może wybrać dowolną liczbę potrzebnych stanów z tabeli i sprawić, aby robot przekazywał informację zwrotną o stanie zgodnie z ustawionym okresem.

Podobnie klient może również wybrać potrzebne kombinacje funkcji sterowania robotem z Tabeli 1-2 w celu wykonania operacji sterowania robotem. Dane komunikacyjne CNDE między klientem a robotem muszą być zgodne z określonym formatem ramki. Porty komunikacyjne CNDE robota to 20005 i 20006. Port 20005 jest używany do komunikacji TCP, a port 20006 do komunikacji UDP.

Korzystanie z funkcji CNDE robota obejmuje głównie następujące cztery kroki:

① Konfiguracja treści danych wejściowych i wyjściowych: Klient wysyła do robota instrukcję konfiguracji wejść i wyjść. Treść instrukcji ma postać ciągu nazw funkcji sterowania lub stanu, takich jak „std_DI_box,cfg_DI_box,motion_queue_len”. Po zarejestrowaniu i rozpoznaniu tych nazw przez robot, robot wysyła do klienta informację zwrotną z typami danych odpowiadających funkcji, np. „UINT8,UINT8,INT32”, co oznacza pomyślną konfigurację.

② Uruchomienie wyjścia danych CNDE robota: Klient wysyła do robota instrukcję uruchomienia wyjścia danych CNDE. Robot zaczyna następnie wysyłać dane stanu robota do klienta za pośrednictwem UDP w postaci tablicy bajtów (tryb little-endian) zgodnie ze skonfigurowanym okresem.

③ Parsowanie danych stanu robota: Klient odbiera dane stanu zwracane przez robota w pętli i parsuje dane na podstawie typów danych zwróconych przez robota podczas konfiguracji wyjść oraz długości bajtowej odpowiadającej każdemu typowi danych w Tabeli 1-3, uzyskując rzeczywiste wartości każdego stanu. Dane wyjściowe CNDE robota obsługują maksymalnie 4096 bajtów. Okres wyjścia CNDE można skonfigurować w zakresie od 1 do 200 ms.

④ Wysyłanie danych sterujących do robota: Klient pakuje dane sterujące na podstawie typów danych zwróconych przez robota podczas konfiguracji wejść oraz długości bajtowej odpowiadającej każdemu typowi danych w Tabeli 1-3, a następnie wysyła je do robota za pośrednictwem komunikacji UDP. Po otrzymaniu danych sterujących robot parsuje je i wykonuje operacje sterowania robotem. CNDE wejściowe robota obsługuje 256 receptur. Klient może najpierw skonfigurować wiele receptur wejściowych zgodnie z potrzebami. Podczas wysyłania danych wejściowych do robota należy określić numer receptury odpowiadający bieżącym danym.

.. centered:: Tabela 1-1 Funkcje konfiguracji wyjść robota

.. list-table::
   :widths: 20 40 80
   :header-rows: 0
   :align: center
   :class: sheet-center

   * - **Nazwa**
     - **Typ danych**
     - **Opis**

   * - std_DI_box
     - UINT8
     - Standardowe wejście DI skrzynki sterowniczej (bit0 ~ bit7 oznaczają DI0 ~ DI7)

   * - cfg_DI_box
     - UINT8
     - Konfigurowalne wejście CI skrzynki sterowniczej (bit0 ~ bit7 oznaczają CI0 ~ CI7)

   * - cfg_DI_tool
     - UINT8
     - Konfigurowalne wejście DI narzędzia skrzynki sterowniczej (bit0 ~ bit2 oznaczają toolDI0 ~ toolDI1)

   * - std_AI0_box
     - DOUBLE
     - Wejście analogowe AI0 skrzynki sterowniczej (0 ~ 4095)

   * - std_AI1_box
     - DOUBLE
     - Wejście analogowe AI1 skrzynki sterowniczej (0 ~ 4095)

   * - std_AI_tool
     - DOUBLE
     - Wejście analogowe tool_AI0 narzędzia końcowego (0 ~ 4095)

   * - run_up_time
     - DOUBLE
     - Statystyka czasu pracy robota od uruchomienia (s)

   * - target_joint_pos
     - DOUBLE_6
     - Pozycja docelowa stawów 1-6 (°)

   * - target_joint_vel
     - DOUBLE_6
     - Prędkość docelowa stawów 1-6 (°/s)

   * - target_joint_acc
     - DOUBLE_6
     - Przyspieszenie docelowe stawów 1-6 (°/s²)

   * - target_joint_current
     - DOUBLE_6
     - Prąd docelowy stawów 1-6 (A)

   * - target_joint_torque
     - DOUBLE_6
     - Moment obrotowy docelowy stawów 1-6 (Nm)

   * - actual_joint_pos
     - DOUBLE_6
     - Bieżąca pozycja stawów 1-6 (°)

   * - actual_joint_vel
     - DOUBLE_6
     - Bieżąca prędkość stawów 1-6 (°/s)

   * - actual_joint_current
     - DOUBLE_6
     - Bieżący prąd stawów 1-6 (A)

   * - actual_joint_torque
     - DOUBLE_6
     - Rzeczywisty moment obrotowy stawów 1-6 (Nm)

   * - actual_TCP_pos
     - DOUBLE_6
     - Bieżąca pozycja narzędzia DKR (mm)

   * - actual_TCP_vel
     - DOUBLE_6
     - Bieżąca prędkość narzędzia DKR (mm/s)

   * - actual_TCP_force
     - DOUBLE_6
     - Całkowita siła narzędzia DKR (N)

   * - target_TCP_pos
     - DOUBLE_6
     - Docelowa pozycja narzędzia DKR (mm)

   * - target_TCP_vel
     - DOUBLE_6
     - Docelowa prędkość narzędzia DKR (mm/s)

   * - std_DO_box
     - UINT8
     - Standardowe wyjście DO skrzynki sterowniczej (bit0 ~ bit7 oznaczają DO0 ~ DO7)

   * - cfg_DO_box
     - UINT8
     - Konfigurowalne wyjście CO skrzynki sterowniczej (bit0 ~ bit7 oznaczają CO0 ~ CO7)

   * - cfg_DO_tool
     - UINT8
     - Standardowe wyjście DO narzędzia skrzynki sterowniczej (bit0 ~ bit1 oznaczają toolDO0 ~ toolDO1)

   * - std_AO0_box
     - DOUBLE
     - Wyjście analogowe AO0 skrzynki sterowniczej (0.0 ~ 4095.0)

   * - std_AO1_box
     - DOUBLE
     - Wyjście analogowe AO1 skrzynki sterowniczej (0.0 ~ 4095.0)

   * - std_AO_tool
     - DOUBLE
     - Wyjście analogowe AO1 narzędzia (0.0 ~ 4095.0)

   * - robot_mode
     - UINT8
     - Tryb robota (0-automatyczny; 1-ręczny)

   * - collision_level
     - UINT8_6
     - Poziom kolizji stawów 1-6 (1 ~ 10)

   * - speed_scaling_man
     - DOUBLE
     - Procent prędkości w trybie ręcznym (0 ~ 100)

   * - speed_scaling_auto
     - DOUBLE
     - Procent prędkości w trybie automatycznym (0 ~ 100)

   * - program_state
     - UINT8
     - Stan działania programu robota (1-zatrzymany; 2-w ruchu; 3-wstrzymany; 4-przeciąganie)

   * - line_number
     - INT32
     - Numer bieżącej linii wykonywanego programu

   * - payload
     - DOUBLE
     - Masa ładunku (kg)

   * - pay_cog
     - DOUBLE_3
     - Środek ciężkości ładunku (x, y, z) (mm)

   * - motion_queue_len
     - INT32
     - Długość bieżącej kolejki ruchu
   
   * - ft_sensor_data
     - DOUBLE_6
     - Surowe dane czujnika siły

   * - main_code
     - INT32
     - Główny kod usterki

   * - sub_code
     - INT32
     - Podrzędny kod usterki

   * - emergency_stop
     - UINT8
     - Stan awaryjnego zatrzymania

   * - motion_done
     - INT32
     - Stan ukończenia ruchu

   * - timestamp_us
     - UINT64
     - Czas systemowy robota (µs)

   * - output_BIT_reg_8xX
     - UINT8_X
     - Rejestry wyjściowe robota typu BIT (8xX oznacza liczbę rejestrów, jeśli potrzebujesz 16 rejestrów wyjściowych typu BIT, rzeczywista nazwa to: „output_BIT_reg_8x2”, robot obsługuje maksymalnie 128 rejestrów wyjściowych typu BIT)

   * - output_INT_reg_X
     - INT32_X
     - Rejestry wyjściowe robota typu INT (X oznacza liczbę rejestrów, jeśli potrzebujesz 16 rejestrów wyjściowych typu INT, rzeczywista nazwa to: „output_INT_reg_16”, robot obsługuje maksymalnie 64 rejestry wyjściowe typu INT)

   * - output_DOUBLE_reg_X
     - DOUBLE_X
     - Rejestry wyjściowe robota typu DOUBLE (X oznacza liczbę rejestrów, jeśli potrzebujesz 16 rejestrów wyjściowych typu DOUBLE, rzeczywista nazwa to: „output_DOUBLE_reg_16”, robot obsługuje maksymalnie 64 rejestry wyjściowe typu DOUBLE)

   * - servoj_time
     - UINT64_5
     - Dane znacznika czasu servoj, jednostka nanosekundy

   * - actual_joint_temp
     - DOUBLE_6
     - Temperatura napędów stawów j1-j6, jednostka °

   * - axle_gen_com_data
     - UINT8_130
     - Ogólne dane okresowe końcówki

   * - abnormal_stop
     - UINT8
     - Stan nieprawidłowy, 0: brak nieprawidłowości, 1: występuje nieprawidłowość

   * - cur_lua_file_name
     - UINT8_256
     - Nazwa bieżącego pliku lua

   * - prog_total_line
     - UINT8
     - Całkowita liczba linii bieżącego pliku

   * - safety_box_signal
     - UINT8_6
     - Sygnały przycisków panelu przyciskowego 0: naciśnięty 1: zwolniony

   * - welding_voltage
     - DOUBLE
     - Rzeczywiste napięcie spawania, jednostka V

   * - welding_current
     - DOUBLE
     - Rzeczywisty prąd spawania, jednostka A

   * - welding_track_speed
     - DOUBLE
     - Prędkość śledzenia spoiny mm/s

   * - tpd_exception
     - UINT8
     - Wyjątek TPD

   * - alarm_reboot_robot
     - UINT8
     - Ostrzeżenie o ponownym uruchomieniu robota

   * - modbus_master_connect
     - UINT8
     - | Stan połączenia 8 masterów Modbus  
       | bit0-bit7 oznaczają masterów 0-7, 0-odłączony, 1-połączony

   * - modbus_slave_connect
     - UINT8
     - Stan połączenia slave Modbus 0-odłączony 1-połączony

   * - btn_box_stop_signal
     - UINT8
     - Sygnał przycisku awaryjnego zatrzymania

   * - drag_alarm
     - UINT8
     - Ostrzeżenie przeciągania

   * - safety_door_alarm
     - UINT8
     - Ostrzeżenie drzwi bezpieczeństwa, 0 brak ostrzeżenia, 1 drzwi bezpieczeństwa wyzwolone

   * - safety_plane_alarm
     - UINT8
     - Ostrzeżenie ściany bezpieczeństwa, 0 brak ostrzeżenia, 1 wejście w ścianę bezpieczeństwa

   * - motion_alarm
     - UINT8
     - | Ostrzeżenie ruchu, 0-brak ostrzeżenia,
       | 1-Zbyt duża zmiana orientacji w instrukcji LIN,
       | 2-Przekroczenie prędkości TCP,
       | 3-Wystąpiła kolizja,
       | 4-Przekroczenie maksymalnej prędkości osi 1,
       | 5-Przekroczenie maksymalnej prędkości osi 2,
       | 6-Przekroczenie maksymalnej prędkości osi 3,
       | 7-Przekroczenie maksymalnej prędkości osi 4,
       | 8-Przekroczenie maksymalnej prędkości osi 5,
       | 9-Przekroczenie maksymalnej prędkości osi 6,
       | 10-Zbyt duże odchylenie między instrukcją a sprzężeniem zwrotnym stawu 1,
       | 11-Zbyt duże odchylenie między instrukcją a sprzężeniem zwrotnym stawu 2,
       | 12-Zbyt duże odchylenie między instrukcją a sprzężeniem zwrotnym stawu 3,
       | 13-Zbyt duże odchylenie między instrukcją a sprzężeniem zwrotnym stawu 4,
       | 14-Zbyt duże odchylenie między instrukcją a sprzężeniem zwrotnym stawu 5,
       | 15-Zbyt duże odchylenie między instrukcją a sprzężeniem zwrotnym stawu 6,
       | 16-Osobliwa pozycja,
       | 17-Adaptacja prędkości ruchu instrukcji LIN,
       | 18-Przekroczenie limitu czasu regulacji prędkości docelowej lub regulacja nieukończona,
       | 19-Nieudany ruch wstawiania obrotowego,
       | 20-Nieudany ruch wstawiania spiralnego,
       | 21-Nieudany ruch wstawiania liniowego,
       | 22-Nieudany ruch lokalizacji powierzchni

   * - interfere_alarm
     - UINT8
     - Ostrzeżenie strefy interferencji, 0 brak ostrzeżenia, 1 wejście w strefę interferencji

   * - udp_cmd_state
     - INT32
     - Stan połączenia UDP

   * - weld_ready_state
     - UINT8
     - Stan gotowości spawarki, 1: gotowa, 0: błąd spawarki

   * - alarm_check_emerg_stop_btn
     - UINT8
     - Ostrzeżenie o nieprawidłowej komunikacji stawów

   * - ts_tm_cmd_com_error
     - UINT8
     - Błąd instrukcji systemu momentu obrotowego

   * - ts_tm_state_com_error
     - UINT8
     - Błąd stanu systemu momentu obrotowego

   * - ctrl_box_error
     - INT32
     - Błąd skrzynki sterowniczej

   * - safety_data_state
     - UINT8
     - Znacznik stanu danych bezpieczeństwa, 0 brak nieprawidłowości, 1-nieprawidłowość

   * - force_sensor_err_state
     - UINT8
     - Błąd przekroczenia limitu czasu połączenia czujnika siły; bit0-bit1 odpowiadają ID1-ID2 czujnika siły

   * - ctrl_open_lua_errcode
     - UINT8_4
     - Kod błędu protokołu otwartego kontrolera

   * - servo_id
     - UINT8
     - Numer ID serwonapędu

   * - servo_errcode
     - INT32
     - Kod usterki serwonapędu

   * - servo_state
     - INT32
     - Stan serwonapędu

   * - servo_actual_pos
     - DOUBLE
     - Bieżąca pozycja serwa

   * - servo_actual_speed
     - DOUBLE
     - Bieżąca prędkość serwa
   
   * - servo_actual_torque
     - DOUBLE
     - Bieżący moment obrotowy serwa
   
   * - gripper_active
     - INT32
     - Stan aktywacji chwytaka
   
   * - gripper_position
     - UINT8
     - Informacja zwrotna o pozycji chwytaka (procent)
   
   * - gripper_speed
     - INT32
     - Informacja zwrotna o prędkości chwytaka (procent)
   
   * - gripper_current
     - INT32
     - Informacja zwrotna o prądzie chwytaka (procent)
   
   * - gripper_temp
     - INT32
     - Bieżąca temperatura chwytaka, jednostka °
   
   * - gripper_voltage
     - INT32
     - Bieżące napięcie chwytaka, jednostka V
   
   * - rotating_gripper_num
     - DOUBLE
     - Informacja zwrotna o liczbie obrotów chwytaka obrotowego
   
   * - rotating_gripper_speed
     - UINT8
     - Informacja zwrotna o prędkości obrotowej chwytaka obrotowego (procent)
   
   * - rotating_gripper_tor
     - UINT8
     - Informacja zwrotna o momencie obrotowym chwytaka obrotowego (procent)
   
   * - weld_break_off_state
     - UINT8
     - Stan przerwania spawania: 0-spawanie nieprzerwane, 1-spawanie przerwane
   
   * - weld_arc_state
     - UINT8
     - Stan łuku spawalniczego 0-łuk nieprzerwany, 1-łuk przerwany
   
   * - smarttool_state
     - UINT32
     - Rozszerzone dane I/O końcówki (Smart-Tool)
   
   * - tool_coord
     - DOUBLE_6
     - Bieżąca pozycja narzędzia względem końcówki
   
   * - wobj_coord
     - DOUBLE_6
     - Bieżąca pozycja przedmiotu względem podstawy
   
   * - exTool_coord
     - DOUBLE_6
     - Bieżąca pozycja zewnętrznego narzędzia względem pozycji narzędzia
   
   * - exAxis_coord
     - DOUBLE_6
     - Bieżąca pozycja zewnętrznej osi względem podstawowego układu współrzędnych
   
   * - robot_state
     - UINT8
     - | Stan pracy robota,
       | 1. zatrzymany; 2. w ruchu; 3. wstrzymany; 4. przeciąganie
   
   * - actual_flange_pos
     - DOUBLE_6
     - Rzeczywista pozycja końcówki
   
   * - target_TCP_cmpvel
     - DOUBLE_2
     - Prędkość liniowa i orientacji instrukcji TCP, jednostka mm/s, °/s
   
   * - actual_TCP_cmpvel
     - DOUBLE_2
     - Rzeczywista prędkość liniowa i orientacji TCP, jednostka mm/s, °/s
   
   * - tool_id
     - INT32
     - Numer narzędzia
   
   * - wobj_id
     - INT32
     - Numer przedmiotu
   
   * - ft_sensor_raw_data
     - DOUBLE_6
     - Surowe dane siły/momentu końcowego - w układzie współrzędnych czujnika
   
   * - ft_sensor_active
     - UINT8
     - Stan aktywacji czujnika siły/momentu
   
   * - gripper_motion_done
     - UINT8
     - Ruch chwytaka zakończony
   
   * - collision_state
     - UINT8
     - Stan wykrywania kolizji
   
   * - trajectory_pnum
     - INT32
     - Bieżący numer punktu w ruchu dyskretnym
   
   * - safety_stop0_state
     - UINT8
     - Stan sygnału bezpiecznego zatrzymania SI0
   
   * - safety_stop1_state
     - UINT8
     - Stan sygnału bezpiecznego zatrzymania SI1
   
   * - gripper_fault_id
     - UINT8
     - Numer uszkodzonego chwytaka
   
   * - gripper_fault
     - INT32
     - Numer błędu chwytaka
   
   * - ext_DI_state
     - UINT8_16
     - Rozszerzone DI
   
   * - ext_DO_state
     - UINT8_16
     - Rozszerzone DO
   
   * - ext_AI_state
     - INT32_4
     - Rozszerzone AI
   
   * - ext_AO_state
     - INT32_4
     - Rozszerzone AO
   
   * - rbt_enable_state
     - INT32
     - Stan ukończenia załączenia napędu
   
   * - joint_driver_torque
     - DOUBLE_6
     - Rzeczywiste wartości momentu obrotowego stawów j1-j6, jednostka Nm
   
   * - robot_time
     - INT32_7
     - Czas systemowy robota, rok, miesiąc, dzień, godzina, minuta, sekunda, milisekunda
   
   * - software_upgrade_state
     - INT32
     - Stan aktualizacji oprogramowania robota
   
   * - end_lua_err_code
     - INT32
     - Stan sygnału przycisku końcowego
   
   * - wide_voltage_ctrl_box_temp
     - DOUBLE
     - Temperatura skrzynki sterowniczej szerokiego napięcia, jednostka °
   
   * - wide_voltage_ctrl_box_fan_current
     - INT32
     - Prąd wentylatora skrzynki sterowniczej szerokiego napięcia
   
   * - last_servoJ_target
     - DOUBLE_6
     - Pozycja ostatniej docelowej instrukcji servoJ
   
   * - servoJ_cmd_num
     - INT32
     - Licznik instrukcji servoJ
   
   * - strange_pos_flag
     - UINT8
     - Znacznik osobliwej pozycji
   
   * - alarm
     - UINT8
     - | Ostrzeżenie, 0-brak ostrzeżenia,
       | 1-Zmiana konfiguracji stawu barkowego,
       | 2-Zmiana konfiguracji stawu łokciowego,
       | 3-Zmiana konfiguracji stawu nadgarstkowego,
       | 4-Nieudana inicjalizacja RPY,
       | 5-Przekroczenie limitu czasu WaitDI,
       | 6-Przekroczenie limitu czasu WaitAI,
       | 7-Przekroczenie limitu czasu WaitToolDI,
       | 8-Przekroczenie limitu czasu WaitToolAI,
       | 9-Nieskonfigurowane DI pomyślnego zajarzenia łuku,
       | 10-Przekroczenie limitu czasu WaitAuxDI,
       | 11-Przekroczenie limitu czasu WaitAuxAI,
       | 12-Nieosiągalny punkt w trajektorii oscylacji,
       | 13-Nieudane obliczenie punktu chwytania śledzenia taśmociągu,
       | 14-Nieprawidłowe dane czujnika momentu obrotowego stawu
   
   * - dr_alarm
     - UINT8
     - | Ostrzeżenie napędu, 0-brak ostrzeżenia,
       | 1-Ostrzeżenie napędu osi 1, możliwe do zresetowania,
       | 2-Ostrzeżenie napędu osi 2, możliwe do zresetowania,
       | 3-Ostrzeżenie napędu osi 3, możliwe do zresetowania,
       | 4-Ostrzeżenie napędu osi 4, możliwe do zresetowania,
       | 5-Ostrzeżenie napędu osi 5, możliwe do zresetowania,
       | 6-Ostrzeżenie napędu osi 6, możliwe do zresetowania
   
   * - alive_slave_num_error
     - UINT8
     - Błąd liczby aktywnych stacji podrzędnych, 0-brak błędu, 1-błąd, niemożliwy do resetowania
   
   * - slave_com_error
     - UINT8_8
     - | Błąd komunikacji stacji podrzędnej, 0-brak błędu,
       | 1-Utrata połączenia ze stacją podrzędną,
       | 2-Stan stacji podrzędnej niezgodny z ustawioną wartością,
       | 3-Stacja podrzędna nieskonfigurowana,
       | 4-Błąd konfiguracji stacji podrzędnej,
       | 5-Błąd inicjalizacji stacji podrzędnej,
       | 6-Błąd inicjalizacji komunikacji e-mail stacji podrzędnej
   
   * - cmd_point_error
     - UINT8
     - | Błąd punktu instrukcji, 0-brak błędu,
       | 1-Błąd punktu instrukcji stawu,
       | 2-Błąd punktu docelowego linii,
       | 3-Błąd punktu pośredniego łuku,
       | 4-Błąd punktu docelowego łuku,
       | 5-Odstęp między punktami łuku zbyt mały,
       | 6-Błąd punktu pośredniego 1 okręgu/linii śrubowej,
       | 7-Błąd punktu pośredniego 2 okręgu/linii śrubowej,
       | 8-Błąd punktu pośredniego 3 okręgu/linii śrubowej,
       | 9-Odstęp między punktami okręgu/linii śrubowej zbyt mały,
       | 10-Błąd punktu instrukcji TPD,
       | 11-Niezgodność narzędzia instrukcji TPD z bieżącym narzędziem,
       | 12-Zbyt duże odchylenie między bieżącą instrukcją TPD a punktem początkowym następnej instrukcji,
       | 13-Błąd przełączania narzędzia wewnętrznego/zewnętrznego,
       | 14-Błąd punktu początkowego nowej linii śrubowej,
       | 15-Błąd punktu instrukcji nowej krzywej średniej,
       | 17-Przekroczenie limitu instrukcji stawu PTP,
       | 18-Przekroczenie limitu instrukcji stawu TPD,
       | 19-Przekroczenie limitu instrukcji stawu LIN/ARC,
       | 20-Przekroczenie prędkości w przestrzeni kartezjańskiej,
       | 21-Przekroczenie limitu instrukcji momentu obrotowego w przestrzeni stawów,
       | 22-Przekroczenie limitu instrukcji stawu JOG,
       | 23-Przekroczenie limitu prędkości instrukcji w przestrzeni stawu dla osi 1,
       | 24-Przekroczenie limitu prędkości instrukcji w przestrzeni stawu dla osi 2,
       | 25-Przekroczenie limitu prędkości instrukcji w przestrzeni stawu dla osi 3,
       | 26-Przekroczenie limitu prędkości instrukcji w przestrzeni stawu dla osi 4,
       | 27-Przekroczenie limitu prędkości instrukcji w przestrzeni stawu dla osi 5,
       | 28-Przekroczenie limitu prędkości instrukcji w przestrzeni stawu dla osi 6,
       | 29-Przekroczenie limitu prędkości sprzężenia zwrotnego stawu,
       | 30-Zbyt duże odchylenie między instrukcją a sprzężeniem zwrotnym stawu,
       | 31-Błąd punktu docelowego DMP (w tym niezgodność narzędzia),
       | 32-Przekroczenie limitu prędkości TCP,
       | 33-Zmiana konfiguracji stawu w następnej instrukcji,
       | 34-Zmiana konfiguracji stawu w bieżącej instrukcji,
       | 35-Przekroczenie limitu prędkości stawu w instrukcji LIN,
       | 36-Przekroczenie progu prędkości adaptacyjnej w instrukcji LIN,
       | 37-Nieosiągalny punkt w trajektorii,
       | 38-Nieosiągalny punkt w trajektorii - osobliwa pozycja,
       | 49-ARCSTART i ARCEND nie pozwalają na instrukcje PTP i SPTP,
       | 50-WEAVESTART i WEAVEEND nie pozwalają na instrukcje PTP i SPTP,
       | 51-Błąd parametrów spawania z oscylacją,
       | 52-Odstęp między punktami instrukcji spawania z oscylacją zbyt mały,
       | 53-Nieosiągalny punkt w trajektorii oscylacji - osobliwa pozycja,
       | 54-Nieosiągalny punkt w trajektorii oscylacji - przekroczenie limitu instrukcji stawu,
       | 55-Nieosiągalny punkt w trajektorii oscylacji - błąd planowania (zgodność kierunku Z narzędzia z kierunkiem X ruchu do przodu),
       | 56-Nieosiągalny punkt w trajektorii oscylacji - błąd punktu pośredniego łuku,
       | 65-Zbyt duże odchylenie instrukcji czujnika laserowego,
       | 66-Przrwanie instrukcji czujnika laserowego, przedwczesne zakończenie śledzenia spoiny,
       | 81-Przekroczenie limitu prędkości instrukcji zewnętrznej osi,
       | 82-Zbyt duże odchylenie między instrukcją a sprzężeniem zwrotnym zewnętrznej osi,
       | 83-Przerwanie komunikacji z rozszerzonym urządzeniem peryferyjnym (zewnętrzna oś/IO),
       | 84-Nieprawidłowa utrata pakietów w komunikacji z rozszerzonym urządzeniem peryferyjnym (zewnętrzna oś/IO),
       | 85-Przekroczenie limitu prędkości instrukcji w przestrzeni stawu dla zewnętrznej osi 1,
       | 86-Przekroczenie limitu prędkości instrukcji w przestrzeni stawu dla zewnętrznej osi 2,
       | 87-Przekroczenie limitu prędkości instrukcji w przestrzeni stawu dla zewnętrznej osi 3,
       | 88-Przekroczenie limitu prędkości instrukcji w przestrzeni stawu dla zewnętrznej osi 4,
       | 89-Błąd komunikacji EtherCAT z rozszerzonym urządzeniem peryferyjnym (zewnętrzna oś/IO),
       | 90-Błąd komunikacji Canopen z rozszerzonym urządzeniem peryferyjnym (zewnętrzna oś/IO),
       | 97-Śledzenie taśmociągu - zbyt duża zmiana orientacji między punktem początkowym a punktem odniesienia,
       | 113-Sterowanie stałą siłą - przekroczenie maksymalnej odległości regulacji w kierunku X,
       | 114-Sterowanie stałą siłą - przekroczenie maksymalnej odległości regulacji w kierunku Y,
       | 115-Sterowanie stałą siłą - przekroczenie maksymalnej odległości regulacji w kierunku Z,
       | 116-Sterowanie stałą siłą - przekroczenie maksymalnego kąta regulacji w kierunku RX,
       | 117-Sterowanie stałą siłą - przekroczenie maksymalnego kąta regulacji w kierunku RY,
       | 118-Sterowanie stałą siłą - przekroczenie maksymalnego kąta regulacji w kierunku RZ,
       | 119-Błąd danych zewnętrznego czujnika,
       | 120-Nieudana próba ruchu eksploracyjnego po linii śrubowej,
       | 121-Nieudany ruch wstawiania obrotowego,
       | 122-Nieudany ruch wstawiania liniowego,
       | 123-Nieudany ruch lokalizacji powierzchni,
       | 124-Nieprawidłowa siła przeciągania, nieudane wejście w tryb przeciągania,
       | 129-Przekroczenie maksymalnej liczby punktów rejestracji momentu obrotowego,
       | 130-Błąd przełączania prędkości,
       | 131-Przekroczenie limitu kierunku narzędzia,
       | 132-Przekroczenie limitu pędu,
       | 133-Przekroczenie limitu mocy,
       | 134-Nieprawidłowość diagnostyki STL-Flash,
       | 135-Nieprawidłowość diagnostyki STL-RAM,
       | 136-Nieprawidłowość diagnostyki STL-CPU,
       | 137-Nieprawidłowe dane bezpieczeństwa II-ECAT płyty bezpieczeństwa,
       | 138-Nieprawidłowe dane bezpieczeństwa ECAT osi 1,
       | 139-Nieprawidłowe dane bezpieczeństwa ECAT osi 2,
       | 140-Nieprawidłowe dane bezpieczeństwa ECAT osi 3,
       | 141-Nieprawidłowe dane bezpieczeństwa ECAT osi 4,
       | 142-Nieprawidłowe dane bezpieczeństwa ECAT osi 5,
       | 143-Nieprawidłowe dane bezpieczeństwa ECAT osi 6,
       | 145-Nieprawidłowa komunikacja między płytą bezpieczeństwa a kontrolerem,
       | 147-Błąd śledzenia ogniska,
       | 148-Przekroczenie limitu prędkości orientacji,
       | 149-Nieprawidłowe sprzężenie zwrotne słowa stanu stawu
   
   * - IO_error
     - UINT8
     - | Błąd I/O, 0-brak błędu,
       | 1-Błąd kanału, możliwy do zresetowania,
       | 2-Błąd wartości, możliwy do zresetowania,
       | 3-Przekroczenie czasu oczekiwania WaitDI, możliwy do zresetowania,
       | 4-Przekroczenie czasu oczekiwania WaitAI, możliwy do zresetowania,
       | 5-Przekroczenie czasu oczekiwania WaitAxleDI, możliwy do zresetowania,
       | 6-Przekroczenie czasu oczekiwania WaitAxleAI, możliwy do zresetowania,
       | 7-Błąd funkcji skonfigurowanej dla kanału, możliwy do zresetowania,
       | 8-Przekroczenie czasu łuku początkowego, możliwy do zresetowania,
       | 9-Przekroczenie czasu łuku końcowego, możliwy do zresetowania,
       | 10-Przekroczenie czasu pozycjonowania, możliwy do zresetowania,
       | 11-Przekroczenie czasu wykrywania IO taśmociągu, możliwy do zresetowania,
       | 12-Przekroczenie czasu oczekiwania WaitAuxDI, możliwy do zresetowania,
       | 13-Przekroczenie czasu oczekiwania WaitAuxAI, możliwy do zresetowania,
       | 14-Przekroczenie czasu pozycjonowania drutu spawalniczego, możliwy do zresetowania
   
   * - gripper_error
     - UINT8
     - Błąd chwytaka, 0-brak błędu, 1-błąd przekroczenia czasu ruchu chwytaka, możliwy do zresetowania
   
   * - file_error
     - UINT8
     - | Błąd pliku konfiguracyjnego, 0-brak błędu,
       | 1-Błąd wersji pliku konfiguracyjnego zbt, błąd inicjalizacji - niemożliwy do resetowania,
       | 2-Nieudane ładowanie pliku konfiguracyjnego zbt, błąd inicjalizacji - niemożliwy do resetowania,
       | 3-Błąd wersji pliku konfiguracyjnego user, błąd inicjalizacji - niemożliwy do resetowania,
       | 4-Nieudane ładowanie pliku konfiguracyjnego user, błąd inicjalizacji - niemożliwy do resetowania,
       | 5-Błąd wersji pliku konfiguracyjnego exaxis, błąd inicjalizacji - niemożliwy do resetowania,
       | 6-Nieudane ładowanie pliku konfiguracyjnego exaxis, błąd inicjalizacji - niemożliwy do resetowania,
       | 7-Niezgodność modelu robota, wymagane ponowne ustawienie - niemożliwy do resetowania,
       | 8-Błąd wersji pliku konfiguracyjnego dhpara, błąd inicjalizacji - niemożliwy do resetowania,
       | 9-Nieudane ładowanie pliku konfiguracyjnego dhpara, błąd inicjalizacji - niemożliwy do resetowania,
       | 10-Model robota nieustawiony - niemożliwy do resetowania,
       | 11-Błąd wersji pliku konfiguracyjnego load, błąd inicjalizacji - niemożliwy do resetowania,
       | 12-Nieudane ładowanie pliku konfiguracyjnego load, błąd inicjalizacji - niemożliwy do resetowania,
       | 13-Błąd wersji pliku konfiguracyjnego speed, błąd inicjalizacji - niemożliwy do resetowania,
       | 14-Nieudane ładowanie pliku konfiguracyjnego speed, błąd inicjalizacji - niemożliwy do resetowania,
       | 15-Błąd wersji pliku konfiguracyjnego weavepara, błąd inicjalizacji - niemożliwy do resetowania,
       | 16-Nieudane ładowanie pliku konfiguracyjnego weavepara, błąd inicjalizacji - niemożliwy do resetowania
   
   * - para_error
     - UINT8
     - | Błąd parametru konfiguracyjnego, 0-brak błędu,
       | 1-Błąd przekroczenia limitu numeru narzędzia - możliwy do zresetowania,
       | 2-Błąd progu ukończenia pozycjonowania - możliwy do zresetowania,
       | 3-Błąd poziomu kolizji - możliwy do zresetowania,
       | 4-Błąd masy ładunku - możliwy do zresetowania,
       | 5-Błąd X środka ciężkości ładunku - możliwy do zresetowania,
       | 6-Błąd Y środka ciężkości ładunku - możliwy do zresetowania,
       | 7-Błąd Z środka ciężkości ładunku - możliwy do zresetowania,
       | 8-Błąd czasu filtrowania DI - możliwy do zresetowania,
       | 9-Błąd czasu filtrowania AxleDI - możliwy do zresetowania,
       | 10-Błąd czasu filtrowania AI - możliwy do zresetowania,
       | 11-Błąd czasu filtrowania AxleAI - możliwy do zresetowania,
       | 12-Błąd zakresu wysokiego/niskiego poziomu DI - możliwy do zresetowania,
       | 13-Błąd zakresu wysokiego/niskiego poziomu DO - możliwy do zresetowania,
       | 14-Błąd przekroczenia limitu numeru przedmiotu - możliwy do zresetowania,
       | 15-Błąd przekroczenia limitu numeru zewnętrznej osi - możliwy do zresetowania,
       | 16-Błąd kanału enkodera śledzenia taśmociągu - możliwy do zresetowania,
       | 17-Błąd numeru osi przedmiotu śledzenia taśmociągu - możliwy do zresetowania,
       | 18-Błąd instalacji FR30L - nieprawidłowa instalacja normalna - możliwy do zresetowania
   
   * - exaxis_out_slimit_error
     - UINT8
     - | Błąd miękkiego limitu zewnętrznej osi, 0-brak błędu,
       | 1-Błąd przekroczenia miękkiego limitu zewnętrznej osi 1, możliwy do zresetowania,
       | 2-Błąd przekroczenia miękkiego limitu zewnętrznej osi 2, możliwy do zresetowania,
       | 3-Błąd przekroczenia miękkiego limitu zewnętrznej osi 3, możliwy do zresetowania,
       | 4-Błąd przekroczenia miękkiego limitu zewnętrznej osi 4, możliwy do zresetowania,
       | 5-Błąd przekroczenia miękkiego limitu zewnętrznej osi 5, możliwy do zresetowania,
       | 6-Błąd przekroczenia miękkiego limitu zewnętrznej osi 6, możliwy do zresetowania
   
   * - dr_com_err
     - UINT8_6
     - Błąd komunikacji napędu, 0-brak błędu, 1-błąd
   
   * - dr_err
     - UINT8
     - | Błąd napędu, 0-brak błędu,
       | 1-Błąd napędu osi 1, niemożliwy do resetowania,
       | 2-Błąd napędu osi 2, niemożliwy do resetowania,
       | 3-Błąd napędu osi 3, niemożliwy do resetowania,
       | 4-Błąd napędu osi 4, niemożliwy do resetowania,
       | 5-Błąd napędu osi 5, niemożliwy do resetowania,
       | 6-Błąd napędu osi 6, niemożliwy do resetowania
   
   * - out_sflimit_err
     - UINT8
     - | Błąd miękkiego limitu, 0-brak błędu,
       | 1-Błąd przekroczenia miękkiego limitu osi 1, możliwy do zresetowania,
       | 2-Błąd przekroczenia miękkiego limitu osi 2, możliwy do zresetowania,
       | 3-Błąd przekroczenia miękkiego limitu osi 3, możliwy do zresetowania,
       | 4-Błąd przekroczenia miękkiego limitu osi 4, możliwy do zresetowania,
       | 5-Błąd przekroczenia miękkiego limitu osi 5, możliwy do zresetowania,
       | 6-Błąd przekroczenia miękkiego limitu osi 6, możliwy do zresetowania

.. centered:: Tabela 1-2 Funkcje konfiguracji wejść sterowania robotem

.. list-table::
   :widths: 20 40 80
   :header-rows: 0
   :align: center
   :class: sheet-center

   * - **Nazwa**
     - **Typ danych**
     - **Opis**

   * - speed_mask
     - UINT8
     - Maska ustawienia prędkości globalnej: 0-nieaktywne; 1-aktywne

   * - speed
     - UINT8
     - Ustawienie prędkości globalnej (0-100)

   * - std_DO_mask
     - UINT8
     - Maska sterowania standardowym wyjściem DO skrzynki sterowniczej (bit0 ~ bit7 oznaczają DO0 ~ DO7)

   * - std_DO_box
     - UINT8
     - Standardowe wyjście DO skrzynki sterowniczej (bit0 ~ bit7 oznaczają DO0 ~ DO7)

   * - cfg_DO_mask
     - UINT8
     - Maska sterowania konfigurowalnym wyjściem CO skrzynki sterowniczej (bit0 ~ bit7 oznaczają CO0 ~ CO7)

   * - cfg_DO_box
     - UINT8
     - Konfigurowalne wyjście CO skrzynki sterowniczej (bit0 ~ bit7 oznaczają CO0 ~ CO7)

   * - cfg_DO_tool_mask
     - UINT8
     - Maska sterowania standardowym wyjściem DO narzędzia skrzynki sterowniczej (bit0 ~ bit1 oznaczają toolDO0 ~ toolDO1)

   * - cfg_DO_tool
     - UINT8
     - Standardowe wyjście DO narzędzia skrzynki sterowniczej (bit0 ~ bit1 oznaczają toolDO0 ~ toolDO1)

   * - std_AO_mask
     - UINT8
     - Maska sterowania wyjściem analogowym robota (bit0 ~ bit1 oznaczają AO0 ~ AO1 skrzynki sterowniczej; bit2 oznacza AO0 narzędzia)

   * - std_AO0_box
     - DOUBLE
     - Wyjście analogowe AO0 skrzynki sterowniczej (0.0 ~ 4095.0)

   * - std_AO1_box
     - DOUBLE
     - Wyjście analogowe AO1 skrzynki sterowniczej (0.0 ~ 4095.0)

   * - std_AO0_tool
     - DOUBLE
     - Wyjście analogowe AO1 narzędzia (0.0 ~ 4095.0)

   * - input_BIT_reg_8xX
     - UINT8_X
     - Rejestry wejściowe robota typu BIT (8xX oznacza liczbę rejestrów, jeśli potrzebujesz 16 rejestrów wejściowych typu BIT, rzeczywista nazwa to: „input_BIT_reg_8x2”, robot obsługuje maksymalnie 128 rejestrów typu BIT)

   * - input_INT_reg_X
     - INT32_X
     - Rejestry wejściowe robota typu INT (X oznacza liczbę rejestrów, jeśli potrzebujesz 16 rejestrów wejściowych typu INT, rzeczywista nazwa to: „input_INT_reg_16”, robot obsługuje maksymalnie 64 rejestry typu INT)
  
   * - input_DOUBLE_reg_X
     - DOUBLE_X
     - Rejestry wejściowe robota typu DOUBLE (X oznacza liczbę rejestrów, jeśli potrzebujesz 16 rejestrów wejściowych typu DOUBLE, rzeczywista nazwa to: „input_DOUBLE_reg_16”, robot obsługuje maksymalnie 64 rejestry typu DOUBLE)

.. centered:: Tabela 1-3 Odpowiedniość typów danych i długości bajtowych

.. list-table::
   :widths: 60 40
   :header-rows: 0
   :align: center
   :class: sheet-center

   * - **Typ danych**
     - **Długość bajtowa**

   * - UINT8
     - 1

   * - INT32
     - 4

   * - DOUBLE
     - 8

   * - UINT8_X
     - 1*X

   * - INT32_X
     - 4*X

   * - DOUBLE_X
     - 8*X