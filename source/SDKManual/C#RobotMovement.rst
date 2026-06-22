Ruch robota
===========

.. toctree:: 
    :maxdepth: 5

Punktowanie JOG
+++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Punktowanie JOG 
    * @param [in] refType Typ punktowania: 0-punktowanie stawów, 2-punktowanie w podstawowym układzie współrzędnych, 4-punktowanie w układzie współrzędnych narzędzia, 8-punktowanie w układzie współrzędnych przedmiotu 
    * @param [in] nb 1-staw 1 (lub oś x), 2-staw 2 (lub oś y), 3-staw 3 (lub oś z), 4-staw 4 (lub obrót wokół osi x), 5-staw 5 (lub obrót wokół osi y), 6-staw 6 (lub obrót wokół osi z)
    * @param [in] dir 0-kierunek ujemny, 1-kierunek dodatni 
    * @param [in] vel Procent prędkości, [0~100] 
    * @param [in] acc Procent przyspieszenia, [0~100] 
    * @param [in] max_dis Maksymalny kąt pojedynczego punktowania, jednostka [°] lub odległość, jednostka [mm] 
    * @return Kod błędu 
    */ 
    int StartJOG(byte refType, byte nb, byte dir, float vel, float acc, float max_dis);

Zatrzymanie punktowania JOG z redukcją prędkości
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Zatrzymanie punktowania JOG z redukcją prędkości
    * @param [in] stopType 1-zatrzymanie punktowania stawów, 3-zatrzymanie punktowania w podstawowym układzie współrzędnych, 5-zatrzymanie punktowania w układzie współrzędnych narzędzia, 9-zatrzymanie punktowania w układzie współrzędnych przedmiotu
    * @return Kod błędu
    */
    int StopJOG(byte stopType);

Natychmiastowe zatrzymanie punktowania JOG
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Natychmiastowe zatrzymanie punktowania JOG
    * @return Kod błędu
    */
    int ImmStopJOG(); 

Przykład kodu sterowania punktowaniem robota
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnJOG_Click(object sender, EventArgs e)
    {
        Robot robot = new Robot();
        robot.RPC("192.168.58.2"); 

        robot.SetSpeed(35);
        robot.StartJOG(0, 1, 0, 15, 20.0f, 30.0f);   // Ruch pojedynczego stawu, StartJOG jest instrukcją nieblokującą, inne instrukcje ruchu (w tym StartJOG) są odrzucane w stanie ruchu
        Thread.Sleep(1000);
        robot.StopJOG(1);  // Zatrzymanie punktowania jednoosiowego robota z redukcją prędkości
        //robot.ImmStopJOG();  // Natychmiastowe zatrzymanie punktowania jednoosiowego robota
        robot.StartJOG(0, 2, 1, 15, 20.0f, 30.0f);
        Thread.Sleep(1000);
        robot.ImmStopJOG();
        robot.StartJOG(0, 3, 1, 15, 20.0f, 30.0f);
        Thread.Sleep(1000);
        robot.ImmStopJOG();
        robot.StartJOG(0, 4, 1, 15, 20.0f, 30.0f);
        Thread.Sleep(1000);
        robot.ImmStopJOG();
        robot.StartJOG(0, 5, 1, 15, 20.0f, 30.0f);
        Thread.Sleep(1000);
        robot.ImmStopJOG();
        robot.StartJOG(0, 6, 1, 15, 20.0f, 30.0f);
        Thread.Sleep(1000);
        robot.ImmStopJOG();

        robot.StartJOG(2, 1, 0, 15, 20.0f, 30.0f);   // Punktowanie w podstawowym układzie współrzędnych
        Thread.Sleep(1000);
        robot.StopJOG(3);  // Zatrzymanie punktowania jednoosiowego robota z redukcją prędkości
        //robot.ImmStopJOG();  // Natychmiastowe zatrzymanie punktowania jednoosiowego robota
        robot.StartJOG(2, 2, 1, 15, 20.0f, 30.0f);
        Thread.Sleep(1000);
        robot.ImmStopJOG();
        robot.StartJOG(2, 3, 1, 15, 20.0f, 30.0f);
        Thread.Sleep(1000);
        robot.ImmStopJOG();
        robot.StartJOG(2, 4, 1, 15, 20.0f, 30.0f);
        Thread.Sleep(1000);
        robot.ImmStopJOG();
        robot.StartJOG(2, 5, 1, 15, 20.0f, 30.0f);
        Thread.Sleep(1000);
        robot.ImmStopJOG();
        robot.StartJOG(2, 6, 1, 15, 20.0f, 30.0f);
        Thread.Sleep(1000);
        robot.ImmStopJOG();

        robot.StartJOG(4, 1, 0, 15, 20.0f, 30.0f);   // Punktowanie w układzie współrzędnych narzędzia
        Thread.Sleep(1000);
        robot.StopJOG(5);  // Zatrzymanie punktowania jednoosiowego robota z redukcją prędkości
        //robot.ImmStopJOG();  // Natychmiastowe zatrzymanie punktowania jednoosiowego robota
        robot.StartJOG(4, 2, 1, 15, 20.0f, 30.0f);
        Thread.Sleep(1000);
        robot.ImmStopJOG();
        robot.StartJOG(4, 3, 1, 15, 20.0f, 30.0f);
        Thread.Sleep(1000);
        robot.ImmStopJOG();
        robot.StartJOG(4, 4, 1, 15, 20.0f, 30.0f);
        Thread.Sleep(1000);
        robot.ImmStopJOG();
        robot.StartJOG(4, 5, 1, 15, 20.0f, 30.0f);
        Thread.Sleep(1000);
        robot.ImmStopJOG();
        robot.StartJOG(4, 6, 1, 15, 20.0f, 30.0f);
        Thread.Sleep(1000);
        robot.ImmStopJOG();

        robot.StartJOG(8, 1, 0, 15, 20.0f, 30.0f);   // Punktowanie w układzie współrzędnych przedmiotu
        Thread.Sleep(1000);
        robot.StopJOG(9);  // Zatrzymanie punktowania jednoosiowego robota z redukcją prędkości
        //robot.ImmStopJOG();  // Natychmiastowe zatrzymanie punktowania jednoosiowego robota
        robot.StartJOG(8, 2, 1, 15, 20.0f, 30.0f);
        Thread.Sleep(1000);
        robot.ImmStopJOG();
        robot.StartJOG(8, 3, 1, 15, 20.0f, 30.0f);
        Thread.Sleep(1000);
        robot.ImmStopJOG();
        robot.StartJOG(8, 4, 1, 15, 20.0f, 30.0f);
        Thread.Sleep(1000);
        robot.ImmStopJOG();
        robot.StartJOG(8, 5, 1, 15, 20.0f, 30.0f);
        Thread.Sleep(1000);
        robot.ImmStopJOG();
        robot.StartJOG(8, 6, 1, 15, 20.0f, 30.0f);
        Thread.Sleep(1000);
        robot.ImmStopJOG();
    }

Ruch w przestrzeni stawów
++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ruch w przestrzeni stawów
    * @param  [in] joint_pos  Docelowa pozycja stawów, jednostka deg
    * @param  [in] desc_pos   Docelowa pozycja i orientacja kartezjańska
    * @param  [in] tool  Numer układu współrzędnych narzędzia, zakres [0~14]
    * @param  [in] user  Numer układu współrzędnych przedmiotu, zakres [0~14]
    * @param  [in] vel  Procent prędkości, zakres [0~100]
    * @param  [in] acc  Procent przyspieszenia, zakres [0~100], tymczasowo nieudostępnione
    * @param  [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]
    * @param  [in] epos  Pozycja osi rozszerzonej, jednostka mm
    * @param  [in] blendT [-1.0]-ruch do pozycji (blokujący), [0~500.0]-czas wygładzenia (nieblokujący), jednostka ms
    * @param  [in] offset_flag  0-brak przesunięcia, 1-przesunięcie w podstawowym układzie współrzędnych / układzie współrzędnych przedmiotu, 2-przesunięcie w układzie współrzędnych narzędzia
    * @param  [in] offset_pos  Wartość przesunięcia pozycji i orientacji
    * @return  Kod błędu
    */
    int MoveJ(JointPos joint_pos, DescPose desc_pos, int tool, int user, float vel, float acc, float ovl, ExaxisPos epos, float blendT, byte offset_flag, DescPose offset_pos); 

Ruch w przestrzeni stawów (automatyczne obliczenie kinematyki prostej)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /** 
    * @brief  Ruch w przestrzeni stawów (automatyczne obliczenie kinematyki prostej)
    * @param  [in] joint_pos  Docelowa pozycja stawów, jednostka deg
    * @param  [in] tool  Numer układu współrzędnych narzędzia, zakres [0~14]
    * @param  [in] user  Numer układu współrzędnych przedmiotu, zakres [0~14]
    * @param  [in] vel  Procent prędkości, zakres [0~100]
    * @param  [in] acc  Procent przyspieszenia, zakres [0~100], tymczasowo nieudostępnione
    * @param  [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]
    * @param  [in] epos  Pozycja osi rozszerzonej, jednostka mm
    * @param  [in] blendT [-1.0]-ruch do pozycji (blokujący), [0~500.0]-czas wygładzenia (nieblokujący), jednostka ms
    * @param  [in] offset_flag  0-brak przesunięcia, 1-przesunięcie w podstawowym układzie współrzędnych / układzie współrzędnych przedmiotu, 2-przesunięcie w układzie współrzędnych narzędzia
    * @param  [in] offset_pos  Wartość przesunięcia pozycji i orientacji
    * @return Kod błędu 
    */ 
    int MoveJ(JointPos joint_pos, int tool, int user, double vel, double acc, double ovl, ExaxisPos epos, double blendT, int offset_flag, DescPose offset_pos)

Ruch liniowy w przestrzeni kartezjańskiej
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ruch liniowy w przestrzeni kartezjańskiej
    * @param [in] joint_pos Docelowa pozycja stawów, jednostka deg
    * @param [in] desc_pos Docelowa pozycja i orientacja kartezjańska
    * @param [in] tool Numer układu współrzędnych narzędzia, zakres [0~14]
    * @param [in] user Numer układu współrzędnych przedmiotu, zakres [0~14]
    * @param [in] vel Procent prędkości, zakres [0~100]
    * @param [in] acc Procent przyspieszenia, zakres [0~100], tymczasowo nieudostępnione
    * @param [in] ovl Współczynnik skalowania prędkości [0~100] / prędkość fizyczna (mm/s)
    * @param [in] blendR [-1.0]-ruch do pozycji (blokujący), [0~1000.0]-promień wygładzenia (nieblokujący), jednostka mm
    * @param [in] blendMode Sposób przejścia; 0-przejście styczne; 1-przejście narożne
    * @param [in] epos Pozycja osi rozszerzonej, jednostka mm
    * @param [in] search 0-brak pozycjonowania drutem spawalniczym, 1-pozycjonowanie drutem spawalniczym
    * @param [in] offset_flag 0-brak przesunięcia, 1-przesunięcie w podstawowym układzie współrzędnych / układzie współrzędnych przedmiotu, 2-przesunięcie w układzie współrzędnych narzędzia
    * @param [in] offset_pos Wartość przesunięcia pozycji i orientacji
    * @param [in] oacc Współczynnik skalowania przyspieszenia [0-100] / przyspieszenie fizyczne (mm/s²)
    * @param [in] velAccParamMode Tryb parametrów prędkości i przyspieszenia; 0-procent; 1-prędkość fizyczna (mm/s) przyspieszenie (mm/s²)
    * @param [in] overSpeedStrategy Strategia obsługi przekroczenia prędkości, 1-standard; 2-zatrzymaj z błędem po przekroczeniu prędkości; 3-adaptacyjne zmniejszenie prędkości, domyślnie 0
    * @param [in] speedPercent Dopuszczalny próg procentowy zmniejszenia prędkości [0-100], domyślnie 10%
    * @return Kod błędu
    */
    public int MoveL(JointPos joint_pos, DescPose desc_pos, int tool, int user, float vel, float acc, float ovl, float blendR, int blendMode, ExaxisPos epos, int search, int offset_flag, DescPose offset_pos, float oacc, int velAccParamMode, int overSpeedStrategy = 0, int speedPercent = 10)

Ruch liniowy w przestrzeni kartezjańskiej (automatyczne obliczenie kinematyki odwrotnej)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Ruch liniowy w przestrzeni kartezjańskiej (automatyczne obliczenie kinematyki odwrotnej)
    * @param [in] desc_pos   Docelowa pozycja i orientacja kartezjańska
    * @param [in] tool  Numer układu współrzędnych narzędzia, zakres [1~15]
    * @param [in] user  Numer układu współrzędnych przedmiotu, zakres [1~15]
    * @param [in] vel  Procent prędkości, zakres [0~100]
    * @param [in] acc  Procent przyspieszenia, zakres [0~100], tymczasowo nieudostępnione
    * @param [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]
    * @param [in] blendR [-1.0]-ruch do pozycji (blokujący), [0~1000.0]-promień wygładzenia (nieblokujący), jednostka mm
    * @param [in] blendMode Sposób przejścia; 0-przejście styczne; 1-przejście narożne
    * @param [in] epos  Pozycja osi rozszerzonej, jednostka mm
    * @param [in] search  0-brak pozycjonowania drutem spawalniczym, 1-pozycjonowanie drutem spawalniczym
    * @param [in] offset_flag  0-brak przesunięcia, 1-przesunięcie w podstawowym układzie współrzędnych / układzie współrzędnych przedmiotu, 2-przesunięcie w układzie współrzędnych narzędzia
    * @param [in] offset_pos  Wartość przesunięcia pozycji i orientacji
    * @param [in] config Konfiguracja przestrzeni stawów dla rozwiązania odwrotnego, [-1]-obliczenie z odniesieniem do bieżącej pozycji stawów, [0~7]-rozwiązanie zgodnie z określoną konfiguracją przestrzeni stawów
    * @param [in] overSpeedStrategy  Strategia obsługi przekroczenia prędkości, 1-standard; 2-zatrzymaj z błędem po przekroczeniu prędkości; 3-adaptacyjne zmniejszenie prędkości, domyślnie 0
    * @param [in] speedPercent  Dopuszczalny próg procentowy zmniejszenia prędkości [0-100], domyślnie 10%
    * @return  Kod błędu
    */
    int MoveL(DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, int blendMode, ExaxisPos epos, int search, int offset_flag, DescPose offset_pos, int config, int overSpeedStrategy, int speedPercent)

Ruch liniowy w przestrzeni kartezjańskiej (z dodanym parametrem trybu parametrów velAccParamMode)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Ruch liniowy w przestrzeni kartezjańskiej (z dodanym parametrem trybu parametrów velAccParamMode)
    * @param  [in] joint_pos  Docelowa pozycja stawów, jednostka deg
    * @param  [in] desc_pos   Docelowa pozycja i orientacja kartezjańska
    * @param  [in] tool  Numer układu współrzędnych narzędzia, zakres [1~15]
    * @param  [in] user  Numer układu współrzędnych przedmiotu, zakres [1~15]
    * @param  [in] vel  Procent prędkości, zakres [0~100]
    * @param  [in] acc  Procent przyspieszenia, zakres [0~100], tymczasowo nieudostępnione
    * @param  [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]
    * @param  [in] blendR [-1.0]-ruch do pozycji (blokujący), [0~1000.0]-promień wygładzenia (nieblokujący), jednostka mm
    * @param  [in] epos  Pozycja osi rozszerzonej, jednostka mm
    * @param  [in] search  0-brak pozycjonowania drutem spawalniczym, 1-pozycjonowanie drutem spawalniczym
    * @param  [in] offset_flag  0-brak przesunięcia, 1-przesunięcie w podstawowym układzie współrzędnych / układzie współrzędnych przedmiotu, 2-przesunięcie w układzie współrzędnych narzędzia
    * @param  [in] offset_pos  Wartość przesunięcia pozycji i orientacji
    * @param  [in] velAccParamMode Tryb parametrów prędkości i przyspieszenia; 0-procent; 1-prędkość fizyczna (mm/s) przyspieszenie (mm/s²)
    * @param  [in] overSpeedStrategy  Strategia obsługi przekroczenia prędkości, 1-standard; 2-zatrzymaj z błędem po przekroczeniu prędkości; 3-adaptacyjne zmniejszenie prędkości, domyślnie 0
    * @param  [in] speedPercent  Dopuszczalny próg procentowy zmniejszenia prędkości [0-100], domyślnie 10%
    * @return  Kod błędu
    */
    public int MoveL(JointPos joint_pos, DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, ExaxisPos epos, int search, int offset_flag, DescPose offset_pos, int velAccParamMode, int overSpeedStrategy, int speedPercent)

Ruch liniowy w przestrzeni kartezjańskiej (przeciążona funkcja 1 z dodanym blendMode)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Ruch liniowy w przestrzeni kartezjańskiej (przeciążona funkcja 1 z dodanym blendMode)
    * @param  [in] joint_pos  Docelowa pozycja stawów, jednostka deg
    * @param  [in] desc_pos   Docelowa pozycja i orientacja kartezjańska
    * @param  [in] tool  Numer układu współrzędnych narzędzia, zakres [1~15]
    * @param  [in] user  Numer układu współrzędnych przedmiotu, zakres [1~15]
    * @param  [in] vel  Procent prędkości, zakres [0~100]
    * @param  [in] acc  Procent przyspieszenia, zakres [0~100], tymczasowo nieudostępnione
    * @param  [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]
    * @param  [in] blendR [-1.0]-ruch do pozycji (blokujący), [0~1000.0]-promień wygładzenia (nieblokujący), jednostka mm
    * @param  [in] blendMode Sposób przejścia; 0-przejście styczne; 1-przejście narożne
    * @param  [in] epos  Pozycja osi rozszerzonej, jednostka mm
    * @param  [in] search  0-brak pozycjonowania drutem spawalniczym, 1-pozycjonowanie drutem spawalniczym
    * @param  [in] offset_flag  0-brak przesunięcia, 1-przesunięcie w podstawowym układzie współrzędnych / układzie współrzędnych przedmiotu, 2-przesunięcie w układzie współrzędnych narzędzia
    * @param  [in] offset_pos  Wartość przesunięcia pozycji i orientacji
    * @param  [in] velAccParamMode Tryb parametrów prędkości i przyspieszenia; 0-procent; 1-prędkość fizyczna (mm/s) przyspieszenie (mm/s²)
    * @param  [in] overSpeedStrategy  Strategia obsługi przekroczenia prędkości, 1-standard; 2-zatrzymaj z błędem po przekroczeniu prędkości; 3-adaptacyjne zmniejszenie prędkości, domyślnie 0
    * @param  [in] speedPercent  Dopuszczalny próg procentowy zmniejszenia prędkości [0-100], domyślnie 10%
    * @return  Kod błędu
    */
    public int MoveL(JointPos joint_pos, DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, int blendMode, ExaxisPos epos, int search, int offset_flag, DescPose offset_pos, int velAccParamMode, int overSpeedStrategy, int speedPercent)

Ruch liniowy w przestrzeni kartezjańskiej (przeciążona funkcja 2 - nie wymaga wprowadzania pozycji stawów)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Ruch liniowy w przestrzeni kartezjańskiej (przeciążona funkcja 2 - nie wymaga wprowadzania pozycji stawów)
    * @param  [in] desc_pos   Docelowa pozycja i orientacja kartezjańska
    * @param  [in] tool  Numer układu współrzędnych narzędzia, zakres [1~15]
    * @param  [in] user  Numer układu współrzędnych przedmiotu, zakres [1~15]
    * @param  [in] vel  Procent prędkości, zakres [0~100]
    * @param  [in] acc  Procent przyspieszenia, zakres [0~100], tymczasowo nieudostępnione
    * @param  [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]
    * @param  [in] blendR [-1.0]-ruch do pozycji (blokujący), [0~1000.0]-promień wygładzenia (nieblokujący), jednostka mm
    * @param  [in] blendMode Sposób przejścia; 0-przejście styczne; 1-przejście narożne
    * @param  [in] epos  Pozycja osi rozszerzonej, jednostka mm
    * @param  [in] search  0-brak pozycjonowania drutem spawalniczym, 1-pozycjonowanie drutem spawalniczym
    * @param  [in] offset_flag  0-brak przesunięcia, 1-przesunięcie w podstawowym układzie współrzędnych / układzie współrzędnych przedmiotu, 2-przesunięcie w układzie współrzędnych narzędzia
    * @param  [in] offset_pos  Wartość przesunięcia pozycji i orientacji
    * @param  [in] config Konfiguracja przestrzeni stawów dla rozwiązania odwrotnego, [-1]-obliczenie z odniesieniem do bieżącej pozycji stawów, [0~7]-rozwiązanie zgodnie z określoną konfiguracją przestrzeni stawów
    * @param  [in] velAccParamMode Tryb parametrów prędkości i przyspieszenia; 0-procent; 1-prędkość fizyczna (mm/s) przyspieszenie (mm/s²)
    * @param  [in] overSpeedStrategy  Strategia obsługi przekroczenia prędkości, 1-standard; 2-zatrzymaj z błędem po przekroczeniu prędkości; 3-adaptacyjne zmniejszenie prędkości, domyślnie 0
    * @param  [in] speedPercent  Dopuszczalny próg procentowy zmniejszenia prędkości [0-100], domyślnie 10%
    * @return  Kod błędu
    */
    public int MoveL(DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, int blendMode, ExaxisPos epos, int search, int offset_flag, DescPose offset_pos, int config, int velAccParamMode, int overSpeedStrategy, int speedPercent)

Ruch łukowy w przestrzeni kartezjańskiej
++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ruch łukowy w przestrzeni kartezjańskiej
    * @param  [in] joint_pos_p  Pozycja stawów punktu pośredniego, jednostka deg
    * @param  [in] desc_pos_p   Pozycja i orientacja kartezjańska punktu pośredniego
    * @param  [in] ptool  Numer układu współrzędnych narzędzia, zakres [0~14]
    * @param  [in] puser  Numer układu współrzędnych przedmiotu, zakres [0~14]
    * @param  [in] pvel  Procent prędkości, zakres [0~100]
    * @param  [in] pacc  Procent przyspieszenia, zakres [0~100], tymczasowo nieudostępnione
    * @param  [in] epos_p  Pozycja osi rozszerzonej punktu pośredniego, jednostka mm
    * @param  [in] poffset_flag  0-brak przesunięcia, 1-przesunięcie w podstawowym układzie współrzędnych / układzie współrzędnych przedmiotu, 2-przesunięcie w układzie współrzędnych narzędzia
    * @param  [in] offset_pos_p  Wartość przesunięcia pozycji i orientacji
    * @param  [in] joint_pos_t  Pozycja stawów punktu docelowego, jednostka deg
    * @param  [in] desc_pos_t   Pozycja i orientacja kartezjańska punktu docelowego
    * @param  [in] ttool  Numer układu współrzędnych narzędzia, zakres [0~14]
    * @param  [in] tuser  Numer układu współrzędnych przedmiotu, zakres [0~14]
    * @param  [in] tvel  Procent prędkości, zakres [0~100]
    * @param  [in] tacc  Procent przyspieszenia, zakres [0~100], tymczasowo nieudostępnione
    * @param  [in] epos_t  Pozycja osi rozszerzonej punktu docelowego, jednostka mm
    * @param  [in] toffset_flag  0-brak przesunięcia, 1-przesunięcie w podstawowym układzie współrzędnych / układzie współrzędnych przedmiotu, 2-przesunięcie w układzie współrzędnych narzędzia
    * @param  [in] offset_pos_t  Wartość przesunięcia pozycji i orientacji
    * @param  [in] ovl  Współczynnik skalowania prędkości [0~100] / prędkość fizyczna (mm/s)
    * @param  [in] blendR [-1.0]-ruch do pozycji (blokujący), [0~1000.0]-promień wygładzenia (nieblokujący), jednostka mm
    * @param  [in] oacc Współczynnik skalowania przyspieszenia [0-100] / przyspieszenie fizyczne (mm/s²)
    * @param  [in] velAccParamMode Tryb parametrów prędkości i przyspieszenia; 0-procent; 1-prędkość fizyczna (mm/s) przyspieszenie (mm/s²)
    * @return  Kod błędu
    */
    public int MoveC(JointPos joint_pos_p, DescPose desc_pos_p, int ptool, int puser, float pvel, float pacc,ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p,JointPos joint_pos_t, DescPose desc_pos_t, int ttool, int tuser, float tvel, float tacc,ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t,float ovl, float blendR, float oacc, int velAccParamMode)

Ruch łukowy w przestrzeni kartezjańskiej (automatyczne obliczenie kinematyki odwrotnej)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Ruch łukowy w przestrzeni kartezjańskiej (automatyczne obliczenie kinematyki odwrotnej)
    * @param [in] desc_pos_p   Pozycja i orientacja kartezjańska punktu pośredniego
    * @param [in] ptool  Numer układu współrzędnych narzędzia, zakres [1~15]
    * @param [in] puser  Numer układu współrzędnych przedmiotu, zakres [1~15]
    * @param [in] pvel  Procent prędkości, zakres [0~100]
    * @param [in] pacc  Procent przyspieszenia, zakres [0~100], tymczasowo nieudostępnione
    * @param [in] epos_p  Pozycja osi rozszerzonej punktu pośredniego, jednostka mm
    * @param [in] poffset_flag  0-brak przesunięcia, 1-przesunięcie w podstawowym układzie współrzędnych / układzie współrzędnych przedmiotu, 2-przesunięcie w układzie współrzędnych narzędzia
    * @param [in] offset_pos_p  Wartość przesunięcia pozycji i orientacji
    * @param [in] desc_pos_t   Pozycja i orientacja kartezjańska punktu docelowego
    * @param [in] ttool  Numer układu współrzędnych narzędzia, zakres [1~15]
    * @param [in] tuser  Numer układu współrzędnych przedmiotu, zakres [1~15]
    * @param [in] tvel  Procent prędkości, zakres [0~100]
    * @param [in] tacc  Procent przyspieszenia, zakres [0~100], tymczasowo nieudostępnione
    * @param [in] epos_t  Pozycja osi rozszerzonej punktu docelowego, jednostka mm
    * @param [in] toffset_flag  0-brak przesunięcia, 1-przesunięcie w podstawowym układzie współrzędnych / układzie współrzędnych przedmiotu, 2-przesunięcie w układzie współrzędnych narzędzia
    * @param [in] offset_pos_t  Wartość przesunięcia pozycji i orientacji
    * @param [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]
    * @param [in] blendR [-1.0]-ruch do pozycji (blokujący), [0~1000.0]-promień wygładzenia (nieblokujący), jednostka mm
    * @param [in] config Konfiguracja przestrzeni stawów dla rozwiązania odwrotnego, [-1]-obliczenie z odniesieniem do bieżącej pozycji stawów, [0~7]-rozwiązanie zgodnie z określoną konfiguracją przestrzeni stawów
    * @return  Kod błędu
    */
    int MoveC(DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t, double ovl, double blendR, int config)

Ruch łukowy w przestrzeni kartezjańskiej (z dodanym parametrem trybu parametrów velAccParamMode)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Ruch łukowy w przestrzeni kartezjańskiej (z dodanym parametrem trybu parametrów velAccParamMode)
    * @param  [in] joint_pos_p  Pozycja stawów punktu pośredniego, jednostka deg
    * @param  [in] desc_pos_p   Pozycja i orientacja kartezjańska punktu pośredniego
    * @param  [in] ptool  Numer układu współrzędnych narzędzia, zakres [1~15]
    * @param  [in] puser  Numer układu współrzędnych przedmiotu, zakres [1~15]
    * @param  [in] pvel  Procent prędkości, zakres [0~100]
    * @param  [in] pacc  Procent przyspieszenia, zakres [0~100], tymczasowo nieudostępnione
    * @param  [in] epos_p  Pozycja osi rozszerzonej punktu pośredniego, jednostka mm
    * @param  [in] poffset_flag  0-brak przesunięcia, 1-przesunięcie w podstawowym układzie współrzędnych / układzie współrzędnych przedmiotu, 2-przesunięcie w układzie współrzędnych narzędzia
    * @param  [in] offset_pos_p  Wartość przesunięcia pozycji i orientacji
    * @param  [in] joint_pos_t  Pozycja stawów punktu docelowego, jednostka deg
    * @param  [in] desc_pos_t   Pozycja i orientacja kartezjańska punktu docelowego
    * @param  [in] ttool  Numer układu współrzędnych narzędzia, zakres [1~15]
    * @param  [in] tuser  Numer układu współrzędnych przedmiotu, zakres [1~15]
    * @param  [in] tvel  Procent prędkości, zakres [0~100]
    * @param  [in] tacc  Procent przyspieszenia, zakres [0~100], tymczasowo nieudostępnione
    * @param  [in] epos_t  Pozycja osi rozszerzonej punktu docelowego, jednostka mm
    * @param  [in] toffset_flag  0-brak przesunięcia, 1-przesunięcie w podstawowym układzie współrzędnych / układzie współrzędnych przedmiotu, 2-przesunięcie w układzie współrzędnych narzędzia
    * @param  [in] offset_pos_t  Wartość przesunięcia pozycji i orientacji
    * @param  [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]
    * @param  [in] blendR [-1.0]-ruch do pozycji (blokujący), [0~1000.0]-promień wygładzenia (nieblokujący), jednostka mm
    * @param  [in] velAccParamMode Tryb parametrów prędkości i przyspieszenia; 0-procent; 1-prędkość fizyczna (mm/s) przyspieszenie (mm/s²)
    * @return  Kod błędu
    */
    public int MoveC(JointPos joint_pos_p, DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p, JointPos joint_pos_t, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t, double ovl, double blendR, int velAccParamMode)

Ruch łukowy w przestrzeni kartezjańskiej (przeciążona funkcja 1 - nie wymaga wprowadzania pozycji stawów)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Ruch łukowy w przestrzeni kartezjańskiej (przeciążona funkcja 1 - nie wymaga wprowadzania pozycji stawów)
    * @param  [in] desc_pos_p   Pozycja i orientacja kartezjańska punktu pośredniego
    * @param  [in] ptool  Numer układu współrzędnych narzędzia, zakres [1~15]
    * @param  [in] puser  Numer układu współrzędnych przedmiotu, zakres [1~15]
    * @param  [in] pvel  Procent prędkości, zakres [0~100]
    * @param  [in] pacc  Procent przyspieszenia, zakres [0~100], tymczasowo nieudostępnione
    * @param  [in] epos_p  Pozycja osi rozszerzonej punktu pośredniego, jednostka mm
    * @param  [in] poffset_flag  0-brak przesunięcia, 1-przesunięcie w podstawowym układzie współrzędnych / układzie współrzędnych przedmiotu, 2-przesunięcie w układzie współrzędnych narzędzia
    * @param  [in] offset_pos_p  Wartość przesunięcia pozycji i orientacji
    * @param  [in] desc_pos_t   Pozycja i orientacja kartezjańska punktu docelowego
    * @param  [in] ttool  Numer układu współrzędnych narzędzia, zakres [1~15]
    * @param  [in] tuser  Numer układu współrzędnych przedmiotu, zakres [1~15]
    * @param  [in] tvel  Procent prędkości, zakres [0~100]
    * @param  [in] tacc  Procent przyspieszenia, zakres [0~100], tymczasowo nieudostępnione
    * @param  [in] epos_t  Pozycja osi rozszerzonej punktu docelowego, jednostka mm
    * @param  [in] toffset_flag  0-brak przesunięcia, 1-przesunięcie w podstawowym układzie współrzędnych / układzie współrzędnych przedmiotu, 2-przesunięcie w układzie współrzędnych narzędzia
    * @param  [in] offset_pos_t  Wartość przesunięcia pozycji i orientacji
    * @param  [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]
    * @param  [in] blendR [-1.0]-ruch do pozycji (blokujący), [0~1000.0]-promień wygładzenia (nieblokujący), jednostka mm
    * @param  [in] config Konfiguracja przestrzeni stawów dla rozwiązania odwrotnego, [-1]-obliczenie z odniesieniem do bieżącej pozycji stawów, [0~7]-rozwiązanie zgodnie z określoną konfiguracją przestrzeni stawów
    * @param  [in] velAccParamMode Tryb parametrów prędkości i przyspieszenia; 0-procent; 1-prędkość fizyczna (mm/s) przyspieszenie (mm/s²)
    * @return  Kod błędu
    */
    public int MoveC(DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t, double ovl, double blendR, int config, int velAccParamMode)

Ruch punkt-punkt w przestrzeni kartezjańskiej
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Ruch punkt-punkt w przestrzeni kartezjańskiej 
    * @param [in] desc_pos Docelowa pozycja i orientacja kartezjańska w podstawowym układzie współrzędnych 
    * @param [in] tool Numer układu współrzędnych narzędzia, zakres [0~14] 
    * @param [in] user Numer układu współrzędnych przedmiotu, zakres [0~14] 
    * @param [in] vel Procent prędkości, zakres [0~100] 
    * @param [in] acc Procent przyspieszenia, zakres [0~100], tymczasowo nieudostępnione 
    * @param [in] ovl Współczynnik skalowania prędkości, zakres [0~100] 
    * @param [in] blendT [-1.0]-ruch do pozycji (blokujący), [0~500.0]-czas wygładzenia (nieblokujący), jednostka ms 
    * @param [in] config Konfiguracja przestrzeni stawów, [-1]-obliczenie z odniesieniem do bieżącej pozycji stawów, [0~7]-obliczenie z odniesieniem do określonej konfiguracji przestrzeni stawów, domyślnie -1 
    * @return Kod błędu 
    */ 
    int MoveCart(DescPose desc_pos, int tool, int user, float vel, float acc, float ovl, float blendT, int config);

Ruch pełnego okręgu w przestrzeni kartezjańskiej
++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3
    
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ruch pełnego okręgu w przestrzeni kartezjańskiej
    * @param  [in] joint_pos_p  Pozycja stawów punktu pośredniego 1, jednostka deg
    * @param  [in] desc_pos_p   Pozycja i orientacja kartezjańska punktu pośredniego 1
    * @param  [in] ptool  Numer układu współrzędnych narzędzia, zakres [0~14]
    * @param  [in] puser  Numer układu współrzędnych przedmiotu, zakres [0~14]
    * @param  [in] pvel  Procent prędkości, zakres [0~100]
    * @param  [in] pacc  Procent przyspieszenia, zakres [0~100], tymczasowo nieudostępnione
    * @param  [in] epos_p  Pozycja osi rozszerzonej punktu pośredniego 1, jednostka mm
    * @param  [in] joint_pos_t  Pozycja stawów punktu pośredniego 2, jednostka deg
    * @param  [in] desc_pos_t   Pozycja i orientacja kartezjańska punktu pośredniego 2
    * @param  [in] ttool  Numer układu współrzędnych narzędzia, zakres [0~14]
    * @param  [in] tuser  Numer układu współrzędnych przedmiotu, zakres [0~14]
    * @param  [in] tvel  Procent prędkości, zakres [0~100]
    * @param  [in] tacc  Procent przyspieszenia, zakres [0~100], tymczasowo nieudostępnione
    * @param  [in] epos_t  Pozycja osi rozszerzonej punktu pośredniego 2, jednostka mm
    * @param  [in] ovl  Współczynnik skalowania prędkości [0~100] / prędkość fizyczna (mm/s)
    * @param  [in] offset_flag  0-brak przesunięcia, 1-przesunięcie w podstawowym układzie współrzędnych / układzie współrzędnych przedmiotu, 2-przesunięcie w układzie współrzędnych narzędzia
    * @param  [in] offset_pos  Wartość przesunięcia pozycji i orientacji
    * @param  [in] oacc Współczynnik skalowania przyspieszenia [0-100] / przyspieszenie fizyczne (mm/s²)
    * @param  [in] blendR -1: blokujący; 0~1000: promień wygładzenia
    * @param  [in] velAccParamMode Tryb parametrów prędkości i przyspieszenia; 0-procent; 1-prędkość fizyczna (mm/s) przyspieszenie (mm/s²)
    * @return  Kod błędu
    */
    public int Circle(JointPos joint_pos_p, DescPose desc_pos_p, int ptool, int puser, float pvel, float pacc,ExaxisPos epos_p, JointPos joint_pos_t, DescPose desc_pos_t, int ttool, int tuser,float tvel, float tacc, ExaxisPos epos_t, float ovl, int offset_flag,DescPose offset_pos, double oacc, double blendR, int velAccParamMode)

Ruch pełnego okręgu w przestrzeni kartezjańskiej (automatyczne obliczenie kinematyki odwrotnej)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
     * @brief  Ruch pełnego okręgu w przestrzeni kartezjańskiej (automatyczne obliczenie kinematyki odwrotnej)
     * @param  [in] desc_pos_p   Pozycja i orientacja kartezjańska punktu pośredniego 1
     * @param  [in] ptool  Numer układu współrzędnych narzędzia, zakres [0~14]
     * @param  [in] puser  Numer układu współrzędnych przedmiotu, zakres [0~14]
     * @param  [in] pvel  Procent prędkości, zakres [0~100]
     * @param  [in] pacc  Procent przyspieszenia, zakres [0~100], tymczasowo nieudostępnione
     * @param  [in] epos_p  Pozycja osi rozszerzonej punktu pośredniego 1, jednostka mm
     * @param  [in] desc_pos_t   Pozycja i orientacja kartezjańska punktu pośredniego 2
     * @param  [in] ttool  Numer układu współrzędnych narzędzia, zakres [0~14]
     * @param  [in] tuser  Numer układu współrzędnych przedmiotu, zakres [0~14]
     * @param  [in] tvel  Procent prędkości, zakres [0~100]
     * @param  [in] tacc  Procent przyspieszenia, zakres [0~100], tymczasowo nieudostępnione
     * @param  [in] epos_t  Pozycja osi rozszerzonej punktu pośredniego 2, jednostka mm
     * @param  [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]
     * @param  [in] offset_flag  0-brak przesunięcia, 1-przesunięcie w podstawowym układzie współrzędnych / układzie współrzędnych przedmiotu, 2-przesunięcie w układzie współrzędnych narzędzia
     * @param  [in] offset_pos  Wartość przesunięcia pozycji i orientacji
     * @param  [in] oacc Procent przyspieszenia
     * @param  [in] blendR -1: blokujący; 0~1000: promień wygładzenia
     * @param  [in] config Konfiguracja przestrzeni stawów dla rozwiązania odwrotnego, [-1]-obliczenie z odniesieniem do bieżącej pozycji stawów, [0~7]-rozwiązanie zgodnie z określoną konfiguracją przestrzeni stawów
     * @return  Kod błędu
     */
    int Circle(DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, double ovl, int offset_flag, DescPose offset_pos, double oacc, double blendR,int config)

Ruch pełnego okręgu w przestrzeni kartezjańskiej (z dodanym parametrem trybu parametrów velAccParamMode)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    *@brief  Ruch pełnego okręgu w przestrzeni kartezjańskiej (z dodanym parametrem trybu parametrów velAccParamMode)
    *@param  [in] joint_pos_p  Pozycja stawów punktu pośredniego 1, jednostka deg
    *@param  [in] desc_pos_p   Pozycja i orientacja kartezjańska punktu pośredniego 1
    *@param  [in] ptool  Numer układu współrzędnych narzędzia, zakres [1~15]
    *@param  [in] puser  Numer układu współrzędnych przedmiotu, zakres [1~15]
    *@param  [in] pvel  Procent prędkości, zakres [0~100]
    *@param  [in] pacc  Procent przyspieszenia, zakres [0~100], tymczasowo nieudostępnione
    *@param  [in] epos_p  Pozycja osi rozszerzonej punktu pośredniego 1, jednostka mm
    *@param  [in] joint_pos_t  Pozycja stawów punktu pośredniego 2, jednostka deg
    *@param  [in] desc_pos_t   Pozycja i orientacja kartezjańska punktu pośredniego 2
    *@param  [in] ttool  Numer układu współrzędnych narzędzia, zakres [1~15]
    *@param  [in] tuser  Numer układu współrzędnych przedmiotu, zakres [1~15]
    *@param  [in] tvel  Procent prędkości, zakres [0~100]
    *@param  [in] tacc  Procent przyspieszenia, zakres [0~100], tymczasowo nieudostępnione
    *@param  [in] epos_t  Pozycja osi rozszerzonej punktu pośredniego 2, jednostka mm
    *@param  [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]
    *@param  [in] offset_flag  0-brak przesunięcia, 1-przesunięcie w podstawowym układzie współrzędnych / układzie współrzędnych przedmiotu, 2-przesunięcie w układzie współrzędnych narzędzia
    *@param  [in] offset_pos  Wartość przesunięcia pozycji i orientacji
    *@param  [in] oacc Procent przyspieszenia
    *@param  [in] blendR -1: blokujący; 0~1000: promień wygładzenia
    *@param  [in] velAccParamMode Tryb parametrów prędkości i przyspieszenia; 0-procent; 1-prędkość fizyczna (mm/s) przyspieszenie (mm/s²)
    *@return  Kod błędu
    */
    public int Circle(JointPos joint_pos_p, DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, JointPos joint_pos_t, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, double ovl, int offset_flag, DescPose offset_pos, double oacc, double blendR, int velAccParamMode)

Ruch pełnego okręgu w przestrzeni kartezjańskiej (przeciążona funkcja 1 - nie wymaga wprowadzania pozycji stawów)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Ruch pełnego okręgu w przestrzeni kartezjańskiej (przeciążona funkcja 1 - nie wymaga wprowadzania pozycji stawów)
    * @param  [in] desc_pos_p   Pozycja i orientacja kartezjańska punktu pośredniego 1
    * @param  [in] ptool  Numer układu współrzędnych narzędzia, zakres [0~14]
    * @param  [in] puser  Numer układu współrzędnych przedmiotu, zakres [0~14]
    * @param  [in] pvel  Procent prędkości, zakres [0~100]
    * @param  [in] pacc  Procent przyspieszenia, zakres [0~100], tymczasowo nieudostępnione
    * @param  [in] epos_p  Pozycja osi rozszerzonej punktu pośredniego 1, jednostka mm
    * @param  [in] desc_pos_t   Pozycja i orientacja kartezjańska punktu pośredniego 2
    * @param  [in] ttool  Numer układu współrzędnych narzędzia, zakres [0~14]
    * @param  [in] tuser  Numer układu współrzędnych przedmiotu, zakres [0~14]
    * @param  [in] tvel  Procent prędkości, zakres [0~100]
    * @param  [in] tacc  Procent przyspieszenia, zakres [0~100], tymczasowo nieudostępnione
    * @param  [in] epos_t  Pozycja osi rozszerzonej punktu pośredniego 2, jednostka mm
    * @param  [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]
    * @param  [in] offset_flag  0-brak przesunięcia, 1-przesunięcie w podstawowym układzie współrzędnych / układzie współrzędnych przedmiotu, 2-przesunięcie w układzie współrzędnych narzędzia
    * @param  [in] offset_pos  Wartość przesunięcia pozycji i orientacji
    * @param  [in] oacc Procent przyspieszenia
    * @param  [in] blendR -1: blokujący; 0~1000: promień wygładzenia
    * @param  [in] config Konfiguracja przestrzeni stawów dla rozwiązania odwrotnego, [-1]-obliczenie z odniesieniem do bieżącej pozycji stawów, [0~7]-rozwiązanie zgodnie z określoną konfiguracją przestrzeni stawów
    * @param  [in] velAccParamMode Tryb parametrów prędkości i przyspieszenia; 0-procent; 1-prędkość fizyczna (mm/s) przyspieszenie (mm/s²)
    * @return  Kod błędu
    */
    public int Circle(DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, double ovl, int offset_flag, DescPose offset_pos, double oacc, double blendR, int config, int velAccParamMode)

Przykład kodu ruchu pełnego okręgu w przestrzeni kartezjańskiej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3
    
.. code-block:: c#
    :linenos:

    private void btnMovetest_Click(object sender, EventArgs e)
    {
        int rtn = 0;
        DescPose middescPoseCir1 = new DescPose(-435.414, -342.926, 309.205, -171.382, -4.513, 171.520);
        JointPos midjointPosCir1 = new JointPos(26.804, -79.866, 106.642, -125.433, -85.562, -54.721);
        DescPose enddescPoseCir1 = new DescPose(-524.862, -217.402, 308.459, -171.425, -4.810, 156.088);
        JointPos endjointPosCir1 = new JointPos(11.399, -78.055, 104.603, -125.421, -85.770, -54.721);

        DescPose middescPoseCir2 = new DescPose(-482.691, -587.899, 318.594, -171.001, -4.999, -172.996);
        JointPos midjointPosCir2 = new JointPos(42.314, -53.600, 67.296, -112.969, -85.533, -54.721);
        DescPose enddescPoseCir2 = new DescPose(-403.942, -489.061, 317.038, -163.189, -10.425, -175.627);
        JointPos endjointPosCir2 = new JointPos(39.959, -70.616, 96.679, -134.243, -82.276, -54.721);

        DescPose middescPoseMoveC = new DescPose(-435.414, -342.926, 309.205, -171.382, -4.513, 171.520);
        JointPos midjointPosMoveC = new JointPos(26.804, -79.866, 106.642, -125.433, -85.562, -54.721);
        DescPose enddescPoseMoveC = new DescPose(-524.862, -217.402, 308.459, -171.425, -4.810, 156.088);
        JointPos endjointPosmoveC = new JointPos(11.399, -78.055, 104.603, -125.421, -85.770, -54.721);

        DescPose middescPoseCir3 = new DescPose(-435.414, -342.926, 309.205, -171.382, -4.513, 171.520);
        JointPos midjointPosCir3 = new JointPos(26.804, -79.866, 106.642, -125.433, -85.562, -54.721);
        DescPose enddescPoseCir3 = new DescPose(-569.505, -405.378, 357.596, -172.862, -10.939, 171.108);
        JointPos endjointPosCir3 = new JointPos(27.138, -63.750, 78.586, -117.861, -90.588, -54.721);

        DescPose middescPoseCir4 = new DescPose(-482.691, -587.899, 318.594, -171.001, -4.999, -172.996);
        JointPos midjointPosCir4 = new JointPos(42.314, -53.600, 67.296, -112.969, -85.533, -54.721);
        DescPose enddescPoseCir4 = new DescPose(-569.505, -405.378, 357.596, -172.862, -10.939, 171.108);
        JointPos endjointPosCir4 = new JointPos(27.138, -63.750, 78.586, -117.861, -90.588, -54.721);

        DescPose startdescPose = new DescPose(-569.505, -405.378, 357.596, -172.862, -10.939, 171.108);
        JointPos startjointPos = new JointPos(27.138, -63.750, 78.586, -117.861, -90.588, -54.721);

        DescPose linedescPose = new DescPose(-403.942, -489.061, 317.038, -163.189, -10.425, -175.627);
        JointPos linejointPos = new JointPos(39.959, -70.616, 96.679, -134.243, -82.276, -54.721);


        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);


        robot.MoveJ(startjointPos, startdescPose, 3, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        rtn = robot.Circle(midjointPosCir1, middescPoseCir1, 3, 0, 100, 100, exaxisPos, endjointPosCir1, enddescPoseCir1, 3, 0, 100, 100, exaxisPos, 100, -1, offdese, 100, 20);
        Console.WriteLine("Circle1" + rtn);
        rtn = robot.Circle(midjointPosCir2, middescPoseCir2, 3, 0, 100, 100, exaxisPos, endjointPosCir2, enddescPoseCir2, 3, 0, 100, 100, exaxisPos, 100, -1, offdese, 100, 20);
        Console.WriteLine("Circle2" + rtn);

        robot.MoveC(midjointPosMoveC, middescPoseMoveC, 3, 0, 100, 100, exaxisPos, 0, offdese, endjointPosmoveC, enddescPoseMoveC, 3, 0, 100, 100, exaxisPos, 0, offdese, 100, 20);
        rtn = robot.Circle(midjointPosCir3, middescPoseCir3, 3, 0, 100, 100, exaxisPos, endjointPosCir3, enddescPoseCir3, 3, 0, 100, 100, exaxisPos, 100, -1, offdese, 100, 20);
        Console.WriteLine("Circle3" + rtn);
        rtn = robot.MoveL(linejointPos, linedescPose, 3, 0, 100, 100, 100, -1, 0, exaxisPos, 0, 0, offdese);
        Console.WriteLine("MoveL " + rtn);
        rtn = robot.Circle(midjointPosCir4, middescPoseCir4, 3, 0, 100, 100, exaxisPos, endjointPosCir4, enddescPoseCir4, 3, 0, 100, 100, exaxisPos, 100, -1, offdese, 100, 20);
        Console.WriteLine("Circle4" + rtn);
    }

Przykład kodu podstawowych instrukcji ruchu robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    public void TestMove()
        int rtn;
        JointPos j1 = new JointPos(-11.904f, -99.669f, 117.473f, -108.616f, -91.726f, 74.256f);
        JointPos j2 = new JointPos(-45.615f, -106.172f, 124.296f, -107.151f, -91.282f, 74.255f);
        JointPos j3 = new JointPos(-29.777f, -84.536f, 109.275f, -114.075f, -86.655f, 74.257f);
        JointPos j4 = new JointPos(-31.154f, -95.317f, 94.276f, -88.079f, -89.740f, 74.256f);
        DescPose desc_pos1 = new DescPose(-419.524f, -13.000f, 351.569f, -178.118f, 0.314f, 3.833f);
        DescPose desc_pos2 = new DescPose(-321.222f, 185.189f, 335.520f, -179.030f, -1.284f, -29.869f);
        DescPose desc_pos3 = new DescPose(-487.434f, 154.362f, 308.576f, 176.600f, 0.268f, -14.061f);
        DescPose desc_pos4 = new DescPose(-443.165f, 147.881f, 480.951f, 179.511f, -0.775f, -15.409f);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        int tool = 0;
        int user = 0;
        float vel = 100.0f;
        float acc = 100.0f;
        float ovl = 100.0f;
        float oacc = 100.0f;
        float blendT = 0.0f;
        float blendR = 0.0f;
        byte flag = 0;
        byte search = 0;
        int blendMode = 0;
        int velAccMode = 0;
        robot.SetSpeed(20);
        rtn = robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        Console.WriteLine($"movej errcode:{rtn}");
        rtn = robot.MoveL(j2, desc_pos2, tool, user, vel, acc, ovl, blendR, blendMode, epos, search, flag, offset_pos, oacc, velAccMode,0,10);
        Console.WriteLine($"movel errcode:{rtn}");
        rtn = robot.MoveC(j3, desc_pos3, tool, user, vel, acc, epos, flag, offset_pos,j4, desc_pos4, tool, user, vel, acc, epos, flag, offset_pos, ovl, blendR, oacc, velAccMode);
        Console.WriteLine($"movec errcode:{rtn}");
        rtn = robot.MoveJ(j2, desc_pos2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        Console.WriteLine($"movej errcode:{rtn}");
        rtn = robot.Circle(j3, desc_pos3, tool, user, vel, acc, epos,j1, desc_pos1, tool, user, vel, acc, epos,ovl, flag, offset_pos, oacc, -1, velAccMode);
        Console.WriteLine($"circle errcode:{rtn}");
        rtn = robot.MoveCart(desc_pos4, tool, user, vel, acc, ovl, blendT, -1);
        Console.WriteLine($"MoveCart errcode:{rtn}");
        rtn = robot.MoveJ(j1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        Console.WriteLine($"movej errcode:{rtn}");
        rtn = robot.MoveL(desc_pos2, tool, user, vel, acc, ovl, blendR, blendMode, epos, search, flag, offset_pos, -1, velAccMode);
        Console.WriteLine($"movel errcode:{rtn}");
        rtn = robot.MoveC(desc_pos3, tool, user, vel, acc, epos, flag, offset_pos,desc_pos4, tool, user, vel, acc, epos, flag, offset_pos,ovl, blendR, -1, velAccMode);
        Console.WriteLine($"movec errcode:{rtn}");
        rtn = robot.MoveJ(j2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        Console.WriteLine($"movej errcode:{rtn}");
        rtn = robot.Circle(desc_pos3, tool, user, vel, acc, epos, desc_pos1, tool, user, vel, acc, epos,ovl, flag, offset_pos, oacc, blendR, -1, velAccMode);
        Console.WriteLine($"circle errcode:{rtn}");
    }

Ruch po linii śrubowej w przestrzeni kartezjańskiej
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ruch po linii śrubowej w przestrzeni kartezjańskiej 
    * @param [in] joint_pos Docelowa pozycja stawów, jednostka deg 
    * @param [in] desc_pos Docelowa pozycja i orientacja kartezjańska 
    * @param [in] tool Numer układu współrzędnych narzędzia, zakres [0~14] 
    * @param [in] user Numer układu współrzędnych przedmiotu, zakres [0~14] 
    * @param [in] vel Procent prędkości, zakres [0~100] 
    * @param [in] acc Procent przyspieszenia, zakres [0~100], tymczasowo nieudostępnione 
    * @param [in] epos Pozycja osi rozszerzonej, jednostka mm 
    * @param [in] ovl Współczynnik skalowania prędkości, zakres [0~100] 
    * @param [in] offset_flag 0-brak przesunięcia, 1-przesunięcie w podstawowym układzie współrzędnych / układzie współrzędnych przedmiotu, 2-przesunięcie w układzie współrzędnych narzędzia 
    * @param [in] offset_pos Wartość przesunięcia pozycji i orientacji 
    * @param [in] spiral_param Parametry spirali 
    * @return Kod błędu 
    */
    int NewSpiral(JointPos joint_pos, DescPose desc_pos, int tool, int user, float vel, float acc, ExaxisPos epos, float ovl, byte offset_flag, DescPose offset_pos, SpiralParam spiral_param); 

Ruch po linii śrubowej w przestrzeni kartezjańskiej (automatyczne obliczenie kinematyki odwrotnej)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Ruch po linii śrubowej w przestrzeni kartezjańskiej (automatyczne obliczenie kinematyki odwrotnej)
    * @param [in] desc_pos   Docelowa pozycja i orientacja kartezjańska
    * @param [in] tool  Numer układu współrzędnych narzędzia, zakres [0~14]
    * @param [in] user  Numer układu współrzędnych przedmiotu, zakres [0~14]
    * @param [in] vel  Procent prędkości, zakres [0~100]
    * @param [in] acc  Procent przyspieszenia, zakres [0~100], tymczasowo nieudostępnione
    * @param [in] epos  Pozycja osi rozszerzonej, jednostka mm
    * @param [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]
    * @param [in] offset_flag  0-brak przesunięcia, 1-przesunięcie w podstawowym układzie współrzędnych / układzie współrzędnych przedmiotu, 2-przesunięcie w układzie współrzędnych narzędzia
    * @param [in] offset_pos  Wartość przesunięcia pozycji i orientacji
    * @param [in] spiral_param  Parametry spirali
    * @param [in] config  Konfiguracja przestrzeni stawów dla rozwiązania odwrotnego, [-1]-obliczenie z odniesieniem do bieżącej pozycji stawów, [0~7]-rozwiązanie zgodnie z określoną konfiguracją przestrzeni stawów
    * @return Kod błędu 
    */
    int NewSpiral(DescPose desc_pos, int tool, int user, double vel, double acc, ExaxisPos epos, double ovl, int offset_flag, DescPose offset_pos, SpiralParam spiral_param,int config)

Przykład kodu ruchu po linii śrubowej
+++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public static int TestSpiral(Robot robot)
    {
        int rtn=-1;
        JointPos j=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        DescPose desc_pos=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose offset_pos1=new DescPose(50, 0, 0, -30, 0, 0);
        DescPose offset_pos2=new DescPose(50, 0, 0, -5, 0, 0);
        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);
        SpiralParam sp=new SpiralParam(1,5.0,50.0,10.0,10.0,0);

        int tool = 0;
        int user = 0;
        double vel = 100.0;
        double acc = 100.0;
        double ovl = 100.0;
        double blendT = 0.0;
        int flag = 2;

        rtn = robot.MoveJ(j, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos1);
         Console.WriteLine("movej errcode:"+ rtn);

        rtn = robot.NewSpiral(desc_pos, tool, user, vel, acc, epos, ovl, flag, offset_pos2, sp,-1);
        Console.WriteLine("newspiral errcode:"+ rtn);

        return 0;
    }

Rozpoczęcie ruchu serwo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Rozpoczęcie ruchu serwo, używane razem z instrukcjami ServoJ, ServoCart
    * @param[in] comType Typ wysyłania instrukcji; 0-xmlrpc; 1-UDP (odpowiadający portowi 20007 robota)
    * @return Kod błędu
    */
    public int ServoMoveStart (int comType = 0)

Zakończenie ruchu serwo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Zakończenie ruchu serwo, używane razem z instrukcjami ServoJ, ServoCart
    * @param[in] comType Typ wysyłania instrukcji; 0-xmlrpc; 1-UDP (odpowiadający portowi 20007 robota)
    * @return  Kod błędu
    */
    public int ServoMoveEnd (int comType = 0)

Ruch w trybie serwo w przestrzeni stawów
++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3
    
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ruch w trybie serwo w przestrzeni stawów
    * @param  [in] joint_pos  Docelowa pozycja stawów, jednostka deg
    * @param  [in] axisPos  Pozycja zewnętrznej osi, jednostka mm
    * @param  [in] acc  Procent przyspieszenia, zakres [0~100], tymczasowo nieudostępnione, domyślnie 0
    * @param  [in] vel  Procent prędkości, zakres [0~100], tymczasowo nieudostępnione, domyślnie 0
    * @param  [in] cmdT  Okres wysyłania instrukcji, jednostka s, zalecany zakres [0.001~0.0016]
    * @param  [in] filterT Czas filtrowania, jednostka s, tymczasowo nieudostępnione, domyślnie 0
    * @param  [in] gain  Wzmacniacz proporcjonalny pozycji docelowej, tymczasowo nieudostępnione, domyślnie 0
    * @param  [in] id ID instrukcji servoJ, domyślnie 0
    * @param  [in] comType Typ wysyłania instrukcji; 0-xmlrpc; 1-UDP (odpowiadający portowi 20007 robota)
    * @return  Kod błędu
    */
    public int ServoJ(JointPos joint_pos, ExaxisPos axisPos, float acc, float vel, float cmdT, float filterT, float gain, int id = 0, int comType = 0)

Przykład kodu SDK ServoJ, ServoMoveStart, ServoMoveEnd w oparciu o komunikację UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3
    
.. code-block:: c#
    :linenos:

    public void TestServoJUDP()
    {
        // Subskrypcja zwrotna
        robot.OnUdpFrameReceived += (comType, frameCount, frameCmdID, contentLen, content) =>
        {
            Console.WriteLine($"[] comType={comType}, count={frameCount}, cmdID={frameCmdID}, content={content}");
        };

        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();

        float vel = 0.0f;
        float acc = 0.0f;
        float cmdT = 0.008f;
        float filterT = 0.0f;
        float gain = 0.0f;
        byte flag = 0;
        int count = 300;
        float dt = 0.1f;
        int cmdID = 0;

        while (true)
        {
            JointPos j = new JointPos(0, -90, 90, 0, 0, 0);
            ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
            DescPose offset_pos = new DescPose(0, -90, 90, 0, 0, 0);
            robot.MoveJ(j, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
            int ret = robot.GetActualJointPosDegree(flag, ref j);
            if (ret == 0)
            {
                count = 300;
                cmdID += 1;
                robot.ServoMoveStart(1);

                while (count > 0)
                {
                    robot.ServoJ(j, epos, acc, vel, cmdT, filterT, gain, cmdID, 1);
                    j.jPos[0] += dt;
                    j.jPos[1] += dt;
                    j.jPos[3] += dt;
                    j.jPos[4] += dt;
                    j.jPos[5] += dt;
                    epos.ePos[0] += dt;
                    count -= 1;
                    Thread.Sleep(1);
                    robot.GetRobotRealTimeState(ref pkg);
                }
                robot.ServoMoveEnd(1);

                Thread.Sleep(1000);
                count = 300;
                robot.ServoMoveStart(1);
                while (count > 0)
                {
                    robot.ServoJ(j, epos, acc, vel, cmdT, filterT, gain, cmdID, 1);
                    j.jPos[0] -= dt;
                    j.jPos[1] -= dt;
                    j.jPos[3] -= dt;
                    j.jPos[4] -= dt;
                    j.jPos[5] -= dt;
                    epos.ePos[0] -= dt;
                    count -= 1;
                    Thread.Sleep(1);
                    robot.GetRobotRealTimeState(ref pkg);
                }
                robot.ServoMoveEnd(1);
            }
            else
            {
                Console.WriteLine($"GetActualJointPosDegree errcode:{ret}");
            }
        }
    }

Przykład kodu ruchu w trybie serwo w przestrzeni stawów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3
    
.. code-block:: c#
    :linenos:

    private void btnJointServoMove_Click(object sender, EventArgs e)
    {
        JointPos j = new JointPos(0, 0, 0, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);

        float vel = 0.0f;
        float acc = 0.0f;
        float cmdT = 0.008f;
        float filterT = 0.0f;
        float gain = 0.0f;
        byte flag = 0;
        int count = 500;
        float dt = 0.1f;
        int cmdID = 0;
        int ret = robot.GetActualJointPosDegree(flag, ref j);
        if (ret == 0)
        {
            robot.ServoMoveStart();

            try
            {
                while (count > 0)
                {

                    robot.ServoJ(j, epos, acc, vel, cmdT, filterT, gain, cmdID);


                    j.jPos[0] += dt;
                    count--;


                    robot.WaitMs((int)(cmdT * 1000));
                }
            }
            finally
            {

                robot.ServoMoveEnd();
            }
        }
        else
        {
            Console.WriteLine($"GetActualJointPosDegree error code: {ret}");

        }
    }

Rozpoczęcie sterowania momentem obrotowym stawu
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Rozpoczęcie sterowania momentem obrotowym stawu
    * @param [in] comType Typ wysyłania instrukcji; 0-xmlrpc; 1-UDP (odpowiadający portowi 20007 robota)
    * @return Kod błędu
    */
    public int ServoJTStart (int comType = 0)

Sterowanie momentem obrotowym stawu
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Sterowanie momentem obrotowym stawu
    * @param [in] torque Momenty obrotowe stawów j1~j6, jednostka Nm
    * @param [in] interval Okres instrukcji, jednostka s, zakres [0.001~0.008]
    * @param [in] checkFlag Strategia wykrywania 0-brak ograniczenia; 1-ograniczenie mocy; 2-ograniczenie prędkości; 3-jednoczesne ograniczenie mocy i prędkości
    * @param [in] jPowerLimit Maksymalne ograniczenie mocy stawu (W)
    * @param [in] jVelLimit Maksymalna prędkość stawu (°/s)
    * @param [in]  comType Typ wysyłania instrukcji; 0-xmlrpc; 1-UDP (odpowiadający portowi 20007 robota)
    * @return Kod błędu
    */
    public int ServoJT(double[] torque, double interval, int checkFlag, double[] jPowerLimit, double[] jVelLimit, int comType = 0)

Zakończenie sterowania momentem obrotowym stawu
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Zakończenie sterowania momentem obrotowym stawu
    * @param[in] comType Typ wysyłania instrukcji; 0-xmlrpc; 1-UDP (odpowiadający portowi 20007 robota)
    * @return  Kod błędu
    */
    public int ServoJTEnd (int comType = 0)

Przykład kodu SDK ServoJT, ServoJTStart, ServoJTEnd w oparciu o komunikację UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public int ServoJTWithSafetyUDP()
    {
        // Subskrypcja zwrotna
        robot.OnUdpFrameReceived += (comType, frameCount, frameCmdID, contentLen, content) =>
        {
            Console.WriteLine($"[UDP odpowiedź] comType={comType}, count={frameCount}, cmdID={frameCmdID}, content={content}");
        };
        while (true)
        {
            robot.ResetAllError();
            Thread.Sleep(500);

            JointPos j = new JointPos(7.053, -89.699, 156.141, -72.751, 7.829, 1.889);
            ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
            DescPose offset_pos = new DescPose(-151.288, -321.186, 221.989, 89.140, 4.361, -0.795);
            robot.MoveJ(j, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);

            double[] torques = new double[6] { 0, 0, 0, 0, 0, 0 };
            robot.GetJointTorques(1, torques);

            robot.ServoJTStart(1);
            ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
            robot.DragTeachSwitch(1);

            int checkFlag = 0;
            double[] jPowerLimit = new double[6] { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
            double[] jVelLimit = new double[6] { 50, 50, 50, 50, 50, 50 };
            int error = 0;
            while (true)
            {

                torques[0] = 0.1;
                error = robot.ServoJT(torques, 0.008, checkFlag, jPowerLimit, jVelLimit, 1);

                Console.WriteLine($"ServoJT rtn is {error}");
                Thread.Sleep(1);

                robot.GetRobotRealTimeState(ref pkg);
                Console.WriteLine($"maincode {pkg.main_code}, subcode {pkg.sub_code}");
                if (pkg.jt_cur_pos[0] > 30)
                {
                    break;
                }
            }

            while (true)
            {

                torques[0] = -0.1;
                error = robot.ServoJT(torques, 0.008, checkFlag, jPowerLimit, jVelLimit, 1);

                Console.WriteLine($"ServoJT rtn is {error}");
                Thread.Sleep(1);

                robot.GetRobotRealTimeState(ref pkg);
                Console.WriteLine($"maincode {pkg.main_code}, subcode {pkg.sub_code}");
                if (pkg.jt_cur_pos[0] < 0)
                {
                    break;
                }
            }

            robot.DragTeachSwitch(0);
            error = robot.ServoJTEnd(1);
        }
        return 0;
    }

Przykład kodu sterowania momentem obrotowym stawu
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button27_Click(object sender, EventArgs e)
    {
        robot.DragTeachSwitch(1);
        robot.SetPowerLimit(1, 200);
        double[] torques = { 0, 0, 0, 0, 0, 0 };
        robot.GetJointTorques(1, torques);

        int count = 100;
        robot.ServoJTStart();
        int error = 0;
        while (count > 0)
        {
            error = robot.ServoJT(torques, 0.001f);
            count--;
            Thread.Sleep(1);
        }
        error = robot.ServoJTEnd();
        robot.DragTeachSwitch(0);
    }

Przykład kodu sterowania momentem obrotowym stawu z ochroną przed przekroczeniem prędkości
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public int ServoJTWithSafety()
    {
        robot.ResetAllError();
        Thread.Sleep(500);

        double[] torques = new double[6] { 0, 0, 0, 0, 0, 0 };
        robot.GetJointTorques(1, torques);

        robot.ServoJTStart();
        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
        robot.DragTeachSwitch(1);

        int checkFlag = 0;
        double[] jPowerLimit = new double[6] { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
        //double[] jPowerLimit = new double[6] { 10.0, 10.0, 10.0, 10.0, 10.0, 10.0 };
        // double[] jVelLimit = new double[6] { 10.0, 10.0, 10.0, 10.0, 10.0, 10.0 };
        double[] jVelLimit = new double[6] {50, 50, 50, 50, 50, 50 };
        int count = 80000;
        int errorNum = 0;
        int error = 0;
        while (count > 0)
        {
            
            torques[2] = torques[2] + 0.01; 
            error = robot.ServoJT(torques, 0.008, checkFlag, jPowerLimit, jVelLimit); 

            Console.WriteLine($"ServoJT rtn is {error}");
            count = count - 1;
            Thread.Sleep(1);
                
            robot.GetRobotRealTimeState(ref pkg);
            Console.WriteLine($"maincode {pkg.main_code}, subcode {pkg.sub_code}");
            if (error != 0)
            {
                errorNum++;
                if (errorNum > 5)
                {
                    break;
                }

            }
        }
        robot.DragTeachSwitch(0);
        error = robot.ServoJTEnd();

        return 0;
    }

Ruch w trybie serwo w przestrzeni kartezjańskiej
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ruch w trybie serwo w przestrzeni kartezjańskiej
    * @param [in] mode 0-ruch absolutny (układ podstawowy), 1-ruch przyrostowy (układ podstawowy), 2-ruch przyrostowy (układ narzędzia)
    * @param [in] desc_pos Docelowa pozycja i orientacja kartezjańska lub przyrost pozycji i orientacji
    * @param [in] exaxis Pozycja osi rozszerzonej
    * @param [in] pos_gain Współczynnik proporcjonalności przyrostu pozycji, działa tylko w ruchu przyrostowym, zakres [0~1]
    * @param [in] acc Procent przyspieszenia, zakres [0~100], tymczasowo nieudostępnione, domyślnie 0
    * @param [in] vel Procent prędkości, zakres [0~100], tymczasowo nieudostępnione, domyślnie 0
    * @param [in] cmdT Okres wysyłania instrukcji, jednostka s, zalecany zakres [0.001~0.016]
    * @param [in] filterT Czas filtrowania, jednostka s, tymczasowo nieudostępnione, domyślnie 0
    * @param [in] gain Wzmacniacz proporcjonalny pozycji docelowej, tymczasowo nieudostępnione, domyślnie 0
    * @return Kod błędu
    */
    public int ServoCart(int mode, DescPose desc_pose, ExaxisPos exaxis, double[] pos_gain, double acc, double vel, double cmdT, double filterT, double gain);

Przykład kodu ruchu w trybie serwo w przestrzeni kartezjańskiej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public void TestServoCart()
    {
        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();

        int rtn;
        DescPose desc_pos_dt = new DescPose(83.00800f, 50.525000f, 29.246f, 179.629f, -7.138f, -166.975f);
        ExaxisPos exaxis = new ExaxisPos(100.0f, 0.0f, 0.0f, 0.0f);
        double[] pos_gain = { 0.0f, 0.0f, 0.0f, 0.0f, 0.0f, 0.0f };
        int mode = 0;
        float vel = 0.0f;
        float acc = 0.0f;
        float cmdT = 0.001f;
        float filterT = 0.0f;
        float gain = 0.0f;
        byte flag = 0;
        int count = 5000;

        robot.SetSpeed(20);

        while (count > 0)
        {
            rtn = robot.ServoCart(mode, desc_pos_dt, exaxis, pos_gain, acc, vel, cmdT, filterT, gain);
            Console.WriteLine($"ServoCart rtn is {rtn}");
            count -= 1;
            desc_pos_dt.tran.x += 0.01f;
            exaxis.ePos[0] += 0.01f;
        }
    }

Rozpoczęcie ruchu po krzywej średniej
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Rozpoczęcie ruchu po krzywej średniej
    * @return  Kod błędu
    */
    int SplineStart();

Ruch PTP po krzywej średniej
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ruch po krzywej średniej w przestrzeni stawów
    * @param  [in] joint_pos  Docelowa pozycja stawów, jednostka deg
    * @param  [in] desc_pos   Docelowa pozycja i orientacja kartezjańska
    * @param  [in] tool  Numer układu współrzędnych narzędzia, zakres [0~14]
    * @param  [in] user  Numer układu współrzędnych przedmiotu, zakres [0~14]
    * @param  [in] vel  Procent prędkości, zakres [0~100]
    * @param  [in] acc  Procent przyspieszenia, zakres [0~100], tymczasowo nieudostępnione
    * @param  [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]   
    * @return  Kod błędu
    */
    int SplinePTP(JointPos joint_pos, DescPose desc_pos, int tool, int user, float vel, float acc, float ovl);

Ruch po krzywej średniej w przestrzeni stawów (automatyczne obliczenie kinematyki prostej)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Ruch po krzywej średniej w przestrzeni stawów (automatyczne obliczenie kinematyki prostej)
    * @param  [in] joint_pos  Docelowa pozycja stawów, jednostka deg
    * @param  [in] tool  Numer układu współrzędnych narzędzia, zakres [0~14]
    * @param  [in] user  Numer układu współrzędnych przedmiotu, zakres [0~14]
    * @param  [in] vel  Procent prędkości, zakres [0~100]
    * @param  [in] acc  Procent przyspieszenia, zakres [0~100], tymczasowo nieudostępnione
    * @param  [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]
    * @return  Kod błędu
    */
    int SplinePTP(JointPos joint_pos, int tool, int user, double vel, double acc, double ovl)

Zakończenie ruchu po krzywej średniej
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Zakończenie ruchu po krzywej średniej
    * @return  Kod błędu
    */
    int SplineEnd(); 

Przykład kodu ruchu po krzywej średniej
+++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnSplineMove_Click(object sender, EventArgs e)
    {
        JointPos j1 = new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j2 = new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
        JointPos j3 = new JointPos(-61.954, -84.409, 108.153, -116.316, -91.283, 74.260);
        JointPos j4 = new JointPos(-89.575, -80.276, 102.713, -116.302, -91.284, 74.267);
        DescPose desc_pos1 = new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_pos2 = new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose desc_pos3 = new DescPose(-327.622, 402.230, 320.402, -178.067, 2.127, -46.207);
        DescPose desc_pos4 = new DescPose(-104.066, 544.321, 327.023, -177.715, 3.371, -73.818);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);

        int tool = 0;
        int user = 0;
        float vel = 100.0f;
        float acc = 100.0f;
        float ovl = 100.0f;
        float blendT = -1.0f;
        byte flag = 0;

        robot.SetSpeed(20);

        int err = -1;
        err = robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        Console.WriteLine($"movej errcode:  {err}");

        robot.SplineStart();
        robot.SplinePTP(j1, desc_pos1, tool, user, vel, acc, ovl);
        robot.SplinePTP(j2, desc_pos2, tool, user, vel, acc, ovl);
        robot.SplinePTP(j3, desc_pos3, tool, user, vel, acc, ovl);
        robot.SplinePTP(j4, desc_pos4, tool, user, vel, acc, ovl);
        robot.SplineEnd();
    }

Rozpoczęcie nowego ruchu po krzywej średniej
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /** 
    * @brief Rozpoczęcie nowego ruchu po krzywej średniej 
    * @param [in] type  0-przejście łukowe, 1-punkty podane są punktami ścieżki
    * @param [in] averageTime  Globalny średni czas połączenia (ms) (10 ~  ), domyślnie 2000
    * @return Kod błędu 
    */ 
    int NewSplineStart(int type, int averageTime=2000);
    
Nowy punkt instrukcji krzywej średniej
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Dodaje punkt instrukcji ruchu po krzywej średniej 
    * @param [in] joint_pos Docelowa pozycja stawów, jednostka deg 
    * @param [in] desc_pos Docelowa pozycja i orientacja kartezjańska 
    * @param [in] tool Numer układu współrzędnych narzędzia, zakres [0~14] 
    * @param [in] user Numer układu współrzędnych przedmiotu, zakres [0~14] 
    * @param [in] vel Procent prędkości, zakres [0~100] 
    * @param [in] acc Procent przyspieszenia, zakres [0~100], tymczasowo nieudostępnione 
    * @param [in] ovl Współczynnik skalowania prędkości, zakres [0~100] 
    * @param [in] blendR [-1.0]-ruch do pozycji (blokujący), [0~1000.0]-promień wygładzenia (nieblokujący), jednostka mm
    * @param [in] lastFlag  Czy jest ostatnim punktem, 0-nie, 1-tak
    * @return Kod błędu 
    */ 
    int NewSplinePoint(JointPos joint_pos, DescPose desc_pos, int tool, int user, float vel, float acc, float ovl, float blendR, int lastFlag);

Nowy punkt instrukcji krzywej średniej (automatyczne obliczenie kinematyki odwrotnej)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Nowy punkt instrukcji krzywej średniej (automatyczne obliczenie kinematyki odwrotnej)
    * @param  [in] desc_pos   Docelowa pozycja i orientacja kartezjańska
    * @param  [in] tool  Numer układu współrzędnych narzędzia, zakres [0~14]
    * @param  [in] user  Numer układu współrzędnych przedmiotu, zakres [0~14]
    * @param  [in] vel  Procent prędkości, zakres [0~100]
    * @param  [in] acc  Procent przyspieszenia, zakres [0~100], tymczasowo nieudostępnione
    * @param  [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]
    * @param  [in] blendR [-1.0]-ruch do pozycji (blokujący), [0~1000.0]-promień wygładzenia (nieblokujący), jednostka mm
    * @param  [in] lastFlag Czy jest ostatnim punktem, 0-nie, 1-tak
    * @param  [in] config Konfiguracja przestrzeni stawów dla rozwiązania odwrotnego, [-1]-obliczenie z odniesieniem do bieżącej pozycji stawów, [0~7]-rozwiązanie zgodnie z określoną konfiguracją przestrzeni stawów
    * @return  Kod błędu
    */
    int NewSplinePoint(DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, int lastFlag,int config)

Zakończenie nowego ruchu po krzywej średniej
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Zakończenie nowego ruchu po krzywej średniej 
    * @return Kod błędu 
    */ 
    int NewSplineEnd();
    
Przykład kodu nowego ruchu po krzywej średniej
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnNewSpline_Click(object sender, EventArgs e)
    {
        JointPos j1 = new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j2 = new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
        JointPos j3 = new JointPos(-61.954, -84.409, 108.153, -116.316, -91.283, 74.260);
        JointPos j4 = new JointPos(-89.575, -80.276, 102.713, -116.302, -91.284, 74.267);
        JointPos j5 = new JointPos(-95.228, -54.621, 73.691, -112.245, -91.280, 74.268);
        DescPose desc_pos1 = new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_pos2 = new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose desc_pos3 = new DescPose(-327.622, 402.230, 320.402, -178.067, 2.127, -46.207);
        DescPose desc_pos4 = new DescPose(-104.066, 544.321, 327.023, -177.715, 3.371, -73.818);
        DescPose desc_pos5 = new DescPose(-33.421, 732.572, 275.103, -177.907, 2.709, -79.482);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);

        int tool = 0;
        int user = 0;
        float vel = 100.0f;
        float acc = 100.0f;
        float ovl = 100.0f;
        float blendT = -1.0f;
        byte flag = 0;

        robot.SetSpeed(20);

        int err = -1;
        err = robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        Console.WriteLine($"movej errcode:  {err}");

        robot.NewSplineStart(1, 2000);
        robot.NewSplinePoint(j1, desc_pos1, tool, user, vel, acc, ovl, -1, 0);
        robot.NewSplinePoint(j2, desc_pos2, tool, user, vel, acc, ovl, -1, 0);
        robot.NewSplinePoint(j3, desc_pos3, tool, user, vel, acc, ovl, -1, 0);
        robot.NewSplinePoint(j4, desc_pos4, tool, user, vel, acc, ovl, -1, 0);
        robot.NewSplinePoint(j5, desc_pos5, tool, user, vel, acc, ovl, -1, 0);
        robot.NewSplineEnd();
    }

Zatrzymanie ruchu
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Zatrzymanie ruchu
    * @return  Kod błędu
    */
    int StopMotion();

Wstrzymanie ruchu
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:
    
    /** 
      * @brief Wstrzymanie ruchu 
      * @return Kod błędu 
    */  
    int PauseMotion();

Wznowienie ruchu
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Wznowienie ruchu 
    * @return Kod błędu 
    */ 
    int ResumeMotion();

Przykład kodu wstrzymania, wznowienia, zatrzymania ruchu
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnMotionPause_Click(object sender, EventArgs e)
    {
        int rtn;
        JointPos j1 = new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j5 = new JointPos(-95.228, -54.621, 73.691, -112.245, -91.280, 74.268);
        DescPose desc_pos1 = new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_pos5 = new DescPose(-33.421, 732.572, 275.103, -177.907, 2.709, -79.482);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);

        int tool = 0;
        int user = 0;
        float vel = 100.0f;
        float acc = 100.0f;
        float ovl = 100.0f;
        float blendT = -1.0f;
        byte flag = 0;

        robot.SetSpeed(20);

        rtn = robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        rtn = robot.MoveJ(j5, desc_pos5, tool, user, vel, acc, ovl, epos, 1, flag, offset_pos);
        Thread.Sleep(1000);
        robot.PauseMotion();

        Thread.Sleep(1000);
        robot.ResumeMotion();

        Thread.Sleep(1000);
        robot.StopMotion();

        Thread.Sleep(1000);

    }

Rozpoczęcie globalnego przesunięcia punktów
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Rozpoczęcie globalnego przesunięcia punktów
    * @param  [in]  flag  0-przesunięcie w podstawowym układzie współrzędnych / układzie współrzędnych przedmiotu, 2-przesunięcie w układzie współrzędnych narzędzia
    * @param  [in] offset_pos  Wartość przesunięcia pozycji i orientacji
    * @return  Kod błędu
    */
    int PointsOffsetEnable(int flag, DescPose offset_pos); 

Zakończenie globalnego przesunięcia punktów
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Zakończenie globalnego przesunięcia punktów
    * @return  Kod błędu
    */
    int PointsOffsetDisable(); 

Przykład kodu przesunięcia punktów
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnPointOffect_Click(object sender, EventArgs e)
    {
        JointPos j1, j2;
        DescPose desc_pos1, desc_pos2, offset_pos, offset_pos1;
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);

        j1 = new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        desc_pos1 = new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);

        j2 = new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);

        desc_pos2 = new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);

        offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        offset_pos1 = new DescPose(50.0, 50.0, 50.0, 5.0, 5.0, 5.0);

        int tool = 0;
        int user = 0;
        float vel = 100.0f;
        float acc = 100.0f;
        float ovl = 100.0f;
        float blendT = -1.0f;
        byte flag = 0;
        int type = 0;

        robot.SetSpeed(20);

        robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveJ(j2, desc_pos2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        Thread.Sleep(1000);
        robot.PointsOffsetEnable(type, offset_pos1);
        Thread.Sleep(1000);
        robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveJ(j2, desc_pos2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        Thread.Sleep(1000);
        robot.PointsOffsetDisable();
    }

Rozpoczęcie chwytania AO skrzynki sterowniczej w locie
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: c#
    :linenos:

    /**
    * @brief Rozpoczęcie chwytania AO skrzynki sterowniczej w locie
    * @param [in] AONum Numer AO skrzynki sterowniczej
    * @param [in] maxTCPSpeed Maksymalna wartość prędkości TCP [1-5000mm/s], domyślnie 1000
    * @param [in] maxAOPercent Procent AO odpowiadający maksymalnej prędkości TCP, domyślnie 100%
    * @param [in] zeroZoneCmp Wartość kompensacji martwego pola, procent AO, liczba całkowita, domyślnie 20%, zakres [0-100]
    * @return Kod błędu
    */
    int MoveAOStart(int AONum, int maxTCPSpeed, int maxAOPercent, int zeroZoneCmp);

Zatrzymanie chwytania AO skrzynki sterowniczej w locie
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7
   
.. code-block:: c#
    :linenos:

    /**
    * @brief Zatrzymanie chwytania AO skrzynki sterowniczej w locie
    * @return Kod błędu
    */
    int MoveAOStop();
    
Rozpoczęcie chwytania AO końcowego w locie
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7
   
.. code-block:: c#
    :linenos:

    /**
    * @brief Rozpoczęcie chwytania AO końcowego w locie
    * @param [in] AONum Numer AO końcowego
    * @param [in] maxTCPSpeed Maksymalna wartość prędkości TCP [1-5000mm/s], domyślnie 1000
    * @param [in] maxAOPercent Procent AO odpowiadający maksymalnej prędkości TCP, domyślnie 100%
    * @param [in] zeroZoneCmp Wartość kompensacji martwego pola, procent AO, liczba całkowita, domyślnie 20%, zakres [0-100]
    * @return Kod błędu
    */
    int MoveToolAOStart(int AONum, int maxTCPSpeed, int maxAOPercent, int zeroZoneCmp);
    
Zatrzymanie chwytania AO końcowego w locie
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7
   
.. code-block:: c#
    :linenos:

    /**
    * @brief Zatrzymanie chwytania AO końcowego w locie
    * @return Kod błędu
    */
    int MoveToolAOStop();

Przykład kodu chwytania AO w locie
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnMoveAO_Click(object sender, EventArgs e)
    {
        JointPos j1 = new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j2 = new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
        DescPose desc_pos1 = new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_pos2 = new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);

        int tool = 0;
        int user = 0;
        float vel = 100.0f;
        float acc = 100.0f;
        float ovl = 100.0f;
        float blendT = 0.0f;
        float blendR = 0.0f;
        byte flag = 0;
        byte search = 0;

        robot.SetSpeed(5);

        robot.MoveAOStart(0,100,100,20);
        robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveJ(j2, desc_pos2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveAOStop();

        robot.MoveToolAOStart(0, 100, 100, 20);
        robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveJ(j2, desc_pos2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveToolAOStop();
    }

Rozpoczęcie filtrowania FIR ruchu PTP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:


    /**
    * @brief Rozpoczęcie filtrowania FIR ruchu PTP
    * @param [in] maxAcc Maksymalna wartość ekstremalna przyspieszenia (deg/s²)
    * @param [in] maxJek Ujednolicona wartość ekstremalna gwałtowności stawu (deg/s³)
    * @return Kod błędu
    */
    int PtpFIRPlanningStart(double maxAcc, double maxJek=1000);

Zakończenie filtrowania FIR ruchu PTP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Zakończenie filtrowania FIR ruchu PTP
    * @return Kod błędu
    */
    int PtpFIRPlanningEnd();

Rozpoczęcie filtrowania FIR ruchu LIN, ARC
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Rozpoczęcie filtrowania FIR ruchu LIN, ARC
    * @param [in] maxAccLin Wartość ekstremalna przyspieszenia liniowego (mm/s²)
    * @param [in] maxAccDeg Wartość ekstremalna przyspieszenia kątowego (deg/s²)
    * @param [in] maxJerkLin Wartość ekstremalna gwałtowności liniowej (mm/s³)
    * @param [in] maxJerkDeg Wartość ekstremalna gwałtowności kątowej (deg/s³)
    * @return Kod błędu
    */
    int LinArcFIRPlanningStart(double maxAccLin, double maxAccDeg, double maxJerkLin, double maxJerkDeg);

Zakończenie filtrowania FIR ruchu LIN, ARC
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Zakończenie filtrowania FIR ruchu LIN, ARC
    * @return Kod błędu
    */
    int LinArcFIRPlanningEnd();

Przykład kodu filtrowania FIR
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:


    private void button69_Click(object sender, EventArgs e)
    {
        int rtn;
        JointPos startjointPos = new JointPos(-11.904f, -99.669f, 117.473f, -108.616f, -91.726f, 74.256f);
        JointPos midjointPos = new JointPos(-45.615f, -106.172f, 124.296f, -107.151f, -91.282f, 74.255f);
        JointPos endjointPos = new JointPos(-29.777f, -84.536f, 109.275f, -114.075f, -86.655f, 74.257f);

        DescPose startdescPose = new DescPose(-419.524f, -13.000f, 351.569f, -178.118f, 0.314f, 3.833f);
        DescPose middescPose = new DescPose(-321.222f, 185.189f, 335.520f, -179.030f, -1.284f, -29.869f);
        DescPose enddescPose = new DescPose(-487.434f, 154.362f, 308.576f, 176.600f, 0.268f, -14.061f);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        rtn = robot.PtpFIRPlanningStart(1000,1000);
        Console.WriteLine("PtpFIRPlanningStart rtn is " + rtn);
        robot.MoveJ( startjointPos,  startdescPose, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.MoveJ( endjointPos,  enddescPose, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.PtpFIRPlanningEnd();
        Console.WriteLine("PtpFIRPlanningEnd rtn is " + rtn);

        robot.LinArcFIRPlanningStart(1000, 1000, 1000, 1000);
        Console.WriteLine("LinArcFIRPlanningStart rtn is " + rtn);
        robot.MoveL( startjointPos,  startdescPose, 0, 0, 100, 100, 100, -1,  exaxisPos, 0, 0,  offdese, 1, 1);
        robot.MoveC( midjointPos,  middescPose, 0, 0, 100, 100,  exaxisPos, 0,  offdese,  endjointPos,  enddescPose, 0, 0, 100, 100,  exaxisPos, 0,  offdese, 100, -1);
        robot.LinArcFIRPlanningEnd();
        Console.WriteLine("LinArcFIRPlanningEnd rtn is " + rtn);
    }

Włączenie wygładzania przyspieszenia
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Włączenie wygładzania przyspieszenia
    * @param  [in] saveFlag Czy zapisać po odłączeniu zasilania
    * @return  Kod błędu
    */
    int AccSmoothStart(bool saveFlag);

Wyłączenie wygładzania przyspieszenia
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Wyłączenie wygładzania przyspieszenia
    * @param  [in] saveFlag Czy zapisać po odłączeniu zasilania
    * @return  Kod błędu
    */
    int AccSmoothEnd(bool saveFlag);

Przykład kodu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button1_Click(object sender, EventArgs e)
    {

        int rtn;
        JointPos startjointPos = new JointPos(-11.904f, -99.669f, 117.473f, -108.616f, -91.726f, 74.256f);
        JointPos endjointPos = new JointPos(-45.615f, -106.172f, 124.296f, -107.151f, -91.282f, 74.255f);

        DescPose startdescPose = new DescPose(-419.524f, -13.000f, 351.569f, -178.118f, 0.314f, 3.833f);
        DescPose enddescPose = new DescPose(-321.222f, 185.189f, 335.520f, -179.030f, -1.284f, -29.869f);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);
        rtn = robot.AccSmoothStart(false);
        Console.WriteLine("AccSmoothStart rtn is " + rtn);
        robot.MoveJ( startjointPos,  startdescPose, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.MoveJ( endjointPos,  enddescPose, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        rtn = robot.AccSmoothEnd(false);
        Console.WriteLine("AccSmoothEnd rtn is " + rtn);
    }

Włączenie określonej prędkości orientacji
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Włączenie określonej prędkości orientacji
    * @param [in] ratio Procent prędkości orientacji [0-300]
    * @return  Kod błędu
    */
    int AngularSpeedStart(int ratio);

Wyłączenie określonej prędkości orientacji
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:
   
    /**
    * @brief Wyłączenie określonej prędkości orientacji
    * @return  Kod błędu
    */
    int AngularSpeedEnd();

Przykład kodu określonej prędkości orientacji robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button71_Click(object sender, EventArgs e)
    {
        int rtn;
        JointPos startjointPos = new JointPos(-11.904f, -99.669f, 117.473f, -108.616f, -91.726f, 74.256f);
        JointPos endjointPos = new JointPos(-45.615f, -106.172f, 124.296f, -107.151f, -91.282f, 74.255f);

        DescPose startdescPose = new DescPose(-419.524f, -13.000f, 351.569f, -178.118f, 0.314f, 3.833f);
        DescPose enddescPose = new DescPose(-321.222f, 185.189f, 335.520f, -179.030f, -1.284f, -29.869f);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);
        rtn = robot.AngularSpeedStart(50);
        Console.WriteLine("AngularSpeedStart rtn is " + rtn);
        robot.MoveJ( startjointPos,  startdescPose, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.MoveJ( endjointPos,  enddescPose, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        rtn = robot.AngularSpeedEnd();
        Console.WriteLine("AngularSpeedEnd rtn is " + rtn);
    }

Rozpoczęcie ochrony przed osobliwą pozycją
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.9

.. code-block:: c#
    :linenos:

    /**
    * @brief Rozpoczęcie ochrony przed osobliwą pozycją
    * @param [in] protectMode Tryb ochrony przed osobliwością, 0: tryb stawów; 1-tryb kartezjański
    * @param [in] minShoulderPos Zakres regulacji osobliwości barku (mm), domyślnie 100
    * @param [in] minElbowPos Zakres regulacji osobliwości łokcia (mm), domyślnie 50
    * @param [in] minWristPos Zakres regulacji osobliwości nadgarstka (°), domyślnie 10
    * @return Kod błędu
    */
    int SingularAvoidStart(int protectMode, double minShoulderPos, double minElbowPos, double minWristPos);

Zatrzymanie ochrony przed osobliwą pozycją
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.9

.. code-block:: c#
    :linenos:

    /**
    * @brief Zatrzymanie ochrony przed osobliwą pozycją
    * @return Kod błędu
    */
    int SingularAvoidEnd();

Przykład kodu
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.9
    
.. code-block:: c#
    :linenos:

    private void btnTestSingularAvoidEArc_Click(object sender, EventArgs e)
    {
        int rtn;
        JointPos startjointPos = new JointPos(-11.904f, -99.669f, 117.473f, -108.616f, -91.726f, 74.256f);
        JointPos endjointPos = new JointPos(-45.615f, -106.172f, 124.296f, -107.151f, -91.282f, 74.255f);

        DescPose startdescPose = new DescPose(-419.524f, -13.000f, 351.569f, -178.118f, 0.314f, 3.833f);
        DescPose enddescPose = new DescPose(-321.222f, 185.189f, 335.520f, -179.030f, -1.284f, -29.869f);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        rtn = robot.SingularAvoidStart(2, 10, 5, 5);
        Console.WriteLine("SingularAvoidStart rtn is " + rtn);
        robot.MoveJ( startjointPos,  startdescPose, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.MoveJ( endjointPos,  enddescPose, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        rtn = robot.SingularAvoidEnd();
        Console.WriteLine("SingularAvoidEnd rtn is " + rtn);
    }

Wyzwolenie sygnału bezpiecznego zatrzymania
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Sygnał wyzwolenia bezpiecznego zatrzymania
    * @return Kod błędu
    */
    int GetSafetyCode();

Opróżnienie kolejki instrukcji ruchu
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Opróżnienie kolejki instrukcji ruchu
    * @return Kod błędu
    */
    public int MotionQueueClear();

Przejście do punktu początkowego linii przecięcia rur
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Przejście do punktu początkowego linii przecięcia rur
    * @param [in] mainPoint Pozycje i orientacje kartezjańskie 6 punktów nauczania rury głównej
    * @param [in] mainExaxisPos Pozycje osi rozszerzonej dla 6 punktów nauczania rury głównej
    * @param [in] piecePoint Pozycje i orientacje kartezjańskie 6 punktów nauczania rury pomocniczej
    * @param [in] pieceExaxisPos Pozycje osi rozszerzonej dla 6 punktów nauczania rury łączącej
    * @param [in] extAxisFlag Czy włączyć oś rozszerzoną; 0-nie włączaj; 1-włącz
    * @param [in] exaxisPos Pozycja osi rozszerzonej punktu początkowego
    * @param [in] tool Numer układu współrzędnych narzędzia
    * @param [in] wobj Numer układu współrzędnych przedmiotu
    * @param [in] vel Procent prędkości
    * @param [in] acc Procent przyspieszenia
    * @param [in] ovl Współczynnik skalowania prędkości
    * @param [in] oacc Współczynnik skalowania przyspieszenia
    * @param [in] moveType Typ ruchu; 0-PTP; 1-LIN
    * @param [in] moveDirection Kierunek ruchu; 0-zgodnie z ruchem wskazówek zegara; 1-przeciwnie do ruchu wskazówek zegara
    * @param [in] offset Przesunięcie
    * @return Kod błędu
    */
    public int MoveToIntersectLineStart(DescPose[] mainPoint, ExaxisPos[] mainExaxisPos, DescPose[] piecePoint, ExaxisPos[] pieceExaxisPos, int extAxisFlag, ExaxisPos exaxisPos, int tool, int wobj, double vel, double acc, double ovl, double oacc, int moveType, int moveDirection, DescPose offset);
            
Ruch po linii przecięcia rur
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ruch po linii przecięcia rur
    * @param [in] mainPoint Pozycje i orientacje kartezjańskie 6 punktów nauczania rury głównej
    * @param [in] mainExaxisPos Pozycje osi rozszerzonej dla 6 punktów nauczania rury głównej
    * @param [in] piecePoint Pozycje i orientacje kartezjańskie 6 punktów nauczania rury pomocniczej
    * @param [in] pieceExaxisPos Pozycje osi rozszerzonej dla 6 punktów nauczania rury łączącej
    * @param [in] extAxisFlag Czy włączyć oś rozszerzoną; 0-nie włączaj; 1-włącz
    * @param [in] exaxisPos Pozycja osi rozszerzonej punktu początkowego
    * @param [in] tool Numer układu współrzędnych narzędzia
    * @param [in] wobj Numer układu współrzędnych przedmiotu
    * @param [in] vel Procent prędkości
    * @param [in] acc Procent przyspieszenia
    * @param [in] ovl Współczynnik skalowania prędkości
    * @param [in] oacc Współczynnik skalowania przyspieszenia
    * @param [in] moveDirection Kierunek ruchu; 0-zgodnie z ruchem wskazówek zegara; 1-przeciwnie do ruchu wskazówek zegara
    * @param [in] offset Przesunięcie
    * @return Kod błędu
    */
    public int MoveIntersectLine(DescPose[] mainPoint, ExaxisPos[] mainExaxisPos, DescPose[] piecePoint, ExaxisPos[] pieceExaxisPos, int extAxisFlag, ExaxisPos[] exaxisPos, int tool, int wobj, double vel, double acc, double ovl, double oacc, int moveDirection, DescPose offset);
                
Przykład kodu ruchu po linii przecięcia rur robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
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

Ruch w miejscu pusty
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ruch w miejscu pusty
    * @return Kod błędu
    */
    public int MoveStationary()

Przykład kodu ruchu w miejscu pustego
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public void LaserSensorRecordandReplay()
    {
        int rtn = robot.LaserSensorRecordandReplay(0, 10, 1, 0, 0.1, 1, 1, 10, 100);
        Console.WriteLine($"LaserSensorRecordandReplay rtn is {rtn}");
        rtn = robot.MoveStationary();
        Console.WriteLine($"MoveStationary rtn is {rtn}");
        rtn = robot.LaserSensorRecord1(0, 10);
        Console.WriteLine($"LaserSensorRecord1 rtn is {rtn}"); 
    }

Rozpoczęcie oscylacji punktowej
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Rozpoczęcie oscylacji punktowej
    * @param [in] weaveNum Numer oscylacji [0-7]
    * @param [in] mode 0-układ współrzędnych narzędzia; 1-punkt odniesienia
    * @param [in] refPoint Współrzędne kartezjańskie punktu odniesienia [x,y,z,a,b,c]
    * @param [in] weaveTime Czas oscylacji [s]
    * @return Kod błędu
    */
    public int OriginPointWeaveStart(int weaveNum, int mode, DescPose refPoint, double weaveTime);
    
Zakończenie oscylacji punktowej
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Zakończenie oscylacji punktowej
    * @return Kod błędu
    */
    public int OriginPointWeaveEnd();
        
Przykład kodu SDK oscylacji punktowej
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    void TestOriginPointWeave()
    {
        // Utwórz obiekt pozycji stawów
        JointPos j = new JointPos(39.886, -98.580, -124.032, -47.393, 90.000, 40.842);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);

        // Współrzędne punktu odniesienia
        DescPose refPoint = new DescPose(400.021, 300.022, 299.996, 179.997, -0.003, -90.956);

        //// Pierwszy ruch
        robot.MoveJ(j, 1, 0, 100, 100, 100, epos, -1, 0, offset_pos);

        // Uruchom oscylację punktową (tryb 0)
        robot.OriginPointWeaveStart(0, 0, refPoint, 3);
        robot.MoveStationary();   // Wykonaj ruch stały (zakładając, że metoda istnieje)
        robot.OriginPointWeaveEnd();

        Thread.Sleep(2000);         // Odczekaj 2 sekundy

        // Drugi ruch
        robot.MoveJ(j, 1, 0, 100, 100, 100, epos, -1, 0, offset_pos);

        // Uruchom oscylację punktową (tryb 1)
        robot.OriginPointWeaveStart(0, 1, refPoint, 3);
        robot.MoveStationary();
        robot.OriginPointWeaveEnd();
    }
        
Przykład kodu SDK oscylacji punktowej (zawierającej laser i oś rozszerzoną)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    void TestOriginPointWeave2()
    {
        // Utwórz obiekt pozycji stawów
        JointPos j = new JointPos(39.886, -98.580, -124.032, -47.393, 90.000, 40.842);
        ExaxisPos epos1 = new ExaxisPos(0, 0, 0, 0);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos2 = new ExaxisPos(5, 0.000, 0.000, 0.000);

        // Współrzędne punktu odniesienia
        DescPose refPoint = new DescPose(400.021, 300.022, 299.996, 179.997, -0.003, -90.956);

        int rtn = 0;
        robot.LaserTrackingSensorConfig("192.168.58.20", 5020);
        robot.LaserTrackingSensorSamplePeriod(20);
        robot.LoadPosSensorDriver(101);

        // Załaduj sterownik UDP
        robot.ExtDevLoadUDPDriver();

        // Ustaw czas zakończenia polecenia zewnętrznej osi
        rtn = robot.SetExAxisCmdDoneTime(5000.0);
        Console.WriteLine("SetExAxisCmdDoneTime rtn is " + rtn);

        // Załącz zewnętrzne osie 1 i 2
        rtn = robot.ExtAxisServoOn(1, 1);
        Console.WriteLine("ExtAxisServoOn axis id 1 rtn is " + rtn);
        rtn = robot.ExtAxisServoOn(2, 1);
        Console.WriteLine("ExtAxisServoOn axis id 2 rtn is " + rtn);
        Thread.Sleep(2000);

        // Ustaw powrót do zera zewnętrznej osi
        robot.ExtAxisSetHoming(1, 0, 10, 2);
        robot.LaserTrackingLaserOnOff(1);


        //// 1---bez osi rozszerzonej
        robot.LaserTrackingTrackOnOff(1, 4);
        robot.Sleep(200);
        // Uruchom oscylację punktową
        robot.OriginPointWeaveStart(0, 0, refPoint, 10);
        robot.MoveStationary();   // Wykonaj ruch stały
        robot.OriginPointWeaveEnd();
        robot.LaserTrackingTrackOnOff(0, 4);

        Thread.Sleep(2000);         // Odczekaj 2 sekundy

        //// 2----z osią rozszerzoną
        robot.ExtAxisMove(epos1, 100, -1);
        robot.LaserTrackingTrackOnOff(1, 4);
        // Uruchom oscylację punktową
        robot.OriginPointWeaveStart(0, 0, refPoint, 20);
        robot.ExtAxisMove(epos2, 100, -1);
        robot.OriginPointWeaveEnd();
        robot.LaserTrackingTrackOnOff(0, 4);
    }
        
Ruch w trybie serwo prędkości w przestrzeni stawów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ruch w trybie serwo prędkości w przestrzeni stawów
    * @param  [in] joint_pos  6 docelowych prędkości stawów, jednostka deg/s
    * @param  [in] axisPos  4 prędkości zewnętrznych osi, jednostka deg/s
    * @param  [in] acc   Procent przyspieszenia, zakres [0~100], tymczasowo nieudostępnione, domyślnie 0
    * @param  [in] vel   Procent prędkości, zakres [0~100], tymczasowo nieudostępnione, domyślnie 0
    * @param  [in] cmdT   Okres wysyłania instrukcji, jednostka s, zalecany zakres [0.001~0.0016]
    * @param  [in] filterT Czas filtrowania, jednostka s, tymczasowo nieudostępnione, domyślnie 0
    * @param  [in] gain   Wzmacniacz proporcjonalny pozycji docelowej, tymczasowo nieudostępnione, domyślnie 0
    * @param  [in] id ID instrukcji servoJ, domyślnie 0
    * @param[in] comType Typ wysyłania instrukcji; 0-xmlrpc; 1-UDP (odpowiadający portowi 20007 robota)
    * @return   Kod błędu
    */
    public int ServoJV(double[] joint_vel, double[] exis_vel, float acc, float vel, float cmdT, float filterT, float gain, int id = 0, int comType = 0)

Przykład kodu ruchu w trybie serwo prędkości w przestrzeni stawów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public int ServoJVtest()
    {
        double[] joint_vel = new double[6] { 10, 0, 0, 0, 0, 0 };
        double[] exis_vel = new double[4] { 0, 0, 0, 0 };
        float acc = 0.0f; 
        float vel = 0.0f;
        float cmdT = 0.01f; 
        float filterT = 0.0f; 
        float gain = 0.0f;
        int cnt = 0;
        while (cnt < 200)
        {
            int error = robot.ServoJV(joint_vel, exis_vel, acc, vel, cmdT, filterT, gain);
            Console.WriteLine($"ServoJV rtn is {error}");
            cnt++;
        }
        return 0;
    }

Rozpoczęcie sterowania MIT stawów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Rozpoczęcie sterowania MIT stawów
    * @param [in]  comType Typ wysyłania instrukcji; 0-xmlrpc; 1-UDP (odpowiadający portowi 20007 robota)
    * @return   Kod błędu
    */
    public int ServoMITStart(int comType = 0)

Zakończenie sterowania MIT stawów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Zakończenie sterowania MIT stawów
    * @param [in]  comType Typ wysyłania instrukcji; 0-xmlrpc; 1-UDP (odpowiadający portowi 20007 robota)
    * @return   Kod błędu
    */
    public int ServoMITEnd(int comType = 0)

Sterowanie MIT stawów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Sterowanie MIT stawów
    * @param [in] posGain Wzmocnienie pozycji stawów j1~j6
    * @param [in] desPos Oczekiwana pozycja stawów j1~j6, jednostka: deg
    * @param [in] velGain Wzmocnienie prędkości stawów j1~j6
    * @param [in] desVel Oczekiwana prędkość stawów j1~j6, jednostka: deg/s
    * @param [in] torque_ff Moment przedni stawów j1~j6, jednostka: Nm
    * @param [in] interval Okres instrukcji, jednostka s, zakres [0.001~0.008]
    * @param [in]  comType Typ wysyłania instrukcji; 0-xmlrpc; 1-UDP (odpowiadający portowi 20007 robota)
    * @return Kod błędu
    */
    public int ServoMIT(double[] posGain, double[] desPos, double[] velGain, double[] desVel, double[] torque_ff, double interval, int comType = 0)

Przykład kodu sterowania MIT stawów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public int ServoMITtest()
    {
        // Subskrypcja zwrotna
        robot.OnUdpFrameReceived += (comType, frameCount, frameCmdID, contentLen, content) =>
        {
            Console.WriteLine($"[UDP odpowiedź] comType={comType}, count={frameCount}, cmdID={frameCmdID}, content={content}");
        };
        while (true)
        {
            robot.ResetAllError();
            Thread.Sleep(500);

            double[] posGain = new double[6] { 0, 0, 0, 0, 0, 0 };
            double[] desPos = new double[6] { 0, 0, 0, 0, 0, 0 };
            double[] velGain = new double[6] { 0, 0, 0, 0, 0, 0 };
            double[] desVel = new double[6] { 0, 0, 0, 0, 0, 0 };
            double[] torques = new double[6] { 0, 0, 0, 0, 0, 0 };
            robot.GetJointTorques(1, torques);
            Console.WriteLine($"111111");
            //robot.ServoMITEnd(0);
            robot.ServoMITStart(0);
            Console.WriteLine($"ServoMITStart");
            ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
            robot.DragTeachSwitch(1);
            Console.WriteLine($"DragTeachSwitch");
            double intev = 0.008;
            double[] jPowerLimit = new double[6] { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
            double[] jVelLimit = new double[6] { 50, 50, 50, 50, 50, 50 };
            int error = 0;
            while (true)
            {

                torques[5] = 0.03;
                Console.WriteLine($"ServoMIT call ");
                error = robot.ServoMIT(posGain, desPos, velGain, desVel, torques, intev, 0);

                Console.WriteLine($"ServoMIT111111 rtn is {error}");
                Thread.Sleep(1);

                robot.GetRobotRealTimeState(ref pkg);
                //Console.WriteLine($"maincode {pkg.main_code}, subcode {pkg.sub_code}");
                Console.WriteLine($"pkg.jt_cur_pos[5]:{pkg.jt_cur_pos[5]}");
                if (pkg.jt_cur_pos[5] > 30)
                {
                    break;
                }
            }

            while (true)
            {

                torques[5] = -0.03;
                error = robot.ServoMIT(posGain, desPos, velGain, desVel, torques, intev, 0);

                Console.WriteLine($"ServoJT222222 rtn is {error}");
                Thread.Sleep(1);

                robot.GetRobotRealTimeState(ref pkg);
                //Console.WriteLine($"maincode {pkg.main_code}, subcode {pkg.sub_code}");
                Console.WriteLine($"pkg.jt_cur_pos[5]:{pkg.jt_cur_pos[5]}");
                if (pkg.jt_cur_pos[5] < 0)
                {
                    break;
                }
            }

            robot.DragTeachSwitch(0);
            error = robot.ServoMITEnd(0);
        }
        return 0;
    }