Urządzenia peryferyjne robota
==============================

.. toctree:: 
    :maxdepth: 5

Konfiguracja chwytaka
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Konfiguracja chwytaka
    * @param  [in] config .company  Producent chwytaka, 1-Robotiq, 2-Huiling, 3-Tianji, 4-Dahuan, 5-Zhixing
    * @param  [in] config .device  Numer urządzenia, Robotiq(0-2F-85 series), Huiling(0-NK series,1-Z-EFG-100), Tianji(0-TEG-110), Dahuan(0-PGI-140), Zhixing(0-CTPM2F20)
    * @param  [in] config .softvesion  Numer wersji oprogramowania, tymczasowo nieużywane, domyślnie 0
    * @param  [in] config .bus  Pozycja magistrali końcowej urządzenia, tymczasowo nieużywane, domyślnie 0
    * @return  Kod błędu
    */
    int SetGripperConfig(DeviceConfig config);

Pobranie konfiguracji chwytaka
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Pobranie konfiguracji chwytaka
    * @param  [out] config .company  Producent chwytaka, 1-Robotiq, 2-Huiling, 3-Tianji, 4-Dahuan, 5-Zhixing
    * @param  [out] config .device  Numer urządzenia, Robotiq(0-2F-85 series), Huiling(0-NK series,1-Z-EFG-100), Tianji(0-TEG-110), Dahuan(0-PGI-140), Zhixing(0-CTPM2F20)
    * @param  [out] config .softvesion  Numer wersji oprogramowania, tymczasowo nieużywane, domyślnie 0
    * @param  [out] config .bus  Pozycja magistrali końcowej urządzenia, tymczasowo nieużywane, domyślnie 0
    * @return  Kod błędu
    */
    int GetGripperConfig(DeviceConfig config);

Aktywacja chwytaka
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Aktywacja chwytaka
    * @param  [in] index  Numer chwytaka
    * @param  [in] act  0-reset, 1-aktywacja
    * @return  Kod błędu
    */
    int ActGripper(int index, int act); 

Sterowanie chwytakiem
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Sterowanie chwytakiem
    * @param  [in] index  Numer chwytaka
    * @param  [in] pos  Procent pozycji, zakres [0~100]
    * @param  [in] vel  Procent prędkości, zakres [0~100]
    * @param  [in] force  Procent momentu, zakres [0~100]
    * @param  [in] max_time  Maksymalny czas oczekiwania, zakres [0~30000], jednostka ms
    * @param  [in] block  0-blokujący, 1-nieblokujący
    * @param  [in] type Typ chwytaka, 0-chwytak równoległy; 1-chwytak obrotowy
    * @param  [in] rotNum Liczba obrotów
    * @param  [in] rotVel Procent prędkości obrotowej [0-100]
    * @param  [in] rotTorque Procent momentu obrotowego [0-100]
    * @return Kod błędu
    */
    int MoveGripper(int index, int pos, int vel, int force, int max_time, int block, int type, double rotNum, int rotVel, int rotTorque); 

Pobranie stanu ruchu chwytaka
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Pobranie stanu ruchu chwytaka
    * @return List[0]:Kod błędu; List[1] : fault  0-brak błędu, 1-jest błąd; List[2]: status  0-ruch niezakończony, 1-ruch zakończony
    */
    List<Integer> GetGripperMotionDone(); 

Pobranie stanu aktywacji chwytaka
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Pobranie stanu aktywacji chwytaka
    * @return  List[0]:Kod błędu; List[1] : fault  0-brak błędu, 1-jest błąd; List[2]: status  bit0~bit15 odpowiada numerom chwytaka 0~15, bit=0 oznacza nieaktywny, bit=1 oznacza aktywny
    */
    List<Number> GetGripperActivateStatus()

Pobranie pozycji chwytaka
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Pobranie pozycji chwytaka
    * @return  List[0]:Kod błędu; List[1] : fault  0-brak błędu, 1-jest błąd; List[2]: position  Procent pozycji, zakres 0~100%
    */
    List<Number> GetGripperCurPosition()

Pobranie prędkości chwytaka
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Pobranie prędkości chwytaka
    * @return  List[0]:Kod błędu; List[1] : fault  0-brak błędu, 1-jest błąd; List[2]: speed  Procent prędkości, zakres 0~100%
    */
    List<Number> GetGripperCurSpeed()

Pobranie prądu chwytaka
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Pobranie prądu chwytaka
    * @return  List[0]:Kod błędu; List[1] : fault  0-brak błędu, 1-jest błąd; List[2]: current  Procent prądu, zakres 0~100%
    */
    List<Number> GetGripperCurCurrent()

Pobranie napięcia chwytaka
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Pobranie napięcia chwytaka
    * @return List[0]:Kod błędu; List[1] : fault  0-brak błędu, 1-jest błąd; List[2]:voltage  Napięcie, jednostka 0.1V
    */
    List<Number> GetGripperVoltage()

Pobranie temperatury chwytaka
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Pobranie temperatury chwytaka
    * @return List[0]:Kod błędu; List[1] : fault  0-brak błędu, 1-jest błąd; List[2]:temp  Temperatura, jednostka ℃
    */
    List<Number> GetGripperTemp()

Obliczenie punktu wstępnego chwytania - wizja
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Obliczenie punktu wstępnego chwytania - wizja 
    * @param [in] desc_pos  Pozycja kartezjańska punktu chwytania
    * @param [in] zlength   Przesunięcie osi Z
    * @param [in] zangle    Przesunięcie obrotu wokół osi Z
    * @param [out] pre_pos  Punkt wstępny
    * @return Kod błędu 
    */ 
    int ComputePrePick(DescPose desc_pos, double zlength, double zangle, DescPose pre_pos);

Obliczenie punktu wycofania - wizja
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Obliczenie punktu wycofania - wizja 
    * @param [in] desc_pos  Pozycja kartezjańska punktu chwytania
    * @param [in] zlength   Przesunięcie osi Z 
    * @param [in] zangle    Przesunięcie obrotu wokół osi Z
    * @param [out] post_poss Punkt wycofania
    * @return Kod błędu 
    */ 
    int ComputePostPick(DescPose desc_pos, double zlength, double zangle, DescPose post_pos);

Przykład kodu operacji chwytakiem robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestGripper(Robot robot)
    {
        int company = 4;
        int device = 0;
        int softversion = 0;
        int bus = 2;
        int index = 2;
        int act = 0;
        int max_time = 30000;
        int block = 0;

        int current_pos = 0;
        int current = 0;
        int voltage = 0;
        int temp = 0;
        int speed = 0;

        DeviceConfig cnn=new DeviceConfig(company,device,softversion,bus);
        robot.SetGripperConfig(cnn);
        robot.GetGripperConfig(cnn);

        robot.ActGripper(index, act);
        robot.Sleep(1000);
        act = 1;
        robot.ActGripper(index, act);
        robot.Sleep(1000);

        robot.MoveGripper(index, 100, 50, 50, max_time, block, 0, 0, 0, 0);
        robot.Sleep(1000);
        robot.MoveGripper(index, 0, 50, 0, max_time, block, 0, 0, 0, 0);

        List<Integer> stat=new ArrayList<>();
        stat=robot.GetGripperMotionDone();

        List<Number> list=new ArrayList<>();
        list=robot.GetGripperActivateStatus();

        list=robot.GetGripperCurPosition();

        list=robot.GetGripperCurCurrent();

        list=robot.GetGripperVoltage();

        list=robot.GetGripperTemp();

        list=robot.GetGripperCurSpeed();

        int retval = 0;
        DescPose prepick_pose = new DescPose(){};
        DescPose postpick_pose = new DescPose(){};

        DescPose p1Desc=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose p2Desc=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);

        retval = robot.ComputePrePick(p1Desc, 10, 0, prepick_pose);

        retval = robot.ComputePostPick(p2Desc, -10, 0, postpick_pose);
        return 0;
    }

Pobranie liczby obrotów chwytaka obrotowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Pobranie liczby obrotów chwytaka obrotowego
    * @return List[0]:Kod błędu List[1]: 0-brak błędu, 1-jest błąd List[2]:Liczba obrotów
    */
    List<Number> GetGripperRotNum(); 

Pobranie procentu prędkości obrotowej chwytaka obrotowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Pobranie procentu prędkości obrotowej chwytaka obrotowego
    * @return List[0]:Kod błędu List[1]: 0-brak błędu, 1-jest błąd List[2]:Procent prędkości obrotowej
    */
    List<Number> GetGripperRotSpeed(); 

Pobranie procentu momentu obrotowego chwytaka obrotowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Pobranie procentu momentu obrotowego chwytaka obrotowego
    * @return List[0]:Kod błędu List[1]: 0-brak błędu, 1-jest błąd List[2]:Procent momentu obrotowego
    */
    List<Number> GetGripperRotTorque(); 

Przykład kodu pobrania stanu chwytaka obrotowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestRotGripperState(Robot robot)
    {
        int fault = 0;
        List<Number> rotNum=new ArrayList<>();
        List<Number> rotSpeed=new ArrayList<>();
        List<Number> rotTorque=new ArrayList<>();

        rotNum=robot.GetGripperRotNum();
        rotSpeed=robot.GetGripperRotSpeed();
        rotTorque=robot.GetGripperRotTorque();
        System.out.println("gripper rot num :"+rotNum.get(2)+ ", gripper rotSpeed :"+rotSpeed.get(2)+",gripper rotTorque : "+rotTorque.get(2));

        return 0;
    }

Uruchomienie, zatrzymanie przenośnika taśmowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Uruchomienie, zatrzymanie przenośnika taśmowego
    * @param  [in] status Stan, 1-uruchom, 0-zatrzymaj
    * @return  Kod błędu
    */
    int ConveyorStartEnd(int status);

Rejestracja punktu detekcji IO
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Rejestracja punktu detekcji IO
    * @return  Kod błędu
    */
    int ConveyorPointIORecord();

Rejestracja punktu A
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Rejestracja punktu A
    * @return  Kod błędu
    */
    int ConveyorPointARecord(); 

Rejestracja punktu odniesienia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Rejestracja punktu odniesienia
    * @return  Kod błędu
    */
    int ConveyorRefPointRecord();

Rejestracja punktu B
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Rejestracja punktu B
    * @return Kod błędu
    */
    int ConveyorPointBRecord(); 

Detekcja IO przedmiotu na przenośniku
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Detekcja IO przedmiotu na przenośniku
    * @param [in] max_t Maksymalny czas detekcji, jednostka ms
    * @return Kod błędu 
    */ 
    int ConveyorIODetect(int max_t);

Pobranie bieżącej pozycji przedmiotu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Pobranie bieżącej pozycji przedmiotu
    * @param [in] mode 1-śledzenie i chwytanie, 2-śledzenie ruchu, 3-śledzenie TPD
    * @return Kod błędu 
    */ 
    int ConveyorGetTrackData(int mode);

Rozpoczęcie śledzenia przenośnika
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Rozpoczęcie śledzenia przenośnika
    * @param [in] status Stan, 1-uruchom, 0-zatrzymaj
    * @return Kod błędu 
    */ 
    int ConveyorTrackStart(int status);

Zatrzymanie śledzenia przenośnika
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Zatrzymanie śledzenia przenośnika
    * @return Kod błędu 
    */ 
    int ConveyorTrackEnd();

Konfiguracja parametrów przenośnika
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionchanged:: Java SDK-v1.0.4-3.8.1

.. code-block:: Java
    :linenos:

    /**
    * @brief  Konfiguracja parametrów przenośnika
    * @param [in] encChannel Kanał enkodera 1~2
    * @param [in] resolution Liczba impulsów enkodera na jeden obrót
    * @param [in] lead Odległość przejścia przenośnika na jeden obrót enkodera
    * @param [in] wpAxis Numer układu przedmiotu dla funkcji śledzenia ruchu wybierz numer układu przedmiotu, dla śledzenia chwytania, śledzenia TPD ustaw na 0
    * @param [in] vision Czy z wizją  0 nie  1 tak
    * @param [in] speedRadio Współczynnik prędkości dla opcji śledzenia chwytania przenośnika (1-100) dla innych opcji domyślnie 1
    * @param [in] followType Typ śledzenia ruchu, 0-śledzenie ruchu; 1-śledzenie kontrolne
    * @param [in] startDis Należy ustawić dla śledzenia kontrolnego, Odległość początkowa śledzenia, -1: automatyczne obliczenie (automatyczne śledzenie kontrolne po dotarciu przedmiotu pod robota), jednostka mm, wartość domyślna 0
    * @param [in] endDis Należy ustawić dla śledzenia kontrolnego, Odległość końcowa śledzenia, jednostka mm, wartość domyślna 100
    * @return Kod błędu
    */
    int ConveyorSetParam(int encChannel, int resolution, double lead, int wpAxis, int vision, double speedRadio, int followType, int startDis, int endDis); 

Ustawienie kompensacji punktu chwytania przenośnika
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Ustawienie kompensacji punktu chwytania przenośnika
    * @param [in] cmp Pozycja kompensacji double[3]{x, y, z}
    * @return Kod błędu 
    */ 
    int ConveyorCatchPointComp(Object[] cmp);

Ruch liniowy przenośnika
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Ruch liniowy
    * @param [in] name Opis punktu ruchu
    * @param [in] tool Numer narzędzia, zakres [0~14]
    * @param [in] wobj Numer przedmiotu, zakres [0~14]
    * @param [in] vel Procent prędkości, zakres [0~100]
    * @param [in] acc Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param [in] ovl Współczynnik skalowania prędkości, zakres [0~100]
    * @param [in] blendR [-1.0]-ruch do pozycji (blokujący), [0~1000.0]-promień wygładzania (nieblokujący), jednostka mm
    * @return Kod błędu 
    */ 
    int ConveyorTrackMoveL(String name, int tool, int wobj, double vel, double acc, double ovl, double blendR);   

Detekcja wejścia komunikacyjnego przenośnika
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.4-3.8.1

.. code-block:: Java
    :linenos:

    /** 
    * @brief Detekcja wejścia komunikacyjnego przenośnika
    * @param [in] timeout Czas oczekiwania na timeout ms
    * @return Kod błędu
    */
    int ConveyorComDetect(int timeout);

Wyzwolenie detekcji wejścia komunikacyjnego przenośnika
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.4-3.8.1

.. code-block:: Java
    :linenos:

    /** 
    * @brief Wyzwolenie detekcji wejścia komunikacyjnego przenośnika
    * @param [in] timeout Czas oczekiwania na timeout ms
    * @return Kod błędu
    */
    int ConveyorComDetectTrigger();

Przykładowy program operacji przenośnika robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestConveyor(Robot robot)
    {
        int retval = 0;

        retval = robot.ConveyorStartEnd(1);

        retval = robot.ConveyorPointIORecord();

        retval = robot.ConveyorPointARecord();

        retval = robot.ConveyorRefPointRecord();

        retval = robot.ConveyorPointBRecord();

        retval = robot.ConveyorStartEnd(0);

        retval = 0;

        retval = robot.ConveyorSetParam(1,10000,200,0,0,20,0,0,100);

        Object[] cmp = new Object[]{ 0.0, 0.0, 0.0 };
        retval = robot.ConveyorCatchPointComp(cmp);

        int index = 1;
        int max_time = 30000;
        int block = 0;
        retval = 0;

        DescPose p1Desc=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose p2Desc=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);


        retval = robot.MoveCart(p1Desc, 1, 0, 100.0, 100.0, 100.0, -1.0, -1);

        retval = robot.WaitMs(1);

        retval = robot.ConveyorTrackStart(1);

        retval = robot.ConveyorTrackMoveL("cvrCatchPoint", 1, 0, 100, 100, 100, -1.0);

        retval = robot.MoveGripper(index, 51, 40, 30, max_time, block, 0, 0, 0, 0);

        retval = robot.ConveyorTrackMoveL("cvrRaisePoint", 1, 0, 100, 100, 100, -1.0);

        retval = robot.ConveyorTrackEnd();

        robot.MoveCart(p2Desc, 1, 0, 100.0, 100.0, 100.0, -1.0, -1);

        retval = robot.MoveGripper(index, 100, 40, 10, max_time, block, 0, 0, 0, 0);

        return 0;
    }

Konfiguracja czujnika końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Konfiguracja czujnika końcowego
    * @param [in] config idCompany Producent, 18-JUNKONG；25-HUIDE
    * @param [in] config idDevice Typ, 0-JUNKONG/RYR6T.V1.0
    * @param [in] config idSoftware Wersja oprogramowania, 0-J1.0/HuiDe1.0(tymczasowo niedostępne)
    * @param [in] config idBus Pozycja podłączenia, 1-port końcowy 1；2-port końcowy 2...8-port końcowy 8(tymczasowo niedostępne)
    * @return Kod błędu
    */
    int AxleSensorConfig(DeviceConfig config);

Pobranie konfiguracji czujnika końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Pobranie konfiguracji czujnika końcowego
    * @param [out] config idCompany Producent, 18-JUNKONG；25-HUIDE
    * @param [out] config idDevice Typ, 0-JUNKONG/RYR6T.V1.0
    * @return Kod błędu
    */
    int AxleSensorConfigGet(DeviceConfig config);

Aktywacja czujnika końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Aktywacja czujnika końcowego
    * @param [in] actFlag 0-reset；1-aktywacja
    * @return Kod błędu
    */
    int AxleSensorActivate(int actFlag);

Zapis do rejestru czujnika końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Zapis do rejestru czujnika końcowego
    * @param [in] devAddr  Numer adresu urządzenia 0-255
    * @param [in] regHAddr Adres rejestru wysoki 8 bitów
    * @param [in] regLAddr Adres rejestru niski 8 bitów
    * @param [in] regNum  Liczba rejestrów 0-255
    * @param [in] data1 Wartość do zapisu do rejestru 1
    * @param [in] data2 Wartość do zapisu do rejestru 2
    * @param [in] isNoBlock 0-blokujący；1-nieblokujący
    * @return Kod błędu
    */
    int AxleSensorRegWrite(int devAddr, int regHAddr, int regLAddr, int regNum, int data1, int data2, int isNoBlock);

Przykład kodu czujnika końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestAxleSensor(Robot robot)
    {
        DeviceConfig con=new DeviceConfig(18,0,0,1);
        robot.AxleSensorConfig(con);
        int company = -1;
        int type = -1;
        robot.AxleSensorConfigGet(con);

        int rtn = robot.AxleSensorActivate(1);

        robot.Sleep(1000);

        rtn = robot.AxleSensorRegWrite(1, 4, 6, 1, 0, 0, 0);
        return 0;
    }

Pobranie protokołu urządzeń peryferyjnych robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Pobranie protokołu urządzeń peryferyjnych robota
    * @return List[0]:Kod błędu; List[1] : int protocol Numer protokołu urządzeń peryferyjnych robota 4096-karta sterująca osią rozszerzenia；4097-ModbusSlave；4098-ModbusMaster 
    */
    List<Integer> GetExDevProtocol();

Ustawienie protokołu urządzeń peryferyjnych robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Ustawienie protokołu urządzeń peryferyjnych robota
    * @param [in] protocol Numer protokołu urządzeń peryferyjnych robota 4096-karta sterująca osią rozszerzenia；4097-ModbusSlave；4098-ModbusMaster
    * @return Kod błędu 
    */
    int SetExDevProtocol(int protocol);

Przykładowy program ustawiania protokołu urządzeń peryferyjnych robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestExDevProtocol(Robot robot)
    {
        int protocol = 4096;
        int rtn = robot.SetExDevProtocol(protocol);
        List<Integer> integer=new ArrayList<>();
        integer = robot.GetExDevProtocol();

        return 0;
    }

Pobranie parametrów komunikacji końcowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Pobranie parametrów komunikacji końcowej
    * @param [out] param Parametry komunikacji końcowej
    * @return Kod błędu 
    */
    int GetAxleCommunicationParam(AxleComParam param)

Ustawienie parametrów komunikacji końcowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Ustawienie parametrów komunikacji końcowej
    * @param [in] param Parametry komunikacji końcowej
    * @return Kod błędu 
    */
    int SetAxleCommunicationParam(AxleComParam param)

Ustawienie typu transferu pliku końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawienie typu transferu pliku końcowego
    * @param [in] type 1-plik aktualizacji MCU；2-plik LUA
    * @return  Kod błędu
    */
    public int SetAxleFileType(int type)

Ustawienie włączenia wykonania LUA końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawienie włączenia wykonania LUA końcowego
    * @param [in] enable 0-niewłączony；1-włączony
    * @return  Kod błędu
    */
    public int SetAxleLuaEnable(int enable)

Odnowienie błędu wyjątkowego pliku LUA końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Odnowienie błędu wyjątkowego pliku LUA końcowego
    * @param [in] status 0-nie odnawiaj；1-odnów
    * @return  Kod błędu
    */
    public int SetRecoverAxleLuaErr(int status)

Pobranie stanu włączenia wykonania LUA końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Pobranie stanu włączenia wykonania LUA końcowego
    * @param [out] status[0]: 0-niewłączony；1-włączony
    * @return  Kod błędu
    */
    int GetAxleLuaEnableStatus(int[] status)

Ustawienie typu włączenia urządzenia końcowego LUA
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawienie typu włączenia urządzenia końcowego LUA
    * @param forceSensorEnable Stan włączenia czujnika siły, 0-niewłączony；1-włączony
    * @param gripperEnable Stan włączenia chwytaka, 0-niewłączony；1-włączony
    * @param IOEnable Stan włączenia urządzenia IO, 0-niewłączony；1-włączony
    * @return  Kod błędu
    */
    public int SetAxleLuaEnableDeviceType(int forceSensorEnable, int gripperEnable, int IOEnable)

Pobranie typu włączenia urządzenia końcowego LUA
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
     * @brief Pobranie typu włączenia urządzenia końcowego LUA
     * @param enable enable[0]:forceSensorEnable Stan włączenia czujnika siły, 0-niewłączony；1-włączony
     * @param enable enable[1]:gripperEnable Stan włączenia chwytaka, 0-niewłączony；1-włączony
     * @param enable enable[2]:IOEnable Stan włączenia urządzenia IO, 0-niewłączony；1-włączony
     * @return  Kod błędu
     */
    public int GetAxleLuaEnableDeviceType(int[] enable)

Pobranie aktualnie skonfigurowanego urządzenia końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
     * @brief Pobranie aktualnie skonfigurowanego urządzenia końcowego
     * @param forceSensorEnable Numer urządzenia włączonego czujnika siły 0-niewłączony；1-włączony
     * @param gripperEnable Numer urządzenia włączonego chwytaka, 0-niewłączony；1-włączony
     * @param IODeviceEnable Numer urządzenia włączonego urządzenia IO, 0-niewłączony；1-włączony
     * @return  Kod błędu
     */
    public int GetAxleLuaEnableDevice(int[] forceSensorEnable, int[] gripperEnable, int[] IODeviceEnable)

Ustawienie włączenia funkcji sterowania ruchem chwytaka
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
     * @brief Ustawienie włączenia funkcji sterowania ruchem chwytaka
     * @param id Numer urządzenia chwytaka
     * @param func func[0]-włączenie chwytaka；func[1]-inicjalizacja chwytaka；2-ustawienie pozycji；3-ustawienie prędkości；4-ustawienie momentu；6-odczyt stanu chwytaka；7-odczyt stanu inicjalizacji；8-odczyt kodu błędu；9-odczyt pozycji；10-odczyt prędkości；11-odczyt momentu
     * @return  Kod błędu
     */
    public int SetAxleLuaGripperFunc(int id, int[] func)

Pobranie włączenia funkcji sterowania ruchem chwytaka
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
     * @brief Pobranie włączenia funkcji sterowania ruchem chwytaka
     * @param id Numer urządzenia chwytaka
     * @param func func[0]-włączenie chwytaka；func[1]-inicjalizacja chwytaka；2-ustawienie pozycji；3-ustawienie prędkości；4-ustawienie momentu；6-odczyt stanu chwytaka；7-odczyt stanu inicjalizacji；8-odczyt kodu błędu；9-odczyt pozycji；10-odczyt prędkości；11-odczyt momentu
     * @return  Kod błędu
     */
    public int GetAxleLuaGripperFunc(int id, int[] func)

Zapis pliku węzła podrzędnego Ethercat robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
     * @brief Zapis pliku węzła podrzędnego Ethercat robota
     * @param type Typ pliku węzła podrzędnego, 1-plik aktualizacji węzła podrzędnego；2-plik konfiguracyjny węzła podrzędnego
     * @param slaveID Numer węzła podrzędnego
     * @param fileName Nazwa przesyłanego pliku
     * @return  Kod błędu
     */
    public int SlaveFileWrite(int type, int slaveID, String fileName)

Przesłanie pliku protokołu otwartego LUA końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
     * @brief Przesłanie pliku protokołu otwartego LUA końcowego
     * @param filePath Ścieżka lokalnego pliku lua ".../AXLE_LUA_End_DaHuan.lua"
     * @return Kod błędu
     */
    public int AxleLuaUpload(String filePath)

Wprowadzenie węzła podrzędnego Ethercat robota w tryb boot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
     * @brief Wprowadzenie węzła podrzędnego Ethercat robota w tryb boot
     * @return  Kod błędu
     */
    public int SetSysServoBootMode()

Przykład kodu operacji na pliku LUA końcowego robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestAxleLua(Robot robot)
    {
        robot.AxleLuaUpload("D://zUP/AXLE_LUA_End_DaHuan.lua");

        AxleComParam param=new AxleComParam(7, 8, 1, 0, 5, 3, 1);
        robot.SetAxleCommunicationParam(param);

        robot.GetAxleCommunicationParam(param);

        robot.SetAxleLuaEnable(1);
        int[] luaEnableStatus = new int[]{0};
        robot.GetAxleLuaEnableStatus(luaEnableStatus);
        robot.SetAxleLuaEnableDeviceType(0, 1, 0);

        int forceEnable = 0;
        int gripperEnable = 0;
        int ioEnable = 0;
        int [] enable=new int[]{0,0,0};
        robot.GetAxleLuaEnableDeviceType(enable);

        int[] func = { 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1 };
        robot.SetAxleLuaGripperFunc(1, func);
        int[] getFunc = { 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0};
        robot.GetAxleLuaGripperFunc(1, getFunc);
        int[] getforceEnable = { 0,0,0,0,0,0,0,0};
        int[] getgripperEnable = { 0,0,0,0,0,0,0,0};
        int[] getioEnable = { 0,0,0,0,0,0,0,0};
        robot.GetAxleLuaEnableDevice(getforceEnable, getgripperEnable, getioEnable);
        for (int i = 0; i < 8; i++)
        {
            System.out.println(getforceEnable[i]);
        }
        System.out.println("getgripperEnable status : ");
        for (int i = 0; i < 8; i++)
        {
            System.out.println(getgripperEnable[i]);
        }
        System.out.println("getioEnable status : ");
        for (int i = 0; i < 8; i++)
        {
            System.out.println(getioEnable[i]);
        }
        robot.ActGripper(1, 0);
        robot.Sleep(2000);
        robot.ActGripper(1, 1);
        robot.Sleep(2000);
        robot.MoveGripper(1, 90, 10, 100, 50000, 0, 0, 0, 0, 0);
        int pos = 0;
        while (true)
        {
            ROBOT_STATE_PKG pkg=new ROBOT_STATE_PKG();
            pkg=robot.GetRobotRealTimeState();
            System.out.println("gripper pos is:"+pkg.gripper_position);
            robot.Sleep(100);
        }

    }

Pobranie stanu przycisków SmartTool
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.4-3.8.1

.. code-block:: Java
    :linenos:

    /**
    * @brief Pobranie stanu przycisków SmartTool
    * @param [out] state Stan przycisków uchwytu SmartTool;(bit0:0-komunikacja normalna；1-utrata komunikacji；bit1-cofnij operację；bit2-wyczyść program；bit3-przycisk A；bit4-przycisk B；bit5-przycisk C；bit6-przycisk D；bit7-przycisk E；bit8-przycisk IO；bit9-ręczny/automatyczny；bit10-start)
    * @return Kod błędu
    */
    int GetSmarttoolBtnState(int[] state)

Przykład kodu przycisków SmartTool
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static void main(String[] args) 
    {
        Robot robot = new Robot();
        robot.SetReconnectParam(true, 100, 500);//设置重连次数、间隔
        robot.LoggerInit(FrLogType.DIRECT, FrLogLevel.INFO, "D://log", 10, 10);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn == 0) {
            System.out.println("rpc连接 success");
        } else {
            System.out.println("rpc连接 fail");
            return;
        }

        int[] state = {0};
        while (true)
        {
            robot.GetSmarttoolBtnState(state);

            String binaryString = String.format("%32s", Integer.toBinaryString(state[0])).replace(' ', '0');
            System.out.println("GetSmarttoolBtnState:"+binaryString);
            robot.Sleep(100);
        }
    }

Przesłanie pliku LUA protokołu otwartego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief Przesłanie pliku LUA protokołu otwartego
    * @param  filePath Ścieżka lokalnego pliku lua protokołu otwartego
    * @return Kod błędu
    */
    public int OpenLuaUpload(String filePath)


Pobranie parametrów karty węzła podrzędnego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Pobranie parametrów karty węzła podrzędnego
    * @param  type  0-Ethercat，1-CClink, 3-Ethercat, 4-EIP
    * @param  version  Wersja protokołu
    * @param  connState  0-niepołączony 1-połączony
    * @return  Kod błędu
    */
    public int GetFieldBusConfig(int[] type, int[] version, int[] connState)

Zapis DO węzła podrzędnego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Zapis DO węzła podrzędnego
    * @param   DOIndex  Numer DO
    * @param   wirteNum  Liczba do zapisu
    * @param   status Wartości do zapisu, maksymalnie 8
    * @return  Kod błędu
    */
    public int FieldBusSlaveWriteDO(int DOIndex, int wirteNum, int[] status)

Zapis AO węzła podrzędnego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /*
    * @brief  Zapis AO węzła podrzędnego
    * @param  AOIndex Numer AO
    * @param  wirteNum Liczba do zapisu
    * @param  status Tablica wartości do zapisu (maksymalnie 8), AO0~AO15 są typu całkowitego, AO16~AO31 są typu zmiennoprzecinkowego
    * @return  Kod błędu
    */
    public int FieldBusSlaveWriteAO(int AOIndex, int wirteNum, double[] status)

Odczyt DI węzła podrzędnego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Odczyt DI węzła podrzędnego
    * @param  DOIndex  Numer DI
    * @param  readNum  Liczba do odczytu
    * @param  status Odczytane wartości, maksymalnie 8
    * @return  Kod błędu
    */
    public int FieldBusSlaveReadDI(int DOIndex, int readNum, int[] status)

Odczyt AI węzła podrzędnego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Odczyt AI węzła podrzędnego
    * @param  AIIndex  Numer AI
    * @param  readNum  Liczba do odczytu
    * @param  status Odczytane wartości, maksymalnie 8
    * @return  Kod błędu
    */
    public int FieldBusSlaveReadAI(int AIIndex, int readNum, double[] status)

Oczekiwanie na wejście rozszerzonego DI
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief Oczekiwanie na wejście rozszerzonego DI
    * @param  DIIndex Numer DI
    * @param  status 0-niski poziom；1-wysoki poziom
    * @param  waitMs Maksymalny czas oczekiwania (ms)
    * @return Kod błędu
    */
    public int FieldBusSlaveWaitDI(int DIIndex, int status, int waitMs)

Oczekiwanie na wejście rozszerzonego AI
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief Oczekiwanie na wejście rozszerzonego AI
    * @param  AIIndex Numer AI
    * @param  waitType 0-większe niż；1-mniejsze niż
    * @param  value Wartość AI
    * @param  waitMs Maksymalny czas oczekiwania (ms)
    * @return Kod błędu
    */
    public int FieldBusSlaveWaitAI(int AIIndex, int waitType, double value, int waitMs)

Przykład kodu instrukcji interfejsów trybu węzła podrzędnego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static void testFieldBusBoard(Robot robot)
    {
        // Przesłanie i załadowanie pliku protokołu otwartego
        robot.OpenLuaUpload("D://zUP/1111/CtrlDev_field.lua");
        robot.Sleep(2000);
        robot.SetCtrlOpenLUAName(3, "CtrlDev_field.lua");
        robot.UnloadCtrlOpenLUA(3);
        robot.LoadCtrlOpenLUA(3);
        robot.Sleep(8000);
        int[] type=new int[1];
        int[] version=new int[1];
        int[] connState=new int[1];
        // Pobranie typu protokołu karty węzła podrzędnego, wersji oprogramowania, stanu połączenia z PLC
        robot.GetFieldBusConfig(type, version, connState);
        System.out.println("type is: "+type[0]+", version is : "+version[0]+", connState is : "+connState[0]);
        // Zapis DO0 = 1, DO1 = 0, DO2 = 1
        int[] ctrl =new int[8];
        ctrl[0] = 1;
        ctrl[1] = 0;
        ctrl[2] = 1;
        robot.FieldBusSlaveWriteDO(0, 3, ctrl);
        // Zapis AO2 = 0x1000
        int[] ctrlAO =new int[8];
        ctrlAO[0] = 0x1000;
        robot.FieldBusSlaveWriteAO(2, 1, ctrlAO);
        int[] DI=new int[4];
        double[] AI=new double[3];
        // Pętla monitorująca DI0~DI3 AI0~AI2
        for (int i = 0; i < 100; i++)
        {
            robot.FieldBusSlaveReadDI(0, 4, DI);
            System.out.println("DI0 is: "+DI[0]+", DI1 is: "+DI[1]+",DI2 is: "+DI[2]+",DI3 is: "+DI[3]);
            robot.FieldBusSlaveReadAI(0, 3, AI);
            System.out.println("AI0 is: "+AI[0]+ ",AI1 is: "+AI[1]+",AI2 is: "+AI[2]);
            robot.Sleep(10);
        }
        // Oczekiwanie, czy DI0 ma wartość 1, czas oczekiwania 100ms i wydrukowanie wyniku
        int ret = robot.FieldBusSlaveWaitDI(0, 1, 100);
        System.out.println("FieldBusSlaveWaitDI result is: "+ ret);
        // Oczekiwanie, czy AI0 jest większe niż 400, czas oczekiwania 100ms i wydrukowanie wyniku
        ret = robot.FieldBusSlaveWaitAI(0,0,400.00,100);
        System.out.println("FieldBusSlaveWaitAI result is: "+ ret);
        robot.CloseRPC();
    }

Sterowanie matrycową przyssawką
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief Sterowanie matrycową przyssawką
    * @param  slaveID Numer węzła podrzędnego
    * @param  len Długość
    * @param  ctrlValue Wartość sterowania 1-zassanie z maksymalnym podciśnieniem 2-zassanie z ustawionym podciśnieniem 3-zatrzymanie zassania
    * @return Kod błędu
    */
    public int SetSuckerCtrl(int slaveID, int len, int[] ctrlValue)

Pobranie stanu matrycowej przyssawki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief Pobranie stanu matrycowej przyssawki
    * @param  slaveID Numer węzła podrzędnego
    * @param  state Stan przyssania 0-zwolnienie przedmiotu 1-wykryto pomyślne przyssanie przedmiotu 2-brak przyssania przedmiotu 3-oderwanie przedmiotu
    * @param  pressValue Bieżące podciśnienie jednostka kpa
    * @param  error Bieżący kod błędu przyssawki
    * @return Kod błędu
    */
    public int GetSuckerState(int slaveID, int[] state, int[] pressValue, int[] error)

Oczekiwanie na stan przyssawki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief Oczekiwanie na stan przyssawki
    * @param  slaveID Numer węzła podrzędnego
    * @param  state Stan przyssania 0-zwolnienie przedmiotu 1-wykryto pomyślne przyssanie przedmiotu 2-brak przyssania przedmiotu 3-oderwanie przedmiotu
    * @param  ms Maksymalny czas oczekiwania
    * @return Kod błędu
    */
    public int WaitSuckerState(int slaveID, int state, int ms)

Przykład kodu instrukcji sterowania matrycową przyssawką
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static void testSucker(Robot robot)
    {
        // Przesłanie i załadowanie pliku protokołu otwartego
        robot.OpenLuaUpload("C：//项目/外设SDK/CtrlDev_sucker.lua");
        robot.Sleep(2000);
        robot.UnloadCtrlOpenLUA(1);
        robot.LoadCtrlOpenLUA(1);
        robot.Sleep(1000);
        // Sterowanie w trybie rozgłaszania przyssawki, zassanie z maksymalną wydajnością
        int[] ctrl = {1};
        robot.SetSuckerCtrl(0, 1, ctrl);
        int[] state=new int[1];
        int[] pressVlaue=new int[1];
        int[] error=new int[1];
        // Pętla monitorująca stan przyssawki nr 1 i nr 12
        for (int i = 0; i < 100; i++)
        {
            robot.GetSuckerState(1, state,pressVlaue, error);
            System.out.println("sucker1 state is:"+state[0]+",pressVlaue is:"+pressVlaue[0]+",error num is"+error[0]);
            robot.GetSuckerState(12, state, pressVlaue, error);
            System.out.println("sucker12 state is :"+state[0]+", pressVlaue is:"+pressVlaue[0]+",error num is:"+error[0]);
            robot.Sleep(100);
        }
        // Oczekiwanie, czy przyssawka nr 1 osiągnęła stan przyssania przedmiotu, czas oczekiwania 100ms
        int ret = robot.WaitSuckerState(1, 1, 100);
        System.out.println("WaitSuckerState result is:"+ ret);
        // Wyłączenie przyssawek nr 1 i nr 12 w trybie unicast
        ctrl[0] = 3;
        robot.SetSuckerCtrl(1, 1, ctrl);
        robot.SetSuckerCtrl(12, 1, ctrl);
        robot.CloseRPC();
    }

Funkcja włączania/wyłączania urządzenia peryferyjnego laserowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Funkcja włączania/wyłączania urządzenia peryferyjnego laserowego
     * @param [in] OnOff 0-wyłącz 1-włącz
     * @param [in] weldId ID spoiny domyślnie 0
     * @return Kod błędu
     */
    public int LaserTrackingLaserOnOff(int OnOff, int weldId)
    
Funkcja rozpoczęcia/zakończenia śledzenia laserowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:
    
    /**
     * @brief Funkcja rozpoczęcia/zakończenia śledzenia laserowego
     * @param [in] OnOff 0-zakończ 1-rozpocznij
     * @param [in] coordId Numer układu narzędzia urządzenia peryferyjnego laserowego
     * @return Kod błędu
     */
    public int LaserTrackingTrackOnOff(int OnOff, int coordId)

Poszukiwanie pozycji laserowej - stały kierunek
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Poszukiwanie pozycji laserowej - stały kierunek
     * @param [in] direction 0-x+ 1-x- 2-y+ 3-y- 4-z+ 5-z-
     * @param [in] vel Prędkość jednostka%
     * @param [in] distance Maksymalna odległość poszukiwania jednostka mm
     * @param [in] timeout Czas timeout poszukiwania jednostka ms
     * @param [in] posSensorNum Numer narzędzia skalibrowanego lasera
     * @return Kod błędu
     */
    public int LaserTrackingSearchStart_xyz(int direction, int vel, int distance, int timeout, int posSensorNum)
    
Poszukiwanie pozycji laserowej - dowolny kierunek
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Poszukiwanie pozycji laserowej - dowolny kierunek
     * @param [in] directionPoint Punkt wejściowy poszukiwania współrzędne xyz
     * @param [in] vel Prędkość jednostka%
     * @param [in] distance Maksymalna odległość poszukiwania jednostka mm
     * @param [in] timeout Czas timeout poszukiwania jednostka ms
     * @param [in] posSensorNum Numer narzędzia skalibrowanego lasera
     * @return Kod błędu
     */
    public int LaserTrackingSearchStart_point(DescTran directionPoint, int vel, int distance, int timeout, int posSensorNum)
   
Zakończenie poszukiwania pozycji laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
   :linenos:

   /**
    * @brief  Zakończenie poszukiwania pozycji laserowej
    * @return Kod błędu
    */
    public int LaserTrackingSearchStop()

Konfiguracja IP lasera
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
   :linenos:

    /**
     * @brief Konfiguracja IP lasera
     * @param [in] ip Adres IP urządzenia peryferyjnego laserowego
     * @param [in] port Numer portu urządzenia peryferyjnego laserowego
     * @return Kod błędu
     */
    public int LaserTrackingSensorConfig(String ip, int port)

Konfiguracja okresu próbkowania urządzenia peryferyjnego laserowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Konfiguracja okresu próbkowania urządzenia peryferyjnego laserowego
     * @param [in] period Okres próbkowania urządzenia peryferyjnego laserowego jednostka ms
     * @return Kod błędu
     */
    public int LaserTrackingSensorSamplePeriod(int period)

Ładowanie sterownika urządzenia peryferyjnego laserowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Ładowanie sterownika urządzenia peryferyjnego laserowego
     * @param [in] type Typ protokołu sterownika urządzenia peryferyjnego laserowego 101-RuiNiu 102-ChuangXiang 103-QuanShi 104-TongZhou 105-AoTai
     * @return Kod błędu
     */
    public int LoadPosSensorDriver(int type)

Rozładowanie sterownika urządzenia peryferyjnego laserowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Rozładowanie sterownika urządzenia peryferyjnego laserowego
     * @return Kod błędu
     */
    public int UnLoadPosSensorDriver()

Rejestracja ścieżki spoiny laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Rejestracja ścieżki spoiny laserowej
     * @param [in] status 0-zatrzymaj rejestrację 1-śledzenie w czasie rzeczywistym 2-rozpocznij rejestrację
     * @param [in] delayTime Czas opóźnienia jednostka ms
     * @return Kod błędu
     */
    public int LaserSensorRecord1(int status, int delayTime)

Odtwarzanie ścieżki spoiny laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Odtwarzanie ścieżki spoiny laserowej
     * @param [in] delayTime Czas opóźnienia jednostka ms
     * @param [in] speed Prędkość jednostka%
     * @return Kod błędu
     */
    public int LaserSensorReplay(int delayTime, double speed)

Odtwarzanie śledzenia laserowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Odtwarzanie śledzenia laserowego
     * @return Kod błędu
     */
    public int MoveLTR()

Odtwarzanie ścieżki spoiny laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
    * @brief Odtwarzanie ścieżki spoiny laserowej
    * @param delayMode Tryb 0-czas opóźnienia 1-odległość opóźnienia
    * @param delayTime Czas opóźnienia jednostka ms
    * @param delayDisExAxisNum Numer osi rozszerzenia opóźnienia
    * @param delayDis Odległość opóźnienia jednostka mm
    * @param sensitivePara Współczynnik czułości kompensacji
    * @param trackMode Typ śledzenia punktowego. 0-ruch asynchroniczny osi rozszerzenia；1-robot
    * @param triggerMode Sposób wyzwalania śledzenia punktowego. 0-czas śledzenia；1-IO
    * @param runTime Czas śledzenia punktowego robota (s)
    * @param speed Prędkość jednostka%
    * @return Kod błędu
    */
    public int LaserSensorRecordandReplay(int delayMode, int delayTime, int delayDisExAxisNum, double delayDis, double sensitivePara, int trackMode, int triggerMode, double runTime, double speed)
    
Ruch do początku zapisu ścieżki spoiny
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Ruch do początku zapisu ścieżki spoiny
     * @param [in] moveType 0-PTP 1-LIN
     * @param [in] ovl Prędkość jednostka%
     * @return Kod błędu
     */
    public int MoveToLaserRecordStart(int moveType, double ovl)

Ruch do końca zapisu ścieżki spoiny
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Ruch do końca zapisu ścieżki spoiny
     * @param [in] moveType 0-PTP 1-LIN
     * @param [in] ovl Prędkość jednostka%
     * @return Kod błędu
     */
    public int MoveToLaserRecordEnd(int moveType, double ovl)

Ruch do punktu poszukiwanego przez czujnik laserowy
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Ruch do punktu poszukiwanego przez czujnik laserowy
     * @param [in] moveFlag Typ ruchu: 0-PTP；1-LIN
     * @param [in] ovl Współczynnik skalowania prędkości, 0-100
     * @param [in] dataFlag Wybór danych bufora spoiny: 0-wykonaj dane planowania；1-wykonaj dane zapisu
     * @param [in] plateType Typ blachy: 0-blacha falista；1-blacha trapezowa；2-blacha ogrodzeniowa；3-beczka；4-stal pancerzowa falista
     * @param [in] trackOffectType Typ przesunięcia czujnika laserowego: 0-bez przesunięcia；1-przesunięcie w układzie bazowym；2-przesunięcie w układzie narzędzia；3-przesunięcie surowych danych czujnika laserowego
     * @param [in] offset Wartość przesunięcia
     * @return Kod błędu
     */
    public int MoveToLaserSeamPos(int moveFlag, double ovl, int dataFlag, int plateType, int trackOffectType, DescPose offset)
    
Pobranie informacji o współrzędnych punktu poszukiwanego przez czujnik laserowy
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Pobranie informacji o współrzędnych punktu poszukiwanego przez czujnik laserowy
     * @param [in] trackOffectType Typ przesunięcia czujnika laserowego: 0-bez przesunięcia；1-przesunięcie w układzie bazowym；2-przesunięcie w układzie narzędzia；3-przesunięcie surowych danych czujnika laserowego
     * @param [in] offset Wartość przesunięcia
     * @param [out] jPos Pozycja przegubów [°]
     * @param [out] descPos Pozycja kartezjańska [mm]
     * @param [out] tool Układ narzędzia
     * @param [out] user Układ przedmiotu
     * @param [out] exaxis Pozycja osi rozszerzenia [mm]
     * @return Kod błędu
     */
    public int GetLaserSeamPos(int trackOffectType, DescPose offset, JointPos jPos, DescPose descPos, int[] tool, int[] user, ExaxisPos exaxis)

Przykład kodu konfiguracji parametrów i debugowania urządzenia peryferyjnego laserowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static void testLaserConfig(Robot robot)
    {
        robot.LaserTrackingSensorConfig("192.168.58.20", 5020);

        robot.LaserTrackingSensorSamplePeriod(20);

        robot.LoadPosSensorDriver(101);
        robot.LaserTrackingLaserOnOff(0,0);

        robot.Sleep(3000);

        robot.LaserTrackingLaserOnOff(1, 0);

        robot.CloseRPC();
    }

Przykład kodu skanowania i odtwarzania ścieżki laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static void testLaserRecordAndReplay(Robot robot)
    {
        // Przesłanie i załadowanie pliku protokołu otwartego
        robot.OpenLuaUpload("D://zUP/CtrlDev_laser_ruiniu-0117.lua");
        robot.Sleep(2000);
        robot.SetCtrlOpenLUAName(0, "CtrlDev_laser_ruiniu-0117.lua");
        robot.UnloadCtrlOpenLUA(0);
        robot.LoadCtrlOpenLUA(0);
        robot.Sleep(8000);

        for (int i=0;i<10;++i){
            JointPos startjointPos=new JointPos(56.205, -117.951, 141.872, -118.149, -94.217, -122.176);
            DescPose startdescPose=new DescPose(-97.552, -282.855, 26.675, 174.182, -1.338, -91.707);
            ExaxisPos exaxisPos=new ExaxisPos(0, 0, 0, 0);
            DescPose offdese=new DescPose(0, 0, 0, 0, 0, 0);
            robot.MoveL(startjointPos, startdescPose, 1, 0, 100, 100, 100, -1, 0,exaxisPos, 0, 0, offdese, 0,1, 1);

            robot.LaserSensorRecord1(2, 10);

            JointPos endjointPos=new JointPos(68.809, -87.100, 121.120, -127.233, -95.038, -109.555);
            DescPose enddescPose=new DescPose(-103.555, -464.234, 13.076, 174.179, -1.344, -91.709);
            robot.MoveL(endjointPos, enddescPose, 1, 0, 50, 100, 100, -1,0, exaxisPos, 0, 0, offdese, 0,1, 1);

            robot.LaserSensorRecord1(0, 10);

            robot.MoveToLaserRecordStart(1, 30);

            robot.LaserSensorReplay(10, 100);

            robot.MoveLTR();

            robot.LaserSensorRecord1(0, 10);
        }

        robot.CloseRPC();
    }

Przykład kodu poszukiwania pozycji laserowej i śledzenia w czasie rzeczywistym
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static void testLasertrack(Robot robot)
    {
        // Przesłanie i załadowanie pliku protokołu otwartego
        robot.OpenLuaUpload("D://zUP/CtrlDev_laser_ruiniu-0117.lua");
        robot.Sleep(2000);
        robot.SetCtrlOpenLUAName(0, "CtrlDev_laser_ruiniu-0117.lua");
        robot.UnloadCtrlOpenLUA(0);
        robot.LoadCtrlOpenLUA(0);
        robot.Sleep(8000);
        for(int i=0;i<10;++i){
            JointPos startjointPos=new JointPos(56.205, -117.951, 141.872, -118.149, -94.217, -122.176);
            DescPose startdescPose=new DescPose(-97.552, -282.855, 26.675, 174.182, -1.338, -91.707);
            ExaxisPos exaxisPos=new ExaxisPos(0, 0, 0, 0);
            DescPose offdese=new DescPose(0, 0, 0, 0, 0, 0);
            DescTran directionPoint=new DescTran();
            robot.MoveL(startjointPos, startdescPose, 1, 0, 100, 100, 100, -1, 0,exaxisPos, 0, 0, offdese, 0,1, 1);

            robot.LaserTrackingSearchStart_xyz(3, 100, 300, 1000, 3);
            robot.LaserTrackingSearchStop();

            // robot.GetRobotTeachingPoint(name, data);
            robot.MoveToLaserSeamPos(1, 30, 0, 0, 0, offdese);
            // printf("%f, %f, %f,%f, %f, %f,%f, %f, %f,%f, %f, %f\n", data[0], data[1], data[2], data[3], data[4], data[5], data[6], data[7], data[8], data[9], data[10], data[11]);

            robot.LaserTrackingTrackOnOff(1, 3);
            // robot.LaserTrackingTrackOn(3);
            JointPos endjointPos=new JointPos(68.809,-87.100,121.120,-127.233,-95.038,-109.555);
            DescPose enddescPose=new DescPose(-103.555,-464.234,13.076,174.179,-1.344,-91.709);
            robot.MoveL(endjointPos, enddescPose, 1, 0, 20, 100, 100, -1, 0,exaxisPos, 0, 0, offdese, 0,1, 1);

            robot.LaserTrackingTrackOnOff(0, 3);
            System.out.println("To jest " + (i+1) + " raz");
        }
        robot.CloseRPC();
    }

Przykład kodu śledzenia laserowego z osią rozszerzenia synchronicznie z robotem
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static void testLasertrackandExitAxis(Robot robot)
    {
        ExaxisPos startexaxisPos =new ExaxisPos( 0,0,0,0 );
        ExaxisPos seamexaxisPos = new ExaxisPos(-10,0,0,0 );
        ExaxisPos endexaxisPos = new ExaxisPos(-30, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0 );
        JointPos seamjointPos=new JointPos(0, 0, 0, 0, 0, 0);
        DescPose seamdescPose=new DescPose(0, 0, 0, 0, 0, 0);

        for(int i =0;i<10;++i) {
            // Ruch do punktu początkowego wymagającego poszukiwania pozycji
            JointPos startjointPos = new JointPos(58.337, -119.628, 146.037, -116.358, -92.224, -117.654);
            DescPose startdescPose = new DescPose(-53.375, -255.363, 0.919, 178.054, 1.077, -94.026);
            robot.ExtAxisSyncMoveJ(startjointPos, startdescPose, 1, 0, 100, 100, 100, startexaxisPos, -1, 0, offdese);

            System.out.println("11111");
            // Rozpoczęcie poszukiwania pozycji w kierunku -y
            int ret = robot.LaserTrackingSearchStart_xyz(3, 100, 300, 1000, 2);
            robot.LaserTrackingSearchStop();
            System.out.println("2222");
            int[] tool = new int[1];
            int[] user = new int[1];
            robot.GetLaserSeamPos(0, offdese, seamjointPos, seamdescPose, tool, user, startexaxisPos);
            System.out.println(seamjointPos.J1 + ", " + seamjointPos.J2 + ", " +
                    seamjointPos.J3 + ", " + seamjointPos.J4 + ", " +
                    seamjointPos.J5 + ", " + seamjointPos.J6 + ", " +
                    seamdescPose.tran.x + ", " + seamdescPose.tran.y + ", " +
                    seamdescPose.tran.z + ", " + seamdescPose.rpy.rx + ", " +
                    seamdescPose.rpy.ry + ", " + seamdescPose.rpy.rz);
            // Jeśli poszukiwanie pozycji zakończone sukcesem
            if (ret == 0) {
                // Synchroniczny ruch robota i osi rozszerzenia do punktu poszukiwanego
                robot.ExtAxisSyncMoveJ(seamjointPos, seamdescPose, 1, 0, 100, 100, 100, seamexaxisPos, -1, 0, offdese);

                // Rozpoczęcie śledzenia laserowego wzdłuż punktu poszukiwanego i synchronicznego ruchu z osią rozszerzenia
                System.out.println("3333");
                robot.LaserTrackingTrackOnOff(1, 2);
                JointPos endjointPos = new JointPos(70.580, -90.918, 126.593, -125.154, -92.162, -105.403);
                DescPose enddescPose = new DescPose(-53.375, -419.020, 0.920, 178.054, 1.076, -94.026);
                robot.ExtAxisSyncMoveL(endjointPos, enddescPose, 1, 0, 20, 100, 100, -1, endexaxisPos, 0, offdese);
                ;
                // Zatrzymanie śledzenia
                robot.LaserTrackingTrackOnOff(0, 2);
                System.out.println("44444");
            }
            System.out.println("Aktualna liczba uruchomień: "+i);
        }
        robot.CloseRPC();
    }

Interfejs SDK włączania/wyłączania funkcji przezroczystej transmisji końcowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Włączenie ogólnej funkcji przezroczystej transmisji końcowej
    * @param włączenie, 0-wyłącz, 1-włącz
    * @return Kod błędu
    */
    public int SetAxleGenComEnable(int mode)

Interfejs SDK wysyłania i odbierania danych aperiodycznych funkcji przezroczystej transmisji końcowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Wysłanie danych aperiodycznych przez końcówkę i oczekiwanie na odpowiedź
    * @param lenSnd Długość wysyłania
    * @param sndBuff Dane wysyłane
    * @param lenRcv Wybór długości odbioru
    * @param [out] rcvData Dane odpowiedzi
    * @return Kod błędu
    */
    public int SndRcvAxleGenComCmdData(int lenSnd, int[] sndBuff, int lenRcv, int[] rcvData)
    
Przykład kodu komunikacji danych aperiodycznych głowicy moxibuscyjnej Beiyikang w oparciu o funkcję przezroczystej transmisji końcowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static void testAxleGenCom(Robot robot) {
    int[] led_on = {0xAB, 0xBA, 0x12, 0x01, 0x01, 0x79};
    int[] led_off = {0xAB, 0xBA, 0x12, 0x01, 0x00, 0x78};
    int[] version = {0xAB, 0xBA, 0x11, 0x00, 0x76};
    int[] state = {0xAB, 0xBA, 0x1B, 0x01, 0xAA, 0x2B};

    int[] rcvdata = new int[16];
    int ret = 0;
    int cnt = 1;

    JointPos p1Joint = new JointPos(88.708, -86.178, 140.989, -141.825, -89.162, -49.879);
    DescPose p1Desc = new DescPose(188.007, -377.850, 260.207, 178.715, 2.823, -131.466);

    JointPos p2Joint = new JointPos(112.131, -75.554, 126.989, -139.027, -88.044, -26.477);
    DescPose p2Desc = new DescPose(368.003, -377.848, 260.211, 178.715, 2.823, -131.465);

    ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
    DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

    // Włączenie funkcji przezroczystej transmisji końcowej
    robot.SetAxleGenComEnable(1);
    robot.SetAxleLuaEnable(1);

    while (cnt <= 10000) {
        // Odczyt numeru wersji
        ret = robot.SndRcvAxleGenComCmdData(5, version, 10, rcvdata);
        if (ret == 0) {
            System.out.printf(" hard version : %d,hard code:%d, soft version:%d %d, soft code:%d \n",
                    rcvdata[4], rcvdata[5], rcvdata[6], rcvdata[7], rcvdata[8]);
        } else {
            System.out.println("SndRcvAxleGenComCmdData version fail: " + ret);
            break;
        }
        robot.Sleep(1000);

        // Odczyt stanu obecności głowicy moxibuscyjnej
        ret = robot.SndRcvAxleGenComCmdData(6, state, 6, rcvdata);
        if (ret == 0) {
            System.out.printf(" state : %d \n", rcvdata[4]);
        }
        robot.Sleep(1000);

        // Włączenie lasera głowicy moxibuscyjnej
        ret = robot.SndRcvAxleGenComCmdData(6, led_on, 6, rcvdata);
        if (ret == 0) {
            System.out.printf("led on rcv data is: %d, %d, %d, %d, %d, %d\n",
                    rcvdata[0], rcvdata[1], rcvdata[2], rcvdata[3], rcvdata[4], rcvdata[5]);
        }
        robot.MoveJ(p1Joint, p1Desc, 0, 0, 100.0, 100.0, 100.0, exaxisPos, -1.0, 0, offdese);
        robot.Sleep(4000);

        // Wyłączenie lasera głowicy moxibuscyjnej
        ret = robot.SndRcvAxleGenComCmdData(6, led_off, 6, rcvdata);
        if (ret == 0) {
            System.out.printf("led off rcv data is: %d, %d, %d, %d, %d, %d \n",
                    rcvdata[0], rcvdata[1], rcvdata[2], rcvdata[3], rcvdata[4], rcvdata[5]);
        }
        robot.MoveJ(p2Joint, p2Desc, 0, 0, 100.0, 100.0, 100.0, exaxisPos, -1.0, 0, offdese);
        robot.Sleep(1000);

        System.out.println("***********************complete No. " + cnt + " SDK test*****************************");
        cnt++;
    }
    }  
    
Pobranie pliku LUA protokołu otwartego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Pobranie pliku LUA protokołu otwartego
    * @param fileName Nazwa pliku protokołu otwartego „CtrlDev_XXX.lua”
    * @param savePath Ścieżka zapisu pliku protokołu otwartego
    * @return Kod błędu
    */
    public int OpenLuaDownload(string fileName, string savePath)

Usunięcie pliku LUA protokołu otwartego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Usunięcie pliku LUA protokołu otwartego
    * @param [in] fileName Nazwa pliku lua protokołu otwartego do usunięcia „CtrlDev_XXX.lua”
    * @return Kod błędu
    */
    public int OpenLuaDelete(string fileName)
        
Usunięcie wszystkich plików LUA protokołu otwartego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Usunięcie wszystkich plików LUA protokołu otwartego
    * @return Kod błędu
    */
    public int AllOpenLuaDelete()

Przykład kodu przesyłania, pobierania i usuwania protokołu otwartego urządzeń peryferyjnych kontrolera
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    public static int TestCtrlOpenLuaOperate(Robot robot) {
        int rtn;
        rtn = robot.OpenLuaUpload("D://zUP/openlua/CtrlDev_WELDING_A.lua");
        System.out.println("OpenLuaUpload rtn is " + rtn);
        rtn = robot.OpenLuaUpload("D://zUP/openlua/CtrlDev_SWDPOLISH.lua");
        System.out.println("OpenLuaUpload rtn is " + rtn);
        rtn = robot.OpenLuaDownload("CtrlDev_WELDING_A.lua", "D://zDOWN/");
        System.out.println("OpenLuaDownload rtn is " + rtn);
        rtn = robot.OpenLuaDownload("CtrlDev_SWDPOLISH.lua", "D://zDOWN/");
        System.out.println("OpenLuaDownload rtn is " + rtn);

        rtn = robot.SetCtrlOpenLUAName(0, "CtrlDev_WELDING_A.lua");
        System.out.println("SetCtrlOpenLUAName rtn is " + rtn);
        rtn = robot.SetCtrlOpenLUAName(1, "CtrlDev_SWDPOLISH.lua");
        System.out.println("SetCtrlOpenLUAName rtn is " + rtn);

        String[] names = new String[4];
        rtn = robot.GetCtrlOpenLUAName(names);
        System.out.println("GetCtrlOpenLUAName rtn is " + rtn + ", names: " +
                names[0] + ", " + names[1] + ", " + names[2] + ", " + names[3]);

        rtn = robot.LoadCtrlOpenLUA(1);
        System.out.println("LoadCtrlOpenLUA rtn is " + rtn);
        robot.Sleep(2000);
        rtn = robot.UnloadCtrlOpenLUA(1);
        System.out.println("UnloadCtrlOpenLUA rtn is " + rtn);

        rtn = robot.OpenLuaDelete("CtrlDev_WELDING_A.lua");
        System.out.println("OpenLuaDelete rtn is " + rtn);
        rtn = robot.AllOpenLuaDelete();
        System.out.println("AllOpenLuaDelete rtn is " + rtn);

        robot.Sleep(1000);
        return 0;
    }