Ruch robota
===========

.. toctree::
    :maxdepth: 5


Ruch jałowy (JOG)
+++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ruch jałowy (JOG)
    * @param  [in]  ref 0-ruch jałowy stawów, 2-ruch jałowy w układzie bazowym, 4-ruch jałowy w układzie narzędzia, 8-ruch jałowy w układzie obiektu
    * @param  [in]  nb 1-staw 1 (lub oś x), 2-staw 2 (lub oś y), 3-staw 3 (lub oś z), 4-staw 4 (lub obrót wokół osi x), 5-staw 5 (lub obrót wokół osi y), 6-staw 6 (lub obrót wokół osi z)
    * @param  [in]  dir 0-kierunek ujemny, 1-kierunek dodatni
    * @param  [in]  vel Procent prędkości, [0~100]
    * @param  [in]  acc Procent przyspieszenia, [0~100]
    * @param  [in]  max_dis Maksymalny kąt pojedynczego ruchu jałowego, jednostka [°] lub odległość, jednostka [mm]
    * @return  Kod błędu
    */
    errno_t  StartJOG(uint8_t ref, uint8_t nb, uint8_t dir, float vel, float acc, float max_dis);

Zatrzymanie ruchu jałowego z opóźnieniem
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Zatrzymanie ruchu jałowego z opóźnieniem
    * @param  [in]  ref  1-zatrzymanie ruchu jałowego stawów, 3-zatrzymanie ruchu jałowego w układzie bazowym, 5-zatrzymanie ruchu jałowego w układzie narzędzia, 9-zatrzymanie ruchu jałowego w układzie obiektu
    * @return  Kod błędu
    */
    errno_t  StopJOG(uint8_t ref);

Natychmiastowe zatrzymanie ruchu jałowego
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Natychmiastowe zatrzymanie ruchu jałowego
    * @return  Kod błędu
    */
    errno_t  ImmStopJOG();

Przykład kodu sterowania ruchem jałowym robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     int TestJOG(void)
     {
         ROBOT_STATE_PKG pkg = {};
         FRRobot robot;
         robot.LoggerInit();
         robot.SetLoggerLevel(1);
         int rtn = robot.RPC("192.168.58.2");
         if (rtn != 0)
         {
             return -1;
         }
         robot.SetReConnectParam(true, 30000, 500);
         for (int i = 0; i < 6; i++)
         {
             robot.StartJOG(0, i + 1, 0, 20.0, 20.0, 30.0);
             robot.Sleep(1000);
             robot.ImmStopJOG();
             robot.Sleep(1000);
         }
         for (int i = 0; i < 6; i++)
         {
             robot.StartJOG(2, i + 1, 0, 20.0, 20.0, 30.0);
             robot.Sleep(1000);
             robot.ImmStopJOG();
             robot.Sleep(1000);
         }
         for (int i = 0; i < 6; i++)
         {
             robot.StartJOG(4, i + 1, 0, 20.0, 20.0, 30.0);
             robot.Sleep(1000);
             robot.StopJOG(5);
             robot.Sleep(1000);
         }
         for (int i = 0; i < 6; i++)
         {
             robot.StartJOG(8, i + 1, 0, 20.0, 20.0, 30.0);
             robot.Sleep(1000);
             robot.StopJOG(9);
             robot.Sleep(1000);
         }
         robot.CloseRPC();
         return 0;
     }

Ruch w przestrzeni stawów
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ruch w przestrzeni stawów
    * @param  [in] joint_pos  Docelowa pozycja stawów, jednostka deg
    * @param  [in] desc_pos   Docelowa poza i orientacja w kartezjańskim układzie współrzędnych
    * @param  [in] tool  Numer układu współrzędnych narzędzia, zakres [0~14]
    * @param  [in] user  Numer układu współrzędnych obiektu, zakres [0~14]
    * @param  [in] vel  Procent prędkości, zakres [0~100]
    * @param  [in] acc  Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param  [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]
    * @param  [in] epos  Pozycja osi rozszerzonej, jednostka mm
    * @param  [in] blendT [-1.0]-ruch do pozycji (blokujący), [0~500.0]-czas wygładzania (nieblokujący), jednostka ms
    * @param  [in] offset_flag 0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie obiektu, 2-przesunięcie w układzie narzędzia
    * @param  [in] offset_pos  Wartość przesunięcia pozy i orientacji
    * @return  Kod błędu
    */
    errno_t  MoveJ(JointPos *joint_pos, DescPose *desc_pos, int tool, int user, float vel, float acc, float ovl, ExaxisPos *epos, float blendT, uint8_t offset_flag, DescPose *offset_pos);

Ruch w przestrzeni stawów (automatyczne obliczanie prostej kinematyki)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Ruch w przestrzeni stawów (automatyczne obliczanie prostej kinematyki)
    * @param [in] joint_pos Docelowa pozycja stawów, jednostka deg
    * @param [in] tool Numer układu współrzędnych narzędzia, zakres [0~14]
    * @param [in] user Numer układu współrzędnych obiektu, zakres [0~14]
    * @param [in] vel Procent prędkości, zakres [0~100]
    * @param [in] acc Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param [in] ovl Współczynnik skalowania prędkości, zakres [0~100]
    * @param [in] epos Pozycja osi rozszerzonej, jednostka mm
    * @param [in] blendT [-1.0]-ruch do pozycji (blokujący), [0~500.0]-czas wygładzania (nieblokujący), jednostka ms
    * @param [in] offset_flag 0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie obiektu, 2-przesunięcie w układzie narzędzia
    * @param [in] offset_pos Wartość przesunięcia pozy i orientacji
    * @return Kod błędu
    */
    errno_t MoveJ(JointPos* joint_pos, int tool, int user, float vel, float acc, float ovl, ExaxisPos* epos, float blendT, uint8_t offset_flag, DescPose* offset_pos);

Ruch liniowy w przestrzeni kartezjańskiej
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ruch liniowy w przestrzeni kartezjańskiej
    * @param [in] joint_pos Docelowa pozycja stawów, jednostka deg
    * @param [in] desc_pos Docelowa poza i orientacja w kartezjańskim układzie współrzędnych
    * @param [in] tool Numer układu współrzędnych narzędzia, zakres [0~14]
    * @param [in] user Numer układu współrzędnych obiektu, zakres [0~14]
    * @param [in] vel Procent prędkości, zakres [0~100]
    * @param [in] acc Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param [in] ovl Współczynnik skalowania prędkości [0~100] / prędkość fizyczna (mm/s)
    * @param [in] blendR [-1.0]-ruch do pozycji (blokujący), [0~1000.0]-promień wygładzania (nieblokujący), jednostka mm
    * @param [in] blendMode Sposób przejścia; 0-przejście styczne wewnętrznie; 1-przejście narożne
    * @param [in] epos Pozycja osi rozszerzonej, jednostka mm
    * @param [in] search 0-brak lokalizacji drutu spawalniczego, 1-lokalizacja drutu spawalniczego
    * @param [in] offset_flag 0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie obiektu, 2-przesunięcie w układzie narzędzia
    * @param [in] offset_pos Wartość przesunięcia pozy i orientacji
    * @param [in] oacc Współczynnik skalowania przyspieszenia [0-100] / przyspieszenie fizyczne (mm/s2)
    * @param [in] velAccParamMode Tryb parametrów prędkości i przyspieszenia; 0-procent; 1-prędkość fizyczna (mm/s) przyspieszenie fizyczne (mm/s2)
    * @param [in] overSpeedStrategy Strategia obsługi przekroczenia prędkości, 1-standardowa; 2-zgłoś błąd i zatrzymaj przy przekroczeniu prędkości; 3-automatyczne zmniejszenie prędkości, domyślnie 0
    * @param [in] speedPercent Procent progu dozwolonego zmniejszenia prędkości [0-100], domyślnie 10%
    * @return Kod błędu
    */
    errno_t MoveL(JointPos *joint_pos, DescPose *desc_pos, int tool, int user, float vel, float acc, float ovl, float blendR, int blendMode, ExaxisPos *epos, uint8_t search, uint8_t offset_flag, DescPose *offset_pos, float oacc = 100.0, int velAccParamMode = 0, int overSpeedStrategy = 0, int speedPercent = 10);

Ruch liniowy w przestrzeni kartezjańskiej (automatyczne obliczanie odwrotnej kinematyki)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Ruch liniowy w przestrzeni kartezjańskiej (automatyczne obliczanie odwrotnej kinematyki)
    * @param [in] desc_pos  Docelowa poza i orientacja w kartezjańskim układzie współrzędnych
    * @param [in] tool Numer układu współrzędnych narzędzia, zakres [0~14]
    * @param [in] user Numer układu współrzędnych obiektu, zakres [0~14]
    * @param [in] vel Procent prędkości, zakres [0~100]
    * @param [in] acc Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param [in] ovl Współczynnik skalowania prędkości, zakres [0~100]
    * @param [in] blendR [-1.0]-ruch do pozycji (blokujący), [0~1000.0]-promień wygładzania (nieblokujący), jednostka mm
    * @param [in] blendMode Sposób przejścia; 0-przejście styczne wewnętrznie; 1-przejście narożne
    * @param [in] epos Pozycja osi rozszerzonej, jednostka mm
    * @param [in] search 0-brak lokalizacji drutu spawalniczego, 1-lokalizacja drutu spawalniczego
    * @param [in] offset_flag 0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie obiektu, 2-przesunięcie w układzie narzędzia
    * @param [in] offset_pos Wartość przesunięcia pozy i orientacji
    * @param [in] config Konfiguracja przestrzeni stawów dla odwrotnej kinematyki, [-1]-obliczenia w oparciu o bieżącą pozycję stawów, [0~7]-obliczenia zgodnie z określoną konfiguracją przestrzeni stawów
    * @param [in] overSpeedStrategy Strategia obsługi przekroczenia prędkości, 1-standardowa; 2-zgłoś błąd i zatrzymaj przy przekroczeniu prędkości; 3-automatyczne zmniejszenie prędkości, domyślnie 0
    * @param [in] speedPercent Procent progu dozwolonego zmniejszenia prędkości [0-100], domyślnie 10%
    * @return Kod błędu
    */
    errno_t MoveL(DescPose* desc_pos, int tool, int user, float vel, float acc, float ovl, float blendR, int blendMode, ExaxisPos* epos, uint8_t search, uint8_t offset_flag, DescPose* offset_pos, int config = -1, int overSpeedStrategy = 0, int speedPercent = 10);

Ruch łukowy w przestrzeni kartezjańskiej
++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ruch łukowy w przestrzeni kartezjańskiej
    * @param  [in] joint_pos_p  Pozycja stawów punktu pośredniego, jednostka deg
    * @param  [in] desc_pos_p   Poza i orientacja punktu pośredniego w kartezjańskim układzie współrzędnych
    * @param  [in] ptool  Numer układu współrzędnych narzędzia, zakres [0~14]
    * @param  [in] puser  Numer układu współrzędnych obiektu, zakres [0~14]
    * @param  [in] pvel  Procent prędkości, zakres [0~100]
    * @param  [in] pacc  Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param  [in] epos_p  Pozycja osi rozszerzonej, jednostka mm
    * @param  [in] poffset_flag  0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie obiektu, 2-przesunięcie w układzie narzędzia
    * @param  [in] offset_pos_p  Wartość przesunięcia pozy i orientacji
    * @param  [in] joint_pos_t  Pozycja stawów punktu docelowego, jednostka deg
    * @param  [in] desc_pos_t   Poza i orientacja punktu docelowego w kartezjańskim układzie współrzędnych
    * @param  [in] ttool  Numer układu współrzędnych narzędzia, zakres [0~14]
    * @param  [in] tuser  Numer układu współrzędnych obiektu, zakres [0~14]
    * @param  [in] tvel  Procent prędkości, zakres [0~100]
    * @param  [in] tacc  Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param  [in] epos_t  Pozycja osi rozszerzonej, jednostka mm
    * @param  [in] toffset_flag  0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie obiektu, 2-przesunięcie w układzie narzędzia
    * @param  [in] offset_pos_t  Wartość przesunięcia pozy i orientacji
    * @param  [in] ovl  Współczynnik skalowania prędkości [0~100] / prędkość fizyczna (mm/s)
    * @param  [in] blendR [-1.0]-ruch do pozycji (blokujący), [0~1000.0]-promień wygładzania (nieblokujący), jednostka mm
    * @param  [in] oacc Współczynnik skalowania przyspieszenia [0-100] / przyspieszenie fizyczne (mm/s2)
    * @param  [in] velAccParamMode Tryb parametrów prędkości i przyspieszenia; 0-procent; 1-prędkość fizyczna (mm/s) przyspieszenie fizyczne (mm/s2)
    * @return  Kod błędu
    */
    errno_t MoveC(JointPos *joint_pos_p, DescPose *desc_pos_p, int ptool, int puser, float pvel, float pacc, ExaxisPos *epos_p, uint8_t poffset_flag, DescPose *offset_pos_p, JointPos *joint_pos_t, DescPose *desc_pos_t, int ttool, int tuser, float tvel, float tacc, ExaxisPos *epos_t, uint8_t toffset_flag, DescPose *offset_pos_t, float ovl, float blendR, float oacc = 100.0, int velAccParamMode = 0);

Ruch łukowy w przestrzeni kartezjańskiej (automatyczne obliczanie odwrotnej kinematyki)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Ruch łukowy w przestrzeni kartezjańskiej (automatyczne obliczanie odwrotnej kinematyki)
    * @param [in] desc_pos_p  Poza i orientacja punktu pośredniego w kartezjańskim układzie współrzędnych
    * @param [in] ptool Numer układu współrzędnych narzędzia, zakres [0~14]
    * @param [in] puser Numer układu współrzędnych obiektu, zakres [0~14]
    * @param [in] pvel Procent prędkości, zakres [0~100]
    * @param [in] pacc Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param [in] epos_p Pozycja osi rozszerzonej, jednostka mm
    * @param [in] poffset_flag 0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie obiektu, 2-przesunięcie w układzie narzędzia
    * @param [in] offset_pos_p Wartość przesunięcia pozy i orientacji
    * @param [in] desc_pos_t  Poza i orientacja punktu docelowego w kartezjańskim układzie współrzędnych
    * @param [in] ttool Numer układu współrzędnych narzędzia, zakres [0~14]
    * @param [in] tuser Numer układu współrzędnych obiektu, zakres [0~14]
    * @param [in] tvel Procent prędkości, zakres [0~100]
    * @param [in] tacc Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param [in] epos_t Pozycja osi rozszerzonej, jednostka mm
    * @param [in] toffset_flag 0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie obiektu, 2-przesunięcie w układzie narzędzia
    * @param [in] offset_pos_t Wartość przesunięcia pozy i orientacji
    * @param [in] ovl Współczynnik skalowania prędkości, zakres [0~100]
    * @param [in] blendR [-1.0]-ruch do pozycji (blokujący), [0~1000.0]-promień wygładzania (nieblokujący), jednostka mm
    * @param [in] config Konfiguracja przestrzeni stawów dla odwrotnej kinematyki, [-1]-obliczenia w oparciu o bieżącą pozycję stawów, [0~7]-obliczenia zgodnie z określoną konfiguracją przestrzeni stawów
    * @return Kod błędu
    */
    errno_t MoveC(DescPose* desc_pos_p, int ptool, int puser, float pvel, float pacc, ExaxisPos* epos_p, uint8_t poffset_flag, DescPose* offset_pos_p, DescPose* desc_pos_t, int ttool, int tuser, float tvel, float tacc, ExaxisPos* epos_t, uint8_t toffset_flag, DescPose* offset_pos_t, float ovl, float blendR, int config = -1);

Ruch pełnego okręgu w przestrzeni kartezjańskiej
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ruch pełnego okręgu w przestrzeni kartezjańskiej
    * @param  [in] joint_pos_p  Pozycja stawów punktu pośredniego 1, jednostka deg
    * @param  [in] desc_pos_p   Poza i orientacja punktu pośredniego 1 w kartezjańskim układzie współrzędnych
    * @param  [in] ptool  Numer układu współrzędnych narzędzia, zakres [0~14]
    * @param  [in] puser  Numer układu współrzędnych obiektu, zakres [0~14]
    * @param  [in] pvel  Procent prędkości, zakres [0~100]
    * @param  [in] pacc  Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param  [in] epos_p  Pozycja osi rozszerzonej, jednostka mm
    * @param  [in] joint_pos_t  Pozycja stawów punktu pośredniego 2, jednostka deg
    * @param  [in] desc_pos_t   Poza i orientacja punktu pośredniego 2 w kartezjańskim układzie współrzędnych
    * @param  [in] ttool  Numer układu współrzędnych narzędzia, zakres [0~14]
    * @param  [in] tuser  Numer układu współrzędnych obiektu, zakres [0~14]
    * @param  [in] tvel  Procent prędkości, zakres [0~100]
    * @param  [in] tacc  Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param  [in] epos_t  Pozycja osi rozszerzonej, jednostka mm
    * @param  [in] ovl  Współczynnik skalowania prędkości [0~100] / prędkość fizyczna (mm/s)
    * @param  [in] offset_flag  0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie obiektu, 2-przesunięcie w układzie narzędzia
    * @param  [in] offset_pos  Wartość przesunięcia pozy i orientacji
    * @param  [in] oacc Współczynnik skalowania przyspieszenia [0-100] / przyspieszenie fizyczne (mm/s2)
    * @param  [in] blendR -1: blokujący; 0~1000: promień wygładzania
    * @param  [in] velAccParamMode Tryb parametrów prędkości i przyspieszenia; 0-procent; 1-prędkość fizyczna (mm/s) przyspieszenie fizyczne (mm/s2)
    * @return  Kod błędu
    */
    errno_t Circle(JointPos* joint_pos_p, DescPose* desc_pos_p, int ptool, int puser, float pvel, float pacc, ExaxisPos* epos_p, JointPos* joint_pos_t, DescPose* desc_pos_t, int ttool, int tuser, float tvel, float tacc, ExaxisPos* epos_t, float ovl, uint8_t offset_flag, DescPose* offset_pos, double oacc = 100.0, double blendR = -1, int velAccParamMode = 0);

Ruch pełnego okręgu w przestrzeni kartezjańskiej (automatyczne obliczanie odwrotnej kinematyki)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Ruch pełnego okręgu w przestrzeni kartezjańskiej (automatyczne obliczanie odwrotnej kinematyki)
    * @param [in] desc_pos_p  Poza i orientacja punktu pośredniego 1 w kartezjańskim układzie współrzędnych
    * @param [in] ptool Numer układu współrzędnych narzędzia, zakres [0~14]
    * @param [in] puser Numer układu współrzędnych obiektu, zakres [0~14]
    * @param [in] pvel Procent prędkości, zakres [0~100]
    * @param [in] pacc Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param [in] epos_p Pozycja osi rozszerzonej, jednostka mm
    * @param [in] desc_pos_t  Poza i orientacja punktu pośredniego 2 w kartezjańskim układzie współrzędnych
    * @param [in] ttool Numer układu współrzędnych narzędzia, zakres [0~14]
    * @param [in] tuser Numer układu współrzędnych obiektu, zakres [0~14]
    * @param [in] tvel Procent prędkości, zakres [0~100]
    * @param [in] tacc Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param [in] epos_t Pozycja osi rozszerzonej, jednostka mm
    * @param [in] ovl Współczynnik skalowania prędkości, zakres [0~100]
    * @param [in] offset_flag 0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie obiektu, 2-przesunięcie w układzie narzędzia
    * @param [in] offset_pos Wartość przesunięcia pozy i orientacji
    * @param [in] oacc Procent przyspieszenia
    * @param [in] blendR -1: blokujący; 0~1000: promień wygładzania
    * @param [in] config Konfiguracja przestrzeni stawów dla odwrotnej kinematyki, [-1]-obliczenia w oparciu o bieżącą pozycję stawów, [0~7]-obliczenia zgodnie z określoną konfiguracją przestrzeni stawów
    * @return Kod błędu
    */
    errno_t Circle(DescPose* desc_pos_p, int ptool, int puser, float pvel, float pacc, ExaxisPos* epos_p, DescPose* desc_pos_t, int ttool, int tuser, float tvel, float tacc, ExaxisPos* epos_t, float ovl, uint8_t offset_flag, DescPose* offset_pos, double oacc = 100.0, double blendR = -1, int config = -1);

Ruch punkt-punkt w przestrzeni kartezjańskiej
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ruch punkt-punkt w przestrzeni kartezjańskiej
    * @param  [in]  desc_pos  Docelowa poza i orientacja w kartezjańskim układzie współrzędnych lub przyrost pozy i orientacji
    * @param  [in] tool  Numer układu współrzędnych narzędzia, zakres [0~14]
    * @param  [in] user  Numer układu współrzędnych obiektu, zakres [0~14]
    * @param  [in] vel  Procent prędkości, zakres [0~100]
    * @param  [in] acc  Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param  [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]
    * @param  [in] blendT [-1.0]-ruch do pozycji (blokujący), [0~500.0]-czas wygładzania (nieblokujący), jednostka ms
    * @param  [in] config  Konfiguracja przestrzeni stawów, [-1]-obliczenia w oparciu o bieżącą pozycję stawów, [0~7]-obliczenia w oparciu o określoną konfigurację przestrzeni stawów, domyślnie -1
    * @return  Kod błędu
    */
    errno_t  MoveCart(DescPose *desc_pos, int tool, int user, float vel, float acc, float ovl, float blendT, int config);

Przykład kodu podstawowych instrukcji ruchu robota
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestMove(void)
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;

        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return -1;
        }
        robot.SetReConnectParam(true, 30000, 500);

        JointPos j1(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j2(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
        JointPos j3(-29.777, -84.536, 109.275, -114.075, -86.655, 74.257);
        JointPos j4(-31.154, -95.317, 94.276, -88.079, -89.740, 74.256);
        DescPose desc_pos1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_pos2(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose desc_pos3(-487.434, 154.362, 308.576, 176.600, 0.268, -14.061);
        DescPose desc_pos4(-443.165, 147.881, 480.951, 179.511, -0.775, -15.409);
        DescPose offset_pos(0, 0, 0, 0, 0, 0);
        ExaxisPos epos(0, 0, 0, 0);
        int tool = 0;
        int user = 0;
        float vel = 100.0;
        float acc = 100.0;
        float ovl = 100.0;
        float oacc = 100.0;
        float blendT = 0.0;
        float blendR = 0.0;
        uint8_t flag = 0;
        uint8_t search = 0;
        int blendMode = 0;
        int velAccMode = 0;
        robot.SetSpeed(20);
        rtn = robot.MoveJ(&j1, &desc_pos1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
        printf("movej errcode:%d\n", rtn);
        rtn = robot.MoveL(&j2, &desc_pos2, tool, user, vel, acc, ovl, blendR, blendMode, &epos, search, flag, &offset_pos, oacc, velAccMode);
        printf("movel errcode:%d\n", rtn);
        rtn = robot.MoveC(&j3, &desc_pos3, tool, user, vel, acc, &epos, flag, &offset_pos, &j4, &desc_pos4, tool, user, vel, acc, &epos, flag, &offset_pos, ovl, blendR, oacc, velAccMode);
        printf("movec errcode:%d\n", rtn);
        rtn = robot.MoveJ(&j2, &desc_pos2, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
        printf("movej errcode:%d\n", rtn);
        rtn = robot.Circle(&j3, &desc_pos3, tool, user, vel, acc, &epos, &j1, &desc_pos1, tool, user, vel, acc, &epos, ovl, flag, &offset_pos, oacc, -1, velAccMode);
        printf("circle errcode:%d\n", rtn);
        rtn = robot.MoveCart(&desc_pos4, tool, user, vel, acc, ovl, blendT, -1);
        printf("MoveCart errcode:%d\n", rtn);
        rtn = robot.MoveJ(&j1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
        printf("movej errcode:%d\n", rtn);
        rtn = robot.MoveL(&desc_pos2, tool, user, vel, acc, ovl, blendR, blendMode, &epos, search, flag, &offset_pos, -1, velAccMode);
        printf("movel errcode:%d\n", rtn);
        rtn = robot.MoveC(&desc_pos3, tool, user, vel, acc, &epos, flag, &offset_pos, &desc_pos4, tool, user, vel, acc, &epos, flag, &offset_pos, ovl, blendR, -1, velAccMode);
        printf("movec errcode:%d\n", rtn);
        rtn = robot.MoveJ(&j2, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
        printf("movej errcode:%d\n", rtn);
        rtn = robot.Circle(&desc_pos3, tool, user, vel, acc, &epos, &desc_pos1, tool, user, vel, acc, &epos, ovl, flag, &offset_pos, oacc, blendR, -1, velAccMode);
        printf("circle errcode:%d\n", rtn);
        robot.CloseRPC();
        return 0;
    }

Ruch spiralny w przestrzeni kartezjańskiej
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ruch spiralny w przestrzeni kartezjańskiej
    * @param  [in] joint_pos  Docelowa pozycja stawów, jednostka deg
    * @param  [in] desc_pos   Docelowa poza i orientacja w kartezjańskim układzie współrzędnych
    * @param  [in] tool  Numer układu współrzędnych narzędzia, zakres [0~14]
    * @param  [in] user  Numer układu współrzędnych obiektu, zakres [0~14]
    * @param  [in] vel  Procent prędkości, zakres [0~100]
    * @param  [in] acc  Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param  [in] epos  Pozycja osi rozszerzonej, jednostka mm
    * @param  [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]
    * @param  [in] offset_flag  0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie obiektu, 2-przesunięcie w układzie narzędzia
    * @param  [in] offset_pos  Wartość przesunięcia pozy i orientacji
    * @param  [in] spiral_param  Parametry spirali
    * @return  Kod błędu
    */
    errno_t  NewSpiral(JointPos *joint_pos, DescPose *desc_pos, int tool, int user, float vel, float acc, ExaxisPos *epos, float ovl, uint8_t offset_flag, DescPose *offset_pos, SpiralParam spiral_param);

Ruch spiralny w przestrzeni kartezjańskiej (automatyczne obliczanie odwrotnej kinematyki)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Ruch spiralny w przestrzeni kartezjańskiej (automatyczne obliczanie odwrotnej kinematyki)
    * @param [in] desc_pos  Docelowa poza i orientacja w kartezjańskim układzie współrzędnych
    * @param [in] tool Numer układu współrzędnych narzędzia, zakres [0~14]
    * @param [in] user Numer układu współrzędnych obiektu, zakres [0~14]
    * @param [in] vel Procent prędkości, zakres [0~100]
    * @param [in] acc Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param [in] epos Pozycja osi rozszerzonej, jednostka mm
    * @param [in] ovl Współczynnik skalowania prędkości, zakres [0~100]
    * @param [in] offset_flag 0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie obiektu, 2-przesunięcie w układzie narzędzia
    * @param [in] offset_pos Wartość przesunięcia pozy i orientacji
    * @param [in] spiral_param Parametry spirali
    * @param [in] config Konfiguracja przestrzeni stawów dla odwrotnej kinematyki, [-1]-obliczenia w oparciu o bieżącą pozycję stawów, [0~7]-obliczenia zgodnie z określoną konfiguracją przestrzeni stawów
    * @return Kod błędu
    */
    errno_t NewSpiral(DescPose* desc_pos, int tool, int user, float vel, float acc, ExaxisPos* epos, float ovl, uint8_t offset_flag, DescPose* offset_pos, SpiralParam spiral_param, int config = -1);

Przykład kodu ruchu spiralnego
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestSpiral(void)
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      robot.LoggerInit();
      robot.SetLoggerLevel(1);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return -1;
      }
      robot.SetReConnectParam(true, 30000, 500);
      JointPos j(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
      DescPose desc_pos(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
      DescPose offset_pos1(50, 0, 0, -30, 0, 0);
      DescPose offset_pos2(50, 0, 0, -5, 0, 0);
      ExaxisPos epos(0, 0, 0, 0);
      SpiralParam sp;
      sp.circle_num = 5;
      sp.circle_angle = 5.0;
      sp.rad_init = 50.0;
      sp.rad_add = 10.0;
      sp.rotaxis_add = 10.0;
      sp.rot_direction = 0;
      int tool = 0;
      int user = 0;
      float vel = 100.0;
      float acc = 100.0;
      float ovl = 100.0;
      float blendT = 0.0;
      uint8_t flag = 2;
      robot.SetSpeed(20);
      rtn = robot.MoveJ(&j, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos1);
      printf("movej errcode:%d\n", rtn);
      rtn = robot.NewSpiral(&desc_pos, tool, user, vel, acc, &epos, ovl, flag, &offset_pos2, sp);
      printf("newspiral errcode:%d\n", rtn);
      robot.CloseRPC();
      return 0;
    }

Rozpoczęcie ruchu serwo
+++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Rozpoczęcie ruchu serwo, używane razem z instrukcjami ServoJ, ServoCart
    * @param [in] comType Typ wysyłania instrukcji; 0-xmlrpc; 1-UDP (odpowiadający portowi 20007 robota)
    * @return Kod błędu
    */
    errno_t ServoMoveStart(int comType = 0);

Zakończenie ruchu serwo
+++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Zakończenie ruchu serwo, używane razem z instrukcjami ServoJ, ServoCart
    * @param [in] comType Typ wysyłania instrukcji; 0-xmlrpc; 1-UDP (odpowiadający portowi 20007 robota)
    * @return Kod błędu
    */
    errno_t ServoMoveEnd(int comType = 0);

Ruch w trybie serwo w przestrzeni stawów
++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Ruch w trybie serwo w przestrzeni stawów
    * @param [in] joint_pos Docelowa pozycja stawów, jednostka deg
    * @param [in] axisPos Pozycja osi zewnętrznej, jednostka mm
    * @param [in] acc Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne, domyślnie 0
    * @param [in] vel Procent prędkości, zakres [0~100], tymczasowo niedostępne, domyślnie 0
    * @param [in] cmdT Okres wysyłania instrukcji, jednostka s, zalecany zakres [0.001~0.0016]
    * @param [in] filterT Czas filtracji, jednostka s, tymczasowo niedostępny, domyślnie 0
    * @param [in] gain Wzmacniacz proporcjonalności pozycji docelowej, tymczasowo niedostępny, domyślnie 0
    * @param [in] id ID instrukcji servoJ, domyślnie 0
    * @param [in] comType Typ wysyłania instrukcji; 0-xmlrpc; 1-UDP (odpowiadający portowi 20007 robota)
    * @return Kod błędu
    */
    errno_t ServoJ(JointPos *joint_pos, ExaxisPos* axisPos, float acc, float vel, float cmdT, float filterT, float gain, int id = 0, int comType = 0);

Przykład programu ruchu w trybie serwo w przestrzeni stawów
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestServoJ(void)
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return -1;
        }
        robot.SetReConnectParam(true, 30000, 500);
        JointPos j(0, 0, 0, 0, 0, 0);
        ExaxisPos epos(0, 0, 0, 0);
        float vel = 0.0;
        float acc = 0.0;
        float cmdT = 0.008;
        float filterT = 0.0;
        float gain = 0.0;
        uint8_t flag = 0;
        int count = 500;
        float dt = 0.1;
        int cmdID = 0;
        int ret = robot.GetActualJointPosDegree(flag, &j);
        if (ret == 0)
        {
            robot.ServoMoveStart();
            while (count)
            {
                robot.ServoJ(&j, &epos, acc, vel, cmdT, filterT, gain, cmdID);
                j.jPos[0] += dt;
                count -= 1;
                robot.WaitMs(cmdT * 1000);
            }
            robot.ServoMoveEnd();
        }
        else
        {
            printf("GetActualJointPosDegree errcode:%d\n", ret);
        }
        robot.CloseRPC();
        return 0;
    }

Przykład kodu ruchu w trybie serwo w przestrzeni stawów robota opartego na komunikacji UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    void UDPFrameCallBack(int srcType, int count, int cmdID, int len, std::string content)
    {
        cout << "recv cmd: cmdID:  " << to_string(cmdID) << "  content is " << content << "  count is " << count << endl;;
            return;
    }

    int TestServoJUDP(void)
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        int rtn = 0;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        rtn = robot.SetCmdRpyCallback(UDPFrameCallBack);
        printf("SetCmdRpyCallback rtn is %d\n", rtn);
        rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return -1;
        }
        robot.SetReConnectParam(true, 30000, 50);
        JointPos j(0, -90, 90, 0, 0, 0);
        ExaxisPos epos(0, 0, 0, 0);
        DescPose offset_pos(0, 0, 0, 0, 0, 0);
        while (true)
        {
            robot.MoveJ(&j, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
            float vel = 0.0;
            float acc = 0.0;
            float cmdT = 0.016;
            float filterT = 0.0;
            float gain = 0.0;
            uint8_t flag = 0;
            float dt = 0.1;
            int cmdID = 0;
            int ret = robot.GetActualJointPosDegree(flag, &j);
            if (ret != 0)
            {
                printf("GetActualJointPosDegree errcode:%d\n", ret);
            }
            int comType = 1;
            int count = 300;
            rtn = robot.ServoMoveStart(comType);
            printf("ServoMoveStart rtn is %d\n", rtn);
            while (count)
            {
                rtn = robot.ServoJ(&j, &epos, acc, vel, cmdT, filterT, gain, cmdID, comType);
                printf("ServoJ rtn is %d\n", rtn);
                j.jPos[0] += dt;
                j.jPos[1] += dt;
                j.jPos[2] += dt;
                j.jPos[3] += dt;
                j.jPos[4] += dt;
                j.jPos[5] += dt;
                epos.ePos[0] += dt;
                count -= 1;
                robot.Sleep(15);
            }
            robot.ServoMoveEnd(comType);
            printf("ServoMoveEnd rtn is %d\n", rtn);
            count = 300;
            robot.ServoMoveStart(comType);
            printf("ServoMoveStart rtn is %d\n", rtn);
            while (count)
            {
                robot.ServoJ(&j, &epos, acc, vel, cmdT, filterT, gain, cmdID, comType);
                printf("ServoJ rtn is %d\n", rtn);
                j.jPos[0] -= dt;
                j.jPos[1] -= dt;
                j.jPos[2] -= dt;
                j.jPos[3] -= dt;
                j.jPos[4] -= dt;
                j.jPos[5] -= dt;
                epos.ePos[0] -= dt;
                count -= 1;
                robot.Sleep(15);
            }
            robot.ServoMoveEnd(comType);
            printf("ServoMoveEnd rtn is %d\n", rtn);
        }
        robot.Sleep(4000);
        robot.CloseRPC();
        return 0;
    }

Rozpoczęcie sterowania momentem stawów
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Rozpoczęcie sterowania momentem stawów
    * @param [in] comType Typ wysyłania instrukcji; 0-xmlrpc; 1-UDP (odpowiadający portowi 20007 robota)
    * @return Kod błędu
    */
    errno_t ServoJTStart(int comType = 0);

Sterowanie momentem stawów
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Sterowanie momentem stawów
    * @param [in] torque Moment stawów j1~j6, jednostka Nm
    * @param [in] interval Okres instrukcji, jednostka s, zakres [0.001~0.008]
    * @param [in] checkFlag Strategia wykrywania 0-brak ograniczenia; 1-ograniczenie mocy; 2-ograniczenie prędkości; 3-jednoczesne ograniczenie mocy i prędkości
    * @param [in] jPowerLimit Maksymalne ograniczenie mocy stawu (W)
    * @param [in] jVelLimit Maksymalna prędkość stawu (°/s)
    * @param [in] comType Typ wysyłania instrukcji; 0-xmlrpc; 1-UDP (odpowiadający portowi 20007 robota)
    * @return Kod błędu
    */
    errno_t ServoJT(float torque[], double interval, int checkFlag, double jPowerLimit[6], double jVelLimit[6], int comType = 0);

Zakończenie sterowania momentem stawów
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Zakończenie sterowania momentem stawów
    * @param [in] comType Typ wysyłania instrukcji; 0-xmlrpc; 1-UDP (odpowiadający portowi 20007 robota)
    * @return Kod błędu
    */
    errno_t ServoJTEnd(int comType = 0);

Przykład kodu sterowania momentem stawów
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    int TestServoJT(void)
     {
         ROBOT_STATE_PKG pkg = {};
         FRRobot robot;
         robot.LoggerInit();
         robot.SetLoggerLevel(1);
         int rtn = robot.RPC("192.168.58.2");
         if (rtn != 0)
         {
             return -1;
         }
         robot.SetReConnectParam(true, 30000, 500);
         robot.DragTeachSwitch(1);
         float torques[] = { 0, 0, 0, 0, 0, 0 };
         robot.GetJointTorques(1, torques);
         int count = 100;
         robot.ServoJTStart();
         int error = 0;
         while (count > 0)
         {
             error = robot.ServoJT(torques, 0.001);
             count = count - 1;
             robot.Sleep(1);
         }
         error = robot.ServoJTEnd();
         robot.DragTeachSwitch(0);
         robot.CloseRPC();
         return 0;
     }

Przykład kodu sterowania momentem stawów z ochroną przed przekroczeniem prędkości
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int ServoJTWithSafety(FRRobot* robot)
    {
        robot->ResetAllError();
        robot->Sleep(500);
        float torques[] = { 0, 0, 0, 0, 0, 0 };
        robot->GetJointTorques(1, torques);
        robot->ServoJTStart();
        ROBOT_STATE_PKG pkg = {};
        robot->DragTeachSwitch(1);
        int checkFlag = 3;
        //double jPowerLimit[6] = {1, 1, 1, 1, 1, 1};
        double jPowerLimit[6] = { 10.0, 10.0, 10.0, 10.0, 10.0, 10.0 };
        double jVelLimit[6] = { 181, 80, 80, 80, 80, 80 };
        int count = 800000;
        int error = 0;
        while (count > 0)
        {
            torques[2] = torques[2] + 0.01;
            error = robot->ServoJT(torques, 0.008, checkFlag, jPowerLimit, jVelLimit);
            if (error != 0)
            {
                robot->ServoJTEnd();
            }
            printf("ServoJT rtn is %d\n", error);
            count = count - 1;
            robot->Sleep(1);
            robot->GetRobotRealTimeState(&pkg);
            printf("maincode %d, subcode %d\n", pkg.main_code, pkg.sub_code);
        }
        robot->DragTeachSwitch(0);
        error = robot->ServoJTEnd();
        return 0;
    }

Przykład kodu sterowania momentem stawów robota opartego na komunikacji UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    void UDPFrameCallBack(int srcType, int count, int cmdID, int len, std::string content)
    {
        cout << "recv cmd: cmdID:  " << to_string(cmdID) << "  content is " << content << "  count is " << count << endl;

        return;
    }
    int TestServoJTUDP(void)
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        robot.SetCmdRpyCallback(UDPFrameCallBack);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
        	return -1;
        }
        robot.SetReConnectParam(true, 30000, 500);
        JointPos j(0, -90, 90, 0, 0, 0);
        ExaxisPos epos(0, 0, 0, 0);
        DescPose offset_pos(0, 0, 0, 0, 0, 0);
        robot.MoveJ(&j, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(1000);
        robot.DragTeachSwitch(1);
        float torques[] = { 0, 0, 0, 0, 0, 0 };
        robot.GetJointTorques(1, torques);
        int comType = 1;
        int count = 100;
        int checkFlag = 3;
        double jPowerLimit[6] = { 10.0, 10.0, 10.0, 10.0, 10.0, 10.0 };
        double jVelLimit[6] = { 80, 80, 80, 80, 80, 80 };
        rtn = robot.ServoJTStart(comType);
        printf("ServoJTStart rtn is %d\n", rtn);
        while (true)
        {
            torques[0] = 0.05;
            rtn = robot.ServoJT(torques, 0.001, checkFlag, jPowerLimit, jVelLimit, comType);
            printf("ServoJT rtn is %d\n", rtn);
            robot.Sleep(1);
            robot.GetRobotRealTimeState(&pkg);
            if (pkg.jt_cur_pos[0] > 30)
            {
                break;
            }
        }
        while (true)
        {
            torques[0] = -0.03;
            rtn = robot.ServoJT(torques, 0.001, checkFlag, jPowerLimit, jVelLimit, comType);
            printf("ServoJT rtn is %d\n", rtn);
            robot.Sleep(1);
            robot.GetRobotRealTimeState(&pkg);
            if (pkg.jt_cur_pos[0] < 0 || pkg.jt_cur_pos[1] < -110)
            {
                break;
            }
        }
        rtn = robot.ServoJTEnd(comType);
        printf("ServoJTEnd rtn is %d\n", rtn);
        robot.DragTeachSwitch(0);
        robot.Sleep(1000);
        robot.CloseRPC();
        return 0;
    }

Ruch w trybie serwo w przestrzeni kartezjańskiej
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Ruch w trybie serwo w przestrzeni kartezjańskiej
    * @param [in] mode 0-ruch absolutny (układ bazowy), 1-ruch przyrostowy (układ bazowy), 2-ruch przyrostowy (układ narzędzia)
    * @param [in] desc_pos Docelowa poza i orientacja w kartezjańskim układzie współrzędnych lub przyrost pozy i orientacji
    * @param [in] exaxis Pozycja osi rozszerzonej
    * @param [in] pos_gain Współczynnik proporcjonalności przyrostu pozy i orientacji, działa tylko w ruchu przyrostowym, zakres [0~1]
    * @param [in] acc Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne, domyślnie 0
    * @param [in] vel Procent prędkości, zakres [0~100], tymczasowo niedostępne, domyślnie 0
    * @param [in] cmdT Okres wysyłania instrukcji, jednostka s, zalecany zakres [0.001~0.016]
    * @param [in] filterT Czas filtracji, jednostka s, tymczasowo niedostępny, domyślnie 0
    * @param [in] gain Wzmacniacz proporcjonalności pozycji docelowej, tymczasowo niedostępny, domyślnie 0
    * @return Kod błędu
    */
    errno_t ServoCart(int mode, DescPose *desc_pose, ExaxisPos exaxis, float pos_gain[6], float acc, float vel, float cmdT, float filterT, float gain);

Przykład kodu ruchu w trybie serwo w przestrzeni kartezjańskiej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestServoCart(void)
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return -1;
        }
        robot.SetReConnectParam(true, 30000, 500);
        DescPose desc_pos_dt = { 83.00800, 50.525000 , 29.246 , 179.629 , -7.138 , -166.975 };
        ExaxisPos exaxis = { 100.0, 0.0, 0.0, 0.0 };
        float pos_gain[6] = { 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 };
        int mode = 0;
        float vel = 0.0;
        float acc = 0.0;
        float cmdT = 0.001;
        float filterT = 0.0;
        float gain = 0.0;
        uint8_t flag = 0;
        int count = 5000;
        robot.SetSpeed(20);
        while (count)
        {
            rtn = robot.ServoCart(mode, &desc_pos_dt, exaxis, pos_gain, acc, vel, cmdT, filterT, gain);
            printf("ServoCart rtn is %d\n", rtn);
            count -= 1;
            desc_pos_dt.tran.x += 0.01;
            exaxis.ePos[0] += 0.01;
        }
        robot.CloseRPC();
        return 0;
    }

Rozpoczęcie ruchu funkcją sklejaną (Spline)
+++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Rozpoczęcie ruchu funkcją sklejaną
    * @return  Kod błędu
    */
    errno_t  SplineStart();

Ruch funkcją sklejaną w przestrzeni stawów (automatyczne obliczanie prostej kinematyki)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Ruch funkcją sklejaną w przestrzeni stawów (automatyczne obliczanie prostej kinematyki)
    * @param [in] joint_pos Docelowa pozycja stawów, jednostka deg
    * @param [in] tool Numer układu współrzędnych narzędzia, zakres [0~14]
    * @param [in] user Numer układu współrzędnych obiektu, zakres [0~14]
    * @param [in] vel Procent prędkości, zakres [0~100]
    * @param [in] acc Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param [in] ovl Współczynnik skalowania prędkości, zakres [0~100]
    * @return Kod błędu
    */
    errno_t SplinePTP(JointPos* joint_pos, int tool, int user, float vel, float acc, float ovl);

Ruch funkcją sklejaną PTP
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ruch funkcją sklejaną w przestrzeni stawów
    * @param  [in] joint_pos  Docelowa pozycja stawów, jednostka deg
    * @param  [in] desc_pos   Docelowa poza i orientacja w kartezjańskim układzie współrzędnych
    * @param  [in] tool  Numer układu współrzędnych narzędzia, zakres [0~14]
    * @param  [in] user  Numer układu współrzędnych obiektu, zakres [0~14]
    * @param  [in] vel  Procent prędkości, zakres [0~100]
    * @param  [in] acc  Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param  [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]
    * @return  Kod błędu
    */
    errno_t  SplinePTP(JointPos *joint_pos, DescPose *desc_pos, int tool, int user, float vel, float acc, float ovl);

Zakończenie ruchu funkcją sklejaną
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Zakończenie ruchu funkcją sklejaną
    * @return  Kod błędu
    */
    errno_t  SplineEnd();

Przykład kodu ruchu funkcją sklejaną
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestSpline(void)
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      robot.LoggerInit();
      robot.SetLoggerLevel(1);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return -1;
      }
      robot.SetReConnectParam(true, 30000, 500);
      JointPos j1(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
      JointPos j2(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
      JointPos j3(-61.954, -84.409, 108.153, -116.316, -91.283, 74.260);
      JointPos j4(-89.575, -80.276, 102.713, -116.302, -91.284, 74.267);
      DescPose desc_pos1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
      DescPose desc_pos2(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
      DescPose desc_pos3(-327.622, 402.230, 320.402, -178.067, 2.127, -46.207);
      DescPose desc_pos4(-104.066, 544.321, 327.023, -177.715, 3.371, -73.818);
      DescPose offset_pos(0, 0, 0, 0, 0, 0);
      ExaxisPos epos(0, 0, 0, 0);
      int tool = 0;
      int user = 0;
      float vel = 100.0;
      float acc = 100.0;
      float ovl = 100.0;
      float blendT = -1.0;
      uint8_t flag = 0;
      robot.SetSpeed(20);
      int err1 = robot.MoveJ(&j1, &desc_pos1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
      printf("movej errcode:%d\n", err1);
      robot.SplineStart();
      robot.SplinePTP(&j1, &desc_pos1, tool, user, vel, acc, ovl);
      robot.SplinePTP(&j2, &desc_pos2, tool, user, vel, acc, ovl);
      robot.SplinePTP(&j3, &desc_pos3, tool, user, vel, acc, ovl);
      robot.SplinePTP(&j4, &desc_pos4, tool, user, vel, acc, ovl);
      robot.SplineEnd();
      err1 = robot.MoveJ(&j1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
      printf("movej errcode:%d\n", err1);
      robot.SplineStart();
      robot.SplinePTP(&j1, tool, user, vel, acc, ovl);
      robot.SplinePTP(&j2, tool, user, vel, acc, ovl);
      robot.SplinePTP(&j3, tool, user, vel, acc, ovl);
      robot.SplinePTP(&j4, tool, user, vel, acc, ovl);
      robot.SplineEnd();
      robot.CloseRPC();
      return 0;
    }

Rozpoczęcie nowego ruchu funkcją sklejaną
+++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Rozpoczęcie nowego ruchu funkcją sklejaną
    * @param [in] type  0-przejście łukowe, 1-punkty zadane są punktami ścieżki
    * @param [in] averageTime Globalny średni czas połączenia (ms) (10 ~ ), domyślnie 2000
    * @return Kod błędu
    */
    errno_t NewSplineStart(int type, int averageTime=2000);

Punkt nowej funkcji sklejanej
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Punkt nowej funkcji sklejanej
    * @param [in] joint_pos Docelowa pozycja stawów, jednostka deg
    * @param [in] desc_pos  Docelowa poza i orientacja w kartezjańskim układzie współrzędnych
    * @param [in] tool Numer układu współrzędnych narzędzia, zakres [0~14]
    * @param [in] user Numer układu współrzędnych obiektu, zakres [0~14]
    * @param [in] vel Procent prędkości, zakres [0~100]
    * @param [in] acc Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param [in] ovl Współczynnik skalowania prędkości, zakres [0~100]
    * @param [in] blendR [-1.0]-ruch do pozycji (blokujący), [0~1000.0]-promień wygładzania (nieblokujący), jednostka mm
    * @param  [in] lastFlag Czy to ostatni punkt, 0-nie, 1-tak
    * @return Kod błędu
    */
    errno_t NewSplinePoint(JointPos *joint_pos, DescPose *desc_pos, int tool, int user, float vel, float acc, float ovl, float blendR, int lastFlag);

Punkt nowej funkcji sklejanej (automatyczne obliczanie odwrotnej kinematyki)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Punkt nowej funkcji sklejanej (automatyczne obliczanie odwrotnej kinematyki)
    * @param [in] desc_pos  Docelowa poza i orientacja w kartezjańskim układzie współrzędnych
    * @param [in] tool Numer układu współrzędnych narzędzia, zakres [0~14]
    * @param [in] user Numer układu współrzędnych obiektu, zakres [0~14]
    * @param [in] vel Procent prędkości, zakres [0~100]
    * @param [in] acc Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param [in] ovl Współczynnik skalowania prędkości, zakres [0~100]
    * @param [in] blendR [-1.0]-ruch do pozycji (blokujący), [0~1000.0]-promień wygładzania (nieblokujący), jednostka mm
    * @param [in] lastFlag Czy to ostatni punkt, 0-nie, 1-tak
    * @param [in] config Konfiguracja przestrzeni stawów dla odwrotnej kinematyki, [-1]-obliczenia w oparciu o bieżącą pozycję stawów, [0~7]-obliczenia zgodnie z określoną konfiguracją przestrzeni stawów
    * @return Kod błędu
    */
    errno_t NewSplinePoint(DescPose* desc_pos, int tool, int user, float vel, float acc, float ovl, float blendR, int lastFlag, int config = -1);

Zakończenie nowego ruchu funkcją sklejaną
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Zakończenie nowego ruchu funkcją sklejaną
    * @return Kod błędu
    */
    errno_t NewSplineEnd();

Przykład kodu nowego ruchu funkcją sklejaną
+++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestNewSpline(void)
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      robot.LoggerInit();
      robot.SetLoggerLevel(1);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return -1;
      }
      robot.SetReConnectParam(true, 30000, 500);
      JointPos j1(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
      JointPos j2(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
      JointPos j3(-61.954, -84.409, 108.153, -116.316, -91.283, 74.260);
      JointPos j4(-89.575, -80.276, 102.713, -116.302, -91.284, 74.267);
      JointPos j5(-95.228, -54.621, 73.691, -112.245, -91.280, 74.268);
      DescPose desc_pos1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
      DescPose desc_pos2(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
      DescPose desc_pos3(-327.622, 402.230, 320.402, -178.067, 2.127, -46.207);
      DescPose desc_pos4(-104.066, 544.321, 327.023, -177.715, 3.371, -73.818);
      DescPose desc_pos5(-33.421, 732.572, 275.103, -177.907, 2.709, -79.482);
      DescPose offset_pos(0, 0, 0, 0, 0, 0);
      ExaxisPos epos(0, 0, 0, 0);
      int tool = 0;
      int user = 0;
      float vel = 100.0;
      float acc = 100.0;
      float ovl = 100.0;
      float blendT = -1.0;
      uint8_t flag = 0;
      robot.SetSpeed(20);
      int err1 = robot.MoveJ(&j1, &desc_pos1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
      printf("movej errcode:%d\n", err1);
      robot.NewSplineStart(1, 2000);
      robot.NewSplinePoint(&j1, &desc_pos1, tool, user, vel, acc, ovl, -1, 0);
      robot.NewSplinePoint(&j2, &desc_pos2, tool, user, vel, acc, ovl, -1, 0);
      robot.NewSplinePoint(&j3, &desc_pos3, tool, user, vel, acc, ovl, -1, 0);
      robot.NewSplinePoint(&j4, &desc_pos4, tool, user, vel, acc, ovl, -1, 0);
      robot.NewSplinePoint(&j5, &desc_pos5, tool, user, vel, acc, ovl, -1, 0);
      robot.NewSplineEnd();
      err1 = robot.MoveJ(&j1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
      printf("movej errcode:%d\n", err1);
      robot.NewSplineStart(1, 2000);
      robot.NewSplinePoint(&desc_pos1, tool, user, vel, acc, ovl, -1, 0);
      robot.NewSplinePoint(&desc_pos2, tool, user, vel, acc, ovl, -1, 0);
      robot.NewSplinePoint(&desc_pos3, tool, user, vel, acc, ovl, -1, 0);
      robot.NewSplinePoint(&desc_pos4, tool, user, vel, acc, ovl, -1, 0);
      robot.NewSplinePoint(&desc_pos5, tool, user, vel, acc, ovl, -1, 0);
      robot.NewSplineEnd();
      robot.CloseRPC();
      return 0;
    }

Zatrzymanie ruchu
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Zatrzymanie ruchu
    * @return  Kod błędu
    */
    errno_t  StopMotion();

Wstrzymanie ruchu
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Wstrzymanie ruchu
    * @return Kod błędu
    */
    errno_t PauseMotion();

Wznowienie ruchu
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Wznowienie ruchu
    * @return Kod błędu
    */
    errno_t ResumeMotion();

Przykład kodu wstrzymywania, wznawiania i zatrzymywania ruchu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     int TestPause(void)
     {
         ROBOT_STATE_PKG pkg = {};
         FRRobot robot;
         robot.LoggerInit();
         robot.SetLoggerLevel(1);
         int rtn = robot.RPC("192.168.58.2");
         if (rtn != 0)
         {
             return -1;
         }
         robot.SetReConnectParam(true, 30000, 500);
         JointPos j1(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
         JointPos j5(-95.228, -54.621, 73.691, -112.245, -91.280, 74.268);
         DescPose desc_pos1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
         DescPose desc_pos5(-33.421, 732.572, 275.103, -177.907, 2.709, -79.482);
         DescPose offset_pos(0, 0, 0, 0, 0, 0);
         ExaxisPos epos(0, 0, 0, 0);
         int tool = 0;
         int user = 0;
         float vel = 100.0;
         float acc = 100.0;
         float ovl = 100.0;
         float blendT = -1.0;
         uint8_t flag = 0;
         robot.SetSpeed(20);
         rtn = robot.MoveJ(&j1, &desc_pos1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
         rtn = robot.MoveJ(&j5, &desc_pos5, tool, user, vel, acc, ovl, &epos, 1, flag, &offset_pos);
         robot.Sleep(1000);
         robot.PauseMotion();
         robot.Sleep(1000);
         robot.ResumeMotion();
         robot.Sleep(1000);
         robot.StopMotion();
         robot.Sleep(1000);
         robot.CloseRPC();
         return 0;
     }

Rozpoczęcie globalnego przesunięcia punktów
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Rozpoczęcie globalnego przesunięcia punktów
    * @param  [in]  flag  0-przesunięcie w układzie bazowym/układzie obiektu, 2-przesunięcie w układzie narzędzia
    * @param  [in] offset_pos  Wartość przesunięcia pozy i orientacji
    * @return  Kod błędu
    */
    errno_t  PointsOffsetEnable(int flag, DescPose *offset_pos);

Zakończenie globalnego przesunięcia punktów
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Zakończenie globalnego przesunięcia punktów
    * @return  Kod błędu
    */
    errno_t  PointsOffsetDisable();

Przykład kodu przesunięcia punktów
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     int TestOffset(void)
     {
         ROBOT_STATE_PKG pkg = {};
         FRRobot robot;
         robot.LoggerInit();
         robot.SetLoggerLevel(1);
         int rtn = robot.RPC("192.168.58.2");
         if (rtn != 0)
         {
             return -1;
         }
         robot.SetReConnectParam(true, 30000, 500);
         JointPos j1(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
         JointPos j2(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
         DescPose desc_pos1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
         DescPose desc_pos2(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
         DescPose offset_pos(0, 0, 0, 0, 0, 0);
         DescPose offset_pos1(0, 0, 50, 0, 0, 0);
         ExaxisPos epos(0, 0, 0, 0);
         int tool = 0;
         int user = 0;
         float vel = 100.0;
         float acc = 100.0;
         float ovl = 100.0;
         float blendT = -1.0;
         uint8_t flag = 0;
         robot.SetSpeed(20);
         robot.MoveJ(&j1, &desc_pos1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
         robot.MoveJ(&j2, &desc_pos2, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
         robot.Sleep(1000);
         robot.PointsOffsetEnable(0, &offset_pos1);
         robot.MoveJ(&j1, &desc_pos1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
         robot.MoveJ(&j2, &desc_pos2, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
         robot.PointsOffsetDisable();
         robot.CloseRPC();
         return 0;
     }

Rozpoczęcie pomiaru przelotowego AO szafy sterowniczej
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Rozpoczęcie pomiaru przelotowego AO szafy sterowniczej
    * @param [in] AONum Numer AO szafy sterowniczej
    * @param [in] maxTCPSpeed Maksymalna wartość prędkości TCP [1-5000mm/s], domyślnie 1000
    * @param [in] maxAOPercent Procent AO odpowiadający maksymalnej wartości prędkości TCP, domyślnie 100%
    * @param [in] zeroZoneCmp Procent AO dla kompensacji martwego pola, liczba całkowita, domyślnie 20%, zakres [0-100]
    * @return Kod błędu
    */
    errno_t MoveAOStart(int AONum, int maxTCPSpeed, int maxAOPercent, int zeroZoneCmp);

Zatrzymanie pomiaru przelotowego AO szafy sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Zatrzymanie pomiaru przelotowego AO szafy sterowniczej
    * @return Kod błędu
    */
    errno_t MoveAOStop();

Rozpoczęcie pomiaru przelotowego AO końcówki
++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Rozpoczęcie pomiaru przelotowego AO końcówki
    * @param [in] AONum Numer AO końcówki
    * @param [in] maxTCPSpeed Maksymalna wartość prędkości TCP [1-5000mm/s], domyślnie 1000
    * @param [in] maxAOPercent Procent AO odpowiadający maksymalnej wartości prędkości TCP, domyślnie 100%
    * @param [in] zeroZoneCmp Procent AO dla kompensacji martwego pola, liczba całkowita, domyślnie 20%, zakres [0-100]
    * @return Kod błędu
    */
    errno_t MoveToolAOStart(int AONum, int maxTCPSpeed, int maxAOPercent, int zeroZoneCmp);

Zatrzymanie pomiaru przelotowego AO końcówki
++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Zatrzymanie pomiaru przelotowego AO końcówki
    * @return Kod błędu
    */
    errno_t MoveToolAOStop();

Przykład kodu pomiaru przelotowego AO
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     int TestMoveAO(void)
     {
         ROBOT_STATE_PKG pkg = {};
         FRRobot robot;
         robot.LoggerInit();
         robot.SetLoggerLevel(1);
         int rtn = robot.RPC("192.168.58.2");
         if (rtn != 0)
         {
             return -1;
         }
         robot.SetReConnectParam(true, 30000, 500);
         JointPos j1(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
         JointPos j2(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
         DescPose desc_pos1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
         DescPose desc_pos2(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
         DescPose offset_pos(0, 0, 0, 0, 0, 0);
         DescPose offset_pos1(0, 0, 50, 0, 0, 0);
         ExaxisPos epos(0, 0, 0, 0);
         int tool = 0;
         int user = 0;
         float vel = 20.0;
         float acc = 20.0;
         float ovl = 100.0;
         float blendT = -1.0;
         uint8_t flag = 0;
         robot.SetSpeed(20);
         robot.MoveAOStart(0, 100, 100, 20);
         robot.MoveJ(&j1, &desc_pos1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
         robot.MoveJ(&j2, &desc_pos2, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
         robot.MoveAOStop();
         robot.Sleep(1000);
         robot.MoveToolAOStart(0, 100, 100, 20);
         robot.MoveJ(&j1, &desc_pos1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
         robot.MoveJ(&j2, &desc_pos2, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
         robot.MoveToolAOStop();
         robot.CloseRPC();
         return 0;
     }

Rozpoczęcie filtracji FIR ruchu PTP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: V3.7.7

.. code-block:: c++
    :linenos:

    /**
    * @brief Rozpoczęcie filtracji FIR ruchu PTP
    * @param [in] maxAcc Maksymalna wartość przyspieszenia (deg/s2)
    * @param [in] maxJek Maksymalna wartość zrywu dla wszystkich stawów (deg/s3)
    * @return Kod błędu
    */
    errno_t PtpFIRPlanningStart(double maxAcc, double maxJek = 1000);

Zakończenie filtracji FIR ruchu PTP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: V3.7.7

.. code-block:: c++
    :linenos:

    /**
	* @brief Zakończenie filtracji FIR ruchu PTP
	* @return Kod błędu
	*/
	errno_t PtpFIRPlanningEnd();

Rozpoczęcie filtracji FIR ruchu LIN i ARC
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: V3.7.7

.. code-block:: c++
    :linenos:

    /**
	* @brief Rozpoczęcie filtracji FIR ruchu LIN i ARC
	* @param [in] maxAccLin Maksymalna wartość liniowego przyspieszenia (mm/s2)
	* @param [in] maxAccDeg Maksymalna wartość kątowego przyspieszenia (deg/s2)
	* @param [in] maxJerkLin Maksymalna wartość liniowego zrywu (mm/s3)
	* @param [in] maxJerkDeg Maksymalna wartość kątowego zrywu (deg/s3)
	* @return Kod błędu
	*/
	errno_t LinArcFIRPlanningStart(double maxAccLin, double maxAccDeg, double maxJerkLin, double maxJerkDeg);

Zakończenie filtracji FIR ruchu LIN i ARC
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: V3.7.7

.. code-block:: c++
    :linenos:

    /**
	* @brief Zakończenie filtracji FIR ruchu LIN i ARC
	* @return Kod błędu
	*/
	errno_t LinArcFIRPlanningEnd();

Przykład kodu filtracji FIR
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

     int TestFIR(void)
     {
         ROBOT_STATE_PKG pkg = {};
         FRRobot robot;
         robot.LoggerInit();
         robot.SetLoggerLevel(1);
         int rtn = robot.RPC("192.168.58.2");
         if (rtn != 0)
         {
             return -1;
         }
         robot.SetReConnectParam(true, 30000, 500);
         JointPos startjointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
         JointPos midjointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
         JointPos endjointPos(-29.777, -84.536, 109.275, -114.075, -86.655, 74.257);
         DescPose startdescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
         DescPose middescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
         DescPose enddescPose(-487.434, 154.362, 308.576, 176.600, 0.268, -14.061);
         ExaxisPos exaxisPos(0, 0, 0, 0);
         DescPose offdese(0, 0, 0, 0, 0, 0);
         rtn = robot.PtpFIRPlanningStart(1000, 1000);
         cout << "PtpFIRPlanningStart rtn is " << rtn << endl;
         robot.MoveJ(&startjointPos, &startdescPose, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.MoveJ(&endjointPos, &enddescPose, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.PtpFIRPlanningEnd();
         cout << "PtpFIRPlanningEnd rtn is " << rtn << endl;
         robot.LinArcFIRPlanningStart(1000, 1000, 1000, 1000);
         cout << "LinArcFIRPlanningStart rtn is " << rtn << endl;
         robot.MoveL(&startjointPos, &startdescPose, 0, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese, 1, 1);
         robot.MoveC(&midjointPos, &middescPose, 0, 0, 100, 100, &exaxisPos, 0, &offdese, &endjointPos, &enddescPose, 0, 0, 100, 100, &exaxisPos, 0, &offdese, 100, -1);
         robot.LinArcFIRPlanningEnd();
         cout << "LinArcFIRPlanningEnd rtn is " << rtn << endl;
         robot.CloseRPC();
         return 0;
     }

Włączenie wygładzania przyspieszenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.1-3.8.1

.. code-block:: c++
    :linenos:

    /**
    * @brief Włączenie wygładzania przyspieszenia
    * @param [in] saveFlag Czy zapisać po odcięciu zasilania
    * @return Kod błędu
    */
    errno_t AccSmoothStart(bool saveFlag);

Wyłączenie wygładzania przyspieszenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.1-3.8.1

.. code-block:: c++
    :linenos:

    /**
    * @brief Wyłączenie wygładzania przyspieszenia
    * @param [in] saveFlag Czy zapisać po odcięciu zasilania
    * @return Kod błędu
    */
    errno_t AccSmoothEnd(bool saveFlag);

Przykład kodu wygładzania przyspieszenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestAccSmooth(void)
     {
         ROBOT_STATE_PKG pkg = {};
         FRRobot robot;
         robot.LoggerInit();
         robot.SetLoggerLevel(1);
         int rtn = robot.RPC("192.168.58.2");
         if (rtn != 0)
         {
             return -1;
         }
         robot.SetReConnectParam(true, 30000, 500);
         JointPos startjointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
         JointPos endjointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
         DescPose startdescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
         DescPose enddescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
         ExaxisPos exaxisPos(0, 0, 0, 0);
         DescPose offdese(0, 0, 0, 0, 0, 0);
         rtn = robot.AccSmoothStart(0);
         cout << "AccSmoothStart rtn is " << rtn << endl;
         robot.MoveJ(&startjointPos, &startdescPose, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.MoveJ(&endjointPos, &enddescPose, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         rtn = robot.AccSmoothEnd(0);
         cout << "AccSmoothEnd rtn is " << rtn << endl;
         robot.CloseRPC();
         return 0;
     }


Włączenie określonej prędkości postawy
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Włączenie określonej prędkości postawy
    * @param [in] ratio Procent prędkości postawy [0-300]
    * @return Kod błędu
    */
    errno_t AngularSpeedStart(int ratio);

Wyłączenie określonej prędkości postawy
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Wyłączenie określonej prędkości postawy
    * @return Kod błędu
    */
    errno_t AngularSpeedEnd();

Przykład kodu określonej prędkości postawy robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestAngularSpeed(void)
     {
         ROBOT_STATE_PKG pkg = {};
         FRRobot robot;
         robot.LoggerInit();
         robot.SetLoggerLevel(1);
         int rtn = robot.RPC("192.168.58.2");
         if (rtn != 0)
         {
             return -1;
         }
         robot.SetReConnectParam(true, 30000, 500);
         JointPos startjointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
         JointPos endjointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
         DescPose startdescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
         DescPose enddescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
         ExaxisPos exaxisPos(0, 0, 0, 0);
         DescPose offdese(0, 0, 0, 0, 0, 0);
         rtn = robot.AngularSpeedStart(50);
         cout << "AngularSpeedStart rtn is " << rtn << endl;
         robot.MoveJ(&startjointPos, &startdescPose, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.MoveJ(&endjointPos, &enddescPose, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         rtn = robot.AngularSpeedEnd();
         cout << "AngularSpeedEnd rtn is " << rtn << endl;
         robot.CloseRPC();
         return 0;
     }

Rozpoczęcie ochrony przed osobliwą pozą i orientacją
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

	/**
	* @brief Rozpoczęcie ochrony przed osobliwą pozą i orientacją
	* @param [in] protectMode Tryb ochrony przed osobliwością, 0: tryb stawów; 1: tryb kartezjański
	* @param [in] minShoulderPos Zakres regulacji osobliwości ramienia (mm), domyślnie 100
	* @param [in] minElbowPos Zakres regulacji osobliwości łokcia (mm), domyślnie 50
	* @param [in] minWristPos Zakres regulacji osobliwości nadgarstka (°), domyślnie 10
	* @return Kod błędu
	*/
	errno_t SingularAvoidStart(int protectMode, double minShoulderPos, double minElbowPos, double minWristPos);

Zatrzymanie ochrony przed osobliwą pozą i orientacją
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

	/**
	* @brief Zatrzymanie ochrony przed osobliwą pozą i orientacją
	* @return Kod błędu
	*/
	errno_t SingularAvoidEnd();

Przykład kodu ochrony przed osobliwą pozą i orientacją robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestAngularSpeed(void)
     {
        ROBOT_STATE_PKG pkg = {};
         FRRobot robot;
         robot.LoggerInit();
         robot.SetLoggerLevel(1);
         int rtn = robot.RPC("192.168.58.2");
         if (rtn != 0)
         {
             return -1;
         }
         robot.SetReConnectParam(true, 30000, 500);
         JointPos startjointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
         JointPos endjointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
         DescPose startdescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
         DescPose enddescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
         ExaxisPos exaxisPos(0, 0, 0, 0);
         DescPose offdese(0, 0, 0, 0, 0, 0);
         rtn = robot.SingularAvoidStart(2, 10, 5, 5);
         cout << "SingularAvoidStart rtn is " << rtn << endl;
         robot.MoveJ(&startjointPos, &startdescPose, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.MoveJ(&endjointPos, &enddescPose, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         rtn = robot.SingularAvoidEnd();
         cout << "SingularAvoidEnd rtn is " << rtn << endl;
         robot.CloseRPC();
         return 0;
     }

Wyczyszczenie kolejki instrukcji ruchu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Wyczyszczenie kolejki instrukcji ruchu
    * @return Kod błędu
    */
    errno_t MotionQueueClear();

Przejazd do punktu początkowego linii przecięcia rur
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Przejazd do punktu początkowego linii przecięcia rur
    * @param [in] mainPoint Pozy i orientacje kartezjańskie 6 punktów nauczania rury głównej
    * @param [in] mainExaxisPos Pozycje osi rozszerzonej dla 6 punktów nauczania rury głównej
    * @param [in] piecePoint Pozy i orientacje kartezjańskie 6 punktów nauczania rury pomocniczej
    * @param [in] pieceExaxisPos Pozycje osi rozszerzonej dla 6 punktów nauczania rury łączącej
    * @param [in] extAxisFlag Czy włączyć oś rozszerzoną; 0-nie włączaj; 1-włącz
    * @param [in] exaxisPos Pozycja osi rozszerzonej punktu początkowego
    * @param [in] tool Numer układu współrzędnych narzędzia
    * @param [in] wobj Numer układu współrzędnych obiektu
    * @param [in] vel Procent prędkości
    * @param [in] acc Procent przyspieszenia
    * @param [in] ovl Współczynnik skalowania prędkości
    * @param [in] oacc Współczynnik skalowania przyspieszenia
    * @param [in] moveType Typ ruchu; 0-PTP; 1-LIN
    * @param [in] moveDirection Kierunek ruchu; 0-zgodnie z ruchem wskazówek zegara; 1-przeciwnie do ruchu wskazówek zegara
    * @param [in] offset Wartość przesunięcia
    * @return Kod błędu
    */
    errno_t MoveToIntersectLineStart(DescPose mainPoint[6], ExaxisPos mainExaxisPos[6], DescPose piecePoint[6], ExaxisPos pieceExaxisPos[6], int extAxisFlag, ExaxisPos exaxisPos, int tool, int wobj, double vel, double acc, double ovl, double oacc, int moveType, int moveDirection, DescPose offset);

Ruch po linii przecięcia rur
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Ruch po linii przecięcia rur
    * @param [in] mainPoint Pozy i orientacje kartezjańskie 6 punktów nauczania rury głównej
    * @param [in] mainExaxisPos Pozycje osi rozszerzonej dla 6 punktów nauczania rury głównej
    * @param [in] piecePoint Pozy i orientacje kartezjańskie 6 punktów nauczania rury pomocniczej
    * @param [in] pieceExaxisPos Pozycje osi rozszerzonej dla 6 punktów nauczania rury łączącej
    * @param [in] extAxisFlag Czy włączyć oś rozszerzoną; 0-nie włączaj; 1-włącz
    * @param [in] exaxisPos Pozycja osi rozszerzonej punktu początkowego
    * @param [in] tool Numer układu współrzędnych narzędzia
    * @param [in] wobj Numer układu współrzędnych obiektu
    * @param [in] vel Procent prędkości
    * @param [in] acc Procent przyspieszenia
    * @param [in] ovl Współczynnik skalowania prędkości
    * @param [in] oacc Współczynnik skalowania przyspieszenia
    * @param [in] moveDirection Kierunek ruchu; 0-zgodnie z ruchem wskazówek zegara; 1-przeciwnie do ruchu wskazówek zegara
    * @param [in] offset Wartość przesunięcia
    * @return Kod błędu
    */
    errno_t MoveIntersectLine(DescPose mainPoint[6], ExaxisPos mainExaxisPos[6], DescPose piecePoint[6], ExaxisPos pieceExaxisPos[6], int extAxisFlag, ExaxisPos exaxisPos[4], int tool, int wobj, double vel, double acc, double ovl, double oacc, int moveDirection, DescPose offset);

Przykład kodu ruchu po linii przecięcia rur robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    void TestIntersectLineMove()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(3);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return ;
        }
        robot.SetReConnectParam(true, 30000, 500);
        DescPose mainPoint[6] = {};
        DescPose piecePoint[6] = {};
        ExaxisPos mainExaxisPos[6] = {};
        ExaxisPos pieceExaxisPos[6] = {};
        int extAxisFlag = 1;
        ExaxisPos exaxisPos[4] = {};
        DescPose offset = { 0.0, 2.0 ,30.0, -2.0, 0.0, 0.0 };
        mainPoint[0] = {490.004, -383.194, 402.735, -9.332, -1.528, 69.594};
        mainPoint[1] = {444.950, -407.117, 389.011, -5.546, -2.196, 65.279};
        mainPoint[2] = {445.168, -463.605, 355.759, -1.544, -10.886, 57.104};
        mainPoint[3] = {507.529, -485.385, 343.013, -0.786, -4.834, 61.799};
        mainPoint[4] = {554.390, -442.647, 367.701, -4.761, -10.181, 64.925};
        mainPoint[5] = {532.552, -394.003, 396.467, -13.732, -13.592, 67.411};
        mainExaxisPos[0] = { -29.996, 0.000, 0.000, 0.000 };
        mainExaxisPos[1] = { -29.996, 0.000, 0.000, 0.000 };
        mainExaxisPos[2] = { -29.996, 0.000, 0.000, 0.000 };
        mainExaxisPos[3] = { -29.996, 0.000, 0.000, 0.000 };
        mainExaxisPos[4] = { -29.996, 0.000, 0.000, 0.000 };
        mainExaxisPos[5] = { -29.996, 0.000, 0.000, 0.000 };
        piecePoint[0] = { 505.571, -192.408, 316.759, 38.098, 37.051, 139.447 };
        piecePoint[1] = {533.837, -201.558, 332.340, 34.644, 42.339, 137.748};
        piecePoint[2] = {530.386, -225.085, 373.808, 35.431, 45.111, 137.560};
        piecePoint[3] = {485.646, -229.195, 383.778, 33.870, 45.173, 137.064};
        piecePoint[4] = {460.551, -212.161, 354.256, 28.856, 45.602, 135.930};
        piecePoint[5] = {474.217, -197.124, 324.611, 42.469, 41.133, 148.167};
        pieceExaxisPos[0] = { -29.996, -0.000, 0.000, 0.000 };
        pieceExaxisPos[1] = { -29.996, -0.000, 0.000, 0.000 };
        pieceExaxisPos[2] = { -29.996, -0.000, 0.000, 0.000 };
        pieceExaxisPos[3] = { -29.996, -0.000, 0.000, 0.000 };
        pieceExaxisPos[4] = { -29.996, -0.000, 0.000, 0.000 };
        pieceExaxisPos[5] = { -29.996, -0.000, 0.000, 0.000 };
        exaxisPos[0] = {-29.996, -0.000, 0.000, 0.000};
        exaxisPos[1] = {-44.994, 90.000, 0.000, 0.000};
        exaxisPos[2] = {-59.992, 0.002, 0.000, 0.000};
        exaxisPos[3] = {-44.994, -89.997, 0.000, 0.000};
        int tool = 2;
        int wobj = 0;
        double vel = 100.0;
        double acc = 100.0;
        double ovl = 12.0;
        double oacc = 12.0;
        int moveType = 1;
        int moveDirection = 1;
        rtn = robot.MoveToIntersectLineStart(mainPoint, mainExaxisPos, piecePoint, pieceExaxisPos, extAxisFlag, exaxisPos[0], tool, wobj, vel, acc, ovl, oacc, moveType, moveDirection, offset);
        printf("MoveToIntersectLineStart rtn is %d\n", rtn);
        rtn = robot.MoveIntersectLine(mainPoint, mainExaxisPos, piecePoint, pieceExaxisPos, extAxisFlag, exaxisPos, tool, wobj, vel, acc, 5.0, 5.0, moveDirection, offset);
        printf("MoveIntersectLine rtn is %d\n", rtn);
        robot.CloseRPC();
        return ;
    }

Ruch w miejscu (bez przemieszczania)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Ruch w miejscu (bez przemieszczania)
    * @return Kod błędu
    */
    errno_t MoveStationary();

Przykład kodu ruchu w miejscu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestLaserStationary(void)
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return 0;
        }
        robot.SetReConnectParam(true, 30000, 500);
        rtn = robot.LaserSensorRecordandReplay(0, 10, 1, 0, 0.1, 1, 0, 10, 100);
        printf("LaserSensorRecordandReplay rtn is %d\n", rtn);
        rtn = robot.MoveStationary();
        printf("MoveStationary rtn is %d\n", rtn);
        rtn = robot.LaserSensorRecord1(0, 10);
        printf("LaserSensorRecordandReplay rtn is %d\n", rtn);
        robot.CloseRPC();
        robot.Sleep(9999999);
        return 0;
    }

Oczekiwanie na Zakończenie Ruchu Pustego w Miejscu
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Oczekuje na zakończenie ruchu pustego w miejscu
    * @return Kod błędu
    */
    errno_t WaitStationaryMotionDone();

Rozpoczęcie wahadła punktowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Rozpoczęcie wahadła punktowego
    * @param [in] weaveNum Numer wahadła [0-7]
    * @param [in] mode 0-układ współrzędnych narzędzia; 1-punkt odniesienia
    * @param [in] refPoint Współrzędne kartezjańskie punktu odniesienia [x, y, z, a, b, c]
    * @param [in] weaveTime Czas wahadła [s]
    * @return Kod błędu
    */
    errno_t OriginPointWeaveStart(int weaveNum, int mode, DescPose refPoint, double weaveTime);

Zakończenie wahadła punktowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Zakończenie wahadła punktowego
    * @return Kod błędu
    */
    errno_t OriginPointWeaveEnd();

Przykład kodu SDK dla wahadła punktowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestOriginPointWeave()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return -1;
        }
        robot.SetReConnectParam(true, 30000, 500);
        JointPos j(39.886, -98.580, -124.032, -47.393, 90.000, 40.842);
        ExaxisPos epos(0, 0, 0, 0);
        DescPose offset_pos(0, 0, 0, 0, 0, 0);
        DescPose refPoint = { 400.021,300.022,299.996,179.997,-0.003,-90.956 };
        robot.MoveJ(&j, 1, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.OriginPointWeaveStart(0, 0, refPoint, 3);
        robot.MoveStationary();
        robot.OriginPointWeaveEnd();
        robot.Sleep(2000);
        robot.MoveJ(&j, 1, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.OriginPointWeaveStart(0, 1, refPoint, 3);
        robot.MoveStationary();
        robot.OriginPointWeaveEnd();
        robot.CloseRPC();
        robot.Sleep(1000);
        return 0;
    }

Przykład kodu wahadła punktowego (z czujnikiem laserowym i osią rozszerzoną)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestOriginPointWeave()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return -1;
        }
        robot.SetReConnectParam(true, 30000, 500);
        JointPos j(39.886, -98.580, -124.032, -47.393, 90.000, 40.842);
        ExaxisPos epos1(0, 0, 0, 0);
        DescPose offset_pos(0, 0, 0, 0, 0, 0);
        ExaxisPos epos2(5, 0.000, 0.000, 0.000);
        DescPose refPoint(400.021, 300.022, 299.996, 179.997, -0.003, -90.956);
        robot.LaserTrackingSensorConfig("192.168.58.20", 5020);
        robot.LaserTrackingSensorSamplePeriod(20);
        robot.LoadPosSensorDriver(101);
        robot.ExtDevLoadUDPDriver();
        rtn = robot.SetExAxisCmdDoneTime(5000.0);
        printf("SetExAxisCmdDoneTime rtn is %d\n" , rtn);
        rtn = robot.ExtAxisServoOn(1, 1);
        printf("ExtAxisServoOn axis id 1 rtn is %d\n" , rtn);
        rtn = robot.ExtAxisServoOn(2, 1);
        printf("ExtAxisServoOn axis id 2 rtn is %d\n" , rtn);
        robot.Sleep(2000);
        robot.ExtAxisSetHoming(1, 0, 10, 2);
        rtn = robot.LaserTrackingLaserOnOff(1, 0);
        printf("LaserTrackingLaserOnOff id 2 rtn is %d\n", rtn);
        robot.LaserTrackingTrackOnOff(1, 4);
        robot.Sleep(200);
        robot.OriginPointWeaveStart(0, 0, refPoint, 10);
        robot.MoveStationary();
        robot.OriginPointWeaveEnd();
        robot.LaserTrackingTrackOnOff(0, 4);

        robot.Sleep(2000);      

        robot.ExtAxisMove(epos1, 100, -1);
        robot.LaserTrackingTrackOnOff(1, 4);
        robot.OriginPointWeaveStart(0, 0, refPoint, 20);
        robot.ExtAxisMove(epos2, 100, -1);
        robot.OriginPointWeaveEnd();
        robot.LaserTrackingTrackOnOff(0, 4);
        robot.CloseRPC();
        robot.Sleep(1000);
        return 0;
    }

Ruch w trybie serwo prędkościowym w przestrzeni stawów
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Ruch w trybie serwo prędkościowym w przestrzeni stawów
    * @param [in] jointVel 6 docelowych prędkości stawów, jednostka deg/s
    * @param [in] axisVel 4 prędkości osi zewnętrznych, jednostka deg/s
    * @param [in] acc Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne, domyślnie 0
    * @param [in] vel Procent prędkości, zakres [0~100], tymczasowo niedostępne, domyślnie 0
    * @param [in] cmdT Okres wysyłania instrukcji, jednostka s, zalecany zakres [0.001~0.0016]
    * @param [in] filterT Czas filtracji, jednostka s, tymczasowo niedostępny, domyślnie 0
    * @param [in] gain Wzmacniacz proporcjonalności pozycji docelowej, tymczasowo niedostępny, domyślnie 0
    * @param [in] id ID instrukcji servoJ, domyślnie 0
    * @param[in] comType Typ wysyłania instrukcji; 0-xmlrpc; 1-UDP (odpowiadający portowi 20007 robota)
    * @return Kod błędu
    */
    errno_t ServoJV(double jointVel[6], double exisVel[4], float acc, float vel, float cmdT, float filterT, float gain, int id = 0, int comType = 0);

Przykład kodu ruchu w trybie serwo prędkościowym w przestrzeni stawów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int ServoJVtest()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        robot.SetReConnectParam(true, 300000, 500);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return -1;
        }
        double joint_vel[6] = { 10.0, 0.0, 0.0, 0.0, 0.0, 0.0 };
        double exis_vel[4] { 0.0, 0.0, 0.0, 0.0 };
        float acc = 0.0f;
        float vel = 0.0f;
        float cmdT = 0.008f;
        float filterT = 0.0f;
        float gain = 0.0f;
        int cnt = 0;
        while (cnt < 200)
        {
            int error = robot.ServoJV(joint_vel, exis_vel, acc, vel, cmdT, filterT, gain);
            printf("ServoJV rtn is %d\n", error);
            cnt++;
        }
        robot.CloseRPC();
        robot.Sleep(1000000);
        return 0;
    }

Rozpoczęcie sterowania MIT stawów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Rozpoczęcie sterowania MIT stawów
    * @param [in] comType Typ wysyłania instrukcji; 0-xmlrpc; 1-UDP (odpowiadający portowi 20007 robota)
    * @return Kod błędu
    */
    errno_t ServoMITStart(int comType = 0);

Zakończenie sterowania MIT stawów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Zakończenie sterowania MIT stawów
    * @param [in] comType Typ wysyłania instrukcji; 0-xmlrpc; 1-UDP (odpowiadający portowi 20007 robota)
    * @return Kod błędu
    */
    errno_t ServoMITEnd(int comType = 0);

Sterowanie MIT stawów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Sterowanie MIT stawów
    * @param [in] posGain Wzmocnienie pozycji stawów j1~j6
    * @param [in] desPos Oczekiwana pozycja stawów j1~j6, jednostka: deg
    * @param [in] velGain Wzmocnienie prędkości stawów j1~j6
    * @param [in] desVel Oczekiwana prędkość stawów j1~j6, jednostka: deg/s
    * @param [in] torque_ff Moment wyprzedzający j1~j6, jednostka: Nm
    * @param [in] interval Okres instrukcji, jednostka s, zakres [0.001~0.008]
    * @param [in] comType Typ wysyłania instrukcji; 0-xmlrpc; 1-UDP (odpowiadający portowi 20007 robota)
    * @return Kod błędu
    */
    errno_t ServoMIT(double posGain[6], double desPos[6], double velGain[6], double desVel[6], double torque_ff[6], double interval, int comType = 0);

Przykład kodu sterowania MIT stawów robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int ServoMITtest()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        robot.SetReConnectParam(true, 30000, 500);
        int rtn = robot.SetCmdRpyCallback(UDPFrameCallBack);
        printf("SetCmdRpyCallback rtn is %d\n", rtn);
        rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return -1;
        }
        while (true)
        {
            robot.ResetAllError();
            robot.Sleep(500);
            double posGain[6] = { 0.0 };
            double desPos[6] = { 0.0 };
            double velGain[6] = { 0.0 };
            double desVel[6] = { 0.0 };
            double torques[6] = { 0.0 };
            float curTorque[6] = { 0.0 };
            robot.GetJointTorques(1, curTorque);
            for (int i = 0; i < 6; i++)
            {
                torques[i] = curTorque[i];
            }
            robot.ServoMITStart(0);
            ROBOT_STATE_PKG pkg = {};
            robot.DragTeachSwitch(1);
            double intev = 0.008;
            double jPowerLimit[6] = { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
            double jVelLimit[6] = { 50, 50, 50, 50, 50, 50 };
            int error = 0;
            while (true)
            {
                torques[5] = 0.02;
                error = robot.ServoMIT(posGain, desPos, velGain, desVel, torques, intev, 0);
                robot.Sleep(1);
                robot.GetRobotRealTimeState(&pkg);
                printf("pkg.jt_cur_pos[5]: %f\n", pkg.jt_cur_pos[5]);
                if (pkg.jt_cur_pos[5] > 30)
                {
                    break;
                }
            }
            while (true)
            {
                torques[5] = -0.02;
                error = robot.ServoMIT(posGain, desPos, velGain, desVel, torques, intev, 0);
                robot.Sleep(1);
                robot.GetRobotRealTimeState(&pkg);
                printf("pkg.jt_cur_pos[5]:%f\n", pkg.jt_cur_pos[5]);
                if (pkg.jt_cur_pos[5] < 0)
                {
                    break;
                }
            }
            robot.DragTeachSwitch(0);
            error = robot.ServoMITEnd(0);
        }
        robot.CloseRPC();
        robot.Sleep(1000000);
        return 0;
    }

Rozpoczęcie Transformacji Punktów Układu Współrzędnych Przedmiotu
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: V3.9.8
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Rozpoczęcie transformacji punktów układu współrzędnych przedmiotu
    * @param [in] workpieceID Numer przedmiotu [0-14]
    * @return Kod błędu, 0 w przypadku sukcesu
    */
    errno_t WorkPieceTrsfStart(int workpieceID);
    
Zakończenie Transformacji Punktów Układu Współrzędnych Przedmiotu
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: V3.9.8

.. code-block:: c++
    :linenos:

    /**
    * @brief Zakończenie transformacji punktów układu współrzędnych przedmiotu
    * @return Kod błędu, 0 w przypadku sukcesu
    */
    errno_t WorkPieceTrsfEnd();
    
Przykład Kodu Ruchu Transformacji Układu Współrzędnych Przedmiotu
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: V3.9.8

.. code-block:: c++
    :linenos:

    int TestWorkPieceTrsf()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        robot.SetReConnectParam(true, 30000, 500);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return 0;
        }
        JointPos j1(-11.188, -64.165, -107.299, -76.706, 89.590, 92.983);
        DescPose desc1(225.986, 190.694, 394.238, -6.230, -23.797, -98.972);
        JointPos j2(-38.148, -97.408, -133.704, -30.999, 89.584, 92.986);
        DescPose desc2(52.741, 262.917, 30.824, -5.696, -9.864, -126.092);
        JointPos j3(-25.561, -123.131, -85.736, -94.911, 89.582, 93.006);
        DescPose desc3(70.455, 88.410, 45.299, -4.101, 31.775, -113.199);
        JointPos j4(-8.013, -125.881, -79.196, -84.440, 89.564, 93.005);
        DescPose desc4(209.453, -73.895, 56.416, -4.727, 17.523, -95.906);
        JointPos j5(-2.722, -94.518, -119.965, -54.518, 89.563, 93.005);
        DescPose desc5(274.800, 81.106, 102.977, -5.467, -2.980, -90.711);
        JointPos j6(-2.671, -56.234, -138.914, -25.099, 95.355, 92.967);
        DescPose desc6(300.392, 177.281, 300.926, -1.909, -51.894, -89.703);
        JointPos j7(-1.229, -121.184, -63.201, -122.331, 93.045, 93.019);
        DescPose desc7(296.856, -31.294, 215.698, -0.589, 34.594, -88.954);
        ExaxisPos exaxis = {0.0, 0.0, 0.0, 0.0};
        DescPose offset(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);
        int tool = 1;
        int workpiece = 1;
        double blend = 5.0;
        robot.MoveJ(&j1, &desc1, tool, workpiece, 100, 100, 100, &exaxis, -1, 0, &offset);
        robot.MoveJ(&j2, &desc2, tool, workpiece, 100, 100, 100, &exaxis, blend, 0, &offset);
        robot.MoveL(&j3, &desc3, tool, workpiece, 10, 100, 100, blend, 0, &exaxis, 0, 1, &offset);
        robot.MoveC(&j4, &desc4, tool, workpiece, 100, 100, &exaxis, 0, &offset, &j5, &desc5, tool, workpiece, 100, 100, &exaxis, 0, &offset, 10, blend);
        robot.Circle(&j6, &desc6, tool, workpiece, 100, 100, &exaxis, &j7, &desc7, tool, workpiece, 100, 100, &exaxis, 10, 0, &offset, 100.0, blend);
        rtn = robot.WorkPieceTrsfStart(2);
        printf("WorkPieceTrsfStart rtn is %d\n", rtn);
        robot.MoveJ(&j1, &desc1, tool, workpiece, 100, 100, 100, &exaxis, -1, 0, &offset);
        robot.MoveJ(&j2, &desc2, tool, workpiece, 100, 100, 100, &exaxis, blend, 0, &offset);
        robot.MoveL(&j3, &desc3, tool, workpiece, 10, 100, 100, blend, 0, &exaxis, 0, 1, &offset);
        robot.MoveC(&j4, &desc4, tool, workpiece, 100, 100, &exaxis, 0, &offset, &j5, &desc5, tool, workpiece, 100, 100, &exaxis, 0, &offset, 10, blend);
        robot.Circle(&j6, &desc6, tool, workpiece, 100, 100, &exaxis, &j7, &desc7, tool, workpiece, 100, 100, &exaxis, 10, 0, &offset, 100.0, blend);    
        rtn = robot.WorkPieceTrsfEnd();
        printf("WorkPieceTrsfEnd rtn is %d\n", rtn);
        robot.CloseRPC();
        robot.Sleep(2000);
    }    