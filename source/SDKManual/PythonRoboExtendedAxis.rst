Oś rozszerzenia
===============

.. toctree:: 
    :maxdepth: 5

Ustawianie parametrów osi rozszerzenia 485
+++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AuxServoSetParam(servoId,servoCompany,servoModel,servoSoftVersion, servoResolution,axisMechTransRatio)``"
    "Opis", "Ustawianie parametrów osi rozszerzenia 485"
    "Parametry wymagane", "- ``servoId``: ID serwonapędu, zakres [1-15], odpowiada ID węzła podrzędnego;
    - ``servoCompany``: Producent serwonapędu, 1-DynaTek;
    - ``servoModel``: Model serwonapędu, 1-FD100-750C;
    - ``servoSoftVersion``: Wersja oprogramowania serwonapędu, 1-V1.0;
    - ``servoResolution``: Rozdzielczość enkodera;
    - ``axisMechTransRatio``: Przełożenie mechaniczne;"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Pobieranie parametrów konfiguracyjnych osi rozszerzenia 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AuxServoGetParam(servoId)``"
    "Opis", "Pobieranie parametrów konfiguracyjnych osi rozszerzenia 485"
    "Parametry wymagane", "- ``servoId``: ID serwonapędu, zakres [1-15], odpowiada ID węzła podrzędnego;"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode;
    - ``servoCompany``: Producent serwonapędu, 1-DynaTek;
    - ``servoModel``: Model serwonapędu, 1-FD100-750C;
    - ``servoSoftVersion``: Wersja oprogramowania serwonapędu, 1-V1.0;
    - ``servoResolution``: Rozdzielczość enkodera;
    - ``axisMechTransRatio``: Przełożenie mechaniczne;"

Ustawianie włączenia/wyłączenia osi rozszerzenia 485
++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AuxServoEnable(servoId,status)``"
    "Opis", "Ustawianie włączenia/wyłączenia osi rozszerzenia 485"
    "Parametry wymagane", "- ``servoId``: ID serwonapędu, zakres [1-15], odpowiada ID węzła podrzędnego;
    - ``status``: Stan włączenia, 0-wyłącz, 1-włącz;"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie trybu sterowania osi rozszerzenia 485
++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AuxServoSetControlMode(servoId,mode)``"
    "Opis", "Ustawianie trybu sterowania osi rozszerzenia 485"
    "Parametry wymagane", "- ``servoId``: ID serwonapędu, zakres [1-15], odpowiada ID węzła podrzędnego;
    - ``mode``: Tryb sterowania, 0-tryb pozycyjny, 1-tryb prędkościowy;"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie pozycji docelowej osi rozszerzenia 485 (tryb pozycyjny)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AuxServoSetTargetPos(servoId,pos,speed)``"
    "Opis", "Ustawianie pozycji docelowej osi rozszerzenia 485 (tryb pozycyjny)"
    "Parametry wymagane", "- ``servoId``: ID serwonapędu, zakres [1-15], odpowiada ID węzła podrzędnego;
    - ``pos``: Pozycja docelowa, mm lub °;
    - ``speed``: Prędkość docelowa, mm/s lub °/s;"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie momentu obrotowego docelowego osi rozszerzenia 485 (tryb momentowy) - tymczasowo niedostępne
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AuxServoSetTargetTorque(servoId,torque)``"
    "Opis", "Ustawianie momentu obrotowego docelowego osi rozszerzenia 485 (tryb momentowy)"
    "Parametry wymagane", "- ``servoId``: ID serwonapędu, zakres [1-15], odpowiada ID węzła podrzędnego;
    - ``torque``: Moment obrotowy docelowy, Nm;"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie powrotu do zera osi rozszerzenia 485
++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AuxServoHoming(servoId,mode,searchVel,latchVel)``"
    "Opis", "Ustawianie powrotu do zera osi rozszerzenia 485"
    "Parametry wymagane", "- ``servoId``: ID serwonapędu, zakres [1-15], odpowiada ID węzła podrzędnego;
    - ``mode``: Tryb powrotu do zera, 1-powrót do zera w bieżącej pozycji; 2-powrót do zera z ograniczeniem ujemnym; 3-powrót do zera z ograniczeniem dodatnim;
    - ``searchVel``: Prędkość poszukiwania zera, mm/s lub °/s;
    - ``latchVel``: Prędkość zatrzasku, mm/s lub °/s;"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Czyszczenie informacji o błędzie osi rozszerzenia 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AuxServoClearError(servoId)``"
    "Opis", "Czyszczenie informacji o błędzie osi rozszerzenia 485"
    "Parametry wymagane", "- ``servoId``: ID serwonapędu, zakres [1-15], odpowiada ID węzła podrzędnego;"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Pobieranie stanu serwonapędu osi rozszerzenia 485
++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AuxServoGetStatus(servoId)``"
    "Opis", "Pobieranie stanu serwonapędu osi rozszerzenia 485"
    "Parametry wymagane", "- ``servoId``: ID serwonapędu, zakres [1-15], odpowiada ID węzła podrzędnego;"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode;
    - ``servoErrCode``: Kod błędu serwonapędu
    - ``servoState``: Stan serwonapędu bit0:0-wyłączony; 1-włączony; bit1:0-brak ruchu; 1-w ruchu; bit2 0-ograniczenie dodatnie nieaktywne; 1-ograniczenie dodatnie aktywne; bit3 0-ograniczenie ujemne nieaktywne; 1-ograniczenie ujemne aktywne; bit4 0-brak pozycjonowania; 1-pozycjonowanie zakończone; bit5:0-brak powrotu do zera; 1-powrót do zera zakończony;
    - ``servoPos``: Bieżąca pozycja serwonapędu mm lub °;
    - ``servoSpeed``: Bieżąca prędkość serwonapędu mm/s lub °/s;
    - ``servoTorque``: Bieżący moment obrotowy serwonapędu Nm;"

Ustawianie prędkości docelowej osi rozszerzenia 485 (tryb prędkościowy)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AuxServoSetTargetSpeed(servoId,speed)``"
    "Opis", "Ustawianie prędkości docelowej osi rozszerzenia 485 (tryb prędkościowy)"
    "Parametry wymagane", "- ``servoId``: ID serwonapędu, zakres [1-15], odpowiada ID węzła podrzędnego;
    - ``speed``: Prędkość docelowa, mm/s lub °/s;"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie numeru osi danych osi rozszerzenia 485 w sprzężeniu zwrotnym stanu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AuxServosetStatusID(servoId)``"
    "Opis", "Ustawianie numeru osi danych osi rozszerzenia 485 w sprzężeniu zwrotnym stanu"
    "Parametry wymagane", "- ``servoId``: ID serwonapędu, zakres [1-15], odpowiada ID węzła podrzędnego;"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie przyspieszenia i opóźnienia ruchu osi rozszerzenia 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AuxServoSetAcc(acc, dec)``"
    "Opis", "Ustawianie przyspieszenia i opóźnienia ruchu osi rozszerzenia 485"
    "Parametry wymagane", "- ``acc``: Przyspieszenie ruchu osi rozszerzenia 485
    - ``dec``: Opóźnienie ruchu osi rozszerzenia 485"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie przyspieszenia i opóźnienia awaryjnego zatrzymania osi rozszerzenia 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AuxServoSetEmergencyStopAcc(acc, dec)``"
    "Opis", "Ustawianie przyspieszenia i opóźnienia awaryjnego zatrzymania osi rozszerzenia 485"
    "Parametry wymagane", "- ``acc``: Przyspieszenie awaryjnego zatrzymania osi rozszerzenia 485
    - ``dec``: Opóźnienie awaryjnego zatrzymania osi rozszerzenia 485"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Pobieranie przyspieszenia i opóźnienia ruchu osi rozszerzenia 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AuxServoGetAcc()``"
    "Opis", "Pobieranie przyspieszenia i opóźnienia ruchu osi rozszerzenia 485"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``acc``: Przyspieszenie ruchu osi rozszerzenia 485
    - ``dec``: Opóźnienie ruchu osi rozszerzenia 485"

Pobieranie przyspieszenia i opóźnienia awaryjnego zatrzymania osi rozszerzenia 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AuxServoGetEmergencyStopAcc()``"
    "Opis", "Pobieranie przyspieszenia i opóźnienia awaryjnego zatrzymania osi rozszerzenia 485"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``acc``: Przyspieszenie awaryjnego zatrzymania osi rozszerzenia 485
    - ``dec``: Opóźnienie awaryjnego zatrzymania osi rozszerzenia 485"

Przykład kodu sterowania osią rozszerzenia
++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    retval = robot.AuxServoSetParam(1, 1, 1, 1, 131072, 15.45)
    print(f"AuxServoSetParam is: {retval}")
    servoCompany = 0
    servoModel = 0
    servoSoftVersion = 0
    servoResolution = 0
    axisMechTransRatio = 0.0
    retval, servoCompany, servoModel, servoSoftVersion, servoResolution, axisMechTransRatio = robot.AuxServoGetParam(1)
    print(f"servoCompany {servoCompany}\n"
          f"servoModel {servoModel}\n"
          f"servoSoftVersion {servoSoftVersion}\n"
          f"servoResolution {servoResolution}\n"
          f"axisMechTransRatio {axisMechTransRatio}\n")
    retval = robot.AuxServoSetParam(1, 10, 11, 12, 13, 14)
    print(f"AuxServoSetParam is: {retval}")
    retval, servoCompany, servoModel, servoSoftVersion, servoResolution, axisMechTransRatio = robot.AuxServoGetParam(1)
    print(f"servoCompany {servoCompany}\n"
          f"servoModel {servoModel}\n"
          f"servoSoftVersion {servoSoftVersion}\n"
          f"servoResolution {servoResolution}\n"
          f"axisMechTransRatio {axisMechTransRatio}\n")
    retval = robot.AuxServoSetParam(1, 1, 1, 1, 131072, 36)
    print(f"AuxServoSetParam is: {retval}")
    time.sleep(3)
    robot.AuxServoSetAcc(3000, 3000)
    robot.AuxServoSetEmergencyStopAcc(5000, 5000)
    time.sleep(1)
    emagacc = 0.0
    emagdec = 0.0
    acc = 0.0
    dec = 0.0
    error,emagacc, emagdec = robot.AuxServoGetEmergencyStopAcc()
    print(f"emergency acc is {emagacc}  dec is {emagdec}")
    error,acc, dec = robot.AuxServoGetAcc()
    print(f"acc is {acc}  dec is {dec}")
    robot.AuxServoSetControlMode(1, 0)
    time.sleep(2)
    retval = robot.AuxServoEnable(1, 0)
    print(f"AuxServoEnable disenable {retval}")
    time.sleep(1)
    servoErrCode = 0
    servoState = 0
    servoPos = 0.0
    servoSpeed = 0.0
    servoTorque = 0.0
    retval, servoErrCode, servoState, servoPos, servoSpeed, servoTorque = robot.AuxServoGetStatus(1)
    print(f"AuxServoGetStatus servoState {servoState}")
    time.sleep(1)
    retval = robot.AuxServoEnable(1, 1)
    print(f"AuxServoEnable enable {retval}")
    time.sleep(1)
    retval, servoErrCode, servoState, servoPos, servoSpeed, servoTorque = robot.AuxServoGetStatus(1)
    print(f"AuxServoGetStatus servoState {servoState}")
    time.sleep(1)
    retval = robot.AuxServoHoming(1, 1, 5, 1,100)
    print(f"AuxServoHoming {retval}")
    time.sleep(3)
    retval = robot.AuxServoSetTargetPos(1, 200, 30,100)
    print(f"AuxServoSetTargetPos {retval}")
    time.sleep(1)
    retval, servoErrCode, servoState, servoPos, servoSpeed, servoTorque = robot.AuxServoGetStatus(1)
    print(f"AuxServoGetStatus servoSpeed {servoSpeed}")
    time.sleep(8)
    robot.AuxServoSetControlMode(1, 1)
    time.sleep(2)
    robot.AuxServoEnable(1, 0)
    time.sleep(1)
    robot.AuxServoEnable(1, 1)
    time.sleep(1)
    robot.AuxServoSetTargetSpeed(1, 100, 80)
    time.sleep(5)
    robot.AuxServoSetTargetSpeed(1, 0, 80)
    robot.CloseRPC()

Konfiguracja parametrów komunikacji UDP dla osi rozszerzenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ExtDevSetUDPComParam(ip, port, period, lossPkgTime, lossPkgNum, disconnectTime, reconnectEnable, reconnectPeriod, reconnectNum, selfConnect)``"
    "Opis", "Konfiguracja parametrów komunikacji UDP dla osi rozszerzenia"
    "Parametry wymagane", "
    - ``ip``: Adres IP PLC;
    - ``port``: Numer portu;
    - ``period``: Okres komunikacji (ms, tymczasowo niedostępne);
    - ``lossPkgTime``: Czas wykrywania utraty pakietów (ms);
    - ``lossPkgNum``: Liczba utraconych pakietów;
    - ``disconnectTime``: Czas potwierdzenia przerwania komunikacji;
    - ``reconnectEnable``: Włączenie automatycznego ponownego łączenia po przerwaniu komunikacji 0-niewłączone 1-włączone;
    - ``reconnectPeriod``: Odstęp czasu ponownego łączenia (ms);
    - ``reconnectNum``: Liczba ponownych łączeń
    - ``selfConnect``: Czy automatycznie ustanowić połączenie po ponownym uruchomieniu zasilania; 0-nie ustanawiaj połączenia; 1-ustanów połączenie"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Pobieranie parametrów komunikacji UDP dla osi rozszerzenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ExtDevGetUDPComParam()``"
    "Opis", "Pobieranie parametrów komunikacji UDP dla osi rozszerzenia"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "
    - Kod błędu sukces-0 błąd- errcode;
    - ``ip``: Adres IP PLC;
    - ``port``: Numer portu;
    - ``period``: Okres komunikacji (ms, tymczasowo niedostępne);
    - ``lossPkgTime``: Czas wykrywania utraty pakietów (ms);
    - ``lossPkgNum``: Liczba utraconych pakietów;
    - ``disconnectTime``: Czas potwierdzenia przerwania komunikacji;
    - ``reconnectEnable``: Włączenie automatycznego ponownego łączenia po przerwaniu komunikacji 0-niewłączone 1-włączone;
    - ``reconnectPeriod``: Odstęp czasu ponownego łączenia (ms);
    - ``reconnectNum``: Liczba ponownych łączeń
    - ``selfConnect``: Czy automatycznie ponownie połączyć po ponownym uruchomieniu skrzynki kontrolnej; 0-nie łącz ponownie; 1-łącz ponownie"

Ładowanie komunikacji UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ExtDevLoadUDPDriver()``"
    "Opis", "Ładowanie komunikacji UDP"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"
    
Rozładowanie komunikacji UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ExtDevUnloadUDPDriver()``"
    "Opis", "Rozładowanie komunikacji UDP"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Przywracanie połączenia po nieprawidłowym przerwaniu komunikacji UDP osi rozszerzenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ExtDevUDPClientComReset()``"
    "Opis", "Przywracanie połączenia po nieprawidłowym przerwaniu komunikacji UDP osi rozszerzenia"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Zamykanie komunikacji po nieprawidłowym przerwaniu komunikacji UDP osi rozszerzenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ExtDevUDPClientComClose()``"
    "Opis", "Zamykanie komunikacji po nieprawidłowym przerwaniu komunikacji UDP osi rozszerzenia"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Konfiguracja parametrów UDP osi rozszerzenia
++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ExtAxisParamConfig(axisId, axisType, axisDirection, axisMax, axisMin, axisVel, axisAcc,axisLead, encResolution, axisOffect, axisCompany, axisModel, axisEncType)``"
    "Opis", "Konfiguracja parametrów UDP osi rozszerzenia"
    "Parametry wymagane", "
    - ``axisId``: Numer osi [1-4];
    - ``axisType``: Typ osi rozszerzenia 0-przesuwna; 1-obrotowa;
    - ``axisDirection``: Kierunek osi rozszerzenia 0-dodatni; 1-ujemny;
    - ``axisMax``: Maksymalna pozycja osi rozszerzenia mm;
    - ``axisMin``: Minimalna pozycja osi rozszerzenia mm;
    - ``axisVel``: Prędkość mm/s;
    - ``axisAcc``: Przyspieszenie mm/s2;
    - ``axisLead``: Skok śruby mm;
    - ``encResolution``: Rozdzielczość enkodera;
    - ``axisOffect``: Przesunięcie osi rozszerzenia punktu początkowego spoiny;
    - ``axisCompany``: Producent serwonapędu 1-Hechuan; 2-Inovance; 3-Panasonic;
    - ``axisModel``: Model serwonapędu 1-Hechuan-SV-XD3EA040L-E, 2-Hechuan-SV-X2EA150A-A, 1-Inovance-SV620PT5R4I, 1-Panasonic-MADLN15SG, 2-Panasonic-MSDLN25SG, 3-Panasonic-MCDLN35SG;
    - ``axisEncType``: Typ enkodera 0-inkrementacyjny; 1-absolutny;"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Pobieranie parametrów UDP osi rozszerzenia
++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ExtAxisGetParamConfig(self, axisID)``"
    "Opis", "Pobieranie parametrów UDP osi rozszerzenia"
    "Parametry wymagane", "
    - ``axisID``: Numer osi rozszerzenia [1-4]
    - ``axisType``: Typ osi rozszerzenia 0-przesuwna; 1-obrotowa
    - ``axisDirection``: Kierunek osi rozszerzenia 0-dodatni; 1-ujemny
    - ``axisMax``: Maksymalna pozycja osi rozszerzenia mm
    - ``axisMin``: Minimalna pozycja osi rozszerzenia mm
    - ``axisVel``: Prędkość mm/s
    - ``axisAcc``: Przyspieszenie mm/s2
    - ``axisLead``: Skok śruby mm
    - ``encResolution``: Rozdzielczość enkodera
    - ``axisOffect``: Przesunięcie osi rozszerzenia punktu początkowego spoiny
    - ``axisCompany``: Producent serwonapędu 1-Hechuan; 2-Inovance; 3-Panasonic
    - ``axisModel``: Model serwonapędu 1-Hechuan-SV-XD3EA040L-E, 2-Hechuan-SV-X2EA150A-A, 1-Inovance-SV620PT5R4I, 1-Panasonic-MADLN15SG, 2-Panasonic-MSDLN25SG, 3-Panasonic-MCDLN35SG
    - ``axisEncType``: Typ enkodera 0-inkrementacyjny; 1-absolutny
    "
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie pozycji rozszerzonego robota względem osi rozszerzenia
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetRobotPosToAxis(installType)``"
    "Opis", "Ustawianie pozycji rozszerzonego robota względem osi rozszerzenia"
    "Parametry wymagane", "- ``installType``: 0-robot zamontowany na osi zewnętrznej, 1-robot zamontowany poza osią zewnętrzną;"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie konfiguracji parametrów DH układu osi rozszerzenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetAxisDHParaConfig(axisConfig,axisDHd1,axisDHd2,axisDHd3,axisDHd4,axisDHa1, axisDHa2,axisDHa3,axisDHa4)``"
    "Opis", "Ustawianie konfiguracji parametrów DH układu osi rozszerzenia"
    "Parametry wymagane", "
    - ``axisConfig``: Konfiguracja osi zewnętrznej, 0-prosta prowadnica liniowa z jednym stopniem swobody, 1-pozycjoner L z dwoma stopniami swobody, 2-trzech stopni swobody, 3-czterech stopni swobody, 4-pozycjoner z jednym stopniem swobody;
    - ``axisDHd1``: Parametr DH osi zewnętrznej d1 mm;
    - ``axisDHd2``: Parametr DH osi zewnętrznej d2 mm;
    - ``axisDHd3``: Parametr DH osi zewnętrznej d3 mm;
    - ``axisDHd4``: Parametr DH osi zewnętrznej d4 mm;
    - ``axisDHa1``: Parametr DH osi zewnętrznej a1 mm;
    - ``axisDHa2``: Parametr DH osi zewnętrznej a2 mm;
    - ``axisDHa3``: Parametr DH osi zewnętrznej a3 mm;
    - ``axisDHa4``: Parametr DH osi zewnętrznej a4 mm;"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"
                          
Włączanie UDP osi rozszerzenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ExtAxisServoOn(axisID, status)``"
    "Opis", "Włączanie UDP osi rozszerzenia"
    "Parametry wymagane", "- ``axisID``: Numer osi [1-4];
    - ``status``: 0-wyłącz; 1-włącz;"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Powrót do zera UDP osi rozszerzenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ExtAxisSetHoming(axisID, mode, searchVel, latchVel)``"
    "Opis", "Powrót do zera UDP osi rozszerzenia"
    "Parametry wymagane", "
    - ``axisID``: Numer osi [1-4];
    - ``mode``: Sposób powrotu do zera 0-powrót do zera w bieżącej pozycji, 1-powrót do zera z ograniczeniem ujemnym, 2-powrót do zera z ograniczeniem dodatnim;
    - ``searchVel``: Prędkość poszukiwania zera (mm/s);
    - ``latchVel``: Prędkość zatrzasku poszukiwania zera (mm/s);"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Rozpoczęcie punktowego ruchu UDP osi rozszerzenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ExtAxisStartJog( axisID, direction, vel, acc, maxDistance)``"
    "Opis", "Rozpoczęcie punktowego ruchu UDP osi rozszerzenia"
    "Parametry wymagane", "
    - ``axisID``: Numer osi [1-4];
    - ``direction``: Kierunek obrotu 0-ujemny; 1-dodatni;
    - ``vel``: Prędkość (mm/s);
    - ``acc``: Przyspieszenie (mm/s);
    - ``maxDistance``: Maksymalna odległość punktowego ruchu;"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Zatrzymanie punktowego ruchu UDP osi rozszerzenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ExtAxisStopJog(axisID)``"
    "Opis", "Zatrzymanie punktowego ruchu UDP osi rozszerzenia"
    "Parametry wymagane", "- ``axisID``: Numer osi [1-4];"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Przykład kodu konfiguracji i punktowego ruchu UDP osi rozszerzenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    from fairino.Robot import RobotState
    import time

    def main():
        # Dodanie potrzebnych danych stanu w czasie rzeczywistym (jeśli potrzebne)
        # rtn = AddRobotRealtimeState([RobotState.ExaxisCoordID])
        # if rtn != 0:
        #     print(f"✗ Dodanie pola nie powiodło się, kod błędu: {rtn}")
        #     return None
        # print("✓ Pole dodane pomyślnie")

        # Połączenie z kontrolerem robota
        robot = Robot.RPC('192.168.58.2')
        time.sleep(0.5)  # Oczekiwanie na połączenie i odbiór danych

        # Konfiguracja parametrów komunikacji UDP
        rtn = robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 200, 1, 100, 5, 1)
        print(f"ExtDevSetUDPComParam rtn is {rtn}")

        # Pobranie parametrów komunikacji UDP
        error, param = robot.ExtDevGetUDPComParam()
        print("ExtDevGetUDPComParam return ", error)
        print("Parametry komunikacji UDP osi rozszerzenia: ", param)

        # Ładowanie sterownika UDP
        robot.ExtDevLoadUDPDriver()

        # Ustawienie czasu zakończenia polecenia osi rozszerzenia
        rtn = robot.SetExAxisCmdDoneTime(5000.0)
        print(f"SetExAxisCmdDoneTime rtn is {rtn}")

        # Włączenie serwonapędu osi rozszerzenia
        rtn = robot.ExtAxisServoOn(1, 1)
        print(f"ExtAxisServoOn axis id 1 rtn is {rtn}")
        rtn = robot.ExtAxisServoOn(2, 1)
        print(f"ExtAxisServoOn axis id 2 rtn is {rtn}")
        time.sleep(2)

        # Powrót do zera osi rozszerzenia
        robot.ExtAxisSetHoming(1, 0, 10, 2)
        time.sleep(2)
        rtn = robot.ExtAxisSetHoming(2, 0, 10, 2)
        print(f"ExtAxisSetHoming rtn is {rtn}")

        time.sleep(4)

        # Ustawienie pozycji robota względem osi rozszerzenia
        rtn = robot.SetRobotPosToAxis(1)
        print(f"SetRobotPosToAxis rtn is {rtn}")

        # Ustawienie konfiguracji parametrów DH osi rozszerzenia
        rtn = robot.SetAxisDHParaConfig(10, 20, 0, 0, 0, 0, 0, 0, 0)
        print(f"SetAxisDHParaConfig rtn is {rtn}")

        # Konfiguracja parametrów osi rozszerzenia 1
        rtn = robot.ExtAxisParamConfig(1, 1, 1, 1000, -1000, 1000, 1000, 1.905, 262144, 200, 1, 0, 0)
        print(f"ExtAxisParamConfig axis 1 rtn is {rtn}")

        # Pobranie konfiguracji parametrów osi rozszerzenia 1
        rtn, axisType, axisDirection, axisMax, axisMin, axisVel, axisAcc, axisLead, encResolution, axisOffect, axisCompany, axisModel, axisEncType = robot.ExtAxisGetParamConfig(1)
        print(f"axis id 1 ExtAxisGetParamConfig : axisType {axisType}, axisDirection {axisDirection}, axisMax {axisMax}, axisMin {axisMin}, axisVel {axisVel}, axisAcc {axisAcc}, axisLead {axisLead}, encResolution {encResolution}, axisOffect {axisOffect}, axisCompany {axisCompany}, axisModel {axisModel}, axisEncType {axisEncType}")

        # Konfiguracja parametrów osi rozszerzenia 2
        rtn = robot.ExtAxisParamConfig(2, 1, 1, 1000, -1000, 1000, 1000, 4.444, 262144, 200, 1, 0, 0)
        print(f"ExtAxisParamConfig axis 2 rtn is {rtn}")

        # Pobranie konfiguracji parametrów osi rozszerzenia 2
        rtn, axisType, axisDirection, axisMax, axisMin, axisVel, axisAcc, axisLead, encResolution, axisOffect, axisCompany, axisModel, axisEncType = robot.ExtAxisGetParamConfig(2)
        print(f"axis id 2 ExtAxisGetParamConfig : axisType {axisType}, axisDirection {axisDirection}, axisMax {axisMax}, axisMin {axisMin}, axisVel {axisVel}, axisAcc {axisAcc}, axisLead {axisLead}, encResolution {encResolution}, axisOffect {axisOffect}, axisCompany {axisCompany}, axisModel {axisModel}, axisEncType {axisEncType}")

        time.sleep(3)

        # Test punktowego ruchu osi rozszerzenia 1
        robot.ExtAxisStartJog(1, 0, 10, 10, 30)
        time.sleep(1)
        robot.ExtAxisStopJog(1)
        time.sleep(3)
        robot.ExtAxisServoOn(1, 0)

        time.sleep(3)

        # Test punktowego ruchu osi rozszerzenia 2
        robot.ExtAxisStartJog(2, 0, 10, 10, 30)
        time.sleep(1)
        robot.ExtAxisStopJog(2)
        time.sleep(3)
        robot.ExtAxisServoOn(2, 0)

        # Rozładowanie sterownika UDP
        robot.ExtDevUnloadUDPDriver()

        # Zamknięcie połączenia
        robot.CloseRPC()


    # Wywołanie funkcji testowej
    main()

Ustawianie punktu odniesienia układu współrzędnych osi rozszerzenia - metoda czterech punktów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ExtAxisSetRefPoint(pointNum)``"
    "Opis", "Ustawianie punktu odniesienia układu współrzędnych osi rozszerzenia - metoda czterech punktów"
    "Parametry wymagane", "- ``pointNum``: Numer punktu [1-4];"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"
        
Obliczanie układu współrzędnych osi rozszerzenia - metoda czterech punktów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ExtAxisComputeECoordSys()``"
    "Opis", "Obliczanie układu współrzędnych osi rozszerzenia - metoda czterech punktów"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode;
    - ``coord``: Wartość układu współrzędnych osi rozszerzenia [x,y,z,rx,ry,rz];"
                 
Ustawianie punktu odniesienia układu współrzędnych pozycjonera - metoda czterech punktów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``PositionorSetRefPoint(pointNum)``"
    "Opis", "Ustawianie punktu odniesienia układu współrzędnych pozycjonera - metoda czterech punktów"
    "Parametry wymagane", "- ``pointNum``: Numer punktu [1-4];"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Obliczanie układu współrzędnych pozycjonera - metoda czterech punktów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``PositionorComputeECoordSys()``"
    "Opis", "Obliczanie układu współrzędnych pozycjonera - metoda czterech punktów"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode;
    - ``coord``: Wartość układu współrzędnych pozycjonera [x,y,z,rx,ry,rz];"
             
Ustawianie pozy punktu kalibracji w układzie współrzędnych końcówki pozycjonera
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetRefPointInExAxisEnd(pos)``"
    "Opis", "Ustawianie pozy punktu kalibracji w układzie współrzędnych końcówki pozycjonera"
    "Parametry wymagane", "- ``pos``: Wartość pozy [x,y,z,rx,ry,rz];"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Stosowanie układu współrzędnych osi rozszerzenia
+++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ExtAxisActiveECoordSys(applyAxisId,axisCoordNum,coord,calibFlag)``"
    "Opis", "Stosowanie układu współrzędnych osi rozszerzenia"
    "Parametry wymagane", "
    - ``applyAxisId``: Numer osi rozszerzenia bit0-bit3 odpowiada numerom osi rozszerzenia 1-4, np. zastosowanie osi rozszerzenia 1 i 3, to 0b 0000 0101, czyli 5;
    - ``axisCoordNum``: Numer układu współrzędnych osi rozszerzenia;
    - ``coord``: Wartość układu współrzędnych [x,y,z,rx,ry,rz];
    - ``calibFlag``: Flaga kalibracji 0-nie, 1-tak;"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Pobieranie układu współrzędnych osi rozszerzenia
+++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ExtAxisGetCoord()``"
    "Opis", "Pobieranie układu współrzędnych osi rozszerzenia"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``coord``: Układ współrzędnych osi rozszerzenia"

Przykład kodu kalibracji układu współrzędnych osi rozszerzenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    rtn = robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 200, 1, 100, 5, 1)
    print(f"ExtDevSetUDPComParam rtn is {rtn}")
    rtn,udp_params = robot.ExtDevGetUDPComParam()
    ip, port, period, lossPkgTime, lossPkgNum, disconnectTime, reconnectEnable, reconnectPeriod, reconnectNum = udp_params
    patam = (
        f"\nip {ip}\nport {port}\nperiod {period}\nlossPkgTime {lossPkgTime}\n"
        f"lossPkgNum {lossPkgNum}\ndisConntime {disconnectTime}\nreconnecable {reconnectEnable}\n"
        f"reconnperiod {reconnectPeriod}\nreconnnun {reconnectNum}"
    )
    print(f"ExtDevGetUDPComParam rtn is {rtn}{patam}")
    robot.ExtDevLoadUDPDriver()
    rtn = robot.ExtAxisServoOn(1, 1)
    print(f"ExtAxisServoOn axis id 1 rtn is {rtn}")
    rtn = robot.ExtAxisServoOn(2, 1)
    print(f"ExtAxisServoOn axis id 2 rtn is {rtn}")
    time.sleep(2)
    robot.ExtAxisSetHoming(1, 0, 10, 2)
    time.sleep(2)
    rtn = robot.ExtAxisSetHoming(2, 0, 10, 2)
    print(f"ExtAxisSetHoming rtn is {rtn}")
    time.sleep(4)
    rtn = robot.SetRobotPosToAxis(1)
    print(f"SetRobotPosToAxis rtn is {rtn}")
    rtn = robot.SetAxisDHParaConfig(1, 128.5, 206.4, 0, 0, 0, 0, 0, 0)
    print(f"SetAxisDHParaConfig rtn is {rtn}")
    rtn = robot.ExtAxisParamConfig(1, 1, 1, 1000, -1000, 1000, 1000, 1.905, 262144, 200, 1, 0, 0)
    print(f"ExtAxisParamConfig axis 1 rtn is {rtn}")
    rtn = robot.ExtAxisParamConfig(2, 1, 1, 1000, -1000, 1000, 1000, 4.444, 262144, 200, 1, 0, 0)
    print(f"ExtAxisParamConfig axis 2 rtn is {rtn}")
    toolCoord = [0, 0, 210, 0, 0, 0]
    robot.SetToolCoord(1, toolCoord, 0, 0, 1, 0)
    jSafe = [115.193, -96.149, 92.489, -87.068, -89.15, -83.488]
    j1 = [117.559, -92.624, 100.329, -96.909, -94.057, -83.488]
    j2 = [112.239, -90.096, 99.282, -95.909, -89.824, -83.488]
    j3 = [110.839, -83.473, 93.166, -89.22, -90.499, -83.487]
    j4 = [107.935, -83.572, 95.424, -92.873, -87.933, -83.488]
    descSafe = [0.0,0.0,0.0,0.0,0.0,0.0]
    desc1 = [0.0,0.0,0.0,0.0,0.0,0.0]
    desc2 = [0.0,0.0,0.0,0.0,0.0,0.0]
    desc3 = [0.0,0.0,0.0,0.0,0.0,0.0]
    desc4 = [0.0,0.0,0.0,0.0,0.0,0.0]
    exaxisPos = [0.0,0.0,0.0,0.0]
    offdese = [0.0,0.0,0.0,0.0,0.0,0.0]
    error, descSafe = robot.GetForwardKin(jSafe)
    robot.MoveJ(joint_pos=jSafe,tool= 1,user= 0,vel= 100)
    time.sleep(2)
    error, desc1 = robot.GetForwardKin(j1)
    robot.MoveJ(joint_pos=j1,tool= 1,user= 0,vel= 100)
    time.sleep(2)
    actualTCPPos = [0.0,0.0,0.0,0.0,0.0,0.0]
    error, actualTCPPos = robot.GetActualTCPPose(0)
    robot.SetRefPointInExAxisEnd(actualTCPPos)
    rtn = robot.PositionorSetRefPoint(1)
    print(f"PositionorSetRefPoint 1 rtn is {rtn}")
    time.sleep(2)
    robot.MoveJ(joint_pos=jSafe,tool= 1,user= 0,vel= 100)
    robot.ExtAxisStartJog(1, 0, 50, 50, 10)
    time.sleep(1)
    robot.ExtAxisStartJog(2, 0, 50, 50, 10)
    time.sleep(1)
    error, desc2 = robot.GetForwardKin(j2)
    rtn = robot.MoveJ(joint_pos=j2,tool= 1,user= 0,vel= 100)
    rtn = robot.PositionorSetRefPoint(2)
    print(f"PositionorSetRefPoint 2 rtn is {rtn}")
    time.sleep(2)
    robot.MoveJ(joint_pos=jSafe,tool= 1,user= 0,vel= 100)
    robot.ExtAxisStartJog(1, 0, 50, 50, 10)
    time.sleep(1)
    robot.ExtAxisStartJog(2, 0, 50, 50, 10)
    time.sleep(1)
    error, desc3 = robot.GetForwardKin(j3)
    robot.MoveJ(joint_pos=j3,tool= 1,user= 0,vel= 100)
    rtn = robot.PositionorSetRefPoint(3)
    print(f"PositionorSetRefPoint 3 rtn is {rtn}")
    time.sleep(2)
    robot.MoveJ(joint_pos=jSafe,tool= 1,user= 0,vel= 100)
    robot.ExtAxisStartJog(1, 0, 50, 50, 10)
    time.sleep(1)
    robot.ExtAxisStartJog(2, 0, 50, 50, 10)
    time.sleep(1)
    error, desc4 = robot.GetForwardKin(j4)
    robot.MoveJ(joint_pos=j4,tool= 1,user= 0,vel= 100)
    rtn = robot.PositionorSetRefPoint(4)
    print(f"PositionorSetRefPoint 4 rtn is {rtn}")
    time.sleep(2)
    axisCoord = [0.0,0.0,0.0,0.0,0.0,0.0]
    error,axisCoord = robot.PositionorComputeECoordSys()
    robot.MoveJ(joint_pos=jSafe,tool= 1,user= 0,vel= 100)
    print(f"PositionorComputeECoordSys rtn is {axisCoord[0]} {axisCoord[1]} {axisCoord[2]} {axisCoord[3]} {axisCoord[4]} {axisCoord[5]}")
    rtn = robot.ExtAxisActiveECoordSys(3, 1, axisCoord, 1)
    print(f"ExtAxisActiveECoordSys rtn is {rtn}")
    robot.CloseRPC()
          
Ruch UDP osi rozszerzenia
++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ExtAxisMove(pos,ovl,blend=-1)``"
    "Opis", "Ruch UDP osi rozszerzenia"
    "Parametry wymagane", "- ``pos=[exaxis[0],exaxis[1],exaxis[2],exaxis[3]]``: Pozycja docelowa pozycja osi 1 ~ pozycja osi 4;
    - ``ovl``: Procent prędkości"
    "Parametry domyślne", "- ``blend``: Parametr wygładzania (mm lub ms), -1, oczekiwanie na zakończenie ruchu, domyślnie -1"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"
                                        
Przykład kodu ruchu UDP osi rozszerzenia
++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    axisPos = [20,0,0,0]
    robot.ExtAxisMove(axisPos, 50, -1)
    robot.CloseRPC()
    return 0

Ruch synchroniczny UDP osi rozszerzenia z ruchem przegubowym robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ExtAxisSyncMoveJ(joint_pos,tool,user,exaxis_pos, desc_pos=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0], vel=20.0, acc=0.0, ovl= 100.0,  blendT=-1.0, offset_flag=0, offset_pos=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0])``"
    "Opis", "Ruch synchroniczny UDP osi rozszerzenia z ruchem przegubowym robota"
    "Parametry wymagane", "
    - ``joint_pos``: Docelowa pozycja przegubów, jednostka [°];
    - ``desc_pos``: Docelowa poza kartezjańska, jednostka [mm][°]
    - ``tool``: Numer narzędzia, [0~14]
    - ``user``: Numer przedmiotu, [0~14]
    - ``exaxis_pos``: Pozycja osi zewnętrznej 1 ~ pozycja osi zewnętrznej 4"
    "Parametry domyślne", "
    - ``desc_pos``: Docelowa poza kartezjańska, jednostka [mm][°] domyślnie [0.0,0.0,0.0,0.0,0.0,0.0], wartość domyślna wywołuje wartość zwracaną z rozwiązania kinematyki prostej;
    - ``vel``: Procent prędkości, [0~100] domyślnie 20.0;
    - ``acc``: Procent przyspieszenia, [0~100] tymczasowo niedostępne, domyślnie 0.0;
    - ``ovl``: Współczynnik skalowania prędkości, [0~100] domyślnie 100.0;
    - ``blendT``: [-1.0]-ruch do pozycji (blokujący), [0~500.0]-czas wygładzania (nieblokujący), jednostka [ms] domyślnie -1.0;
    - ``offset_flag``: [0]-brak przesunięcia, [1]-przesunięcie w układzie przedmiotu/bazowym, [2]-przesunięcie w układzie narzędzia domyślnie 0;
    - ``offset_pos``: Wartość przesunięcia pozy, jednostka [mm][°] domyślnie [0.0,0.0,0.0,0.0,0.0,0.0];"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode;"
                                        
Przykład kodu ruchu synchronicznego UDP osi rozszerzenia z ruchem przegubowym robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    # Ustawienie parametrów komunikacji UDP i załadowanie
    robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10)
    robot.ExtDevLoadUDPDriver()
    # Ustawienie parametrów osi rozszerzenia
    robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0)
    robot.SetRobotPosToAxis(1)
    robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0)
    # Włączenie i powrót do zera osi rozszerzenia
    robot.ExtAxisServoOn(1, 0)
    robot.ExtAxisSetHoming(1, 0, 20, 3)
    # Kalibracja układu współrzędnych osi rozszerzenia
    pos = []  # Proszę wpisać współrzędne punktu kalibracyjnego
    robot.SetRefPointInExAxisEnd(pos)
    robot.PositionorSetRefPoint(1)  # Tę operację należy powtórzyć 4 razy (używając 4 punktów)
    error,coord = robot.PositionorComputeECoordSys()
    robot.ExtAxisActiveECoordSys(1, 1, coord, 1)
    # Punkt początkowy i końcowy ruchu synchronicznego
    startdescPose = []  # Proszę wpisać konkretne współrzędne
    startjointPos = []  # Proszę wpisać konkretne współrzędne
    startexaxisPos = []  # Proszę wpisać konkretne współrzędne
    enddescPose = []  # Proszę wpisać konkretne współrzędne
    endjointPos = []  # Proszę wpisać konkretne współrzędne
    endexaxisPos = []  # Proszę wpisać konkretne współrzędne
    # Ruch do punktu początkowego
    robot.ExtAxisMove(startexaxisPos, 20, -1)
    offdese = [0, 0, 0, 0, 0, 0]
    robot.MoveJ(joint_pos=startjointPos,tool= 1,user= 1,vel= 100,acc= 100,ovl= 100,exaxis_pos= startexaxisPos,blendT= 0,offset_flag= 0,offset_pos= offdese)
    robot.ExtAxisSyncMoveJ(endjointPos, enddescPose, 1, 1, endexaxisPos, 100, 100, 100, -1, 0, offdese)
    robot.CloseRPC()
                  
Ruch synchroniczny UDP osi rozszerzenia z ruchem liniowym robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ExtAxisSyncMoveL(desc_pos, tool, user, exaxis_pos, joint_pos=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0], vel=20.0, acc=0.0, ovl=100.0, blendR=-1.0, search=0, offset_flag=0, offset_pos=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0],config=-1)``"
    "Opis", "Ruch synchroniczny UDP osi rozszerzenia z ruchem liniowym robota"
    "Parametry wymagane", "
    - ``desc_pos``: Docelowa poza kartezjańska, jednostka [mm][°];
    - ``tool``: Numer narzędzia, [0~14];
    - ``user``: Numer przedmiotu, [0~14];
    - ``exaxis_pos``: Pozycja osi zewnętrznej 1 ~ pozycja osi zewnętrznej 4;"
    "Parametry domyślne", "
    - ``joint_pos``: Docelowa pozycja przegubów, jednostka [°] domyślnie [0.0,0.0,0.0,0.0,0.0,0.0], wartość domyślna wywołuje wartość zwracaną z rozwiązania kinematyki odwrotnej;
    - ``vel``: Procent prędkości, [0~100] domyślnie 20.0;
    - ``acc``: Procent przyspieszenia, [0~100] tymczasowo niedostępne, domyślnie 0.0;
    - ``ovl``: Współczynnik skalowania prędkości, [0~100] domyślnie 100.0;
    - ``blendR``: [-1.0]-ruch do pozycji (blokujący), [0~500.0]-czas wygładzania (nieblokujący), jednostka [ms] domyślnie -1.0;
    - ``search``: [0]-brak poszukiwania pozycji drutu, [1]-poszukiwanie pozycji drutu;
    - ``offset_flag``: [0]-brak przesunięcia, [1]-przesunięcie w układzie przedmiotu/bazowym, [2]-przesunięcie w układzie narzędzia domyślnie 0;
    - ``offset_pos``: Wartość przesunięcia pozy, jednostka [mm][°] domyślnie [0.0,0.0,0.0,0.0,0.0,0.0];
    - ``config``: Konfiguracja przestrzeni przegubów dla kinematyki odwrotnej, [-1]-obliczenia względem bieżącej pozycji przegubów, [0~7]-obliczenia według określonej konfiguracji przestrzeni przegubów, domyślnie -1"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode;"
                                            
Przykład kodu ruchu synchronicznego UDP osi rozszerzenia z ruchem liniowym robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    # Ustawienie parametrów komunikacji UDP i załadowanie
    robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10)
    robot.ExtDevLoadUDPDriver()
    # Ustawienie parametrów osi rozszerzenia
    robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0)
    robot.SetRobotPosToAxis(1)
    robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0)
    # Włączenie i powrót do zera osi rozszerzenia
    robot.ExtAxisServoOn(1, 0)
    robot.ExtAxisSetHoming(1, 0, 20, 3)
    # Kalibracja układu współrzędnych osi rozszerzenia
    pos = []  # Proszę wpisać współrzędne punktu kalibracyjnego
    robot.SetRefPointInExAxisEnd(pos)
    robot.PositionorSetRefPoint(1)  # Należy wywołać 4 razy w celu kalibracji
    error,coord = robot.PositionorComputeECoordSys()
    robot.ExtAxisActiveECoordSys(1, 1, coord, 1)
    # Punkt początkowy i końcowy ruchu synchronicznego
    startdescPose = []  # Proszę wpisać współrzędne
    startjointPos = []  # Proszę wpisać współrzędne
    startexaxisPos = []  # Proszę wpisać współrzędne
    enddescPose = []  # Proszę wpisać współrzędne
    endjointPos = []  # Proszę wpisać współrzędne
    endexaxisPos = []  # Proszę wpisać współrzędne
    # Ruch do punktu początkowego
    robot.ExtAxisMove(startexaxisPos, 20, -1)
    offdese = [0, 0, 0, 0, 0, 0]
    robot.MoveJ(joint_pos=startjointPos, tool= 1,user= 1,vel= 100,acc= 100,ovl= 100,exaxis_pos= startexaxisPos,blendT= 0)
    # Wykonanie synchronicznego ruchu liniowego
    robot.ExtAxisSyncMoveL(endjointPos, enddescPose, 1, 1, endexaxisPos, 100, 100, 100, 0, 0, offdese)
    robot.CloseRPC()
                      
Ruch synchroniczny UDP osi rozszerzenia z ruchem po łuku robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ExtAxisSyncMoveC(desc_pos_p, tool_p, user_p,exaxis_pos_p, desc_pos_t, tool_t, user_t,exaxis_pos_t,joint_pos_p=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0], joint_pos_t=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0],vel_p=20.0, acc_p=100.0, offset_flag_p=0, offset_pos_p =[0.0, 0.0, 0.0, 0.0, 0.0, 0.0], vel_t=20.0, acc_t=100.0, offset_flag_t=0, offset_pos_t=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0], ovl=100.0, blendR=-1.0, config=-1)``"
    "Opis", "Ruch synchroniczny UDP osi rozszerzenia z ruchem po łuku robota"
    "Parametry wymagane", "
    - ``desc_pos_p``: Pozycja kartezjańska punktu pośredniego, jednostka [mm][°];
    - ``tool_p``: Numer narzędzia punktu pośredniego, [0~14];
    - ``user_p``: Numer przedmiotu punktu pośredniego, [0~14];
    - ``exaxis_pos_p``: Pozycja osi zewnętrznej 1 ~ pozycja osi zewnętrznej 4 punktu pośredniego domyślnie [0.0,0.0,0.0,0.0];
    - ``desc_pos_t``: Docelowa poza kartezjańska punktu docelowego, jednostka [mm][°];
    - ``tool_t``: Numer narzędzia, [0~14];
    - ``user_t``: Numer przedmiotu, [0~14];
    - ``exaxis_pos_t``: Pozycja osi zewnętrznej 1 ~ pozycja osi zewnętrznej 4 punktu docelowego domyślnie [0.0,0.0,0.0,0.0];"
    "Parametry domyślne", "
    - ``joint_pos_p``: Docelowa pozycja przegubów, jednostka [°] domyślnie [0.0,0.0,0.0,0.0,0.0,0.0], wartość domyślna wywołuje wartość zwracaną z rozwiązania kinematyki odwrotnej;
    - ``joint_pos_t``: Docelowa pozycja przegubów, jednostka [°] domyślnie [0.0,0.0,0.0,0.0,0.0,0.0], wartość domyślna wywołuje wartość zwracaną z rozwiązania kinematyki odwrotnej;
    - ``vel_p``: Procent prędkości punktu pośredniego, [0~100] domyślnie 20.0;
    - ``acc_p``: Procent przyspieszenia punktu pośredniego, [0~100] tymczasowo niedostępne, domyślnie 0.0;   
    - ``offset_flag_p``: Czy przesunięcie punktu pośredniego [0]-brak przesunięcia, [1]-przesunięcie w układzie przedmiotu/bazowym, [2]-przesunięcie w układzie narzędzia domyślnie 0;
    - ``offset_pos_p``: Wartość przesunięcia pozy punktu pośredniego, jednostka [mm][°] domyślnie [0.0,0.0,0.0,0.0,0.0,0.0];
    - ``vel_t``: Procent prędkości punktu docelowego, [0~100] domyślnie 20.0;
    - ``acc_t``: Procent przyspieszenia punktu docelowego, [0~100] tymczasowo niedostępne domyślnie 0.0;
    - ``offset_flag_t``: Czy przesunięcie punktu docelowego [0]-brak przesunięcia, [1]-przesunięcie w układzie przedmiotu/bazowym, [2]-przesunięcie w układzie narzędzia domyślnie 0;
    - ``offset_pos_t``: Wartość przesunięcia pozy punktu docelowego, jednostka [mm][°] domyślnie [0.0,0.0,0.0,0.0,0.0,0.0];
    - ``ovl``: Współczynnik skalowania prędkości, [0~100] domyślnie 100.0;
    - ``blendR``: [-1.0]-ruch do pozycji (blokujący), [0~1000]-promień wygładzania (nieblokujący), jednostka [mm] domyślnie -1.0;
    - ``config``: Konfiguracja przestrzeni przegubów dla kinematyki odwrotnej, [-1]-obliczenia względem bieżącej pozycji przegubów, [0~7]-obliczenia według określonej konfiguracji przestrzeni przegubów, domyślnie -1"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode;"
                                                
Przykład kodu ruchu synchronicznego UDP osi rozszerzenia z ruchem po łuku robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    # Ustawienie parametrów komunikacji UDP i załadowanie
    robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10)
    robot.ExtDevLoadUDPDriver()
    # Ustawienie parametrów osi rozszerzenia
    robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0)
    robot.SetRobotPosToAxis(1)
    robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0)
    # Włączenie i powrót do zera osi rozszerzenia
    robot.ExtAxisServoOn(1, 0)
    robot.ExtAxisSetHoming(1, 0, 20, 3)
    # Kalibracja układu współrzędnych osi rozszerzenia
    pos = []  # Wprowadź współrzędne punktu kalibracyjnego
    robot.SetRefPointInExAxisEnd(pos)
    robot.PositionorSetRefPoint(1)  # Wywołaj 4 razy w celu wykonania kalibracji
    coord = []
    error,coord = robot.PositionorComputeECoordSys()
    robot.ExtAxisActiveECoordSys(1, 1, coord, 1)
    # Punkt początkowy, pośredni i końcowy łuku synchronicznego
    startdescPose = []# Wprowadź współrzędne
    startjointPos = []# Wprowadź współrzędne
    startexaxisPos =[]  # Wprowadź współrzędne osi rozszerzenia
    middescPose = []# Wprowadź punkt pośredni
    midjointPos = []
    midexaxisPos =[]
    enddescPose = []
    endjointPos = []
    endexaxisPos =[]
    # Ruch do punktu początkowego
    robot.ExtAxisMove(startexaxisPos, 20, -1)
    offdese = [0, 0, 0, 0, 0, 0]
    robot.MoveJ(joint_pos=startjointPos,tool= 1,user= 1,vel= 100,acc= 100,ovl= 100,exaxis_pos= startexaxisPos,blendT= 0,offset_flag= 0,offset_pos= offdese)
    # Rozpoczęcie synchronicznego ruchu po łuku
    robot.ExtAxisSyncMoveC(midjointPos,middescPose,1,1,midexaxisPos,
                           endjointPos,enddescPose,1,1,endexaxisPos,
                           100,100,0,offdese,
                           100,100,0,offdese,
                           100,0)
    robot.CloseRPC()

Ustawianie rozszerzonego DO
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetAuxDO(DONum,bOpen,smooth,block)``"
    "Opis", "Ustawianie rozszerzonego DO"
    "Parametry wymagane", "
    - ``DONum``: Numer DO;
    - ``bOpen``: Przełącznik True-wł., False-wył.;
    - ``smooth``: Czy wygładzać True - tak, False - nie;
    - ``block``: Czy blokować True - tak, False - nie;"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie rozszerzonego AO
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetAuxAO(AONum,value,block)``"
    "Opis", "Ustawianie rozszerzonego AO"
    "Parametry wymagane", "
    - ``AONum``: Numer AO;
    - ``value``: Wartość analogowa [0-4095];
    - ``block``: Czy blokować True - tak, False - nie;"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"
        
Ustawianie czasu filtracji wejścia rozszerzonego DI
++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetAuxDIFilterTime(filterTime)``"
    "Opis", "Ustawianie czasu filtracji wejścia rozszerzonego DI"
    "Parametry wymagane", "- ``filterTime``: Czas filtracji (ms);"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"
        
Ustawianie czasu filtracji wejścia rozszerzonego AI
++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetAuxAIFilterTime(AINum,filterTime)``"
    "Opis", "Ustawianie czasu filtracji wejścia rozszerzonego AI"
    "Parametry wymagane", "
    - ``AINum``: Numer AI;
    - ``filterTime``: Czas filtracji (ms);"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"
        
Oczekiwanie na wejście rozszerzonego DI
++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WaitAuxDI(DINum,bOpen,time,errorAlarm)``"
    "Opis", "Oczekiwanie na wejście rozszerzonego DI"
    "Parametry wymagane", "
    - ``DINum``: Numer DI;
    - ``bOpen``: Przełącznik True-wł., False-wył.;
    - ``time``: Maksymalny czas oczekiwania (ms);
    - ``errorAlarm``: Czy kontynuować ruch True-tak, False-nie"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"
        
Oczekiwanie na wejście rozszerzonego AI
++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WaitAuxAI(,AINum,sign,value,time,errorAlarm)``"
    "Opis", "Oczekiwanie na wejście rozszerzonego AI"
    "Parametry wymagane", "
    - ``AINum``: Numer AI;
    - ``sign``: 0-większe niż; 1-mniejsze niż;
    - ``value``: Wartość AI;
    - ``time``: Maksymalny czas oczekiwania (ms);
    - ``errorAlarm``: Czy kontynuować ruch True-tak, False-nie"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"
        
Pobieranie wartości rozszerzonego DI
++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetAuxDI(DINum,isNoBlock)``"
    "Opis", "Pobieranie wartości rozszerzonego DI"
    "Parametry wymagane", "
    - ``DINum``: Numer DI;
    - ``isNoBlock``: Czy blokować True-blokujący false-nieblokujący;"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode;
    - ``isOpen``: 0-wył.; 1-wł.;"
          
Pobieranie wartości rozszerzonego AI
++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetAuxAI(AINum,isNoBlock)``"
    "Opis", "Pobieranie wartości rozszerzonego AI"
    "Parametry wymagane", "
    - ``AINum``: Numer AI;
    - ``isNoBlock``: Czy blokować True-blokujący False-nieblokujący"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode;
    - ``value``: Wartość wejściowa;"

Przykład kodu rozszerzonego IO
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    for i in range(128):
        robot.SetAuxDO(i, True, False, True)
        time.sleep(0.1)
    for i in range(128):
        robot.SetAuxDO(i, False, False, True)
        time.sleep(0.1)
    for i in range(409):
        value1 = i * 10
        value2 = 4095 - i * 10
        robot.SetAuxAO(0, value1, True)
        robot.SetAuxAO(1, value2, True)
        robot.SetAuxAO(2, value1, True)
        robot.SetAuxAO(3, value2, True)
        time.sleep(0.01)
    robot.SetAuxDIFilterTime(10)
    robot.SetAuxAIFilterTime(0, 10)
    for i in range(20):
        curValue = False
        error, curValue = robot.GetAuxDI(i, False)  # Uwaga: w zależności od implementacji biblioteki, może wymagać modyfikacji
        print(f"DI{i}   {curValue}")
    curValue = -1
    for i in range(4):
        error, curValue = robot.GetAuxAI(i, True)  # Podobnie uwaga na przekazywanie przez referencję
        print(f"AI{i}   {curValue}")
    robot.WaitAuxDI(1, False, 1000, False)
    robot.WaitAuxAI(1, 1, 132, 1000, False)
    robot.CloseRPC()

Włączanie urządzenia ruchomego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``TractorEnable(enable)``"
    "Opis", "Włączanie urządzenia ruchomego"
    "Parametry wymagane", "- ``enable``: Stan włączenia, 0-wyłącz, 1-włącz"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Powrót do zera urządzenia ruchomego
+++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``TractorHoming()``"
    "Opis", "Powrót do zera urządzenia ruchomego"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ruch liniowy urządzenia ruchomego
+++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``TractorMoveL(distance, vel)``"
    "Opis", "Ruch liniowy urządzenia ruchomego"
    "Parametry wymagane", "- ``distance``: Odległość ruchu liniowego (mm)
    - ``vel``: Procent prędkości ruchu liniowego (0-100)"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ruch po łuku urządzenia ruchomego
+++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``TractorMoveC(radio, angle, vel)``"
    "Opis", "Ruch po łuku urządzenia ruchomego"
    "Parametry wymagane", "- ``radio``: Promień ruchu po łuku (mm)
    - ``angle``: Kąt ruchu po łuku (°)
    - ``vel``: Procent prędkości ruchu po łuku (0-100)"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Zatrzymanie ruchu urządzenia ruchomego
++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ProgramStop()``"
    "Opis", "Zatrzymanie ruchu urządzenia ruchomego"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Przykład kodu urządzenia ruchomego
++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    robot.ExtDevSetUDPComParam("192.168.58.2", 2021, 2, 50, 5, 50, 1, 50, 10, 1)
    robot.ExtDevLoadUDPDriver()
    rtn = robot.ExtAxisServoOn(1, 1)
    rtn = robot.ExtAxisServoOn(2, 1)
    time.sleep(2)
    robot.ExtAxisSetHoming(1, 0, 10, 2)
    time.sleep(2)
    rtn = robot.ExtAxisSetHoming(2, 0, 10, 2)
    time.sleep(4)
    robot.ExtAxisParamConfig(1, 0, 0, 50000, -50000, 1000, 1000, 6.280, 16384, 200, 0, 0, 0)
    robot.ExtAxisParamConfig(2, 0, 0, 50000, -50000, 1000, 1000, 6.280, 16384, 200, 0, 0, 0)
    robot.SetAxisDHParaConfig(5, 0, 0, 0, 0, 0, 0, 0, 0)
    robot.TractorEnable(False)
    time.sleep(2)
    robot.TractorEnable(True)
    time.sleep(2)
    robot.TractorHoming()
    time.sleep(2)
    robot.TractorMoveL(100, 2)
    time.sleep(5)
    robot.TractorStop()
    robot.TractorMoveL(-100, 20)
    time.sleep(5)
    robot.TractorMoveC(300, 90, 20)
    time.sleep(10)
    robot.TractorMoveC(300, -90, 20)
    time.sleep(1)
    robot.CloseRPC()

Punkt rejestracji czujnika laserowego
+++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LaserRecordPoint(coordID)``"
    "Opis", "Punkt rejestracji czujnika laserowego"
    "Parametry wymagane", "- ``coordID``: Układ współrzędnych czujnika laserowego"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``joint``: Pozycja przegubów punktu rozpoznanego przez czujnik laserowy
    - ``desc``: Pozycja kartezjańska punktu rozpoznanego przez czujnik laserowy
    - ``exaxis``: Pozycja osi rozszerzenia punktu rozpoznanego przez czujnik laserowy"

Przykład kodu punktu rejestracji czujnika laserowego
++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.4

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    direction_point = [0, 0, 0]
    rtn = robot.LaserTrackingSearchStart(2, direction_point, 10, 100, 10000, 2)
    print(f"LaserTrackingSearchStart rtn is {rtn}")
    robot.LaserTrackingSearchStop()
    coord_id = 2
    rtn, joint, desc, exaxis = robot.LaserRecordPoint(coord_id)
    print(f"rtn is {rtn}")
    print(f"desc_pos:{desc[0]},{desc[1]},{desc[2]},"
          f"{desc[3]},{desc[4]},{desc[5]}")
    print(f"joint_pos:{joint[0]},{joint[1]},{joint[2]},{joint[3]},{joint[4]},{joint[5]}")
    print(f"exaxis pos is {exaxis[0]} {exaxis[1]} {exaxis[2]} {exaxis[3]}")
    off = [0] * 6
    robot.MoveJ(joint,tool=1,user=0,vel=100,acc=100,ovl=50,exaxis_pos=exaxis,blendT=-1,offset_flag=0,offset_pos=off)
    robot.CloseRPC()

Ustawianie strategii ruchu synchronicznego osi rozszerzenia z robotem
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetExAxisRobotPlan(strategy)``"
    "Opis", "Ustawianie strategii ruchu synchronicznego osi rozszerzenia z robotem"
    "Parametry wymagane", "- ``strategy``: Strategia; 0-z robotem jako głównym; 1-oś rozszerzenia synchroniczna z robotem"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Przykład kodu ustawiania strategii ruchu synchronicznego osi rozszerzenia z robotem
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.5

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    joint_pos1 = [-22.016, -49.217, 124.714, -161.100, -85.108, -0.333]
    joint_pos2 = [-21.083, -46.613, 110.079, -147.796, -80.757, -0.330]
    joint_pos3 = [-25.572, -60.090, 135.397, -163.889, -82.489, -0.345]
    desc_pos1 = [2.637, -0.001, 30.673, 178.786, -4.134, 68.326]
    desc_pos2 = [213.812, -1.440, 47.311, 177.410, 0.166, 68.946]
    desc_pos3 = [444.342, -12.723, 82.470, -177.701, -1.325, 65.151]
    epos1 = [0.001, 0.000, 0.000, 0.000]
    epos2 = [299.977, 0.000, 0.000, 0.000]
    epos3 = [399.969, 0.000, 0.000, 0.000]
    offset_pos = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    rtn = robot.SetExAxisRobotPlan(0)
    print(f"SetExAxisRobotPlan rtn is {rtn}")
    time.sleep(1)
    rtn = robot.ExtAxisSyncMoveL(desc_pos=desc_pos1,tool=1,user=0,vel=100,acc=100,ovl=100,blendR=-1,exaxis_pos=epos1,offset_flag=0,offset_pos=offset_pos)
    print(f"ExtAxisSyncMoveL 1 rtn is {rtn}")
    rtn = robot.ExtAxisSyncMoveL(desc_pos=desc_pos2,tool=1,user=0,vel=100,acc=100,ovl=100,blendR=-1,exaxis_pos=epos2,offset_flag=0,offset_pos=offset_pos)
    print(f"ExtAxisSyncMoveL 2 rtn is {rtn}")
    rtn = robot.ExtAxisSyncMoveL(desc_pos=desc_pos3,tool=1,user=0,vel=100,acc=100,ovl=100,blendR=-1,exaxis_pos=epos3,offset_flag=0,offset_pos=offset_pos)
    print(f"ExtAxisSyncMoveL 3 rtn is {rtn}")
    time.sleep(8)
    robot.CloseRPC()

Ustawianie czasu zakończenia pozycjonowania UDP osi rozszerzenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetExAxisCmdDoneTime(time)``"
    "Opis", "Ustawianie czasu zakończenia pozycjonowania UDP osi rozszerzenia"
    "Parametry wymagane", "- ``time``: Czas zakończenia pozycjonowania [ms]"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"