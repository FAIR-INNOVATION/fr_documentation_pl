Opis struktur danych
====================

.. toctree:: 
    :maxdepth: 5

Typ struktury pakietu sprzężenia zwrotnego stanu robota
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: python
    :linenos:

    class ROBOT_AUX_STATE(Structure):
        _pack_ = 1
        _fields_ = [
            ("servoId", c_uint8),         # Numer ID serwonapędu
            ("servoErrCode", c_int),     # Kod błędu serwonapędu
            ("servoState", c_int),       # Stan serwonapędu
            ("servoPos", c_double),      # Bieżąca pozycja serwonapędu
            ("servoVel", c_float),       # Bieżąca prędkość serwonapędu
            ("servoTorque", c_float),    # Bieżący moment obrotowy serwonapędu
        ]

    class EXT_AXIS_STATUS(Structure):
        _pack_ = 1
        _fields_ = [
            ("pos", c_double),        # Pozycja osi rozszerzenia
            ("vel", c_double),        # Prędkość osi rozszerzenia
            ("errorCode", c_int),     # Kod błędu osi rozszerzenia
            ("ready", c_uint8),        # Serwonapęd gotowy
            ("inPos", c_uint8),        # Serwonapęd na pozycji
            ("alarm", c_uint8),        # Alarm serwonapędu
            ("flerr", c_uint8),        # Błąd śledzenia
            ("nlimit", c_uint8),       # Osiągnięto ujemnego ograniczenia
            ("pLimit", c_uint8),       # Osiągnięto dodatniego ograniczenia
            ("mdbsOffLine", c_uint8),  # Utrata połączenia magistrali 485 sterownika
            ("mdbsTimeout", c_uint8),  # Przekroczenie czasu komunikacji 485 między kartą sterującą a skrzynką kontrolną
            ("homingStatus", c_uint8), # Stan powrotu do zera osi rozszerzenia
        ]

    class WELDING_BREAKOFF_STATE(Structure):
        _pack_ = 1
        _fields_ = [
            ("breakOffState", c_uint8),        # Stan przerwania spawania
            ("weldArcState", c_uint8),        # Stan przerwania łuku spawalniczego
        ]

    # ==================== Pełna struktura stanu robota ====================
    class RobotStatePkg(Structure):
        """
        Pakiet danych sprzężenia zwrotnego stanu robota
        """
        _pack_ = 1
        _fields_ = [
            # Informacje nagłówka ramki
            ("frame_head", c_uint16),           # Nagłówek ramki, ustalony na 0x5A5A
            ("frame_cnt", c_uint8),             # Licznik ramek, licznik cykliczny 0-255
            ("data_len", c_uint16),             # Długość zawartości danych
            ("program_state", c_uint8),         # Stan wykonania programu, 1-zatrzymany; 2-działa; 3-wstrzymany
            ("robot_state", c_uint8),             # Stan ruchu robota, 1-zatrzymany; 2-działa; 3-wstrzymany; 4-przeciąganie
            ("main_code", c_int),               # Główny kod błędu
            ("sub_code", c_int),                # Podrzędny kod błędu
            ("robot_mode", c_uint8),            # Tryb robota, 1-tryb ręczny; 0-tryb automatyczny

            # Pozycje i prędkości przegubów
            ("jt_cur_pos", c_double * 6),       # Bieżące pozycje 6 przegubów, jednostka deg
            ("tl_cur_pos", c_double * 6),       # Bieżąca pozycja narzędzia [x,y,z,rx,ry,rz]
            ("flange_cur_pos", c_double * 6),   # Bieżąca pozycja kołnierza końcowego [x,y,z,rx,ry,rz]
            ("actual_qd", c_double * 6),        # Bieżące prędkości 6 przegubów, jednostka deg/s
            ("actual_qdd", c_double * 6),       # Bieżące przyspieszenia 6 przegubów, jednostka deg/s^2
            ("target_TCP_CmpSpeed", c_double * 2),  # Prędkość wypadkowa zadana TCP [pozycja mm/s, postawa deg/s]
            ("target_TCP_Speed", c_double * 6), # Prędkość zadana TCP [x,y,z,rx,ry,rz]
            ("actual_TCP_CmpSpeed", c_double * 2),  # Prędkość wypadkowa rzeczywista TCP [pozycja mm/s, postawa deg/s]
            ("actual_TCP_Speed", c_double * 6), # Prędkość rzeczywista TCP [x,y,z,rx,ry,rz]
            ("jt_cur_tor", c_double * 6),       # Bieżące momenty obrotowe 6 przegubów, jednostka N·m

            # Układy narzędzia i przedmiotu
            ("tool", c_int),                    # Numer zastosowanego układu narzędzia
            ("user", c_int),                    # Numer zastosowanego układu przedmiotu

            # Wejścia/wyjścia cyfrowe
            ("cl_dgt_output_h", c_uint8),       # Wyjście IO cyfrowego skrzynki kontrolnej 15-8
            ("cl_dgt_output_l", c_uint8),       # Wyjście IO cyfrowego skrzynki kontrolnej 7-0
            ("tl_dgt_output_l", c_uint8),       # Wyjście IO cyfrowego narzędzia 7-0, tylko bit0-bit1 są ważne
            ("cl_dgt_input_h", c_uint8),        # Wejście IO cyfrowego skrzynki kontrolnej 15-8
            ("cl_dgt_input_l", c_uint8),        # Wejście IO cyfrowego skrzynki kontrolnej 7-0
            ("tl_dgt_input_l", c_uint8),        # Wejście IO cyfrowego narzędzia 7-0, tylko bit0-bit1 są ważne

            # Wejścia/wyjścia analogowe 
            ("cl_analog_input", c_uint16 * 2),  # Wejście analogowe skrzynki kontrolnej [0],[1]
            ("tl_anglog_input", c_uint16),      # Wejście analogowe narzędzia

            # Czujnik momentu
            ("ft_sensor_raw_data", c_double * 6),   # Surowe dane czujnika momentu
            ("ft_sensor_data", c_double * 6),      # Dane czujnika momentu
            ("ft_sensor_active", c_uint8),          # Stan aktywacji czujnika momentu

            # Sygnały stanu
            ("EmergencyStop", c_uint8),         # Flaga zatrzymania awaryjnego, 0-brak zatrzymania awaryjnego, 1-zatrzymanie awaryjne wciśnięte
            ("motion_done", c_int),             # Sygnał osiągnięcia pozycji ruchu, 1-osiągnięto, 0-nie osiągnięto
            ("gripper_motiondone", c_uint8),    # Sygnał zakończenia ruchu chwytaka, 1-zakończono, 0-nie zakończono
            ("mc_queue_len", c_int),            # Długość kolejki instrukcji ruchu
            ("collisionState", c_uint8),        # Wykrycie kolizji, 1-kolizja, 0-brak kolizji
            ("trajectory_pnum", c_int),         # Numer punktu trajektorii
            ("safety_stop0_state", c_uint8),    # Sygnał bezpiecznego zatrzymania SI0
            ("safety_stop1_state", c_uint8),    # Sygnał bezpiecznego zatrzymania SI1

            # Informacje o chwytaku
            ("gripper_fault_id", c_uint8),      # Numer chwytaka z błędem
            ("gripper_fault", c_uint16),        # Usterka chwytaka
            ("gripper_active", c_uint16),      # Stan aktywacji chwytaka
            ("gripper_position", c_uint8),      # Pozycja chwytaka
            ("gripper_speed", c_int8),          # Prędkość chwytaka
            ("gripper_current", c_int8),        # Prąd chwytaka
            ("gripper_temp", c_int),            # Temperatura chwytaka
            ("gripper_voltage", c_int),         # Napięcie chwytaka

            # Stan osi rozszerzenia
            ("aux_axis_state", ROBOT_AUX_STATE * 25),    # Stan osi rozszerzenia 485 (25)
            ("extAxisStatus", EXT_AXIS_STATUS * 4), # Stan osi rozszerzenia UDP (4)

            # Stan rozszerzonych IO
            ("extDIState", c_uint16 * 8),       # Wejście rozszerzonego DI
            ("extDOState", c_uint16 * 8),       # Wyjście rozszerzonego DO
            ("extAIState", c_uint16 * 4),        # Wejście rozszerzonego AI
            ("extAOState", c_uint16 * 4),        # Wyjście rozszerzonego AO

            # Stan robota i przegubów
            ("rbtEnableState", c_int),                  # Stan włączenia robota
            ("jointDriverTorque", c_double * 6),        # Moment obrotowy sterownika przegubu robota
            ("jointDriverTemperature", c_double * 6),   # Temperatura sterownika przegubu robota

            # Czas robota
            #("robotTime", c_int * 7),             # Czas systemowy robota [rok,miesiąc, dzień, godzina, minuta, sekunda, ms]
            ("year", ctypes.c_uint16),  # Rok
            ("mouth", ctypes.c_uint8),  # Miesiąc
            ("day", ctypes.c_uint8),  # Dzień
            ("hour", ctypes.c_uint8),  # Godzina
            ("minute", ctypes.c_uint8),  # Minuta
            ("second", ctypes.c_uint8),  # Sekunda
            ("millisecond", ctypes.c_uint16),  # Milisekunda

            ("softwareUpgradeState", c_int),      # Stan aktualizacji oprogramowania robota
            ("endLuaErrCode", c_uint16),          # Stan wykonania LUA końcówki

            # Wyjścia analogowe
            ("cl_analog_output", c_uint16 * 2), # Wyjście analogowe skrzynki kontrolnej [0],[1]
            ("tl_analog_output", c_uint16),       # Wyjście analogowe narzędzia

            # Chwytak obrotowy
            ("gripperRotNum", c_float),         # Bieżąca liczba obrotów chwytaka obrotowego
            ("gripperRotSpeed", c_uint8),       # Bieżący procent prędkości obrotowej chwytaka obrotowego
            ("gripperRotTorque", c_uint8),      # Bieżący procent momentu obrotowego chwytaka obrotowego

            # Stan przerwania spawania - przy użyciu struktury
            ("weldingBreakOffState", WELDING_BREAKOFF_STATE),  # Stan przerwania spawania

            # Docelowy moment obrotowy przegubów
            ("jt_tgt_tor", c_double * 6),       # Docelowy moment obrotowy przegubów

            ("smartToolState", c_int),          # Stan przycisków uchwytu SmartTool
            ("wideVoltageCtrlBoxTemp", c_float),        # Temperatura szerokonapięciowej skrzynki kontrolnej
            ("wideVoltageCtrlBoxFanCurrent", c_uint16), # Prąd wentylatora szerokonapięciowej skrzynki kontrolnej (mA)

            # Wartości układów współrzędnych
            ("toolCoord", c_double * 6),        # Bieżące wartości układu narzędzia; x,y,z,rx,ry,rz
            ("wobjCoord", c_double * 6),        # Bieżące wartości układu przedmiotu; x,y,z,rx,ry,rz
            ("extoolCoord", c_double * 6),      # Bieżące wartości zewnętrznego układu narzędzia; x,y,z,rx,ry,rz
            ("exAxisCoord", c_double * 6),      # Bieżące wartości układu osi rozszerzenia; x,y,z,rx,ry,rz

            # Obciążenie
            ("load", c_double),                 # Masa obciążenia
            ("loadCog", c_double * 3),            # Środek ciężkości obciążenia

            # Instrukcje serwo
            ("lastServoTarget", c_double * 6),  # Ostatnia pozycja docelowa ServoJ w kolejce
            ("servoJCmdNum", c_int),            # Licznik instrukcji servoJ

            # Dane docelowe przegubów
            ("targetJointPos", c_double * 6),   # Instrukcje pozycji 6 przegubów, jednostka °
            ("targetJointVel", c_double * 6),   # Instrukcje prędkości 6 przegubów, jednostka °/s
            ("targetJointAcc", c_double * 6),   # Instrukcje przyspieszenia 6 przegubów, jednostka °/s2
            ("targetJointCurrent", c_double * 6), # Instrukcje prądu 6 przegubów, jednostka A
            ("actualJointCurrent", c_double * 6), # Bieżące prądy 6 przegubów, jednostka A
            ("actualTCPForce", c_double * 6),   # Moment na końcówce robota Nm; x,y,z,rx,ry,rz
            ("targetTCPPos", c_double * 6),     # Instrukcja pozycji TCP robota mm; x,y,z,rx,ry,rz

            ("collisionLevel", c_uint8 * 6),    # Poziom kolizji robota
            ("speedScaleManual", c_double),     # Procent prędkości globalnej w trybie ręcznym
            ("speedScaleAuto", c_double),       # Procent prędkości globalnej w trybie automatycznym
            ("luaLineNum", c_int),              # Bieżący numer linii wykonania programu lua
            ("abnomalStop", c_uint8),           # 0-brak nieprawidłowości; 1-występuje nieprawidłowość
            ("currentLuaFileName", c_uint8 * 256),  # Nazwa bieżącego działającego programu lua
            ("programTotalLine", c_uint8),      # Całkowita liczba linii programu lua
            ("safetyBoxSingal", c_uint8 * 6),   # Stan przycisków na puszce przyciskowej robota

            # Dane spawalnicze
            ("weldVoltage", c_double),          # Napięcie spawania V
            ("weldCurrent", c_double),          # Prąd spawania
            ("weldTrackVel", c_double),         # Prędkość śledzenia spoiny mm/s

            ("tpdException", c_uint8),            # Przekroczenie limitu ładowania trajektorii TPD, 0-nie przekroczono, 1-przekroczono
            ("alarmRebootRobot", c_uint8),      # Ostrzeżenie, 1-zwolnij przycisk zatrzymania awaryjnego i wyłącz zasilanie skrzynki kontrolnej, 2-nieprawidłowość komunikacji przegubu, wyłącz zasilanie skrzynki kontrolnej
            ("modbusMasterConnect", c_uint8),   # bity bit0-bit7 odpowiadają stanom połączenia mastera 0-7 ModbusTCP
            ("modbusSlaveConnect", c_uint8),    # Stan połączenia slave ModbusTCP
            ("btnBoxStopSignal", c_uint8),      # Sygnał zatrzymania awaryjnego puszki przyciskowej
            ("dragAlarm", c_uint8),             # Ostrzeżenie przeciągania
            ("safetyDoorAlarm", c_uint8),       # Ostrzeżenie drzwi bezpieczeństwa
            ("safetyPlaneAlarm", c_uint8),      # Ostrzeżenie wejścia w ścianę bezpieczeństwa
            ("motonAlarm", c_uint8),            # Ostrzeżenie ruchu
            ("interfaceAlarm", c_uint8),        # Ostrzeżenie wejścia w strefę interferencji
            ("udpCmdState", c_int),             # Stan połączenia komunikacyjnego UDP portu 20007
            ("weldReadyState", c_uint8),        # Stan gotowości spawarki
            ("alarmCheckEmergStopBtn", c_uint8),    # 0-normalny; 1-nieprawidłowość komunikacji, sprawdź czy przycisk zatrzymania awaryjnego jest zwolniony
            ("tsTmCmdComError", c_uint8),       # 0-normalny; 1-niepowodzenie komunikacji instrukcji momentu
            ("tsTmStateComError", c_uint8),     # 0-normalny; 1-niepowodzenie komunikacji stanu momentu
            ("ctrlBoxError", c_int),            # Błąd skrzynki kontrolnej
            ("safetyDataState", c_uint8),       # Flaga stanu danych bezpieczeństwa
            ("forceSensorErrState", c_uint8),   # Błąd timeout połączenia czujnika siły
            ("ctrlOpenLuaErrCode", c_uint8 * 4),  # Kody błędów protokołu 4 urządzeń peryferyjnych kontrolera
            ("strangePosFlag", c_uint8),        # Flaga bieżącej osobliwej pozy
            ("alarm", c_uint8),                 # Ostrzeżenie
            ("driverAlarm", c_uint8),           # Numer osi z alarmem sterownika
            ("aliveSlaveNumError", c_uint8),    # Błąd liczby aktywnych węzłów podrzędnych
            ("slaveComError", c_uint8 * 8),     # Stan błędu węzła podrzędnego
            ("cmdPointError", c_uint8),         # Błąd punktu instrukcji
            ("IOError", c_uint8),               # Błąd IO
            ("gripperError", c_uint8),          # Błąd chwytaka
            ("fileError", c_uint8),             # Błąd pliku
            ("paraError", c_uint8),             # Błąd parametru
            ("exaxisOutLimitError", c_uint8),   # Błąd przekroczenia miękkiego ograniczenia osi zewnętrznej
            ("driverComError", c_uint8 * 6),    # Błąd komunikacji ze sterownikiem
            ("driverError", c_uint8),           # Numer osi z błędem komunikacji sterownika
            ("outSoftLimitError", c_uint8),     # Błąd przekroczenia miękkiego ograniczenia
            ("axleGenComData", c_uint8 * 130),   # Dane aperiodyczne ogólnej komunikacji osi
            ("socketConnTimeout", c_uint8),     # Przekroczenie czasu połączenia socket
            ("socketReadTimeout", c_uint8),     # Przekroczenie czasu odczytu socket
            ("tsWebStateComErr", c_uint8),      # Błąd komunikacji stanu TS_WEB
            ("exaxisCoordID", c_uint8),         # ID zewnętrznej osi rozszerzenia
            ("check_sum", c_uint16)          # Suma kontrolna
        ]

Pakiet danych sprzężenia zwrotnego stanu kontrolera
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. versionadded:: python SDK-v2.1.7
    
.. csv-table:: 
    :header-rows: 1
    :name: Pakiet danych sprzężenia zwrotnego stanu kontrolera
    :widths: 20 30

    "Zmienna","Znaczenie"
    "program_state","Stan wykonania programu, 1-zatrzymany; 2-działa; 3-wstrzymany"
    "robot_state","Stan ruchu robota, 1-zatrzymany; 2-działa; 3-wstrzymany; 4-przeciąganie"
    "main_code","Główny kod błędu"
    "sub_code",	Podrzędny kod błędu"
    "robot_mode","Tryb robota, 0-tryb automatyczny; 1-tryb ręczny"
    "jt_cur_pos[i]","Bieżąca pozycja przegubów, jednostka deg, i:0~5"
    "tl_cur_pos[i]","Bieżąca poza narzędzia, jednostka deg&mm, i:0~5"
    "flange_cur_pos[i]","Bieżąca poza kołnierza końcowego, jednostka deg&mm, i:0~5"
    "actual_qd[i]","Bieżąca prędkość przegubów robota, jednostka deg/s, i:0~5"
    "actual_qdd[i]","Bieżące przyspieszenie przegubów robota, jednostka deg/s^2, i:0~5"
    "target_TCP_CmpSpeed[i]","Prędkość wypadkowa zadana TCP robota, jednostka mm/s&deg/s, i:0~1"
    "target_TCP_Speed[i]","Prędkość zadana TCP robota, jednostka mm/s&deg/s, i:0~5"
    "actual_TCP_CmpSpeed[i]","Prędkość wypadkowa rzeczywista TCP robota, jednostka mm/s&deg/s, i:0~1"
    "actual_TCP_Speed[i]","Prędkość rzeczywista TCP robota, jednostka mm/s&deg/s, i:0~5"
    "jt_cur_tor[i]","Bieżący moment obrotowy, jednostka N·m, i:0~5"
    "tool","Numer zastosowanego układu narzędzia"
    "user","Numer zastosowanego układu przedmiotu"
    "cl_dgt_output_h","Wyjście IO cyfrowego skrzynki kontrolnej 15-8"
    "cl_dgt_output_l","Wyjście IO cyfrowego skrzynki kontrolnej 7-0"
    "tl_dgt_output_l","Wyjście IO cyfrowego narzędzia 7-0, tylko bit0-bit1 są ważne"
    "dgt_input_h","Wejście IO cyfrowego skrzynki kontrolnej 15-8"
    "cl_dgt_input_l","Wejście IO cyfrowego skrzynki kontrolnej 7-0"
    "tl_dgt_input_l","Wejście IO cyfrowego narzędzia 7-0, tylko bit0-bit1 są ważne"
    "cl_analog_input[i]","Wejście analogowe skrzynki kontrolnej, i:0~2"
    "tl_anglog_input","Wejście analogowe narzędzia"
    "ft_sensor_raw_data","Surowe dane czujnika momentu, jednostka N&Nm, i:0~5"
    "ft_sensor_data","Dane czujnika momentu, jednostka N&Nm, i:0~5"
    "ft_sensor_active","Stan aktywacji czujnika momentu, 0-reset, 1-aktywacja"
    "EmergencyStop","Flaga zatrzymania awaryjnego, 0-brak zatrzymania awaryjnego, 1-zatrzymanie awaryjne wciśnięte"
    "motion_done","Sygnał osiągnięcia pozycji ruchu, 1-osiągnięto, 0-nie osiągnięto"
    "gripper_motiondone","Sygnał zakończenia ruchu chwytaka, 1-zakończono, 0-nie zakończono"
    "mc_queue_len","Długość kolejki instrukcji ruchu"
    "collisionState","Wykrycie kolizji, 1-kolizja, 0-brak kolizji"
    "trajectory_pnum","Numer punktu trajektorii"
    "safety_stop0_state","Sygnał bezpiecznego zatrzymania SI0"
    "safety_stop1_state","Sygnał bezpiecznego zatrzymania SI1"
    "gripper_fault_id","Numer chwytaka z błędem"
    "gripper_fault","Usterka chwytaka"
    "gripper_active","Stan aktywacji chwytaka, 0-nieaktywny, 1-aktywny"
    "gripper_position","Pozycja chwytaka (procent)"
    "gripper_speed","Prędkość chwytaka (procent)"
    "gripper_current","Prąd chwytaka (procent)"
    "gripper_tmp","Temperatura chwytaka, jednostka ℃"
    "gripper_voltage","Napięcie chwytaka, jednostka V"
    "auxState.servoId","Oś rozszerzenia 485, numer ID serwonapędu, i:0~3"
    "auxState.servoErrCode","Oś rozszerzenia 485, kod błędu serwonapędu, i:0~3"
    "auxState.servoState","Oś rozszerzenia 485, stan serwonapędu, i:0~3"
    "auxState.servoPos","Oś rozszerzenia 485, bieżąca pozycja serwonapędu, i:0~3"
    "auxState.servoVel","Oś rozszerzenia 485, bieżąca prędkość serwonapędu, i:0~3"
    "auxState.servoTorque","Oś rozszerzenia 485, bieżący moment obrotowy serwonapędu, i:0~3"
    "extAxisStatus[i].pos","Oś rozszerzenia UDP, pozycja, i:0~3"
    "extAxisStatus[i].vel","Oś rozszerzenia UDP, prędkość, i:0~3"
    "extAxisStatus[i].errorCode","Oś rozszerzenia UDP, kod błędu, i:0~3"
    "extAxisStatus[i].ready","Oś rozszerzenia UDP, serwonapęd gotowy, i:0~3"
    "extAxisStatus[i].inPos","Oś rozszerzenia UDP, serwonapęd na pozycji, i:0~3"
    "extAxisStatus[i].alarm","Oś rozszerzenia UDP, alarm serwonapędu, i:0~3"
    "extAxisStatus[i].flerr","Oś rozszerzenia UDP, błąd śledzenia, i:0~3"
    "extAxisStatus[i].nlimit","Oś rozszerzenia UDP, osiągnięto ujemnego ograniczenia, i:0~3"
    "extAxisStatus[i].pLimit","Oś rozszerzenia UDP, osiągnięto dodatniego ograniczenia, i:0~3"
    "extAxisStatus[i].mdbsOffLine","Oś rozszerzenia UDP, utrata połączenia magistrali 485 sterownika"
    "extAxisStatus[i].mdbsTimeout","Oś rozszerzenia UDP, przekroczenie czasu komunikacji 485 między kartą sterującą a skrzynką kontrolną"
    "extAxisStatus[i].homingStatus","Oś rozszerzenia UDP, stan powrotu do zera"
    "extDIState","Stan rozszerzonego wejścia cyfrowego"
    "extDOState","Stan rozszerzonego wyjścia cyfrowego"
    "extAIState","Stan rozszerzonego wejścia analogowego"
    "extAOState","Stan rozszerzonego wyjścia analogowego"
    "rbtEnableState","Stan włączenia robota"
    "jointDriverTorque","Bieżący moment obrotowy sterownika przegubu"
    "jointDriverTemperature","Bieżąca temperatura sterownika przegubu"
    "year","Rok"
    "mouth","Miesiąc"
    "day","Dzień"
    "hour","Godzina"
    "minute","Minuta"
    "second","Sekunda"
    "millisecond","Milisekunda"
    "softwareUpgradeState","Stan aktualizacji oprogramowania robota"
    "endLuaErrCode","Stan wykonania LUA końcówki"
    "cl_analog_output[i]","Wyjście analogowe skrzynki kontrolnej, i:0~1"
    "tl_analog_output","Wyjście analogowe narzędzia"
    "gripperRotNum","Bieżąca liczba obrotów chwytaka obrotowego"
    "gripperRotSpeed","Bieżący procent prędkości obrotowej chwytaka obrotowego"
    "gripperRotTorque","Bieżący procent momentu obrotowego chwytaka obrotowego"
    "weldingBreakOffState","Stan przerwania spawania"
    "jt_tgt_tor","Docelowy moment obrotowy przegubów"
    "smartToolState","Stan przycisków uchwytu SmartTool"
    "wideVoltageCtrlBoxTemp","Temperatura szerokonapięciowej skrzynki kontrolnej"
    "wideVoltageCtrlBoxFanCurrent","Prąd wentylatora szerokonapięciowej skrzynki kontrolnej (ma)"
    "toolCoord[i]","Układ narzędzia, i:0~5"
    "wobjCoord[i]","Układ przedmiotu, i:0~5"
    "extoolCoord[i]","Zewnętrzny układ narzędzia, i:0~5"
    "exAxisCoord[i]","Układ osi rozszerzenia, i:0~5"
    "load","Masa obciążenia"
    "loadCog[i]","Środek ciężkości obciążenia, i:0~2"
    "lastServoTarget[i]","Ostatnia pozycja docelowa ServoJ w kolejce, i:0~5"
    "servoJCmdNum","Licznik instrukcji ServoJ"

Stan serwonapędu
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. versionadded:: python SDK-v2.1.3
    
.. csv-table:: 
    :header-rows: 1
    :name: Stan serwonapędu
    :widths: 20 30

    "Zmienna","Znaczenie"
    "servoId","Numer ID serwonapędu"
    "servoErrCode","Kod błędu serwonapędu"
    "servoState","Stan serwonapędu"
    "servoPos","Bieżąca pozycja serwonapędu"
    "servoVel","Bieżąca prędkość serwonapędu"
    "servoTorque","Bieżący moment obrotowy serwonapędu"

Stan osi rozszerzenia
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. versionadded:: python SDK-v2.1.3
    
.. csv-table:: 
    :header-rows: 1
    :name: Stan osi rozszerzenia
    :widths: 20 30

    "Zmienna","Znaczenie"
    "pos","Pozycja osi rozszerzenia"
    "vel","Prędkość osi rozszerzenia"
    "errorCode","Kod błędu osi rozszerzenia"
    "ready","Serwonapęd gotowy"
    "inPos","Serwonapęd na pozycji"
    "alarm","Alarm serwonapędu"
    "flerr","Błąd śledzenia"
    "nlimit","Osiągnięto ujemnego ograniczenia"
    "pLimit","Osiągnięto dodatniego ograniczenia"
    "mdbsOffLine","Utrata połączenia magistrali 485 sterownika"
    "mdbsTimeout","Przekroczenie czasu komunikacji 485 między kartą sterującą a skrzynką kontrolną"
    "homingStatus","Stan powrotu do zera osi rozszerzenia"

Stan przerwania spawania
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. versionadded:: python SDK-v2.1.3
    
.. csv-table:: 
    :header-rows: 1
    :name: Stan przerwania spawania
    :widths: 20 30

    "Zmienna","Znaczenie"
    "breakOffState","Stan przerwania spawania"
    "weldArcState","Stan przerwania łuku spawalniczego"

Przykład kodu
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    print("program_state:", robot.robot_state_pkg.program_state)
    print("robot_state:", robot.robot_state_pkg.robot_state)
    print("main_code:", robot.robot_state_pkg.main_code)
    print("sub_code:", robot.robot_state_pkg.sub_code)
    print("robot_mode:", robot.robot_state_pkg.robot_mode)
    print("jt_cur_pos0:", robot.robot_state_pkg.jt_cur_pos[0])
    print("jt_cur_pos1:", robot.robot_state_pkg.jt_cur_pos[1])
    print("jt_cur_pos2:", robot.robot_state_pkg.jt_cur_pos[2])
    print("jt_cur_pos3:", robot.robot_state_pkg.jt_cur_pos[3])
    print("jt_cur_pos4:", robot.robot_state_pkg.jt_cur_pos[4])
    print("jt_cur_pos5:", robot.robot_state_pkg.jt_cur_pos[5])
    print("tl_cur_pos0:", robot.robot_state_pkg.tl_cur_pos[0])
    print("tl_cur_pos1:", robot.robot_state_pkg.tl_cur_pos[1])
    print("tl_cur_pos2:", robot.robot_state_pkg.tl_cur_pos[2])
    print("tl_cur_pos3:", robot.robot_state_pkg.tl_cur_pos[3])
    print("tl_cur_pos4:", robot.robot_state_pkg.tl_cur_pos[4])
    print("tl_cur_pos5:", robot.robot_state_pkg.tl_cur_pos[5])
    print("flange_cur_pos0:", robot.robot_state_pkg.flange_cur_pos[0])
    print("flange_cur_pos1:", robot.robot_state_pkg.flange_cur_pos[1])
    print("flange_cur_pos2:", robot.robot_state_pkg.flange_cur_pos[2])
    print("flange_cur_pos3:", robot.robot_state_pkg.flange_cur_pos[3])
    print("flange_cur_pos4:", robot.robot_state_pkg.flange_cur_pos[4])
    print("flange_cur_pos5:", robot.robot_state_pkg.flange_cur_pos[5])
    print("actual_qd0:", robot.robot_state_pkg.actual_qd[0])
    print("actual_qd1:", robot.robot_state_pkg.actual_qd[1])
    print("actual_qd2:", robot.robot_state_pkg.actual_qd[2])
    print("actual_qd3:", robot.robot_state_pkg.actual_qd[3])
    print("actual_qd4:", robot.robot_state_pkg.actual_qd[4])
    print("actual_qd5:", robot.robot_state_pkg.actual_qd[5])
    print("actual_qdd0:", robot.robot_state_pkg.actual_qdd[0])
    print("actual_qdd1:", robot.robot_state_pkg.actual_qdd[1])
    print("actual_qdd2:", robot.robot_state_pkg.actual_qdd[2])
    print("actual_qdd3:", robot.robot_state_pkg.actual_qdd[3])
    print("actual_qdd4:", robot.robot_state_pkg.actual_qdd[4])
    print("actual_qdd5:", robot.robot_state_pkg.actual_qdd[5])
    print("target_TCP_CmpSpeed0:", robot.robot_state_pkg.target_TCP_CmpSpeed[0])
    print("target_TCP_CmpSpeed1:", robot.robot_state_pkg.target_TCP_CmpSpeed[1])
    print("target_TCP_Speed0:", robot.robot_state_pkg.target_TCP_Speed[0])
    print("target_TCP_Speed1:", robot.robot_state_pkg.target_TCP_Speed[1])
    print("target_TCP_Speed2:", robot.robot_state_pkg.target_TCP_Speed[2])
    print("target_TCP_Speed3:", robot.robot_state_pkg.target_TCP_Speed[3])
    print("target_TCP_Speed4:", robot.robot_state_pkg.target_TCP_Speed[4])
    print("target_TCP_Speed5:", robot.robot_state_pkg.target_TCP_Speed[5])
    print("actual_TCP_CmpSpeed0:", robot.robot_state_pkg.actual_TCP_CmpSpeed[0])
    print("actual_TCP_CmpSpeed1:", robot.robot_state_pkg.actual_TCP_CmpSpeed[1])
    print("actual_TCP_Speed0:", robot.robot_state_pkg.actual_TCP_Speed[0])
    print("actual_TCP_Speed1:", robot.robot_state_pkg.actual_TCP_Speed[1])
    print("actual_TCP_Speed2:", robot.robot_state_pkg.actual_TCP_Speed[2])
    print("actual_TCP_Speed3:", robot.robot_state_pkg.actual_TCP_Speed[3])
    print("actual_TCP_Speed4:", robot.robot_state_pkg.actual_TCP_Speed[4])
    print("actual_TCP_Speed5:", robot.robot_state_pkg.actual_TCP_Speed[5])
    print("jt_cur_tor0:", robot.robot_state_pkg.jt_cur_tor[0])
    print("jt_cur_tor1:", robot.robot_state_pkg.jt_cur_tor[1])
    print("jt_cur_tor2:", robot.robot_state_pkg.jt_cur_tor[2])
    print("jt_cur_tor3:", robot.robot_state_pkg.jt_cur_tor[3])
    print("jt_cur_tor4:", robot.robot_state_pkg.jt_cur_tor[4])
    print("jt_cur_tor5:", robot.robot_state_pkg.jt_cur_tor[5])
    print("tool:", robot.robot_state_pkg.tool)
    print("user:", robot.robot_state_pkg.user)
    print("cl_dgt_output_h:", robot.robot_state_pkg.cl_dgt_output_h)
    print("cl_dgt_output_l:", robot.robot_state_pkg.cl_dgt_output_l)
    print("tl_dgt_output_l:", robot.robot_state_pkg.tl_dgt_output_l)
    print("cl_dgt_input_h:", robot.robot_state_pkg.cl_dgt_input_h)
    print("cl_dgt_input_l:", robot.robot_state_pkg.cl_dgt_input_l)
    print("tl_dgt_input_l:", robot.robot_state_pkg.tl_dgt_input_l)
    print("cl_analog_input0:", robot.robot_state_pkg.cl_analog_input[0])
    print("cl_analog_input1:", robot.robot_state_pkg.cl_analog_input[1])
    print("tl_anglog_input:", robot.robot_state_pkg.tl_anglog_input)
    print("ft_sensor_raw_data0:", robot.robot_state_pkg.ft_sensor_raw_data[0])
    print("ft_sensor_raw_data1:", robot.robot_state_pkg.ft_sensor_raw_data[1])
    print("ft_sensor_raw_data2:", robot.robot_state_pkg.ft_sensor_raw_data[2])
    print("ft_sensor_raw_data3:", robot.robot_state_pkg.ft_sensor_raw_data[3])
    print("ft_sensor_raw_data4:", robot.robot_state_pkg.ft_sensor_raw_data[4])
    print("ft_sensor_raw_data5:", robot.robot_state_pkg.ft_sensor_raw_data[5])
    print("ft_sensor_data0:", robot.robot_state_pkg.ft_sensor_data[0])
    print("ft_sensor_data1:", robot.robot_state_pkg.ft_sensor_data[1])
    print("ft_sensor_data2:", robot.robot_state_pkg.ft_sensor_data[2])
    print("ft_sensor_data3:", robot.robot_state_pkg.ft_sensor_data[3])
    print("ft_sensor_data4:", robot.robot_state_pkg.ft_sensor_data[4])
    print("ft_sensor_data5:", robot.robot_state_pkg.ft_sensor_data[5])
    print("ft_sensor_active:", robot.robot_state_pkg.ft_sensor_active)
    print("EmergencyStop:", robot.robot_state_pkg.EmergencyStop)
    print("motion_done:", robot.robot_state_pkg.motion_done)
    print("gripper_motiondone:", robot.robot_state_pkg.gripper_motiondone)
    print("mc_queue_len:", robot.robot_state_pkg.mc_queue_len)
    print("collisionState:", robot.robot_state_pkg.collisionState)
    print("trajectory_pnum:", robot.robot_state_pkg.trajectory_pnum)
    print("safety_stop0_state:", robot.robot_state_pkg.safety_stop0_state)
    print("safety_stop1_state:", robot.robot_state_pkg.safety_stop1_state)
    print("gripper_fault_id:", robot.robot_state_pkg.gripper_fault_id)
    print("gripper_fault:", robot.robot_state_pkg.gripper_fault)
    print("gripper_active:", robot.robot_state_pkg.gripper_active)
    print("gripper_position:", robot.robot_state_pkg.gripper_position)
    print("gripper_speed:", robot.robot_state_pkg.gripper_speed)
    print("gripper_current:", robot.robot_state_pkg.gripper_current)
    print("gripper_tmp:", robot.robot_state_pkg.gripper_tmp)
    print("gripper_voltage:", robot.robot_state_pkg.gripper_voltage)
    print("auxState.servoId:", robot.robot_state_pkg.auxState.servoId)
    print("auxState.servoErrCode:", robot.robot_state_pkg.auxState.servoErrCode)
    print("auxState.servoState:", robot.robot_state_pkg.auxState.servoState)
    print("auxState.servoPos:", robot.robot_state_pkg.auxState.servoPos)
    print("auxState.servoVel:", robot.robot_state_pkg.auxState.servoVel)
    print("auxState.servoTorque:", robot.robot_state_pkg.auxState.servoTorque)
    for i in range(4):
        print("extAxisStatus.pos:", i,robot.robot_state_pkg.extAxisStatus[i].pos)
        print("extAxisStatus.vel:", i,robot.robot_state_pkg.extAxisStatus[i].vel)
        print("extAxisStatus.errorCode:", i,robot.robot_state_pkg.extAxisStatus[i].errorCode)
        print("extAxisStatus.ready:", i,robot.robot_state_pkg.extAxisStatus[i].ready)
        print("extAxisStatus.inPos:", i,robot.robot_state_pkg.extAxisStatus[i].inPos)
        print("extAxisStatus.alarm:", i,robot.robot_state_pkg.extAxisStatus[i].alarm)
        print("extAxisStatus.flerr:", i,robot.robot_state_pkg.extAxisStatus[i].flerr)
        print("extAxisStatus.nlimit:", i,robot.robot_state_pkg.extAxisStatus[i].nlimit)
        print("extAxisStatus.pLimit:", i,robot.robot_state_pkg.extAxisStatus[i].pLimit)
        print("extAxisStatus.mdbsOffLine:", i,robot.robot_state_pkg.extAxisStatus[i].mdbsOffLine)
        print("extAxisStatus.mdbsTimeout:", i,robot.robot_state_pkg.extAxisStatus[i].mdbsTimeout)
        print("extAxisStatus.homingStatus:", i,robot.robot_state_pkg.extAxisStatus[i].homingStatus)
    for i in range(8):
        print("extDIState:",i, robot.robot_state_pkg.extDIState[i])
        print("extDOState:", i,robot.robot_state_pkg.extDOState[i])
    for i in range(4):
        print("extAIState:", i,robot.robot_state_pkg.extAIState[i])
        print("extAOState:", robot.robot_state_pkg.extAOState[i])
    print("rbtEnableState:", robot.robot_state_pkg.rbtEnableState)
    print("jointDriverTorque0:", robot.robot_state_pkg.jointDriverTorque[0])
    print("jointDriverTorque1:", robot.robot_state_pkg.jointDriverTorque[1])
    print("jointDriverTorque2:", robot.robot_state_pkg.jointDriverTorque[2])
    print("jointDriverTorque3:", robot.robot_state_pkg.jointDriverTorque[3])
    print("jointDriverTorque4:", robot.robot_state_pkg.jointDriverTorque[4])
    print("jointDriverTorque5:", robot.robot_state_pkg.jointDriverTorque[5])
    print("jointDriverTemperature:", robot.robot_state_pkg.jointDriverTemperature[0])
    print("jointDriverTemperature:", robot.robot_state_pkg.jointDriverTemperature[1])
    print("jointDriverTemperature:", robot.robot_state_pkg.jointDriverTemperature[2])
    print("jointDriverTemperature:", robot.robot_state_pkg.jointDriverTemperature[3])
    print("jointDriverTemperature:", robot.robot_state_pkg.jointDriverTemperature[4])
    print("jointDriverTemperature:", robot.robot_state_pkg.jointDriverTemperature[5])
    print("year:", robot.robot_state_pkg.year)
    print("mouth:", robot.robot_state_pkg.mouth)
    print("day:", robot.robot_state_pkg.day)
    print("hour:", robot.robot_state_pkg.hour)
    print("minute:", robot.robot_state_pkg.minute)
    print("second:", robot.robot_state_pkg.second)
    print("millisecond:", robot.robot_state_pkg.millisecond)
    print("softwareUpgradeState:", robot.robot_state_pkg.softwareUpgradeState)
    print("endLuaErrCode:", robot.robot_state_pkg.endLuaErrCode)
    print("cl_analog_output[0]:", robot.robot_state_pkg.cl_analog_output[0])
    print("cl_analog_output[1]:", robot.robot_state_pkg.cl_analog_output[1])
    print("tl_analog_output:", robot.robot_state_pkg.tl_analog_output)
    print("gripperRotNum:", robot.robot_state_pkg.gripperRotNum)
    print("gripperRotSpeed:", robot.robot_state_pkg.gripperRotSpeed)
    print("gripperRotTorque:", robot.robot_state_pkg.gripperRotTorque)
    print("jt_tgt_tor:", robot.robot_state_pkg.jt_tgt_tor)
    print("smartToolState:", robot.robot_state_pkg.smartToolState)
    print("wideVoltageCtrlBoxTemp:", robot.robot_state_pkg.wideVoltageCtrlBoxTemp)
    print("wideVoltageCtrlBoxFanCurrent:", robot.robot_state_pkg.wideVoltageCtrlBoxFanCurrent)
    print("toolCoord0:", robot.robot_state_pkg.toolCoord[0])
    print("toolCoord1:", robot.robot_state_pkg.toolCoord[1])
    print("toolCoord2:", robot.robot_state_pkg.toolCoord[2])
    print("toolCoord3:", robot.robot_state_pkg.toolCoord[3])
    print("toolCoord4:", robot.robot_state_pkg.toolCoord[4])
    print("toolCoord5:", robot.robot_state_pkg.toolCoord[5])
    print("wobjCoord0:", robot.robot_state_pkg.wobjCoord[0])
    print("wobjCoord1:", robot.robot_state_pkg.wobjCoord[1])
    print("wobjCoord2:", robot.robot_state_pkg.wobjCoord[2])
    print("wobjCoord3:", robot.robot_state_pkg.wobjCoord[3])
    print("wobjCoord4:", robot.robot_state_pkg.wobjCoord[4])
    print("wobjCoord5:", robot.robot_state_pkg.wobjCoord[5])
    print("extoolCoord0:", robot.robot_state_pkg.extoolCoord[0])
    print("extoolCoord1:", robot.robot_state_pkg.extoolCoord[1])
    print("extoolCoord2:", robot.robot_state_pkg.extoolCoord[2])
    print("extoolCoord3:", robot.robot_state_pkg.extoolCoord[3])
    print("extoolCoord4:", robot.robot_state_pkg.extoolCoord[4])
    print("extoolCoord5:", robot.robot_state_pkg.extoolCoord[5])
    print("exAxisCoord0:", robot.robot_state_pkg.exAxisCoord[0])
    print("exAxisCoord1:", robot.robot_state_pkg.exAxisCoord[1])
    print("exAxisCoord2:", robot.robot_state_pkg.exAxisCoord[2])
    print("exAxisCoord3:", robot.robot_state_pkg.exAxisCoord[3])
    print("exAxisCoord4:", robot.robot_state_pkg.exAxisCoord[4])
    print("exAxisCoord5:", robot.robot_state_pkg.exAxisCoord[5])
    print("load:", robot.robot_state_pkg.load)
    print("loadCog0:", robot.robot_state_pkg.loadCog[0])
    print("loadCog1:", robot.robot_state_pkg.loadCog[1])
    print("loadCog2:", robot.robot_state_pkg.loadCog[2])
    print("lastServoTarget0:", robot.robot_state_pkg.lastServoTarget[0])
    print("lastServoTarget1:", robot.robot_state_pkg.lastServoTarget[1])
    print("lastServoTarget2:", robot.robot_state_pkg.lastServoTarget[2])
    print("lastServoTarget3:", robot.robot_state_pkg.lastServoTarget[3])
    print("lastServoTarget4:", robot.robot_state_pkg.lastServoTarget[4])
    print("lastServoTarget5:", robot.robot_state_pkg.lastServoTarget[5])
    print("servoJCmdNum:", robot.robot_state_pkg.servoJCmdNum)

Typ wyliczeniowy listy konfiguracyjnej sprzężenia zwrotnego stanu robota
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: python
    :linenos:

    class RobotState(enum.Enum):
        """Wyliczenie typów stanów CNDE"""
        FrameHead = 0
        FrameCnt = 1
        DataLen = 2
        ProgramState = 3
        RobotState = 4
        MainCode = 5
        SubCode = 6
        RobotMode = 7
        JointCurPos = 8
        ToolCurPos = 9
        FlangeCurPos = 10
        ActualJointVel = 11
        ActualJointAcc = 12
        TargetTCPCmpSpeed = 13
        TargetTCPSpeed = 14
        ActualTCPCmpSpeed = 15
        ActualTCPSpeed = 16
        ActualJointTorque = 17
        Tool = 18
        User = 19
        ClDgtOutputH = 20
        ClDgtOutputL = 21
        TlDgtOutputL = 22
        ClDgtInputH = 23
        ClDgtInputL = 24
        TlDgtInputL = 25
        ClAnalogInput = 26
        TlAnglogInput = 27
        FtSensorRawData = 28
        FtSensorData = 29
        FtSensorActive = 30
        EmergencyStop = 31
        MotionDone = 32
        GripperMotiondone = 33
        McQueueLen = 34
        CollisionState = 35
        TrajectoryPnum = 36
        SafetyStop0State = 37
        SafetyStop1State = 38
        GripperFaultId = 39
        GripperFault = 40
        GripperActive = 41
        GripperPosition = 42
        GripperSpeed = 43
        GripperCurrent = 44
        GripperTemp = 45
        GripperVoltage = 46
        AuxState = 47
        ExtAxisStatus = 48
        ExtDIState = 49
        ExtDOState = 50
        ExtAIState = 51
        ExtAOState = 52
        RbtEnableState = 53
        JointDriverTorque = 54
        JointDriverTemperature = 55
        RobotTime = 56
        SoftwareUpgradeState = 57
        EndLuaErrCode = 58
        ClAnalogOutput = 59
        TlAnalogOutput = 60
        GripperRotNum = 61
        GripperRotSpeed = 62
        GripperRotTorque = 63
        WeldingBreakOffState = 64
        TargetJointTorque = 65
        SmartToolState = 66
        WideVoltageCtrlBoxTemp = 67
        WideVoltageCtrlBoxFanCurrent = 68
        ToolCoord = 69
        WobjCoord = 70
        ExtoolCoord = 71
        ExAxisCoord = 72
        Load = 73
        LoadCog = 74
        LastServoTarget = 75
        ServoJCmdNum = 76
        TargetJointPos = 77
        TargetJointVel = 78
        TargetJointAcc = 79
        TargetJointCurrent = 80
        ActualJointCurrent = 81
        ActualTCPForce = 82
        TargetTCPPos = 83
        CollisionLevel = 84
        SpeedScaleManual = 85
        SpeedScaleAuto = 86
        LuaLineNum = 87
        AbnomalStop = 88
        CurrentLuaFileName = 89
        ProgramTotalLine = 90
        SafetyBoxSingal = 91
        WeldVoltage = 92
        WeldCurrent = 93
        WeldTrackVel = 94
        TpdException = 95
        AlarmRebootRobot = 96
        ModbusMasterConnect = 97
        ModbusSlaveConnect = 98
        BtnBoxStopSignal = 99
        DragAlarm = 100
        SafetyDoorAlarm = 101
        SafetyPlaneAlarm = 102
        MotonAlarm = 103
        InterfaceAlarm = 104
        UdpCmdState = 105
        WeldReadyState = 106
        AlarmCheckEmergStopBtn = 107
        TsTmCmdComError = 108
        TsTmStateComError = 109
        CtrlBoxError = 110
        SafetyDataState = 111
        ForceSensorErrState = 112
        CtrlOpenLuaErrCode = 113
        StrangePosFlag = 114
        Alarm = 115
        DriverAlarm = 116
        AliveSlaveNumError = 117
        SlaveComError = 118
        CmdPointError = 119
        IOError = 120
        GripperError = 121
        FileError = 122
        ParaError = 123
        ExaxisOutLimitError = 124
        DriverComError = 125
        DriverError = 126
        OutSoftLimitError = 127
        AxleGenComData = 128
        SocketConnTimeout = 129
        SocketReadTimeout = 130
        TsWebStateComErr = 131
        ExaxisCoordID = 132
        CheckSum = 133