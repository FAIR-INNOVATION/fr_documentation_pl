Ustawienia bezpieczeństwa robota
=================================

.. toctree:: 
    :maxdepth: 5

Ustawianie poziomu kolizji
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawianie poziomu kolizji
    * @param  [in]  mode  0-poziom, 1-procent
    * @param  [in]  level Próg kolizji, poziom odpowiada zakresowi [1 - 10 dla poziomów 1-10, 100-wyłączone], procent odpowiada zakresowi [0~10 dla 0% - 100%]
    * @param  [in]  config 0-nie aktualizuj pliku konfiguracyjnego, 1-aktualizuj plik konfiguracyjny
    * @return  Kod błędu
    */
    int SetAnticollision(int mode, Object[] level, int config); 

Ustawianie strategii po kolizji
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Ustawianie strategii po kolizji
    * @param  [in] strategy  0-zatrzymaj z błędem, 1-kontynuuj działanie
    * @param  [in] safeTime  Czas bezpiecznego zatrzymania [1000 - 2000] ms
    * @param  [in] safeDistance  Bezpieczna odległość zatrzymania [1-150] mm
    * @param  [in] safetyMargin  Współczynniki bezpieczeństwa dla j1-j6 [1-10]
    * @return  Kod błędu  
    */
    int SetCollisionStrategy(int strategy, int safeTime, int safeDistance, int safetyMargin[]); 

Rozpoczęcie funkcji niestandardowego progu detekcji kolizji
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.3-3.8.0

.. code-block:: Java
    :linenos:

    /**
    * @brief  Rozpoczęcie funkcji niestandardowego progu detekcji kolizji, ustawienie progów detekcji kolizji dla strony przegubów i strony TCP
    * @param  [in] flag 1-tylko detekcja przegubów włączona; 2-tylko detekcja TCP włączona; 3-detekcja przegubów i TCP włączone jednocześnie
    * @param  [in] jointDetectionThreshould Próg detekcji kolizji przegubów j1-j6
    * @param  [in] tcpDetectionThreshould  Próg detekcji kolizji TCP, xyzabc
    * @param  [in] block 0-nieblokujący; 1-blokujący
    * @return  Kod błędu
    */   
    public int CustomCollisionDetectionStart(int flag, double[] jointDetectionThreshould, double[] tcpDetectionThreshould, int block);

Zakończenie funkcji niestandardowego progu detekcji kolizji
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: Java SDK-v1.0.3-3.8.0

.. code-block:: Java
    :linenos:

    /**
    * @brief  Zakończenie funkcji niestandardowego progu detekcji kolizji
    * @return  Kod błędu
    */   
    public int CustomCollisionDetectionEnd();

Przykład kodu ustawiania poziomu kolizji robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestCollision(Robot robot)
    {
        int mode = 0;
        int config = 1;
        Object[] level1 = new Object[]{ 1.0,2.0,3.0,4.0,5.0,6.0 };
        Object[] level2 = new Object[]{ 50.0,20.0,30.0,40.0,50.0,60.0 };

        int rtn = robot.SetAnticollision(mode, level1, config);
        System.out.println("SetAnticollision mode 0 rtn is: "+ rtn);
        mode = 1;
        rtn = robot.SetAnticollision(mode, level2, config);
        System.out.println("SetAnticollision mode 1 rtn is :"+ rtn);

        JointPos p1Joint=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos p2Joint=new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);

        DescPose p1Desc=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose p2Desc=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);

        ExaxisPos exaxisPos=new ExaxisPos(0.0, 0.0, 0.0, 0.0);
        DescPose offdese=new DescPose(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);
        robot.MoveL(p2Joint, p2Desc, 0, 0, 100, 100, 100, 2,0, exaxisPos, 0, 0, offdese,0,10);
        robot.ResetAllError();
        int[] safety = new int[]{ 5,5,5,5,5,5 };
        rtn = robot.SetCollisionStrategy(3, 1000, 150, 250, safety);
        System.out.println("SetCollisionStrategy rtn is:"+ rtn);

        double[] jointDetectionThreshould = new double[]{ 0.1, 0.1, 0.1, 0.1, 0.1, 0.1 };
        double[] tcpDetectionThreshould =new double[] { 60,60,60,60,60,60 };
        rtn = robot.CustomCollisionDetectionStart(3, jointDetectionThreshould, tcpDetectionThreshould, 0);
        System.out.println("CustomCollisionDetectionStart rtn is :"+ rtn);

        robot.MoveL(p1Joint, p1Desc, 0, 0, 100, 100, 100, -1,0, exaxisPos, 0, 0, offdese,0,10);
        robot.MoveL(p2Joint, p2Desc, 0, 0, 100, 100, 100, -1,0, exaxisPos, 0, 0, offdese,0,10);
        rtn = robot.CustomCollisionDetectionEnd();
        System.out.println("CustomCollisionDetectionEnd rtn is: "+ rtn);
        return 0;
    }

Ustawianie dodatniego ograniczenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Ustawianie dodatniego ograniczenia
    * @param  [in] limit Pozycje sześciu przegubów, jednostka deg
    * @return  Kod błędu
    */
    int SetLimitPositive(Object[] limit); 

Ustawianie ujemnego ograniczenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Ustawianie ujemnego ograniczenia
    * @param  [in] limit Pozycje sześciu przegubów, jednostka deg
    * @return  Kod błędu
    */
    int SetLimitNegative(Object[] limit); 

Pobieranie kątów miękkiego ograniczenia przegubów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Pobieranie kątów miękkiego ograniczenia przegubów
    * @param  [in] flag 0-blokujący, 1-nieblokujący
    * @param  [out] negative  Kąt ujemnego ograniczenia, jednostka deg
    * @param  [out] positive  Kąt dodatniego ograniczenia, jednostka deg
    * @return  Kod błędu
    */
    int GetJointSoftLimitDeg(int flag, Object[] negative, Object[] positive); 

Przykład kodu ustawiania ograniczeń robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestLimit(Robot robot)
    {
        Object[] plimit =new Object[] { 170.0,80.0,150.0,80.0,170.0,160.0 };
        robot.SetLimitPositive(plimit);
        Object[] nlimit =new Object[] { -170.0,-260.0,-150.0,-260.0,-170.0,-160.0 };
        robot.SetLimitNegative(nlimit);

        Object[] neg_deg =new Object[] {0, 0 , 0, 0, 0, 0}, pos_deg = new Object[]{0, 0 , 0, 0, 0, 0};
        robot.GetJointSoftLimitDeg(1,  neg_deg,  pos_deg);
        System.out.println("neg limit deg:"+ neg_deg[0]+","+ neg_deg[1]+","+ neg_deg[2]+","+ neg_deg[3]+","+ neg_deg[4]+","+ neg_deg[5]);
        System.out.println("pos limit deg:"+pos_deg[0]+","+ pos_deg[1]+","+ pos_deg[2]+","+ pos_deg[3]+","+ pos_deg[4]+","+pos_deg[5]);
        return 0;
    }

Ustawianie metody detekcji kolizji robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionchanged:: Java SDK-v1.0.5-3.8.2

.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawianie metody detekcji kolizji robota
    * @param [in] method Metoda detekcji kolizji: 0-tryb prądowy; 1-podwójny enkoder; 2-tryb prądowy i podwójny enkoder włączone jednocześnie
    * @param [in] thresholdMode Sposób progu poziomu kolizji; 0-stały próg poziomu kolizji; 1-niestandardowy próg detekcji kolizji
    * @return Kod błędu
    */
    int SetCollisionDetectionMethod(int method,int thresholdMode)

Włączanie/wyłączanie detekcji kolizji w stanie statycznym
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Włączanie/wyłączanie detekcji kolizji w stanie statycznym
    * @param  [in] status 0-wyłączone; 1-włączone
    * @return  Kod błędu
    */
    public int SetStaticCollisionOnOff(int status)

Przykład kodu ustawiania metody detekcji kolizji robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestCollisionMethod(Robot robot)
    {
        int rtn = robot.SetCollisionDetectionMethod(0);

        rtn = robot.SetStaticCollisionOnOff(1);
        System.out.println("SetStaticCollisionOnOff On rtn is:"+ rtn);
        robot.Sleep(5000);
        rtn = robot.SetStaticCollisionOnOff(0);
        System.out.println("SetStaticCollisionOnOff Off rtn is:"+ rtn);

        robot.CloseRPC();
        return 0;
    }

Detekcja momentu obrotowego i mocy przegubów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Detekcja momentu obrotowego i mocy przegubów
    * @param  [in] status 0-wyłączone; 1-włączone
    * @param  [in] power Ustawiona maksymalna moc (W)
    * @return  Kod błędu
    */
    public int SetPowerLimit(int status, double power)

Przykład kodu detekcji momentu obrotowego i mocy przegubów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestPowerLimit(Robot robot)
    {
        robot.DragTeachSwitch(1);
        robot.SetPowerLimit(1, 200);
        List<Number> joint_toq=new ArrayList<>();
        joint_toq=robot.GetJointTorques(1);

        int count = 100;
        robot.ServoJTStart(); //   #servoJT开始
        int error = 0;
        while (count > 0)
        {
            count = count - 1;
            robot.Sleep(1);
        }
        error = robot.ServoJTEnd();
        robot.DragTeachSwitch(0);

        robot.CloseRPC();
        return 0;
    }
    
Ustawianie parametrów bezpiecznej prędkości
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawianie parametrów bezpiecznej prędkości
    * @param enable 0-wył.; 1-włączone w trybie ręcznym; 2-włączone we wszystkich trybach (automatyczne ograniczanie prędkości nie jest obsługiwane)
    * @param maxTCPVel Ograniczenie maksymalnej prędkości TCP; [0-1000] mm/s
    * @param strategy Strategia po przekroczeniu prędkości; 0-zatrzymaj i alarmuj; 1-automatyczne ograniczanie prędkości; 2-zatrzymaj, alarmuj i dezaktywuj
    * @return Kod błędu
    */
    public int SetVelReducePara(int enable, double maxTCPVel, int strategy)
        
Przykład kodu SDK ustawiania parametrów bezpiecznej prędkości
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestSetVelReducePara(Robot robot) {
        int rtn = 0;

        JointPos j1 = new JointPos(0, -90, 90, 0, 0, 0);
        JointPos j2 = new JointPos(90, -90, 90, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);

        robot.SetSpeed(80);
        rtn = robot.SetVelReducePara(2, 30, 1);
        System.out.printf("SetVelReducePara param error rtn is %d\n", rtn);

        rtn = robot.SetVelReducePara(0, 30, 1);
        System.out.printf("SetVelReducePara disable reduce vel rtn is %d\n", rtn);
        robot.MoveJ(j1, 0, 0, 100, 100, 100.0, epos, -1.0, 0, offset_pos);
        robot.MoveJ(j2, 0, 0, 100, 100, 100.0, epos, -1.0, 0, offset_pos);

        rtn = robot.SetVelReducePara(1, 30, 1);
        System.out.printf("SetVelReducePara reduce vel rtn is %d\n", rtn);
        robot.MoveJ(j1, 0, 0, 100, 100, 100.0, epos, -1.0, 0, offset_pos);
        robot.MoveJ(j2, 0, 0, 100, 100, 100.0, epos, -1.0, 0, offset_pos);

        rtn = robot.SetVelReducePara(2, 30, 2);
        System.out.printf("SetVelReducePara disable robot rtn is %d\n", rtn);
        robot.MoveJ(j1, 0, 0, 100, 100, 100.0, epos, -1.0, 0, offset_pos);
        robot.MoveJ(j2, 0, 0, 100, 100, 100.0, epos, -1.0, 0, offset_pos);

        robot.Sleep(2000);
        robot.ResetAllError();
        robot.RobotEnable(1);
        robot.Sleep(1000);

        rtn = robot.SetVelReducePara(2, 30, 0);
        System.out.printf("SetVelReducePara report error rtn is %d\n", rtn);
        robot.MoveJ(j1, 0, 0, 100, 100, 100.0, epos, -1.0, 0, offset_pos);
        robot.MoveJ(j2, 0, 0, 100, 100, 100.0, epos, -1.0, 0, offset_pos);

        robot.Sleep(1000);
        return 0;
    }