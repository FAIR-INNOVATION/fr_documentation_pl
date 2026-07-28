Zapytanie o stan robota
=======================

.. toctree:: 
    :maxdepth: 5

Pobranie bieżącej pozycji stawów (stopnie)
+++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera bieżącą pozycję stawów (stopnie)
    * @param  [in] flag 0-blokujący, 1-nieblokujący
    * @param  [out] jPos Sześć pozycji stawów, jednostka deg
    * @return  Kod błędu
    */
    int GetActualJointPosDegree(byte flag, ref JointPos jPos); 

Pobranie bieżącej pozycji stawów (radiany)
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera bieżącą pozycję stawów (radiany)
    * @param  [in] flag 0-blokujący, 1-nieblokujący
    * @param  [out] jPos Sześć pozycji stawów, jednostka rad
    * @return  Kod błędu
    */   
    int GetActualJointPosRadian(byte flag, ref JointPos jPos);

Pobranie prędkości sprzężenia zwrotnego stawów
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Pobiera prędkość sprzężenia zwrotnego stawów - deg/s 
    * @param [in] flag 0-blokujący, 1-nieblokujący 
    * @param [out] speed Sześć prędkości stawów 
    * @return Kod błędu 
    */
    int GetActualJointSpeedsDegree(byte flag, ref double[] speed);

Pobranie przyspieszenia sprzężenia zwrotnego stawów
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Pobiera przyspieszenie sprzężenia zwrotnego stawów - deg/s^2 
    * @param [in] flag 0-blokujący, 1-nieblokujący 
    * @param [out] acc Sześć przyspieszeń stawów 
    * @return Kod błędu 
    */
    int GetActualJointAccDegree(byte flag, ref double[] acc); 

Pobranie prędkości instrukcji TCP - prędkość złożona
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Pobiera prędkość instrukcji TCP - prędkość złożona 
    * @param [in] flag 0-blokujący, 1-nieblokujący 
    * @param [out] tcp_speed Prędkość liniowa 
    * @param [out] ori_speed Prędkość orientacji 
    * @return Kod błędu 
    */
    int GetTargetTCPCompositeSpeed(byte flag, ref double tcp_speed, ref double ori_speed); 

Pobranie prędkości sprzężenia zwrotnego TCP - prędkość złożona
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:
    
    /** 
    * @brief Pobiera prędkość sprzężenia zwrotnego TCP - prędkość złożona
    * @param [in] flag 0-blokujący, 1-nieblokujący 
    * @param [out] tcp_speed Prędkość liniowa 
    * @param [out] ori_speed Prędkość orientacji 
    * @return Kod błędu 
    */
    int GetActualTCPCompositeSpeed(byte flag, ref double tcp_speed, ref double ori_speed);

Pobranie prędkości instrukcji TCP - prędkości składowe
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Pobiera prędkość instrukcji TCP - prędkości składowe
    * @param [in] flag 0-blokujący, 1-nieblokujący 
    * @param [out] speed Prędkości [x,y,z,rx,ry,rz] 
    * @return Kod błędu 
    */
    int GetTargetTCPSpeed(byte flag, ref double[] speed);

Pobranie prędkości sprzężenia zwrotnego TCP - prędkości składowe
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Pobiera prędkość sprzężenia zwrotnego TCP - prędkości składowe
    * @param [in] flag 0-blokujący, 1-nieblokujący 
    * @param [out] speed Prędkości [x,y,z,rx,ry,rz] 
    * @return Kod błędu 
    */
    int GetActualTCPSpeed(byte flag, ref double[] speed);

Pobranie bieżącej pozycji i orientacji narzędzia
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera bieżącą pozycję i orientację narzędzia
    * @param  [in] flag  0-blokujący, 1-nieblokujący
    * @param  [out] desc_pos  Pozycja i orientacja narzędzia
    * @return  Kod błędu
    */
    int GetActualTCPPose(byte flag, ref DescPose desc_pos); 

Pobranie bieżącego numeru układu współrzędnych narzędzia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera bieżący numer układu współrzędnych narzędzia
    * @param  [in] flag  0-blokujący, 1-nieblokujący
    * @param  [out] id  Numer układu współrzędnych narzędzia
    * @return  Kod błędu
    */
    int GetActualTCPNum(byte flag, ref int id);  

Pobranie bieżącego numeru układu współrzędnych przedmiotu
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera bieżący numer układu współrzędnych przedmiotu
    * @param  [in] flag  0-blokujący, 1-nieblokujący
    * @param  [out] id  Numer układu współrzędnych przedmiotu
    * @return  Kod błędu
    */
    int GetActualWObjNum(byte flag, ref int id);

Pobranie bieżącej pozycji i orientacji kołnierza końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera bieżącą pozycję i orientację kołnierza końcowego
    * @param  [in] flag  0-blokujący, 1-nieblokujący
    * @param  [out] desc_pos  Pozycja i orientacja kołnierza
    * @return  Kod błędu
    */
    int GetActualToolFlangePose(byte flag, ref DescPose desc_pos);   

Pobranie bieżącego momentu obrotowego stawów
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Pobiera bieżący moment obrotowy stawów
    * @param  [in] flag 0-blokujący, 1-nieblokujący
    * @param  [out] torques Moment obrotowy stawów
    * @return  Kod błędu
    */
    int GetJointTorques(byte flag, float[] torques); 

Pobranie czasu systemowego
++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera czas systemowy
    * @param  [out] t_ms Jednostka ms, można konwertować na czas UTC, w stanie awarii robota GetClock zwraca 0 i kod błędu
    * @return  Kod błędu
    */
    public int GetSystemClock(ref double t_ms)

Sprawdzenie, czy ruch robota został zakończony
++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Sprawdza, czy ruch robota został zakończony
    * @param  [out]  state  0-niezakończony, 1-zakończony
    * @return  Kod błędu
    */   
    int GetRobotMotionDone(ref byte state);

Sprawdzenie długości bufora kolejki ruchu robota
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Sprawdza długość bufora kolejki ruchu robota 
    * @param [out] len   Długość bufora
    * @return Kod błędu 
    */
    int GetMotionQueueLength(ref int len);

Pobranie stanu awaryjnego zatrzymania robota
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Pobiera stan awaryjnego zatrzymania robota
    * @param [out] state Stan awaryjnego zatrzymania, 0-brak, 1-awaryjne zatrzymanie
    * @return Kod błędu  
    */
    int GetRobotEmergencyStopState(ref byte state);

Pobranie stanu komunikacji SDK z robotem
++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Pobiera stan komunikacji SDK z robotem
    * @param [out]  state Stan komunikacji, 0-komunikacja normalna, 1-komunikacja nieprawidłowa
    */
    int GetSDKComState(ref int state);

Pobranie sygnału bezpiecznego zatrzymania
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Pobiera sygnał bezpiecznego zatrzymania
    * @param [out]  si0_state Sygnał bezpiecznego zatrzymania SI0, 0-nieaktywny, 1-aktywny
    * @param [out]  si1_state Sygnał bezpiecznego zatrzymania SI1, 0-nieaktywny, 1-aktywny
    */
    int GetSafetyStopState(ref byte si0_state, ref byte si1_state);

Pobranie temperatury napędu stawu robota (°C)
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Pobiera temperaturę napędu stawu robota (°C)
    * @return Kod błędu
    */
    int GetJointDriverTemperature(double[] temperature);

Pobranie momentu obrotowego napędu stawu robota (Nm)
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Pobiera moment obrotowy napędu stawu robota (Nm)
    * @return Kod błędu
    */
    int GetJointDriverTorque(double torque[]);

Pobranie najnowszej ramki danych stanu robota w czasie rzeczywistym (zmiana mechanizmu wewnętrznego)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Pobiera najnowszą ramkę danych stanu robota w czasie rzeczywistym (wewnętrzny wątek ciągle aktualizuje, ten interfejs bezpośrednio zwraca dane z bufora)
    * @param [out] pkg Parametr referencyjny do odbioru danych stanu robota (struktura ROBOT_STATE_PKG)
    * @return Sukces zwraca 0; błąd zwraca ujemny kod błędu (np. błąd komunikacji sieciowej)
    */
    public int GetRobotRealTimeState(ref ROBOT_STATE_PKG pkg)

Przykład kodu zapytania o stan robota
+++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button29_Click(object sender, EventArgs e)
    {
        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
        double yangle = 0, zangle = 0;
        robot.GetRobotInstallAngle(ref yangle, ref zangle);
        Console.WriteLine($"yangle:{yangle},zangle:{zangle}");

        JointPos j_deg = new JointPos(0,0,0,0,0,0);
        robot.GetActualJointPosDegree(0, ref j_deg);
        Console.WriteLine($"joint pos deg:{j_deg.jPos[0]},{j_deg.jPos[1]},{j_deg.jPos[2]},{j_deg.jPos[3]},{j_deg.jPos[4]},{j_deg.jPos[5]}");

        double[] jointSpeed = new double[6];
        robot.GetActualJointSpeedsDegree(0, ref jointSpeed);
        Console.WriteLine($"joint speeds deg:{jointSpeed[0]},{jointSpeed[1]},{jointSpeed[2]},{jointSpeed[3]},{jointSpeed[4]},{jointSpeed[5]}");

        double[] jointAcc = new double[6];
        robot.GetActualJointAccDegree(0, ref jointAcc);
        Console.WriteLine($"joint acc deg:{jointAcc[0]},{jointAcc[1]},{jointAcc[2]},{jointAcc[3]},{jointAcc[4]},{jointAcc[5]}");

        double tcp_speed = 0, ori_speed = 0;
        robot.GetTargetTCPCompositeSpeed(0, ref tcp_speed, ref ori_speed);
        Console.WriteLine($"GetTargetTCPCompositeSpeed tcp {tcp_speed}; ori {ori_speed}");

        robot.GetActualTCPCompositeSpeed(0, ref tcp_speed, ref ori_speed);
        Console.WriteLine($"GetActualTCPCompositeSpeed tcp {tcp_speed}; ori {ori_speed}");

        double[] targetSpeed = new double[6];
        robot.GetTargetTCPSpeed(0,ref targetSpeed);
        Console.WriteLine($"GetTargetTCPSpeed {targetSpeed[0]},{targetSpeed[1]},{targetSpeed[2]},{targetSpeed[3]},{targetSpeed[4]},{targetSpeed[5]}");

        double[] actualSpeed = new double[6];
        robot.GetActualTCPSpeed(0, ref actualSpeed);
        Console.WriteLine($"GetTargetTCPSpeed {actualSpeed[0]},{actualSpeed[1]},{actualSpeed[2]},{actualSpeed[3]},{actualSpeed[4]},{actualSpeed[5]}");

        DescPose tcp = new DescPose(0, 0, 0, 0, 0, 0);
        robot.GetActualTCPPose(0, ref tcp);
        Console.WriteLine($"tcp pose:{tcp.tran.x},{tcp.tran.y},{tcp.tran.z},{tcp.rpy.rx},{tcp.rpy.ry},{tcp.rpy.rz}");

        DescPose flange = new DescPose(0, 0, 0, 0, 0, 0);
        robot.GetActualToolFlangePose(0, ref flange);
        Console.WriteLine($"flange pose:{flange.tran.x},{flange.tran.y},{flange.tran.z},{flange.rpy.rx},{flange.rpy.ry},{flange.rpy.rz}");

        int id = 0;
        robot.GetActualTCPNum(0, ref id);
        Console.WriteLine($"tcp num:{id}");

        robot.GetActualWObjNum(0, ref id);
        Console.WriteLine($"wobj num:{id}");

        double[] jtorque = new double[6];
        robot.GetJointTorques(0, jtorque);
        Console.WriteLine($"torques:{jtorque[0]},{jtorque[1]},{jtorque[2]},{jtorque[3]},{jtorque[4]},{jtorque[5]}");

        double t_ms = 0;
        robot.GetSystemClock(ref t_ms);
        Console.WriteLine($"system clock:{t_ms}");

        int config = 0;
        robot.GetRobotCurJointsConfig(ref config);
        Console.WriteLine($"joint config:{config}");

        byte motionDone = 0;
        robot.GetRobotMotionDone(ref motionDone);
        Console.WriteLine($"GetRobotMotionDone :{motionDone}");

        int len = 0;
        robot.GetMotionQueueLength(ref len);
        Console.WriteLine($"GetMotionQueueLength :{len}");

        byte emergState = 0;
        robot.GetRobotEmergencyStopState(ref emergState);
        Console.WriteLine($"GetRobotEmergencyStopState :{emergState}");

        int comstate = 0;
        robot.GetSDKComState(ref comstate);
        Console.WriteLine($"GetSDKComState :{comstate}");

        byte si0_state = 0, si1_state = 0;
        robot.GetSafetyStopState(ref si0_state, ref si1_state);
        Console.WriteLine($"GetSafetyStopState :{si0_state} {si1_state}");

        double[] temp = new double[6];
        robot.GetJointDriverTemperature(temp);
        Console.WriteLine($"Temperature:{temp[0]},{temp[1]},{temp[2]},{temp[3]},{temp[4]},{temp[5]}");

        double[] torque = new double[6];
        robot.GetJointDriverTorque(torque);
        Console.WriteLine($"torque:{torque[0]},{torque[1]},{torque[2]},{torque[3]},{torque[4]},{torque[5]}");

        robot.GetRobotRealTimeState(ref pkg);
    }

Rozwiązanie odwrotnej kinematyki
++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Rozwiązanie odwrotnej kinematyki
    * @param  [in] type 0-pozycja bezwzględna (układ podstawowy), 1-pozycja przyrostowa (układ podstawowy), 2-pozycja przyrostowa (układ narzędzia)
    * @param  [in] desc_pos Pozycja i orientacja kartezjańska
    * @param  [in] config Konfiguracja przestrzeni stawów, [-1]-obliczenie z odniesieniem do bieżącej pozycji stawów, [0~7]-rozwiązanie zgodnie z określoną konfiguracją przestrzeni stawów
    * @param  [out] joint_pos Pozycja stawów
    * @return  Kod błędu
    */ 
    int GetInverseKin(int type, DescPose desc_pos, int config, ref JointPos joint_pos);

Rozwiązanie odwrotnej kinematyki (z pozycją odniesienia)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Rozwiązanie odwrotnej kinematyki, sprawdzenie, czy istnieje rozwiązanie w odniesieniu do określonej pozycji stawów
    * @param  [in] type 0-pozycja bezwzględna (układ podstawowy), 1-pozycja przyrostowa (układ podstawowy), 2-pozycja przyrostowa (układ narzędzia)
    * @param  [in] desc_pos Pozycja i orientacja kartezjańska
    * @param  [in] joint_pos_ref Referencyjna pozycja stawów
    * @param  [out] result 0-brak rozwiązania, 1-jest rozwiązanie
    * @return  Kod błędu
    */   
    int GetInverseKinRef(int posMode, DescPose desc_pos, JointPos joint_pos_ref, ref JointPos joint_pos); 

Rozwiązanie odwrotnej kinematyki z uwzględnieniem pozycji osi rozszerzonej w przestrzeni kartezjańskiej
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Rozwiązanie odwrotnej kinematyki z uwzględnieniem pozycji osi rozszerzonej w przestrzeni kartezjańskiej
    * @param [in] type 0-pozycja bezwzględna (układ podstawowy), 1-pozycja przyrostowa (układ podstawowy), 2-pozycja przyrostowa (układ narzędzia)
    * @param [in] desc_pos Pozycja i orientacja kartezjańska
    * @param [in] exaxis Pozycja osi rozszerzonej
    * @param [in] tool Numer narzędzia
    * @param [in] workPiece Numer przedmiotu
    * @param [out] joint_pos Pozycja stawów
    * @return Kod błędu
    */
    public int GetInverseKinExaxis(int type, DescPose desc_pos, ExaxisPos exaxis, int tool, int workPiece, ref JointPos joint_pos);

Przykład kodu rozwiązania odwrotnej kinematyki z uwzględnieniem pozycji osi rozszerzonej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public void TestInverseKinExaxis()
    {
        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
        

        DescPose desc = new DescPose(99.957f, -0.002f, 29.994f, -176.569f, -6.757f, -167.462f);
        ExaxisPos exaxis = new ExaxisPos(100.0f, 0.0f, 0.0f, 0.0f);
        JointPos jointPos = new JointPos(0,0,0,0,0,0);
        DescPose offsetPos = new DescPose(0.0f, 0.0f, 0.0f, 0.0f, 0.0f, 0.0f);
        int rtn;
        robot.GetRobotRealTimeState(ref pkg);
        int toolnum = pkg.tool;
        int workPcsNum = pkg.user;

        robot.GetInverseKinExaxis(0, desc, exaxis, toolnum, workPcsNum, ref jointPos);
        Console.WriteLine($"GetInverseKinExaxis joint is {jointPos.jPos[0]}, {jointPos.jPos[1]}, {jointPos.jPos[2]}, {jointPos.jPos[3]}, {jointPos.jPos[4]}, {jointPos.jPos[5]}");

        robot.ExtAxisMove(exaxis, 100, -1);

        int blendMode = 0;
        int velAccMode = 0;
        float oacc = 100.0f;
        byte flag = 0;
        robot.MoveJ(jointPos, desc, toolnum, workPcsNum, (float)100.0, (float)100.0, (float)100.0, exaxis, -1, 0, offsetPos);
    }

Sprawdzenie, czy istnieje rozwiązanie odwrotnej kinematyki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Rozwiązanie odwrotnej kinematyki, sprawdzenie, czy istnieje rozwiązanie dla określonej referencyjnej pozycji stawów
    * @param [in] posMode 0-pozycja bezwzględna, 1-pozycja względna - układ podstawowy, 2-pozycja względna - układ narzędzia 
    * @param [in] desc_pos Pozycja i orientacja kartezjańska 
    * @param [in] joint_pos_ref Referencyjna pozycja stawów 
    * @param [out] hasResult 0-brak rozwiązania, 1-jest rozwiązanie 
    * @return Kod błędu 
    */ 
    int GetInverseKinHasSolution(int posMode, DescPose desc_pos, JointPos joint_pos_ref, ref bool hasResult);  

Rozwiązanie prostej kinematyki
++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Rozwiązanie prostej kinematyki
    * @param  [in] joint_pos Pozycja stawów
    * @param  [out] desc_pos Pozycja i orientacja kartezjańska
    * @return  Kod błędu
    */
    int GetForwardKin(JointPos joint_pos, ref DescPose desc_pos); 

Przykład kodu obliczeń prostej i odwrotnej kinematyki robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button30_Click(object sender, EventArgs e)
    {
        JointPos j1 = new JointPos(-11.904f, -99.669f, 117.473f, -108.616f, -91.726f, 74.256f);
        DescPose desc_pos1 = new DescPose(-419.524f, -13.000f, 351.569f, -178.118f, 0.314f, 3.833f);

        JointPos inverseRtn = new JointPos(0, 0, 0, 0, 0, 0);

        robot.GetInverseKin(0, desc_pos1, -1, ref inverseRtn);
        Console.WriteLine($"dcs1 GetInverseKin rtn is {inverseRtn.jPos[0]} {inverseRtn.jPos[1]} {inverseRtn.jPos[2]} {inverseRtn.jPos[3]} {inverseRtn.jPos[4]} {inverseRtn.jPos[5]}");
        robot.GetInverseKinRef(0,  desc_pos1, j1, ref inverseRtn);
        Console.WriteLine($"dcs1 GetInverseKinRef rtn is {inverseRtn.jPos[0]} {inverseRtn.jPos[1]} {inverseRtn.jPos[2]} {inverseRtn.jPos[3]} {inverseRtn.jPos[4]} {inverseRtn.jPos[5]}");

        bool hasResut = false;
        robot.GetInverseKinHasSolution(0,  desc_pos1,  j1, ref hasResut);
        Console.WriteLine($"dcs1 GetInverseKinRef result {hasResut}");

        DescPose forwordResult = new DescPose(0, 0, 0, 0, 0, 0);
        robot.GetForwardKin(j1, ref forwordResult);
        Console.WriteLine($"jpos1 forwordResult rtn is {forwordResult.tran.x} {forwordResult.tran.y} {forwordResult.tran.z} {forwordResult.rpy.rx} {forwordResult.rpy.ry} {forwordResult.rpy.rz}");
    }

Sprawdzenie danych punktu zarządzania nauczaniem robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Sprawdza dane punktu zarządzania nauczaniem robota 
    * @param [in] name    Nazwa punktu
    * @param [out] data   Dane punktu double[20]{x,y,z,rx,ry,rz,j1,j2,j3,j4,j5,j6,tool, wobj,speed,acc,e1,e2,e3,e4}
    * @return Kod błędu 
    */ 
    int GetRobotTeachingPoint(string name, ref double[] data); 

Pobranie wartości kompensacji parametrów DH robota
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Pobiera wartości kompensacji parametrów DH robota 
    * @param [out] dhCompensation Wartości kompensacji parametrów DH robota (mm) [cmpstD1, cmpstA2, cmpstA3, cmpstD4, cmpstD5, cmpstD6]
    * @return Kod błędu 
    */
    int GetDHCompensation(ref double[] dhCompensation);


Pobranie kodu SN skrzynki sterowniczej
++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Pobiera kod SN skrzynki sterowniczej
    * @param [out] SNCode Kod SN skrzynki sterowniczej
    * @return Kod błędu
    */
    int GetRobotSN(ref string SNCode);

Przykład kodu sprawdzania danych punktu zarządzania nauczaniem robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button31_Click(object sender, EventArgs e)
    {
        string name = "A0";
        double[] data = new double[20];
        int rtn = robot.GetRobotTeachingPoint(name, ref data);
        Console.WriteLine(" {0} name is: {1} \n", rtn, name);
        for (int i = 0; i < 20; i++)
        {
            Console.WriteLine("data is: {0} \n", data[i]);
        }

        int que_len = 0;
        rtn = robot.GetMotionQueueLength(ref que_len);
        Console.WriteLine("GetMotionQueueLength rtn is: {0}, queue length is: {1} \n", rtn, que_len);

        double[] dh = { 0, 0, 0, 0, 0, 0 };
        int retval = 0;
        retval = robot.GetDHCompensation(ref dh);
        Console.WriteLine($"retval is  {retval}");
        Console.WriteLine($"dh is {dh[0]}, {dh[1]}, {dh[2]}, {dh[3]}, {dh[4]}, {dh[5]}");
        string SN = "";
        robot.GetRobotSN(ref SN);
        Console.WriteLine($"robot SN is  {SN}");
    }

Pobieranie Układu Współrzędnych Narzędzia według ID
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C#SDK-V3.9.8

.. code-block:: c#
    :linenos:

    /**
    * @brief Pobiera układ współrzędnych narzędzia według ID
    * @param [in] id Numer układu współrzędnych narzędzia
    * @param [out] coord Wartości układu współrzędnych
    * @param [out] type Typ narzędzia: 0-narzędzie; 1-czujnik
    * @param [out] install Pozycja instalacji: 0-koniec robota; 1-na zewnątrz robota
    * @param [out] toolID ID narzędzia
    * @param [out] loadNo Numer obciążenia
    * @return Kod błędu
    */
    int GetToolCoordWithID(int id, ref DescPose coord, ref int type, ref int install, ref int toolID, ref int loadNo)

Pobieranie Układu Współrzędnych Przedmiotu według ID
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C#SDK-V3.9.8

.. code-block:: c#
    :linenos:

    /**
    * @brief Pobiera układ współrzędnych przedmiotu według ID
    * @param [in] id Numer układu współrzędnych przedmiotu
    * @param [out] coord Wartości układu współrzędnych
    * @param [out] refFrame Referencyjny układ współrzędnych
    * @return Kod błędu
    */
    public int GetWObjCoordWithID(int id, ref DescPose coord, ref int refFrame)

Pobieranie Zewnętrznego Układu Współrzędnych Narzędzia według ID
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C#SDK-V3.9.8

.. code-block:: c#
    :linenos:

    /**
    * @brief Pobiera zewnętrzny układ współrzędnych narzędzia według ID
    * @param [in] id Numer zewnętrznego układu współrzędnych narzędzia, 20-39 odpowiadają zewnętrznym układom współrzędnych narzędzi 0-19
    * @param [out] coord Pozycja TCP stałego narzędzia zewnętrznego na robocie
    * @param [out] tcoord Pozycja układu współrzędnych przedmiotu zamontowanego na końcówce robota
    * @return Kod błędu
    */
    public int GetExToolCoordWithID(int id, ref DescPose coord, ref DescPose tcoord)

Pobieranie Układu Współrzędnych Osi Rozszerzonej według ID
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C#SDK-V3.9.8

.. code-block:: c#
    :linenos:

    /**
    * @brief Pobiera układ współrzędnych osi rozszerzonej według ID
    * @param [in] id Numer zewnętrznego układu współrzędnych narzędzia
    * @param [out] coord Wartości układu współrzędnych
    * @param [out] axisCoordNum Numer osi rozszerzonej; bit0-bit3 odpowiadają osiom rozszerzonym 1-4; np. wartość axisCoordNum 3 odpowiada osiom rozszerzonym [1, 2]
    * @param [out] calibFlag Flaga kalibracji; 0-niekalibrowany; 1-kalibrowany
    * @return Kod błędu
    */
    public int GetExAxisCoordWithID(int id, ref DescPose coord, ref int axisCoordNum, ref int calibFlag)

Pobranie bieżącego układu współrzędnych narzędzia
+++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
     * @brief Pobiera bieżący układ współrzędnych narzędzia
     * @param [out] coord Wartości układu współrzędnych
     * @return Kod błędu
     */
    public int GetCurToolCoord(ref DescPose coord)

Pobranie bieżącego układu współrzędnych przedmiotu
++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
     * @brief Pobiera bieżący układ współrzędnych przedmiotu
     * @param [out] coord Wartości układu współrzędnych
     * @return Kod błędu
     */
    public int GetCurWObjCoord(ref DescPose coord)

Pobranie bieżącego zewnętrznego układu współrzędnych narzędzia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
     * @brief Pobiera bieżący zewnętrzny układ współrzędnych narzędzia
     * @param  [out] coord Wartości układu współrzędnych
     * @return Kod błędu
     */
    public int GetCurExToolCoord(ref DescPose coord)

Pobranie bieżącego układu współrzędnych osi rozszerzonej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
     * @brief Pobiera bieżący układ współrzędnych osi rozszerzonej
     * @param [out] coord Wartości układu współrzędnych
     * @return Kod błędu
     */
    public int GetCurExAxisCoord(ref DescPose coord)

Przykład Kodu Pobierania Współrzędnych według ID
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C#SDK-V3.9.8

.. code-block:: c#
    :linenos:

    public int TestCoord()
    {
        int rtn;
        int id = 1;

        // GetToolCoordWithID
        DescPose toolCoord = new DescPose(0, 0, 0, 0, 0, 0);
        int type = 0, install = 0, toolID = 0, loadNo = 0;
        rtn = robot.GetToolCoordWithID(id, ref toolCoord, ref type, ref install, ref toolID, ref loadNo);
        Console.WriteLine("GetToolCoordWithID {0}, {1:F3} {2:F3} {3:F3} {4:F3} {5:F3} {6:F3}, type={7}, install={8}, toolID={9}, loadNo={10}",
            id, toolCoord.tran.x, toolCoord.tran.y, toolCoord.tran.z,
            toolCoord.rpy.rx, toolCoord.rpy.ry, toolCoord.rpy.rz, type, install, toolID, loadNo);

        // GetWObjCoordWithID
        DescPose wobjCoord = new DescPose(0, 0, 0, 0, 0, 0);
        int refFrame = 0;
        rtn = robot.GetWObjCoordWithID(id, ref wobjCoord, ref refFrame);
        Console.WriteLine("GetWObjCoordWithID {0}, {1:F3} {2:F3} {3:F3} {4:F3} {5:F3} {6:F3}, refFrame={7}",
            id, wobjCoord.tran.x, wobjCoord.tran.y, wobjCoord.tran.z,
            wobjCoord.rpy.rx, wobjCoord.rpy.ry, wobjCoord.rpy.rz, refFrame);

        // GetExToolCoordWithID
        DescPose extoolCoord = new DescPose(0, 0, 0, 0, 0, 0);
        DescPose exworkpieceCoord = new DescPose(0, 0, 0, 0, 0, 0);
        rtn = robot.GetExToolCoordWithID(21, ref extoolCoord, ref exworkpieceCoord);
        Console.WriteLine("GetExToolCoordWithID 21, {0:F3} {1:F3} {2:F3} {3:F3} {4:F3} {5:F3}",
            extoolCoord.tran.x, extoolCoord.tran.y, extoolCoord.tran.z,
            extoolCoord.rpy.rx, extoolCoord.rpy.ry, extoolCoord.rpy.rz);
        Console.WriteLine("  tcoord: {0:F3} {1:F3} {2:F3} {3:F3} {4:F3} {5:F3}",
            exworkpieceCoord.tran.x, exworkpieceCoord.tran.y, exworkpieceCoord.tran.z,
            exworkpieceCoord.rpy.rx, exworkpieceCoord.rpy.ry, exworkpieceCoord.rpy.rz);

        // GetExAxisCoordWithID
        DescPose exAxisCoord = new DescPose(0, 0, 0, 0, 0, 0);
        int axisCoordNum = 0, calibFlag = 0;
        rtn = robot.GetExAxisCoordWithID(id, ref exAxisCoord, ref axisCoordNum, ref calibFlag);
        Console.WriteLine("GetExAxisCoordWithID {0}, {1:F3} {2:F3} {3:F3} {4:F3} {5:F3} {6:F3}, axisCoordNum={7}, calibFlag={8}",
            id, exAxisCoord.tran.x, exAxisCoord.tran.y, exAxisCoord.tran.z,
            exAxisCoord.rpy.rx, exAxisCoord.rpy.ry, exAxisCoord.rpy.rz, axisCoordNum, calibFlag);

        // GetTargetPayloadWithID
        double weight = 0.0;
        DescTran cog = new DescTran(0, 0, 0);
        rtn = robot.GetTargetPayloadWithID(id, ref weight, ref cog);
        Console.WriteLine("GetTargetPayloadWithID {0}, {1:F3} {2:F3} {3:F3} {4:F3}",
            id, weight, cog.x, cog.y, cog.z);

        // GetCurToolCoord
        rtn = robot.GetCurToolCoord(ref toolCoord);
        Console.WriteLine("GetCurToolCoord {0:F3} {1:F3} {2:F3} {3:F3} {4:F3} {5:F3}",
            toolCoord.tran.x, toolCoord.tran.y, toolCoord.tran.z,
            toolCoord.rpy.rx, toolCoord.rpy.ry, toolCoord.rpy.rz);

        // GetCurWObjCoord
        rtn = robot.GetCurWObjCoord(ref wobjCoord);
        Console.WriteLine("GetCurWObjCoord {0:F3} {1:F3} {2:F3} {3:F3} {4:F3} {5:F3}",
            wobjCoord.tran.x, wobjCoord.tran.y, wobjCoord.tran.z,
            wobjCoord.rpy.rx, wobjCoord.rpy.ry, wobjCoord.rpy.rz);

        // GetCurExToolCoord
        rtn = robot.GetCurExToolCoord(ref extoolCoord);
        Console.WriteLine("GetCurExToolCoord {0:F3} {1:F3} {2:F3} {3:F3} {4:F3} {5:F3}",
            extoolCoord.tran.x, extoolCoord.tran.y, extoolCoord.tran.z,
            extoolCoord.rpy.rx, extoolCoord.rpy.ry, extoolCoord.rpy.rz);

        // GetCurExAxisCoord
        rtn = robot.GetCurExAxisCoord(ref exAxisCoord);
        Console.WriteLine("GetCurExAxisCoord {0:F3} {1:F3} {2:F3} {3:F3} {4:F3} {5:F3}",
            exAxisCoord.tran.x, exAxisCoord.tran.y, exAxisCoord.tran.z,
            exAxisCoord.rpy.rx, exAxisCoord.rpy.ry, exAxisCoord.rpy.rz);

        // GetTargetPayload / GetTargetPayloadCog
        double weightT = 0.0;
        DescTran cogT = new DescTran(0, 0, 0);
        robot.GetTargetPayload(0, ref weightT);
        robot.GetTargetPayloadCog(0, ref cogT);
        Console.WriteLine("GetTargetPayload {0:F3} {1:F3} {2:F3} {3:F3}",
            weightT, cogT.x, cogT.y, cogT.z);

        // SetToolCoord
        DescPose coordSet = new DescPose(0, 1, 2, 3, 4, 5);
        rtn = robot.SetToolCoord(1, coordSet, 0, 0, 1, 0);
        Console.WriteLine("SetToolCoord(1) rtn={0}", rtn);

        // SetWObjCoord
        rtn = robot.SetWObjCoord(1, coordSet, 0);
        Console.WriteLine("SetWObjCoord(1) rtn={0}", rtn);

        // SetLoadWeight + SetLoadCoord
        rtn = robot.SetLoadWeight(1, 1.3f);
        Console.WriteLine("SetLoadWeight(1,1.3) rtn={0}", rtn);

        DescTran loadCog = new DescTran(10, 20, 30);
        rtn = robot.SetLoadCoord(1, loadCog);
        Console.WriteLine("SetLoadCoord(1,10,20,30) rtn={0}", rtn);

        // SetExToolCoord
        DescPose etcp = new DescPose(0, 0, 100, 0, 0, 0);
        DescPose etool = new DescPose(0, 0, 50, 0, 0, 0);
        rtn = robot.SetExToolCoord(21, etcp, etool);
        Console.WriteLine("SetExToolCoord(21) rtn={0}", rtn);
        // SetExToolList
        rtn = robot.SetExToolList(21, etcp, etool);
        Console.WriteLine("SetExToolList(21) rtn={0}", rtn);

        // ExtAxisActiveECoordSys
        rtn = robot.ExtAxisActiveECoordSys(1, 1, coordSet, 1);
        Console.WriteLine("ExtAxisActiveECoordSys(1,1,..,1) rtn={0}", rtn);

        return 0;
    }