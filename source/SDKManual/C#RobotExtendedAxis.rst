Oś rozszerzona
==============

.. toctree:: 
    :maxdepth: 5

Ustawienie parametrów osi rozszerzonej 485
++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /** 
    * @brief Ustawia parametry osi rozszerzonej 485
    * @param [in] servoId ID serwonapędu, zakres [1-15], odpowiada ID stacji podrzędnej 
    * @param [in] servoCompany Producent serwonapędu, 1-Dynatect
    * @param [in] servoModel Model serwonapędu, 1-FD100-750C
    * @param [in] servoSoftVersion Wersja oprogramowania serwonapędu, 1-V1.0
    * @param [in] servoResolution Rozdzielczość enkodera
    * @param [in] axisMechTransRatio Przełożenie mechaniczne
    * @return Kod błędu 
    */
    int AuxServoSetParam(int servoId, int servoCompany, int servoModel, int servoSoftVersion, int servoResolution, double axisMechTransRatio);
    
Pobranie parametrów konfiguracyjnych osi rozszerzonej 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /** 
    * @brief Pobiera parametry konfiguracyjne osi rozszerzonej 485
    * @param [in] servoId ID serwonapędu, zakres [1-15], odpowiada ID stacji podrzędnej 
    * @param [out] servoCompany Producent serwonapędu, 1-Dynatect
    * @param [out] servoModel Model serwonapędu, 1-FD100-750C
    * @param [out] servoSoftVersion Wersja oprogramowania serwonapędu, 1-V1.0
    * @param [out] servoResolution Rozdzielczość enkodera
    * @param [out] axisMechTransRatio Przełożenie mechaniczne
    * @return Kod błędu 
    */
    int AuxServoGetParam(int servoId, ref int servoCompany, ref int servoModel, ref int servoSoftVersion, ref int servoResolution, ref double axisMechTransRatio);
    
Ustawienie załączenia/odłączenia osi rozszerzonej 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /** 
    * @brief Ustawia załączenie/odłączenie osi rozszerzonej 485
    * @param [in] servoId ID serwonapędu, zakres [1-15], odpowiada ID stacji podrzędnej 
    * @param [in] status Stan załączenia, 0-odłączenie, 1-załączenie
    * @return Kod błędu 
    */
    int AuxServoEnable(int servoId, int status);
        
Ustawienie trybu sterowania osi rozszerzonej 485
++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /** 
    * @brief Ustawia tryb sterowania osi rozszerzonej 485
    * @param [in] servoId ID serwonapędu, zakres [1-15], odpowiada ID stacji podrzędnej 
    * @param [in] mode Tryb sterowania, 0-tryb pozycyjny, 1-tryb prędkości
    * @return Kod błędu 
    */
    int AuxServoSetControlMode(int servoId, int mode);

Ustawienie pozycji docelowej osi rozszerzonej 485 (tryb pozycyjny)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /** 
    * @brief Ustawia pozycję docelową osi rozszerzonej 485 (tryb pozycyjny)
    * @param [in] servoId ID serwonapędu, zakres [1-15], odpowiada ID stacji podrzędnej 
    * @param [in] pos Pozycja docelowa, mm lub °
    * @param [in] speed Prędkość docelowa, mm/s lub °/s
    * @return Kod błędu 
    */
    int AuxServoSetTargetPos(int servoId, double pos, double speed);

Ustawienie prędkości docelowej osi rozszerzonej 485 (tryb prędkości)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /** 
    * @brief Ustawia prędkość docelową osi rozszerzonej 485 (tryb prędkości)
    * @param [in] servoId ID serwonapędu, zakres [1-15], odpowiada ID stacji podrzędnej 
    * @param [in] speed Prędkość docelowa, mm/s lub °/s
    * @return Kod błędu 
    */
    int AuxServoSetTargetSpeed(int servoId, double speed);
    
Ustawienie momentu docelowego osi rozszerzonej 485 (tryb momentowy) -- tymczasowo nieudostępnione
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /** 
    * @brief Ustawia moment docelowy osi rozszerzonej 485 (tryb momentowy) -- tymczasowo nieudostępnione
    * @param [in] servoId ID serwonapędu, zakres [1-15], odpowiada ID stacji podrzędnej 
    * @param [in] torque Moment docelowy, Nm
    * @return Kod błędu 
    */
    int AuxServoSetTargetTorque(int servoId, double torque);

Ustawienie powrotu do zera osi rozszerzonej 485
+++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /** 
    * @brief Ustawia powrót do zera osi rozszerzonej 485
    * @param [in] servoId ID serwonapędu, zakres [1-15], odpowiada ID stacji podrzędnej 
    * @param [in] mode Tryb powrotu do zera, 1-powrót do zera z bieżącej pozycji; 2-powrót do zera z ogranicznikiem ujemnym; 3-powrót do zera z ogranicznikiem dodatnim
    * @param [in] searchVel Prędkość poszukiwania zera, mm/s lub °/s
    * @param [in] latchVel Prędkość pozycjonowania w zerze, mm/s lub °/s
    * @return Kod błędu 
    */
    int AuxServoHoming(int servoId, int mode, double searchVel, double latchVel);
        
Wyczyść informację o błędzie osi rozszerzonej 485
+++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /** 
    * @brief Czyści informację o błędzie osi rozszerzonej 485
    * @param [in] servoId ID serwonapędu, zakres [1-15], odpowiada ID stacji podrzędnej 
    * @return Kod błędu 
    */
    int AuxServoClearError(int servoId);

Pobranie stanu serwonapędu osi rozszerzonej 485
++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /** 
    * @brief Pobiera stan serwonapędu osi rozszerzonej 485
    * @param [in] servoId ID serwonapędu, zakres [1-15], odpowiada ID stacji podrzędnej 
    * @param [out] servoErrCode Kod usterki serwonapędu
    * @param [out] servoState Stan serwonapędu  bit0:0-niezałączony; 1-załączony;  bit1:0-nie w ruchu; 1-w ruchu;  bit2 0-ogranicznik dodatni nie wyzwolony; 1-ogranicznik dodatni wyzwolony; bit3 0-ogranicznik ujemny nie wyzwolony; 1-ogranicznik ujemny wyzwolony; bit4 0-pozycjonowanie niezakończone; 1-pozycjonowanie zakończone;  bit5:0-nie wyzerowano; 1-wyzerowano
    * @param [out] servoPos Bieżąca pozycja serwa mm lub °
    * @param [out] servoSpeed Bieżąca prędkość serwa mm/s lub °/s
    * @param [out] servoTorque Bieżący moment serwa Nm
    * @return Kod błędu 
    */
    int AuxServoGetStatus(int servoId, ref int servoErrCode, ref int servoState, ref double servoPos, ref double servoSpeed, ref double servoTorque);
    
Ustawienie numeru osi danych osi rozszerzonej 485 w informacji zwrotnej o stanie
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6
    
.. code-block:: c#
    :linenos:

    /** 
    * @brief Ustawia numer osi danych osi rozszerzonej 485 w informacji zwrotnej o stanie
    * @param [in] servoId ID serwonapędu, zakres [1-15], odpowiada ID stacji podrzędnej 
    * @return Kod błędu 
    */
    int AuxServosetStatusID(int servoId);

Ustawienie przyspieszenia i opóźnienia ruchu osi rozszerzonej 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: C#
    :linenos:

    /**
    * @brief Ustawia przyspieszenie i opóźnienie ruchu osi rozszerzonej 485
    * @param [in] acc Przyspieszenie ruchu osi rozszerzonej 485
    * @param [in] dec Opóźnienie ruchu osi rozszerzonej 485
    * @return  Kod błędu
    */
    int AuxServoSetAcc(double acc, double dec);

Ustawienie przyspieszenia i opóźnienia awaryjnego zatrzymania osi rozszerzonej 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: C#
    :linenos:

    /**
    * @brief Ustawia przyspieszenie i opóźnienie awaryjnego zatrzymania osi rozszerzonej 485
    * @param [in] acc Przyspieszenie awaryjnego zatrzymania osi rozszerzonej 485
    * @param [in] dec Opóźnienie awaryjnego zatrzymania osi rozszerzonej 485
    * @return  Kod błędu
    */
    int AuxServoSetEmergencyStopAcc(double acc, double dec);

Pobranie przyspieszenia i opóźnienia ruchu osi rozszerzonej 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: C#
    :linenos:

    /**
    * @brief Pobiera przyspieszenie i opóźnienie ruchu osi rozszerzonej 485
    * @param [out] acc Przyspieszenie ruchu osi rozszerzonej 485
    * @param [out] dec Opóźnienie ruchu osi rozszerzonej 485
    * @return  Kod błędu
    */
    int AuxServoGetAcc(ref double acc, ref double dec);

Pobranie przyspieszenia i opóźnienia awaryjnego zatrzymania osi rozszerzonej 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: C#
    :linenos:

    /**
    * @brief Pobiera przyspieszenie i opóźnienie awaryjnego zatrzymania osi rozszerzonej 485
    * @param [out] acc Przyspieszenie awaryjnego zatrzymania osi rozszerzonej 485
    * @param [out] dec Opóźnienie awaryjnego zatrzymania osi rozszerzonej 485
    * @return  Kod błędu
    */
    int AuxServoGetEmergencyStopAcc(ref double acc, ref double dec);

Przykład kodu sterowania osią rozszerzoną
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2

.. code-block:: c#
    :linenos:

    private void button64_Click(object sender, EventArgs e)
    {
        int retval = robot.AuxServoSetParam(1, 1, 1, 1, 131072, 15.45);
        Console.WriteLine($"AuxServoSetParam is: {retval}");

        int servoCompany = 0;
        int servoModel = 0;
        int servoSoftVersion = 0;
        int servoResolution = 0;
        double axisMechTransRatio = 0;
        retval = robot.AuxServoGetParam(1, ref servoCompany, ref servoModel, ref servoSoftVersion, ref servoResolution, ref axisMechTransRatio);
        Console.WriteLine($"servoCompany {servoCompany}\n" +
            $"servoModel {servoModel}\n" +
            $"servoSoftVersion {servoSoftVersion}\n" +
            $"servoResolution {servoResolution}\n" +
            $"axisMechTransRatio {axisMechTransRatio}\n");

        retval = robot.AuxServoSetParam(1, 10, 11, 12, 13, 14);
        Console.WriteLine($"AuxServoSetParam is: {retval}");

        retval = robot.AuxServoGetParam(1, ref servoCompany, ref servoModel, ref servoSoftVersion, ref servoResolution, ref axisMechTransRatio);
        Console.WriteLine($"servoCompany {servoCompany}\n" +
            $"servoModel {servoModel}\n" +
            $"servoSoftVersion {servoSoftVersion}\n" +
            $"servoResolution {servoResolution}\n" +
            $"axisMechTransRatio {axisMechTransRatio}\n");

        retval = robot.AuxServoSetParam(1, 1, 1, 1, 131072, 36);
        Console.WriteLine($"AuxServoSetParam is: {retval}");
        Thread.Sleep(3000);

        robot.AuxServoSetAcc(3000, 3000);
        robot.AuxServoSetEmergencyStopAcc(5000, 5000);
        Thread.Sleep(1000);
        double emagacc = 0, acc = 0;
        double emagdec = 0, dec = 0;
        robot.AuxServoGetEmergencyStopAcc(ref emagacc, ref emagdec);
        Console.WriteLine($"emergency acc is {emagacc}  dec is {emagdec}");
        robot.AuxServoGetAcc(ref acc, ref dec);
        Console.WriteLine($"acc is {acc}  dec is {dec}");

        robot.AuxServoSetControlMode(1, 0);
        Thread.Sleep(2000);

        retval = robot.AuxServoEnable(1, 0);
        Console.WriteLine($"AuxServoEnable disenable {retval}");
        Thread.Sleep(1000);
        int servoerrcode = 0;
        int servoErrCode = 0;
        int servoState = 0;
        double servoPos = 0;
        double servoSpeed = 0;
        double servoTorque = 0;
        retval = robot.AuxServoGetStatus(1, ref servoErrCode, ref servoState, ref servoPos, ref servoSpeed, ref servoTorque);
        Console.WriteLine($"AuxServoGetStatus servoState {servoState}");
        Thread.Sleep(1000);

        retval = robot.AuxServoEnable(1, 1);
        Console.WriteLine($"AuxServoEnable enable {retval}");
        Thread.Sleep(1000);
        retval = robot.AuxServoGetStatus(1, ref servoErrCode, ref servoState, ref servoPos, ref servoSpeed, ref servoTorque);
        Console.WriteLine($"AuxServoGetStatus servoState {servoState}");
        Thread.Sleep(1000);

        retval = robot.AuxServoHoming(1, 1, 5, 1);
        Console.WriteLine($"AuxServoHoming {retval}");
        Thread.Sleep(3000);

        retval = robot.AuxServoSetTargetPos(1, 200, 30);
        Console.WriteLine($"AuxServoSetTargetPos {retval}");
        Thread.Sleep(1000);
        retval = robot.AuxServoGetStatus(1, ref servoErrCode, ref servoState, ref servoPos, ref servoSpeed, ref servoTorque);
        Console.WriteLine($"AuxServoGetStatus servoSpeed {servoSpeed}");
        Thread.Sleep(8000);

        robot.AuxServoSetControlMode(1, 1);
        Thread.Sleep(2000);

        robot.AuxServoEnable(1, 0);
        Thread.Sleep(1000);
        robot.AuxServoEnable(1, 1);
        Thread.Sleep(1000);
        robot.AuxServoSetTargetSpeed(1, 100, 80);

        Thread.Sleep(5000);
        robot.AuxServoSetTargetSpeed(1, 0, 80);
    }

Konfiguracja parametrów komunikacji UDP osi rozszerzonej
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Konfiguracja parametrów komunikacji UDP osi rozszerzonej
    * @param [in] ip Adres IP PLC
    * @param [in] port Numer portu
    * @param [in] period Okres komunikacji (ms, domyślnie 2, nie modyfikować tego parametru)
    * @param [in] lossPkgTime Czas wykrywania utraty pakietów (ms)
    * @param [in] lossPkgNum Liczba utraconych pakietów
    * @param [in] disconnectTime Czas potwierdzenia przerwania komunikacji
    * @param [in] reconnectEnable Włączenie automatycznego ponownego łączenia po przerwaniu komunikacji 0-niewłączone 1-włączone
    * @param [in] reconnectPeriod Odstęp między próbami ponownego połączenia (ms)
    * @param [in] reconnectNum Liczba prób ponownego połączenia
    * @param [in] selfConnect Czy automatycznie nawiązywać połączenie po ponownym uruchomieniu z wyłączeniem zasilania; 0-nienawiązuj połączenia; 1-nawiąż połączenie
    * @return Kod błędu
    */
    int ExtDevSetUDPComParam(std::string ip, int port, int period, int lossPkgTime, int lossPkgNum, int disconnectTime, int reconnectEnable, int reconnectPeriod, int reconnectNum, int selfConnect);
         
Pobranie parametrów komunikacji UDP osi rozszerzonej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Pobiera parametry komunikacji UDP osi rozszerzonej
    * @param [out] ip Adres IP PLC
    * @param [out] port Numer portu
    * @param [out] period Okres komunikacji (ms, domyślnie 2, nie modyfikować tego parametru)
    * @param [out] lossPkgTime Czas wykrywania utraty pakietów (ms)
    * @param [out] lossPkgNum Liczba utraconych pakietów
    * @param [out] disconnectTime Czas potwierdzenia przerwania komunikacji
    * @param [out] reconnectEnable Włączenie automatycznego ponownego łączenia po przerwaniu komunikacji 0-niewłączone 1-włączone
    * @param [out] reconnectPeriod Odstęp między próbami ponownego połączenia (ms)
    * @param [out] reconnectNum Liczba prób ponownego połączenia
    * @param [out] selfConnect Czy automatycznie ponownie łączyć po ponownym uruchomieniu skrzynki sterowniczej; 0-nie łącz; 1-łącz
    * @return Kod błędu
    */
    public int ExtDevGetUDPComParam(ref string ip, ref int port, ref int period, ref int lossPkgTime, ref int lossPkgNum, ref int disconnectTime, ref int reconnectEnable, ref int reconnectPeriod, ref int reconnectNum, ref int selfConnect)
        
Ładowanie komunikacji UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Ładuje komunikację UDP
    * @return Kod błędu
    */
    int ExtDevLoadUDPDriver();

Rozładowanie komunikacji UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Rozładowuje komunikację UDP
    * @return Kod błędu
    */
    int ExtDevUnloadUDPDriver();

Przywrócenie połączenia po przerwaniu komunikacji UDP osi rozszerzonej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Przywraca połączenie po przerwaniu komunikacji UDP osi rozszerzonej
    * @return Kod błędu
    */
    int ExtDevUDPClientComReset();

Zamknięcie komunikacji po przerwaniu komunikacji UDP osi rozszerzonej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Zamyka komunikację po przerwaniu komunikacji UDP osi rozszerzonej
    * @return Kod błędu
    */
    int ExtDevUDPClientComClose();

Konfiguracja parametrów UDP osi rozszerzonej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Konfiguracja parametrów UDP osi rozszerzonej
    * @param [in] axisID Numer osi
    * @param [in] axisType Typ osi rozszerzonej 0-przesuw; 1-obrót
    * @param [in] axisDirection Kierunek osi rozszerzonej 0-dodatni; 1-ujemny 
    * @param [in] axisMax Maksymalna pozycja osi rozszerzonej mm
    * @param [in] axisMin Minimalna pozycja osi rozszerzonej mm
    * @param [in] axisVel Prędkość mm/s
    * @param [in] axisAcc Przyspieszenie mm/s²
    * @param [in] axisLead Skok mm
    * @param [in] encResolution Rozdzielczość enkodera
    * @param [in] axisOffect Przesunięcie osi rozszerzonej punktu początkowego spoiny
    * @param [in] axisCompany Producent napędu 1-Hochuan; 2-Inovance; 3-Panasonic
    * @param [in] axisModel Model napędu 1-Hochuan-SV-XD3EA040L-E, 2-Hochuan-SV-X2EA150A-A, 1-Inovance-SV620PT5R4I, 1-Panasonic-MADLN15SG, 2-Panasonic-MSDLN25SG, 3-Panasonic-MCDLN35SG
    * @param [in] axisEncType Typ enkodera 0-inkrementalny; 1-absolutny
    * @return Kod błędu
    */
    int ExtAxisParamConfig(int axisID, int axisType, int axisDirection, double axisMax, double axisMin, double axisVel, double axisAcc, double axisLead, long encResolution, double axisOffect, int axisCompany, int axisModel, int axisEncType);

Pobranie parametrów UDP osi rozszerzonej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: C#
    :linenos:

    /**
    * @brief Pobranie parametrów UDP osi rozszerzonej
    * @param [in] axisID Numer osi rozszerzonej [1-4]
    * @param [out] axisType Typ osi rozszerzonej 0-przesuw; 1-obrót
    * @param [out] axisDirection Kierunek osi rozszerzonej 0-dodatni; 1-ujemny
    * @param [out] axisMax Maksymalna pozycja osi rozszerzonej mm
    * @param [out] axisMin Minimalna pozycja osi rozszerzonej mm
    * @param [out] axisVel Prędkość mm/s
    * @param [out] axisAcc Przyspieszenie mm/s²
    * @param [out] axisLead Skok mm
    * @param [out] encResolution Rozdzielczość enkodera
    * @param [out] axisOffect Przesunięcie osi rozszerzonej punktu początkowego spoiny
    * @param [out] axisCompany Producent napędu 1-Hochuan; 2-Inovance; 3-Panasonic
    * @param [out] axisModel Model napędu 1-Hochuan-SV-XD3EA040L-E, 2-Hochuan-SV-X2EA150A-A, 1-Inovance-SV620PT5R4I, 1-Panasonic-MADLN15SG, 2-Panasonic-MSDLN25SG, 3-Panasonic-MCDLN35SG
    * @param [out] axisEncType Typ enkodera 0-inkrementalny; 1-absolutny
    * @return Kod błędu
    */
    public int ExtAxisGetParamConfig(int axisID, ref int axisType, ref int axisDirection, ref double axisMax, ref double axisMin, ref double axisVel, ref double axisAcc, ref double axisLead, ref int encResolution, ref double axisOffect, ref int axisCompany, ref int axisModel, ref int axisEncType)

Ustawienie pozycji instalacji osi rozszerzonej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Ustawia pozycję instalacji osi rozszerzonej
    * @param [in] installType 0-robot zainstalowany na zewnętrznej osi, 1-robot zainstalowany poza zewnętrzną osią
    * @return Kod błędu
    */
    int SetRobotPosToAxis(int installType);

Konfiguracja parametrów DH systemu osi rozszerzonej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Konfiguracja parametrów DH systemu osi rozszerzonej
    * @param [in]  axisConfig Konfiguracja zewnętrznej osi, 0-prosta szyna przesuwna o jednym stopniu swobody, 1-pozycjoner L o dwóch stopniach swobody, 2-trzech stopniach, 3-czterech stopniach, 4-pozycjoner o jednym stopniu swobody
    * @param [in]  axisDHd1 Parametr DH zewnętrznej osi d1 mm
    * @param [in]  axisDHd2 Parametr DH zewnętrznej osi d2 mm
    * @param [in]  axisDHd3 Parametr DH zewnętrznej osi d3 mm
    * @param [in]  axisDHd4 Parametr DH zewnętrznej osi d4 mm
    * @param [in]  axisDHa1 Parametr DH zewnętrznej osi a1 mm
    * @param [in]  axisDHa2 Parametr DH zewnętrznej osi a2 mm
    * @param [in]  axisDHa3 Parametr DH zewnętrznej osi a3 mm
    * @param [in]  axisDHa4 Parametr DH zewnętrznej osi a4 mm
    * @return Kod błędu
    */
    int SetAxisDHParaConfig(int axisConfig, double axisDHd1, double axisDHd2, double axisDHd3, double axisDHd4, double axisDHa1, double axisDHa2, double axisDHa3, double axisDHa4);

Załączenie UDP osi rozszerzonej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Załączenie UDP osi rozszerzonej
    * @param [in] axisID Numer osi [1-4]
    * @param [in] status 0-odłączenie; 1-załączenie
    * @return Kod błędu
    */
    int ExtAxisServoOn(int axisID, int status);

Powrót do zera UDP osi rozszerzonej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Powrót do zera UDP osi rozszerzonej
    * @param [in] axisID Numer osi [1-4]
    * @param [in] mode Sposób powrotu do zera 0-powrót do zera z bieżącej pozycji, 1-powrót do zera z ogranicznikiem ujemnym, 2-powrót do zera z ogranicznikiem dodatnim
    * @param [in] searchVel Prędkość poszukiwania zera (mm/s)
    * @param [in] latchVel Prędkość pozycjonowania w zerze (mm/s)
    * @return Kod błędu
    */
    int ExtAxisSetHoming(int axisID, int mode, double searchVel, double latchVel);

Rozpoczęcie punktowania UDP osi rozszerzonej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Rozpoczęcie punktowania UDP osi rozszerzonej
    * @param [in] axisID Numer osi [1-4]
    * @param [in] direction Kierunek obrotu 0-wsteczny; 1-do przodu
    * @param [in] vel Prędkość (mm/s)
    * @param [in] acc Przyspieszenie (mm/s²)
    * @param [in] maxDistance Maksymalna odległość punktowania
    * @return Kod błędu
    */
    int ExtAxisStartJog(int axisID, int direction, double vel, double acc, double maxDistance);
    
Zatrzymanie punktowania UDP osi rozszerzonej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Zatrzymanie punktowania UDP osi rozszerzonej
    * @param [in] axisID Numer osi [1-4]
    * @return Kod błędu
    */
    int ExtAxisStopJog(int axisID);

Przykład kodu konfiguracji i punktowania UDP osi rozszerzonej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: C#
    :linenos:

    private void button65_Click(object sender, EventArgs e)
    {
        int rtn = robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 200, 1, 100, 5, 1);
        Console.WriteLine("ExtDevSetUDPComParam rtn is " + rtn);
        string ip = ""; int port = 0; int period = 0; int lossPkgTime = 0; int lossPkgNum = 0; int disconnectTime = 0; int reconnectEnable = 0; int reconnectPeriod = 0; int reconnectNum = 0; int selfConnect = 0;
        rtn = robot.ExtDevGetUDPComParam(ref ip, ref port, ref period, ref lossPkgTime, ref lossPkgNum, ref disconnectTime, ref reconnectEnable, ref reconnectPeriod, ref reconnectNum, ref selfConnect);
        string param = "\nip " + ip + "\nport " + port.ToString() + "\nperiod  " + period.ToString() + "\nlossPkgTime " + lossPkgTime.ToString() + "\nlossPkgNum  " + lossPkgNum.ToString() + "\ndisConntime  " + disconnectTime.ToString() + "\nreconnecable  " + reconnectEnable.ToString() + "\nreconnperiod  " + reconnectPeriod.ToString() + "\nreconnnun  " + reconnectNum.ToString() + "\nselfConnect  " + selfConnect.ToString();
        Console.WriteLine("ExtDevGetUDPComParam rtn is " + rtn + param);

        robot.ExtDevLoadUDPDriver();

        rtn = robot.ExtAxisServoOn(1, 1);
        Console.WriteLine("ExtAxisServoOn axis id 1 rtn is " + rtn);
        rtn = robot.ExtAxisServoOn(2, 1);
        Console.WriteLine("ExtAxisServoOn axis id 2 rtn is " + rtn);
        Thread.Sleep(2000);

        rtn = robot.ExtAxisSetHoming(1, 0, 10, 2);
        Console.WriteLine("ExtAxisSetHoming 1 rtnn is  " + rtn);
        Thread.Sleep(2000);
        rtn = robot.ExtAxisSetHoming(2, 0, 10, 2);
        Console.WriteLine("ExtAxisSetHoming 2 rtnn is  " + rtn);

        Thread.Sleep(4000);

        rtn = robot.SetRobotPosToAxis(1);
        Console.WriteLine("SetRobotPosToAxis rtn is " + rtn);
        rtn = robot.SetAxisDHParaConfig(10, 20, 0, 0, 0, 0, 0, 0, 0);
        Console.WriteLine("SetAxisDHParaConfig rtn is " + rtn);


        int axisType = -1;
        int axisDirection = -1;
        double axisMax = -1;
        double axisMin = -1;
        double axisVel = -1;
        double axisAcc = -1;
        double axisLead = -1;
        int encResolution = -1;
        double axisOffect = -1;
        int axisCompany = -1;
        int axisModel = -1;
        int axisEncType = -1;

        rtn = robot.ExtAxisParamConfig(1, 1, 1, 1000, -1000, 1000, 1000, 1.905f, 262144, 200, 1, 0, 0);
        Console.WriteLine("ExtAxisParamConfig axis 1 rtn is " + rtn);
        rtn = robot.ExtAxisGetParamConfig(1, ref axisType, ref axisDirection, ref axisMax, ref axisMin, ref axisVel, ref axisAcc, ref axisLead, ref encResolution, ref axisOffect, ref axisCompany, ref axisModel, ref axisEncType);
        Console.WriteLine($"axis id 1 ExtAxisGetParamConfig : axisType {axisType}, axisDirection {axisDirection}, axisMax {axisMax}, axisMin {axisMin}, axisVel {axisVel}, axisAcc {axisAcc}, axisLead {axisLead}, encResolution {encResolution}, axisOffect {axisOffect}, axisCompany {axisCompany}, axisModel {axisModel}, axisEncType {axisEncType}\n");
                                                                                                                                                                                    

        rtn = robot.ExtAxisParamConfig(2, 1, 1, 1000, -1000, 1000, 1000, 4.444f, 262144, 200, 1, 0, 0);
        Console.WriteLine("ExtAxisParamConfig axis 2 rtn is " + rtn);
        rtn = robot.ExtAxisGetParamConfig(2, ref axisType, ref axisDirection, ref axisMax,  ref axisMin, ref axisVel, ref axisAcc, ref axisLead, ref encResolution, ref axisOffect, ref axisCompany, ref axisModel, ref axisEncType);
        Console.WriteLine($"axis id 2 ExtAxisGetParamConfig : axisType {axisType}, axisDirection {axisDirection}, axisMax {axisMax}, axisMin {axisMin}, axisVel {axisVel}, axisAcc {axisAcc}, axisLead {axisLead}, encResolution {encResolution}, axisOffect {axisOffect}, axisCompany {axisCompany}, axisModel {axisModel}, axisEncType {axisEncType}\n");


        Thread.Sleep(3000);
        robot.ExtAxisStartJog(1, 0, 10, 10, 30);
        Thread.Sleep(1000);
        robot.ExtAxisStopJog(1);
        Thread.Sleep(3000);
        robot.ExtAxisServoOn(1, 0);

        Thread.Sleep(3000);
        robot.ExtAxisStartJog(2, 0, 10, 10, 30);
        Thread.Sleep(1000);
        robot.ExtAxisStopJog(2);
        Thread.Sleep(3000);
        robot.ExtAxisServoOn(2, 0);
        Thread.Sleep(3000);
        robot.ExtDevUnloadUDPDriver();
    }

Ustawienie punktu odniesienia układu współrzędnych osi rozszerzonej - metoda czteropunktowa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Ustawia punkt odniesienia układu współrzędnych osi rozszerzonej - metoda czteropunktowa
    * @param [in] pointNum Numer punktu [1-4]
    * @return Kod błędu
    */
    int ExtAxisSetRefPoint(int pointNum);

Obliczenie układu współrzędnych osi rozszerzonej - metoda czteropunktowa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Oblicza układ współrzędnych osi rozszerzonej - metoda czteropunktowa
    * @param [out] coord Wartości układu współrzędnych
    * @return Kod błędu
    */
    int ExtAxisComputeECoordSys(DescPose& coord);

Zastosowanie układu współrzędnych osi rozszerzonej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Zastosowanie układu współrzędnych osi rozszerzonej
    * @param [in] applyAxisId Numer osi rozszerzonej bit0-bit3 odpowiada numerom osi rozszerzonej 1-4, np. zastosowanie osi rozszerzonej 1 i 3 to 0b 0000 0101, czyli 5
    * @param [in] axisCoordNum Numer układu współrzędnych osi rozszerzonej
    * @param [in] coord Wartości układu współrzędnych
    * @param [in] calibFlag Znacznik kalibracji 0-nie, 1-tak
    * @return Kod błędu
    */
    int ExtAxisActiveECoordSys(int applyAxisId, int axisCoordNum, DescPose coord, int calibFlag);

Ustawienie pozycji punktu odniesienia kalibracji w układzie współrzędnych końcówki pozycjonera
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Ustawia pozycję punktu odniesienia kalibracji w układzie współrzędnych końcówki pozycjonera
    * @param [in] pos Wartości pozycji i orientacji
    * @return Kod błędu
    */
    int SetRefPointInExAxisEnd(DescPose pos);

Ustawienie punktu odniesienia układu współrzędnych pozycjonera
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Ustawienie punktu odniesienia układu współrzędnych pozycjonera
    * @param [in] pointNum Numer punktu [1-4]
    * @return Kod błędu
    */
    int PositionorSetRefPoint(int pointNum);

Obliczenie układu współrzędnych pozycjonera - metoda czteropunktowa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Obliczenie układu współrzędnych pozycjonera - metoda czteropunktowa
    * @param [out] coord Wartości układu współrzędnych
    * @return Kod błędu
    */
    int PositionorComputeECoordSys(DescPose& coord);

Pobranie układu współrzędnych osi rozszerzonej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Pobiera układ współrzędnych osi rozszerzonej
    * @param [out] coord Układ współrzędnych osi rozszerzonej
    * @return Kod błędu
    */
    int ExtAxisGetCoord(ref DescPose coord);

Przykład kodu kalibracji układu współrzędnych osi rozszerzonej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:

    private void button66_Click(object sender, EventArgs e)
    {
        int rtn = robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 200, 1, 100, 5,1);
        Console.WriteLine("ExtDevSetUDPComParam rtn is " + rtn);
        string ip = ""; int port = 0; int period = 0; int lossPkgTime = 0; int lossPkgNum = 0; int disconnectTime = 0; int reconnectEnable = 0; int reconnectPeriod = 0; int reconnectNum = 0;
        rtn = robot.ExtDevGetUDPComParam(ref ip, ref port, ref period, ref lossPkgTime, ref lossPkgNum, ref disconnectTime, ref reconnectEnable, ref reconnectPeriod, ref reconnectNum);
        string param = "\nip " + ip + "\nport " + port.ToString() + "\nperiod  " + period.ToString() + "\nlossPkgTime " + lossPkgTime.ToString() + "\nlossPkgNum  " + lossPkgNum.ToString() + "\ndisConntime  " + disconnectTime.ToString() + "\nreconnecable  " + reconnectEnable.ToString() + "\nreconnperiod  " + reconnectPeriod.ToString() + "\nreconnnun  " + reconnectNum.ToString();
        Console.WriteLine("ExtDevGetUDPComParam rtn is " + rtn + param);

        robot.ExtDevLoadUDPDriver();

        rtn = robot.ExtAxisServoOn(1, 1);
        Console.WriteLine("ExtAxisServoOn axis id 1 rtn is " + rtn);
        rtn = robot.ExtAxisServoOn(2, 1);
        Console.WriteLine("ExtAxisServoOn axis id 2 rtn is " + rtn);
        Thread.Sleep(2000);

        robot.ExtAxisSetHoming(1, 0, 10, 2);
        Thread.Sleep(2000);
        rtn = robot.ExtAxisSetHoming(2, 0, 10, 2);
        Console.WriteLine("ExtAxisSetHoming rtnn is  " + rtn);

        Thread.Sleep(4000);

        rtn = robot.SetRobotPosToAxis(1);
        Console.WriteLine("SetRobotPosToAxis rtn is " + rtn);
        rtn = robot.SetAxisDHParaConfig(1, 128.5f, 206.4f, 0, 0, 0, 0, 0, 0);
        Console.WriteLine("SetAxisDHParaConfig rtn is " + rtn);
        rtn = robot.ExtAxisParamConfig(1, 1, 1, 1000, -1000, 1000, 1000, 1.905f, 262144, 200, 1, 0, 0);
        Console.WriteLine("ExtAxisParamConfig axis 1 rtn is " + rtn);
        rtn = robot.ExtAxisParamConfig(2, 1, 1, 1000, -1000, 1000, 1000, 4.444f, 262144, 200, 1, 0, 0);
        Console.WriteLine("ExtAxisParamConfig axis 1 rtn is " + rtn);

        DescPose toolCoord = new DescPose(0, 0, 210, 0, 0, 0);
        robot.SetToolCoord(1, toolCoord, 0, 0, 1, 0);

        JointPos jSafe = new JointPos(115.193f, -96.149f, 92.489f, -87.068f, -89.15f, -83.488f);
        JointPos j1 = new JointPos(117.559f, -92.624f, 100.329f, -96.909f, -94.057f, -83.488f);
        JointPos j2 = new JointPos(112.239f, -90.096f, 99.282f, -95.909f, -89.824f, -83.488f);
        JointPos j3 = new JointPos(110.839f, -83.473f, 93.166f, -89.22f, -90.499f, -83.487f);
        JointPos j4 = new JointPos(107.935f, -83.572f, 95.424f, -92.873f, -87.933f, -83.488f);

        DescPose descSafe = new DescPose();
        DescPose desc1 = new DescPose();
        DescPose desc2 = new DescPose();
        DescPose desc3 = new DescPose();
        DescPose desc4 = new DescPose();
        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        robot.GetForwardKin( jSafe,  ref descSafe);
        robot.MoveJ( jSafe,  descSafe, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        Thread.Sleep(2000);

        robot.GetForwardKin( j1, ref desc1);
        robot.MoveJ( j1,  desc1, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        Thread.Sleep(2000);

        DescPose actualTCPPos = new DescPose();
        robot.GetActualTCPPose(0, ref actualTCPPos);
        robot.SetRefPointInExAxisEnd(actualTCPPos);
        rtn = robot.PositionorSetRefPoint(1);
        Console.WriteLine("PositionorSetRefPoint 1 rtn is " + rtn);
        Thread.Sleep(2000);

        robot.MoveJ( jSafe,  descSafe, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.ExtAxisStartJog(1, 0, 50, 50, 10);
        Thread.Sleep(1000);
        robot.ExtAxisStartJog(2, 0, 50, 50, 10);
        Thread.Sleep(1000);
        robot.GetForwardKin( j2, ref desc2);
        rtn = robot.MoveJ( j2,  desc2, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        rtn = robot.PositionorSetRefPoint(2);
        Console.WriteLine("PositionorSetRefPoint 2 rtn is " + rtn);
        Thread.Sleep(2000);

        robot.MoveJ( jSafe,  descSafe, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.ExtAxisStartJog(1, 0, 50, 50, 10);
        Thread.Sleep(1000);
        robot.ExtAxisStartJog(2, 0, 50, 50, 10);
        Thread.Sleep(1000);
        robot.GetForwardKin( j3, ref desc3);
        robot.MoveJ( j3,  desc3, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        rtn = robot.PositionorSetRefPoint(3);
        Console.WriteLine("PositionorSetRefPoint 3 rtn is " + rtn);
        Thread.Sleep(2000);

        robot.MoveJ( jSafe,  descSafe, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.ExtAxisStartJog(1, 0, 50, 50, 10);
        Thread.Sleep(1000);
        robot.ExtAxisStartJog(2, 0, 50, 50, 10);
        Thread.Sleep(1000);
        robot.GetForwardKin(j4, ref desc4);
        robot.MoveJ(j4, desc4, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        rtn = robot.PositionorSetRefPoint(4);
        Console.WriteLine("PositionorSetRefPoint 4 rtn is " + rtn);
        Thread.Sleep(2000);

        DescPose axisCoord = new DescPose();
        robot.PositionorComputeECoordSys(ref axisCoord);
        robot.MoveJ(jSafe, descSafe, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        Console.WriteLine("PositionorComputeECoordSys rtn is {0} {1} {2} {3} {4} {5}", axisCoord.tran.x, axisCoord.tran.y, axisCoord.tran.z, axisCoord.rpy.rx, axisCoord.rpy.ry, axisCoord.rpy.rz);
        rtn = robot.ExtAxisActiveECoordSys(3, 1, axisCoord, 1);
        Console.WriteLine("ExtAxisActiveECoordSys rtn is " + rtn);
    }

Ruch UDP osi rozszerzonej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4

.. code-block:: C#
    :linenos:

    /**
    * @brief Ruch UDP osi rozszerzonej
    * @param [in] pos Pozycja docelowa
    * @param [in] ovl Procent prędkości
    * @param [in] blend Parametr wygładzenia (mm lub ms)
    * @return Kod błędu
    */
    int ExtAxisMove(ExaxisPos pos, double ovl, double blend=-1);

Przykład kodu ruchu UDP osi rozszerzonej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: C#
    :linenos:

    private void button66_Click(object sender, EventArgs e)
    {
        ExaxisPos axisPos;
        axisPos.ePos[0] = 20;
        axisPos.ePos[1] = 0;
        axisPos.ePos[2] = 0;
        axisPos.ePos[3] = 0;
        robot.ExtAxisMove(axisPos, 50);
    }

Ruch synchroniczny UDP osi rozszerzonej z ruchem stawowym robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Ruch synchroniczny UDP osi rozszerzonej z ruchem stawowym robota
    * @param [in] joint_pos Docelowa pozycja stawów, jednostka deg
    * @param [in] desc_pos Docelowa pozycja i orientacja kartezjańska
    * @param [in] tool Numer układu współrzędnych narzędzia, zakres [0~14]
    * @param [in] user Numer układu współrzędnych przedmiotu, zakres [0~14]
    * @param [in] vel Procent prędkości, zakres [0~100]
    * @param [in] acc Procent przyspieszenia, zakres [0~100], tymczasowo nieudostępnione
    * @param [in] ovl Współczynnik skalowania prędkości, zakres [0~100]
    * @param [in] epos Pozycja osi rozszerzonej, jednostka mm
    * @param [in] blendT [-1.0]-ruch do pozycji (blokujący), [0~500.0]-czas wygładzenia (nieblokujący), jednostka ms
    * @param [in] offset_flag 0-brak przesunięcia, 1-przesunięcie w podstawowym układzie współrzędnych / układzie współrzędnych przedmiotu, 2-przesunięcie w układzie współrzędnych narzędzia
    * @param [in] offset_pos Wartość przesunięcia pozycji i orientacji
    * @return  Kod błędu
    */
    int ExtAxisSyncMoveJ(JointPos joint_pos, DescPose desc_pos, int tool, int user, float vel, float acc, float ovl, ExaxisPos epos, float blendT, byte offset_flag, DescPose offset_pos);

Przykład kodu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: C#
    :linenos:

    private void btnSyncMoveJ_Click(object sender, EventArgs e)
    {
        Robot robot = new Robot();
        robot.RPC("192.168.58.2");

        //1. Kalibracja i zastosowanie układu współrzędnych narzędzia robota. Możesz użyć metody czteropunktowej lub sześciopunktowej do kalibracji i zastosowania układu współrzędnych narzędzia. Interfejsy związane z kalibracją układu współrzędnych narzędzia są następujące:
        //    int SetToolPoint(int point_num);  // Ustawienie punktu odniesienia narzędzia - metoda sześciopunktowa
        //    int ComputeTool(ref DescPose tcp_pose);  // Obliczenie układu współrzędnych narzędzia
        //    int SetTcp4RefPoint(int point_num);    // Ustawienie punktu odniesienia narzędzia - metoda czteropunktowa
        //    int ComputeTcp4(ref DescPose tcp_pose);   // Obliczenie układu współrzędnych narzędzia - metoda czteropunktowa
        //    int SetToolCoord(int id, DescPose coord, int type, int install);  // Ustawienie i zastosowanie układu współrzędnych narzędzia
        //    int SetToolList(int id, DescPose coord, int type, int install);   // Ustawienie listy układów współrzędnych narzędzia

        //2. Ustawienie parametrów komunikacji UDP i załadowanie komunikacji UDP
        robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10);
        robot.ExtDevLoadUDPDriver();

        //3. Ustawienie parametrów osi rozszerzonej, w tym typu osi rozszerzonej, parametrów napędu osi rozszerzonej, parametrów DH osi rozszerzonej
        robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0); // Pozycjoner jednoosiowy i parametry DH
        robot.SetRobotPosToAxis(1);  // Pozycja instalacji osi rozszerzonej
        robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0); // Parametry napędu, w tym przykładzie dla pozycjonera jednoosiowego, wystarczy ustawić parametry jednego napędu. Jeśli wybierzesz typ osi rozszerzonej zawierający wiele osi, musisz ustawić parametry napędu dla każdej osi.

        //4. Załączenie wybranej osi, powrót do zera
        robot.ExtAxisServoOn(1, 0);
        robot.ExtAxisSetHoming(1, 0, 20, 3);

        //5. Kalibracja układu współrzędnych osi rozszerzonej i zastosowanie (uwaga: interfejsy kalibracji dla pozycjonera i szyny przesuwnej są różne, poniżej przedstawiono interfejsy dla pozycjonera)
        DescPose pos = new DescPose(/* Wprowadź współrzędne swojego punktu kalibracji */);
        robot.SetRefPointInExAxisEnd(pos);
        robot.PositionorSetRefPoint(1); /* Musisz skalibrować oś rozszerzoną za pomocą czterech punktów w różnych pozycjach, więc musisz wywołać ten interfejs 4 razy, aby zakończyć kalibrację */
        DescPose coord = new DescPose( );
        robot.PositionorComputeECoordSys(ref coord); // Obliczenie wyniku kalibracji osi rozszerzonej
        robot.ExtAxisActiveECoordSys(1, 1, coord, 1);  // Zastosowanie wyniku kalibracji do układu współrzędnych osi rozszerzonej

        //6. Kalibracja układu współrzędnych przedmiotu na osi rozszerzonej, będziesz potrzebować następujących interfejsów
        //int SetWObjCoordPoint(int point_num);
        //int ComputeWObjCoord(int method, ref DescPose wobj_pose);
        //int SetWObjCoord(int id, DescPose coord);
        //int SetWObjList(int id, DescPose coord);

        //7. Zapisz punkt początkowy ruchu synchronicznego stawów
        DescPose startdescPose = new DescPose(/*Wprowadź swoje współrzędne*/);
        JointPos startjointPos = new JointPos(/*Wprowadź swoje współrzędne*/);
        ExaxisPos startexaxisPos = new ExaxisPos(/* Wprowadź współrzędne punktu początkowego osi rozszerzonej */);

        //8. Zapisz współrzędne punktu końcowego ruchu synchronicznego stawów
        DescPose enddescPose = new DescPose(/*Wprowadź swoje współrzędne*/);
        JointPos endjointPos = new JointPos(/*Wprowadź swoje współrzędne*/);
        ExaxisPos endexaxisPos = new ExaxisPos(/* Wprowadź współrzędne punktu końcowego osi rozszerzonej */);

        //9. Napisz program ruchu synchronicznego
        // Ruch do punktu początkowego, zakładając, że zastosowany układ współrzędnych narzędzia i przedmiotu to 1
        robot.ExtAxisMove(startexaxisPos, 20);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);
        robot.MoveJ(startjointPos, startdescPose, 1, 1, 100, 100, 100, startexaxisPos, 0, 0, offdese);

        // Rozpocznij ruch synchroniczny
        robot.ExtAxisSyncMoveJ(endjointPos, enddescPose, 1, 1, 100, 100, 100, endexaxisPos, -1, 0, offdese);
    }

Ruch synchroniczny UDP osi rozszerzonej z ruchem liniowym robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Ruch synchroniczny UDP osi rozszerzonej z ruchem liniowym robota
    * @param [in] joint_pos  Docelowa pozycja stawów, jednostka deg
    * @param [in] desc_pos   Docelowa pozycja i orientacja kartezjańska
    * @param [in] tool  Numer układu współrzędnych narzędzia, zakres [0~14]
    * @param [in] user  Numer układu współrzędnych przedmiotu, zakres [0~14]
    * @param [in] vel  Procent prędkości, zakres [0~100]
    * @param [in] acc  Procent przyspieszenia, zakres [0~100], tymczasowo nieudostępnione
    * @param [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]
    * @param [in] blendR [-1.0]-ruch do pozycji (blokujący), [0~1000.0]-promień wygładzenia (nieblokujący), jednostka mm
    * @param [in] epos  Pozycja osi rozszerzonej, jednostka mm
    * @param [in] offset_flag  0-brak przesunięcia, 1-przesunięcie w podstawowym układzie współrzędnych / układzie współrzędnych przedmiotu, 2-przesunięcie w układzie współrzędnych narzędzia
    * @param [in] offset_pos  Wartość przesunięcia pozycji i orientacji
    * @return Kod błędu
    */
    int ExtAxisSyncMoveL(JointPos joint_pos, DescPose desc_pos, int tool, int user, float vel, float acc, float ovl, float blendR, ExaxisPos epos, int offset_flag, DescPose offset_pos);

Przykład kodu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: C#
    :linenos:

    private void btnSyncMoveL_Click(object sender, EventArgs e)
    {
        Robot robot = new Robot();
        robot.RPC("192.168.58.2");

    //1. Kalibracja i zastosowanie układu współrzędnych narzędzia robota. Możesz użyć metody czteropunktowej lub sześciopunktowej do kalibracji i zastosowania układu współrzędnych narzędzia. Interfejsy związane z kalibracją układu współrzędnych narzędzia są następujące:
        //    int SetToolPoint(int point_num);  // Ustawienie punktu odniesienia narzędzia - metoda sześciopunktowa
        //    int ComputeTool(ref DescPose tcp_pose);  // Obliczenie układu współrzędnych narzędzia
        //    int SetTcp4RefPoint(int point_num);    // Ustawienie punktu odniesienia narzędzia - metoda czteropunktowa
        //    int ComputeTcp4(ref DescPose tcp_pose);   // Obliczenie układu współrzędnych narzędzia - metoda czteropunktowa
        //    int SetToolCoord(int id, DescPose coord, int type, int install);  // Ustawienie i zastosowanie układu współrzędnych narzędzia
        //    int SetToolList(int id, DescPose coord, int type, int install);   // Ustawienie listy układów współrzędnych narzędzia

        //2. Ustawienie parametrów komunikacji UDP i załadowanie komunikacji UDP
        robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10);
        robot.ExtDevLoadUDPDriver();

        //3. Ustawienie parametrów osi rozszerzonej, w tym typu osi rozszerzonej, parametrów napędu osi rozszerzonej, parametrów DH osi rozszerzonej
        robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0); // Pozycjoner jednoosiowy i parametry DH
        robot.SetRobotPosToAxis(1);  // Pozycja instalacji osi rozszerzonej
        robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0); // Parametry napędu, w tym przykładzie dla pozycjonera jednoosiowego, wystarczy ustawić parametry jednego napędu. Jeśli wybierzesz typ osi rozszerzonej zawierający wiele osi, musisz ustawić parametry napędu dla każdej osi.

        //4. Załączenie wybranej osi, powrót do zera
        robot.ExtAxisServoOn(1, 0);
        robot.ExtAxisSetHoming(1, 0, 20, 3);

        //5. Kalibracja układu współrzędnych osi rozszerzonej i zastosowanie
        DescPose pos = new DescPose(/* Wprowadź współrzędne swojego punktu kalibracji */);
        robot.SetRefPointInExAxisEnd(pos);
        robot.PositionorSetRefPoint(1); /* Musisz skalibrować oś rozszerzoną za pomocą czterech punktów w różnych pozycjach, więc musisz wywołać ten interfejs 4 razy, aby zakończyć kalibrację */
        DescPose coord = new DescPose();
        robot.PositionorComputeECoordSys(ref coord); // Obliczenie wyniku kalibracji osi rozszerzonej
        robot.ExtAxisActiveECoordSys(1, 1, coord, 1);  // Zastosowanie wyniku kalibracji do układu współrzędnych osi rozszerzonej

        //6. Kalibracja układu współrzędnych przedmiotu na osi rozszerzonej, będziesz potrzebować następujących interfejsów
        //int SetWObjCoordPoint(int point_num);
        //int ComputeWObjCoord(int method, ref DescPose wobj_pose);
        //int SetWObjCoord(int id, DescPose coord);
        //int SetWObjList(int id, DescPose coord);

        //7. Zapisz punkt początkowy ruchu synchronicznego liniowego
        DescPose startdescPose = new DescPose(/*Wprowadź swoje współrzędne*/);
        JointPos startjointPos = new JointPos(/*Wprowadź swoje współrzędne*/);
        ExaxisPos startexaxisPos = new ExaxisPos(/* Wprowadź współrzędne punktu początkowego osi rozszerzonej */);

        //8. Zapisz współrzędne punktu końcowego ruchu synchronicznego liniowego
        DescPose enddescPose = new DescPose(/*Wprowadź swoje współrzędne*/);
        JointPos endjointPos = new JointPos(/*Wprowadź swoje współrzędne*/);
        ExaxisPos endexaxisPos = new ExaxisPos(/* Wprowadź współrzędne punktu końcowego osi rozszerzonej */);

        //9. Napisz program ruchu synchronicznego
        // Ruch do punktu początkowego, zakładając, że zastosowany układ współrzędnych narzędzia i przedmiotu to 1
        robot.ExtAxisMove(startexaxisPos, 20);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);
        robot.MoveJ(startjointPos, startdescPose, 1, 1, 100, 100, 100, startexaxisPos, 0, 0, offdese);

        // Rozpocznij ruch synchroniczny
        robot.ExtAxisSyncMoveL(endjointPos, enddescPose, 1, 1, 100, 100, 100, 0, endexaxisPos, 0, offdese);
    }
    
Ruch synchroniczny UDP osi rozszerzonej z ruchem łukowym robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Ruch synchroniczny UDP osi rozszerzonej z ruchem łukowym robota
    * @param [in] joint_pos_p  Pozycja stawów punktu pośredniego, jednostka deg
    * @param [in] desc_pos_p   Pozycja i orientacja kartezjańska punktu pośredniego
    * @param [in] ptool  Numer układu współrzędnych narzędzia, zakres [0~14]
    * @param [in] puser  Numer układu współrzędnych przedmiotu, zakres [0~14]
    * @param [in] pvel  Procent prędkości, zakres [0~100]
    * @param [in] pacc  Procent przyspieszenia, zakres [0~100], tymczasowo nieudostępnione
    * @param [in] epos_p  Pozycja osi rozszerzonej punktu pośredniego, jednostka mm
    * @param [in] poffset_flag  0-brak przesunięcia, 1-przesunięcie w podstawowym układzie współrzędnych / układzie współrzędnych przedmiotu, 2-przesunięcie w układzie współrzędnych narzędzia
    * @param [in] offset_pos_p  Wartość przesunięcia pozycji i orientacji
    * @param [in] joint_pos_t  Pozycja stawów punktu docelowego, jednostka deg
    * @param [in] desc_pos_t   Pozycja i orientacja kartezjańska punktu docelowego
    * @param [in] ttool  Numer układu współrzędnych narzędzia, zakres [0~14]
    * @param [in] tuser  Numer układu współrzędnych przedmiotu, zakres [0~14]
    * @param [in] tvel  Procent prędkości, zakres [0~100]
    * @param [in] tacc  Procent przyspieszenia, zakres [0~100], tymczasowo nieudostępnione
    * @param [in] epos_t  Pozycja osi rozszerzonej punktu docelowego, jednostka mm
    * @param [in] toffset_flag  0-brak przesunięcia, 1-przesunięcie w podstawowym układzie współrzędnych / układzie współrzędnych przedmiotu, 2-przesunięcie w układzie współrzędnych narzędzia
    * @param [in] offset_pos_t  Wartość przesunięcia pozycji i orientacji	 
    * @param [in] ovl  Współczynnik skalowania prędkości, zakres [0~100]
    * @param [in] blendR [-1.0]-ruch do pozycji (blokujący), [0~1000.0]-promień wygładzenia (nieblokujący), jednostka mm
    * @return Kod błędu
    */
    int ExtAxisSyncMoveC(JointPos joint_pos_p, DescPose desc_pos_p, int ptool, int puser, float pvel, float pacc, ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p, JointPos joint_pos_t, DescPose desc_pos_t, int ttool, int tuser, float tvel, float tacc, ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t, float ovl, float blendR);
    
Przykład kodu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: C#
    :linenos:

    private void btnSyncMoveC_Click(object sender, EventArgs e)
    {
        Robot robot = new Robot();
        robot.RPC("192.168.58.2");

    //1. Kalibracja i zastosowanie układu współrzędnych narzędzia robota. Możesz użyć metody czteropunktowej lub sześciopunktowej do kalibracji i zastosowania układu współrzędnych narzędzia. Interfejsy związane z kalibracją układu współrzędnych narzędzia są następujące:
        //    int SetToolPoint(int point_num);  // Ustawienie punktu odniesienia narzędzia - metoda sześciopunktowa
        //    int ComputeTool(ref DescPose tcp_pose);  // Obliczenie układu współrzędnych narzędzia
        //    int SetTcp4RefPoint(int point_num);    // Ustawienie punktu odniesienia narzędzia - metoda czteropunktowa
        //    int ComputeTcp4(ref DescPose tcp_pose);   // Obliczenie układu współrzędnych narzędzia - metoda czteropunktowa
        //    int SetToolCoord(int id, DescPose coord, int type, int install);  // Ustawienie i zastosowanie układu współrzędnych narzędzia
        //    int SetToolList(int id, DescPose coord, int type, int install);   // Ustawienie listy układów współrzędnych narzędzia

        //2. Ustawienie parametrów komunikacji UDP i załadowanie komunikacji UDP
        robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10);
        robot.ExtDevLoadUDPDriver();

        //3. Ustawienie parametrów osi rozszerzonej, w tym typu osi rozszerzonej, parametrów napędu osi rozszerzonej, parametrów DH osi rozszerzonej
        robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0); // Pozycjoner jednoosiowy i parametry DH
        robot.SetRobotPosToAxis(1);  // Pozycja instalacji osi rozszerzonej
        robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0); // Parametry napędu, w tym przykładzie dla pozycjonera jednoosiowego, wystarczy ustawić parametry jednego napędu. Jeśli wybierzesz typ osi rozszerzonej zawierający wiele osi, musisz ustawić parametry napędu dla każdej osi.

        //4. Załączenie wybranej osi, powrót do zera
        robot.ExtAxisServoOn(1, 0);
        robot.ExtAxisSetHoming(1, 0, 20, 3);

        //5. Kalibracja układu współrzędnych osi rozszerzonej i zastosowanie
        DescPose pos = new DescPose(/* Wprowadź współrzędne swojego punktu kalibracji */);
        robot.SetRefPointInExAxisEnd(pos);
        robot.PositionorSetRefPoint(1); /* Musisz skalibrować oś rozszerzoną za pomocą czterech punktów w różnych pozycjach, więc musisz wywołać ten interfejs 4 razy, aby zakończyć kalibrację */
        DescPose coord = new DescPose();
        robot.PositionorComputeECoordSys(ref coord); // Obliczenie wyniku kalibracji osi rozszerzonej
        robot.ExtAxisActiveECoordSys(1, 1, coord, 1);  // Zastosowanie wyniku kalibracji do układu współrzędnych osi rozszerzonej

        //6. Kalibracja układu współrzędnych przedmiotu na osi rozszerzonej, będziesz potrzebować następujących interfejsów
        //int SetWObjCoordPoint(int point_num);
        //int ComputeWObjCoord(int method, ref DescPose wobj_pose);
        //int SetWObjCoord(int id, DescPose coord);
        //int SetWObjList(int id, DescPose coord);

        //7. Zapisz punkt początkowy ruchu synchronicznego łukowego
        DescPose startdescPose = new DescPose(/*Wprowadź swoje współrzędne*/);
        JointPos startjointPos = new JointPos(/*Wprowadź swoje współrzędne*/);
        ExaxisPos startexaxisPos = new ExaxisPos(/* Wprowadź współrzędne punktu początkowego osi rozszerzonej */);

        //8. Zapisz współrzędne punktu końcowego ruchu synchronicznego łukowego
        DescPose enddescPose = new DescPose(/*Wprowadź swoje współrzędne*/);
        JointPos endjointPos = new JointPos(/*Wprowadź swoje współrzędne*/);
        ExaxisPos endexaxisPos = new ExaxisPos(/* Wprowadź współrzędne punktu końcowego osi rozszerzonej */);

        //8. Zapisz współrzędne punktu pośredniego ruchu synchronicznego łukowego
        DescPose middescPose = new DescPose(/*Wprowadź swoje współrzędne*/);
        JointPos midjointPos = new JointPos(/*Wprowadź swoje współrzędne*/);
        ExaxisPos midexaxisPos = new ExaxisPos(/* Wprowadź współrzędne osi rozszerzonej w punkcie pośrednim łuku robota */);

        //9. Napisz program ruchu synchronicznego
        // Ruch do punktu początkowego, zakładając, że zastosowany układ współrzędnych narzędzia i przedmiotu to 1
        robot.ExtAxisMove(startexaxisPos, 20);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);
        robot.MoveJ(startjointPos, startdescPose, 1, 1, 100, 100, 100, startexaxisPos, 0, 0, offdese);

        // Rozpocznij ruch synchroniczny
        robot.ExtAxisSyncMoveC(midjointPos, middescPose, 1, 1, 100, 100, midexaxisPos, 0, offdese, endjointPos, enddescPose, 1, 1, 100, 100, endexaxisPos, 0, offdese, 100, 0);
    }

Ustawienie rozszerzonego DO
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Ustawia rozszerzone DO
    * @param [in] DONum Numer DO
    * @param [in] bOpen Przełącznik true-wł.; false-wył.
    * @param [in] smooth Czy wygładzać
    * @param [in] block Czy blokować
    * @return Kod błędu
    */
    int SetAuxDO(int DONum, bool bOpen, bool smooth, bool block);
        
Ustawienie rozszerzonego AO
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Ustawia rozszerzone AO
    * @param [in] AONum Numer AO 
    * @param [in] value Wartość analogowa [0-4095]
    * @param [in] block Czy blokować
    * @return Kod błędu
    */
    int SetAuxAO(int AONum, double value, bool block);
            
Ustawienie czasu filtrowania wejścia rozszerzonego DI
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Ustawia czas filtrowania wejścia rozszerzonego DI
    * @param [in] filterTime Czas filtrowania (ms)
    * @return Kod błędu
    */
    int SetAuxDIFilterTime(int filterTime);

Ustawienie czasu filtrowania wejścia rozszerzonego AI
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Ustawia czas filtrowania wejścia rozszerzonego AI
    * @param [in] filterTime Czas filtrowania (ms)
    * @return Kod błędu
    */
    int SetAuxAIFilterTime(int filterTime);

Oczekiwanie na wejście rozszerzone DI
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Oczekuje na wejście rozszerzone DI
    * @param [in] DINum Numer DI
    * @param [in] bOpen Przełącznik 0-wył.; 1-wł.
    * @param [in] time Maksymalny czas oczekiwania (ms)
    * @param [in] errorAlarm Czy kontynuować ruch
    * @return Kod błędu
    */
    int WaitAuxDI(int DINum, bool bOpen, int time, bool errorAlarm);
    
Oczekiwanie na wejście rozszerzone AI
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
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
    int WaitAuxAI(int AINum, int sign, int value, int time, bool errorAlarm);
        
Pobranie wartości rozszerzonego DI
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Pobiera wartość rozszerzonego DI
    * @param [in] DINum Numer DI
    * @param [in] isNoBlock Czy blokować
    * @param [out] isOpen 0-wył.; 1-wł.
    * @return Kod błędu
    */
    int GetAuxDI(int DINum, bool isNoBlock, bool& isOpen);
            
Pobranie wartości rozszerzonego AI
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Pobiera wartość rozszerzonego AI
    * @param [in] AINum Numer AI
    * @param [in] isNoBlock Czy blokować
    * @param [in] value Wartość wejściowa
    * @return Kod błędu
    */
    int GetAuxAI(int AINum, bool isNoBlock, int& value);

Przykład kodu rozszerzonego I/O
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: C#
    :linenos:

    private void btnAODO_Click(object sender, EventArgs e)
    {
        int rtn;
        for (int i = 0; i < 128; i++)
        {
            robot.SetAuxDO(i, true, false, true);
            Thread.Sleep(100);
        }
        for (int i = 0; i < 128; i++)
        {
            robot.SetAuxDO(i, false, false, true);
            Thread.Sleep(100);
        }

        for (int i = 0; i < 409; i++)
        {
            robot.SetAuxAO(0, i * 10, true);
            robot.SetAuxAO(1, 4095 - i * 10, true);
            robot.SetAuxAO(2, i * 10, true);
            robot.SetAuxAO(3, 4095 - i * 10, true);
            Thread.Sleep(10);
        }

        robot.SetAuxDIFilterTime(10);
        robot.SetAuxAIFilterTime(0, 10);

        for (int i = 0; i < 20; i++)
        {
            bool curValue = false;
            rtn = robot.GetAuxDI(i, false, ref curValue);
            Console.WriteLine("DI" + i + "   " + curValue);
        }
        int curValueAI = -1;
        for (int i = 0; i < 4; i++)
        {
            rtn = robot.GetAuxAI(i, true, ref curValueAI);
        }

        robot.WaitAuxDI(1, false, 1000, false);
        robot.WaitAuxAI(1, 1, 132, 1000, false);
    }

Załączenie urządzenia ruchomego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.9

.. code-block:: c#
    :linenos:

    /**
    * @brief Załączenie urządzenia ruchomego
    * @param enable false-odłączenie; true-załączenie
    * @return Kod błędu
    */
    int TractorEnable(bool enable);

Zatrzymanie ruchu urządzenia ruchomego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.9

.. code-block:: c#
    :linenos:

    /**
    * @brief Zatrzymanie ruchu urządzenia ruchomego
    * @return Kod błędu
    */
    int TractorStop();

Powrót do zera urządzenia ruchomego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.9

.. code-block:: c#
    :linenos:

    /**
    * @brief Powrót do zera urządzenia ruchomego
    * @return Kod błędu
    */
    int  TractorHoming();

Ruch liniowy urządzenia ruchomego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.9

.. code-block:: c#
    :linenos:

    /**
    * @brief Ruch liniowy urządzenia ruchomego
    * @param distance Odległość ruchu liniowego (mm)
    * @param vel Procent prędkości ruchu liniowego (0-100)
    * @return Kod błędu
    */
    int TractorMoveL(double distance, double vel);

Ruch łukowy urządzenia ruchomego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.9

.. code-block:: c#
    :linenos:

    /**
    * @brief Ruch łukowy urządzenia ruchomego
    * @param radio Promień ruchu łukowego (mm)
    * @param angle Kąt ruchu łukowego (°)
    * @param vel Procent prędkości ruchu liniowego (0-100)
    * @return Kod błędu
    */
    int TractorMoveC(double radio, double angle, double vel);

Przykład kodu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    private void button6_Click(object sender, EventArgs e)
    {
        int rtn;
        robot.ExtDevSetUDPComParam("192.168.58.2", 2021, 2, 50, 5, 50, 1, 50, 10,1);
        robot.ExtDevLoadUDPDriver();
        rtn = robot.ExtAxisServoOn(1, 1);
        rtn = robot.ExtAxisServoOn(2, 1);
        Thread.Sleep(2000);
        robot.ExtAxisSetHoming(1, 0, 10, 2);
        Thread.Sleep(2000);
        rtn = robot.ExtAxisSetHoming(2, 0, 10, 2);
        Thread.Sleep(4000);
        robot.ExtAxisParamConfig(1, 0, 0, 50000, -50000, 1000, 1000, 6.280f, 16384, 200, 0, 0, 0);
        robot.ExtAxisParamConfig(2, 0, 0, 50000, -50000, 1000, 1000, 6.280f, 16384, 200, 0, 0, 0);
        robot.SetAxisDHParaConfig(5, 0, 0, 0, 0, 0, 0, 0, 0);
        robot.TractorEnable(false);
        Thread.Sleep(2000);
        robot.TractorEnable(true);
        Thread.Sleep(2000);
        robot.TractorHoming();
        Thread.Sleep(2000);
        robot.TractorMoveL(100, 2);
        Thread.Sleep(5000);
        robot.TractorStop();
        robot.TractorMoveL(-100, 20);
        Thread.Sleep(5000);
        robot.TractorMoveC(300, 90, 20);
        Thread.Sleep(10000);
        robot.TractorMoveC(300, -90, 20);
        Thread.Sleep(1000);
        robot.TractorStop();    
    }

Ustawienie strategii ruchu synchronicznego osi rozszerzonej z robotem
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:


    /**
    * @brief Ustawia strategię ruchu synchronicznego osi rozszerzonej z robotem
    * @param strategy Strategia; 0-z robotem jako głównym; 1-oś rozszerzona i robot synchronicznie
    * @return Kod błędu
    */
    int SetExAxisRobotPlan(int strategy)

Przykład kodu ustawienia strategii ruchu synchronicznego osi rozszerzonej z robotem
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:


    private void button94_Click(object sender, EventArgs e)
    {
        JointPos joint_pos1 = new JointPos(-22.016, -49.217, 124.714, -161.100, -85.108, -0.333);
        JointPos joint_pos2 = new JointPos(-21.083, -46.613, 110.079, -147.796, -80.757, -0.330);
        JointPos joint_pos3 = new JointPos(-25.572, -60.090, 135.397, -163.889, -82.489, -0.345);
        DescPose desc_pos1 = new DescPose(2.637, -0.001, 30.673, 178.786, -4.134, 68.326);
        DescPose desc_pos2 = new DescPose(213.812, -1.440, 47.311, 177.410, 0.166, 68.946);
        DescPose desc_pos3 = new DescPose(444.342, -12.723, 82.470, -177.701, -1.325, 65.151);   
        ExaxisPos epos1 = new ExaxisPos(0.001, 0.000, 0.000, 0.000);
        ExaxisPos epos2 = new ExaxisPos(299.977, 0.000, 0.000, 0.000);
        ExaxisPos epos3 = new ExaxisPos(399.969, 0.000, 0.000, 0.000);      
        DescPose offset_pos = new DescPose(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);
        int rtn = robot.SetExAxisRobotPlan(0);
        Console.WriteLine($"SetExAxisRobotPlan rtn is {rtn}");
        Thread.Sleep(1000);
        rtn = robot.ExtAxisSyncMoveL(joint_pos1, desc_pos1, 1, 0, 100, 100, 100, -1, epos1, 0, offset_pos);
        Console.WriteLine($"ExtAxisSyncMoveL 1 rtn is {rtn}");

        rtn = robot.ExtAxisSyncMoveL(joint_pos2, desc_pos2, 1, 0, 100, 100, 100, -1, epos2, 0, offset_pos);
        Console.WriteLine($"ExtAxisSyncMoveL 2 rtn is {rtn}");
        rtn = robot.ExtAxisSyncMoveL(joint_pos3, desc_pos3, 1, 0, 100, 100, 100, -1, epos3, 0, offset_pos);
        Console.WriteLine($"ExtAxisSyncMoveL 3 rtn is {rtn}");
        Thread.Sleep(8000);
    }

Ustawienie czasu zakończenia pozycjonowania UDP osi rozszerzonej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawienie czasu zakończenia pozycjonowania UDP osi rozszerzonej
    * @param [in] time Czas zakończenia pozycjonowania [ms]
    * @return Kod błędu
    */
    public int SetExAxisCmdDoneTime(double time)