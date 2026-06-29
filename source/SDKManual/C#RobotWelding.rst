Spawanie robotem
================

.. toctree:: 
    :maxdepth: 5

Ustawienie parametrów krzywej procesu spawania
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ustawia parametry krzywej procesu spawania
    * @param  [in] id Numer procesu spawania (1-99)
    * @param  [in] startCurrent Prąd zajarzenia łuku (A)
    * @param  [in] startVoltage Napięcie zajarzenia łuku (V)
    * @param  [in] startTime Czas zajarzenia łuku (ms)
    * @param  [in] weldCurrent Prąd spawania (A)
    * @param  [in] weldVoltage Napięcie spawania (V)
    * @param  [in] endCurrent Prąd wygaszenia łuku (A)
    * @param  [in] endVoltage Napięcie wygaszenia łuku (V)
    * @param  [in] endTime Czas wygaszenia łuku (ms)
    * @return  Kod błędu
    */
    int WeldingSetProcessParam(int id, double startCurrent, double startVoltage, double startTime, double weldCurrent, double weldVoltage, double endCurrent, double endVoltage, double endTime);

Pobranie parametrów krzywej procesu spawania
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera parametry krzywej procesu spawania
    * @param  [in] id Numer procesu spawania (1-99)
    * @param  [out] startCurrent Prąd zajarzenia łuku (A)
    * @param  [out] startVoltage Napięcie zajarzenia łuku (V)
    * @param  [out] startTime Czas zajarzenia łuku (ms)
    * @param  [out] weldCurrent Prąd spawania (A)
    * @param  [out] weldVoltage Napięcie spawania (V)
    * @param  [out] endCurrent Prąd wygaszenia łuku (A)
    * @param  [out] endVoltage Napięcie wygaszenia łuku (V)
    * @param  [out] endTime Czas wygaszenia łuku (ms)
    * @return  Kod błędu
    */
    int WeldingGetProcessParam(int id, ref double startCurrent, ref double startVoltage, ref double startTime, ref double weldCurrent, ref double weldVoltage, ref double endCurrent, ref double endVoltage, ref double endTime);

Ustawienie zależności między prądem spawania a wyjściem analogowym
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia zależność między prądem spawania a wyjściem analogowym
    * @param [in] currentMin Wartość prądu w lewym punkcie zależności liniowej prąd spawania - wyjście analogowe (A)
    * @param [in] currentMax Wartość prądu w prawym punkcie zależności liniowej prąd spawania - wyjście analogowe (A)
    * @param [in] outputVoltageMin Wartość napięcia wyjściowego analogowego w lewym punkcie zależności liniowej prąd spawania - wyjście analogowe (V)
    * @param [in] outputVoltageMax Wartość napięcia wyjściowego analogowego w prawym punkcie zależności liniowej prąd spawania - wyjście analogowe (V)
    * @return Kod błędu
    */
    int WeldingSetCurrentRelation(double currentMin, double currentMax, double outputVoltageMin, double outputVoltageMax);

Ustawienie zależności między napięciem spawania a wyjściem analogowym
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia zależność między napięciem spawania a wyjściem analogowym
    * @param [in] weldVoltageMin Wartość napięcia spawania w lewym punkcie zależności liniowej napięcie spawania - wyjście analogowe (A)
    * @param [in] weldVoltageMax Wartość napięcia spawania w prawym punkcie zależności liniowej napięcie spawania - wyjście analogowe (A)
    * @param [in] outputVoltageMin Wartość napięcia wyjściowego analogowego w lewym punkcie zależności liniowej napięcie spawania - wyjście analogowe (V)
    * @param [in] outputVoltageMax Wartość napięcia wyjściowego analogowego w prawym punkcie zależności liniowej napięcie spawania - wyjście analogowe (V)
    * @return Kod błędu
    */
    int WeldingSetVoltageRelation(double weldVoltageMin, double weldVoltageMax, double outputVoltageMin, double outputVoltageMax);

Pobranie zależności między prądem spawania a wyjściem analogowym
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Pobiera zależność między prądem spawania a wyjściem analogowym
    * @param [out] currentMin Wartość prądu w lewym punkcie zależności liniowej prąd spawania - wyjście analogowe (A)
    * @param [out] currentMax Wartość prądu w prawym punkcie zależności liniowej prąd spawania - wyjście analogowe (A)
    * @param [out] outputVoltageMin Wartość napięcia wyjściowego analogowego w lewym punkcie zależności liniowej prąd spawania - wyjście analogowe (V)
    * @param [out] outputVoltageMax Wartość napięcia wyjściowego analogowego w prawym punkcie zależności liniowej prąd spawania - wyjście analogowe (V)
    * @return Kod błędu
    */
    int WeldingGetCurrentRelation(ref double currentMin, ref double currentMax, ref double outputVoltageMin, ref double outputVoltageMax);

Pobranie zależności między napięciem spawania a wyjściem analogowym
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Pobiera zależność między napięciem spawania a wyjściem analogowym
    * @param [out] weldVoltageMin Wartość napięcia spawania w lewym punkcie zależności liniowej napięcie spawania - wyjście analogowe (A)
    * @param [out] weldVoltageMax Wartość napięcia spawania w prawym punkcie zależności liniowej napięcie spawania - wyjście analogowe (A)
    * @param [out] outputVoltageMin Wartość napięcia wyjściowego analogowego w lewym punkcie zależności liniowej napięcie spawania - wyjście analogowe (V)
    * @param [out] outputVoltageMax Wartość napięcia wyjściowego analogowego w prawym punkcie zależności liniowej napięcie spawania - wyjście analogowe (V)
    * @return Kod błędu
    */
    int WeldingGetVoltageRelation(ref double weldVoltageMin, ref double weldVoltageMax, ref double outputVoltageMin, ref double outputVoltageMax);

Ustawienie prądu spawania
+++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia prąd spawania
    * @param [in] ioType Typ I/O sterowania 0-I/O skrzynki sterowniczej; 1-rozszerzone I/O
    * @param [in] current Wartość prądu spawania (A)
    * @param [in] AOIndex Port wyjścia analogowego sterowania prądem spawania skrzynki sterowniczej (0-1)
    * @return Kod błędu
    */
    int WeldingSetCurrent(int ioType, double current, int AOIndex);

Ustawienie napięcia spawania
++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia napięcie spawania
    * @param [in] ioType Typ I/O sterowania 0-I/O skrzynki sterowniczej; 1-rozszerzone I/O
    * @param [in] voltage Wartość napięcia spawania (A)
    * @param [in] AOIndex Port wyjścia analogowego sterowania napięciem spawania skrzynki sterowniczej (0-1)
    * @return Kod błędu
    */
    int WeldingSetVoltage(int ioType, double voltage, int AOIndex);

Ustawienie parametrów oscylacji
++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:

    /** 
    * @brief Ustawia parametry oscylacji
    * @param [in] weaveNum Numer konfiguracji parametrów spawania z oscylacją
    * @param [in] weaveType Typ oscylacji 0-płaszczyznowa oscylacja trójkątna; 1-pionowa oscylacja L-trójkątna; 2-okrężna zgodnie z ruchem wskazówek zegara; 3-okrężna przeciwnie do ruchu wskazówek zegara; 4-płaszczyznowa oscylacja sinusoidalna; 5-pionowa oscylacja L-sinusoidalna; 6-pionowa oscylacja trójkątna; 7-pionowa oscylacja sinusoidalna
    * @param [in] weaveFrequency Częstotliwość oscylacji (Hz)
    * @param [in] weaveIncStayTime Tryb oczekiwania 0-cykl nie zawiera czasu oczekiwania; 1-cykl zawiera czas oczekiwania
    * @param [in] weaveRange Amplituda oscylacji (mm)
    * @param [in] weaveLeftRange Długość lewego ramienia w pionowej oscylacji trójkątnej (mm)
    * @param [in] weaveRightRange Długość prawego ramienia w pionowej oscylacji trójkątnej (mm)
    * @param [in] additionalStayTime Czas zatrzymania w punkcie wierzchołkowym pionowej oscylacji trójkątnej (mm)
    * @param [in] weaveLeftStayTime Czas zatrzymania po lewej stronie oscylacji (ms)
    * @param [in] weaveRightStayTime Czas zatrzymania po prawej stronie oscylacji (ms)
    * @param [in] weaveCircleRadio Współczynnik cofania dla oscylacji okrężnej (0-100%)
    * @param [in] weaveStationary Oczekiwanie w pozycji oscylacji, 0-pozycja kontynuuje ruch w czasie oczekiwania; 1-pozycja jest nieruchoma w czasie oczekiwania
    * @param [in] weaveYawAngle Azymut kierunku oscylacji (obrót wokół osi Z oscylacji), jednostka °
    * @return Kod błędu 
    */
    int WeaveSetPara(int weaveNum, int weaveType, double weaveFrequency, int weaveIncStayTime, double weaveRange, double weaveLeftRange, double weaveRightRange, int additionalStayTime, int weaveLeftStayTime, int weaveRightStayTime, int weaveCircleRadio, int weaveStationary, double weaveYawAngle, double weaveRotAngle=0);

Przykład kodu ustawiania parametrów spawania
++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:

    private void button7_Click(object sender, EventArgs e)
    {
        robot.WeldingSetProcessParam(1, 177, 27, 1000, 178, 28, 176, 26, 1000);
        robot.WeldingSetProcessParam(2, 188, 28, 555, 199, 29, 133, 23, 333);

        double startCurrent = 0;
        double startVoltage = 0;
        double startTime = 0;
        double weldCurrent = 0;
        double weldVoltage = 0;
        double endCurrent = 0;
        double endVoltage = 0;
        double endTime = 0;

        robot.WeldingGetProcessParam(1, ref startCurrent, ref startVoltage, ref startTime, ref weldCurrent, ref weldVoltage, ref endCurrent, ref endVoltage, ref endTime);
        Console.WriteLine("the Num 1 process param is " + startCurrent + " " + startVoltage + " " + startTime + " " + weldCurrent + " " + weldVoltage + " " + endCurrent + " " + endVoltage + " " + endTime);
        robot.WeldingGetProcessParam(2, ref startCurrent, ref startVoltage, ref startTime, ref weldCurrent, ref weldVoltage, ref endCurrent, ref endVoltage, ref endTime);
        Console.WriteLine("the Num 2 process param is " + startCurrent + " " + startVoltage + " " + startTime + " " + weldCurrent + " " + weldVoltage + " " + endCurrent + " " + endVoltage + " " + endTime);

        int rtn = robot.WeldingSetCurrentRelation(0, 400, 0, 10, 0);
        Console.WriteLine("WeldingSetCurrentRelation rtn is: " + rtn);

        rtn = robot.WeldingSetVoltageRelation(0, 40, 0, 10, 1);
        Console.WriteLine("WeldingSetVoltageRelation rtn is: " + rtn);

        double current_min = 0;
        double current_max = 0;
        double vol_min = 0;
        double vol_max = 0;
        double output_vmin = 0;
        double output_vmax = 0;
        int curIndex = 0;
        int volIndex = 0;
        rtn = robot.WeldingGetCurrentRelation(ref current_min, ref current_max, ref output_vmin, ref output_vmax, ref curIndex);
        Console.WriteLine("WeldingGetCurrentRelation rtn is: " + rtn);
        Console.WriteLine("current min " + current_min + " current max " + current_max + " output vol min " + output_vmin + " output vol max " + output_vmax);

        rtn = robot.WeldingGetVoltageRelation(ref vol_min, ref vol_max, ref output_vmin, ref output_vmax, ref volIndex);
        Console.WriteLine("WeldingGetVoltageRelation rtn is: " + rtn);
        Console.WriteLine("vol min " + vol_min + " vol max " + vol_max + " output vol min " + output_vmin + " output vol max " + output_vmax);

        rtn = robot.WeldingSetCurrent(1, 100, 0, 0);
        Console.WriteLine("WeldingSetCurrent rtn is: " + rtn);

        System.Threading.Thread.Sleep(3000);

        rtn = robot.WeldingSetVoltage(1, 10, 0, 0);
        Console.WriteLine("WeldingSetVoltage rtn is: " + rtn);

        rtn = robot.WeaveSetPara(0, 0, 2.000000, 0, 10.000000, 0.000000, 0.000000, 0, 0, 0, 0, 0, 60.000000);
        Console.WriteLine("rtn is: " + rtn);

        robot.WeaveOnlineSetPara(0, 0, 1, 0, 20, 0, 0, 0, 0);

        rtn = robot.WeldingSetCheckArcInterruptionParam(1, 200);
        Console.WriteLine("WeldingSetCheckArcInterruptionParam    " + rtn);
        rtn = robot.WeldingSetReWeldAfterBreakOffParam(1, 5.7, 98.2, 0);
        Console.WriteLine("WeldingSetReWeldAfterBreakOffParam    " + rtn);
        int enable = 0;
        double length = 0;
        double velocity = 0;
        int moveType = 0;
        int checkEnable = 0;
        int arcInterruptTimeLength = 0;
        rtn = robot.WeldingGetCheckArcInterruptionParam(ref checkEnable, ref arcInterruptTimeLength);
        Console.WriteLine("WeldingGetCheckArcInterruptionParam  checkEnable  " + checkEnable + "   arcInterruptTimeLength  " + arcInterruptTimeLength);
        rtn = robot.WeldingGetReWeldAfterBreakOffParam(ref enable, ref length, ref velocity, ref moveType);
        Console.WriteLine("WeldingGetReWeldAfterBreakOffParam  enable = " + enable + ", length = " + length + ", velocity = " + velocity + ", moveType = " + moveType);

        robot.SetWeldMachineCtrlModeExtDoNum(17);
        for (int i = 0; i < 5; i++)
        {
            robot.SetWeldMachineCtrlMode(0);
            Thread.Sleep(1000);
            robot.SetWeldMachineCtrlMode(1);
            Thread.Sleep(1000);
        }

    }

Natychmiastowe ustawienie parametrów oscylacji
++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Natychmiastowe ustawienie parametrów oscylacji
    * @param [in] weaveNum Numer konfiguracji parametrów spawania z oscylacją
    * @param [in] weaveType Typ oscylacji 0-płaszczyznowa oscylacja trójkątna; 1-pionowa oscylacja L-trójkątna; 2-okrężna zgodnie z ruchem wskazówek zegara; 3-okrężna przeciwnie do ruchu wskazówek zegara; 4-płaszczyznowa oscylacja sinusoidalna; 5-pionowa oscylacja L-sinusoidalna; 6-pionowa oscylacja trójkątna; 7-pionowa oscylacja sinusoidalna
    * @param [in] weaveFrequency Częstotliwość oscylacji (Hz)
    * @param [in] weaveIncStayTime Tryb oczekiwania 0-cykl nie zawiera czasu oczekiwania; 1-cykl zawiera czas oczekiwania
    * @param [in] weaveRange Amplituda oscylacji (mm)
    * @param [in] weaveLeftStayTime Czas zatrzymania po lewej stronie oscylacji (ms)
    * @param [in] weaveRightStayTime Czas zatrzymania po prawej stronie oscylacji (ms)
    * @param [in] weaveCircleRadio Współczynnik cofania dla oscylacji okrężnej (0-100%)
    * @param [in] weaveStationary Oczekiwanie w pozycji oscylacji, 0-pozycja kontynuuje ruch w czasie oczekiwania; 1-pozycja jest nieruchoma w czasie oczekiwania
    * @return Kod błędu
    */
    int WeaveOnlineSetPara(int weaveNum, int weaveType, double weaveFrequency, int weaveIncStayTime, double weaveRange, int weaveLeftStayTime, int weaveRightStayTime, int weaveCircleRadio, int weaveStationary);

Ustawienie parametrów wykrywania nieoczekiwanego przerwania łuku spawalniczego robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia parametry wykrywania nieoczekiwanego przerwania łuku spawalniczego robota
    * @param [in] checkEnable Czy włączyć wykrywanie; 0-nie włączaj; 1-włącz
    * @param [in] arcInterruptTimeLength Czas potwierdzenia przerwania łuku (ms)
    * @return Kod błędu
    */
    int WeldingSetCheckArcInterruptionParam(int checkEnable, int arcInterruptTimeLength)

Pobranie parametrów wykrywania nieoczekiwanego przerwania łuku spawalniczego robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Pobiera parametry wykrywania nieoczekiwanego przerwania łuku spawalniczego robota
    * @param [out] checkEnable Czy włączyć wykrywanie; 0-nie włączaj; 1-włącz
    * @param [out] arcInterruptTimeLength Czas potwierdzenia przerwania łuku (ms)
    * @return Kod błędu
    */
    int WeldingGetCheckArcInterruptionParam(ref int checkEnable, ref int arcInterruptTimeLength)

Ustawienie parametrów wznowienia spawania po przerwaniu spawania robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia parametry wznowienia spawania po przerwaniu spawania robota
    * @param[in] enable Czy włączyć wznowienie spawania po przerwaniu
    * @param[in] length Odległość nakładania się spoiny (mm)
    * @param[in] velocity Procent prędkości powrotu robota do punktu ponownego zajarzenia łuku (0-100)
    * @param[in] moveType Sposób ruchu robota do punktu ponownego zajarzenia łuku; 0-LIN; 1-PTP
    * @return Kod błędu
    */
    int WeldingSetReWeldAfterBreakOffParam(int enable, double length, double velocity, int moveType)

Pobranie parametrów wznowienia spawania po przerwaniu spawania robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Pobiera parametry wznowienia spawania po przerwaniu spawania robota
    * @param [out] enable Czy włączyć wznowienie spawania po przerwaniu
    * @param [out] length Odległość nakładania się spoiny (mm)
    * @param [out] velocity Procent prędkości powrotu robota do punktu ponownego zajarzenia łuku (0-100)
    * @param [out] moveType Sposób ruchu robota do punktu ponownego zajarzenia łuku; 0-LIN; 1-PTP
    * @return Kod błędu
    */
    int WeldingGetReWeldAfterBreakOffParam(ref int enable, ref double length, ref double velocity, ref int moveType)

Ustawienie rozszerzonego portu DO trybu sterowania spawarką
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia rozszerzony port DO trybu sterowania spawarką
    * @param DONum Port DO trybu sterowania spawarką (0-127)
    * @return Kod błędu
    */
    int SetWeldMachineCtrlModeExtDoNum(int DONum);

Ustawienie trybu sterowania spawarką
++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia tryb sterowania spawarką
    * @param [in] mode Tryb sterowania spawarką; 0-tryb jednorodny DC; 1-tryb jednorodny pulsacyjny; 2-tryb JOB; 3-tryb sterowania lokalnego; 4-tryb oddzielny; 5-tryb CC/CV; 6-TIG; 7-CMT
    * @param [in] ioType Typ sterowania; 0-I/O skrzynki sterowniczej; 1-protokół komunikacji cyfrowej (UDP); 2-protokół komunikacji cyfrowej (ModbusTCP)
    * @return Kod błędu
    */
    public int SetWeldMachineCtrlMode(int mode,int ioType = 1)

Rozpoczęcie spawania
++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Rozpoczęcie spawania
    * @param [in] ioType Typ I/O 0-I/O kontrolera; 1-rozszerzone I/O
    * @param [in] arcNum Numer pliku konfiguracyjnego spawarki
    * @param [in] timeout Czas przekroczenia limitu zajarzenia łuku
    * @return Kod błędu
    */
    int ARCStart(int ioType, int arcNum, int timeout);

Zakończenie spawania
++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Zakończenie spawania
    * @param [in] ioType Typ I/O 0-I/O kontrolera; 1-rozszerzone I/O
    * @param [in] arcNum Numer pliku konfiguracyjnego spawarki
    * @param [in] timeout Czas przekroczenia limitu wygaszenia łuku
    * @return Kod błędu
    */
    int ARCEnd(int ioType, int arcNum, int timeout);

Rozpoczęcie oscylacji
+++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Rozpoczęcie oscylacji
    * @param [in] weaveNum Numer konfiguracji parametrów spawania z oscylacją
    * @return Kod błędu
    */
    int WeaveStart(int weaveNum);

Zakończenie oscylacji
+++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Zakończenie oscylacji
    * @param [in] weaveNum Numer konfiguracji parametrów spawania z oscylacją
    * @return Kod błędu
    */
    int WeaveEnd(int weaveNum);

Podawanie drutu do przodu
+++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Podawanie drutu do przodu
    * @param [in] ioType Typ I/O 0-I/O kontrolera; 1-rozszerzone I/O
    * @param [in] wireFeed Sterowanie podawaniem drutu 0-zatrzymaj podawanie; 1-podawaj
    * @return Kod błędu
    */
    int SetForwardWireFeed(int ioType, int wireFeed); 	

Podawanie drutu do tyłu
+++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Podawanie drutu do tyłu
    * @param [in] ioType Typ I/O 0-I/O kontrolera; 1-rozszerzone I/O
    * @param [in] wireFeed Sterowanie podawaniem drutu 0-zatrzymaj podawanie; 1-podawaj
    * @return Kod błędu
    */
    int SetReverseWireFeed(int ioType, int wireFeed);

Podawanie gazu
++++++++++++++
.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Podawanie gazu
    * @param [in] ioType Typ I/O 0-I/O kontrolera; 1-rozszerzone I/O
    * @param [in] airControl Sterowanie podawaniem gazu 0-zatrzymaj podawanie; 1-podawaj
    * @return Kod błędu
    */
    int SetAspirated(int ioType, int airControl);

Ustawienie wznowienia spawania po przerwaniu spawania robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawienie wznowienia spawania po przerwaniu spawania robota
    * @return Kod błędu
    */
    int WeldingStartReWeldAfterBreakOff()

Ustawienie wyjścia ze spawania po przerwaniu spawania robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawienie wyjścia ze spawania po przerwaniu spawania robota
    * @return Kod błędu
    */
    int WeldingAbortWeldAfterBreakOff()

Przykład kodu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button7_Click(object sender, EventArgs e)
    {
        robot.WeldingSetCurrent(1, 230, 0, 0);
        robot.WeldingSetVoltage(1, 24, 0, 1);

        DescPose p1Desc = new DescPose(228.879, -503.594, 453.984, -175.580, 8.293, 171.267);
        JointPos p1Joint = new JointPos(102.700, -85.333, 90.518, -102.365, -83.932, 22.134);

        DescPose p2Desc = new DescPose(-333.302, -435.580, 449.866, -174.997, 2.017, 109.815);
        JointPos p2Joint = new JointPos(41.862, -85.333, 90.526, -100.587, -90.014, 22.135);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        robot.MoveJ(p1Joint, p1Desc, 13, 0, 20, 100, 100, exaxisPos, -1, 0, offdese);
        robot.ARCStart(1, 0, 10000);
        robot.WeaveStart(0);
        robot.MoveL (p2Joint, p2Desc, 13, 0, 20, 100, 100, -1, 0, exaxisPos, 0, 0, offdese);
        robot.ARCEnd(1, 0, 10000);
        robot.WeaveEnd(0);
    }

Rozpoczęcie spawania odcinkowego
++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /** 
    * @brief Rozpoczęcie spawania odcinkowego
    * @param [in] startDesePos Pozycja kartezjańska punktu początkowego
    * @param [in] endDesePos Pozycja i orientacja kartezjańska punktu końcowego
    * @param [in] startJPos Pozycja stawów punktu początkowego
    * @param [in] endJPos Pozycja stawów punktu końcowego
    * @param [in] weldLength Długość odcinka spawanego (mm)
    * @param [in] noWeldLength Długość odcinka niespawanego (mm)
    * @param [in] weldIOType Typ I/O spawania (0-I/O skrzynki sterowniczej; 1-rozszerzone I/O)
    * @param [in] arcNum Numer pliku konfiguracyjnego spawarki
    * @param [in] weldTimeout Czas przekroczenia limitu zajarzenia/wygaszenia łuku
    * @param [in] isWeave Czy stosować oscylację
    * @param [in] weaveNum Numer konfiguracji parametrów spawania z oscylacją
    * @param [in] tool Numer narzędzia
    * @param [in] user Numer przedmiotu
    * @param [in] vel Procent prędkości, zakres [0~100]
    * @param [in] acc Procent przyspieszenia, zakres [0~100], tymczasowo nieudostępnione
    * @param [in] ovl Współczynnik skalowania prędkości, zakres [0~100]
    * @param [in] blendR [-1.0]-ruch do pozycji (blokujący), [0~1000.0]-promień wygładzenia (nieblokujący), jednostka mm	 
    * @param [in] epos Pozycja osi rozszerzonej, jednostka mm
    * @param [in] search 0-brak pozycjonowania drutem spawalniczym, 1-pozycjonowanie drutem spawalniczym
    * @param [in] offset_flag 0-brak przesunięcia, 1-przesunięcie w podstawowym układzie współrzędnych / układzie współrzędnych przedmiotu, 2-przesunięcie w układzie współrzędnych narzędzia
    * @param [in] offset_pos Wartość przesunięcia pozycji i orientacji
    * @return Kod błędu 
    */
    int SegmentWeldStart(DescPose startDesePos, DescPose endDesePos, JointPos startJPos, JointPos endJPos, double weldLength, double noWeldLength, int weldIOType, int arcNum, int weldTimeout,bool isWeave, int weaveNum, int tool, int user, float vel, float acc, float ovl, float blendR, ExaxisPos epos, byte search, byte offset_flag, DescPose offset_pos);

Przykład kodu spawania odcinkowego robota
+++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    private void btnWeldStart_Click(object sender, EventArgs e)
    {
        robot.WeldingSetCurrent(1, 230, 0, 0);
        robot.WeldingSetVoltage(1, 24, 0, 1);

        DescPose p1Desc = new DescPose(228.879, -503.594, 453.984, -175.580, 8.293, 171.267);
        JointPos p1Joint = new JointPos(102.700, -85.333, 90.518, -102.365, -83.932, 22.134);

        DescPose p2Desc = new DescPose(-333.302, -435.580, 449.866, -174.997, 2.017, 109.815);
        JointPos p2Joint = new JointPos(41.862, -85.333, 90.526, -100.587, -90.014, 22.135);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        int rtn = robot.SegmentWeldStart( p1Desc,  p2Desc,  p1Joint,  p2Joint, 20, 20, 0, 0, 5000, false, 0, 0, 0, 100, 100, 100, -1,  exaxisPos, 0, 0,  offdese);
        Console.WriteLine("SegmentWeldStart rtn is {0}", rtn);
    }

Rozpoczęcie symulacji oscylacji
++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Rozpoczęcie symulacji oscylacji
    * @param  [in] weaveNum  Numer parametrów oscylacji
    * @return  Kod błędu
    */
    int WeaveStartSim(int weaveNum);

Zakończenie symulacji oscylacji
+++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Zakończenie symulacji oscylacji
    * @param  [in] weaveNum  Numer parametrów oscylacji
    * @return  Kod błędu
    */
    int WeaveEndSim(int weaveNum);

Rozpoczęcie ostrzegania o wykrywaniu trajektorii (bez ruchu)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Rozpoczęcie ostrzegania o wykrywaniu trajektorii (bez ruchu)
    * @param  [in] weaveNum  Numer parametrów oscylacji
    * @return  Kod błędu
    */
    int WeaveInspectStart(int weaveNum);

Zakończenie ostrzegania o wykrywaniu trajektorii (bez ruchu)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Zakończenie ostrzegania o wykrywaniu trajektorii (bez ruchu)
    * @param  [in] weaveNum  Numer parametrów oscylacji
    * @return  Kod błędu
    */
    int WeaveInspectEnd(int weaveNum);

Rozpoczęcie stopniowej zmiany oscylacji
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:

    /**
    * @brief  Rozpoczęcie stopniowej zmiany oscylacji
    * @param [in] weaveChangeFlag 1-zmiana parametrów oscylacji; 2-zmiana parametrów oscylacji + prędkość spawania
    * @param [in] weaveNum Numer oscylacji 
    * @param [in] velStart Prędkość początkowa spawania (cm/min)
    * @param [in] velEnd Prędkość końcowa spawania (cm/min)
    * @return  Kod błędu
    */
    int WeaveChangeStart(int weaveChangeFlag, int weaveNum, double velStart, double velEnd);

Zakończenie stopniowej zmiany oscylacji
++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Zakończenie stopniowej zmiany oscylacji
    * @return  Kod błędu
    */
    int WeaveChangeEnd()

Przykład kodu spawania ze stopniową zmianą oscylacji robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:

    private void btnweld_Click(object sender, EventArgs e)
    {
        DescPose p1Desc = new DescPose(228.879, -503.594, 453.984, -175.580, 8.293, 171.267);
        JointPos p1Joint = new JointPos(102.700, -85.333, 90.518, -102.365, -83.932, 22.134);

        DescPose p2Desc = new DescPose(-333.302, -435.580, 449.866, -174.997, 2.017, 109.815);
        JointPos p2Joint = new JointPos(41.862, -85.333, 90.526, -100.587, -90.014, 22.135);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        robot.MoveJ(p1Joint, p1Desc, 13, 0, 20, 100, 100, exaxisPos, -1, 0, offdese);
        robot.WeaveStartSim(0);
        robot.MoveL(p2Joint, p2Desc, 13, 0, 20, 100, 100, -1, 0, exaxisPos, 0, 0, offdese);
        robot.WeaveEndSim(0);
        robot.MoveJ(p1Joint, p1Desc, 13, 0, 20, 100, 100, exaxisPos, -1, 0, offdese);
        robot.WeaveInspectStart(0);
        robot.MoveL(p2Joint, p2Desc, 13, 0, 20, 100, 100, -1, 0, exaxisPos, 0, 0, offdese);
        robot.WeaveInspectEnd(0);

        robot.WeldingSetVoltage(1, 19, 0, 0);
        robot.WeldingSetCurrent(1, 190, 0, 0);
        robot.MoveL( p1Joint,  p1Desc, 1, 1, 100, 100, 50, -1,  exaxisPos, 0, 0,  offdese);
        robot.ARCStart(1, 0, 10000);
        robot.ArcWeldTraceControl(1, 0, 1, 0.06, 5, 5, 60, 1, 0.06, 5, 5, 80, 0, 0, 4, 1, 10, 0, 0);
        robot.WeaveStart(0);
        robot.WeaveChangeStart(1, 0, 50, 30);
        robot.MoveL( p2Joint,  p2Desc, 1, 1, 100, 100, 1, -1,  exaxisPos, 0, 0,  offdese);
        robot.WeaveChangeEnd();
        robot.WeaveEnd(0);
        robot.ArcWeldTraceControl(0, 0, 1, 0.06, 5, 5, 60, 1, 0.06, 5, 5, 80, 0, 0, 4, 1, 10, 0, 0);
        robot.ARCEnd(1, 0, 10000);
    }

Rozszerzone I/O - konfiguracja sygnału wykrywania gazu spawarki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Rozszerzone I/O - konfiguracja sygnału wykrywania gazu spawarki
    * @param  [in] DONum  Rozszerzony numer DO sygnału wykrywania gazu
    * @return  Kod błędu
    */
    int SetAirControlExtDoNum(int DONum);

Rozszerzone I/O - konfiguracja sygnału zajarzenia łuku spawarki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Rozszerzone I/O - konfiguracja sygnału zajarzenia łuku spawarki
    * @param  [in] DONum  Rozszerzony numer DO sygnału zajarzenia łuku spawarki
    * @return  Kod błędu
    */
    int SetArcStartExtDoNum(int DONum);

Rozszerzone I/O - konfiguracja sygnału podawania drutu do tyłu spawarki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Rozszerzone I/O - konfiguracja sygnału podawania drutu do tyłu spawarki
    * @param  [in] DONum  Rozszerzony numer DO sygnału podawania drutu do tyłu
    * @return  Kod błędu
    */
    int SetWireReverseFeedExtDoNum(int DONum);

Rozszerzone I/O - konfiguracja sygnału podawania drutu do przodu spawarki
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Rozszerzone I/O - konfiguracja sygnału podawania drutu do przodu spawarki
    * @param  [in] DONum  Rozszerzony numer DO sygnału podawania drutu do przodu
    * @return  Kod błędu
    */
    int SetWireForwardFeedExtDoNum(int DONum);

Rozszerzone I/O - konfiguracja sygnału pomyślnego zajarzenia łuku spawarki
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Rozszerzone I/O - konfiguracja sygnału pomyślnego zajarzenia łuku spawarki
    * @param  [in] DINum  Rozszerzony numer DI sygnału pomyślnego zajarzenia łuku
    * @return  Kod błędu
    */
    int SetArcDoneExtDiNum(int DINum);

Rozszerzone I/O - konfiguracja sygnału gotowości spawarki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Rozszerzone I/O - konfiguracja sygnału gotowości spawarki
    * @param  [in] DINum  Rozszerzony numer DI sygnału gotowości spawarki
    * @return  Kod błędu
    */
    int SetWeldReadyExtDiNum(int DINum);

Rozszerzone I/O - konfiguracja sygnału wznowienia spawania po przerwaniu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Rozszerzone I/O - konfiguracja sygnału wznowienia spawania po przerwaniu
    * @param  [in] reWeldDINum  Rozszerzony numer DI sygnału wznowienia spawania po przerwaniu
    * @param  [in] abortWeldDINum  Rozszerzony numer DI sygnału wyjścia ze spawania po przerwaniu
    * @return  Kod błędu
    */
    int SetExtDIWeldBreakOffRecover(int reWeldDINum, int abortWeldDINum);

Przykład kodu ustawiania rozszerzonych sygnałów I/O spawania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button51_Click(object sender, EventArgs e)
    {
        robot.SetArcStartExtDoNum(10);
        robot.SetAirControlExtDoNum(20);
        robot.SetWireForwardFeedExtDoNum(30);
        robot.SetWireReverseFeedExtDoNum(40);

        robot.SetWeldReadyExtDiNum(50);
        robot.SetArcDoneExtDiNum(60);
        robot.SetExtDIWeldBreakOffRecover(70, 80);
        robot.SetWireSearchExtDIONum(0, 1);
    }

Sterowanie śledzeniem łuku
+++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Sterowanie śledzeniem łuku
    * @param  [in] flag Przełącznik, 0-wył.; 1-wł.
    * @param  [in] dalayTime Czas opóźnienia, jednostka ms
    * @param  [in] isLeftRight Kompensacja odchylenia lewo-prawo
    * @param  [in] klr Współczynnik regulacji lewo-prawo (czułość)
    * @param  [in] tStartLr Czas rozpoczęcia kompensacji lewo-prawo cyc
    * @param  [in] stepMaxLr Maksymalna wielkość kompensacji na raz lewo-prawo mm
    * @param  [in] sumMaxLr Maksymalna całkowita wielkość kompensacji lewo-prawo mm
    * @param  [in] isUpLow Kompensacja odchylenia góra-dół
    * @param  [in] kud Współczynnik regulacji góra-dół (czułość)
    * @param  [in] tStartUd Czas rozpoczęcia kompensacji góra-dół cyc
    * @param  [in] stepMaxUd Maksymalna wielkość kompensacji na raz góra-dół mm
    * @param  [in] sumMaxUd Maksymalna całkowita wielkość kompensacji góra-dół
    * @param  [in] axisSelect Wybór układu współrzędnych góra-dół, 0-oscylacja; 1-narzędzie; 2-podstawa
    * @param  [in] referenceType Sposób ustawiania prądu odniesienia góra-dół, 0-sprzężenie zwrotne; 1-stała
    * @param  [in] referSampleStartUd Rozpoczęcie próbkowania prądu odniesienia góra-dół (sprzężenie zwrotne), cyc
    * @param  [in] referSampleCountUd Liczba cykli próbkowania prądu odniesienia góra-dół (sprzężenie zwrotne), cyc
    * @param  [in] referenceCurrent Prąd odniesienia góra-dół mA
    *  @param  [in] offsetType Typ śledzenia z przesunięciem, 0-bez przesunięcia; 1-próbkowanie; 2-procent /version 3.7.9
    * @param  [in] offsetParameter Parametr przesunięcia; próbkowanie (czas rozpoczęcia próbkowania przesunięcia, domyślnie jeden cykl); procent (procent przesunięcia (-100 ~ 100)) /version 3.7.9
    * @return  Kod błędu
    */
    int ArcWeldTraceControl(int flag, double delaytime, int isLeftRight, double klr, double tStartLr, double stepMaxLr, double sumMaxLr, int isUpLow, double kud, double tStartUd, double stepMaxUd, double sumMaxUd, int axisSelect, int referenceType, double referSampleStartUd, double referSampleCountUd, double referenceCurrent, int offsetType, int offsetParameter);

Wybór pasma AI śledzenia łuku
+++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Wybór pasma AI śledzenia łuku
    * @param  [in] channel Wybór pasma AI śledzenia łuku, [0-3]
    * @return  Kod błędu
    */
    int ArcWeldTraceExtAIChannelConfig(int channel);

Rozpoczęcie kompensacji śledzenia łuku + wielowarstwowe i wielościeżkowe
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Rozpoczęcie kompensacji śledzenia łuku + wielowarstwowe i wielościeżkowe
    * @return Kod błędu
    */
    int ArcWeldTraceReplayStart();

Zakończenie kompensacji śledzenia łuku + wielowarstwowe i wielościeżkowe
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

        /**
         * @brief Zakończenie kompensacji śledzenia łuku + wielowarstwowe i wielościeżkowe
         * @return Kod błędu
         */
    int ArcWeldTraceReplayEnd();

Zmiana współrzędnych przesunięcia - spawanie wielowarstwowe i wielościeżkowe
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

     /**
     * @brief Zmiana współrzędnych przesunięcia - spawanie wielowarstwowe i wielościeżkowe
     * @param [in] pointO Pozycja i orientacja kartezjańska punktu odniesienia
     * @param [in] pointX Pozycja i orientacja kartezjańska punktu w kierunku przesunięcia X punktu odniesienia
     * @param [in] pointZ Pozycja i orientacja kartezjańska punktu w kierunku przesunięcia Z punktu odniesienia
     * @param [in] dx Wielkość przesunięcia w kierunku X (mm)
     * @param [in] dy Wielkość przesunięcia w kierunku Z (mm)
     * @param [in] db Wielkość przesunięcia wokół osi Y (°)
     * @param [out] offset Wynikowe przesunięcie
     * @return Kod błędu
     */
    int MultilayerOffsetTrsfToBase(DescTran pointO, DescTran pointX, DescTran pointZ, double dx, double dy, double db, ref DescPose offset);

Przykład kodu śledzenia łuku dla spawania wielowarstwowego i wielościeżkowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    private void button52_Click(object sender, EventArgs e)
    {
        JointPos mulitilineorigin1_joint = new JointPos(-24.090, -63.501, 84.288, -111.940, -93.426, 57.669);
        DescPose mulitilineorigin1_desc = new DescPose(-677.559, 190.951, -1.205, 1.144, -41.482, -82.577);

        DescTran mulitilineX1_desc = new DescTran();
        mulitilineX1_desc.x = -677.556;
        mulitilineX1_desc.y = 211.949;
        mulitilineX1_desc.z = -1.206;

        DescTran mulitilineZ1_desc = new DescTran();
        mulitilineZ1_desc.x = -677.564;
        mulitilineZ1_desc.y = 190.956;
        mulitilineZ1_desc.z = 19.817;

        JointPos mulitilinesafe_joint = new JointPos(-25.734, -63.778, 81.502, -108.975, -93.392, 56.021);
        DescPose mulitilinesafe_desc = new DescPose(-677.561, 211.950, 19.812, 1.144, -41.482, -82.577);
        JointPos mulitilineorigin2_joint = new JointPos(-29.743, -75.623, 101.241, -116.354, -94.928, 55.735);
        DescPose mulitilineorigin2_desc = new DescPose(-563.961, 215.359, -0.681, 2.845, -40.476, -87.443);

        DescTran mulitilineX2_desc = new DescTran();
        mulitilineX2_desc.x = -563.965;
        mulitilineX2_desc.y = 220.355;
        mulitilineX2_desc.z = -0.680;

        DescTran mulitilineZ2_desc = new DescTran();
        mulitilineZ2_desc.x = -563.968;
        mulitilineZ2_desc.y = 215.362;
        mulitilineZ2_desc.z = 4.331;

        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        DescPose offset = new DescPose(0, 0, 0, 0, 0, 0);

        Thread.Sleep(10);
        int error = robot.MoveJ( mulitilinesafe_joint,  mulitilinesafe_desc, 13, 0, 10, 100, 100,  epos, -1, 0,  offset);
        Console.WriteLine("MoveJ return: {0}", error);

        error = robot.MoveL( mulitilineorigin1_joint,  mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1,  epos, 0, 0,  offset, 0, 100);
        Console.WriteLine("MoveL return: {0}", error);

        error = robot.MoveJ(mulitilinesafe_joint, mulitilinesafe_desc, 13, 0, 10, 100, 100, epos, -1, 0, offset);
        Console.WriteLine("MoveJ return: {0}", error);

        error = robot.MoveL(mulitilineorigin2_joint, mulitilineorigin2_desc, 13, 0, 10, 100, 100, -1,  epos, 0, 0,  offset, 0, 100);
        Console.WriteLine("MoveL return: {0}", error);

        error = robot.MoveJ(mulitilinesafe_joint, mulitilinesafe_desc, 13, 0, 10, 100, 100, epos, -1, 0, offset);
        Console.WriteLine("MoveJ return: {0}", error);

        error = robot.MoveL( mulitilineorigin1_joint,  mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1,  epos, 0, 0,  offset, 0, 100);
        Console.WriteLine("MoveL return: {0}", error);

        error = robot.ARCStart(1, 0, 3000);
        Console.WriteLine("ARCStart return: {0}", error);

        error = robot.WeaveStart(0);
        Console.WriteLine("WeaveStart return: {0}", error);

        error = robot.ArcWeldTraceControl(1, 0, 1, 0.06, 5, 5, 50, 1, 0.06, 5, 5, 55, 0, 0, 4, 1, 10);
        Console.WriteLine("ArcWeldTraceControl return: {0}", error);

        error = robot.MoveL( mulitilineorigin2_joint,  mulitilineorigin2_desc, 13, 0, 1, 100, 100, -1,  epos, 0, 0,  offset, 0, 100);
        Console.WriteLine("MoveL return: {0}", error);

        error = robot.ArcWeldTraceControl(0, 0, 1, 0.06, 5, 5, 50, 1, 0.06, 5, 5, 55, 0, 0, 4, 1, 10);
        Console.WriteLine("ArcWeldTraceControl return: {0}", error);

        error = robot.WeaveEnd(0);
        Console.WriteLine("WeaveEnd return: {0}", error);

        error = robot.ARCEnd(1, 0, 10000);
        Console.WriteLine("ARCEnd return: {0}", error);

        error = robot.MoveJ(mulitilinesafe_joint, mulitilinesafe_desc, 13, 0, 10, 100, 100, epos, -1, 0, offset);
        Console.WriteLine("MoveJ return: {0}", error);

        error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin1_desc.tran, mulitilineX1_desc, mulitilineZ1_desc, 10.0, 0.0, 0.0, ref offset);
        Console.WriteLine("MultilayerOffsetTrsfToBase return: {0}  offect is {1} {2} {3}", error, offset.tran.x, offset.tran.y, offset.tran.z);

        error = robot.MoveL( mulitilineorigin1_joint,  mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1,  epos, 0, 1,  offset, 0, 100);
        Console.WriteLine("MoveL return: {0}", error);

        error = robot.ARCStart(1, 0, 3000);
        Console.WriteLine("ARCStart return: {0}", error);

        error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin2_desc.tran, mulitilineX2_desc, mulitilineZ2_desc, 10, 0, 0, ref offset);
        Console.WriteLine("MultilayerOffsetTrsfToBase return: {0}  offect is {1} {2} {3}", error, offset.tran.x, offset.tran.y, offset.tran.z);

        error = robot.ArcWeldTraceReplayStart();
        Console.WriteLine("ArcWeldTraceReplayStart return: {0}", error);

        error = robot.MoveL( mulitilineorigin2_joint,  mulitilineorigin2_desc, 13, 0, 2, 100, 100, -1,  epos, 0, 1,  offset, 0, 100);
        Console.WriteLine("MoveL return: {0}", error);

        error = robot.ArcWeldTraceReplayEnd();
        Console.WriteLine("ArcWeldTraceReplayEnd return: {0}", error);

        error = robot.ARCEnd(1, 0, 10000);
        Console.WriteLine("ARCEnd return: {0}", error);

        error = robot.MoveJ(mulitilinesafe_joint, mulitilinesafe_desc, 13, 0, 10, 100, 100, epos, -1, 0, offset);
        Console.WriteLine("MoveJ return: {0}", error);

        error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin1_desc.tran, mulitilineX1_desc, mulitilineZ1_desc, 0, 10, 0, ref offset);
        Console.WriteLine("MultilayerOffsetTrsfToBase return: {0}  offect is {1} {2} {3}", error, offset.tran.x, offset.tran.y, offset.tran.z);

        error = robot.MoveL( mulitilineorigin1_joint,  mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1,  epos, 0, 1,  offset, 0, 100);
        Console.WriteLine("MoveL return: {0}", error);

        error = robot.ARCStart(1, 0, 3000);
        Console.WriteLine("ARCStart return: {0}", error);

        error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin2_desc.tran, mulitilineX2_desc, mulitilineZ2_desc, 0, 10, 0, ref offset);
        Console.WriteLine("MultilayerOffsetTrsfToBase return: {0}  offect is {1} {2} {3}", error, offset.tran.x, offset.tran.y, offset.tran.z);

        error = robot.ArcWeldTraceReplayStart();
        Console.WriteLine("MoveJ return: {0}", error);

        error = robot.MoveL(mulitilineorigin2_joint, mulitilineorigin2_desc, 13, 1, 2, 100, 100, -1, epos, 1, 1, offset, 1, 100);
        Console.WriteLine("MoveL return: {0}", error);

        error = robot.ArcWeldTraceReplayEnd();
        Console.WriteLine("ArcWeldTraceReplayEnd return: {0}", error);

        error = robot.ARCEnd(1, 0, 3000);
        Console.WriteLine("ARCEnd return: {0}", error);

        error = robot.MoveJ(mulitilinesafe_joint, mulitilinesafe_desc, 13, 0, 10, 100, 100, epos, -1, 0, offset);
        Console.WriteLine("MoveJ return: {0}", error);
    }

Wybór kanału AI sprzężenia zwrotnego prądu spawarki śledzenia łuku
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:
    
    /**
    * @brief Wybór kanału AI sprzężenia zwrotnego prądu spawarki śledzenia łuku
    * @param [in]  channel Kanał; 0-rozszerzone AI0; 1-rozszerzone AI1; 2-rozszerzone AI2; 3-rozszerzone AI3; 4-AI0 skrzynki sterowniczej; 5-AI1 skrzynki sterowniczej
    * @return Kod błędu
    */
    int ArcWeldTraceAIChannelCurrent(int channel);

Wybór kanału AI sprzężenia zwrotnego napięcia spawarki śledzenia łuku
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Wybór kanału AI sprzężenia zwrotnego napięcia spawarki śledzenia łuku
    * @param [in]  channel Kanał; 0-rozszerzone AI0; 1-rozszerzone AI1; 2-rozszerzone AI2; 3-rozszerzone AI3; 4-AI0 skrzynki sterowniczej; 5-AI1 skrzynki sterowniczej
    * @return Kod błędu
    */
    int ArcWeldTraceAIChannelVoltage(int channel);

Parametry konwersji sprzężenia zwrotnego prądu spawarki śledzenia łuku
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Parametry konwersji sprzężenia zwrotnego prądu spawarki śledzenia łuku
    * @param [in] AILow Dolna granica kanału AI, wartość domyślna 0V, zakres [0-10V]
    * @param [in] AIHigh Górna granica kanału AI, wartość domyślna 10V, zakres [0-10V]
    * @param [in] currentLow Wartość prądu spawarki odpowiadająca dolnej granicy kanału AI, wartość domyślna 0V, zakres [0-200V]
    * @param [in] currentHigh Wartość prądu spawarki odpowiadająca górnej granicy kanału AI, wartość domyślna 100V, zakres [0-200V]
    * @return Kod błędu
    */
    public int ArcWeldTraceCurrentPara(double AILow, double AIHigh, double currentLow, double currentHigh)

Parametry konwersji sprzężenia zwrotnego napięcia spawarki śledzenia łuku
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Parametry konwersji sprzężenia zwrotnego napięcia spawarki śledzenia łuku
    * @param [in] AILow Dolna granica kanału AI, wartość domyślna 0V, zakres [0-10V]
    * @param [in] AIHigh Górna granica kanału AI, wartość domyślna 10V, zakres [0-10V]
    * @param [in] voltageLow Wartość napięcia spawarki odpowiadająca dolnej granicy kanału AI, wartość domyślna 0V, zakres [0-200V]
    * @param [in] voltageHigh Wartość napięcia spawarki odpowiadająca górnej granicy kanału AI, wartość domyślna 100V, zakres [0-200V]
    * @return Kod błędu
    */
    public int ArcWeldTraceVoltagePara(double AILow, double AIHigh, double voltageLow, double voltageHigh)

Przykład kodu śledzenia łuku
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:

    private void button8_Click(object sender, EventArgs e)
    {
        DescPose startdescPose = new DescPose(441.901, 416.508, -51.979, -179.234, 0.718, -115.305);
        JointPos startjointPos = new JointPos(-146.22, -60.551, 104.859, -135.317, -90.289, 59.088);

        DescPose enddescPose = new DescPose(441.901, 615.317, -51.979, -179.234, 0.718, -115.305);
        JointPos endjointPos = new JointPos(-133.22, -44.193, 74.934, -121.661, -90.509, 72.087);

        DescPose safetydescPose = new DescPose(441.901, 416.508, -51.979, -179.234, 0.718, -115.305);
        JointPos safetyjointPos = new JointPos(-146.22, -60.551, 104.859, -135.317, -90.289, 59.088);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);
        robot.MoveJ(safetyjointPos, safetydescPose, 1, 0, 20, 100, 100, exaxisPos, -1, 0, offdese);

        robot.WeldingSetCurrentRelation(0, 495, 1, 10, 0);
        robot.WeldingSetVoltageRelation(10, 45, 1, 10, 1);
        robot.WeldingSetVoltage(0, 25, 1, 0); 
        robot.WeldingSetCurrent(0, 260, 0, 0); 

        int rtn = robot.ArcWeldTraceAIChannelCurrent(4);
        Console.WriteLine("ArcWeldTraceAIChannelCurrent rtn is " + rtn);
        rtn = robot.ArcWeldTraceAIChannelVoltage(5);
        Console.WriteLine("ArcWeldTraceAIChannelVoltage rtn is " + rtn);
        rtn = robot.ArcWeldTraceCurrentPara((double)0, (double)5, (double)0, (double)500);
        Console.WriteLine("ArcWeldTraceCurrentPara rtn is " + rtn);
        rtn = robot.ArcWeldTraceVoltagePara((double)1.018, (double)10, (double)0, (double)50);
        Console.WriteLine("ArcWeldTraceVoltagePara rtn is " + rtn);

        robot.MoveJ(startjointPos, startdescPose, 1, 0, 20, 100, 100, exaxisPos, -1, 0, offdese);
        robot.ArcWeldTraceControl(1, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);
        robot.ARCStart(0, 0, 10000);
        robot.WeaveStart(0);
            robot.MoveL(endjointPos, enddescPose, 1, 0, 100, 100, 2, -1, 0,exaxisPos, 0, 0, offdese);
        robot.ARCEnd(0, 0, 10000);
        robot.WeaveEnd(0);
        robot.ArcWeldTraceControl(0, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);
        robot.MoveJ(safetyjointPos, safetydescPose, 1, 0, 20, 100, 100, exaxisPos, -1, 0, offdese);

    }

Ustawienie rozszerzonych portów I/O pozycjonowania drutu spawalniczego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia rozszerzone porty I/O pozycjonowania drutu spawalniczego
    * @param searchDoneDINum Port DO pomyślnego pozycjonowania drutu spawalniczego (0-127)
    * @param searchStartDONum Port DO sterowania uruchamianiem/zatrzymywaniem pozycjonowania drutu spawalniczego (0-127)
    * @return Kod błędu
    */
    int SetWireSearchExtDIONum(int searchDoneDINum, int searchStartDONum);

Rozpoczęcie pozycjonowania drutu spawalniczego
++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Rozpoczęcie pozycjonowania drutu spawalniczego
    * @param  [in] refPos  1-punkt odniesienia 0-punkt kontaktu
    * @param  [in] searchVel   Prędkość pozycjonowania %
    * @param  [in] searchDis  Odległość pozycjonowania mm
    * @param  [in] autoBackFlag Znacznik automatycznego powrotu, 0-nie automatyczny; 1-automatyczny
    * @param  [in] autoBackVel  Prędkość automatycznego powrotu %
    * @param  [in] autoBackDis  Odległość automatycznego powrotu mm
    * @param  [in] offectFlag  1-pozycjonowanie z przesunięciem; 0-pozycjonowanie punktem nauczania
    * @return  Kod błędu
    */
    int WireSearchStart(int refPos, double searchVel, int searchDis, int autoBackFlag, double autoBackVel, int autoBackDis, int offectFlag);

Zakończenie pozycjonowania drutu spawalniczego
++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Zakończenie pozycjonowania drutu spawalniczego
    * @param  [in] refPos  1-punkt odniesienia 2-punkt kontaktu
    * @param  [in] searchVel   Prędkość pozycjonowania %
    * @param  [in] searchDis  Odległość pozycjonowania mm
    * @param  [in] autoBackFlag Znacznik automatycznego powrotu, 0-nie automatyczny; 1-automatyczny
    * @param  [in] autoBackVel  Prędkość automatycznego powrotu %
    * @param  [in] autoBackDis  Odległość automatycznego powrotu mm
    * @param  [in] offectFlag  1-pozycjonowanie z przesunięciem; 2-pozycjonowanie punktem nauczania
    * @return  Kod błędu
    */
    int WireSearchEnd(int refPos, double searchVel, int searchDis, int autoBackFlag, double autoBackVel, int autoBackDis, int offectFlag);

Obliczenie przesunięcia pozycjonowania drutu spawalniczego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obliczenie przesunięcia pozycjonowania drutu spawalniczego
    * @param  [in] seamType  Typ spoiny
    * @param  [in] method   Metoda obliczeniowa
    * @param  [in] varNameRef Punkty odniesienia 1-6, "#" oznacza brak zmiennej punktowej
    * @param  [in] varNameRes Punkty kontaktu 1-6, "#" oznacza brak zmiennej punktowej
    * @param  [out] offectFlag 0-przesunięcie jest bezpośrednio dodawane do punktu instrukcji; 1-przesunięcie wymaga transformacji współrzędnych punktu instrukcji
    * @param  [out] offect Przesunięcie pozycji i orientacji [x, y, z, a, b, c]
    * @return  Kod błędu
    */
    int GetWireSearchOffset(int seamType, int method, string[] varNameRef, string[] varNameRes, ref int offsetFlag, ref DescPose offset);

Oczekiwanie na zakończenie pozycjonowania drutu spawalniczego
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Oczekiwanie na zakończenie pozycjonowania drutu spawalniczego
    * @return  Kod błędu
    */
    int WireSearchWait(string name);

Zapis punktu kontaktu pozycjonowania drutu spawalniczego do bazy danych
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Zapis punktu kontaktu pozycjonowania drutu spawalniczego do bazy danych
    * @param  [in] varName  Nazwa punktu kontaktu "RES0" ~ "RES99"
    * @param  [in] pos  Dane punktu kontaktu [x, y, x, a, b, c]
    * @return  Kod błędu
    */
    int SetPointToDatabase(string varName, DescPose pos);

Przykład kodu pozycjonowania drutu spawalniczego robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button53_Click(object sender, EventArgs e)
    {
        DescPose toolCoord=new DescPose(0, 0, 200, 0, 0, 0);
        robot.SetToolCoord(1, toolCoord, 0, 0, 1, 0);
        DescPose wobjCoord=new DescPose(0, 0, 0, 0, 0, 0);
        robot.SetWObjCoord(1, wobjCoord, 0);

        int rtn0, rtn1, rtn2 = 0;
        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        DescPose descStart = new DescPose(216.543, 445.175, 93.465, 179.683, 1.757, -112.641);
        JointPos jointStart = new JointPos(-128.345, -86.660, 114.679, -119.625, -89.219, 74.303);

        DescPose descEnd = new DescPose(111.143, 523.384, 87.659, 179.703, 1.835, -97.750);
        JointPos jointEnd = new JointPos(-113.454, -81.060, 109.328, -119.954, -89.218, 74.302);

        robot.MoveL(jointStart, descStart, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese);
        robot.MoveL(jointEnd, descEnd, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese);

        DescPose descREF0A = new DescPose(142.135, 367.604, 86.523, 179.728, 1.922, -111.089);
        JointPos jointREF0A = new JointPos(-126.794, -100.834, 128.922, -119.864, -89.218, 74.302);

        DescPose descREF0B = new DescPose(254.633, 463.125, 72.604, 179.845, 2.341, -114.704);
        JointPos jointREF0B = new JointPos(-130.413, -81.093, 112.044, -123.163, -89.217, 74.303);

        DescPose descREF1A = new DescPose(92.556, 485.259, 47.476, -179.932, 3.130, -97.512);
        JointPos jointREF1A = new JointPos(-113.231, -83.815, 119.877, -129.092, -89.217, 74.303);

        DescPose descREF1B = new DescPose(203.103, 583.836, 63.909, 179.991, 2.854, -103.372);
        JointPos jointREF1B = new JointPos(-119.088, -69.676, 98.692, -121.761, -89.219, 74.303);

        rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
        robot.MoveL(jointREF0A, descREF0A, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese);  //punkt początkowy
        robot.MoveL(jointREF0B, descREF0B, 1, 1, 100, 100, 100, -1, exaxisPos, 1, 0, offdese);  //punkt kierunkowy
        rtn1 = robot.WireSearchWait("REF0");
        rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

        rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
        robot.MoveL(jointREF1A, descREF1A, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese);  //punkt początkowy
        robot.MoveL(jointREF1B, descREF1B, 1, 1, 100, 100, 100, -1, exaxisPos, 1, 0, offdese);  //punkt kierunkowy
        rtn1 = robot.WireSearchWait("REF1");
        rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

        rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
        robot.MoveL(jointREF0A, descREF0A, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese);  //punkt początkowy
        robot.MoveL(jointREF0B, descREF0B, 1, 1, 100, 100, 100, -1, exaxisPos, 1, 0, offdese);  //punkt kierunkowy
        rtn1 = robot.WireSearchWait("RES0");
        rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

        rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
        robot.MoveL(jointREF1A, descREF1A, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese);  //punkt początkowy
        robot.MoveL(jointREF1B, descREF1B, 1, 1, 100, 100, 100, -1, exaxisPos, 1, 0, offdese);  //punkt kierunkowy
        rtn1 = robot.WireSearchWait("RES1");
        rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

        string[] varNameRef = { "REF0", "REF1", "#", "#", "#", "#" };
        string[] varNameRes = { "RES0", "RES1", "#", "#", "#", "#" };
        int offectFlag = 0;
        DescPose offectPos = new DescPose(0, 0, 0, 0, 0, 0);
        rtn0 = robot.GetWireSearchOffset(0, 0, varNameRef, varNameRes, ref offectFlag, ref offectPos);
        robot.PointsOffsetEnable(0, offectPos);
        robot.MoveL(jointStart, descStart, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese);
        robot.MoveL(jointEnd, descEnd, 1, 1, 100, 100, 100, -1, exaxisPos, 1, 0, offdese);
        robot.PointsOffsetDisable();
    }

Ustawienie rozpoczęcia stopniowej zmiany napięcia spawania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawienie rozpoczęcia stopniowej zmiany napięcia spawania
    * @param [in] IOType Typ sterowania; 0-I/O skrzynki sterowniczej; 1-protokół komunikacji cyfrowej (UDP); 2-protokół komunikacji cyfrowej (ModbusTCP)
    * @param [in] voltageStart Początkowe napięcie spawania (V)
    * @param [in] voltageEnd Końcowe napięcie spawania (V)
    * @param [in] AOIndex Numer portu AO skrzynki sterowniczej (0-1)
    * @param [in] blend Czy wygładzać 0-niewygładzone; 1-wygładzone
    * @return Kod błędu
    */
    int WeldingSetVoltageGradualChangeStart(int IOType, double voltageStart, double voltageEnd, int AOIndex, int blend);

Ustawienie zakończenia stopniowej zmiany napięcia spawania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawienie zakończenia stopniowej zmiany napięcia spawania
    * @return Kod błędu
    */
    int WeldingSetVoltageGradualChangeEnd();

Ustawienie rozpoczęcia stopniowej zmiany prądu spawania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawienie rozpoczęcia stopniowej zmiany prądu spawania
    * @param [in] IOType Typ sterowania; 0-I/O skrzynki sterowniczej; 1-protokół komunikacji cyfrowej (UDP); 2-protokół komunikacji cyfrowej (ModbusTCP)
    * @param [in] voltageStart Początkowy prąd spawania (A)
    * @param [in] voltageEnd Końcowy prąd spawania (A)
    * @param [in] AOIndex Numer portu AO skrzynki sterowniczej (0-1)
    * @param [in] blend Czy wygładzać 0-niewygładzone; 1-wygładzone
    * @return Kod błędu
    */
    int WeldingSetCurrentGradualChangeStart(int IOType, double currentStart, double currentEnd, int AOIndex, int blend);

Ustawienie zakończenia stopniowej zmiany prądu spawania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawienie zakończenia stopniowej zmiany prądu spawania
    * @return Kod błędu
    */
    int WeldingSetCurrentGradualChangeEnd();

Przykład kodu stopniowej zmiany prądu i napięcia spawania robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:

    private void btnweld_Click(object sender, EventArgs e)
    {
        DescPose startdescPose = new DescPose(-319.303, -240.689, 116.379, -175.879, -0.337, 148.239);
        JointPos startjointPos = new JointPos(20.474, -103.554, 126.774, -116.682, -87.746, -37.709);

        DescPose enddescPose = new DescPose(-454.166, -327.159, 62.217, 177.199, -2.276, 154.955);
        JointPos endjointPos = new JointPos(27.176, -74.423, 104.557, -119.315, -93.514, -37.698);

        DescPose safedescPose = new DescPose(-375.533, -543.319, 19.798, 177.486, -2.489, 175.825);
        JointPos safejointPos = new JointPos(48.074, -59.714, 89.955, -119.777, -93.508, -37.683);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        robot.WeldingSetCurrentRelation(0, 495, 1, 10, 0);
        robot.WeldingSetVoltageRelation(10, 45, 1, 10, 1);

        robot.WeldingSetVoltage(0, 25, 1, 0);//
        robot.WeldingSetCurrent(0, 260, 0, 0);// 

        robot.MoveJ(safejointPos, safedescPose, 1, 0, 5, 100, 100, exaxisPos, -1, 0, offdese);

        int rtn = robot.WeldingSetCurrentGradualChangeStart(0, 260, 220, 0, 0);
        Console.WriteLine($"WeldingSetCurrentGradualChangeStart rtn is {rtn}");
        rtn = robot.WeldingSetVoltageGradualChangeStart(0, 25, 22, 1, 0);
        Console.WriteLine($"WeldingSetVoltageGradualChangeStart rtn is {rtn}");

        rtn = robot.ArcWeldTraceControl(1, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);
        Console.WriteLine($"ArcWeldTraceControl rtn is {rtn}");

        robot.MoveJ(startjointPos, startdescPose, 1, 0, 5, 100, 100, exaxisPos, -1, 0, offdese);

        robot.ARCStart(0, 0, 10000);
        robot.WeaveStart(0);
        rtn = robot.WeaveChangeStart(2, 1, 24, 36);
        Console.WriteLine($"WeaveChangeStart rtn is {rtn}");
        //robot.MoveL(endjointPos, enddescPose, 1, 0, 100, 100, 2, -1, exaxisPos, 0, 0, offdese);
        robot.ARCEnd(0, 0, 10000);
        robot.WeaveChangeEnd();
        robot.WeaveEnd(0);
        robot.ArcWeldTraceControl(0, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);
        robot.WeldingSetCurrentGradualChangeEnd();
        robot.WeldingSetVoltageGradualChangeEnd();
    }

Ustawienie niestandardowych parametrów oscylacji
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
     * @brief Ustawienie niestandardowych parametrów oscylacji
     * @param [in] id Niestandardowy numer oscylacji: 0-2
     * @param [in] pointNum Liczba punktów oscylacji 0-10
     * @param [in] point Dane punktów ruchu x,y,z
     * @param [in] stayTime Czas zatrzymania oscylacji ms
     * @param [in] frequency Częstotliwość oscylacji Hz
     * @param [in] incStayType Tryb oczekiwania: 0-cykl nie zawiera czasu oczekiwania; 1-cykl zawiera czas oczekiwania
     * @param [in] stationary Oczekiwanie w pozycji oscylacji: 0-kontynuuj ruch w czasie oczekiwania; 1-pozycja nieruchoma w czasie oczekiwania
     * @return  Kod błędu
     */
    public int CustomWeaveSetPara(int id, int pointNum, DescTran[] points, double[] stayTimes, double frequency, int incStayType, int stationary)

Pobranie niestandardowych parametrów oscylacji
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
     * @brief Pobranie niestandardowych parametrów oscylacji
     * @param [in] id Niestandardowy numer oscylacji: 0-2
     * @param [out] pointNum Liczba punktów oscylacji 0-10
     * @param [out] point Dane punktów ruchu x,y,z
     * @param [out] stayTime Czas zatrzymania oscylacji ms
     * @param [out] frequency Częstotliwość oscylacji Hz
     * @param [out] incStayType Tryb oczekiwania: 0-cykl nie zawiera czasu oczekiwania; 1-cykl zawiera czas oczekiwania
     * @param [out] stationary Oczekiwanie w pozycji oscylacji: 0-kontynuuj ruch w czasie oczekiwania; 1-pozycja nieruchoma w czasie oczekiwania
     * @return  Kod błędu
     */
    public int CustomWeaveGetPara(int id, ref int pointNum, ref DescTran[] points, ref double[] stayTimes, ref double frequency, ref int incStayType, ref int stationary)

Przykład kodu niestandardowych parametrów oscylacji
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:

    public void TestCoordMain5()
    {  
        DescTran[] points = new DescTran[10];
        for (int i = 0; i < 10; i++)
        {
            points[i] = new DescTran();
        }
        points[0].x = -3;
        points[0].y = -3;
        points[0].z = 0;
        points[1].x = -6;
        points[1].y = 0;
        points[1].z = 0;
        points[2].x = -3;
        points[2].y = 3;
        points[2].z = 0;
        points[3].x = 0;
        points[3].y = 0;
        points[3].z = 0;
        double[] stayTimes = new double[10] { 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 };
        int rtn = robot.CustomWeaveSetPara(2, 4, points, stayTimes, 1.000, 0, 0);
        Console.WriteLine($"CustomWeaveSetPara rtn is {rtn}");
        System.Threading.Thread.Sleep(1000);
        int pointNum = 0;
        double frequency = 0;
        int incStayType = 0;
        int stationary = 0;
        rtn = robot.CustomWeaveGetPara(2, ref pointNum, ref points, ref stayTimes, ref frequency, ref incStayType, ref stationary);
        Console.WriteLine($"pointNum is {pointNum}");
        for (int i = 0; i < pointNum; i++)
        {
            Console.WriteLine($"point {i}, point x y z {points[i].x:F6} {points[i].y:F6} {points[i].z:F6}");
        }
        Console.WriteLine($"fre is {frequency:F6}, stay is {incStayType} {stationary}");
        robot.WeaveSetPara(0, 9, 1.000000, 1, 5.000000, 6.000000, 5.000000, 50, 100, 100, 0, 1, 0.000000, 0.000000);
        DescPose desc_p1 = new DescPose(-288.650, 367.807, 288.404, 0.000, -0.001, 0.001);
        DescPose desc_p2 = new DescPose(-431.714, 367.815, 288.415, 0.001, 0.001, 0.000);    
        DescPose desc_p3 = new DescPose(-348.666, 427.798, 288.404, -0.000, -0.000, 0.001);
        JointPos j1 = new JointPos(140.656,  -84.560,  -91.707, -93.734,  90.000,50.655 );
        JointPos j2 = new JointPos ( 149.873, -98.298, -77.599,  -94.103,  90.000,  59.873 );
        JointPos j3 = new JointPos (139.773,  -96.173, -80.014,  -93.814,  90.000,  49.772 );
        ExaxisPos epos = new ExaxisPos(0,0,0,0);
        DescPose offset_pos = new DescPose(0,0,0,0,0,0);
        robot.MoveJ(j1, desc_p1, 3, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.WeaveStart(0);
        robot.Circle(j3, desc_p3, 3, 0, 100, 100, epos, j2, desc_p2, 3, 0, 100, 100, epos, 10, -1, offset_pos, 100, -1, 0);
        robot.WeaveEnd(0);
        robot.MoveJ(j1, desc_p1, 3, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.WeaveStart(0);
        robot.MoveC(j3, desc_p3, 3, 0, 100, 100, epos, 0, offset_pos, j2, desc_p2, 3, 0, 100, 100, epos, 0, offset_pos, 10, -1, 0);
        robot.WeaveEnd(0);
        robot.MoveJ(j1, desc_p1, 3, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.WeaveStart(0);
        robot.MoveL(j2, desc_p2, 3, 0, 100, 100, 10, -1, epos, 0, 0, offset_pos, 0, 0, 10);
        robot.WeaveEnd(0);
    }

Konfiguracja parametrów spawarki laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Zapisanie parametrów konfiguracyjnych jednego z 10 grup procesowych spawarki laserowej i skonfigurowanie ich dla spawarki
    * @param[in] io_type Typ komunikacji 0-IO 1-UDP
    * @param[in] num Numer grupy do ustawienia (1~10)
    * @param[in] scanSpeed Prędkość skanowania
    * @param[in] scanWidth Szerokość skanowania
    * @param[in] peakPower Moc szczytowa
    * @param[in] dutyCycle Współczynnik wypełnienia
    * @param[in] freq Częstotliwość
    * @return Kod błędu
    */
    public int SetLaserWeldingParam(int io_type, int num, int scanSpeed, int scanWidth, int peakPower, int dutyCycle, int freq)

Ustawienie rozpoczęcia/zakończenia spawania laserowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawienie włączenia/wyłączenia spawarki laserowej
    * @param[in] io_type Typ komunikacji 0-IO 1-UDP
    * @param[in] status Słowo sterujące 0-wyłącz emisję 1-włącz emisję
    * @param[in] max_waittime Maksymalny czas oczekiwania
    * @return Kod błędu
    */
    public int SetLaserWeldingStartEnd(int io_type, int status, int max_waittime)

Włączenie/wyłączenie spawarki laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Włączenie/wyłączenie spawarki laserowej
    * @param[in] io_type Typ komunikacji 0-IO 1-UDP
    * @param[in] status 0-wyłącz 1-włącz
    * @return Kod błędu
    */
    public int SetLaserWeldingEnable(int io_type, int status)

Resetowanie awarii spawarki laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Resetowanie awarii spawarki laserowej
    * @param[in] io_type Typ komunikacji 0-IO 1-UDP
    * @param[in] status Słowo sterujące 0-nieważne 1-reset awarii
    * @return Kod błędu
    */
    public int ResetLaserWeldingErr(int io_type, int status)

Pobranie stanu pracy spawarki laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Pobranie stanu pracy spawarki laserowej
    * @param[in] io_type Typ komunikacji 0-IO 1-UDP
    * @param[out] status Słowo sterujące 0-zatrzymana 1-pracuje
    * @return Kod błędu
    */
    public int GetLaserWeldingRunningState(int io_type, ref int status)

Pobranie stanu awarii spawarki laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Pobranie stanu awarii spawarki laserowej
    * @param[in] io_type Typ komunikacji 0-IO 1-UDP
    * @param[out] status 0-brak awarii 1-występuje awaria
    * @return Kod błędu
    */
    public int GetLaserWeldingErrState(int io_type, ref int status)

Pobranie parametrów konfiguracyjnych spawarki laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Pobranie parametrów konfiguracyjnych jednej z 10 grup procesowych spawarki laserowej
    * @param[in] num Numer grupy do ustawienia (1~10)
    * @param[out] scanSpeed Prędkość skanowania
    * @param[out] scanWidth Szerokość skanowania
    * @param[out] peakPower Moc szczytowa
    * @param[out] dutyCycle Współczynnik wypełnienia
    * @param[out] freq Częstotliwość
    * @return Kod błędu
    */
    public int GetLaserWeldingParamTarget(int num, ref int scanSpeed, ref int scanWidth, ref int peakPower, ref int dutyCycle, ref int freq)

Pobranie aktualnie obowiązujących parametrów konfiguracyjnych spawarki laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Pobranie aktualnie obowiązujących parametrów konfiguracyjnych spawarki laserowej
    * @param[in] io_type Typ komunikacji 0-IO 1-UDP
    * @param[out] scanSpeed Prędkość skanowania
    * @param[out] scanWidth Szerokość skanowania
    * @param[out] peakPower Moc szczytowa
    * @param[out] dutyCycle Współczynnik wypełnienia
    * @param[out] freq Częstotliwość
    * @return Kod błędu
    */
    public int GetLaserWeldingParamActual(int io_type, ref int scanSpeed, ref int scanWidth, ref int peakPower, ref int dutyCycle, ref int freq)
    
Konfiguracja rozszerzonego portu DO włączania spawarki laserowej
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawienie rozszerzonego I/O dla spawarki laserowej - portu DO włączania
    * @param[in] ctrlModeDONum Numer rozszerzonego portu DO włączania spawarki laserowej
    * @return Kod błędu
    */
    public int SetLaserWeldingEnableExtDoNum(int ctrlModeDONum)

Konfiguracja rozszerzonego portu DO uruchamiania spawarki laserowej
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawienie rozszerzonego I/O dla spawarki laserowej - portu DO uruchamiania
    * @param[in] ctrlModeDONum Numer rozszerzonego portu DO uruchamiania spawarki laserowej (włączanie/wyłączanie emisji)
    * @return Kod błędu
    */
    public int SetLaserWeldingStartExtDoNum(int ctrlModeDONum)

Konfiguracja rozszerzonego portu DO resetowania awarii spawarki laserowej
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawienie rozszerzonego I/O dla spawarki laserowej - portu DO resetowania awarii
    * @param[in] ctrlModeDONum Numer rozszerzonego portu DO resetowania awarii spawarki laserowej
    * @return Kod błędu
    */
    public int SetLaserWeldingErrResetExtDoNum(int ctrlModeDONum)

Konfiguracja rozszerzonego DI stanu pracy spawarki laserowej (stan emisji)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Konfiguracja rozszerzonego DI stanu pracy spawarki laserowej (stan emisji)
    * @param[in] diNum Numer rozszerzonego portu DI stanu pracy spawarki laserowej (stan emisji)
    * @return Kod błędu
    */
    public int SetLaserWeldingRunningStateExtDiNum(int diNum)
    
Konfiguracja rozszerzonego portu DI stanu awarii spawarki laserowej
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Konfiguracja rozszerzonego DI stanu awarii spawarki laserowej
    * @param[in] diNum Numer rozszerzonego portu DI stanu awarii spawarki laserowej
    * @return Kod błędu
    */
    public int SetLaserWeldingErrStateExtDiNum(int diNum)
        
Przykład kodu spawania laserowego
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    private void btnLaserWeld_Click(object sender, EventArgs e)
    {

        int rtn = -1;
        // Załadowanie sterownika UDP
        rtn = robot.ExtDevLoadUDPDriver();
        if (rtn != 0)
        {
            Console.WriteLine("Failed to load UDP driver, error code: " + rtn);
        }
        Thread.Sleep(1000);

        // Ustawienie parametrów spawania laserowego: io_type=1, num=3, scanSpeed=2000, scanWidth=3, peakPower=1500, dutyCycle=100, freq=1000
        rtn = robot.SetLaserWeldingParam(1, 3, 2000, 3, 1500, 100, 1000);
        if (rtn != 0)
        {
            Console.WriteLine("SetLaserWeldingParam failed, error code: " + rtn);
        }
        else
        {
            Console.WriteLine("SetLaserWeldingParam success");
        }

        // Ustawienie numeru portu DO uruchamiania
        rtn = robot.SetLaserWeldingStartExtDoNum(1);
        if (rtn != 0)
        {
            Console.WriteLine("SetLaserWeldingStartExtDoNum failed, error code: " + rtn);
        }

        // Ustawienie trybu 0 (tryb nauczania)
        rtn = robot.Mode(0);
        if (rtn != 0)
        {
            Console.WriteLine("Set mode 0 failed, error code: " + rtn);
        }
        Thread.Sleep(1000);


        DescPose desc_pos1 = new DescPose(-303.721, -206.960, 297.105, 152.209, 19.857, 109.166);
        DescPose desc_pos2 = new DescPose(-301.575, -254.888, 284.786, 155.919, 26.946, 111.629);
        DescPose desc_safe = new DescPose(-344.386, -280.830, 435.073, 173.835, 15.333, 124.931);


        ExaxisPos exaxis = new ExaxisPos(0.0, 0.0, 0.0, 0.0);
        DescPose offset = new DescPose(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);

        // Przejście do pierwszego punktu spawania
        int error = robot.MoveL(desc_pos1, 0, 0, 100, 100, 100, -1, 0, exaxis, 0, 0, offset, -1, 0);
        Console.WriteLine("MoveL to pos1 return: " + error);

        // Włączenie lasera (emisja)
        rtn = robot.SetLaserWeldingStartEnd(1, 1, 10000);
        if (rtn != 0)
        {
            Console.WriteLine("SetLaserWeldingStartEnd (start) failed, error code: " + rtn);
        }
        else
        {
            Console.WriteLine("Laser started");
        }

        // Przejście do drugiego punktu spawania (podczas spawania)
        rtn = robot.MoveL(desc_pos2, 0, 0, 30, 100, 100, -1, 0, exaxis, 0, 0, offset, -1, 0);
        Console.WriteLine("MoveL to pos2 return: " + rtn);

        Thread.Sleep(500);
        // Wyłączenie lasera (zakończenie emisji)
        rtn = robot.SetLaserWeldingStartEnd(1, 0, 10000);
        if (rtn != 0)
        {
            Console.WriteLine("SetLaserWeldingStartEnd (stop) failed, error code: " + rtn);
        }
        else
        {
            Console.WriteLine("Laser stopped");
        }

        // Przejście do punktu bezpiecznego
        rtn = robot.MoveL(desc_safe, 0, 0, 100, 100, 100, -1, 0, exaxis, 0, 0, offset, -1, 0);
        Console.WriteLine("MoveL to safe_pos return: " + rtn);

        // Ustawienie trybu 1 (tryb zdalny)
        rtn = robot.Mode(1);
        if (rtn != 0)
        {
            Console.WriteLine("Set mode 1 failed, error code: " + rtn);
        }
        Thread.Sleep(1000);

        // Zamknięcie połączenia
        robot.CloseRPC();
        Thread.Sleep(1000);

        Console.WriteLine("Test completed");

        return ;
    }

Ustawianie powrotu do punktu zerowego cyklu po zakończeniu splotu
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief  Ustawia, czy po zakończeniu splotu wrócić do punktu zerowego cyklu
    * @param [in] flag Czy wrócić do punktu zerowego cyklu po zakończeniu splotu; 0-nie wracać; 1-wrócić do punktu zerowego cyklu
    * @return  Kod błędu
    */
    public int SetWeavebackCenterConfig(int flag) 
           
Pobieranie parametrów powrotu do punktu zerowego cyklu po zakończeniu splotu
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera parametry powrotu do punktu zerowego cyklu po zakończeniu splotu
    * @param [out] flag Czy wrócić do punktu zerowego cyklu po zakończeniu splotu; 0-nie wracać; 1-wrócić do punktu zerowego cyklu
    * @return  Kod błędu
    */
    public int GetWeavebackCenterConfig(ref int flag)
           
Przykład kodu powrotu do punktu zerowego cyklu po zakończeniu splotu
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    public void TestSplineWeave()
    {
        int rtn;

        // Konfiguracja powrotu splotu do środka
        robot.SetWeavebackCenterConfig(1);
        int weaveBackConfig = 0;
        robot.GetWeavebackCenterConfig(ref weaveBackConfig);
        Console.WriteLine("GetWeavebackCenterConfig: {0}", weaveBackConfig);

        JointPos j1 = new JointPos(9.000, -66.067, 67.706, -103.217, -90.151, 100.669);
        JointPos j2 = new JointPos(-4.660, -107.973, 103.734, -76.214, -89.999, 90.886);
        JointPos j3 = new JointPos(-36.762, -77.380, 91.364, -127.159, -90.024, 54.833);
        JointPos j4 = new JointPos(-62.875, -89.460, 86.437, -77.030, -90.012, 31.539);
        DescPose desc_pos1 = new DescPose(-654.129, -235.344, 246.543, 6.010, -11.535, -176.787);
        DescPose desc_pos2 = new DescPose(-273.710, -100.871, 280.935, 5.692, 9.522, 179.512);
        DescPose desc_pos3 = new DescPose(-566.093, 311.278, 215.008, -10.453, -17.486, -174.209);
        DescPose desc_pos4 = new DescPose(-246.558, 328.240, 292.173, 13.912, 4.437, -179.067);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        int tool = 2;
        int user = 0;
        float vel = 100.0f;
        float acc = 100.0f;
        float ovl = 20.0f;
        float blendT = 0.0f;
        float blendR = 0.0f;
        byte flag = 0;

        robot.SetSpeed(1);

        // Przesunięcie do punktu początkowego j1
        rtn = robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, 100.0f, epos, blendT, flag, offset_pos);
        Console.WriteLine("MoveJ to j1 rtn: {0}", rtn);

        // Splot + ruch krzywej spline
        robot.WeaveStart(0);
        robot.NewSplineStart(0, 6000);
        robot.NewSplinePoint(j1, desc_pos1, tool, user, vel, acc, ovl, -1.0f, 0);
        robot.NewSplinePoint(j2, desc_pos2, tool, user, vel, acc, ovl, -1.0f, 0);
        robot.NewSplinePoint(j3, desc_pos3, tool, user, vel, acc, ovl, -1.0f, 0);
        robot.NewSplinePoint(j4, desc_pos4, tool, user, vel, acc, ovl, -1.0f, 1);
        robot.NewSplineEnd();

        Console.WriteLine("TestSplineWeave completed");
    }    