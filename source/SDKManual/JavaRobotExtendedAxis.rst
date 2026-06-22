Oś rozszerzona
==============

.. toctree::
    :maxdepth: 5

Ustawianie parametrów osi rozszerzonej 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia parametry osi rozszerzonej 485
    * @param [in] servoId ID serwonapędu, zakres [1-16], odpowiada ID stacji podrzędnej
    * @param [in] param Parametry osi rozszerzonej 485
    * @return Kod błędu
    */
    int AuxServoSetParam(int servoId, Axis485Param param)

Pobieranie parametrów osi rozszerzonej 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera parametry konfiguracyjne osi rozszerzonej 485
    * @param [in] servoId ID serwonapędu, zakres [1-16], odpowiada ID stacji podrzędnej
    * @param [out] param Parametry osi rozszerzonej 485
    * @return Kod błędu
    */
    int AuxServoGetParam(int servoId, Axis485Param param);

Włączanie/wyłączanie zasilania osi rozszerzonej 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Włącza/wyłącza zasilanie osi rozszerzonej 485
    * @param [in] servoId ID serwonapędu, zakres [1-16], odpowiada ID stacji podrzędnej
    * @param [in] status Stan zasilania, 0-wyłączone, 1-włączone
    * @return Kod błędu
    */
    int AuxServoEnable(int servoId, int status);

Ustawianie trybu sterowania osi rozszerzonej 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia tryb sterowania osi rozszerzonej 485
    * @param [in] servoId ID serwonapędu, zakres [1-16], odpowiada ID stacji podrzędnej
    * @param [in] mode Tryb sterowania, 0-tryb pozycyjny, 1-tryb prędkościowy
    * @return Kod błędu
    */
    int AuxServoSetControlMode(int servoId, int mode);

Ustawianie pozycji docelowej osi rozszerzonej 485 (tryb pozycyjny)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia pozycję docelową osi rozszerzonej 485 (tryb pozycyjny)
    * @param [in] servoId ID serwonapędu, zakres [1-16], odpowiada ID stacji podrzędnej
    * @param [in] pos Pozycja docelowa, mm lub °
    * @param [in] speed Prędkość docelowa, mm/s lub °/s
    * @param [in] acc Procent przyspieszenia [0-100]
    * @return Kod błędu
    */
    int AuxServoSetTargetPos(int servoId, double pos, double speed, double acc);

Ustawianie momentu obrotowego docelowego osi rozszerzonej 485 (tryb momentowy) - tymczasowo niedostępne
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia moment obrotowy docelowy osi rozszerzonej 485 (tryb momentowy) - tymczasowo niedostępne
    * @param [in] servoId ID serwonapędu, zakres [1-16], odpowiada ID stacji podrzędnej
    * @param [in] torque Moment docelowy, Nm
    * @return Kod błędu
    */
    int AuxServoSetTargetTorque(int servoId, double torque);

Ustawianie powrotu do zera osi rozszerzonej 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia powrót do zera osi rozszerzonej 485
    * @param [in] servoId ID serwonapędu, zakres [1-16], odpowiada ID stacji podrzędnej
    * @param [in] mode Tryb powrotu do zera, 1-powrót do bieżącej pozycji; 2-powrót do ujemnego ogranicznika; 3-powrót do dodatniego ogranicznika
    * @param [in] searchVel Prędkość poszukiwania zera, mm/s lub °/s
    * @param [in] latchVel Prędkość zatrzaskiwania zera, mm/s lub °/s
    * @param [in] acc Procent przyspieszenia [0-100]
    * @return Kod błędu
    */
    int AuxServoHoming(int servoId, int mode, double searchVel, double latchVel);

Czyszczenie informacji o błędzie osi rozszerzonej 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Czyści informacje o błędzie osi rozszerzonej 485
    * @param [in] servoId ID serwonapędu, zakres [1-16], odpowiada ID stacji podrzędnej
    * @return Kod błędu
    */
    int AuxServoClearError(int servoId);

Pobieranie stanu serwonapędu osi rozszerzonej 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera stan serwonapędu osi rozszerzonej 485
    * @param [in] servoId ID serwonapędu, zakres [1-16], odpowiada ID stacji podrzędnej
    * @param [in] servoErrCode Kod błędu serwonapędu
    * @param [in] servoState Stan serwonapędu bit0:0-niewłączony; 1-włączony; bit1:0-nie w ruchu; 1-w ruchu; bit4:0-nie ukończono pozycjonowania; 1-ukończono pozycjonowanie; bit5:0-nie wyzerowano; 1-wyzerowano
    * @param [in] servoPos Bieżąca pozycja serwonapędu mm lub °
    * @param [in] servoSpeed Bieżąca prędkość serwonapędu mm/s lub °/s
    * @param [in] servoTorque Bieżący moment obrotowy serwonapędu Nm
    * @return Kod błędu
    */
    int AuxServoGetStatus(int servoId, int[] servoErrCode, int[] servoState, double[] servoPos, double[] servoSpeed, double[] servoTorque)

Ustawianie prędkości docelowej osi rozszerzonej 485 (tryb prędkościowy)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia prędkość docelową osi rozszerzonej 485 (tryb prędkościowy)
    * @param [in] servoId ID serwonapędu, zakres [1-16], odpowiada ID stacji podrzędnej
    * @param [in] speed Prędkość docelowa, mm/s lub °/s
    * @param [in] acc Procent przyspieszenia [0-100]
    * @return Kod błędu
    */
    int AuxServoSetTargetSpeed(int servoId, double speed, double acc);

Ustawianie numeru osi danych osi rozszerzonej 485 w sprzężeniu zwrotnym stanu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia numer osi danych osi rozszerzonej 485 w sprzężeniu zwrotnym stanu
    * @param [in] servoId ID serwonapędu, zakres [1-16], odpowiada ID stacji podrzędnej
    * @return Kod błędu
    */
    int AuxServosetStatusID(int servoId);

Ustawianie przyspieszenia i opóźnienia ruchu osi rozszerzonej 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia przyspieszenie i opóźnienie ruchu osi rozszerzonej 485
    * @param [in] acc Przyspieszenie ruchu osi rozszerzonej 485
    * @param [in] dec Opóźnienie ruchu osi rozszerzonej 485
    * @return Kod błędu
    */
    int AuxServoSetAcc(double acc, double dec)

Ustawianie przyspieszenia i opóźnienia awaryjnego zatrzymania osi rozszerzonej 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia przyspieszenie i opóźnienie awaryjnego zatrzymania osi rozszerzonej 485
    * @param [in] acc Przyspieszenie awaryjnego zatrzymania osi rozszerzonej 485
    * @param [in] dec Opóźnienie awaryjnego zatrzymania osi rozszerzonej 485
    * @return Kod błędu
    */
    int AuxServoSetEmergencyStopAcc(double acc, double dec)

Pobieranie przyspieszenia i opóźnienia ruchu osi rozszerzonej 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera przyspieszenie i opóźnienie ruchu osi rozszerzonej 485
    * @return List[0]:kod błędu; List[1]:przyspieszenie ruchu osi rozszerzonej 485; List[2]:opóźnienie ruchu osi rozszerzonej 485
    */
    List<Number> AuxServoGetAcc()

Pobieranie przyspieszenia i opóźnienia awaryjnego zatrzymania osi rozszerzonej 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera przyspieszenie i opóźnienie awaryjnego zatrzymania osi rozszerzonej 485
    * @return List[0]:kod błędu; List[1]:przyspieszenie awaryjnego zatrzymania osi rozszerzonej 485; List[2]:opóźnienie awaryjnego zatrzymania osi rozszerzonej 485
    */
    List<Number> AuxServoGetEmergencyStopAcc()

Przykład kodu sterowania osią rozszerzoną
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int Test485Auxservo(Robot robot)
    {
        Axis485Param ax=new Axis485Param(1, 1, 1, 131072, 15.45);
        int retval = robot.AuxServoSetParam(1, ax);

        Axis485Param ax2=new Axis485Param();
        retval = robot.AuxServoGetParam(1, ax2);

        ax.servoCompany=10;
        ax.servoModel=11;
        ax.servoSoftVersion=12;
        ax.servoResolution=13;
        ax.axisMechTransRatio=14;

        retval = robot.AuxServoSetParam(1, ax);

        retval = robot.AuxServoGetParam(1,ax2);

        ax.servoCompany=1;
        ax.servoModel=1;
        ax.servoSoftVersion=1;
        ax.servoResolution=131072;
        ax.axisMechTransRatio=36;

        retval = robot.AuxServoSetParam(1, ax);
        robot.Sleep(3000);

        robot.AuxServoSetAcc(3000, 3000);
        robot.AuxServoSetEmergencyStopAcc(5000, 5000);
        robot.Sleep(1000);
        double emagacc = 0, acc = 0;
        double emagdec = 0, dec = 0;

        List<Number> aux=new ArrayList<>();

        aux=robot.AuxServoGetEmergencyStopAcc();
        aux=robot.AuxServoGetAcc();

        robot.AuxServoSetControlMode(1, 0);
        robot.Sleep(2000);

        retval = robot.AuxServoEnable(1, 0);
        robot.Sleep(1000);
        int[] servoerrcode =new int[]{0};
        int[] servoErrCode=new int[]{0};
        int[] servoState=new int[]{0};
        double[] servoPos=new double[]{0};
        double[] servoSpeed=new double[]{0};
        double[] servoTorque=new double[]{0};
        retval = robot.AuxServoGetStatus(1, servoErrCode, servoState, servoPos, servoSpeed, servoTorque);
        robot.Sleep(1000);;

        retval = robot.AuxServoEnable(1, 1);
        robot.Sleep(1000);
        retval = robot.AuxServoGetStatus(1, servoErrCode, servoState, servoPos, servoSpeed, servoTorque);
        robot.Sleep(1000);

        retval = robot.AuxServoHoming(1, 1, 5, 1,100);
        robot.Sleep(3000);

        retval = robot.AuxServoSetTargetPos(1, 200, 30,100);
        robot.Sleep(1000);
        retval = robot.AuxServoGetStatus(1, servoErrCode, servoState, servoPos, servoSpeed, servoTorque);
        robot.Sleep(8000);


        robot.AuxServoSetControlMode(1, 1);
        robot.Sleep(2000);

        robot.AuxServoEnable(1, 0);
        robot.Sleep(1000);
        robot.AuxServoEnable(1, 1);
        robot.Sleep(1000);
        robot.AuxServoSetTargetSpeed(1, 100, 80);

        robot.Sleep(5000);
        robot.AuxServoSetTargetSpeed(1, 0, 80);

        robot.CloseRPC();
        return 0;
    }

Konfiguracja parametrów komunikacji UDP dla osi rozszerzonej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-v1.0.5-3.8.2

.. code-block:: Java
    :linenos:

    /**
    * @brief Konfiguruje parametry komunikacji UDP dla osi rozszerzonej
    * @param [in] param Parametry komunikacji
    * @return Kod błędu
    */
    int ExtDevSetUDPComParam(UDPComParam param);

Pobieranie konfiguracji parametrów komunikacji UDP dla osi rozszerzonej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera parametry komunikacji UDP dla osi rozszerzonej
    * @param [out] ip Adres IP PLC
    * @param [out] port Numer portu
    * @param [out] period Okres komunikacji (ms, domyślnie 2, nie modyfikować tego parametru)
    * @param [out] lossPkgTime Czas wykrywania utraty pakietów (ms)
    * @param [out] lossPkgNum Liczba utraconych pakietów
    * @param [out] disconnectTime Czas potwierdzenia przerwania komunikacji
    * @param [out] reconnectEnable Włączenie automatycznego ponownego łączenia po przerwaniu komunikacji 0-nie włączone 1-włączone
    * @param [out] reconnectPeriod Odstęp między próbami ponownego łączenia (ms)
    * @param [out] reconnectNum Liczba prób ponownego łączenia
    * @param [out] selfConnect Czy automatycznie ponownie połączyć po ponownym uruchomieniu szafy sterowniczej; 0-nie łącz ponownie; 1-łącz ponownie
    * @return Kod błędu
    */
    public int ExtDevGetUDPComParam(ref string ip, ref int port, ref int period, ref int lossPkgTime, ref int lossPkgNum, ref int disconnectTime, ref int reconnectEnable, ref int reconnectPeriod, ref int reconnectNum, ref int selfConnect)

Ładowanie komunikacji UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ładuje komunikację UDP
    * @return Kod błędu
    */
    int ExtDevLoadUDPDriver();

Zwolnienie komunikacji UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Zwolnienie komunikacji UDP
    * @return Kod błędu
    */
    int ExtDevUnloadUDPDriver();

Przywracanie połączenia po przerwaniu komunikacji UDP osi rozszerzonej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Przywraca połączenie po przerwaniu komunikacji UDP osi rozszerzonej
    * @return Kod błędu
    */
    int ExtDevUDPClientComReset();

Zamykanie komunikacji po przerwaniu komunikacji UDP osi rozszerzonej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Zamyka komunikację po przerwaniu komunikacji UDP osi rozszerzonej
    * @return Kod błędu
    */
    int ExtDevUDPClientComClose();

Konfiguracja parametrów osi rozszerzonej UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Konfiguruje parametry osi rozszerzonej UDP
    * @param [in] axisID Numer osi
    * @param [in] axisType Typ osi rozszerzonej 0-przesuwna; 1-obrotowa
    * @param [in] axisDirection Kierunek osi rozszerzonej 0-dodatni; 1-ujemny
    * @param [in] axisMax Maksymalna pozycja osi rozszerzonej mm
    * @param [in] axisMin Minimalna pozycja osi rozszerzonej mm
    * @param [in] axisVel Prędkość mm/s
    * @param [in] axisAcc Przyspieszenie mm/s2
    * @param [in] axisLead Skok śruby pociągowej mm
    * @param [in] encResolution Rozdzielczość enkodera
    * @param [in] axisOffect Przesunięcie osi rozszerzonej punktu początkowego spoiny
    * @param [in] axisCompany Producent sterownika 1-Hechuan; 2-Huichuan; 3-Panasonic
    * @param [in] axisModel Model sterownika 1-Hechuan-SV-XD3EA040L-E, 2-Hechuan-SV-X2EA150A-A, 1-Huichuan-SV620PT5R4I, 1-Panasonic-MADLN15SG, 2-Panasonic-MSDLN25SG, 3-Panasonic-MCDLN35SG
    * @param [in] axisEncType Typ enkodera 0-inkrementalny; 1-absolutny
    * @return Kod błędu
    */
    int ExtAxisParamConfig(int axisID, int axisType, int axisDirection, double axisMax, double axisMin, double axisVel, double axisAcc, double axisLead, int encResolution, double axisOffect, int axisCompany, int axisModel, int axisEncType);

Pobieranie parametrów osi rozszerzonej UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera parametry osi rozszerzonej UDP
    * @param  axisID Numer osi rozszerzonej [1-4]
    * @param  params Tablica parametrów wyjściowych, długość 12, kolejność:
    *               [0] axisType Typ osi rozszerzonej 0-przesuwna; 1-obrotowa
    *               [1] axisDirection Kierunek osi rozszerzonej 0-dodatni; 1-ujemny
    *               [2] axisMax Maksymalna pozycja osi rozszerzonej mm
    *               [3] axisMin Minimalna pozycja osi rozszerzonej mm
    *               [4] axisVel Prędkość mm/s
    *               [5] axisAcc Przyspieszenie mm/s2
    *               [6] axisLead Skok śruby pociągowej mm
    *               [7] encResolution Rozdzielczość enkodera
    *               [8] axisOffect Przesunięcie osi rozszerzonej punktu początkowego spoiny
    *               [9] axisCompany Producent sterownika 1-Hechuan; 2-Huichuan; 3-Panasonic
    *               [10] axisModel Model sterownika
    *               [11] axisEncType Typ enkodera 0-inkrementalny; 1-absolutny
    * @return Kod błędu
    */
    public int ExtAxisGetParamConfig(int axisID, Object[] params)

Ustawianie pozycji montażowej osi rozszerzonej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia pozycję montażową osi rozszerzonej
    * @param [in] installType 0-robot zamontowany na osi zewnętrznej, 1-robot zamontowany poza osią zewnętrzną
    * @return Kod błędu
    */
    int SetRobotPosToAxis(int installType);

Ustawianie konfiguracji parametrów DH systemu osi rozszerzonej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia konfigurację parametrów DH systemu osi rozszerzonej
    * @param [in]  axisConfig Konfiguracja osi zewnętrznej, 0-jednokierunkowa prosta szyna szynowa, 1-dwukierunkowy pozycjoner typu L, 2-trójkierunkowa, 3-czterokierunkowa, 4-jednokierunkowy pozycjoner
    * @param [in]  axisDHd1 Parametr DH osi zewnętrznej d1 mm
    * @param [in]  axisDHd2 Parametr DH osi zewnętrznej d2 mm
    * @param [in]  axisDHd3 Parametr DH osi zewnętrznej d3 mm
    * @param [in]  axisDHd4 Parametr DH osi zewnętrznej d4 mm
    * @param [in]  axisDHa1 Parametr DH osi zewnętrznej a1 mm
    * @param [in]  axisDHa2 Parametr DH osi zewnętrznej a2 mm
    * @param [in]  axisDHa3 Parametr DH osi zewnętrznej a3 mm
    * @param [in]  axisDHa4 Parametr DH osi zewnętrznej a4 mm
    * @return Kod błędu
    */
    int SetAxisDHParaConfig(int axisConfig, double axisDHd1, double axisDHd2, double axisDHd3, double axisDHd4, double axisDHa1, double axisDHa2, double axisDHa3, double axisDHa4);

Włączanie zasilania osi rozszerzonej UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Włącza zasilanie osi rozszerzonej UDP
    * @param [in] axisID Numer osi [1-4]
    * @param [in] status 0-wyłączone; 1-włączone
    * @return Kod błędu
    */
    int ExtAxisServoOn(int axisID, int status);

Powrót do zera osi rozszerzonej UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Powrót do zera osi rozszerzonej UDP
    * @param [in] axisID Numer osi [1-4]
    * @param [in] mode Sposób powrotu do zera 0-powrót do bieżącej pozycji, 1-powrót do ujemnego ogranicznika, 2-powrót do dodatniego ogranicznika
    * @param [in] searchVel Prędkość poszukiwania zera (mm/s)
    * @param [in] latchVel Prędkość zatrzaskiwania zera (mm/s)
    * @return Kod błędu
    */
    int ExtAxisSetHoming(int axisID, int mode, double searchVel, double latchVel);

Rozpoczęcie ruchu jałowego osi rozszerzonej UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Rozpoczyna ruch jałowy osi rozszerzonej UDP
    * @param [in] axisID Numer osi [1-4]
    * @param [in] direction Kierunek obrotu 0-przeciwny; 1-zgodny
    * @param [in] vel Prędkość (mm/s)
    * @param [in] acc (Przyspieszenie mm/s2)
    * @param [in] maxDistance Maksymalna odległość ruchu jałowego
    * @return Kod błędu
    */
    int ExtAxisStartJog(int axisID, int direction, double vel, double acc, double maxDistance);

Zatrzymanie ruchu jałowego osi rozszerzonej UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Zatrzymuje ruch jałowy osi rozszerzonej UDP
    * @param [in] axisID Numer osi [1-4]
    * @return Kod błędu
    */
    int ExtAxisStopJog(int axisID);

Przykład kodu konfiguracji i ruchu jałowego osi rozszerzonej UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestUDPAxis(Robot robot) {
        int rtn = -1;

        UDPComParam param = new UDPComParam("192.168.58.88", 2021, 2, 100, 3, 200, 1, 100, 5, 1);
        rtn = robot.ExtDevSetUDPComParam(param);
        System.out.println("ExtDevSetUDPComParam rtn is " + rtn);

        UDPComParam getParam = new UDPComParam();
        rtn = robot.ExtDevGetUDPComParam(getParam);
        String paramStr = "\nip " + getParam.ip + "\nport " + getParam.port + "\nperiod " + getParam.period +
                "\nlossPkgTime " + getParam.lossPkgTime + "\nlossPkgNum " + getParam.lossPkgNum +
                "\ndisconnectTime " + getParam.disconnectTime + "\nreconnectEnable " + getParam.reconnectEnable +
                "\nreconnectPeriod " + getParam.reconnectPeriod + "\nreconnectNum " + getParam.reconnectNum +
                "\nselfConnect " + getParam.selfConnect;
        System.out.println("ExtDevGetUDPComParam rtn is " + rtn + paramStr);

        robot.ExtDevLoadUDPDriver();

        rtn = robot.SetExAxisCmdDoneTime(5000.0);
        System.out.println("SetExAxisCmdDoneTime rtn is " + rtn);

        rtn = robot.ExtAxisServoOn(1, 1);
        System.out.println("ExtAxisServoOn axis id 1 rtn is " + rtn);
        rtn = robot.ExtAxisServoOn(2, 1);
        System.out.println("ExtAxisServoOn axis id 2 rtn is " + rtn);
        robot.Sleep(2000);

        robot.ExtAxisSetHoming(1, 0, 10, 2);
        robot.Sleep(2000);
        rtn = robot.ExtAxisSetHoming(2, 0, 10, 2);
        System.out.println("ExtAxisSetHoming rtn is " + rtn);

        robot.Sleep(4000);

        rtn = robot.SetRobotPosToAxis(1);
        System.out.println("SetRobotPosToAxis rtn is " + rtn);

        rtn = robot.SetAxisDHParaConfig(10, 20, 0, 0, 0, 0, 0, 0, 0);
        System.out.println("SetAxisDHParaConfig rtn is " + rtn);

        rtn = robot.ExtAxisParamConfig(1, 1, 1, 1000, -1000, 1000, 1000, 1.905, 262144, 200, 1, 0, 0);
        System.out.println("ExtAxisParamConfig axis 1 rtn is " + rtn);

        Object[] params1 = new Object[12];
        rtn = robot.ExtAxisGetParamConfig(1, params1);
        System.out.printf("axis id 1 ExtAxisGetParamConfig : axisType %d, axisDirection %d, axisMax %.2f, axisMin %.2f, axisVel %.2f, axisAcc %.2f, axisLead %.2f, encResolution %d, axisOffect %.2f, axisCompany %d, axisModel %d, axisEncType %d\n",
                (int)params1[0], (int)params1[1], (double)params1[2], (double)params1[3],
                (double)params1[4], (double)params1[5], (double)params1[6], (int)params1[7],
                (double)params1[8], (int)params1[9], (int)params1[10], (int)params1[11]);

        rtn = robot.ExtAxisParamConfig(2, 1, 1, 1000, -1000, 1000, 1000, 4.444, 262144, 200, 1, 0, 0);
        System.out.println("ExtAxisParamConfig axis 2 rtn is " + rtn);

        Object[] params2 = new Object[12];
        rtn = robot.ExtAxisGetParamConfig(2, params2);
        System.out.printf("axis id 2 ExtAxisGetParamConfig : axisType %d, axisDirection %d, axisMax %.2f, axisMin %.2f, axisVel %.2f, axisAcc %.2f, axisLead %.2f, encResolution %d, axisOffect %.2f, axisCompany %d, axisModel %d, axisEncType %d\n",
                (int)params2[0], (int)params2[1], (double)params2[2], (double)params2[3],
                (double)params2[4], (double)params2[5], (double)params2[6], (int)params2[7],
                (double)params2[8], (int)params2[9], (int)params2[10], (int)params2[11]);

        robot.Sleep(3000);

        robot.ExtAxisStartJog(1, 0, 10, 10, 30);
        robot.Sleep(1000);
        robot.ExtAxisStopJog(1);
        robot.Sleep(3000);
        robot.ExtAxisServoOn(1, 0);

        robot.Sleep(3000);

        robot.ExtAxisStartJog(2, 0, 10, 10, 30);
        robot.Sleep(1000);
        robot.ExtAxisStopJog(2);
        robot.Sleep(3000);
        robot.ExtAxisServoOn(2, 0);
        robot.ExtDevUnloadUDPDriver();

        return 0;
    }

Ustawianie punktu odniesienia układu współrzędnych osi rozszerzonej - metoda czterech punktów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia punkt odniesienia układu współrzędnych osi rozszerzonej - metoda czterech punktów
    * @param [in]  pointNum Numer punktu [1-4]
    * @return Kod błędu
    */
    int ExtAxisSetRefPoint(int pointNum);

Obliczanie układu współrzędnych osi rozszerzonej - metoda czterech punktów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Oblicza układ współrzędnych osi rozszerzonej - metoda czterech punktów
    * @param [out]  coord Wartości układu współrzędnych
    * @return Kod błędu
    */
    int ExtAxisComputeECoordSys(DescPose coord);

Ustawianie punktu odniesienia układu współrzędnych pozycjonera
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia punkt odniesienia układu współrzędnych pozycjonera
    * @param [in]  pointNum Numer punktu [1-4]
    * @return Kod błędu
    */
    int PositionorSetRefPoint(int pointNum);

Obliczanie układu współrzędnych pozycjonera - metoda czterech punktów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Oblicza układ współrzędnych pozycjonera - metoda czterech punktów
    * @param [out] coord Wartości układu współrzędnych
    * @return Kod błędu
    */
    int PositionorComputeECoordSys(DescPose coord);

Ustawianie pozy i orientacji punktu odniesienia kalibracji w układzie współrzędnych końcówki pozycjonera
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia pozy i orientację punktu odniesienia kalibracji w układzie współrzędnych końcówki pozycjonera
    * @param [in] pos Wartości pozy i orientacji
    * @return Kod błędu
    */
    int SetRefPointInExAxisEnd(DescPose pos);

Stosowanie układu współrzędnych osi rozszerzonej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Stosuje układ współrzędnych osi rozszerzonej
    * @param [in]  applyAxisId Numer osi rozszerzonej bit0-bit3 odpowiada numerom osi rozszerzonej 1-4, np. zastosowanie osi rozszerzonych 1 i 3 to 0b 0000 0101; czyli 5
    * @param [in]  axisCoordNum Numer układu współrzędnych osi rozszerzonej
    * @param [in]  coord Wartości układu współrzędnych
    * @param [in]  calibFlag Flaga kalibracji 0-nie, 1-tak
    * @return Kod błędu
    */
    int ExtAxisActiveECoordSys(int applyAxisId, int axisCoordNum, DescPose coord, int calibFlag);

Pobieranie układu współrzędnych osi rozszerzonej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.5-3.8.2

.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera układ współrzędnych osi rozszerzonej
    * @param [out] coord Układ współrzędnych osi rozszerzonej
    * @return Kod błędu
    */
    int ExtAxisGetCoord(DescPose coord);

Przykład kodu kalibracji układu współrzędnych osi rozszerzonej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestUDPAxisCalib(Robot robot)
    {
        UDPComParam para1=new UDPComParam("192.168.58.88", 2021, 2, 100, 3, 200, 1, 100, 5, 1);

        int rtn = robot.ExtDevSetUDPComParam(para1);
        String ip = ""; int port = 0; int period = 0; int lossPkgTime = 0; int lossPkgNum = 0; int disconnectTime = 0; int reconnectEnable = 0; int reconnectPeriod = 0; int reconnectNum = 0;
        UDPComParam para2=new UDPComParam(ip, port, period, lossPkgTime, lossPkgNum, disconnectTime, reconnectEnable, reconnectPeriod, reconnectNum,0);

        rtn = robot.ExtDevGetUDPComParam(para2);

        robot.ExtDevLoadUDPDriver();

        rtn = robot.ExtAxisServoOn(1, 1);
        rtn = robot.ExtAxisServoOn(2, 1);

        robot.Sleep(4000);

        rtn = robot.SetRobotPosToAxis(1);
        rtn = robot.SetAxisDHParaConfig(1, 128.5, 206.4,  0, 0, 0, 0, 0, 0);
        rtn = robot.ExtAxisParamConfig(1, 1, 1, 1000, -1000, 1000, 1000, 1.905, 262144, 200, 1, 0, 0);
        rtn = robot.ExtAxisParamConfig(2, 1, 1, 1000, -1000, 1000, 1000, 4.444, 262144, 200, 1, 0, 0);

        DescPose toolCoord=new DescPose(0, 0, 210, 0, 0, 0);
        robot.SetToolCoord(1, toolCoord, 0, 0, 1, 0);

        JointPos jSafe=new JointPos(115.193, -96.149, 92.489, -87.068, -89.15, -83.488);
        JointPos j1=new JointPos(117.559, -92.624, 100.329, -96.909, -94.057, -83.488);
        JointPos j2=new JointPos(112.239, -90.096, 99.282, -95.909, -89.824, -83.488);
        JointPos j3=new JointPos(110.839, -83.473, 93.166, -89.22, -90.499, -83.487);
        JointPos j4=new JointPos(107.935, -83.572, 95.424, -92.873, -87.933, -83.488);

        DescPose descSafe =new DescPose(0,0,0,0,0,0);
        DescPose desc1 = new DescPose(0,0,0,0,0,0);
        DescPose desc2 = new DescPose(0,0,0,0,0,0);
        DescPose desc3 = new DescPose(0,0,0,0,0,0);
        DescPose desc4 = new DescPose(0,0,0,0,0,0);
        ExaxisPos exaxisPos =new ExaxisPos(0,0,0,0);
        DescPose offdese =new DescPose(0, 0, 0, 0, 0, 0);

        robot.GetForwardKin(jSafe, descSafe);
        robot.MoveJ(jSafe, descSafe, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.Sleep(2000);

        robot.GetForwardKin(j1, desc1);
        robot.MoveJ(j1, desc1, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.Sleep(2000);

        DescPose actualTCPPos =new DescPose(0,0,0,0,0,0);

        robot.GetActualTCPPose(actualTCPPos);
        robot.SetRefPointInExAxisEnd(actualTCPPos);
        rtn = robot.PositionorSetRefPoint(1);
        robot.Sleep(2000);

        robot.MoveJ(jSafe, descSafe, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.ExtAxisStartJog(1, 0, 50, 50, 10);
        robot.Sleep(1000);
        robot.ExtAxisStartJog(2, 0, 50, 50, 10);
        robot.Sleep(1000);
        robot.GetForwardKin(j2, desc2);
        rtn = robot.MoveJ(j2, desc2, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        rtn = robot.PositionorSetRefPoint(2);
        robot.Sleep(2000);

        robot.MoveJ(jSafe, descSafe, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.ExtAxisStartJog(1, 0, 50, 50, 10);
        robot.Sleep(1000);
        robot.ExtAxisStartJog(2, 0, 50, 50, 10);
        robot.Sleep(1000);
        robot.GetForwardKin(j3, desc3);
        robot.MoveJ(j3, desc3, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        rtn = robot.PositionorSetRefPoint(3);
        robot.Sleep(2000);

        robot.MoveJ(jSafe, descSafe, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.ExtAxisStartJog(1, 0, 50, 50, 10);
        robot.Sleep(1000);
        robot.ExtAxisStartJog(2, 0, 50, 50, 10);
        robot.Sleep(1000);
        robot.GetForwardKin(j4, desc4);
        robot.MoveJ(j4, desc4, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        rtn = robot.PositionorSetRefPoint(4);
        robot.Sleep(2000);

        DescPose axisCoord = new DescPose();
        robot.PositionorComputeECoordSys(axisCoord);
        robot.MoveJ(jSafe, descSafe, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        rtn = robot.ExtAxisActiveECoordSys(3, 1, axisCoord, 1);

        robot.CloseRPC();
        return 0;
    }

Ruch osi rozszerzonej UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:

    /**
    * @brief Ruch osi rozszerzonej UDP
    * @param [in] pos Pozycja docelowa
    * @param [in] ovl Procent prędkości
    * @param [in] blend Parametr wygładzania (mm lub ms)
    * @return Kod błędu
    */
    int ExtAxisMove(ExaxisPos pos, double ovl, double blend)

Przykład kodu ruchu osi rozszerzonej UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestUDPAxisCalib(Robot robot)
    {
        ExaxisPos exaxisPos = new ExaxisPos( 20, 0, 0, 0 );
        robot.ExtAxisMove(exaxisPos,40);
        robot.CloseRPC();
        return 0;
    }

Ruch synchroniczny osi rozszerzonej UDP z ruchem stawowym robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ruch synchroniczny osi rozszerzonej UDP z ruchem stawowym robota
    * @param [in] joint_pos Docelowa pozycja stawów, jednostka deg
    * @param [in] desc_pos Docelowa poza i orientacja w kartezjańskim układzie współrzędnych
    * @param [in] tool Numer narzędzia, zakres [0~14]
    * @param [in] user Numer obiektu, zakres [0~14]
    * @param [in] vel Procent prędkości, zakres [0~100]
    * @param [in] acc Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param [in] ovl Współczynnik skalowania prędkości, zakres [0~100]
    * @param [in] epos Pozycja osi rozszerzonej, jednostka mm
    * @param [in] blendT [-1.0]-ruch do pozycji (blokujący), [0~500.0]-czas wygładzania (nieblokujący), jednostka ms
    * @param [in] offset_flag 0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie obiektu, 2-przesunięcie w układzie narzędzia
    * @param [in] ffset_pos Wartość przesunięcia pozy i orientacji
    * @return Kod błędu
    */
    int ExtAxisSyncMoveJ(JointPos joint_pos, DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, ExaxisPos epos, double blendT, int offset_flag, DescPose offset_pos);

Ruch synchroniczny osi rozszerzonej UDP z ruchem stawowym robota (automatyczne obliczanie prostej kinematyki)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief Ruch synchroniczny osi rozszerzonej UDP z ruchem stawowym robota (automatyczne obliczanie prostej kinematyki)
    * @param [in] joint_pos Docelowa pozycja stawów, jednostka deg
    * @param [in] tool Numer narzędzia, zakres [0~14]
    * @param [in] user Numer obiektu, zakres [0~14]
    * @param [in] vel Procent prędkości, zakres [0~100]
    * @param [in] acc Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param [in] ovl Współczynnik skalowania prędkości, zakres [0~100]
    * @param [in] epos Pozycja osi rozszerzonej, jednostka mm
    * @param [in] blendT [-1.0]-ruch do pozycji (blokujący), [0~500.0]-czas wygładzania (nieblokujący), jednostka ms
    * @param [in] offset_flag 0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie obiektu, 2-przesunięcie w układzie narzędzia
    * @param [in] offset_pos Wartość przesunięcia pozy i orientacji
    * @return Kod błędu
    */
    int ExtAxisSyncMoveJ(JointPos joint_pos, int tool, int user, double vel, double acc, double ovl, ExaxisPos epos, double blendT, int offset_flag, DescPose offset_pos)

Przykład kodu ruchu synchronicznego z ruchem stawowym robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public int testSyncMoveJ(Robot robot)
    {
        //1. Kalibracja i zastosowanie układu współrzędnych narzędzia robota. Możesz użyć metody czterech lub sześciu punktów do kalibracji i zastosowania układu współrzędnych narzędzia. Interfejsy związane z kalibracją układu współrzędnych narzędzia są następujące:
        //  int SetToolPoint(int point_num); //Ustawia punkt odniesienia narzędzia - metoda sześciu punktów
        //  int ComputeTool(ref DescPose tcp_pose); //Oblicza układ współrzędnych narzędzia
        //  int SetTcp4RefPoint(int point_num);  //Ustawia punkt odniesienia narzędzia - metoda czterech punktów
        //  int ComputeTcp4(ref DescPose tcp_pose);  //Oblicza układ współrzędnych narzędzia - metoda czterech punktów
        //  int SetToolCoord(int id, DescPose coord, int type, int install); //Ustawia i stosuje układ współrzędnych narzędzia
        //  int SetToolList(int id, DescPose coord, int type, int install);  //Ustawia i stosuje listę układów współrzędnych narzędzia
        //2. Ustaw parametry komunikacji UDP i załaduj komunikację UDP
        UDPComParam param=new UDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10,0);
        robot.ExtDevSetUDPComParam(param);
        robot.ExtDevLoadUDPDriver();
        //3. Ustaw parametry osi rozszerzonej, w tym typ osi rozszerzonej, parametry sterownika osi rozszerzonej, parametry DH osi rozszerzonej
        robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0); //Jednoosiowy pozycjoner i parametry DH
        robot.SetRobotPosToAxis(1); //Pozycja montażowa osi rozszerzonej
        robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0); //Parametry sterownika serwonapędu. W tym przykładzie dla pozycjonera jednoosiowego wystarczy ustawić parametry jednego sterownika. Jeśli wybierzesz typ osi rozszerzonej zawierający wiele osi, musisz ustawić parametry sterownika dla każdej osi.
        //4. Włącz zasilanie wybranej osi i wykonaj powrót do zera
        robot.ExtAxisServoOn(1, 0);
        robot.ExtAxisSetHoming(1, 0, 20, 3);
        //5. Wykonaj kalibrację układu współrzędnych osi rozszerzonej i zastosuj go
        DescPose pos = new DescPose(/* Wprowadź współrzędne swojego punktu kalibracyjnego */ );
        robot.SetRefPointInExAxisEnd(pos);
        robot.PositionorSetRefPoint(1); /*Musisz skalibrować oś rozszerzoną za pomocą czterech różnych pozycji punktów, dlatego musisz wywołać ten interfejs 4 razy, aby zakończyć kalibrację */
        DescPose coord = new DescPose();
        robot.PositionorComputeECoordSys(coord); //Oblicz wynik kalibracji osi rozszerzonej
        robot.ExtAxisActiveECoordSys(1, 1, coord, 1); //Zastosuj wynik kalibracji do układu współrzędnych osi rozszerzonej
        //6. Kalibracja układu współrzędnych obiektu na osi rozszerzonej. Będziesz potrzebować następujących interfejsów:
        //int SetWObjCoordPoint(int point_num);
        //int ComputeWObjCoord(int method, ref DescPose wobj_pose);
        //int SetWObjCoord(int id, DescPose coord);
        //int SetWObjList(int id, DescPose coord);
        //7. Zapisz punkt początkowy synchronicznego ruchu stawowego
        DescPose startdescPose = new DescPose(/* Wprowadź swoje współrzędne */ );
        JointPos startjointPos = new JointPos(/* Wprowadź swoje współrzędne */ );
        ExaxisPos startexaxisPos = new ExaxisPos(/* Wprowadź współrzędne punktu początkowego osi rozszerzonej */ );
        //8. Zapisz współrzędne punktu końcowego synchronicznego ruchu stawowego
        DescPose enddescPose = new DescPose(/* Wprowadź swoje współrzędne */ );
        JointPos endjointPos = new JointPos(/* Wprowadź swoje współrzędne */ );
        ExaxisPos endexaxisPos =new ExaxisPos(/* Wprowadź współrzędne punktu końcowego osi rozszerzonej */);
        //9. Napisz program ruchu synchronicznego
        //Przejedź do punktu początkowego, zakładając, że stosowane układy współrzędnych narzędzia i obiektu to 1
        robot.ExtAxisMove(startexaxisPos, 20);
        DescPose offdese = new DescPose( 0, 0, 0, 0, 0, 0 );
        robot.MoveJ(startjointPos, startdescPose, 1, 1, 100, 100, 100, startexaxisPos, 0, 0, offdese);
        //Rozpocznij ruch synchroniczny
        robot.ExtAxisSyncMoveJ(endjointPos, enddescPose, 1, 1, 100, 100, 100, endexaxisPos, -1, 0, offdese);
        robot.MoveJ(startjointPos, 1, 1, 100, 100, 100, startexaxisPos, 0, 0, offdese);
        //Rozpocznij ruch synchroniczny
        robot.ExtAxisSyncMoveJ(endjointPos, 1, 1, 100, 100, 100, endexaxisPos, -1, 0, offdese);
        robot.CloseRPC();
        return 0;
    }

Ruch synchroniczny osi rozszerzonej UDP z ruchem liniowym robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ruch synchroniczny osi rozszerzonej UDP z ruchem liniowym robota
    * @param [in] joint_pos Docelowa pozycja stawów, jednostka deg
    * @param [in] desc_pos Docelowa poza i orientacja w kartezjańskim układzie współrzędnych
    * @param [in] tool Numer narzędzia, zakres [0~14]
    * @param [in] user Numer obiektu, zakres [0~14]
    * @param [in] vel Procent prędkości, zakres [0~100]
    * @param [in] acc Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param [in] ovl Współczynnik skalowania prędkości, zakres [0~100]
    * @param [in] blendR [-1.0]-ruch do pozycji (blokujący), [0~1000.0]-promień wygładzania (nieblokujący), jednostka mm
    * @param [in] epos Pozycja osi rozszerzonej, jednostka mm
    * @param [in] offset_flag 0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie obiektu, 2-przesunięcie w układzie narzędzia
    * @param [in] offset_pos Wartość przesunięcia pozy i orientacji
    * @return Kod błędu
    */
    int ExtAxisSyncMoveL(JointPos joint_pos, DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, ExaxisPos epos, int offset_flag, DescPose offset_pos);

Ruch synchroniczny osi rozszerzonej UDP z ruchem liniowym robota (automatyczne obliczanie odwrotnej kinematyki)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief Ruch synchroniczny osi rozszerzonej UDP z ruchem liniowym robota (automatyczne obliczanie odwrotnej kinematyki)
    * @param [in] desc_pos Docelowa poza i orientacja w kartezjańskim układzie współrzędnych
    * @param [in] tool Numer narzędzia, zakres [0~14]
    * @param [in] user Numer obiektu, zakres [0~14]
    * @param [in] vel Procent prędkości, zakres [0~100]
    * @param [in] acc Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param [in] ovl Współczynnik skalowania prędkości, zakres [0~100]
    * @param [in] blendR [-1.0]-ruch do pozycji (blokujący), [0~1000.0]-promień wygładzania (nieblokujący), jednostka mm
    * @param [in] epos Pozycja osi rozszerzonej, jednostka mm
    * @param [in] offset_flag 0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie obiektu, 2-przesunięcie w układzie narzędzia
    * @param [in] offset_pos Wartość przesunięcia pozy i orientacji
    * @param [in] config Konfiguracja przestrzeni stawów dla odwrotnej kinematyki, [-1]-obliczenia w oparciu o bieżącą pozycję stawów, [0~7]-obliczenia zgodnie z określoną konfiguracją przestrzeni stawów
    * @return Kod błędu
    */
    int ExtAxisSyncMoveL(DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, ExaxisPos epos, int offset_flag, DescPose offset_pos,int config)

Przykład kodu ruchu synchronicznego z ruchem liniowym robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public int testSyncMoveL(Robot robot)
    {
        //1. Kalibracja i zastosowanie układu współrzędnych narzędzia robota. Możesz użyć metody czterech lub sześciu punktów do kalibracji i zastosowania układu współrzędnych narzędzia. Interfejsy związane z kalibracją układu współrzędnych narzędzia są następujące:
        //  int SetToolPoint(int point_num); //Ustawia punkt odniesienia narzędzia - metoda sześciu punktów
        //  int ComputeTool(ref DescPose tcp_pose); //Oblicza układ współrzędnych narzędzia
        //  int SetTcp4RefPoint(int point_num);  //Ustawia punkt odniesienia narzędzia - metoda czterech punktów
        //  int ComputeTcp4(ref DescPose tcp_pose);  //Oblicza układ współrzędnych narzędzia - metoda czterech punktów
        //  int SetToolCoord(int id, DescPose coord, int type, int install); //Ustawia i stosuje układ współrzędnych narzędzia
        //  int SetToolList(int id, DescPose coord, int type, int install);  //Ustawia i stosuje listę układów współrzędnych narzędzia
        //2. Ustaw parametry komunikacji UDP i załaduj komunikację UDP
        UDPComParam param=new UDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10,0);
        robot.ExtDevSetUDPComParam(param);
        robot.ExtDevLoadUDPDriver();
        //3. Ustaw parametry osi rozszerzonej, w tym typ osi rozszerzonej, parametry sterownika osi rozszerzonej, parametry DH osi rozszerzonej
        robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0); //Jednoosiowy pozycjoner i parametry DH
        robot.SetRobotPosToAxis(1); //Pozycja montażowa osi rozszerzonej
        robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0); //Parametry sterownika serwonapędu. W tym przykładzie dla pozycjonera jednoosiowego wystarczy ustawić parametry jednego sterownika. Jeśli wybierzesz typ osi rozszerzonej zawierający wiele osi, musisz ustawić parametry sterownika dla każdej osi.
        //4. Włącz zasilanie wybranej osi i wykonaj powrót do zera
        robot.ExtAxisServoOn(1, 0);
        robot.ExtAxisSetHoming(1, 0, 20, 3);
        //5. Wykonaj kalibrację układu współrzędnych osi rozszerzonej i zastosuj go
        DescPose pos = new DescPose(/* Wprowadź współrzędne swojego punktu kalibracyjnego */ );
        robot.SetRefPointInExAxisEnd(pos);
        robot.PositionorSetRefPoint(1); /*Musisz skalibrować oś rozszerzoną za pomocą czterech różnych pozycji punktów, dlatego musisz wywołać ten interfejs 4 razy, aby zakończyć kalibrację */
        DescPose coord = new DescPose();
        robot.PositionorComputeECoordSys(coord); //Oblicz wynik kalibracji osi rozszerzonej
        robot.ExtAxisActiveECoordSys(1, 1, coord, 1); //Zastosuj wynik kalibracji do układu współrzędnych osi rozszerzonej
        //6. Kalibracja układu współrzędnych obiektu na osi rozszerzonej. Będziesz potrzebować następujących interfejsów:
        //int SetWObjCoordPoint(int point_num);
        //int ComputeWObjCoord(int method, ref DescPose wobj_pose);
        //int SetWObjCoord(int id, DescPose coord);
        //int SetWObjList(int id, DescPose coord);
        //7. Zapisz punkt początkowy synchronicznego ruchu liniowego
        DescPose startdescPose = new DescPose(/* Wprowadź swoje współrzędne */ );
        JointPos startjointPos = new JointPos(/* Wprowadź swoje współrzędne */ );
        ExaxisPos startexaxisPos = new ExaxisPos(/* Wprowadź współrzędne punktu początkowego osi rozszerzonej */ );
        //8. Zapisz współrzędne punktu końcowego synchronicznego ruchu liniowego
        DescPose enddescPose = new DescPose(/* Wprowadź swoje współrzędne */ );
        JointPos endjointPos = new JointPos(/* Wprowadź swoje współrzędne */ );
        ExaxisPos endexaxisPos =new ExaxisPos(/* Wprowadź współrzędne punktu końcowego osi rozszerzonej */);
        //9. Napisz program ruchu synchronicznego
        //Przejedź do punktu początkowego, zakładając, że stosowane układy współrzędnych narzędzia i obiektu to 1
        robot.ExtAxisMove(startexaxisPos, 20);
        DescPose offdese = new DescPose( 0, 0, 0, 0, 0, 0 );
        robot.MoveJ(startjointPos, startdescPose, 1, 1, 100, 100, 100, startexaxisPos, 0, 0, offdese);
        //Rozpocznij ruch synchroniczny
        robot.ExtAxisSyncMoveL(endjointPos, enddescPose, 1, 1, 100, 100, 100, 0, endexaxisPos, 0, offdese);
        robot.MoveJ(startjointPos, 1, 1, 100, 100, 100, startexaxisPos, 0, 0, offdese);
        //Rozpocznij ruch synchroniczny
        robot.ExtAxisSyncMoveL(enddescPose, 1, 1, 100, 100, 100, 0, endexaxisPos, 0, offdese,-1);
        robot.CloseRPC();
        return 0;
    }

Ruch synchroniczny osi rozszerzonej UDP z ruchem łukowym robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ruch synchroniczny osi rozszerzonej UDP z ruchem łukowym robota
    * @param [in] joint_pos_p Pozycja stawów punktu pośredniego, jednostka deg
    * @param [in] desc_pos_p Poza i orientacja punktu pośredniego w kartezjańskim układzie współrzędnych
    * @param [in] ptool Numer narzędzia, zakres [0~14]
    * @param [in] puser Numer obiektu, zakres [0~14]
    * @param [in] pvel Procent prędkości, zakres [0~100]
    * @param [in] pacc Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param [in] epos_p Pozycja osi rozszerzonej punktu pośredniego, jednostka mm
    * @param [in] poffset_flag 0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie obiektu, 2-przesunięcie w układzie narzędzia
    * @param [in] offset_pos_p Wartość przesunięcia pozy i orientacji
    * @param [in] joint_pos_t Pozycja stawów punktu docelowego, jednostka deg
    * @param [in] desc_pos_t Poza i orientacja punktu docelowego w kartezjańskim układzie współrzędnych
    * @param [in] ttool Numer narzędzia, zakres [0~14]
    * @param [in] tuser Numer obiektu, zakres [0~14]
    * @param [in] tvel Procent prędkości, zakres [0~100]
    * @param [in] tacc Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param [in] epos_t Pozycja osi rozszerzonej punktu docelowego, jednostka mm
    * @param [in] toffset_flag 0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie obiektu, 2-przesunięcie w układzie narzędzia
    * @param [in] offset_pos_t Wartość przesunięcia pozy i orientacji
    * @param [in] ovl Współczynnik skalowania prędkości, zakres [0~100]
    * @param [in] blendR [-1.0]-ruch do pozycji (blokujący), [0~1000.0]-promień wygładzania (nieblokujący), jednostka mm
    * @return Kod błędu
    */
    int ExtAxisSyncMoveC(JointPos joint_pos_p, DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p, JointPos joint_pos_t, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t, double ovl, double blendR);

Ruch synchroniczny osi rozszerzonej UDP z ruchem łukowym robota (automatyczne obliczanie odwrotnej kinematyki)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief Ruch synchroniczny osi rozszerzonej UDP z ruchem łukowym robota (automatyczne obliczanie odwrotnej kinematyki)
    * @param [in] desc_pos_p Poza i orientacja punktu pośredniego w kartezjańskim układzie współrzędnych
    * @param [in] ptool Numer narzędzia, zakres [0~14]
    * @param [in] puser Numer obiektu, zakres [0~14]
    * @param [in] pvel Procent prędkości, zakres [0~100]
    * @param [in] pacc Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param [in] epos_p Pozycja osi rozszerzonej punktu pośredniego, jednostka mm
    * @param [in] poffset_flag 0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie obiektu, 2-przesunięcie w układzie narzędzia
    * @param [in] offset_pos_p Wartość przesunięcia pozy i orientacji
    * @param [in] desc_pos_t Poza i orientacja punktu docelowego w kartezjańskim układzie współrzędnych
    * @param [in] ttool Numer narzędzia, zakres [0~14]
    * @param [in] tuser Numer obiektu, zakres [0~14]
    * @param [in] tvel Procent prędkości, zakres [0~100]
    * @param [in] tacc Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param [in] epos_t Pozycja osi rozszerzonej punktu docelowego, jednostka mm
    * @param [in] toffset_flag 0-brak przesunięcia, 1-przesunięcie w układzie bazowym/układzie obiektu, 2-przesunięcie w układzie narzędzia
    * @param [in] offset_pos_t Wartość przesunięcia pozy i orientacji
    * @param [in] ovl Współczynnik skalowania prędkości, zakres [0~100]
    * @param [in] blendR [-1.0]-ruch do pozycji (blokujący), [0~1000.0]-promień wygładzania (nieblokujący), jednostka mm
    * @param [in] config Konfiguracja przestrzeni stawów dla odwrotnej kinematyki, [-1]-obliczenia w oparciu o bieżącą pozycję stawów, [0~7]-obliczenia zgodnie z określoną konfiguracją przestrzeni stawów
    * @return Kod błędu
    */
    int ExtAxisSyncMoveC(DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t, double ovl, double blendR,int config)

Przykład kodu ruchu synchronicznego z ruchem łukowym robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public int testSyncMoveC(Robot robot)
    {
        //1. Kalibracja i zastosowanie układu współrzędnych narzędzia robota. Możesz użyć metody czterech lub sześciu punktów do kalibracji i zastosowania układu współrzędnych narzędzia. Interfejsy związane z kalibracją układu współrzędnych narzędzia są następujące:
        //  int SetToolPoint(int point_num); //Ustawia punkt odniesienia narzędzia - metoda sześciu punktów
        //  int ComputeTool(ref DescPose tcp_pose); //Oblicza układ współrzędnych narzędzia
        //  int SetTcp4RefPoint(int point_num);  //Ustawia punkt odniesienia narzędzia - metoda czterech punktów
        //  int ComputeTcp4(ref DescPose tcp_pose);  //Oblicza układ współrzędnych narzędzia - metoda czterech punktów
        //  int SetToolCoord(int id, DescPose coord, int type, int install); //Ustawia i stosuje układ współrzędnych narzędzia
        //  int SetToolList(int id, DescPose coord, int type, int install);  //Ustawia i stosuje listę układów współrzędnych narzędzia
        //2. Ustaw parametry komunikacji UDP i załaduj komunikację UDP
        UDPComParam param=new UDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10,0);
        robot.ExtDevSetUDPComParam(param);
        robot.ExtDevLoadUDPDriver();
        //3. Ustaw parametry osi rozszerzonej, w tym typ osi rozszerzonej, parametry sterownika osi rozszerzonej, parametry DH osi rozszerzonej
        robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0); //Jednoosiowy pozycjoner i parametry DH
        robot.SetRobotPosToAxis(1); //Pozycja montażowa osi rozszerzonej
        robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0); //Parametry sterownika serwonapędu. W tym przykładzie dla pozycjonera jednoosiowego wystarczy ustawić parametry jednego sterownika. Jeśli wybierzesz typ osi rozszerzonej zawierający wiele osi, musisz ustawić parametry sterownika dla każdej osi.
        //4. Włącz zasilanie wybranej osi i wykonaj powrót do zera
        robot.ExtAxisServoOn(1, 0);
        robot.ExtAxisSetHoming(1, 0, 20, 3);
        //5. Wykonaj kalibrację układu współrzędnych osi rozszerzonej i zastosuj go
        DescPose pos = new DescPose(/* Wprowadź współrzędne swojego punktu kalibracyjnego */ );
        robot.SetRefPointInExAxisEnd(pos);
        robot.PositionorSetRefPoint(1); /*Musisz skalibrować oś rozszerzoną za pomocą czterech różnych pozycji punktów, dlatego musisz wywołać ten interfejs 4 razy, aby zakończyć kalibrację */
        DescPose coord = new DescPose();
        robot.PositionorComputeECoordSys(coord); //Oblicz wynik kalibracji osi rozszerzonej
        robot.ExtAxisActiveECoordSys(1, 1, coord, 1); //Zastosuj wynik kalibracji do układu współrzędnych osi rozszerzonej
        //6. Kalibracja układu współrzędnych obiektu na osi rozszerzonej. Będziesz potrzebować następujących interfejsów:
        //int SetWObjCoordPoint(int point_num);
        //int ComputeWObjCoord(int method, ref DescPose wobj_pose);
        //int SetWObjCoord(int id, DescPose coord);
        //int SetWObjList(int id, DescPose coord);
        //7. Zapisz punkt początkowy synchronicznego ruchu łukowego
        DescPose startdescPose = new DescPose(/* Wprowadź swoje współrzędne */ );
        JointPos startjointPos = new JointPos(/* Wprowadź swoje współrzędne */ );
        ExaxisPos startexaxisPos = new ExaxisPos(/* Wprowadź współrzędne punktu początkowego osi rozszerzonej */ );
        //8. Zapisz współrzędne punktu końcowego synchronicznego ruchu łukowego
        DescPose enddescPose = new DescPose(/* Wprowadź swoje współrzędne */ );
        JointPos endjointPos = new JointPos(/* Wprowadź swoje współrzędne */ );
        ExaxisPos endexaxisPos = new ExaxisPos(/* Wprowadź współrzędne punktu końcowego osi rozszerzonej */ );
        //9. Zapisz współrzędne punktu pośredniego synchronicznego ruchu łukowego
        DescPose middescPose = new DescPose(/* Wprowadź swoje współrzędne */ );
        JointPos midjointPos =new JointPos(/* Wprowadź swoje współrzędne */ );
        ExaxisPos midexaxisPos = new ExaxisPos(/* Wprowadź współrzędne osi rozszerzonej w punkcie pośrednim łuku robota */ );
        //10. Napisz program ruchu synchronicznego
        //Przejedź do punktu początkowego, zakładając, że stosowane układy współrzędnych narzędzia i obiektu to 1
        robot.ExtAxisMove(startexaxisPos, 20);
        DescPose offdese = new DescPose( 0, 0, 0, 0, 0, 0 );
        robot.MoveJ(startjointPos, startdescPose, 1, 1, 100, 100, 100, startexaxisPos, 0, 0, offdese);
        //Rozpocznij ruch synchroniczny
        robot.ExtAxisSyncMoveC(midjointPos, middescPose, 1, 1, 100, 100, midexaxisPos, 0, offdese, endjointPos, enddescPose, 1, 1, 100, 100, endexaxisPos, 0, offdese, 100, 0);
        robot.MoveJ(startjointPos, 1, 1, 100, 100, 100, startexaxisPos, 0, 0, offdese);
        //Rozpocznij ruch synchroniczny
        robot.ExtAxisSyncMoveC(middescPose, 1, 1, 100, 100, midexaxisPos, 0, offdese, enddescPose, 1, 1, 100, 100, endexaxisPos, 0, offdese, 100, 0,-1);
        robot.CloseRPC();
        return 0;
    }

Ustawianie rozszerzonego wyjścia cyfrowego (DO)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia rozszerzone wyjście cyfrowe (DO)
    * @param [in] DONum Numer DO
    * @param [in] bOpen Stan przełącznika true-włączone; false-wyłączone
    * @param [in] smooth Czy wygładzać
    * @param [in] block Czy blokować
    * @return Kod błędu
    */
    int SetAuxDO(int DONum, boolean bOpen, boolean smooth, boolean block);

Ustawianie rozszerzonego wyjścia analogowego (AO)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia rozszerzone wyjście analogowe (AO)
    * @param [in] AONum Numer AO
    * @param [in] value Wartość analogowa [0-4095]
    * @param [in] block Czy blokować
    * @return Kod błędu
    */
    int SetAuxAO(int AONum, double value, boolean block);

Ustawianie czasu filtracji wejścia rozszerzonego DI
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia czas filtracji wejścia rozszerzonego DI
    * @param [in] filterTime Czas filtracji (ms)
    * @return Kod błędu
    */
    int SetAuxDIFilterTime(int filterTime);

Ustawianie czasu filtracji wejścia rozszerzonego AI
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia czas filtracji wejścia rozszerzonego AI
    * @param [in] AONum Numer AO
    * @param [in] filterTime Czas filtracji (ms)
    * @return Kod błędu
    */
    int SetAuxAIFilterTime(int AONum, int filterTime);

Oczekiwanie na wejście rozszerzone DI
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Oczekuje na wejście rozszerzone DI
    * @param [in] DINum Numer DI
    * @param [in] bOpen Stan przełącznika 0-wyłączone; 1-włączone
    * @param [in] time Maksymalny czas oczekiwania (ms)
    * @param [in] errorAlarm Czy kontynuować ruch
    * @return Kod błędu
    */
    int WaitAuxDI(int DINum, boolean bOpen, int time, boolean errorAlarm);

Oczekiwanie na wejście rozszerzone AI
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Oczekuje na wejście rozszerzone AI
    * @param [in] AINum Numer AI
    * @param [in] sign 0-większe niż; 1-mniejsze niż
    * @param [in] value Wartość AI
    * @param [in] time Maksymalny czas oczekiwania (ms)
    * @param [in] errorAlarm Czy kontynuować ruch
    * @return Kod błędu
    */
    int WaitAuxAI(int AINum, int sign, int value, int time, boolean errorAlarm);

Pobieranie wartości rozszerzonego DI
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera wartość rozszerzonego DI
    * @param [in] DINum Numer DI
    * @param [in] isNoBlock Czy blokować
    * @return List[0]:kod błędu; List[1] : isOpen 0-wyłączone; 1-włączone
    */
    List<Integer> GetAuxDI(int DINum, boolean isNoBlock)

Pobieranie wartości rozszerzonego AI
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera wartość rozszerzonego AI
    * @param [in] AINum Numer AI
    * @param [in] isNoBlock Czy blokować
    * @return List[0]:kod błędu; List[1] : value Wartość wejściowa
    */
    List<Integer> GetAuxAI(int AINum, boolean isNoBlock);

Przykład kodu rozszerzonego IO
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestAuxDOAO(Robot robot)
    {
        for (int i = 0; i < 128; i++)
        {
            robot.SetAuxDO(i, true, false, true);
            robot.Sleep(100);
        }
        for (int i = 0; i < 128; i++)
        {
            robot.SetAuxDO(i, false, false, true);
            robot.Sleep(100);
        }

        for (int i = 0; i < 409; i++)
        {
            robot.SetAuxAO(0, i * 10, true);
            robot.SetAuxAO(1, 4095 - i * 10, true);
            robot.SetAuxAO(2, i * 10, true);
            robot.SetAuxAO(3, 4095 - i * 10, true);
            robot.Sleep(10);
        }

        robot.SetAuxDIFilterTime(10);
        robot.SetAuxAIFilterTime(0, 10);


        int curValue = -1;
        List<Integer> liter=new ArrayList<>();
        for (int i = 0; i < 4; i++)
        {
            liter = robot.GetAuxAI(i, true);
        }

        robot.WaitAuxDI(1, false, 1000, false);
        robot.WaitAuxAI(1, 1, 132, 1000, false);

        robot.CloseRPC();
        return 0;
    }

Włączanie zasilania mobilnego urządzenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Włącza zasilanie mobilnego urządzenia
    * @param [in] enable false-wyłączone; true-włączone
    * @return Kod błędu
    */
    int TractorEnable(Boolean enable);

Powrót do zera mobilnego urządzenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Powrót do zera mobilnego urządzenia
    * @return Kod błędu
    */
    int TractorHoming();

Ruch liniowy mobilnego urządzenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ruch liniowy mobilnego urządzenia
    * @param [in] distance Dystans ruchu liniowego (mm)
    * @param [in] vel Procent prędkości ruchu liniowego (0-100)
    * @return Kod błędu
    */
    int TractorMoveL(double distance, double vel);

Ruch łukowy mobilnego urządzenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ruch łukowy mobilnego urządzenia
    * @param [in] radio Promień ruchu łukowego (mm)
    * @param [in] angle Kąt ruchu łukowego (°)
    * @param [in] vel Procent prędkości ruchu liniowego (0-100)
    * @return Kod błędu
    */
    int TractorMoveC(double radio, double angle, double vel);

Zatrzymanie ruchu mobilnego urządzenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Zatrzymuje ruch mobilnego urządzenia
    * @return Kod błędu
    */
    int TractorStop();

Przykład kodu mobilnego urządzenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void main(String[] args)
    {
        Robot robot = new Robot();
        robot.SetReconnectParam(true,20,500);//ustawienie liczby prób ponownego łączenia i odstępu
        robot.LoggerInit(FrLogType.DIRECT, FrLogLevel.INFO, "D://log", 10, 10);
        int rtn = robot.RPC("192.168.58.2");
        if(rtn == 0)
        {
            System.out.println("rpc połączenie success");
        }
        else
        {
            System.out.println("rpc połączenie fail");
            return ;
        }
        UDPComParam param = new UDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10);
        robot.ExtDevSetUDPComParam(param);//komunikacja UDP osi rozszerzonej
        robot.ExtAxisParamConfig(1, 0, 0, 50000, -50000, 1000, 1000, 6.280, 16384, 200, 0, 0, 0);
        robot.ExtAxisParamConfig(2, 0, 0, 50000, -50000, 1000, 1000, 6.280, 16384, 200, 0, 0, 0);
        robot.SetAxisDHParaConfig(5, 0, 0, 0, 0, 0, 0, 0, 0);

        robot.TractorEnable(false);
        robot.Sleep(2000);
        robot.TractorEnable(true);
        robot.Sleep(2000);
        robot.TractorHoming();

        robot.Sleep(2000);
        robot.TractorMoveL(100, 20);
        robot.Sleep(5000);
        robot.TractorMoveL(-100, 20);
        robot.Sleep(5000);
        robot.TractorMoveC(300, 90, 20);
        robot.Sleep(2000);
        robot.TractorStop();//zatrzymanie wózka
        robot.TractorMoveC(300, -90, 20);
    }

Ustawianie czasu zakończenia pozycjonowania osi rozszerzonej UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia czas zakończenia pozycjonowania osi rozszerzonej UDP
    * @param time Czas zakończenia pozycjonowania [ms]
    * @return Kod błędu
    */
    public int SetExAxisCmdDoneTime(double time)