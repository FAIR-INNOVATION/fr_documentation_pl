Urządzenia peryferyjne robota
==============================

.. toctree:: 
    :maxdepth: 5

Konfiguracja chwytaka
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetGripperConfig(company,device,softversion=0,bus=0)``"
    "Opis", "Konfiguracja chwytaka"
    "Parametry wymagane", "- ``company``: Producent chwytaka, 1-Robotiq, 2-Huiling, 3-Tianji, 4-Dahuan, 5-Zhixing;
    - ``device``: Numer urządzenia, Robotiq(0-2F-85 series), Huiling(0-NK series,1-Z-EFG-100), Tianji(0-TEG-110), Dahuan(0-PGI-140), Zhixing(0-CTPM2F20)"
    "Parametry domyślne", "- ``softversion``: Numer wersji oprogramowania, tymczasowo nieużywane, domyślnie 0;
    - ``bus``: Pozycja magistrali końcowej urządzenia, tymczasowo nieużywane, domyślnie 0;"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode "

Pobieranie konfiguracji chwytaka
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetGripperConfig()``"
    "Opis", "Pobieranie konfiguracji chwytaka"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode 
    - ``[number,company,device,softversion]``: number, Numer chwytaka; company, Producent chwytaka, 1-Robotiq, 2-Huiling, 3-Tianji, 4-Dahuan, 5-Zhixing; device, Numer urządzenia, Robotiq(0-2F-85 series), Huiling(0-NK series,1-Z-EFG-100), Tianji(0-TEG-110), Dahuan(0-PGI-140), Zhixing(0-CTPM2F20); softvesion, Numer wersji oprogramowania, tymczasowo nieużywane, domyślnie 0."

Aktywacja chwytaka
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ActGripper(index,action)``"
    "Opis", "Aktywacja chwytaka"
    "Parametry wymagane", "- ``index``: Numer chwytaka;
    - ``action``: 0-reset, 1-aktywacja"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode "

Sterowanie chwytakiem
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``MoveGripper(index,pos,vel,force,maxtime,block,type,rotNum,rotVel,rotTorque)``"
    "Opis", "Sterowanie chwytakiem"
    "Parametry wymagane", "- ``index``: Numer chwytaka;
    - ``pos``: Procent pozycji, zakres [0~100];
    - ``vel``: Procent prędkości, zakres [0~100];
    - ``force``: Procent momentu, zakres [0~100];
    - ``maxtime``: Maksymalny czas oczekiwania, zakres [0~30000], jednostka [ms];
    - ``block``: 0-blokujący, 1-nieblokujący;
    - ``type``: Typ chwytaka, 0-chwytak równoległy; 1-chwytak obrotowy;
    - ``rotNum``: rotNum Liczba obrotów;
    - ``rotVel``: Procent prędkości obrotowej [0-100];
    - ``rotTorque``: Procent momentu obrotowego [0-100]."
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode "

Pobieranie stanu ruchu chwytaka
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetGripperMotionDone()``"
    "Opis", "Pobieranie stanu ruchu chwytaka"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode 
    - ``[fault,status]``: Stan ruchu chwytaka, fault:0-brak błędu, 1-jest błąd; status:0-ruch niezakończony, 1-ruch zakończony"

Pobieranie stanu aktywacji chwytaka
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetGripperActivateStatus()``"
    "Opis", "Pobieranie stanu aktywacji chwytaka"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode 
    - ``fault``: 0-brak błędu, 1-jest błąd
    - ``gripper_active``: bit0~bit15 odpowiada numerom chwytaka 0~15, bit=0 oznacza nieaktywny, bit=1 oznacza aktywny"

Pobieranie pozycji chwytaka
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetGripperCurPosition()``"
    "Opis", "Pobieranie pozycji chwytaka"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode 
    - ``fault``: 0-brak błędu, 1-jest błąd
    - ``position``: Procent pozycji, zakres 0~100%"

Pobieranie prędkości chwytaka
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetGripperCurSpeed()``"
    "Opis", "Pobieranie prędkości chwytaka"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode 
    - ``fault``: 0-brak błędu, 1-jest błąd
    - ``speed``: Procent prędkości, zakres 0~100%"

Pobieranie prądu chwytaka
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetGripperCurCurrent()``"
    "Opis", "Pobieranie prądu chwytaka"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode 
    - ``fault``: 0-brak błędu, 1-jest błąd
    - ``current``: Procent prądu, zakres 0~100%"

Pobieranie napięcia chwytaka
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetGripperVoltage()``"
    "Opis", "Pobieranie napięcia chwytaka"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode 
    - ``fault``: 0-brak błędu, 1-jest błąd
    - ``voltage``: Napięcie, jednostka 0.1V"

Pobieranie temperatury chwytaka
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetGripperTemp()``"
    "Opis", "Pobieranie temperatury chwytaka"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode 
    - ``fault``: 0-brak błędu, 1-jest błąd
    - ``temp``: Temperatura, jednostka ℃"

Obliczenie punktu wstępnego chwytania - wizja
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ComputePrePick(desc_pos, zlength, zangle)``"
    "Opis", "Obliczenie punktu wstępnego chwytania - wizja"
    "Parametry wymagane", "- ``desc_pos``: Pozycja kartezjańska punktu chwytania;
    - ``zlength``: Przesunięcie osi Z;
    - ``zangle``: Przesunięcie obrotu wokół osi Z"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode 
    - ``pre_pos``: Pozycja kartezjańska punktu wstępnego"

Obliczenie punktu wycofania - wizja
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ComputePostPick(desc_pos, zlength, zangle)``"
    "Opis", "Obliczenie punktu wycofania - wizja"
    "Parametry wymagane", "- ``desc_pos``: Pozycja kartezjańska punktu chwytania;
    - ``zlength``: Przesunięcie osi Z;
    - ``zangle``: Przesunięcie obrotu wokół osi Z"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode 
    - ``post_pos``: Pozycja kartezjańska punktu wycofania"

Przykład kodu operacji chwytakiem robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 

    from fairino import Robot
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    company = 4
    device = 0
    softversion = 0
    bus = 2
    index = 2
    act = 0
    max_time = 30000
    block = 0
    status = 0
    fault = 0
    active_status = 0
    current_pos = 0
    current = 0
    voltage = 0
    temp = 0
    speed = 0
    robot.SetGripperConfig(company, device, softversion, bus)
    time.sleep(1)
    error,[company, device, softversion, bus] = robot.GetGripperConfig()
    print(f"gripper config:{company},{device},{softversion},{bus}")
    robot.ActGripper(index, act)
    time.sleep(1)
    act = 1
    robot.ActGripper(index, act)
    time.sleep(1)
    error = robot.MoveGripper(index, 90, 50, 50, max_time, block, 0, 0, 0, 0)
    print(f"MoveGripper retval is:{error}")
    time.sleep(1)
    error = robot.MoveGripper(index, 30, 50, 0, max_time, block, 0, 0, 0, 0)
    print(f"MoveGripper retval is:{error}")
    error, [fault, status] = robot.GetGripperMotionDone()
    print(f"motion status:{fault},{status}")
    error, [fault, active_status] = robot.GetGripperActivateStatus()
    print(f"gripper active fault is:{fault},status is:{active_status}")
    error, [fault, current_pos] = robot.GetGripperCurPosition()
    print(f"fault is:{fault},current position is:{current_pos}")
    error, [fault, current] = robot.GetGripperCurCurrent()
    print(f"fault is:{fault},current current is:{current}")
    error, [fault, voltage] = robot.GetGripperVoltage()
    print(f"fault is:{fault},current voltage is:{voltage}")
    error, [fault, temp] = robot.GetGripperTemp()
    print(f"fault is:{fault},current temperature is:{temp}")
    error, [fault, speed] = robot.GetGripperCurSpeed()
    print(f"fault is:{fault},current speed is:{speed}")
    retval = 0
    prepick_pose = [0.0]*6
    postpick_pose = [0.0]*6
    p1Desc = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    p2Desc = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    retval, prepick_pose = robot.ComputePrePick(p1Desc, 10, 0)
    print(f"ComputePrePick retval is:{retval}")
    print(f"xyz is:{prepick_pose[0]},{prepick_pose[1]},{prepick_pose[2]};rpy is:{prepick_pose[3]},{prepick_pose[4]},{prepick_pose[5]}")
    retval, postpick_pose = robot.ComputePostPick(p2Desc, -10, 0)
    print(f"ComputePostPick retval is:{retval}")
    print(f"xyz is:{postpick_pose[0]},{postpick_pose[1]},{postpick_pose[2]};rpy is:{postpick_pose[3]},{postpick_pose[4]},{postpick_pose[5]}")
    robot.CloseRPC()

Pobieranie liczby obrotów chwytaka obrotowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetGripperRotNum()``"
    "Opis", "Pobieranie liczby obrotów chwytaka obrotowego"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode 
    - ``fault``: 0-brak błędu, 1-jest błąd
    - ``num``: Liczba obrotów"

Pobieranie procentu prędkości obrotowej chwytaka obrotowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetGripperRotSpeed()``"
    "Opis", "Pobieranie procentu prędkości obrotowej chwytaka obrotowego"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode 
    - ``fault``: 0-brak błędu, 1-jest błąd
    - ``speed``: Procent prędkości obrotowej"

Pobieranie procentu momentu obrotowego chwytaka obrotowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetGripperRotTorque()``"
    "Opis", "Pobieranie procentu momentu obrotowego chwytaka obrotowego"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode 
    - ``fault``: 0-brak błędu, 1-jest błąd
    - ``torque``: Procent momentu obrotowego"

Przykład kodu pobrania stanu chwytaka obrotowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 

    from fairino import Robot
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    fault = 0
    rotNum = 0.0
    rotSpeed = 0
    rotTorque = 0
    error,fault, rotNum = robot.GetGripperRotNum()
    error,fault, rotSpeed = robot.GetGripperRotSpeed()
    error,fault, rotTorque = robot.GetGripperRotTorque()
    print(f"gripper rot num:{rotNum},gripper rotSpeed:{rotSpeed},gripper rotTorque:{rotTorque}")
    robot.CloseRPC()

Uruchomienie, zatrzymanie przenośnika taśmowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ConveyorStartEnd(status)``"
    "Opis", "Uruchomienie, zatrzymanie przenośnika taśmowego"
    "Parametry wymagane", "- ``status``: Stan przenośnika, 1-uruchom, 0-zatrzymaj"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Rejestracja punktu detekcji IO
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ConveyorPointIORecord()``"
    "Opis", "Rejestracja punktu detekcji IO"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Rejestracja punktu A
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ConveyorPointARecord()``"
    "Opis", "Rejestracja punktu A"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Rejestracja punktu odniesienia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ConveyorRefPointRecord()``"
    "Opis", "Rejestracja punktu odniesienia"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Rejestracja punktu B
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ConveyorPointBRecord()``"
    "Opis", "Rejestracja punktu B"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Detekcja IO przedmiotu na przenośniku
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ConveyorIODetect(max_t)``"
    "Opis", "Detekcja IO przedmiotu na przenośniku"
    "Parametry wymagane", "- ``max_t``: Maksymalny czas detekcji, jednostka ms"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Pobieranie bieżącej pozycji przedmiotu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ConveyorGetTrackData(mode)``"
    "Opis", "Pobieranie bieżącej pozycji przedmiotu"
    "Parametry wymagane", "- ``mode``: 1-śledzenie i chwytanie 2-śledzenie ruchu 3-śledzenie TPD"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Rozpoczęcie śledzenia przenośnika
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ConveyorTrackStart(status)``"
    "Opis", "Rozpoczęcie śledzenia przenośnika"
    "Parametry wymagane", "- ``status``: Stan, 1-uruchom, 0-zatrzymaj"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Zatrzymanie śledzenia przenośnika
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ConveyorTrackEnd()``"
    "Opis", "Zatrzymanie śledzenia przenośnika"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Konfiguracja parametrów przenośnika
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ConveyorSetParam(param, followType, startDis, endDis)``"
    "Opis", "Konfiguracja parametrów przenośnika"
    "Parametry wymagane", "- ``param``: = [encChannel,resolution,lead,wpAxis,vision,speedRadio] 
                    - ``encChannel``: Kanał enkodera 1-2
                    - ``resolution``: Rozdzielczość enkodera - liczba impulsów na jeden obrót enkodera
                    - ``lead``: Przełożenie mechaniczne - odległość przejścia przenośnika na jeden obrót enkodera
                    - ``wpAxis``: Numer układu przedmiotu dla funkcji śledzenia ruchu wybierz numer układu przedmiotu, dla śledzenia chwytania, śledzenia TPD ustaw na 0
                    - ``vision``: Czy z wizją 0-nie 1-tak,
                    - ``speedRadio``: Współczynnik prędkości - dla śledzenia chwytania przenośnika zakres prędkości (1-100), dla śledzenia ruchu, śledzenia TPD ustaw na 1
    - ``followType``: Typ śledzenia ruchu, 0-śledzenie ruchu; 1-śledzenie kontrolne"
    "Parametry domyślne", "- ``startDis``: Należy ustawić dla śledzenia kontrolnego, Odległość początkowa śledzenia, -1: automatyczne obliczenie (automatyczne śledzenie kontrolne po dotarciu przedmiotu pod robota), jednostka mm, wartość domyślna 0
    - ``endDis``: Należy ustawić dla śledzenia kontrolnego, Odległość końcowa śledzenia, jednostka mm, wartość domyślna 100"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Kompensacja punktu chwytania przenośnika
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ConveyorCatchPointComp(cmp)``"
    "Opis", "Kompensacja punktu chwytania przenośnika"
    "Parametry wymagane", "- ``cmp``: Pozycja kompensacji [x,y,z]"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ruch liniowy
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ConveyorTrackMoveL(name,tool,wobj,vel=20,acc=100,ovl=100,blendR=-1.0)``"
    "Opis", "Ruch liniowy"
    "Parametry wymagane", "- ``name``: cvrCatchPoint lub cvrRaisePoint
    - ``tool``: Numer narzędzia
    - ``wobj``: Numer przedmiotu"
    "Parametry domyślne", "- ``vel``: Prędkość domyślnie 20
    - ``acc``: Przyspieszenie domyślnie 100
    - ``ovl``: Współczynnik skalowania prędkości domyślnie 100
    - ``blendR``: [-1.0]-ruch do pozycji (blokujący), [0~1000]-promień wygładzania (nieblokujący), jednostka [mm] domyślnie -1.0"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Detekcja wejścia komunikacyjnego przenośnika
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ConveyorComDetect(timeout)``"
    "Opis", "Detekcja wejścia komunikacyjnego przenośnika"
    "Parametry wymagane", "- ``timeout``: Czas oczekiwania na timeout ms"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Wyzwolenie detekcji wejścia komunikacyjnego przenośnika
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ConveyorComDetectTrigger()``"
    "Opis", "Wyzwolenie detekcji wejścia komunikacyjnego przenośnika"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Przykład kodu operacji przenośnika robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    retval = robot.ConveyorStartEnd(1)
    print(f"ConveyorStartEnd retval is:{retval}")
    retval = robot.ConveyorPointIORecord()
    print(f"ConveyorPointIORecord retval is:{retval}")
    retval = robot.ConveyorPointARecord()
    print(f"ConveyorPointARecord retval is:{retval}")
    retval = robot.ConveyorRefPointRecord()
    print(f"ConveyorRefPointRecord retval is:{retval}")
    retval = robot.ConveyorPointBRecord()
    print(f"ConveyorPointBRecord retval is:{retval}")
    retval = robot.ConveyorStartEnd(0)
    print(f"ConveyorStartEnd retval is:{retval}")
    param = [1.0, 10000.0, 200.0, 0.0, 0.0, 20.0]
    retval = robot.ConveyorSetParam(param,0)
    print(f"ConveyorSetParam retval is:{retval}")
    cmp = [0.0, 0.0, 0.0]
    retval = robot.ConveyorCatchPointComp(cmp)
    print(f"ConveyorCatchPointComp retval is:{retval}")
    index = 1
    max_time = 30000
    block = 0
    retval = 0
    p1Desc = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    p2Desc = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    retval = robot.MoveCart(p1Desc, 1, 0, 100.0)
    print(f"MoveCart retval is:{retval}")
    retval = robot.WaitMs(1)
    print(f"WaitMs retval is:{retval}")
    retval = robot.ConveyorIODetect(10000)
    print(f"ConveyorIODetect retval is:{retval}")
    retval = robot.ConveyorGetTrackData(1)
    print(f"ConveyorGetTrackData retval is:{retval}")
    retval = robot.ConveyorTrackStart(1)
    print(f"ConveyorTrackStart retval is:{retval}")
    retval = robot.ConveyorTrackMoveL("cvrCatchPoint", 1, 0, 100)
    print(f"TrackMoveL retval is:{retval}")
    retval = robot.MoveGripper(index, 51, 40, 30, max_time, block, 0, 0, 0, 0)
    print(f"MoveGripper retval is:{retval}")
    retval = robot.ConveyorTrackMoveL("cvrRaisePoint", 1, 0, 100)
    print(f"TrackMoveL retval is:{retval}")
    retval = robot.ConveyorTrackEnd()
    print(f"ConveyorTrackEnd retval is:{retval}")
    robot.MoveCart(p2Desc, 1, 0, 100.0, 100.0)
    retval = robot.MoveGripper(index, 100, 40, 10, max_time, block, 0, 0, 0, 0)
    print(f"MoveGripper retval is:{retval}")
    robot.CloseRPC()

Konfiguracja czujnika końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AxleSensorConfig(idCompany, idDevice, idSoftware, idBus)``"
    "Opis", "Konfiguracja czujnika końcowego"
    "Parametry wymagane", "
    - ``idCompany``: Producent, 18-JUNKONG; 25-HUIDE
    - ``idDevice``: Typ, 0-JUNKONG/RYR6T.V1.0
    - ``idSoftware``: Wersja oprogramowania, 0-J1.0/HuiDe1.0 (tymczasowo niedostępne)
    - ``idBus``: Pozycja podłączenia, 1-port końcowy 1; 2-port końcowy 2...8-port końcowy 8 (tymczasowo niedostępne)
    "
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Pobieranie konfiguracji czujnika końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AxleSensorConfigGet()``"
    "Opis", "Pobieranie konfiguracji czujnika końcowego"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``idCompany``: Producent, 18-JUNKONG; 25-HUIDE
    - ``idDevice``: Typ, 0-JUNKONG/RYR6T.V1.0"
        
Aktywacja czujnika końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AxleSensorActivate(actFlag)``"
    "Opis", "Aktywacja czujnika końcowego"
    "Parametry wymagane", "``actFlag``: 0-reset; 1-aktywacja"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``coord``: Wartość układu współrzędnych [x,y,z,rx,ry,rz]"

Zapis do rejestru czujnika końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AxleSensorRegWrite(devAddr, regHAddr, regLAddr, regNum, data1, data2, isNoBlock)``"
    "Opis", "Zapis do rejestru czujnika końcowego"
    "Parametry wymagane", "- ``devAddr``: Numer adresu urządzenia 0-255
    - ``regHAddr``: Adres rejestru wysoki 8 bitów
    - ``regLAddr``: Adres rejestru niski 8 bitów
    - ``regNum``: Liczba rejestrów 0-255
    - ``data1``: Wartość do zapisu do rejestru 1
    - ``data2``: Wartość do zapisu do rejestru 2
    - ``isNoBlock``: Czy blokować 0-blokujący; 1-nieblokujący"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode "

Przykład kodu czujnika końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    robot.AxleSensorConfig(18, 0, 0, 1)
    error, company, type = robot.AxleSensorConfigGet()
    print(f"company is:{company},type is:{type}")
    rtn = robot.AxleSensorActivate(1)
    print(f"AxleSensorActivate rtn is:{rtn}")
    time.sleep(1)
    rtn = robot.AxleSensorRegWrite(1, 4, 6, 1, 0, 0, 0)
    print(f"AxleSensorRegWrite rtn is:{rtn}")
    robot.CloseRPC()

Pobieranie protokołu urządzeń peryferyjnych robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetExDevProtocol()``"
    "Opis", "Pobieranie protokołu urządzeń peryferyjnych robota"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode; 
    - ``protocol``: Numer protokołu urządzeń peryferyjnych robota 4096-karta sterująca osią rozszerzenia; 4097-ModbusSlave; 4098-ModbusMaster"

Ustawianie protokołu urządzeń peryferyjnych robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetExDevProtocol(protocol)``"
    "Opis", "Ustawianie protokołu urządzeń peryferyjnych robota"
    "Parametry wymagane", "- ``protocol``: Numer protokołu urządzeń peryferyjnych robota 4096-karta sterująca osią rozszerzenia; 4097-ModbusSlave; 4098-ModbusMaster"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Przykład kodu ustawiania protokołu urządzeń peryferyjnych robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 

    from fairino import Robot
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    protocol = 4096
    rtn = robot.SetExDevProtocol(protocol)
    print(f"SetExDevProtocol rtn:{rtn}")
    rtn, protocol = robot.GetExDevProtocol()
    print(f"GetExDevProtocol rtn:{rtn},protocol is:{protocol}")
    robot.CloseRPC()


Pobieranie parametrów komunikacji końcowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetAxleCommunicationParam()``"
    "Opis", "Pobieranie parametrów komunikacji końcowej"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode 
    - ``baudRate``: Prędkość transmisji: obsługiwane 1-9600, 2-14400, 3-19200, 4-38400, 5-56000, 6-67600, 7-115200, 8-128000
    - ``dataBit``: Bity danych: obsługiwane (8,9), obecnie często używane 8
    - ``stopBit``: Bity stopu: 1-1, 2-0.5, 3-2, 4-1.5, obecnie często używane 1
    - ``verify``: Bit parzystości: 0-None, 1-Odd, 2-Even, obecnie często używane 0
    - ``timeout``: Czas timeout: 1~1000 ms, wartość ta musi być odpowiednio dostosowana do urządzenia peryferyjnego
    - ``timeoutTimes``: Liczba timeoutów: 1~10, głównie do ponownego wysyłania po czasie, aby zmniejszyć sporadyczne anomalie i poprawić doświadczenie użytkownika
    - ``period``: Odstęp czasu instrukcji okresowych: 1~1000 ms, głównie dla odstępu czasu każdego wysyłania instrukcji okresowych"

Ustawianie parametrów komunikacji końcowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetAxleCommunicationParam(baudRate, dataBit, stopBit, verify, timeout, timeoutTimes, period)``"
    "Opis", "Ustawianie parametrów komunikacji końcowej"
    "Parametry wymagane", "- ``baudRate``: Prędkość transmisji: obsługiwane 1-9600, 2-14400, 3-19200, 4-38400, 5-56000, 6-67600, 7-115200, 8-128000
    - ``dataBit``: Bity danych: obsługiwane (8,9), obecnie często używane 8
    - ``stopBit``: Bity stopu: 1-1, 2-0.5, 3-2, 4-1.5, obecnie często używane 1
    - ``verify``: Bit parzystości: 0-None, 1-Odd, 2-Even, obecnie często używane 0
    - ``timeout``: Czas timeout: 1~1000 ms, wartość ta musi być odpowiednio dostosowana do urządzenia peryferyjnego
    - ``timeoutTimes``: Liczba timeoutów: 1~10, głównie do ponownego wysyłania po czasie, aby zmniejszyć sporadyczne anomalie i poprawić doświadczenie użytkownika
    - ``period``: Odstęp czasu instrukcji okresowych: 1~1000 ms, głównie dla odstępu czasu każdego wysyłania instrukcji okresowych"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode "

Ustawianie typu transferu pliku końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetAxleFileType(type)``"
    "Opis", "Ustawianie typu transferu pliku końcowego"
    "Parametry wymagane", "- ``type``: 1-plik aktualizacji MCU, 2-plik LUA"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode "

Ustawianie włączenia wykonania LUA końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetAxleLuaEnable(enable)``"
    "Opis", "Ustawianie włączenia wykonania LUA końcowego"
    "Parametry wymagane", "- ``enable``: 0-niewłączony; 1-włączony"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode "

Odnowienie błędu wyjątkowego pliku LUA końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetRecoverAxleLuaErr(enable)``"
    "Opis", "Odnowienie błędu wyjątkowego pliku LUA końcowego"
    "Parametry wymagane", "- ``status``: 0-nie odnawiaj; 1-odnów"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode "

Pobieranie stanu włączenia wykonania LUA końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetAxleLuaEnableStatus()``"
    "Opis", "Pobieranie stanu włączenia wykonania LUA końcowego"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode 
    - ``enable``: 0-niewłączony; 1-włączony"

Ustawianie typu włączenia urządzenia końcowego LUA
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetAxleLuaEnableDeviceType(forceSensorEnable, gripperEnable, IOEnable)``"
    "Opis", "Ustawianie typu włączenia urządzenia końcowego LUA"
    "Parametry wymagane", "- ``forceSensorEnable``: Stan włączenia czujnika siły, 0-niewłączony; 1-włączony
    - ``gripperEnable``: Stan włączenia chwytaka, 0-niewłączony; 1-włączony
    - ``IOEnable``: Stan włączenia urządzenia IO, 0-niewłączony; 1-włączony"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode "

Pobieranie typu włączenia urządzenia końcowego LUA
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetAxleLuaEnableDeviceType()``"
    "Opis", "Pobieranie typu włączenia urządzenia końcowego LUA"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode 
    - ``forceSensorEnable``: Stan włączenia czujnika siły, 0-niewłączony; 1-włączony
    - ``gripperEnable``: Stan włączenia chwytaka, 0-niewłączony; 1-włączony
    - ``IOEnable``: Stan włączenia urządzenia IO, 0-niewłączony; 1-włączony"

Pobieranie aktualnie skonfigurowanego urządzenia końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetAxleLuaEnableDevice()``"
    "Opis", "Pobieranie aktualnie skonfigurowanego urządzenia końcowego"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode 
    - ``forceSensorEnable[8]``: Stan włączenia czujnika siły, 0-niewłączony; 1-włączony
    - ``gripperEnable[8]``: Stan włączenia chwytaka, 0-niewłączony; 1-włączony
    - ``IOEnable[8]``: Stan włączenia urządzenia IO, 0-niewłączony; 1-włączony"

Ustawianie włączenia funkcji sterowania ruchem chwytaka
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetAxleLuaGripperFunc(id, func)``"
    "Opis", "Ustawianie włączenia funkcji sterowania ruchem chwytaka"
    "Parametry wymagane", "- ``id``: Numer urządzenia chwytaka
    - ``func``: 0-włączenie chwytaka; 1-inicjalizacja chwytaka; 2-ustawienie pozycji; 3-ustawienie prędkości; 4-ustawienie momentu; 6-odczyt stanu chwytaka; 7-odczyt stanu inicjalizacji; 8-odczyt kodu błędu; 9-odczyt pozycji; 10-odczyt prędkości; 11-odczyt momentu, 12-15 zarezerwowane"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode "

Pobieranie włączenia funkcji sterowania ruchem chwytaka
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetAxleLuaGripperFunc(id)``"
    "Opis", "Pobieranie włączenia funkcji sterowania ruchem chwytaka"
    "Parametry wymagane", "- ``id``: Numer urządzenia chwytaka"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode 
    - ``func``: 0-włączenie chwytaka; 1-inicjalizacja chwytaka; 2-ustawienie pozycji; 3-ustawienie prędkości; 4-ustawienie momentu; 6-odczyt stanu chwytaka; 7-odczyt stanu inicjalizacji; 8-odczyt kodu błędu; 9-odczyt pozycji; 10-odczyt prędkości; 11-odczyt momentu, 12-15 zarezerwowane"

Zapis pliku węzła podrzędnego Ethercat robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SlaveFileWrite(type,slaveID,fileName)``"
    "Opis", "Zapis pliku węzła podrzędnego Ethercat robota"
    "Parametry wymagane", "- ``type``: Typ pliku węzła podrzędnego, 1-plik aktualizacji węzła podrzędnego; 2-plik konfiguracyjny węzła podrzędnego
    - ``slaveID``: Numer węzła podrzędnego
    - ``fileName``: Nazwa przesyłanego pliku"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Przesłanie pliku protokołu otwartego LUA końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AxleLuaUpload(filePath)``"
    "Opis", "Przesłanie pliku protokołu otwartego LUA końcowego"
    "Parametry wymagane", "- ``filePath``: Ścieżka lokalnego pliku lua .../AXLE_LUA_End_DaHuan.lua"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Wprowadzenie węzła podrzędnego Ethercat robota w tryb boot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetSysServoBootMode(filePath)``"
    "Opis", "Wprowadzenie węzła podrzędnego Ethercat robota w tryb boot"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Przykład kodu operacji na pliku LUA końcowego robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 

    from fairino import Robot
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    robot.AxleLuaUpload("D://zUP/AXLE_LUA_End_DaHuan.lua")
    param = [7, 8, 1, 0, 5, 3, 1]  # parametry odpowiadające AxleComParam
    robot.SetAxleCommunicationParam(7, 8, 1, 0, 5, 3, 1)
    error,getParam0,getParam1,getParam2,getParam3,getParam4,getParam5,getParam6 = robot.GetAxleCommunicationParam()
    print(f"GetAxleCommunicationParam param is:{getParam0} {getParam1} {getParam2} {getParam3} {getParam4} {getParam5} {getParam6}")
    robot.SetAxleLuaEnable(1)
    error,luaEnableStatus = robot.GetAxleLuaEnableStatus()
    robot.SetAxleLuaEnableDeviceType(0, 1, 0)
    error,forceEnable, gripperEnable, ioEnable = robot.GetAxleLuaEnableDeviceType()
    print(f"GetAxleLuaEnableDeviceType param is:{forceEnable} {gripperEnable} {ioEnable}")
    func = [1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1]
    robot.SetAxleLuaGripperFunc(1, func)
    error,getFunc = robot.GetAxleLuaGripperFunc(1)
    error,getforceEnable, getgripperEnable, getioEnable = robot.GetAxleLuaEnableDevice()
    print("\ngetforceEnable status:", end=" ")
    for i in range(8):
        print(f"{getforceEnable[i]},", end="")
    print("\ngetgripperEnable status:", end=" ")
    for i in range(8):
        print(f"{getgripperEnable[i]},", end="")
    print("\ngetioEnable status:", end=" ")
    for i in range(8):
        print(f"{getioEnable[i]},", end="")
    print()
    robot.ActGripper(1, 0)
    time.sleep(2)
    robot.ActGripper(1, 1)
    time.sleep(2)
    robot.MoveGripper(1, 90, 10, 100, 50000, 0, 0, 0, 0, 0)
    while True:
        error,pkg = robot.GetRobotRealTimeState()
        print(f"gripper pos is:{pkg.gripper_position}")
        time.sleep(0.1)
    robot.CloseRPC()

    
Pobieranie stanu przycisków SmartTool
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetSmarttoolBtnState()``"
    "Opis", "Pobieranie stanu przycisków SmartTool"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``state``: Stan przycisków uchwytu SmartTool; (bit0:0-komunikacja normalna; 1-utrata komunikacji; bit1-cofnij operację; bit2-wyczyść program; bit3-przycisk A; bit4-przycisk B; bit5-przycisk C; bit6-przycisk D; bit7-przycisk E; bit8-przycisk IO; bit9-ręczny/automatyczny; bit10-start)"

Przykład kodu przycisków SmartTool
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    while True:
        error,state = robot.GetSmarttoolBtnState()
        print(f"{state:016b}")
        time.sleep(0.1)

Ustawianie wykrywania siły obciążenia przed włączeniem przeciągania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetTorqueDetectionSwitch(flag)``"
    "Opis", "Ustawianie wykrywania siły obciążenia przed włączeniem przeciągania"
    "Parametry wymagane", "- ``flag``: 0-wyłączone; 1-włączone"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Funkcja włączania/wyłączania urządzenia peryferyjnego laserowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LaserTrackingLaserOnOff(OnOff, weldId)``"
    "Opis", "Funkcja włączania/wyłączania urządzenia peryferyjnego laserowego"
    "Parametry wymagane", "- ``OnOff``: 0-wyłączone; 1-włączone"
    "Parametry domyślne", "- ``weldId``: ID spoiny domyślnie 0"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Funkcja rozpoczęcia/zakończenia śledzenia laserowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LaserTrackingTrackOnOff(OnOff, coordId)``"
    "Opis", "Funkcja rozpoczęcia/zakończenia śledzenia laserowego"
    "Parametry wymagane", "- ``OnOff``: 0-wyłączone; 1-włączone
    - ``coordId``: Numer układu narzędzia urządzenia peryferyjnego laserowego"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Poszukiwanie pozycji laserowej - stały kierunek
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LaserTrackingSearchStart_xyz(direction, vel, distance, timeout, posSensorNum)``"
    "Opis", "Poszukiwanie pozycji laserowej - stały kierunek"
    "Parametry wymagane", "- ``direction``: 0-x+ 1-x- 2-y+ 3-y- 4-z+ 5-z-
    - ``vel``: Prędkość jednostka%
    - ``distance``: Maksymalna odległość poszukiwania jednostka mm
    - ``timeout``: Czas timeout poszukiwania jednostka ms
    - ``posSensorNum``: Numer narzędzia skalibrowanego lasera"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Poszukiwanie pozycji laserowej - dowolny kierunek
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LaserTrackingSearchStart_point(directionPoint, vel, distance, timeout, posSensorNum)``"
    "Opis", "Poszukiwanie pozycji laserowej - dowolny kierunek"
    "Parametry wymagane", "- ``directionPoint``: Współrzędne xyz punktu wejściowego poszukiwania, [x,y,z]
    - ``vel``: Prędkość jednostka%
    - ``distance``: Maksymalna odległość poszukiwania jednostka mm
    - ``timeout``: Czas timeout poszukiwania jednostka ms
    - ``posSensorNum``: Numer narzędzia skalibrowanego lasera"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Konfiguracja IP lasera
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LaserTrackingSensorConfig(ip, port)``"
    "Opis", "Konfiguracja IP lasera"
    "Parametry wymagane", "- ``ip``: Adres IP urządzenia peryferyjnego laserowego
    - ``port``: Numer portu urządzenia peryferyjnego laserowego"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Konfiguracja okresu próbkowania urządzenia peryferyjnego laserowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LaserTrackingSensorSamplePeriod(period)``"
    "Opis", "Konfiguracja okresu próbkowania urządzenia peryferyjnego laserowego"
    "Parametry wymagane", "- ``period``: Okres próbkowania urządzenia peryferyjnego laserowego jednostka ms"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ładowanie sterownika urządzenia peryferyjnego laserowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LoadPosSensorDriver(type)``"
    "Opis", "Ładowanie sterownika urządzenia peryferyjnego laserowego"
    "Parametry wymagane", "- ``type``: Typ protokołu sterownika urządzenia peryferyjnego laserowego 101-RuiNiu 102-ChuangXiang 103-QuanShi 104-TongZhou 105-AoTai"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Rozładowanie sterownika urządzenia peryferyjnego laserowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``UnLoadPosSensorDriver()``"
    "Opis", "Rozładowanie sterownika urządzenia peryferyjnego laserowego"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Rejestracja ścieżki spoiny laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LaserSensorRecord1(status, delayTime)``"
    "Opis", "Rejestracja ścieżki spoiny laserowej"
    "Parametry wymagane", "- ``status``: 0-zatrzymaj rejestrację 1-śledzenie w czasie rzeczywistym 2-rozpocznij rejestrację
    - ``delayTime``: Czas opóźnienia jednostka ms"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Odtwarzanie ścieżki spoiny laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LaserSensorReplay(delayTime, speed)``"
    "Opis", "Odtwarzanie ścieżki spoiny laserowej"
    "Parametry wymagane", "- ``delayTime``: Czas opóźnienia jednostka ms
    - ``speed``: Prędkość jednostka%"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"
    
Odtwarzanie śledzenia laserowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``MoveLTR()``"
    "Opis", "Odtwarzanie śledzenia laserowego"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Odtwarzanie ścieżki spoiny laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LaserSensorRecordandReplay(delayMode, delayTime, delayDisExAxisNum, delayDis, sensitivePara, int trackMode, int triggerMode, double runTime, speed)``"
    "Opis", "Odtwarzanie ścieżki spoiny laserowej"
    "Parametry wymagane", "- ``delayMode``: Tryb 0-czas opóźnienia 1-odległość opóźnienia
    - ``delayTime``: Czas opóźnienia jednostka ms
    - ``delayDisExAxisNum``: Numer osi rozszerzenia opóźnienia
    - ``delayDis``: Odległość opóźnienia jednostka mm
    - ``sensitivePara``: Współczynnik czułości kompensacji
    - ``trackMode``: Typ śledzenia punktowego. 0-ruch asynchroniczny osi rozszerzenia; 1-robot
    - ``triggerMode``: Sposób wyzwalania śledzenia punktowego. 0-czas śledzenia; 1-IO
    - ``runTime``: Czas śledzenia punktowego robota (s)
    - ``speed``: Prędkość jednostka%"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ruch do początku zapisu ścieżki spoiny
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``MoveToLaserRecordStart(moveType, ovl)``"
    "Opis", "Ruch do początku zapisu ścieżki spoiny"
    "Parametry wymagane", "- ``moveType``: 0-PTP 1-LIN
    - ``ovl``: Prędkość jednostka%"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ruch do końca zapisu ścieżki spoiny
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``MoveToLaserRecordEnd(moveType, ovl)``"
    "Opis", "Ruch do końca zapisu ścieżki spoiny"
    "Parametry wymagane", "- ``moveType``: 0-PTP 1-LIN
    - ``ovl``: Prędkość jednostka%"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ruch do punktu poszukiwanego przez czujnik laserowy
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``MoveToLaserSeamPos(moveFlag, ovl, dataFlag, plateType, trackOffectType, offset)``"
    "Opis", "Ruch do punktu poszukiwanego przez czujnik laserowy"
    "Parametry wymagane", "- ``moveFlag``: Typ ruchu: 0-PTP; 1-LIN
    - ``ovl``: Współczynnik skalowania prędkości, 0-100
    - ``dataFlag``: Wybór danych bufora spoiny: 0-wykonaj dane planowania; 1-wykonaj dane zapisu
    - ``plateType``: Typ blachy: 0-blacha falista; 1-blacha trapezowa; 2-blacha ogrodzeniowa; 3-beczka; 4-stal pancerzowa falista
    - ``trackOffectType``: Typ przesunięcia czujnika laserowego: 0-bez przesunięcia; 1-przesunięcie w układzie bazowym; 2-przesunięcie w układzie narzędzia; 3-przesunięcie surowych danych czujnika laserowego
    - ``offset``: Wartość przesunięcia"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Pobieranie informacji o współrzędnych punktu poszukiwanego przez czujnik laserowy
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetLaserSeamPos(trackOffectType, offset)``"
    "Opis", "Pobieranie informacji o współrzędnych punktu poszukiwanego przez czujnik laserowy"
    "Parametry wymagane", "- ``trackOffectType``: Typ przesunięcia czujnika laserowego: 0-bez przesunięcia; 1-przesunięcie w układzie bazowym; 2-przesunięcie w układzie narzędzia; 3-przesunięcie surowych danych czujnika laserowego
    - ``offset``: Wartość przesunięcia"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``jPos``: Pozycja przegubów [°]
    - ``descPos``: Pozycja kartezjańska [mm]
    - ``tool``: Układ narzędzia
    - ``user``: Układ przedmiotu
    - ``exaxis``: Pozycja osi rozszerzenia [mm]"

Przykład kodu konfiguracji parametrów i debugowania urządzenia peryferyjnego laserowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 

    from fairino import Robot
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    robot.LaserTrackingSensorConfig("192.168.58.20", 5020)
    robot.LaserTrackingSensorSamplePeriod(20)
    robot.LoadPosSensorDriver(101)
    robot.LaserTrackingLaserOnOff(0, 0)
    time.sleep(3)
    robot.LaserTrackingLaserOnOff(1, 0)
    robot.CloseRPC()

Przykład kodu skanowania i odtwarzania ścieżki laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 

    from fairino import Robot
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    robot.OpenLuaUpload("D://zUP/CtrlDev_laser_ruiniu-0117.lua")
    time.sleep(2)
    robot.SetCtrlOpenLUAName(0, "CtrlDev_laser_ruiniu-0117.lua")
    robot.UnloadCtrlOpenLUA(0)
    robot.LoadCtrlOpenLUA(0)
    time.sleep(8)
    i = 0
    while i<10:
        startjointPos = [56.205, -117.951, 141.872, -118.149, -94.217, -122.176]
        startdescPose = [-97.552, -282.855, 26.675, 174.182, -1.338, -91.707]
        exaxisPos = [0.0] * 4
        offdese = [0.0] * 6
        robot.MoveL(desc_pos=startdescPose,tool= 1,user= 0,vel= 100,acc= 100,ovl= 100,blendR= -1,exaxis_pos= exaxisPos,search= 0,offset_flag= 0, offset_pos= offdese,overSpeedStrategy= 1,speedPercent= 1)
        robot.LaserSensorRecord1(2, 10)
        endjointPos = [68.809, -87.100, 121.120, -127.233, -95.038, -109.555]
        enddescPose = [-103.555, -464.234, 13.076, 174.179, -1.344, -91.709]
        robot.MoveL(desc_pos=enddescPose,tool= 1,user= 0,vel= 50,acc= 100,ovl= 100,blendR= -1,exaxis_pos= exaxisPos,search= 0,offset_flag= 0, offset_pos= offdese,overSpeedStrategy= 1,speedPercent= 1)
        robot.LaserSensorRecord1(0, 10)
        robot.MoveToLaserRecordStart(1, 30)
        robot.LaserSensorReplay(10, 100)
        robot.MoveLTR()
        robot.LaserSensorRecord1(0, 10)
        i = i+1
    robot.CloseRPC()

Przykład kodu poszukiwania pozycji laserowej i śledzenia w czasie rzeczywistym
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 

    from fairino import Robot
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    robot.OpenLuaUpload("D://zUP/CtrlDev_laser_ruiniu-0117.lua")
    time.sleep(2)
    robot.SetCtrlOpenLUAName(0, "CtrlDev_laser_ruiniu-0117.lua")
    robot.UnloadCtrlOpenLUA(0)
    robot.LoadCtrlOpenLUA(0)
    time.sleep(8)
    time.sleep(8)
    i = 0
    while i < 10:
        startjointPos = [56.205, -117.951, 141.872, -118.149, -94.217, -122.176]
        startdescPose = [-97.552, -282.855, 26.675, 174.182, -1.338, -91.707]
        exaxisPos = [0.0] * 4
        offdese = [0.0] * 6
        directionPoint = [0.0] * 3
        robot.MoveL(desc_pos=startdescPose,tool= 1,user= 0,vel= 100,acc= 100,ovl= 100,blendR= -1,exaxis_pos= exaxisPos,search= 0,offset_flag= 0, offset_pos= offdese,overSpeedStrategy= 1,speedPercent= 1)
        robot.LaserTrackingSearchStart_xyz(3, 100, 300, 1000, 3)
        robot.LaserTrackingSearchStop()
        robot.MoveToLaserSeamPos(1, 30, 0, 0, 0, offdese)
        robot.LaserTrackingTrackOnOff(1, 3)
        endjointPos = [68.809, -87.100, 121.120, -127.233, -95.038, -109.555]
        enddescPose = [-103.555, -464.234, 13.076, 174.179, -1.344, -91.709]
        robot.MoveL(desc_pos=enddescPose,tool= 1,user= 0,vel= 20,acc= 100,ovl= 100,blendR= -1,exaxis_pos= exaxisPos,search= 0,offset_flag= 0, offset_pos= offdese,overSpeedStrategy= 1,speedPercent= 1)
        robot.LaserTrackingTrackOnOff(0, 3)
        i = i + 1
        print(i)
    robot.CloseRPC()

Przykład kodu śledzenia laserowego z osią rozszerzenia synchronicznie z robotem
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 

    from fairino import Robot
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    startexaxisPos = [0.0, 0.0, 0.0, 0.0]
    seamexaxisPos = [-10.0, 0.0, 0.0, 0.0]
    endexaxisPos = [-30.0, 0.0, 0.0, 0.0]
    offdese = [0.0] * 6
    seamjointPos = [0.0] * 6
    seamdescPose = [0.0] * 6
    i=0
    while i < 10:
        startjointPos = [58.337, -119.628, 146.037, -116.358, -92.224, -117.654]
        startdescPose = [-53.375, -255.363, 0.919, 178.054, 1.077, -94.026]
        robot.ExtAxisSyncMoveJ(joint_pos=startjointPos, tool=1,user= 0,vel= 100,acc= 100, ovl=100,exaxis_pos= startexaxisPos,blendT= -1,offset_flag= 0,offset_pos= offdese)
        ret = robot.LaserTrackingSearchStart_xyz(3, 100, 300, 1000, 2)
        robot.LaserTrackingSearchStop()
        tool = 0
        user = 0
        rnte, seamjointPos, seamdescPose, tool, user, startexaxisPos = robot.GetLaserSeamPos(0, offdese)
        print(f"{seamjointPos[0]},{seamjointPos[1]},{seamjointPos[2]},{seamjointPos[3]},{seamjointPos[4]},{seamjointPos[5]},{seamdescPose[0]},{seamdescPose[1]},{seamdescPose[2]},{seamdescPose[3]},{seamdescPose[4]},{seamdescPose[5]}")
        if ret == 0:
            robot.ExtAxisSyncMoveJ(joint_pos=seamjointPos, tool=1,user= 0,vel= 100,acc= 100, ovl=100,exaxis_pos= seamexaxisPos,blendT= -1,offset_flag= 0,offset_pos= offdese)
            robot.LaserTrackingTrackOnOff(1, 2)
            endjointPos = [70.580, -90.918, 126.593, -125.154, -92.162, -105.403]
            enddescPose = [-53.375, -419.020, 0.920, 178.054, 1.076, -94.026]
            robot.ExtAxisSyncMoveL(desc_pos=enddescPose, tool=1,user= 0,vel= 20,acc= 100, ovl=100,blendR= -1,exaxis_pos= endexaxisPos,offset_pos= offdese)
            robot.LaserTrackingTrackOnOff(0, 2)
        i = i+1
        print(i)
    robot.CloseRPC()

Sterowanie matrycową przyssawką
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetSuckerCtrl(slaveID, len, ctrlValue)``"
    "Opis", "Sterowanie matrycową przyssawką"
    "Parametry wymagane", "- ``slaveID``: Numer węzła podrzędnego
    - ``len``: Długość
    - ``ctrlValue``: Wartość sterowania 1-zassanie z maksymalnym podciśnieniem 2-zassanie z ustawionym podciśnieniem 3-zatrzymanie zassania"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Pobieranie stanu matrycowej przyssawki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetSuckerState(slaveID)``"
    "Opis", "Pobieranie stanu matrycowej przyssawki"
    "Parametry wymagane", "- ``slaveID``: Numer węzła podrzędnego"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``state``: Stan przyssania 0-zwolnienie przedmiotu 1-wykryto pomyślne przyssanie przedmiotu 2-brak przyssania przedmiotu 3-oderwanie przedmiotu
    - ``pressValue``: Bieżące podciśnienie jednostka kpa
    - ``error``: Bieżący kod błędu przyssawki"

Oczekiwanie na stan przyssawki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``WaitSuckerState(slaveID, state, ms)``"
    "Opis", "Oczekiwanie na stan przyssawki"
    "Parametry wymagane", "- ``slaveID``: Numer węzła podrzędnego
    - ``state``: Stan przyssania 0-zwolnienie przedmiotu 1-wykryto pomyślne przyssanie przedmiotu 2-brak przyssania przedmiotu 3-oderwanie przedmiotu
    - ``ms``: Maksymalny czas oczekiwania"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Przykład kodu instrukcji sterowania matrycową przyssawką
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.5

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    robot.OpenLuaUpload("C://项目/外设SDK/CtrlDev_sucker.lua")
    time.sleep(2)
    robot.UnloadCtrlOpenLUA(1)
    robot.LoadCtrlOpenLUA(1)
    time.sleep(1)
    ctrl = bytearray(20)
    ctrl[0] = 1
    robot.SetSuckerCtrl(0, 1, ctrl)
    for i in range(100):
        rtn, state, press_value, error = robot.GetSuckerState(1)
        print(f"sucker1 state is {state}, pressValue is {press_value}, error num is {error}")
        rtn, state, press_value, error = robot.GetSuckerState(12)
        print(f"sucker12 state is {state}, pressValue is {press_value}, error num is {error}")
        time.sleep(0.1)
    ret = robot.WaitSuckerState(1, 1, 100)
    print(f"WaitSuckerState result is {ret}")
    ctrl[0] = 3
    robot.SetSuckerCtrl(1, 1, ctrl)
    robot.SetSuckerCtrl(12, 1, ctrl)
    robot.CloseRPC()

Przesłanie pliku LUA protokołu otwartego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``OpenLuaUpload(filePath)``"
    "Opis", "Przesłanie pliku LUA protokołu otwartego"
    "Parametry wymagane", "- ``filePath``: Ścieżka lokalnego pliku lua protokołu otwartego"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Pobieranie parametrów karty węzła podrzędnego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetFieldBusConfig()``"
    "Opis", "Pobieranie parametrów karty węzła podrzędnego"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``type``: 0-Ethercat, 1-CClink, 3-Ethercat, 4-EIP
    - ``version``: Wersja protokołu
    - ``connState``: 0-niepołączony 1-połączony"

Zapis DO węzła podrzędnego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``FieldBusSlaveWriteDO(DOIndex, wirteNum, status)``"
    "Opis", "Zapis DO węzła podrzędnego"
    "Parametry wymagane", "- ``DOIndex``: Numer DO
    - ``wirteNum``: Liczba do zapisu
    - ``status``: Wartości do zapisu, maksymalnie 8"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Zapis AO węzła podrzędnego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``FieldBusSlaveWriteAO(AOIndex, wirteNum, status)``"
    "Opis", "Zapis AO węzła podrzędnego"
    "Parametry wymagane", "- ``AOIndex``: Numer AO
    - ``wirteNum``: Liczba do zapisu
    - ``status``: Wartości do zapisu, maksymalnie 8"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Odczyt DI węzła podrzędnego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``FieldBusSlaveReadDI(DOIndex, readeNum)``"
    "Opis", "Odczyt DI węzła podrzędnego"
    "Parametry wymagane", "- ``DOIndex``: Numer DI
    - ``readeNum``: Liczba do odczytu"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``status[8]``: Odczytane wartości, maksymalnie 8"

Odczyt AI węzła podrzędnego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``FieldBusSlaveReadAI(AOIndex, readeNum)``"
    "Opis", "Odczyt AI węzła podrzędnego"
    "Parametry wymagane", "- ``AOIndex``: Numer AI
    - ``readeNum``: Liczba do odczytu"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``status[8]``: Odczytane wartości, maksymalnie 8"

Oczekiwanie na wejście rozszerzonego DI
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``FieldBusSlaveWaitDI(DIIndex, status, waitMs)``"
    "Opis", "Oczekiwanie na wejście rozszerzonego DI"
    "Parametry wymagane", "- ``DIIndex``: Numer DI
    - ``status``: 0-niski poziom; 1-wysoki poziom
    - ``waitMs``: Maksymalny czas oczekiwania (ms)"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Oczekiwanie na wejście rozszerzonego AI
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``FieldBusSlaveWaitAI(AIIndex, waitType, value, waitMs)``"
    "Opis", "Oczekiwanie na wejście rozszerzonego AI"
    "Parametry wymagane", "- ``AIIndex``: Numer AI
    - ``waitType``: 0-większe niż; 1-mniejsze niż
    - ``value``: Wartość AI
    - ``waitMs``: Maksymalny czas oczekiwania (ms)"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Przykład kodu instrukcji interfejsów trybu węzła podrzędnego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.5

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    robot.OpenLuaUpload("D://zUP/外设/CtrlDev_field.lua")
    time.sleep(2)
    robot.SetCtrlOpenLUAName(3,"CtrlDev_field.lua")
    robot.UnloadCtrlOpenLUA(3)
    robot.LoadCtrlOpenLUA(3)
    time.sleep(8)
    rtn,type, version, conn_state = robot.GetFieldBusConfig()
    print(f"type is {type}, version is {version}, connState is {conn_state}")
    # Zapis wyjść cyfrowych
    ctrl = [1, 0, 1]  # DO0=1, DO1=0, DO2=1
    robot.FieldBusSlaveWriteDO(0, 3, ctrl)
    # Zapis wyjścia analogowego
    ctrl_ao = [0x1000]  # AO2 = 0x1000
    robot.FieldBusSlaveWriteAO(2, 1, ctrl_ao)
    for i in range(100):
        rtn,di = robot.FieldBusSlaveReadDI(0, 4)
        print(f"DI0 is {di[0]}, DI1 is {di[1]}, DI2 is {di[2]}, DI3 is {di[3]}")
        rtn, ai = robot.FieldBusSlaveReadAI(0, 3)
        print(f"AI0 is {ai[0]}, AI1 is {ai[1]}, AI2 is {ai[2]}")
        time.sleep(0.01)
    ret = robot.FieldBusSlaveWaitDI(0, 1, 100)
    print(f"FieldBusSlaveWaitDI result is {ret}")
    ret = robot.FieldBusSlaveWaitAI(0, 0, 400.00, 100)
    print(f"FieldBusSlaveWaitAI result is {ret}")
    robot.CloseRPC()

Interfejs SDK włączania/wyłączania funkcji przezroczystej transmisji końcowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetAxleGenComEnable(mode)``"
    "Opis", "Włączenie ogólnej funkcji przezroczystej transmisji końcowej"
    "Parametry wymagane", "- ``mode``: Włączenie, 0-wyłączone, 1-włączone"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Interfejs SDK wysyłania i odbierania danych aperiodycznych funkcji przezroczystej transmisji końcowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SndRcvAxleGenComCmdData( len_snd, sndBuff, len_rcv)``"
    "Opis", "Wysłanie danych aperiodycznych przez końcówkę i oczekiwanie na odpowiedź"
    "Parametry wymagane", "
    - ``len_snd``: Długość wysyłania;
    - ``sndBuff[]``: Dane wysyłane;
    - ``len_rcv``: Wybór długości odbioru;
    - ``rcvBuff[]``: Dane odpowiedzi;"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Przykład kodu komunikacji danych aperiodycznych głowicy moxibuscyjnej Beiyikang w oparciu o funkcję przezroczystej transmisji końcowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 

    from time import sleep
    from fairino import Robot
    from ctypes import sizeof
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')

    import time


    def testAxleGenCom(self):

        led_on = [0xAB, 0xBA, 0x12, 0x01, 0x01, 0x79]
        led_off = [0xAB, 0xBA, 0x12, 0x01, 0x00, 0x78]
        version = [0xAB, 0xBA, 0x11, 0x00, 0x76]
        state = [0xAB, 0xBA, 0x1B, 0x01, 0xAA, 0x2B]
        cycleState = [0xAB, 0xBA, 0x12, 0x01, 0x00, 0x78]
        cnt = 1

        p1Joint = [88.708, -86.178, 140.989, -141.825, -89.162, -49.879]
        p1Desc = [188.007, -377.850, 260.207, 178.715, 2.823, -131.466]
        p2Joint = [112.131, -75.554, 126.989, -139.027, -88.044, -26.477]
        p2Desc = [368.003, -377.848, 260.211, 178.715, 2.823, -131.465]

        exaxisPos = [0, 0, 0, 0]
        offdese = [0, 0, 0, 0, 0, 0]

        # Włączenie funkcji przezroczystej transmisji końcowej
        robot.SetAxleGenComEnable(1)
        robot.SetAxleLuaEnable(1)

        while cnt <= 10000:
            # Odczyt numeru wersji
            ret,rcvdata = robot.SndRcvAxleGenComCmdData(len_snd=5, sndBuff=version, len_rcv=10)
            print(ret)
            print(rcvdata)
            print(f"hard version : {rcvdata[4]},hard code:{rcvdata[5]}, soft version:{rcvdata[6]} {rcvdata[7]}, soft code:{rcvdata[8]}")
            if ret != 0:
                break
            time.sleep(1)
            # Odczyt stanu obecności głowicy moxibuscyjnej
            ret,rcvdata = robot.SndRcvAxleGenComCmdData(6, state, 6)
            print(f"state : {rcvdata[4]} ")
            time.sleep(1)
            # Włączenie lasera głowicy moxibuscyjnej
            ret,rcvdata = robot.SndRcvAxleGenComCmdData(6, led_on, 6)
            print(f"led on rcv data is: {rcvdata[0]}, {rcvdata[1]}, {rcvdata[2]}, {rcvdata[3]}, {rcvdata[4]}, {rcvdata[5]}")
            robot.MoveJ(joint_pos=p1Joint, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=exaxisPos, blendT=-1,
                            offset_flag=0, offset_pos=offdese)
            time.sleep(4)
            # Wyłączenie lasera głowicy moxibuscyjnej
            ret, rcvdata = robot.SndRcvAxleGenComCmdData(6, led_off, 6)
            print(f"led off rcv data is: {rcvdata[0]}, {rcvdata[1]}, {rcvdata[2]}, {rcvdata[3]}, {rcvdata[4]}, {rcvdata[5]}")
            robot.MoveJ(joint_pos=p2Joint, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=exaxisPos, blendT=-1,offset_flag=0, offset_pos=offdese)
            time.sleep(1)
            print(f"***********************complate No. {cnt} SDK test*****************************")
            cnt = cnt + 1

        robot.CloseRPC()
        return 0

    testAxleGenCom(robot)
    
Pobranie pliku LUA protokołu otwartego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``OpenLuaDownload(fileName, savePath)``"
    "Opis", "Pobranie pliku LUA protokołu otwartego"
    "Parametry wymagane", "
    - ``fileName``: Nazwa pliku protokołu otwartego CtrlDev_XXX.lua;
    - ``savePath``: Ścieżka zapisu pliku protokołu otwartego;
    "
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"
    
Usunięcie określonego pliku LUA protokołu otwartego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``OpenLuaDelete(fileName)``"
    "Opis", "Usunięcie określonego pliku LUA protokołu otwartego"
    "Parametry wymagane", "
    - ``fileName``: Nazwa pliku lua protokołu otwartego do usunięcia CtrlDev_XXX.lua
    "
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"
    
Usunięcie wszystkich plików LUA protokołu otwartego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``AllOpenLuaDelete()``"
    "Opis", "Usunięcie wszystkich plików LUA protokołu otwartego"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Przykład kodu SDK operacji na pliku lua protokołu otwartego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 

    from time import sleep
    import time
    from fairino import Robot

    # Połączenie z kontrolerem robota
    robot = Robot.RPC('192.168.58.2')


    def TestCtrlOpenLuaOperate(self):
        # Przesłanie pliku Lua do robota
        rtn = robot.OpenLuaUpload("D://zUP/openlua/CtrlDev_WELDING_A.lua")
        print(f"OpenLuaUpload rtn is {rtn}")
        
        rtn = robot.OpenLuaUpload("D://zUP/openlua/CtrlDev_SWDPOLISH.lua")
        print(f"OpenLuaUpload rtn is {rtn}")
        
        # Pobranie pliku Lua z robota
        rtn = robot.OpenLuaDownload("CtrlDev_WELDING_A.lua", "D://zDOWN/")
        print(f"OpenLuaDownload rtn is {rtn}")
        
        rtn = robot.OpenLuaDownload("CtrlDev_SWDPOLISH.lua", "D://zDOWN/")
        print(f"OpenLuaDownload rtn is {rtn}")
        
        # Ustawienie nazwy pliku Lua otwartego sterowania
        rtn = robot.SetCtrlOpenLUAName(0, "CtrlDev_WELDING_A.lua")
        print(f"SetCtrlOpenLUAName rtn is {rtn}")
        
        rtn = robot.SetCtrlOpenLUAName(1, "CtrlDev_SWDPOLISH.lua")
        print(f"SetCtrlOpenLUAName rtn is {rtn}")
        
        # Pobranie nazwy pliku Lua otwartego sterowania
        rtn, name = robot.GetCtrlOpenLUAName()
        print(f"ctrl open lua names : {name[0]}, {name[1]}, {name[2]}, {name[3]}")
        
        # Załadowanie Lua otwartego sterowania
        rtn = robot.LoadCtrlOpenLUA(1)
        print(f"LoadCtrlOpenLUA rtn is {rtn}")
        time.sleep(2)
        
        # Rozładowanie Lua otwartego sterowania
        rtn = robot.UnloadCtrlOpenLUA(1)
        print(f"UnloadCtrlOpenLUA rtn is {rtn}")
        
        # Usunięcie określonego pliku Lua
        rtn = robot.OpenLuaDelete("CtrlDev_WELDING_A.lua")
        print(f"OpenLuaDelete rtn is {rtn}")
        
        # Usunięcie wszystkich plików Lua
        rtn = robot.AllOpenLuaDelete()
        print(f"AllOpenLuaDelete rtn is {rtn}")
        
        # Zamknięcie połączenia
        robot.CloseRPC()
        time.sleep(1)


    # Wywołanie funkcji testowej
    TestCtrlOpenLuaOperate(robot)