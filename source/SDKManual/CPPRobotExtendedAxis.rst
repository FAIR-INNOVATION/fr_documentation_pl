Oś rozszerzona
=================

.. toctree::
    :maxdepth: 5

Ustawianie parametrów osi rozszerzonej 485
+++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia parametry osi rozszerzonej 485
    * @param [in] servoId ID serwonapędu, zakres [1-15], odpowiada ID stacji podrzędnej
    * @param [in] servoCompany Producent serwonapędu, 1 - Dynatect
    * @param [in] servoModel Model serwonapędu, 1 - FD100-750C
    * @param [in] servoSoftVersion Wersja oprogramowania serwonapędu, 1 - V1.0
    * @param [in] servoResolution Rozdzielczość enkodera
    * @param [in] axisMechTransRatio Mechaniczne przełożenie transmisyjne
    * @return Kod błędu
    */
    errno_t AuxServoSetParam(int servoId, int servoCompany, int servoModel, int servoSoftVersion, int servoResolution, double axisMechTransRatio);

Pobieranie parametrów konfiguracyjnych osi rozszerzonej 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera parametry konfiguracyjne osi rozszerzonej 485
    * @param [in] servoId ID serwonapędu, zakres [1-15], odpowiada ID stacji podrzędnej
    * @param [out] servoCompany Producent serwonapędu, 1 - Dynatect
    * @param [out] servoModel Model serwonapędu, 1 - FD100-750C
    * @param [out] servoSoftVersion Wersja oprogramowania serwonapędu, 1 - V1.0
    * @param [out] servoResolution Rozdzielczość enkodera
    * @param [out] axisMechTransRatio Mechaniczne przełożenie transmisyjne
    * @return Kod błędu
    */
    errno_t AuxServoGetParam(int servoId, int* servoCompany, int* servoModel, int* servoSoftVersion, int* servoResolution, double* axisMechTransRatio);

Włączanie/wyłączanie zasilania osi rozszerzonej 485
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Włącza/wyłącza zasilanie osi rozszerzonej 485
    * @param [in] servoId ID serwonapędu, zakres [1-15], odpowiada ID stacji podrzędnej
    * @param [in] status Stan zasilania, 0 - wyłączone, 1 - włączone
    * @return Kod błędu
    */
    errno_t AuxServoEnable(int servoId, int status);

Ustawianie trybu sterowania osi rozszerzonej 485
+++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia tryb sterowania osi rozszerzonej 485
    * @param [in] servoId ID serwonapędu, zakres [1-15], odpowiada ID stacji podrzędnej
    * @param [in] mode Tryb sterowania, 0 - tryb pozycyjny, 1 - tryb prędkościowy
    * @return Kod błędu
    */
    errno_t AuxServoSetControlMode(int servoId, int mode);

Ustawianie pozycji docelowej osi rozszerzonej 485 (tryb pozycyjny)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia pozycję docelową osi rozszerzonej 485 (tryb pozycyjny)
    * @param [in] servoId ID serwonapędu, zakres [1-15], odpowiada ID stacji podrzędnej
    * @param [in] pos Pozycja docelowa, mm lub °
    * @param [in] speed Prędkość docelowa, mm/s lub °/s
    * @return Kod błędu
    */
    errno_t AuxServoSetTargetPos(int servoId, double pos, double speed);

Ustawianie momentu obrotowego docelowego osi rozszerzonej 485 (tryb momentowy) - Tymczasowo niedostępne
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia moment obrotowy docelowy osi rozszerzonej 485 (tryb momentowy)
    * @param [in] servoId ID serwonapędu, zakres [1-15], odpowiada ID stacji podrzędnej
    * @param [in] torque Moment docelowy, Nm
    * @return Kod błędu
    */
    errno_t AuxServoSetTargetTorque(int servoId, double torque);

Ustawianie powrotu do zera osi rozszerzonej 485
++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia powrót do zera osi rozszerzonej 485
    * @param [in] servoId ID serwonapędu, zakres [1-15], odpowiada ID stacji podrzędnej
    * @param [in] mode Tryb powrotu do zera, 0 - powrót do bieżącej pozycji; 1 - powrót do ogranicznika
    * @param [in] searchVel Prędkość poszukiwania zera, mm/s lub °/s
    * @param [in] latchVel Prędkość zatrzaskiwania, mm/s lub °/s
    * @return Kod błędu
    */
    errno_t AuxServoHoming(int servoId, int mode, double searchVel, double latchVel);

Czyszczenie informacji o błędzie osi rozszerzonej 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Czyści informacje o błędzie osi rozszerzonej 485
    * @param [in] servoId ID serwonapędu, zakres [1-15], odpowiada ID stacji podrzędnej
    * @return Kod błędu
    */
    errno_t AuxServoClearError(int servoId);

Pobieranie stanu serwonapędu osi rozszerzonej 485
++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera stan serwonapędu osi rozszerzonej 485
    * @param [in] servoId ID serwonapędu, zakres [1-15], odpowiada ID stacji podrzędnej
    * @param [out] servoErrCode Kod błędu serwonapędu
    * @param [out] servoState Stan serwonapędu [liczba dziesiętna konwertowana na binarną, bit0-bit5: serwonapęd włączony - serwonapęd pracuje - zadziałanie dodatniego ogranicznika - zadziałanie ujemnego ogranicznika - pozycjonowanie zakończone - powrót do zera zakończony]
    * @param [out] servoPos Bieżąca pozycja serwonapędu mm lub °
    * @param [out] servoSpeed Bieżąca prędkość serwonapędu mm/s lub °/s
    * @param [out] servoTorque Bieżący moment obrotowy serwonapędu Nm
    * @return Kod błędu
    */
    errno_t AuxServoGetStatus(int servoId, int* servoErrCode, int* servoState, double* servoPos, double* servoSpeed, double* servoTorque);

Ustawianie prędkości docelowej osi rozszerzonej 485 (tryb prędkościowy)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia prędkość docelową osi rozszerzonej 485 (tryb prędkościowy)
    * @param [in] servoId ID serwonapędu, zakres [1-15], odpowiada ID stacji podrzędnej
    * @param [in] speed Prędkość docelowa, mm/s lub °/s
    * @return Kod błędu
    */
    errno_t AuxServoSetTargetSpeed(int servoId, double speed);

Ustawianie numeru osi danych osi rozszerzonej 485 w sprzężeniu zwrotnym stanu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia numer osi danych osi rozszerzonej 485 w sprzężeniu zwrotnym stanu
    * @param [in] servoId ID serwonapędu, zakres [1-15], odpowiada ID stacji podrzędnej
    * @return Kod błędu
    */
    errno_t AuxServosetStatusID(int servoId);

Ustawianie przyspieszenia i opóźnienia ruchu osi rozszerzonej 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia przyspieszenie i opóźnienie ruchu osi rozszerzonej 485
    * @param [in] acc Przyspieszenie ruchu osi rozszerzonej 485
    * @param [in] dec Opóźnienie ruchu osi rozszerzonej 485
    * @return Kod błędu
    */
    errno_t AuxServoSetAcc(double acc, double dec);

Ustawianie przyspieszenia i opóźnienia awaryjnego zatrzymania osi rozszerzonej 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia przyspieszenie i opóźnienie awaryjnego zatrzymania osi rozszerzonej 485
    * @param [in] acc Przyspieszenie awaryjnego zatrzymania osi rozszerzonej 485
    * @param [in] dec Opóźnienie awaryjnego zatrzymania osi rozszerzonej 485
    * @return Kod błędu
    */
    errno_t AuxServoSetEmergencyStopAcc(double acc, double dec);

Pobieranie przyspieszenia i opóźnienia ruchu osi rozszerzonej 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera przyspieszenie i opóźnienie ruchu osi rozszerzonej 485
    * @param [out] acc Przyspieszenie ruchu osi rozszerzonej 485
    * @param [out] dec Opóźnienie ruchu osi rozszerzonej 485
    * @return Kod błędu
    */
    errno_t AuxServoGetAcc(double& acc, double& dec);

Pobieranie przyspieszenia i opóźnienia awaryjnego zatrzymania osi rozszerzonej 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera przyspieszenie i opóźnienie awaryjnego zatrzymania osi rozszerzonej 485
    * @param [out] acc Przyspieszenie awaryjnego zatrzymania osi rozszerzonej 485
    * @param [out] dec Opóźnienie awaryjnego zatrzymania osi rozszerzonej 485
    * @return Kod błędu
    */
    errno_t AuxServoGetEmergencyStopAcc(double& acc, double& dec);

Przykład kodu sterowania osią rozszerzoną
++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    int Test485Auxservo(void)
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
      int retval = robot.AuxServoSetParam(1, 1, 1, 1, 131072, 15.45);
      std::cout << "AuxServoSetParam is: " << retval << std::endl;
      int servoCompany;
      int servoModel;
      int servoSoftVersion;
      int servoResolution;
      double axisMechTransRatio;
      retval = robot.AuxServoGetParam(1, &servoCompany, &servoModel, &servoSoftVersion, &servoResolution, &axisMechTransRatio);
      std::cout << "servoCompany " << servoCompany << "\n"
        << "servoModel " << servoModel << "\n"
        << "servoSoftVersion " << servoSoftVersion << "\n"
        << "servoResolution " << servoResolution << "\n"
        << "axisMechTransRatio " << axisMechTransRatio << "\n"
        << std::endl;
      retval = robot.AuxServoSetParam(1, 10, 11, 12, 13, 14);
      std::cout << "AuxServoSetParam is: " << retval << std::endl;
      retval = robot.AuxServoGetParam(1, &servoCompany, &servoModel, &servoSoftVersion, &servoResolution, &axisMechTransRatio);
      std::cout << "servoCompany " << servoCompany << "\n"
        << "servoModel " << servoModel << "\n"
        << "servoSoftVersion " << servoSoftVersion << "\n"
        << "servoResolution " << servoResolution << "\n"
        << "axisMechTransRatio " << axisMechTransRatio << "\n"
        << std::endl;
      retval = robot.AuxServoSetParam(1, 1, 1, 1, 131072, 36);
      std::cout << "AuxServoSetParam is: " << retval << std::endl;
      robot.Sleep(3000);
      robot.AuxServoSetAcc(3000, 3000);
      robot.AuxServoSetEmergencyStopAcc(5000, 5000);
      robot.Sleep(1000);
      double emagacc = 0, acc = 0;
      double emagdec = 0, dec = 0;
      robot.AuxServoGetEmergencyStopAcc(emagacc, emagdec);
      printf("emergency acc is %f dec is %f \n", emagacc, emagdec);
      robot.AuxServoGetAcc(acc, dec);
      printf("acc is %f dec is %f \n", acc, dec);
      robot.AuxServoSetControlMode(1, 0);
      robot.Sleep(2000);
      retval = robot.AuxServoEnable(1, 0);
      std::cout << "AuxServoEnable disenable " << retval << std::endl;
      robot.Sleep(1000);
      int servoerrcode = 0;
      int servoErrCode;
      int servoState;
      double servoPos;
      double servoSpeed;
      double servoTorque;
      retval = robot.AuxServoGetStatus(1, &servoErrCode, &servoState, &servoPos, &servoSpeed, &servoTorque);
      std::cout << "AuxServoGetStatus servoState " << servoState << std::endl;
      robot.Sleep(1000);;
      retval = robot.AuxServoEnable(1, 1);
      std::cout << "AuxServoEnable enable " << retval << std::endl;
      robot.Sleep(1000);
      retval = robot.AuxServoGetStatus(1, &servoErrCode, &servoState, &servoPos, &servoSpeed, &servoTorque);
      std::cout << "AuxServoGetStatus servoState " << servoState << std::endl;
      robot.Sleep(1000);
      retval = robot.AuxServoHoming(1, 1, 5, 1);
      std::cout << "AuxServoHoming " << retval << std::endl;
      robot.Sleep(3000);
      retval = robot.AuxServoSetTargetPos(1, 200, 30);
      std::cout << "AuxServoSetTargetPos " << retval << std::endl;
      robot.Sleep(1000);
      retval = robot.AuxServoGetStatus(1, &servoErrCode, &servoState, &servoPos, &servoSpeed, &servoTorque);
      std::cout << "AuxServoGetStatus servoSpeed " << servoSpeed << std::endl;
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
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Konfiguruje parametry komunikacji UDP dla osi rozszerzonej
    * @param [in] ip Adres IP PLC
    * @param [in] port Numer portu
    * @param [in] period Okres komunikacji (ms, domyślnie 2, nie modyfikować tego parametru)
    * @param [in] lossPkgTime Czas wykrywania utraty pakietów (ms)
    * @param [in] lossPkgNum Liczba utraconych pakietów
    * @param [in] disconnectTime Czas potwierdzenia przerwania komunikacji
    * @param [in] reconnectEnable Włączenie automatycznego ponownego łączenia po przerwaniu komunikacji 0 - nie włączone, 1 - włączone
    * @param [in] reconnectPeriod Odstęp między próbami ponownego łączenia (ms)
    * @param [in] reconnectNum Liczba prób ponownego łączenia
    * @param [in] selfConnect Czy automatycznie nawiązać połączenie po ponownym uruchomieniu zasilania; 0 - nie nawiązuj połączenia; 1 - nawiąż połączenie
    * @return Kod błędu
    */
    errno_t ExtDevSetUDPComParam(std::string ip, int port, int period, int lossPkgTime, int lossPkgNum, int disconnectTime, int reconnectEnable, int reconnectPeriod, int reconnectNum, int selfConnect = 1);

Pobieranie konfiguracji parametrów komunikacji UDP dla osi rozszerzonej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera parametry komunikacji UDP dla osi rozszerzonej
    * @param [out] ip Adres IP PLC
    * @param [out] port Numer portu
    * @param [out] period Okres komunikacji (ms, domyślnie 2, nie modyfikować tego parametru)
    * @param [out] lossPkgTime Czas wykrywania utraty pakietów (ms)
    * @param [out] lossPkgNum Liczba utraconych pakietów
    * @param [out] disconnectTime Czas potwierdzenia przerwania komunikacji
    * @param [out] reconnectEnable Włączenie automatycznego ponownego łączenia po przerwaniu komunikacji 0 - nie włączone, 1 - włączone
    * @param [out] reconnectPeriod Odstęp między próbami ponownego łączenia (ms)
    * @param [out] reconnectNum Liczba prób ponownego łączenia
    * @param [out] selfStart Czy automatycznie ponownie połączyć po ponownym uruchomieniu szafy sterowniczej; 0 - nie łącz ponownie; 1 - łącz ponownie
    * @return Kod błędu
    */
    errno_t ExtDevGetUDPComParam(std::string& ip, int& port, int& period, int& lossPkgTime, int& lossPkgNum, int& disconnectTime, int& reconnectEnable, int& reconnectPeriod, int& reconnectNum, int& selfConnect);

Ładowanie komunikacji UDP
+++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ładuje komunikację UDP
    * @return Kod błędu
    */
    errno_t ExtDevLoadUDPDriver();

Zwolnienie komunikacji UDP
+++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Zwolnienie komunikacji UDP
    * @return Kod błędu
    */
    errno_t ExtDevUnloadUDPDriver();

Przywracanie połączenia po przerwaniu komunikacji UDP osi rozszerzonej
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Przywraca połączenie po przerwaniu komunikacji UDP osi rozszerzonej
    * @return Kod błędu
    */
    errno_t ExtDevUDPClientComReset();

Zamykanie komunikacji po przerwaniu komunikacji UDP osi rozszerzonej
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Zamyka komunikację po przerwaniu komunikacji UDP osi rozszerzonej
    * @return Kod błędu
    */
    errno_t ExtDevUDPClientComClose();

Konfiguracja parametrów osi rozszerzonej UDP
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Konfiguruje parametry osi rozszerzonej UDP
    * @param [in] axisID Numer osi
    * @param [in] axisType Typ osi rozszerzonej 0 - przesuwna; 1 - obrotowa
    * @param [in] axisDirection Kierunek osi rozszerzonej 0 - dodatni; 1 - ujemny
    * @param [in] axisMax Maksymalna pozycja osi rozszerzonej mm
    * @param [in] axisMin Minimalna pozycja osi rozszerzonej mm
    * @param [in] axisVel Prędkość mm/s
    * @param [in] axisAcc Przyspieszenie mm/s2
    * @param [in] axisLead Skok śruby pociągowej mm
    * @param [in] encResolution Rozdzielczość enkodera
    * @param [in] axisOffect Przesunięcie osi rozszerzonej punktu początkowego spoiny
    * @param [in] axisCompany Producent sterownika 1 - Hechuan; 2 - Huichuan; 3 - Panasonic
    * @param [in] axisModel Model sterownika 1 - Hechuan-SV-XD3EA040L-E, 2 - Hechuan-SV-X2EA150A-A, 1 - Huichuan-SV620PT5R4I, 1 - Panasonic-MADLN15SG, 2 - Panasonic-MSDLN25SG, 3 - Panasonic-MCDLN35SG
    * @param [in] axisEncType Typ enkodera 0 - inkrementalny; 1 - absolutny
    * @return Kod błędu
    */
    errno_t ExtAxisParamConfig(int axisID, int axisType, int axisDirection, double axisMax, double axisMin, double axisVel, double axisAcc, double axisLead, long encResolution, double axisOffect, int axisCompany, int axisModel, int axisEncType);

Pobieranie parametrów osi rozszerzonej UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera parametry osi rozszerzonej UDP
    * @param [in] axisID Numer osi rozszerzonej [1-4]
    * @param [out] axisType Typ osi rozszerzonej 0 - przesuwna; 1 - obrotowa
    * @param [out] axisDirection Kierunek osi rozszerzonej 0 - dodatni; 1 - ujemny
    * @param [out] axisMax Maksymalna pozycja osi rozszerzonej mm
    * @param [out] axisMin Minimalna pozycja osi rozszerzonej mm
    * @param [out] axisVel Prędkość mm/s
    * @param [out] axisAcc Przyspieszenie mm/s2
    * @param [out] axisLead Skok śruby pociągowej mm
    * @param [out] encResolution Rozdzielczość enkodera
    * @param [out] axisOffect Przesunięcie osi rozszerzonej punktu początkowego spoiny
    * @param [out] axisCompany Producent sterownika 1 - Hechuan; 2 - Huichuan; 3 - Panasonic
    * @param [out] axisModel Model sterownika 1 - Hechuan-SV-XD3EA040L-E, 2 - Hechuan-SV-X2EA150A-A, 1 - Huichuan-SV620PT5R4I, 1 - Panasonic-MADLN15SG, 2 - Panasonic-MSDLN25SG, 3 - Panasonic-MCDLN35SG
    * @param [out] axisEncType Typ enkodera 0 - inkrementalny; 1 - absolutny
    * @return Kod błędu
    */
    errno_t ExtAxisGetParamConfig(int axisID, int& axisType, int& axisDirection, double& axisMax, double& axisMin, double& axisVel, double& axisAcc, double& axisLead, int& encResolution, double& axisOffect, int& axisCompany, int& axisModel, int& axisEncType);

Ustawianie pozycji montażowej osi rozszerzonej
+++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia pozycję montażową osi rozszerzonej
    * @param [in] installType 0 - robot zamontowany na osi zewnętrznej, 1 - robot zamontowany poza osią zewnętrzną
    * @return Kod błędu
    */
    errno_t SetRobotPosToAxis(int installType);

Ustawianie konfiguracji parametrów DH systemu osi rozszerzonej
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia konfigurację parametrów DH systemu osi rozszerzonej
    * @param [in]  axisConfig Konfiguracja osi zewnętrznej, 0 - jednokierunkowa prosta szyna szynowa, 1 - dwukierunkowa pozycjoner typu L, 2 - trzykierunkowa, 3 - czterokierunkowa, 4 - jednokierunkowy pozycjoner
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
    errno_t SetAxisDHParaConfig(int axisConfig, double axisDHd1, double axisDHd2, double axisDHd3, double axisDHd4, double axisDHa1, double axisDHa2, double axisDHa3, double axisDHa4);

Włączanie zasilania osi rozszerzonej UDP
+++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Włącza zasilanie osi rozszerzonej UDP
    * @param [in] axisID Numer osi [1-4]
    * @param [in] status 0 - wyłączone; 1 - włączone
    * @return Kod błędu
    */
    errno_t ExtAxisServoOn(int axisID, int status);

Powrót do zera osi rozszerzonej UDP
++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Powrót do zera osi rozszerzonej UDP
    * @param [in] axisID Numer osi [1-4]
    * @param [in] mode Sposób powrotu do zera 0 - powrót do bieżącej pozycji, 1 - powrót do ujemnego ogranicznika, 2 - powrót do dodatniego ogranicznika
    * @param [in] searchVel Prędkość poszukiwania zera (mm/s)
    * @param [in] latchVel Prędkość zatrzaskiwania zera (mm/s)
    * @return Kod błędu
    */
    errno_t ExtAxisSetHoming(int axisID, int mode, double searchVel, double latchVel);

Rozpoczęcie ruchu jałowego osi rozszerzonej UDP
++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Rozpoczyna ruch jałowy osi rozszerzonej UDP
    * @param [in] axisID Numer osi [1-4]
    * @param [in] direction Kierunek obrotu 0 - przeciwny; 1 - zgodny
    * @param [in] vel Prędkość (mm/s)
    * @param [in] acc Przyspieszenie (mm/s2)
    * @param [in] maxDistance Maksymalna odległość ruchu jałowego
    * @return Kod błędu
    */
    errno_t ExtAxisStartJog(int axisID, int direction, double vel, double acc, double maxDistance);

Zatrzymanie ruchu jałowego osi rozszerzonej UDP
++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Zatrzymuje ruch jałowy osi rozszerzonej UDP
    * @param [in] axisID Numer osi [1-4]
    * @return Kod błędu
    */
    errno_t ExtAxisStopJog(int axisID);

Przykład kodu konfiguracji i ruchu jałowego osi rozszerzonej UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestUDPAxis(void)
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
        rtn = robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 200, 1, 100, 5, 1);
        cout << "ExtDevSetUDPComParam rtn is " << rtn << endl;
        string ip = ""; int port = 0; int period = 0; int lossPkgTime = 0; int lossPkgNum = 0; int disconnectTime = 0; int reconnectEnable = 0; int reconnectPeriod = 0; int reconnectNum = 0; int selfConnect = 0;
        rtn = robot.ExtDevGetUDPComParam(ip, port, period, lossPkgTime, lossPkgNum, disconnectTime, reconnectEnable, reconnectPeriod, reconnectNum, selfConnect);
        string patam = "\nip " + ip + "\nport " + to_string(port) + "\nperiod  " + to_string(period) + "\nlossPkgTime " + to_string(lossPkgTime) + "\nlossPkgNum  " + to_string(lossPkgNum) + "\ndisConntime  " +
            to_string(disconnectTime) + "\nreconnecable  " + to_string(reconnectEnable) + "\nreconnperiod  " + to_string(reconnectPeriod) + "\nreconnnun  " + to_string(reconnectNum) + "\nselfConnect  " + to_string(selfConnect);
        cout << "ExtDevGetUDPComParam rtn is " << rtn << patam << endl;
        robot.ExtDevLoadUDPDriver();
        rtn = robot.SetExAxisCmdDoneTime(5000.0);
        cout << "SetExAxisCmdDoneTime rtn is " << rtn << endl;
        rtn = robot.ExtAxisServoOn(1, 1);
        cout << "ExtAxisServoOn axis id 1 rtn is " << rtn << endl;
        rtn = robot.ExtAxisServoOn(2, 1);
        cout << "ExtAxisServoOn axis id 2 rtn is " << rtn << endl;
        robot.Sleep(2000);
        robot.ExtAxisSetHoming(1, 0, 10, 2);
        robot.Sleep(2000);
        rtn = robot.ExtAxisSetHoming(2, 0, 10, 2);
        cout << "ExtAxisSetHoming rtnn is  " << rtn << endl;
        robot.Sleep(4000);
        rtn = robot.SetRobotPosToAxis(1);
        cout << "SetRobotPosToAxis rtn is " << rtn << endl;
        rtn = robot.SetAxisDHParaConfig(10, 20, 0, 0, 0, 0, 0, 0, 0);
        cout << "SetAxisDHParaConfig rtn is " << rtn << endl;
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
        rtn = robot.ExtAxisParamConfig(1, 1, 1, 1000, -1000, 1000, 1000, 1.905, 262144, 200, 1, 0, 0);
        cout << "ExtAxisParamConfig axis 1 rtn is " << rtn << endl;
        rtn = robot.ExtAxisGetParamConfig(1, axisType, axisDirection, axisMax, axisMin, axisVel, axisAcc, axisLead, encResolution, axisOffect, axisCompany, axisModel, axisEncType);
        printf("axis id 1 ExtAxisGetParamConfig : axisType %d, axisDirection %d, axisMax %lf, axisMin %lf, axisVel %lf, axisAcc %lf, axisLead%lf, encResolution %d, axisOffect %f, axisCompany %d, axisModel %d, axisEncType %d\n",
            axisType, axisDirection, axisMax, axisMin, axisVel, axisAcc, axisLead, encResolution, axisOffect, axisCompany, axisModel, axisEncType);
            rtn = robot.ExtAxisParamConfig(2, 1, 1, 1000, -1000, 1000, 1000, 4.444, 262144, 200, 1, 0, 0);
        cout << "ExtAxisParamConfig axis 2 rtn is " << rtn << endl;
        rtn = robot.ExtAxisGetParamConfig(2, axisType, axisDirection, axisMax, axisMin, axisVel, axisAcc, axisLead, encResolution, axisOffect, axisCompany, axisModel, axisEncType);
        printf("axis id 2 ExtAxisGetParamConfig : axisType %d, axisDirection %d, axisMax %lf, axisMin %lf, axisVel %lf, axisAcc %lf, axisLead%lf, encResolution %d, axisOffect %f, axisCompany %d, axisModel %d, axisEncType %d\n",
            axisType, axisDirection, axisMax, axisMin, axisVel, axisAcc, axisLead, encResolution, axisOffect, axisCompany, axisModel, axisEncType);
        robot.Sleep(1000 * 3);
        robot.ExtAxisStartJog(1, 0, 10, 10, 30);
        robot.Sleep(1000 * 1);
        robot.ExtAxisStopJog(1);
        robot.Sleep(1000 * 3);
        robot.ExtAxisServoOn(1, 0);
        robot.Sleep(1000 * 3);
        robot.ExtAxisStartJog(2, 0, 10, 10, 30);
        robot.Sleep(1000 * 1);
        robot.ExtAxisStopJog(2);
        robot.Sleep(1000 * 3);
        robot.ExtAxisServoOn(2, 0);
        robot.Sleep(1000 * 1);
        robot.ExtDevUnloadUDPDriver();
        robot.CloseRPC();
        return 0;
    }

Ustawianie punktu odniesienia układu współrzędnych osi rozszerzonej - metoda czterech punktów
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia punkt odniesienia układu współrzędnych osi rozszerzonej - metoda czterech punktów
    * @param [in]  pointNum Numer punktu [1-4]
    * @return Kod błędu
    */
    errno_t ExtAxisSetRefPoint(int pointNum);

Obliczanie układu współrzędnych osi rozszerzonej - metoda czterech punktów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Oblicza układ współrzędnych osi rozszerzonej - metoda czterech punktów
    * @param [out]  coord Wartości układu współrzędnych
    * @return Kod błędu
    */
    errno_t ExtAxisComputeECoordSys(DescPose& coord);

Ustawianie punktu odniesienia układu współrzędnych pozycjonera
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia punkt odniesienia układu współrzędnych pozycjonera
    * @param [in]  pointNum Numer punktu [1-4]
    * @return Kod błędu
    */
    errno_t PositionorSetRefPoint(int pointNum);

Obliczanie układu współrzędnych pozycjonera - metoda czterech punktów
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Oblicza układ współrzędnych pozycjonera - metoda czterech punktów
    * @param [out] coord Wartości układu współrzędnych
    * @return Kod błędu
    */
    errno_t PositionorComputeECoordSys(DescPose& coord);

Ustawianie pozy i orientacji punktu odniesienia kalibracji w układzie współrzędnych końcówki pozycjonera
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia pozy i orientację punktu odniesienia kalibracji w układzie współrzędnych końcówki pozycjonera
    * @param [in] pos Wartości pozy i orientacji
    * @return Kod błędu
    */
    errno_t SetRefPointInExAxisEnd(DescPose pos);

Stosowanie układu współrzędnych osi rozszerzonej
+++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Stosuje układ współrzędnych osi rozszerzonej
    * @param [in]  applyAxisId Numer osi rozszerzonej bit0-bit3 odpowiada numerom osi rozszerzonej 1-4, np. zastosowanie osi rozszerzonych 1 i 3 to 0b 0000 0101; czyli 5
    * @param [in]  axisCoordNum Numer układu współrzędnych osi rozszerzonej
    * @param [in]  coord Wartości układu współrzędnych
    * @param [in]  calibFlag Flaga kalibracji 0 - nie, 1 - tak
    * @return Kod błędu
    */
    errno_t ExtAxisActiveECoordSys(int applyAxisId, int axisCoordNum, DescPose coord, int calibFlag);

Pobieranie układu współrzędnych osi rozszerzonej
+++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera układ współrzędnych osi rozszerzonej
    * @param [out] coord Układ współrzędnych osi rozszerzonej
    * @return Kod błędu
    */
    errno_t ExtAxisGetCoord(DescPose& coord);

Przykład kodu kalibracji układu współrzędnych osi rozszerzonej
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestUDPAxisCalib(void)
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
       rtn = robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 200, 1, 100, 5, 1);
       cout << "ExtDevSetUDPComParam rtn is " << rtn << endl;
       string ip = ""; int port = 0; int period = 0; int lossPkgTime = 0; int lossPkgNum = 0; int disconnectTime = 0; int reconnectEnable = 0; int reconnectPeriod = 0; int reconnectNum = 0;
       rtn = robot.ExtDevGetUDPComParam(ip, port, period, lossPkgTime, lossPkgNum, disconnectTime, reconnectEnable, reconnectPeriod, reconnectNum);
       string patam = "\nip " + ip + "\nport " + to_string(port) + "\nperiod " + to_string(period) + "\nlossPkgTime " + to_string(lossPkgTime) + "\nlossPkgNum " + to_string(lossPkgNum) + "\ndisConntime " + to_string(disconnectTime) + "\nreconnecable " + to_string(reconnectEnable) + "\nreconnperiod " + to_string(reconnectPeriod) + "\nreconnnun " + to_string(reconnectNum);
       cout << "ExtDevGetUDPComParam rtn is " << rtn << patam << endl;
       robot.ExtDevLoadUDPDriver();
       rtn = robot.ExtAxisServoOn(1, 1);
       cout << "ExtAxisServoOn axis id 1 rtn is " << rtn << endl;
       rtn = robot.ExtAxisServoOn(2, 1);
       cout << "ExtAxisServoOn axis id 2 rtn is " << rtn << endl;
       robot.Sleep(2000);
       robot.ExtAxisSetHoming(1, 0, 10, 2);
       robot.Sleep(2000);
       rtn = robot.ExtAxisSetHoming(2, 0, 10, 2);
       cout << "ExtAxisSetHoming rtnn is " << rtn << endl;
       robot.Sleep(4000);
       rtn = robot.SetRobotPosToAxis(1);
       cout << "SetRobotPosToAxis rtn is " << rtn << endl;
       rtn = robot.SetAxisDHParaConfig(1, 128.5, 206.4, 0, 0, 0, 0, 0, 0);
       cout << "SetAxisDHParaConfig rtn is " << rtn << endl;
       rtn = robot.ExtAxisParamConfig(1, 1, 1, 1000, -1000, 1000, 1000, 1.905, 262144, 200, 1, 0, 0);
       cout << "ExtAxisParamConfig axis 1 rtn is " << rtn << endl;
       rtn = robot.ExtAxisParamConfig(2, 1, 1, 1000, -1000, 1000, 1000, 4.444, 262144, 200, 1, 0, 0);
       cout << "ExtAxisParamConfig axis 1 rtn is " << rtn << endl;
       DescPose toolCoord(0, 0, 210, 0, 0, 0);
       robot.SetToolCoord(1, &toolCoord, 0, 0, 1, 0);
       JointPos jSafe(115.193, -96.149, 92.489, -87.068, -89.15, -83.488);
       JointPos j1(117.559, -92.624, 100.329, -96.909, -94.057, -83.488);
       JointPos j2(112.239, -90.096, 99.282, -95.909, -89.824, -83.488);
       JointPos j3(110.839, -83.473, 93.166, -89.22, -90.499, -83.487);
       JointPos j4(107.935, -83.572, 95.424, -92.873, -87.933, -83.488);
       DescPose descSafe = {};
       DescPose desc1 = {};
       DescPose desc2 = {};
       DescPose desc3 = {};
       DescPose desc4 = {};
       ExaxisPos exaxisPos = { 0, 0, 0, 0 };
       DescPose offdese = { 0, 0, 0, 0, 0, 0 };
       robot.GetForwardKin(&jSafe, &descSafe);
       robot.MoveJ(&jSafe, &descSafe, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       robot.Sleep(2000);
       robot.GetForwardKin(&j1, &desc1);
       robot.MoveJ(&j1, &desc1, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       robot.Sleep(2000);
       DescPose actualTCPPos = {};
       robot.GetActualTCPPose(0, &actualTCPPos);
       robot.SetRefPointInExAxisEnd(actualTCPPos);
       rtn = robot.PositionorSetRefPoint(1);
       cout << "PositionorSetRefPoint 1 rtn is " << rtn << endl;
       robot.Sleep(2000);
       robot.MoveJ(&jSafe, &descSafe, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       robot.ExtAxisStartJog(1, 0, 50, 50, 10);
       robot.Sleep(1000);
       robot.ExtAxisStartJog(2, 0, 50, 50, 10);
       robot.Sleep(1000);
       robot.GetForwardKin(&j2, &desc2);
       rtn = robot.MoveJ(&j2, &desc2, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       rtn = robot.PositionorSetRefPoint(2);
       cout << "PositionorSetRefPoint 2 rtn is " << rtn << endl;
       robot.Sleep(2000);
       robot.MoveJ(&jSafe, &descSafe, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       robot.ExtAxisStartJog(1, 0, 50, 50, 10);
       robot.Sleep(1000);
       robot.ExtAxisStartJog(2, 0, 50, 50, 10);
       robot.Sleep(1000);
       robot.GetForwardKin(&j3, &desc3);
       robot.MoveJ(&j3, &desc3, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       rtn = robot.PositionorSetRefPoint(3);
       cout << "PositionorSetRefPoint 3 rtn is " << rtn << endl;
       robot.Sleep(2000);
       robot.MoveJ(&jSafe, &descSafe, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       robot.ExtAxisStartJog(1, 0, 50, 50, 10);
       robot.Sleep(1000);
       robot.ExtAxisStartJog(2, 0, 50, 50, 10);
       robot.Sleep(1000);
       robot.GetForwardKin(&j4, &desc4);
       robot.MoveJ(&j4, &desc4, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       rtn = robot.PositionorSetRefPoint(4);
       cout << "PositionorSetRefPoint 4 rtn is " << rtn << endl;
       robot.Sleep(2000);
       DescPose axisCoord = {};
       robot.PositionorComputeECoordSys(axisCoord);
       robot.MoveJ(&jSafe, &descSafe, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       printf("PositionorComputeECoordSys rtn is %f %f %f %f %f %f\n", axisCoord.tran.x, axisCoord.tran.y, axisCoord.tran.z, axisCoord.rpy.rx, axisCoord.rpy.ry, axisCoord.rpy.rz);
       rtn = robot.ExtAxisActiveECoordSys(3, 1, axisCoord, 1);
       cout << "ExtAxisActiveECoordSys rtn is " << rtn << endl;
    DescPose getCoord(0, 0, 0, 0, 0, 0);
    rtn = robot.ExtAxisGetCoord(getCoord);
    printf("ExtAxisGetCoord rtn is %f %f %f %f %f %f\n", getCoord.tran.x, getCoord.tran.y, getCoord.tran.z, getCoord.rpy.rx, getCoord.rpy.ry, getCoord.rpy.rz);
    robot.CloseRPC();
    return 0;
    }

Ruch osi rozszerzonej UDP
+++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.2.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ruch osi rozszerzonej UDP
    * @param [in] pos Pozycja docelowa
    * @param [in] ovl Procent prędkości
    * @param [in] blend Parametr wygładzania (mm lub ms); -1: oczekuj na zakończenie ruchu
    * @return Kod błędu
    */
    errno_t ExtAxisMove(ExaxisPos pos, double ovl, double blend = -1);

Przykład kodu ruchu osi rozszerzonej UDP
+++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestUDPAxisCalib(void)
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
      ExaxisPos axisPos;
      axisPos.ePos[0] = 20;
      axisPos.ePos[1] = 0;
      axisPos.ePos[2] = 0;
      axisPos.ePos[3] = 0;
      robot.ExtAxisMove(axisPos, 50);
      robot.CloseRPC();
      return 0;
    }

Ruch synchroniczny osi rozszerzonej UDP z ruchem stawowym robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
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
    * @param [in] blendT [-1.0] - ruch do pozycji (blokujący), [0~500.0] - czas wygładzania (nieblokujący), jednostka ms
    * @param [in] offset_flag 0 - brak przesunięcia, 1 - przesunięcie w układzie bazowym/układzie obiektu, 2 - przesunięcie w układzie narzędzia
    * @param [in] offset_pos Wartość przesunięcia pozy i orientacji
    * @return Kod błędu
    */
    errno_t ExtAxisSyncMoveJ(JointPos joint_pos, DescPose desc_pos, int tool, int user, float vel, float acc, float ovl, ExaxisPos epos, float blendT, byte offset_flag, DescPose offset_pos);

Ruch synchroniczny osi rozszerzonej UDP z ruchem stawowym robota (automatyczne obliczanie prostej kinematyki)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
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
    * @param [in] blendT [-1.0] - ruch do pozycji (blokujący), [0~500.0] - czas wygładzania (nieblokujący), jednostka ms
    * @param [in] offset_flag 0 - brak przesunięcia, 1 - przesunięcie w układzie bazowym/układzie obiektu, 2 - przesunięcie w układzie narzędzia
    * @param [in] offset_pos Wartość przesunięcia pozy i orientacji
    * @return Kod błędu
    */
    errno_t ExtAxisSyncMoveJ(JointPos joint_pos, int tool, int user, float vel, float acc, float ovl, ExaxisPos epos, float blendT, uint8_t offset_flag, DescPose offset_pos);

Przykład kodu ruchu synchronicznego z ruchem stawowym robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int testSyncMoveJ()
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
      //1. Kalibracja i zastosowanie układu współrzędnych narzędzia robota. Możesz użyć metody czterech lub sześciu punktów do kalibracji i zastosowania układu współrzędnych narzędzia. Interfejsy związane z kalibracją układu współrzędnych narzędzia są następujące:
      //  int SetToolPoint(int point_num); //Ustawia punkt odniesienia narzędzia - metoda sześciu punktów
      //  int ComputeTool(ref DescPose tcp_pose); //Oblicza układ współrzędnych narzędzia
      //  int SetTcp4RefPoint(int point_num);  //Ustawia punkt odniesienia narzędzia - metoda czterech punktów
      //  int ComputeTcp4(ref DescPose tcp_pose);  //Oblicza układ współrzędnych narzędzia - metoda czterech punktów
      //  int SetToolCoord(int id, DescPose coord, int type, int install); //Ustawia i stosuje układ współrzędnych narzędzia
      //  int SetToolList(int id, DescPose coord, int type, int install);  //Ustawia i stosuje listę układów współrzędnych narzędzia
      //2. Ustaw parametry komunikacji UDP i załaduj komunikację UDP
      robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10);
      robot.ExtDevLoadUDPDriver();
      //3. Ustaw parametry osi rozszerzonej, w tym typ osi rozszerzonej, parametry sterownika osi rozszerzonej, parametry DH osi rozszerzonej
      robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0); //Jednoosiowy pozycjoner i parametry DH
      robot.SetRobotPosToAxis(1); //Pozycja montażowa osi rozszerzonej
      robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0); //Parametry sterownika serwonapędu. W tym przykładzie dla pozycjonera jednoosiowego wystarczy ustawić parametry jednego sterownika. Jeśli wybierzesz typ osi rozszerzonej zawierający wiele osi, musisz ustawić parametry sterownika dla każdej osi.
      //4. Włącz zasilanie wybranej osi i wykonaj powrót do zera
      robot.ExtAxisServoOn(1, 0);
      robot.ExtAxisSetHoming(1, 0, 20, 3);
      //5. Wykonaj kalibrację układu współrzędnych osi rozszerzonej i zastosuj go
      DescPose pos = {/* Wprowadź współrzędne swojego punktu kalibracyjnego */ };
      robot.SetRefPointInExAxisEnd(pos);
      robot.PositionorSetRefPoint(1); /*Musisz skalibrować oś rozszerzoną za pomocą czterech różnych pozycji punktów, dlatego musisz wywołać ten interfejs 4 razy, aby zakończyć kalibrację */
      DescPose coord = {};
      robot.PositionorComputeECoordSys(coord); //Oblicz wynik kalibracji osi rozszerzonej
      robot.ExtAxisActiveECoordSys(1, 1, coord, 1); //Zastosuj wynik kalibracji do układu współrzędnych osi rozszerzonej
      //6. Kalibracja układu współrzędnych obiektu na osi rozszerzonej. Będziesz potrzebować następujących interfejsów:
      //int SetWObjCoordPoint(int point_num);
      //int ComputeWObjCoord(int method, ref DescPose wobj_pose);
      //int SetWObjCoord(int id, DescPose coord);
      //int SetWObjList(int id, DescPose coord);
      //7. Zapisz punkt początkowy synchronicznego ruchu stawowego
      DescPose startdescPose = {/* Wprowadź swoje współrzędne */ };
      JointPos startjointPos = {/* Wprowadź swoje współrzędne */ };
      ExaxisPos startexaxisPos = {/* Wprowadź współrzędne punktu początkowego osi rozszerzonej */ };
      //8. Zapisz współrzędne punktu końcowego synchronicznego ruchu stawowego
      DescPose enddescPose = {/* Wprowadź swoje współrzędne */ };
      JointPos endjointPos = {/* Wprowadź swoje współrzędne */ };
      ExaxisPos endexaxisPos = {/* Wprowadź współrzędne punktu końcowego osi rozszerzonej */ };
      //9. Napisz program ruchu synchronicznego
      //Przejedź do punktu początkowego, zakładając, że stosowane układy współrzędnych narzędzia i obiektu to 1
      robot.ExtAxisMove(startexaxisPos, 20);
      DescPose offdese = { 0, 0, 0, 0, 0, 0 };
      robot.MoveJ(&startjointPos, &startdescPose, 1, 1, 100, 100, 100, &startexaxisPos, 0, 0, &offdese);
      //Rozpocznij ruch synchroniczny
      robot.ExtAxisSyncMoveJ(endjointPos, enddescPose, 1, 1, 100, 100, 100, endexaxisPos, -1, 0, offdese);
      robot.MoveJ(&startjointPos, 1, 1, 100, 100, 100, &startexaxisPos, 0, 0, &offdese);
      //Rozpocznij ruch synchroniczny
      robot.ExtAxisSyncMoveJ(endjointPos, 1, 1, 100, 100, 100, endexaxisPos, -1, 0, offdese);
      robot.CloseRPC();
    }

Ruch synchroniczny osi rozszerzonej UDP z ruchem liniowym robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
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
    * @param [in] blendR [-1.0] - ruch do pozycji (blokujący), [0~1000.0] - promień wygładzania (nieblokujący), jednostka mm
    * @param [in] epos Pozycja osi rozszerzonej, jednostka mm
    * @param [in] offset_flag 0 - brak przesunięcia, 1 - przesunięcie w układzie bazowym/układzie obiektu, 2 - przesunięcie w układzie narzędzia
    * @param [in] offset_pos Wartość przesunięcia pozy i orientacji
    * @return Kod błędu
    */
    errno_t ExtAxisSyncMoveL(JointPos joint_pos, DescPose desc_pos, int tool, int user, float vel, float acc, float ovl, float blendR, ExaxisPos epos, int offset_flag, DescPose offset_pos);

Ruch synchroniczny osi rozszerzonej UDP z ruchem liniowym robota (automatyczne obliczanie odwrotnej kinematyki)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Ruch synchroniczny osi rozszerzonej UDP z ruchem liniowym robota (automatyczne obliczanie odwrotnej kinematyki)
    * @param [in] desc_pos Docelowa poza i orientacja w kartezjańskim układzie współrzędnych
    * @param [in] tool Numer narzędzia, zakres [0~14]
    * @param [in] user Numer obiektu, zakres [0~14]
    * @param [in] vel Procent prędkości, zakres [0~100]
    * @param [in] acc Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param [in] ovl Współczynnik skalowania prędkości, zakres [0~100]
    * @param [in] blendR [-1.0] - ruch do pozycji (blokujący), [0~1000.0] - promień wygładzania (nieblokujący), jednostka mm
    * @param [in] epos Pozycja osi rozszerzonej, jednostka mm
    * @param [in] offset_flag 0 - brak przesunięcia, 1 - przesunięcie w układzie bazowym/układzie obiektu, 2 - przesunięcie w układzie narzędzia
    * @param [in] offset_pos Wartość przesunięcia pozy i orientacji
    * @param [in] config Konfiguracja przestrzeni stawów dla odwrotnej kinematyki, [-1] - obliczenia w oparciu o bieżącą pozycję stawów, [0~7] - obliczenia zgodnie z określoną konfiguracją przestrzeni stawów
    * @return Kod błędu
    */
    errno_t ExtAxisSyncMoveL(DescPose desc_pos, int tool, int user, float vel, float acc, float ovl, float blendR, ExaxisPos epos, uint8_t offset_flag, DescPose offset_pos, int config = -1);

Przykład kodu ruchu synchronicznego z ruchem liniowym robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int testSyncMoveL()
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
      //1. Kalibracja i zastosowanie układu współrzędnych narzędzia robota. Możesz użyć metody czterech lub sześciu punktów do kalibracji i zastosowania układu współrzędnych narzędzia. Interfejsy związane z kalibracją układu współrzędnych narzędzia są następujące:
      //  int SetToolPoint(int point_num); //Ustawia punkt odniesienia narzędzia - metoda sześciu punktów
      //  int ComputeTool(ref DescPose tcp_pose); //Oblicza układ współrzędnych narzędzia
      //  int SetTcp4RefPoint(int point_num);  //Ustawia punkt odniesienia narzędzia - metoda czterech punktów
      //  int ComputeTcp4(ref DescPose tcp_pose);  //Oblicza układ współrzędnych narzędzia - metoda czterech punktów
      //  int SetToolCoord(int id, DescPose coord, int type, int install); //Ustawia i stosuje układ współrzędnych narzędzia
      //  int SetToolList(int id, DescPose coord, int type, int install);  //Ustawia i stosuje listę układów współrzędnych narzędzia
      //2. Ustaw parametry komunikacji UDP i załaduj komunikację UDP
      robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10);
      robot.ExtDevLoadUDPDriver();
      //3. Ustaw parametry osi rozszerzonej, w tym typ osi rozszerzonej, parametry sterownika osi rozszerzonej, parametry DH osi rozszerzonej
      robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0); //Jednoosiowy pozycjoner i parametry DH
      robot.SetRobotPosToAxis(1); //Pozycja montażowa osi rozszerzonej
      robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0); //Parametry sterownika serwonapędu. W tym przykładzie dla pozycjonera jednoosiowego wystarczy ustawić parametry jednego sterownika. Jeśli wybierzesz typ osi rozszerzonej zawierający wiele osi, musisz ustawić parametry sterownika dla każdej osi.
      //4. Włącz zasilanie wybranej osi i wykonaj powrót do zera
      robot.ExtAxisServoOn(1, 0);
      robot.ExtAxisSetHoming(1, 0, 20, 3);
      //5. Wykonaj kalibrację układu współrzędnych osi rozszerzonej i zastosuj go
      DescPose pos = {/* Wprowadź współrzędne swojego punktu kalibracyjnego */ };
      robot.SetRefPointInExAxisEnd(pos);
      robot.PositionorSetRefPoint(1); /*Musisz skalibrować oś rozszerzoną za pomocą czterech różnych pozycji punktów, dlatego musisz wywołać ten interfejs 4 razy, aby zakończyć kalibrację */
      DescPose coord = {};
      robot.PositionorComputeECoordSys(coord); //Oblicz wynik kalibracji osi rozszerzonej
      robot.ExtAxisActiveECoordSys(1, 1, coord, 1); //Zastosuj wynik kalibracji do układu współrzędnych osi rozszerzonej
      //6. Kalibracja układu współrzędnych obiektu na osi rozszerzonej. Będziesz potrzebować następujących interfejsów:
      //int SetWObjCoordPoint(int point_num);
      //int ComputeWObjCoord(int method, ref DescPose wobj_pose);
      //int SetWObjCoord(int id, DescPose coord);
      //int SetWObjList(int id, DescPose coord);
      //7. Zapisz punkt początkowy synchronicznego ruchu liniowego
      DescPose startdescPose = {/* Wprowadź swoje współrzędne */ };
      JointPos startjointPos = {/* Wprowadź swoje współrzędne */ };
      ExaxisPos startexaxisPos = {/* Wprowadź współrzędne punktu początkowego osi rozszerzonej */ };
      //8. Zapisz współrzędne punktu końcowego synchronicznego ruchu liniowego
      DescPose enddescPose = {/* Wprowadź swoje współrzędne */ };
      JointPos endjointPos = {/* Wprowadź swoje współrzędne */ };
      ExaxisPos endexaxisPos = {/* Wprowadź współrzędne punktu końcowego osi rozszerzonej */ };
      //9. Napisz program ruchu synchronicznego
      //Przejedź do punktu początkowego, zakładając, że stosowane układy współrzędnych narzędzia i obiektu to 1
      robot.ExtAxisMove(startexaxisPos, 20);
      DescPose offdese = { 0, 0, 0, 0, 0, 0 };
      robot.MoveJ(&startjointPos, &startdescPose, 1, 1, 100, 100, 100, &startexaxisPos, 0, 0, &offdese);
      //Rozpocznij ruch synchroniczny
      robot.ExtAxisSyncMoveL(endjointPos, enddescPose, 1, 1, 100, 100, 100, 0, endexaxisPos, 0, offdese);

      robot.MoveJ(&startjointPos, 1, 1, 100, 100, 100, &startexaxisPos, 0, 0, &offdese);
      //Rozpocznij ruch synchroniczny
      robot.ExtAxisSyncMoveL(enddescPose, 1, 1, 100, 100, 100, 0, endexaxisPos, 0, offdese);
      robot.CloseRPC();
    }

Ruch synchroniczny osi rozszerzonej UDP z ruchem łukowym robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
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
    * @param [in] poffset_flag 0 - brak przesunięcia, 1 - przesunięcie w układzie bazowym/układzie obiektu, 2 - przesunięcie w układzie narzędzia
    * @param [in] offset_pos_p Wartość przesunięcia pozy i orientacji
    * @param [in] joint_pos_t Pozycja stawów punktu docelowego, jednostka deg
    * @param [in] desc_pos_t Poza i orientacja punktu docelowego w kartezjańskim układzie współrzędnych
    * @param [in] ttool Numer narzędzia, zakres [0~14]
    * @param [in] tuser Numer obiektu, zakres [0~14]
    * @param [in] tvel Procent prędkości, zakres [0~100]
    * @param [in] tacc Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param [in] epos_t Pozycja osi rozszerzonej punktu docelowego, jednostka mm
    * @param [in] toffset_flag 0 - brak przesunięcia, 1 - przesunięcie w układzie bazowym/układzie obiektu, 2 - przesunięcie w układzie narzędzia
    * @param [in] offset_pos_t Wartość przesunięcia pozy i orientacji
    * @param [in] ovl Współczynnik skalowania prędkości, zakres [0~100]
    * @param [in] blendR [-1.0] - ruch do pozycji (blokujący), [0~1000.0] - promień wygładzania (nieblokujący), jednostka mm
    * @return Kod błędu
    */
    errno_t ExtAxisSyncMoveC(JointPos joint_pos_p, DescPose desc_pos_p, int ptool, int puser, float pvel, float pacc, ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p, JointPos joint_pos_t, DescPose desc_pos_t, int ttool, int tuser, float tvel, float tacc, ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t, float ovl, float blendR);

Ruch synchroniczny osi rozszerzonej UDP z ruchem łukowym robota (automatyczne obliczanie odwrotnej kinematyki)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Ruch synchroniczny osi rozszerzonej UDP z ruchem łukowym robota (automatyczne obliczanie odwrotnej kinematyki)
    * @param [in] desc_pos_p Poza i orientacja punktu pośredniego w kartezjańskim układzie współrzędnych
    * @param [in] ptool Numer narzędzia, zakres [0~14]
    * @param [in] puser Numer obiektu, zakres [0~14]
    * @param [in] pvel Procent prędkości, zakres [0~100]
    * @param [in] pacc Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param [in] epos_p Pozycja osi rozszerzonej punktu pośredniego, jednostka mm
    * @param [in] poffset_flag 0 - brak przesunięcia, 1 - przesunięcie w układzie bazowym/układzie obiektu, 2 - przesunięcie w układzie narzędzia
    * @param [in] offset_pos_p Wartość przesunięcia pozy i orientacji
    * @param [in] desc_pos_t Poza i orientacja punktu docelowego w kartezjańskim układzie współrzędnych
    * @param [in] ttool Numer narzędzia, zakres [0~14]
    * @param [in] tuser Numer obiektu, zakres [0~14]
    * @param [in] tvel Procent prędkości, zakres [0~100]
    * @param [in] tacc Procent przyspieszenia, zakres [0~100], tymczasowo niedostępne
    * @param [in] epos_t Pozycja osi rozszerzonej punktu docelowego, jednostka mm
    * @param [in] toffset_flag 0 - brak przesunięcia, 1 - przesunięcie w układzie bazowym/układzie obiektu, 2 - przesunięcie w układzie narzędzia
    * @param [in] offset_pos_t Wartość przesunięcia pozy i orientacji
    * @param [in] ovl Współczynnik skalowania prędkości, zakres [0~100]
    * @param [in] blendR [-1.0] - ruch do pozycji (blokujący), [0~1000.0] - promień wygładzania (nieblokujący), jednostka mm
    * @param [in] config Konfiguracja przestrzeni stawów dla odwrotnej kinematyki, [-1] - obliczenia w oparciu o bieżącą pozycję stawów, [0~7] - obliczenia zgodnie z określoną konfiguracją przestrzeni stawów
    * @return Kod błędu
    */
    errno_t ExtAxisSyncMoveC(DescPose desc_pos_p, int ptool, int puser, float pvel, float pacc, ExaxisPos epos_p, uint8_t poffset_flag, DescPose offset_pos_p, DescPose desc_pos_t, int ttool, int tuser, float tvel, float tacc, ExaxisPos epos_t, uint8_t toffset_flag, DescPose offset_pos_t, float ovl, float blendR, int config = -1);

Przykład kodu ruchu synchronicznego z ruchem łukowym robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int testSyncMoveC()
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
      //1. Kalibracja i zastosowanie układu współrzędnych narzędzia robota. Możesz użyć metody czterech lub sześciu punktów do kalibracji i zastosowania układu współrzędnych narzędzia. Interfejsy związane z kalibracją układu współrzędnych narzędzia są następujące:
      //  int SetToolPoint(int point_num); //Ustawia punkt odniesienia narzędzia - metoda sześciu punktów
      //  int ComputeTool(ref DescPose tcp_pose); //Oblicza układ współrzędnych narzędzia
      //  int SetTcp4RefPoint(int point_num);  //Ustawia punkt odniesienia narzędzia - metoda czterech punktów
      //  int ComputeTcp4(ref DescPose tcp_pose);  //Oblicza układ współrzędnych narzędzia - metoda czterech punktów
      //  int SetToolCoord(int id, DescPose coord, int type, int install); //Ustawia i stosuje układ współrzędnych narzędzia
      //  int SetToolList(int id, DescPose coord, int type, int install);  //Ustawia i stosuje listę układów współrzędnych narzędzia
      //2. Ustaw parametry komunikacji UDP i załaduj komunikację UDP
      robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10);
      robot.ExtDevLoadUDPDriver();
      //3. Ustaw parametry osi rozszerzonej, w tym typ osi rozszerzonej, parametry sterownika osi rozszerzonej, parametry DH osi rozszerzonej
      robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0); //Jednoosiowy pozycjoner i parametry DH
      robot.SetRobotPosToAxis(1); //Pozycja montażowa osi rozszerzonej
      robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0); //Parametry sterownika serwonapędu. W tym przykładzie dla pozycjonera jednoosiowego wystarczy ustawić parametry jednego sterownika. Jeśli wybierzesz typ osi rozszerzonej zawierający wiele osi, musisz ustawić parametry sterownika dla każdej osi.
      //4. Włącz zasilanie wybranej osi i wykonaj powrót do zera
      robot.ExtAxisServoOn(1, 0);
      robot.ExtAxisSetHoming(1, 0, 20, 3);
      //5. Wykonaj kalibrację układu współrzędnych osi rozszerzonej i zastosuj go
      DescPose pos = {/* Wprowadź współrzędne swojego punktu kalibracyjnego */ };
      robot.SetRefPointInExAxisEnd(pos);
      robot.PositionorSetRefPoint(1); /*Musisz skalibrować oś rozszerzoną za pomocą czterech różnych pozycji punktów, dlatego musisz wywołać ten interfejs 4 razy, aby zakończyć kalibrację */
      DescPose coord = {};
      robot.PositionorComputeECoordSys(coord); //Oblicz wynik kalibracji osi rozszerzonej
      robot.ExtAxisActiveECoordSys(1, 1, coord, 1); //Zastosuj wynik kalibracji do układu współrzędnych osi rozszerzonej
      //6. Kalibracja układu współrzędnych obiektu na osi rozszerzonej. Będziesz potrzebować następujących interfejsów:
      //int SetWObjCoordPoint(int point_num);
      //int ComputeWObjCoord(int method, ref DescPose wobj_pose);
      //int SetWObjCoord(int id, DescPose coord);
      //int SetWObjList(int id, DescPose coord);
      //7. Zapisz punkt początkowy synchronicznego ruchu łukowego
      DescPose startdescPose = {/* Wprowadź swoje współrzędne */ };
      JointPos startjointPos = {/* Wprowadź swoje współrzędne */ };
      ExaxisPos startexaxisPos = {/* Wprowadź współrzędne punktu początkowego osi rozszerzonej */ };
      //8. Zapisz współrzędne punktu końcowego synchronicznego ruchu łukowego
      DescPose enddescPose = {/* Wprowadź swoje współrzędne */ };
      JointPos endjointPos = {/* Wprowadź swoje współrzędne */ };
      ExaxisPos endexaxisPos = {/* Wprowadź współrzędne punktu końcowego osi rozszerzonej */ };
      //9. Zapisz współrzędne punktu pośredniego synchronicznego ruchu łukowego
      DescPose middescPose = {/* Wprowadź swoje współrzędne */ };
      JointPos midjointPos = {/* Wprowadź swoje współrzędne */ };
      ExaxisPos midexaxisPos = {/* Wprowadź współrzędne osi rozszerzonej w punkcie pośrednim łuku robota */ };
      //10. Napisz program ruchu synchronicznego
      //Przejedź do punktu początkowego, zakładając, że stosowane układy współrzędnych narzędzia i obiektu to 1
      robot.ExtAxisMove(startexaxisPos, 20);
      DescPose offdese = { 0, 0, 0, 0, 0, 0 };
      robot.MoveJ(&startjointPos, &startdescPose, 1, 1, 100, 100, 100, &startexaxisPos, 0, 0, &offdese);
      //Rozpocznij ruch synchroniczny
      robot.ExtAxisSyncMoveC(midjointPos, middescPose, 1, 1, 100, 100, midexaxisPos, 0, offdese, endjointPos, enddescPose, 1, 1, 100, 100, endexaxisPos, 0, offdese, 100, 0);
      robot.MoveJ(&startjointPos, 1, 1, 100, 100, 100, &startexaxisPos, 0, 0, &offdese);
      //Rozpocznij ruch synchroniczny
      robot.ExtAxisSyncMoveC(middescPose, 1, 1, 100, 100, midexaxisPos, 0, offdese, enddescPose, 1, 1, 100, 100, endexaxisPos, 0, offdese, 100, 0);
      robot.CloseRPC();
    }

Ustawianie rozszerzonego wyjścia cyfrowego (DO)
++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia rozszerzone wyjście cyfrowe (DO)
    * @param [in] DONum Numer DO
    * @param [in] bOpen Stan przełącznika true - włączone; false - wyłączone
    * @param [in] smooth Czy wygładzać
    * @param [in] block Czy blokować
    * @return Kod błędu
    */
    errno_t SetAuxDO(int DONum, bool bOpen, bool smooth, bool block);

Ustawianie rozszerzonego wyjścia analogowego (AO)
++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia rozszerzone wyjście analogowe (AO)
    * @param [in] AONum Numer AO
    * @param [in] value Wartość analogowa [0-4095]
    * @param [in] block Czy blokować
    * @return Kod błędu
    */
    errno_t SetAuxAO(int AONum, double value, bool block);

Ustawianie czasu filtracji wejścia rozszerzonego DI
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia czas filtracji wejścia rozszerzonego DI
    * @param [in] filterTime Czas filtracji (ms)
    * @return Kod błędu
    */
    errno_t SetAuxDIFilterTime(int filterTime);

Ustawianie czasu filtracji wejścia rozszerzonego AI
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia czas filtracji wejścia rozszerzonego AI
    * @param [in] filterTime Czas filtracji (ms)
    * @return Kod błędu
    */
    errno_t SetAuxAIFilterTime(int filterTime);

Oczekiwanie na wejście rozszerzone DI
+++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Oczekuje na wejście rozszerzone DI
    * @param [in] DINum Numer DI
    * @param [in] bOpen Stan przełącznika 0 - wyłączone; 1 - włączone
    * @param [in] time Maksymalny czas oczekiwania (ms)
    * @param [in] errorAlarm Czy kontynuować ruch
    * @return Kod błędu
    */
    errno_t WaitAuxDI(int DINum, bool bOpen, int time, bool errorAlarm);

Oczekiwanie na wejście rozszerzone AI
+++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Oczekuje na wejście rozszerzone AI
    * @param [in] AINum Numer AI
    * @param [in] sign 0 - większe niż; 1 - mniejsze niż
    * @param [in] value Wartość AI
    * @param [in] time Maksymalny czas oczekiwania (ms)
    * @param [in] errorAlarm Czy kontynuować ruch
    * @return Kod błędu
    */
    errno_t WaitAuxAI(int AINum, int sign, int value, int time, bool errorAlarm);

Pobieranie wartości rozszerzonego DI
++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera wartość rozszerzonego DI
    * @param [in] DINum Numer DI
    * @param [in] isNoBlock Czy blokować
    * @param [out] isOpen 0 - wyłączone; 1 - włączone
    * @return Kod błędu
    */
    errno_t GetAuxDI(int DINum, bool isNoBlock, bool& isOpen);

Pobieranie wartości rozszerzonego AI
++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera wartość rozszerzonego AI
    * @param [in] AINum Numer AI
    * @param [in] isNoBlock Czy blokować
    * @param [in] value Wartość wejściowa
    * @return Kod błędu
    */
    errno_t GetAuxAI(int AINum, bool isNoBlock, int& value);

Przykład kodu rozszerzonego IO
++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestAuxDOAO(void)
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
      for (int i = 0; i < 128; i++)
      {
        robot.SetAuxDO(i, true, false, true);
        Sleep(100);
      }
      for (int i = 0; i < 128; i++)
      {
        robot.SetAuxDO(i, false, false, true);
        Sleep(100);
      }
      for (int i = 0; i < 409; i++)
      {
        robot.SetAuxAO(0, i * 10, true);
        robot.SetAuxAO(1, 4095 - i * 10, true);
        robot.SetAuxAO(2, i * 10, true);
        robot.SetAuxAO(3, 4095 - i * 10, true);
        Sleep(10);
      }
      robot.SetAuxDIFilterTime(10);
      robot.SetAuxAIFilterTime(0, 10);
      for (int i = 0; i < 20; i++)
      {
        bool curValue = false;
        int rtn = robot.GetAuxDI(i, false, curValue);
        cout << "DI" << i << "  " << curValue << endl;
      }
      int curValue = -1;
      for (int i = 0; i < 4; i++)
      {
        rtn = robot.GetAuxAI(i, true, curValue);
      }
      robot.WaitAuxDI(1, false, 1000, false);
      robot.WaitAuxAI(1, 1, 132, 1000, false);
      robot.CloseRPC();
      return 0;
    }

Włączanie zasilania mobilnego urządzenia
+++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Włącza zasilanie mobilnego urządzenia
    * @param enable false - wyłączone; true - włączone
    * @return Kod błędu
    */
    errno_t TractorEnable(bool enable);

Powrót do zera mobilnego urządzenia
++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Powrót do zera mobilnego urządzenia
    * @return Kod błędu
    */
    errno_t TractorHoming();

Ruch liniowy mobilnego urządzenia
++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ruch liniowy mobilnego urządzenia
    * @param distance Dystans ruchu liniowego (mm)
    * @param vel Procent prędkości ruchu liniowego (0-100)
    * @return Kod błędu
    */
    errno_t TractorMoveL(double distance, double vel);

Ruch łukowy mobilnego urządzenia
+++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ruch łukowy mobilnego urządzenia
    * @param radio Promień ruchu łukowego (mm)
    * @param angle Kąt ruchu łukowego (°)
    * @param vel Procent prędkości ruchu liniowego (0-100)
    * @return Kod błędu
    */
    errno_t TractorMoveC(double radio, double angle, double vel);

Zatrzymanie ruchu mobilnego urządzenia
++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Zatrzymuje ruch mobilnego urządzenia
    * @return Kod błędu
    */
    errno_t TractorStop();

Przykład kodu mobilnego urządzenia
++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestTractor(void)
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
      robot.ExtDevSetUDPComParam("192.168.58.2", 2021, 2, 50, 5, 50, 1, 50, 10, 1);
      robot.ExtDevLoadUDPDriver();
      rtn = robot.ExtAxisServoOn(1, 1);
      rtn = robot.ExtAxisServoOn(2, 1);
      robot.Sleep(2000);
      robot.ExtAxisSetHoming(1, 0, 10, 2);
      robot.Sleep(2000);
      rtn = robot.ExtAxisSetHoming(2, 0, 10, 2);
      robot.Sleep(4000);
      robot.ExtAxisParamConfig(1, 0, 0, 50000, -50000, 1000, 1000, 6.280, 16384, 200, 0, 0, 0);
      robot.ExtAxisParamConfig(2, 0, 0, 50000, -50000, 1000, 1000, 6.280, 16384, 200, 0, 0, 0);
      robot.SetAxisDHParaConfig(5, 0, 0, 0, 0, 0, 0, 0, 0);
      robot.TractorEnable(false);
      robot.Sleep(2000);
      robot.TractorEnable(true);
      robot.Sleep(2000);
      robot.TractorHoming();
      robot.Sleep(2000);
      robot.TractorMoveL(100, 2);
      robot.Sleep(5000);
      robot.TractorStop();
      robot.TractorMoveL(-100, 20);
      robot.Sleep(5000);
      robot.TractorMoveC(300, 90, 20);
      robot.Sleep(10000);
      robot.TractorMoveC(300, -90, 20);
      robot.Sleep(1);
      robot.CloseRPC();
      return 0;
    }

Ustawianie czasu zakończenia pozycjonowania osi rozszerzonej UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia czas zakończenia pozycjonowania osi rozszerzonej UDP
    * @param [in] time Czas zakończenia pozycjonowania [ms]
    * @return Kod błędu
    */
    errno_t SetExAxisCmdDoneTime(double time);