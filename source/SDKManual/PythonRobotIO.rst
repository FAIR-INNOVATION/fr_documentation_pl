Wejścia/Wyjścia (IO) robota
============================

.. toctree:: 
    :maxdepth: 5

Ustawianie wyjścia cyfrowego skrzynki kontrolnej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetDO(id, status, smooth=0, block=0)``"
    "Opis", "Ustawianie wyjścia cyfrowego skrzynki kontrolnej"
    "Parametry wymagane", "-  ``id``: Numer wejścia/wyjścia, zakres [0~15];
    - ``status``: 0-wył., 1-wł.;"
    "Parametry domyślne", "- ``smooth``: 0-niewygładzane, 1-wygładzane domyślnie 0;
    - ``block``: 0-blokujący, 1-nieblokujący domyślnie 0"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie wyjścia cyfrowego narzędzia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetToolDO (id, status, smooth=0, block=0)``"
    "Opis", "Ustawianie wyjścia cyfrowego narzędzia"
    "Parametry wymagane", "-  ``id``: Numer wejścia/wyjścia, zakres [0~1];
    - ``status``: 0-wył., 1-wł.;"
    "Parametry domyślne", "- ``smooth``: 0-niewygładzane, 1-wygładzane;
    - ``block``: 0-blokujący, 1-nieblokujący."
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie wyjścia analogowego skrzynki kontrolnej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetAO(id,value,block=0)``"
    "Opis", "Ustawianie wyjścia analogowego skrzynki kontrolnej"
    "Parametry wymagane", "- ``id``: Numer wejścia/wyjścia, zakres [0~1];
    - ``value``: Procent wartości prądu lub napięcia, zakres [0~100%] odpowiada wartości prądu [0~20mA] lub napięcia [0~10V];"
    "Parametry domyślne", "- ``block``: [0]-blokujący, [1]-nieblokujący domyślnie 0"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie wyjścia analogowego narzędzia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetToolAO(id,value,block=0)``"
    "Opis", "Ustawianie wyjścia analogowego narzędzia"
    "Parametry wymagane", "- ``id``: Numer wejścia/wyjścia, zakres [0];
    - ``value``: Procent wartości prądu lub napięcia, zakres [0~100%] odpowiada wartości prądu [0~20mA] lub napięcia [0~10V];"
    "Parametry domyślne", "- ``block``: [0]-blokujący, [1]-nieblokujący domyślnie 0"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Przykład kodu ustawiania wyjść cyfrowych i analogowych
+++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    status = 1
    smooth = 0  
    block = 0 
    for i in range(16):
        robot.SetDO(i, status, smooth, block)
        time.sleep(0.3) 
    status = 0 
    for i in range(16):
        robot.SetDO(i, status, smooth, block)
        time.sleep(0.3)
    status = 1
    for i in range(2):
        robot.SetToolDO(i, status, smooth, block)
        time.sleep(1) 
    status = 0 
    for i in range(2):
        robot.SetToolDO(i, status, smooth, block)
        time.sleep(1)
    for i in range(100):
        robot.SetAO(0, i, block)
        time.sleep(0.03)
    for i in range(100):
        robot.SetToolAO(0, i, block)
        time.sleep(0.03)
    robot.CloseRPC()

Pobieranie wejścia cyfrowego skrzynki kontrolnej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetDI(id, block=0)``"
    "Opis", "Pobieranie wejścia cyfrowego skrzynki kontrolnej"
    "Parametry wymagane", "- ``id``: Numer wejścia/wyjścia, zakres [0~15];"
    "Parametry domyślne", "- ``block``: 0-blokujący, 1-nieblokujący domyślnie 0"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``di``: 0-niski poziom, 1-wysoki poziom"

Pobieranie wejścia cyfrowego narzędzia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetToolDI(id, block=0)``"
    "Opis", "Pobieranie wejścia cyfrowego narzędzia"
    "Parametry wymagane", "- ``id``: Numer wejścia/wyjścia, zakres [0~1];"
    "Parametry domyślne", "- ``block``: 0-blokujący, 1-nieblokujący domyślnie 0"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode
    - ``di``: 0-niski poziom, 1-wysoki poziom"

Pobieranie wejścia analogowego skrzynki kontrolnej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetAI(id, block = 0)``"
    "Opis", "Pobieranie wejścia analogowego skrzynki kontrolnej"
    "Parametry wymagane", "- ``id``: Numer wejścia/wyjścia, zakres [0~1];"
    "Parametry domyślne", "- ``block``: 0-blokujący, 1-nieblokujący domyślnie 0 "
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``value``: Procent wejściowej wartości prądu lub napięcia, zakres [0~100] odpowiada wartości prądu [0~20mA] lub napięcia [0~10V]"

Pobieranie wejścia analogowego narzędzia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetToolAI(id, block = 0)``"
    "Opis", "Pobieranie wejścia analogowego końcówki"
    "Parametry wymagane", "- ``id``: Numer wejścia/wyjścia, zakres [0];"
    "Parametry domyślne", "- ``block``: 0-blokujący, 1-nieblokujący domyślnie 0"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``value``: Procent wejściowej wartości prądu lub napięcia, zakres [0~100] odpowiada wartości prądu [0~20mA] lub napięcia [0~10V]"

Pobieranie stanu przycisku rejestracji punktu końcowego robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetAxlePointRecordBtnState()``"
    "Opis", "Pobieranie stanu przycisku rejestracji punktu końcowego robota"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``buttonstatus``: Stan przycisku, 0-wciśnięty, 1-zwolniony"

Pobieranie stanu wyjścia DO końcówki robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetToolDO()``"
    "Opis", "Pobieranie stanu wyjścia DO końcówki robota"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``do_state``: Stan wyjścia DO, do0~do1 odpowiadają bit1~bit2, zaczynając od bit0"

Pobieranie stanu wyjścia DO kontrolera robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetDO()``"
    "Opis", "Pobieranie stanu wyjścia DO kontrolera robota"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``do_state_h``: Stan wyjścia DO, co0~co7 odpowiadają bit0~bit7 do_state_l Stan wyjścia DO, do0~do7 odpowiadają bit0~bit7"

Przykład kodu pobierania stanów DI i DO robota
+++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    block = 0 
    error,di = robot.GetDI(0, block)
    print(f"di0: {di}")
    error,tool_di = robot.GetToolDI(1, block)
    print(f"tool_di1: {tool_di}")
    error,ai = robot.GetAI(0, block)
    print(f"ai0: {ai:.2f}") 
    error,tool_ai = robot.GetToolAI(0, block)
    print(f"tool_ai0: {tool_ai:.2f}")
    error,button_state = robot.GetAxlePointRecordBtnState()
    print(f"_button_state is: {button_state}")
    error,tool_do_state = robot.GetToolDO()
    print(f"tool DO state: {tool_do_state}")
    error,[do_state_h, do_state_l] = robot.GetDO()
    print(f"DO state hight  : {do_state_h}")
    print(f"DO state low : {do_state_l}")
    robot.CloseRPC()

Oczekiwanie na wejście cyfrowe skrzynki kontrolnej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WaitDI(id,status,maxtime,opt)``"
    "Opis", "Oczekiwanie na wejście cyfrowe skrzynki kontrolnej"
    "Parametry wymagane", "- ``id``: Numer wejścia/wyjścia, zakres [0~15];
    - ``status``: 0-wył., 1-wł.;
    - ``maxtime``: Maksymalny czas oczekiwania, jednostka [ms];
    - ``opt``: Strategia po czasie, 0-zatrzymanie programu i powiadomienie o czasie, 1-ignorowanie powiadomienia o czasie i kontynuacja programu, 2-oczekiwanie w nieskończoność"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Oczekiwanie na wielokanałowe wejście cyfrowe skrzynki kontrolnej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WaitMultiDI(mode,id,status,maxtime,opt)``"
    "Opis", "Oczekiwanie na wielokanałowe wejście cyfrowe skrzynki kontrolnej"
    "Parametry wymagane", "- ``mode``: [0]-AND wielu kanałów, [1]-OR wielu kanałów;
    - ``id``: Numer wejścia/wyjścia, bit0~bit7 odpowiadają DI0~DI7, bit8~bit15 odpowiadają CI0~CI7;
    - ``status``: bit0~bit7 odpowiadają stanom DI0~DI7, bit8~bit15 odpowiadają stanom bitów CI0~CI7 [0]-wył., [1]-wł.;
    - ``maxtime``: Maksymalny czas oczekiwania, jednostka [ms];
    - ``opt``: Strategia po czasie, 0-zatrzymanie programu i powiadomienie o czasie, 1-ignorowanie powiadomienia o czasie i kontynuacja programu, 2-oczekiwanie w nieskończoność."
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Oczekiwanie na wejście cyfrowe narzędzia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WaitToolDI(id,status,maxtime,opt)``"
    "Opis", "Oczekiwanie na wejście cyfrowe końcówki"
    "Parametry wymagane", "- ``id``: Numer wejścia/wyjścia, zakres [0~1];
    - ``status``: 0-wył., 1-wł.;
    - ``maxtime``: Maksymalny czas oczekiwania, jednostka [ms];
    - ``opt``: Strategia po czasie, 0-zatrzymanie programu i powiadomienie o czasie, 1-ignorowanie powiadomienia o czasie i kontynuacja programu, 2-oczekiwanie w nieskończoność"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Oczekiwanie na wejście analogowe skrzynki kontrolnej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WaitAI(id,sign,value,maxtime,opt)``"
    "Opis", "Oczekiwanie na wejście analogowe skrzynki kontrolnej"
    "Parametry wymagane", "- ``id``: Numer wejścia/wyjścia, zakres [0~1];
    - ``sign``: 0-większe niż, 1-mniejsze niż
    - ``value``: Procent wejściowej wartości prądu lub napięcia, zakres [0~100] odpowiada wartości prądu [0~20mA] lub napięcia [0~10V];
    - ``maxtime``: Maksymalny czas oczekiwania, jednostka [ms];
    - ``opt``: Strategia po czasie, 0-zatrzymanie programu i powiadomienie o czasie, 1-ignorowanie powiadomienia o czasie i kontynuacja programu, 2-oczekiwanie w nieskończoność"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Oczekiwanie na wejście analogowe narzędzia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WaitToolAI(id,sign,value,maxtime,opt)``"
    "Opis", "Oczekiwanie na wejście analogowe końcówki"
    "Parametry wymagane", "- ``id``: Numer wejścia/wyjścia, zakres [0];
    - ``sign``: 0-większe niż, 1-mniejsze niż
    - ``value``: Procent wejściowej wartości prądu lub napięcia, zakres [0~100] odpowiada wartości prądu [0~20mA] lub napięcia [0~10V];
    - ``maxtime``: Maksymalny czas oczekiwania, jednostka [ms];
    - ``opt``: Strategia po czasie, 0-zatrzymanie programu i powiadomienie o czasie, 1-ignorowanie powiadomienia o czasie i kontynuacja programu, 2-oczekiwanie w nieskończoność"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Przykład kodu oczekiwania na cyfrowe i analogowe sygnały wejściowe skrzynki kontrolnej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    status = 1
    smooth = 0
    block = 0
    for i in range(16):
        robot.SetDO(i, status, smooth, block)
        time.sleep(0.3)
    status = 0
    for i in range(16):
        robot.SetDO(i, status, smooth, block)
        time.sleep(0.3)
    status = 1
    for i in range(2):
        robot.SetToolDO(i, status, smooth, block)
        time.sleep(1)
    status = 0
    for i in range(2):
        robot.SetToolDO(i, status, smooth, block)
        time.sleep(1)
    for i in range(100):
        robot.SetAO(0, i, block)
        time.sleep(0.03)
    for i in range(100):
        robot.SetToolAO(0, i, block)
        time.sleep(0.03)
    block = 0
    error,di = robot.GetDI(0, block)
    print(f"di0: {di}")
    error,tool_di = robot.GetToolDI(1, block)
    print(f"tool_di1: {tool_di}")
    error,ai = robot.GetAI(0, block)
    print(f"ai0: {ai:.2f}")
    error,tool_ai = robot.GetToolAI(0, block)
    print(f"tool_ai0: {tool_ai:.2f}")
    error,button_state = robot.GetAxlePointRecordBtnState()
    print(f"_button_state is: {button_state}")
    error,tool_do_state = robot.GetToolDO()
    print(f"tool DO state: {tool_do_state}")
    error,[do_state_h, do_state_l] = robot.GetDO()
    print(f"DO state hight  : {do_state_h}")
    print(f"DO state low : {do_state_l}")
    rtn = robot.WaitDI(0, 1, 1000, 1)
    print(f"WaitDI over; rtn is: {rtn}")
    rtn = robot.WaitMultiDI(1, 3, 3, 1000, 1)
    print(f"WaitDI over; rtn is: {rtn}")
    rtn = robot.WaitToolDI(1, 1, 1000, 1)
    print(f"WaitDI over; rtn is: {rtn}")
    rtn = robot.WaitAI(0, 0, 50, 1000, 1)
    print(f"WaitDI over; rtn is: {rtn}")
    rtn = robot.WaitToolAI(0, 0, 50, 1000, 1)
    print(f"WaitDI over; rtn is: {rtn}")
    robot.CloseRPC()

Ustawianie, czy wyjście DO skrzynki kontrolnej jest resetowane po zatrzymaniu/wstrzymaniu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetOutputResetCtlBoxDO(resetFlag,reloadFlag)``"
    "Opis", "Ustawianie, czy wyjście DO skrzynki kontrolnej jest resetowane po zatrzymaniu/wstrzymaniu"
    "Parametry wymagane", "
    - ``resetFlag``: 0-nie resetuj; 1-resetuj
    - ``reloadFlag``: Czy ponownie załadować po wznowieniu po wstrzymaniu, 0-nie ładuj; 1-ładuj"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie, czy wyjście AO skrzynki kontrolnej jest resetowane po zatrzymaniu/wstrzymaniu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetOutputResetCtlBoxDO(resetFlag,reloadFlag)``"
    "Opis", "Ustawianie, czy wyjście AO skrzynki kontrolnej jest resetowane po zatrzymaniu/wstrzymaniu"
    "Parametry wymagane", "
    - ``resetFlag``: 0-nie resetuj; 1-resetuj
    - ``reloadFlag``: Czy ponownie załadować po wznowieniu po wstrzymaniu, 0-nie ładuj; 1-ładuj"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie, czy wyjście DO narzędzia końcowego jest resetowane po zatrzymaniu/wstrzymaniu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetOutputResetAxleDO(resetFlag,reloadFlag)``"
    "Opis", "Ustawianie, czy wyjście DO narzędzia końcowego jest resetowane po zatrzymaniu/wstrzymaniu"
    "Parametry wymagane", "
    - ``resetFlag``: 0-nie resetuj; 1-resetuj
    - ``reloadFlag``: Czy ponownie załadować po wznowieniu po wstrzymaniu, 0-nie ładuj; 1-ładuj"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie, czy wyjście AO narzędzia końcowego jest resetowane po zatrzymaniu/wstrzymaniu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetOutputResetAxleAO(resetFlag,reloadFlag)``"
    "Opis", "Ustawianie, czy wyjście AO narzędzia końcowego jest resetowane po zatrzymaniu/wstrzymaniu"
    "Parametry wymagane", "
    - ``resetFlag``: 0-nie resetuj; 1-resetuj
    - ``reloadFlag``: Czy ponownie załadować po wznowieniu po wstrzymaniu, 0-nie ładuj; 1-ładuj"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie, czy wyjście rozszerzonego DO jest resetowane po zatrzymaniu/wstrzymaniu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetOutputResetExtDO (resetFlag,reloadFlag)``"
    "Opis", "Ustawianie, czy wyjście rozszerzonego DO jest resetowane po zatrzymaniu/wstrzymaniu"
    "Parametry wymagane", "
    - ``resetFlag``: 0-nie resetuj; 1-resetuj
    - ``reloadFlag``: Czy ponownie załadować po wznowieniu po wstrzymaniu, 0-nie ładuj; 1-ładuj"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie, czy wyjście rozszerzonego AO jest resetowane po zatrzymaniu/wstrzymaniu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetOutputResetExtAO (resetFlag,reloadFlag)``"
    "Opis", "Ustawianie, czy wyjście rozszerzonego AO jest resetowane po zatrzymaniu/wstrzymaniu"
    "Parametry wymagane", "
    - ``resetFlag``: 0-nie resetuj; 1-resetuj
    - ``reloadFlag``: Czy ponownie załadować po wznowieniu po wstrzymaniu, 0-nie ładuj; 1-ładuj"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie, czy wyjście SmartTool jest resetowane po zatrzymaniu/wstrzymaniu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetOutputResetSmartToolDO(resetFlag,reloadFlag)``"
    "Opis", "Ustawianie, czy wyjście SmartTool jest resetowane po zatrzymaniu/wstrzymaniu"
    "Parametry wymagane", "
    - ``resetFlag``: 0-nie resetuj; 1-resetuj
    - ``reloadFlag``: Czy ponownie załadować po wznowieniu po wstrzymaniu, 0-nie ładuj; 1-ładuj"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode "

Przykład kodu resetowania wyjść po zatrzymaniu/wstrzymaniu programu LUA
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    robot = Robot.RPC('192.168.58.2')
    for i in range(16):
        robot.SetDO(i, 1, 0, 0)
        time.sleep(0.2)
    resetFlag = 0
    resumeReloadFlag = 0
    rtn = robot.SetOutputResetCtlBoxDO(resetFlag, resumeReloadFlag)
    robot.SetOutputResetCtlBoxAO(resetFlag, resumeReloadFlag)
    robot.SetOutputResetAxleDO(resetFlag, resumeReloadFlag)
    robot.SetOutputResetAxleAO(resetFlag, resumeReloadFlag)
    robot.SetOutputResetExtDO(resetFlag, resumeReloadFlag)
    robot.SetOutputResetExtAO(resetFlag, resumeReloadFlag)
    robot.SetOutputResetSmartToolDO(resetFlag, resumeReloadFlag)
    robot.ProgramLoad("test.lua")
    robot.ProgramRun()
    time.sleep(2)
    robot.PauseMotion()
    time.sleep(2)
    robot.ResumeMotion()
    time.sleep(2)
    robot.CloseRPC()
    return 0
    
Ustawianie funkcji konfigurowalnego portu CI
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetDIConfig(config)``"
    "Opis", "Ustawianie funkcji konfigurowalnego portu CI"
    "Parametry wymagane", "
    - ``config``: Tablica kodów funkcji CI0-CI7, 0-brak;1-pomyślne zajarzenie łuku;2-gotowość spawarki;3-wykrywanie przenośnika;4-wstrzymanie;5-wznowienie;6-uruchomienie;7-zatrzymanie;
      58-wstrzymanie/wznowienie;9-uruchomienie/zatrzymanie;10-przeciąganie nożne;11-przejście do punktu początkowego zadania;12-przełączanie ręczny/automatyczny;
      613-pomyślne znalezienie pozycji drutu;14-przerwanie ruchu;15-uruchomienie programu głównego;16-uruchomienie przewijania;17-potwierdzenie uruchomienia;
      718-sygnał detekcji fotoelektrycznej X;19-sygnał detekcji fotoelektrycznej Y;20-zewnętrzny sygnał zatrzymania awaryjnego 1;21-zewnętrzny sygnał zatrzymania awaryjnego 2;
      822-tryb redukcji pierwszego stopnia;23-tryb redukcji drugiego stopnia;24-tryb redukcji trzeciego stopnia (zatrzymanie);25-wznowienie spawania;26-zakończenie spawania;
      927-włączenie przeciągania wspomaganego;28-wyłączenie przeciągania wspomaganego;29-włączenie/wyłączenie przeciągania wspomaganego;30-wyczyszczenie wszystkich błędów;
      1031-przełączanie ręczny/automatyczny (poziom wysoki/niski);32-włączenie zasilania;33-wyłączenie zasilania;34-włączenie/wyłączenie zasilania (zbocze narastające/opadające);35-rozpoczęcie/zakończenie śledzenia punktowego"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode "
    
Pobieranie funkcji konfigurowalnego portu CI skrzynki kontrolnej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetDIConfig()``"
    "Opis", "Pobieranie funkcji konfigurowalnego portu CI skrzynki kontrolnej"
    "Parametry wymagane", "
    - ``config``: Tablica kodów funkcji CI0-CI7, 0-brak;1-pomyślne zajarzenie łuku;2-gotowość spawarki;3-wykrywanie przenośnika;4-wstrzymanie;5-wznowienie;6-uruchomienie;7-zatrzymanie;
      58-wstrzymanie/wznowienie;9-uruchomienie/zatrzymanie;10-przeciąganie nożne;11-przejście do punktu początkowego zadania;12-przełączanie ręczny/automatyczny;
      613-pomyślne znalezienie pozycji drutu;14-przerwanie ruchu;15-uruchomienie programu głównego;16-uruchomienie przewijania;17-potwierdzenie uruchomienia;
      718-sygnał detekcji fotoelektrycznej X;19-sygnał detekcji fotoelektrycznej Y;20-zewnętrzny sygnał zatrzymania awaryjnego 1;21-zewnętrzny sygnał zatrzymania awaryjnego 2;
      822-tryb redukcji pierwszego stopnia;23-tryb redukcji drugiego stopnia;24-tryb redukcji trzeciego stopnia (zatrzymanie);25-wznowienie spawania;26-zakończenie spawania;
      927-włączenie przeciągania wspomaganego;28-wyłączenie przeciągania wspomaganego;29-włączenie/wyłączenie przeciągania wspomaganego;30-wyczyszczenie wszystkich błędów;
      1031-przełączanie ręczny/automatyczny (poziom wysoki/niski);32-włączenie zasilania;33-wyłączenie zasilania;34-włączenie/wyłączenie zasilania (zbocze narastające/opadające);35-rozpoczęcie/zakończenie śledzenia punktowego"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode "
    
Ustawianie funkcji konfigurowalnego portu CO
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetDOConfig(config)``"
    "Opis", "Ustawianie funkcji konfigurowalnego portu CO"
    "Parametry wymagane", "
    - ``config``: Tablica kodów funkcji CO0-CO7, 0-brak;1-błąd robota;2-robot w ruchu;3-uruchamianie/zatrzymywanie natrysku;4-czyszczenie pistoletu natryskowego;5-sygnał podawania gazu;6-sygnał zajarzenia łuku;7-punktowe podawanie drutu;
      58-podawanie drutu wstecz;9-wejście JOB 1;10-wejście JOB 2;11-wejście JOB 3;12-sterowanie uruchamianiem/zatrzymywaniem przenośnika;13-robot wstrzymany;14-osiągnięcie punktu początkowego zadania;
      615-osiągnięcie strefy interferencji;16-sterowanie uruchamianiem/zatrzymywaniem poszukiwania pozycji drutu;17-robot uruchomiony;18-uruchomienie/zatrzymanie programu;19-tryb ręczny/automatyczny;20-sygnał wyjścia zatrzymania awaryjnego 1-bezpieczeństwo;
      721-sygnał wyjścia zatrzymania awaryjnego 2-bezpieczeństwo;22-zatrzymanie działania skryptu LUA;23-wyjście stanu bezpieczeństwa-bezpieczeństwo;24-wyjście stanu zatrzymania ochronnego-bezpieczeństwo;
      825-robot w ruchu-bezpieczeństwo;26-robot w trybie redukcji-bezpieczeństwo;27-robot w trybie nieredukcji-bezpieczeństwo;28-robot niezatrzymany;29-błąd robota-błąd punktu instrukcji;
      930-błąd robota-błąd sterownika;31-błąd robota-błąd przekroczenia miękkiego ograniczenia;32-błąd robota-błąd kolizji;33-błąd robota-błąd liczby aktywnych węzłów podrzędnych;
      1034-błąd robota-błąd węzła podrzędnego;35-błąd robota-błąd IO;36-błąd robota-błąd chwytaka;37-błąd robota-błąd pliku;38-błąd robota-błąd osobliwej pozy;
      1139-błąd robota-błąd komunikacji sterownika;40-błąd robota-błąd parametru;41-błąd robota-błąd przekroczenia miękkiego ograniczenia osi zewnętrznej;42-ostrzeżenie robota-ostrzeżenie;
      1243-ostrzeżenie robota-ostrzeżenie drzwi bezpieczeństwa;44-ostrzeżenie robota-ostrzeżenie ruchu;45-ostrzeżenie robota-ostrzeżenie strefy interferencji;46-ostrzeżenie robota-ostrzeżenie ściany bezpieczeństwa;
      1347-stan włączenia zasilania;48-automatyczne podnoszenie podczas utraty połączenia;49-ostrzeżenie interferencji sześcianu 1;50-ostrzeżenie interferencji sześcianu 2;51-ostrzeżenie interferencji sześcianu 3;52-ostrzeżenie interferencji sześcianu 4;"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode "
    
Pobieranie funkcji konfigurowalnego portu CO
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetDOConfig()``"
    "Opis", "Pobieranie funkcji konfigurowalnego portu CO"
    "Parametry wymagane", "
    - ``config``: Tablica kodów funkcji CO0-CO7, 0-brak;1-błąd robota;2-robot w ruchu;3-uruchamianie/zatrzymywanie natrysku;4-czyszczenie pistoletu natryskowego;5-sygnał podawania gazu;6-sygnał zajarzenia łuku;7-punktowe podawanie drutu;
      58-podawanie drutu wstecz;9-wejście JOB 1;10-wejście JOB 2;11-wejście JOB 3;12-sterowanie uruchamianiem/zatrzymywaniem przenośnika;13-robot wstrzymany;14-osiągnięcie punktu początkowego zadania;
      615-osiągnięcie strefy interferencji;16-sterowanie uruchamianiem/zatrzymywaniem poszukiwania pozycji drutu;17-robot uruchomiony;18-uruchomienie/zatrzymanie programu;19-tryb ręczny/automatyczny;20-sygnał wyjścia zatrzymania awaryjnego 1-bezpieczeństwo;
      721-sygnał wyjścia zatrzymania awaryjnego 2-bezpieczeństwo;22-zatrzymanie działania skryptu LUA;23-wyjście stanu bezpieczeństwa-bezpieczeństwo;24-wyjście stanu zatrzymania ochronnego-bezpieczeństwo;
      825-robot w ruchu-bezpieczeństwo;26-robot w trybie redukcji-bezpieczeństwo;27-robot w trybie nieredukcji-bezpieczeństwo;28-robot niezatrzymany;29-błąd robota-błąd punktu instrukcji;
      930-błąd robota-błąd sterownika;31-błąd robota-błąd przekroczenia miękkiego ograniczenia;32-błąd robota-błąd kolizji;33-błąd robota-błąd liczby aktywnych węzłów podrzędnych;
      1034-błąd robota-błąd węzła podrzędnego;35-błąd robota-błąd IO;36-błąd robota-błąd chwytaka;37-błąd robota-błąd pliku;38-błąd robota-błąd osobliwej pozy;
      1139-błąd robota-błąd komunikacji sterownika;40-błąd robota-błąd parametru;41-błąd robota-błąd przekroczenia miękkiego ograniczenia osi zewnętrznej;42-ostrzeżenie robota-ostrzeżenie;
      1243-ostrzeżenie robota-ostrzeżenie drzwi bezpieczeństwa;44-ostrzeżenie robota-ostrzeżenie ruchu;45-ostrzeżenie robota-ostrzeżenie strefy interferencji;46-ostrzeżenie robota-ostrzeżenie ściany bezpieczeństwa;
      1347-stan włączenia zasilania;48-automatyczne podnoszenie podczas utraty połączenia;49-ostrzeżenie interferencji sześcianu 1;50-ostrzeżenie interferencji sześcianu 2;51-ostrzeżenie interferencji sześcianu 3;52-ostrzeżenie interferencji sześcianu 4;"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode "
    
Ustawianie funkcji konfigurowalnego portu End-CI końcówki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetToolDIConfig(config)``"
    "Opis", "Ustawianie funkcji konfigurowalnego portu End-CI końcówki"
    "Parametry wymagane", "
    - ``config``: Tablica kodów funkcji End CI0-CI1, 0-brak;1-przełącznik narzędzia przeciągania i uczenia;2-sygnał rejestracji punktu;3-przełączanie ręczny/automatyczny (sygnał impulsowy);4-rozpoczęcie/zatrzymanie rejestracji TPD;5-wstrzymanie ruchu;
      56-wznowienie ruchu;7-uruchomienie;8-zatrzymanie;9-wstrzymanie/wznowienie;10-uruchomienie/zatrzymanie;11-włączenie przeciągania wspomaganego czujnikiem siły;12-wyłączenie przeciągania wspomaganego czujnikiem siły;
      613-włączenie/wyłączenie przeciągania wspomaganego czujnikiem siły;14-sygnał detekcji laserowej X;15-sygnał detekcji laserowej Y;16-ruch PTP do punktu początkowego zadania;17-przerwanie ruchu, zatrzymanie bieżącego ruchu zgodnie z sygnałem;
      718-uruchomienie programu głównego;19-uruchomienie przewijania;20-potwierdzenie uruchomienia;21-wznowienie spawania;22-zakończenie spawania;23-wyczyszczenie błędu;24-przełączanie ręczny/automatyczny (poziom wysoki/niski)
      825-włączenie zasilania;26-wyłączenie zasilania;27-włączenie/wyłączenie zasilania;28-sygnał uruchamiania/zatrzymywania serwośledzenia laserowego;"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode "
    
Pobieranie funkcji konfigurowalnego portu End-CI końcówki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetToolDIConfig()``"
    "Opis", "Pobieranie funkcji konfigurowalnego portu End-CI końcówki"
    "Parametry wymagane", "
    - ``config``: Tablica kodów funkcji End CI0-CI1, 0-brak;1-przełącznik narzędzia przeciągania i uczenia;2-sygnał rejestracji punktu;3-przełączanie ręczny/automatyczny (sygnał impulsowy);4-rozpoczęcie/zatrzymanie rejestracji TPD;5-wstrzymanie ruchu;
      56-wznowienie ruchu;7-uruchomienie;8-zatrzymanie;9-wstrzymanie/wznowienie;10-uruchomienie/zatrzymanie;11-włączenie przeciągania wspomaganego czujnikiem siły;12-wyłączenie przeciągania wspomaganego czujnikiem siły;
      613-włączenie/wyłączenie przeciągania wspomaganego czujnikiem siły;14-sygnał detekcji laserowej X;15-sygnał detekcji laserowej Y;16-ruch PTP do punktu początkowego zadania;17-przerwanie ruchu, zatrzymanie bieżącego ruchu zgodnie z sygnałem;
      718-uruchomienie programu głównego;19-uruchomienie przewijania;20-potwierdzenie uruchomienia;21-wznowienie spawania;22-zakończenie spawania;23-wyczyszczenie błędu;24-przełączanie ręczny/automatyczny (poziom wysoki/niski)
      825-włączenie zasilania;26-wyłączenie zasilania;27-włączenie/wyłączenie zasilania;28-sygnał uruchamiania/zatrzymywania serwośledzenia laserowego;"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode "
    
Ustawianie stanu aktywnego konfigurowalnego CI skrzynki kontrolnej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetDIConfigLevel(config)``"
    "Opis", "Ustawianie stanu aktywnego konfigurowalnego CI skrzynki kontrolnej"
    "Parametry wymagane", "
    - ``config``: Tablica stanów aktywnych portów CI0-CI7; 0-aktywny wysoki poziom; 1-aktywny niski poziom"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"
    
Pobieranie stanu aktywnego konfigurowalnego CI skrzynki kontrolnej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetDIConfigLevel()``"
    "Opis", "Pobieranie stanu aktywnego konfigurowalnego CI skrzynki kontrolnej"
    "Parametry wymagane", "
    - ``config``: Tablica stanów aktywnych portów CI0-CI7; 0-aktywny wysoki poziom; 1-aktywny niski poziom"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"
    
Ustawianie stanu aktywnego konfigurowalnego CO skrzynki kontrolnej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetDOConfigLevel(config)``"
    "Opis", "Ustawianie stanu aktywnego konfigurowalnego CO skrzynki kontrolnej"
    "Parametry wymagane", "
    - ``config``: Tablica stanów aktywnych portów CO0-CO7; 0-aktywny wysoki poziom; 1-aktywny niski poziom"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"
    
Pobieranie stanu aktywnego konfigurowalnego CO skrzynki kontrolnej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetDOConfigLevel()``"
    "Opis", "Pobieranie stanu aktywnego konfigurowalnego CO skrzynki kontrolnej"
    "Parametry wymagane", "
    - ``config``: Tablica stanów aktywnych portów CO0-CO7; 0-aktywny wysoki poziom; 1-aktywny niski poziom"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"
    
Ustawianie stanu aktywnego konfigurowalnego CI końcówki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetToolDIConfigLevel(config)``"
    "Opis", "Ustawianie stanu aktywnego konfigurowalnego CI końcówki"
    "Parametry wymagane", "
    - ``config``: Tablica stanów aktywnych portów CI0-CI7; 0-aktywny wysoki poziom; 1-aktywny niski poziom"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"
    
Pobieranie stanu aktywnego konfigurowalnego CI końcówki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetToolDIConfigLevel()``"
    "Opis", "Pobieranie stanu aktywnego konfigurowalnego CI końcówki"
    "Parametry wymagane", "
    - ``config``: Tablica stanów aktywnych portów CI0-CI7; 0-aktywny wysoki poziom; 1-aktywny niski poziom"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"
    
Ustawianie stanu aktywnego standardowego DI skrzynki kontrolnej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetStandardDILevel(config)``"
    "Opis", "Ustawianie stanu aktywnego standardowego DI skrzynki kontrolnej"
    "Parametry wymagane", "
    - ``config``: Tablica stanów aktywnych portów DI0-DI7; 0-aktywny wysoki poziom; 1-aktywny niski poziom"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"
    
Pobieranie stanu aktywnego standardowego DI skrzynki kontrolnej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetStandardDILevel()``"
    "Opis", "Pobieranie stanu aktywnego standardowego DI skrzynki kontrolnej"
    "Parametry wymagane", "
    - ``config``: Tablica stanów aktywnych portów DI0-DI7; 0-aktywny wysoki poziom; 1-aktywny niski poziom"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"
    
Ustawianie stanu aktywnego standardowego DO skrzynki kontrolnej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetStandardDOLevel(config)``"
    "Opis", "Ustawianie stanu aktywnego standardowego DO skrzynki kontrolnej"
    "Parametry wymagane", "
    - ``config``: Tablica stanów aktywnych portów DO0-DO7; 0-aktywny wysoki poziom; 1-aktywny niski poziom"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"
    
Pobieranie stanu aktywnego standardowego DO skrzynki kontrolnej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetStandardDOLevel()``"
    "Opis", "Pobieranie stanu aktywnego standardowego DO skrzynki kontrolnej"
    "Parametry wymagane", "
    - ``config``: Tablica stanów aktywnych portów DO0-DO7; 0-aktywny wysoki poziom; 1-aktywny niski poziom"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"
    
Przykład kodu SDK związany z konfiguracją IO
+++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from time import sleep
    import time
    from fairino import Robot

    # Połączenie z kontrolerem robota
    robot = Robot.RPC('192.168.58.2')


    def TestIOConfig(self):
        # Ustawianie i pobieranie konfiguracji DI
        setDIConfig = [1, 2, 3, 4, 5, 6, 7, 8]
        getDIConfig = [0] * 8
        rtn = robot.SetDIConfig(setDIConfig)
        print(f"SetDIConfig rtn is {rtn}")
        rtn, getDIConfig = robot.GetDIConfig()
        print(f"GetDIConfig rtn is {rtn}, value is {getDIConfig[0]} {getDIConfig[1]} {getDIConfig[2]} {getDIConfig[3]} {getDIConfig[4]} {getDIConfig[5]} {getDIConfig[6]} {getDIConfig[7]}")

        # Ustawianie i pobieranie konfiguracji DO
        setDOConfig = [9, 10, 11, 12, 13, 14, 15, 16]
        getDOConfig = [0] * 8
        rtn = robot.SetDOConfig(setDOConfig)
        print(f"SetDOConfig rtn is {rtn}")
        rtn, getDOConfig = robot.GetDOConfig()
        print(f"GetDOConfig rtn is {rtn}, value is {getDOConfig[0]} {getDOConfig[1]} {getDOConfig[2]} {getDOConfig[3]} {getDOConfig[4]} {getDOConfig[5]} {getDOConfig[6]} {getDOConfig[7]}")

        # Ustawianie i pobieranie konfiguracji DI narzędzia
        setToolDIConfig = [17, 18]
        getToolDIConfig = [0] * 2
        rtn = robot.SetToolDIConfig(setToolDIConfig)
        print(f"SetToolDIConfig rtn is {rtn}")
        rtn, getToolDIConfig = robot.GetToolDIConfig()
        print(f"GetToolDIConfig rtn is {rtn}, value is {getToolDIConfig[0]} {getToolDIConfig[1]}")

        # Ustawianie i pobieranie konfiguracji poziomu DI (0: aktywny niski poziom, 1: aktywny wysoki poziom)
        setDIConfigLevel = [1, 1, 1, 1, 0, 0, 0, 0]
        getDIConfigLevel = [0] * 8
        rtn = robot.SetDIConfigLevel(setDIConfigLevel)
        print(f"SetDIConfigLevel rtn is {rtn}")
        rtn, getDIConfigLevel = robot.GetDIConfigLevel()
        print(f"GetDIConfigLevel rtn is {rtn}, value is {getDIConfigLevel[0]} {getDIConfigLevel[1]} {getDIConfigLevel[2]} {getDIConfigLevel[3]} {getDIConfigLevel[4]} {getDIConfigLevel[5]} {getDIConfigLevel[6]} {getDIConfigLevel[7]}")

        # Ustawianie i pobieranie konfiguracji poziomu DO (0: aktywny niski poziom, 1: aktywny wysoki poziom)
        setDOConfigLevel = [0, 0, 0, 0, 1, 1, 1, 1]
        getDOConfigLevel = [0] * 8
        rtn = robot.SetDOConfigLevel(setDOConfigLevel)
        print(f"SetDOConfigLevel rtn is {rtn}")
        rtn, getDOConfigLevel = robot.GetDOConfigLevel()
        print(f"GetDOConfigLevel rtn is {rtn}, value is {getDOConfigLevel[0]} {getDOConfigLevel[1]} {getDOConfigLevel[2]} {getDOConfigLevel[3]} {getDOConfigLevel[4]} {getDOConfigLevel[5]} {getDOConfigLevel[6]} {getDOConfigLevel[7]}")

        # Ustawianie i pobieranie konfiguracji poziomu DI narzędzia
        setToolDIConfigLevel = [1, 0]
        getToolDIConfigLevel = [0] * 2
        rtn = robot.SetToolDIConfigLevel(setToolDIConfigLevel)
        print(f"SetToolDIConfigLevel rtn is {rtn}")
        rtn, getToolDIConfigLevel = robot.GetToolDIConfigLevel()
        print(f"GetToolDIConfigLevel rtn is {rtn}, value is {getToolDIConfigLevel[0]} {getToolDIConfigLevel[1]}")

        # Ustawianie i pobieranie konfiguracji poziomu standardowego DI
        setStandardDILevel = [1, 1, 1, 1, 0, 0, 0, 0]
        getStandardDILevel = [0] * 8
        rtn = robot.SetStandardDILevel(setStandardDILevel)
        print(f"SetStandardDILevel rtn is {rtn}")
        rtn, getStandardDILevel = robot.GetStandardDILevel()
        print(f"GetStandardDILevel rtn is {rtn}, value is {getStandardDILevel[0]} {getStandardDILevel[1]} {getStandardDILevel[2]} {getStandardDILevel[3]} {getStandardDILevel[4]} {getStandardDILevel[5]} {getStandardDILevel[6]} {getStandardDILevel[7]}")

        # Ustawianie i pobieranie konfiguracji poziomu standardowego DO
        setStandardDOLevel = [0, 0, 0, 0, 1, 1, 1, 1]
        getStandardDOLevel = [0] * 8
        rtn = robot.SetStandardDOLevel(setStandardDOLevel)
        print(f"SetStandardDOLevel rtn is {rtn}")
        rtn, getStandardDOLevel = robot.GetStandardDOLevel()
        print(f"GetStandsrdDOLevel rtn is {rtn}, value is {getStandardDOLevel[0]} {getStandardDOLevel[1]} {getStandardDOLevel[2]} {getStandardDOLevel[3]} {getStandardDOLevel[4]} {getStandardDOLevel[5]} {getStandardDOLevel[6]} {getStandardDOLevel[7]}")

        # Oczekiwanie 2 sekundy
        time.sleep(2)

        # Zamknięcie połączenia
        robot.CloseRPC()
        time.sleep(1)

    # Wywołanie funkcji testowej
    TestIOConfig(robot)