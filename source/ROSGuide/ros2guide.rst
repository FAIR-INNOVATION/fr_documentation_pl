Przedmowa
+++++++++
fairino_hardware to interfejs API opracowany przez FAIRINO dla robota współpracującego w oparciu o ROS2, mający na celu umożliwienie użytkownikom początkującym łatwiejszego korzystania z SDK FAIRINO. Dzięki plikowi konfiguracyjnemu parametrów, który umożliwia konfigurację domyślnych parametrów, można dostosować się do różnych wymagań klienta.

fairino_hardware
++++++++++++++++
W tym rozdziale opisano, jak skonfigurować środowisko uruchomieniowe aplikacji.

Instalacja podstawowego środowiska
----------------------------------

Zaleca się używanie systemu Ubuntu 22.04 LTS (Jammy). Po zakończeniu instalacji systemu należy zainstalować ROS2. Zalecana wersja to ros2-humble. Pełną instrukcję instalacji ROS2 można znaleźć pod adresem: https://docs.ros.org/en/humble/index.html.
Przed właściwą kompilacją fairino_hardware należy również zainstalować oficjalny pakiet ros2_control. Pełną instrukcję instalacji ros2_control można znaleźć pod adresem: https://control.ros.org/humble/index.html. Oficjalna strona oferuje dwa sposoby instalacji ros2_control: instalację za pomocą poleceń oraz instalację poprzez kompilację źródeł. Ponieważ instalacja za pomocą poleceń może prowadzić do niepełnej instalacji pakietów funkcjonalnych, zaleca się użycie metody kompilacji źródeł.

Poniżej szczegółowo opisano proces instalacji ROS2 (humble):

1. Otwórz okno shell

.. code-block:: shell
    :linenos:

    locale  # check for UTF-8

    sudo apt update && sudo apt install locales
    sudo locale-gen en_US en_US.UTF-8
    sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
    export LANG=en_US.UTF-8

    locale  # verify settings

2. Ustaw źródła

.. code-block:: shell
    :linenos:
    
    sudo apt install software-properties-common
    sudo add-apt-repository universe

    sudo apt update && sudo apt install curl -y
    sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg

    echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null

3. Zainstaluj ROS2

.. code-block:: shell
    :linenos:

    sudo apt update
    sudo apt upgrade
    sudo apt install ros-humble-desktop

4. Na koniec zainstaluj narzędzia deweloperskie

.. code-block:: shell
    :linenos:

    sudo apt install ros-dev-tools

Poniżej szczegółowo opisano proces instalacji ros2_control:

1. Najpierw source zasobów ROS2

.. code-block:: shell
    :linenos:

    source /opt/ros/humble/setup.bash

2. Utwórz obszar roboczy ros2_control i pobierz zasoby

.. code-block:: shell
    :linenos:

    mkdir -p ~/ros2_control_ws/src
    cd ~/ros2_control_ws/
    wget https://raw.githubusercontent.com/ros-controls/ros2_control_ci/master/ros_controls.$ROS_DISTRO.repos
    vcs import src < ros_controls.$ROS_DISTRO.repos

3. Zainstaluj pakiety zależności

.. code-block:: shell
    :linenos:

    rosdep update --rosdistro=$ROS_DISTRO
    sudo apt-get update
    rosdep install --from-paths src --ignore-src -r -y

4. Skompiluj ros2_control

.. code-block:: shell
    :linenos:

    . /opt/ros/${ROS_DISTRO}/setup.sh
    colcon build --symlink-install

Kompilacja i budowanie fairino_hardware
---------------------------------------

1. Utwórz obszar roboczy colcon
fairino_hardware składa się z dwóch pakietów funkcjonalnych: pakietu funkcjonalnego niestandardowych struktur danych fairino_msgs oraz pakietu funkcjonalnego głównego programu fairino_hardware. Po zainstalowaniu podstawowego środowiska, najpierw utwórz obszar roboczy colcon, na przykład:

Najpierw należy source zasobów ROS2 i ros2_control

.. code-block:: shell
    :linenos:

    source /opt/ros/humble/setup.bash
    source ~/ros2_control_ws/install/setup.bash

Następnie utwórz obszar roboczy

.. code-block:: shell
    :linenos:

    cd ~/
    mkdir -p ros2_ws/src

2. Skompiluj pakiety funkcjonalne
Skopiuj kod pakietu instalacyjnego do katalogu ros2_ws/src, a następnie w katalogu ros2_ws uruchom następujące polecenia:

.. code-block:: shell
    :linenos:

    source ~/ros2_control_ws/install/setup.bash

Po zakończeniu powyższego polecenia uruchom następujące polecenie:

.. code-block:: shell
    :linenos:

    colcon build --packages-select fairino_msgs

Po zakończeniu kompilacji poprzedniego polecenia, użyj następującego polecenia do kompilacji fairino_hardware:

.. code-block::  shell
    :linenos:

    colcon build --packages-select fairino_hardware

Szybki start
++++++++++++

Proces uruchamiania
-------------------
W terminalu Ubuntu wpisz:

.. code-block::  shell
    :linenos:

    cd ros2_ws
    source install/setup.bash
    ros2 run fairino_hardware ros2_cmd_server

.. image:: img/fr_ros2_001.png
    :width: 6in
    :align: center

Proces przeglądania informacji zwrotnej o stanie ramienia mechanicznego
-----------------------------------------------------------------------
Informacja zwrotna o stanie ramienia mechanicznego jest publikowana przez topic. Użytkownik może zaobserwować odświeżanie danych stanu za pomocą wbudowanych poleceń ros2, może również napisać program w celu pobrania tych danych. Poniżej przedstawiono, jak zaobserwować dane stanu ramienia mechanicznego za pomocą poleceń ros2.

W terminalu Ubuntu wpisz:

.. code-block:: shell
    :linenos:

    cd ros2_ws
    source install/setup.bash
    ros2 topic echo /nonrt_state_data

W oknie terminalu można zobaczyć ciągle odświeżające się dane stanu, jak pokazano na poniższym rysunku.

.. image:: img/fr_ros2_002.png
    :width: 6in
    :align: center

Proces wysyłania instrukcji
---------------------------
W terminalu Ubuntu wpisz:

.. code-block:: shell
    :linenos:

    cd ros2_ws
    source install/setup.bash
    rqt

Po wykonaniu powyższych poleceń zostanie wywołany interfejs GUI rqt, jak pokazano na poniższym rysunku.

.. image:: img/fr_ros2_003.png
    :width: 6in
    :align: center

W interfejsie GUI wybierz plugins -> service -> service caller, aby wywołać następujący interfejs. Wybierz usługę /fairino_remote_command_service. W polu expression wprowadź ciąg instrukcji i kliknij Call. W dolnym oknie dialogowym pojawi się odpowiedź.

.. image:: img/fr_ros2_004.png
    :width: 6in
    :align: center

.. important:: 

   - Opis zasad dotyczących wprowadzanego ciągu znaków:

   Program wewnętrznie filtruje formę wprowadzonego ciągu znaków. Format wprowadzanej funkcji musi mieć postać [nazwa_funkcji](), a ciąg parametrów w nawiasach okrągłych może składać się wyłącznie z liter, cyfr, przecinków i znaku minus. Pojawienie się innych znaków lub spowoduje błąd.

   - Opis wartości zwrotnych instrukcji:

   Z wyjątkiem instrukcji GET, która zwraca ciąg znaków, wartości zwrotne pozostałych funkcji są typu int. Zazwyczaj 0 oznacza błąd, 1 oznacza prawidłowe wykonanie. W przypadku pojawienia się innych wartości, należy odnieść się do kodów błędów zdefiniowanych w SDK xmlrpc.

Proces modyfikacji parametrów
-----------------------------
Ponieważ uproszczone SDK jest ulepszeniem natywnego interfejsu SDK, uproszczenie polega na nadaniu pewnym parametrom wartości domyślnych. W praktyce mogą jednak wystąpić sytuacje, w których domyślne parametry nie spełniają wymagań. W takim przypadku można zmodyfikować wartości odpowiednich parametrów domyślnych, a następnie załadować je do węzła.

W plikach źródłowych znajduje się plik parametrów fairino_remotecmdinterface_para.yaml. Parametry w tym pliku są wstępnie ustawionymi wartościami domyślnymi, służącymi do uproszczenia parametrów wejściowych instrukcji. Można je modyfikować zgodnie z własnymi potrzebami, a następnie użyć polecenia do dynamicznej modyfikacji parametrów: ros2 param load fr_command_server ~/ros2_ws/src/fairino_hardware/fairino_remotecmdinterface_para.yaml.

Opis API
++++++++

.. code-block:: c++
    :linenos:

    /*
    Opis funkcji: Zapisuje informację o punkcie stawowym
    id - numer ID zapisywanego punktu, zaczynając od 1. Uwaga: ten ID jest niezależny od ID punktu CARTPoint
    double j1-j6 - pozycje 6 stawów, jednostka: stopnie
    */
    int JNTPoint(int id, double j1, double j2, double j3, double j4, double j5, double j6)
    // Przykład
    JNTPoint(1,10,11,12,13,14,15)

    /*
    Opis funkcji: Zapisuje informację o punkcie kartezjańskim
    id - numer ID zapisywanego punktu, zaczynając od 1. Uwaga: ten ID jest niezależny od ID punktu JNTPoint
    double x,y,z,rx,ry,rz - informacja o punkcie kartezjańskim, jednostka pozycji: mm, jednostka kąta: stopnie
    */
    int CARTPoint(int id, double x,y,z,rx,ry,rz)//Zapisuje punkt w przestrzeni kartezjańskiej
    // Przykład
    CARTPoint(1,100,110,200,0,0,0)

    /*
    Opis funkcji: Pobiera informację o punkcie stawowym lub kartezjańskim o określonym numerze
    string name - 'JNT' lub 'CART', JNT oznacza pobranie informacji o punkcie stawowym, 'CART' oznacza pobranie informacji o punkcie kartezjańskim
    int id - ID punktu, zaczynając od 1
    */
    string GET(string name, int id)//Pobiera treść punktu o odpowiednim numerze ID, name może być JNT lub CART
    // Przykład
    GET(JNT,1)

    /*
    Opis funkcji: Przełącznik trybu przeciągania
    uint8_t state - 1-włącz tryb przeciągania, 0-wyłącz tryb przeciągania
    */
    int DragTeachSwitch(uint8_t state)
    // Przykład
    DragTeachSwitch(0)

    /*
    Opis funkcji: Przełącznik załączenia ramienia mechanicznego
    uint8_t state - 1-załącz ramię mechaniczne, 0-odłącz ramię mechaniczne
    */
    int RobotEnable(uint8_t state)
    // Przykład
    RobotEnable(1)

    /*
    Opis funkcji: Przełączanie trybu
    uint8_t state - 1-tryb ręczny, 0-tryb automatyczny
    */
    int Mode(uint8_t state)
    // Przykład
    Mode(1)

    /*
    Opis funkcji: Ustawia prędkość ramienia mechanicznego w bieżącym trybie
    float vel - procent prędkości, zakres 1-100
    */
    int SetSpeed(float vel)
    // Przykład
    SetSpeed(10)

    /*
    Opis funkcji: Ustawia i ładuje układ współrzędnych narzędzia o określonym numerze
    int id - numer układu współrzędnych narzędzia, zakres 1-15
    float x,y,z,rx,ry,rz - informacja o przesunięciu układu współrzędnych narzędzia
    */
    int SetToolCoord(int id, float x,float y, float z,float rx,float ry,float rz)
    // Przykład
    SetToolCoord(1,0,0,0,0,0,0)

    /*
    Opis funkcji: Ustawia listę układów współrzędnych narzędzia
    int id - numer układu współrzędnych narzędzia, zakres 1-15
    float x,y,z,rx,ry,rz - informacja o przesunięciu układu współrzędnych narzędzia
    */
    int SetToolList(int id, float x,float y, float z,float rx,float ry,float rz );
    // Przykład
    SetToolList(1,0,0,0,0,0,0)

    /*
    Opis funkcji: Ustawia zewnętrzny układ współrzędnych narzędzia
    int id - numer układu współrzędnych narzędzia, zakres 1-15
    float x,y,z,rx,ry,rz - informacja o przesunięciu zewnętrznego układu współrzędnych narzędzia
    */
    int SetExToolCoord(int id, float x,float y, float z,float rx,float ry,float rz);	
    // Przykład
    SetExToolCoord(1,0,0,0,0,0,0)

    /*
    Opis funkcji: Ustawia listę zewnętrznych układów współrzędnych narzędzia
    int id - numer układu współrzędnych narzędzia, zakres 1-15
    float x,y,z,rx,ry,rz - informacja o przesunięciu zewnętrznego układu współrzędnych narzędzia
    */
    int SetExToolList(int id, float x,float y, float z,float rx,float ry,float rz);
    // Przykład
    SetExToolList(1,0,0,0,0,0,0)

    /*
    Opis funkcji: Ustawia układ współrzędnych przedmiotu
    int id - numer układu współrzędnych przedmiotu, zakres 1-15
    float x,y,z,rx,ry,rz - informacja o przesunięciu układu współrzędnych przedmiotu
    */
    int SetWObjCoord(int id, float x,float y, float z,float rx,float ry,float rz);
    // Przykład
    SetWObjCoord(1,0,0,0,0,0,0)

    /*
    Opis funkcji: Ustawia listę układów współrzędnych przedmiotu
    int id - numer układu współrzędnych przedmiotu, zakres 1-15
    float x,y,z,rx,ry,rz - informacja o przesunięciu układu współrzędnych przedmiotu
    */
    int SetWObjList(int id, float x,float y, float z,float rx,float ry,float rz);
    // Przykład
    SetWObjList(1,0,0,0,0,0,0)

    /*
    Opis funkcji: Ustawia masę ładunku końcowego
    float weight - masa ładunku, jednostka kg
    */
    int SetLoadWeight(float weight);
    // Przykład
    SetLoadWeight(3.5)

    /*
    Opis funkcji: Ustawia współrzędne środka ciężkości ładunku końcowego
    float x,y,z - współrzędne środka ciężkości, jednostka mm
    */
    int SetLoadCoord(float x,float y,float z);
    // Przykład
    SetLoadCoord(10,20,30)

    /*
    Opis funkcji: Ustawia sposób instalacji robota
    uint8_t install - sposób instalacji, 0-instalacja normalna, 1-instalacja boczna, 2-instalacja odwrócona
    */
    int SetRobotInstallPos(uint8_t install);
    // Przykład
    SetRobotInstallPos(0)

    /*
    Opis funkcji: Ustawia kąt instalacji robota, instalacja swobodna
    double yangle - kąt nachylenia
    double zangle - kąt obrotu
    */
    int SetRobotInstallAngle(double yangle,double zangle);
    // Przykład
    SetRobotInstallAngle(90,0)


    // Konfiguracja bezpieczeństwa
    /*
    Opis funkcji: Ustawia poziom kolizji robota
    float level1-level6 - poziom kolizji dla osi 1-6, zakres 1-10
    */
    int SetAnticollision(float level1, float level2, float level3, float level4, float level5, folat level6);
    // Przykład
    SetAnticollision(1,1,1,1,1,1)

    /*
	 * @brief  Ustawia strategię po kolizji
	 * @param  [in] strategy  0-zatrzymaj z błędem, 1-kontynuuj działanie
	 * @param  [in] safeTime  Czas bezpiecznego zatrzymania [1000 - 2000] ms
	 * @param  [in] safeDistance  Odległość bezpiecznego zatrzymania [1-150] mm
	 * @param  [in] safeVel  Prędkość bezpieczeństwa [50-250] mm/s
	 * @param  [in] safetyMargin  Współczynnik bezpieczeństwa j1-j6 [1-10]
	 * @return  Kod błędu
    */
	int SetCollisionStrategy(int strategy, int safeTime, int safeDistance, int safeVel, int safetyMargin[])
    // Przykład
    SetCollisionStrategy(1)

    /*
	 * @brief Ustawia metodę wykrywania kolizji robota
	 * @param [in] method Metoda wykrywania kolizji: 0-tryb prądowy; 1-podwójny enkoder; 2-tryb prądowy i podwójny enkoder włączone jednocześnie
     * @param [in] thresholdMode Sposób progu poziomu kolizji; 0-stały próg poziomu kolizji; 1-niestandardowy próg wykrywania kolizji
	 * @return Kod błędu
    */
	int SetCollisionDetectionMethod(int method, int thresholdMode);
    // Przykład
    SetCollisionDetectionMethod(0,0)


    /*
	 * @brief Ustawia włączanie/wyłączanie wykrywania kolizji w stanie spoczynku
	 * @param  [in] status 0-wyłączone; 1-włączone
	 * @return Kod błędu
    */
	int SetStaticCollisionOnOff(int status);
    // Przykład
    SetStaticCollisionOnOff(1)



    /*
	 * @brief Wykrywanie momentu obrotowego i mocy stawu
	 * @param  [in] status 0-wyłączone; 1-włączone
	 * @param  [in] power Ustawiona maksymalna moc (W)
	 * @return Kod błędu
    */
	int SetPowerLimit(int status, double power);
    //Przykład
    SetPowerLimit(1,100)

    /*
	 * @brief  Konfiguruje czujnik siły
	 * @param  [in] company   Producent czujnika siły, 17-Kunwei Technology, 19-Chińskie Akademia Technologii Kosmicznych, 20-ATI sensor, 21-Zhongke Midian, 22-Weihang Minxin, 23-NBIT, 24-Xinjingcheng (XJC), 26-NSR
	 * @param  [in] device   Numer urządzenia, Kunwei(0-KWR75B), Chińska Akademia Technologii Kosmicznych(0-MCS6A-200-4), ATI(0-AXIA80-M8), Zhongke Midian(0-MST2010), Weihang Minxin(0-WHC6L-YB-10A), NBIT(0-XLH93003ACS), Xinjingcheng XJC(0-XJC-6F-D82), NSR(0-NSR-FTSensorA)
	 * @param  [in] softvesion   Numer wersji oprogramowania, tymczasowo nieużywane, domyślnie 0
	 * @param  [in] bus  Pozycja magistrali, na której zawieszono urządzenie, tymczasowo nieużywane, domyślnie 0
	 * @return  Kod błędu
    */
	int FT_SetConfig(int company, int device, int softvesion, int bus);
    // Przykład
    FT_SetConfig(0,1,0,0)



    /*
	 * @brief  Pobiera konfigurację czujnika siły
	 * @param  [out] company   Producent czujnika siły, do ustalenia
	 * @param  [out] device   Numer urządzenia, tymczasowo nieużywane, domyślnie 0
	 * @param  [out] softvesion   Numer wersji oprogramowania, tymczasowo nieużywane, domyślnie 0
	 * @param  [out] bus  Pozycja magistrali, na której zawieszono urządzenie, tymczasowo nieużywane, domyślnie 0
	 * @return  Kod błędu
    */
	int FT_GetConfig(int *company, int *device, int *softvesion, int *bus);
    // Przykład
    FT_GetConfig()


    /*
	 * @brief  Aktywacja czujnika siły
	 * @param  [in] act  0-reset, 1-aktywacja
	 * @return  Kod błędu
    */
	int FT_Activate(uint8_t act);
    // Przykład
    FT_Activate(1)


    /*
	 * @brief  Zerowanie czujnika siły
	 * @param  [in] act  0-usunięcie zera, 1-korekta zera
	 * @return  Kod błędu
    */
	int FT_SetZero(uint8_t act);
    // Przykład
    FT_SetZero(1)

    /*
	 * @brief  Ochrona przed kolizją
	 * @param  [in] flag 0-wyłącz ochronę przed kolizją, 1-włącz ochronę przed kolizją
	 * @param  [in] sensor_id Numer czujnika siły
	 * @param  [in] select  Wybór, czy sześć stopni swobody ma wykrywać kolizję, 0-nie wykrywa, 1-wykrywa
	 * @param  [in] ft  Siła/moment kolizji, fx, fy, fz, tx, ty, tz
	 * @param  [in] max_threshold Maksymalny próg
	 * @param  [in] min_threshold Minimalny próg
	 * @note   Zakres wykrywania siły/momentu: (ft - min_threshold, ft + max_threshold)
	 * @return  Kod błędu
    */
	int FT_Guard(uint8_t flag, int sensor_id, uint8_t select[6], ForceTorque *ft, float max_threshold[6], float min_threshold[6]);
    // Przykład
    FT_Guard(1,1,0,0,1,0,0,0,0,0,100,0,0,0,0,0,200,0,0,0,0,0,50,0,0,0)


    /*
	 * @brief  Sterowanie stałą siłą
	 * @param  [in] flag 0-wyłącz sterowanie stałą siłą, 1-włącz sterowanie stałą siłą
	 * @param  [in] sensor_id Numer czujnika siły
	 * @param  [in] select  Wybór, czy sześć stopni swobody ma wykrywać kolizję, 0-nie wykrywa, 1-wykrywa
	 * @param  [in] ft  Siła/moment kolizji, fx, fy, fz, tx, ty, tz
	 * @param  [in] ft_pid Parametry pid siły, parametry pid momentu
	 * @param  [in] adj_sign Sterowanie uruchamianiem/zatrzymywaniem adaptacji, 0-wyłączone, 1-włączone
	 * @param  [in] ILC_sign Sterowanie uruchamianiem/zatrzymywaniem ILC, 0-zatrzymaj, 1-trening, 2-praktyka
	 * @param  [in] max_dis Maksymalna odległość regulacji, jednostka mm
	 * @param  [in] max_ang Maksymalny kąt regulacji, jednostka deg
	 * @param  [in] filter_Sign Znacznik włączenia filtrowania 0-wył.; 1-wł., domyślnie wyłączone
     * @param  [in] posAdapt_sign Znacznik włączenia zgodności orientacji 0-wył.; 1-wł., domyślnie wyłączone
     * @param  [in] isNoBlock Znacznik blokowania, 0-blokujące; 1-nieblokujące
	 * @return  Kod błędu
    */
	int FT_Control(uint8_t flag, int sensor_id, uint8_t select[6], ForceTorque *ft, float ft_pid[6], uint8_t adj_sign, uint8_t ILC_sign, float max_dis, float max_ang, int filter_Sign = 0, int posAdapt_sign = 0, int isNoBlock = 0);
    // Przykład
    FT_Control(1,1,0,0,1,0,0,0,0,0,-10,0,0,0,0.0005,0,0,0,0,0,0,0,100,10,0,0,0) 


    /*
	 * @brief  Włączenie sterowania podatnego
	 * @param  [in] p Współczynnik regulacji pozycji lub współczynnik podatności
	 * @param  [in] force Próg siły włączenia podatności, jednostka N
	 * @return  Kod błędu
    */
	int FT_ComplianceStart(float p, float force);
    // Przykład
    FT_ComplianceStart(0.005,20)


    /**
	 * @brief  Wyłączenie sterowania podatnego
	 * @return  Kod błędu
    */
	int FT_ComplianceStop();
    // Przykład
    FT_ComplianceStop()

    /*
    Opis funkcji: Ustawia dodatni limit, uwaga: ustawiona wartość musi mieścić się w zakresie twardego limitu
    float limit1-limit6 - wartości limitu dla 6 stawów
    */
    int SetLimitPositive(float limit1, float limit2, float limit3, float limit4, float limit5, float limit6);
    // Przykład
    SetLimitPositive(100,90,90,90,90,90)

    /*
    Opis funkcji: Ustawia ujemny limit, uwaga: ustawiona wartość musi mieścić się w zakresie twardego limitu
    float limit1-limit6 - wartości limitu dla 6 stawów
    */
    int SetLimitNegative(float limit1, float limit2, float limit3, float limit4, float limit5, float limit6);
    // Przykład
    SetLimitNegative(-100,-90,-90,-90,-90,-90)

    /*
    Opis funkcji: Czyszczenie stanu błędu
    */
    int ResetAllError();

    /*
    Opis funkcji: Przełącznik kompensacji tarcia stawów
    uint8_t state - 0-wył., 1-wł.
    */
    int FrictionCompensationOnOff(uint8_t state);
    // Przykład
    FrictionCompensationOnOff(1)

    /*
    Opis funkcji: Ustawia współczynnik kompensacji tarcia stawów - instalacja normalna
    float coeff1-coeff6 - współczynniki kompensacji dla 6 stawów, zakres 0-1
    */
    int SetFrictionValue_level(float coeff1,float coeff1,float coeff3,float coeff4,float coeff5,float coeff6);
    // Przykład
    SetFrictionValue_level(1,1,1,1,1,1)

    /*
    Opis funkcji: Ustawia współczynnik kompensacji tarcia stawów - instalacja boczna
    float coeff1-coeff6 - współczynniki kompensacji dla 6 stawów, zakres 0-1
    */
    int SetFrictionValue_wall(float coeff1,float coeff1,float coeff3,float coeff4,float coeff5,float coeff6);
    // Przykład
    SetFrictionValue_wall(0.5,0.5,0.5,0.5,0.5,0.5)

    /*
    Opis funkcji: Ustawia współczynnik kompensacji tarcia stawów - instalacja odwrócona
    float coeff1-coeff6 - współczynniki kompensacji dla 6 stawów, zakres 0-1
    */
    int SetFrictionValue_ceiling(float coeff1,float coeff1,float coeff3,float coeff4,float coeff5,float coeff6);
    // Przykład
    SetFrictionValue_ceiling(0.5,0.5,0.5,0.5,0.5,0.5)


    // Sterowanie urządzeniami peryferyjnymi
    /*
    Opis funkcji: Aktywacja chwytaka
    int index - numer chwytaka
    uint8_t act - 0-reset, 1-aktywacja
    */
    int ActGripper(int index,uint8_t act);
    // Przykład
    ActGripper(1,1)

    /*
    Opis funkcji: Sterowanie chwytakiem
    int index - numer chwytaka
    int pos - procent pozycji, zakres 0-100
    */
    int MoveGripper(int index,int pos);
    // Przykład
    MoveGripper(1,10)


    // Sterowanie I/O
    /*
    Opis funkcji: Ustawia wyjście cyfrowe skrzynki sterowniczej
    int id - numer I/O, zakres 0-15
    uint8_t status - 0-wył., 1-wł.
    */
    int SetDO(int id,uint8_t status);
    // Przykład
    SetDO(1,1)

    /*
    Opis funkcji: Ustawia wyjście cyfrowe narzędzia
    int id - numer I/O, zakres 0-1
    uint8_t status - 0-wył., 1-wł.
    */
    int SetToolDO(int id,uint8_t status);
    // Przykład
    SetToolDO(0,1)

    /*
    Opis funkcji: Ustawia wyjście analogowe skrzynki sterowniczej
    int id - numer I/O, zakres 0-1
    float value - procent wartości prądu lub napięcia, zakres 0-100
    */
    int SetAO(int id,float value);
    // Przykład
    SetAO(1,100)

    /*
    Opis funkcji: Ustawia wyjście analogowe narzędzia
    int id - numer I/O, zakres 0
    float value - procent wartości prądu lub napięcia, zakres 0-100
    */
    int SetToolAO(int id,float value);
    // Przykład
    SetToolAO(0,100)


    // Instrukcje ruchu
    /*
    Opis funkcji: Punktowanie robota
    uint8_t ref - 0-punktowanie stawów, 2-punktowanie w podstawowym układzie współrzędnych, 4-punktowanie w układzie współrzędnych narzędzia, 8-punktowanie w układzie współrzędnych przedmiotu
    uint8_t nb - 1-staw 1 (lub oś x), 2-staw 2 (lub oś y), 3-staw 3 (lub oś z), 4-staw 4 (lub obrót wokół osi x), 5-staw 5 (lub obrót wokół osi y), 6-staw 6 (lub obrót wokół osi z)
    uint8_t dir - 0-kierunek ujemny, 1-kierunek dodatni
    float vel - procent prędkości, zakres 0-100
    */
    int StartJOG(uint8_t ref, uint8_t nb, uint8_t dir, float vel);
    // Przykład
    StartJOG(1,1,1,10)

    /*
    Opis funkcji: Zatrzymanie punktowania robota
    uint8_t ref - 0-zatrzymanie punktowania stawów, 2-zatrzymanie punktowania w podstawowym układzie współrzędnych, 4-zatrzymanie punktowania w układzie współrzędnych narzędzia, 8-zatrzymanie punktowania w układzie współrzędnych przedmiotu
    */
    int StopJOG(uint8_t ref);
    // Przykład
    StopJOG(1)

    /*
    Opis funkcji: Natychmiastowe zatrzymanie punktowania robota
    */
    int ImmStopJOG();

    /*
    Opis funkcji: Ruch w przestrzeni stawów
    string point_name - nazwa wstępnie zapisanego punktu, np. JNT1 oznacza punkt stawowy o numerze 1, CART1 oznacza punkt kartezjański o numerze 1. Instrukcja MoveJ obsługuje wprowadzanie punktów stawowych lub kartezjańskich. Należy pamiętać, że instrukcja MoveJ zawiera w parametrach domyślnych określony układ współrzędnych narzędzia i układ współrzędnych przedmiotu. Jeśli numery tych układów są niezgodne z aktualnie załadowanymi, instrukcja spowoduje błąd. Należy zmodyfikować parametry układów współrzędnych w parametrach domyślnych i załadować parametry przed uruchomieniem tej instrukcji ruchu.
    float vel - procent prędkości instrukcji, zakres 0-100
    int tool - numer układu współrzędnych narzędzia
    int user - numer układu współrzędnych przedmiotu
    double expos1 - pozycja zewnętrznej osi 1
    double expos2 - pozycja zewnętrznej osi 2
    double expos3 - pozycja zewnętrznej osi 3
    double expos4 - pozycja zewnętrznej osi 4
    */
    int MoveJ(string point_name, float vel, int tool, int user, double expos1, double expos2, double expos3, double expos4);//point_name to wprowadzona wstępnie zapisana informacja o punkcie
    // Przykład
    MoveJ(JNT1,10,1,1,0,0,0,0)

    /*
    Opis funkcji: Ruch liniowy w przestrzeni kartezjańskiej
    string point_name - nazwa wstępnie zapisanego punktu, np. JNT1 oznacza punkt stawowy o numerze 1, CART1 oznacza punkt kartezjański o numerze 1. Instrukcja MoveL obsługuje wprowadzanie punktów stawowych lub kartezjańskich. Należy pamiętać, że instrukcja MoveL zawiera w parametrach domyślnych określony układ współrzędnych narzędzia i układ współrzędnych przedmiotu. Jeśli numery tych układów są niezgodne z aktualnie załadowanymi, instrukcja spowoduje błąd. Należy zmodyfikować parametry układów współrzędnych w parametrach domyślnych i załadować parametry przed uruchomieniem tej instrukcji ruchu.
    float vel - procent prędkości instrukcji, zakres 0-100
    int tool - numer układu współrzędnych narzędzia
    int user - numer układu współrzędnych przedmiotu
    double expos1 - pozycja zewnętrznej osi 1
    double expos2 - pozycja zewnętrznej osi 2
    double expos3 - pozycja zewnętrznej osi 3
    double expos4 - pozycja zewnętrznej osi 4
    */
    int MoveL(string point_name, float vel, int tool, int user, double expos1, double expos2, double expos3, double expos4);
    // Przykład
    MoveL(CART1,10,1,1,0,0,0,0)

    /*
    Opis funkcji: Ruch łukowy w przestrzeni kartezjańskiej
    string point1_name, point2_name - nazwy wstępnie zapisanych punktów, np. JNT1 oznacza punkt stawowy o numerze 1, CART1 oznacza punkt kartezjański o numerze 1. Instrukcja MoveC obsługuje wprowadzanie punktów stawowych lub kartezjańskich, ale oba punkty muszą być tego samego typu, tzn. nie obsługuje wprowadzenia pierwszego punktu jako punktu stawowego, a drugiego jako punktu kartezjańskiego. Należy pamiętać, że instrukcja MoveC zawiera w parametrach domyślnych określony układ współrzędnych narzędzia i układ współrzędnych przedmiotu. Jeśli numery tych układów są niezgodne z aktualnie załadowanymi, instrukcja spowoduje błąd. Należy zmodyfikować parametry układów współrzędnych w parametrach domyślnych i załadować parametry przed uruchomieniem tej instrukcji ruchu.
    float vel - procent prędkości instrukcji, zakres 0-100
    int tool - numer układu współrzędnych narzędzia
    int user - numer układu współrzędnych przedmiotu
    double expos1 - pozycja zewnętrznej osi 1 dla punktu 1
    double expos2 - pozycja zewnętrznej osi 2 dla punktu 1
    double expos3 - pozycja zewnętrznej osi 3 dla punktu 1
    double expos4 - pozycja zewnętrznej osi 4 dla punktu 1
    double expos1 - pozycja zewnętrznej osi 1 dla punktu 2
    double expos2 - pozycja zewnętrznej osi 2 dla punktu 2
    double expos3 - pozycja zewnętrznej osi 3 dla punktu 2
    double expos4 - pozycja zewnętrznej osi 4 dla punktu 2
    */
    int MoveC(string point1_name, string point2_name, float vel, int tool, int user, double expos1, double expos2, double expos3, double expos4, double expos1, double expos2, double expos3, double expos4);
    // Przykład
    MoveC(JNT1,JNT2,10,1,1,0,0,0,0,0,0,0,0)

    /*
    Opis funkcji: Rozpoczęcie ruchu po krzywej średniej
    */
    int SplineStart();

    /*
    Opis funkcji: Ruch po krzywej średniej w przestrzeni stawów. Instrukcja obsługuje tylko wprowadzanie danych stawowych, takich jak JNT1. Wprowadzenie punktu kartezjańskiego spowoduje błąd.
    string point_name - nazwa wstępnie zapisanego punktu, np. JNT1 oznacza punkt stawowy o numerze 1.
    float vel - procent prędkości, zakres 0-100
    */
    int SplinePTP(string point_name, float vel);
    // Przykład
    SplinePTP(JNT2,10)

    /*
    Opis funkcji: Zakończenie ruchu po krzywej średniej
    */
    int SplineEnd();

    /*
    Opis funkcji: Rozpoczęcie ruchu po krzywej średniej w przestrzeni kartezjańskiej
    uint8_t ctlpoint - 0-trajektoria przechodzi przez punkty ścieżki, 1-trajektoria nie przechodzi przez punkty sterujące, wymagane co najmniej 4 punkty
    */
    int NewSplineStart(uint8_t ctlpoint);
    // Przykład
    NewSplineStart(1)

    /*
    Opis funkcji: Ruch po krzywej średniej w przestrzeni kartezjańskiej. Można wprowadzać tylko punkty kartezjańskie, takie jak CART1. Wprowadzenie punktu stawowego spowoduje błąd.
    string point_name - nazwa wstępnie zapisanego punktu, np. CART1 oznacza punkt kartezjański o numerze 1.
    float vel - procent prędkości, zakres 0-100
    int lastflag - 0-nie jest ostatnim punktem, 1-jest ostatnim punktem
    */
    int NewSplinePoint(string point_name, float vel, int lastflag);
    // Przykład
    NewSplinePoint(JNT2,20,0)

    /*
    Opis funkcji: Zakończenie ruchu po krzywej średniej w przestrzeni kartezjańskiej
    */
    int NewSplineEnd();

    /*
    Opis funkcji: Zatrzymanie ruchu
    */
    int StopMotion();

    /*
    Opis funkcji: Rozpoczęcie globalnego przesunięcia punktów
    int flag - 0-przesunięcie w podstawowym układzie współrzędnych / układzie współrzędnych przedmiotu, 2-przesunięcie w układzie współrzędnych narzędzia
    double x,y,z,rx,ry,rz - wartość przesunięcia pozycji i orientacji
    */
    int PointsOffsetEnable(int flag, double x, double y, double z, double rx, double ry, double rz);
    // Przykład
    PointsOffsetEnable(1,10,10,10,0,0,0)

    /*
    Opis funkcji: Zakończenie globalnego przesunięcia punktów
    */
    int PointsOffsetDisable();