Opis struktur danych
====================

.. toctree:: 
    :maxdepth: 5

Typ danych pozycji stawów
++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Typ danych pozycji stawów 
    */  
    struct JointPos
    {
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] jPos;   /* Sześć pozycji stawów, jednostka deg */
    }

Typ danych pozycji w przestrzeni kartezjańskiej
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Typ danych pozycji w przestrzeni kartezjańskiej
    */
    struct DescTran
    {
        public double x;    /* Współrzędna osi X, jednostka mm  */
        public double y;    /* Współrzędna osi Y, jednostka mm  */
        public double z;    /* Współrzędna osi Z, jednostka mm  */
    }

Typ danych orientacji w kątach Eulera
+++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Typ danych orientacji w kątach Eulera
    */
    struct Rpy
    {
    public double rx;   /* Kąt obrotu wokół stałej osi X, jednostka: deg  */
    public double ry;   /* Kąt obrotu wokół stałej osi Y, jednostka: deg  */
    public double rz;   /* Kąt obrotu wokół stałej osi Z, jednostka: deg  */
    }

Typ danych pozycji i orientacji w przestrzeni kartezjańskiej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    *@brief Typ pozycji i orientacji w przestrzeni kartezjańskiej
    */
    struct DescPose
    {
        public DescTran tran;     /* Pozycja w przestrzeni kartezjańskiej  */
        public Rpy rpy;			/* Orientacja w przestrzeni kartezjańskiej  */
    }

Typ danych pozycji osi rozszerzonej
+++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Typ danych pozycji osi rozszerzonej
    */
    struct ExaxisPos
    {
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 4)]
        public double[] ePos;   /* Pozycje czterech osi rozszerzonych, jednostka mm */
    }

Typ danych czujnika siły i momentu obrotowego
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Składowe siły i momentu obrotowego czujnika siły
    */
    struct ForceTorque
    {
        public double fx;  /* Składowa siły wzdłuż osi X, jednostka N  */
        public double fy;  /* Składowa siły wzdłuż osi Y, jednostka N  */
        public double fz;  /* Składowa siły wzdłuż osi Z, jednostka N  */
        public double tx;  /* Składowa momentu obrotowego wokół osi X, jednostka Nm */
        public double ty;  /* Składowa momentu obrotowego wokół osi Y, jednostka Nm */
        public double tz;  /* Składowa momentu obrotowego wokół osi Z, jednostka Nm */
    }

Typ danych parametrów spirali
+++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public struct SpiralParam
    {
        public int circle_num;           /* Liczba zwojów spirali  */
        public float circle_angle;         /* Kąt nachylenia spirali  */
        public float rad_init;             /* Początkowy promień spirali, jednostka mm  */
        public float rad_add;              /* Przyrost promienia  */
        public float rotaxis_add;          /* Przyrost kierunku osi obrotu  */
        public uint rot_direction;  /* Kierunek obrotu, 0-zgodnie z ruchem wskazówek zegara, 1-przeciwnie do ruchu wskazówek zegara  */
        public int velAccMode;      // Tryb parametrów prędkości i przyspieszenia: 0-stała prędkość kątowa; 1-stała prędkość liniowa
        public SpiralParam(int num, float angle, float initRad, float addRad, float axisAdd, uint direction, int mode)
        {
            circle_num = num;
            circle_angle = angle;
            rad_init = initRad;
            rad_add = addRad;
            rotaxis_add = axisAdd;
            rot_direction = direction;
            velAccMode = mode;
        }
    }

Typ stanu osi rozszerzonej
+++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /**
    * @brief  Typ stanu osi rozszerzonej
    */
    [StructLayout(LayoutKind.Sequential, Pack = 1)]
    public struct ROBOT_AUX_STATE
    {
        public byte servoId;           // Numer ID serwonapędu
        public int servoErrCode;       // Kod usterki serwonapędu
        public int servoState;         // Stan serwonapędu
        public double servoPos;        // Bieżąca pozycja serwa
        public float servoVel;         // Bieżąca prędkość serwa
        public float servoTorque;      // Bieżący moment obrotowy serwa
    }

Stan przerwania spawania
++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    [StructLayout(LayoutKind.Sequential, Pack = 1)]
    public struct WELDING_BREAKOFF_STATE
    {
        public byte breakOffState;  // Stan przerwania spawania
        public byte weldArcState;   // Stan przerwania łuku spawalniczego
    }

Typ struktury informacji zwrotnej o stanie robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3
    
.. code-block:: c#
    :linenos:

    /**
    * @brief  Typ struktury informacji zwrotnej o stanie robota
    */
    [StructLayout(LayoutKind.Sequential, Pack = 1)]
    public class ROBOT_STATE_PKG
    {
        public UInt16 frame_head;           // Nagłówek ramki 0x5A5A
        public byte frame_cnt;              // Licznik ramek
        public UInt16 data_len;             // Długość danych  5
        public byte program_state;          // Stan działania programu, 1-zatrzymany; 2-działa; 3-wstrzymany;
        public byte robot_state;            // Stan ruchu robota, 1-zatrzymany; 2-działa; 3-wstrzymany; 4-przeciąganie
        public int main_code;               // Główny kod usterki
        public int sub_code;                // Podrzędny kod usterki
        public byte robot_mode;             // Tryb robota, 1-tryb ręczny; 0-tryb automatyczny;

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] jt_cur_pos;         // Bieżące pozycje 6 stawów, jednostka deg
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] tl_cur_pos;         // Bieżąca pozycja narzędzia
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] flange_cur_pos;     // Bieżąca pozycja kołnierza końcowego
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] actual_qd;          // Bieżące prędkości 6 stawów, jednostka deg/s
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] actual_qdd;         // Bieżące przyspieszenia 6 stawów, jednostka deg/s^2
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 2)]
        public double[] target_TCP_CmpSpeed;// Prędkość złożona instrukcji TCP (pozycja, orientacja)
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] target_TCP_Speed;   // Prędkość instrukcji TCP
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 2)]
        public double[] actual_TCP_CmpSpeed;// Rzeczywista prędkość złożona TCP
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] actual_TCP_Speed;   // Rzeczywista prędkość TCP
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] jt_cur_tor;         // Bieżące momenty obrotowe 6 stawów, jednostka N·m

        public int tool;                    // Numer zastosowanego układu współrzędnych narzędzia
        public int user;                    // Numer zastosowanego układu współrzędnych przedmiotu
        public byte cl_dgt_output_h;        // Wyjście cyfrowe I/O skrzynki sterowniczej 15-8
        public byte cl_dgt_output_l;        // Wyjście cyfrowe I/O skrzynki sterowniczej 7-0
        public byte tl_dgt_output_l;        // Wyjście cyfrowe I/O narzędzia 7-0, tylko bit0-bit1 są aktywne
        public byte cl_dgt_input_h;         // Wejście cyfrowe I/O skrzynki sterowniczej 15-8
        public byte cl_dgt_input_l;         // Wejście cyfrowe I/O skrzynki sterowniczej 7-0
        public byte tl_dgt_input_l;         // Wejście cyfrowe I/O narzędzia 7-0, tylko bit0-bit1 są aktywne

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 2)]
        public UInt16[] cl_analog_input;        // Wejście analogowe skrzynki sterowniczej
        public UInt16 tl_anglog_input;          // Wejście analogowe narzędzia                            

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] ft_sensor_raw_data; // Surowe dane czujnika siły i momentu
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] ft_sensor_data;     // Dane czujnika siły i momentu
        public byte ft_sensor_active;       // Stan aktywacji czujnika siły i momentu, 0-reset, 1-aktywacja

        public byte EmergencyStop;          // Znacznik awaryjnego zatrzymania, 0-niewciśnięty, 1-wciśnięty
        public int motion_done;             // Sygnał osiągnięcia pozycji, 1-osiągnięto, 0-nie osiągnięto
        public byte gripper_motiondone;     // Sygnał zakończenia ruchu chwytaka, 1-zakończono, 0-nie zakończono
        public int mc_queue_len;            // Długość kolejki instrukcji ruchu
        public byte collisionState;         // Wykrywanie kolizji, 1-kolizja, 0-brak kolizji
        public int trajectory_pnum;         // Numer punktu trajektorii
        public byte safety_stop0_state;     // Sygnał bezpiecznego zatrzymania SI0
        public byte safety_stop1_state;     // Sygnał bezpiecznego zatrzymania SI1
        public byte gripper_fault_id;       // Numer uszkodzonego chwytaka
        public UInt16 gripper_fault;     /* Błąd chwytaka */
        public UInt16 gripper_active;    /* Stan aktywacji chwytaka */
        public byte gripper_position;       // Pozycja chwytaka
        public byte gripper_speed;       /* Prędkość chwytaka */
        public byte gripper_current;     /* Prąd chwytaka */
        public int gripper_temp;            // Temperatura chwytaka
        public int gripper_voltage;         // Napięcie chwytaka

        public ROBOT_AUX_STATE auxState;   // Stan osi rozszerzonej 485

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 4)]
        public EXT_AXIS_STATUS[] extAxisStatus; // Stan osi rozszerzonej UDP

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 8)]
        public UInt16[] extDIState;        // Wejście rozszerzone DI
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 8)]
        public UInt16[] extDOState;        // Wyjście rozszerzone DO
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 4)]
        public UInt16[] extAIState;        // Wejście rozszerzone AI
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 4)]
        public UInt16[] extAOState;        // Wyjście rozszerzone AO

        public int rbtEnableState;          // Stan załączenia robota

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] jointDriverTorque;      // Moment obrotowy napędu stawu robota
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] jointDriverTemperature; // Temperatura napędu stawu robota

        public ROBOT_TIME robotTime;        // Czas systemowy robota
        public int softwareUpgradeState;    // Stan aktualizacji oprogramowania robota
        public UInt16 endLuaErrCode;    // Stan działania LUA końcówki 

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 2)]
        public  UInt16[] cl_analog_output;  // Wyjście analogowe skrzynki sterowniczej				  
        public UInt16 tl_analog_output;     // Wyjście analogowe narzędzia				  

        public float gripperRotNum;         // Bieżąca liczba obrotów chwytaka obrotowego
        public byte gripperRotSpeed;        // Bieżący procent prędkości obrotowej chwytaka obrotowego
        public byte gripperRotTorque;       // Bieżący procent momentu obrotowego chwytaka obrotowego

        public WELDING_BREAKOFF_STATE weldingBreakOffState; // Stan przerwania spawania

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] jt_tgt_tor;         // Instrukcja momentu obrotowego stawu
        public int smartToolState;          // Stan przycisków uchwytu SmartTool
        public float wideVoltageCtrlBoxTemp; // Temperatura skrzynki sterowniczej szerokiego napięcia
        public UInt16 wideVoltageCtrlBoxFanVel;   // Prąd wentylatora skrzynki sterowniczej szerokiego napięcia (mA)

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] toolCoord;          // Wartości bieżącego układu współrzędnych narzędzia; x,y,z,rx,ry,rz
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] wobjCoord;          // Wartości bieżącego układu współrzędnych przedmiotu; x,y,z,rx,ry,rz
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] extoolCoord;        // Wartości bieżącego zewnętrznego układu współrzędnych narzędzia; x,y,z,rx,ry,rz
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] exAxisCoord;        // Wartości bieżącego układu współrzędnych osi rozszerzonej; x,y,z,rx,ry,rz

        public double load;                 // Masa ładunku
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 3)]
        public double[] loadCog;            // Środek ciężkości ładunku
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] lastServoTarget;    // Ostatnia docelowa pozycja ServoJ w kolejce
        public int servoJCmdNum;            // Licznik instrukcji servoJ

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] targetJointPos;     // Instrukcje pozycji 6 stawów, jednostka °
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] targetJointVel;     // Instrukcje prędkości 6 stawów, jednostka °/s
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] targetJointAcc;     // Instrukcje przyspieszeń 6 stawów, jednostka °/s²
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] targetJointCurrent; // Instrukcje prądu 6 stawów, jednostka A
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] actualJointCurrent; // Bieżące prądy 6 stawów, jednostka A
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] actualTCPForce;     // Moment końcowy robota Nm; x,y,z,rx,ry,rz
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] targetTCPPos;       // Instrukcje pozycji TCP robota mm; x,y,z,rx,ry,rz
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public byte[] collisionLevel;       // Poziom kolizji robota

        public double speedScaleManual;     // Procent prędkości globalnej w trybie ręcznym
        public double speedScaleAuto;       // Procent prędkości globalnej w trybie automatycznym
        public int luaLineNum;              // Bieżący numer linii programu lua
        public byte abnomalStop;            // 0-brak nieprawidłowości; 1-występuje nieprawidłowość

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 256)]
        public byte[] currentLuaFileName;   // Nazwa bieżącego programu lua
        public byte programTotalLine;       // Całkowita liczba linii programu lua
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public byte[] safetyBoxSingal;      // Stan przycisków panelu przyciskowego robota

        public double weldVoltage;          // Napięcie spawania V
        public double weldCurrent;          // Prąd spawania
        public double weldTrackVel;         // Prędkość śledzenia spoiny mm/s

        public byte tpdException;           // Przekroczenie limitu liczby załadowanych trajektorii TPD, 0-nie przekroczono, 1-przekroczono
        public byte alarmRebootRobot;       // Ostrzeżenie, 1-zwolnij przycisk awaryjnego zatrzymania, wyłącz i włącz ponownie skrzynkę sterowniczą, 2-nieprawidłowa komunikacja stawów, wyłącz i włącz ponownie skrzynkę sterowniczą
        public byte modbusMasterConnect;    /* Stan połączenia masterów ModbusTCP 0-7, bity bit0-bit7, 0-odłączony, 1-połączony */
        public byte modbusSlaveConnect;     /* Stan połączenia slave ModbusTCP, 0-odłączony; 1-połączony */
        public byte btnBoxStopSignal;       /* Sygnał awaryjnego zatrzymania panelu przyciskowego, 0-zwolniony; 1-wciśnięty */
        public byte dragAlarm;              /* Ostrzeżenie przeciągania, aktualnie w trybie automatycznym, 0-brak alarmu, 1-alarm, 2-nieprawidłowość pozycji sprzężenia zwrotnego, brak przełączania */
        public byte safetyDoorAlarm;        /* Ostrzeżenie drzwi bezpieczeństwa; 0-drzwi bezpieczeństwa zamknięte; 1-drzwi bezpieczeństwa otwarte */
        public byte safetyPlaneAlarm;       /* Ostrzeżenie wejścia w ścianę bezpieczeństwa; 0-nie weszło w ścianę bezpieczeństwa; 1-weszło w ścianę bezpieczeństwa */
        public byte motonAlarm;             /* Ostrzeżenie ruchu */
        public byte interfaceAlarm;         /* Ostrzeżenie wejścia w strefę interferencji */
        public int udpCmdState;             /* Stan połączenia komunikacji UDP na porcie 20007 */
        public byte weldReadyState;         /* Stan gotowości spawarki */
        public byte alarmCheckEmergStopBtn; /* 0-normalny; 1-nieprawidłowość komunikacji, sprawdź, czy przycisk awaryjnego zatrzymania jest zwolniony */
        public byte tsTmCmdComError;        /* 0-normalny; 1-błąd komunikacji instrukcji momentu */
        public byte tsTmStateComError;      /* 0-normalny; 1-błąd komunikacji stanu momentu */
        public int ctrlBoxError;            /* Błąd skrzynki sterowniczej */
        public byte safetyDataState;        /* Znacznik stanu danych bezpieczeństwa, 0-normalny, 1-nieprawidłowy */
        public byte forceSensorErrState;    /* Błąd przekroczenia limitu czasu połączenia czujnika siły; bit0-bit1 odpowiadają ID1-ID2 czujnika siły */

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 4)]
        public byte[] ctrlOpenLuaErrCode;   /* 4 kody błędów protokołu otwartego urządzeń peryferyjnych kontrolera (kod błędu 500) */

        public byte strangePosFlag;         /* Znacznik bieżącej osobliwej pozycji; 0-normalny; 1-osobliwa pozycja */
        public byte alarm;                  /* Ostrzeżenie */
        public byte driverAlarm;            /* Numer osi alarmu napędu */
        public byte aliveSlaveNumError;     /* Błąd liczby aktywnych stacji podrzędnych, 0: normalny; 1: błąd liczby */

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 8)]
        public byte[] slaveComError;        /* Błąd stacji podrzędnej, 0: normalny; 1: utrata połączenia ze stacją podrzędną; 2: stan stacji podrzędnej niezgodny z ustawioną wartością; 3: stacja podrzędna nieskonfigurowana; 4: błąd konfiguracji stacji podrzędnej; 5: błąd inicjalizacji stacji podrzędnej; 6: błąd inicjalizacji komunikacji e-mail stacji podrzędnej */

        public byte cmdPointError;          /* Błąd punktu instrukcji */
        public byte IOError;                /* Błąd I/O */
        public byte gripperError;           /* Błąd chwytaka */
        public byte fileError;              /* Błąd pliku */
        public byte paraError;              /* Błąd parametru */
        public byte exaxisOutLimitError;    /* Błąd przekroczenia miękkiego limitu osi rozszerzonej */

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public byte[] driverComError;       /* Błąd komunikacji z napędem */
        public byte driverError;            /* Numer osi błędu komunikacji napędu */
        public byte outSoftLimitError;      /* Błąd przekroczenia miękkiego limitu */

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 130)]
        public byte[] axleGenComData;       /* Dane zwrotne transmisji transparentnej końcówki robota */

        public byte socketConnTimeout;     /* Znacznik przekroczenia limitu czasu połączenia socket */
        public byte socketReadTimeout;     /* Znacznik przekroczenia limitu czasu odczytu socket */
        public byte tsWebStateComErr;      /* ts_web_state_com_err */
        public byte exaxisCoordID;         /* Numer układu współrzędnych osi rozszerzonej */
        public UInt16 check_sum;         /* Suma kontrolna */                 

        // Konstruktor: inicjalizuje wszystkie pola tablicowe
        public ROBOT_STATE_PKG()
        {
            jt_cur_pos = new double[6];
            tl_cur_pos = new double[6];
            flange_cur_pos = new double[6];
            actual_qd = new double[6];
            actual_qdd = new double[6];
            target_TCP_CmpSpeed = new double[2];
            target_TCP_Speed = new double[6];
            actual_TCP_CmpSpeed = new double[2];
            actual_TCP_Speed = new double[6];
            jt_cur_tor = new double[6];
            cl_analog_input = new ushort[2];
            ft_sensor_raw_data = new double[6];
            ft_sensor_data = new double[6];
            extAxisStatus = new EXT_AXIS_STATUS[4];
            extDIState = new ushort[8];
            extDOState = new ushort[8];
            extAIState = new ushort[4];
            extAOState = new ushort[4];
            jointDriverTorque = new double[6];
            jointDriverTemperature = new double[6];
            cl_analog_output = new ushort[2];
            jt_tgt_tor = new double[6];
            toolCoord = new double[6];
            wobjCoord = new double[6];
            extoolCoord = new double[6];
            exAxisCoord = new double[6];
            loadCog = new double[3];
            lastServoTarget = new double[6];
            targetJointPos = new double[6];
            targetJointVel = new double[6];
            targetJointAcc = new double[6];
            targetJointCurrent = new double[6];
            actualJointCurrent = new double[6];
            actualTCPForce = new double[6];
            targetTCPPos = new double[6];
            collisionLevel = new byte[6];
            currentLuaFileName = new byte[256];
            safetyBoxSingal = new byte[6];
            ctrlOpenLuaErrCode = new byte[4];
            slaveComError = new byte[8];
            driverComError = new byte[6];
            axleGenComData = new byte[130];
        }
    }

Typ wyliczeniowy konfiguracji informacji zwrotnej o stanie robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief  Wyliczenie konfigurowalnych stanów robota, zakres 0~132
    */
    public enum RobotState
    {
        FrameHead = 0,
        FrameCnt = 1,
        DataLen = 2,
        ProgramState = 3,
        RobotState = 4,
        MainCode = 5,
        SubCode = 6,
        RobotMode = 7,
        JointCurPos = 8,
        ToolCurPos = 9,
        FlangeCurPos = 10,
        ActualJointVel = 11,
        ActualJointAcc = 12,
        TargetTCPCmpSpeed = 13,
        TargetTCPSpeed = 14,
        ActualTCPCmpSpeed = 15,
        ActualTCPSpeed = 16,
        ActualJointTorque = 17,
        Tool = 18,
        User = 19,
        ClDgtOutputH = 20,
        ClDgtOutputL = 21,
        TlDgtOutputL = 22,
        ClDgtInputH = 23,
        ClDgtInputL = 24,
        TlDgtInputL = 25,
        ClAnalogInput = 26,
        TlAnglogInput = 27,
        FtSensorRawData = 28,
        FtSensorData = 29,
        FtSensorActive = 30,
        EmergencyStop = 31,
        MotionDone = 32,
        GripperMotiondone = 33,
        McQueueLen = 34,
        CollisionState = 35,
        TrajectoryPnum = 36,
        SafetyStop0State = 37,
        SafetyStop1State = 38,
        GripperFaultId = 39,
        GripperFault = 40,
        GripperActive = 41,
        GripperPosition = 42,
        GripperSpeed = 43,
        GripperCurrent = 44,
        GripperTemp = 45,
        GripperVoltage = 46,
        AuxState = 47,
        ExtAxisStatus = 48,
        ExtDIState = 49,
        ExtDOState = 50,
        ExtAIState = 51,
        ExtAOState = 52,
        RbtEnableState = 53,
        JointDriverTorque = 54,
        JointDriverTemperature = 55,
        RobotTime = 56,
        SoftwareUpgradeState = 57,
        EndLuaErrCode = 58,
        ClAnalogOutput = 59,
        TlAnalogOutput = 60,
        GripperRotNum = 61,
        GripperRotSpeed = 62,
        GripperRotTorque = 63,
        WeldingBreakOffState = 64,
        TargetJointTorque = 65,
        SmartToolState = 66,
        WideVoltageCtrlBoxTemp = 67,
        WideVoltageCtrlBoxFanCurrent = 68,
        ToolCoord = 69,
        WobjCoord = 70,
        ExtoolCoord = 71,
        ExAxisCoord = 72,
        Load = 73,
        LoadCog = 74,
        LastServoTarget = 75,
        ServoJCmdNum = 76,
        TargetJointPos = 77,
        TargetJointVel = 78,
        TargetJointAcc = 79,
        TargetJointCurrent = 80,
        ActualJointCurrent = 81,
        ActualTCPForce = 82,
        TargetTCPPos = 83,
        CollisionLevel = 84,
        SpeedScaleManual = 85,
        SpeedScaleAuto = 86,
        LuaLineNum = 87,
        AbnomalStop = 88,
        CurrentLuaFileName = 89,
        ProgramTotalLine = 90,
        SafetyBoxSingal = 91,
        WeldVoltage = 92,
        WeldCurrent = 93,
        WeldTrackVel = 94,
        TpdException = 95,
        AlarmRebootRobot = 96,
        ModbusMasterConnect = 97,
        ModbusSlaveConnect = 98,
        BtnBoxStopSignal = 99,
        DragAlarm = 100,
        SafetyDoorAlarm = 101,
        SafetyPlaneAlarm = 102,
        MotonAlarm = 103,
        InterfaceAlarm = 104,
        UdpCmdState = 105,
        WeldReadyState = 106,
        AlarmCheckEmergStopBtn = 107,
        TsTmCmdComError = 108,
        TsTmStateComError = 109,
        CtrlBoxError = 110,
        SafetyDataState = 111,
        ForceSensorErrState = 112,
        CtrlOpenLuaErrCode = 113,
        StrangePosFlag = 114,
        Alarm = 115,
        DriverAlarm = 116,
        AliveSlaveNumError = 117,
        SlaveComError = 118,
        CmdPointError = 119,
        IOError = 120,
        GripperError = 121,
        FileError = 122,
        ParaError = 123,
        ExaxisOutLimitError = 124,
        DriverComError = 125,
        DriverError = 126,
        OutSoftLimitError = 127,
        AxleGenComData = 128,
        SocketConnTimeout = 129,     // socket connection timeout, bit0-bit4: socketID 1-4
        SocketReadTimeout = 130,     // socket read timeout, bit0-bit4: socketID 1-4
        TsWebStateComErr = 131,     // web-torque communication failure; 0-normal; 1-failure
        ExaxisCoordID = 132          // Numer układu współrzędnych osi rozszerzonej
    }