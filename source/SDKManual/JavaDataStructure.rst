Opis struktur danych
====================

.. toctree::
    :maxdepth: 5

Typ danych pozycji stawów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Typ danych pozycji stawów
    */
    public class JointPos
    {
      double J1;
      double J2;
      double J3;
      double J4;
      double J5;
      double J6;

      public JointPos(double j1, double j2, double j3, double j4, double j5, double j6)
      {
        J1 = j1;
        J2 = j2;
        J3 = j3;
        J4 = j4;
        J5 = j5;
        J6 = j6;
      }

      public JointPos()
      {

      }
    }

Typ danych pozycji w przestrzeni kartezjańskiej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Typ danych pozycji w przestrzeni kartezjańskiej
    */
    public class DescTran
    {
      public double x = 0.0;    /* współrzędna osi X, jednostka mm  */
      public double y = 0.0;    /* współrzędna osi Y, jednostka mm  */
      public double z = 0.0;    /* współrzędna osi Z, jednostka mm  */
      public DescTran(double posX, double posY, double posZ)
      {
        x = posX;
        y = posY;
        z = posZ;
      }

      public DescTran()
      {

      }

    }

Typ danych orientacji kątów Eulera
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Typ danych orientacji kątów Eulera
    */
    public class Rpy
    {
      public double rx = 0.0;   /* kąt obrotu wokół stałej osi X, jednostka: deg  */
      public double ry = 0.0;   /* kąt obrotu wokół stałej osi Y, jednostka: deg  */
      public double rz = 0.0;   /* kąt obrotu wokół stałej osi Z, jednostka: deg  */
      public Rpy(double rotateX, double rotateY, double rotateZ)
      {
        rx = rotateX;
        ry = rotateY;
        rz = rotateZ;
      }
    }

Typ danych pozy i orientacji w przestrzeni kartezjańskiej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    *@brief Typ danych pozy i orientacji w przestrzeni kartezjańskiej
    */
    public class DescPose
    {
      public DescTran tran = new DescTran(0.0, 0.0, 0.0);      /* pozycja w przestrzeni kartezjańskiej  */
      public Rpy rpy = new Rpy(0.0, 0.0, 0.0);                 /* orientacja w przestrzeni kartezjańskiej  */

      public DescPose()
      {

      }

      public DescPose(DescTran descTran, Rpy rotateRpy)
      {
        tran = descTran;
        rpy = rotateRpy;
      }

      public DescPose(double tranX, double tranY, double tranZ, double rX, double ry, double rz)
      {
        tran.x = tranX;
        tran.y = tranY;
        tran.z = tranZ;
        rpy.rx = rX;
        rpy.ry = ry;
        rpy.rz = rz;
      }

      public String toString()
      {
        return String.valueOf(tran.x) + "," +  String.valueOf(tran.y) + "," +String.valueOf(tran.z) + "," +String.valueOf(rpy.rx) + "," +String.valueOf(rpy.ry) + "," +String.valueOf(rpy.rz);
      }
    }

Typ danych pozycji osi rozszerzonej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Typ danych pozycji osi rozszerzonej
    */
    public class ExaxisPos
    {
      public double axis1 = 0.0;
      public double axis2 = 0.0;
      public double axis3 = 0.0;
      public double axis4 = 0.0;

      public ExaxisPos()
      {

      }
      public ExaxisPos(double[] exaxisPos)
      {
        axis1 = exaxisPos[0];
        axis2 = exaxisPos[1];
        axis3 = exaxisPos[2];
        axis4 = exaxisPos[3];
      }

      public ExaxisPos(double pos1, double pos2, double pos3, double pos4)
      {
        axis1 = pos1;
        axis2 = pos2;
        axis3 = pos3;
        axis4 = pos4;
      }
    }

Typ danych czujnika siły/momentu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Składowe siły i momentu czujnika siły
    */
    public class ForceTorque
    {
      public double fx;  /* składowa siły wzdłuż osi X, jednostka N  */
      public double fy;  /* składowa siły wzdłuż osi Y, jednostka N  */
      public double fz;  /* składowa siły wzdłuż osi Z, jednostka N  */
      public double tx;  /* składowa momentu wokół osi X, jednostka Nm */
      public double ty;  /* składowa momentu wokół osi Y, jednostka Nm */
      public double tz;  /* składowa momentu wokół osi Z, jednostka Nm */
      public ForceTorque(double fX, double fY, double fZ, double tX, double tY, double tZ)
      {
        fx = fX;
        fy = fY;
        fz = fZ;
        tx = tX;
        ty = tY;
        tz = tZ;
      }
    }

Typ danych parametrów spirali
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Typ danych parametrów spirali
    */
    public class SpiralParam
    {
        public int circle_num;           /* liczba zwojów spirali  */
        public double circle_angle;         /* kąt nachylenia spirali  */
        public double rad_init;             /* początkowy promień spirali, jednostka mm  */
        public double rad_add;              /* przyrost promienia  */
        public double rotaxis_add;          /* przyrost w kierunku osi obrotu  */
        public int rot_direction;  /* kierunek obrotu, 0-zgodny z ruchem wskazówek zegara, 1-przeciwny do ruchu wskazówek zegara  */
        public int velAccMode;     /* tryb parametrów prędkości i przyspieszenia: 0-stała prędkość kątowa; 1-stała prędkość liniowa */
        public SpiralParam(int circleNum, double circleAngle, double radInit, double radAdd, double rotaxisAdd, int rotDirection,int vel_AccMode)
        {
            circle_num = circleNum;
            circle_angle = circleAngle;
            rad_init = radInit;
            rad_add = radAdd;
            rotaxis_add = rotaxisAdd;
            rot_direction = rotDirection;
            velAccMode=vel_AccMode;
        }
    }

Typ stanu osi rozszerzonej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Typ stanu osi rozszerzonej
    */
    public class EXT_AXIS_STATUS
    {
     public double pos = 0;        // pozycja osi rozszerzonej
     public double vel = 0;        // prędkość osi rozszerzonej
     public int errorCode = 0;     // kod błędu osi rozszerzonej
     public int ready = 0;        // serwo gotowe
     public int inPos = 0;        // serwo na pozycji
     public int alarm = 0;        // alarm serwa
     public int flerr = 0;        // błąd śledzenia
     public int nlimit = 0;       // osiągnięto ujemnego ogranicznika
     public int pLimit = 0;       // osiągnięto dodatniego ogranicznika
     public int mdbsOffLine = 0;  // magistrala 485 sterownika rozłączona
     public int mdbsTimeout = 0;  // przekroczenie czasu komunikacji 485 między kartą sterującą a szafą sterowniczą
     public int homingStatus = 0; // stan powrotu osi rozszerzonej do zera
    }

Typ czujnika
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Typ czujnika
    */
    public class DeviceConfig
    {
      int company = 0;          // producent
      int device = 0;           // typ/numer urządzenia
      int softwareVersion = 0;  // wersja oprogramowania
      int bus = 0;              // pozycja montażu

      public DeviceConfig()
      {

      }

      public DeviceConfig(int company, int device, int softwareVersion, int bus)
      {
        this.company = company;
        this.device = device;
        this.softwareVersion = softwareVersion;
        this.bus = bus;
      }
    }

Konfiguracja osi rozszerzonej 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Konfiguracja osi rozszerzonej 485
    */
    public class Axis485Param
    {
      int servoCompany;           // producent serwonapędu, 1-Dynatect
      int servoModel;             // model serwonapędu, 1-FD100-750C
      int servoSoftVersion;       // wersja oprogramowania serwonapędu, 1-V1.0
      int servoResolution;        // rozdzielczość enkodera
      double axisMechTransRatio;  // mechaniczne przełożenie transmisyjne

      public Axis485Param(int company, int model, int softVersion, int resolution, double mechTransRatio)
      {
        servoCompany = company;
        servoModel = model;
        servoSoftVersion = softVersion;
        servoResolution = resolution;
        axisMechTransRatio = mechTransRatio;
      }

      public Axis485Param()
      {

      }
    }

Stan sterownika serwonapędu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Stan sterownika serwonapędu
    */
    public class ROBOT_AUX_STATE
    {
      public int servoId = 0;           // ID serwonapędu
      public int servoErrCode = 0;       // kod błędu serwonapędu
      public int servoState = 0;         // stan serwonapędu
      public double servoPos = 0;        // bieżąca pozycja serwa
      public float servoVel = 0;         // bieżąca prędkość serwa
      public float servoTorque = 0;      // bieżący moment serwa    25
    }

Stan przerwania spawania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Stan przerwania spawania
    */
    public class WELDING_BREAKOFF_STATE
    {
      public int breakOffState = 0;  // stan przerwania spawania
      public int weldArcState = 0;   // stan przerwania łuku spawania
    }

Parametry komunikacji UDP osi rozszerzonej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Parametry komunikacji UDP osi rozszerzonej
    */
    public class EXTERNAL_AXIS_UDP_PARAM
    {
      public String ip = "192.168.58.88";// adres IP
      public int port = 2021;            // numer portu
      public int period = 2;             // okres komunikacji (ms, domyślnie 2, nie modyfikować tego parametru)
      public int lossPkgTime = 50;       // czas wykrywania utraty pakietów (ms)
      public int lossPkgNum = 2;         // liczba utraconych pakietów
      public int disconnectTime = 100;   // czas potwierdzenia przerwania komunikacji
      public int reconnectEnable = 0;    // włączenie automatycznego ponownego łączenia po przerwaniu komunikacji 0-nie włączone 1-włączone
      public int reconnectPeriod = 100;  // odstęp między próbami ponownego łączenia (ms)
      public int reconnectNum = 3;       // liczba prób ponownego łączenia
      public int selfConnect =0;         // czy automatycznie nawiązać połączenie po ponownym uruchomieniu zasilania; 0-nie nawiązuj; 1-nawiąż
    }

Typ struktury sprzężenia zwrotnego stanu robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Typ struktury sprzężenia zwrotnego stanu robota
    * /
    public class ROBOT_STATE_PKG {
        public int frame_head;                      // nagłówek ramki
        public int frame_cnt;                       // licznik ramek
        public int data_len;                        // długość danych
        public int program_state;                   // stan programu - 1-zatrzymany; 2-działa; 3-wstrzymany
        public int robot_state;                     // stan ruchu robota - 1-zatrzymany; 2-działa; 3-wstrzymany; 4-przeciągany
        public int main_code;                       // główny kod błędu
        public int sub_code;                        // podrzędny kod błędu
        public int robot_mode;                      // tryb robota - 1-tryb ręczny; 0-tryb automatyczny
        public double[] jt_cur_pos = new double[6]; // bieżące pozycje stawów 6 osi, jednostka deg
        public double[] tl_cur_pos = new double[6]; // bieżąca pozycja narzędzia - [x,y,z,rx,ry,rz]
        public double[] flange_cur_pos = new double[6]; // bieżąca pozycja kołnierza końcowego - [x,y,z,rx,ry,rz]
        public double[] actual_qd = new double[6];  // bieżące prędkości 6 stawów, jednostka deg/s
        public double[] actual_qdd = new double[6]; // bieżące przyspieszenia 6 stawów, jednostka deg/s^2
        public double[] target_TCP_CmpSpeed = new double[2]; // zadana prędkość wypadkowa TCP - [pozycja mm/s, orientacja deg/s]
        public double[] target_TCP_Speed = new double[6]; // zadana prędkość TCP - [vx,vy,vz,wx,wy,wz]
        public double[] actual_TCP_CmpSpeed = new double[2]; // rzeczywista prędkość wypadkowa TCP - [pozycja mm/s, orientacja deg/s]
        public double[] actual_TCP_Speed = new double[6]; // rzeczywista prędkość TCP - [vx,vy,vz,wx,wy,wz]
        public double[] jt_cur_tor = new double[6]; // bieżące momenty stawów
        public int tool;                            // ID narzędzia
        public int user;                            // ID obiektu
        public int cl_dgt_output_h;                 // wysoki bajt wyjścia cyfrowego szafy sterowniczej
        public int cl_dgt_output_l;                 // niski bajt wyjścia cyfrowego szafy sterowniczej
        public int tl_dgt_output_l;                 // niski bajt wyjścia cyfrowego narzędzia
        public int cl_dgt_input_h;                  // wysoki bajt wejścia cyfrowego szafy sterowniczej
        public int cl_dgt_input_l;                  // niski bajt wejścia cyfrowego szafy sterowniczej
        public int tl_dgt_input_l;                  // niski bajt wejścia cyfrowego narzędzia
        public int[] cl_analog_input = new int[2];  // wejście analogowe szafy sterowniczej
        public int tl_anglog_input;                 // wejście analogowe narzędzia
        public double[] ft_sensor_raw_data = new double[6]; // surowe dane czujnika siły
        public double[] ft_sensor_data = new double[6]; // dane czujnika siły
        public int ft_sensor_active;                // stan aktywacji czujnika siły
        public int EmergencyStop;                   // stan awaryjnego zatrzymania
        public int motion_done;                     // ruch zakończony
        public int gripper_motiondone;              // Sygnał zakończenia ruchu chwytaka, 0-nie zakończono, 1-zakończono (nie wykryto obiektu), 2-ruch zakończony (wykryto obiekt)
        public int mc_queue_len;                    // długość kolejki ruchu
        public int collisionState;                  // stan kolizji
        public int trajectory_pnum;                 // numer punktu trajektorii
        public int safety_stop0_state;              // stan bezpiecznego zatrzymania 0
        public int safety_stop1_state;              // stan bezpiecznego zatrzymania 1
        public int gripper_fault_id;                // ID błędu chwytaka
        public int gripper_fault;                   // błąd chwytaka
        public int gripper_active;                  // aktywacja chwytaka
        public int gripper_position;                // pozycja chwytaka
        public int gripper_speed;                   // prędkość chwytaka
        public int gripper_current;                 // prąd chwytaka
        public int gripper_temp;                    // temperatura chwytaka
        public int gripper_voltage;                 // napięcie chwytaka
        public AuxState aux_state = new AuxState(); // stan wewnętrznej osi pomocniczej
        public EXT_AXIS_STATUS[] extAxisStatus = new EXT_AXIS_STATUS[4]; // tablica stanów osi rozszerzonej
        public short[] extDIState = new short[8];   // rozszerzone IO - DI
        public short[] extDOState = new short[8];   // rozszerzone IO - DO
        public short[] extAIState = new short[4];   // rozszerzone IO - AI
        public short[] extAOState = new short[4];   // rozszerzone IO - AO
        public int rbtEnableState;                  // stan włączenia robota
        public double[] jointDriverTorque = new double[6]; // momenty sterowników stawów
        public double[] jointDriverTemperature = new double[6]; // temperatury sterowników stawów
        public ROBOT_TIME robotTime = new ROBOT_TIME(); // obiekt czasu robota
        public int softwareUpgradeState;            // stan aktualizacji oprogramowania
        public int endLuaErrCode;                   // kod błędu Lua końcówki
        public int[] cl_analog_output = new int[2]; // wyjście analogowe szafy sterowniczej
        public int tl_analog_output;                // wyjście analogowe narzędzia
        public float gripperRotNum;                 // liczba obrotów chwytaka obrotowego
        public int gripperRotSpeed;                 // prędkość chwytaka obrotowego
        public int gripperRotTorque;                // moment chwytaka obrotowego
        public WELDING_BREAKOFF_STATE weldingBreakOffState = new WELDING_BREAKOFF_STATE(); // stan przerwania spawania
        public double[] jt_tgt_tor = new double[6]; // docelowe momenty stawów
        public int smartToolState;                  // stan inteligentnego narzędzia
        public float wideVoltageCtrlBoxTemp;        // temperatura szafy sterowniczej z szerokim zakresem napięcia
        public int wideVoltageCtrlBoxFanCurrent;    // prąd wentylatora szafy sterowniczej z szerokim zakresem napięcia
        public double[] toolCoord = new double[6];  // układ współrzędnych narzędzia
        public double[] wobjCoord = new double[6];  // układ współrzędnych obiektu
        public double[] extoolCoord = new double[6]; // zewnętrzny układ współrzędnych narzędzia
        public double[] exAxisCoord = new double[6]; // układ współrzędnych osi rozszerzonej
        public double load;                         // obciążenie
        public double[] loadCog = new double[3];    // środek ciężkości obciążenia
        public double[] lastServoTarget = new double[6]; // poprzednia docelowa pozycja servoJ
        public int servoJCmdNum;                    // liczba poleceń servoJ
        public double[] targetJointPos = new double[6]; // docelowa pozycja stawów
        public double[] targetJointVel = new double[6]; // docelowa prędkość stawów
        public double[] targetJointAcc = new double[6]; // docelowe przyspieszenie stawów
        public double[] targetJointCurrent = new double[6]; // docelowy prąd stawów
        public double[] actualJointCurrent = new double[6]; // rzeczywisty prąd stawów
        public double[] actualTCPForce = new double[6]; // rzeczywista siła TCP
        public double[] targetTCPPos = new double[6]; // docelowa pozycja TCP
        public int[] collisionLevel = new int[6];   // poziom kolizji
        public double speedScaleManual;              // proporcja prędkości w trybie ręcznym
        public double speedScaleAuto;                // proporcja prędkości w trybie automatycznym
        public int luaLineNum;                       // numer linii Lua
        public int abnomalStop;                      // zatrzymanie awaryjne
        public String currentLuaFileName;            // bieżąca nazwa pliku Lua
        public int programTotalLine;                 // całkowita liczba linii programu
        public int[] safetyBoxSingal = new int[6];   // sygnały skrzynki bezpieczeństwa
        public double weldVoltage;                   // napięcie spawania
        public double weldCurrent;                   // prąd spawania
        public double weldTrackVel;                  // prędkość śledzenia spawania
        public int tpdException;                     // wyjątek TPD
        public int alarmRebootRobot;                 // alarm - restart robota
        public int modbusMasterConnect;              // połączenie mastera Modbus
        public int modbusSlaveConnect;               // połączenie slave'a Modbus
        public int btnBoxStopSignal;                 // sygnał zatrzymania z przycisku
        public int dragAlarm;                        // alarm przeciągania
        public int safetyDoorAlarm;                  // alarm drzwi bezpieczeństwa
        public int safetyPlaneAlarm;                 // alarm płaszczyzny bezpieczeństwa
        public int motonAlarm;                       // alarm ruchu
        public int interfaceAlarm;                   // alarm interferencji
        public int udpCmdState;                      // stan polecenia UDP
        public int weldReadyState;                   // stan gotowości spawania
        public int alarmCheckEmergStopBtn;           // alarm - sprawdzenie przycisku awaryjnego zatrzymania
        public int tsTmCmdComError;                  // błąd komunikacji polecenia
        public int tsTmStateComError;                // błąd komunikacji stanu
        public int ctrlBoxError;                     // błąd szafy sterowniczej
        public int safetyDataState;                  // stan danych bezpieczeństwa
        public int forceSensorErrState;              // stan błędu czujnika siły
        public int[] ctrlOpenLuaErrCode = new int[4]; // kod błędu otwarcia Lua sterowania
        public int strangePosFlag;                   // flaga osobliwej pozycji
        public int alarm;                            // alarm
        public int driverAlarm;                      // alarm sterownika
        public int aliveSlaveNumError;               // błąd liczby aktywnych stacji podrzędnych
        public int[] slaveComError = new int[8];     // błąd komunikacji stacji podrzędnej
        public int cmdPointError;                    // błąd punktu polecenia
        public int IOError;                          // błąd IO
        public int gripperError;                     // błąd chwytaka
        public int fileError;                        // błąd pliku
        public int paraError;                        // błąd parametru
        public int exaxisOutLimitError;              // błąd przekroczenia miękkiego ograniczenia osi rozszerzonej
        public int[] driverComError = new int[6];    // błąd komunikacji ze sterownikiem
        public int driverError;                      // błąd sterownika
        public int outSoftLimitError;                // błąd przekroczenia miękkiego ograniczenia
        public byte[] axleGenComData = new byte[130]; // dane komunikacji ogólnej osi
        public int check_sum;                        // suma kontrolna
        public int socketConnTimeout;                // przekroczenie czasu połączenia socket
        public int socketReadTimeout;                // przekroczenie czasu odczytu socket
        public int tsWebStateComErr;                 // błąd komunikacji stanu TS Web
        public int exaxisCoordID;                  // numer układu współrzędnych osi rozszerzonej
    }

Klasa wyniku konfiguracji sprzężenia zwrotnego stanu robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * Klasa wyniku konfiguracji sprzężenia zwrotnego stanu robota, zawiera listę stanów i okres
    */
    public static class StateConfigResult {
      public final List<RobotState> stateList;
      public final int period;
    }

Typ wyliczeniowy konfiguracji sprzężenia zwrotnego stanu robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * Typ wyliczeniowy stanu robota
    * Używany do konfiguracji sprzężenia zwrotnego stanu w czasie rzeczywistym
    */
    enum class RobotState
    {
        ProgramState,           // Stan programu, 1-zatrzymany; 2-działa; 3-wstrzymany
        RobotState,             // Stan ruchu robota, 1-zatrzymany; 2-działa; 3-wstrzymany; 4-przeciągany
        MainCode,               // Główny kod błędu
        SubCode,                // Podrzędny kod błędu
        RobotMode,              // Tryb robota, 1-tryb ręczny; 0-tryb automatyczny
        JointCurPos,            // Bieżące pozycje stawów 6 osi, jednostka deg
        ToolCurPos,             // Bieżąca pozycja narzędzia: [0] pozycja wzdłuż osi X (mm), [1] wzdłuż osi Y (mm), [2] wzdłuż osi Z (mm), [3] obrót wokół stałej osi X (deg), [4] obrót wokół stałej osi Y (deg), [5] obrót wokół stałej osi Z (deg)
        FlangeCurPos,          // Bieżąca pozycja kołnierza końcowego: [0] wzdłuż osi X (mm), [1] wzdłuż osi Y (mm), [2] wzdłuż osi Z (mm), [3] obrót wokół stałej osi X (deg), [4] obrót wokół stałej osi Y (deg), [5] obrót wokół stałej osi Z (deg)
        ActualJointVel,        // Bieżące prędkości 6 stawów, jednostka deg/s
        ActualJointAcc,        // Bieżące przyspieszenia 6 stawów, jednostka deg/s^2
        TargetTCPCmpSpeed,     // Zadana prędkość wypadkowa TCP: [0] pozycja (mm/s), [1] orientacja (deg/s)
        TargetTCPSpeed,        // Zadana prędkość TCP: [0] wzdłuż osi X (mm/s), [1] wzdłuż osi Y (mm/s), [2] wzdłuż osi Z (mm/s), [3] prędkość kątowa wokół X (deg/s), [4] wokół Y (deg/s), [5] wokół Z (deg/s)
        ActualTCPCmpSpeed,     // Rzeczywista prędkość wypadkowa TCP: [0] pozycja (mm/s), [1] orientacja (deg/s)
        ActualTCPSpeed,        // Rzeczywista prędkość TCP: [0] wzdłuż osi X (mm/s), [1] wzdłuż osi Y (mm/s), [2] wzdłuż osi Z (mm/s), [3] prędkość kątowa wokół X (deg/s), [4] wokół Y (deg/s), [5] wokół Z (deg/s)
        ActualJointTorque,     // Bieżące momenty 6 stawów, jednostka N·m
        Tool,                  // Numer zastosowanego układu współrzędnych narzędzia
        User,                  // Numer zastosowanego układu współrzędnych obiektu
        ClDgtOutputH,          // Wyjście cyfrowe IO szafy sterowniczej 15-8
        ClDgtOutputL,          // Wyjście cyfrowe IO szafy sterowniczej 7-0
        TlDgtOutputL,          // Wyjście cyfrowe IO narzędzia 7-0, tylko bity 0-1 są ważne
        ClDgtInputH,           // Wejście cyfrowe IO szafy sterowniczej 15-8
        ClDgtInputL,           // Wejście cyfrowe IO szafy sterowniczej 7-0
        TlDgtInputL,           // Wejście cyfrowe IO narzędzia 7-0, tylko bity 0-1 są ważne
        ClAnalogInput,         // Wejście analogowe szafy sterowniczej: [0] kanał 0, [1] kanał 1
        TlAnalogInput,         // Wejście analogowe narzędzia
        FtSensorRawData,       // Surowe dane czujnika siły/momentu: [0] siła wzdłuż osi X (N), [1] siła wzdłuż osi Y (N), [2] siła wzdłuż osi Z (N), [3] moment wokół osi X (Nm), [4] moment wokół osi Y (Nm), [5] moment wokół osi Z (Nm)
        FtSensorData,          // Dane czujnika siły/momentu (przetworzone): [0] siła wzdłuż osi X (N), [1] siła wzdłuż osi Y (N), [2] siła wzdłuż osi Z (N), [3] moment wokół osi X (Nm), [4] moment wokół osi Y (Nm), [5] moment wokół osi Z (Nm)
        FtSensorActive,        // Stan aktywacji czujnika siły/momentu, 0-reset, 1-aktywacja
        EmergencyStop,         // Flaga awaryjnego zatrzymania, 0-awaryjne zatrzymanie niewciśnięte, 1-awaryjne zatrzymanie wciśnięte
        MotionDone,            // Sygnał osiągnięcia pozycji, 1-osiągnięto, 0-nie osiągnięto
        GripperMotiondone,     // Sygnał zakończenia ruchu chwytaka, 1-zakończono, 0-nie zakończono
        McQueueLen,            // Długość kolejki instrukcji ruchu
        CollisionState,        // Wykrywanie kolizji, 1-kolizja, 0-brak kolizji
        TrajectoryPnum,        // Numer punktu trajektorii
        SafetyStop0State,      // Sygnał bezpiecznego zatrzymania SI0
        SafetyStop1State,      // Sygnał bezpiecznego zatrzymania SI1
        GripperFaultId,        // Numer chwytaka z błędem
        GripperFault,          // Błąd chwytaka
        GripperActive,         // Stan aktywacji chwytaka
        GripperPosition,       // Pozycja chwytaka
        GripperSpeed,          // Prędkość chwytaka
        GripperCurrent,        // Prąd chwytaka
        GripperTemp,           // Temperatura chwytaka
        GripperVoltage,        // Napięcie chwytaka
        AuxState,              // Stan osi rozszerzonej 485
        ExtAxisStatus,         // Stan osi rozszerzonej UDP (4 osie)
        ExtDIState,            // Rozszerzone wejście DI (8)
        ExtDOState,            // Rozszerzone wyjście DO (8)
        ExtAIState,            // Rozszerzone wejście AI (4)
        ExtAOState,            // Rozszerzone wyjście AO (4)
        RbtEnableState,        // Stan włączenia robota
        JointDriverTorque,     // Moment sterownika stawów robota (6 stawów)
        JointDriverTemperature,// Temperatura sterownika stawów robota (6 stawów)
        RobotTime,             // Czas systemowy robota
        SoftwareUpgradeState,  // Stan aktualizacji oprogramowania robota
        EndLuaErrCode,         // Stan wykonania LUA końcówki
        ClAnalogOutput,        // Wyjście analogowe szafy sterowniczej (2)
        TlAnalogOutput,        // Wyjście analogowe narzędzia
        GripperRotNum,         // Bieżąca liczba obrotów chwytaka obrotowego
        GripperRotSpeed,       // Bieżący procent prędkości obrotowej chwytaka obrotowego
        GripperRotTorque,      // Bieżący procent momentu obrotowego chwytaka obrotowego
        WeldingBreakOffState,  // Stan przerwania spawania
        TargetJointTorque,     // Docelowy moment stawów (6 stawów)
        SmartToolState,        // Stan przycisków uchwytu SmartTool
        WideVoltageCtrlBoxTemp,// Temperatura szafy sterowniczej z szerokim zakresem napięcia
        WideVoltageCtrlBoxFanCurrent, // Prąd wentylatora szafy sterowniczej z szerokim zakresem napięcia (mA)
        ToolCoord,             // Wartości bieżącego układu współrzędnych narzędzia: x, y, z, rx, ry, rz
        WobjCoord,             // Wartości bieżącego układu współrzędnych obiektu: x, y, z, rx, ry, rz
        ExtoolCoord,           // Wartości bieżącego zewnętrznego układu współrzędnych narzędzia: x, y, z, rx, ry, rz
        ExAxisCoord,           // Wartości bieżącego układu współrzędnych osi rozszerzonej: x, y, z, rx, ry, rz
        Load,                  // Masa obciążenia
        LoadCog,               // Środek ciężkości obciążenia: x, y, z
        LastServoTarget,       // Ostatnia docelowa pozycja ServoJ w kolejce (6 stawów)
        ServoJCmdNum,          // Licznik instrukcji servoJ
        TargetJointPos,        // Docelowa pozycja 6 stawów, jednostka °
        TargetJointVel,        // Docelowa prędkość 6 stawów, jednostka °/s
        TargetJointAcc,        // Docelowe przyspieszenie 6 stawów, jednostka °/s²
        TargetJointCurrent,    // Docelowy prąd 6 stawów, jednostka A
        ActualJointCurrent,    // Bieżący prąd 6 stawów, jednostka A
        ActualTCPForce,        // Moment na końcówce robota: x, y, z, rx, ry, rz, jednostka Nm
        TargetTCPPos,          // Docelowa pozycja TCP robota: x, y, z, rx, ry, rz, jednostka mm
        CollisionLevel,        // Poziom kolizji robota (6)
        SpeedScaleManual,      // Globalny procent prędkości w trybie ręcznym
        SpeedScaleAuto,        // Globalny procent prędkości w trybie automatycznym
        LuaLineNum,            // Numer bieżącej linii programu lua
        AbnomalStop,           // 0-brak wyjątku; 1-wystąpił wyjątek
        CurrentLuaFileName,    // Nazwa bieżącego uruchomionego programu lua
        ProgramTotalLine,      // Całkowita liczba linii programu lua
        SafetyBoxSingal,       // Stan przycisków skrzynki przycisków robota (6)
        WeldVoltage,           // Napięcie spawania V
        WeldCurrent,           // Prąd spawania
        WeldTrackVel,          // Prędkość śledzenia spawiny mm/s
        TpdException,          // Przekroczenie limitu ładowania trajektorii TPD, 0-nie przekroczono, 1-przekroczono
        AlarmRebootRobot,      // Ostrzeżenie: 1-po zwolnieniu awaryjnego zatrzymania wymagane odcięcie zasilania i restart, 2-nieprawidłowa komunikacja stawów wymagane odcięcie zasilania i restart
        ModbusMasterConnect,   // bity 0-7 odpowiadają stanom połączenia masterów Modbus TCP 0-7, 0-niepołączony, 1-połączony
        ModbusSlaveConnect,    // Stan połączenia slave'a Modbus TCP, 0-niepołączony, 1-połączony
        BtnBoxStopSignal,      // Sygnał awaryjnego zatrzymania skrzynki przycisków, 0-zwolniony awaryjny stop, 1-wciśnięty awaryjny stop
        DragAlarm,            // Ostrzeżenie przeciągania: 0-brak alarmu, 1-alarm, 2-nieprawidłowe sprzężenie zwrotne pozycji - brak przełączania
        SafetyDoorAlarm,      // Ostrzeżenie drzwi bezpieczeństwa: 0-zamknięte, 1-otwarte
        SafetyPlaneAlarm,     // Ostrzeżenie ściany bezpieczeństwa: 0-nie wchodzono, 1-wchodzono
        MotonAlarm,           // Ostrzeżenie ruchu
        InterfaceAlarm,       // Ostrzeżenie wejścia w obszar interferencji
        UdpCmdState,          // Stan połączenia komunikacji UDP na porcie 20007
        WeldReadyState,       // Stan gotowości spawarki
        AlarmCheckEmergStopBtn, // 0-normalny; 1-nieprawidłowa komunikacja, sprawdź przycisk awaryjnego zatrzymania
        TsTmCmdComError,      // 0-normalny; 1-nieudana komunikacja polecenia momentu
        TsTmStateComError,    // 0-normalny; 1-nieudana komunikacja stanu momentu
        CtrlBoxError,         // Błąd szafy sterowniczej
        SafetyDataState,      // Stan danych bezpieczeństwa, 0-normalny, 1-nieprawidłowy
        ForceSensorErrState,  // Przekroczenie czasu połączenia czujnika siły, bity 0-1 odpowiadają ID1-ID2
        CtrlOpenLuaErrCode,   // Kody błędów 4 protokołów urządzeń peryferyjnych sterownika (kod błędu 500)
        StrangePosFlag,       // Flaga osobliwej pozy i orientacji: 0-normalny, 1-osobliwa pozy i orientacja
        Alarm,                // Ostrzeżenie
        DriverAlarm,          // Numer osi z alarmem sterownika
        AliveSlaveNumError,   // Błąd liczby aktywnych stacji podrzędnych: 0-normalny, 1-błąd liczby
        SlaveComError,        // Błąd stacji podrzędnej: 0-normalny, 1-rozłączona, 2-niezgodność stanu, 3-nieskonfigurowana, 4-błąd konfiguracji, 5-błąd inicjalizacji, 6-błąd inicjalizacji komunikacji e-mail
        CmdPointError,        // Błąd punktu instrukcji
        IOError,              // Błąd IO
        GripperError,         // Błąd chwytaka
        FileError,            // Błąd pliku
        ParaError,            // Błąd parametru
        ExaxisOutLimitError,  // Błąd przekroczenia miękkiego ograniczenia osi zewnętrznej
        DriverComError,       // Błąd komunikacji ze sterownikiem (6 osi)
        DriverError,          // Numer osi z błędem komunikacji sterownika
        OutSoftLimitError,    // Błąd przekroczenia miękkiego ograniczenia
        AxleGenComData,       // Dane sprzężenia zwrotnego transmisji przez końcówkę robota
        SocketConnTimeout,    // Przekroczenie czasu połączenia socket, bity 0-4 odpowiadają socketID 1-4
        SocketReadTimeout,    // Przekroczenie czasu odczytu socket, bity 0-4 odpowiadają socketID 1-4
        TsWebStateComErr,     // Nieudana komunikacja momentu web: 0-normalny, 1-nieudana
        ExaxisCoordID          // numer układu współrzędnych osi rozszerzonej
    };