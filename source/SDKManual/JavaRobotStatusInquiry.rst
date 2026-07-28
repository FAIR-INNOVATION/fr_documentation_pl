Zapytanie o stan robota
=======================

.. toctree:: 
    :maxdepth: 5

Pobieranie bieżącej pozycji przegubów (kąt)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Pobieranie bieżącej pozycji przegubów (kąt)
    * @param  [out] jPos Pobrane pozycje sześciu przegubów, jednostka deg
    * @return  Kod błędu
    */
    int GetActualJointPosDegree(JointPos jPos); 

Pobieranie prędkości sprzężenia zwrotnego przegubów - deg/s
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Pobieranie prędkości sprzężenia zwrotnego przegubów - deg/s 
    * @param [out] speed Prędkości sześciu przegubów
    * @return Kod błędu 
    */
    int GetActualJointSpeedsDegree(Object[] speed);

Pobieranie przyspieszenia sprzężenia zwrotnego przegubów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Pobieranie przyspieszenia sprzężenia zwrotnego przegubów - deg/s^2
    * @param  [in] flag 0-blokujący, 1-nieblokujący
    * @param  [out] acc Przyspieszenia sześciu przegubów
    * @return  Kod błędu
    */
    public int GetActualJointAccDegree(int flag, Object[] acc)

Pobieranie prędkości wypadkowej zadanej TCP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Pobieranie prędkości zadanej TCP
    * @param  [in] flag 0-blokujący, 1-nieblokujący
    * @param  [out] tcp_speed Prędkość liniowa
    * @param  [out] ori_speed Prędkość pozy
    * @return  Kod błędu
    */
    public int GetTargetTCPCompositeSpeed(int flag, double tcp_speed, double ori_speed)

Pobieranie prędkości wypadkowej sprzężenia zwrotnego TCP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Pobieranie prędkości wypadkowej sprzężenia zwrotnego TCP
    * @param  [in] flag 0-blokujący, 1-nieblokujący
    * @param  [out] tcp_speed Prędkość liniowa
    * @param  [out] ori_speed Prędkość pozy
    * @return  Kod błędu
    */
    public int GetActualTCPCompositeSpeed(int flag, double tcp_speed, double ori_speed)

Pobieranie prędkości zadanej TCP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Pobieranie prędkości zadanej TCP
    * @param  [in] flag 0-blokujący, 1-nieblokujący
    * @param  [out] speed Prędkości [x,y,z,rx,ry,rz]
    * @return  Kod błędu
    */
    public int GetTargetTCPSpeed(int flag, Object[] speed)

Pobieranie prędkości sprzężenia zwrotnego TCP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Pobieranie prędkości sprzężenia zwrotnego TCP
    * @param  [in] flag 0-blokujący, 1-nieblokujący
    * @param  [out] speed Prędkości [x,y,z,rx,ry,rz]
    * @return  Kod błędu
    */
    public int GetActualTCPSpeed(int flag, Object[] speed)

Pobieranie bieżącej pozy narzędzia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Pobieranie bieżącej pozy narzędzia
    * @param  [out] desc_pos  Pozycja narzędzia
    * @return  Kod błędu
    */
    int GetActualTCPPose(DescPose desc_pos); 

Pobieranie bieżącego numeru układu narzędzia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Pobieranie bieżącego numeru układu narzędzia
    * @param  [in] flag  0-blokujący, 1-nieblokujący
    * @param  [out] id  Numer układu narzędzia
    * @return  Kod błędu
    */
    int GetActualTCPNum(int flag, int[] id)

Pobieranie bieżącego numeru układu przedmiotu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Pobieranie bieżącego numeru układu przedmiotu
    * @param  [in] flag  0-blokujący, 1-nieblokujący
    * @param  [out] id  Numer układu przedmiotu
    * @return  Kod błędu
    */
    public int GetActualWObjNum(int flag, int[] id)

Pobieranie bieżącej pozy kołnierza końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Pobieranie bieżącej pozy kołnierza końcowego
    * @param  [in] flag  0-blokujący, 1-nieblokujący
    * @param  [out] desc_pos  Pozycja kołnierza
    * @return  Kod błędu
    */
    public int GetActualToolFlangePose(int flag, DescPose desc_pos)

Pobieranie bieżącego momentu obrotowego przegubów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Pobieranie bieżącego momentu obrotowego przegubów
    * @param  [in]  flag 0-blokujący, 1-nieblokujący
    * @param  [out]  torques Moment obrotowy przegubów
    * @return  Kod błędu
    */
    int GetJointTorques(int flag, Object[] torques);

Pobieranie czasu systemowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Pobieranie czasu systemowego
    * @return  List[0]:int Kod błędu; List[1]:double t_ms jednostka ms
    */
    List<Number> GetSystemClock();

Sprawdzanie, czy ruch robota został zakończony
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Sprawdzanie, czy ruch robota został zakończony
    * @param   [out] state  0-niezakończony, 1-zakończony
    * @return  Kod błędu
    */
    public int GetRobotMotionDone(int[] state)

Sprawdzanie długości bufora kolejki ruchu robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Sprawdzanie długości bufora kolejki ruchu robota
    * @param   [out] len  Długość bufora
    * @return  Kod błędu
    */
    public int GetMotionQueueLength(int[] len)

Pobieranie stanu zatrzymania awaryjnego robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Pobieranie stanu zatrzymania awaryjnego robota
    * @param [out] state Stan zatrzymania awaryjnego, 0-brak zatrzymania awaryjnego, 1-zatrzymanie awaryjne
    * @return Kod błędu
    */
    public int GetRobotEmergencyStopState(int[] state)

Pobieranie stanu komunikacji SDK z robotem
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Pobieranie stanu komunikacji SDK z robotem
    * @return state Stan komunikacji, 0-komunikacja normalna, 1-komunikacja nieprawidłowa
    */
    public int GetSDKComState()

Pobieranie sygnału bezpiecznego zatrzymania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Pobieranie sygnału bezpiecznego zatrzymania
    * @param  [out] si0_state Sygnał bezpiecznego zatrzymania SI0, 0-nieaktywny, 1-aktywny
    * @param  [out] si1_state Sygnał bezpiecznego zatrzymania SI1, 0-nieaktywny, 1-aktywny
    * @return Kod błędu
    */
    public int GetSafetyStopState(int[] si0_state, int[] si1_state)

Pobieranie temperatury sterownika przegubu robota (℃)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Pobieranie temperatury sterownika przegubu robota (℃)
    * @param  [out] temperature Temperatura
    * @return Kod błędu
    */
    public int GetJointDriverTemperature(double[] temperature)

Pobieranie momentu obrotowego sterownika przegubu robota (Nm)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Pobieranie momentu obrotowego sterownika przegubu robota (Nm)
    * @param  [out] torque Moment obrotowy
    * @return Kod błędu
    */
    public int GetJointDriverTorque(double[] torque)

Pobieranie struktury stanu robota w czasie rzeczywistym
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Pobieranie struktury stanu robota w czasie rzeczywistym
    * @return Struktura stanu w czasie rzeczywistym
    */
    public ROBOT_STATE_PKG GetRobotRealTimeState()

Przykład kodu zapytania o stan robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestGetStatus(Robot robot)
    {
        List<Number> angle=new ArrayList<>();
        angle=robot.GetRobotInstallAngle();
        System.out.println("yangle:"+angle.get(1)+",zangle:"+angle.get(2));

        JointPos j_deg =new JointPos(){};
        robot.GetActualJointPosDegree( j_deg);

        Object[] jointSpeed =new Object[] { 0,0,0,0,0,0 };
        robot.GetActualJointSpeedsDegree(jointSpeed);

        Object[] jointAcc = new Object[]{0,0,0,0,0,0 };
        robot.GetActualJointAccDegree(0, jointAcc);

        double tcp_speed = 0.0;
        double ori_speed = 0.0;
        robot.GetTargetTCPCompositeSpeed(0, tcp_speed, ori_speed);

        robot.GetActualTCPCompositeSpeed(0, tcp_speed, ori_speed);

        Object[] targetSpeed =new Object[] { 0,0,0,0,0,0 };
        robot.GetTargetTCPSpeed(0, targetSpeed);

        Object[] actualSpeed =new Object[] {0,0,0,0,0,0 };
        robot.GetActualTCPSpeed(0, actualSpeed);

        DescPose tcp = new DescPose(){};
        robot.GetActualTCPPose(tcp);

        DescPose flange = new DescPose(){};
        robot.GetActualToolFlangePose(0, flange);

        int[] id = {};
        robot.GetActualTCPNum(0, id);

        robot.GetActualWObjNum(0, id);

        List<Number> jtorque=new ArrayList<>();
        jtorque=robot.GetJointTorques(0);

        List<Number> t_ms = new ArrayList<>();
        t_ms=robot.GetSystemClock();

        List<Integer> config = new ArrayList<>();
        config=robot.GetRobotCurJointsConfig();

        int motionDone = 0;
        robot.GetRobotMotionDone(motionDone);

        int[] len ={0 };
        robot.GetMotionQueueLength(len);

        int[] emergState = {0};
        robot.GetRobotEmergencyStopState(emergState);

        int comstate = 0;
        comstate=robot.GetSDKComState();

        int[] si0_state=new int[]{0}, si1_state=new int[]{0};
        robot.GetSafetyStopState(si0_state, si1_state);

        double[] temp =new double[] { 0,0,0,0,0,0 };
        robot.GetJointDriverTemperature(temp);

        double[] torque = new double[]{ 0,0,0,0,0,0 };
        robot.GetJointDriverTorque(torque);

        ROBOT_STATE_PKG pkg=new ROBOT_STATE_PKG();
        pkg=robot.GetRobotRealTimeState();

        return 0;
    }

Rozwiązanie kinematyki odwrotnej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Rozwiązanie kinematyki odwrotnej
    * @param  [in] type 0-pozycja absolutna (układ bazowy), 1-pozycja przyrostowa (układ bazowy), 2-pozycja przyrostowa (układ narzędzia)
    * @param  [in] desc_pos Pozycja kartezjańska
    * @param  [in] config Konfiguracja przestrzeni przegubów, [-1]-obliczenia względem bieżącej pozycji przegubów, [0~7]-obliczenia według określonej konfiguracji przestrzeni przegubów
    * @param  [out] joint_pos Pozycja przegubów
    * @return  Kod błędu
    */ 
    int GetInverseKin(int type, DescPose desc_pos, int config, JointPos joint_pos);

Rozwiązanie kinematyki odwrotnej (z pozycją referencyjną)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Rozwiązanie kinematyki odwrotnej, obliczenia względem podanej pozycji referencyjnej przegubów
    * @param  [in] posMode 0-pozycja absolutna, 1-pozycja względna - układ bazowy, 2-pozycja względna - układ narzędzia
    * @param  [in] desc_pos Pozycja kartezjańska
    * @param  [in] joint_pos_ref Referencyjna pozycja przegubów
    * @param  [out] joint_pos Pozycja przegubów
    * @return  Kod błędu
    */   
    int GetInverseKinRef(int posMode, DescPose desc_pos, JointPos joint_pos_ref, JointPos joint_pos); 

Rozwiązanie kinematyki odwrotnej, przestrzeń kartezjańska z uwzględnieniem pozycji osi rozszerzenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Rozwiązanie kinematyki odwrotnej, przestrzeń kartezjańska z uwzględnieniem pozycji osi rozszerzenia
    * @param  type 0-pozycja absolutna (układ bazowy), 1-pozycja przyrostowa (układ bazowy), 2-pozycja przyrostowa (układ narzędzia)
    * @param  desc_pos Pozycja kartezjańska
    * @param  exaxis Pozycja osi rozszerzenia
    * @param  tool Numer narzędzia
    * @param  workPiece Numer przedmiotu
    * @param  joint_pos Pozycja przegubów
    * @return Kod błędu
    */
    public int GetInverseKinExaxis(int type, DescPose desc_pos, ExaxisPos exaxis, int tool, int workPiece, JointPos joint_pos)
    
Przykład kodu rozwiązania kinematyki odwrotnej z uwzględnieniem pozycji osi rozszerzenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static void  TestInverseKinExaxis(Robot robot)
    {
        DescPose desc=new DescPose(99.957, -0.002, 29.994, -176.569, -6.757, -167.462);
        ExaxisPos exaxis=new ExaxisPos(100.0, 0.0, 0.0, 0.0);
        JointPos jointPos =new JointPos();
        DescPose offsetPos =new DescPose();
        ROBOT_STATE_PKG pkg=robot.GetRobotRealTimeState();
        int toolnum = pkg.tool;
        int workPcsNum = pkg.user;
        robot.GetInverseKinExaxis(0, desc, exaxis, toolnum, workPcsNum, jointPos);
        System.out.printf("GetInverseKinExaxis joint is %f, %f, %f, %f, %f, %f\n", jointPos.J1, jointPos.J2, jointPos.J3, jointPos.J4, jointPos.J5, jointPos.J6);
        robot.ExtAxisMove(exaxis, 100, -1);
        robot.MoveJ(jointPos, desc, toolnum, workPcsNum, 100.0, 100.0, 100.0, exaxis, -1, 0, offsetPos);
        robot.CloseRPC();
        robot.Sleep(9999999);
    }

Sprawdzanie, czy kinematyka odwrotna ma rozwiązanie
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Sprawdzanie, czy kinematyka odwrotna ma rozwiązanie, odniesienie do podanej pozycji referencyjnej przegubów
    * @param  [in] posMode 0-pozycja absolutna, 1-pozycja względna - układ bazowy, 2-pozycja względna - układ narzędzia
    * @param  [in] desc_pos Pozycja kartezjańska
    * @param  [in] joint_pos_ref Referencyjna pozycja przegubów
    * @return  Kod błędu  List[0]:Kod błędu; List[1]: int hasResult 0-brak rozwiązania, 1-jest rozwiązanie
    */   
    List<Integer> GetInverseKinHasSolution(int posMode, DescPose desc_pos, JointPos joint_pos_ref);  

Rozwiązanie kinematyki prostej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Rozwiązanie kinematyki prostej
    * @param  [in] joint_pos Pozycja przegubów
    * @param  [out] desc_pos Pozycja kartezjańska
    * @return  Kod błędu
    */
    int GetForwardKin(JointPos joint_pos, DescPose desc_pos); 

Przykład kodu obliczeń kinematyki prostej i odwrotnej robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestInverseKin(Robot robot)
    {
        JointPos j1=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        DescPose desc_pos1=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);

        JointPos inverseRtn = new JointPos(){};

        robot.GetInverseKin(0, desc_pos1, -1, inverseRtn);
        robot.GetInverseKinRef(0, desc_pos1, j1, inverseRtn);

        int hasResut = 0;
        robot.GetInverseKinHasSolution(0, desc_pos1, j1);

        DescPose forwordResult = new DescPose(){};
        robot.GetForwardKin(j1, forwordResult);

        return 0;
    }

Zapytanie o dane punktu zarządzania nauczaniem robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Zapytanie o dane punktu zarządzania nauczaniem robota 
    * @param [in]  name  Nazwa punktu
    * @return  List[0]:Kod błędu; List[1] - List[20] : Dane punktu double[20]{x,y,z,rx,ry,rz,j1,j2,j3,j4,j5,j6,tool,wobj,speed,acc,e1,e2,e3,e4} 
    */ 
    List<Number> GetRobotTeachingPoint(String name); 

Pobieranie wartości kompensacji parametrów DH robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Pobieranie wartości kompensacji parametrów DH robota
    * @param dhCompensation Wartości kompensacji parametrów DH robota (mm) [cmpstD1,cmpstA2,cmpstA3,cmpstD4,cmpstD5,cmpstD6]
    * @return Kod błędu
    */
    public int GetDHCompensation(Object[] dhCompensation)

Pobieranie numeru SN skrzynki kontrolnej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.4-3.8.1

.. code-block:: Java
    :linenos:

    /**
    * @brief Pobieranie numeru SN skrzynki kontrolnej
    * @param [out] SNCode Numer SN skrzynki kontrolnej
    * @return Kod błędu
    */
    int GetRobotSN(String[] SNCode);

Przykład kodu zapytania o dane punktu zarządzania nauczaniem robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestGetTeachPoint(Robot robot)
    {
        String name = "P1";
        List<Number> data=new ArrayList<>();
        data = robot.GetRobotTeachingPoint(name);
        System.out.println(name+" name is: "+data.get(0));
        for (int i = 0; i < 20; i++)
        {
            System.out.println("data is: "+ data.get(i+1));
        }

        int[] que_len = {0};
        int rtn = robot.GetMotionQueueLength(que_len);
        System.out.println("GetMotionQueueLength rtn is:"+rtn+", queue length is:"+ que_len[0]);

        Object[] dh = new Object[]{ 0,0,0,0,0,0 };
        int retval = 0;
        retval = robot.GetDHCompensation(dh);
        System.out.println("retval is: "+retval);

        String[] SN = new String[]{""};
        robot.GetRobotSN(SN);
        System.out.println("robot SN is "+SN[0]);
        return 0;
    }

Pobieranie Układu Współrzędnych Narzędzia według ID
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-V3.9.8

.. code-block:: Java
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
    int GetToolCoordWithID(int id, DescPose coord, int[] type, int[] install, int[] toolID, int[] loadNo)

Pobieranie Układu Współrzędnych Przedmiotu według ID
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-V3.9.8

.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera układ współrzędnych przedmiotu według ID
    * @param [in] id Numer układu współrzędnych przedmiotu
    * @param [out] coord Wartości układu współrzędnych
    * @param [out] refFrame Referencyjny układ współrzędnych
    * @return Kod błędu
    */
    public int GetWObjCoordWithID(int id, DescPose coord, int[] refFrame)

Pobieranie Zewnętrznego Układu Współrzędnych Narzędzia według ID
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-V3.9.8

.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera zewnętrzny układ współrzędnych narzędzia według ID
    * @param [in] id Numer zewnętrznego układu współrzędnych narzędzia, 20-39 odpowiadają zewnętrznym układom współrzędnych narzędzi 0-19
    * @param [out] coord Pozycja TCP stałego narzędzia zewnętrznego na robocie
    * @param [out] tcoord Pozycja układu współrzędnych przedmiotu zamontowanego na końcówce robota
    * @return Kod błędu
    */
    public int GetExToolCoordWithID(int id, DescPose coord, DescPose tcoord)

Pobieranie Układu Współrzędnych Osi Rozszerzonej według ID
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-V3.9.8

.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera układ współrzędnych osi rozszerzonej według ID
    * @param [in] id Numer zewnętrznego układu współrzędnych narzędzia
    * @param [out] coord Wartości układu współrzędnych
    * @param [out] axisCoordNum Numer osi rozszerzonej; bit0-bit3 odpowiadają osiom rozszerzonym 1-4; np. wartość axisCoordNum 3 odpowiada osiom rozszerzonym [1, 2]
    * @param [out] calibFlag Flaga kalibracji; 0-niekalibrowany; 1-kalibrowany
    * @return Kod błędu
    */
    public int GetExAxisCoordWithID (int id, DescPose coord, int[] axisCoordNum, int[] calibFlag)

Pobieranie bieżącego układu narzędzia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Pobieranie bieżącego układu narzędzia
     * @param [out] coord Wartości układu współrzędnych
     * @return Kod błędu
     */
    public int GetCurToolCoord(DescPose coord)

Pobieranie bieżącego układu przedmiotu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Pobieranie bieżącego układu przedmiotu
     * @param [out] coord Wartości układu współrzędnych
     * @return Kod błędu
     */
    public int GetCurWObjCoord(DescPose coord)

Pobieranie bieżącego zewnętrznego układu narzędzia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Pobieranie bieżącego zewnętrznego układu narzędzia
     * @param  [out] coord Wartości układu współrzędnych
     * @return Kod błędu
     */
    public int GetCurExToolCoord(DescPose coord)

Pobieranie bieżącego układu osi rozszerzenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Pobieranie bieżącego układu osi rozszerzenia
     * @param [out] coord Wartości układu współrzędnych
     * @return Kod błędu
     */
    public int GetCurExAxisCoord(DescPose coord)

Przykład kodu układów współrzędnych robota i obciążenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestCoord(Robot robot)
    {
        int id = 1;
        DescPose toolCoord = new DescPose();
        DescPose extoolCoord = new DescPose();
        DescPose exworkpieceCoord = new DescPose();
        DescPose wobjCoord = new DescPose();
        DescPose exAxisCoord = new DescPose();
        int[] type = new int[1];
        int[] install = new int[1];
        int[] toolID = new int[1];
        int[] loadNo = new int[1];
        robot.GetToolCoordWithID(id, toolCoord, type, install, toolID, loadNo);
        System.out.printf("GetToolCoordWithID %d, %f %f %f %f %f %f,  type = %d, install = %d, toolID = %d, loadNo = %d\n", id,
            toolCoord.tran.x, toolCoord.tran.y, toolCoord.tran.z,
            toolCoord.rpy.rx, toolCoord.rpy.ry, toolCoord.rpy.rz, type[0], install[0], toolID[0], loadNo[0]);
        int[] refFrame = new int[1];
        robot.GetWObjCoordWithID(id, wobjCoord, refFrame);
        System.out.printf("GetWObjCoordWithID %d, %f %f %f %f %f %f, refFrame = %d\n", id,
            wobjCoord.tran.x, wobjCoord.tran.y, wobjCoord.tran.z,
            wobjCoord.rpy.rx, wobjCoord.rpy.ry, wobjCoord.rpy.rz, refFrame[0]);


        robot.GetExToolCoordWithID(21, extoolCoord, exworkpieceCoord);
        System.out.printf("GetExToolCoordWithID %d, %f %f %f %f %f %f\n", id,
            extoolCoord.tran.x, extoolCoord.tran.y, extoolCoord.tran.z,
            extoolCoord.rpy.rx, extoolCoord.rpy.ry, extoolCoord.rpy.rz,
            exworkpieceCoord.tran.x, exworkpieceCoord.tran.y, exworkpieceCoord.tran.z,
            exworkpieceCoord.rpy.rx, exworkpieceCoord.rpy.ry, exworkpieceCoord.rpy.rz);

        int[] axisCoordNum = new int[1];
        int[] calibFlag = new int[1];
        robot.GetExAxisCoordWithID(id, exAxisCoord, axisCoordNum, calibFlag);
        System.out.printf("GetExAxisCoordWithID %d, %f %f %f %f %f %f, axisCoordNum = %d, calibFlag = %d\n", id,
            exAxisCoord.tran.x, exAxisCoord.tran.y, exAxisCoord.tran.z,
            exAxisCoord.rpy.rx, exAxisCoord.rpy.ry, exAxisCoord.rpy.rz, axisCoordNum[0], calibFlag[0]);

        double[] weight = new double[1];
        DescTran cog = new DescTran();
        robot.GetTargetPayloadWithID(id, weight, cog);
        System.out.println("GetTargetPayload is " + weightT.get(0) + " cogT is  " + cogT.x + "  " + cogT.y + "  " + cogT.z);
        robot.GetCurToolCoord(toolCoord);
        System.out.printf("GetCurToolCoord %f %f %f %f %f %f\n",
            toolCoord.tran.x, toolCoord.tran.y, toolCoord.tran.z,
            toolCoord.rpy.rx, toolCoord.rpy.ry, toolCoord.rpy.rz);
        robot.GetCurWObjCoord(wobjCoord);
        System.out.printf("GetCurWObjCoord %f %f %f %f %f %f\n",
            wobjCoord.tran.x, wobjCoord.tran.y, wobjCoord.tran.z,
            wobjCoord.rpy.rx, wobjCoord.rpy.ry, wobjCoord.rpy.rz);
        robot.GetCurExToolCoord(extoolCoord);
        System.out.printf("GetExToolCoordWithID %f %f %f %f %f %f\n",
            extoolCoord.tran.x, extoolCoord.tran.y, extoolCoord.tran.z,
            extoolCoord.rpy.rx, extoolCoord.rpy.ry, extoolCoord.rpy.rz);
        robot.GetCurExAxisCoord(exAxisCoord);
        System.out.printf("GetCurExAxisCoord %f %f %f %f %f %f\n",
            exAxisCoord.tran.x, exAxisCoord.tran.y, exAxisCoord.tran.z,
            exAxisCoord.rpy.rx, exAxisCoord.rpy.ry, exAxisCoord.rpy.rz);
        DescTran cogT = new DescTran();
        List<Number> weightT = robot.GetTargetPayload(0);
        robot.GetTargetPayloadCog(0, cogT);
        System.out.printf("GetTargetPayload %f %f %f %f\n", weightT.get(0),
            cogT.x, cogT.y, cogT.z);
        DescPose coordSet = new DescPose(0, 1, 2, 3, 4, 5);
        robot.SetToolCoord(1, coordSet, 0, 0, 1, 0);
        robot.SetWObjCoord(1, coordSet, 0);
        robot.SetLoadWeight(1, 1.3);
        cog.x = 10;
        cog.y = 20;
        cog.z = 30;
        robot.SetLoadCoord(1, cog);
        DescPose etcp = new DescPose(0, 0, 100, 0, 0, 0);
        DescPose etool = new DescPose(0, 0, 50, 0, 0, 0);
        int rtn = robot.SetExToolCoord(21, etcp, etool);
        System.out.printf("SetExToolCoord rtn is %d\n", rtn);
        robot.ExtAxisActiveECoordSys(1, 1, coordSet, 1);
        return 0;
    }