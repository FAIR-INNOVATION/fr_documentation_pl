Podstawy robota
===============

.. toctree:: 
    :maxdepth: 5

Tworzenie instancji robota
++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``RPC(ip)``"
    "Opis", "Tworzy instancję obiektu robota"
    "Parametry wymagane", "- ``ip``: Adres IP robota, domyślny adres fabryczny to „192.168.58.2”"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Sukces: Zwraca obiekt robota
    - Błąd: Utworzony obiekt zostanie zniszczony"

Zamykanie połączenia RPC
++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``CloseRPC()``"
    "Opis", "Zamyka połączenie RPC"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Brak"

Sprawdzanie numeru wersji SDK
+++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetSDKVersion()``"
    "Opis", "Sprawdza numer wersji SDK"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd-errcode
    - ``sdk``: Numer wersji SDK, numer wersji kontrolera"

Pobieranie IP kontrolera
++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetControllerIP()``"
    "Opis", "Sprawdza IP kontrolera"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``ip``: IP kontrolera"

Sterowanie wejściem lub wyjściem robota z trybu przeciągania i uczenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``DragTeachSwitch(state)``"
    "Opis", "Sterowanie wejściem lub wyjściem robota z trybu przeciągania i uczenia"
    "Parametry wymagane", "- ``state``: 1- Wejście w tryb przeciągania i uczenia, 0- Wyjście z trybu przeciągania i uczenia"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Sprawdzanie, czy robot jest w trybie przeciągania
+++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``IsInDragTeach()``"
    "Opis", "Sprawdza, czy robot jest w trybie przeciągania i uczenia"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``state``: 0- Tryb przeciągania i uczenia nieaktywny, 1- Tryb przeciągania i uczenia aktywny"

Sterowanie włączeniem lub wyłączeniem zasilania robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``RobotEnable(state)``"
    "Opis", "Sterowanie włączeniem lub wyłączeniem zasilania robota"
    "Parametry wymagane", "- ``state``: 1- Włączenie zasilania, 0- Wyłączenie zasilania"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode "


Sterowanie przełączaniem trybu ręcznego/automatycznego robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``Mode(state)``"
    "Opis", "Sterowanie przełączaniem trybu ręcznego/automatycznego robota"
    "Parametry wymagane", "- ``state``: 0- Tryb automatyczny, 1- Tryb ręczny"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Zamykanie systemu operacyjnego robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ShutDownRobotOS()``"
    "Opis", "Zamykanie systemu operacyjnego robota"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Inicjalizacja parametrów logowania
+++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LoggerInit(output_model=1, file_path="", file_num=5)``"
    "Opis", "Inicjalizacja parametrów logowania"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "- ``output_model``: Tryb wyjścia, 0-wyjście bezpośrednie; 1-wyjście buforowane; 2-wyjście asynchroniczne, domyślnie 1
    - ``file_path``: Ścieżka zapisu pliku + nazwa, nazwa musi być w formacie xxx.log, np. /home/fr/linux/fairino.log. Domyślnie ścieżka lokalizacji programu wykonywalnego, domyślna nazwa to: fairino_year+month+data.log (np. fairino_2024_03_13.log);
    - ``file_num``: Liczba plików do przechowywania w rolce, od 1 do 20, wartość domyślna to 5. Maksymalny rozmiar pojedynczego pliku to 50 MB;"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie poziomu filtrowania logów
++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetLoggerLevel(lvl=1)``"
    "Opis", "Ustawianie poziomu filtrowania logów"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "- ``lvl``: Wartość poziomu filtrowania, im mniejsza wartość, tym mniej logów jest wypisywanych, 1-error, 2-warning, 3-inform, 4-debug, wartość domyślna to 1"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Przykład kodu podstawowego sterowania robotem
+++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 

    from fairino import Robot
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    error,version = robot.GetSDKVersion()
    print(f"SDK version: {version}")
    error,ip = robot.GetControllerIP()
    print(f"controller ip: {ip}")
    robot.Mode(1)
    time.sleep(1)
    robot.DragTeachSwitch(state=1)
    time.sleep(1)
    error,state = robot.IsInDragTeach()
    print(f"drag state: {state}")
    time.sleep(3)
    robot.DragTeachSwitch(state=0)
    time.sleep(1)
    error,state = robot.IsInDragTeach()
    print(f"drag state: {state}")
    time.sleep(3)
    robot.RobotEnable(0)
    time.sleep(3)
    robot.RobotEnable(1)
    robot.Mode(0)
    time.sleep(1)
    robot.Mode(1)
    robot.CloseRPC()

Pobieranie wersji oprogramowania robota
+++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetSoftwareVersion()``"
    "Opis", "Pobiera wersję oprogramowania robota"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``robotModel``: Model robota
    - ``webVersion``: Wersja web
    - ``controllerVersion``: Wersja kontrolera"

Pobieranie informacji o wersji sprzętowej robota
+++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetSlaveHardVersion()``"
    "Opis", "Pobiera informacje o wersji sprzętowej robota"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``ctrlBoxBoardVersion``: Wersja skrzynki kontrolnej
    - ``driver1Version``
    - ``driver2Version``
    - ``driver3Version``
    - ``driver4Version``
    - ``driver5Version``
    - ``driver6Version``
    - ``endBoardVersion``"

Pobieranie informacji o wersji firmware robota
+++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetSlaveFirmVersion()``"
    "Opis", "Pobiera informacje o wersji firmware robota"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``ctrlBoxBoardVersion``: Wersja skrzynki kontrolnej
    - ``driver1Version``
    - ``driver2Version``
    - ``driver3Version``
    - ``driver4Version``
    - ``driver5Version``
    - ``driver6Version``
    - ``endBoardVersion``"

Przykład kodu pobierania wersji oprogramowania i firmware robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    rtn,robotModel, webversion, controllerVersion = robot.GetSoftwareVersion()
    print(f"Getsoftwareversion rtn is: {rtn}")
    print(f"robotmodel is: {robotModel}, webversion is: {webversion}, controllerVersion is: {controllerVersion}\n")
    rtn,ctrlBoxBoardversion, driver1version, driver2version,driver3version, driver4version, driver5version,driver6version, endBoardversion = robot.GetHardwareversion()
    print(f"GetHardwareversion rtn is: {rtn}")
    print(f"GetHardwareversion get hardware version is: {ctrlBoxBoardversion}, {driver1version}, {driver2version}, "
          f"{driver3version}, {driver4version}, {driver5version}, {driver6version}, {endBoardversion}\n")
    rtn,ctrlBoxBoardversion, driver1version, driver2version,driver3version, driver4version, driver5version,driver6version, endBoardversion = robot.GetFirmwareVersion()
    print(f"GetFirmwareversion rtn is: {rtn}")
    print(f"GetFirmwareversion get firmware version is: {ctrlBoxBoardversion}, {driver1version}, {driver2version}, "
          f"{driver3version}, {driver4version}, {driver5version}, {driver6version}, {endBoardversion}\n")
    robot.CloseRPC()