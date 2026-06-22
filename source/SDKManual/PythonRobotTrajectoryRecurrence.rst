Odtwarzanie trajektorii robota
===============================

.. toctree:: 
    :maxdepth: 5

Ustawianie parametrów rejestracji trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetTPDParam(name, period_ms, type=1,di_choose=0, do_choose=0)``"
    "Opis", "Ustawianie parametrów rejestracji trajektorii"
    "Parametry wymagane", "- ``name``: Nazwa trajektorii;
    - ``period_ms``: Okres próbkowania, stała wartość, 2 ms, 4 ms lub 8 ms;"
    "Parametry domyślne", "- ``type``: Typ danych, 1-pozycja przegubów;
    - ``di_choose``: Wybór DI, bit0~bit7 odpowiadają DI0~DI7 skrzynki kontrolnej, bit8~bit9 odpowiadają DI0~DI1 końcówki, 0-nie wybieraj, 1-wybierz, domyślnie 0;
    - ``do_choose``: Wybór DO, bit0~bit7 odpowiadają DO0~DO7 skrzynki kontrolnej, bit8~bit9 odpowiadają DO0~DO1 końcówki, 0-nie wybieraj, 1-wybierz, domyślnie 0"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Rozpoczęcie rejestracji trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetTPDStart(name, period_ms, type=1,di_choose=0, do_choose=0)``"
    "Opis", "Rozpoczęcie rejestracji trajektorii"
    "Parametry wymagane", "- ``name``: Nazwa trajektorii;
    - ``period_ms``: Okres próbkowania, stała wartość, 2 ms, 4 ms lub 8 ms;"
    "Parametry domyślne", "- ``type``: Typ danych, 1-pozycja przegubów, domyślnie 1;
    - ``di_choose``: Wybór DI, bit0~bit7 odpowiadają DI0~DI7 skrzynki kontrolnej, bit8~bit9 odpowiadają DI0~DI1 końcówki, 0-nie wybieraj, 1-wybierz, domyślnie 0;
    - ``do_choose``: Wybór DO, bit0~bit7 odpowiadają DO0~DO7 skrzynki kontrolnej, bit8~bit9 odpowiadają DO0~DO1 końcówki, 0-nie wybieraj, 1-wybierz, domyślnie 0"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Zatrzymanie rejestracji trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetWebTPDStop()``"
    "Opis", "Zatrzymanie rejestracji trajektorii"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Usunięcie zarejestrowanej trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetTPDDelete(name)``"
    "Opis", "Usunięcie zarejestrowanej trajektorii"
    "Parametry wymagane", "- ``name``: Nazwa trajektorii"
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
    type = 1
    name = "tpd2025"
    period_ms = 4
    di_choose = 0
    do_choose = 0
    robot.SetTPDParam(name, period_ms)
    robot.Mode(1)
    time.sleep(1)
    robot.DragTeachSwitch(1)
    robot.SetTPDStart(name, period_ms)
    print("SetTPDStart")
    time.sleep(10)
    robot.SetWebTPDStop()
    robot.DragTeachSwitch(0)
    robot.CloseRPC()

Wstępne ładowanie trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LoadTPD(name)``"
    "Opis", "Wstępne ładowanie trajektorii"
    "Parametry wymagane", "- ``name``: Nazwa trajektorii"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Odtwarzanie trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``MoveTPD(name,blend,ovl)``"
    "Opis", "Odtwarzanie trajektorii"
    "Parametry wymagane", "- ``name``: Nazwa trajektorii
    - ``blend``: Czy wygładzać, 0-nie, 1-tak
    - ``ovl``: Współczynnik skalowania prędkości, zakres [0~100]"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Pobieranie początkowej pozy trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetTPDStartPose(name)``"
    "Opis", "Pobieranie początkowej pozy trajektorii"
    "Parametry wymagane", "- ``name``: Nazwa trajektorii"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``desc_pose=[x,y,z,rx,ry,rz]``: Początkowa poza trajektorii"

Przykład kodu rejestracji trajektorii TPD robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    type = 1
    name = "tpd2025"
    period_ms = 4
    di_choose = 0
    do_choose = 0
    ovl = 100.0
    blend = 0
    rtn = robot.LoadTPD(name)
    print(f"LoadTPD rtn is: {rtn}")
    error,start_pose = robot.GetTPDStartPose(name)
    print(f"start pose, xyz is: {start_pose[0]},{start_pose[1]},{start_pose[2]}. "
          f"rpy is: {start_pose[3]},{start_pose[4]},{start_pose[5]}")
    robot.MoveCart(start_pose, 0, 0, 100, 100)
    time.sleep(1)
    rtn = robot.MoveTPD(name, blend, ovl)
    print(f"MoveTPD rtn is: {rtn}")
    time.sleep(5)
    robot.SetTPDDelete(name)
    robot.CloseRPC()

Wstępne przetwarzanie trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LoadTrajectoryJ(name,ovl,opt=1)``"
    "Opis", "Wstępne przetwarzanie trajektorii"
    "Parametry wymagane", "
    - ``name``: Nazwa trajektorii, np. trajHelix_aima_1.txt, dopuszczalna również pełna ścieżka, np. /fruser/traj/trajHelix_aima_1.txt;
    - ``ovl``: Procent skalowania prędkości, zakres [0~100];"
    "Parametry domyślne", "- ``opt``: 1-punkt kontrolny, domyślnie 1"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Odtwarzanie trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``MoveTrajectoryJ()``"
    "Opis", "Odtwarzanie trajektorii"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Pobieranie początkowej pozy trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetTrajectoryStartPose(name)``"
    "Opis", "Pobieranie początkowej pozy trajektorii"
    "Parametry wymagane", "``name``: Nazwa trajektorii"
    "Parametry domyślne", "Brak"       
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``desc_pose=[x,y,z,rx,ry,rz]``: Początkowa poza trajektorii"

Pobieranie numeru punktu trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetTrajectoryPointNum()``"
    "Opis", "Pobieranie numeru punktu trajektorii"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``pnum``: Numer punktu trajektorii"

Ustawianie prędkości podczas odtwarzania trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetTrajectoryJSpeed(ovl,mode)``"
    "Opis", "Ustawianie prędkości podczas odtwarzania trajektorii"
    "Parametry wymagane", "
    - ``ovl``: Procent skalowania prędkości, zakres [0~100]
    - ``mode``: 0-tryb zmniejszania prędkości; 1-bezpośrednie przełączanie"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Przykład kodu ustawiania prędkości podczas odtwarzania trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from time import sleep
    import time
    from fairino import Robot

    # Połączenie z kontrolerem robota
    robot = Robot.RPC('192.168.58.2')


    def TestSetTrajectoryJSpeed(self):
        # Przesłanie pliku trajektorii
        rtn = robot.TrajectoryJUpLoad("C://Users/lenovo/Desktop/trajHelix_aima_1.txt")
        print(f"Upload TrajectoryJ A {rtn}")

        traj_file_name = "trajHelix_aima_1.txt"
        # Załadowanie pliku trajektorii, parametry: nazwa pliku, procent prędkości, czy zapętlić (1: zapętlenie)
        rtn = robot.LoadTrajectoryJ(name=traj_file_name, ovl=100, opt=1)
        print(f"LoadTrajectoryJ {traj_file_name}, rtn is: {rtn}")

        # Pobranie początkowej pozy trajektorii
        rtn, traj_start_pose = robot.GetTrajectoryStartPose(name=traj_file_name)
        print(f"GetTrajectoryStartPose is: {rtn}")
        print(
            f"desc_pos:{traj_start_pose[0]},{traj_start_pose[1]},{traj_start_pose[2]},{traj_start_pose[3]},{traj_start_pose[4]},{traj_start_pose[5]}")

        time.sleep(1)

        # Ustawienie prędkości podstawowej i przejście do punktu początkowego trajektorii
        robot.SetSpeed(50)
        robot.MoveCart(desc_pos=traj_start_pose, tool=0, user=0, vel=100, acc=100, ovl=100, blendT=-1, config=-1)

        # Pobranie liczby punktów trajektorii
        rtn, traj_num = robot.GetTrajectoryPointNum()
        print(f"GetTrajectoryStartPose rtn is: {rtn}, traj num is: {traj_num}")

        # Rozpoczęcie odtwarzania trajektorii
        rtn = robot.MoveTrajectoryJ()
        print(f"MoveTrajectoryJ rtn is: {rtn}")

        time.sleep(1)

        # Pobranie stanu robota w czasie rzeczywistym
        trajspeedMode = 0
        while True:
            rtn, pkg = robot.GetRobotRealTimeState()
            if pkg.motion_done != 0:
                break

            # Ustawienie prędkości trajektorii na 10%
            rtn = robot.SetTrajectoryJSpeed(ovl=10.0, mode=trajspeedMode)
            print(f"SetTrajectoryJSpeed is: {rtn}")

            time.sleep(1)

            # Ustawienie prędkości trajektorii na 80%
            rtn = robot.SetTrajectoryJSpeed(ovl=80.0, mode=trajspeedMode)
            print(f"SetTrajectoryJSpeed is: {rtn}")

            time.sleep(1)

        # Zamknięcie połączenia
        robot.CloseRPC()
        time.sleep(1)


    # Wywołanie funkcji testowej
    TestSetTrajectoryJSpeed(robot)

Ustawianie siły i momentu obrotowego podczas odtwarzania trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetTrajectoryJForceTorque(ft)``"
    "Opis", "Ustawianie siły i momentu obrotowego podczas odtwarzania trajektorii"
    "Parametry wymagane", "``ft=[fx,fy,fz,tx,ty,tz]``: jednostka N i Nm"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie siły w kierunku X podczas odtwarzania trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetTrajectoryJForceFx(fx)``"
    "Opis", "Ustawianie siły w kierunku X podczas odtwarzania trajektorii"
    "Parametry wymagane", "``ft``: Siła w kierunku X, jednostka N"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie siły w kierunku Y podczas odtwarzania trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetTrajectoryJForceFx(fy)``"
    "Opis", "Ustawianie siły w kierunku Y podczas odtwarzania trajektorii"
    "Parametry wymagane", "``fy``: Siła w kierunku Y, jednostka N"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie siły w kierunku Z podczas odtwarzania trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetTrajectoryJForceFx(fz)``"
    "Opis", "Ustawianie siły w kierunku Z podczas odtwarzania trajektorii"
    "Parametry wymagane", "``fz``: Siła w kierunku Z, jednostka N"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie momentu obrotowego wokół osi X podczas odtwarzania trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetTrajectoryJTorqueTx(tx)``"
    "Opis", "Ustawianie momentu obrotowego wokół osi X podczas odtwarzania trajektorii"
    "Parametry wymagane", "``tx``: Moment obrotowy wokół osi X, jednostka Nm"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie momentu obrotowego wokół osi Y podczas odtwarzania trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetTrajectoryJTorqueTx(ty)``"
    "Opis", "Ustawianie momentu obrotowego wokół osi Y podczas odtwarzania trajektorii"
    "Parametry wymagane", "``ty``: Moment obrotowy wokół osi Y, jednostka Nm"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie momentu obrotowego wokół osi Z podczas odtwarzania trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetTrajectoryJTorqueTx(tz)``"
    "Opis", "Ustawianie momentu obrotowego wokół osi Z podczas odtwarzania trajektorii"
    "Parametry wymagane", "- ``tz``: Moment obrotowy wokół osi Z, jednostka Nm"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Przesyłanie pliku trajektorii J
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``TrajectoryJUpLoad(filePath)``"
    "Opis", "Przesyłanie pliku trajektorii J"
    "Parametry wymagane", "- ``filePath``: Pełna ścieżka przesyłanego pliku trajektorii, C://test/testJ.txt"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Usuwanie pliku trajektorii J
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``TrajectoryJDelete(filePath)``"
    "Opis", "Usuwanie pliku trajektorii J"
    "Parametry wymagane", "- ``filePath``: Pełna ścieżka usuwalnego pliku trajektorii, C://test/testJ.txt"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Przykład kodu odtwarzania pliku trajektorii J robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    rtn = robot.TrajectoryJUpLoad("D://zUP/traj.txt")
    print(f"Upload TrajectoryJ A {rtn}")
    traj_file_name = "traj.txt"
    rtn = robot.LoadTrajectoryJ(traj_file_name, 100, 1)
    print(f"LoadTrajectoryJ {traj_file_name}, rtn is: {rtn}")
    rtn,traj_start_pose = robot.GetTrajectoryStartPose(traj_file_name)
    print(f"GetTrajectoryStartPose is: {rtn}")
    print(f"desc_pos:{traj_start_pose[0]},{traj_start_pose[1]},{traj_start_pose[2]},"
          f"{traj_start_pose[3]},{traj_start_pose[4]},{traj_start_pose[5]}")
    time.sleep(1)
    robot.SetSpeed(50)
    robot.MoveCart(traj_start_pose, 0, 0, 50, 100, 100)
    rtn,traj_num = robot.GetTrajectoryPointNum()
    print(f"GetTrajectoryStartPose rtn is: {rtn}, traj num is: {traj_num}")
    rtn = robot.SetTrajectoryJSpeed(50.0)
    print(f"SetTrajectoryJSpeed is: {rtn}")
    traj_force = [0.0,0.0,0.0,0.0,0.0,0.0]
    traj_force[0] = 10  # fx = 10
    rtn = robot.SetTrajectoryJForceTorque(traj_force)
    print(f"SetTrajectoryJForceTorque rtn is: {rtn}")
    rtn = robot.SetTrajectoryJForceFx(10.0)
    print(f"SetTrajectoryJForceFx rtn is: {rtn}")
    rtn = robot.SetTrajectoryJForceFy(0.0)
    print(f"SetTrajectoryJForceFy rtn is: {rtn}")
    rtn = robot.SetTrajectoryJForceFz(0.0)
    print(f"SetTrajectoryJForceFz rtn is: {rtn}")
    rtn = robot.SetTrajectoryJTorqueTx(10.0)
    print(f"SetTrajectoryJTorqueTx rtn is: {rtn}")
    rtn = robot.SetTrajectoryJTorqueTy(10.0)
    print(f"SetTrajectoryJTorqueTy rtn is: {rtn}")
    rtn = robot.SetTrajectoryJTorqueTz(10.0)
    print(f"SetTrajectoryJTorqueTz rtn is: {rtn}")
    rtn = robot.MoveTrajectoryJ()
    print(f"MoveTrajectoryJ rtn is: {rtn}")
    robot.CloseRPC()

Wstępne przetwarzanie trajektorii (Look-Ahead)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``LoadTrajectoryLA(name, mode, errorLim, type, precision, vamx, amax, jmax, flag)``"
    "Opis", "Wstępne przetwarzanie trajektorii (Look-Ahead)"
    "Parametry wymagane", "- ``name``: Nazwa pliku trajektorii
    - ``mode``: Tryb próbkowania, 0-bez próbkowania; 1-równomierne próbkowanie odstępów danych; 2-próbkowanie z ograniczeniem błędu
    - ``errorLim``: Ograniczenie błędu, obowiązuje przy użyciu aproksymacji liniowej
    - ``type``: Sposób wygładzania, 0-wygładzanie Beziera
    - ``precision``: Dokładność wygładzania, obowiązuje przy użyciu wygładzania Beziera
    - ``vamx``: Ustawiona maksymalna prędkość, mm/s
    - ``amax``: Ustawione maksymalne przyspieszenie, mm/s2
    - ``jmax``: Ustawione maksymalne zryw, mm/s3
    - ``flag``: Przełącznik włączania Look-Ahead ze stałą prędkością 0-niewłączony; 1-włączony"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Odtwarzanie trajektorii (Look-Ahead)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.0

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``MoveTrajectoryLA()``"
    "Opis", "Odtwarzanie trajektorii (Look-Ahead)"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Przykład kodu odtwarzania trajektorii (Look-Ahead)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    rtn = robot.TrajectoryJUpLoad("D://zUP/traj.txt")
    print(f"Upload TrajectoryJ A {rtn}")
    traj_file_name = "traj.txt"
    rtn = robot.LoadTrajectoryLA(traj_file_name, 1, 2, 0, 2, 50, 200, 1000, 0)
    print(f"LoadTrajectoryLA {traj_file_name}, rtn is: {rtn}")
    rtn, traj_start_pose = robot.GetTrajectoryStartPose(traj_file_name)
    print(f"GetTrajectoryStartPose is: {rtn}")
    print(f"desc_pos: {traj_start_pose[0]},{traj_start_pose[1]},{traj_start_pose[2]},{traj_start_pose[3]},{traj_start_pose[4]},{traj_start_pose[5]}")
    time.sleep(1)
    robot.SetSpeed(50)
    robot.MoveCart(traj_start_pose, 0, 0, 100, 100, 100)
    rtn = robot.MoveTrajectoryLA()
    print(f"MoveTrajectoryLA rtn is: {rtn}")
    robot.CloseRPC()

Ruch do punktu początkowego rejestracji trajektorii TPD
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``MoveToTPDStart(name, moveType, ovl)``"
    "Opis", "Ruch do punktu początkowego rejestracji trajektorii TPD"
    "Parametry wymagane", "
    - ``name``: Nazwa pliku trajektorii
    - ``moveType``: Typ ruchu; 0-PTP; 1-LIN
    - ``ovl``: Procent skalowania prędkości, zakres [0~100]
    "
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Przykład kodu SDK ruchu do punktu początkowego rejestracji trajektorii TPD
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from time import sleep
    from fairino import Robot
    from ctypes import sizeof
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    import time

    def TestTPD(self):
        type = 1
        name = "tpd2025"
        period_ms = 4
        di_choose = 0
        do_choose = 0

        robot.SetTPDParam(type=type, name=name, period_ms=period_ms, di_choose=di_choose, do_choose=do_choose)

        robot.Mode(1)
        time.sleep(1)
        robot.DragTeachSwitch(1)
        robot.SetTPDStart(type=type, name=name, period_ms=period_ms, di_choose=di_choose, do_choose=do_choose)
        time.sleep(3)
        robot.SetWebTPDStop()
        robot.DragTeachSwitch(0)

        time.sleep(1)
        ovl = 100.0
        blend = 0
        start_pose = [0.0] * 6
        rtn = robot.LoadTPD(name)
        print(f"LoadTPD rtn is: {rtn}")

        rtn, start_pose = robot.GetTPDStartPose(name)
        print(f"start pose, xyz is: {start_pose[0]},{start_pose[1]},{start_pose[2]}. rpy is: {start_pose[3]},{start_pose[4]},{start_pose[5]}")
        # robot.MoveCart(desc_pos=start_pose, tool=0, user=0, vel=100, acc=100, ovl=ovl, blendT=-1, config=-1)
        # time.sleep(1)

        rtn = robot.MoveToTPDStart(name, 0, 100)
        print(f"MoveToTPDStart rtn is: {rtn}")

        rtn = robot.MoveTPD(name, blend, ovl)
        print(f"MoveTPD rtn is: {rtn}")
        time.sleep(5)

        robot.SetTPDDelete(name)

        robot.CloseRPC()
        return 0

    TestTPD(robot)