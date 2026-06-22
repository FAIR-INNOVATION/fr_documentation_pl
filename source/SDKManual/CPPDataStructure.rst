Opis struktur danych
====================

.. toctree:: 
    :maxdepth: 5

Typ wartości zwracanej przez wywołanie interfejsu
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    typedef int errno_t;

Typ danych pozycji stawów
++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Typ danych pozycji stawów
    */
    typedef struct
    {
        double jPos[6];   /* Sześć pozycji stawów, jednostka deg */
    } JointPos;

Typ danych pozycji w przestrzeni kartezjańskiej
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Typ danych pozycji w przestrzeni kartezjańskiej
    */
    typedef struct
    {
        double x;    /* Współrzędna osi X, jednostka mm  */
        double y;    /* Współrzędna osi Y, jednostka mm  */
        double z;    /* Współrzędna osi Z, jednostka mm  */
    } DescTran;

Typ danych orientacji w kątach Eulera
+++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Typ danych orientacji w kątach Eulera
    */
    typedef struct
    {
        double rx;   /* Kąt obrotu wokół stałej osi X, jednostka: deg  */
        double ry;   /* Kąt obrotu wokół stałej osi Y, jednostka: deg  */
        double rz;   /* Kąt obrotu wokół stałej osi Z, jednostka: deg  */
    } Rpy;

Typ danych pozycji i orientacji w przestrzeni kartezjańskiej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    *@brief Typ pozycji i orientacji w przestrzeni kartezjańskiej
    */
    typedef struct
    {
        DescTran tran;      /* Pozycja w przestrzeni kartezjańskiej  */
        Rpy rpy;            /* Orientacja w przestrzeni kartezjańskiej  */
    } DescPose;

Typ danych pozycji osi rozszerzonej
+++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Typ danych pozycji osi rozszerzonej
    */
    typedef struct
    {
        double ePos[4];   /* Pozycje czterech osi rozszerzonych, jednostka mm */
    } ExaxisPos;

Typ danych czujnika siły i momentu obrotowego
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Składowe siły i momentu obrotowego czujnika siły
    */
    typedef struct
    {
        double fx;  /* Składowa siły wzdłuż osi X, jednostka N  */
        double fy;  /* Składowa siły wzdłuż osi Y, jednostka N  */
        double fz;  /* Składowa siły wzdłuż osi Z, jednostka N  */
        double tx;  /* Składowa momentu obrotowego wokół osi X, jednostka Nm */
        double ty;  /* Składowa momentu obrotowego wokół osi Y, jednostka Nm */
        double tz;  /* Składowa momentu obrotowego wokół osi Z, jednostka Nm */
    } ForceTorque;

Typ danych parametrów spirali
+++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Typ danych parametrów spirali
    */
    typedef struct
    {
        int    circle_num;           /* Liczba zwojów spirali  */
        float  circle_angle;         /* Kąt nachylenia spirali  */
        float  rad_init;             /* Początkowy promień spirali, jednostka mm  */
        float  rad_add;              /* Przyrost promienia  */
        float  rotaxis_add;          /* Przyrost kierunku osi obrotu  */
        int rot_direction;   /* Kierunek obrotu, 0-zgodnie z ruchem wskazówek zegara, 1-przeciwnie do ruchu wskazówek zegara  */
        int velAccMode;      /* Tryb parametrów prędkości i przyspieszenia: 0-stała prędkość kątowa; 1-stała prędkość liniowa */
    } SpiralParam;

Pakiet informacji zwrotnej o stanie kontrolera
++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
     * @brief  Pakiet informacji zwrotnej o stanie kontrolera
     */
    typedef struct _ROBOT_STATE_PKG
    {
      uint16_t frame_head;   // Nagłówek ramki, umownie 0x5A5A 
      uint8_t frame_cnt;    // Licznik ramek, zliczanie cykliczne 0-255 
      uint16_t data_len;    // Długość treści danych 
      uint8_t program_state;  // Stan działania programu, 1-zatrzymany; 2-działa; 3-wstrzymany;
      uint8_t robot_state;   // Stan ruchu robota, 1-zatrzymany; 2-działa; 3-wstrzymany; 4-przeciąganie 
      int   main_code;    // Główny kod usterki 
      int   sub_code;    // Podrzędny kod usterki 
      uint8_t robot_mode;   // Tryb robota, 1-tryb ręczny; 0-tryb automatyczny; 
      double  jt_cur_pos[6];  // Bieżące pozycje 6 stawów, jednostka deg 
      double  tl_cur_pos[6];  // Bieżąca pozycja narzędzia
            // tl_cur_pos[0], pozycja wzdłuż osi X, jednostka mm,
            // tl_cur_pos[1], pozycja wzdłuż osi Y, jednostka mm,
            // tl_cur_pos[2], pozycja wzdłuż osi Z, jednostka mm,
            // tl_cur_pos[3], kąt obrotu wokół stałej osi X, jednostka deg
            // tl_cur_pos[4], kąt obrotu wokół stałej osi Y, jednostka deg
            // tl_cur_pos[5], kąt obrotu wokół stałej osi Z, jednostka deg 
      double  flange_cur_pos[6]; // Bieżąca pozycja kołnierza końcowego
            // flange_cur_pos[0], pozycja wzdłuż osi X, jednostka mm,
            // flange_cur_pos[1], pozycja wzdłuż osi Y, jednostka mm,
            // flange_cur_pos[2], pozycja wzdłuż osi Z, jednostka mm,
            // flange_cur_pos[3], kąt obrotu wokół stałej osi X, jednostka deg
            // flange_cur_pos[4], kąt obrotu wokół stałej osi Y, jednostka deg
            // flange_cur_pos[5], kąt obrotu wokół stałej osi Z, jednostka deg
      double  actual_qd[6];   // Bieżące prędkości 6 stawów, jednostka deg/s 
      double  actual_qdd[6];   // Bieżące przyspieszenia 6 stawów, jednostka deg/s² 
      double  target_TCP_CmpSpeed[2]; 
            // target_TCP_CmpSpeed[0], prędkość złożona instrukcji TCP (pozycja), jednostka mm/s
            // target_TCP_CmpSpeed[1], prędkość złożona instrukcji TCP (orientacja), jednostka deg/s */
      double  target_TCP_Speed[6];  // Prędkość instrukcji TCP
              // target_TCP_Speed[0], prędkość wzdłuż osi X, jednostka mm/s,
              // target_TCP_Speed[1], prędkość wzdłuż osi Y, jednostka mm/s,
              // target_TCP_Speed[2], prędkość wzdłuż osi Z, jednostka mm/s,
              // target_TCP_Speed[3], prędkość kątowa wokół stałej osi X, jednostka deg/s
              // target_TCP_Speed[4], prędkość kątowa wokół stałej osi Y, jednostka deg/s
              // target_TCP_Speed[5], prędkość kątowa wokół stałej osi Z, jednostka deg/s */
      double  actual_TCP_CmpSpeed[2]; 
              // actual_TCP_CmpSpeed[0], rzeczywista prędkość złożona TCP (pozycja), jednostka mm/s
              // actual_TCP_CmpSpeed[1], rzeczywista prędkość złożona TCP (orientacja), jednostka deg/s 
      double  actual_TCP_Speed[6];  // Rzeczywista prędkość TCP
              // actual_TCP_Speed[0], prędkość wzdłuż osi X, jednostka mm/s,
              // actual_TCP_Speed[1], prędkość wzdłuż osi Y, jednostka mm/s,
              // actual_TCP_Speed[2], prędkość wzdłuż osi Z, jednostka mm/s,
              // actual_TCP_Speed[3], prędkość kątowa wokół stałej osi X, jednostka deg/s
              // actual_TCP_Speed[4], prędkość kątowa wokół stałej osi Y, jednostka deg/s
              // actual_TCP_Speed[5], prędkość kątowa wokół stałej osi Z, jednostka deg/s 
      double  jt_cur_tor[6];   // Bieżące momenty obrotowe 6 stawów, jednostka N·m 
      int   tool;        // Numer zastosowanego układu współrzędnych narzędzia 
      int   user;        // Numer zastosowanego układu współrzędnych przedmiotu 
      uint8_t cl_dgt_output_h;  // Wyjście cyfrowe I/O skrzynki sterowniczej 15-8 
      uint8_t cl_dgt_output_l;  // Wyjście cyfrowe I/O skrzynki sterowniczej 7-0 
      uint8_t tl_dgt_output_l;  // Wyjście cyfrowe I/O narzędzia 7-0, tylko bit0-bit1 są aktywne 
      uint8_t cl_dgt_input_h;   // Wejście cyfrowe I/O skrzynki sterowniczej 15-8 
      uint8_t cl_dgt_input_l;   // Wejście cyfrowe I/O skrzynki sterowniczej 7-0 
      uint8_t tl_dgt_input_l;   // Wejście cyfrowe I/O narzędzia 7-0, tylko bit0-bit1 są aktywne 
      uint16_t cl_analog_input[2]; // cl_analog_input[0], wejście analogowe skrzynki sterowniczej 0
                    //cl_analog_input[1], wejście analogowe skrzynki sterowniczej 1 
      uint16_t tl_anglog_input;  // Wejście analogowe narzędzia 
      double  ft_sensor_raw_data[6]; // Surowe dane czujnika siły i momentu
              // ft_sensor_raw_data[0], siła wzdłuż osi X, jednostka N
              // ft_sensor_raw_data[1], siła wzdłuż osi Y, jednostka N
              // ft_sensor_raw_data[2], siła wzdłuż osi Z, jednostka N
              // ft_sensor_raw_data[3], moment wokół osi X, jednostka Nm
              // ft_sensor_raw_data[4], moment wokół osi Y, jednostka Nm
              // ft_sensor_raw_data[5], moment wokół osi Z, jednostka Nm 
      double  ft_sensor_data[6];   // Dane czujnika siły i momentu (przetworzone),
              // ft_sensor_data[0], siła wzdłuż osi X, jednostka N
              // ft_sensor_data[1], siła wzdłuż osi Y, jednostka N
              // ft_sensor_data[2], siła wzdłuż osi Z, jednostka N
              // ft_sensor_data[3], moment wokół osi X, jednostka Nm
              // ft_sensor_data[4], moment wokół osi Y, jednostka Nm
              // ft_sensor_data[5], moment wokół osi Z, jednostka Nm 
      uint8_t ft_sensor_active;  // Stan aktywacji czujnika siły i momentu, 0-reset, 1-aktywacja 
      uint8_t EmergencyStop;   // Znacznik awaryjnego zatrzymania, 0-niewciśnięty, 1-wciśnięty 
      int   motion_done;    // Sygnał osiągnięcia pozycji, 1-osiągnięto, 0-nie osiągnięto 
      uint8_t gripper_motiondone; // Sygnał zakończenia ruchu chwytaka, 1-zakończono, 0-nie zakończono 
      int   mc_queue_len;    // Długość kolejki instrukcji ruchu 
      uint8_t collisionState;   // Wykrywanie kolizji, 1-kolizja, 0-brak kolizji 
      int   trajectory_pnum;  // Numer punktu trajektorii 
      uint8_t safety_stop0_state; // Sygnał bezpiecznego zatrzymania SI0 
      uint8_t safety_stop1_state; // Sygnał bezpiecznego zatrzymania SI1 
      uint8_t gripper_fault_id;  // Numer uszkodzonego chwytaka 
      uint16_t gripper_fault;   // Błąd chwytaka 
      uint16_t gripper_active;   // Stan aktywacji chwytaka 
      uint8_t gripper_position;  // Pozycja chwytaka 
      int8_t  gripper_speed;   // Prędkość chwytaka 
      int8_t  gripper_current;  // Prąd chwytaka 
      int   gripper_temp;    // Temperatura chwytaka 
      int   gripper_voltage;  // Napięcie chwytaka 
      robot_aux_state aux_state;  // Stan osi rozszerzonej 485
      EXT_AXIS_STATUS extAxisStatus[4]; // Stan osi rozszerzonej UDP 
      uint16_t extDIState[8];    // Wejście rozszerzone DI
      uint16_t extDOState[8];    // Wyjście rozszerzone DO
      uint16_t extAIState[4];    // Wejście rozszerzone AI
      uint16_t extAOState[4];    // Wyjście rozszerzone AO
      int rbtEnableState;      // Stan załączenia robota
      double  jointDriverTorque[6];    // Moment obrotowy napędu stawu robota
      double  jointDriverTemperature[6];  // Temperatura napędu stawu robota
      RobotTime robotTime;      // Czas systemowy robota
      int softwareUpgradeState;   // Stan aktualizacji oprogramowania robota
      uint16_t endLuaErrCode;    // Stan działania LUA końcówki
      uint16_t cl_analog_output[2]; // Wyjście analogowe skrzynki sterowniczej
      uint16_t tl_analog_output;   // Wyjście analogowe narzędzia
      float gripperRotNum;      // Bieżąca liczba obrotów chwytaka obrotowego
      uint8_t gripperRotSpeed;    // Bieżący procent prędkości obrotowej chwytaka obrotowego
      uint8_t gripperRotTorque;   // Bieżący procent momentu obrotowego chwytaka obrotowego
      WELDING_BREAKOFF_STATE weldingBreakOffState; //Stan przerwania spawania
      double jt_tgt_tor[6];         // Instrukcja momentu obrotowego stawu
      int smartToolState;          // Stan przycisków uchwytu SmartTool
      float wideVoltageCtrlBoxTemp;     // Temperatura skrzynki sterowniczej szerokiego napięcia
      uint16_t wideVoltageCtrlBoxFanCurrent;// Prąd wentylatora skrzynki sterowniczej szerokiego napięcia (mA)
      double toolCoord[6];    // Wartości bieżącego układu współrzędnych narzędzia; x,y,z,rx,ry,rz
      double wobjCoord[6];    // Wartości bieżącego układu współrzędnych przedmiotu; x,y,z,rx,ry,rz
      double extoolCoord[6];   // Wartości bieżącego zewnętrznego układu współrzędnych narzędzia; x,y,z,rx,ry,rz
      double exAxisCoord[6];   // Wartości bieżącego układu współrzędnych osi rozszerzonej; x,y,z,rx,ry,rz
      double load;        // Masa ładunku
      double loadCog[3];     // Środek ciężkości ładunku
      double lastServoTarget[6]; // Ostatnia docelowa pozycja ServoJ w kolejce
      int servoJCmdNum;      // Licznik instrukcji servoJ
      double targetJointPos[6];  // Instrukcje pozycji 6 stawów, jednostka °
      double targetJointVel[6];  // Instrukcje prędkości 6 stawów, jednostka °/s
      double targetJointAcc[6];  // Instrukcje przyspieszeń 6 stawów, jednostka °/s²
      double targetJointCurrent[6]; // Instrukcje prądu 6 stawów, jednostka A
      double actualJointCurrent[6]; // Bieżące prądy 6 stawów, jednostka A
      double actualTCPForce[6];  // Moment końcowy robota Nm; x,y,z,rx,ry,rz
      double targetTCPPos[6];   // Instrukcje pozycji TCP robota mm; x,y,z,rx,ry,rz
      uint8_t collisionLevel[6]; // Poziom kolizji robota
      double speedScaleManual;  // Procent prędkości globalnej w trybie ręcznym
      double speedScaleAuto;   // Procent prędkości globalnej w trybie automatycznym
      int luaLineNum;       // Bieżący numer linii programu lua
      uint8_t abnomalStop;    // 0-brak nieprawidłowości; 1-występuje nieprawidłowość
      char currentLuaFileName[256]; // Nazwa bieżącego programu lua
      uint8_t programTotalLine;  // Całkowita liczba linii programu lua
      uint8_t safetyBoxSingal[6]; // Stan przycisków panelu przyciskowego robota
      double weldVoltage;     // Napięcie spawania V
      double weldCurrent;     // Prąd spawania
      double weldTrackVel;    // Prędkość śledzenia spoiny mm/s
      uint8_t tpdException;    // Przekroczenie limitu liczby załadowanych trajektorii TPD, 0-nie przekroczono, 1-przekroczono 
      uint8_t alarmRebootRobot;  // Ostrzeżenie, 1-zwolnij przycisk awaryjnego zatrzymania, wyłącz i włącz ponownie skrzynkę sterowniczą, 2-nieprawidłowa komunikacja stawów, wyłącz i włącz ponownie skrzynkę sterowniczą
      uint8_t modbusMasterConnect; // bit0-bit7 odpowiadają stanom połączenia masterów ModbusTCP 0-7, 0-odłączony, 1-połączony
      uint8_t modbusSlaveConnect;  // Stan połączenia slave ModbusTCP, 0-odłączony; 1-połączony
      uint8_t btnBoxStopSignal;   // Sygnał awaryjnego zatrzymania panelu przyciskowego, 0-zwolniony; 1-wciśnięty
      uint8_t dragAlarm;      // Ostrzeżenie przeciągania, aktualnie w trybie automatycznym, 0-brak alarmu, 1-alarm, 2-nieprawidłowość pozycji sprzężenia zwrotnego, brak przełączania
      uint8_t safetyDoorAlarm;   // Ostrzeżenie drzwi bezpieczeństwa; 0-drzwi bezpieczeństwa zamknięte; 1-drzwi bezpieczeństwa otwarte
      uint8_t safetyPlaneAlarm;   // Ostrzeżenie wejścia w ścianę bezpieczeństwa; 0-nie weszło w ścianę bezpieczeństwa; 1-weszło w ścianę bezpieczeństwa
      uint8_t motonAlarm;      // Ostrzeżenie ruchu
      uint8_t interfaceAlarm;    // Ostrzeżenie wejścia w strefę interferencji
      int udpCmdState;       // Stan połączenia komunikacji UDP na porcie 20007
      uint8_t weldReadyState;    // Stan gotowości spawarki
      uint8_t alarmCheckEmergStopBtn; // 0-normalny; 1-nieprawidłowość komunikacji, sprawdź, czy przycisk awaryjnego zatrzymania jest zwolniony
      uint8_t tsTmCmdComError;   // 0-normalny; 1-błąd komunikacji instrukcji momentu
      uint8_t tsTmStateComError;  // 0-normalny; 1-błąd komunikacji stanu momentu
      int ctrlBoxError;       // Błąd skrzynki sterowniczej
      uint8_t safetyDataState;   // Znacznik stanu danych bezpieczeństwa, 0-normalny, 1-nieprawidłowy
      uint8_t forceSensorErrState; // Błąd przekroczenia limitu czasu połączenia czujnika siły; bit0-bit1 odpowiadają ID1-ID2 czujnika siły
      uint8_t ctrlOpenLuaErrCode[4]; // 4 kody błędów protokołu otwartego urządzeń peryferyjnych kontrolera (kod błędu 500)
      uint8_t strangePosFlag; // Znacznik bieżącej osobliwej pozycji; 0-normalny; 1-osobliwa pozycja
      uint8_t alarm;      // Ostrzeżenie
      uint8_t driverAlarm;   // Numer osi alarmu napędu
      uint8_t aliveSlaveNumError; // Błąd liczby aktywnych stacji podrzędnych, 0: normalny; 1: błąd liczby
      uint8_t slaveComError[8];  // Błąd stacji podrzędnej, 0: normalny; 1: utrata połączenia ze stacją podrzędną; 2: stan stacji podrzędnej niezgodny z ustawioną wartością; 3: stacja podrzędna nieskonfigurowana; 4: błąd konfiguracji stacji podrzędnej; 5: błąd inicjalizacji stacji podrzędnej; 6: błąd inicjalizacji komunikacji e-mail stacji podrzędnej
      uint8_t cmdPointError;   // Błąd punktu instrukcji
      uint8_t IOError;      // Błąd I/O
      uint8_t gripperError;    // Błąd chwytaka
      uint8_t fileError;     // Błąd pliku
      uint8_t paraError;     // Błąd parametru
      uint8_t exaxisOutLimitError;  // Błąd przekroczenia miękkiego limitu zewnętrznej osi
      uint8_t driverComError[6];   // Błąd komunikacji z napędem
      uint8_t driverError;      // Numer osi błędu komunikacji napędu
      uint8_t outSoftLimitError;   // Błąd przekroczenia miękkiego limitu
      char axleGenComData[130];   // Dane zwrotne transmisji transparentnej końcówki robota
      uint8_t socketConnTimeout;   // Przekroczenie limitu czasu połączenia socket, bit0-bit4: socketID 1-4
      uint8_t socketReadTimeout;   // Przekroczenie limitu czasu odczytu socket, bit0-bit4: socketID 1-4
      uint8_t tsWebStateComErr;   // web - błąd komunikacji momentu; 0-normalny; 1-błąd
      uint8_t exaxisCoordID;     // Numer układu współrzędnych osi rozszerzonej
      uint16_t check_sum;     // Suma kontrolna
    } ROBOT_STATE_PKG;

Typ wyliczeniowy konfiguracji informacji zwrotnej o stanie robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    enum class RobotState
    {
        ProgramState = 3,           // Stan działania programu, 1-zatrzymany; 2-działa; 3-wstrzymany
        RobotState = 4,             // Stan ruchu robota, 1-zatrzymany; 2-działa; 3-wstrzymany; 4-przeciąganie
        MainCode = 5,               // Główny kod usterki
        SubCode = 6,                // Podrzędny kod usterki
        RobotMode = 7,              // Tryb robota, 1-tryb ręczny; 0-tryb automatyczny
        JointCurPos = 8,            // Bieżące pozycje 6 stawów, jednostka deg
        ToolCurPos = 9,             // Bieżąca pozycja narzędzia: [0]pozycja wzdłuż osi X (mm), [1]wzdłuż Y (mm), [2]wzdłuż Z (mm), [3]obrót wokół stałej osi X (deg), [4]wokół Y (deg), [5]wokół Z (deg)
        FlangeCurPos = 10,          // Bieżąca pozycja kołnierza końcowego: [0]wzdłuż X (mm), [1]wzdłuż Y (mm), [2]wzdłuż Z (mm), [3]obrót wokół X (deg), [4]wokół Y (deg), [5]wokół Z (deg)
        ActualJointVel = 11,        // Bieżące prędkości 6 stawów, jednostka deg/s
        ActualJointAcc = 12,        // Bieżące przyspieszenia 6 stawów, jednostka deg/s²
        TargetTCPCmpSpeed = 13,     // Prędkość złożona instrukcji TCP: [0]pozycja (mm/s), [1]orientacja (deg/s)
        TargetTCPSpeed = 14,        // Prędkość instrukcji TCP: [0]wzdłuż X (mm/s), [1]wzdłuż Y (mm/s), [2]wzdłuż Z (mm/s), [3]prędkość kątowa wokół X (deg/s), [4]wokół Y (deg/s), [5]wokół Z (deg/s)
        ActualTCPCmpSpeed = 15,     // Rzeczywista prędkość złożona TCP: [0]pozycja (mm/s), [1]orientacja (deg/s)
        ActualTCPSpeed = 16,        // Rzeczywista prędkość TCP: [0]wzdłuż X (mm/s), [1]wzdłuż Y (mm/s), [2]wzdłuż Z (mm/s), [3]prędkość kątowa wokół X (deg/s), [4]wokół Y (deg/s), [5]wokół Z (deg/s)
        ActualJointTorque = 17,     // Bieżące momenty obrotowe 6 stawów, jednostka N·m
        Tool = 18,                  // Numer zastosowanego układu współrzędnych narzędzia
        User = 19,                  // Numer zastosowanego układu współrzędnych przedmiotu
        ClDgtOutputH = 20,          // Wyjście cyfrowe I/O skrzynki sterowniczej 15-8
        ClDgtOutputL = 21,          // Wyjście cyfrowe I/O skrzynki sterowniczej 7-0
        TlDgtOutputL = 22,          // Wyjście cyfrowe I/O narzędzia 7-0, tylko bit0-bit1 są aktywne
        ClDgtInputH = 23,           // Wejście cyfrowe I/O skrzynki sterowniczej 15-8
        ClDgtInputL = 24,           // Wejście cyfrowe I/O skrzynki sterowniczej 7-0
        TlDgtInputL = 25,           // Wejście cyfrowe I/O narzędzia 7-0, tylko bit0-bit1 są aktywne
        ClAnalogInput = 26,         // Wejście analogowe skrzynki sterowniczej: [0]kanał 0, [1]kanał 1
        TlAnalogInput = 27,         // Wejście analogowe narzędzia
        FtSensorRawData = 28,       // Surowe dane czujnika siły i momentu: [0]siła wzdłuż X (N), [1]wzdłuż Y (N), [2]wzdłuż Z (N), [3]moment wokół X (Nm), [4]wokół Y (Nm), [5]wokół Z (Nm)
        FtSensorData = 29,          // Dane czujnika siły i momentu (przetworzone): [0]siła wzdłuż X (N), [1]wzdłuż Y (N), [2]wzdłuż Z (N), [3]moment wokół X (Nm), [4]wokół Y (Nm), [5]wokół Z (Nm)
        FtSensorActive = 30,        // Stan aktywacji czujnika siły i momentu, 0-reset, 1-aktywacja
        EmergencyStop = 31,         // Znacznik awaryjnego zatrzymania, 0-niewciśnięty, 1-wciśnięty
        MotionDone = 32,            // Sygnał osiągnięcia pozycji, 1-osiągnięto, 0-nie osiągnięto
        GripperMotiondone = 33,     // Sygnał zakończenia ruchu chwytaka, 1-zakończono, 0-nie zakończono
        McQueueLen = 34,            // Długość kolejki instrukcji ruchu
        CollisionState = 35,        // Wykrywanie kolizji, 1-kolizja, 0-brak kolizji
        TrajectoryPnum = 36,        // Numer punktu trajektorii
        SafetyStop0State = 37,      // Sygnał bezpiecznego zatrzymania SI0
        SafetyStop1State = 38,      // Sygnał bezpiecznego zatrzymania SI1
        GripperFaultId = 39,        // Numer uszkodzonego chwytaka
        GripperFault = 40,          // Błąd chwytaka
        GripperActive = 41,         // Stan aktywacji chwytaka
        GripperPosition = 42,       // Pozycja chwytaka
        GripperSpeed = 43,          // Prędkość chwytaka
        GripperCurrent = 44,        // Prąd chwytaka
        GripperTemp = 45,           // Temperatura chwytaka
        GripperVoltage = 46,        // Napięcie chwytaka
        AuxState = 47,              // Stan osi rozszerzonej 485
        ExtAxisStatus = 48,         // Stan osi rozszerzonej UDP (4 osie)
        ExtDIState = 49,            // Wejście rozszerzone DI (8)
        ExtDOState = 50,            // Wyjście rozszerzone DO (8)
        ExtAIState = 51,            // Wejście rozszerzone AI (4)
        ExtAOState = 52,            // Wyjście rozszerzone AO (4)
        RbtEnableState = 53,        // Stan załączenia robota
        JointDriverTorque = 54,     // Moment obrotowy napędu stawu robota (6 stawów)
        JointDriverTemperature = 55,// Temperatura napędu stawu robota (6 stawów)
        RobotTime = 56,             // Czas systemowy robota
        SoftwareUpgradeState = 57,  // Stan aktualizacji oprogramowania robota
        EndLuaErrCode = 58,         // Stan działania LUA końcówki
        ClAnalogOutput = 59,        // Wyjście analogowe skrzynki sterowniczej (2)
        TlAnalogOutput = 60,        // Wyjście analogowe narzędzia
        GripperRotNum = 61,         // Bieżąca liczba obrotów chwytaka obrotowego
        GripperRotSpeed = 62,       // Bieżący procent prędkości obrotowej chwytaka obrotowego
        GripperRotTorque = 63,      // Bieżący procent momentu obrotowego chwytaka obrotowego
        WeldingBreakOffState = 64,  // Stan przerwania spawania
        TargetJointTorque = 65,     // Instrukcja momentu obrotowego stawu (6 stawów)
        SmartToolState = 66,        // Stan przycisków uchwytu SmartTool
        WideVoltageCtrlBoxTemp = 67,// Temperatura skrzynki sterowniczej szerokiego napięcia
        WideVoltageCtrlBoxFanCurrent = 68, // Prąd wentylatora skrzynki sterowniczej szerokiego napięcia (mA)
        ToolCoord = 69,             // Wartości bieżącego układu współrzędnych narzędzia: x,y,z,rx,ry,rz
        WobjCoord = 70,             // Wartości bieżącego układu współrzędnych przedmiotu: x,y,z,rx,ry,rz
        ExtoolCoord = 71,           // Wartości bieżącego zewnętrznego układu współrzędnych narzędzia: x,y,z,rx,ry,rz
        ExAxisCoord = 72,           // Wartości bieżącego układu współrzędnych osi rozszerzonej: x,y,z,rx,ry,rz
        Load = 73,                  // Masa ładunku
        LoadCog = 74,               // Środek ciężkości ładunku: x,y,z
        LastServoTarget = 75,       // Ostatnia docelowa pozycja ServoJ w kolejce (6 stawów)
        ServoJCmdNum = 76,          // Licznik instrukcji servoJ
        TargetJointPos = 77,        // Instrukcje pozycji 6 stawów, jednostka °
        TargetJointVel = 78,        // Instrukcje prędkości 6 stawów, jednostka °/s
        TargetJointAcc = 79,        // Instrukcje przyspieszeń 6 stawów, jednostka °/s²
        TargetJointCurrent = 80,    // Instrukcje prądu 6 stawów, jednostka A
        ActualJointCurrent = 81,    // Bieżące prądy 6 stawów, jednostka A
        ActualTCPForce = 82,        // Moment końcowy robota: x,y,z,rx,ry,rz, jednostka Nm
        TargetTCPPos = 83,          // Instrukcje pozycji TCP robota: x,y,z,rx,ry,rz, jednostka mm
        CollisionLevel = 84,        // Poziom kolizji robota (6)
        SpeedScaleManual = 85,      // Procent prędkości globalnej w trybie ręcznym
        SpeedScaleAuto = 86,        // Procent prędkości globalnej w trybie automatycznym
        LuaLineNum = 87,            // Bieżący numer linii programu lua
        AbnomalStop = 88,           // 0-brak nieprawidłowości; 1-występuje nieprawidłowość
        CurrentLuaFileName = 89,    // Nazwa bieżącego programu lua
        ProgramTotalLine = 90,      // Całkowita liczba linii programu lua
        SafetyBoxSingal = 91,       // Stan przycisków panelu przyciskowego robota (6)
        WeldVoltage = 92,           // Napięcie spawania V
        WeldCurrent = 93,           // Prąd spawania
        WeldTrackVel = 94,          // Prędkość śledzenia spoiny mm/s
        TpdException = 95,          // Przekroczenie limitu liczby załadowanych trajektorii TPD, 0-nie przekroczono, 1-przekroczono
        AlarmRebootRobot = 96,      // Ostrzeżenie: 1-zwolnij awaryjne zatrzymanie i wyłącz/włącz zasilanie, 2-nieprawidłowa komunikacja stawów, wyłącz/włącz zasilanie
        ModbusMasterConnect = 97,   // bity 0-7 odpowiadają stanom połączenia masterów ModbusTCP 0-7, 0-odłączony, 1-połączony
        ModbusSlaveConnect = 98,    // Stan połączenia slave ModbusTCP, 0-odłączony, 1-połączony
        BtnBoxStopSignal = 99,      // Sygnał awaryjnego zatrzymania panelu przyciskowego, 0-zwolniony, 1-wciśnięty
        DragAlarm = 100,            // Ostrzeżenie przeciągania: 0-brak alarmu, 1-alarm, 2-nieprawidłowość pozycji sprzężenia zwrotnego, brak przełączania
        SafetyDoorAlarm = 101,      // Ostrzeżenie drzwi bezpieczeństwa: 0-zamknięte, 1-otwarte
        SafetyPlaneAlarm = 102,     // Ostrzeżenie ściany bezpieczeństwa: 0-nie weszło, 1-weszło
        MotonAlarm = 103,           // Ostrzeżenie ruchu
        InterfaceAlarm = 104,       // Ostrzeżenie wejścia w strefę interferencji
        UdpCmdState = 105,          // Stan połączenia komunikacji UDP na porcie 20007
        WeldReadyState = 106,       // Stan gotowości spawarki
        AlarmCheckEmergStopBtn = 107, // 0-normalny; 1-nieprawidłowa komunikacja, sprawdź przycisk awaryjnego zatrzymania
        TsTmCmdComError = 108,      // 0-normalny; 1-błąd komunikacji instrukcji momentu
        TsTmStateComError = 109,    // 0-normalny; 1-błąd komunikacji stanu momentu
        CtrlBoxError = 110,         // Błąd skrzynki sterowniczej
        SafetyDataState = 111,      // Znacznik stanu danych bezpieczeństwa, 0-normalny, 1-nieprawidłowy
        ForceSensorErrState = 112,  // Błąd przekroczenia limitu czasu połączenia czujnika siły, bit0-bit1 odpowiadają ID1-ID2
        CtrlOpenLuaErrCode = 113,   // 4 kody błędów protokołu otwartego urządzeń peryferyjnych kontrolera (kod błędu 500)
        StrangePosFlag = 114,       // Znacznik osobliwej pozycji: 0-normalny, 1-osobliwa pozycja
        Alarm = 115,                // Ostrzeżenie
        DriverAlarm = 116,          // Numer osi alarmu napędu
        AliveSlaveNumError = 117,   // Błąd liczby aktywnych stacji podrzędnych: 0-normalny, 1-błąd liczby
        SlaveComError = 118,        // Błąd stacji podrzędnej: 0-normalny, 1-utrata połączenia, 2-niezgodność stanu, 3-nieskonfigurowana, 4-błąd konfiguracji, 5-błąd inicjalizacji, 6-błąd inicjalizacji komunikacji e-mail
        CmdPointError = 119,        // Błąd punktu instrukcji
        IOError = 120,              // Błąd I/O
        GripperError = 121,         // Błąd chwytaka
        FileError = 122,            // Błąd pliku
        ParaError = 123,            // Błąd parametru
        ExaxisOutLimitError = 124,  // Błąd przekroczenia miękkiego limitu zewnętrznej osi
        DriverComError = 125,       // Błąd komunikacji z napędem (6 osi)
        DriverError = 126,          // Numer osi błędu komunikacji napędu
        OutSoftLimitError = 127,    // Błąd przekroczenia miękkiego limitu
        AxleGenComData = 128,       // Dane zwrotne transmisji transparentnej końcówki robota
        SocketConnTimeout = 129,    // Przekroczenie limitu czasu połączenia socket, bit0-bit4 odpowiadają socketID 1-4
        SocketReadTimeout = 130,    // Przekroczenie limitu czasu odczytu socket, bit0-bit4 odpowiadają socketID 1-4
        TsWebStateComErr = 131,     // web - błąd komunikacji momentu: 0-normalny, 1-błąd
        ExaxisCoordID = 132         // Numer układu współrzędnych osi rozszerzonej
    };