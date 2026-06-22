Inne interfejsy
===============

.. toctree:: 
    :maxdepth: 5

Pobieranie klucza publicznego SSH
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetSSHKeygen()``"
    "Opis", "Pobieranie klucza publicznego SSH"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``keygen``: Klucz publiczny"

Wysyłanie polecenia SCP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetSSHScpCmd(mode, sshname, sship, usr_file_url, robot_file_url)``"
    "Opis", "Wysyłanie polecenia SCP"
    "Parametry wymagane", "- ``mode``: 0-upload (komputer nadrzędny -> kontroler), 1-pobranie (kontroler -> komputer nadrzędny)
    - ``sshname``: Nazwa użytkownika komputera nadrzędnego
    - ``sship``: Adres IP komputera nadrzędnego
    - ``usr_file_url``: Ścieżka do pliku na komputerze nadrzędnym
    - ``robot_file_url``: Ścieżka do pliku w kontrolerze robota"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Obliczanie wartości MD5 pliku w określonej ścieżce
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ComputeFileMD5(file_path)``"
    "Opis", "Obliczanie wartości MD5 pliku w określonej ścieżce"
    "Parametry wymagane", "- ``file_path``: Ścieżka do pliku wraz z nazwą. Domyślna ścieżka folderu Traj to:/fruser/traj/, np. /fruser/traj/trajHelix_aima_1.txt"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``md5``: Wartość MD5 pliku"

Przykład kodu dla poleceń SSH i MD5 robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    file_path = "/fruser/airlab.lua"
    md5 = ""
    emerg_state = 0
    si0_state = 0
    si1_state = 0
    sdk_com_state = 0
    ssh_keygen = ""
    retval,ssh_keygen = robot.GetSSHKeygen()
    print(f"GetSSHKeygen retval is: {retval}")
    print(f"ssh key is: {ssh_keygen}")
    ssh_name = "fr"
    ssh_ip = "192.168.58.45"
    ssh_route = "/home/fr"
    ssh_robot_url = "/root/robot/dhpara.config"
    retval = robot.SetSSHScpCmd(1, ssh_name, ssh_ip, ssh_route, ssh_robot_url)
    print(f"SetSSHScpCmd retval is: {retval}")
    print(f"robot url is: {ssh_robot_url}")
    error, md5 = robot.ComputeFileMD5(file_path)
    print(f"md5 is: {md5}")
    robot.CloseRPC()

Ustawianie okresu zwrotnego portu 20004 robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetRobotRealtimeStateSamplePeriod(period)``"
    "Opis", "Ustawianie okresu zwrotnego portu 20004 robota"
    "Parametry wymagane", "- ``period``: Okres zwrotny portu 20004 robota (ms)"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode "

Pobieranie okresu zwrotnego portu 20004 robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetRobotRealtimeStateSamplePeriod()``"
    "Opis", "Pobieranie okresu zwrotnego portu 20004 robota"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode 
    - ``period``: Okres zwrotny portu 20004 robota (ms)"

Przykład konfiguracji okresu zwrotnego stanu portu 20004 robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    robot.SetRobotRealtimeStateSamplePeriod(10)
    error,getPeriod = robot.GetRobotRealtimeStateSamplePeriod()
    print(f"period is {getPeriod}")
    time.sleep(1)
    robot.CloseRPC()

Aktualizacja oprogramowania robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SoftwareUpgrade(filePath, block)``"
    "Opis", "Aktualizacja oprogramowania robota"
    "Parametry wymagane", "- ``filePath``: Pełna ścieżka pakietu aktualizacyjnego oprogramowania
    - ``block``: Czy blokować do czasu zakończenia aktualizacji true: blokuj; false: nieblokujący"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode "

Pobieranie statusu aktualizacji oprogramowania robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetSoftwareUpgradeState()``"
    "Opis", "Pobieranie statusu aktualizacji oprogramowania robota"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode 
    - ``state``: Status aktualizacji pakietu oprogramowania robota, 0: bezczynność lub przesyłanie pakietu aktualizacyjnego, 1~100: procent ukończenia aktualizacji, -1: niepowodzenie aktualizacji oprogramowania, -2: niepowodzenie weryfikacji, -3: niepowodzenie weryfikacji wersji, -4: niepowodzenie dekompresji, -5: niepowodzenie aktualizacji konfiguracji użytkownika, -6: niepowodzenie aktualizacji konfiguracji urządzeń peryferyjnych, -7: niepowodzenie aktualizacji konfiguracji osi rozszerzenia, -8: niepowodzenie aktualizacji konfiguracji robota, -9: niepowodzenie aktualizacji konfiguracji parametrów DH"

Przykład kodu aktualizacji oprogramowania robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    error = robot.SoftwareUpgrade("D://zUP/QNX382/software.tar.gz", False)
    print(f"SoftwareUpgrade error is {error}")
    while True:
        curState = robot.GetSoftwareUpgradeState()
        print(f"upgrade state is {curState}")
        time.sleep(3)
    robot.CloseRPC()

Pobieranie bazy danych tabeli punktów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``PointTableDownLoad(point_table_name, save_file_path)``"
    "Opis", "Pobieranie bazy danych tabeli punktów"
    "Parametry wymagane", "- ``point_table_name``: Nazwa tabeli punktów do pobrania pointTable1.db;
    - ``save_file_path``: Ścieżka zapisu pobranej tabeli punktów C://test/;"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Przesyłanie bazy danych tabeli punktów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``PointTableUpLoad(point_table_file_path)``"
    "Opis", "Przesyłanie bazy danych tabeli punktów"
    "Parametry wymagane", "- ``point_table_file_path``: Pełna ścieżka przesyłanej tabeli punktów C://test/pointTable1.db"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Aktualizacja pliku Lua tabeli punktów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``PointTableUpdateLua(point_table_name, lua_file_name)``"
    "Opis", "Aktualizacja pliku Lua tabeli punktów"
    "Parametry wymagane", "- ``point_table_name``: Nazwa tabeli punktów do przełączenia pointTable1.db. Gdy tabela punktów jest pusta, tzn. "", oznacza to aktualizację programu Lua do programu początkowego bez zastosowanej tabeli punktów
    - ``lua_file_name``: Nazwa pliku Lua do aktualizacji testPointTable.lua"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Przykład operacji na tabeli punktów robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 

    from fairino import Robot
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    save_path = "D://zDOWN/"
    point_table_name = "point_table_FR5.db"
    rtn = robot.PointTableDownLoad(point_table_name, save_path)
    print(f"download : {point_table_name} fail: {rtn}")
    upload_path = "D://zDOWN/point_table_FR5.db"
    rtn = robot.PointTableUpLoad(upload_path)
    print(f"retval is: {rtn}")
    point_tablename = "point_table_FR5.db"
    lua_name = "test0610.lua"
    rtn,error = robot.PointTableUpdateLua(point_tablename, lua_name)
    print(f"retval is: {rtn}")
    robot.CloseRPC()

Pobieranie logów kontrolera
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``RbLogDownload(savePath)``"
    "Opis", "Pobieranie logów kontrolera"
    "Parametry wymagane", "- ``savePath``: Ścieżka zapisu pliku D://zDown/"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Pobieranie wszystkich źródeł danych
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AllDataSourceDownload(savePath)``"
    "Opis", "Pobieranie wszystkich źródeł danych"
    "Parametry wymagane", "- ``savePath``: Ścieżka zapisu pliku D://zDown/"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Pobieranie pakietu kopii zapasowej danych
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``DataPackageDownload(savePath)``"
    "Opis", "Pobieranie pakietu kopii zapasowej danych"
    "Parametry wymagane", "- ``savePath``: Ścieżka zapisu pliku D://zDown/"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Przykład kodu pobierania danych z kontrolera
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    rtn = robot.RbLogDownload("D://zDOWN/")
    print(f"RbLogDownload rtn is {rtn}")
    rtn = robot.AllDataSourceDownload("D://zDOWN/")
    print(f"AllDataSourceDownload rtn is {rtn}")
    rtn = robot.DataPackageDownload("D://zDOWN/")
    print(f"DataPackageDownload rtn is {rtn}")
    robot.CloseRPC()

Ustawianie aktualizacji enkodera
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetEncoderUpgrade(path)``"
    "Opis", "Ustawianie aktualizacji enkodera"
    "Parametry wymagane", "- ``path``: Pełna ścieżka lokalnego pakietu aktualizacyjnego (D://zUP/XXXXX.bin)"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"
    
Ustawianie aktualizacji firmware przegubów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetJointFirmwareUpgrade(type, path)``"
    "Opis", "Ustawianie aktualizacji firmware przegubów"
    "Parametry wymagane", "- ``type``: Typ pliku aktualizacyjnego; 1-aktualizacja firmware; 2-aktualizacja pliku konfiguracyjnego węzła podrzędnego
    - ``path``: Pełna ścieżka lokalnego pakietu aktualizacyjnego (D://zUP/XXXXX.bin)"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie aktualizacji firmware skrzynki kontrolnej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetCtrlFirmwareUpgrade(type, path)``"
    "Opis", "Ustawianie aktualizacji firmware skrzynki kontrolnej"
    "Parametry wymagane", "- ``type``: Typ pliku aktualizacyjnego; 1-aktualizacja firmware; 2-aktualizacja pliku konfiguracyjnego węzła podrzędnego
    - ``path``: Pełna ścieżka lokalnego pakietu aktualizacyjnego (D://zUP/XXXXX.bin)"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"
    
Ustawianie aktualizacji firmware końcówki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetEndFirmwareUpgrade(type, path)``"
    "Opis", "Ustawianie aktualizacji firmware końcówki"
    "Parametry wymagane", "- ``type``: Typ pliku aktualizacyjnego; 1-aktualizacja firmware; 2-aktualizacja pliku konfiguracyjnego węzła podrzędnego
    - ``path``: Pełna ścieżka lokalnego pakietu aktualizacyjnego (D://zUP/XXXXX.bin)"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"
       
Aktualizacja pliku konfiguracji pełnych parametrów przegubu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``JointAllParamUpgrade(path)``"
    "Opis", "Aktualizacja pliku konfiguracji pełnych parametrów przegubu"
    "Parametry wymagane", "- ``path``: Pełna ścieżka lokalnego pakietu aktualizacyjnego (D://zUP/XXXXX.bin)"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Przykład kodu aktualizacji firmware węzła podrzędnego robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    robot.RobotEnable(0)
    time.sleep(0.2)
    rtn = robot.JointAllParamUpgrade("D://zUP/MT/joint0603/jointallparameters.db")
    print(f"robot JointAllParamUpgrade rtn is {rtn}")
    rtn = robot.SetCtrlFirmwareUpgrade(2, "D://zUP/MT/FAIR_Cobot_Cbd_Asix_V2.0.bin")
    print(f"robot SetCtrlFirmwareUpgrade rtn is {rtn}")
    rtn = robot.SetEndFirmwareUpgrade(2, "D://zUP/MT/FAIR_Cobot_Axle_Asix_V2.4.bin")
    print(f"robot SetEndFirmwareUpgrade rtn is {rtn}")
    robot.SetSysServoBootMode()
    time.sleep(0.2)
    rtn = robot.SetCtrlFirmwareUpgrade(1, "D://zUP/MT/FR_CTRL_PRIMCU_FV201412_MAIN_U4_T01_20250630(MT).bin")
    print(f"robot SetCtrlFirmwareUpgrade rtn is {rtn}")
    rtn = robot.SetEndFirmwareUpgrade(1, "D://zUP/MT/FR_END_FV2010010_MAIN_U1_T01_20250603.bin")
    print(f"robot SetEndFirmwareUpgrade rtn is {rtn}")
    rtn = robot.SetJointFirmwareUpgrade(1, "D://zUP/MT/FR_SERVO_FV504215_MAIN_U7_T07_20250603.bin")
    print(f"robot SetJointFirmwareUpgrade rtn is {rtn}")
    robot.CloseRPC()
       
Aktualizacja systemu operacyjnego robota (skrzynka kontrolna LA)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``KernelUpgrade(filePath)``"
    "Opis", "Aktualizacja systemu operacyjnego robota (skrzynka kontrolna LA)"
    "Parametry wymagane", "- ``filePath``: Pełna ścieżka pakietu aktualizacyjnego systemu operacyjnego"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"
       
Pobieranie wyniku aktualizacji systemu operacyjnego robota (skrzynka kontrolna LA)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetKernelUpgradeResult()``"
    "Opis", "Pobieranie wyniku aktualizacji systemu operacyjnego robota (skrzynka kontrolna LA)"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"
       
Generowanie logów MCU robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``RobotMCULogCollect()``"
    "Opis", "Generowanie logów MCU robota"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"
           
Ustawianie zatrzymania robota po rozłączeniu komunikacji portu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetRobotStopOnComDisc(portID, enable, confirmTime)``"
    "Opis", "Ustawianie zatrzymania robota po rozłączeniu komunikacji portu"
    "Parametry wymagane", "
    - ``portID``: Numer portu 0-8080; 1-8083; 2-20002; 3-20004
    - ``enable``: 0-wyłączone; 1-włączone
    - ``confirmTime``: Czas potwierdzenia przerwania komunikacji (ms)[0-5000]"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"
           
Pobieranie parametrów zatrzymania robota po rozłączeniu komunikacji portu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetRobotStopOnComDisc(portID)``"
    "Opis", "Pobieranie parametrów zatrzymania robota po rozłączeniu komunikacji portu"
    "Parametry wymagane", "
    - ``portID``: Numer portu 0-8080; 1-8083; 2-20002; 3-20004
    - ``enable``: 0-wyłączone; 1-włączone
    - ``confirmTime``: Czas potwierdzenia przerwania komunikacji (ms)[0-5000]"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Przykład kodu parametrów zatrzymania robota po rozłączeniu komunikacji portu
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from time import sleep
    import time
    from fairino import Robot
    # Połączenie z kontrolerem robota
    robot = Robot.RPC('192.168.58.2')

    def test_robot_stop_on_com_disc(self):
        # Inicjalizacja parametrów
        enable = False
        confirm_time = 0

        # Ustawienie funkcji zatrzymania robota po rozłączeniu komunikacji
        rtn = robot.SetRobotStopOnComDisc(0, True, 330)
        print(f"SetRobotStopOnComDisc index0: {rtn}")

        rtn = robot.SetRobotStopOnComDisc(1, True, 550)
        print(f"SetRobotStopOnComDisc index1: {rtn}")

        rtn = robot.SetRobotStopOnComDisc(2, True, 110)
        print(f"SetRobotStopOnComDisc index2: {rtn}")

        rtn = robot.SetRobotStopOnComDisc(3, True, 220)
        print(f"SetRobotStopOnComDisc index3: {rtn}")

        # Pobranie ustawień zatrzymania robota po rozłączeniu komunikacji
        rtn, enable, confirm_time = robot.GetRobotStopOnComDisc(0)
        print(f"GetRobotStopOnComDisc 8080 rtn {rtn}; enable is {enable}; confirm time is {confirm_time}")

        rtn, enable, confirm_time = robot.GetRobotStopOnComDisc(1)
        print(f"GetRobotStopOnComDisc 80803 rtn {rtn}; enable is {enable}; confirm time is {confirm_time}")

        rtn, enable, confirm_time = robot.GetRobotStopOnComDisc(2)
        print(f"GetRobotStopOnComDisc 20002 rtn {rtn}; enable is {enable}; confirm time is {confirm_time}")

        rtn, enable, confirm_time = robot.GetRobotStopOnComDisc(3)
        print(f"GetRobotStopOnComDisc 20004 rtn {rtn}; enable is {enable}; confirm time is {confirm_time}")

        # Zamknięcie połączenia RPC
        robot.CloseRPC()
        return 0

    test_robot_stop_on_com_disc(robot)

Wysyłanie ramki polecenia UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SendUDPFrame(frame)``"
    "Opis", "Wysyłanie ramki polecenia UDP"
    "Parametry wymagane", "
    - ``frame``: Wysyłane dane UDP, transmisja przezroczysta, bez enkapsulacji"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Przykład kodu SDK dla komunikacji UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from time import sleep
    import time
    from fairino import Robot

    # Połączenie z kontrolerem robota
    robot = Robot.RPC('192.168.58.2')

    def TestSendUDPFrame(self):
        # Ustawienie wywołania zwrotnego
        def callback(src_type, count, cmd_id, data_len, content):
            print("Otrzymano odpowiedź: cmd_id={} count={} data_len={} content={}".format(cmd_id, count, data_len, content))
            return 0
        robot.SetUDPCmdRpyCallback(callback)

        rtn = robot.SendUDPFrame("/f/bIII20III303III7IIIMode(0)III/b/f")
        print(f"SendUDPFrame Mode(0) rtn is {rtn}")
        time.sleep(1)

        rtn = robot.SendUDPFrame("/f/bIII21III303III7IIIMode(1)III/b/f")
        print(f"SendUDPFrame Mode(1) rtn is {rtn}")
        time.sleep(1)

        rtn = robot.SendUDPFrame(
            "/f/bIII49III201III184IIIMoveJ(-15.625, -82.680, 101.654, -110.950, -88.290, 0.017, -383.012, -2.325, 242.655, -178.024, 1.710, 74.416, 0, 0, 100, 100, 100, 0.000, 0.000, 0.000, 0.000, -1, 0, 0, 0, 0, 0, 0, 0)III/b/f")
        print(f"SendUDPFrame MoveJ(-15.625) rtn is {rtn}")
        time.sleep(1)

        rtn = robot.SendUDPFrame(
            "/f/bIII48III203III199IIIMoveL(-75.622, -82.680, 101.654, -110.950, -88.290, 0.017, -193.537, 330.525, 242.657, -178.024, 1.710, 14.420, 0, 0, 100, 100, 100, -1, 0, 0.000, 0.000, 0.000, 0.000, 0, 0, 0, 0, 0, 0, 0, 0, 100, 0)III/b/f")
        print(f"SendUDPFrame MoveL(-75.622) rtn is {rtn}")
        time.sleep(1)

        rtn = robot.SendUDPFrame("/f/bIII4III905III20IIIGetSoftwareVersion()III/b/f")
        print(f"SendUDPFrame GetSoftwareVersion() rtn is {rtn}")

        time.sleep(1)

        # Test weryfikacji danych wysyłanej ramki UDP
        rtn = robot.SendUDPFrame("/f/bIII20III303III7IIIMode(0)III/b/f")
        print(f"SendUDPFrame rtn is {rtn}")

        rtn = robot.SendUDPFrame("III20III303III7IIIMode(0)III/b/f")
        print(f"SendUDPFrame rtn is {rtn}")

        rtn = robot.SendUDPFrame("/f/bIII20III303III7IIIMode(0)")
        print(f"SendUDPFrame rtn is {rtn}")

        rtn = robot.SendUDPFrame("/f/bIII20III303III6IIIMode(0)III/b/f")
        print(f"SendUDPFrame rtn is {rtn}")

        rtn = robot.SendUDPFrame("/f/b|||20|||303|||7|||Mode(0)|||/b/f")
        print(f"SendUDPFrame rtn is {rtn}")

        rtn = robot.SendUDPFrame("/f/bII20II303II7IIMode(0)II/b/f")
        print(f"SendUDPFrame rtn is {rtn}")

        robot.CloseRPC()
        time.sleep(1)

    TestSendUDPFrame(robot)
    
Ustawianie niestandardowego koloru lampki końcówki robota przez użytkownika
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetUserLEDColor(r, g, b)``"
    "Opis", "Ustawianie niestandardowego koloru lampki końcówki robota przez użytkownika"
    "Parametry wymagane", "
    - ``r``: Sterowanie czerwoną lampką końcówki; 0-wyłącz; 1-włącz
    - ``g``: Sterowanie zieloną lampką końcówki; 0-wyłącz; 1-włącz
    - ``b``: Sterowanie niebieską lampką końcówki; 0-wyłącz; 1-włącz
    - "
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Przykład kodu SDK ustawiania niestandardowego koloru lampki końcówki robota przez użytkownika
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from time import sleep
    import time
    from fairino import Robot

    # Połączenie z kontrolerem robota
    robot = Robot.RPC('192.168.58.2')


    def testled(self):
        # Ustawienie koloru lampki LED przez użytkownika
        # Kolejność parametrów: R, G, B (czerwony, zielony, niebieski)

        # Biały (czerwony, zielony, niebieski - wszystkie włączone)
        robot.SetUserLEDColor(True, True, True)
        time.sleep(1)

        # Wyłączenie wszystkich lampek
        robot.SetUserLEDColor(False, False, False)
        time.sleep(1)

        # Czerwony (tylko czerwona lampka włączona)
        robot.SetUserLEDColor(True, False, False)
        time.sleep(1)

        # Zielony (tylko zielona lampka włączona)
        robot.SetUserLEDColor(False, True, False)
        time.sleep(1)

        # Niebieski (tylko niebieska lampka włączona)
        robot.SetUserLEDColor(False, False, True)

        # Zamknięcie połączenia
        robot.CloseRPC()

    testled(robot)