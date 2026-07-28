Spawanie
========

.. toctree:: 
    :maxdepth: 5
    
Ustawianie parametrów krzywej procesu spawania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeldingSetProcessParam(id, startCurrent, startVoltage, startTime, weldCurrent, weldVoltage, endCurrent, endVoltage, endTime)``"
    "Opis", "Ustawianie parametrów krzywej procesu spawania"
    "Parametry wymagane", "
    - ``id``: Numer procesu spawania (1-99)
    - ``startCurrent``: Prąd zapłonu łuku (A)
    - ``startVoltage``: Napięcie zapłonu łuku (V)
    - ``startTime``: Czas zapłonu łuku (ms)
    - ``weldCurrent``: Prąd spawania (A)
    - ``weldVoltage``: Napięcie spawania (V)
    - ``endCurrent``: Prąd wygaszenia łuku (A)
    - ``endVoltage``: Napięcie wygaszenia łuku (V)
    - ``endTime``: Czas wygaszenia łuku (ms)
    "
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode" 

Pobieranie parametrów krzywej procesu spawania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeldingGetProcessParam(id)``"
    "Opis", "Pobieranie parametrów krzywej procesu spawania"
    "Parametry wymagane", "
    - ``id``: Numer procesu spawania (1-99)
    "
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``startCurrent``: Prąd zapłonu łuku (A)
    - ``startVoltage``: Napięcie zapłonu łuku (V)
    - ``startTime``: Czas zapłonu łuku (ms)
    - ``weldCurrent``: Prąd spawania (A)
    - ``weldVoltage``: Napięcie spawania (V)
    - ``endCurrent``: Prąd wygaszenia łuku (A)
    - ``endVoltage``: Napięcie wygaszenia łuku (V)
    - ``endTime``: Czas wygaszenia łuku (ms)
    " 

Ustawianie zależności między prądem spawania a wyjściowym sygnałem analogowym
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionchanged:: python SDK-v2.0.5
    
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeldingSetCurrentRelation(currentMin, currentMax, outputVoltageMin, outputVoltageMax)``"
    "Opis", "Ustawianie zależności między prądem spawania a wyjściowym sygnałem analogowym"
    "Parametry wymagane", "- ``currentMin``: Wartość prądu w lewym punkcie zależności liniowej prąd spawania - wyjście analogowe (A)
    - ``currentMax``: Wartość prądu w prawym punkcie zależności liniowej prąd spawania - wyjście analogowe (A)
    - ``outputVoltageMin``: Wartość napięcia wyjściowego analogowego w lewym punkcie zależności liniowej prąd spawania - wyjście analogowe (V)
    - ``outputVoltageMax``: Wartość napięcia wyjściowego analogowego w prawym punkcie zależności liniowej prąd spawania - wyjście analogowe (V)
    - ``AOIndex``: Port wyjścia analogowego prądu spawania"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie zależności między napięciem spawania a wyjściowym sygnałem analogowym
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionchanged:: python SDK-v2.0.5
    
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeldingSetVoltageRelation(weldVoltageMin, weldVoltageMax, outputVoltageMin, outputVoltageMax)``"
    "Opis", "Ustawianie zależności między napięciem spawania a wyjściowym sygnałem analogowym"
    "Parametry wymagane", "- ``weldVoltageMin``: Wartość napięcia spawania w lewym punkcie zależności liniowej napięcie spawania - wyjście analogowe (A)
    - ``weldVoltageMax``: Wartość napięcia spawania w prawym punkcie zależności liniowej napięcie spawania - wyjście analogowe (A)
    - ``outputVoltageMin``: Wartość napięcia wyjściowego analogowego w lewym punkcie zależności liniowej napięcie spawania - wyjście analogowe (V)
    - ``outputVoltageMax``: Wartość napięcia wyjściowego analogowego w prawym punkcie zależności liniowej napięcie spawania - wyjście analogowe (V)
    - ``AOIndex``: Port wyjścia analogowego napięcia spawania"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Pobieranie zależności między prądem spawania a wyjściowym sygnałem analogowym
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionchanged:: python SDK-v2.0.5
    
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeldingGetCurrentRelation()``"
    "Opis", "Pobieranie zależności między prądem spawania a wyjściowym sygnałem analogowym"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``currentMin``: Wartość prądu w lewym punkcie zależności liniowej prąd spawania - wyjście analogowe (A)
    - ``currentMax``: Wartość prądu w prawym punkcie zależności liniowej prąd spawania - wyjście analogowe (A)
    - ``outputVoltageMin``: Wartość napięcia wyjściowego analogowego w lewym punkcie zależności liniowej prąd spawania - wyjście analogowe (V)
    - ``outputVoltageMax``: Wartość napięcia wyjściowego analogowego w prawym punkcie zależności liniowej prąd spawania - wyjście analogowe (V)
    - ``AOIndex``: Port wyjścia analogowego napięcia spawania"

Pobieranie zależności między napięciem spawania a wyjściowym sygnałem analogowym
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionchanged:: python SDK-v2.0.5
    
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeldingGetVoltageRelation()``"
    "Opis", "Pobieranie zależności między napięciem spawania a wyjściowym sygnałem analogowym"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``weldVoltageMin``: Wartość napięcia spawania w lewym punkcie zależności liniowej napięcie spawania - wyjście analogowe (V)
    - ``weldVoltageMax``: Wartość napięcia spawania w prawym punkcie zależności liniowej napięcie spawania - wyjście analogowe (V)
    - ``outputVoltageMin``: Wartość napięcia wyjściowego analogowego w lewym punkcie zależności liniowej napięcie spawania - wyjście analogowe (V)
    - ``outputVoltageMax``: Wartość napięcia wyjściowego analogowego w prawym punkcie zależności liniowej prąd spawania - wyjście analogowe (V)
    - ``AOIndex``: Port wyjścia analogowego napięcia spawania"

Ustawianie prądu spawania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionchanged:: python SDK-v2.0.5
    
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeldingSetCurrent(ioType, current, AOIndex, blend)``"
    "Opis", "Ustawianie prądu spawania"
    "Parametry wymagane", "- ``ioType``: Typ 0-IO kontrolera; 1-rozszerzone IO
    - ``current``: Wartość prądu spawania (A)
    - ``AOIndex``: Port wyjścia analogowego prądu spawania skrzynki kontrolnej (0-1)
    - ``blend``: Czy wygładzać 0-nie, 1-tak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie napięcia spawania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionchanged:: python SDK-v2.0.5
    
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeldingSetVoltage(ioType, voltage, AOIndex, blend)``"
    "Opis", "Ustawianie napięcia spawania"
    "Parametry wymagane", "- ``ioType``: Typ 0-IO kontrolera; 1-rozszerzone IO
    - ``voltage``: Wartość napięcia spawania (V)
    - ``AOIndex``: Port wyjścia analogowego prądu spawania skrzynki kontrolnej (0-1)
    - ``blend``: Czy wygładzać 0-nie, 1-tak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie parametrów ruchu wahadłowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionchanged:: python SDK-v2.1.2
    
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeaveSetPara(weaveNum, weaveType, weaveFrequency, weaveIncStayTime, weaveRange, weaveLeftRange, weaveRightRange, additionalStayTime, weaveLeftStayTime, weaveRightStayTime, weaveCircleRadio, weaveStationary, weaveYawAngle, weaveRotAngle)``"
    "Opis", "Ustawianie parametrów ruchu wahadłowego"
    "Parametry wymagane", "- ``weaveNum``: Numer konfiguracji parametrów spawania wahadłowego
    - ``weaveType``: Typ wahadła 0-płaskie wahadło trójkątne; 1-pionowe wahadło trójkątne typu L; 2-kołowe wahadło zgodne z ruchem wskazówek zegara; 3-kołowe wahadło przeciwnie do ruchu wskazówek zegara; 4-płaskie wahadło sinusoidalne; 5-pionowe wahadło sinusoidalne typu L; 6-pionowe wahadło trójkątne; 7-pionowe wahadło sinusoidalne
    - ``weaveFrequency``: Częstotliwość wahadła (Hz)
    - ``weaveIncStayTime``: Tryb oczekiwania 0-cykl nie zawiera czasu oczekiwania; 1-cykl zawiera czas oczekiwania
    - ``weaveRange``: Amplituda wahadła (mm)
    - ``weaveLeftRange``: Długość lewej cięciwy w pionowym wahadle trójkątnym (mm)
    - ``weaveRightRange``: Długość prawej cięciwy w pionowym wahadle trójkątnym (mm)
    - ``additionalStayTime``: Czas postoju w punkcie wierzchołkowym pionowego wahadła trójkątnego (ms)
    - ``weaveLeftStayTime``: Czas postoju po lewej stronie wahadła (ms)
    - ``weaveRightStayTime``: Czas postoju po prawej stronie wahadła (ms)
    - ``weaveCircleRadio``: Wahadło kołowe - współczynnik powrotu (0-100%)
    - ``weaveStationary``: Oczekiwanie w pozycji wahadła, 0-ruch kontynuowany w czasie oczekiwania; 1-pozycja nieruchoma w czasie oczekiwania"
    "Parametry domyślne", "- ``weaveYawAngle``: Azymut kierunku wahadła (obrót wokół osi Z wahadła), jednostka °, domyślnie 0
    - ``weaveRotAngle``: Azymut kierunku wahadła (obrót wokół osi X wahadła), jednostka °, domyślnie 0"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Przykład kodu ustawiania parametrów spawania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    robot.WeldingSetProcessParam(1, 177, 27, 1000, 178, 28, 176, 26, 1000)
    robot.WeldingSetProcessParam(2, 188, 28, 555, 199, 29, 133, 23, 333)
    start_current = 0
    start_voltage = 0
    start_time = 0
    weld_current = 0
    weld_voltage = 0
    end_current = 0
    end_voltage = 0
    end_time = 0
    error, start_current, start_voltage, start_time, weld_current, weld_voltage, end_current,end_voltage, end_time = robot.WeldingGetProcessParam(1)
    print(f"the Num 1 process param is {start_current} {start_voltage} {start_time} {weld_current} {weld_voltage} {end_current} {end_voltage} {end_time}")
    error, start_current, start_voltage, start_time, weld_current, weld_voltage, end_current,end_voltage, end_time = robot.WeldingGetProcessParam(2)
    print(f"the Num 2 process param is {start_current} {start_voltage} {start_time} {weld_current} {weld_voltage} {end_current} {end_voltage} {end_time}")
    rtn = robot.WeldingSetCurrentRelation(0, 400, 0, 10, 0)
    print(f"WeldingSetCurrentRelation rtn is: {rtn}")
    rtn = robot.WeldingSetVoltageRelation(0, 40, 0, 10, 1)
    print(f"WeldingSetVoltageRelation rtn is: {rtn}")
    current_min = 0
    current_max = 0
    vol_min = 0
    vol_max = 0
    output_vmin = 0
    output_vmax = 0
    cur_index = 0
    vol_index = 0
    rtn,current_min, current_max, output_vmin, output_vmax, cur_index = robot.WeldingGetCurrentRelation()
    print(f"WeldingGetCurrentRelation rtn is: {rtn}")
    print(f"current min {current_min} current max {current_max} output vol min {output_vmin} output vol max {output_vmax}")
    rtn,vol_min, vol_max, output_vmin, output_vmax, vol_index = robot.WeldingGetVoltageRelation()
    print(f"WeldingGetVoltageRelation rtn is: {rtn}")
    print(f"vol min {vol_min} vol max {vol_max} output vol min {output_vmin} output vol max {output_vmax}")
    rtn = robot.WeldingSetCurrent(1, 100, 0, 0)
    print(f"WeldingSetCurrent rtn is: {rtn}")
    time.sleep(3)
    rtn = robot.WeldingSetVoltage(1, 10, 0, 0)
    print(f"WeldingSetVoltage rtn is: {rtn}")
    rtn = robot.WeaveSetPara(0, 0, 2.000000, 0, 10.000000, 0.000000, 0.000000, 0, 0, 0, 0, 0,0.0, 60.000000)
    print(f"rtn is: {rtn}")
    robot.WeaveOnlineSetPara(0, 0, 1, 0, 20, 0, 0, 0, 0)
    rtn = robot.WeldingSetCheckArcInterruptionParam(1, 200)
    print(f"WeldingSetCheckArcInterruptionParam {rtn}")
    rtn = robot.WeldingSetReWeldAfterBreakOffParam(1, 5.7, 98.2, 0)
    print(f"WeldingSetReWeldAfterBreakOffParam {rtn}")
    enable = 0
    length = 0
    velocity = 0
    move_type = 0
    check_enable = 0
    arc_interrupt_time_length = 0
    rtn,check_enable, arc_interrupt_time_length = robot.WeldingGetCheckArcInterruptionParam()
    print(f"WeldingGetCheckArcInterruptionParam checkEnable {check_enable} arcInterruptTimeLength {arc_interrupt_time_length}")
    rtn,enable, length, velocity, move_type = robot.WeldingGetReWeldAfterBreakOffParam()
    print(f"WeldingGetReWeldAfterBreakOffParam enable = {enable}, length = {length}, velocity = {velocity}, moveType = {move_type}")
    robot.SetWeldMachineCtrlModeExtDoNum(17)
    for i in range(5):
        robot.SetWeldMachineCtrlMode(0)
        time.sleep(1)
        robot.SetWeldMachineCtrlMode(1)
        time.sleep(1)
    robot.CloseRPC()

Natychmiastowe ustawianie parametrów ruchu wahadłowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.1
    
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeaveOnlineSetPara (weaveNum, weaveType, weaveFrequency, weaveIncStayTime, weaveRange, weaveLeftStayTime, weaveRightStayTime, weaveCircleRadio, weaveStationary)``"
    "Opis", "Natychmiastowe ustawianie parametrów ruchu wahadłowego"
    "Parametry wymagane", "- ``weaveNum``: Numer konfiguracji parametrów spawania wahadłowego
    - ``weaveType``: Typ wahadła 0-płaskie wahadło trójkątne; 1-pionowe wahadło trójkątne typu L; 2-kołowe wahadło zgodne z ruchem wskazówek zegara; 3-kołowe wahadło przeciwnie do ruchu wskazówek zegara; 4-płaskie wahadło sinusoidalne; 5-pionowe wahadło sinusoidalne typu L; 6-pionowe wahadło trójkątne; 7-pionowe wahadło sinusoidalne
    - ``weaveFrequency``: Częstotliwość wahadła (Hz)
    - ``weaveIncStayTime``: Tryb oczekiwania 0-cykl nie zawiera czasu oczekiwania; 1-cykl zawiera czas oczekiwania
    - ``weaveRange``: Amplituda wahadła (mm)
    - ``weaveLeftStayTime``: Czas postoju po lewej stronie wahadła (ms)
    - ``weaveRightStayTime``: Czas postoju po prawej stronie wahadła (ms)
    - ``weaveCircleRadio``: Wahadło kołowe - współczynnik powrotu (0-100%)
    - ``weaveStationary``: Oczekiwanie w pozycji wahadła, 0-ruch kontynuowany w czasie oczekiwania; 1-pozycja nieruchoma w czasie oczekiwania"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Pobieranie parametrów wykrywania nieoczekiwanego przerwania łuku spawalniczego robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeldingGetCheckArcInterruptionParam()``"
    "Opis", "Pobieranie parametrów wykrywania nieoczekiwanego przerwania łuku spawalniczego robota"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode 
    - ``checkEnable``: Czy włączyć wykrywanie; 0-nie; 1-tak
    - ``arcInterruptTimeLength``: Czas potwierdzenia przerwania łuku (ms)"

Ustawianie parametrów wykrywania nieoczekiwanego przerwania łuku spawalniczego robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeldingSetCheckArcInterruptionParam(checkEnable, arcInterruptTimeLength)``"
    "Opis", "Ustawianie parametrów wykrywania nieoczekiwanego przerwania łuku spawalniczego robota"
    "Parametry wymagane", "- ``checkEnable``: Czy włączyć wykrywanie; 0-nie; 1-tak
    - ``arcInterruptTimeLength``: Czas potwierdzenia przerwania łuku (ms)"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode "

Pobieranie parametrów wznawiania spawania po przerwaniu robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeldingGetReWeldAfterBreakOffParam()``"
    "Opis", "Pobieranie parametrów wznawiania spawania po przerwaniu robota"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode 
    - ``enable``: Czy włączyć wznawianie spawania po przerwaniu
    - ``length``: Długość zakładki spoiny (mm)
    - ``velocity``: Procent prędkości powrotu robota do punktu ponownego zapłonu łuku (0-100)
    - ``moveType``: Sposób ruchu robota do punktu ponownego zapłonu łuku; 0-LIN; 1-PTP"

Ustawianie parametrów wznawiania spawania po przerwaniu robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeldingSetReWeldAfterBreakOffParam(enable, length, velocity, moveType)``"
    "Opis", "Ustawianie parametrów wznawiania spawania po przerwaniu robota"
    "Parametry wymagane", "- ``enable``: Czy włączyć wznawianie spawania po przerwaniu
    - ``length``: Długość zakładki spoiny (mm)
    - ``velocity``: Procent prędkości powrotu robota do punktu ponownego zapłonu łuku (0-100)
    - ``moveType``: Sposób ruchu robota do punktu ponownego zapłonu łuku; 0-LIN; 1-PTP"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode "

Ustawianie rozszerzonego portu DO trybu sterowania spawarką
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetWeldMachineCtrlModeExtDoNum(DONum)``"
    "Opis", "Ustawianie rozszerzonego portu DO trybu sterowania spawarką"
    "Parametry wymagane", "- ``DONum``: Port DO trybu sterowania spawarką (0-127)"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode" 

Ustawianie trybu sterowania spawarką
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetWeldMachineCtrlMode(mode, ioType)``"
    "Opis", "Ustawianie trybu sterowania spawarką"
    "Parametry wymagane", "
    - ``ioType``: Typ sterowania; 0-IO skrzynki kontrolnej; 1-protokół komunikacji cyfrowej (UDP); 2-protokół komunikacji cyfrowej (ModbusTCP)
    - ``mode``: Tryb sterowania spawarką; 0-jednowartościowy"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode" 

Pobieranie Trybu Sterowania Spawarką
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v3.9.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetWeldMachineCtrlMode(self)``"
    "Opis", "Pobiera tryb sterowania spawarką"
    "Parametry Wymagane", "
    - ``mode``: Tryb sterowania spawarką; 0-tryb jednopokrętłowy DC; 1-tryb jednopokrętłowy impulsowy; 2-tryb JOB; 3-tryb sterowania lokalnego; 4-tryb oddzielny; 5-tryb CC/CV; 6-TIG; 7-CMT
    "
    "Parametry Domyślne", "Brak"
    "Wartość Zwracana", "Kod błędu, 0-sukces; niezerowy-błąd" 

Przykład Kodu Pobierania Trybu Sterowania Spawarką
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v3.9.8

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time

    def main():
        robot = Robot.RPC('192.168.58.2')
        time.sleep(0.5)  

        robot.WeldingSetProcessParam(1, 177, 27, 1000, 178, 28, 176, 26, 1000)
        robot.WeldingSetProcessParam(2, 188, 28, 555, 199, 29, 133, 23, 333)

        start_current = 0
        start_voltage = 0
        start_time = 0
        weld_current = 0
        weld_voltage = 0
        end_current = 0
        end_voltage = 0
        end_time = 0

        error, start_current, start_voltage, start_time, weld_current, weld_voltage, end_current,end_voltage, end_time = robot.WeldingGetProcessParam(1)
        print(f"the Num 1 process param is {start_current} {start_voltage} {start_time} {weld_current} {weld_voltage} {end_current} {end_voltage} {end_time}")

        error, start_current, start_voltage, start_time, weld_current, weld_voltage, end_current,end_voltage, end_time = robot.WeldingGetProcessParam(2)
        print(f"the Num 2 process param is {start_current} {start_voltage} {start_time} {weld_current} {weld_voltage} {end_current} {end_voltage} {end_time}")

        rtn = robot.WeldingSetCurrentRelation(0, 400, 0, 10, 0)
        print(f"WeldingSetCurrentRelation rtn is: {rtn}")

        rtn = robot.WeldingSetVoltageRelation(0, 40, 0, 10, 1)
        print(f"WeldingSetVoltageRelation rtn is: {rtn}")

        current_min = 0
        current_max = 0
        vol_min = 0
        vol_max = 0
        output_vmin = 0
        output_vmax = 0
        cur_index = 0
        vol_index = 0

        rtn,current_min, current_max, output_vmin, output_vmax, cur_index = robot.WeldingGetCurrentRelation()
        print(f"WeldingGetCurrentRelation rtn is: {rtn}")
        print(
            f"current min {current_min} current max {current_max} output vol min {output_vmin} output vol max {output_vmax}")

        rtn,vol_min, vol_max, output_vmin, output_vmax, vol_index = robot.WeldingGetVoltageRelation()
        print(f"WeldingGetVoltageRelation rtn is: {rtn}")
        print(f"vol min {vol_min} vol max {vol_max} output vol min {output_vmin} output vol max {output_vmax}")

        rtn = robot.WeldingSetCurrent(1, 100, 0, 0)
        print(f"WeldingSetCurrent rtn is: {rtn}")

        time.sleep(3)

        rtn = robot.WeldingSetVoltage(1, 10, 0, 0)
        print(f"WeldingSetVoltage rtn is: {rtn}")

        rtn = robot.WeaveSetPara(0, 0, 2.000000, 0, 10.000000, 0.000000, 0.000000, 0, 0, 0, 0, 0,0.0, 60.000000)
        print(f"rtn is: {rtn}")

        robot.WeaveOnlineSetPara(0, 0, 1, 0, 20, 0, 0, 0, 0)

        rtn = robot.WeldingSetCheckArcInterruptionParam(1, 200)
        print(f"WeldingSetCheckArcInterruptionParam {rtn}")

        rtn = robot.WeldingSetReWeldAfterBreakOffParam(1, 5.7, 98.2, 0)
        print(f"WeldingSetReWeldAfterBreakOffParam {rtn}")

        enable = 0
        length = 0
        velocity = 0
        move_type = 0
        check_enable = 0
        arc_interrupt_time_length = 0

        rtn,check_enable, arc_interrupt_time_length = robot.WeldingGetCheckArcInterruptionParam()
        print(
            f"WeldingGetCheckArcInterruptionParam checkEnable {check_enable} arcInterruptTimeLength {arc_interrupt_time_length}")

        rtn,enable, length, velocity, move_type = robot.WeldingGetReWeldAfterBreakOffParam()
        print(
            f"WeldingGetReWeldAfterBreakOffParam enable = {enable}, length = {length}, velocity = {velocity}, moveType = {move_type}")

        robot.SetWeldMachineCtrlModeExtDoNum(17)
        for i in range(5):
            robot.SetWeldMachineCtrlMode(0,1)
            error,getCtrlMode=robot.GetWeldMachineCtrlMode
            print(f"GetWeldMachineCtrlMode = {getCtrlMode}")
            time.sleep(1)
            robot.SetWeldMachineCtrlMode(1,1)
            error, getCtrlMode = robot.GetWeldMachineCtrlMode
            print(f"GetWeldMachineCtrlMode = {getCtrlMode}")
            time.sleep(1)

        robot.CloseRPC()    

Rozpoczęcie spawania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ARCStart(ioType, arcNum, timeout)``"
    "Opis", "Rozpoczęcie spawania"
    "Parametry wymagane", "- ``ioType``: Typ IO 0-IO kontrolera; 1-rozszerzone IO
    - ``arcNum``: Numer pliku konfiguracyjnego spawarki
    - ``timeout``: Czas timeout zapłonu łuku"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Zakończenie spawania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.1
    
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ARCEnd(ioType, arcNum, timeout)``"
    "Opis", "Zakończenie spawania"
    "Parametry wymagane", "- ``ioType``: Typ 0-IO kontrolera; 1-rozszerzone IO
    - ``arcNum``: Numer pliku konfiguracyjnego spawarki
    - ``timeout``: Czas timeout zapłonu łuku"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Rozpoczęcie ruchu wahadłowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.1
    
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeaveStart(weaveNum)``"
    "Opis", "Rozpoczęcie ruchu wahadłowego"
    "Parametry wymagane", "- ``weaveNum``: Typ 0-IO kontrolera; 1-rozszerzone IO"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Zakończenie ruchu wahadłowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.1
    
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeaveEnd(weaveNum)``"
    "Opis", "Zakończenie ruchu wahadłowego"
    "Parametry wymagane", "- ``weaveNum``: Numer konfiguracji parametrów spawania wahadłowego"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Podawanie drutu do przodu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.1
    
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetForwardWireFeed(ioType, wireFeed)``"
    "Opis", "Podawanie drutu do przodu"
    "Parametry wymagane", "- ``ioType``: 0-IO kontrolera; 1-rozszerzone IO
    - ``wireFeed``: Sterowanie podawaniem drutu 0-zatrzymaj podawanie; 1-podawaj"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Podawanie drutu do tyłu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.1
    
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetReverseWireFeed(ioType, wireFeed)``"
    "Opis", "Podawanie drutu do tyłu"
    "Parametry wymagane", "- ``ioType``: 0-IO kontrolera; 1-rozszerzone IO
    - ``wireFeed``: Sterowanie podawaniem drutu 0-zatrzymaj podawanie; 1-podawaj"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Podawanie gazu osłonowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.1
    
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetAspirated(ioType, airControl)``"
    "Opis", "Podawanie gazu osłonowego"
    "Parametry wymagane", "- ``ioType``: 0-IO kontrolera; 1-rozszerzone IO
    - ``airControl``: Sterowanie podawaniem gazu 0-zatrzymaj podawanie; 1-podawaj"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie wznowienia spawania po przerwaniu robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeldingStartReWeldAfterBreakOff()``"
    "Opis", "Ustawianie wznowienia spawania po przerwaniu robota"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode "

Ustawianie wyjścia ze spawania po przerwaniu robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeldingAbortWeldAfterBreakOff()``"
    "Opis", "Ustawianie wyjścia ze spawania po przerwaniu robota"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode "

Przykład kodu sterowania spawaniem robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    robot.SetForwardWireFeed(0, 1)
    time.sleep(1)
    robot.SetForwardWireFeed(0, 0)
    robot.SetReverseWireFeed(0, 1)
    time.sleep(1)
    robot.SetReverseWireFeed(0, 0)
    robot.SetAspirated(0, 1)
    time.sleep(1)
    robot.SetAspirated(0, 0)
    robot.WeldingSetCurrent(1, 230, 0, 0)
    robot.WeldingSetVoltage(1, 24, 0, 1)
    p1Desc = [228.879, -503.594, 453.984, -175.580, 8.293, 171.267]
    p1Joint = [102.700, -85.333, 90.518, -102.365, -83.932, 22.134]
    p2Desc = [-333.302, -435.580, 449.866, -174.997, 2.017, 109.815]
    p2Joint = [41.862, -85.333, 90.526, -100.587, -90.014, 22.135]
    exaxisPos = [0, 0, 0, 0]
    offdese = [0, 0, 0, 0, 0, 0]
    robot.MoveJ(joint_pos=p1Joint, tool=13, user=0)
    robot.ARCStart(1, 0, 10000)
    robot.WeaveStart(0)
    robot.MoveL(desc_pos=p2Desc, tool=13, user=0)
    robot.ARCEnd(1, 0, 10000)
    robot.WeaveEnd(0)
    robot.WeldingStartReWeldAfterBreakOff()
    robot.WeldingAbortWeldAfterBreakOff()
    robot.CloseRPC()

Rozpoczęcie spawania segmentowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.1
    
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SegmentWeldStart(startDesePos,  endDesePos, startJPos, endJPos, weldLength, noWeldLength, weldIOType, arcNum, weldTimeout, isWeave,weaveNum,tool,user,vel=20.0, acc=0.0, ovl=100.0, blendR=-1.0,exaxis_pos=[0.0, 0.0, 0.0, 0.0],  search=0, offset_flag=0, offset_pos=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0])``"
    "Opis", "Rozpoczęcie spawania segmentowego"
    "Parametry wymagane", "- ``startDesePos``: Początkowa poza kartezjańska, jednostka [mm][°]
    - ``endDesePos``: Docelowa poza kartezjańska, jednostka [mm][°]
    - ``startJPos``: Początkowa pozycja przegubów, jednostka [°] 
    - ``endJPos``: Docelowa pozycja przegubów, jednostka [°]  
    - ``weldLength``: Długość spawania, jednostka [mm] 
    - ``noWeldLength``: Długość niespawana, jednostka [mm] 
    - ``weldIOType``: Typ IO spawania (0-IO skrzynki kontrolnej; 1-rozszerzone IO) 
    - ``arcNum``: Numer pliku konfiguracyjnego spawarki
    - ``weldTimeout``: Czas timeout wygaszenia łuku 
    - ``isWeave``: Spawanie False-nie spawaj 
    - ``weaveNum``: Numer konfiguracji parametrów spawania wahadłowego 
    - ``tool``: Numer narzędzia, [0~14]
    - ``user``: Numer przedmiotu, [0~14]"
    "Parametry domyślne", "- ``vel``: Procent prędkości, [0~100] domyślnie 20.0
    - ``acc``: Przyspieszenie [0~100] tymczasowo niedostępne domyślnie 0.0
    - ``ovl``: Współczynnik skalowania prędkości, [0~100] domyślnie 100.0
    - ``blendR``: [-1.0]-ruch do pozycji (blokujący), [0~1000]-promień wygładzania (nieblokujący), jednostka [mm] domyślnie -1.0
    - ``exaxis_pos``: Pozycja osi zewnętrznej 1 ~ pozycja osi zewnętrznej 4 domyślnie [0.0,0.0,0.0,0.0]
    - ``search``: [0]-brak poszukiwania pozycji drutu, [1]-poszukiwanie pozycji drutu
    - ``offset_flag``: [0]-brak przesunięcia, [1]-przesunięcie w układzie przedmiotu/bazowym, [2]-przesunięcie w układzie narzędzia domyślnie 0
    - ``offset_pos``: Wartość przesunięcia pozy, jednostka [mm][°] domyślnie [0.0,0.0,0.0,0.0,0.0,0.0]"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode"

Przykład kodu spawania segmentowego robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    robot.WeldingSetCurrent(1, 230, 0, 0)
    robot.WeldingSetVoltage(1, 24, 0, 1)
    p1Desc = [228.879, -503.594, 453.984, -175.580, 8.293, 171.267]
    p1Joint = [102.700, -85.333, 90.518, -102.365, -83.932, 22.134]
    p2Desc = [-333.302, -435.580, 449.866, -174.997, 2.017, 109.815]
    p2Joint = [41.862, -85.333, 90.526, -100.587, -90.014, 22.135]
    exaxisPos = [0, 0, 0, 0]
    offdese = [0, 0, 0, 0, 0, 0]
    rtn = robot.SegmentWeldStart(p1Desc, p2Desc, p1Joint, p2Joint, 20, 20, 0, 0, 5000, 0, 0, 0, 0)
    print(f"SegmentWeldStart rtn is {rtn}")
    robot.CloseRPC()

Rozpoczęcie symulacji ruchu wahadłowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeaveStartSim(weaveNum)``"
    "Opis", "Rozpoczęcie symulacji ruchu wahadłowego"
    "Parametry wymagane", "- ``weaveNum``: Numer parametrów wahadła"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode" 

Zakończenie symulacji ruchu wahadłowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeaveEndSim(weaveNum)``"
    "Opis", "Zakończenie symulacji ruchu wahadłowego"
    "Parametry wymagane", "- ``weaveNum``: Numer parametrów wahadła"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode" 

Rozpoczęcie ostrzegania o wykrywaniu trajektorii (bez ruchu)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeaveInspectStart(weaveNum)``"
    "Opis", "Rozpoczęcie ostrzegania o wykrywaniu trajektorii (bez ruchu)"
    "Parametry wymagane", "- ``weaveNum``: Numer parametrów wahadła"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode" 

Zakończenie ostrzegania o wykrywaniu trajektorii (bez ruchu)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeaveInspectEnd(weaveNum)``"
    "Opis", "Zakończenie ostrzegania o wykrywaniu trajektorii (bez ruchu)"
    "Parametry wymagane", "- ``weaveNum``: Numer parametrów wahadła"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode" 

Rozpoczęcie zmiany parametrów wahadła
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeaveChangeStart(weaveChangeFlag, weaveNum, velStart, velEnd)``"
    "Opis", "Rozpoczęcie zmiany parametrów wahadła"
    "Parametry wymagane", "- ``weaveChangeFlag``: Numer wahadła 1-zmiana parametrów wahadła; 2-zmiana parametrów wahadła + prędkości spawania
    - ``weaveNum``: Numer wahadła
    - ``velStart``: Prędkość początkowa spawania, (cm/min)
    - ``velEnd``: Prędkość końcowa spawania, (cm/min)"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode "

Przykład kodu spawania ze zmianą parametrów wahadła robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    p1Desc = [228.879, -503.594, 453.984, -175.580, 8.293, 171.267]
    p1Joint = [102.700, -85.333, 90.518, -102.365, -83.932, 22.134]
    p2Desc = [-333.302, -435.580, 449.866, -174.997, 2.017, 109.815]
    p2Joint = [41.862, -85.333, 90.526, -100.587, -90.014, 22.135]
    exaxisPos = [0, 0, 0, 0]
    offdese = [0, 0, 0, 0, 0, 0]
    robot.MoveJ(joint_pos= p1Joint,tool= 13,user= 0)
    robot.WeaveStartSim(0)
    robot.MoveL(desc_pos= p2Desc,tool= 13,user= 0)
    robot.WeaveEndSim(0)
    robot.MoveJ(joint_pos= p1Joint,tool= 13,user= 0)
    robot.WeaveInspectStart(0)
    robot.MoveL(desc_pos= p2Desc,tool= 13,user= 0,)
    robot.WeaveInspectEnd(0)
    robot.WeldingSetVoltage(1, 19, 0, 0)
    robot.WeldingSetCurrent(1, 190, 0, 0)
    robot.MoveL(desc_pos= p1Desc,tool= 1,user= 1,vel= 100,acc= 100,ovl= 50)
    robot.ARCStart(1, 0, 10000)
    robot.ArcWeldTraceControl(1, 0, 1, 0.06, 5, 5, 60, 1, 0.06, 5, 5, 80, 0, 0, 4, 1, 10, 0, 0)
    robot.WeaveStart(0)
    robot.WeaveChangeStart(1, 0, 50, 30)
    robot.MoveL(desc_pos= p2Desc,tool= 1,user= 1,vel= 100)
    robot.WeaveChangeEnd()
    robot.WeaveEnd(0)
    robot.ArcWeldTraceControl(0, 0, 1, 0.06, 5, 5, 60, 1, 0.06, 5, 5, 80, 0, 0, 4, 1, 10, 0, 0)
    robot.ARCEnd(1, 0, 10000)
    robot.CloseRPC()

Zakończenie zmiany parametrów wahadła
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.9-3.7.9

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeaveChangeEnd()``"
    "Opis", "Zakończenie zmiany parametrów wahadła"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode "

Rozszerzone IO - konfiguracja sygnału detekcji gazu spawarki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetAirControlExtDoNum(DONum)``"
    "Opis", "Rozszerzone IO - konfiguracja sygnału detekcji gazu spawarki"
    "Parametry wymagane", "
    - ``DONum``: Rozszerzony numer DO sygnału detekcji gazu
    "
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode" 

Rozszerzone IO - konfiguracja sygnału zapłonu łuku spawarki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetArcStartExtDoNum(DONum)``"
    "Opis", "Rozszerzone IO - konfiguracja sygnału zapłonu łuku spawarki"
    "Parametry wymagane", "
    - ``DONum``: Rozszerzony numer DO sygnału detekcji gazu
    "
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode" 
        
Rozszerzone IO - konfiguracja sygnału podawania drutu do tyłu spawarki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetWireReverseFeedExtDoNum(DONum)``"
    "Opis", "Rozszerzone IO - konfiguracja sygnału podawania drutu do tyłu spawarki"
    "Parametry wymagane", "
    - ``DONum``: Rozszerzony numer DO sygnału detekcji gazu
    "
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode" 
        
Rozszerzone IO - konfiguracja sygnału podawania drutu do przodu spawarki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetWireForwardFeedExtDoNum(DONum)``"
    "Opis", "Rozszerzone IO - konfiguracja sygnału podawania drutu do przodu spawarki"
    "Parametry wymagane", "
    - ``DONum``: Rozszerzony numer DO sygnału detekcji gazu
    "
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode" 
        
Rozszerzone IO - konfiguracja sygnału pomyślnego zapłonu łuku spawarki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetArcDoneExtDiNum(DINum)``"
    "Opis", "Rozszerzone IO - konfiguracja sygnału pomyślnego zapłonu łuku spawarki"
    "Parametry wymagane", "
    - ``DINum``: Rozszerzony numer DI sygnału gotowości spawarki
    "
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode" 
        
Rozszerzone IO - konfiguracja sygnału gotowości spawarki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetArcDoneExtDiNum(DINum)``"
    "Opis", "Rozszerzone IO - konfiguracja sygnału gotowości spawarki"
    "Parametry wymagane", "
    - ``DINum``: Rozszerzony numer DI sygnału gotowości spawarki
    "
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode" 
        
Rozszerzone IO - konfiguracja sygnału wznowienia po przerwaniu spawania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetExtDIWeldBreakOffRecover(reWeldDINum, abortWeldDINum)``"
    "Opis", "Rozszerzone IO - konfiguracja sygnału wznowienia po przerwaniu spawania"
    "Parametry wymagane", "
    - ``reWeldDINum``: Rozszerzony numer DI sygnału wznowienia spawania po przerwaniu
    - ``abortWeldDINum``: Rozszerzony numer DI sygnału wyjścia ze spawania po przerwaniu
    "
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode" 

Przykład kodu konfiguracji rozszerzonych sygnałów IO spawania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    rtn = robot.SetArcStartExtDoNum(10)
    print(f"SetArcStartExtDoNum rtn is {rtn}")
    rtn = robot.SetAirControlExtDoNum(20)
    print(f"SetAirControlExtDoNum rtn is {rtn}")
    rtn = robot.SetWireForwardFeedExtDoNum(30)
    print(f"SetWireForwardFeedExtDoNum rtn is {rtn}")
    rtn = robot.SetWireReverseFeedExtDoNum(40)
    rtn = robot.SetWeldReadyExtDiNum(50)
    print(f"SetWeldReadyExtDiNum rtn is {rtn}")
    rtn = robot.SetArcDoneExtDiNum(60)
    print(f"SetArcDoneExtDiNum rtn is {rtn}")
    rtn = robot.SetExtDIWeldBreakOffRecover(70, 80)
    print(f"SetExtDIWeldBreakOffRecover rtn is {rtn}")
    rtn = robot.SetWireSearchExtDIONum(0, 1)
    print(f"SetWireSearchExtDIONum rtn is {rtn}")
    robot.CloseRPC()

Pobieranie Konfiguracji Funkcji Rozszerzonego DI
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-V3.9.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetExtDIConfig(self)``"
    "Opis", "Pobiera konfigurację funkcji rozszerzonego DI"
    "Parametry Wymagane", "
    - ``DIConfig``: Konfiguracja wejścia rozszerzonego DI; DIConfig[0]-port rozszerzonego DI gotowości spawarki
    - ``DIConfig[1]``: Port rozszerzonego DI pomyślnego rozpoczęcia łuku
    - ``DIConfig[2]``: Port rozszerzonego DI wznowienia przerwania spawania
    - ``DIConfig[3]``: Port rozszerzonego DI wyjścia z przerwania spawania
    - ``DIConfig[4]``: Port rozszerzonego DI pomyślnego wyszukiwania drutu
    - ``DIConfig[5]``: Port rozszerzonego DI statusu pracy spawarki laserowej
    - ``DIConfig[6]``: Port rozszerzonego DI statusu awarii spawarki laserowej
    - ``DIConfig[7-15]``: Zarezerwowane
    "
    "Parametry Domyślne", "Brak"
    "Wartość Zwracana", "Kod błędu, 0-sukces; niezerowy-błąd" 

Pobieranie Konfiguracji Funkcji Rozszerzonego DO
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-V3.9.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetExtDOConfig(self)``"
    "Opis", "Pobiera konfigurację funkcji rozszerzonego DO"
    "Parametry Wymagane", "
    - ``DOConfig``: Konfiguracja wyjścia rozszerzonego DO; DOConfig[0]-port rozszerzonego DO rozpoczęcia łuku spawarki
    - ``DOConfig[1]``: Port rozszerzonego DO detekcji gazu
    - ``DOConfig[2]``: Port rozszerzonego DO podawania drutu do przodu
    - ``DOConfig[3]``: Port rozszerzonego DO podawania drutu do tyłu
    - ``DOConfig[4]``: Port rozszerzonego DO wyszukiwania drutu
    - ``DOConfig[5]``: Port rozszerzonego DO trybu sterowania spawarką
    - ``DOConfig[6]``: Port rozszerzonego DO włączenia spawarki laserowej
    - ``DOConfig[7]``: Port rozszerzonego DO uruchomienia spawarki laserowej (emisja lasera)
    - ``DOConfig[8]``: Port rozszerzonego DO resetowania spawarki laserowej
    - ``DOConfig[9-15]``: Zarezerwowane
    "
    "Parametry Domyślne", "Brak"
    "Wartość Zwracana", "Kod błędu, 0-sukces; niezerowy-błąd" 

Przykład Kodu Pobierania Rozszerzonego DI/DO
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-V3.9.8

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time

    def main():
        robot = Robot.RPC('192.168.58.2')
        time.sleep(0.5)  

    rtn = robot.SetArcStartExtDoNum(10)
        print(f"SetArcStartExtDoNum rtn is {rtn}")

        rtn = robot.SetAirControlExtDoNum(20)
        print(f"SetAirControlExtDoNum rtn is {rtn}")

        rtn = robot.SetWireForwardFeedExtDoNum(30)
        print(f"SetWireForwardFeedExtDoNum rtn is {rtn}")

        rtn = robot.SetWireReverseFeedExtDoNum(40)
        print(f"SetWireReverseFeedExtDoNum rtn is {rtn}")

        rtn = robot.SetWeldReadyExtDiNum(50)
        print(f"SetWeldReadyExtDiNum rtn is {rtn}")

        rtn = robot.SetArcDoneExtDiNum(60)
        print(f"SetArcDoneExtDiNum rtn is {rtn}")

        rtn = robot.SetExtDIWeldBreakOffRecover(70, 80)
        print(f"SetExtDIWeldBreakOffRecover rtn is {rtn}")

        rtn = robot.SetWireSearchExtDIONum(0, 1)
        print(f"SetWireSearchExtDIONum rtn is {rtn}")

        rtn, DIConfig = robot.GetExtDIConfig()
        print(f"GetExtDIConfig rtn is {rtn}")
        print(f"welder ready {DIConfig[0]}")
        print(f"arc done {DIConfig[1]}")
        print(f"reweld start {DIConfig[2]}")
        print(f"abort reweld {DIConfig[3]}")
        print(f"wiresearch done {DIConfig[4]}")
        print(f"Laser welding State {DIConfig[5]}")
        print(f"laser welding error state {DIConfig[6]}")

        rtn, DOConfig = robot.GetExtDOConfig()
        print(f"GetExtDOConfig rtn is {rtn}")
        print(f"Arc Start {DOConfig[0]}")
        print(f"Air Test {DOConfig[1]}")
        print(f"Wire forward {DOConfig[2]}")
        print(f"Wire Inverse {DOConfig[3]}")
        print(f"wiresearch {DOConfig[4]}")
        print(f"Weld Mode {DOConfig[5]}")
        print(f"laser Enable {DOConfig[6]}")
        print(f"Laser On {DOConfig[7]}")
        print(f"Laser Reset Error {DOConfig[8]}")

        robot.CloseRPC()

Sterowanie śledzeniem łuku
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.9-3.7.9

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ArcWeldTraceControl(flag,delaytime, isLeftRight, klr, tStartLr, stepMaxLr, sumMaxLr, isUpLow, kud, tStartUd, stepMaxUd, sumMaxUd, axisSelect, referenceType, referSampleStartUd, referSampleCountUd, referenceCurrent, offsetType, offsetParameter)``"
    "Opis", "Sterowanie śledzeniem łuku"
    "Parametry wymagane", "- ``flag``: Przełącznik, 0-wył.; 1-wł.
    - ``delayTime``: Czas opóźnienia, jednostka ms
    - ``isLeftRight``: Kompensacja odchylenia lewo-prawo 0-wyłączona, 1-włączona
    - ``klr``: Współczynnik regulacji lewo-prawo (czułość)
    - ``tStartLr``: Czas rozpoczęcia kompensacji lewo-prawo cyc
    - ``stepMaxLr``: Maksymalna wielkość kompensacji na raz lewo-prawo mm
    - ``sumMaxLr``: Maksymalna całkowita wielkość kompensacji lewo-prawo mm
    - ``isUpLow``: Kompensacja odchylenia góra-dół 0-wyłączona, 1-włączona
    - ``kud``: Współczynnik regulacji góra-dół (czułość)
    - ``tStartUd``: Czas rozpoczęcia kompensacji góra-dół cyc
    - ``stepMaxUd``: Maksymalna wielkość kompensacji na raz góra-dół mm
    - ``sumMaxUd``: Maksymalna całkowita wielkość kompensacji góra-dół
    - ``axisSelect``: Wybór układu współrzędnych góra-dół, 0-wahadłowy; 1-narzędzia; 2-podstawy
    - ``referenceType``: Sposób ustawienia prądu odniesienia góra-dół, 0-sprzężenie zwrotne; 1-stała
    - ``referSampleStartUd``: Początek próbkowania prądu odniesienia góra-dół (sprzężenie zwrotne), cyc
    - ``referSampleCountUd``: Liczba cykli próbkowania prądu odniesienia góra-dół (sprzężenie zwrotne), cyc
    - ``referenceCurrent``: Prąd odniesienia góra-dół mA
    - ``offsetType``: Typ śledzenia z przesunięciem, 0-bez przesunięcia; 1-próbkowanie; 2-procent
    - ``offsetParameter``: Parametr przesunięcia; próbkowanie (czas rozpoczęcia próbkowania przesunięcia, domyślnie jeden cykl); procent (procent przesunięcia (-100 ~ 100))"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode" 

Wybór pasma przenoszenia AI śledzenia łuku
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ArcWeldTraceExtAIChannelConfig(channel)``"
    "Opis", "Wybór pasma przenoszenia AI śledzenia łuku"
    "Parametry wymagane", "- ``channel``: Wybór pasma przenoszenia AI śledzenia łuku, [0-3]"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode" 

Włączenie kompensacji śledzenia łuku + wielowarstwowej, wielościeżkowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ArcWeldTraceReplayStart()``"
    "Opis", "Włączenie kompensacji śledzenia łuku + wielowarstwowej, wielościeżkowej"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Wyłączenie kompensacji śledzenia łuku + wielowarstwowej, wielościeżkowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ArcWeldTraceReplayEnd()``"
    "Opis", "Wyłączenie kompensacji śledzenia łuku + wielowarstwowej, wielościeżkowej"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Zmiana współrzędnych przesunięcia - spawanie wielowarstwowe, wielościeżkowe
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``MultilayerOffsetTrsfToBase(pointo, pointX, pointZ, dx, dy, db)``"
    "Opis", "Zmiana współrzędnych przesunięcia - spawanie wielowarstwowe, wielościeżkowe"
    "Parametry wymagane", "- ``pointo``: Pozycja kartezjańska punktu odniesienia
    - ``pointX``: Pozycja kartezjańska punktu wskazującego kierunek przesunięcia X punktu odniesienia
    - ``pointZ``: Pozycja kartezjańska punktu wskazującego kierunek przesunięcia Z punktu odniesienia
    - ``dx``: Wielkość przesunięcia w kierunku X (mm)
    - ``dz``: Wielkość przesunięcia w kierunku Z (mm)
    - ``dry``: Wielkość przesunięcia wokół osi Y (°)"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode 
    - ``offset``: Wynikowe przesunięcie"

Przykład kodu śledzenia łuku dla spawania wielowarstwowego, wielościeżkowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    mulitilineorigin1_joint = [-24.090, -63.501, 84.288, -111.940, -93.426, 57.669]
    mulitilineorigin1_desc = [-677.559, 190.951, -1.205, 1.144, -41.482, -82.577]
    mulitilineX1_desc = [-677.556, 211.949, -1.206]
    mulitilineZ1_desc = [-677.564, 190.956, 19.817]
    mulitilinesafe_joint = [-25.734, -63.778, 81.502, -108.975, -93.392, 56.021]
    mulitilinesafe_desc = [-677.561, 211.950, 19.812, 1.144, -41.482, -82.577]
    mulitilineorigin2_joint = [-29.743, -75.623, 101.241, -116.354, -94.928, 55.735]
    mulitilineorigin2_desc = [-563.961, 215.359, -0.681, 2.845, -40.476, -87.443]
    mulitilineX2_desc = [-563.965, 220.355, -0.680]
    mulitilineZ2_desc = [-563.968, 215.362, 4.331]
    epos = [0, 0, 0, 0]
    offset = [0, 0, 0, 0, 0, 0]
    time.sleep(0.01)
    error = robot.MoveJ(joint_pos= mulitilinesafe_joint,tool= 13,user= 0,vel= 10)
    print(f"MoveJ return: {error}")
    error = robot.MoveL(desc_pos= mulitilineorigin1_desc,tool= 13,user= 0,vel= 10,speedPercent=100)
    print(f"MoveL return: {error}")
    error = robot.MoveJ(joint_pos= mulitilinesafe_joint,tool= 13,user= 0,vel= 10)
    print(f"MoveJ return: {error}")
    error = robot.MoveL(desc_pos= mulitilineorigin2_desc,tool= 13,user= 0,vel= 10,speedPercent=100)
    print(f"MoveL return: {error}")
    error = robot.MoveJ(joint_pos= mulitilinesafe_joint,tool= 13,user= 0,vel= 10)
    print(f"MoveJ return: {error}")
    error = robot.MoveL(desc_pos= mulitilineorigin1_desc,tool= 13,user= 0,vel= 10,speedPercent=100)
    print(f"MoveL return: {error}")
    error = robot.ARCStart(1, 0, 3000)
    print(f"ARCStart return: {error}")
    error = robot.WeaveStart(0)
    print(f"WeaveStart return: {error}")
    error = robot.ArcWeldTraceControl(1, 0, 1, 0.06, 5, 5, 50, 1, 0.06, 5, 5, 55, 0, 0, 4, 1, 10,0,0)
    print(f"ArcWeldTraceControl return: {error}")
    error = robot.MoveL(desc_pos= mulitilineorigin2_desc,tool= 13,user= 0,vel= 1,speedPercent=100)
    print(f"MoveL return: {error}")
    error = robot.ArcWeldTraceControl(0, 0, 1, 0.06, 5, 5, 50, 1, 0.06, 5, 5, 55, 0, 0, 4, 1, 10,0,0)
    print(f"ArcWeldTraceControl return: {error}")
    error = robot.WeaveEnd(0)
    print(f"WeaveEnd return: {error}")
    error = robot.ARCEnd(1, 0, 10000)
    print(f"ARCEnd return: {error}")
    error = robot.MoveJ(joint_pos= mulitilinesafe_joint,tool= 13,user= 0,vel= 10)
    print(f"MoveJ return: {error}")
    error,offset = robot.MultilayerOffsetTrsfToBase(mulitilineorigin1_desc[:3], mulitilineX1_desc, mulitilineZ1_desc, 10.0, 0.0, 0.0)
    print(f"MultilayerOffsetTrsfToBase return: {error}")
    error = robot.MoveL(desc_pos= mulitilineorigin1_desc,tool= 13,user= 0,vel= 10,speedPercent=100)
    print(f"MoveL return: {error}")
    error = robot.ARCStart(1, 0, 3000)
    print(f"ARCStart return: {error}")
    error, offset = robot.MultilayerOffsetTrsfToBase(mulitilineorigin2_desc[:3], mulitilineX2_desc, mulitilineZ2_desc, 10, 0, 0)
    print(f"MultilayerOffsetTrsfToBase return: {error}")
    error = robot.ArcWeldTraceReplayStart()
    print(f"ArcWeldTraceReplayStart return: {error}")
    error = robot.MoveL(desc_pos= mulitilineorigin2_desc,tool= 13,user= 0,vel= 2,speedPercent=100)
    print(f"MoveL return: {error}")
    error = robot.ArcWeldTraceReplayEnd()
    print(f"ArcWeldTraceReplayEnd return: {error}")
    error = robot.ARCEnd(1, 0, 10000)
    print(f"ARCEnd return: {error}")
    error = robot.MoveJ(joint_pos= mulitilinesafe_joint,tool= 13,user= 0,vel= 10)
    print(f"MoveJ return: {error}")
    error, offset = robot.MultilayerOffsetTrsfToBase(mulitilineorigin1_desc[:3], mulitilineX1_desc, mulitilineZ1_desc, 0, 10, 0)
    print(f"MultilayerOffsetTrsfToBase return: {error}")
    error = robot.MoveL(desc_pos= mulitilineorigin1_desc,tool= 13,user= 0,vel= 10,speedPercent=100)
    print(f"MoveL return: {error}")
    error = robot.ARCStart(1, 0, 3000)
    print(f"ARCStart return: {error}")
    error, offset = robot.MultilayerOffsetTrsfToBase(mulitilineorigin2_desc[:3], mulitilineX2_desc, mulitilineZ2_desc, 0, 10, 0)
    error = robot.ArcWeldTraceReplayStart()
    print(f"ArcWeldTraceReplayStart return: {error}")
    error = robot.MoveL(desc_pos= mulitilineorigin2_desc,tool= 13,user= 0,vel= 2,speedPercent=100)
    print(f"MoveL return: {error}")
    error = robot.ArcWeldTraceReplayEnd()
    print(f"ArcWeldTraceReplayEnd return: {error}")
    error = robot.ARCEnd(1, 0, 3000)
    print(f"ARCEnd return: {error}")
    error = robot.MoveJ(joint_pos= mulitilinesafe_joint,tool= 13,user= 0,vel= 10)
    print(f"MoveJ return: {error}")
    robot.CloseRPC()

Wybór kanału AI sprzężenia zwrotnego prądu spawarki dla śledzenia łuku
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ArcWeldTraceAIChannelCurrent(channel)``"
    "Opis", "Wybór kanału AI sprzężenia zwrotnego prądu spawarki dla śledzenia łuku"
    "Parametry wymagane", "- ``channel``: Kanał; 0-rozszerzony AI0; 1-rozszerzony AI1; 2-rozszerzony AI2; 3-rozszerzony AI3; 4-AI0 skrzynki kontrolnej; 5-AI1 skrzynki kontrolnej"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Wybór kanału AI sprzężenia zwrotnego napięcia spawarki dla śledzenia łuku
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ArcWeldTraceAIChannelVoltage(channel)``"
    "Opis", "Wybór kanału AI sprzężenia zwrotnego napięcia spawarki dla śledzenia łuku"
    "Parametry wymagane", "- ``channel``: Kanał; 0-rozszerzony AI0; 1-rozszerzony AI1; 2-rozszerzony AI2; 3-rozszerzony AI3; 4-AI0 skrzynki kontrolnej; 5-AI1 skrzynki kontrolnej"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Parametry konwersji sprzężenia zwrotnego prądu spawarki dla śledzenia łuku
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ArcWeldTraceCurrentPara(AILow, AIHigh, currentLow, currentHigh)``"
    "Opis", "Parametry konwersji sprzężenia zwrotnego prądu spawarki dla śledzenia łuku"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "- ``AILow``: Dolna granica kanału AI, domyślnie 0V, zakres [0-10V]
    - ``AIHigh``: Górna granica kanału AI, domyślnie 10V, zakres [0-10V]
    - ``currentLow``: Wartość prądu spawarki odpowiadająca dolnej granicy kanału AI, domyślnie 0V, zakres [0-200V]
    - ``currentHigh``: Wartość prądu spawarki odpowiadająca górnej granicy kanału AI, domyślnie 100V, zakres [0-200V]"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Parametry konwersji sprzężenia zwrotnego napięcia spawarki dla śledzenia łuku
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ArcWeldTraceVoltagePara(AILow, AIHigh, voltageLow, voltageHigh)``"
    "Opis", "Parametry konwersji sprzężenia zwrotnego napięcia spawarki dla śledzenia łuku"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "- ``AILow``: Dolna granica kanału AI, domyślnie 0V, zakres [0-10V]
    - ``AIHigh``: Górna granica kanału AI, domyślnie 10V, zakres [0-10V]
    - ``voltageLow``: Wartość napięcia spawarki odpowiadająca dolnej granicy kanału AI, domyślnie 0V, zakres [0-200V]
    - ``voltageHigh``: Wartość napięcia spawarki odpowiadająca górnej granicy kanału AI, domyślnie 100V, zakres [0-200V]"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Przykład kodu śledzenia łuku
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')

    safetydescPose = [-504.043,275.181,40.908,-28.002,-42.025,-14.044]
    safetyjointPos = [-39.078,-76.732,87.227,-99.47,-94.301,18.714]
    startdescPose = [-473.86,257.879,-20.849,-37.317,-42.021,2.543]
    startjointPos = [-43.487,-76.526,95.568,-104.445,-89.356,3.72]
    enddescPose = [-499.844,141.225,7.72,-34.856,-40.17,13.13]
    endjointPos = [-31.305,-82.998,99.401,-104.426,-89.35,3.696]
    exaxisPos = [0, 0, 0, 0]
    offdese = [0, 0, 0, 0, 0, 0]
    robot.MoveJ(joint_pos=safetyjointPos, tool=1, user=0, vel=20, acc=100)
    robot.WeldingSetCurrentRelation(0, 495, 1, 10, 0)
    robot.WeldingSetVoltageRelation(10, 45, 1, 10, 1)
    robot.WeldingSetVoltage(0, 25, 1, 0)  # ----设置电压
    robot.WeldingSetCurrent(0, 260, 0, 0)  # ----设置电流
    rtn = robot.ArcWeldTraceAIChannelCurrent(4)
    print("ArcWeldTraceAIChannelCurrent rtn is", rtn)
    rtn = robot.ArcWeldTraceAIChannelVoltage(5)
    print("ArcWeldTraceAIChannelVoltage rtn is", rtn)
    rtn = robot.ArcWeldTraceCurrentPara(0, 5, 0, 500)
    print("ArcWeldTraceCurrentPara rtn is", rtn)
    rtn = robot.ArcWeldTraceVoltagePara(1.018, 10, 0, 50)
    print("ArcWeldTraceVoltagePara rtn is", rtn)
    robot.MoveJ(joint_pos=startjointPos, tool=1, user=0, vel=20, acc=100)
    robot.ArcWeldTraceControl(1, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0)
    robot.ARCStart(0, 0, 10000)
    robot.WeaveStart(0)
    robot.MoveL(desc_pos=enddescPose, tool=1, user=0, vel=100, ovl= 2, acc=100)
    robot.ARCEnd(0, 0, 10000)
    robot.WeaveEnd(0)
    robot.ArcWeldTraceControl(0, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0)
    robot.MoveJ(joint_pos=safetyjointPos, tool=1, user=0, vel=20, acc=100)

Ustawianie rozszerzonego portu IO dla poszukiwania pozycji drutu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetWireSearchExtDIONum(searchDoneDINum, searchStartDONum)``"
    "Opis", "Ustawianie rozszerzonego portu IO dla poszukiwania pozycji drutu"
    "Parametry wymagane", "- ``searchDoneDINum``: Port DO pomyślnego poszukiwania pozycji drutu (0-127)
    - ``searchStartDONum``: Port DO sterowania uruchamianiem/zatrzymywaniem poszukiwania pozycji drutu (0-127)"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode" 

Przykład kodu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    toolCoord = [0, 0, 200, 0, 0, 0]
    robot.SetToolCoord(1, toolCoord, 0, 0, 1, 0)
    wobjCoord = [0, 0, 0, 0, 0, 0]
    robot.SetWObjCoord(1, wobjCoord, 0)
    robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 50, 5, 50, 1, 50, 10)
    robot.ExtDevLoadUDPDriver()
    robot.SetWireSearchExtDIONum(0, 0)
    exaxisPos = [0, 0, 0, 0]
    offdese = [0, 0, 0, 0, 0, 0]
    descStart = [216.543, 445.175, 93.465, 179.683, 1.757, -112.641]
    jointStart = [-128.345, -86.660, 114.679, -119.625, -89.219, 74.303]
    descEnd = [111.143, 523.384, 87.659, 179.703, 1.835, -97.750]
    jointEnd = [-113.454, -81.060, 109.328, -119.954, -89.218, 74.302]
    error = robot.MoveL(desc_pos=descStart,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos=descEnd,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    descREF0A = [142.135, 367.604, 86.523, 179.728, 1.922, -111.089]
    jointREF0A = [-126.794, -100.834, 128.922, -119.864, -89.218, 74.302]
    descREF0B = [254.633, 463.125, 72.604, 179.845, 2.341, -114.704]
    jointREF0B = [-130.413, -81.093, 112.044, -123.163, -89.217, 74.303]
    descREF1A = [92.556, 485.259, 47.476, -179.932, 3.130, -97.512]
    jointREF1A = [-113.231, -83.815, 119.877, -129.092, -89.217, 74.303]
    descREF1B = [203.103, 583.836, 63.909, 179.991, 2.854, -103.372]
    jointREF1B = [-119.088, -69.676, 98.692, -121.761, -89.219, 74.303]
    error = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchStart return: {error}")
    error = robot.MoveL(desc_pos=descREF0A,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos=descREF0B,tool= 1,user= 1,vel= 100,search=1)
    print(f"MoveL return: {error}")
    error = robot.WireSearchWait("REF0")
    print(f"WireSearchWait return: {error}")
    error = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchEnd return: {error}")
    error = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchStart return: {error}")
    error = robot.MoveL(desc_pos= descREF1A,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos= descREF1B,tool= 1,user= 1,vel= 100,search=1)
    print(f"MoveL return: {error}")
    error = robot.WireSearchWait("REF1")
    print(f"WireSearchWait return: {error}")
    error = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0)
    error = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchStart return: {error}")
    error = robot.MoveL(desc_pos= descREF0A,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos= descREF0B,tool= 1,user= 1,vel= 100,search=1)
    print(f"MoveL return: {error}")
    error = robot.WireSearchWait("RES0")
    print(f"WireSearchWait return: {error}")
    error = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchEnd return: {error}")
    error = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchStart return: {error}")
    error = robot.MoveL(desc_pos= descREF1A,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos= descREF1B,tool= 1,user= 1,vel= 100,search=1)
    print(f"MoveL return: {error}")
    error = robot.WireSearchWait("RES1")
    print(f"WireSearchWait return: {error}")
    error = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchEnd return: {error}")
    varNameRef = ["REF0", "REF1", "#", "#", "#", "#"]
    varNameRes = ["RES0", "RES1", "#", "#", "#", "#"]
    offectFlag = 0
    offectPos = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    error, offectFlag, offectPos = robot.GetWireSearchOffset(0, 0, varNameRef, varNameRes)
    print(f"GetWireSearchOffset return: {error}")
    error = robot.PointsOffsetEnable(0, offectPos)
    print(f"PointsOffsetEnable return: {error}")
    error = robot.MoveL(desc_pos= descStart,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos= descEnd,tool= 1,user= 1,vel= 100,search=1)
    print(f"MoveL return: {error}")
    error = robot.PointsOffsetDisable()
    robot.CloseRPC()

Rozpoczęcie poszukiwania pozycji drutu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WireSearchStart(refPos,searchVel,searchDis,autoBackFlag,autoBackVel,autoBackDis,offectFlag)``"
    "Opis", "Rozpoczęcie poszukiwania pozycji drutu"
    "Parametry wymagane", "- ``refPos``: 1-punkt odniesienia 0-punkt kontaktu
    - ``searchVel``: Prędkość poszukiwania %
    - ``searchDis``: Odległość poszukiwania mm
    - ``autoBackFlag``: Flaga automatycznego powrotu, 0-nie automatyczny; -automatyczny
    - ``autoBackVel``: Prędkość automatycznego powrotu %
    - ``autoBackDis``: Odległość automatycznego powrotu mm
    - ``offectFlag``: 1-poszukiwanie z przesunięciem; 0-poszukiwanie punktu nauczania"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Zakończenie poszukiwania pozycji drutu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WireSearchEnd(refPos,searchVel,searchDis,autoBackFlag,autoBackVel,autoBackDis,offectFlag)``"
    "Opis", "Zakończenie poszukiwania pozycji drutu"
    "Parametry wymagane", "- ``refPos``: 1-punkt odniesienia 2-punkt kontaktu
    - ``searchVel``: Prędkość poszukiwania %
    - ``searchDis``: Odległość poszukiwania mm
    - ``autoBackFlag``: Flaga automatycznego powrotu, 0-nie automatyczny; -automatyczny
    - ``autoBackVel``: Prędkość automatycznego powrotu %
    - ``autoBackDis``: Odległość automatycznego powrotu mm
    - ``offectFlag``: 1-poszukiwanie z przesunięciem; 2-poszukiwanie punktu nauczania"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Obliczanie przesunięcia poszukiwania pozycji drutu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetWireSearchOffset(seamType, method,varNameRef,varNameRes)``"
    "Opis", "Obliczanie przesunięcia poszukiwania pozycji drutu"
    "Parametry wymagane", "- ``seamType``: Typ spoiny
    - ``method``: Metoda obliczeniowa
    - ``varNameRef``: Punkty odniesienia 1-6, „#” oznacza brak zmiennej punktowej
    - ``varNameRes``: Punkty kontaktu 1-6, „#” oznacza brak zmiennej punktowej"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``offsetFlag``: 0-przesunięcie bezpośrednio dodawane do punktu instrukcji; 1-przesunięcie wymaga transformacji współrzędnych punktu instrukcji
    - ``offset``: Przesunięcie pozy [x, y, z, a, b, c]"

Oczekiwanie na zakończenie poszukiwania pozycji drutu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WireSearchWait(varname)``"
    "Opis", "Oczekiwanie na zakończenie poszukiwania pozycji drutu"
    "Parametry wymagane", "- ``varName``: Nazwa punktu kontaktu „RES0” ~ „RES99”"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode" 

Zapis punktu kontaktu poszukiwania pozycji drutu do bazy danych
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetPointToDatabase(varName,pos)``"
    "Opis", "Zapis punktu kontaktu poszukiwania pozycji drutu do bazy danych"
    "Parametry wymagane", "- ``varName``: Nazwa punktu kontaktu „RES0” ~ „RES99”
    - ``pos``: Dane punktu kontaktu [x, y, x, a, b, c]"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode" 

Przykład kodu poszukiwania pozycji drutu robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    toolCoord = [0, 0, 200, 0, 0, 0]
    robot.SetToolCoord(1, toolCoord, 0, 0, 1, 0)
    wobjCoord = [0, 0, 0, 0, 0, 0]
    robot.SetWObjCoord(1, wobjCoord, 0)
    exaxisPos = [0, 0, 0, 0]
    offdese = [0, 0, 0, 0, 0, 0]
    descStart = [216.543, 445.175, 93.465, 179.683, 1.757, -112.641]
    jointStart = [-128.345, -86.660, 114.679, -119.625, -89.219, 74.303]
    descEnd = [111.143, 523.384, 87.659, 179.703, 1.835, -97.750]
    jointEnd = [-113.454, -81.060, 109.328, -119.954, -89.218, 74.302]
    error = robot.MoveL(desc_pos=descStart,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos=descEnd,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    descREF0A = [142.135, 367.604, 86.523, 179.728, 1.922, -111.089]
    jointREF0A = [-126.794, -100.834, 128.922, -119.864, -89.218, 74.302]
    descREF0B = [254.633, 463.125, 72.604, 179.845, 2.341, -114.704]
    jointREF0B = [-130.413, -81.093, 112.044, -123.163, -89.217, 74.303]
    descREF1A = [92.556, 485.259, 47.476, -179.932, 3.130, -97.512]
    jointREF1A = [-113.231, -83.815, 119.877, -129.092, -89.217, 74.303]
    descREF1B = [203.103, 583.836, 63.909, 179.991, 2.854, -103.372]
    jointREF1B = [-119.088, -69.676, 98.692, -121.761, -89.219, 74.303]
    error = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchStart return: {error}")
    error = robot.MoveL(desc_pos=descREF0A,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos=descREF0B,tool= 1,user= 1,vel= 100,search=1)
    print(f"MoveL return: {error}")
    error = robot.WireSearchWait("REF0")
    print(f"WireSearchWait return: {error}")
    error = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchEnd return: {error}")
    error = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchStart return: {error}")
    error = robot.MoveL(desc_pos= descREF1A,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos= descREF1B,tool= 1,user= 1,vel= 100,search=1)
    print(f"MoveL return: {error}")
    error = robot.WireSearchWait("REF1")
    print(f"WireSearchWait return: {error}")
    error = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0)
    error = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchStart return: {error}")
    error = robot.MoveL(desc_pos= descREF0A,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos= descREF0B,tool= 1,user= 1,vel= 100,search=1)
    print(f"MoveL return: {error}")
    error = robot.WireSearchWait("RES0")
    print(f"WireSearchWait return: {error}")
    error = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchEnd return: {error}")
    error = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchStart return: {error}")
    error = robot.MoveL(desc_pos= descREF1A,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos= descREF1B,tool= 1,user= 1,vel= 100,search=1)
    print(f"MoveL return: {error}")
    error = robot.WireSearchWait("RES1")
    print(f"WireSearchWait return: {error}")
    error = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchEnd return: {error}")
    varNameRef = ["REF0", "REF1", "#", "#", "#", "#"]
    varNameRes = ["RES0", "RES1", "#", "#", "#", "#"]
    offectFlag = 0
    offectPos = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    error, offectFlag, offectPos = robot.GetWireSearchOffset(0, 0, varNameRef, varNameRes)
    print(f"GetWireSearchOffset return: {error}")
    error = robot.PointsOffsetEnable(0, offectPos)
    print(f"PointsOffsetEnable return: {error}")
    error = robot.MoveL(desc_pos= descStart,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos= descEnd,tool= 1,user= 1,vel= 100,search=1)
    print(f"MoveL return: {error}")
    error = robot.PointsOffsetDisable()
    robot.CloseRPC()

Ustawianie rozpoczęcia zmiany napięcia spawania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeldingSetVoltageGradualChangeStart(IOType, voltageStart, voltageEnd, AOIndex, blend)``"
    "Opis", "Ustawianie rozpoczęcia zmiany napięcia spawania"
    "Parametry wymagane", "- ``IOType``: Typ sterowania; 0-IO skrzynki kontrolnej; 1-protokół komunikacji cyfrowej (UDP); 2-protokół komunikacji cyfrowej (ModbusTCP)
    - ``voltageStart``: Początkowe napięcie spawania (V)
    - ``voltageEnd``: Końcowe napięcie spawania (V)
    - ``AOIndex``: Numer portu AO skrzynki kontrolnej (0-1)
    - ``blend``: Czy wygładzać 0-nie; 1-tak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie zakończenia zmiany napięcia spawania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeldingSetVoltageGradualChangeEnd()``"
    "Opis", "Ustawianie zakończenia zmiany napięcia spawania"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie rozpoczęcia zmiany prądu spawania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeldingSetCurrentGradualChangeStart(IOType, currentStart, currentEnd, AOIndex, blend)``"
    "Opis", "Ustawianie rozpoczęcia zmiany prądu spawania"
    "Parametry wymagane", "- ``IOType``: Typ sterowania; 0-IO skrzynki kontrolnej; 1-protokół komunikacji cyfrowej (UDP); 2-protokół komunikacji cyfrowej (ModbusTCP)
    - ``currentStart``: Początkowy prąd spawania (A)
    - ``currentEnd``: Końcowy prąd spawania (A)
    - ``AOIndex``: Numer portu AO skrzynki kontrolnej (0-1)
    - ``blend``: Czy wygładzać 0-nie; 1-tak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie zakończenia zmiany prądu spawania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WeldingSetCurrentGradualChangeEnd()``"
    "Opis", "Ustawianie zakończenia zmiany prądu spawania"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Przykład kodu zmiany prądu i napięcia spawania robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    startdescPose = [-484.707, 276.996, -14.013, -37.657, -40.508, -1.548]
    startjointPos = [-45.421, -75.673, 93.627, -104.302, -87.938, 6.005]
    enddescPose = [-508.767, 137.109, -13.966, -37.639, -40.508, -1.559]
    endjointPos = [-32.768, -80.947, 100.254, -106.201, -87.201, 18.648]
    safedescPose = [-484.709, 294.436, 13.621, -37.660, -40.508, -1.545]
    safejointPos = [-46.604, -75.410, 89.109, -100.003, -88.012, 4.823]
    exaxisPos = [0, 0, 0, 0]
    offdese = [0, 0, 0, 0, 0, 0]
    robot.WeldingSetCurrentRelation(0, 495, 1, 10, 0)
    robot.WeldingSetVoltageRelation(10, 45, 1, 10, 1)
    robot.WeldingSetVoltage(0, 25, 1, 0)  # ----设置电压
    robot.WeldingSetCurrent(0, 260, 0, 0)  # ----设置电流
    robot.MoveJ(joint_pos=safejointPos, tool=1, user=0, vel=5, acc=100)
    rtn = robot.WeldingSetCurrentGradualChangeStart(0, 260, 220, 0, 0)
    print("WeldingSetCurrentGradualChangeStart rtn is", rtn)
    rtn = robot.WeldingSetVoltageGradualChangeStart(0, 25, 22, 1, 0)
    print("WeldingSetVoltageGradualChangeStart rtn is", rtn)
    rtn = robot.ArcWeldTraceControl(1, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0)
    print("ArcWeldTraceControl rtn is", rtn)
    robot.MoveJ(joint_pos=startjointPos, tool=1, user=0, vel=5, acc=100)
    robot.ARCStart(0, 0, 10000)
    robot.WeaveStart(0)
    robot.WeaveChangeStart(2, 1, 24, 36)
    robot.MoveL(desc_pos=enddescPose, tool=1, user=0, vel=100, ovl=2, acc=100)
    robot.ARCEnd(0, 0, 10000)
    robot.WeaveChangeEnd()
    robot.WeaveEnd(0)
    robot.ArcWeldTraceControl(0, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0)
    robot.WeldingSetCurrentGradualChangeEnd()
    robot.WeldingSetVoltageGradualChangeEnd()

Ustawianie niestandardowych parametrów ruchu wahadłowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``CustomWeaveSetPara(id, pointNum, point, stayTime, frequency, incStayType, stationary)``"
    "Opis", "Ustawianie niestandardowych parametrów ruchu wahadłowego"
    "Parametry wymagane", "- ``id``: Niestandardowy numer wahadła: 0-2
    - ``pointNum``: Liczba punktów wahadła 0-10
    - ``point``: Dane punktów końcowych ruchu x,y,z
    - ``stayTime``: Czas postoju wahadła ms
    - ``frequency``: Częstotliwość wahadła Hz
    - ``incStayType``: Tryb oczekiwania: 0-cykl nie zawiera czasu oczekiwania; 1-cykl zawiera czas oczekiwania
    - ``stationary``: Oczekiwanie w pozycji wahadła: 0-kontynuacja ruchu w czasie oczekiwania; 1-pozycja nieruchoma w czasie oczekiwania"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Pobieranie niestandardowych parametrów ruchu wahadłowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``CustomWeaveGetPara(id)``"
    "Opis", "Pobieranie niestandardowych parametrów ruchu wahadłowego"
    "Parametry wymagane", "- ``id``: Niestandardowy numer wahadła: 0-2"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``pointNum``: Liczba punktów wahadła 0-10
    - ``point``: Dane punktów końcowych ruchu x,y,z
    - ``stayTime``: Czas postoju wahadła ms
    - ``frequency``: Częstotliwość wahadła Hz
    - ``incStayType``: Tryb oczekiwania: 0-cykl nie zawiera czasu oczekiwania; 1-cykl zawiera czas oczekiwania
    - ``stationary``: Oczekiwanie w pozycji wahadła: 0-kontynuacja ruchu w czasie oczekiwania; 1-pozycja nieruchoma w czasie oczekiwania"

Przykład kodu niestandardowych parametrów ruchu wahadłowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    point = [0.0] * 30
    point[0] = -3.0
    point[1] = -3.0
    point[2] = 0.0
    point[3] = -6.0
    point[4] = 0.0
    point[5] = 0.0
    point[6] = -3.0
    point[7] = 3.0
    point[8] = 0.0
    point[9] = 0.0
    point[10] = 0.0
    point[11] = 0.0
    stayTime = [0.0] * 10
    rtn = robot.CustomWeaveSetPara(2, 4, point, stayTime, 1.000, 0, 0)
    print(f"CustomWeaveSetPara rtn is {rtn}")
    time.sleep(1)
    pointNum = 0
    frequency = 0.0
    incStayType = 0
    stationary = 0
    rtn, pointNum, point, stayTime, frequency, incStayType, stationary = robot.CustomWeaveGetPara(2)
    print(f"pointNum is {pointNum}")
    for i in range(pointNum):
        print(f"point {i}, point x y z {point[i * 3 + 0]},{point[i * 3 + 1]},{point[i * 3 + 2]}")
    print(f"fre is {frequency}, stay is {incStayType},{stationary}")
    robot.WeaveSetPara(0, 9, 1.000000, 1, 5.000000, 6.000000, 5.000000, 50, 100, 100, 0, 1, 0.000000, 0.000000)
    desc_p1 = [-288.650, 367.807, 288.404, 0.000, -0.001, 0.001]
    desc_p2 = [-431.714, 367.815, 288.415, 0.001, 0.001, 0.000]
    desc_p3 = [-348.666, 427.798, 288.404, -0.000, -0.000, 0.001]
    j1 = [140.656, -84.560, -91.707, -93.734, 90.000, 50.655]
    j2 = [149.873, -98.298, -77.599, -94.103, 90.000, 59.873]
    j3 = [139.773, -96.173, -80.014, -93.814, 90.000, 49.772]
    epos = [0.0] * 4
    offset_pos = [0.0] * 6
    robot.MoveJ(joint_pos=j1, tool=3, user=0, vel=100)
    robot.WeaveStart(0)
    robot.Circle(desc_pos_p=desc_p3, tool_p=3, user_p=0, vel_p=50, desc_pos_t=desc_p2, tool_t=3, user_t=0, vel_t=50, oacc=10)
    robot.WeaveEnd(0)
    robot.MoveJ(joint_pos=j1, tool=3, user=0, vel=100)
    robot.WeaveStart(0)
    robot.MoveC(desc_pos_p=desc_p3, tool_p=3, user_p=0, vel_p=50, desc_pos_t=desc_p2, tool_t=3, user_t=0, vel_t=50)
    robot.WeaveEnd(0)
    robot.MoveJ(joint_pos=j1, tool=3, user=0, vel=100)
    robot.WeaveStart(0)
    robot.MoveL(desc_pos=desc_p2, tool=3, user=0, vel=100, ovl=10, speedPercent=100)
    robot.WeaveEnd(0)
    robot.CloseRPC()

Konfiguracja parametrów spawarki laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetLaserWeldingParam(self, num, scanSpeed, scanWidth, peakPower, dutyCycle, Freq, io_type=1)``"
    "Opis", "Zapis parametrów konfiguracyjnych jednej z 10 grup procesowych spawarki laserowej i skonfigurowanie ich dla spawarki"
    "Parametry wymagane", "
    - ``io_type``: Typ komunikacji 0-IO 1-UDP
    - ``Num``: Numer grupy do ustawienia (1~10)
    - ``scanSpeed``: Prędkość skanowania
    - ``scanWidth``: Szerokość skanowania
    - ``peakPower``: Moc szczytowa
    - ``dutyCycle``: Współczynnik wypełnienia
    - ``Freq``: Częstotliwość
    "
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie rozpoczęcia/zatrzymania spawania laserowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetLaserWeldingStartEnd(self, status, io_type=1, max_waittime=10000)``"
    "Opis", "Ustawianie włączania/wyłączania spawarki laserowej"
    "Parametry wymagane", "
    - ``io_type``: Typ komunikacji 0-IO 1-UDP
    - ``status``: Słowo sterujące 0-wyłącz wiązkę 1-włącz wiązkę
    - ``max_waittime``: Maksymalny czas oczekiwania
    "
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Włączanie/wyłączanie spawarki laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetLaserWeldingEnable(self, status, io_type=1)``"
    "Opis", "Włączanie/wyłączanie spawarki laserowej"
    "Parametry wymagane", "
    - ``io_type``: Typ komunikacji 0-IO 1-UDP
    - ``status``: 0-wyłącz 1-włącz
    "
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Resetowanie błędów spawarki laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ResetLaserWeldingErr(self,status, io_type=1)``"
    "Opis", "Resetowanie błędów spawarki laserowej"
    "Parametry wymagane", "
    - ``io_type``: Typ komunikacji 0-IO 1-UDP
    - ``status``: Słowo sterujące 0-nieważne 1-resetowanie błędu
    "
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Pobieranie stanu pracy spawarki laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetLaserWeldingRunningState(self, io_type=1)``"
    "Opis", "Pobieranie stanu pracy spawarki laserowej"
    "Parametry wymagane", "
    - ``io_type``: Typ komunikacji 0-IO 1-UDP
    - ``status``: Słowo sterujące 0-zatrzymana 1-pracuje
    "
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Pobieranie stanu awarii spawarki laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetLaserWeldingErrState(self, io_type=1)``"
    "Opis", "Pobieranie stanu awarii spawarki laserowej"
    "Parametry wymagane", "
    - ``io_type``: Typ komunikacji 0-IO 1-UDP
    - ``status``: 0-brak awarii 1-występuje awaria
    "
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Pobieranie parametrów konfiguracyjnych spawarki laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetLaserWeldingParamTarget(self, num)``"
    "Opis", "Pobieranie parametrów konfiguracyjnych jednej z 10 grup procesowych spawarki laserowej"
    "Parametry wymagane", "
    - ``Num``: Numer grupy do ustawienia (1~10)
    - ``scanSpeed``: Prędkość skanowania
    - ``scanWidth``: Szerokość skanowania
    - ``peakPower``: Moc szczytowa
    - ``dutyCycle``: Współczynnik wypełnienia
    - ``Freq``: Częstotliwość
    "
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Pobieranie aktualnie obowiązujących parametrów konfiguracyjnych spawarki laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetLaserWeldingParamActual(self, io_type=1)``"
    "Opis", "Pobieranie aktualnie obowiązujących parametrów konfiguracyjnych spawarki laserowej"
    "Parametry wymagane", "
    - ``io_type``: Typ komunikacji 0-IO 1-UDP
    - ``scanSpeed``: Prędkość skanowania
    - ``scanWidth``: Szerokość skanowania
    - ``peakPower``: Moc szczytowa
    - ``dutyCycle``: Współczynnik wypełnienia
    - ``Freq``: Częstotliwość
    "
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Konfiguracja rozszerzonego portu DO włączania spawarki laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetLaserWeldingEnableExtDoNum(self, ctrlModeDONum)``"
    "Opis", "Konfiguracja rozszerzonego portu DO włączania spawarki laserowej"
    "Parametry wymagane", "
    - ``ctrlModeDONum``: Rozszerzony numer portu DO włączania spawarki laserowej
    "
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Konfiguracja rozszerzonego portu DO uruchamiania spawarki laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetLaserWeldingStartExtDoNum(self, ctrlModeDONum)``"
    "Opis", "Konfiguracja rozszerzonego portu DO uruchamiania spawarki laserowej"
    "Parametry wymagane", "
    - ``ctrlModeDONum``: Rozszerzony numer portu DO uruchamiania (włączania/wyłączania wiązki) spawarki laserowej
    "
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Konfiguracja rozszerzonego portu DO resetowania błędów spawarki laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetLaserWeldingErrResetExtDoNum(self, ctrlModeDONum)``"
    "Opis", "Konfiguracja rozszerzonego portu DO resetowania błędów spawarki laserowej"
    "Parametry wymagane", "
    - ``ctrlModeDONum``: Rozszerzony numer portu DO resetowania błędów spawarki laserowej
    "
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Konfiguracja rozszerzonego portu DI stanu pracy (stanu wiązki) spawarki laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetLaserWeldingRunningStateExtDiNum(self, diNum)``"
    "Opis", "Konfiguracja rozszerzonego portu DI stanu pracy (stanu wiązki) spawarki laserowej"
    "Parametry wymagane", "
    - ``diNum``: Rozszerzony port DI stanu pracy (stanu wiązki) spawarki laserowej
    "
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Konfiguracja rozszerzonego portu DI stanu awarii spawarki laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetLaserWeldingErrStateExtDiNum(self, diNum)``"
    "Opis", "Konfiguracja rozszerzonego portu DI stanu awarii spawarki laserowej"
    "Parametry wymagane", "
    - ``diNum``: Rozszerzony port DI stanu awarii spawarki laserowej
    "
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Przykład kodu spawania laserowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 

    from time import sleep
    from fairino import Robot
    import time

    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')

    def testLsaerWeld():
        robot.ExtDevLoadUDPDriver()
        time.sleep(1)

        robot.SetLaserWeldingParam(num = 3, scanSpeed = 2000, scanWidth = 3, peakPower = 1500, dutyCycle = 100, Freq = 1000, io_type=1)
        robot.SetLaserWeldingStartExtDoNum(ctrlModeDONum=1)

        robot.Mode(0)
        time.sleep(1)

        desc_pos1 = [-303.721, -206.960, 297.105, 152.209, 19.857, 109.166]
        desc_pos2 = [-301.575, -254.888, 284.786, 155.919, 26.946, 111.629]
        desc_safe = [-344.386, -280.830, 435.073, 173.835, 15.333, 124.931]
        jointPos1 = [9.827, -99.740, 120.088, -78.900, -77.241, -17.904]
        jointPos2 = [15.251, -96.456, 120.138, -84.664, -68.542, -17.843]
        jointSafe = [19.142, -98.078, 101.493, -83.078, -77.070, -17.794]

        error = robot.MoveL(desc_pos=desc_pos1,joint_pos=jointPos1, tool=1, user=0, vel=100, ovl= 2, acc=100)
        print("MoveL return:", error)
        robot.SetLaserWeldingStartEnd(1, io_type=1, max_waittime=10000)

        error = robot.MoveL(desc_pos=desc_pos2, joint_pos=jointPos2, tool=1, user=0, vel=100, ovl= 2, acc=100)
        print("MoveL return:", error)
        robot.SetLaserWeldingStartEnd(0, io_type=1, max_waittime=10000)

        error = robot.MoveL(desc_pos=desc_safe, joint_pos=jointSafe, tool=1, user=0, vel=100, ovl= 2, acc=100)
        print("MoveL return:", error)

        robot.Mode(1)
        time.sleep(1)

        # Zamknięcie połączenia
        robot.CloseRPC()
        time.sleep(1)

    # Wywołanie funkcji testowej
    testLsaerWeld()

Ustawianie Powrotu do Punktu Zerowego Cyklu po Zakończeniu Splotu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetWeaveBackCenterConfig(self, flag)``"
    "Opis", "Ustawia, czy po zakończeniu splotu wrócić do punktu zerowego cyklu"
    "Parametry Wymagane", "
    - ``flag``: Czy wrócić do punktu zerowego cyklu po zakończeniu splotu; 0-nie wracać; 1-wrócić do punktu zerowego cyklu
    "
    "Parametry Domyślne", "Brak"
    "Wartość Zwracana", "Kod błędu, 0-sukces; niezerowy-błąd"    

Pobieranie Parametrów Powrotu do Punktu Zerowego Cyklu po Zakończeniu Splotu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetWeaveBackCenterConfig(self)``"
    "Opis", "Pobiera parametry powrotu do punktu zerowego cyklu po zakończeniu splotu"
    "Parametry Wymagane", "
    - ``flag``: Czy wrócić do punktu zerowego cyklu po zakończeniu splotu; 0-nie wracać; 1-wrócić do punktu zerowego cyklu
    "
    "Parametry Domyślne", "Brak"
    "Wartość Zwracana", "Kod błędu, 0-sukces; niezerowy-błąd"   

Przykład Kodu Powrotu do Punktu Zerowego Cyklu po Zakończeniu Splotu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 

    from fairino import Robot
    import time

    def main():
        robot = Robot.RPC('192.168.58.2')
        time.sleep(0.5)  

        def callback(src_type, count, cmd_id, data_len, content):
            print(" cmd_id={} count={} data_len={} content={}".format(cmd_id, count, data_len, content))
            return 0

        robot.SetUDPCmdRpyCallback(callback)

        j1 = [9.000, -66.067, 67.706, -103.217, -90.151, 100.669]
        j2 = [-4.660, -107.973, 103.734, -76.214, -89.999, 90.886]
        j3 = [-36.762, -77.380, 91.364, -127.159, -90.024, 54.833]
        j4 = [-62.875, -89.460, 86.437, -77.030, -90.012, 31.539]

    
        desc_pos1 = [-654.129, -235.344, 246.543, 6.010, -11.535, -176.787]
        desc_pos2 = [-273.710, -100.871, 280.935, 5.692, 9.522, 179.512]
        desc_pos3 = [-566.093, 311.278, 215.008, -10.453, -17.486, -174.209]
        desc_pos4 = [-246.558, 328.240, 292.173, 13.912, 4.437, -179.067]

        offset_pos = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
        epos = [0.0, 0.0, 0.0, 0.0]

        tool = 2
        user = 0
        vel = 100.0
        acc = 100.0
        ovl = 20.0
        oacc = 100.0
        blendT = 0.0
        blendR = 0.0
        flag = 0
        search = 0
        blendMode = 0
        velAccMode = 0

        robot.SetSpeed(1)

        robot.WeaveEnd(0)

        rtn = robot.SetWeaveBackCenterConfig(1)
        print(f"SetWeaveBackCenterConfig rtn is {rtn}")

        rtn, weaveBackConfig = robot.GetWeaveBackCenterConfig()
        print(f"GetWeavebackCenterConfig {weaveBackConfig}")

        rtn = robot.MoveJ(joint_pos=j1, desc_pos=desc_pos1, tool=tool, user=user,
                        vel=vel, acc=acc, ovl=100.0, exaxis_pos=epos,
                        blendT=blendT, offset_flag=flag, offset_pos=offset_pos)
        print(f"MoveJ rtn is {rtn}")

        robot.WeaveStart(0)

        robot.NewSplineStart(0, 6000)

        rtn = robot.NewSplinePoint(joint_pos=j1, desc_pos=desc_pos1, tool=tool, user=user,lastFlag=0,
                                vel=vel, acc=acc, ovl=ovl, blendR=-1, config=0)
        print(f"NewSplinePoint 1 rtn is {rtn}")

        rtn = robot.NewSplinePoint(joint_pos=j2, desc_pos=desc_pos2, tool=tool, user=user,lastFlag=0,
                                vel=vel, acc=acc, ovl=ovl, blendR=-1, config=0)
        print(f"NewSplinePoint 2 rtn is {rtn}")

        rtn = robot.NewSplinePoint(joint_pos=j3, desc_pos=desc_pos3, tool=tool, user=user,lastFlag=0,
                                vel=vel, acc=acc, ovl=ovl, blendR=-1, config=0)
        print(f"NewSplinePoint 3 rtn is {rtn}")

        rtn = robot.NewSplinePoint(joint_pos=j4, desc_pos=desc_pos4, tool=tool, user=user,lastFlag=1,
                                vel=vel, acc=acc, ovl=ovl, blendR=-1, config=1)
        print(f"NewSplinePoint 4 rtn is {rtn}")

        robot.NewSplineEnd()

        robot.CloseRPC()


    if __name__ == "__main__":
        main()