Użytkowanie programu WebAPP robota
==================================

.. toctree:: 
    :maxdepth: 5

Ustawianie automatycznego ładowania domyślnego programu roboczego przy starcie
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LoadDefaultProgConfig(flag,program_name)``"
    "Opis", "Ustawianie automatycznego ładowania domyślnego programu roboczego przy starcie"
    "Parametry wymagane", "
    - ``flag``: 1-ładuj automatycznie domyślny program przy starcie, 0-nie ładuj automatycznie domyślnego programu
    - ``program_name``: Nazwa i ścieżka programu roboczego, np. movej.lua"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ładowanie określonego programu roboczego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ProgramLoad(program_name)``"
    "Opis", "Ładowanie określonego programu roboczego"
    "Parametry wymagane", "- ``program_name``: Nazwa i ścieżka programu roboczego, np. movej.lua"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Pobieranie nazwy załadowanego programu roboczego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetLoadedProgram()``"
    "Opis", "Pobieranie nazwy załadowanego programu roboczego"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``program_name``: Nazwa załadowanego programu roboczego"

Pobieranie bieżącego numeru linii wykonania programu roboczego robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetCurrentLine()``"
    "Opis", "Pobieranie bieżącego numeru linii wykonania programu roboczego robota"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``line_num``: Bieżący numer linii wykonania programu roboczego robota"

Uruchamianie bieżącego załadowanego programu roboczego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ProgramRun()``"
    "Opis", "Uruchamianie bieżącego załadowanego programu roboczego"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Wstrzymywanie bieżącego uruchomionego programu roboczego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ProgramPause()``"
    "Opis", "Wstrzymywanie bieżącego uruchomionego programu roboczego"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Wznawianie bieżącego wstrzymanego programu roboczego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ProgramResume()``"
    "Opis", "Wznawianie bieżącego wstrzymanego programu roboczego"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Zatrzymywanie bieżącego uruchomionego programu roboczego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ProgramStop()``"
    "Opis", "Zatrzymywanie bieżącego uruchomionego programu roboczego"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Pobieranie stanu wykonania programu roboczego robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetProgramState()``"
    "Opis", "Pobieranie stanu wykonania programu roboczego robota"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``state``: Stan wykonania programu roboczego robota, 1-program zatrzymany lub brak uruchomionego programu, 2-program działa, 3-program wstrzymany"

Przykład kodu operacji na programie LUA robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    program_name = "test0610.lua"
    loaded_name = ""
    state = 0
    line = 0
    robot.Mode(0)
    robot.LoadDefaultProgConfig(0, program_name)
    robot.ProgramLoad(program_name)
    robot.ProgramRun()
    time.sleep(1)
    robot.ProgramPause()
    error,state = robot.GetProgramState()
    print(f"program state:{state}")
    error,line = robot.GetCurrentLine()
    print(f"current line:{line}")
    error,loaded_name = robot.GetLoadedProgram()
    print(f"program name:{loaded_name}")
    time.sleep(1)
    robot.ProgramResume()
    time.sleep(1)
    robot.ProgramStop()
    time.sleep(1)
    robot.CloseRPC()

Pobieranie pliku LUA
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30
    
    "Prototyp", "``LuaDownLoad(fileName, savePath)``"
    "Opis", "Pobieranie pliku LUA"
    "Parametry wymagane", "- ``fileName``: Nazwa pliku lua do pobrania, np. „test.lua”
    - ``savePath``: Lokalna ścieżka zapisu pliku, np. „D://Down/”"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Usuwanie pliku LUA
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LuaDelete(fileName)``"
    "Opis", "Usuwanie pliku LUA"
    "Parametry wymagane", "- ``fileName``: Nazwa pliku lua do usunięcia „test.lua”"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Pobieranie nazw wszystkich bieżących plików lua
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetLuaList()``"
    "Opis", "Pobieranie nazw wszystkich bieżących plików lua"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``lua_num``: Liczba plików lua
    - ``luaNames``: Lista nazw plików lua"

Przesyłanie pliku LUA
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LuaUpload(filePath)``"
    "Opis", "Przesyłanie pliku LUA"
    "Parametry wymagane", "- ``filePath``: Pełna ścieżka przesyłanego pliku, np. D://test/test.lua"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - errorStr (zwracane, jeśli plik lua zawiera błąd)"

Przykład kodu przesyłania i pobierania pliku LUA robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 

    from fairino import Robot
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    rtn,lua_num,luaNames = robot.GetLuaList()
    print(f"res is:{rtn}")
    print(f"size is:{lua_num}")
    for name in luaNames:
        print(name)
    rtn = robot.LuaDownLoad("test0610.lua", "D://zDOWN/")
    print(f"LuaDownLoad rtn is:{rtn}")
    rtn = robot.LuaUpload("D://zDOWN/test0610.lua")
    print(f"LuaUpload rtn is:{rtn}")
    rtn = robot.LuaDelete("test0610.lua")
    print(f"LuaDelete rtn is:{rtn}")
    robot.CloseRPC()