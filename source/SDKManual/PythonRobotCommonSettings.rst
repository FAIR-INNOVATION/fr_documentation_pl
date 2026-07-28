Ustawienia ogólne robota
========================

.. toctree:: 
    :maxdepth: 5

Ustawianie punktu odniesienia narzędzia - metoda sześciu punktów
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetToolPoint(point_num)``"
    "Opis", "Ustawianie punktu odniesienia narzędzia - metoda sześciu punktów"
    "Parametry wymagane", "- ``point_num``: Numer punktu, zakres [1~6]"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Obliczanie układu współrzędnych narzędzia - metoda sześciu punktów
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ComputeTool()``"
    "Opis", "Obliczanie układu współrzędnych narzędzia - metoda sześciu punktów (obliczenia po ustawieniu sześciu punktów odniesienia narzędzia)"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``tcp_pose=[x,y,z,rx,ry,rz]``: Układ współrzędnych narzędzia"

Ustawianie punktu odniesienia narzędzia - metoda czterech punktów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetTcp4RefPoint(point_num)``"
    "Opis", "Ustawianie punktu odniesienia narzędzia - metoda czterech punktów"
    "Parametry wymagane", "``point_num``: Numer punktu, zakres [1~4]"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``tcp_pose=[x,y,z,rx,ry,rz]``: Układ współrzędnych narzędzia"

Obliczanie układu współrzędnych narzędzia - metoda czterech punktów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ComputeTcp4()``"
    "Opis", "Obliczanie układu współrzędnych narzędzia - metoda czterech punktów (obliczenia po ustawieniu czterech punktów odniesienia narzędzia)"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``tcp_pose=[x,y,z,rx,ry,rz]``: Układ współrzędnych narzędzia"

Obliczanie układu współrzędnych narzędzia na podstawie informacji o punktach
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ComputeToolCoordWithPoints(method, pos)``"
    "Opis", "Obliczanie układu współrzędnych narzędzia na podstawie informacji o punktach"
    "Parametry wymagane", "- ``method``: Metoda obliczeniowa; 0-metoda czterech punktów; 1-metoda sześciu punktów
    - ``pos``: Grupa pozycji przegubów, długość tablicy wynosi 4 dla metody czterech punktów, 6 dla metody sześciu punktów"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode 
    - ``tcp_offset=[x,y,z,rx,ry,rz]``: Układ współrzędnych narzędzia obliczony na podstawie informacji o punktach, jednostka [mm][°]"

Ustawianie układu współrzędnych narzędzia
+++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetToolCoord(id,t_coord,type,install,toolID,loadNum)``"
    "Opis", "Ustawianie układu współrzędnych narzędzia"
    "Parametry wymagane", "- ``id``: Numer układu współrzędnych, zakres [1~15];
    - ``t_coord``: Pozycja środka narzędzia względem środka kołnierza końcowego, jednostka [mm][°];
    - ``type``: 0-układ współrzędnych narzędzia, 1-układ współrzędnych czujnika;
    - ``install``: Pozycja montażu, 0-koniec robota, 1-na zewnątrz robota
    - ``toolID``: ID narzędzia
    - ``loadNum``: Numer obciążenia"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode "

Ustawianie listy układów współrzędnych narzędzia
+++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetToolList(id,t_coord ,type, install, loadNum)``"
    "Opis", "Ustawianie listy układów współrzędnych narzędzia"
    "Parametry wymagane", "- ``id``: Numer układu współrzędnych, zakres [1~15];
    - ``t_coord``: [x,y,z,rx,ry,rz] Pozycja środka narzędzia względem środka kołnierza końcowego, jednostka [mm][°];
    - ``type``: 0-układ współrzędnych narzędzia, 1-układ współrzędnych czujnika;
    - ``install``: Pozycja montażu, 0-koniec robota, 1-na zewnątrz robota
    - ``loadNum``: Numer obciążenia"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode "

Pobieranie bieżącego układu współrzędnych narzędzia
+++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetTCPOffset(flag=1)``"
    "Opis", "Pobieranie bieżącego układu współrzędnych narzędzia"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "``flag``: 0-blokujący, 1-nieblokujący, domyślnie 1"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``tcp_offset=[x,y,z,rx,ry,rz]``: Bieżąca względna pozycja układu współrzędnych narzędzia, jednostka [mm][°]"

Przykład kodu operacji na układzie współrzędnych narzędzia robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    p1Desc = [186.331, 487.913, 209.850, 149.030, 0.688, -114.347]
    p2Desc = [69.721, 535.073, 202.882, -144.406, -14.775, -89.012]
    p3Desc = [146.861, 578.426, 205.598, 175.997, -36.178, -93.437]
    p4Desc = [136.284, 509.876, 225.613, 178.987, 1.372, -100.696]
    p5Desc = [138.395, 505.972, 298.016, 179.134, 2.147, -101.110]
    p6Desc = [105.553, 454.325, 232.017, -179.426, 0.444, -99.952]
    p1Joint = [-127.876, -75.341, 115.417, -122.741, -59.820, 74.300]
    p2Joint = [-101.780, -69.828, 110.917, -125.740, -127.841, 74.300]
    p3Joint = [-112.851, -60.191, 86.566, -80.676, -97.463, 74.300]
    p4Joint = [-116.397, -76.281, 113.845, -128.611, -88.654, 74.299]
    p5Joint = [-116.814, -82.333, 109.162, -118.662, -88.585, 74.302]
    p6Joint = [-115.649, -84.367, 122.447, -128.663, -90.432, 74.303]
    exaxisPos = [0, 0, 0, 0]
    offdese = [0, 0, 0, 0, 0, 0]
    posJ = [p1Joint, p2Joint, p3Joint, p4Joint, p5Joint, p6Joint]
    rtn,coordRtn = robot.ComputeToolCoordWithPoints(1, posJ)
    print(f"ComputeToolCoordWithPoints    {rtn}  coord is {coordRtn[0]} {coordRtn[1]} {coordRtn[2]} {coordRtn[3]} {coordRtn[4]} {coordRtn[5]}")
    robot.MoveJ(joint_pos=p1Joint,tool=0, user=0, vel=100)
    robot.SetToolPoint(1)
    robot.MoveJ(joint_pos=p2Joint,tool=0, user=0, vel=100)
    robot.SetToolPoint(2)
    robot.MoveJ(joint_pos=p3Joint,tool=0, user=0, vel=100)
    robot.SetToolPoint(3)
    robot.MoveJ(joint_pos=p4Joint,tool=0, user=0, vel=100)
    robot.SetToolPoint(4)
    robot.MoveJ(joint_pos=p5Joint,tool=0, user=0, vel=100)
    robot.SetToolPoint(5)
    robot.MoveJ(joint_pos=p6Joint,tool=0, user=0, vel=100)
    robot.SetToolPoint(6)
    rtn,coordRtn = robot.ComputeTool()
    print(f"6 Point ComputeTool        {rtn}  coord is {coordRtn[0]} {coordRtn[1]} {coordRtn[2]} {coordRtn[3]} {coordRtn[4]} {coordRtn[5]}")
    robot.SetToolList(1, coordRtn, 0, 0, 0)
    robot.MoveJ(joint_pos=p1Joint,tool=0, user=0, vel=100)
    robot.SetTcp4RefPoint(1)
    robot.MoveJ(joint_pos=p2Joint,tool=0, user=0, vel=100)
    robot.SetTcp4RefPoint(2)
    robot.MoveJ(joint_pos=p3Joint,tool=0, user=0, vel=100)
    robot.SetTcp4RefPoint(3)
    robot.MoveJ(joint_pos=p4Joint,tool=0, user=0, vel=100)
    robot.SetTcp4RefPoint(4)
    rtn,coordRtn = robot.ComputeTcp4()
    print(f"4 Point ComputeTool        {rtn}  coord is {coordRtn[0]} {coordRtn[1]} {coordRtn[2]} {coordRtn[3]} {coordRtn[4]} {coordRtn[5]}")
    robot.SetToolCoord(2, coordRtn, 0, 0, 1, 0)
    rtn,getCoord = robot.GetTCPOffset(0)
    print(f"GetTCPOffset    {rtn}  coord is {getCoord[0]} {getCoord[1]} {getCoord[2]} {getCoord[3]} {getCoord[4]} {getCoord[5]}")
    robot.CloseRPC()

Ustawianie punktu odniesienia zewnętrznego narzędzia - metoda trzech punktów
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetExTCPPoint(point_num)``"
    "Opis", "Ustawianie punktu odniesienia zewnętrznego narzędzia - metoda trzech punktów"
    "Parametry wymagane", "- ``point_num``: Numer punktu, zakres [1~3]"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode "

Obliczanie zewnętrznego układu współrzędnych narzędzia - metoda trzech punktów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ComputeExTCF(point_num)``"
    "Opis", "Obliczanie zewnętrznego układu współrzędnych narzędzia - metoda trzech punktów (obliczenia po ustawieniu trzech punktów odniesienia)"
    "Parametry wymagane", "``point_num``: Numer punktu, zakres [1~3]"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode 
    - ``etcp=[x,y,z,rx,ry,rz]``: Zewnętrzny układ współrzędnych narzędzia"

Ustawianie zewnętrznego układu współrzędnych narzędzia
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetExToolCoord(id,etcp,etool)``"
    "Opis", "Ustawianie zewnętrznego układu współrzędnych narzędzia"
    "Parametry wymagane", "- ``id``: Numer układu współrzędnych, 20-39 odpowiadają zewnętrznym układom współrzędnych narzędzi 0-19;
    - ``etcp``: [x,y,z,rx,ry,rz] Zewnętrzny układ współrzędnych narzędzia, jednostka [mm][°];
    - ``etool``: [x,y,z,rx,ry,rz] Końcowy układ współrzędnych narzędzia, jednostka [mm][°];"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie listy zewnętrznych układów współrzędnych narzędzia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetExToolList(id,etcp ,etool)``"
    "Opis", "Ustawianie listy zewnętrznych układów współrzędnych narzędzia"
    "Parametry wymagane", "- ``id``: Numer układu współrzędnych, 20-39 odpowiadają zewnętrznym układom współrzędnych narzędzi 0-19;
    - ``etcp``: Zewnętrzny układ współrzędnych narzędzia, jednostka [mm][°];
    - ``etool``: Końcowy układ współrzędnych narzędzia, jednostka [mm][°];"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode "

Przykład kodu operacji na zewnętrznym układzie współrzędnych narzędzia robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

    from time import sleep
    import time
    from fairino import Robot

    robot = Robot.RPC('192.168.58.2')

    def TestExtCoord(self):
        p1Desc = [-89.606, 779.517, 193.516, 178.000, 0.476, -92.484]
        p1Joint = [-108.145, -50.137, 85.818, -125.599, -87.946, 74.329]

        p2Desc = [-24.656, 850.384, 191.361, 177.079, -2.058, -95.355]
        p2Joint = [-111.024, -41.538, 69.222, -114.913, -87.743, 74.329]

        p3Desc = [-99.813, 766.661, 241.878, -176.817, 1.917, -91.604]
        p3Joint = [-107.266, -56.116, 85.971, -122.560, -92.548, 74.331]

        exaxisPos = [0, 0, 0, 0]
        offdese = [0, 0, 0, 0, 0, 0]

        posTCP = [p1Desc, p2Desc, p3Desc]
        # coordRtn = DescPose()

        robot.MoveJ(joint_pos=p1Joint,tool=1, user=0, vel=50)
        robot.SetExTCPPoint(1)
        robot.MoveJ(joint_pos=p2Joint,tool=1, user=0, vel=50)
        robot.SetExTCPPoint(2)
        robot.MoveJ(joint_pos=p3Joint,tool=1, user=0, vel=50)
        robot.SetExTCPPoint(3)
        rtn,coordRtn = robot.ComputeExTCF()
        print(f"ComputeExTCF {rtn}  coord is {coordRtn[0]} {coordRtn[1]} {coordRtn[2]} {coordRtn[3]} {coordRtn[4]} {coordRtn[5]}")

        robot.SetExToolCoord(21, coordRtn, offdese)
        robot.SetExToolList(21, coordRtn, offdese)

        robot.CloseRPC()
    TestExtCoord(robot)

Ustawianie punktu odniesienia przedmiotu - metoda trzech punktów
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetWObjCoordPoint(point_num)``"
    "Opis", "Ustawianie punktu odniesienia przedmiotu - metoda trzech punktów"
    "Parametry wymagane", "``point_num``: Numer punktu, zakres [1~3]"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode "

Obliczanie układu współrzędnych przedmiotu - metoda trzech punktów
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ComputeWObjCoord(method, refFrame)``"
    "Opis", "Obliczanie układu współrzędnych przedmiotu - metoda trzech punktów (obliczenia po ustawieniu trzech punktów odniesienia);"
    "Parametry wymagane", "- ``method``: Sposób obliczania 0: punkt początkowy - oś X - oś Z, 1: punkt początkowy - oś X - płaszczyzna XY
    - ``refFrame``: Układ odniesienia"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode 
    - ``wobj_pose=[x,y,z,rx,ry,rz]``: Układ współrzędnych przedmiotu"

Ustawianie układu współrzędnych przedmiotu
++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetWObjCoord(id, coord, refFrame)``"
    "Opis", "Ustawianie układu współrzędnych przedmiotu"
    "Parametry wymagane", "- ``id``: Numer układu współrzędnych, zakres [0~14];
    - ``coord``: Pozycja układu współrzędnych przedmiotu względem środka kołnierza końcowego, jednostka [mm][°]
    - ``refFrame``: Układ odniesienia"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie listy układów współrzędnych przedmiotu
+++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetWObjList(id, coord, refFrame)``"
    "Opis", "Ustawianie listy układów współrzędnych przedmiotu"
    "Parametry wymagane", "- ``id``: Numer układu współrzędnych, zakres [0~14];
    - ``coord``: Pozycja układu współrzędnych przedmiotu względem środka kołnierza końcowego, jednostka [mm][°]
    - ``refFrame``: Układ odniesienia"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode "

Obliczanie układu współrzędnych przedmiotu na podstawie informacji o punktach
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ComputeWObjCoordWithPoints(method, pos, refFrame)``"
    "Opis", "Obliczanie układu współrzędnych przedmiotu na podstawie informacji o punktach"
    "Parametry wymagane", "- ``method``: Metoda obliczeniowa; 0: punkt początkowy - oś X - oś Z, 1: punkt początkowy - oś X - płaszczyzna XY
    - ``pos``: Grupa trzech pozycji TCP
    - ``refFrame``: Układ odniesienia"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode 
    - ``wobj_offset=[x,y,z,rx,ry,rz]``: Układ współrzędnych przedmiotu obliczony na podstawie informacji o punktach, jednostka [mm][°]"

Pobieranie bieżącego układu współrzędnych przedmiotu
+++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetWObjOffset(flag=1)``"
    "Opis", "Pobieranie bieżącego układu współrzędnych przedmiotu"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "``flag``: 0-blokujący, 1-nieblokujący, domyślnie 1"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``wobj_offset=[x,y,z,rx,ry,rz]``: Bieżąca względna pozycja układu współrzędnych przedmiotu, jednostka [mm][°]"

Przykład kodu operacji na układzie współrzędnych przedmiotu robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    p1Desc = [-89.606, 779.517, 193.516, 178.000, 0.476, -92.484]
    p2Desc = [-24.656, 850.384, 191.361, 177.079, -2.058, -95.355]
    p3Desc = [-99.813, 766.661, 241.878, -176.817, 1.917, -91.604]
    p1Joint = [-108.145, -50.137, 85.818, -125.599, -87.946, 74.329]
    p2Joint = [-111.024, -41.538, 69.222, -114.913, -87.743, 74.329]
    p3Joint = [-107.266, -56.116, 85.971, -122.560, -92.548, 74.331]
    exaxisPos = [0, 0, 0, 0]
    offdese = [0, 0, 0, 0, 0, 0]
    posTCP = [p1Desc, p2Desc, p3Desc]
    rtn,coordRtn = robot.ComputeWObjCoordWithPoints(1, posTCP, 0)
    print(f"ComputeWObjCoordWithPoints    {rtn}  coord is {coordRtn[0]} {coordRtn[1]} {coordRtn[2]} {coordRtn[3]} {coordRtn[4]} {coordRtn[5]}")
    robot.MoveJ(joint_pos=p1Joint,tool=1, user=0, vel=100)
    robot.SetWObjCoordPoint(1)
    robot.MoveJ(joint_pos=p2Joint,tool=1, user=0, vel=100)
    robot.SetWObjCoordPoint(2)
    robot.MoveJ(joint_pos=p3Joint,tool=1, user=0, vel=100)
    robot.SetWObjCoordPoint(3)
    rtn,coordRtn = robot.ComputeWObjCoord(1, 0)
    print(f"ComputeWObjCoord   {rtn}  coord is {coordRtn[0]} {coordRtn[1]} {coordRtn[2]} {coordRtn[3]} {coordRtn[4]} {coordRtn[5]}")
    robot.SetWObjCoord(1, coordRtn, 0)
    robot.SetWObjList(1, coordRtn, 0)
    rtn,getWobjDesc = robot.GetWObjOffset(0)
    print(f"GetWObjOffset    {rtn}  coord is {getWobjDesc[0]} {getWobjDesc[1]} {getWobjDesc[2]} {getWobjDesc[3]} {getWobjDesc[4]} {getWobjDesc[5]}")
    robot.CloseRPC()

Ustawianie prędkości globalnej
++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetSpeed(vel)``"
    "Opis", "Ustawianie prędkości globalnej"
    "Parametry wymagane", "- ``vel``: Procent prędkości, zakres [0~100]"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie przyspieszenia robota
++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetOaccScale(acc)``"
    "Opis", "Ustawianie przyspieszenia robota"
    "Parametry wymagane", "- ``acc``: Procent przyspieszenia robota"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode "

Pobieranie domyślnej prędkości
++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetDefaultTransVel()``"
    "Opis", "Pobieranie domyślnej prędkości"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``vel``: Domyślna prędkość, jednostka [mm/s]"

Ustawianie ciężaru obciążenia końcowego
+++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetLoadWeight(loadNum, weight)``"
    "Opis", "Ustawianie ciężaru obciążenia końcowego, nieprawidłowe ustawienie ciężaru obciążenia może spowodować utratę kontroli nad robotem w trybie przeciągania"
    "Parametry wymagane", "- ``loadNum``: Numer obciążenia
    - ``weight``: Jednostka [kg]"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode "

Ustawianie współrzędnych środka ciężkości obciążenia końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetLoadCoord(x,y,z,loadNum = 0)``"
    "Opis", "Ustawianie współrzędnych środka ciężkości obciążenia końcowego, nieprawidłowe ustawienie środka ciężkości obciążenia może spowodować utratę kontroli nad robotem w trybie przeciągania"
    "Parametry wymagane", "- ``x``: Współrzędna środka ciężkości, jednostka [mm]
    - ``y``: Współrzędna środka ciężkości, jednostka [mm]
    - ``z``: Współrzędna środka ciężkości, jednostka [mm]"
    "Parametry domyślne", "- ``loadNum``: Numer obciążenia, domyślnie 0"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode "

Pobieranie ciężaru bieżącego obciążenia
++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetTargetPayload(flag=1)``"
    "Opis", "Pobieranie masy bieżącego obciążenia"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "``flag``: 0-blokujący, 1-nieblokujący, domyślnie 1"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``weight``: Bieżący ciężar obciążenia, jednostka [kg]"

Pobieranie środka ciężkości bieżącego obciążenia
+++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetTargetPayloadCog(flag=1)``"
    "Opis", "Pobieranie środka ciężkości bieżącego obciążenia"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "``flag``: 0-blokujący, 1-nieblokujący, domyślnie 1"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``cog=[x,y,z]``: Bieżące współrzędne środka ciężkości, jednostka [mm]"

Ustawianie sposobu montażu robota - montaż stały
+++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetRobotInstallPos(method)``"
    "Opis", "Ustawianie sposobu montażu robota - montaż stały, nieprawidłowe ustawienie sposobu montażu może spowodować utratę kontroli nad robotem w trybie przeciągania"
    "Parametry wymagane", "- ``method``: 0-montaż poziomy, 1-montaż boczny, 2-montaż sufitowy"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode "

Ustawianie kąta montażu robota - montaż swobodny
+++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetRobotInstallAngle(yangle,zangle)``"
    "Opis", "Ustawianie kąta montażu robota - montaż swobodny, nieprawidłowe ustawienie kąta montażu może spowodować utratę kontroli nad robotem w trybie przeciągania"
    "Parametry wymagane", "- ``yangle``: Kąt pochylenia
    - ``zangle``: Kąt obrotu"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Pobieranie kąta montażu robota
++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetRobotInstallAngle()``"
    "Opis", "Pobieranie kąta montażu robota"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``[yangle,zangle]``: yangle-kąt pochylenia, zangle-kąt obrotu"

Ustawianie wartości zmiennej systemowej
++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetSysVarValue(id,value)``"
    "Opis", "Ustawianie zmiennej systemowej"
    "Parametry wymagane", "- ``id``: Numer zmiennej, zakres [1~20];
    - ``value``: Wartość zmiennej"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Pobieranie wartości zmiennej systemowej
+++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetSysVarValue(id)``"
    "Opis", "Pobieranie wartości zmiennej systemowej"
    "Parametry wymagane", "- ``id``: Numer zmiennej systemowej, zakres [1~20]"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``var_value``: Wartość zmiennej systemowej"

Przykład kodu ustawień ogólnych robota
++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    for i in range(1, 100):
        robot.SetSpeed(i)
        robot.SetOaccScale(i)
        time.sleep(0.03)
    error,defaultVel = robot.GetDefaultTransVel()
    print(f"GetDefaultTransVel is {defaultVel}")
    for i in range(1, 21):
        robot.SetSysVarValue(i, i + 0.5)
        time.sleep(0.1)
    for i in range(1, 21):
        value = robot.GetSysVarValue(i)
        print(f"sys value {i} is: {value}")
        time.sleep(0.1)
    robot.SetLoadWeight(0, 2.5)
    robot.SetLoadCoord(3.0,4.0,5.0)
    time.sleep(1)
    error,getLoad = robot.GetTargetPayload(0)
    error,getLoadTran = robot.GetTargetPayloadCog(0)
    print(f"get load is {getLoad}; get load cog is {getLoadTran[0]} {getLoadTran[1]} {getLoadTran[2]}")
    robot.SetRobotInstallPos(0)
    robot.SetRobotInstallAngle(15.0, 25.0)
    error,[anglex, angley] = robot.GetRobotInstallAngle()
    print(f"GetRobotInstallAngle x: {anglex}; y: {angley}")
    robot.CloseRPC()

Przełącznik kompensacji tarcia przegubów
+++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``FrictionCompensationOnOff(state)``"
    "Opis", "Przełącznik kompensacji tarcia przegubów"
    "Parametry wymagane", "- ``state``: 0-wył., 1-wł."
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie współczynnika kompensacji tarcia przegubów - montaż poziomy
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetFrictionValue_level(coeff)``"
    "Opis", "Ustawianie współczynnika kompensacji tarcia przegubów - montaż stały - montaż poziomy"
    "Parametry wymagane", "- ``coeff=[j1,j2,j3,j4,j5,j6]``: Współczynniki kompensacji dla sześciu przegubów"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie współczynnika kompensacji tarcia przegubów - montaż boczny
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetFrictionValue_wall(coeff)``"
    "Opis", "Ustawianie współczynnika kompensacji tarcia przegubów - montaż stały - montaż boczny"
    "Parametry wymagane", "- ``coeff=[j1,j2,j3,j4,j5,j6]``: Współczynniki kompensacji dla sześciu przegubów"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie współczynnika kompensacji tarcia przegubów - montaż sufitowy
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetFrictionValue_ceiling(coeff)``"
    "Opis", "Ustawianie współczynnika kompensacji tarcia przegubów - montaż stały - montaż sufitowy"
    "Parametry wymagane", "- ``coeff=[j1,j2,j3,j4,j5,j6]``: Współczynniki kompensacji dla sześciu przegubów"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie współczynnika kompensacji tarcia przegubów - montaż swobodny
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetFrictionValue_freedom(coeff)``"
    "Opis", "Ustawianie współczynnika kompensacji tarcia przegubów - montaż swobodny"
    "Parametry wymagane", "- ``coeff=[j1,j2,j3,j4,j5,j6]``: Współczynniki kompensacji dla sześciu przegubów"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Przykład kodu ustawiania kompensacji tarcia przegubów robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    lcoeff = [0.9, 0.9, 0.9, 0.9, 0.9, 0.9]
    wcoeff = [0.4, 0.4, 0.4, 0.4, 0.4, 0.4]
    ccoeff = [0.6, 0.6, 0.6, 0.6, 0.6, 0.6]
    fcoeff = [0.5, 0.5, 0.5, 0.5, 0.5, 0.5]
    rtn = robot.FrictionCompensationOnOff(1)
    print(f"FrictionCompensationOnOff rtn is {rtn}")
    rtn = robot.SetFrictionValue_level(lcoeff)
    print(f"SetFrictionValue_level rtn is {rtn}")
    rtn = robot.SetFrictionValue_wall(wcoeff)
    print(f"SetFrictionValue_wall rtn is {rtn}")
    rtn = robot.SetFrictionValue_ceiling(ccoeff)
    print(f"SetFrictionValue_ceiling rtn is {rtn}")
    rtn = robot.SetFrictionValue_freedom(fcoeff)
    print(f"SetFrictionValue_freedom rtn is {rtn}")
    robot.CloseRPC()

Sprawdzanie kodu błędu robota
+++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetRobotErrorCode()``"
    "Opis", "Sprawdzanie kodu błędu robota"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``[maincode subcode]``: Kod błędu robota, maincode-główny kod błędu, subcode-podrzędny kod błędu"

Czyszczenie stanu błędu
+++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ResetAllError()``"
    "Opis", "Czyszczenie stanu błędu, można wyczyścić tylko błędy, które można zresetować"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Przykład kodu pobierania stanu awarii i czyszczenia błędu robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    p1Joint = [-108.145, -50.137, 85.818, -125.599, -87.946, 74.329]
    robot.MoveJ(joint_pos=p1Joint, tool=5, user=2, vel=50)
    time.sleep(1)
    error,[maincode, subcode] = robot.GetRobotErrorCode()
    print(f"robot maincode is {maincode}; subcode is {subcode}")
    time.sleep(1)
    robot.ResetAllError()
    time.sleep(1)
    error,[maincode, subcode] = robot.GetRobotErrorCode()
    print(f"robot maincode is {maincode}; subcode is {subcode}")
    robot.CloseRPC()

Ustawianie parametrów monitorowania temperatury i prędkości wentylatora szerokonapięciowej skrzynki kontrolnej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetWideBoxTempFanMonitorParam(enable, period)``"
    "Opis", "Ustawianie parametrów monitorowania temperatury i prędkości wentylatora szerokonapięciowej skrzynki kontrolnej"
    "Parametry wymagane", "- ``enable``: 0-niewłączone monitorowanie; 1-włączone monitorowanie
    - ``period``: Okres monitorowania (s), zakres 1-100"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Pobieranie parametrów monitorowania temperatury i prędkości wentylatora szerokonapięciowej skrzynki kontrolnej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetWideBoxTempFanMonitorParam()``"
    "Opis", "Pobieranie parametrów monitorowania temperatury i prędkości wentylatora szerokonapięciowej skrzynki kontrolnej"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``enable``: 0-niewłączone monitorowanie; 1-włączone monitorowanie
    - ``period``: Okres monitorowania (s), zakres 1-100"

Przykład kodu pobierania temperatury i prądu wentylatora szerokonapięciowej skrzynki kontrolnej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    robot.SetWideBoxTempFanMonitorParam(1, 2)
    error, enable, period = robot.GetWideBoxTempFanMonitorParam()
    print(f"GetWideBoxTempFanMonitorParam enable is:{enable},period is:{period}")
    for i in range(100):
        error, pkg = robot.GetRobotRealTimeState()
        print(f"robot ctrl box temp is:{pkg.wideVoltageCtrlBoxTemp},fan current is:{pkg.wideVoltageCtrlBoxFanCurrent}")
        time.sleep(0.1)
    rtn = robot.SetWideBoxTempFanMonitorParam(0, 2)
    print(f"SetWideBoxTempFanMonitorParam rtn is:{rtn}")
    error, enable, period = robot.GetWideBoxTempFanMonitorParam()
    print(f"GetWideBoxTempFanMonitorParam enable is:{enable},period is:{period}")
    for i in range(100):
        error, pkg = robot.GetRobotRealTimeState()
        print(f"robot ctrl box temp is:{pkg.wideVoltageCtrlBoxTemp},fan current is:{pkg.wideVoltageCtrlBoxFanCurrent}")
        time.sleep(0.1)
    robot.CloseRPC()

Ustawianie punktu kalibracji ogniska
++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetFocusCalibPoint(pointNum, point)``"
    "Opis", "Ustawianie punktu kalibracji ogniska"
    "Parametry wymagane", "- ``pointNum``: Numer punktu kalibracji ogniska 1-8
    - ``point``: Współrzędne punktu kalibracyjnego"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Obliczanie wyniku kalibracji ogniska
++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``ComputeFocusCalib(pointNum)``"
    "Opis", "Obliczanie wyniku kalibracji ogniska"
    "Parametry wymagane", "- ``pointNum``: Liczba punktów kalibracyjnych"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``resultPos``: Wynik kalibracji XYZ
    - ``accuracy``: Błąd dokładności kalibracji"

Rozpoczęcie śledzenia ogniska
+++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``FocusStart(kp=50.0, kpredic=19.0, aMax=1440, vMax=180, type=0)``"
    "Opis", "Rozpoczęcie śledzenia ogniska"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "- ``kp``: Parametr proporcjonalny, domyślnie 50.0
    - ``kpredic``: Parametr sprzężenia przedniego, domyślnie 19.0
    - ``aMax``: Maksymalne ograniczenie przyspieszenia kątowego, domyślnie 1440°/s^2
    - ``vMax``: Maksymalne ograniczenie prędkości kątowej, domyślnie 180°/s
    - ``type``: Blokowanie kierunku osi X (0-odniesienie do wektora wejściowego; 1-poziomo; 2-pionowo), domyślnie 0"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Zatrzymanie śledzenia ogniska
+++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``FocusEnd()``"
    "Opis", "Zatrzymanie śledzenia ogniska"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Ustawianie współrzędnych ogniska
++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetFocusPosition(pos)``"
    "Opis", "Ustawianie współrzędnych ogniska"
    "Parametry wymagane", "- ``pos``: Współrzędne ogniska XYZ"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Przykład kodu śledzenia ogniska robota
++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    p1Desc = [186.331, 487.913, 209.850, 149.030, 0.688, -114.347]
    p1Joint = [-127.876, -75.341, 115.417, -122.741, -59.820, 74.300]
    p2Desc = [69.721, 535.073, 202.882, -144.406, -14.775, -89.012]
    p2Joint = [-101.780, -69.828, 110.917, -125.740, -127.841, 74.300]
    p3Desc = [146.861, 578.426, 205.598, 175.997, -36.178, -93.437]
    p3Joint = [-112.851, -60.191, 86.566, -80.676, -97.463, 74.300]
    p4Desc = [136.284, 509.876, 225.613, 178.987, 1.372, -100.696]
    p4Joint = [-116.397, -76.281, 113.845, -128.611, -88.654, 74.299]
    p5Desc = [138.395, 505.972, 298.016, 179.134, 2.147, -101.110]
    p5Joint = [-116.814, -82.333, 109.162, -118.662, -88.585, 74.302]
    p6Desc = [105.553, 454.325, 232.017, -179.426, 0.444, -99.952]
    p6Joint = [-115.649, -84.367, 122.447, -128.663, -90.432, 74.303]
    exaxisPos = [0, 0, 0, 0]
    offdese = [0, 0, 100, 0, 0, 0]
    robot.MoveJ(joint_pos=p1Joint,tool=0,user=0,vel=100,acc=100,ovl=100,exaxis_pos=exaxisPos,blendT=-1,offset_flag=0,offset_pos=offdese)
    robot.SetTcp4RefPoint(1)
    robot.MoveJ(joint_pos=p2Joint,tool=0,user=0,vel=100,acc=100,ovl=100,exaxis_pos=exaxisPos,blendT=-1,offset_flag=0,offset_pos=offdese)
    robot.SetTcp4RefPoint(2)
    robot.MoveJ(joint_pos=p3Joint,tool=0,user=0,vel=100,acc=100,ovl=100,exaxis_pos=exaxisPos,blendT=-1,offset_flag=0,offset_pos=offdese)
    robot.SetTcp4RefPoint(3)
    robot.MoveJ(joint_pos=p4Joint,tool=0,user=0,vel=100,acc=100,ovl=100,exaxis_pos=exaxisPos,blendT=-1,offset_flag=0,offset_pos=offdese)
    robot.SetTcp4RefPoint(4)
    rtn,coordRtn = robot.ComputeTcp4()
    print(f"4 Point ComputeTool {rtn} coord is {coordRtn[0]} {coordRtn[1]} {coordRtn[2]} "
          f"{coordRtn[3]} {coordRtn[4]} {coordRtn[5]}")
    robot.SetToolCoord(1, coordRtn, 0, 0, 1, 0)
    error, p1Desc = robot.GetForwardKin(p1Joint)
    error, p2Desc = robot.GetForwardKin(p2Joint)
    error, p3Desc = robot.GetForwardKin(p3Joint)
    robot.SetFocusCalibPoint(1, p1Desc)
    robot.SetFocusCalibPoint(2, p2Desc)
    robot.SetFocusCalibPoint(3, p3Desc)
    rtn, resultPos, accuracy = robot.ComputeFocusCalib(pointNum=3)
    print(f"ComputeFocusCalib coord is {rtn} {resultPos[0]} {resultPos[1]} {resultPos[2]} accuracy is {accuracy}")
    rtn = robot.SetFocusPosition(resultPos)
    error, p5Desc = robot.GetForwardKin(p5Joint)
    error, p6Desc = robot.GetForwardKin(p6Joint)
    robot.MoveL(desc_pos=p5Desc,tool=1,user=0,vel=10,acc=100,ovl=100,blendR=-1,blendMode=0,exaxis_pos=exaxisPos,search=0,offset_flag=1,offset_pos=offdese)
    robot.MoveL(desc_pos=p6Desc,tool=1,user=0,vel=10,acc=100,ovl=100,blendR=-1,blendMode=0,exaxis_pos=exaxisPos,search=0,offset_flag=1,offset_pos=offdese)
    robot.FocusStart(50, 19, 710, 90, 0)
    robot.MoveL(desc_pos=p5Desc,tool=1,user=0,vel=10,acc=100,ovl=100,blendR=-1,blendMode=0,exaxis_pos=exaxisPos,search=0,offset_flag=1,offset_pos=offdese)
    robot.MoveL(desc_pos=p6Desc,tool=1,user=0,vel=10,acc=100,ovl=100,blendR=-1,blendMode=0,exaxis_pos=exaxisPos,search=0,offset_flag=1,offset_pos=offdese)
    robot.FocusEnd()
    robot.CloseRPC()

Włączenie funkcji kalibracji czułości czujnika momentu obrotowego przegubów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``JointSensitivityEnable(status)``"
    "Opis", "Włączenie funkcji kalibracji czułości czujnika momentu obrotowego przegubów"
    "Parametry wymagane", "- ``status``: 0-wyłączone; 1-włączone"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Zbieranie danych czułości czujnika momentu obrotowego przegubów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``JointSensitivityCollect()``"
    "Opis", "Zbieranie danych czułości czujnika momentu obrotowego przegubów"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"
    
Pobieranie wyniku kalibracji czułości czujnika momentu obrotowego przegubów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``JointSensitivityCalibration()``"
    "Opis", "Pobieranie wyniku kalibracji czułości czujnika momentu obrotowego przegubów"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``calibResult``: Czułość przegubów j1~j6 [0-1]
    - ``linearityn``: Liniowość przegubów j1~j6 [0-1]"

Pobieranie błędu histerezy czujnika momentu obrotowego przegubów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``JointHysteresisError()``"
    "Opis", "Pobieranie błędu histerezy czujnika momentu obrotowego przegubów"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``hysteresisError``: Błąd histerezy przegubów j1~j6"

Pobieranie powtarzalności czujnika momentu obrotowego przegubów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``JointRepeatability()``"
    "Opis", "Pobieranie powtarzalności czujnika momentu obrotowego przegubów"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``repeatability``: Powtarzalność przegubów j1~j6"

Ustawianie parametrów czujnika siły przegubów
++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetAdmittanceParams(M, B, K, threshold, sensitivity, setZeroFlag)``"
    "Opis", "Ustawianie parametrów czujnika siły przegubów"
    "Parametry wymagane", "
    - ``M``: Współczynniki masy J1-J6 [0.001 ~ 10]
    - ``B``: Współczynniki tłumienia J1-J6 [0.001 ~ 10]
    - ``K``: Współczynniki sztywności J1-J6 [0.001 ~ 10]
    - ``threshold``: Próg sterowania siłą, Nm
    - ``sensitivity``: Czułość, Nm/V, [0 ~ 10]
    - ``setZeroFlag``: Flaga włączenia funkcji; 0-wyłączona; 1-włączona; 2-rejestracja punktu zerowego w pozycji 1; 3-rejestracja punktu zerowego w pozycji 2"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode"

Przykład kodu automatycznej kalibracji czułości czujnika momentu obrotowego przegubów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    robot = Robot.RPC('192.168.58.2')
    rtn = robot.JointSensitivityEnable(0)
    rtn = robot.JointSensitivityEnable(1)
    print(f"JointSensitivityEnable rtn is {rtn}")
    curJPos = [0.0] * 6
    rtn, curJPos = robot.GetActualJointPosDegree(0)
    epos = [0.0] * 4
    offset_pos = [0.0] * 6
    jointPos1 = [curJPos[0], 0.0, 0.0, -90.0, 0.02, curJPos[5]]
    descPos1 = [0.0] * 6
    rtn, descPos1 = robot.GetForwardKin(jointPos1)
    robot.MoveJ(joint_pos=jointPos1, desc_pos=descPos1, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.2)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 1 rtn is {rtn}")
    time.sleep(0.1)
    jointPos2 = [curJPos[0], -30.0, 0.0, -90.0, 0.02, curJPos[5]]
    descPos2 = [0.0] * 6
    rtn, descPos2 = robot.GetForwardKin(jointPos2)
    robot.MoveJ(joint_pos=jointPos2, desc_pos=descPos2, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 2 rtn is {rtn}")
    time.sleep(0.1)
    jointPos3 = [curJPos[0], -60.0, 0.0, -90.0, 0.02, curJPos[5]]
    descPos3 = [0.0] * 6
    rtn, descPos3 = robot.GetForwardKin(jointPos3)
    robot.MoveJ(joint_pos=jointPos3, desc_pos=descPos3, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 3 rtn is {rtn}")
    time.sleep(0.1)
    jointPos4 = [curJPos[0], -90.0, 0.0, -90.0, 0.02, curJPos[5]]
    descPos4 = [0.0] * 6
    rtn, descPos4 = robot.GetForwardKin(jointPos4)
    robot.MoveJ(joint_pos=jointPos4, desc_pos=descPos4, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 4 rtn is {rtn}")
    time.sleep(0.1)
    jointPos5 = [curJPos[0], -120.0, 0.0, -90.0, 0.02, curJPos[5]]
    descPos5 = [0.0] * 6
    rtn, descPos5 = robot.GetForwardKin(jointPos5)
    robot.MoveJ(joint_pos=jointPos5, desc_pos=descPos5, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 5 rtn is {rtn}")
    time.sleep(0.1)
    jointPos6 = [curJPos[0], -150.0, 0.0, -90.0, 0.02, curJPos[5]]
    descPos6 = [0.0] * 6
    rtn, descPos6 = robot.GetForwardKin(jointPos6)
    robot.MoveJ(joint_pos=jointPos6, desc_pos=descPos6, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 6 rtn is {rtn}")
    time.sleep(0.1)
    jointPos7 = [curJPos[0], -180.0, 0.0, -90.0, 0.02, curJPos[5]]
    descPos7 = [0.0] * 6
    rtn, descPos7 = robot.GetForwardKin(jointPos7)
    robot.MoveJ(joint_pos=jointPos7, desc_pos=descPos7, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 7 rtn is {rtn}")
    time.sleep(0.1)
    robot.MoveJ(joint_pos=jointPos6, desc_pos=descPos6, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 8 rtn is {rtn}")
    time.sleep(0.1)
    robot.MoveJ(joint_pos=jointPos5, desc_pos=descPos5, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 9 rtn is {rtn}")
    time.sleep(0.1)
    robot.MoveJ(joint_pos=jointPos4, desc_pos=descPos4, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 10 rtn is {rtn}")
    time.sleep(0.1)
    robot.MoveJ(joint_pos=jointPos3, desc_pos=descPos3, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 11 rtn is {rtn}")
    time.sleep(0.1)
    robot.MoveJ(joint_pos=jointPos2, desc_pos=descPos2, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 12 rtn is {rtn}")
    time.sleep(0.1)
    robot.MoveJ(joint_pos=jointPos1, desc_pos=descPos1, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.2)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 13 rtn is {rtn}")
    time.sleep(0.1)
    calibResult = [0.0] * 6
    linearity = [0.0] * 6
    rtn,calibResult, linearity = robot.JointSensitivityCalibration()
    print(f"JointSensitivityCalibration rtn is {rtn}")
    rtn = robot.JointSensitivityEnable(0)
    print(f"JointSensitivityEnable rtn is {rtn}")
    print(f"jointSensor Calib result is {calibResult[0]},{calibResult[1]},{calibResult[2]},{calibResult[3]},{calibResult[4]},{calibResult[5]}")
    print( f"jointSensor linearity is {linearity[0]},{linearity[1]},{linearity[2]},{linearity[3]},{linearity[4]},{linearity[5]}")
    hysteresisError = [0.0] * 6
    rtn,hysteresisError = robot.JointHysteresisError()
    print(f"JointHysteresisError result is {hysteresisError[0]},{hysteresisError[1]},{hysteresisError[2]},{hysteresisError[3]},{hysteresisError[4]},{hysteresisError[5]}")
    repeatability = [0.0] * 6
    rtn,repeatability = robot.JointRepeatability()
    print(f"JointRepeatability result is {repeatability[0]},{repeatability[1]},{repeatability[2]},{repeatability[3]},{repeatability[4]},{repeatability[5]}")
    M = [1.0] * 6
    B = [1.0] * 6
    K = [0.0] * 6
    threshold = [1.0] * 6
    setZeroFlag = 1
    rtn = robot.SetAdmittanceParams(M, B, K, threshold, calibResult, setZeroFlag)
    print(f"SetAdmittanceParams rtn is {rtn}")
    robot.CloseRPC()

Pobieranie liczby błędnych ramek dla 8 portów węzłów podrzędnych robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetSlavePortErrCounter()``"
    "Opis", "Pobieranie liczby błędnych ramek dla 8 portów węzłów podrzędnych robota"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``inRecvErr``: Liczba błędnych ramek odebranych na wejściu
    - ``inCRCErr``: Liczba błędnych ramek CRC na wejściu
    - ``inTransmitErr``: Liczba błędnych ramek transmitowanych na wejściu
    - ``inLinkErr``: Liczba błędów łącza na wejściu
    - ``outRecvErr``: Liczba błędnych ramek odebranych na wyjściu
    - ``outCRCErr``: Liczba błędnych ramek CRC na wyjściu
    - ``outTransmitErr``: Liczba błędnych ramek transmitowanych na wyjściu
    - ``outLinkErr``: Liczba błędów łącza na wyjściu"

Zerowanie licznika błędnych ramek portu węzła podrzędnego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``JointSensitivityEnable(slaveID)``"
    "Opis", "Zerowanie licznika błędnych ramek portu węzła podrzędnego"
    "Parametry wymagane", "- ``slaveID``: Numer węzła podrzędnego 0~7"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Przykład kodu pobierania błędnych ramek portu węzła podrzędnego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    inRecvErr = [0] * 8
    inCRCErr = [0] * 8
    inTransmitErr = [0] * 8
    inLinkErr = [0] * 8
    outRecvErr = [0] * 8
    outCRCErr = [0] * 8
    outTransmitErr = [0] * 8
    outLinkErr = [0] * 8
    rtn,inRecvErr, inCRCErr, inTransmitErr, inLinkErr, outRecvErr, outCRCErr, outTransmitErr, outLinkErr = robot.GetSlavePortErrCounter()
    for i in range(8):
        if inRecvErr[i] != 0:
            print(f"inRecvErr {i} is {inRecvErr[i]}")
        if inCRCErr[i] != 0:
            print(f"inCRCErr {i} is {inCRCErr[i]}")
        if inTransmitErr[i] != 0:
            print(f"inTransmitErr {i} is {inTransmitErr[i]}")
        if inLinkErr[i] != 0:
            print(f"inLinkErr {i} is {inLinkErr[i]}")
        if outRecvErr[i] != 0:
            print(f"outRecvErr {i} is {outRecvErr[i]}")
        if outCRCErr[i] != 0:
            print(f"outCRCErr {i} is {outCRCErr[i]}")
        if outTransmitErr[i] != 0:
            print(f"outTransmitErr {i} is {outTransmitErr[i]}")
        if outLinkErr[i] != 0:
            print(f"outLinkErr {i} is {outLinkErr[i]}")
    print("others has no err!")
    for i in range(8):
        robot.SlavePortErrCounterClear(i)
    robot.CloseRPC()

Ustawianie współczynnika sprzężenia przedniego prędkości dla każdej osi
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetVelFeedForwardRatio(radio)``"
    "Opis", "Ustawianie współczynnika sprzężenia przedniego prędkości dla każdej osi"
    "Parametry wymagane", "- ``radio``: Współczynnik sprzężenia przedniego prędkości dla każdej osi"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "Kod błędu sukces-0 błąd- errcode"

Pobieranie współczynnika sprzężenia przedniego prędkości dla każdej osi
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetVelFeedForwardRatio()``"
    "Opis", "Pobieranie współczynnika sprzężenia przedniego prędkości dla każdej osi"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``radio``: Współczynnik sprzężenia przedniego prędkości dla każdej osi"

Przykład kodu współczynnika sprzężenia przedniego prędkości robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    setRadio = [1.0, 1.0, 1.0, 1.0, 1.0, 1.0]
    robot.SetVelFeedForwardRatio(setRadio)
    getRadio = [0.0] * 6
    rtn,getRadio = robot.GetVelFeedForwardRatio()
    print(f"{getRadio[0]},{getRadio[1]},{getRadio[2]},{getRadio[3]},{getRadio[4]},{getRadio[5]}")
    robot.CloseRPC()

Kalibracja TCP czujnika fotoelektrycznego - obliczanie RPY narzędzia
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``TCPComputeRPY(Btool, Etool, sensor, radius, dz)``"
    "Opis", "Kalibracja TCP czujnika fotoelektrycznego - obliczanie RPY narzędzia"
    "Parametry wymagane", "
    - ``Btool``: Pozycja kartezjańska robota
    - ``Etool``: Bieżąca wartość układu współrzędnych narzędzia
    - ``Btsenserool``: Bieżąca wartość układu współrzędnych czujnika (tymczasowo niedostępne)
    - ``radius``: Promień ruchu po okręgu mm (tymczasowo niedostępne)
    - ``dz``: Odległość ruchu wzdłuż ujemnego kierunku osi Z układu bazowego; gdy dz = 10000, funkcja bezpośrednio zwraca RPY narzędzia"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode"

Kalibracja TCP czujnika fotoelektrycznego - obliczanie XYZ narzędzia
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``TCPComputeXYZ(select, originDirection, pos1, pos2, pos3, pos4)``"
    "Opis", "Kalibracja TCP czujnika fotoelektrycznego - obliczanie XYZ narzędzia"
    "Parametry wymagane", "
    - ``select``: 0-obliczanie TCP narzędzia; 1-obliczanie punktu początkowego czujnika; 2-obliczanie postawy czujnika; 3-bezpośrednie zwrócenie TCP narzędzia; 4-rejestracja bieżącego układu współrzędnych przedmiotu i narzędzia
    - ``originDirection``: 0-kierunek X; 1-kierunek Y; 2-kierunek Z
    - ``pos1``: Pozycja kartezjańska robota 1
    - ``pos2``: Pozycja kartezjańska robota 2
    - ``pos3``: Pozycja kartezjańska robota 3
    - ``pos4``: Pozycja kartezjańska robota 4"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "
    - Kod błędu sukces-0 błąd- errcode
    - Wartość zwracana (w przypadku pomyślnego wywołania) Wartości XYZ TCP narzędzia"

Kalibracja TCP czujnika fotoelektrycznego - rozpoczęcie rejestracji pozycji środka kołnierza końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``TCPRecordFlangePosStart()``"
    "Opis", "Kalibracja TCP czujnika fotoelektrycznego - rozpoczęcie rejestracji pozycji środka kołnierza końcowego"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode"

Kalibracja TCP czujnika fotoelektrycznego - zatrzymanie rejestracji pozycji środka kołnierza końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``TCPRecordFlangePosEnd()``"
    "Opis", "Kalibracja TCP czujnika fotoelektrycznego - zatrzymanie rejestracji pozycji środka kołnierza końcowego"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode"

Kalibracja TCP czujnika fotoelektrycznego - pobieranie pozycji środka narzędzia końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``TCPGetRecordFlangePos()``"
    "Opis", "Kalibracja TCP czujnika fotoelektrycznego - pobieranie pozycji środka narzędzia końcowego"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "
    - Kod błędu sukces-0 błąd- errcode
    - Wartość zwracana (w przypadku pomyślnego wywołania) Pozycja środka narzędzia końcowego (x,y,z)"

Kalibracja TCP czujnika fotoelektrycznego
++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``PhotoelectricSensorTCPCalibration(self, luaFile, offsetX)``"
    "Opis", "Kalibracja TCP czujnika fotoelektrycznego"
    "Parametry wymagane", "
    - ``luaFile``: Nazwa programu lua do automatycznej kalibracji: np. `FR_CalibrateTheToolTcp.lua`
    - ``offsetX``: Przesunięcie punktu nauczania (x,y,z) mm"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "
    - Kod błędu sukces-0 błąd- errcode
    - Wartość zwracana (w przypadku pomyślnego wywołania) Wartości XYZ TCP narzędzia"

Przykład kodu kalibracji TCP czujnika fotoelektrycznego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 

    from fairino import Robot
    import time
    robot = Robot.RPC('192.168.58.2')
    offset = [10.0, 10.0, 3.0]
    TCP = [0.0] * 6
    rtn, TCP = robot.PhotoelectricSensorTCPCalibration("FR_CalibrateTheToolTcp.lua", offset)
    print(f"PhotoelectricSensorTCPCalibration rtn is {rtn},{TCP[0]},{TCP[1]},{TCP[2]},{TCP[3]},{TCP[4]},{TCP[5]}")
    robot.CloseRPC()
    return 0

Ustawianie Prędkości w Czasie Rzeczywistym (Rama Komendy, Niskie Opóźnienie)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetSpeedInstant(self, vel)``"
    "Opis", "Ustawianie prędkości w czasie rzeczywistym (rama komendy, niskie opóźnienie)"
    "Parametry Wymagane", "
    - ``vel``: Procent prędkości, zakres [0~100]"
    "Parametry Domyślne", "Brak"
    "Wartość Zwracana", "
    - Kod błędu, 0-sukces; niezerowy-błąd"

Ustawianie Przesunięcia Splotu w Czasie Rzeczywistym
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``SetWeaveOffsetRT(self, offset)``"
    "Opis", "Ustawia przesunięcie splotu w czasie rzeczywistym"
    "Parametry Wymagane", "
    - ``offset``: Przesunięcie w czasie rzeczywistym [x,y,z,rx,ry,rz], jednostka [mm, °]"
    "Parametry Domyślne", "Brak"
    "Wartość Zwracana", "
    - Kod błędu, 0-sukces; niezerowy-błąd"

Przykład Kodu Testu Prędkości i Przesunięcia Splotu    
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 

    from fairino import Robot
    import time
    import threading


    def main():
        robot = Robot.RPC('192.168.58.2')
        time.sleep(0.5)  

        epos = [0.0, 0.0, 0.0, 0.0]
        offset_pos = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]

        j1 = [5.027, -84.331, -75.139, -103.690, 86.379, 20.794]
        d1 = [324.752, -83.339, 366.314, -172.321, -0.936, -106.047]

        j2 = [-35.335, -117.598, -57.174, -95.234, 90.001, -19.560]
        d2 = [324.999, -355.439, 260.000, 179.995, 0.003, -105.775]

        j3 = [59.787, -117.594, -57.183, -95.222, 90.006, 75.562]
        d3 = [324.998, 355.441, 260.002, 179.995, 0.003, -105.775]

        rtn = 0

        print("\nStep 1: MoveJ to start point")
        rtn = robot.MoveJ(joint_pos=j1, desc_pos=d1, tool=1, user=0, vel=100, acc=100, ovl=50,
                        exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
        print(f"  MoveJ(j1) rtn={rtn}")
        time.sleep(0.5)

        print("\nStep 2: MoveJ to weave entry point")
        rtn = robot.MoveJ(joint_pos=j2, desc_pos=d2, tool=1, user=0, vel=100, acc=100, ovl=50,
                        exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
        print(f"  MoveJ(j2) rtn={rtn}")
        time.sleep(0.5)

        print("\nStep 3: WeaveStart + MoveL in background thread")
        robot.WeaveStart(0)

        weave_running = True
        move_rtn = [0]  

        def weave_move_thread():
            rtn_val = robot.MoveL(joint_pos=j3, desc_pos=d3, tool=1, user=0, vel=100, acc=100, ovl=5,
                                blendR=-1, offset_flag=0, exaxis_pos=epos, search=0,
                                offset_pos=offset_pos, config=5, velAccParamMode=0, overSpeedStrategy=0, speedPercent=10)
            print(f"  MoveL(weave) thread finished, rtn={rtn_val}")
            move_rtn[0] = rtn_val
            nonlocal weave_running
            weave_running = False

        weave_thread = threading.Thread(target=weave_move_thread)
        weave_thread.daemon = True
        weave_thread.start()
        time.sleep(0.5)  

        print("\nStep 4: SetSpeed test during weaving")
        speed_values = [20, 50, 80, 30, 60, 10]
        for speed in speed_values:
            if not weave_running:
                break
            rtn = robot.SetSpeedInstant(speed)
            print(f"  SetSpeed({speed}) -> rtn={rtn}")
            # rtn, pkg = robot.GetRobotRealTimeState()
            # print(f"target_TCP_CmpSpeed: [{', '.join([f'{x:.3f}' for x in pkg.target_TCP_CmpSpeed])}]")
            time.sleep(5)

        time.sleep(5)

        print("\nStep 5: SetWeaveOffsetRT test (50 iterations, delta=0.1)")
        accum_offset = 0.0
        for i in range(50):
            if not weave_running:
                break
            accum_offset += 1
            weave_offset = [0.0, 0.0, accum_offset, 0.0, 0.0, 0.0]
            rtn = robot.SetWeaveOffsetRT(weave_offset)
            rtn, pkg = robot.GetRobotRealTimeState()
            print(f"  [{i+1}/50] SetWeaveOffsetRT(x={accum_offset:.1f}) -> rtn={rtn}, "
                f"TCP_pos=({pkg.tl_cur_pos[0]:.2f},{pkg.tl_cur_pos[1]:.2f},{pkg.tl_cur_pos[2]:.2f})")
            time.sleep(0.1)

        print("\nStep 6: Wait for weave MoveL, then WeaveEnd")
        weave_thread.join()
        robot.WeaveEnd(0)
        time.sleep(0.5)

        print("\nStep 7: MoveL back to start")
        rtn = robot.MoveL(joint_pos=j1, desc_pos=d1, tool=1, user=0, vel=100, acc=100, ovl=50,
                        blendR=-1, offset_flag=0, exaxis_pos=epos, search=0,
                        offset_pos=offset_pos, config=50, velAccParamMode=0, overSpeedStrategy=0, speedPercent=10)
        print(f"  MoveL(back) rtn={rtn}")

        rtn, pkg = robot.GetRobotRealTimeState()
        print(f"\n  Final robot state: main_code={pkg.main_code}, sub_code={pkg.sub_code}")
        
        robot.CloseRPC()


    if __name__ == "__main__":
        main()    