Zapytanie o stan robota
=======================

.. toctree:: 
    :maxdepth: 5

Pobieranie bieżącej pozycji przegubów (kąt)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetActualJointPosDegree(flag=1)``"
    "Opis", "Pobieranie bieżącej pozycji przegubów (kąt)"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "- ``flag``: 0-blokujący, 1-nieblokujący, domyślnie 1"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``joint_pos=[j1,j2,j3,j4,j5,j6]``: Bieżąca pozycja przegubów (kąt)"

Pobieranie bieżącej pozycji przegubów (radian)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetActualJointPosRadian(flag=1)``"
    "Opis", "Pobieranie bieżącej pozycji przegubów (radian)"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "- ``flag``: 0-blokujący, 1-nieblokujący, domyślnie 1"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``joint_pos=[j1,j2,j3,j4,j5,j6]``: Bieżąca pozycja przegubów (radian)"

Pobieranie prędkości sprzężenia zwrotnego przegubów - deg/s
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetActualJointSpeedsDegree(flag=1)``"
    "Opis", "Pobieranie prędkości sprzężenia zwrotnego przegubów - deg/s"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "- ``flag``: 0-blokujący, 1-nieblokujący, domyślnie 1"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``speed=[j1,j2,j3,j4,j5,j6]``: Prędkości sprzężenia zwrotnego przegubów - deg/s"

Pobieranie przyspieszenia sprzężenia zwrotnego przegubów - deg/s^2
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetActualJointAccDegree(flag=1)``"
    "Opis", "Pobieranie przyspieszenia sprzężenia zwrotnego przegubów - deg/s^2"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "- ``flag``: 0-blokujący, 1-nieblokujący, domyślnie 1"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``acc=[j1,j2,j3,j4,j5,j6]``: Przyspieszenia sprzężenia zwrotnego przegubów - deg/s^2"

Pobieranie prędkości wypadkowej zadanej TCP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetTargetTCPCompositeSpeed(flag=1)``"
    "Opis", "Pobieranie prędkości wypadkowej zadanej TCP"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "- ``flag``: 0-blokujący, 1-nieblokujący, domyślnie 1"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``[tcp_speed,ori_speed]``: tcp_speed - liniowa prędkość wypadkowa ori_speed - prędkość wypadkowa pozy"

Pobieranie prędkości wypadkowej sprzężenia zwrotnego TCP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetActualTCPCompositeSpeed(flag=1)``"
    "Opis", "Pobieranie prędkości wypadkowej sprzężenia zwrotnego TCP"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "- ``flag``: 0-blokujący, 1-nieblokujący, domyślnie 1"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``[tcp_speed,ori_speed]``: tcp_speed - liniowa prędkość wypadkowa ori_speed - prędkość wypadkowa pozy"

Pobieranie prędkości zadanej TCP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetTargetTCPSpeed(flag=1)``"
    "Opis", "Pobieranie prędkości zadanej TCP"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "- ``flag``: 0-blokujący, 1-nieblokujący, domyślnie 1"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``speed=[x,y,z,rx,ry,rz]``: Prędkość zadana TCP, mm/s"

Pobieranie prędkości sprzężenia zwrotnego TCP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetActualTCPSpeed(flag=1)``"
    "Opis", "Pobieranie prędkości sprzężenia zwrotnego TCP"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "- ``flag``: 0-blokujący, 1-nieblokujący, domyślnie 1"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``speed=[x,y,z,rx,ry,rz]``: Prędkość sprzężenia zwrotnego TCP"

Pobieranie bieżącej pozy narzędzia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetActualTCPPose(flag=1)``"
    "Opis", "Pobieranie bieżącej pozy narzędzia"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "- ``flag``: 0-blokujący, 1-nieblokujący, domyślnie 1"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``tcp_pose=[x,y,z,rx,ry,rz]``: Bieżąca poza narzędzia"

Pobieranie bieżącego numeru układu narzędzia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetActualTCPNum(flag=1)``"
    "Opis", "Pobieranie bieżącego numeru układu narzędzia"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "- ``flag``: 0-blokujący, 1-nieblokujący, domyślnie 1"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``tool_id``: Numer układu narzędzia"

Pobieranie bieżącego numeru układu przedmiotu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetActualWObjNum(flag=1)``"
    "Opis", "Pobieranie bieżącego numeru układu przedmiotu"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "- ``flag``: 0-blokujący, 1-nieblokujący, domyślnie 1"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``wobj_id``: Numer układu przedmiotu"

Pobieranie bieżącej pozy kołnierza końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetActualToolFlangePose(flag=1)``"
    "Opis", "Pobieranie bieżącej pozy kołnierza końcowego"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "- ``flag``: 0-blokujący, 1-nieblokujący, domyślnie 1"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``flange_pose=[x,y,z,rx,ry,rz]``: Bieżąca poza kołnierza końcowego"

Pobieranie bieżącego momentu obrotowego przegubów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetJointTorques(flag=1)``"
    "Opis", "Pobieranie bieżącego momentu obrotowego przegubów"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "``flag``: 0-blokujący, 1-nieblokujący, domyślnie 1"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``torques=[j1,j2,j3,j4,j5,j6]``: Moment obrotowy przegubów"

Pobieranie czasu systemowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetSystemClock()``"
    "Opis", "Pobieranie czasu systemowego"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``t_ms``: Czas systemowy, jednostka [ms]"

Sprawdzanie, czy ruch robota został zakończony
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetRobotMotionDone()``"
    "Opis", "Sprawdzanie, czy ruch robota został zakończony"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``state``: Stan ruchu robota, 0-niezakończony, 1-zakończony"

Sprawdzanie długości bufora kolejki ruchu robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetMotionQueueLength()``"
    "Opis", "Sprawdzanie długości bufora kolejki ruchu robota"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``len``: Długość bufora"

Pobieranie stanu zatrzymania awaryjnego robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetRobotEmergencyStopState()``"
    "Opis", "Pobieranie stanu zatrzymania awaryjnego robota"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``state``: Stan zatrzymania awaryjnego, 0-brak zatrzymania awaryjnego, 1-zatrzymanie awaryjne"

Pobieranie stanu komunikacji SDK z robotem
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetSDKComState()``"
    "Opis", "Pobieranie stanu komunikacji SDK z robotem"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``state``: Stan komunikacji, 0-komunikacja normalna, 1-komunikacja nieprawidłowa"

Pobieranie sygnału bezpiecznego zatrzymania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetSafetyStopState()``"
    "Opis", "Pobieranie sygnału bezpiecznego zatrzymania"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``[si0_state,si1_state]``: si0_state - sygnał bezpiecznego zatrzymania SI0, 0-nieaktywny, 1-aktywny; si1_state - sygnał bezpiecznego zatrzymania SI1, 0-nieaktywny, 1-aktywny"

Pobieranie bieżącej temperatury sterownika przegubu (℃)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetJointDriverTemperature()``"
    "Opis", "Pobieranie bieżącej temperatury sterownika przegubu (℃)"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``data=[t1,t2,t3,t4,t5,t6]``: Bieżące temperatury każdego przegubu"

Pobieranie bieżącego momentu obrotowego sterownika przegubu (Nm)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetJointDriverTorque()``"
    "Opis", "Pobieranie bieżącego momentu obrotowego sterownika przegubu (Nm)"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``data=[j1,j2,j3,j4,j5,j6]``: Moment obrotowy przegubów [fx,fy,fz,tx,ty,tz]"

Pobieranie stanu robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetRobotRealTimeState()``"
    "Opis", "Pobieranie stanu robota"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``robot_state_pkg``: Struktura stanu robota"

Przykład kodu zapytania o stan robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    error,[yangle, zangle] = robot.GetRobotInstallAngle()
    print(f"yangle:{yangle},zangle:{zangle}")
    error,j_deg = robot.GetActualJointPosDegree(0)
    print(f"joint pos deg:{j_deg[0]},{j_deg[1]},{j_deg[2]},{j_deg[3]},{j_deg[4]},{j_deg[5]}")
    error,jointSpeed = robot.GetActualJointSpeedsDegree(0)
    print(f"joint speeds deg:{jointSpeed[0]},{jointSpeed[1]},{jointSpeed[2]},{jointSpeed[3]},{jointSpeed[4]},{jointSpeed[5]}")
    error,jointAcc = robot.GetActualJointAccDegree(0)
    print(f"joint acc deg:{jointAcc[0]},{jointAcc[1]},{jointAcc[2]},{jointAcc[3]},{jointAcc[4]},{jointAcc[5]}")
    error,[tcp_speed, ori_speed] = robot.GetTargetTCPCompositeSpeed(0)
    print(f"GetTargetTCPCompositeSpeed tcp {tcp_speed}; ori {ori_speed}")
    error,[tcp_speed, ori_speed] = robot.GetActualTCPCompositeSpeed(0)
    print(f"GetActualTCPCompositeSpeed tcp {tcp_speed}; ori {ori_speed}")
    error,targetSpeed = robot.GetTargetTCPSpeed(0)
    print(f"GetTargetTCPSpeed {targetSpeed[0]},{targetSpeed[1]},{targetSpeed[2]},{targetSpeed[3]},{targetSpeed[4]},{targetSpeed[5]}")
    error,actualSpeed = robot.GetActualTCPSpeed(0)
    print(f"GetActualTCPSpeed {actualSpeed[0]},{actualSpeed[1]},{actualSpeed[2]},{actualSpeed[3]},{actualSpeed[4]},{actualSpeed[5]}")
    error,tcp = robot.GetActualTCPPose(0)
    print(f"tcp pose:{tcp[0]},{tcp[1]},{tcp[2]},{tcp[3]},{tcp[4]},{tcp[5]}")
    error,flange = robot.GetActualToolFlangePose(0)
    print(f"flange pose:{flange[0]},{flange[1]},{flange[2]},{flange[3]},{flange[4]},{flange[5]}")
    error,id = robot.GetActualTCPNum(0)
    print(f"tcp num:{id}")
    error,id = robot.GetActualWObjNum(0)
    print(f"wobj num:{id}")
    error,jtorque = robot.GetJointTorques(0)
    print(f"torques:{jtorque[0]},{jtorque[1]},{jtorque[2]},{jtorque[3]},{jtorque[4]},{jtorque[5]}")
    error,t_ms = robot.GetSystemClock()
    print(f"system clock:{t_ms}")
    error,config = robot.GetRobotCurJointsConfig()
    print(f"joint config:{config}")
    error,motionDone = robot.GetRobotMotionDone()
    print(f"GetRobotMotionDone:{motionDone}")
    error,len = robot.GetMotionQueueLength()
    print(f"GetMotionQueueLength:{len}")
    error,emergState = robot.GetRobotEmergencyStopState()
    print(f"GetRobotEmergencyStopState:{emergState}")
    error,comstate = robot.GetSDKComState()
    print(f"GetSDKComState:{comstate}")
    error,[si0_state, si1_state] = robot.GetSafetyStopState()
    print(f"GetSafetyStopState:{si0_state} {si1_state}")
    error,temp = robot.GetJointDriverTemperature()
    print(f"Temperature:{temp[0]},{temp[1]},{temp[2]},{temp[3]},{temp[4]},{temp[5]}")
    error,torque = robot.GetJointDriverTorque()
    print(f"torque:{torque[0]},{torque[1]},{torque[2]},{torque[3]},{torque[4]},{torque[5]}")
    error,pkg = robot.GetRobotRealTimeState()
    robot.CloseRPC()

Rozwiązanie kinematyki odwrotnej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetInverseKin(type,desc_pos,config=-1)``"
    "Opis", "Kinematyka odwrotna, rozwiązanie pozycji przegubów na podstawie pozy kartezjańskiej"
    "Parametry wymagane", "- ``type``: 0-pozycja absolutna (układ bazowy), 1-pozycja względna (układ bazowy), 2-pozycja względna (układ narzędzia)
    - ``desc_pose``: [x,y,z,rx,ry,rz], poza narzędzia, jednostka [mm][°]"
    "Parametry domyślne", "- ``config``: Konfiguracja przegubów, [-1]-obliczenia względem bieżącej pozycji przegubów, [0~7]-obliczenia według konfiguracji przegubów, domyślnie -1"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``joint_pos=[j1,j2,j3,j4,j5,j6]``: Rozwiązanie kinematyki odwrotnej, pozycja przegubów na podstawie pozy kartezjańskiej"

Rozwiązanie kinematyki odwrotnej - z określoną pozycją odniesienia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetInverseKinRef(type,desc_pos,joint_pos_ref)``"
    "Opis", "Kinematyka odwrotna, rozwiązanie pozycji przegubów na podstawie pozy narzędzia, z określoną pozycją odniesienia przegubów"
    "Parametry wymagane", "- ``type``: 0-pozycja absolutna (układ bazowy), 1-pozycja względna (układ bazowy), 2-pozycja względna (układ narzędzia)
    - ``desc_pos``: [x,y,z,rx,ry,rz] poza narzędzia, jednostka [mm][°]
    - ``joint_pos_ref``: [j1,j2,j3,j4,j5,j6], referencyjna pozycja przegubów, jednostka [°]"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``joint_pos=[j1,j2,j3,j4,j5,j6]``: Rozwiązanie kinematyki odwrotnej, pozycja przegubów na podstawie pozy narzędzia"

Rozwiązanie kinematyki odwrotnej, przestrzeń kartezjańska z uwzględnieniem pozycji osi rozszerzenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetInverseKinExaxis(type, desc_pos, exaxis, tool, workPiece)``"
    "Opis", "Rozwiązanie kinematyki odwrotnej, przestrzeń kartezjańska z uwzględnieniem pozycji osi rozszerzenia"
    "Parametry wymagane", "- ``type``: 0-pozycja absolutna (układ bazowy), 1-pozycja przyrostowa (układ bazowy), 2-pozycja przyrostowa (układ narzędzia)
    - ``desc_pos``: Pozycja kartezjańska
    - ``exaxis``: Pozycja osi rozszerzenia
    - ``tool``: Numer narzędzia
    - ``workPiece``: Numer przedmiotu"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``joint_pos``: Pozycja przegubów"

Przykład kodu rozwiązania kinematyki odwrotnej z uwzględnieniem pozycji osi rozszerzenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    robot = Robot.RPC('192.168.58.2')
    desc = [99.957, -0.002, 29.994, -176.569, -6.757, -167.462]
    exaxis = [100.0, 0.0, 0.0, 0.0]
    jointPos = [0.0] * 6
    offsetPos = [0.0] * 6
    rtn,pkg = robot.GetRobotRealTimeState()
    toolnum = pkg.tool
    workPcsNum = pkg.user
    rtn, jointPos = robot.GetInverseKinExaxis(0, desc, exaxis, toolnum, workPcsNum)
    print(f"GetInverseKinExaxis joint is {jointPos[0]},{jointPos[1]},{jointPos[2]},{jointPos[3]},{jointPos[4]},{jointPos[5]}")
    robot.ExtAxisMove(exaxis, 100, -1)
    robot.MoveJ(joint_pos=jointPos, desc_pos=desc, tool=toolnum, user=workPcsNum, vel=100.0, acc=100.0, ovl=100.0, exaxis_pos=exaxis, blendT=-1, offset_flag=0, offset_pos=offsetPos)
    robot.CloseRPC()
    return 0

Sprawdzanie, czy kinematyka odwrotna ma rozwiązanie
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetInverseKinHasSolution(type,desc_pos,joint_pos_ref)``"
    "Opis", "Sprawdzanie, czy kinematyka odwrotna (rozwiązanie pozycji przegubów na podstawie pozy narzędzia) ma rozwiązanie"
    "Parametry wymagane", "- ``type``: 0-pozycja absolutna (układ bazowy), 1-pozycja względna (układ bazowy), 2-pozycja względna (układ narzędzia)
    - ``desc_pos``: [x,y,z,rx,ry,rz] poza narzędzia, jednostka [mm][°]
    - ``joint_pos_ref``: [j1,j2,j3,j4,j5,j6], referencyjna pozycja przegubów, jednostka [°]"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``result``: „True” - ma rozwiązanie, „False” - nie ma rozwiązania"

Rozwiązanie kinematyki prostej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetForwardKin(joint_pos)``"
    "Opis", "Kinematyka prosta, rozwiązanie pozy narzędzia na podstawie pozycji przegubów"
    "Parametry wymagane", "- ``joint_pos``: [j1,j2,j3,j4,j5,j6]: pozycja przegubów, jednostka [°]"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``desc_pos=[x,y,z,rx,ry,rz]``: Rozwiązanie kinematyki prostej, poza narzędzia na podstawie pozycji przegubów"

Przykład kodu obliczeń kinematyki prostej i odwrotnej robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    j1 = [-11.904, -99.669, 117.473, -108.616, -91.726, 74.256]
    desc_pos1 = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    error, inverseRtn = robot.GetInverseKin(0, desc_pos=desc_pos1, config=-1)
    print(f"dcs1 GetInverseKin rtn is {inverseRtn[0]}, {inverseRtn[1]}, {inverseRtn[2]}, "
          f"{inverseRtn[3]}, {inverseRtn[4]}, {inverseRtn[5]}")
    error, inverseRtn = robot.GetInverseKinRef(0, desc_pos=desc_pos1, joint_pos_ref=j1)
    print(f"dcs1 GetInverseKinRef rtn is {inverseRtn[0]}, {inverseRtn[1]}, {inverseRtn[2]}, "
          f"{inverseRtn[3]}, {inverseRtn[4]}, {inverseRtn[5]}")
    error, hasResult = robot.GetInverseKinHasSolution(0, desc_pos=desc_pos1, joint_pos_ref=j1)
    print(f"dcs1 GetInverseKinRef result {hasResult}")
    error, forwordResult = robot.GetForwardKin(j1)
    print(f"jpos1 forwordResult rtn is {forwordResult[0]}, {forwordResult[1]}, {forwordResult[2]}, "
          f"{forwordResult[3]}, {forwordResult[4]}, {forwordResult[5]}")
    robot.CloseRPC()

Zapytanie o dane punktu zarządzania nauczaniem robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetRobotTeachingPoint(name)``"
    "Opis", "Zapytanie o dane punktu zarządzania nauczaniem robota"
    "Parametry wymagane", "``name``: Nazwa punktu"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``[x,y,z,rx,ry,rz,j1,j2,j3,j4,j5,j6,tool,wobj,speed,acc,e1,e2,e3,e4]``: Dane punktu"

Pobieranie parametrów kompensacji DH
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetDHCompensation()``"
    "Opis", "Pobieranie parametrów kompensacji DH"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``dhCompensation=[cmpstD1,cmpstA2,cmpstA3,cmpstD4,cmpstD5,cmpstD6]``: Wartości kompensacji parametrów DH robota (mm)"

Pobieranie numeru SN skrzynki kontrolnej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetRobotSN()``"
    "Opis", "Pobieranie numeru SN skrzynki kontrolnej"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``SNCode``: Numer SN skrzynki kontrolnej"

Przykład kodu zapytania o dane punktu zarządzania nauczaniem robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Połączenie z kontrolerem robota, po pomyślnym połączeniu zwraca obiekt robota
    robot = Robot.RPC('192.168.58.2')
    name = "P1"
    rtn, data = robot.GetRobotTeachingPoint(name)
    print(f"{rtn} name is: {name}")
    for i in range(20):
        print(f"data is: {data[i]}")
    rtn,que_len = robot.GetMotionQueueLength()
    print(f"GetMotionQueueLength rtn is: {rtn}, queue length is: {que_len}")
    retval,dh = robot.GetDHCompensation()
    print(f"retval is: {retval}")
    print(f"dh is: {dh[0]} {dh[1]} {dh[2]} {dh[3]} {dh[4]} {dh[5]}")
    error,sn = robot.GetRobotSN()
    print(f"robot SN is {sn[0]}")
    robot.CloseRPC()

Pobieranie Układu Współrzędnych Narzędzia według ID
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: python SDK-V3.9.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetToolCoordWithID(id)``"
    "Opis", "Pobiera układ współrzędnych narzędzia według ID"
    "Parametry Wymagane", "- ``id``: Numer układu współrzędnych narzędzia"
    "Parametry Domyślne", "Brak"
    "Wartość Zwracana", "
    - Kod błędu, 0-sukces; niezerowy-błąd
    - ``coord``: Wartości układu współrzędnych
    - ``type``: Typ narzędzia (opcjonalny) 0-narzędzie; 1-czujnik
    - ``install``: Pozycja instalacji (opcjonalna) 0-koniec robota; 1-na zewnątrz robota
    - ``toolID``: ID narzędzia
    - ``loadNo``: Numer obciążenia
    "

Pobieranie Układu Współrzędnych Przedmiotu według ID
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: python SDK-V3.9.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetWObjCoordWithID(id)``"
    "Opis", "Pobiera układ współrzędnych przedmiotu według ID"
    "Parametry Wymagane", "- ``id``: Numer układu współrzędnych przedmiotu"
    "Parametry Domyślne", "Brak"
    "Wartość Zwracana", "
    - Kod błędu, 0-sukces; niezerowy-błąd
    - ``coord``: Wartości układu współrzędnych
    - ``refFrame``: Referencyjny układ współrzędnych
    "

Pobieranie Zewnętrznego Układu Współrzędnych Narzędzia według ID
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: python SDK-V3.9.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetExToolCoordWithID(id)``"
    "Opis", "Pobiera zewnętrzny układ współrzędnych narzędzia według ID"
    "Parametry Wymagane", "- ``id``: Numer zewnętrznego układu współrzędnych narzędzia"
    "Parametry Domyślne", "Brak"
    "Wartość Zwracana", "
    - Kod błędu, 0-sukces; niezerowy-błąd
    - ``coord``: Wartości układu współrzędnych
    - ``tcoord``: Pozycja układu współrzędnych przedmiotu zamontowanego na końcówce robota (6 wartości: [x, y, z, rx, ry, rz])
    "

Pobieranie Układu Współrzędnych Osi Rozszerzonej według ID
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetExAxisCoordWithID(id)``"
    "Opis", "Pobiera układ współrzędnych osi rozszerzonej według ID"
    "Parametry Wymagane", "- ``id``: Numer układu współrzędnych osi rozszerzonej"
    "Parametry Domyślne", "Brak"
    "Wartość Zwracana", "
    - Kod błędu, 0-sukces; niezerowy-błąd
    - ``coord``: Wartości układu współrzędnych
    - ``axisCoordNum``: Numer osi rozszerzonej (opcjonalny) bit0-bit3 odpowiadają osiom rozszerzonym 1-4; np. wartość 3 odpowiada osiom rozszerzonym [1,2]
    - ``calibFlag``: Flaga kalibracji (opcjonalna) 0-niekalibrowany; 1-kalibrowany
    "

Pobieranie masy i środka ciężkości obciążenia według numeru
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetTargetPayloadWithID(id)``"
    "Opis", "Pobieranie masy i środka ciężkości obciążenia według numeru"
    "Parametry wymagane", "- ``id``: Numer układu osi rozszerzenia"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``weight``: Masa obciążenia
    - ``cog``: Środek ciężkości obciążenia"

Pobieranie bieżącego układu narzędzia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetCurToolCoord()``"
    "Opis", "Pobieranie bieżącego układu narzędzia"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``coord``: Wartość układu współrzędnych"

Pobieranie bieżącego układu przedmiotu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetCurWObjCoord()``"
    "Opis", "Pobieranie bieżącego układu przedmiotu"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``coord``: Wartość układu współrzędnych"

Pobieranie bieżącego zewnętrznego układu narzędzia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetCurExToolCoord()``"
    "Opis", "Pobieranie bieżącego zewnętrznego układu narzędzia"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``coord``: Wartość układu współrzędnych"

Pobieranie bieżącego układu osi rozszerzenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototyp", "``GetCurExAxisCoord()``"
    "Opis", "Pobieranie bieżącego układu osi rozszerzenia"
    "Parametry wymagane", "Brak"
    "Parametry domyślne", "Brak"
    "Wartość zwracana", "- Kod błędu sukces-0 błąd- errcode
    - ``coord``: Wartość układu współrzędnych"

Przykład kodu układów współrzędnych robota i obciążenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time

    def main():
        robot = Robot.RPC('192.168.58.2')
        time.sleep(0.5)  

        time.sleep(2)

        id = 1
        rtn, toolCoord, type_val, install, toolID, loadNo = robot.GetToolCoordWithID(id)
        print(f"GetToolCoordWithID {id}, {toolCoord[0]:.6f} {toolCoord[1]:.6f} {toolCoord[2]:.6f} {toolCoord[3]:.6f} {toolCoord[4]:.6f} {toolCoord[5]:.6f},  type = {type_val}, install = {install}, toolID = {toolID}, loadNo = {loadNo}")
        rtn, wobjCoord, refFrame = robot.GetWObjCoordWithID(id)
        print(f"GetWObjCoordWithID {id}, {wobjCoord[0]:.6f} {wobjCoord[1]:.6f} {wobjCoord[2]:.6f} {wobjCoord[3]:.6f} {wobjCoord[4]:.6f} {wobjCoord[5]:.6f}, refFrame = {refFrame}")
        rtn, extoolCoord, exworkpieceCoord = robot.GetExToolCoordWithID(21)
        print(f"GetExToolCoordWithID {id}, {extoolCoord[0]:.6f} {extoolCoord[1]:.6f} {extoolCoord[2]:.6f} {extoolCoord[3]:.6f} {extoolCoord[4]:.6f} {extoolCoord[5]:.6f}, {exworkpieceCoord[0]:.6f} {exworkpieceCoord[1]:.6f} {exworkpieceCoord[2]:.6f} {exworkpieceCoord[3]:.6f} {exworkpieceCoord[4]:.6f} {exworkpieceCoord[5]:.6f}")
        rtn, exAxisCoord, axisCoordNum, calibFlag = robot.GetExAxisCoordWithID(id)
        print(f"GetExAxisCoordWithID {id}, {exAxisCoord[0]:.6f} {exAxisCoord[1]:.6f} {exAxisCoord[2]:.6f} {exAxisCoord[3]:.6f} {exAxisCoord[4]:.6f} {exAxisCoord[5]:.6f}, axisCoordNum = {axisCoordNum}, calibFlag = {calibFlag}")
        rtn, weight, cog = robot.GetTargetPayloadWithID(id)
        print(f"GetTargetPayloadWithID {id}, {weight:.6f} {cog[0]:.6f} {cog[1]:.6f} {cog[2]:.6f}")
        rtn, toolCoord = robot.GetCurToolCoord()
        print(f"GetCurToolCoord {toolCoord[0]:.6f} {toolCoord[1]:.6f} {toolCoord[2]:.6f} {toolCoord[3]:.6f} {toolCoord[4]:.6f} {toolCoord[5]:.6f}")
        rtn, wobjCoord = robot.GetCurWObjCoord()
        print(f"GetCurWObjCoord {wobjCoord[0]:.6f} {wobjCoord[1]:.6f} {wobjCoord[2]:.6f} {wobjCoord[3]:.6f} {wobjCoord[4]:.6f} {wobjCoord[5]:.6f}")
        rtn, extoolCoord = robot.GetCurExToolCoord()
        print(f"GetCurExToolCoord {extoolCoord[0]:.6f} {extoolCoord[1]:.6f} {extoolCoord[2]:.6f} {extoolCoord[3]:.6f} {extoolCoord[4]:.6f} {extoolCoord[5]:.6f}")

        rtn, exAxisCoord = robot.GetCurExAxisCoord()
        print(f"GetCurExAxisCoord {exAxisCoord[0]:.6f} {exAxisCoord[1]:.6f} {exAxisCoord[2]:.6f} {exAxisCoord[3]:.6f} {exAxisCoord[4]:.6f} {exAxisCoord[5]:.6f}")
        rtn, weightT = robot.GetTargetPayload(0)
        rtn, cogT = robot.GetTargetPayloadCog(0)
        print(f"GetTargetPayload {weightT:.6f} {cogT[0]:.6f} {cogT[1]:.6f} {cogT[2]:.6f}")
        coordSet = [0.0, 1.0, 2.0, 3.0, 4.0, 5.0]

        rtn = robot.SetToolCoord(1, coordSet, 0, 0, 1, 0)
        print(f"SetToolCoord rtn is {rtn}")

        rtn = robot.SetWObjCoord(1, coordSet, 0)
        print(f"SetWObjCoord rtn is {rtn}")

        rtn = robot.SetLoadWeight(1, 1.3)
        print(f"SetLoadWeight rtn is {rtn}")

        rtn = robot.SetLoadCoord(10.0, 20.0, 30.0,1)
        print(f"SetLoadCoord rtn is {rtn}")

        etcp = [0.0, 0.0, 100.0, 0.0, 0.0, 0.0]
        etool = [0.0, 0.0, 50.0, 0.0, 0.0, 0.0]
        rtn = robot.SetExToolCoord(21, etcp, etool)
        print(f"SetExToolCoord rtn is {rtn}")

        rtn = robot.ExtAxisActiveECoordSys(1, 1, coordSet, 1)
        print(f"ExtAxisActiveECoordSys rtn is {rtn}")

        robot.CloseRPC()

    if __name__ == "__main__":
        main()