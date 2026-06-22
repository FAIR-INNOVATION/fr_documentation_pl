Spawanie robotem
================

.. toctree:: 
    :maxdepth: 5


Ustawianie parametrów krzywej procesu spawania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Ustawianie parametrów krzywej procesu spawania
    * @param [in] id Numer procesu spawania (1-99)
    * @param [in] param Parametry procesu spawania
    * @return Kod błędu 
    */
    int WeldingSetProcessParam(int id, WeldingProcessParam param);

Pobieranie parametrów krzywej procesu spawania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Pobieranie parametrów krzywej procesu spawania
    * @param [in] id Numer procesu spawania (1-99)
    * @param [out] param Parametry procesu spawania
    * @return Kod błędu 
    */
    int WeldingGetProcessParam(int id, WeldingProcessParam param);

Ustawianie zależności między prądem spawania a wyjściowym sygnałem analogowym
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawianie zależności między prądem spawania a wyjściowym sygnałem analogowym
    * @param [in] relation Wartość zależności
    * @return Kod błędu
    */
    int WeldingSetCurrentRelation(WeldCurrentAORelation relation);

Ustawianie zależności między napięciem spawania a wyjściowym sygnałem analogowym
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawianie zależności między napięciem spawania a wyjściowym sygnałem analogowym
    * @param [in] relation Wartość zależności napięcie spawania - wyjście analogowe
    * @return Kod błędu
    */
    int WeldingSetVoltageRelation(WeldVoltageAORelation relation);

Pobieranie zależności między prądem spawania a wyjściowym sygnałem analogowym
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Pobieranie zależności między prądem spawania a wyjściowym sygnałem analogowym
    * @param [out] relation Wartość zależności
    * @return Kod błędu
    */
    int WeldingGetCurrentRelation(WeldCurrentAORelation relation);

Pobieranie zależności między napięciem spawania a wyjściowym sygnałem analogowym
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Pobieranie zależności między napięciem spawania a wyjściowym sygnałem analogowym
    * @param [out] relation Wartość zależności napięcie spawania - wyjście analogowe
    * @return Kod błędu
    */
    int WeldingGetVoltageRelation(WeldVoltageAORelation relation);

Ustawianie prądu spawania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawianie prądu spawania
    * @param [in] ioType Typ IO sterowania 0-IO skrzynki kontrolnej; 1-rozszerzone IO
    * @param [in] current Wartość prądu spawania (A)
    * @param [in] AOIndex Port wyjścia analogowego prądu spawania skrzynki kontrolnej (0-1)
    * @param [in] blend Czy wygładzać 0-nie; 1-tak
    * @return Kod błędu
    */
    int WeldingSetCurrent(int ioType, double current, int AOIndex, int blend);

Ustawianie napięcia spawania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawianie napięcia spawania
    * @param [in] ioType Typ IO sterowania 0-IO skrzynki kontrolnej; 1-rozszerzone IO
    * @param [in] voltage Wartość napięcia spawania (V)
    * @param [in] AOIndex Port wyjścia analogowego napięcia spawania skrzynki kontrolnej (0-1)
    * @param [in] blend Czy wygładzać 0-nie; 1-tak
    * @return Kod błędu
    */
    int WeldingSetVoltage(int ioType, double voltage, int AOIndex, int blend);

Ustawianie parametrów ruchu wahadłowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionchanged:: Java SDK-v1.0.5-3.8.2

.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawianie parametrów ruchu wahadłowego
    * @param [in] weaveNum Numer konfiguracji parametrów spawania wahadłowego
    * @param [in] weaveType Typ wahadła 0-płaskie wahadło trójkątne; 1-pionowe wahadło trójkątne typu L; 2-kołowe wahadło zgodne z ruchem wskazówek zegara; 3-kołowe wahadło przeciwnie do ruchu wskazówek zegara; 4-płaskie wahadło sinusoidalne; 5-pionowe wahadło sinusoidalne typu L; 6-pionowe wahadło trójkątne; 7-pionowe wahadło sinusoidalne
    * @param [in] weaveFrequency Częstotliwość wahadła (Hz)
    * @param [in] weaveIncStayTime Tryb oczekiwania 0-cykl nie zawiera czasu oczekiwania; 1-cykl zawiera czas oczekiwania
    * @param [in] weaveRange Amplituda wahadła (mm)
    * @param [in] weaveLeftRange Długość lewej cięciwy w pionowym wahadle trójkątnym (mm)
    * @param [in] weaveRightRange Długość prawej cięciwy w pionowym wahadle trójkątnym (mm)
    * @param [in] additionalStayTime Czas postoju w punkcie wierzchołkowym pionowego wahadła trójkątnego (ms)
    * @param [in] weaveLeftStayTime Czas postoju po lewej stronie wahadła (ms)
    * @param [in] weaveRightStayTime Czas postoju po prawej stronie wahadła (ms)
    * @param [in] weaveCircleRadio Wahadło kołowe - współczynnik powrotu (0-100%)
    * @param [in] weaveStationary Oczekiwanie w pozycji wahadła, 0-ruch kontynuowany w czasie oczekiwania; 1-pozycja nieruchoma w czasie oczekiwania
    * @param [in] weaveYawAngle Azymut kierunku wahadła (obrót wokół osi Z wahadła), jednostka °
    * @param [in] weaveRotAngle Azymut kierunku wahadła (obrót wokół osi X wahadła), jednostka °
    * @return Kod błędu
    */
    int WeaveSetPara(int weaveNum, int weaveType, double weaveFrequency, int weaveIncStayTime, double weaveRange, double weaveLeftRange, double weaveRightRange, int additionalStayTime, int weaveLeftStayTime, int weaveRightStayTime, int weaveCircleRadio, int weaveStationary, double weaveYawAngle,double weaveRotAngle)

Przykład kodu ustawiania parametrów spawania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestSetWeldParam(Robot robot)
    {
        WeldingProcessParam para1=new WeldingProcessParam(177, 27, 1000, 178, 28, 176, 26, 1000);
        WeldingProcessParam para2=new WeldingProcessParam(188, 28, 555, 199, 29, 133, 23, 333);

        robot.WeldingSetProcessParam(1, para1);
        robot.WeldingSetProcessParam(2, para2);

        double startCurrent = 0;
        double startVoltage = 0;
        int startTime = 0;
        double weldCurrent = 0;
        double weldVoltage = 0;
        double endCurrent = 0;
        double endVoltage = 0;
        int endTime = 0;

        WeldingProcessParam param=new WeldingProcessParam( startCurrent, startVoltage, startTime, weldCurrent, weldVoltage, endCurrent, endVoltage, endTime);
        robot.WeldingGetProcessParam(1,param);
        robot.WeldingGetProcessParam(2,param);

        WeldCurrentAORelation rela1=new WeldCurrentAORelation(0,400,0,10,0);
        int rtn = robot.WeldingSetCurrentRelation(rela1);

        WeldVoltageAORelation rela2=new WeldVoltageAORelation(0, 40, 0, 10, 1);
        rtn = robot.WeldingSetVoltageRelation(rela2);

        double current_min = 0;
        double current_max = 0;
        double vol_min = 0;
        double vol_max = 0;
        double output_vmin = 0;
        double output_vmax = 0;
        int curIndex = 0;
        int volIndex = 0;
        WeldCurrentAORelation rela3=new WeldCurrentAORelation(current_min, current_max, output_vmin, output_vmax, curIndex);
        rtn = robot.WeldingGetCurrentRelation(rela3);

        WeldVoltageAORelation rela4=new WeldVoltageAORelation(0,0,0,0,0);
        rtn = robot.WeldingGetVoltageRelation(rela4);

        rtn = robot.WeldingSetCurrent(0, 100, 0, 0);

        robot.Sleep(3000);

        rtn = robot.WeldingSetVoltage(0, 10, 0, 0);

        rtn = robot.WeaveSetPara(0, 0, 2.000000, 0, 10.000000, 0.000000, 0.000000, 0, 0, 0, 0, 0, 60.000000,0);

        robot.WeaveOnlineSetPara(0, 0, 1, 0, 20, 0, 0, 0, 0);

        rtn = robot.WeldingSetCheckArcInterruptionParam(1, 200);
        rtn = robot.WeldingSetReWeldAfterBreakOffParam(1, 5.7, 98.2, 0);
        int enable = 0;
        double length = 0;
        double velocity = 0;
        int moveType = 0;
        int checkEnable = 0;
        int arcInterruptTimeLength = 0;
        List<Integer> inter=new ArrayList<>();
        List<Number> num=new ArrayList<>();

        inter = robot.WeldingGetCheckArcInterruptionParam();
        num = robot.WeldingGetReWeldAfterBreakOffParam();

        robot.SetWeldMachineCtrlModeExtDoNum(17);
        for (int i = 0; i < 5; i++)
        {
            robot.SetWeldMachineCtrlMode(0);
            robot.Sleep(1000);
            robot.SetWeldMachineCtrlMode(1);
            robot.Sleep(1000);
        }
        return 0;
    }

Natychmiastowe ustawianie parametrów ruchu wahadłowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Natychmiastowe ustawianie parametrów ruchu wahadłowego
    * @param [in] weaveNum Numer konfiguracji parametrów spawania wahadłowego
    * @param [in]weaveType Typ wahadła 0-płaskie wahadło trójkątne; 1-pionowe wahadło trójkątne typu L; 2-kołowe wahadło zgodne z ruchem wskazówek zegara; 3-kołowe wahadło przeciwnie do ruchu wskazówek zegara; 4-płaskie wahadło sinusoidalne; 5-pionowe wahadło sinusoidalne typu L; 6-pionowe wahadło trójkątne; 7-pionowe wahadło sinusoidalne
    * @param [in]weaveFrequency Częstotliwość wahadła (Hz)
    * @param [in]weaveIncStayTime Tryb oczekiwania 0-cykl nie zawiera czasu oczekiwania; 1-cykl zawiera czas oczekiwania
    * @param [in]weaveRange Amplituda wahadła (mm)
    * @param [in]weaveLeftStayTime Czas postoju po lewej stronie wahadła (ms)
    * @param [in]weaveRightStayTime Czas postoju po prawej stronie wahadła (ms)
    * @param [in]weaveCircleRadio Wahadło kołowe - współczynnik powrotu (0-100%)
    * @param [in]weaveStationary Oczekiwanie w pozycji wahadła, 0-ruch kontynuowany w czasie oczekiwania; 1-pozycja nieruchoma w czasie oczekiwania
    * @return Kod błędu
    */
    int WeaveOnlineSetPara(int weaveNum, int weaveType, double weaveFrequency, int weaveIncStayTime, double weaveRange, int weaveLeftStayTime, int weaveRightStayTime, int weaveCircleRadio, int weaveStationary);

Ustawianie parametrów wykrywania nieoczekiwanego przerwania łuku spawalniczego robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Ustawianie parametrów wykrywania nieoczekiwanego przerwania łuku spawalniczego robota
    * @param [in] checkEnable Czy włączyć wykrywanie; 0-nie; 1-tak
    * @param [in] arcInterruptTimeLength Czas potwierdzenia przerwania łuku (ms)
    * @return Kod błędu 
    */
    int WeldingSetCheckArcInterruptionParam(int checkEnable, int arcInterruptTimeLength);

Pobieranie parametrów wykrywania nieoczekiwanego przerwania łuku spawalniczego robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Pobieranie parametrów wykrywania nieoczekiwanego przerwania łuku spawalniczego robota
    * @return List[0]:Kod błędu; List[1]:double Czy włączyć wykrywanie; 0-nie; 1-tak; List[2]:Czas potwierdzenia przerwania łuku (ms) 
    */
    List<Integer> WeldingGetCheckArcInterruptionParam();

Ustawianie parametrów wznawiania spawania po przerwaniu robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Ustawianie parametrów wznawiania spawania po przerwaniu robota
    * @param [in] enable Czy włączyć wznawianie spawania po przerwaniu
    * @param [in] length Długość zakładki spoiny (mm)
    * @param [in] velocity Procent prędkości powrotu robota do punktu ponownego zapłonu łuku (0-100)
    * @param [in] moveType Sposób ruchu robota do punktu ponownego zapłonu łuku; 0-LIN; 1-PTP
    * @return Kod błędu 
    */
    int WeldingSetReWeldAfterBreakOffParam(int enable, double length, double velocity, int moveType);

Pobieranie parametrów wznawiania spawania po przerwaniu robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Pobieranie parametrów wznawiania spawania po przerwaniu robota
    * @return List[0]:Kod błędu; List[1]:int Czy włączyć wznawianie spawania po przerwaniu; List[2]:double Długość zakładki spoiny (mm);
    * @return List[3]:double Procent prędkości powrotu robota do punktu ponownego zapłonu łuku (0-100);List[4]:int Sposób ruchu robota do punktu ponownego zapłonu łuku; 0-LIN; 1-PTP 
    */
    List<Number> WeldingGetReWeldAfterBreakOffParam();

Ustawianie rozszerzonego portu DO trybu sterowania spawarką
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Ustawianie rozszerzonego portu DO trybu sterowania spawarką
    * @param [in] DONum Port DO trybu sterowania spawarką (0-127)
    * @return Kod błędu 
    */
    int SetWeldMachineCtrlModeExtDoNum(int DONum);

Ustawianie trybu sterowania spawarką
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawianie trybu sterowania spawarką
    * @param mode Tryb sterowania spawarką; 0-tryb jednowartościowy DC; 1-tryb jednowartościowy impulsowy; 2-tryb JOB; 3-tryb sterowania lokalnego; 4-tryb oddzielny; 5-tryb CC/CV; 6-TIG; 7-CMT
    * @param ioType Typ sterowania; 0-IO skrzynki kontrolnej; 1-protokół komunikacji cyfrowej (UDP); 2-protokół komunikacji cyfrowej (ModbusTCP)
    * @return Kod błędu* @return Kod błędu
    */
    public int SetWeldMachineCtrlMode(int mode, int ioType)

Rozpoczęcie spawania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Rozpoczęcie spawania
    * @param [in] ioType Typ IO 0-IO kontrolera; 1-rozszerzone IO
    * @param [in] arcNum Numer pliku konfiguracyjnego spawarki
    * @param [in] timeout Czas timeout zapłonu łuku
    * @return Kod błędu
    */
    int ARCStart(int ioType, int arcNum, int timeout);

Zakończenie spawania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Zakończenie spawania
    * @param [in] ioType Typ IO 0-IO kontrolera; 1-rozszerzone IO
    * @param [in] arcNum Numer pliku konfiguracyjnego spawarki
    * @param [in] timeout Czas timeout wygaszenia łuku
    * @return Kod błędu
    */
    int ARCEnd(int ioType, int arcNum, int timeout);

Rozpoczęcie ruchu wahadłowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Rozpoczęcie ruchu wahadłowego
    * @param [in] weaveNum Numer konfiguracji parametrów spawania wahadłowego
    * @return Kod błędu
    */
    int WeaveStart(int weaveNum);

Zakończenie ruchu wahadłowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Zakończenie ruchu wahadłowego
    * @param [in] weaveNum Numer konfiguracji parametrów spawania wahadłowego
    * @return Kod błędu
    */
    int WeaveEnd(int weaveNum);

Podawanie drutu do przodu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Podawanie drutu do przodu
    * @param [in] ioType Typ IO 0-IO kontrolera; 1-rozszerzone IO
    * @param [in] wireFeed Sterowanie podawaniem drutu 0-zatrzymaj podawanie; 1-podawaj
    * @return Kod błędu
    */
    int SetForwardWireFeed(int ioType, int wireFeed); 	

Podawanie drutu do tyłu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Podawanie drutu do tyłu
    * @param [in] ioType Typ IO 0-IO kontrolera; 1-rozszerzone IO
    * @param [in] wireFeed Sterowanie podawaniem drutu 0-zatrzymaj podawanie; 1-podawaj
    * @return Kod błędu
    */
    int SetReverseWireFeed(int ioType, int wireFeed);

Podawanie gazu osłonowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Podawanie gazu osłonowego
    * @param [in] ioType Typ IO 0-IO kontrolera; 1-rozszerzone IO
    * @param [in] airControl Sterowanie podawaniem gazu 0-zatrzymaj podawanie; 1-podawaj
    * @return Kod błędu
    */
    int SetAspirated(int ioType, int airControl);

Ustawianie wznowienia spawania po przerwaniu robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Ustawianie wznowienia spawania po przerwaniu robota
    * @return Kod błędu 
    */
    int WeldingStartReWeldAfterBreakOff();

Ustawianie wyjścia ze spawania po przerwaniu robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Ustawianie wyjścia ze spawania po przerwaniu robota
    * @return Kod błędu 
    */
    int WeldingAbortWeldAfterBreakOff();

Przykład kodu sterowania spawaniem robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestWelding(Robot robot)
    {
        robot.WeldingSetCurrent(0, 230, 0, 0);
        robot.WeldingSetVoltage(0, 24, 0, 1);

        DescPose p1Desc=new DescPose(228.879, -503.594, 453.984, -175.580, 8.293, 171.267);
        JointPos p1Joint=new JointPos(102.700, -85.333, 90.518, -102.365, -83.932, 22.134);

        DescPose p2Desc=new DescPose(-333.302, -435.580, 449.866, -174.997, 2.017, 109.815);
        JointPos p2Joint=new JointPos(41.862, -85.333, 90.526, -100.587, -90.014, 22.135);

        ExaxisPos exaxisPos=new ExaxisPos(0, 0, 0, 0);
        DescPose offdese=new DescPose(0, 0, 0, 0, 0, 0);

        robot.MoveJ(p1Joint, p1Desc, 13, 0, 20, 100, 100, exaxisPos, -1, 0, offdese);
        robot.ARCStart(1, 0, 10000);
        robot.WeaveStart(0);
        robot.MoveL(p2Joint, p2Desc, 13, 0, 20, 100, 100, -1, 0, exaxisPos, 0, 0, offdese,0,10);
        robot.ARCEnd(1, 0, 10000);
        robot.WeaveEnd(0);
        return 0;
    }

Rozpoczęcie spawania segmentowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Rozpoczęcie spawania segmentowego
    * @param [in] startDesePos Pozycja kartezjańska punktu początkowego
    * @param [in] endDesePos Pozycja kartezjańska punktu końcowego
    * @param [in] startJPos Pozycja przegubów punktu początkowego
    * @param [in] endJPos Pozycja przegubów punktu końcowego
    * @param [in] weldLength Długość segmentu spawanego (mm)
    * @param [in] noWeldLength Długość segmentu niespawanego (mm)
    * @param [in] weldIOType Typ IO spawania (0-IO skrzynki kontrolnej; 1-rozszerzone IO)
    * @param [in] arcNum Numer pliku konfiguracyjnego spawarki
    * @param [in] weldTimeout Czas timeout zapłonu/wygaszenia łuku
    * @param [in] isWeave Czy ruch wahadłowy
    * @param [in] weaveNum Numer konfiguracji parametrów spawania wahadłowego
    * @param [in] tool Numer narzędzia
    * @param [in] user Numer przedmiotu
    * @param [in] vel  Procent prędkości, zakres [0~100]
    * @param [in] acc  Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]
    * @param [in] blendR [-1.0]-ruch do pozycji (blokujący), [0~1000.0]-promień wygładzania (nieblokujący), jednostka mm
    * @param [in] epos  Pozycja osi rozszerzenia, jednostka mm
    * @param [in] search  0-brak poszukiwania pozycji drutu, 1-poszukiwanie pozycji drutu
    * @param [in] offset_flag  0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie przedmiotu, 2-przesunięcie w układzie narzędzia
    * @param [in] offset_pos  Wartość przesunięcia pozy
    * @return Kod błędu 
    */
    int SegmentWeldStart(DescPose startDesePos, DescPose endDesePos, JointPos startJPos, JointPos endJPos, double weldLength, double noWeldLength, int weldIOType,int arcNum, int weldTimeout, boolean isWeave, int weaveNum, int tool, int user, double vel, double acc, double ovl, double blendR, ExaxisPos epos, int search, int offset_flag, DescPose offset_pos);

Przykład kodu spawania segmentowego robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestSegWeld(Robot robot)
    {
        robot.WeldingSetCurrent(0, 230, 0, 0);
        robot.WeldingSetVoltage(0, 24, 0, 1);

        DescPose p1Desc=new DescPose(228.879, -503.594, 453.984, -175.580, 8.293, 171.267);
        JointPos p1Joint=new JointPos(102.700, -85.333, 90.518, -102.365, -83.932, 22.134);

        DescPose p2Desc=new DescPose(-333.302, -435.580, 449.866, -174.997, 2.017, 109.815);
        JointPos p2Joint=new JointPos(41.862, -85.333, 90.526, -100.587, -90.014, 22.135);

        ExaxisPos exaxisPos=new ExaxisPos(0, 0, 0, 0);
        DescPose offdese=new DescPose(0, 0, 0, 0, 0, 0);

        robot.GetForwardKin(p1Joint,p1Desc);
        robot.GetForwardKin(p2Joint,p2Desc);

        int rtn = robot.SegmentWeldStart(p1Desc, p2Desc, p1Joint, p2Joint, 20, 20, 0, 0, 5000, true,0, 1, 0, 30, 100, 100, -1, exaxisPos, 0, 0, offdese);
        return 0;
    }

Rozpoczęcie symulacji ruchu wahadłowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Rozpoczęcie symulacji ruchu wahadłowego
    * @param [in] weaveNum  Numer parametrów wahadła
    * @return Kod błędu 
    */
    int WeaveStartSim(int weaveNum);

Zakończenie symulacji ruchu wahadłowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Zakończenie symulacji ruchu wahadłowego
    * @param [in] weaveNum  Numer parametrów wahadła
    * @return Kod błędu 
    */
    int WeaveEndSim(int weaveNum);

Rozpoczęcie ostrzegania o wykrywaniu trajektorii (bez ruchu)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Rozpoczęcie ostrzegania o wykrywaniu trajektorii (bez ruchu)
    * @param [in] weaveNum   Numer parametrów wahadła
    * @return Kod błędu 
    */
    int WeaveInspectStart(int weaveNum);

Zakończenie ostrzegania o wykrywaniu trajektorii (bez ruchu)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Zakończenie ostrzegania o wykrywaniu trajektorii (bez ruchu)
    * @param [in] weaveNum   Numer parametrów wahadła
    * @return Kod błędu 
    */
    int WeaveInspectEnd(int weaveNum);

Rozpoczęcie zmiany parametrów wahadła
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionchanged:: Java SDK-v1.0.5-3.8.2

.. code-block:: Java
    :linenos:

    /**
    * @brief  Rozpoczęcie zmiany parametrów wahadła
    * @param  [in] weaveChangeFlag 1-zmiana parametrów wahadła; 2-zmiana parametrów wahadła + prędkości spawania
    * @param  [in] weaveNum Numer wahadła
    * @param  [in] velStart Prędkość początkowa spawania, (cm/min)
    * @param  [in] velEnd Prędkość końcowa spawania, (cm/min)
    * @return Kod błędu
    */
    int WeaveChangeStart(int weaveChangeFlag, int weaveNum, double velStart, double velEnd)

Przykład kodu spawania ze zmianą parametrów wahadła robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestWeave(Robot robot)
    {
        DescPose p1Desc=new DescPose(228.879, -503.594, 453.984, -175.580, 8.293, 171.267);
        JointPos p1Joint=new JointPos(102.700, -85.333, 90.518, -102.365, -83.932, 22.134);

        DescPose p2Desc=new DescPose(-333.302, -435.580, 449.866, -174.997, 2.017, 109.815);
        JointPos p2Joint=new JointPos(41.862, -85.333, 90.526, -100.587, -90.014, 22.135);

        ExaxisPos exaxisPos=new ExaxisPos(0, 0, 0, 0);
        DescPose offdese=new DescPose(0, 0, 0, 0, 0, 0);

        robot.MoveJ(p1Joint, p1Desc, 13, 0, 20, 100, 100, exaxisPos, -1, 0, offdese);
        robot.WeaveStartSim(0);
        robot.MoveL(p2Joint, p2Desc, 13, 0, 20, 100, 100, -1, 0, exaxisPos, 0, 0, offdese,0,10);
        robot.WeaveEndSim(0);
        robot.MoveJ(p1Joint, p1Desc, 13, 0, 20, 100, 100, exaxisPos, -1, 0, offdese);
        robot.WeaveInspectStart(0);
        robot.MoveL(p2Joint, p2Desc, 13, 0, 20, 100, 100, -1, 0, exaxisPos, 0, 0, offdese,0,10);
        robot.WeaveInspectEnd(0);

        robot.WeldingSetVoltage(1, 19, 0, 0);
        robot.WeldingSetCurrent(1, 190, 0, 0);
        robot.MoveL(p1Joint, p1Desc, 1, 1, 100, 100, 50, -1,0, exaxisPos, 0, 0, offdese,0,10);
        robot.ARCStart(1, 0, 10000);
        robot.ArcWeldTraceControl(1, 0, 1, 0.06, 5, 5, 60, 1, 0.06, 5, 5, 80, 0, 0, 4, 1, 10, 0, 0);
        robot.WeaveStart(0);
        robot.WeaveChangeStart(1, 0, 50, 30);
        robot.MoveL(p2Joint, p2Desc, 1, 1, 100, 100, 1, -1, 0,exaxisPos, 0, 0, offdese,0,10);
        robot.WeaveChangeEnd();
        robot.WeaveEnd(0);
        robot.ArcWeldTraceControl(0, 0, 1, 0.06, 5, 5, 60, 1, 0.06, 5, 5, 80, 0, 0, 4, 1, 10, 0, 0);
        robot.ARCEnd(1, 0, 10000);
        return 0;
    }

Zakończenie zmiany parametrów wahadła
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.2-3.7.9

.. code-block:: Java
    :linenos:

    /**
    * @brief Zakończenie zmiany parametrów wahadła
    * @return Kod błędu
    */
    int WeaveChangeEnd(); 

Rozszerzone IO - konfiguracja sygnału detekcji gazu spawarki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Rozszerzone IO - konfiguracja sygnału detekcji gazu spawarki
    * @param [in] DONum  Rozszerzony numer DO sygnału detekcji gazu
    * @return Kod błędu 
    */
    int SetAirControlExtDoNum(int DONum);

Rozszerzone IO - konfiguracja sygnału zapłonu łuku spawarki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Rozszerzone IO - konfiguracja sygnału zapłonu łuku spawarki
    * @param [in] DONum  Rozszerzony numer DO sygnału zapłonu łuku spawarki
    * @return Kod błędu 
    */
    int SetArcStartExtDoNum(int DONum);

Rozszerzone IO - konfiguracja sygnału podawania drutu do tyłu spawarki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Rozszerzone IO - konfiguracja sygnału podawania drutu do tyłu spawarki
    * @param [in] DONum  Rozszerzony numer DO sygnału podawania drutu do tyłu
    * @return Kod błędu 
    */
    int SetWireReverseFeedExtDoNum(int DONum);

Rozszerzone IO - konfiguracja sygnału podawania drutu do przodu spawarki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Rozszerzone IO - konfiguracja sygnału podawania drutu do przodu spawarki
    * @param [in] DONum  Rozszerzony numer DO sygnału podawania drutu do przodu
    * @return Kod błędu 
    */
    int SetWireForwardFeedExtDoNum(int DONum);

Rozszerzone IO - konfiguracja sygnału pomyślnego zapłonu łuku spawarki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Rozszerzone IO - konfiguracja sygnału pomyślnego zapłonu łuku spawarki
    * @param [in] DINum  Rozszerzony numer DI sygnału pomyślnego zapłonu łuku
    * @return Kod błędu 
    */
    int SetArcDoneExtDiNum(int DINum);

Rozszerzone IO - konfiguracja sygnału gotowości spawarki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Rozszerzone IO - konfiguracja sygnału gotowości spawarki
    * @param [in] DINum  Rozszerzony numer DI sygnału gotowości spawarki
    * @return Kod błędu 
    */
    int SetWeldReadyExtDiNum(int DINum);

Rozszerzone IO - konfiguracja sygnału wznowienia po przerwaniu spawania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Rozszerzone IO - konfiguracja sygnału wznowienia po przerwaniu spawania
    * @param [in] reWeldDINum  Rozszerzony numer DI sygnału wznowienia spawania po przerwaniu
    * @param [in] abortWeldDINum  Rozszerzony numer DI sygnału wyjścia ze spawania po przerwaniu
    * @return Kod błędu 
    */
    int SetExtDIWeldBreakOffRecover(int reWeldDINum, int abortWeldDINum);

Przykład kodu konfiguracji rozszerzonych sygnałów IO spawania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestExtDIConfig(Robot robot)
    {
        robot.SetArcStartExtDoNum(10);
        robot.SetAirControlExtDoNum(20);
        robot.SetWireForwardFeedExtDoNum(30);
        robot.SetWireReverseFeedExtDoNum(40);

        robot.SetWeldReadyExtDiNum(50);
        robot.SetArcDoneExtDiNum(60);
        robot.SetExtDIWeldBreakOffRecover(70, 80);
        robot.SetWireSearchExtDIONum(0, 1);

        return 0;
    }

Sterowanie śledzeniem łuku
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionchanged:: Java SDK-v1.0.2-3.7.9

.. code-block:: Java
    :linenos:

    /** 
    * @brief Sterowanie śledzeniem łuku
    * @param [in] flag Przełącznik, 0-wył.; 1-wł.
    * @param [in] delaytime Czas opóźnienia, jednostka ms
    * @param [in] isLeftRight Kompensacja odchylenia lewo-prawo
    * @param [in] klr Współczynnik regulacji lewo-prawo (czułość)
    * @param [in] tStartLr Czas rozpoczęcia kompensacji lewo-prawo cyc
    * @param [in] stepMaxLr Maksymalna wielkość kompensacji na raz lewo-prawo mm
    * @param [in] sumMaxLr Maksymalna całkowita wielkość kompensacji lewo-prawo mm
    * @param [in] isUpLow Kompensacja odchylenia góra-dół
    * @param [in] kud Współczynnik regulacji góra-dół (czułość)
    * @param [in] tStartUd Czas rozpoczęcia kompensacji góra-dół cyc
    * @param [in] stepMaxUd Maksymalna wielkość kompensacji na raz góra-dół mm
    * @param [in] sumMaxUd Maksymalna całkowita wielkość kompensacji góra-dół
    * @param [in] axisSelect Wybór układu współrzędnych góra-dół, 0-wahadłowy; 1-narzędzia; 2-podstawy
    * @param [in] referenceType Sposób ustawienia prądu odniesienia góra-dół, 0-sprzężenie zwrotne; 1-stała
    * @param [in] referSampleStartUd Początek próbkowania prądu odniesienia góra-dół (sprzężenie zwrotne), cyc
    * @param [in] referSampleCountUd Liczba cykli próbkowania prądu odniesienia góra-dół (sprzężenie zwrotne), cyc
    * @param [in] referenceCurrent Prąd odniesienia góra-dół mA
    * @param [in] offsetType Typ śledzenia z przesunięciem, 0-bez przesunięcia; 1-próbkowanie; 2-procent
    * @param [in] offsetParameter Parametr przesunięcia; próbkowanie (czas rozpoczęcia próbkowania przesunięcia, domyślnie jeden cykl); procent (procent przesunięcia (-100 ~ 100))
    * @return Kod błędu 
    */
    int ArcWeldTraceControl(int flag, double delaytime, int isLeftRight, double klr, double tStartLr, double stepMaxLr, double sumMaxLr, int isUpLow, double kud, double tStartUd, double stepMaxUd, double sumMaxUd, int axisSelect, int referenceType, double referSampleStartUd, double referSampleCountUd, double referenceCurrent,int offsetType, int offsetParameter);

Wybór pasma przenoszenia AI śledzenia łuku
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Wybór pasma przenoszenia AI śledzenia łuku
    * @param  channel Wybór pasma przenoszenia AI śledzenia łuku, [0-3]
    * @return  Kod błędu
    */
    public int ArcWeldTraceExtAIChannelConfig(int channel)

Włączenie kompensacji śledzenia łuku + wielowarstwowej, wielościeżkowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Włączenie kompensacji śledzenia łuku + wielowarstwowej, wielościeżkowej
    * @return Kod błędu
    */
    public int ArcWeldTraceReplayStart()

Wyłączenie kompensacji śledzenia łuku + wielowarstwowej, wielościeżkowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Wyłączenie kompensacji śledzenia łuku + wielowarstwowej, wielościeżkowej
    * @return Kod błędu
    */
    public int ArcWeldTraceReplayEnd()

Zmiana współrzędnych przesunięcia - spawanie wielowarstwowe, wielościeżkowe
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Zmiana współrzędnych przesunięcia - spawanie wielowarstwowe, wielościeżkowe
    * @param pointO Pozycja kartezjańska punktu odniesienia
    * @param pointX Pozycja kartezjańska punktu wskazującego kierunek przesunięcia X punktu odniesienia
    * @param pointZ Pozycja kartezjańska punktu wskazującego kierunek przesunięcia Z punktu odniesienia
    * @param dx Wielkość przesunięcia w kierunku X (mm)
    * @param dz Wielkość przesunięcia w kierunku Z (mm)
    * @param dry Wielkość przesunięcia wokół osi Y (°)
    * @param offset Wynikowe przesunięcie
    * @return Kod błędu
    */
    public int MultilayerOffsetTrsfToBase(DescTran pointO, DescTran pointX, DescTran pointZ, double dx, double dz, double dry, DescPose offset)

Przykład kodu śledzenia łuku dla spawania wielowarstwowego, wielościeżkowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestArcWeldTrace(Robot robot)
    {
        JointPos mulitilineorigin1_joint=new JointPos(-24.090, -63.501, 84.288, -111.940, -93.426, 57.669);
        DescPose mulitilineorigin1_desc=new DescPose(-677.559, 190.951, -1.205, 1.144, -41.482, -82.577);

        DescTran mulitilineX1_desc=new DescTran(0,0,0);
        mulitilineX1_desc.x = -677.556;
        mulitilineX1_desc.y = 211.949;
        mulitilineX1_desc.z = -1.206;

        DescTran mulitilineZ1_desc=new DescTran(0,0,0);
        mulitilineZ1_desc.x = -677.564;
        mulitilineZ1_desc.y = 190.956;
        mulitilineZ1_desc.z = 19.817;

        JointPos mulitilinesafe_joint=new JointPos(-25.734, -63.778, 81.502, -108.975, -93.392, 56.021);
        DescPose mulitilinesafe_desc=new DescPose(-677.561, 211.950, 19.812, 1.144, -41.482, -82.577);
        JointPos mulitilineorigin2_joint=new JointPos(-29.743, -75.623, 101.241, -116.354, -94.928, 55.735);
        DescPose mulitilineorigin2_desc=new DescPose(-563.961, 215.359, -0.681, 2.845, -40.476, -87.443);

        DescTran mulitilineX2_desc=new DescTran(0,0,0);
        mulitilineX2_desc.x = -563.965;
        mulitilineX2_desc.y = 220.355;
        mulitilineX2_desc.z = -0.680;

        DescTran mulitilineZ2_desc=new DescTran(0,0,0);
        mulitilineZ2_desc.x = -563.968;
        mulitilineZ2_desc.y = 215.362;
        mulitilineZ2_desc.z = 4.331;

        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);
        DescPose offset=new DescPose(0, 0, 0, 0, 0, 0);

        robot.Sleep(10);
        int error = robot.MoveJ(mulitilinesafe_joint, mulitilinesafe_desc, 13, 0, 10, 100, 100, epos, -1, 0, offset);

        error = robot.MoveL(mulitilineorigin1_joint, mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1, 0,epos, 0, 0, offset, 0, 100);

        error = robot.MoveJ(mulitilinesafe_joint, mulitilinesafe_desc, 13, 0, 10, 100, 100, epos, -1, 0, offset);

        error = robot.MoveL(mulitilineorigin2_joint, mulitilineorigin2_desc, 13, 0, 10, 100, 100, -1, 0,epos, 0, 0, offset, 0, 100);

        error = robot.MoveJ(mulitilinesafe_joint, mulitilinesafe_desc, 13, 0, 10, 100, 100, epos, -1, 0, offset);

        error = robot.MoveL(mulitilineorigin1_joint, mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1,0, epos, 0, 0, offset, 0, 100);

        error = robot.ARCStart(1, 0, 3000);

        error = robot.WeaveStart(0);

        error = robot.ArcWeldTraceControl(1, 0, 1, 0.06, 5, 5, 50, 1, 0.06, 5, 5, 55, 0, 0, 4, 1, 10,0,0);

        error = robot.MoveL(mulitilineorigin2_joint, mulitilineorigin2_desc, 13, 0, 1, 100, 100, -1, 0,epos, 0, 0,offset, 0, 100);

        error = robot.ArcWeldTraceControl(0, 0, 1, 0.06, 5, 5, 50, 1, 0.06, 5, 5, 55, 0, 0, 4, 1, 10,0,0);

        error = robot.WeaveEnd(0);

        error = robot.ARCEnd(1, 0, 10000);

        error = robot.MoveJ(mulitilinesafe_joint, mulitilinesafe_desc, 13, 0, 10, 100, 100, epos, -1, 0, offset);

        error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin1_desc.tran, mulitilineX1_desc, mulitilineZ1_desc, 10.0, 0.0, 0.0, offset);

        error = robot.MoveL(mulitilineorigin1_joint, mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1, 0,epos, 0, 1, offset, 0, 100);

        error = robot.ARCStart(1, 0, 3000);

        error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin2_desc.tran, mulitilineX2_desc, mulitilineZ2_desc, 10, 0, 0, offset);

        error = robot.ArcWeldTraceReplayStart();

        error = robot.MoveL(mulitilineorigin2_joint, mulitilineorigin2_desc, 13, 0, 2, 100, 100, -1, 0,epos, 0, 1, offset, 0, 100);

        error = robot.ArcWeldTraceReplayEnd();

        error = robot.ARCEnd(1, 0, 10000);

        error = robot.MoveJ(mulitilinesafe_joint, mulitilinesafe_desc, 13, 0, 10, 100, 100, epos, -1, 0, offset);

        error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin1_desc.tran, mulitilineX1_desc, mulitilineZ1_desc, 0, 10, 0, offset);

        error = robot.MoveL(mulitilineorigin1_joint, mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1,0, epos, 0, 1, offset, 0, 100);

        error = robot.ARCStart(1, 0, 3000);

        error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin2_desc.tran, mulitilineX2_desc, mulitilineZ2_desc, 0, 10, 0, offset);

        error = robot.ArcWeldTraceReplayStart();

        error = robot.MoveL(mulitilineorigin2_joint, mulitilineorigin2_desc, 13, 0, 2, 100, 100, -1,0, epos, 0, 1, offset, 0, 100);

        error = robot.ArcWeldTraceReplayEnd();

        error = robot.ARCEnd(1, 0, 3000);

        error = robot.MoveJ(mulitilinesafe_joint, mulitilinesafe_desc, 13, 0, 10, 100, 100, epos, -1, 0, offset);

        robot.CloseRPC();
        return 0;
    }

Wybór kanału AI sprzężenia zwrotnego prądu spawarki dla śledzenia łuku
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.5-3.8.2

.. code-block:: Java
    :linenos:

    /**
    * @brief Wybór kanału AI sprzężenia zwrotnego prądu spawarki dla śledzenia łuku
    * @param  [in] channel Kanał; 0-rozszerzony AI0; 1-rozszerzony AI1; 2-rozszerzony AI2; 3-rozszerzony AI3; 4-AI0 skrzynki kontrolnej; 5-AI1 skrzynki kontrolnej
    * @return Kod błędu
    */
    int ArcWeldTraceAIChannelCurrent(int channel)

Wybór kanału AI sprzężenia zwrotnego napięcia spawarki dla śledzenia łuku
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.5-3.8.2

.. code-block:: Java
    :linenos:

    /**
    * @brief Wybór kanału AI sprzężenia zwrotnego napięcia spawarki dla śledzenia łuku
    * @param  [in] channel Kanał; 0-rozszerzony AI0; 1-rozszerzony AI1; 2-rozszerzony AI2; 3-rozszerzony AI3; 4-AI0 skrzynki kontrolnej; 5-AI1 skrzynki kontrolnej
    * @return Kod błędu
    */
    int ArcWeldTraceAIChannelVoltage(int channel)

Parametry konwersji sprzężenia zwrotnego prądu spawarki dla śledzenia łuku
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.5-3.8.2

.. code-block:: Java
    :linenos:

    /**
    * @brief Parametry konwersji sprzężenia zwrotnego prądu spawarki dla śledzenia łuku
    * @param [in] AILow Dolna granica kanału AI, domyślnie 0V, zakres [0-10V]
    * @param [in] AIHigh Górna granica kanału AI, domyślnie 10V, zakres [0-10V]
    * @param [in] currentLow Wartość prądu spawarki odpowiadająca dolnej granicy kanału AI, domyślnie 0V, zakres [0-200V]
    * @param [in] currentHigh Wartość prądu spawarki odpowiadająca górnej granicy kanału AI, domyślnie 100V, zakres [0-200V]
    * @return Kod błędu
    */
    int ArcWeldTraceCurrentPara(double AILow, double AIHigh, double currentLow, double currentHigh)

Parametry konwersji sprzężenia zwrotnego napięcia spawarki dla śledzenia łuku
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.5-3.8.2

.. code-block:: Java
    :linenos:

    /**
    * @brief Parametry konwersji sprzężenia zwrotnego napięcia spawarki dla śledzenia łuku
    * @param [in] AILow Dolna granica kanału AI, domyślnie 0V, zakres [0-10V]
    * @param [in] AIHigh Górna granica kanału AI, domyślnie 10V, zakres [0-10V]
    * @param [in] voltageLow Wartość napięcia spawarki odpowiadająca dolnej granicy kanału AI, domyślnie 0V, zakres [0-200V]
    * @param [in] voltageHigh Wartość napięcia spawarki odpowiadająca górnej granicy kanału AI, domyślnie 100V, zakres [0-200V]
    * @return Kod błędu
    */
    int ArcWeldTraceVoltagePara(double AILow, double AIHigh, double voltageLow, double voltageHigh)

Przykład kodu śledzenia łuku
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static void WeldTraceControlWithCtrlBoxAI(Robot robot)
    {
        DescPose startdescPose = new DescPose(-473.86, 257.879, -20.849, -37.317, -42.021, 2.543);
        JointPos startjointPos = new JointPos(-43.487, -76.526, 95.568, -104.445, -89.356, 3.72);

        DescPose safedescPose = new DescPose(-504.043, 275.181, 40.908, -28.002, -42.025, -14.044);
        JointPos safejointPos = new JointPos(-39.078, -76.732, 87.227, -99.47, -94.301, 18.714);

        DescPose enddescPose = new DescPose(-499.844, 141.225, 7.72, -34.856, -40.17, 13.13);
        JointPos endjointPos = new JointPos(-31.305, -82.998, 99.401, -104.426, -89.35, 3.696);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);
        //起始运动到安全点
        robot.MoveJ(safejointPos, safedescPose, 1, 0, 5, 20, 100, exaxisPos, -1, 0, offdese);

        WeldCurrentAORelation current = new WeldCurrentAORelation(0, 495, 1, 10, 0);
        WeldVoltageAORelation voltage = new WeldVoltageAORelation(10, 45, 1, 10, 1);
        robot.WeldingSetCurrentRelation(current);//电流与输出模拟量的关系
        robot.WeldingSetVoltageRelation(voltage);//电压与输出模拟量的关系
        robot.WeldingSetVoltage(0, 25, 1, 0);//设置电压
        robot.WeldingSetCurrent(0, 260, 0, 0);//设置电流

        int rtn = robot.ArcWeldTraceAIChannelCurrent(4);
        System.out.println("ArcWeldTraceAIChannelCurrent rtn is " + rtn);

        rtn = robot.ArcWeldTraceAIChannelVoltage(5);
        System.out.println("ArcWeldTraceAIChannelVoltage rtn is " + rtn);

        rtn = robot.ArcWeldTraceCurrentPara(0.0, 5, 0, 500);
        System.out.println("ArcWeldTraceCurrentPara rtn is " + rtn);

        rtn = robot.ArcWeldTraceVoltagePara(1.018, 10, 0, 50);
        System.out.println("ArcWeldTraceVoltagePara rtn is " + rtn);

        robot.MoveJ(startjointPos, startdescPose, 1, 0, 20, 20, 100, exaxisPos, -1, 0, offdese);
        robot.ArcWeldTraceControl(1, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);
        robot.ARCStart(0, 0, 10000);
        robot.WeaveStart(0);
        robot.MoveL(endjointPos, enddescPose, 1, 0, 100, 100, 2, -1, 0, exaxisPos, 0, 0, offdese, 0, 10);
        robot.ARCEnd(0, 0, 10000);
        robot.WeaveEnd(0);
        robot.ArcWeldTraceControl(0, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);

        robot.MoveJ(safejointPos, safedescPose, 1, 0, 20, 20, 100, exaxisPos, -1, 0, offdese);
    }

Ustawianie rozszerzonego portu IO dla poszukiwania pozycji drutu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Ustawianie rozszerzonego portu IO dla poszukiwania pozycji drutu
    * @param [in] searchDoneDINum Port DO pomyślnego poszukiwania pozycji drutu (0-127)
    * @param [in] searchStartDONum Port DO sterowania uruchamianiem/zatrzymywaniem poszukiwania pozycji drutu (0-127)
    * @return Kod błędu
    */
    int SetWireSearchExtDIONum(int searchDoneDINum, int searchStartDONum);

Przykładowy program
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    private static void TestUDPWireSearch(Robot robot)
    {
        UDPComParam param = new UDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10,0);
        robot.ExtDevSetUDPComParam(param);//udp扩展轴通讯

        robot.SetWireSearchExtDIONum(0, 0);

        int rtn0, rtn1, rtn2 = 0;
        ExaxisPos exaxisPos = new ExaxisPos(0.0, 0.0, 0.0, 0.0);
        DescPose offdese = new DescPose(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);

        DescPose descStart = new DescPose(-158.767, -510.596, 271.709, -179.427, -0.745, -137.349);
        JointPos jointStart = new JointPos(61.667, -79.848, 108.639, -119.682, -89.700, -70.985);

        DescPose descEnd = new DescPose(0.332, -516.427, 270.688, 178.165, 0.017, -119.989);
        JointPos jointEnd = new JointPos(79.021, -81.839, 110.752, -118.298, -91.729, -70.981);

        robot.MoveL(jointStart, descStart, 1, 0, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 0, 100);
        robot.MoveL(jointEnd, descEnd, 1, 0, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 0, 100);

        DescPose descREF0A = new DescPose(-66.106, -560.746, 270.381, 176.479, -0.126, -126.745);
        JointPos jointREF0A = new JointPos(73.531, -75.588, 102.941, -116.250, -93.347, -69.689);

        DescPose descREF0B = new DescPose(-66.109, -528.440, 270.407, 176.479, -0.129, -126.744);
        JointPos jointREF0B = new JointPos(72.534, -79.625, 108.046, -117.379, -93.366, -70.687);

        DescPose descREF1A = new DescPose(72.975, -473.242, 270.399, 176.479, -0.129, -126.744);
        JointPos jointREF1A = new JointPos(87.169, -86.509, 115.710, -117.341, -92.993, -56.034);

        DescPose descREF1B = new DescPose(31.355, -473.238, 270.405, 176.480, -0.130, -126.745);
        JointPos jointREF1B = new JointPos(82.117, -87.146, 116.470, -117.737, -93.145, -61.090);

        rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
        robot.MoveL(jointREF0A, descREF0A, 1, 0, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 0, 100);  //起点
        robot.MoveL(jointREF0B, descREF0B, 1, 0, 10, 100, 100, -1, exaxisPos, 1, 0, offdese, 0, 100);  //方向点
        rtn1 = robot.WireSearchWait("REF0");
        rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

        rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
        robot.MoveL(jointREF1A, descREF1A, 1, 0, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 0, 100);  //起点
        robot.MoveL(jointREF1B, descREF1B, 1, 0, 10, 100, 100, -1, exaxisPos, 1, 0, offdese, 0, 100);  //方向点
        rtn1 = robot.WireSearchWait("REF1");
        rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

        rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
        robot.MoveL(jointREF0A, descREF0A, 1, 0, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 0, 100);  //起点
        robot.MoveL(jointREF0B, descREF0B, 1, 0, 10, 100, 100, -1, exaxisPos, 1, 0, offdese, 0, 100);  //方向点
        rtn1 = robot.WireSearchWait("RES0");
        rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

        rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
        robot.MoveL(jointREF1A, descREF1A, 1, 0, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 0, 100);  //起点
        robot.MoveL(jointREF1B, descREF1B, 1, 0, 10, 100, 100, -1, exaxisPos, 1, 0, offdese, 0, 100);  //方向点
        rtn1 = robot.WireSearchWait("RES1");
        rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

        String[] varNameRef = {"REF0", "REF1", "#", "#", "#", "#"};
        String[] varNameRes = {"RES0", "RES1", "#", "#", "#", "#"};
        int offectFlag = 0;
        //DescPose offectPos = new DescPose(0, 0, 0, 0, 0, 0);
        DescOffset offset = new DescOffset();
        rtn0 = robot.GetWireSearchOffset(0, 0, varNameRef, varNameRes, offset);
        robot.PointsOffsetEnable(0, offset.offset);
        robot.MoveL(jointStart, descStart, 1, 0, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 0, 100);
        robot.MoveL(jointEnd, descEnd, 1, 0, 100, 100, 100, -1, exaxisPos, 1, 0, offdese, 0, 100);
        robot.PointsOffsetDisable();
    }

Rozpoczęcie poszukiwania pozycji drutu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Rozpoczęcie poszukiwania pozycji drutu
    * @param [in] refPos  1-punkt odniesienia 0-punkt kontaktu
    * @param [in] searchVel   Prędkość poszukiwania %
    * @param [in] searchDis  Odległość poszukiwania mm
    * @param [in] autoBackFlag Flaga automatycznego powrotu, 0-nie automatyczny; 1-automatyczny
    * @param [in] autoBackVel  Prędkość automatycznego powrotu %
    * @param [in] autoBackDis  Odległość automatycznego powrotu mm
    * @param [in] offectFlag  1-poszukiwanie z przesunięciem; 0-poszukiwanie punktu nauczania
    * @return Kod błędu 
    */
    int WireSearchStart(int refPos, double searchVel, int searchDis, int autoBackFlag, double autoBackVel, int autoBackDis, int offectFlag);

Zakończenie poszukiwania pozycji drutu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Zakończenie poszukiwania pozycji drutu
    * @param [in] refPos  1-punkt odniesienia 2-punkt kontaktu
    * @param [in] searchVel   Prędkość poszukiwania %
    * @param [in] searchDis  Odległość poszukiwania mm
    * @param [in] autoBackFlag Flaga automatycznego powrotu, 0-nie automatyczny; 1-automatyczny
    * @param [in] autoBackVel  Prędkość automatycznego powrotu %
    * @param [in] autoBackDis  Odległość automatycznego powrotu mm
    * @param [in] offectFlag  1-poszukiwanie z przesunięciem; 2-poszukiwanie punktu nauczania
    * @return Kod błędu 
    */
    int WireSearchEnd(int refPos, double searchVel, int searchDis, int autoBackFlag, double autoBackVel, int autoBackDis, int offectFlag);

Obliczanie przesunięcia poszukiwania pozycji drutu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Obliczanie przesunięcia poszukiwania pozycji drutu
    * @param [in] seamType  Typ spoiny
    * @param [in] method   Metoda obliczeniowa
    * @param [in] varNameRef Punkty odniesienia 1-6, „#” oznacza brak zmiennej punktowej
    * @param [in] varNameRes Punkty kontaktu 1-6, „#” oznacza brak zmiennej punktowej
    * @param [out] offset Przesunięcie pozy [x, y, z, a, b, c] i sposób przesunięcia
    * @return Kod błędu 
    */
    int GetWireSearchOffset(int seamType, int method, String[] varNameRef, String[] varNameRes, DescOffset offset);

Oczekiwanie na zakończenie poszukiwania pozycji drutu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Oczekiwanie na zakończenie poszukiwania pozycji drutu
    * @return Kod błędu 
    */
    int WireSearchWait(String name);

Zapis punktu kontaktu poszukiwania pozycji drutu do bazy danych
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Zapis punktu kontaktu poszukiwania pozycji drutu do bazy danych
    * @param [in] varName  Nazwa punktu kontaktu „RES0” ~ „RES99”
    * @param [in] pos  Dane punktu kontaktu [x, y, x, a, b, c]
    * @return Kod błędu 
    */
    int SetPointToDatabase(String varName, DescPose pos);

Przykład kodu poszukiwania pozycji drutu robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestWireSearch(Robot robot)
    {
        DescPose toolCoord=new DescPose(0, 0, 200, 0, 0, 0);
        robot.SetToolCoord(1, toolCoord, 0, 0, 1, 0);
        DescPose wobjCoord=new DescPose(0, 0, 0, 0, 0, 0);
        robot.SetWObjCoord(1, wobjCoord, 0);

        int rtn0, rtn1, rtn2 = 0;
        ExaxisPos exaxisPos = new ExaxisPos( 0, 0, 0, 0 );
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);


        DescPose descStart = new DescPose(216.543, 445.175, 93.465, 179.683, 1.757, -112.641);
        JointPos jointStart = new JointPos(-128.345, -86.660, 114.679, -119.625, -89.219, 74.303);

        DescPose descEnd =new DescPose(111.143, 523.384, 87.659, 179.703, 1.835, -97.750);
        JointPos jointEnd =new JointPos(-113.454, -81.060, 109.328, -119.954, -89.218, 74.302 );

        robot.MoveL(jointStart, descStart, 1, 1, 100, 100, 100, -1,0, exaxisPos, 0, 0, offdese,0,100);
        robot.MoveL(jointEnd, descEnd, 1, 1, 100, 100, 100, -1, 0,exaxisPos, 0, 0, offdese,0,100);

        DescPose descREF0A = new DescPose(142.135, 367.604, 86.523, 179.728, 1.922, -111.089);
        JointPos jointREF0A =new JointPos(-126.794, -100.834, 128.922, -119.864, -89.218, 74.302);

        DescPose descREF0B = new DescPose(254.633, 463.125, 72.604, 179.845, 2.341, -114.704);
        JointPos jointREF0B = new JointPos(-130.413, -81.093, 112.044, -123.163, -89.217, 74.303);

        DescPose descREF1A =new DescPose(92.556, 485.259, 47.476, -179.932, 3.130, -97.512);
        JointPos jointREF1A =new JointPos(-113.231, -83.815, 119.877, -129.092, -89.217, 74.303);

        DescPose descREF1B =new DescPose(203.103, 583.836, 63.909, 179.991, 2.854, -103.372);
        JointPos jointREF1B = new JointPos(-119.088, -69.676, 98.692, -121.761, -89.219, 74.303);

        rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
        robot.MoveL(jointREF0A, descREF0A, 1, 1, 100, 100, 100, -1,0, exaxisPos, 0, 0, offdese,0,10);  //起点
        robot.MoveL(jointREF0B, descREF0B, 1, 1, 100, 100, 100, -1,0, exaxisPos, 1, 0, offdese,0,10);  //方向点
        rtn1 = robot.WireSearchWait("REF0");
        rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

        rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
        robot.MoveL(jointREF1A, descREF1A, 1, 1, 100, 100, 100, -1, 0,exaxisPos, 0, 0, offdese,0,10);  //起点
        robot.MoveL(jointREF1B, descREF1B, 1, 1, 100, 100, 100, -1,0, exaxisPos, 1, 0, offdese,0,10);  //方向点
        rtn1 = robot.WireSearchWait("REF1");
        rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

        rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
        robot.MoveL(jointREF0A, descREF0A, 1, 1, 100, 100, 100, -1,0, exaxisPos, 0, 0, offdese,0,10);  //起点
        robot.MoveL(jointREF0B, descREF0B, 1, 1, 100, 100, 100, -1,0, exaxisPos, 1, 0, offdese,0,10);  //方向点
        rtn1 = robot.WireSearchWait("RES0");
        rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

        rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
        robot.MoveL(jointREF1A, descREF1A, 1, 1, 100, 100, 100, -1, 0,exaxisPos, 0, 0, offdese,0,10);  //起点
        robot.MoveL(jointREF1B, descREF1B, 1, 1, 100, 100, 100, -1, 0,exaxisPos, 1, 0, offdese,0,10);  //方向点
        rtn1 = robot.WireSearchWait("RES1");
        rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

        String[] varNameRef =new String[]{"REF0", "REF1", "#", "#", "#", "#"};
        String[] varNameRes = new String[]{ "RES0", "RES1", "#", "#", "#", "#" };
        int offectFlag = 0;

        DescPose pos = new DescPose(0,0,0,0,0,0);
        DescOffset offectPos=new DescOffset();
        offectPos.offset=pos;
        offectPos.offsetFlag=0;

        rtn0 = robot.GetWireSearchOffset(0, 0, varNameRef, varNameRes, offectPos);
        robot.PointsOffsetEnable(0, pos);
        robot.MoveL(jointStart, descStart, 1, 1, 100, 100, 100, -1,0, exaxisPos, 0, 0, offdese,0,10);
        robot.MoveL(jointEnd, descEnd, 1, 1, 100, 100, 100, -1, 0,exaxisPos, 1, 0, offdese,0,10);
        robot.PointsOffsetDisable();

        robot.CloseRPC();
        return 0;
    }

Ustawianie rozpoczęcia zmiany napięcia spawania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.5-3.8.2

.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawianie rozpoczęcia zmiany napięcia spawania
    * @param [in] IOType Typ sterowania; 0-IO skrzynki kontrolnej; 1-protokół komunikacji cyfrowej (UDP); 2-protokół komunikacji cyfrowej (ModbusTCP)
    * @param [in] voltageStart Początkowe napięcie spawania (V)
    * @param [in] voltageEnd Końcowe napięcie spawania (V)
    * @param [in] AOIndex Numer portu AO skrzynki kontrolnej (0-1)
    * @param [in] blend Czy wygładzać 0-nie; 1-tak
    * @return Kod błędu
    */
    int WeldingSetVoltageGradualChangeStart(int IOType, double voltageStart, double voltageEnd, int AOIndex, int blend)

Ustawianie zakończenia zmiany napięcia spawania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.5-3.8.2

.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawianie zakończenia zmiany napięcia spawania
    * @return Kod błędu
    */
    int WeldingSetVoltageGradualChangeEnd()

Ustawianie rozpoczęcia zmiany prądu spawania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.5-3.8.2

.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawianie rozpoczęcia zmiany prądu spawania
    * @param [in] IOType Typ sterowania; 0-IO skrzynki kontrolnej; 1-protokół komunikacji cyfrowej (UDP); 2-protokół komunikacji cyfrowej (ModbusTCP)
    * @param [in] currentStart Początkowy prąd spawania (A)
    * @param [in] currentEnd Końcowy prąd spawania (A)
    * @param [in] AOIndex Numer portu AO skrzynki kontrolnej (0-1)
    * @param [in] blend Czy wygładzać 0-nie; 1-tak
    * @return Kod błędu
    */
    int WeldingSetCurrentGradualChangeStart(int IOType, double currentStart, double currentEnd, int AOIndex, int blend)

Ustawianie zakończenia zmiany prądu spawania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.5-3.8.2

.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawianie zakończenia zmiany prądu spawania
    * @return Kod błędu
    */
    int WeldingSetCurrentGradualChangeEnd()

Przykład kodu zmiany prądu i napięcia spawania robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static void WeldparamChange(Robot robot) 
    {
        DescPose startdescPose = new DescPose(-484.707, 276.996, -14.013, -37.657, -40.508, -1.548);
        JointPos startjointPos = new JointPos(-45.421, -75.673, 93.627, -104.302, -87.938, 6.005);

        DescPose enddescPose = new DescPose(-508.767, 137.109, -13.966, -37.639, -40.508, -1.559);
        JointPos endjointPos = new JointPos(-32.768, -80.947, 100.254, -106.201, -87.201, 18.648);

        DescPose safedescPose = new DescPose(-484.709, 294.436, 13.621, -37.660, -40.508, -1.545);
        JointPos safejointPos = new JointPos(-46.604, -75.410, 89.109, -100.003, -88.012, 4.823);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        WeldCurrentAORelation cur = new WeldCurrentAORelation(0, 495, 1, 10, 0);
        WeldVoltageAORelation vol = new WeldVoltageAORelation(10, 45, 1, 10, 1);
        robot.WeldingSetCurrentRelation(cur);
        robot.WeldingSetVoltageRelation(vol);

        robot.WeldingSetVoltage(0, 25, 1, 0);// ----设置电压
        robot.WeldingSetCurrent(0, 260, 0, 0);// ----设置电流

        robot.MoveJ(safejointPos, safedescPose, 1, 0, 5, 100, 100, exaxisPos, -1, 0, offdese);

        robot.WeldingSetCurrentGradualChangeStart(0, 260, 220, 0, 0);
        robot.WeldingSetVoltageGradualChangeStart(0, 25, 22, 1, 0);
        int rtn = robot.ArcWeldTraceControl(1, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);

        robot.MoveJ(startjointPos, startdescPose, 1, 0, 5, 100, 100, exaxisPos, -1, 0, offdese);
        System.out.println("ArcWeldTraceControl rtn is " + rtn);

        robot.ARCStart(0, 0, 10000);
        robot.WeaveStart(0);
        robot.WeaveChangeStart(2, 1, 24, 36);
        robot.MoveL(endjointPos, enddescPose, 1, 0, 100, 100, 2, -1, 0, exaxisPos, 0, 0, offdese, 0, 10);
        robot.ARCEnd(0, 0, 10000);
        robot.WeaveChangeEnd();
        robot.WeaveEnd(0);
        robot.ArcWeldTraceControl(0, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);
        robot.WeldingSetCurrentGradualChangeEnd();
        robot.WeldingSetVoltageGradualChangeEnd();
    }

Ustawianie niestandardowych parametrów ruchu wahadłowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Ustawianie niestandardowych parametrów ruchu wahadłowego
     * @param [in] id Niestandardowy numer wahadła: 0-2
     * @param [in] pointNum Liczba punktów wahadła 0-10
     * @param [in] point Dane punktów końcowych ruchu x,y,z
     * @param [in] stayTime Czas postoju wahadła ms
     * @param [in] frequency Częstotliwość wahadła Hz
     * @param [in] incStayType Tryb oczekiwania: 0-cykl nie zawiera czasu oczekiwania; 1-cykl zawiera czas oczekiwania
     * @param [in] stationary Oczekiwanie w pozycji wahadła: 0-kontynuacja ruchu w czasie oczekiwania; 1-pozycja nieruchoma w czasie oczekiwania
     * @return  Kod błędu
     */
    public int CustomWeaveSetPara(int id, int pointNum, DescTran[] point, double[] stayTime, double frequency, int incStayType, int stationary)

Pobieranie niestandardowych parametrów ruchu wahadłowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Pobieranie niestandardowych parametrów ruchu wahadłowego
     * @param [in] id Niestandardowy numer wahadła: 0-2
     * @param [out] pointNum Liczba punktów wahadła 0-10
     * @param [out] point Dane punktów końcowych ruchu x,y,z
     * @param [out] stayTime Czas postoju wahadła ms
     * @param [out] frequency Częstotliwość wahadła Hz
     * @param [out] incStayType Tryb oczekiwania: 0-cykl nie zawiera czasu oczekiwania; 1-cykl zawiera czas oczekiwania
     * @param [out] stationary Oczekiwanie w pozycji wahadła: 0-kontynuacja ruchu w czasie oczekiwania; 1-pozycja nieruchoma w czasie oczekiwania
     * @return  Kod błędu
     */
    public int CustomWeaveGetPara(int id, int[] pointNum, DescTran[] point, double[] stayTime, double[] frequency, int[] incStayType, int[] stationary)

Przykład kodu niestandardowych parametrów ruchu wahadłowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static void TestCustomWeaveSetPara(Robot robot)
    {
        DescTran[] point = new DescTran[10];
        point[0]=new DescTran();
        point[0].x = -3;
        point[0].y = -3;
        point[0].z = 0;

        point[1]=new DescTran();
        point[1].x = -6;
        point[1].y = 0;
        point[1].z = 0;

        point[2]=new DescTran();
        point[2].x = -3;
        point[2].y = 3;
        point[2].z = 0;

        point[3]=new DescTran();
        point[3].x = 0;
        point[3].y = 0;
        point[3].z = 0;
        point[4]=new DescTran(0,0,0);
        point[5]=new DescTran(0,0,0);
        point[6]=new DescTran(0,0,0);
        point[7]=new DescTran(0,0,0);
        point[8]=new DescTran(0,0,0);
        point[9]=new DescTran(0,0,0);

        double[] stayTime =new double[] { 0,0,0,0,0,0,0,0,0,0 };
        int rtn = robot.CustomWeaveSetPara(2, 4, point, stayTime, 1.000, 0, 0);
        System.out.println("CustomWeaveSetPara rtn is :"+ rtn);
        robot.Sleep(1000);

        int[] pointNum = new int[1];
        double[] frequency=new double[1];
        int[] incStayType=new int[1];
        int[] stationary=new int[1];
        robot.CustomWeaveGetPara(2, pointNum, point, stayTime, frequency, incStayType, stationary);
        System.out.println("pointNum is :"+ pointNum[0]);
        for (int i = 0; i < pointNum[0]; i++)
        {
            System.out.println("point:"+i+", "+ point[i].x+", "+ point[i].y+", "+ point[i].z);
        }
        System.out.println("fre is :"+ frequency[0]+", stay is:"+ incStayType[0]+", "+ stationary[0]);

        robot.WeaveSetPara(0, 9, 1.000000, 1, 5.000000,
                6.000000, 5.000000, 50, 100, 100,
                0, 1, 0.000000, 0.000000);

        DescPose desc_p1 =new DescPose(-288.650, 367.807, 288.404, 0.000, -0.001, 0.001 );
        DescPose desc_p2 = new DescPose( -431.714, 367.815, 288.415, 0.001, 0.001, 0.000 );
        DescPose desc_p3 = new DescPose( -348.666, 427.798, 288.404, -0.000, -0.000, 0.001 );
        JointPos j1 = new JointPos( 140.656, -84.560, -91.707, -93.734, 90.000, 50.655 );
        JointPos j2 = new JointPos( 149.873, -98.298, -77.599, -94.103, 90.000, 59.873 );
        JointPos j3 = new JointPos( 139.773, -96.173, -80.014, -93.814, 90.000, 49.772 );

        ExaxisPos epos = new ExaxisPos();
        DescPose offset_pos = new DescPose();

        robot.MoveJ(j1, desc_p1, 3, 0, 100, 100,100, epos, -1, 0, offset_pos);
        robot.WeaveStart(0);
        robot.Circle(j3, desc_p3, 3, 0, 100, 100, epos, j2, desc_p2, 3, 0, 100, 100, epos, 10, -1, offset_pos,0,-1,0);
        robot.WeaveEnd(0);
        robot.MoveJ(j1, desc_p1, 3, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.WeaveStart(0);
        robot.MoveC(j3, desc_p3, 3, 0, 100, 100, epos, 0, offset_pos, j2, desc_p2, 3, 0, 100, 100, epos, 0, offset_pos, 10, -1,0);
        robot.WeaveEnd(0);
        robot.MoveJ(j1, desc_p1, 3, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.WeaveStart(0);
        robot.MoveL(j2, desc_p2, 3, 0, 100, 100, 10, -1,epos, 0, 0, offset_pos, 0,0, 100);
        robot.WeaveEnd(0);

        robot.CloseRPC();
    }

Konfiguracja parametrów spawarki laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Konfiguracja parametrów spawarki laserowej
    * @param  io_type Typ komunikacji 0-IO 1-UDP
    * @param  num Numer grupy do ustawienia (1~10)
    * @param  scanSpeed Prędkość skanowania
    * @param  scanWidth Szerokość skanowania
    * @param  peakPower Moc szczytowa
    * @param  dutyCycle Współczynnik wypełnienia
    * @param  freq Częstotliwość
    * @return Kod błędu
    */
    public int SetLaserWeldingParam(int io_type, int num, int scanSpeed, int scanWidth, int peakPower, int dutyCycle, int freq);

Ustawianie rozpoczęcia/zatrzymania spawania laserowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawianie rozpoczęcia/zatrzymania spawania laserowego
    * @param io_type Typ komunikacji 0-IO 1-UDP
    * @param status Słowo sterujące 0-wyłącz wiązkę 1-włącz wiązkę
    * @param max_waittime Maksymalny czas oczekiwania, jednostka milisekundy, domyślnie 10000
    * @return Kod błędu
    */
    public int SetLaserWeldingStartEnd(int io_type, int status, int max_waittime)

Włączanie/wyłączanie spawarki laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Włączanie/wyłączanie spawarki laserowej
    * @param io_type Typ komunikacji 0-IO 1-UDP
    * @param status 0-wyłącz 1-włącz
    * @return Kod błędu
    */
    public int SetLaserWeldingEnable(int io_type, int status)

Resetowanie błędów spawarki laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Resetowanie błędów spawarki laserowej
    * @param io_type Typ komunikacji 0-IO 1-UDP
    * @param status Słowo sterujące 0-nieważne 1-resetowanie błędu
    * @return Kod błędu
    */
    public int ResetLaserWeldingErr(int io_type, int status)

Pobieranie stanu pracy spawarki laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Pobieranie stanu pracy spawarki laserowej
    * @param io_type Typ komunikacji 0-IO 1-UDP
    * @param  status Słowo sterujące 0-zatrzymana 1-pracuje
    * @return Kod błędu
    */
    public int GetLaserWeldingRunningState(int io_type, int[] status)

Pobieranie stanu awarii spawarki laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Pobieranie stanu awarii spawarki laserowej
    * @param io_type Typ komunikacji 0-IO 1-UDP
    * @param  status 0-brak awarii 1-występuje awaria
    * @return Kod błędu
    */
    public int GetLaserWeldingErrState(int io_type, int[] status)

Pobieranie parametrów konfiguracyjnych spawarki laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Pobieranie parametrów konfiguracyjnych jednej z 10 grup procesowych spawarki laserowej
    * @param num Numer grupy do ustawienia (1~10)
    * @param params Tablica parametrów wyjściowych: [scanSpeed, scanWidth, peakPower, dutyCycle, freq]
    * @return Kod błędu
    */
    public int GetLaserWeldingParamTarget(int num, int[] params)

Pobieranie aktualnie obowiązujących parametrów konfiguracyjnych spawarki laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Pobieranie aktualnie obowiązujących parametrów konfiguracyjnych spawarki laserowej
    * @param io_type Typ komunikacji 0-IO 1-UDP
    * @param params Tablica parametrów wyjściowych: [scanSpeed, scanWidth, peakPower, dutyCycle, freq]
    * @return Kod błędu
    */
    public int GetLaserWeldingParamActual(int io_type, int[] params)

Konfiguracja rozszerzonego portu DO włączania spawarki laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawianie rozszerzonego IO dla spawarki laserowej, portu DO włączania
    * @param ctrlModeDONum Rozszerzony numer portu DO włączania spawarki laserowej
    * @return Kod błędu
    */
    public int SetLaserWeldingEnableExtDoNum(int ctrlModeDONum)

Konfiguracja rozszerzonego portu DO uruchamiania spawarki laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawianie rozszerzonego IO dla spawarki laserowej, portu DO uruchamiania
    * @param ctrlModeDONum Rozszerzony numer portu DO uruchamiania (włączania/wyłączania wiązki) spawarki laserowej
    * @return Kod błędu
    */
    public int SetLaserWeldingStartExtDoNum(int ctrlModeDONum)

Konfiguracja rozszerzonego portu DO resetowania błędów spawarki laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawianie rozszerzonego IO dla spawarki laserowej, portu DO resetowania błędów
    * @param ctrlModeDONum Rozszerzony numer portu DO resetowania błędów spawarki laserowej
    * @return Kod błędu
    */
    public int SetLaserWeldingErrResetExtDoNum(int ctrlModeDONum)

Konfiguracja rozszerzonego portu DI stanu pracy (stanu wiązki) spawarki laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Konfiguracja rozszerzonego portu DI stanu pracy (stanu wiązki) spawarki laserowej
    * @param diNum Rozszerzony port DI stanu pracy (stanu wiązki) spawarki laserowej
    * @return Kod błędu, 0 oznacza sukces, wartość niezerowa oznacza błąd
    */
    public int SetLaserWeldingRunningStateExtDiNum(int diNum);

Konfiguracja rozszerzonego portu DI stanu awarii spawarki laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Konfiguracja rozszerzonego portu DI stanu awarii spawarki laserowej
    * @param diNum Rozszerzony port DI stanu awarii spawarki laserowej
    * @return Kod błędu, 0 oznacza sukces, wartość niezerowa oznacza błąd
    */
    public int SetLaserWeldingErrStateExtDiNum(int diNum);

Przykład kodu spawania laserowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int testLsaerWeld(Robot robot) {
        int rtn = -1;
        rtn = robot.ExtDevLoadUDPDriver();
        if (rtn != 0) {
            System.out.println("Failed to load UDP driver, error code: " + rtn);
        }
        robot.Sleep(1000);
        rtn = robot.SetLaserWeldingParam(1, 3, 2000, 3, 1500, 100, 1000);
        if (rtn != 0) {
            System.out.println("SetLaserWeldingParam failed, error code: " + rtn);
        } else {
            System.out.println("SetLaserWeldingParam success");
        }
        rtn = robot.SetLaserWeldingStartExtDoNum(1);
        if (rtn != 0) {
            System.out.println("SetLaserWeldingStartExtDoNum failed, error code: " + rtn);
        }
        rtn = robot.Mode(0);
        if (rtn != 0) {
            System.out.println("Set mode 0 failed, error code: " + rtn);
        }
        robot.Sleep(1000);
        DescPose desc_pos1 = new DescPose(-303.721, -206.960, 297.105, 152.209, 19.857, 109.166);
        DescPose desc_pos2 = new DescPose(-301.575, -254.888, 284.786, 155.919, 26.946, 111.629);
        DescPose desc_safe = new DescPose(-344.386, -280.830, 435.073, 173.835, 15.333, 124.931);

        JointPos jointPos1 = new JointPos(9.827, -99.740, 120.088, -78.900, -77.241, -17.904);
        JointPos jointPos2 = new JointPos(15.251, -96.456, 120.138, -84.664, -68.542, -17.843);
        JointPos jointSafe = new JointPos(19.142, -98.078, 101.493, -83.078, -77.070, -17.794);

        ExaxisPos exaxis = new ExaxisPos(0.0, 0.0, 0.0, 0.0);
        DescPose offset = new DescPose(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);
        int error = robot.MoveL(desc_pos1, 0, 0, 100, 100, 100, -1, 0, exaxis, 0, 0, offset, -1, 0,0,0);
        System.out.println("MoveL to pos1 return: " + error);
        rtn = robot.SetLaserWeldingStartEnd(1, 1, 10000);
        if (rtn != 0) {
            System.out.println("SetLaserWeldingStartEnd (start) failed, error code: " + rtn);
        } else {
            System.out.println("Laser started");
        }
        rtn = robot.MoveL(desc_pos2, 0, 0, 30, 100, 100, -1, 0, exaxis, 0, 0, offset, -1, 0,0, 0);
        System.out.println("MoveL to pos2 return: " + rtn);
        rtn = robot.SetLaserWeldingStartEnd(1, 0, 10000);
        if (rtn != 0) {
            System.out.println("SetLaserWeldingStartEnd (stop) failed, error code: " + rtn);
        } else {
            System.out.println("Laser stopped");
        }
        robot.Sleep(500);
        rtn = robot.MoveL(desc_safe, 0, 0, 100, 100, 100, -1, 0, exaxis, 0, 0, offset, -1, 0,0,0);
        System.out.println("MoveL to safe_pos return: " + rtn);
        rtn = robot.Mode(1);
        if (rtn != 0) {
            System.out.println("Set mode 1 failed, error code: " + rtn);
        }
        robot.Sleep(1000);
        robot.CloseRPC();
        robot.Sleep(1000);

        System.out.println("Test completed");

        return 0;
    }