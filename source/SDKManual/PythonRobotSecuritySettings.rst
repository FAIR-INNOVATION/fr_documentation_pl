Ustawienia bezpieczeństwa robota
================================

.. toctree:: 
    :maxdepth: 5

Ustawianie poziomu kolizji
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetAnticollision (mode,level,config)``"
    "Opis", "Ustawianie poziomu kolizji"
    "Parametry wymagane", "- ``mode``: 0-poziom, 1-procent;
    - ``level=[j1,j2,j3,j4,j5,j6]``: Próg kolizji;
    - ``config``: 0-nie aktualizuj pliku konfiguracyjnego, 1-aktualizuj plik konfiguracyjny"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie strategii po kolizji
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetCollisionStrategy(strategy,safeTime,safeDistance,safeVel,safetyMargin)``"
    "Opis", "Ustawianie strategii po kolizji"
    "Parametry wymagane", "- ``strategy``: 0-zatrzymaj z błędem, 1-kontynuuj działanie, 2-zatrzymaj z błędem, 3-tryb momentu grawitacyjnego, 4-tryb odpowiedzi oscylacyjnej, 5-tryb odbicia po kolizji"
    "Parametry domyślne", "- ``safeTime``: Czas bezpiecznego zatrzymania [1000-2000] ms, domyślnie: 1000
    - ``safeDistance``: Bezpieczna odległość zatrzymania [1-150] mm, domyślnie: 100
    - ``safeVel``: Bezpieczna prędkość zatrzymania [50-250] mm/s, domyślnie: 250
    - ``safetyMargin[6]``: Współczynniki bezpieczeństwa [1-10], domyślnie: [10,10,10,10,10,10]"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Rozpoczęcie funkcji niestandardowego progu detekcji kolizji, ustawienie progów detekcji kolizji dla strony przegubów i strony TCP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.0

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``CustomCollisionDetectionStart(flag, jointDetectionThreshould, tcpDetectionThreshould, block)``"
    "Opis", "Rozpoczęcie funkcji niestandardowego progu detekcji kolizji, ustawienie progów detekcji kolizji dla strony przegubów i strony TCP"
    "Parametry wymagane", "- ``flag``: 1-tylko detekcja przegubów włączona; 2-tylko detekcja TCP włączona; 3-detekcja przegubów i TCP włączone jednocześnie
    - ``jointDetectionThreshould``: Próg detekcji kolizji przegubów j1-j6
    - ``tcpDetectionThreshould``: Próg detekcji kolizji TCP, xyzabc
    - ``block``: 0-nieblokujący; 1-blokujący"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode"

Zakończenie funkcji niestandardowego progu detekcji kolizji
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.0

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``CustomCollisionDetectionEnd()``"
    "Opis", "Zakończenie funkcji niestandardowego progu detekcji kolizji"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode"

Przykład kodu ustawiania poziomu kolizji robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 

    from fairino import Robot
    import time
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    mode = 0
    config = 1
    level1 = [1.0, 2.0, 3.0, 4.0, 5.0, 6.0]
    level2 = [50.0, 20.0, 30.0, 40.0, 50.0, 60.0]
    rtn = robot.SetAnticollision(mode, level1, config)
    print(f"SetAnticollision mode 0 rtn is {rtn}")
    mode = 1
    rtn = robot.SetAnticollision(mode, level2, config)
    print(f"SetAnticollision mode 1 rtn is {rtn}")
    p1Joint = [-11.904, -99.669, 117.473, -108.616, -91.726, 74.256]
    p2Joint = [-45.615, -106.172, 124.296, -107.151, -91.282, 74.255]
    p1Desc = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    p2Desc = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    exaxisPos = [0.0, 0.0, 0.0, 0.0]
    offdese = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    robot.MoveL(desc_pos=p2Desc, tool=0, user=0, vel=100, blendR=2)
    robot.ResetAllError()
    safety = [5, 5, 5, 5, 5, 5]
    rtn = robot.SetCollisionStrategy(3, 1000, 150, 250, safety)
    print(f"SetCollisionStrategy rtn is {rtn}")
    jointDetectionThreshould = [0.1, 0.1, 0.1, 0.1, 0.1, 0.1]
    tcpDetectionThreshould = [60, 60, 60, 60, 60, 60]
    rtn = robot.CustomCollisionDetectionStart(3, jointDetectionThreshould, tcpDetectionThreshould, 0)
    print(f"CustomCollisionDetectionStart rtn is {rtn}")
    robot.MoveL(desc_pos=p1Desc, tool=0, user=0, vel=100)
    robot.MoveL(desc_pos=p2Desc, tool=0, user=0, vel=100)
    rtn = robot.CustomCollisionDetectionEnd()
    print(f"CustomCollisionDetectionEnd rtn is {rtn}")
    robot.CloseRPC()

Ustawianie dodatniego ograniczenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetLimitPositive(p_limit)``"
    "Opis", "Ustawianie dodatniego ograniczenia"
    "Parametry wymagane", "- ``p_limit=[j1,j2,j3,j4,j5,j6]``: Pozycje sześciu przegubów"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie ujemnego ograniczenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetLimitNegative(n_limit)``"
    "Opis", "Ustawianie ujemnego ograniczenia"
    "Parametry wymagane", "- ``n_limit=[j1,j2,j3,j4,j5,j6]``: Pozycje sześciu przegubów"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Pobieranie kątów miękkiego ograniczenia przegubów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetJointSoftLimitDeg(flag=1)``"
    "Opis", "Pobieranie kątów miękkiego ograniczenia przegubów"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "``flag``: 0-blokujący, 1-nieblokujący domyślnie 1"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``[j1min,j1max,j2min,j2max,j3min,j3max, j4min,j4max,j5min, j5max, j6min,j6max]``: Oś 1 ~ oś 6, ujemne i dodatnie ograniczenie przegubów, jednostka [mm]"

Przykład kodu ustawiania ograniczeń robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 

    from fairino import Robot
    import time
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    plimit = [170.0, 80.0, 150.0, 80.0, 170.0, 160.0]
    robot.SetLimitPositive(plimit)
    nlimit = [-170.0, -260.0, -150.0, -260.0, -170.0, -160.0]
    robot.SetLimitNegative(nlimit)
    error,neg_deg = robot.GetJointSoftLimitDeg(0)
    print(f"pos limit deg: {neg_deg[1]}, {neg_deg[3]}, {neg_deg[5]}, {neg_deg[7]}, {neg_deg[9]}, {neg_deg[11]}")
    print(f"neg limit deg: {neg_deg[0]}, {neg_deg[2]}, {neg_deg[4]}, {neg_deg[6]}, {neg_deg[8]}, {neg_deg[10]}")
    robot.CloseRPC()

Ustawianie metody detekcji kolizji robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetCollisionDetectionMethod(method, thresholdMode)``"
    "Opis", "Ustawianie metody detekcji kolizji robota"
    "Parametry wymagane", "
    - ``method``: Metoda detekcji kolizji: 0-tryb prądowy; 1-podwójny enkoder; 2-tryb prądowy i podwójny enkoder włączone jednocześnie
    - ``thresholdMode``: Sposób progu poziomu kolizji; 0-stały próg poziomu kolizji; 1-niestandardowy próg detekcji kolizji  
    "
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode"

Włączanie/wyłączanie detekcji kolizji w stanie statycznym
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetStaticCollisionOnOff(status)``"
    "Opis", "Włączanie/wyłączanie detekcji kolizji w stanie statycznym"
    "Parametry wymagane", "
    - ``status``: 0-wyłączone; 1-włączone
    "
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode"

Przykład kodu ustawiania metody detekcji kolizji robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 

    from fairino import Robot
    import time
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    rtn = robot.SetCollisionDetectionMethod(0,0)
    rtn = robot.SetStaticCollisionOnOff(1)
    print(f"SetStaticCollisionOnOff On rtn is {rtn}")
    time.sleep(5)
    rtn = robot.SetStaticCollisionOnOff(0)
    print(f"SetStaticCollisionOnOff Off rtn is {rtn}")
    robot.CloseRPC()

Detekcja momentu obrotowego i mocy przegubów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetPowerLimit(status, power)``"
    "Opis", "Detekcja momentu obrotowego i mocy przegubów"
    "Parametry wymagane", "
    - ``status``: 0-wyłączone; 1-włączone
    - ``power``: Ustawiona maksymalna moc (W)
    "
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode"
    
Przykład kodu detekcji momentu obrotowego i mocy przegubów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 

    from fairino import Robot
    import time
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    robot.DragTeachSwitch(1)
    robot.SetPowerLimit(1, 200)
    error,torques = robot.GetJointTorques(1)
    count = 100
    robot.ServoJTStart()
    while count > 0:
        error = robot.ServoJT(torques, 0.001)
        count -= 1
        time.sleep(0.001)  # opóźnienie 1 ms
    error = robot.ServoJTEnd()
    robot.DragTeachSwitch(0)
    robot.CloseRPC()

Ustawianie parametrów bezpiecznej prędkości
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetVelReducePara(enable, maxTCPVel, strategy, maxJointVel=[45.0, 45.0, 45.0, 45.0, 45.0, 45.0])``"
    "Opis", "Ustawia parametry prędkości bezpieczeństwa"
    "Parametry Wymagane", "
    - ``enable``: 0-wyłączony; 1-włączony w trybie ręcznym; 2-włączony we wszystkich trybach (automatyczne ograniczenie prędkości nieobsługiwane)
    - ``maxTCPVel``: Maksymalny limit prędkości TCP; [0-1000] mm/s
    - ``strategy``: Strategia po przekroczeniu prędkości; 0-zatrzymaj i alarm; 1-automatyczne ograniczenie prędkości; 2-zatrzymaj i alarm z wyłączeniem
    - ``maxJointVel``: Maksymalna prędkość dla 6 stawów (°/s), domyślnie [45.0, 45.0, 45.0, 45.0, 45.0, 45.0]
    "
    "Parametry Domyślne", "Brak"
    "Wartość Zwracana", "- Kod błędu, 0-sukces; niezerowy-błąd"

Przykład kodu SDK ustawiania parametrów bezpiecznej prędkości
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 

    from fairino import Robot
    import time

    def main():
        robot = Robot.RPC('192.168.58.2')
        time.sleep(0.5)  

        j1 = [10.220, -11.121, -118.086, -46.739, 82.036, 131.503]
        j2 = [89.782, -11.122, -118.086, -46.740, 82.036, 131.504]

        epos = [0.0, 0.0, 0.0, 0.0]
        offset_pos = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]

        robot.SetSpeed(20)

        maxJointVel = [100.0, 100.0, 100.0, 100.0, 100.0, 100.0]

        rtn = robot.SetVelReducePara(0, 200, 0, maxJointVel)
        robot.MoveJ(joint_pos=j2, tool=1, user=2, vel=100, acc=100, ovl=100,
                    exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)

        rtn = robot.SetVelReducePara(2, 200, 0, maxJointVel)
        print(f"SetVelReduceParaA param error rtn is {rtn}")

        robot.MoveJ(joint_pos=j1, tool=1, user=2, vel=100, acc=100, ovl=100,
                    exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
        robot.MoveJ(joint_pos=j2, tool=1, user=2, vel=100, acc=100, ovl=100,
                    exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)

        maxJointVel = [20.0, 20.0, 20.0, 20.0, 20.0, 20.0]
        rtn = robot.SetVelReducePara(2, 200, 0, maxJointVel)
        print(f"SetVelReduceParaB reduce vel rtn is {rtn}")

        robot.MoveJ(joint_pos=j1, tool=1, user=2, vel=100, acc=100, ovl=100,
                    exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
        robot.MoveJ(joint_pos=j2, tool=1, user=2, vel=100, acc=100, ovl=100,
                    exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)

        robot.CloseRPC()

    if __name__ == "__main__":
        main()