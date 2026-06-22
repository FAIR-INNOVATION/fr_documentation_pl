Spawanie robotem
================

.. toctree::
    :maxdepth: 5

Ustawianie parametrów krzywej procesu spawania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Ustawia parametry krzywej procesu spawania
     * @param [in] id Numer procesu spawania (1-99)
     * @param [in] startCurrent Prąd rozpoczęcia łuku (A)
     * @param [in] startVoltage Napięcie rozpoczęcia łuku (V)
     * @param [in] startTime Czas rozpoczęcia łuku (ms)
     * @param [in] weldCurrent Prąd spawania (A)
     * @param [in] weldVoltage Napięcie spawania (V)
     * @param [in] endCurrent Prąd zakończenia łuku (A)
     * @param [in] endVoltage Napięcie zakończenia łuku (V)
     * @param [in] endTime Czas zakończenia łuku (ms)
     * @return Kod błędu
     */
    errno_t WeldingSetProcessParam(int id, double startCurrent, double startVoltage, double startTime, double weldCurrent, double weldVoltage, double endCurrent, double endVoltage, double endTime);

Pobieranie parametrów krzywej procesu spawania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Pobiera parametry krzywej procesu spawania
     * @param [in] id Numer procesu spawania (1-99)
     * @param [out] startCurrent Prąd rozpoczęcia łuku (A)
     * @param [out] startVoltage Napięcie rozpoczęcia łuku (V)
     * @param [out] startTime Czas rozpoczęcia łuku (ms)
     * @param [out] weldCurrent Prąd spawania (A)
     * @param [out] weldVoltage Napięcie spawania (V)
     * @param [out] endCurrent Prąd zakończenia łuku (A)
     * @param [out] endVoltage Napięcie zakończenia łuku (V)
     * @param [out] endTime Czas zakończenia łuku (ms)
     * @return Kod błędu
     */
    errno_t WeldingGetProcessParam(int id, double& startCurrent, double& startVoltage, double& startTime, double& weldCurrent, double& weldVoltage, double& endCurrent, double& endVoltage, double& endTime);

Ustawianie zależności prądu spawania od wyjścia analogowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia zależność prądu spawania od wyjścia analogowego
    * @param [in] currentMin Wartość prądu w lewym punkcie zależności liniowej prąd spawania - wyjście analogowe (A)
    * @param [in] currentMax Wartość prądu w prawym punkcie zależności liniowej prąd spawania - wyjście analogowe (A)
    * @param [in] outputVoltageMin Wartość napięcia wyjściowego analogowego w lewym punkcie zależności prąd spawania - wyjście analogowe (V)
    * @param [in] outputVoltageMax Wartość napięcia wyjściowego analogowego w prawym punkcie zależności prąd spawania - wyjście analogowe (V)
    * @return Kod błędu
    */
    errno_t WeldingSetCurrentRelation(double currentMin, double currentMax, double outputVoltageMin, double outputVoltageMax);

Ustawianie zależności napięcia spawania od wyjścia analogowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia zależność napięcia spawania od wyjścia analogowego
    * @param [in] weldVoltageMin Wartość napięcia spawania w lewym punkcie zależności napięcie spawania - wyjście analogowe (A)
    * @param [in] weldVoltageMax Wartość napięcia spawania w prawym punkcie zależności napięcie spawania - wyjście analogowe (A)
    * @param [in] outputVoltageMin Wartość napięcia wyjściowego analogowego w lewym punkcie zależności napięcie spawania - wyjście analogowe (V)
    * @param [in] outputVoltageMax Wartość napięcia wyjściowego analogowego w prawym punkcie zależności napięcie spawania - wyjście analogowe (V)
    * @return Kod błędu
    */
    errno_t WeldingSetVoltageRelation(double weldVoltageMin, double weldVoltageMax, double outputVoltageMin, double outputVoltageMax);

Pobieranie zależności prądu spawania od wyjścia analogowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera zależność prądu spawania od wyjścia analogowego
    * @param [out] currentMin Wartość prądu w lewym punkcie zależności liniowej prąd spawania - wyjście analogowe (A)
    * @param [out] currentMax Wartość prądu w prawym punkcie zależności liniowej prąd spawania - wyjście analogowe (A)
    * @param [out] outputVoltageMin Wartość napięcia wyjściowego analogowego w lewym punkcie zależności prąd spawania - wyjście analogowe (V)
    * @param [out] outputVoltageMax Wartość napięcia wyjściowego analogowego w prawym punkcie zależności prąd spawania - wyjście analogowe (V)
    * @return Kod błędu
    */
    errno_t WeldingGetCurrentRelation(double *currentMin, double *currentMax, double *outputVoltageMin, double *outputVoltageMax);

Pobieranie zależności napięcia spawania od wyjścia analogowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera zależność napięcia spawania od wyjścia analogowego
    * @param [out] weldVoltageMin Wartość napięcia spawania w lewym punkcie zależności napięcie spawania - wyjście analogowe (A)
    * @param [out] weldVoltageMax Wartość napięcia spawania w prawym punkcie zależności napięcie spawania - wyjście analogowe (A)
    * @param [out] outputVoltageMin Wartość napięcia wyjściowego analogowego w lewym punkcie zależności napięcie spawania - wyjście analogowe (V)
    * @param [out] outputVoltageMax Wartość napięcia wyjściowego analogowego w prawym punkcie zależności napięcie spawania - wyjście analogowe (V)
    * @return Kod błędu
    */
    errno_t WeldingGetVoltageRelation(double *weldVoltageMin, double *weldVoltageMax, double *outputVoltageMin, double *outputVoltageMax);

Ustawianie prądu spawania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia prąd spawania
    * @param [in] ioType Typ IO sterowania 0-IO szafy sterowniczej; 1-rozszerzone IO
    * @param [in] current Wartość prądu spawania (A)
    * @param [in] AOIndex Port wyjścia analogowego szafy sterowniczej dla prądu spawania (0-1)
    * @param [in] blend Czy wygładzać 0-niewygładzone; 1-wygładzone
    * @return Kod błędu
    */
    errno_t WeldingSetCurrent(int ioType, double current, int AOIndex, int blend);

Ustawianie napięcia spawania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia napięcie spawania
    * @param [in] ioType Typ IO sterowania 0-IO szafy sterowniczej; 1-rozszerzone IO
    * @param [in] voltage Wartość napięcia spawania (A)
    * @param [in] AOIndex Port wyjścia analogowego szafy sterowniczej dla napięcia spawania (0-1)
    * @param [in] blend Czy wygładzać 0-niewygładzone; 1-wygładzone
    * @return Kod błędu
    */
    errno_t WeldingSetVoltage(int ioType, double voltage, int AOIndex, int blend);

Ustawianie parametrów wahadła
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Ustawia parametry wahadła
     * @param [in] weaveNum Numer konfiguracji parametrów spawania wahadłowego
     * @param [in] weaveType Typ wahadła 0-płaskie wahadło trójkątne; 1-pionowe wahadło trójkątne w kształcie L; 2-okrężne wahadło zgodne z ruchem wskazówek zegara; 3-okrężne wahadło przeciwne do ruchu wskazówek zegara; 4-płaskie wahadło sinusoidalne; 5-pionowe wahadło sinusoidalne w kształcie L; 6-pionowe wahadło trójkątne; 7-pionowe wahadło sinusoidalne
     * @param [in] weaveFrequency Częstotliwość wahadła (Hz)
     * @param [in] weaveIncStayTime Tryb oczekiwania 0-cykl nie zawiera czasu oczekiwania; 1-cykl zawiera czas oczekiwania
     * @param [in] weaveRange Amplituda wahadła (mm)
     * @param [in] weaveLeftRange Długość lewej cięciwy dla pionowego wahadła trójkątnego (mm)
     * @param [in] weaveRightRange Długość prawej cięciwy dla pionowego wahadła trójkątnego (mm)
     * @param [in] additionalStayTime Czas oczekiwania w wierzchołku trójkąta dla pionowego wahadła trójkątnego (mm)
     * @param [in] weaveLeftStayTime Lewy czas postoju wahadła (ms)
     * @param [in] weaveRightStayTime Prawy czas postoju wahadła (ms)
     * @param [in] weaveCircleRadio Okrężne wahadło - współczynnik powrotu (0-100%)
     * @param [in] weaveStationary Oczekiwanie na pozycji wahadła, 0-pozycja kontynuuje ruch w czasie oczekiwania; 1-pozycja nieruchoma w czasie oczekiwania
     * @param [in] weaveYawAngle Azymut kierunku wahadła (obrót wokół osi Z wahadła), jednostka °
     * @param [in] weaveRotAngle Kąt przechyłu bocznego kierunku wahadła (odchylenie wokół osi X wahadła), jednostka °
     * @return Kod błędu
     */
      errno_t WeaveSetPara(int weaveNum, int weaveType, double weaveFrequency, int weaveIncStayTime, double weaveRange, double weaveLeftRange, double weaveRightRange, int additionalStayTime, int weaveLeftStayTime, int weaveRightStayTime, int weaveCircleRadio, int weaveStationary, double weaveYawAngle, double weaveRotAngle = 0);

Przykład kodu ustawiania parametrów spawania
++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestSetWeldParam(void)
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
      robot.WeldingGetProcessParam(1, startCurrent, startVoltage, startTime, weldCurrent, weldVoltage, endCurrent, endVoltage, endTime);
      cout << "the Num 1 process param is " << startCurrent << " " << startVoltage << " " << startTime << " " << weldCurrent << " " << weldVoltage << " " << endCurrent << " " << endVoltage << " " << endTime << endl;
      robot.WeldingGetProcessParam(2, startCurrent, startVoltage, startTime, weldCurrent, weldVoltage, endCurrent, endVoltage, endTime);
      cout << "the Num 2 process param is " << startCurrent << " " << startVoltage << " " << startTime << " " << weldCurrent << " " << weldVoltage << " " << endCurrent << " " << endVoltage << " " << endTime << endl;
      rtn = robot.WeldingSetCurrentRelation(0, 400, 0, 10, 0);
      cout << "WeldingSetCurrentRelation rtn is: " << rtn << endl;
      rtn = robot.WeldingSetVoltageRelation(0, 40, 0, 10, 1);
      cout << "WeldingSetVoltageRelation rtn is: " << rtn << endl;
      double current_min = 0;
      double current_max = 0;
      double vol_min = 0;
      double vol_max = 0;
      double output_vmin = 0;
      double output_vmax = 0;
      int curIndex = 0;
      int volIndex = 0;
      rtn = robot.WeldingGetCurrentRelation(&current_min, &current_max, &output_vmin, &output_vmax, &curIndex);
      cout << "WeldingGetCurrentRelation rtn is: " << rtn << endl;
      cout << "current min " << current_min << " current max " << current_max << " output vol min " << output_vmin << " output vol max " << output_vmax << endl;
      rtn = robot.WeldingGetVoltageRelation(&vol_min, &vol_max, &output_vmin, &output_vmax, &volIndex);
      cout << "WeldingGetVoltageRelation rtn is: " << rtn << endl;
      cout << "vol min " << vol_min << " vol max " << vol_max << " output vol min " << output_vmin << " output vol max " << output_vmax << endl;
      rtn = robot.WeldingSetCurrent(1, 100, 0, 0);
      cout << "WeldingSetCurrent rtn is: " << rtn << endl;
      this_thread::sleep_for(chrono::seconds(3));
      rtn = robot.WeldingSetVoltage(1, 10, 0, 0);
      cout << "WeldingSetVoltage rtn is: " << rtn << endl;
      rtn = robot.WeaveSetPara(0, 0, 2.000000, 0, 10.000000, 0.000000, 0.000000, 0, 0, 0, 0, 0, 60.000000);
      cout << "rtn is: " << rtn << endl;
      robot.WeaveOnlineSetPara(0, 0, 1, 0, 20, 0, 0, 0, 0);
      rtn = robot.WeldingSetCheckArcInterruptionParam(1, 200);
      printf("WeldingSetCheckArcInterruptionParam  %d\n", rtn);
      rtn = robot.WeldingSetReWeldAfterBreakOffParam(1, 5.7, 98.2, 0);
      printf("WeldingSetReWeldAfterBreakOffParam  %d\n", rtn);
      int enable = 0;
      double length = 0;
      double velocity = 0;
      int moveType = 0;
      int checkEnable = 0;
      int arcInterruptTimeLength = 0;
      rtn = robot.WeldingGetCheckArcInterruptionParam(&checkEnable, &arcInterruptTimeLength);
      printf("WeldingGetCheckArcInterruptionParam checkEnable %d  arcInterruptTimeLength %d\n", checkEnable, arcInterruptTimeLength);
      rtn = robot.WeldingGetReWeldAfterBreakOffParam(&enable, &length, &velocity, &moveType);
      printf("WeldingGetReWeldAfterBreakOffParam enable = %d, length = %lf, velocity = %lf, moveType = %d\n", enable, length, velocity, moveType);
      robot.SetWeldMachineCtrlModeExtDoNum(17);
      for (int i = 0; i < 5; i++)
      {
        robot.SetWeldMachineCtrlMode(0);
        robot.Sleep(1000);
        robot.SetWeldMachineCtrlMode(1);
        robot.Sleep(1000);
      }
      robot.CloseRPC();
      return 0;
    }

Natychmiastowe ustawianie parametrów wahadła
++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Natychmiastowe ustawianie parametrów wahadła
    * @param [in] weaveNum Numer konfiguracji parametrów spawania wahadłowego
    * @param [in] weaveType Typ wahadła 0-płaskie wahadło trójkątne; 1-pionowe wahadło trójkątne w kształcie L; 2-okrężne wahadło zgodne z ruchem wskazówek zegara; 3-okrężne wahadło przeciwne do ruchu wskazówek zegara; 4-płaskie wahadło sinusoidalne; 5-pionowe wahadło sinusoidalne w kształcie L; 6-pionowe wahadło trójkątne; 7-pionowe wahadło sinusoidalne
    * @param [in] weaveFrequency Częstotliwość wahadła (Hz)
    * @param [in] weaveIncStayTime Tryb oczekiwania 0-cykl nie zawiera czasu oczekiwania; 1-cykl zawiera czas oczekiwania
    * @param [in] weaveRange Amplituda wahadła (mm)
    * @param [in] weaveLeftStayTime Lewy czas postoju wahadła (ms)
    * @param [in] weaveRightStayTime Prawy czas postoju wahadła (ms)
    * @param [in] weaveCircleRadio Okrężne wahadło - współczynnik powrotu (0-100%)
    * @param [in] weaveStationary Oczekiwanie na pozycji wahadła, 0-pozycja kontynuuje ruch w czasie oczekiwania; 1-pozycja nieruchoma w czasie oczekiwania
    * @return Kod błędu
    */
    errno_t WeaveOnlineSetPara(int weaveNum, int weaveType, double weaveFrequency, int weaveIncStayTime, double weaveRange, int weaveLeftStayTime, int weaveRightStayTime, int weaveCircleRadio, int weaveStationary);

Ustawianie parametrów wykrywania nieoczekiwanego przerwania łuku spawania robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.8-3.7.8

.. code-block:: c++
    :linenos:

    /**
     * @brief Ustawia parametry wykrywania nieoczekiwanego przerwania łuku spawania robota
     * @param [in] checkEnable Czy włączyć wykrywanie; 0-niewłączone; 1-włączone
     * @param [in] arcInterruptTimeLength Czas potwierdzenia przerwania łuku (ms)
     * @return Kod błędu
     */
    errno_t WeldingSetCheckArcInterruptionParam(int checkEnable, int arcInterruptTimeLength);

Pobieranie parametrów wykrywania nieoczekiwanego przerwania łuku spawania robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.8-3.7.8

.. code-block:: c++
    :linenos:

    /**
     * @brief Pobiera parametry wykrywania nieoczekiwanego przerwania łuku spawania robota
     * @param [out] checkEnable Czy włączyć wykrywanie; 0-niewłączone; 1-włączone
     * @param [out] arcInterruptTimeLength Czas potwierdzenia przerwania łuku (ms)
     * @return Kod błędu
     */
    errno_t WeldingGetCheckArcInterruptionParam(int* checkEnable, int* arcInterruptTimeLength);

Ustawianie parametrów wznowienia po przerwaniu spawania robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.8-3.7.8

.. code-block:: c++
    :linenos:

    /**
     * @brief Ustawia parametry wznowienia po przerwaniu spawania robota
     * @param [in] enable Czy włączyć wznowienie po przerwaniu spawania
     * @param [in] length Odległość nakładania spoiny (mm)
     * @param [in] velocity Procent prędkości powrotu robota do punktu ponownego rozpoczęcia łuku (0-100)
     * @param [in] moveType Sposób ruchu robota do punktu ponownego rozpoczęcia łuku; 0-LIN; 1-PTP
     * @return Kod błędu
     */
    errno_t WeldingSetReWeldAfterBreakOffParam(int enable, double length, double velocity, int moveType);

Pobieranie parametrów wznowienia po przerwaniu spawania robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.8-3.7.8

.. code-block:: c++
    :linenos:

    /**
     * @brief Pobiera parametry wznowienia po przerwaniu spawania robota
     * @param [out] enable Czy włączyć wznowienie po przerwaniu spawania
     * @param [out] length Odległość nakładania spoiny (mm)
     * @param [out] velocity Procent prędkości powrotu robota do punktu ponownego rozpoczęcia łuku (0-100)
     * @param [out] moveType Sposób ruchu robota do punktu ponownego rozpoczęcia łuku; 0-LIN; 1-PTP
     * @return Kod błędu
     */
    errno_t WeldingGetReWeldAfterBreakOffParam(int* enable, double* length, double* velocity, int* moveType);

Ustawianie rozszerzonego portu DO trybu sterowania spawarką
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia rozszerzony port DO trybu sterowania spawarką
    * @param DONum Port DO trybu sterowania spawarką (0-127)
    * @return Kod błędu
    */
    errno_t SetWeldMachineCtrlModeExtDoNum(int DONum);

Ustawianie trybu sterowania spawarką
++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia tryb sterowania spawarką
    * @param [in] mode Tryb sterowania spawarką; 0-tryb stałego prądu/napięcia; 1-tryb impulsowy; 2-tryb JOB; 3-tryb zdalnego sterowania; 4-tryb oddzielny; 5-tryb CC/CV; 6-TIG; 7-CMT
    * @param [in] ioType Typ sterowania; 0-IO szafy sterowniczej; 1-Protokół komunikacji cyfrowej (UDP); 2-Protokół komunikacji cyfrowej (ModbusTCP)
    * @return Kod błędu
    */
    errno_t SetWeldMachineCtrlMode(int mode, int ioType = 1);

Rozpoczęcie spawania
++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Rozpoczęcie spawania
    * @param [in] ioType typ IO 0-IO sterownika; 1-rozszerzone IO
    * @param [in] arcNum Numer pliku konfiguracyjnego spawarki
    * @param [in] timeout Czas timeoutu rozpoczęcia łuku
    * @return Kod błędu
    */
    errno_t ARCStart(int ioType, int arcNum, int timeout);

Zakończenie spawania
++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Zakończenie spawania
    * @param [in] ioType typ IO 0-IO sterownika; 1-rozszerzone IO
    * @param [in] arcNum Numer pliku konfiguracyjnego spawarki
    * @param [in] timeout Czas timeoutu zgaśnięcia łuku
    * @return Kod błędu
    */
    errno_t ARCEnd(int ioType, int arcNum, int timeout);

Rozpoczęcie wahadła
+++++++++++++++++++
.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Rozpoczęcie wahadła
    * @param [in] weaveNum Numer konfiguracji parametrów spawania wahadłowego
    * @return Kod błędu
    */
    errno_t WeaveStart(int weaveNum);

Zakończenie wahadła
+++++++++++++++++++
.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Zakończenie wahadła
    * @param [in] weaveNum Numer konfiguracji parametrów spawania wahadłowego
    * @return Kod błędu
    */
    errno_t WeaveEnd(int weaveNum);

Podawanie drutu w przód
+++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Podawanie drutu w przód
    * @param [in] ioType typ IO 0-IO sterownika; 1-rozszerzone IO
    * @param [in] wireFeed Sterowanie podawaniem drutu 0-zatrzymaj podawanie drutu; 1-podawaj drut
    * @return Kod błędu
    */
    errno_t SetForwardWireFeed(int ioType, int wireFeed);

Podawanie drutu w tył
+++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Podawanie drutu w tył
    * @param [in] ioType typ IO 0-IO sterownika; 1-rozszerzone IO
    * @param [in] wireFeed Sterowanie podawaniem drutu 0-zatrzymaj podawanie drutu; 1-podawaj drut
    * @return Kod błędu
    */
    errno_t SetReverseWireFeed(int ioType, int wireFeed);

Podawanie gazu
++++++++++++++
.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Podawanie gazu
    * @param [in] ioType typ IO 0-IO sterownika; 1-rozszerzone IO
    * @param [in] airControl Sterowanie podawaniem gazu 0-zatrzymaj podawanie gazu; 1-podawaj gaz
    * @return Kod błędu
    */
    errno_t SetAspirated(int ioType, int airControl);

Ustawianie wznowienia spawania po przerwaniu spawania robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.8-3.7.8

.. code-block:: c++
    :linenos:

    /**
     * @brief Ustawia wznowienie spawania po przerwaniu spawania robota
     * @return Kod błędu
     */
    errno_t WeldingStartReWeldAfterBreakOff();

Ustawianie wyjścia z spawania po przerwaniu spawania robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.8-3.7.8

.. code-block:: c++
    :linenos:

    /**
     * @brief Ustawia wyjście z spawania po przerwaniu spawania robota
     * @return Kod błędu
     */
    errno_t WeldingAbortWeldAfterBreakOff();

Przykład kodu sterowania spawaniem robota
+++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestWelding(void)
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
      robot.SetForwardWireFeed(0, 1);
      robot.Sleep(1000);
      robot.SetForwardWireFeed(0, 0);
      robot.SetReverseWireFeed(0, 1);
      robot.Sleep(1000);
      robot.SetReverseWireFeed(0, 0);
      robot.SetAspirated(0, 1);
      robot.Sleep(1000);
      robot.SetAspirated(0, 0);
      robot.WeldingSetCurrent(1, 230, 0, 0);
      robot.WeldingSetVoltage(1, 24, 0, 1);
      DescPose p1Desc(228.879, -503.594, 453.984, -175.580, 8.293, 171.267);
      JointPos p1Joint(102.700, -85.333, 90.518, -102.365, -83.932, 22.134);
      DescPose p2Desc(-333.302, -435.580, 449.866, -174.997, 2.017, 109.815);
      JointPos p2Joint(41.862, -85.333, 90.526, -100.587, -90.014, 22.135);
      ExaxisPos exaxisPos(0, 0, 0, 0);
      DescPose offdese(0, 0, 0, 0, 0, 0);
      robot.MoveJ(&p1Joint, &p1Desc, 13, 0, 20, 100, 100, &exaxisPos, -1, 0, &offdese);
      robot.ARCStart(1, 0, 10000);
      robot.WeaveStart(0);
      robot.MoveL(&p2Joint, &p2Desc, 13, 0, 20, 100, 100, -1, 0, &exaxisPos, 0, 0, &offdese);
      robot.ARCEnd(1, 0, 10000);
      robot.WeaveEnd(0);
      robot.WeldingStartReWeldAfterBreakOff();
      robot.WeldingAbortWeldAfterBreakOff();
      robot.CloseRPC();
      return 0;
    }

Rozpoczęcie spawania odcinkowego
++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Rozpoczęcie spawania odcinkowego
    * @param [in] startDesePos Pozycja kartezjańska punktu początkowego
    * @param [in] endDesePos Pozycja i orientacja kartezjańska punktu końcowego
    * @param [in] startJPos Pozycja stawów punktu początkowego
    * @param [in] endJPos Pozycja stawów punktu końcowego
    * @param [in] weldLength Długość odcinka spawanego (mm)
    * @param [in] noWeldLength Długość odcinka niespawanego (mm)
    * @param [in] weldIOType Typ IO spawania (0-IO szafy sterowniczej; 1-rozszerzone IO)
    * @param [in] arcNum Numer pliku konfiguracyjnego spawarki
    * @param [in] weldTimeout Czas timeoutu rozpoczęcia/zakończenia łuku
    * @param [in] isWeave Czy wahadło
    * @param [in] weaveNum Numer konfiguracji parametrów spawania wahadłowego
    * @param [in] tool Numer układu współrzędnych narzędzia, zakres [0~14]
    * @param [in] user Numer układu współrzędnych obiektu, zakres [0~14]
    * @param [in] vel Procent prędkości, zakres [0~100]
    * @param [in] acc Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param [in] ovl Współczynnik skalowania prędkości, zakres [0~100]
    * @param [in] blendR [-1.0]-ruch do pozycji (blokujący), [0~1000.0]-promień wygładzania (nieblokujący), jednostka mm
    * @param [in] epos Pozycja osi rozszerzonej, jednostka mm
    * @param [in] search 0-brak lokalizacji drutu spawalniczego, 1-lokalizacja drutu spawalniczego
    * @param [in] offset_flag 0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie obiektu, 2-przesunięcie w układzie narzędzia
    * @param [in] offset_pos Wartość przesunięcia pozy i orientacji
    * @return Kod błędu
    */
    errno_t SegmentWeldStart(DescPose *startDesePos, DescPose *endDesePos, JointPos *startJPos, JointPos *endJPos, double weldLength, double noWeldLength, int weldIOType, int arcNum, int weldTimeout, bool isWeave, int weaveNum, int tool, int user, float vel, float acc, float ovl, float blendR, ExaxisPos *epos, uint8_t search, uint8_t offset_flag, DescPose *offset_pos);

Przykład kodu spawania odcinkowego robota
+++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.2.0

.. code-block:: c++
    :linenos:

    int TestSegWeld(void)
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
      robot.WeldingSetCurrent(1, 230, 0, 0);
      robot.WeldingSetVoltage(1, 24, 0, 1);
      DescPose p1Desc(228.879, -503.594, 453.984, -175.580, 8.293, 171.267);
      JointPos p1Joint(102.700, -85.333, 90.518, -102.365, -83.932, 22.134);
      DescPose p2Desc(-333.302, -435.580, 449.866, -174.997, 2.017, 109.815);
      JointPos p2Joint(41.862, -85.333, 90.526, -100.587, -90.014, 22.135);
      ExaxisPos exaxisPos(0, 0, 0, 0);
      DescPose offdese(0, 0, 0, 0, 0, 0);
      rtn = robot.SegmentWeldStart(&p1Desc, &p2Desc, &p1Joint, &p2Joint, 20, 20, 0, 0, 5000, 0, 0, 0, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese);
      printf("SegmentWeldStart rtn is %d\n", rtn);
      robot.CloseRPC();
      return 0;
    }

Rozpoczęcie symulacji wahadła
+++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Rozpoczęcie symulacji wahadła
     * @param [in] weaveNum Numer parametrów wahadła
     * @return Kod błędu
     */
    errno_t WeaveStartSim(int weaveNum);

Zakończenie symulacji wahadła
+++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Zakończenie symulacji wahadła
     * @param [in] weaveNum Numer parametrów wahadła
     * @return Kod błędu
     */
    errno_t WeaveEndSim(int weaveNum);

Rozpoczęcie ostrzegania o wykryciu trajektorii (bez ruchu)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Rozpoczęcie ostrzegania o wykryciu trajektorii (bez ruchu)
     * @param [in] weaveNum  Numer parametrów wahadła
     * @return Kod błędu
     */
    errno_t WeaveInspectStart(int weaveNum);

Zakończenie ostrzegania o wykryciu trajektorii (bez ruchu)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Zakończenie ostrzegania o wykryciu trajektorii (bez ruchu)
     * @param [in] weaveNum  Numer parametrów wahadła
     * @return Kod błędu
     */
    errno_t WeaveInspectEnd(int weaveNum);

Rozpoczęcie gradientu wahadła
+++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Rozpoczęcie gradientu wahadła
     * @param [in] weaveChangeFlag 1-zmiana parametrów wahadła; 2-zmiana parametrów wahadła + prędkości spawania
     * @param [in] weaveNum Numer wahadła
     * @param [in] velStart Prędkość początkowa spawania (cm/min)
     * @param [in] velEnd Prędkość końcowa spawania (cm/min)
     * @return Kod błędu
     */
     errno_t WeaveChangeStart(int weaveChangeFlag, int weaveNum, double velStart, double velEnd);

Przykład kodu spawania z gradientem wahadła robota
++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestWeave(void)
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
      DescPose p1Desc(228.879, -503.594, 453.984, -175.580, 8.293, 171.267);
      JointPos p1Joint(102.700, -85.333, 90.518, -102.365, -83.932, 22.134);
      DescPose p2Desc(-333.302, -435.580, 449.866, -174.997, 2.017, 109.815);
      JointPos p2Joint(41.862, -85.333, 90.526, -100.587, -90.014, 22.135);
      ExaxisPos exaxisPos(0, 0, 0, 0);
      DescPose offdese(0, 0, 0, 0, 0, 0);
      robot.MoveJ(&p1Joint, &p1Desc, 13, 0, 20, 100, 100, &exaxisPos, -1, 0, &offdese);
      robot.WeaveStartSim(0);
      robot.MoveL(&p2Joint, &p2Desc, 13, 0, 20, 100, 100, -1, 0, &exaxisPos, 0, 0, &offdese);
      robot.WeaveEndSim(0);
      robot.MoveJ(&p1Joint, &p1Desc, 13, 0, 20, 100, 100, &exaxisPos, -1, 0, &offdese);
      robot.WeaveInspectStart(0);
      robot.MoveL(&p2Joint, &p2Desc, 13, 0, 20, 100, 100, -1, 0, &exaxisPos, 0, 0, &offdese);
      robot.WeaveInspectEnd(0);
      robot.WeldingSetVoltage(1, 19, 0, 0);
      robot.WeldingSetCurrent(1, 190, 0, 0);
      robot.MoveL(&p1Joint, &p1Desc, 1, 1, 100, 100, 50, -1, &exaxisPos, 0, 0, &offdese);
      robot.ARCStart(1, 0, 10000);
      robot.ArcWeldTraceControl(1, 0, 1, 0.06, 5, 5, 60, 1, 0.06, 5, 5, 80, 0, 0, 4, 1, 10, 0, 0);
      robot.WeaveStart(0);
      robot.WeaveChangeStart(1, 0, 50, 30);
      robot.MoveL(&p2Joint, &p2Desc, 1, 1, 100, 100, 1, -1, &exaxisPos, 0, 0, &offdese);
      robot.WeaveChangeEnd();
      robot.WeaveEnd(0);
      robot.ArcWeldTraceControl(0, 0, 1, 0.06, 5, 5, 60, 1, 0.06, 5, 5, 80, 0, 0, 4, 1, 10, 0, 0);
      robot.ARCEnd(1, 0, 10000);
      robot.CloseRPC();
      return 0;
    }

Zakończenie gradientu wahadła
+++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.0-3.8.0

.. code-block:: c++
    :linenos:

    /**
     * @brief  Zakończenie gradientu wahadła
     * @return  Kod błędu
     */
    errno_t WeaveChangeEnd();

Rozszerzone IO - konfiguracja sygnału detekcji gazu spawarki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Rozszerzone IO - konfiguracja sygnału detekcji gazu spawarki
     * @param [in] DONum Rozszerzony numer DO sygnału detekcji gazu
     * @return Kod błędu
     */
    errno_t SetAirControlExtDoNum(int DONum);

Rozszerzone IO - konfiguracja sygnału rozpoczęcia łuku spawarki
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Rozszerzone IO - konfiguracja sygnału rozpoczęcia łuku spawarki
     * @param [in] DONum Rozszerzony numer DO sygnału rozpoczęcia łuku spawarki
     * @return Kod błędu
     */
    errno_t SetArcStartExtDoNum(int DONum);

Rozszerzone IO - konfiguracja sygnału podawania drutu w tył spawarki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Rozszerzone IO - konfiguracja sygnału podawania drutu w tył spawarki
     * @param [in] DONum Rozszerzony numer DO sygnału podawania drutu w tył
     * @return Kod błędu
     */
    errno_t SetWireReverseFeedExtDoNum(int DONum);

Rozszerzone IO - konfiguracja sygnału podawania drutu w przód spawarki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Rozszerzone IO - konfiguracja sygnału podawania drutu w przód spawarki
     * @param [in] DONum Rozszerzony numer DO sygnału podawania drutu w przód
     * @return Kod błędu
     */
    errno_t SetWireForwardFeedExtDoNum(int DONum);

Rozszerzone IO - konfiguracja sygnału sukcesu rozpoczęcia łuku spawarki
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Rozszerzone IO - konfiguracja sygnału sukcesu rozpoczęcia łuku spawarki
     * @param [in] DINum Rozszerzony numer DI sygnału sukcesu rozpoczęcia łuku
     * @return Kod błędu
     */
    errno_t SetArcDoneExtDiNum(int DINum);

Rozszerzone IO - konfiguracja sygnału gotowości spawarki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Rozszerzone IO - konfiguracja sygnału gotowości spawarki
     * @param [in] DINum Rozszerzony numer DI sygnału gotowości spawarki
     * @return Kod błędu
     */
    errno_t SetWeldReadyExtDiNum(int DINum);

Rozszerzone IO - konfiguracja sygnału wznowienia po przerwaniu spawania
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Rozszerzone IO - konfiguracja sygnału wznowienia po przerwaniu spawania
     * @param [in] reWeldDINum Rozszerzony numer DI sygnału wznowienia spawania po przerwaniu
     * @param [in] abortWeldDINum Rozszerzony numer DI sygnału wyjścia z spawania po przerwaniu
     * @return Kod błędu
     */
    errno_t SetExtDIWeldBreakOffRecover(int reWeldDINum, int abortWeldDINum);

Przykład kodu ustawiania sygnałów spawania rozszerzonego IO
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestExtDIConfig(void)
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
      robot.SetArcStartExtDoNum(10);
      robot.SetAirControlExtDoNum(20);
      robot.SetWireForwardFeedExtDoNum(30);
      robot.SetWireReverseFeedExtDoNum(40);
      robot.SetWeldReadyExtDiNum(50);
      robot.SetArcDoneExtDiNum(60);
      robot.SetExtDIWeldBreakOffRecover(70, 80);
      robot.SetWireSearchExtDIONum(0, 1);
      robot.CloseRPC();
      return 0;
    }

Sterowanie śledzeniem łuku spawalniczego
++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

      /**
      * @brief  Sterowanie śledzeniem łuku spawalniczego
      * @param  [in] flag Przełącznik, 0-wył.; 1-wł.
      * @param  [in] dalayTime Czas opóźnienia, jednostka ms
      * @param  [in] isLeftRight Kompensacja odchylenia lewo/prawo
      * @param  [in] klr Współczynnik regulacji lewo/prawo (czułość);
      * @param  [in] tStartLr Czas rozpoczęcia kompensacji lewo/prawo cyc
      * @param  [in] stepMaxLr Maksymalna wielkość kompensacji na cykl lewo/prawo mm
      * @param  [in] sumMaxLr Maksymalna całkowita wielkość kompensacji lewo/prawo mm
      * @param  [in] isUpLow Kompensacja odchylenia góra/dół
      * @param  [in] kud Współczynnik regulacji góra/dół (czułość);
      * @param  [in] tStartUd Czas rozpoczęcia kompensacji góra/dół cyc
      * @param  [in] stepMaxUd Maksymalna wielkość kompensacji na cykl góra/dół mm
      * @param  [in] sumMaxUd Maksymalna całkowita wielkość kompensacji góra/dół
      * @param  [in] axisSelect Wybór układu współrzędnych góra/dół, 0-wahadło; 1-narzędzie; 2-podstawa
      * @param  [in] referenceType Sposób ustawienia prądu odniesienia góra/dół, 0-sprzężenie zwrotne; 1-stała
      * @param  [in] referSampleStartUd Rozpoczęcie zliczania próbkowania prądu odniesienia góra/dół (sprzężenie zwrotne); cyc
      * @param  [in] referSampleCountUd Liczba cykli próbkowania prądu odniesienia góra/dół (sprzężenie zwrotne); cyc
      * @param  [in] referenceCurrent Prąd odniesienia góra/dół mA
      * @param  [in] offsetType Typ śledzenia z przesunięciem, 0-bez przesunięcia; 1-próbkowanie; 2-procent
      * @param  [in] offsetParameter Parametr przesunięcia; próbkowanie (czas rozpoczęcia próbkowania przesunięcia, domyślnie jeden cykl); procent (procent przesunięcia (-100 ~ 100))
      * @return  Kod błędu
      */
     errno_t ArcWeldTraceControl(int flag, double delaytime, int isLeftRight, double klr, double tStartLr, double stepMaxLr, double sumMaxLr, int isUpLow, double kud, double tStartUd, double stepMaxUd, double sumMaxUd, int axisSelect, int referenceType, double referSampleStartUd, double referSampleCountUd, double referenceCurrent, int offsetType = 0, int offsetParameter = 0);

Ustawianie portu wejściowego sygnału śledzenia łuku spawalniczego
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

     /**
      * @brief  Ustawia port wejściowy sygnału śledzenia łuku spawalniczego
      * @param  [in] channel Pasmo AI dla śledzenia łuku spawalniczego, [0-3]
      * @return  Kod błędu
      */
     errno_t ArcWeldTraceExtAIChannelConfig(int channel);

Rozpoczęcie śledzenia łuku spawalniczego + kompensacji wielowarstwowej i wielościeżkowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Rozpoczęcie śledzenia łuku spawalniczego + kompensacji wielowarstwowej i wielościeżkowej
    * @return Kod błędu
    */
    errno_t ArcWeldTraceReplayStart();

Zakończenie śledzenia łuku spawalniczego + kompensacji wielowarstwowej i wielościeżkowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Zakończenie śledzenia łuku spawalniczego + kompensacji wielowarstwowej i wielościeżkowej
    * @return Kod błędu
    */
    errno_t ArcWeldTraceReplayEnd();

Zmiana współrzędnych przesunięcia - spawanie wielowarstwowe i wielościeżkowe
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Zmiana współrzędnych przesunięcia - spawanie wielowarstwowe i wielościeżkowe
    * @return Kod błędu
    */
    errno_t MultilayerOffsetTrsfToBase(DescTran pointO, DescTran pointX, DescTran pointZ, double dx, double dy, double db, DescPose& offset);

Przykład kodu śledzenia łuku spawalniczego dla spawania wielowarstwowego i wielościeżkowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestArcWeldTrace(void)
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
      JointPos mulitilineorigin1_joint(-24.090, -63.501, 84.288, -111.940, -93.426, 57.669);
      DescPose mulitilineorigin1_desc(-677.559, 190.951, -1.205, 1.144, -41.482, -82.577);
      DescTran mulitilineX1_desc;
      mulitilineX1_desc.x = -677.556;
      mulitilineX1_desc.y = 211.949;
      mulitilineX1_desc.z = -1.206;
      DescTran mulitilineZ1_desc;
      mulitilineZ1_desc.x = -677.564;
      mulitilineZ1_desc.y = 190.956;
      mulitilineZ1_desc.z = 19.817;
      JointPos mulitilinesafe_joint(-25.734, -63.778, 81.502, -108.975, -93.392, 56.021);
      DescPose mulitilinesafe_desc(-677.561, 211.950, 19.812, 1.144, -41.482, -82.577);
      JointPos mulitilineorigin2_joint(-29.743, -75.623, 101.241, -116.354, -94.928, 55.735);
      DescPose mulitilineorigin2_desc(-563.961, 215.359, -0.681, 2.845, -40.476, -87.443);
      DescTran mulitilineX2_desc;
      mulitilineX2_desc.x = -563.965;
      mulitilineX2_desc.y = 220.355;
      mulitilineX2_desc.z = -0.680;
      DescTran mulitilineZ2_desc;
      mulitilineZ2_desc.x = -563.968;
      mulitilineZ2_desc.y = 215.362;
      mulitilineZ2_desc.z = 4.331;
      ExaxisPos epos(0, 0, 0, 0);
      DescPose offset(0, 0, 0, 0, 0, 0);
      robot.Sleep(10);
      int error = robot.MoveJ(&mulitilinesafe_joint, &mulitilinesafe_desc, 13, 0, 10, 100, 100, &epos, -1, 0, &offset);
      printf("MoveJ return: %d\n", error);
      error = robot.MoveL(&mulitilineorigin1_joint, &mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1, &epos, 0, 0, &offset, 0, 100);
      printf("MoveL return: %d\n", error);
      error = robot.MoveJ(&mulitilinesafe_joint, &mulitilinesafe_desc, 13, 0, 10, 100, 100, &epos, -1, 0, &offset);
      printf("MoveJ return: %d\n", error);
      error = robot.MoveL(&mulitilineorigin2_joint, &mulitilineorigin2_desc, 13, 0, 10, 100, 100, -1, &epos, 0, 0, &offset, 0, 100);
      printf("MoveL return: %d\n", error);
      error = robot.MoveJ(&mulitilinesafe_joint, &mulitilinesafe_desc, 13, 0, 10, 100, 100, &epos, -1, 0, &offset);
      printf("MoveJ return: %d\n", error);
      error = robot.MoveL(&mulitilineorigin1_joint, &mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1, &epos, 0, 0, &offset, 0, 100);
      printf("MoveL return: %d\n", error);
      error = robot.ARCStart(1, 0, 3000);
      printf("ARCStart return: %d\n", error);
      error = robot.WeaveStart(0);
      printf("WeaveStart return: %d\n", error);
      error = robot.ArcWeldTraceControl(1, 0, 1, 0.06, 5, 5, 50, 1, 0.06, 5, 5, 55, 0, 0, 4, 1, 10);
      printf("ArcWeldTraceControl return: %d\n", error);
      error = robot.MoveL(&mulitilineorigin2_joint, &mulitilineorigin2_desc, 13, 0, 1, 100, 100, -1, &epos, 0, 0, &offset, 0, 100);
      printf("MoveL return: %d\n", error);
      error = robot.ArcWeldTraceControl(0, 0, 1, 0.06, 5, 5, 50, 1, 0.06, 5, 5, 55, 0, 0, 4, 1, 10);
      printf("ArcWeldTraceControl return: %d\n", error);
      error = robot.WeaveEnd(0);
      printf("WeaveEnd return: %d\n", error);
      error = robot.ARCEnd(1, 0, 10000);
      printf("ARCEnd return: %d\n", error);
      error = robot.MoveJ(&mulitilinesafe_joint, &mulitilinesafe_desc, 13, 0, 10, 100, 100, &epos, -1, 0, &offset);
      printf("MoveJ return: %d\n", error);
      error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin1_desc.tran, mulitilineX1_desc, mulitilineZ1_desc, 10.0, 0.0, 0.0, offset);
      printf("MultilayerOffsetTrsfToBase return: %d offect is %f %f %f \n", error, offset.tran.x, offset.tran.y, offset.tran.z);
      error = robot.MoveL(&mulitilineorigin1_joint, &mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1, &epos, 0, 1, &offset, 0, 100);
      printf("MoveL return: %d\n", error);
      error = robot.ARCStart(1, 0, 3000);
      printf("ARCStart return: %d\n", error);
      error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin2_desc.tran, mulitilineX2_desc, mulitilineZ2_desc, 10, 0, 0, offset);
      printf("MultilayerOffsetTrsfToBase return: %d offect is %f %f %f \n", error, offset.tran.x, offset.tran.y, offset.tran.z);
      error = robot.ArcWeldTraceReplayStart();
      printf("ArcWeldTraceReplayStart return: %d\n", error);
      error = robot.MoveL(&mulitilineorigin2_joint, &mulitilineorigin2_desc, 13, 0, 2, 100, 100, -1, &epos, 0, 1, &offset, 0, 100);
      printf("MoveL return: %d\n", error);
      error = robot.ArcWeldTraceReplayEnd();
      printf("ArcWeldTraceReplayEnd return: %d\n", error);
      error = robot.ARCEnd(1, 0, 10000);
      printf("ARCEnd return: %d\n", error);
      error = robot.MoveJ(&mulitilinesafe_joint, &mulitilinesafe_desc, 13, 0, 10, 100, 100, &epos, -1, 0, &offset);
      printf("MoveJ return: %d\n", error);
      error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin1_desc.tran, mulitilineX1_desc, mulitilineZ1_desc, 0, 10, 0, offset);
      printf("MultilayerOffsetTrsfToBase return: %d offect is %f %f %f \n", error, offset.tran.x, offset.tran.y, offset.tran.z);
      error = robot.MoveL(&mulitilineorigin1_joint, &mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1, &epos, 0, 1, &offset, 0, 100);
      printf("MoveL return: %d\n", error);
      error = robot.ARCStart(1, 0, 3000);
      printf("ARCStart return: %d\n", error);
      error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin2_desc.tran, mulitilineX2_desc, mulitilineZ2_desc, 0, 10, 0, offset);
      printf("MultilayerOffsetTrsfToBase return: %d offect is %f %f %f \n", error, offset.tran.x, offset.tran.y, offset.tran.z);
      error = robot.ArcWeldTraceReplayStart();
      printf("MoveJ return: %d\n", error);
      error = robot.MoveL(&mulitilineorigin2_joint, &mulitilineorigin2_desc, 13, 0, 2, 100, 100, -1, &epos, 0, 1, &offset, 0, 100);
      printf("MoveL return: %d\n", error);
      error = robot.ArcWeldTraceReplayEnd();
      printf("ArcWeldTraceReplayEnd return: %d\n", error);
      error = robot.ARCEnd(1, 0, 3000);
      printf("ARCEnd return: %d\n", error);
      error = robot.MoveJ(&mulitilinesafe_joint, &mulitilinesafe_desc, 13, 0, 10, 100, 100, &epos, -1, 0, &offset);
      printf("MoveJ return: %d\n", error);
      robot.CloseRPC();
      return 0;
    }

Wybór kanału AI dla sprzężenia zwrotnego prądu spawarki w śledzeniu łuku spawalniczego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Wybór kanału AI dla sprzężenia zwrotnego prądu spawarki w śledzeniu łuku spawalniczego
     * @param [in]  channel Kanał; 0-rozszerzone AI0; 1-rozszerzone AI1; 2-rozszerzone AI2; 3-rozszerzone AI3; 4-AI0 szafy sterowniczej; 5-AI1 szafy sterowniczej
     * @return Kod błędu
     */
     errno_t ArcWeldTraceAIChannelCurrent(int channel);

Wybór kanału AI dla sprzężenia zwrotnego napięcia spawarki w śledzeniu łuku spawalniczego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Wybór kanału AI dla sprzężenia zwrotnego napięcia spawarki w śledzeniu łuku spawalniczego
     * @param [in]  channel Kanał; 0-rozszerzone AI0; 1-rozszerzone AI1; 2-rozszerzone AI2; 3-rozszerzone AI3; 4-AI0 szafy sterowniczej; 5-AI1 szafy sterowniczej
     * @return Kod błędu
     */
     errno_t ArcWeldTraceAIChannelVoltage(int channel);

Parametry konwersji sprzężenia zwrotnego prądu spawarki w śledzeniu łuku spawalniczego
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     /**
      * @brief Parametry konwersji sprzężenia zwrotnego prądu spawarki w śledzeniu łuku spawalniczego
      * @param [in] AILow Dolna granica kanału AI, wartość domyślna 0V, zakres [0-10V]
      * @param [in] AIHigh Górna granica kanału AI, wartość domyślna 10V, zakres [0-10V]
      * @param [in] currentLow Wartość prądu spawarki odpowiadająca dolnej granicy kanału AI, wartość domyślna 0V, zakres [0-200V]
      * @param [in] currentHigh Wartość prądu spawarki odpowiadająca górnej granicy kanału AI, wartość domyślna 100V, zakres [0-200V]
      * @return Kod błędu
      */
     errno_t ArcWeldTraceCurrentPara(float AILow, float AIHigh, float currentLow, float currentHigh);

Parametry konwersji sprzężenia zwrotnego napięcia spawarki w śledzeniu łuku spawalniczego
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     /**
    * @brief Parametry konwersji sprzężenia zwrotnego napięcia spawarki w śledzeniu łuku spawalniczego
    * @param [in] AILow Dolna granica kanału AI, wartość domyślna 0V, zakres [0-10V]
    * @param [in] AIHigh Górna granica kanału AI, wartość domyślna 10V, zakres [0-10V]
    * @param [in] voltageLow Wartość napięcia spawarki odpowiadająca dolnej granicy kanału AI, wartość domyślna 0V, zakres [0-200V]
    * @param [in] voltageHigh Wartość napięcia spawarki odpowiadająca górnej granicy kanału AI, wartość domyślna 100V, zakres [0-200V]
    * @return Kod błędu
    */
    errno_t ArcWeldTraceVoltagePara(float AILow, float AIHigh, float voltageLow, float voltageHigh);

Przykład kodu śledzenia łuku spawalniczego
++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int WeldTraceControlWithCtrlBoxAI(FRRobot* robot)
    {
      DescPose startdescPose = { -473.86, 257.879, -20.849, -37.317, -42.021, 2.543 };
      JointPos startjointPos = { -43.487, -76.526, 95.568, -104.445, -89.356, 3.72 };

      DescPose enddescPose = { -499.844, 141.225, 7.72, -34.856, -40.17, 13.13 };
      JointPos endjointPos = { -31.305, -82.998, 99.401, -104.426, -89.35, 3.696 };

      DescPose safedescPose = { -504.043, 275.181, 40.908, -28.002, -42.025, -14.044 };
      JointPos safejointPos = { -39.078, -76.732, 87.227, -99.47, -94.301, 18.714 };

      ExaxisPos exaxisPos = { 0, 0, 0, 0 };
      DescPose offdese = { 0, 0, 0, 0, 0, 0 };

      robot->WeldingSetCurrentRelation(0, 495, 1, 10, 0);
      robot->WeldingSetVoltageRelation(10, 45, 1, 10, 1);

      robot->WeldingSetVoltage(0, 25, 1, 0);// ---- ustawienie napięcia
      robot->WeldingSetCurrent(0, 260, 0, 0);// ---- ustawienie prądu

      int rtn = robot->ArcWeldTraceAIChannelCurrent(4);
      cout << "ArcWeldTraceAIChannelCurrent rtn is " << rtn << endl;
      rtn = robot->ArcWeldTraceAIChannelVoltage(5);
      cout << "ArcWeldTraceAIChannelVoltage rtn is " << rtn << endl;
      rtn = robot->ArcWeldTraceCurrentPara(0, 5, 0, 500);
      cout << "ArcWeldTraceCurrentPara rtn is " << rtn << endl;
      rtn = robot->ArcWeldTraceVoltagePara(1.018, 10, 0, 50);
      cout << "ArcWeldTraceVoltagePara rtn is " << rtn << endl;
      robot->MoveJ(&safejointPos, &safedescPose, 1, 0, 5, 100, 100, &exaxisPos, -1, 0, &offdese);
      robot->MoveJ(&startjointPos, &startdescPose, 1, 0, 5, 100, 100, &exaxisPos, -1, 0, &offdese);
      rtn = robot->ArcWeldTraceControl(1, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);
      cout << "ArcWeldTraceControl rtn is " << rtn << endl;
      robot->ARCStart(0, 0, 10000);
      robot->WeaveStart(0);
      robot->MoveL(&endjointPos, &enddescPose, 1, 0, 100, 100, 2, -1, &exaxisPos, 0, 0, &offdese);
      robot->ARCEnd(0, 0, 10000);
      robot->WeaveEnd(0);
      robot->ArcWeldTraceControl(0, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);
      return 0;
    }

Ustawianie rozszerzonego portu IO dla lokalizacji drutu spawalniczego
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia rozszerzony port IO dla lokalizacji drutu spawalniczego
    * @param searchDoneDINum Port DO sukcesu lokalizacji drutu spawalniczego (0-127)
    * @param searchStartDONum Port DO sterowania uruchamianiem/zatrzymywaniem lokalizacji drutu spawalniczego (0-127)
    * @return Kod błędu
    */
    errno_t SetWireSearchExtDIONum(int searchDoneDINum, int searchStartDONum);

Przykładowy program
+++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    void TestUDPWireSearch(FRRobot* robot)
    {
    robot->ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 50, 5, 50, 1, 50, 10);
    robot->ExtDevLoadUDPDriver();

    robot->SetWireSearchExtDIONum(0, 0);

    int rtn0, rtn1, rtn2 = 0;
    ExaxisPos exaxisPos = { 0.0, 0.0, 0.0, 0.0 };
    DescPose offdese = { 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 };

    DescPose descStart = { -158.767, -510.596, 271.709, -179.427, -0.745, -137.349 };
    JointPos jointStart = { 61.667, -79.848, 108.639, -119.682, -89.700, -70.985 };

    DescPose descEnd = { 0.332, -516.427, 270.688, 178.165, 0.017, -119.989 };
    JointPos jointEnd = { 79.021, -81.839, 110.752, -118.298, -91.729, -70.981 };

    robot->MoveL(&jointStart, &descStart, 1, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese);
    robot->MoveL(&jointEnd, &descEnd, 1, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese);

    DescPose descREF0A = { -66.106, -560.746, 270.381, 176.479, -0.126, -126.745 };
    JointPos jointREF0A = { 73.531, -75.588, 102.941, -116.250, -93.347, -69.689 };

    DescPose descREF0B = { -66.109, -528.440, 270.407, 176.479, -0.129, -126.744 };
    JointPos jointREF0B = { 72.534, -79.625, 108.046, -117.379, -93.366, -70.687 };

    DescPose descREF1A = { 72.975, -473.242, 270.399, 176.479, -0.129, -126.744 };
    JointPos jointREF1A = { 87.169, -86.509, 115.710, -117.341, -92.993, -56.034 };

    DescPose descREF1B = { 31.355, -473.238, 270.405, 176.480, -0.130, -126.745 };
    JointPos jointREF1B = { 82.117, -87.146, 116.470, -117.737, -93.145, -61.090 };

    rtn0 = robot->WireSearchStart(0, 10, 100, 0, 10, 100, 0);
    robot->MoveL(&jointREF0A, &descREF0A, 1, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese); //punkt początkowy
    robot->MoveL(&jointREF0B, &descREF0B, 1, 0, 10, 100, 100, -1, &exaxisPos, 1, 0, &offdese); //punkt kierunkowy
    rtn1 = robot->WireSearchWait("REF0");
    rtn2 = robot->WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

    rtn0 = robot->WireSearchStart(0, 10, 100, 0, 10, 100, 0);
    robot->MoveL(&jointREF1A, &descREF1A, 1, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese); //punkt początkowy
    robot->MoveL(&jointREF1B, &descREF1B, 1, 0, 10, 100, 100, -1, &exaxisPos, 1, 0, &offdese); //punkt kierunkowy
    rtn1 = robot->WireSearchWait("REF1");
    rtn2 = robot->WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

    rtn0 = robot->WireSearchStart(0, 10, 100, 0, 10, 100, 0);
    robot->MoveL(&jointREF0A, &descREF0A, 1, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese); //punkt początkowy
    robot->MoveL(&jointREF0B, &descREF0B, 1, 0, 10, 100, 100, -1, &exaxisPos, 1, 0, &offdese); //punkt kierunkowy
    rtn1 = robot->WireSearchWait("RES0");
    rtn2 = robot->WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

    rtn0 = robot->WireSearchStart(0, 10, 100, 0, 10, 100, 0);
    robot->MoveL(&jointREF1A, &descREF1A, 1, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese); //punkt początkowy
    robot->MoveL(&jointREF1B, &descREF1B, 1, 0, 10, 100, 100, -1, &exaxisPos, 1, 0, &offdese); //punkt kierunkowy
    rtn1 = robot->WireSearchWait("RES1");
    rtn2 = robot->WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

    vector <string> varNameRef = { "REF0", "REF1", "#", "#", "#", "#" };
    vector <string> varNameRes = { "RES0", "RES1", "#", "#", "#", "#" };
    int offectFlag = 0;
    DescPose offectPos = { 0, 0, 0, 0, 0, 0 };
    rtn0 = robot->GetWireSearchOffset(0, 0, varNameRef, varNameRes, offectFlag, offectPos);
    robot->PointsOffsetEnable(0, &offectPos);
    robot->MoveL(&jointStart, &descStart, 1, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese);
    robot->MoveL(&jointEnd, &descEnd, 1, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese);
    robot->PointsOffsetDisable();
    }

Rozpoczęcie lokalizacji drutu spawalniczego
+++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief  Rozpoczęcie lokalizacji drutu spawalniczego
    * @param  [in] refPos  1-punkt odniesienia 0-punkt kontaktu
    * @param  [in] searchVel   Prędkość lokalizacji %
    * @param  [in] searchDis  Odległość lokalizacji mm
    * @param  [in] autoBackFlag Flaga automatycznego powrotu, 0-nie automatyczny; -automatyczny
    * @param  [in] autoBackVel  Prędkość automatycznego powrotu %
    * @param  [in] autoBackDis  Odległość automatycznego powrotu mm
    * @param  [in] offectFlag  1-lokalizacja z przesunięciem; 0-lokalizacja punktem nauczania
    * @return  Kod błędu
    */
     errno_t WireSearchStart(int refPos, float searchVel, int searchDis, int autoBackFlag, float autoBackVel, int autoBackDis, int offectFlag);

Zakończenie lokalizacji drutu spawalniczego
+++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

     /**
      * @brief  Zakończenie lokalizacji drutu spawalniczego
      * @param  [in] refPos  1-punkt odniesienia 2-punkt kontaktu
      * @param  [in] searchVel   Prędkość lokalizacji %
      * @param  [in] searchDis  Odległość lokalizacji mm
      * @param  [in] autoBackFlag Flaga automatycznego powrotu, 0-nie automatyczny; -automatyczny
      * @param  [in] autoBackVel  Prędkość automatycznego powrotu %
      * @param  [in] autoBackDis  Odległość automatycznego powrotu mm
      * @param  [in] offectFlag  1-lokalizacja z przesunięciem; 2-lokalizacja punktem nauczania
      * @return  Kod błędu
      */
     errno_t WireSearchEnd(int refPos, float searchVel, int searchDis, int autoBackFlag, float autoBackVel, int autoBackDis, int offectFlag);

Obliczanie przesunięcia lokalizacji drutu spawalniczego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

     /**
      * @brief  Obliczanie przesunięcia lokalizacji drutu spawalniczego
      * @param  [in] seamType  Typ spoiny
      * @param  [in] method   Metoda obliczeniowa
      * @param  [in] varNameRef Punkty odniesienia 1-6, „#” oznacza brak punktu
      * @param  [in] varNameRes Punkty kontaktu 1-6, „#” oznacza brak punktu
      * @param  [out] offectFlag 0-przesunięcie dodawane bezpośrednio do punktu instrukcji; 1-przesunięcie wymaga transformacji współrzędnych punktu instrukcji
      * @param  [out] offect Pozycja i orientacja przesunięcia [x, y, z, a, b, c]
      * @return  Kod błędu
      */
     errno_t GetWireSearchOffset(int seamType, int method, std::vector<std::string> varNameRef, std::vector<std::string> varNameRes, int& offectFlag, DescPose& offect);

Oczekiwanie na zakończenie lokalizacji drutu spawalniczego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

     /**
      * @brief  Oczekiwanie na zakończenie lokalizacji drutu spawalniczego
      * @return  Kod błędu
      */
     errno_t WireSearchWait(std::string varName);

Zapis punktu kontaktu lokalizacji drutu spawalniczego do bazy danych
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

     /**
      * @brief  Zapis punktu kontaktu lokalizacji drutu spawalniczego do bazy danych
      * @param  [in] varName  Nazwa punktu kontaktu „RES0” ~ „RES99”
      * @param  [in] pos  Dane punktu kontaktu [x, y, x, a, b, c]
      * @return  Kod błędu
      */
     errno_t SetPointToDatabase(std::string varName, DescPose pos);

Przykład kodu lokalizacji drutu spawalniczego robota
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    int TestWireSearch(void)
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
      DescPose toolCoord(0, 0, 200, 0, 0, 0);
      robot.SetToolCoord(1, &toolCoord, 0, 0, 1, 0);
      DescPose wobjCoord(0, 0, 0, 0, 0, 0);
      robot.SetWObjCoord(1, &wobjCoord, 0);
      int rtn0, rtn1, rtn2 = 0;
      ExaxisPos exaxisPos = { 0, 0, 0, 0 };
      DescPose offdese = { 0, 0, 0, 0, 0, 0 };
      DescPose descStart = { 216.543, 445.175, 93.465, 179.683, 1.757, -112.641 };
      JointPos jointStart = { -128.345, -86.660, 114.679, -119.625, -89.219, 74.303 };
      DescPose descEnd = { 111.143, 523.384, 87.659, 179.703, 1.835, -97.750 };
      JointPos jointEnd = { -113.454, -81.060, 109.328, -119.954, -89.218, 74.302 };
      robot.MoveL(&jointStart, &descStart, 1, 1, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese);
      robot.MoveL(&jointEnd, &descEnd, 1, 1, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese);
      DescPose descREF0A = { 142.135, 367.604, 86.523, 179.728, 1.922, -111.089 };
      JointPos jointREF0A = { -126.794, -100.834, 128.922, -119.864, -89.218, 74.302 };
      DescPose descREF0B = { 254.633, 463.125, 72.604, 179.845, 2.341, -114.704 };
      JointPos jointREF0B = { -130.413, -81.093, 112.044, -123.163, -89.217, 74.303 };
      DescPose descREF1A = { 92.556, 485.259, 47.476, -179.932, 3.130, -97.512 };
      JointPos jointREF1A = { -113.231, -83.815, 119.877, -129.092, -89.217, 74.303 };
      DescPose descREF1B = { 203.103, 583.836, 63.909, 179.991, 2.854, -103.372 };
      JointPos jointREF1B = { -119.088, -69.676, 98.692, -121.761, -89.219, 74.303 };
      rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
      robot.MoveL(&jointREF0A, &descREF0A, 1, 1, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese); //punkt początkowy
      robot.MoveL(&jointREF0B, &descREF0B, 1, 1, 100, 100, 100, -1, &exaxisPos, 1, 0, &offdese); //punkt kierunkowy
      rtn1 = robot.WireSearchWait("REF0");
      rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);
      rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
      robot.MoveL(&jointREF1A, &descREF1A, 1, 1, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese); //punkt początkowy
      robot.MoveL(&jointREF1B, &descREF1B, 1, 1, 100, 100, 100, -1, &exaxisPos, 1, 0, &offdese); //punkt kierunkowy
      rtn1 = robot.WireSearchWait("REF1");
      rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);
      rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
      robot.MoveL(&jointREF0A, &descREF0A, 1, 1, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese); //punkt początkowy
      robot.MoveL(&jointREF0B, &descREF0B, 1, 1, 100, 100, 100, -1, &exaxisPos, 1, 0, &offdese); //punkt kierunkowy
      rtn1 = robot.WireSearchWait("RES0");
      rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);
      rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
      robot.MoveL(&jointREF1A, &descREF1A, 1, 1, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese); //punkt początkowy
      robot.MoveL(&jointREF1B, &descREF1B, 1, 1, 100, 100, 100, -1, &exaxisPos, 1, 0, &offdese); //punkt kierunkowy
      rtn1 = robot.WireSearchWait("RES1");
      rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);
      vector <string> varNameRef = { "REF0", "REF1", "#", "#", "#", "#" };
      vector <string> varNameRes = { "RES0", "RES1", "#", "#", "#", "#" };
      int offectFlag = 0;
      DescPose offectPos = { 0, 0, 0, 0, 0, 0 };
      rtn0 = robot.GetWireSearchOffset(0, 0, varNameRef, varNameRes, offectFlag, offectPos);
      robot.PointsOffsetEnable(0, &offectPos);
      robot.MoveL(&jointStart, &descStart, 1, 1, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese);
      robot.MoveL(&jointEnd, &descEnd, 1, 1, 100, 100, 100, -1, &exaxisPos, 1, 0, &offdese);
      robot.PointsOffsetDisable();
      robot.CloseRPC();
      return 0;

Rozpoczęcie gradientu napięcia spawania
+++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

     /**
    * @brief Rozpoczęcie gradientu napięcia spawania
    * @param [in] IOType Typ sterowania; 0-IO szafy sterowniczej; 1-Protokół komunikacji cyfrowej (UDP); 2-Protokół komunikacji cyfrowej (ModbusTCP)
    * @param [in] voltageStart Początkowe napięcie spawania (V)
    * @param [in] voltageEnd Końcowe napięcie spawania (V)
    * @param [in] AOIndex Numer portu AO szafy sterowniczej (0-1)
    * @param [in] blend Czy wygładzać 0-niewygładzone; 1-wygładzone
    * @return Kod błędu
    */
    errno_t WeldingSetVoltageGradualChangeStart(int IOType, double voltageStart, double voltageEnd, int AOIndex, int blend);

Zakończenie gradientu napięcia spawania
+++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

     /**
      * @brief Zakończenie gradientu napięcia spawania
      * @return Kod błędu
      */
     errno_t WeldingSetVoltageGradualChangeEnd();

Rozpoczęcie gradientu prądu spawania
++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

     /**
      * @brief Rozpoczęcie gradientu prądu spawania
      * @param [in] IOType Typ sterowania; 0-IO szafy sterowniczej; 1-Protokół komunikacji cyfrowej (UDP); 2-Protokół komunikacji cyfrowej (ModbusTCP)
      * @param [in] voltageStart Początkowy prąd spawania (A)
      * @param [in] voltageEnd Końcowy prąd spawania (A)
      * @param [in] AOIndex Numer portu AO szafy sterowniczej (0-1)
      * @param [in] blend Czy wygładzać 0-niewygładzone; 1-wygładzone
      * @return Kod błędu
      */
     errno_t WeldingSetCurrentGradualChangeStart(int IOType, double currentStart, double currentEnd, int AOIndex, int blend);

Zakończenie gradientu prądu spawania
++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
     * @brief Zakończenie gradientu prądu spawania
     * @return Kod błędu
     */
    errno_t WeldingSetCurrentGradualChangeEnd();

Przykład kodu gradientu prądu i napięcia spawania robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int WeldparamChange(FRRobot* robot)
    {
      DescPose startdescPose = { -484.707, 276.996, -14.013, -37.657, -40.508, -1.548 };
      JointPos startjointPos = { -45.421, -75.673, 93.627, -104.302, -87.938, 6.005 };

      DescPose enddescPose = { -508.767, 137.109, -13.966, -37.639, -40.508, -1.559 };
      JointPos endjointPos = { -32.768, -80.947, 100.254, -106.201, -87.201, 18.648 };

      DescPose safedescPose = { -484.709, 294.436, 13.621, -37.660, -40.508, -1.545 };
      JointPos safejointPos = { -46.604, -75.410, 89.109, -100.003, -88.012, 4.823 };
      ExaxisPos exaxisPos = { 0, 0, 0, 0 };
      DescPose offdese = { 0, 0, 0, 0, 0, 0 };

      robot->WeldingSetCurrentRelation(0, 495, 1, 10, 0);
      robot->WeldingSetVoltageRelation(10, 45, 1, 10, 1);
      robot->MoveJ(&safejointPos, &safedescPose, 1, 0, 5, 100, 100, &exaxisPos, -1, 0, &offdese);
      int rtn = robot->WeldingSetCurrentGradualChangeStart(0, 260, 220, 0, 0);
      cout << "WeldingSetCurrentGradualChangeStart rtn is " << rtn << endl;
      rtn = robot->WeldingSetVoltageGradualChangeStart(0, 25, 22, 1, 0);
      cout << "WeldingSetVoltageGradualChangeStart rtn is " << rtn << endl;
      rtn = robot->ArcWeldTraceControl(1, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);
      cout << "ArcWeldTraceControl rtn is " << rtn << endl;
      robot->MoveJ(&startjointPos, &startdescPose, 1, 0, 5, 100, 100, &exaxisPos, -1, 0, &offdese);

      robot->ARCStart(0, 0, 10000);
      robot->WeaveStart(0);
      robot->WeaveChangeStart(2, 1, 24, 36);
      robot->MoveL(&endjointPos, &enddescPose, 1, 0, 100, 100, 2, -1, &exaxisPos, 0, 0, &offdese);
      robot->ARCEnd(0, 0, 10000);
      robot->WeaveChangeEnd();
      robot->WeaveEnd(0);
      robot->ArcWeldTraceControl(0, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);
      robot->WeldingSetCurrentGradualChangeEnd();
      robot->WeldingSetVoltageGradualChangeEnd();
      return 0;
    }

Ustawianie niestandardowych parametrów wahadła
++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia niestandardowe parametry wahadła
    * @param [in] id Niestandardowy numer wahadła: 0-2
    * @param [in] pointNum Liczba punktów wahadła 0-10
    * @param [in] point Dane punktów ruchu x, y, z
    * @param [in] stayTime Czas postoju wahadła ms
    * @param [in] frequency Częstotliwość wahadła Hz
    * @param [in] incStayType Tryb oczekiwania: 0-cykl nie zawiera czasu oczekiwania; 1-cykl zawiera czas oczekiwania
    * @param [in] stationary Oczekiwanie na pozycji wahadła: 0-kontynuuj ruch w czasie oczekiwania; 1-pozycja nieruchoma w czasie oczekiwania
    * @return Kod błędu
    */
    errno_t CustomWeaveSetPara(int id, int pointNum, DescTran point[10], double stayTime[10], double frequency, int incStayType, int stationary);

Pobieranie niestandardowych parametrów wahadła
++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera niestandardowe parametry wahadła
    * @param [in] id Niestandardowy numer wahadła: 0-2
    * @param [out] pointNum Liczba punktów wahadła 0-10
    * @param [out] point Dane punktów ruchu x, y, z
    * @param [out] stayTime Czas postoju wahadła ms
    * @param [out] frequency Częstotliwość wahadła Hz
    * @param [out] incStayType Tryb oczekiwania: 0-cykl nie zawiera czasu oczekiwania; 1-cykl zawiera czas oczekiwania
    * @param [out] stationary Oczekiwanie na pozycji wahadła: 0-kontynuuj ruch w czasie oczekiwania; 1-pozycja nieruchoma w czasie oczekiwania
    * @return Kod błędu
    */
    errno_t CustomWeaveGetPara(int id, int& pointNum, DescTran point[10], double stayTime[10], double& frequency, int& incStayType, int& stationary);

Przykład kodu niestandardowych parametrów wahadła
+++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    int TestCustomWeaveSetPara()
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
      DescTran point[10] = {};
      point[0].x = -3;
      point[0].y = -3;
      point[0].z = 0;
      point[1].x = -6;
      point[1].y = 0;
      point[1].z = 0;
      point[2].x = -3;
      point[2].y = 3;
      point[2].z = 0;
      point[3].x = 0;
      point[3].y = 0;
      point[3].z = 0;
      double stayTime[10] = { 0,0,0,0,0,0,0,0,0,0 };
      rtn = robot.CustomWeaveSetPara(2, 4, point, stayTime, 1.000, 0, 0);
      printf("CustomWeaveSetPara rtn is %d\n", rtn);
      robot.Sleep(1000);
      int pointNum = 0;
      double frequency;
      int incStayType;
      int stationary;
      robot.CustomWeaveGetPara(2, pointNum, point, stayTime, frequency, incStayType, stationary);
      printf("pointNum is %d\n", pointNum);
      for (int i = 0; i < pointNum; i++)
      {
        printf("point %d, point x y z %f %f %f\n", i, point[i].x, point[i].y, point[i].z);
      }
      printf("fre is %f, stay is %d %d \n", frequency, incStayType, stationary);
      robot.WeaveSetPara(0, 9, 1.000000, 1, 5.000000, 6.000000, 5.000000, 50, 100, 100, 0, 1, 0.000000, 0.000000);
      DescPose desc_p1 = { -288.650, 367.807, 288.404, 0.000, -0.001, 0.001 };
      DescPose desc_p2 = { -431.714, 367.815, 288.415, 0.001, 0.001, 0.000 };
      DescPose desc_p3 = { -348.666, 427.798, 288.404, -0.000, -0.000, 0.001 };
      JointPos j1 = { 140.656, -84.560, -91.707, -93.734, 90.000, 50.655 };
      JointPos j2 = { 149.873, -98.298, -77.599, -94.103, 90.000, 59.873 };
      JointPos j3 = { 139.773, -96.173, -80.014, -93.814, 90.000, 49.772 };
      ExaxisPos epos = {};
      DescPose offset_pos = {};
      robot.MoveJ(&j1, &desc_p1, 3, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
      robot.WeaveStart(0);
      robot.Circle(&j3, &desc_p3, 3, 0, 100, 100, &epos, &j2, &desc_p2, 3, 0, 100, 100, &epos, 10, -1, &offset_pos);
      robot.WeaveEnd(0);
      robot.MoveJ(&j1, &desc_p1, 3, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
      robot.WeaveStart(0);
      robot.MoveC(&j3, &desc_p3, 3, 0, 100, 100, &epos, 0, &offset_pos, &j2, &desc_p2, 3, 0, 100, 100, &epos, 0, &offset_pos, 10, -1);
      robot.WeaveEnd(0);
      robot.MoveJ(&j1, &desc_p1, 3, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
      robot.WeaveStart(0);
      robot.MoveL(&j2, &desc_p2, 3, 0, 100, 100, 10, -1, &epos, 0, 0, &offset_pos, 0, 100);
      robot.WeaveEnd(0);
      robot.CloseRPC();
    }

Konfiguracja parametrów spawarki laserowej
++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Konfiguracja parametrów spawarki laserowej
    * @param[in] io_type Typ komunikacji 0-IO 1-UDP
    * @param[in] num Numer grupy do ustawienia (1~10)
    * @param[in] scanSpeed Prędkość skanowania
    * @param[in] scanWidth Szerokość skanowania
    * @param[in] peakPower Moc szczytowa
    * @param[in] dutyCycle Współczynnik wypełnienia
    * @param[in] freq Częstotliwość
    * @return Kod błędu
    */
    errno_t SetLaserWeldingParam(int io_type, int num, int scanSpeed, int scanWidth, int peakPower, int dutyCycle, int freq);

Ustawianie rozpoczęcia/zatrzymania spawania laserowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawianie rozpoczęcia/zatrzymania spawania laserowego
    * @param[in] io_type Typ komunikacji 0-IO 1-UDP
    * @param[in] status Słowo sterujące 0-zatrzymaj emisję 1-rozpocznij emisję
    * @param[in] max_waittime Maksymalny czas oczekiwania, jednostka milisekundy, domyślnie 10000
    * @return Kod błędu
    */
    errno_t SetLaserWeldingStartEnd(int io_type, int status, int max_waittime = 10000);

Włączanie/wyłączanie spawarki laserowej
+++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Włączanie/wyłączanie spawarki laserowej
    * @param[in] io_type Typ komunikacji 0-IO 1-UDP
    * @param[in] status 0-wyłącz 1-włącz
    * @return Kod błędu
    */
    errno_t SetLaserWeldingEnable(int io_type, int status);

Resetowanie usterki spawarki laserowej
++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Resetowanie usterki spawarki laserowej
    * @param[in] io_type Typ komunikacji 0-IO 1-UDP
    * @param[in] status Słowo sterujące 0-nieważne 1-reset usterki
    * @return Kod błędu
    */
    errno_t ResetLaserWeldingErr(int io_type, int status);

Pobieranie stanu pracy spawarki laserowej
+++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobieranie stanu pracy spawarki laserowej
    * @param[in] io_type Typ komunikacji 0-IO 1-UDP
    * @param[out] status Słowo sterujące 0-zatrzymana 1-pracuje
    * @return Kod błędu
    */
    errno_t GetLaserWeldingRunningState(int io_type, int& status);

Pobieranie stanu usterki spawarki laserowej
+++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobieranie stanu usterki spawarki laserowej
    * @param[in] io_type Typ komunikacji 0-IO 1-UDP
    * @param[out] status 0-brak usterki 1-istnieje usterka
    * @return Kod błędu
    */
    errno_t GetLaserWeldingErrState(int io_type, int& status);

Pobieranie parametrów konfiguracyjnych spawarki laserowej
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobieranie parametrów konfiguracyjnych spawarki laserowej
    * @param[in] num Numer grupy do ustawienia (1~10)
    * @param[out] scanSpeed Prędkość skanowania
    * @param[out] scanWidth Szerokość skanowania
    * @param[out] peakPower Moc szczytowa
    * @param[out] dutyCycle Współczynnik wypełnienia
    * @param[out] freq Częstotliwość
    * @return Kod błędu
    */
    errno_t GetLaserWeldingParamTarget(int num, int& scanSpeed, int& scanWidth, int& peakPower, int& dutyCycle, int& freq);

Pobieranie aktualnie obowiązujących parametrów konfiguracyjnych spawarki laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobieranie aktualnie obowiązujących parametrów konfiguracyjnych spawarki laserowej
    * @param[in] io_type Typ komunikacji 0-IO 1-UDP
    * @param[out] scanSpeed Prędkość skanowania
    * @param[out] scanWidth Szerokość skanowania
    * @param[out] peakPower Moc szczytowa
    * @param[out] dutyCycle Współczynnik wypełnienia
    * @param[out] freq Częstotliwość
    * @return Kod błędu, 0 oznacza sukces, niezerowy oznacza niepowodzenie
    */
    errno_t GetLaserWeldingParamActual(int io_type, int& scanSpeed, int& scanWidth, int& peakPower, int& dutyCycle, int& freq);

Konfiguracja rozszerzonego portu DO włączania spawarki laserowej przez IO
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Konfiguracja rozszerzonego portu DO włączania spawarki laserowej przez IO
    * @param[in] ctrlModeDONum Numer rozszerzonego portu DO włączania spawarki laserowej
    * @return Kod błędu, 0 oznacza sukces, niezerowy oznacza niepowodzenie
    */
    errno_t SetLaserWeldingEnableExtDoNum(int ctrlModeDONum);

Konfiguracja rozszerzonego portu DO uruchamiania spawarki laserowej przez IO
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Konfiguracja rozszerzonego portu DO uruchamiania spawarki laserowej przez IO
    * @param[in] ctrlModeDONum Numer rozszerzonego portu DO uruchamiania spawarki laserowej (rozpoczęcie/zakończenie emisji)
    * @return Kod błędu, 0 oznacza sukces, niezerowy oznacza niepowodzenie
    */
    errno_t SetLaserWeldingStartExtDoNum(int ctrlModeDONum);

Konfiguracja rozszerzonego portu DO resetowania usterki spawarki laserowej przez IO
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Konfiguracja rozszerzonego portu DO resetowania usterki spawarki laserowej przez IO
    * @param[in] ctrlModeDONum Numer rozszerzonego portu DO resetowania usterki spawarki laserowej
    * @return Kod błędu, 0 oznacza sukces, niezerowy oznacza niepowodzenie
    */
    errno_t SetLaserWeldingErrResetExtDoNum(int ctrlModeDONum);

Konfiguracja rozszerzonego portu DI stanu pracy (stanu emisji) spawarki laserowej przez IO
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Konfiguracja rozszerzonego portu DI stanu pracy (stanu emisji) spawarki laserowej przez IO
    * @param[in] diNum Konfiguracja rozszerzonego portu DI stanu pracy (stanu emisji) spawarki laserowej
    * @return Kod błędu, 0 oznacza sukces, niezerowy oznacza niepowodzenie
    */
    errno_t SetLaserWeldingRunningStateExtDiNum(int diNum);

Konfiguracja rozszerzonego portu DI stanu usterki spawarki laserowej przez IO
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Konfiguracja rozszerzonego portu DI stanu usterki spawarki laserowej przez IO
    * @param[in] diNum Konfiguracja rozszerzonego portu DI stanu usterki spawarki laserowej
    * @return Kod błędu, 0 oznacza sukces, niezerowy oznacza niepowodzenie
    */
    errno_t SetLaserWeldingErrStateExtDiNum(int diNum);

Przykład kodu spawania laserowego
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestLaserWeld()
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
        rtn = robot.ExtDevLoadUDPDriver();
        if (rtn != 0)
        {
            std::cout << "Failed to load UDP driver, error code: " << rtn << std::endl;
        }
        robot.Sleep(1000);
        rtn = robot.SetLaserWeldingParam(1, 3, 2000, 3, 1500, 100, 1000);
        if (rtn != 0)
        {
            std::cout << "SetLaserWeldingParam failed, error code: " << rtn << std::endl;
        }
        else
        {
            std::cout << "SetLaserWeldingParam success" << std::endl;
        }
        rtn = robot.SetLaserWeldingStartExtDoNum(1);
        if (rtn != 0)
        {
            std::cout << "SetLaserWeldingStartExtDoNum failed, error code: " << rtn << std::endl;
        }
        rtn = robot.Mode(0);
        if (rtn != 0)
        {
            std::cout << "Set mode 0 failed, error code: " << rtn << std::endl;
        }
        robot.Sleep(1000);
        DescPose desc_pos1(-303.721, -206.960, 297.105, 152.209, 19.857, 109.166);
        DescPose desc_pos2(-301.575, -254.888, 284.786, 155.919, 26.946, 111.629);
        DescPose desc_safe(-344.386, -280.830, 435.073, 173.835, 15.333, 124.931);
        JointPos jointPos1(9.827, -99.740, 120.088, -78.900, -77.241, -17.904);
        JointPos jointPos2(15.251, -96.456, 120.138, -84.664, -68.542, -17.843);
        JointPos jointSafe(19.142, -98.078, 101.493, -83.078, -77.070, -17.794);
        ExaxisPos exaxis(0.0, 0.0, 0.0, 0.0);
        DescPose offset(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);
        int error = robot.MoveL(&desc_pos1,0, 0, 100, 100, 100, -1, 0, &exaxis, 0, 0, &offset, -1, 0);
        std::cout << "MoveL to pos1 return: " << error << std::endl;
        rtn = robot.SetLaserWeldingStartEnd(1, 1, 10000);
        if (rtn != 0)
        {
            std::cout << "SetLaserWeldingStartEnd (start) failed, error code: " << rtn << std::endl;
        }
        else
        {
            std::cout << "Laser started" << std::endl;
        }
        rtn = robot.MoveL(&desc_pos2,0, 0, 30, 100, 100, -1, 0, &exaxis, 0, 0, &offset, -1, 0);
        std::cout << "MoveL to pos2 return: " << rtn << std::endl;
        rtn = robot.SetLaserWeldingStartEnd(1, 0, 10000);
        if (rtn != 0)
        {
            std::cout << "SetLaserWeldingStartEnd (stop) failed, error code: " << rtn << std::endl;
        }
        else
        {
            std::cout << "Laser stopped" << std::endl;
        }
        robot.Sleep(500);
        rtn = robot.MoveL(&desc_safe, 0, 0, 100, 100, 100, -1, 0, &exaxis, 0, 0, &offset, -1, 0);
        std::cout << "MoveL to safe_pos return: " << rtn << std::endl;
        rtn = robot.Mode(1);
        if (rtn != 0)
        {
            std::cout << "Set mode 1 failed, error code: " << rtn << std::endl;
        }
        robot.Sleep(1000);
        robot.CloseRPC();
        robot.Sleep(1000);
        std::cout << "Test completed" << std::endl;
        return 0;
    }