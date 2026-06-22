Ruch robota
============

.. toctree:: 
    :maxdepth: 5


Jog (punktowy ruch)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Jog (punktowy ruch) 
    * @param [in] refType 0-jog przegubów, 2-jog w układzie bazowym, 4-jog w układzie narzędzia, 8-jog w układzie przedmiotu
    * @param [in] nb 1-przegub 1(lub oś X), 2-przegub 2(lub oś Y), 3-przegub 3(lub oś Z), 4-przegub 4(lub obrót wokół osi X), 5-przegub 5(lub obrót wokół osi Y), 6-przegub 6(lub obrót wokół osi Z)
    * @param [in] dir 0-kierunek ujemny, 1-kierunek dodatni
    * @param [in] vel Procent prędkości, [0~100]
    * @param [in] acc Procent przyspieszenia, [0~100]
    * @param [in] max_dis Maksymalny kąt pojedynczego ruchu punktowego, jednostka [°] lub odległość, jednostka [mm]
    * @return Kod błędu 
    */ 
    int StartJOG(int refType, int nb, int dir, double vel, double acc, double max_dis);

Zatrzymanie jog z redukcją prędkości
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Zatrzymanie jog z redukcją prędkości
    * @param  [in]  stopType  1-zatrzymanie jog przegubów, 3-zatrzymanie jog w układzie bazowym, 5-zatrzymanie jog w układzie narzędzia, 9-zatrzymanie jog w układzie przedmiotu
    * @return  Kod błędu
    */
    int StopJOG(int stopType);

Natychmiastowe zatrzymanie jog
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Natychmiastowe zatrzymanie jog
    * @return  Kod błędu
    */
    int ImmStopJOG(); 

Przykład kodu sterowania punktowego robotem
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static  int TestJOG(Robot robot)
    {
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
        return 0;
    }

Ruch w przestrzeni przegubów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Ruch w przestrzeni przegubów
    * @param  [in] joint_pos  Docelowa pozycja przegubów, jednostka deg
    * @param  [in] desc_pos  Docelowa poza kartezjańska
    * @param  [in] tool  Numer narzędzia, zakres [0~14]
    * @param  [in] user  Numer przedmiotu, zakres [0~14]
    * @param  [in] vel  Procent prędkości, zakres [0~100]
    * @param  [in] acc  Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param  [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]
    * @param  [in] epos  Pozycja osi rozszerzenia, jednostka mm
    * @param  [in] blendT [-1.0]-ruch do pozycji (blokujący), [0~500.0]-czas wygładzania (nieblokujący), jednostka ms
    * @param  [in] offset_flag  0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie przedmiotu, 2-przesunięcie w układzie narzędzia
    * @param  [in] offset_pos  Wartość przesunięcia pozy
    * @return  Kod błędu
    */
    int MoveJ(JointPos joint_pos, DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, ExaxisPos epos, double blendT, int offset_flag, DescPose offset_pos);

Ruch w przestrzeni przegubów (automatyczne obliczenia kinematyki prostej)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /** 
    * @brief  Ruch w przestrzeni przegubów (automatyczne obliczenia kinematyki prostej)
    * @param  [in] joint_pos  Docelowa pozycja przegubów, jednostka deg
    * @param  [in] tool  Numer narzędzia, zakres [0~14]
    * @param  [in] user  Numer przedmiotu, zakres [0~14]
    * @param  [in] vel  Procent prędkości, zakres [0~100]
    * @param  [in] acc  Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param  [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]
    * @param  [in] epos  Pozycja osi rozszerzenia, jednostka mm
    * @param  [in] blendT [-1.0]-ruch do pozycji (blokujący), [0~500.0]-czas wygładzania (nieblokujący), jednostka ms
    * @param  [in] offset_flag  0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie przedmiotu, 2-przesunięcie w układzie narzędzia
    * @param  [in] offset_pos  Wartość przesunięcia pozy
    * @return  Kod błędu 
    */ 
    int MoveJ(JointPos joint_pos, int tool, int user, double vel, double acc, double ovl, ExaxisPos epos, double blendT, int offset_flag, DescPose offset_pos)

Ruch liniowy w przestrzeni kartezjańskiej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionchanged:: Java SDK-v1.0.5-3.8.2

.. code-block:: Java
    :linenos:

    /**
    * @brief  Ruch liniowy w przestrzeni kartezjańskiej (przeciążona funkcja 1 z dodanym blendMode)
    * @param  joint_pos  Docelowa pozycja przegubów, jednostka deg
    * @param  desc_pos   Docelowa poza kartezjańska
    * @param  tool  Numer narzędzia, zakres [1~15]
    * @param  user  Numer przedmiotu, zakres [1~15]
    * @param  vel  Procent prędkości, zakres [0~100]
    * @param  acc  Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param  ovl  Współczynnik skalowania prędkości [0~100]/prędkość fizyczna (mm/s)
    * @param  blendR [-1.0]-ruch do pozycji (blokujący), [0~1000.0]-promień wygładzania (nieblokujący), jednostka mm
    * @param  blendMode Sposób przejścia; 0-przejście styczne wewnętrznie; 1-przejście narożne
    * @param  epos  Pozycja osi rozszerzenia, jednostka mm
    * @param  search  0-brak poszukiwania pozycji drutu, 1-poszukiwanie pozycji drutu
    * @param  offset_flag  0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie przedmiotu, 2-przesunięcie w układzie narzędzia
    * @param  offset_pos  Wartość przesunięcia pozy
    * @param  oacc Współczynnik skalowania przyspieszenia [0-100]/przyspieszenie fizyczne (mm/s2)
    * @param  velAccParamMode Tryb parametrów prędkości i przyspieszenia; 0-procentowy; 1-prędkość fizyczna (mm/s) przyspieszenie (mm/s2)
    * @param  overSpeedStrategy  Strategia przekroczenia prędkości, 1-standardowa; 2-zatrzymanie z błędem przy przekroczeniu prędkości; 3-adaptacyjne zmniejszenie prędkości, domyślnie 0
    * @param  speedPercent  Procentowy próg dopuszczalnego zmniejszenia prędkości [0-100], domyślnie 10%
    * @return  Kod błędu
    */
    public int MoveL(JointPos joint_pos, DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, int blendMode, ExaxisPos epos, int search, int offset_flag, DescPose offset_pos, double oacc,int velAccParamMode, int overSpeedStrategy, int speedPercent)

Ruch liniowy w przestrzeni kartezjańskiej (automatyczne obliczenia kinematyki odwrotnej)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Ruch liniowy w przestrzeni kartezjańskiej (automatyczne obliczenia kinematyki odwrotnej)
    * @param [in] desc_pos   Docelowa poza kartezjańska
    * @param [in] tool  Numer narzędzia, zakres [1~15]
    * @param [in] user  Numer przedmiotu, zakres [1~15]
    * @param [in] vel  Procent prędkości, zakres [0~100]
    * @param [in] acc  Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]
    * @param [in] blendR [-1.0]-ruch do pozycji (blokujący), [0~1000.0]-promień wygładzania (nieblokujący), jednostka mm
    * @param [in] blendMode Sposób przejścia; 0-przejście styczne wewnętrznie; 1-przejście narożne
    * @param [in] epos  Pozycja osi rozszerzenia, jednostka mm
    * @param [in] search  0-brak poszukiwania pozycji drutu, 1-poszukiwanie pozycji drutu
    * @param [in] offset_flag  0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie przedmiotu, 2-przesunięcie w układzie narzędzia
    * @param [in] offset_pos  Wartość przesunięcia pozy
    * @param [in] config Konfiguracja przestrzeni przegubów dla kinematyki odwrotnej, [-1]-obliczenia względem bieżącej pozycji przegubów, [0~7]-obliczenia według określonej konfiguracji przestrzeni przegubów
    * @param [in] overSpeedStrategy  Strategia przekroczenia prędkości, 1-standardowa; 2-zatrzymanie z błędem przy przekroczeniu prędkości; 3-adaptacyjne zmniejszenie prędkości, domyślnie 0
    * @param [in] speedPercent  Procentowy próg dopuszczalnego zmniejszenia prędkości [0-100], domyślnie 10%
    * @return  Kod błędu
    */
    int MoveL(DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, int blendMode, ExaxisPos epos, int search, int offset_flag, DescPose offset_pos, int config, int overSpeedStrategy, int speedPercent)

Ruch liniowy w przestrzeni kartezjańskiej (z dodanym parametrem trybu parametrów prędkości i przyspieszenia velAccParamMode)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Ruch liniowy w przestrzeni kartezjańskiej (z dodanym parametrem trybu parametrów prędkości i przyspieszenia velAccParamMode)
    * @param  [in] joint_pos  Docelowa pozycja przegubów, jednostka deg
    * @param  [in] desc_pos   Docelowa poza kartezjańska
    * @param  [in] tool  Numer narzędzia, zakres [1~15]
    * @param  [in] user  Numer przedmiotu, zakres [1~15]
    * @param  [in] vel  Procent prędkości, zakres [0~100]
    * @param  [in] acc  Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param  [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]
    * @param  [in] blendR [-1.0]-ruch do pozycji (blokujący), [0~1000.0]-promień wygładzania (nieblokujący), jednostka mm
    * @param  [in] epos  Pozycja osi rozszerzenia, jednostka mm
    * @param  [in] search  0-brak poszukiwania pozycji drutu, 1-poszukiwanie pozycji drutu
    * @param  [in] offset_flag  0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie przedmiotu, 2-przesunięcie w układzie narzędzia
    * @param  [in] offset_pos  Wartość przesunięcia pozy
    * @param  [in] velAccParamMode Tryb parametrów prędkości i przyspieszenia; 0-procentowy; 1-prędkość fizyczna (mm/s) przyspieszenie (mm/s2)
    * @param  [in] overSpeedStrategy  Strategia przekroczenia prędkości, 1-standardowa; 2-zatrzymanie z błędem przy przekroczeniu prędkości; 3-adaptacyjne zmniejszenie prędkości, domyślnie 0
    * @param  [in] speedPercent  Procentowy próg dopuszczalnego zmniejszenia prędkości [0-100], domyślnie 10%
    * @return  Kod błędu
    */
    public int MoveL(JointPos joint_pos, DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, ExaxisPos epos, int search, int offset_flag, DescPose offset_pos, int velAccParamMode, int overSpeedStrategy, int speedPercent)

Ruch liniowy w przestrzeni kartezjańskiej (przeciążona funkcja 1 z dodanym blendMode)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Ruch liniowy w przestrzeni kartezjańskiej (przeciążona funkcja 1 z dodanym blendMode)
    * @param  [in] joint_pos  Docelowa pozycja przegubów, jednostka deg
    * @param  [in] desc_pos   Docelowa poza kartezjańska
    * @param  [in] tool  Numer narzędzia, zakres [1~15]
    * @param  [in] user  Numer przedmiotu, zakres [1~15]
    * @param  [in] vel  Procent prędkości, zakres [0~100]
    * @param  [in] acc  Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param  [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]
    * @param  [in] blendR [-1.0]-ruch do pozycji (blokujący), [0~1000.0]-promień wygładzania (nieblokujący), jednostka mm
    * @param  [in] blendMode Sposób przejścia; 0-przejście styczne wewnętrznie; 1-przejście narożne
    * @param  [in] epos  Pozycja osi rozszerzenia, jednostka mm
    * @param  [in] search  0-brak poszukiwania pozycji drutu, 1-poszukiwanie pozycji drutu
    * @param  [in] offset_flag  0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie przedmiotu, 2-przesunięcie w układzie narzędzia
    * @param  [in] offset_pos  Wartość przesunięcia pozy
    * @param  [in] velAccParamMode Tryb parametrów prędkości i przyspieszenia; 0-procentowy; 1-prędkość fizyczna (mm/s) przyspieszenie (mm/s2)
    * @param  [in] overSpeedStrategy  Strategia przekroczenia prędkości, 1-standardowa; 2-zatrzymanie z błędem przy przekroczeniu prędkości; 3-adaptacyjne zmniejszenie prędkości, domyślnie 0
    * @param  [in] speedPercent  Procentowy próg dopuszczalnego zmniejszenia prędkości [0-100], domyślnie 10%
    * @return  Kod błędu
    */
    public int MoveL(JointPos joint_pos, DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, int blendMode, ExaxisPos epos, int search, int offset_flag, DescPose offset_pos, int velAccParamMode, int overSpeedStrategy, int speedPercent)

Ruch liniowy w przestrzeni kartezjańskiej (przeciążona funkcja 2 bez konieczności podawania pozycji przegubów)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Ruch liniowy w przestrzeni kartezjańskiej (przeciążona funkcja 2 bez konieczności podawania pozycji przegubów)
    * @param  [in] desc_pos   Docelowa poza kartezjańska
    * @param  [in] tool  Numer narzędzia, zakres [1~15]
    * @param  [in] user  Numer przedmiotu, zakres [1~15]
    * @param  [in] vel  Procent prędkości, zakres [0~100]
    * @param  [in] acc  Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param  [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]
    * @param  [in] blendR [-1.0]-ruch do pozycji (blokujący), [0~1000.0]-promień wygładzania (nieblokujący), jednostka mm
    * @param  [in] blendMode Sposób przejścia; 0-przejście styczne wewnętrznie; 1-przejście narożne
    * @param  [in] epos  Pozycja osi rozszerzenia, jednostka mm
    * @param  [in] search  0-brak poszukiwania pozycji drutu, 1-poszukiwanie pozycji drutu
    * @param  [in] offset_flag  0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie przedmiotu, 2-przesunięcie w układzie narzędzia
    * @param  [in] offset_pos  Wartość przesunięcia pozy
    * @param  [in] config Konfiguracja przestrzeni przegubów dla kinematyki odwrotnej, [-1]-obliczenia względem bieżącej pozycji przegubów, [0~7]-obliczenia według określonej konfiguracji przestrzeni przegubów
    * @param  [in] velAccParamMode Tryb parametrów prędkości i przyspieszenia; 0-procentowy; 1-prędkość fizyczna (mm/s) przyspieszenie (mm/s2)
    * @param  [in] overSpeedStrategy  Strategia przekroczenia prędkości, 1-standardowa; 2-zatrzymanie z błędem przy przekroczeniu prędkości; 3-adaptacyjne zmniejszenie prędkości, domyślnie 0
    * @param  [in] speedPercent  Procentowy próg dopuszczalnego zmniejszenia prędkości [0-100], domyślnie 10%
    * @return  Kod błędu
    */
    public int MoveL(DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, int blendMode, ExaxisPos epos, int search, int offset_flag, DescPose offset_pos, int config, int velAccParamMode, int overSpeedStrategy, int speedPercent)

Ruch po łuku w przestrzeni kartezjańskiej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Ruch po łuku w przestrzeni kartezjańskiej
    * @param  joint_pos_p  Pozycja przegubów punktu pośredniego, jednostka deg
    * @param  desc_pos_p   Pozycja kartezjańska punktu pośredniego
    * @param  ptool  Numer narzędzia, zakres [1~15]
    * @param  puser  Numer przedmiotu, zakres [1~15]
    * @param  pvel  Procent prędkości, zakres [0~100]
    * @param  pacc  Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param  epos_p  Pozycja osi rozszerzenia, jednostka mm
    * @param  poffset_flag  0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie przedmiotu, 2-przesunięcie w układzie narzędzia
    * @param  offset_pos_p  Wartość przesunięcia pozy
    * @param  joint_pos_t  Pozycja przegubów punktu docelowego, jednostka deg
    * @param  desc_pos_t   Pozycja kartezjańska punktu docelowego
    * @param  ttool  Numer narzędzia, zakres [1~15]
    * @param  tuser  Numer przedmiotu, zakres [1~15]
    * @param  tvel  Procent prędkości, zakres [0~100]
    * @param  tacc  Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param  epos_t  Pozycja osi rozszerzenia, jednostka mm
    * @param  toffset_flag  0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie przedmiotu, 2-przesunięcie w układzie narzędzia
    * @param  offset_pos_t  Wartość przesunięcia pozy
    * @param  ovl  Współczynnik skalowania prędkości [0~100]/prędkość fizyczna (mm/s)
    * @param  blendR [-1.0]-ruch do pozycji (blokujący), [0~1000.0]-promień wygładzania (nieblokujący), jednostka mm
    * @param  oacc Współczynnik skalowania przyspieszenia [0-100]/przyspieszenie fizyczne (mm/s2)
    * @param  velAccParamMode Tryb parametrów prędkości i przyspieszenia; 0-procentowy; 1-prędkość fizyczna (mm/s) przyspieszenie (mm/s2)
    * @return  Kod błędu
    */
    public int MoveC(JointPos joint_pos_p, DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p, JointPos joint_pos_t, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t, double ovl, double blendR, double oacc,int velAccParamMode)

Ruch po łuku w przestrzeni kartezjańskiej (automatyczne obliczenia kinematyki odwrotnej)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Ruch po łuku w przestrzeni kartezjańskiej (automatyczne obliczenia kinematyki odwrotnej)
    * @param [in] desc_pos_p   Pozycja kartezjańska punktu pośredniego
    * @param [in] ptool  Numer narzędzia, zakres [1~15]
    * @param [in] puser  Numer przedmiotu, zakres [1~15]
    * @param [in] pvel  Procent prędkości, zakres [0~100]
    * @param [in] pacc  Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param [in] epos_p  Pozycja osi rozszerzenia, jednostka mm
    * @param [in] poffset_flag  0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie przedmiotu, 2-przesunięcie w układzie narzędzia
    * @param [in] offset_pos_p  Wartość przesunięcia pozy
    * @param [in] desc_pos_t   Pozycja kartezjańska punktu docelowego
    * @param [in] ttool  Numer narzędzia, zakres [1~15]
    * @param [in] tuser  Numer przedmiotu, zakres [1~15]
    * @param [in] tvel  Procent prędkości, zakres [0~100]
    * @param [in] tacc  Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param [in] epos_t  Pozycja osi rozszerzenia, jednostka mm
    * @param [in] toffset_flag  0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie przedmiotu, 2-przesunięcie w układzie narzędzia
    * @param [in] offset_pos_t  Wartość przesunięcia pozy
    * @param [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]
    * @param [in] blendR [-1.0]-ruch do pozycji (blokujący), [0~1000.0]-promień wygładzania (nieblokujący), jednostka mm
    * @param [in] config Konfiguracja przestrzeni przegubów dla kinematyki odwrotnej, [-1]-obliczenia względem bieżącej pozycji przegubów, [0~7]-obliczenia według określonej konfiguracji przestrzeni przegubów
    * @return  Kod błędu
    */
    int MoveC(DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t, double ovl, double blendR, int config)

Ruch po łuku w przestrzeni kartezjańskiej (z dodanym parametrem trybu parametrów prędkości i przyspieszenia velAccParamMode)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Ruch po łuku w przestrzeni kartezjańskiej (z dodanym parametrem trybu parametrów prędkości i przyspieszenia velAccParamMode)
    * @param  [in] joint_pos_p  Pozycja przegubów punktu pośredniego, jednostka deg
    * @param  [in] desc_pos_p   Pozycja kartezjańska punktu pośredniego
    * @param  [in] ptool  Numer narzędzia, zakres [1~15]
    * @param  [in] puser  Numer przedmiotu, zakres [1~15]
    * @param  [in] pvel  Procent prędkości, zakres [0~100]
    * @param  [in] pacc  Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param  [in] epos_p  Pozycja osi rozszerzenia, jednostka mm
    * @param  [in] poffset_flag  0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie przedmiotu, 2-przesunięcie w układzie narzędzia
    * @param  [in] offset_pos_p  Wartość przesunięcia pozy
    * @param  [in] joint_pos_t  Pozycja przegubów punktu docelowego, jednostka deg
    * @param  [in] desc_pos_t   Pozycja kartezjańska punktu docelowego
    * @param  [in] ttool  Numer narzędzia, zakres [1~15]
    * @param  [in] tuser  Numer przedmiotu, zakres [1~15]
    * @param  [in] tvel  Procent prędkości, zakres [0~100]
    * @param  [in] tacc  Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param  [in] epos_t  Pozycja osi rozszerzenia, jednostka mm
    * @param  [in] toffset_flag  0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie przedmiotu, 2-przesunięcie w układzie narzędzia
    * @param  [in] offset_pos_t  Wartość przesunięcia pozy
    * @param  [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]
    * @param  [in] blendR [-1.0]-ruch do pozycji (blokujący), [0~1000.0]-promień wygładzania (nieblokujący), jednostka mm
    * @param  [in] velAccParamMode Tryb parametrów prędkości i przyspieszenia; 0-procentowy; 1-prędkość fizyczna (mm/s) przyspieszenie (mm/s2)
    * @return  Kod błędu
    */
    public int MoveC(JointPos joint_pos_p, DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p, JointPos joint_pos_t, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t, double ovl, double blendR, int velAccParamMode)

Ruch po łuku w przestrzeni kartezjańskiej (przeciążona funkcja 1 bez konieczności podawania pozycji przegubów)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Ruch po łuku w przestrzeni kartezjańskiej (przeciążona funkcja 1 bez konieczności podawania pozycji przegubów)
    * @param  [in] desc_pos_p   Pozycja kartezjańska punktu pośredniego    * @param  [in] ptool  Numer narzędzia, zakres [1~15]
    * @param  [in] puser  Numer przedmiotu, zakres [1~15]
    * @param  [in] pvel  Procent prędkości, zakres [0~100]
    * @param  [in] pacc  Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param  [in] epos_p  Pozycja osi rozszerzenia, jednostka mm
    * @param  [in] poffset_flag  0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie przedmiotu, 2-przesunięcie w układzie narzędzia
    * @param  [in] offset_pos_p  Wartość przesunięcia pozy
    * @param  [in] desc_pos_t   Pozycja kartezjańska punktu docelowego
    * @param  [in] ttool  Numer narzędzia, zakres [1~15]
    * @param  [in] tuser  Numer przedmiotu, zakres [1~15]
    * @param  [in] tvel  Procent prędkości, zakres [0~100]
    * @param  [in] tacc  Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param  [in] epos_t  Pozycja osi rozszerzenia, jednostka mm
    * @param  [in] toffset_flag  0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie przedmiotu, 2-przesunięcie w układzie narzędzia
    * @param  [in] offset_pos_t  Wartość przesunięcia pozy
    * @param  [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]
    * @param  [in] blendR [-1.0]-ruch do pozycji (blokujący), [0~1000.0]-promień wygładzania (nieblokujący), jednostka mm
    * @param  [in] config Konfiguracja przestrzeni przegubów dla kinematyki odwrotnej, [-1]-obliczenia względem bieżącej pozycji przegubów, [0~7]-obliczenia według określonej konfiguracji przestrzeni przegubów
    * @param  [in] velAccParamMode Tryb parametrów prędkości i przyspieszenia; 0-procentowy; 1-prędkość fizyczna (mm/s) przyspieszenie (mm/s2)
    * @return  Kod błędu
    */
    public int MoveC(DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t, double ovl, double blendR, int config, int velAccParamMode)

Ruch po pełnym okręgu w przestrzeni kartezjańskiej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionchanged:: Java SDK-v1.0.6-3.8.3

.. code-block:: Java
    :linenos:

    /**
    *@brief  Ruch po pełnym okręgu w przestrzeni kartezjańskiej
    *@param  joint_pos_p  Pozycja przegubów punktu pośredniego 1, jednostka deg
    *@param  desc_pos_p   Pozycja kartezjańska punktu pośredniego 1
    *@param  ptool  Numer narzędzia, zakres [1~15]
    *@param  puser  Numer przedmiotu, zakres [1~15]
    *@param  pvel  Procent prędkości, zakres [0~100]
    *@param  pacc  Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    *@param  epos_p  Pozycja osi rozszerzenia, jednostka mm
    *@param  joint_pos_t  Pozycja przegubów punktu pośredniego 2, jednostka deg
    *@param  desc_pos_t   Pozycja kartezjańska punktu pośredniego 2
    *@param  ttool  Numer narzędzia, zakres [1~15]
    *@param  tuser  Numer przedmiotu, zakres [1~15]
    *@param  tvel  Procent prędkości, zakres [0~100]
    *@param  tacc  Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    *@param  epos_t  Pozycja osi rozszerzenia, jednostka mm
    *@param  ovl  Współczynnik skalowania prędkości [0~100]/prędkość fizyczna (mm/s)
    *@param  offset_flag  0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie przedmiotu, 2-przesunięcie w układzie narzędzia
    *@param  offset_pos  Wartość przesunięcia pozy
    *@param  oacc Współczynnik skalowania przyspieszenia [0-100]/przyspieszenie fizyczne (mm/s2)
    *@param  blendR -1: blokujący; 0~1000: promień wygładzania
    *@param  velAccParamMode Tryb parametrów prędkości i przyspieszenia; 0-procentowy; 1-prędkość fizyczna (mm/s) przyspieszenie (mm/s2)
    *@return  Kod błędu
    */
    public int Circle(JointPos joint_pos_p, DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, JointPos joint_pos_t, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, double ovl, int offset_flag, DescPose offset_pos, double oacc, double blendR, int velAccParamMode)

Ruch po pełnym okręgu w przestrzeni kartezjańskiej (automatyczne obliczenia kinematyki odwrotnej)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
     * @brief  Ruch po pełnym okręgu w przestrzeni kartezjańskiej (automatyczne obliczenia kinematyki odwrotnej)
     * @param  [in] desc_pos_p   Pozycja kartezjańska punktu pośredniego 1
     * @param  [in] ptool  Numer narzędzia, zakres [0~14]
     * @param  [in] puser  Numer przedmiotu, zakres [0~14]
     * @param  [in] pvel  Procent prędkości, zakres [0~100]
     * @param  [in] pacc  Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
     * @param  [in] epos_p  Pozycja osi rozszerzenia, jednostka mm
     * @param  [in] desc_pos_t   Pozycja kartezjańska punktu pośredniego 2
     * @param  [in] ttool  Numer narzędzia, zakres [0~14]
     * @param  [in] tuser  Numer przedmiotu, zakres [0~14]
     * @param  [in] tvel  Procent prędkości, zakres [0~100]
     * @param  [in] tacc  Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
     * @param  [in] epos_t  Pozycja osi rozszerzenia, jednostka mm
     * @param  [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]
     * @param  [in] offset_flag  0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie przedmiotu, 2-przesunięcie w układzie narzędzia
     * @param  [in] offset_pos  Wartość przesunięcia pozy
     * @param  [in] oacc Procent przyspieszenia
     * @param  [in] blendR -1: blokujący; 0~1000: promień wygładzania
     * @param  [in] config Konfiguracja przestrzeni przegubów dla kinematyki odwrotnej, [-1]-obliczenia względem bieżącej pozycji przegubów, [0~7]-obliczenia według określonej konfiguracji przestrzeni przegubów
     * @return  Kod błędu
     */
    int Circle(DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, double ovl, int offset_flag, DescPose offset_pos, double oacc, double blendR,int config)

Ruch po pełnym okręgu w przestrzeni kartezjańskiej (z dodanym parametrem trybu parametrów prędkości i przyspieszenia velAccParamMode)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    *@brief  Ruch po pełnym okręgu w przestrzeni kartezjańskiej (z dodanym parametrem trybu parametrów prędkości i przyspieszenia velAccParamMode)
    *@param  [in] joint_pos_p  Pozycja przegubów punktu pośredniego 1, jednostka deg
    *@param  [in] desc_pos_p   Pozycja kartezjańska punktu pośredniego 1
    *@param  [in] ptool  Numer narzędzia, zakres [1~15]
    *@param  [in] puser  Numer przedmiotu, zakres [1~15]
    *@param  [in] pvel  Procent prędkości, zakres [0~100]
    *@param  [in] pacc  Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    *@param  [in] epos_p  Pozycja osi rozszerzenia, jednostka mm
    *@param  [in] joint_pos_t  Pozycja przegubów punktu pośredniego 2, jednostka deg
    *@param  [in] desc_pos_t   Pozycja kartezjańska punktu pośredniego 2
    *@param  [in] ttool  Numer narzędzia, zakres [1~15]
    *@param  [in] tuser  Numer przedmiotu, zakres [1~15]
    *@param  [in] tvel  Procent prędkości, zakres [0~100]
    *@param  [in] tacc  Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    *@param  [in] epos_t  Pozycja osi rozszerzenia, jednostka mm
    *@param  [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]
    *@param  [in] offset_flag  0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie przedmiotu, 2-przesunięcie w układzie narzędzia
    *@param  [in] offset_pos  Wartość przesunięcia pozy
    *@param  [in] oacc Procent przyspieszenia
    *@param  [in] blendR -1: blokujący; 0~1000: promień wygładzania
    *@param  [in] velAccParamMode Tryb parametrów prędkości i przyspieszenia; 0-procentowy; 1-prędkość fizyczna (mm/s) przyspieszenie (mm/s2)
    *@return  Kod błędu
    */
    public int Circle(JointPos joint_pos_p, DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, JointPos joint_pos_t, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, double ovl, int offset_flag, DescPose offset_pos, double oacc, double blendR, int velAccParamMode)

Ruch po pełnym okręgu w przestrzeni kartezjańskiej (przeciążona funkcja 1 bez konieczności podawania pozycji przegubów)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Ruch po pełnym okręgu w przestrzeni kartezjańskiej (przeciążona funkcja 1 bez konieczności podawania pozycji przegubów)
    * @param  [in] desc_pos_p   Pozycja kartezjańska punktu pośredniego 1
    * @param  [in] ptool  Numer narzędzia, zakres [0~14]
    * @param  [in] puser  Numer przedmiotu, zakres [0~14]
    * @param  [in] pvel  Procent prędkości, zakres [0~100]
    * @param  [in] pacc  Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param  [in] epos_p  Pozycja osi rozszerzenia, jednostka mm
    * @param  [in] desc_pos_t   Pozycja kartezjańska punktu pośredniego 2
    * @param  [in] ttool  Numer narzędzia, zakres [0~14]
    * @param  [in] tuser  Numer przedmiotu, zakres [0~14]
    * @param  [in] tvel  Procent prędkości, zakres [0~100]
    * @param  [in] tacc  Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param  [in] epos_t  Pozycja osi rozszerzenia, jednostka mm
    * @param  [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]
    * @param  [in] offset_flag  0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie przedmiotu, 2-przesunięcie w układzie narzędzia
    * @param  [in] offset_pos  Wartość przesunięcia pozy
    * @param  [in] oacc Procent przyspieszenia
    * @param  [in] blendR -1: blokujący; 0~1000: promień wygładzania
    * @param  [in] config Konfiguracja przestrzeni przegubów dla kinematyki odwrotnej, [-1]-obliczenia względem bieżącej pozycji przegubów, [0~7]-obliczenia według określonej konfiguracji przestrzeni przegubów
    * @param  [in] velAccParamMode Tryb parametrów prędkości i przyspieszenia; 0-procentowy; 1-prędkość fizyczna (mm/s) przyspieszenie (mm/s2)
    * @return  Kod błędu
    */
    public int Circle(DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, double ovl, int offset_flag, DescPose offset_pos, double oacc, double blendR, int config, int velAccParamMode)

Ruch punkt-punkt w przestrzeni kartezjańskiej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Ruch punkt-punkt w przestrzeni kartezjańskiej 
    * @param [in] desc_pos  Docelowa poza kartezjańska lub przyrost pozy
    * @param [in] tool  Numer narzędzia, zakres [0~14]
    * @param [in] user  Numer przedmiotu, zakres [0~14]
    * @param [in] vel  Procent prędkości, zakres [0~100]
    * @param [in] acc  Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]
    * @param [in] blendT [-1.0]-ruch do pozycji (blokujący), [0~500.0]-czas wygładzania (nieblokujący), jednostka ms
    * @param [in] config  Konfiguracja przestrzeni przegubów, [-1]-obliczenia względem bieżącej pozycji przegubów, [0~7]-obliczenia według określonej konfiguracji przestrzeni przegubów, domyślnie -1
    * @return Kod błędu 
    */ 
    int MoveCart(DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendT, int config);

Przykład kodu podstawowych instrukcji ruchu robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestMove(Robot robot)
    {
        int rtn=-1;
        JointPos j1=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j2=new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
        JointPos j3=new JointPos(-29.777, -84.536, 109.275, -114.075, -86.655, 74.257);
        JointPos j4=new JointPos(-31.154, -95.317, 94.276, -88.079, -89.740, 74.256);
        DescPose desc_pos1=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_pos2=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose desc_pos3=new DescPose(-487.434, 154.362, 308.576, 176.600, 0.268, -14.061);
        DescPose desc_pos4=new DescPose(-443.165, 147.881, 480.951, 179.511, -0.775, -15.409);
        DescPose offset_pos=new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);
        int tool = 0;
        int user = 0;
        double vel = 100.0;
        double acc = 100.0;
        double ovl = 100.0;
        double oacc = 100.0;
        double blendT = 0.0;
        double blendR = 0.0;
        int flag = 0;
        int search = 0;
        int blendMode = 0;
        int velAccMode = 0;
        robot.SetSpeed(20);
        rtn = robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        System.out.printf("movej errcode:%d\n", rtn);
        rtn = robot.MoveL(j2, desc_pos2, tool, user, vel, acc, ovl, blendR, blendMode, epos, search, flag, offset_pos, oacc, velAccMode,0,10);
        System.out.printf("movel errcode:%d\n", rtn);
        rtn = robot.MoveC(j3, desc_pos3, tool, user, vel, acc, epos, flag, offset_pos, j4, desc_pos4, tool, user, vel, acc, epos, flag, offset_pos, ovl, blendR, oacc, velAccMode);
        System.out.printf("movec errcode:%d\n", rtn);
        rtn = robot.MoveJ(j2, desc_pos2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        System.out.printf("movej errcode:%d\n", rtn);
        rtn = robot.Circle(j3, desc_pos3, tool, user, vel, acc, epos, j1, desc_pos1, tool, user, vel, acc, epos, ovl, flag, offset_pos, oacc, -1, velAccMode);
        System.out.printf("circle errcode:%d\n", rtn);
        rtn = robot.MoveCart(desc_pos4, tool, user, vel, acc, ovl, blendT, -1);
        System.out.printf("MoveCart errcode:%d\n", rtn);
        rtn = robot.MoveJ(j1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        System.out.printf("movej errcode:%d\n", rtn);
        rtn = robot.MoveL(desc_pos2, tool, user, vel, acc, ovl, blendR, blendMode, epos, search, flag, offset_pos, -1, velAccMode,0,10);
        System.out.printf("movel errcode:%d\n", rtn);
        rtn = robot.MoveC(desc_pos3, tool, user, vel, acc, epos, flag, offset_pos, desc_pos4, tool, user, vel, acc, epos, flag, offset_pos, ovl, blendR, -1, velAccMode);
        System.out.printf("movec errcode:%d\n", rtn);
        rtn = robot.MoveJ(j2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        System.out.printf("movej errcode:%d\n", rtn);
        rtn = robot.Circle(desc_pos3, tool, user, vel, acc, epos, desc_pos1, tool, user, vel, acc, epos, ovl, flag, offset_pos, oacc, blendR, -1, velAccMode);
        System.out.printf("circle errcode:%d\n", rtn);
        return 0;
    }

Ruch po spirali w przestrzeni kartezjańskiej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Ruch po spirali w przestrzeni kartezjańskiej 
    * @param [in] joint_pos  Docelowa pozycja przegubów, jednostka deg
    * @param [in] desc_pos   Docelowa poza kartezjańska
    * @param [in] tool  Numer narzędzia, zakres [0~14]
    * @param [in] user  Numer przedmiotu, zakres [0~14]
    * @param [in] vel  Procent prędkości, zakres [0~100]
    * @param [in] acc  Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param [in] epos  Pozycja osi rozszerzenia, jednostka mm
    * @param [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]
    * @param [in] offset_flag  0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie przedmiotu, 2-przesunięcie w układzie narzędzia
    * @param [in] offset_pos  Wartość przesunięcia pozy
    * @return Kod błędu 
    */
    int NewSpiral(JointPos joint_pos, DescPose desc_pos, int tool, int user, double vel, double acc, ExaxisPos epos, double ovl, int offset_flag, DescPose offset_pos, SpiralParam spiral_param);

Ruch po spirali w przestrzeni kartezjańskiej (automatyczne obliczenia kinematyki odwrotnej)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief Ruch po spirali w przestrzeni kartezjańskiej (automatyczne obliczenia kinematyki odwrotnej)
    * @param [in] desc_pos   Docelowa poza kartezjańska
    * @param [in] tool  Numer narzędzia, zakres [0~14]
    * @param [in] user  Numer przedmiotu, zakres [0~14]
    * @param [in] vel  Procent prędkości, zakres [0~100]
    * @param [in] acc  Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param [in] epos  Pozycja osi rozszerzenia, jednostka mm
    * @param [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]
    * @param [in] offset_flag  0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie przedmiotu, 2-przesunięcie w układzie narzędzia
    * @param [in] offset_pos  Wartość przesunięcia pozy
    * @param [in] spiral_param  Parametry spirali
    * @param [in] config  Konfiguracja przestrzeni przegubów dla kinematyki odwrotnej, [-1]-obliczenia względem bieżącej pozycji przegubów, [0~7]-obliczenia według określonej konfiguracji przestrzeni przegubów
    * @return Kod błędu 
    */
    int NewSpiral(DescPose desc_pos, int tool, int user, double vel, double acc, ExaxisPos epos, double ovl, int offset_flag, DescPose offset_pos, SpiralParam spiral_param,int config)

Przykład kodu ruchu po spirali
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
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
        System.out.println("movej errcode:"+ rtn);

        rtn = robot.NewSpiral(desc_pos, tool, user, vel, acc, epos, ovl, flag, offset_pos2, sp,-1);
        System.out.println("newspiral errcode:"+ rtn);

        return 0;
    }

Rozpoczęcie ruchu serwo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Rozpoczęcie ruchu serwo, używane razem z instrukcjami ServoJ, ServoCart
    * @param comType Typ wysyłania instrukcji; 0-xmlrpc; 1-UDP (odpowiadający portowi 20007 robota)
    * @return Kod błędu
    */
    public int ServoMoveStart (int comType)

Zakończenie ruchu serwo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Zakończenie ruchu serwo, używane razem z instrukcjami ServoJ, ServoCart
    * @param comType Typ wysyłania instrukcji; 0-xmlrpc; 1-UDP (odpowiadający portowi 20007 robota)
    * @return Kod błędu
    */
    public int ServoMoveEnd (int comType)

Ruch w trybie serwo w przestrzeni przegubów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionchanged:: Java SDK-v1.0.6-3.8.3

.. code-block:: Java
    :linenos:

    /**
    * @brief  Ruch w trybie serwo w przestrzeni przegubów
    * @param  joint_pos  Docelowa pozycja przegubów, jednostka deg
    * @param  axisPos  Pozycja zewnętrznej osi, jednostka mm
    * @param  acc  Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne, domyślnie 0
    * @param  vel  Procent prędkości, zakres [0~100], tymczasowo niedostępne, domyślnie 0
    * @param  cmdT  Okres wysyłania instrukcji, jednostka s, zalecany zakres [0.001~0.0016]
    * @param  filterT Czas filtrowania, jednostka s, tymczasowo niedostępne, domyślnie 0
    * @param  gain  Wzmocnienie proporcjonalne pozycji docelowej, tymczasowo niedostępne, domyślnie 0
    * @param  id ID instrukcji servoJ, domyślnie 0
    * @param comType Typ wysyłania instrukcji; 0-xmlrpc; 1-UDP (odpowiadający portowi 20007 robota)
    * @return Kod błędu
    */
    public int ServoJ(JointPos joint_pos, ExaxisPos axisPos, float acc, float vel, float cmdT, float filterT, float gain, int id, int comType)

Przykład kodu SDK dla ServoJ, ServoMoveStart, ServoMoveEnd opartych na komunikacji UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestServoJ(Robot robot)
    {
        robot.udpCmdClient.SetUDPCmdRpyCallback((srcType, count, cmdID, dataLen, content) -> {
            System.out.println("\n[Received UDP reply from robot]");
            System.out.println("srcType: " + srcType);
            System.out.println("count: " + count);
            System.out.println("cmdID: " + cmdID);
            System.out.println("dataLen: " + dataLen);
            System.out.println("content: " + content);
            return 0;
        });
        int rtn=-1;

        JointPos j=new JointPos(0, 0, 0, 0, 0, 0);
        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);

        double vel = 0.0;
        double acc = 0.0;
        double cmdT = 0.016;
        double filterT = 0.0;
        double gain = 0.0;
        int flag = 0;
        int count = 300;
        double dt = 0.1;
        int cmdID = 0;
        int comType = 1;
        int ret = robot.GetActualJointPosDegree(j);
        if (ret == 0)
        {
            robot.ServoMoveStart(comType);
            count = 300;
            while (count>0)
            {
                robot.ServoJ(j, epos, acc, vel, cmdT, filterT, gain, cmdID, comType);
                j.J1 += dt;
                j.J2 += dt;
                j.J4 += dt;
                j.J5 += dt;
                j.J6 += dt;
                epos.axis1 += dt;
                count -= 1;
                robot.Sleep(10);
            }
            robot.ServoMoveEnd(comType);

            robot.Sleep(1000);
            robot.ServoMoveStart(comType);
            count = 300;
            while (count>0)
            {
                robot.ServoJ(j, epos, acc, vel, cmdT, filterT, gain, cmdID, comType);
                j.J1 -= dt;
                j.J2 -= dt;
                j.J4 -= dt;
                j.J5 -= dt;
                j.J6 -= dt;
                epos.axis1 -= dt;
                count -= 1;
                robot.Sleep(10);
            }
            robot.ServoMoveEnd(comType);
        }
        else
        {
            System.out.println("GetActualJointPosDegree errcode:"+ ret);
        }
    }

Przykładowy program ruchu w trybie serwo w przestrzeni przegubów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static void TestServoJ()
    {
        Robot robot = new Robot();
        robot.SetReconnectParam(true,20,500);//设置重连次数、间隔
        robot.LoggerInit(FrLogType.DIRECT, FrLogLevel.INFO, "D://log", 10, 10);
        int rtn = robot.RPC("192.168.58.2");
        if(rtn == 0)
        {
            System.out.println("rpc连接 success");
        }
        else
        {
            System.out.println("rpc连接 fail");
            return ;
        }
        JointPos j5 = new JointPos();
        ExaxisPos ePos=new ExaxisPos();
        int ret = robot.GetActualJointPosDegree(j5);
        if (ret == 0)
        {
            int count = 200;
            while (count > 0)
            {
                robot.ServoJ(j5, ePos,100, 100, 0.008, 0, 0);
                j5.J1 += 0.2;//1关节位置增加
                count -= 1;
                robot.WaitMs((int)(8));
            }
        }
    }

Rozpoczęcie sterowania momentem obrotowym przegubów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Rozpoczęcie sterowania momentem obrotowym przegubów
    * @param  comType Typ wysyłania instrukcji; 0-xmlrpc; 1-UDP (odpowiadający portowi 20007 robota)
    * @return  Kod błędu
    */
    public int ServoJTStart (int comType)

Sterowanie momentem obrotowym przegubów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Sterowanie momentem obrotowym przegubów
    * @param torque moment obrotowy przegubów j1~j6, jednostka Nm
    * @param interval Okres instrukcji, jednostka s, zakres [0.001~0.008]
    * @param checkFlag Strategia wykrywania 0-brak ograniczeń; 1-ograniczenie mocy; 2-ograniczenie prędkości; 3-ograniczenie mocy i prędkości jednocześnie
    * @param jPowerLimit Maksymalne ograniczenie mocy przegubu (W)
    * @param jVelLimit Maksymalna prędkość przegubu (°/s)
    * @param  comType Typ wysyłania instrukcji; 0-xmlrpc; 1-UDP (odpowiadający portowi 20007 robota)
    * @return Kod błędu
    */
    public int ServoJT(double[] torque, double interval, int checkFlag, double[] jPowerLimit, double[] jVelLimit, int comType)

Zakończenie sterowania momentem obrotowym przegubów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Zakończenie sterowania momentem obrotowym przegubów
    * @param comType Typ wysyłania instrukcji; 0-xmlrpc; 1-UDP (odpowiadający portowi 20007 robota)
    * @return  Kod błędu
    */
    public int ServoJTEnd (int comType)

Przykładowy program ruchu w trybie serwo w przestrzeni przegubów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestServoJT(Robot robot)
    {

        robot.DragTeachSwitch(1);
        List<Number> joint_toq=new ArrayList<>();
        joint_toq=robot.GetJointTorques(1);

        int count = 100;
        robot.ServoJTStart(); //   #servoJT开始
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

Przykład kodu SDK dla ServoJT, ServoJTStart, ServoJTEnd opartych na komunikacji UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static void ServoJTWithSafety(Robot robot)
    {
        robot.udpCmdClient.SetUDPCmdRpyCallback((srcType, count, cmdID, dataLen, content) -> {
            System.out.println("\n[Received UDP reply from robot]");
            System.out.println("srcType: " + srcType);
            System.out.println("count: " + count);
            System.out.println("cmdID: " + cmdID);
            System.out.println("dataLen: " + dataLen);
            System.out.println("content: " + content);
            return 0;
        });
        while (true) {
            robot.ResetAllError();
            robot.Sleep(500);
            List<Number> torques;
            torques=robot.GetJointTorques(1);
            robot.ServoJTStart(1); //   #servoJT开始
            ROBOT_STATE_PKG pkg=new ROBOT_STATE_PKG();
            robot.DragTeachSwitch(1);
            int checkFlag = 3;//-1,3
            double[] jPowerLimit = { 10.0, 10.0, 10.0, 10.0, 10.0, 10.0 };
            double[] jVelLimit = { 50, 50, 50, 50, 50, 50};//180.1,-1
            int count = 800000;
            int error = 0;
            int comType = 1;

            double[] tor=new double[]{(double)torques.get(1),(double)torques.get(2),(double)torques.get(3),(double)torques.get(4),(double)torques.get(5),(double)torques.get(6)};

            while (true) {
                tor[0] = 0.08;//  #每次1轴增加0.01NM，运动100次
                error = robot.ServoJT(tor, 0.01, checkFlag, jPowerLimit, jVelLimit, comType);  //# 关节空间伺服模式运动
                System.out.printf("ServoJT rtn is %d\n", error);
                count = count - 1;
                robot.Sleep(1);
                pkg = robot.GetRobotRealTimeState();
                System.out.printf("maincode %d, subcode %d\n", pkg.main_code, pkg.sub_code);
                if (pkg.jt_cur_pos[0] > 30)
                    break;
            }

            tor = new double[]{(double) torques.get(1), (double) torques.get(2), (double) torques.get(3), (double) torques.get(4), (double) torques.get(5), (double) torques.get(6)};
            while (true) {
                tor[0] = -0.08;//  #每次1轴增加0.01NM，运动100次
                error = robot.ServoJT(tor, 0.01, checkFlag, jPowerLimit, jVelLimit, 1);  //# 关节空间伺服模式运动
                System.out.printf("ServoJT rtn is %d\n", error);
                count = count - 1;
                robot.Sleep(1);
                pkg = robot.GetRobotRealTimeState();
                System.out.printf("maincode %d, subcode %d\n", pkg.main_code, pkg.sub_code);
                if (pkg.jt_cur_pos[0] < 0)
                    break;
            }

            robot.DragTeachSwitch(0);

            error = robot.ServoJTEnd(1);  //#伺服运动结束
        }
    }

Przykład kodu sterowania momentem obrotowym przegubów z ochroną przed przekroczeniem prędkości
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static void ServoJTWithSafety(Robot robot)
    {
        robot.ResetAllError();
        robot.Sleep(500);
        List<Number> torques;
        torques=robot.GetJointTorques(1);
        robot.ServoJTStart(); //   #servoJT开始
        ROBOT_STATE_PKG pkg=new ROBOT_STATE_PKG();
        robot.DragTeachSwitch(1);
        int checkFlag = 3;//-1,3
        //double[] jPowerLimit = {1.0,1.0,1.0,1.0,1.0,1.0};//5001
        double[] jPowerLimit = { 10.0, 10.0, 10.0, 10.0, 10.0, 10.0 };
        double[] jVelLimit = { 50, 50, 50, 50, 50, 50};//180.1,-1
        int count = 800000;
        int error = 0;
        double[] tor=new double[]{(double)torques.get(1),(double)torques.get(2),(double)torques.get(3),(double)torques.get(4),(double)torques.get(5),(double)torques.get(6)};
        while (count > 0)
        {
            tor[2] = tor[2]+0.01;//  #每次1轴增加0.01NM，运动100次
            error = robot.ServoJT(tor, 0.01, checkFlag, jPowerLimit, jVelLimit);  //# 关节空间伺服模式运动
            System.out.printf("ServoJT rtn is %d\n", error);
            count = count - 1;
            robot.Sleep(1);
            pkg=robot.GetRobotRealTimeState();
            System.out.printf("maincode %d, subcode %d\n", pkg.main_code, pkg.sub_code);
        }
        robot.DragTeachSwitch(0);
        error = robot.ServoJTEnd();  //#伺服运动结束
    }

Ruch w trybie serwo w przestrzeni kartezjańskiej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    *@brief Ruch w trybie serwo w przestrzeni kartezjańskiej
    *@param mode 0-ruch absolutny (układ bazowy), 1-ruch przyrostowy (układ bazowy), 2-ruch przyrostowy (układ narzędzia)
    *@param desc_pose Docelowa poza kartezjańska lub przyrost pozy
    *@param exaxis Pozycja osi rozszerzenia
    *@param pos_gain Współczynnik proporcjonalny przyrostu pozy, działa tylko w ruchu przyrostowym, zakres [0~1]
    *@param acc Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne, domyślnie 0
    *@param vel Procent prędkości, zakres [0~100], tymczasowo niedostępne, domyślnie 0
    *@param cmdT Okres wysyłania instrukcji, jednostka s, zalecany zakres [0.001~0.016]
    *@param filterT Czas filtrowania, jednostka s, tymczasowo niedostępne, domyślnie 0
    *@param gain Wzmocnienie proporcjonalne pozycji docelowej, tymczasowo niedostępne, domyślnie 0
    *@return Kod błędu
    */
    public int ServoCart(int mode, DescPose desc_pose, ExaxisPos exaxis, double[] pos_gain, double acc, double vel, double cmdT, double filterT, double gain)

Przykład kodu ruchu w trybie serwo w przestrzeni kartezjańskiej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static void TestServoCart1(Robot robot)
    {
        DescPose desc_pos_dt = new DescPose(83.00800, 50.525000 , 29.246 , 179.629 , -7.138 , -166.975 );
        ExaxisPos exaxis = new ExaxisPos( 100.0, 0.0, 0.0, 0.0 );
        double[] pos_gain = { 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 };
        int mode = 0;
        double vel = 0.0;
        double acc = 0.0;
        double cmdT = 0.001;
        double filterT = 0.0;
        double gain = 0.0;
        int flag = 0;
        int count = 5000;
        robot.SetSpeed(20);
        while (count>0)
        {
            int rtn = robot.ServoCart(mode, desc_pos_dt, exaxis, pos_gain, acc, vel, cmdT, filterT, gain);
            System.out.printf("ServoCart rtn is %d\n", rtn);
            count -= 1;
            desc_pos_dt.tran.x += 0.01;
            exaxis.axis1 += 0.01;
        }
        robot.CloseRPC();
    }

Rozpoczęcie ruchu po krzywej składanej (spline)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Rozpoczęcie ruchu po krzywej składanej (spline)
    * @return  Kod błędu
    */
    int SplineStart();

Ruch PTP (punkt-punkt) po krzywej składanej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Ruch po krzywej składanej w przestrzeni przegubów
    * @param  [in] joint_pos  Docelowa pozycja przegubów, jednostka deg
    * @param  [in] desc_pos   Docelowa poza kartezjańska
    * @param  [in] tool  Numer narzędzia, zakres [0~14]
    * @param  [in] user  Numer przedmiotu, zakres [0~14]
    * @param  [in] vel  Procent prędkości, zakres [0~100]
    * @param  [in] acc  Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param  [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]
    * @return  Kod błędu
    */
    int SplinePTP(JointPos joint_pos, DescPose desc_pos, int tool, int user, double vel, double acc, double ovl);

Ruch po krzywej składanej w przestrzeni przegubów (automatyczne obliczenia kinematyki prostej)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Ruch po krzywej składanej w przestrzeni przegubów (automatyczne obliczenia kinematyki prostej)
    * @param  [in] joint_pos  Docelowa pozycja przegubów, jednostka deg
    * @param  [in] tool  Numer narzędzia, zakres [0~14]
    * @param  [in] user  Numer przedmiotu, zakres [0~14]
    * @param  [in] vel  Procent prędkości, zakres [0~100]
    * @param  [in] acc  Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param  [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]
    * @return  Kod błędu
    */
    int SplinePTP(JointPos joint_pos, int tool, int user, double vel, double acc, double ovl)

Zakończenie ruchu po krzywej składanej (spline)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Zakończenie ruchu po krzywej składanej (spline)
    * @return  Kod błędu
    */
    int SplineEnd(); 

Przykład kodu ruchu po krzywej składanej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestSpline(Robot robot)
    {
        JointPos j1=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j2=new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
        JointPos j3=new JointPos(-61.954, -84.409, 108.153, -116.316, -91.283, 74.260);
        JointPos j4=new JointPos(-89.575, -80.276, 102.713, -116.302, -91.284, 74.267);
        DescPose offset_pos=new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);

        int tool = 0;
        int user = 0;
        double vel = 100.0;
        double acc = 100.0;
        double ovl = 100.0;
        double blendT = -1.0;
        int flag = 0;

        int err1 = robot.MoveJ(j1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        System.out.println("movej errcode:"+ err1);
        robot.SplineStart();
        robot.SplinePTP(j1, tool, user, vel, acc, ovl);
        robot.SplinePTP(j2, tool, user, vel, acc, ovl);
        robot.SplinePTP(j3, tool, user, vel, acc, ovl);
        robot.SplinePTP(j4, tool, user, vel, acc, ovl);
        robot.SplineEnd();
        return 0;
    }

Rozpoczęcie nowego ruchu po krzywej składanej (new spline)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Rozpoczęcie nowego ruchu po krzywej składanej (new spline) 
    * @param [in] type   0-przejście łukowe, 1-punkty podane jako punkty ścieżki
    * @param [in] averageTime  Globalny średni czas łączenia (ms)(10 ~  ), domyślnie 2000
    * @return Kod błędu 
    */ 
    int NewSplineStart(int type, int averageTime);
    
Punkt instrukcji nowej krzywej składanej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Dodanie punktu instrukcji ruchu po krzywej składanej 
    * @param [in] joint_pos  Docelowa pozycja przegubów, jednostka deg
    * @param [in] desc_pos   Docelowa poza kartezjańska
    * @param [in] tool  Numer narzędzia, zakres [0~14]
    * @param [in] user  Numer przedmiotu, zakres [0~14]
    * @param [in] vel  Procent prędkości, zakres [0~100]
    * @param [in] acc  Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]
    * @param [in] blendR [-1.0]-ruch do pozycji (blokujący), [0~1000.0]-promień wygładzania (nieblokujący), jednostka mm
    * @param [in] lastFlag Czy to ostatni punkt, 0-nie, 1-tak
    * @return Kod błędu 
    */ 
    int NewSplinePoint(JointPos joint_pos, DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, int lastFlag);

Punkt instrukcji nowej krzywej składanej (automatyczne obliczenia kinematyki odwrotnej)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief Punkt instrukcji nowej krzywej składanej (automatyczne obliczenia kinematyki odwrotnej)
    * @param  [in] desc_pos   Docelowa poza kartezjańska
    * @param  [in] tool  Numer narzędzia, zakres [0~14]
    * @param  [in] user  Numer przedmiotu, zakres [0~14]
    * @param  [in] vel  Procent prędkości, zakres [0~100]
    * @param  [in] acc  Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param  [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]
    * @param  [in] blendR [-1.0]-ruch do pozycji (blokujący), [0~1000.0]-promień wygładzania (nieblokujący), jednostka mm
    * @param  [in] lastFlag Czy to ostatni punkt, 0-nie, 1-tak
    * @param  [in] config Konfiguracja przestrzeni przegubów dla kinematyki odwrotnej, [-1]-obliczenia względem bieżącej pozycji przegubów, [0~7]-obliczenia według określonej konfiguracji przestrzeni przegubów
    * @return  Kod błędu
    */
    int NewSplinePoint(DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, int lastFlag,int config)

Zakończenie nowego ruchu po krzywej składanej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Zakończenie nowego ruchu po krzywej składanej 
    * @return Kod błędu 
    */ 
    int NewSplineEnd();
    
Przykład kodu nowego ruchu po krzywej składanej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestNewSpline(Robot robot)
    {
        JointPos j1=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        DescPose desc_pos1=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_pos2=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose desc_pos3=new DescPose(-327.622, 402.230, 320.402, -178.067, 2.127, -46.207);
        DescPose desc_pos4=new DescPose(-104.066, 544.321, 327.023, -177.715, 3.371, -73.818);
        DescPose desc_pos5=new DescPose(-33.421, 732.572, 275.103, -177.907, 2.709, -79.482);
        DescPose offset_pos=new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);


        int tool = 0;
        int user = 0;
        double vel = 100.0;
        double acc = 100.0;
        double ovl = 100.0;
        double blendT = -1.0;
        int flag = 0;


        int err1 = robot.MoveJ(j1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        System.out.println("movej errcode:"+ err1);
        robot.NewSplineStart(1, 2000);
        robot.NewSplinePoint(desc_pos1, tool, user, vel, acc, ovl, -1, 0,-1);
        robot.NewSplinePoint(desc_pos2, tool, user, vel, acc, ovl, -1, 0,-1);
        robot.NewSplinePoint(desc_pos3, tool, user, vel, acc, ovl, -1, 0,-1);
        robot.NewSplinePoint(desc_pos4, tool, user, vel, acc, ovl, -1, 0,-1);
        robot.NewSplinePoint(desc_pos5, tool, user, vel, acc, ovl, -1, 0,-1);
        robot.NewSplineEnd();
        return 0;
    }

Zatrzymanie ruchu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Zatrzymanie ruchu
    * @return  Kod błędu
    */
    int StopMotion();

Wstrzymanie ruchu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:
    
    /** 
      * @brief Wstrzymanie ruchu 
      * @return Kod błędu 
    */  
    int PauseMotion();

Wznowienie ruchu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Wznowienie ruchu 
    * @return Kod błędu 
    */ 
    int ResumeMotion();

Przykład kodu wstrzymywania, wznawiania i zatrzymywania ruchu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestPause(Robot robot)
    {
        JointPos j1=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j5=new JointPos(-95.228, -54.621, 73.691, -112.245, -91.280, 74.268);
        DescPose desc_pos1=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_pos5=new DescPose(-33.421, 732.572, 275.103, -177.907, 2.709, -79.482);
        DescPose offset_pos=new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);

        int tool = 0;
        int user = 0;
        double vel = 100.0;
        double acc = 100.0;
        double ovl = 100.0;
        double blendT = -1.0;
        int flag = 0;

        robot.SetSpeed(20);
        int rtn=-1;
        rtn = robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        rtn = robot.MoveJ(j5, desc_pos5, tool, user, vel, acc, ovl, epos, 1, flag, offset_pos);
        robot.Sleep(1000);
        robot.PauseMotion();

        robot.Sleep(1000);
        robot.ResumeMotion();

        robot.Sleep(1000);
        robot.StopMotion();

        robot.Sleep(1000);

        return 0;
    }

Rozpoczęcie globalnego przesunięcia punktów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Rozpoczęcie globalnego przesunięcia punktów
    * @param  [in]  flag  0-przesunięcie w układzie bazowym/układzie przedmiotu, 2-przesunięcie w układzie narzędzia
    * @param  [in]  offset_pos  Wartość przesunięcia pozy
    * @return  Kod błędu
    */
    int PointsOffsetEnable(int flag, DescPose offset_pos); 


Zakończenie globalnego przesunięcia punktów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Zakończenie globalnego przesunięcia punktów
    * @return  Kod błędu
    */
    int PointsOffsetDisable(); 

Przykład kodu przesunięcia punktów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestOffset(Robot robot)
    {
        JointPos j1=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j2=new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);

        DescPose desc_pos1=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_pos2=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);

        DescPose offset_pos=new DescPose(0, 0, 0, 0, 0, 0);
        DescPose offset_pos1=new DescPose(0, 0, 50, 0, 0, 0);
        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);

        int tool = 0;
        int user = 0;
        double vel = 100.0;
        double acc = 100.0;
        double ovl = 100.0;
        double blendT = -1.0;
        int flag = 0;

        robot.SetSpeed(20);

        robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveJ(j2, desc_pos2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.Sleep(1000);
        robot.PointsOffsetEnable(0, offset_pos1);
        robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveJ(j2, desc_pos2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.PointsOffsetDisable();

        return 0;
    }

Rozpoczęcie zdjęcia seryjnego AO skrzynki kontrolnej (fly拍摄)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Rozpoczęcie zdjęcia seryjnego AO skrzynki kontrolnej (fly拍摄)
    * @param [in] AONum Numer AO skrzynki kontrolnej
    * @param [in] maxTCPSpeed Maksymalna wartość prędkości TCP [1-5000mm/s], domyślnie 1000
    * @param [in] maxAOPercent Procent AO odpowiadający maksymalnej prędkości TCP, domyślnie 100%
    * @param [in] zeroZoneCmp Wartość kompensacji strefy nieczułości, procent AO, liczba całkowita, domyślnie 20%, zakres [0-100]
    * @return Kod błędu
    */
    int MoveAOStart(int AONum, int maxTCPSpeed, int maxAOPercent, int zeroZoneCmp);

Zatrzymanie zdjęcia seryjnego AO skrzynki kontrolnej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Zatrzymanie zdjęcia seryjnego AO skrzynki kontrolnej
    * @return Kod błędu
    */
    int MoveAOStop();
    
Rozpoczęcie zdjęcia seryjnego AO końcówki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Rozpoczęcie zdjęcia seryjnego AO końcówki
    * @param [in] AONum Numer AO końcówki
    * @param [in] maxTCPSpeed Maksymalna wartość prędkości TCP [1-5000mm/s], domyślnie 1000
    * @param [in] maxAOPercent Procent AO odpowiadający maksymalnej prędkości TCP, domyślnie 100%
    * @param [in] zeroZoneCmp Wartość kompensacji strefy nieczułości, procent AO, liczba całkowita, domyślnie 20%, zakres [0-100]
    * @return Kod błędu
    */
    int MoveToolAOStart(int AONum, int maxTCPSpeed, int maxAOPercent, int zeroZoneCmp);
    
Zatrzymanie zdjęcia seryjnego AO końcówki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Zatrzymanie zdjęcia seryjnego AO końcówki
    * @return Kod błędu
    */
    int MoveToolAOStop();

Przykład kodu zdjęcia seryjnego AO
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestMoveAO(Robot robot)
    {
        JointPos j1=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j2=new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);

        DescPose desc_pos1=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_pos2=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);

        DescPose offset_pos=new DescPose(0, 0, 0, 0, 0, 0);
        DescPose offset_pos1=new DescPose(0, 0, 50, 0, 0, 0);
        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);

        int tool = 0;
        int user = 0;
        double vel = 20.0;
        double acc = 20.0;
        double ovl = 100.0;
        double blendT = -1.0;
        int flag = 0;

        robot.SetSpeed(20);

        robot.MoveAOStart(0, 100, 100, 20);
        robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveJ(j2, desc_pos2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveAOStop();

        robot.Sleep(1000);

        robot.MoveToolAOStart(0, 100, 100, 20);
        robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveJ(j2, desc_pos2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveToolAOStop();

        return 0;
    }

Rozpoczęcie filtracji FIR ruchu PTP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionchanged:: Java SDK-v1.0.5-3.8.2

.. code-block:: Java
    :linenos:

    /**
    * @brief Rozpoczęcie filtracji FIR ruchu PTP
    * @param [in] maxAcc Maksymalna wartość ekstremalna przyspieszenia (deg/s2)
    * @param [in] maxJek Ekstremalna wartość zrywu dla ujednoliconych przegubów (deg/s3)
    * @return Kod błędu
    */
    int PtpFIRPlanningStart(double maxAcc,double maxJek);

Zakończenie filtracji FIR ruchu PTP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Zakończenie filtracji FIR ruchu PTP
    * @return Kod błędu
    */
    int PtpFIRPlanningEnd();

Rozpoczęcie filtracji FIR ruchu LIN i ARC
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Rozpoczęcie filtracji FIR ruchu LIN i ARC
    * @param [in] maxAccLin Ekstremalna wartość przyspieszenia liniowego (mm/s2)
    * @param [in] maxAccDeg Ekstremalna wartość przyspieszenia kątowego (deg/s2)
    * @param [in] maxJerkLin Ekstremalna wartość zrywu liniowego (mm/s3)
    * @param [in] maxJerkDeg Ekstremalna wartość zrywu kątowego (deg/s3)
    * @return Kod błędu
    */
    int LinArcFIRPlanningStart(double maxAccLin, double maxAccDeg, double maxJerkLin, double maxJerkDeg);

Zakończenie filtracji FIR ruchu LIN i ARC
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Zakończenie filtracji FIR ruchu LIN i ARC
    * @return Kod błędu
    */
    int LinArcFIRPlanningEnd();

Przykład kodu filtracji FIR
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestFIR(Robot robot)
    {
        JointPos startjointPos=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos midjointPos=new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
        JointPos endjointPos=new JointPos(-29.777, -84.536, 109.275, -114.075, -86.655, 74.257);

        DescPose startdescPose=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose middescPose=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose enddescPose=new DescPose(-487.434, 154.362, 308.576, 176.600, 0.268, -14.061);

        ExaxisPos exaxisPos=new ExaxisPos(0, 0, 0, 0);
        DescPose offdese=new DescPose(0, 0, 0, 0, 0, 0);

        int rtn = robot.PtpFIRPlanningStart(1000, 1000);
        robot.MoveJ(startjointPos, startdescPose, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.MoveJ(endjointPos, enddescPose, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.PtpFIRPlanningEnd();

        robot.LinArcFIRPlanningStart(1000, 1000, 1000, 1000);
        robot.MoveL(startjointPos, startdescPose, 0, 0, 100, 100, 100, -1, 0,exaxisPos, 0, 0, offdese, 1, 1);
        robot.MoveC(midjointPos, middescPose, 0, 0, 100, 100, exaxisPos, 0, offdese, endjointPos, enddescPose, 0, 0, 100, 100, exaxisPos, 0, offdese, 100, -1);
        robot.LinArcFIRPlanningEnd();
        return 0;
    }

Włączenie wygładzania przyspieszenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.4-3.8.1
.. code-block:: Java
    :linenos:

    /**
     * @brief Włączenie wygładzania przyspieszenia
     * @param [in] saveFlag Czy zapisać po odłączeniu zasilania
     * @return  Kod błędu
     */
    public int AccSmoothStart(boolean saveFlag)

Wyłączenie wygładzania przyspieszenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.4-3.8.1
.. code-block:: Java
    :linenos:

    /**
     * @brief Wyłączenie wygładzania przyspieszenia
     * @param [in] saveFlag Czy zapisać po odłączeniu zasilania
     * @return  Kod błędu
     */
    public int AccSmoothEnd(boolean saveFlag)

Przykład kodu wygładzania przyspieszenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestAccSmooth(Robot robot)
    {
        JointPos startjointPos=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos endjointPos=new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);

        DescPose startdescPose=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose enddescPose=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);

        ExaxisPos exaxisPos=new ExaxisPos(0, 0, 0, 0);
        DescPose offdese=new DescPose(0,0,0,0,0,0);
        int rtn = robot.AccSmoothStart(false);
        robot.MoveJ(startjointPos, startdescPose, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.MoveJ(endjointPos, enddescPose, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        rtn = robot.AccSmoothEnd(false);

        robot.CloseRPC();
        return 0;
    }

Włączenie określonej prędkości pozy
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
     * @brief Włączenie określonej prędkości pozy
     * @param [in] ratio Procent prędkości pozy [0-300]
     * @return  Kod błędu
     */
    int AngularSpeedStart(int ratio)

Wyłączenie określonej prędkości pozy
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
     * @brief Wyłączenie określonej prędkości pozy
     * @return  Kod błędu
     */
    int AngularSpeedEnd();

Przykład kodu określonej prędkości pozy robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestAngularSpeed(Robot robot)
    {
        JointPos startjointPos=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos endjointPos=new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);

        DescPose startdescPose=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose enddescPose=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);

        ExaxisPos exaxisPos=new ExaxisPos(0, 0, 0, 0);
        DescPose offdese=new DescPose(0, 0, 0, 0, 0, 0);
        int rtn = robot.AngularSpeedStart(50);
        robot.MoveJ(startjointPos, startdescPose, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.MoveJ(endjointPos, enddescPose, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        rtn = robot.AngularSpeedEnd();

        return 0;
    }

Rozpoczęcie ochrony przed osobliwą pozycją
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Rozpoczęcie ochrony przed osobliwą pozycją
    * @param  [in]  protectMode Tryb ochrony przed osobliwością, 0: tryb przegubowy; 1-tryb kartezjański
    * @param  [in]  minShoulderPos Zakres regulacji osobliwości barku (mm), domyślnie 100
    * @param  [in]  minElbowPos Zakres regulacji osobliwości łokcia (mm), domyślnie 50
    * @param  [in]  minWristPos Zakres regulacji osobliwości nadgarstka (°), domyślnie 10
    * @return  Kod błędu
    */
    int SingularAvoidStart(int protectMode, double minShoulderPos, double minElbowPos, double minWristPos);

Zatrzymanie ochrony przed osobliwą pozycją
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Zatrzymanie ochrony przed osobliwą pozycją
    * @return  Kod błędu
    */
    int SingularAvoidEnd();

Przykład kodu ochrony przed osobliwą pozycją robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestAngularSpeed(Robot robot)
    {
        JointPos startjointPos=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos endjointPos=new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);

        DescPose startdescPose=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose enddescPose=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);

        ExaxisPos exaxisPos=new ExaxisPos(0, 0, 0, 0);
        DescPose offdese=new DescPose(0, 0, 0, 0, 0, 0);
        int rtn = robot.AngularSpeedStart(50);
        robot.MoveJ(startjointPos, startdescPose, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.MoveJ(endjointPos, enddescPose, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        rtn = robot.AngularSpeedEnd();

        return 0;
    }

Wyczyszczenie kolejki instrukcji ruchu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Wyczyszczenie kolejki instrukcji ruchu
    * @return Kod błędu
    */
    public int MotionQueueClear()

Przejście do punktu początkowego linii przecięcia rur
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Przejście do punktu początkowego linii przecięcia rur
    * @param [in] mainPoint Pozycje kartezjańskie 6 punktów nauczania rury głównej
    * @param [in] mainExaxisPos Pozycje osi rozszerzenia 6 punktów nauczania rury głównej
    * @param [in] piecePoint Pozycje kartezjańskie 6 punktów nauczania rury pomocniczej
    * @param [in] pieceExaxisPos Pozycje osi rozszerzenia 6 punktów nauczania rury łączącej
    * @param [in] extAxisFlag Czy włączyć oś rozszerzenia; 0-niewłączony; 1-włączony
    * @param [in] exaxisPos Pozycja osi rozszerzenia punktu początkowego
    * @param [in] tool Numer układu narzędzia
    * @param [in] wobj Numer układu przedmiotu
    * @param [in] vel Procent prędkości
    * @param [in] acc Procent przyspieszenia
    * @param [in] ovl Współczynnik skalowania prędkości
    * @param [in] oacc Współczynnik skalowania przyspieszenia
    * @param [in] moveType Typ ruchu; 0-PTP；1-LIN
    * @param [in] moveDirection Kierunek ruchu; 0-zgodnie z ruchem wskazówek zegara；1-przeciwnie do ruchu wskazówek zegara
    * @param [in] offset Wartość przesunięcia
    * @return Kod błędu
    */
    public int MoveToIntersectLineStart(DescPose[] mainPoint, ExaxisPos[] mainExaxisPos, DescPose[] piecePoint, ExaxisPos[] pieceExaxisPos, int extAxisFlag, ExaxisPos exaxisPos, int tool, int wobj, double vel, double acc, double ovl, double oacc, int moveType, int moveDirection, DescPose offset);
            
Ruch po linii przecięcia rur
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Ruch po linii przecięcia rur
    * @param [in] mainPoint Pozycje kartezjańskie 6 punktów nauczania rury głównej
    * @param [in] mainExaxisPos Pozycje osi rozszerzenia 6 punktów nauczania rury głównej
    * @param [in] piecePoint Pozycje kartezjańskie 6 punktów nauczania rury pomocniczej
    * @param [in] pieceExaxisPos Pozycje osi rozszerzenia 6 punktów nauczania rury łączącej
    * @param [in] extAxisFlag Czy włączyć oś rozszerzenia; 0-niewłączony; 1-włączony
    * @param [in] exaxisPos Pozycje osi rozszerzenia punktu początkowego
    * @param [in] tool Numer układu narzędzia
    * @param [in] wobj Numer układu przedmiotu
    * @param [in] vel Procent prędkości
    * @param [in] acc Procent przyspieszenia
    * @param [in] ovl Współczynnik skalowania prędkości
    * @param [in] oacc Współczynnik skalowania przyspieszenia
    * @param [in] moveDirection Kierunek ruchu; 0-zgodnie z ruchem wskazówek zegara；1-przeciwnie do ruchu wskazówek zegara
    * @param [in] offset Wartość przesunięcia
    * @return Kod błędu
    */
    public int MoveIntersectLine(DescPose[] mainPoint, ExaxisPos[] mainExaxisPos, DescPose[] piecePoint, ExaxisPos[] pieceExaxisPos, int extAxisFlag, ExaxisPos[] exaxisPos, int tool, int wobj, double vel, double acc, double ovl, double oacc, int moveDirection, DescPose offset);
                
Przykład kodu ruchu robota po linii przecięcia rur
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static void TestIntersectLineMove(Robot robot)
    {
        DescPose[] mainPoint = new DescPose[6];
        DescPose[] piecePoint = new DescPose[6];
        ExaxisPos[] mainExaxisPos = new ExaxisPos[6];
        ExaxisPos[] pieceExaxisPos = new ExaxisPos[6];
        int extAxisFlag = 1;
        ExaxisPos[] exaxisPos = new ExaxisPos[4];
        DescPose offset =new DescPose(0.0, 2.0 ,30.0, -2.0, 0.0, 0.0 );
        mainPoint[0] = new DescPose(490.004, -383.194, 402.735, -9.332, -1.528, 69.594);
        mainPoint[1] = new DescPose(444.950, -407.117, 389.011, -5.546, -2.196, 65.279);
        mainPoint[2] = new DescPose(445.168, -463.605, 355.759, -1.544, -10.886, 57.104);
        mainPoint[3] = new DescPose(507.529, -485.385, 343.013, -0.786, -4.834, 61.799);
        mainPoint[4] = new DescPose(554.390, -442.647, 367.701, -4.761, -10.181, 64.925);
        mainPoint[5] = new DescPose(532.552, -394.003, 396.467, -13.732, -13.592, 67.411);
        mainExaxisPos[0] = new ExaxisPos(-29.996, 0.000, 0.000, 0.000 );
        mainExaxisPos[1] = new ExaxisPos(-29.996, 0.000, 0.000, 0.000 );
        mainExaxisPos[2] = new ExaxisPos(-29.996, 0.000, 0.000, 0.000 );
        mainExaxisPos[3] = new ExaxisPos(-29.996, 0.000, 0.000, 0.000 );
        mainExaxisPos[4] = new ExaxisPos(-29.996, 0.000, 0.000, 0.000 );
        mainExaxisPos[5] = new ExaxisPos(-29.996, 0.000, 0.000, 0.000 );
        piecePoint[0] = new DescPose( 505.571, -192.408, 316.759, 38.098, 37.051, 139.447);
        piecePoint[1] =new DescPose(533.837, -201.558, 332.340, 34.644, 42.339, 137.748);
        piecePoint[2] =new DescPose(530.386, -225.085, 373.808, 35.431, 45.111, 137.560);
        piecePoint[3] =new DescPose(485.646, -229.195, 383.778, 33.870, 45.173, 137.064);
        piecePoint[4] =new DescPose(460.551, -212.161, 354.256, 28.856, 45.602, 135.930);
        piecePoint[5] =new DescPose(474.217, -197.124, 324.611, 42.469, 41.133, 148.167);
        pieceExaxisPos[0] = new ExaxisPos( -29.996, -0.000, 0.000, 0.000);
        pieceExaxisPos[1] = new ExaxisPos( -29.996, -0.000, 0.000, 0.000);
        pieceExaxisPos[2] = new ExaxisPos( -29.996, -0.000, 0.000, 0.000);
        pieceExaxisPos[3] = new ExaxisPos( -29.996, -0.000, 0.000, 0.000);
        pieceExaxisPos[4] = new ExaxisPos( -29.996, -0.000, 0.000, 0.000);
        pieceExaxisPos[5] = new ExaxisPos( -29.996, -0.000, 0.000, 0.000);
        exaxisPos[0] = new ExaxisPos(-29.996, -0.000, 0.000, 0.000);
        exaxisPos[1] = new ExaxisPos(-44.994, 90.000, 0.000, 0.000);
        exaxisPos[2] = new ExaxisPos(-59.992, 0.002, 0.000, 0.000);
        exaxisPos[3] = new ExaxisPos(-44.994, -89.997, 0.000, 0.000);
        int tool = 2;
        int wobj = 0;
        double vel = 100.0;
        double acc = 100.0;
        double ovl = 12.0;
        double oacc = 12.0;
        int moveType = 1;
        int moveDirection = 1;
        int  rtn = robot.MoveToIntersectLineStart(mainPoint, mainExaxisPos, piecePoint, pieceExaxisPos, extAxisFlag, exaxisPos[0], tool, wobj, vel, acc, ovl, oacc, moveType, moveDirection, offset);
        System.out.printf("MoveToIntersectLineStart rtn is %d\n", rtn);
        rtn = robot.MoveIntersectLine(mainPoint, mainExaxisPos, piecePoint, pieceExaxisPos, extAxisFlag, exaxisPos, tool, wobj, vel, acc, 5.0, 5.0, moveDirection, offset);
        System.out.printf("MoveIntersectLine rtn is %d\n", rtn);
        robot.CloseRPC();
        return ;
    }
                
Ruch w miejscu (pusty ruch)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Ruch w miejscu (pusty ruch)
    * @return Kod błędu
    */
    public int MoveStationary()

Przykład kodu ruchu w miejscu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static void test_RecordandReplay(Robot robot)
    {
        int rtn = robot.LaserSensorRecordandReplay(0, 10, 1, 0, 0.1, 1, 1, 10, 100);
        System.out.printf("LaserSensorRecordandReplay rtn is %d\n", rtn);
        rtn = robot.MoveStationary();
        System.out.printf("MoveStationary rtn is %d\n", rtn);
        rtn = robot.LaserSensorRecord1(0, 10);
        System.out.printf("LaserSensorRecordandReplay rtn is %d\n", rtn);
        robot.CloseRPC();
        robot.Sleep(9999999);
    }

Rozpoczęcie wahadła w punkcie stałym
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Rozpoczęcie wahadła w punkcie stałym
    * @param [in] weaveNum Numer wahadła [0-7]
    * @param [in] mode 0-układ narzędzia; 1-punkt odniesienia
    * @param [in] refPoint Współrzędne kartezjańskie punktu odniesienia [x,y,z,a,b,c]
    * @param [in] weaveTime Czas wahadła [s]
    * @return Kod błędu
    */
    public int OriginPointWeaveStart(int weaveNum, int mode, DescPose refPoint, double weaveTime)
    
Zakończenie wahadła w punkcie stałym
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Zakończenie wahadła w punkcie stałym
    * @return Kod błędu
    */
    public int OriginPointWeaveEnd();
        
Przykład kodu SDK dla wahadła w punkcie stałym
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestOriginPointWeave(Robot robot) {
        JointPos j = new JointPos(39.886, -98.580, -124.032, -47.393, 90.000, 40.842);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);

        DescPose refPoint = new DescPose(400.021, 300.022, 299.996, 179.997, -0.003, -90.956);
        robot.MoveJ(j, 1, 0, 100, 100, 100.0, epos, -1.0, 0, offset_pos);
        
        robot.OriginPointWeaveStart(0, 0, refPoint, 3);
        robot.MoveStationary();
        robot.OriginPointWeaveEnd();

        robot.Sleep(2000);

        robot.MoveJ(j, 1, 0, 100, 100, 100.0, epos, -1.0, 0, offset_pos);
        robot.OriginPointWeaveStart(0, 1, refPoint, 3);
        robot.MoveStationary();
        robot.OriginPointWeaveEnd();

        robot.Sleep(1000);
        return 0;
    }

Przykład kodu SDK dla wahadła w punkcie stałym (z laserem i osią rozszerzenia)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestOriginPointWeave(Robot robot) {
        JointPos j = new JointPos(39.886, -98.580, -124.032, -47.393, 90.000, 40.842);
        ExaxisPos epos1 = new ExaxisPos(0, 0, 0, 0);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos2 = new ExaxisPos(5, 0, 0, 0);
        DescPose refPoint = new DescPose(400.021, 300.022, 299.996, 179.997, -0.003, -90.956);

        int rtn = 0;
        robot.LaserTrackingSensorConfig("192.168.58.20", 5020);
        robot.LaserTrackingSensorSamplePeriod(20);
        robot.LoadPosSensorDriver(101);

        // 加载 UDP 驱动
        robot.ExtDevLoadUDPDriver();

        // 设置外部轴命令完成时间
        rtn = robot.SetExAxisCmdDoneTime(5000.0);
        System.out.println("SetExAxisCmdDoneTime rtn is " + rtn);
        // 使能外部轴 1 和 2
        rtn = robot.ExtAxisServoOn(1, 1);
        System.out.println("ExtAxisServoOn axis id 1 rtn is " + rtn);
        rtn = robot.ExtAxisServoOn(2, 1);
        System.out.println("ExtAxisServoOn axis id 2 rtn is " + rtn);
        robot.Sleep(2000);

        // 设置外部轴回零
        robot.ExtAxisSetHoming(1, 0, 10, 2);
        robot.LaserTrackingLaserOnOff(1,0);


        // 1---不带扩展轴
        robot.LaserTrackingTrackOnOff(1, 4);
        robot.Sleep(200);
        // 启动定点摆动
        robot.OriginPointWeaveStart(0, 0, refPoint, 10);
        robot.MoveStationary();   // 执行固定运动（假设该方法存在）
        robot.OriginPointWeaveEnd();
        robot.LaserTrackingTrackOnOff(0, 4);

        robot.Sleep(2000);         // 等待2秒

        // 2----带扩展轴
        robot.ExtAxisMove(epos1, 100, -1);
        robot.LaserTrackingTrackOnOff(1, 4);
        // 启动定点摆动
        robot.OriginPointWeaveStart(0, 0, refPoint, 20);
        robot.ExtAxisMove(epos2, 100, -1);
        robot.OriginPointWeaveEnd();
        robot.LaserTrackingTrackOnOff(0, 4);

        robot.Sleep(1000);
        return 0;
    }
    
Ruch w trybie serwo prędkościowym w przestrzeni przegubów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Ruch w trybie serwo prędkościowym w przestrzeni przegubów
    * @param   joint_vel  6 docelowych prędkości przegubów, jednostka deg/s
    * @param   exis_vel  4 prędkości zewnętrznych osi, jednostka deg/s
    * @param   acc  Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne, domyślnie 0
    * @param   vel  Procent prędkości, zakres [0~100], tymczasowo niedostępne, domyślnie 0
    * @param   cmdT  Okres wysyłania instrukcji, jednostka s, zalecany zakres [0.001~0.0016]
    * @param   filterT Czas filtrowania, jednostka s, tymczasowo niedostępne, domyślnie 0
    * @param   gain  Wzmocnienie proporcjonalne pozycji docelowej, tymczasowo niedostępne, domyślnie 0
    * @param   id  ID instrukcji servoJ, domyślnie 0
    * @param   comType Typ wysyłania instrukcji; 0-xmlrpc; 1-UDP (odpowiadający portowi 20007 robota)
    * @return  Kod błędu
    */
    public int ServoJV(double[] joint_vel, double[] exis_vel, double acc, double vel, double cmdT, double filterT, double gain, int id, int comType)

Przykład kodu ruchu w trybie serwo prędkościowym w przestrzeni przegubów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int ServoJVtest(Robot robot)
    {
        double[] joint_vel = new double[] { 10, 0, 0, 0, 0, 0 };
        double[] exis_vel = new double[] { 0, 0, 0, 0 };
        double acc = 0.0;
        double vel = 0.0;
        double cmdT = 0.008;
        double filterT = 0.0;
        double gain = 0.0;
        int cnt = 0;
        while (cnt < 200)
        {
            int error = robot.ServoJV(joint_vel, exis_vel, acc, vel, cmdT, filterT, gain);
            System.out.println("MAIN ServoJV rtn is " + error);
    //            robot.Sleep(10);
            cnt++;
        }

        return 0;
    }

Rozpoczęcie sterowania MIT przegubów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Rozpoczęcie sterowania MIT przegubów
    * @param  comType Typ wysyłania instrukcji; 0-xmlrpc; 1-UDP (odpowiadający portowi 20007 robota)
    * @return Kod błędu
    */
    errno_t ServoMITStart(int comType = 0);

Zakończenie sterowania MIT przegubów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Zakończenie sterowania MIT przegubów
    * @param  comType Typ wysyłania instrukcji; 0-xmlrpc; 1-UDP (odpowiadający portowi 20007 robota)
    * @return Kod błędu
    */
    public int ServoMITEnd(int comType);

Sterowanie MIT przegubów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Sterowanie MIT przegubów
    * @param  posGain Wzmocnienie pozycji przegubów j1~j6
    * @param  desPos Oczekiwana pozycja przegubów j1~j6 jednostka:deg
    * @param  velGain Wzmocnienie prędkości przegubów j1~j6
    * @param  desVel Oczekiwana prędkość przegubów j1~j6 jednostka:deg/s
    * @param  torque_ff Moment wyprzedzający j1~j6 jednostka:Nm
    * @param  interval Okres instrukcji, jednostka s, zakres [0.001~0.008]
    * @param  comType Typ wysyłania instrukcji; 0-xmlrpc; 1-UDP (odpowiadający portowi 20007 robota)
    * @return Kod błędu
    */
    public int ServoMIT(double[] posGain, double[] desPos, double[] velGain, double[] desVel, double[] torque_ff, double interval, int comType)

Przykład kodu sterowania MIT przegubów robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int ServoMITtest(Robot robot)
    {
            robot.udpCmdClient.SetUDPCmdRpyCallback((srcType, count, cmdID, dataLen, content) -> {
            System.out.println("\n[Received UDP reply from robot]");
            System.out.println("srcType: " + srcType);
            System.out.println("count: " + count);
            System.out.println("cmdID: " + cmdID);
            System.out.println("dataLen: " + dataLen);
            System.out.println("content: " + content);
            return 0;
        });
        while (true)
        {
            robot.ResetAllError();
            robot.Sleep(500);

            double[] posGain = new double[] { 0, 0, 0, 0, 0, 0 };
            double[] desPos = new double[] { 0, 0, 0, 0, 0, 0 };
            double[] velGain = new double[] { 0, 0, 0, 0, 0, 0 };
            double[] desVel = new double[] { 0, 0, 0, 0, 0, 0 };

            List<Number> joint_toq=new ArrayList<>();
            joint_toq=robot.GetJointTorques(1);
            double[] torques=new double[]{(double)joint_toq.get(1),(double)joint_toq.get(2),(double)joint_toq.get(3),(double)joint_toq.get(4),(double)joint_toq.get(5),(double)joint_toq.get(6)};
            System.out.println("111111");

            robot.ServoMITStart(0);
            System.out.println("ServoMITStart");

            ROBOT_STATE_PKG pkg = robot.GetRobotRealTimeState();
            robot.DragTeachSwitch(1);
            System.out.println("DragTeachSwitch");

            double intev = 0.008;
            int error = 0;

            while (true)
            {
                torques[5] = 0.03;
                System.out.println("ServoMIT call");
                error = robot.ServoMIT(posGain, desPos, velGain, desVel, torques, intev, 0);

                System.out.println("ServoMIT111111 rtn is " + error);
                robot.Sleep(1);

                pkg = robot.GetRobotRealTimeState();
                System.out.println("pkg.jt_cur_pos[5]:" + pkg.jt_cur_pos[5]);
                if (pkg.jt_cur_pos[5] > 30)
                {
                    break;
                }
            }

            while (true)
            {
                torques[5] = -0.03;
                error = robot.ServoMIT(posGain, desPos, velGain, desVel, torques, intev, 0);

                System.out.println("ServoJT222222 rtn is " + error);
                robot.Sleep(1);

                pkg = robot.GetRobotRealTimeState();
                System.out.println("pkg.jt_cur_pos[5]:" + pkg.jt_cur_pos[5]);
                if (pkg.jt_cur_pos[5] < 0)
                {
                    break;
                }
            }

            robot.DragTeachSwitch(0);
            error = robot.ServoMITEnd(0);
        }
        // return 0;
    }