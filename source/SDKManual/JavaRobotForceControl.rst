Sterowanie siłą robota
======================

.. toctree::
    :maxdepth: 5

Konfiguracja czujnika siły
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Konfiguruje czujnik siły
    * @param  config company: Producent czujnika siły, 17-Kunwei Technology, 19-Instytut Kosmiczny 11, 20-Czujnik ATI, 21-Zhongke Midian, 22-Weihang Minxin, 23-NBIT, 24-Xinjingcheng (XJC), 26-NSR
    * @param  config device: Numer urządzenia, Kunwei (0-KWR75B), Instytut Kosmiczny 11 (0-MCS6A-200-4), ATI (0-AXIA80-M8), Zhongke Midian (0-MST2010), Weihang Minxin (0-WHC6L-YB-10A), NBIT (0-XLH93003ACS), Xinjingcheng XJC (0-XJC-6F-D82), NSR (0-NSR-FTSensorA)
    * @param  config softvesion: Numer wersji oprogramowania, tymczasowo nieużywany, domyślnie 0
    * @param  config bus: Pozycja magistrali końcowej, na której zamontowane jest urządzenie, tymczasowo nieużywane, domyślnie 0
    * @return  Kod błędu
    */
    int FT_SetConfig(DeviceConfig config);

Pobieranie konfiguracji czujnika siły
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera konfigurację czujnika siły
    * @param [out] config company: Producent czujnika siły, 17-Kunwei Technology, 19-Instytut Kosmiczny 11, 20-ATI, 21-Zhongke Midian, 22-Weihang Minxin
    * @param [out] config device: Numer urządzenia, Kunwei (0-KWR75B), Instytut Kosmiczny 11 (0-MCS6A-200-4), ATI (0-AXIA80-M8), Zhongke Midian (0-MST2010), Weihang Minxin (0-WHC6L-YB-10A)
    * @param [out] config softvesion: Numer wersji oprogramowania, tymczasowo nieużywany, domyślnie 0
    * @param [out] config bus: Pozycja magistrali końcowej, na której zamontowane jest urządzenie, tymczasowo nieużywane, domyślnie 0
    * @return Kod błędu
    */
    int FT_GetConfig(DeviceConfig config);

Aktywacja czujnika siły
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Aktywuje czujnik siły
    * @param [in] act  0-reset, 1-aktywacja
    * @return  Kod błędu
    */
    int FT_Activate(int act);

Zerowanie czujnika siły
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Zeruje czujnik siły
    * @param [in] act  0-usuń punkt zerowy, 1-korekcja zera
    * @return  Kod błędu
    */
    int FT_SetZero(int act);

Ustawianie układu odniesienia czujnika siły
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Ustawia układ odniesienia czujnika siły
    * @param [in] type  0-układ współrzędnych narzędzia, 1-układ współrzędnych bazowych, 2-swobodny układ współrzędnych
    * @param [in] coord  Wartości swobodnego układu współrzędnych
    * @return  Kod błędu
    */
    int FT_SetRCS(int type, DescPose coord);

Ustawianie masy obciążenia pod czujnikiem siły
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia masę obciążenia pod czujnikiem siły
    * @param [in] weight Masa obciążenia [kg]
    * @return Kod błędu
    */
    int SetForceSensorPayLoad(double weight);

Ustawianie środka ciężkości obciążenia pod czujnikiem siły
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia środek ciężkości obciążenia pod czujnikiem siły
    * @param [in] cog Środek ciężkości obciążenia [mm]
    * @return Kod błędu
    */
    int SetForceSensorPayLoadCog(DescTran cog);

Pobieranie masy obciążenia pod czujnikiem siły
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera masę obciążenia pod czujnikiem siły
    * @return List[0]:kod błędu; List[1] : weight masa obciążenia [kg]
    */
    List<Number> GetForceSensorPayLoad();

Pobieranie środka ciężkości obciążenia pod czujnikiem siły
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera środek ciężkości obciążenia pod czujnikiem siły
    * @param [out] cog Środek ciężkości obciążenia [mm]
    * @return Kod błędu
    */
    int GetForceSensorPayLoadCog(DescTran cog);

Automatyczne zerowanie czujnika siły
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Automatyczne zerowanie czujnika siły
    * @param [in] massCenter Masa czujnika (kg) i środek ciężkości (mm)
    * @return Kod błędu
    */
    int ForceSensorAutoComputeLoad(MassCenter massCenter);

Pobieranie danych siły/momentu w układzie odniesienia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Pobiera dane siły/momentu w układzie odniesienia
    * @param  [in] flag 0-blokujący, 1-nieblokujący
    * @param  [out] ft   Siła/moment, fx, fy, fz, tx, ty, tz
    * @return  Kod błędu
    */
    int FT_GetForceTorqueRCS(int flag, ForceTorque ft);

Pobieranie surowych danych siły/momentu z czujnika siły
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Pobiera surowe dane siły/momentu z czujnika siły
    * @param  [in] flag 0-blokujący, 1-nieblokujący
    * @param  [out] ft   Siła/moment, fx, fy, fz, tx, ty, tz
    * @return  Kod błędu
    */
    int FT_GetForceTorqueOrigin(int flag, ForceTorque ft);

Przykład kodu konfiguracji czujnika siły i automatycznego zerowania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestFTInit(Robot robot)
    {
        DescTran tr1=new DescTran(0,0,0);
        robot.SetForceSensorPayload(0);
        robot.SetForceSensorPayloadCog(tr1);

        int company = 24;
        int device = 0;
        int softversion = 0;
        int bus = 1;
        int index = 1;

        DeviceConfig con=new DeviceConfig(company,device,softversion,bus);
        robot.FT_SetConfig(con);
        robot.Sleep(1000);
        robot.FT_GetConfig(con);
        robot.Sleep(1000);

        robot.FT_Activate(0);
        robot.Sleep(1000);
        robot.FT_Activate(1);
        robot.Sleep(1000);

        robot.Sleep(1000);
        robot.FT_SetZero(0);
        robot.Sleep(1000);

        ForceTorque ft=new ForceTorque(0,0,0,0,0,0);
        robot.FT_GetForceTorqueOrigin(0, ft);
        robot.FT_SetZero(1);
        robot.Sleep(1000);

        DescPose ftCoord = new DescPose();
        robot.FT_SetRCS(0, ftCoord);

        robot.SetForceSensorPayload(0.824);

        DescTran tr=new DescTran(0.778, 2.554, 48.765);
        robot.SetForceSensorPayloadCog(tr);
        List<Number> weight = new ArrayList<>();
        double x = 0, y = 0, z = 0;
        weight=robot.GetForceSensorPayload();
        robot.GetForceSensorPayloadCog(tr);
        tr.x=0;
        tr.y=0;
        tr.z=0;
        robot.SetForceSensorPayload(0);
        robot.SetForceSensorPayloadCog(tr);

        double computeWeight = 0;
        DescTran tran = new DescTran();
        MassCenter mass=new MassCenter();
        mass.weight=weight.get(1).doubleValue();
        mass.cog=tran;
        robot.ForceSensorAutoComputeLoad(mass);
        return 0;
    }

Rejestracja identyfikacji masy obciążenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Rejestracja identyfikacji masy obciążenia
    * @param  [in] id   Numer układu współrzędnych czujnika, zakres [1~14]
    * @return  Kod błędu
    */
    int FT_PdIdenRecord(int id);

Obliczanie identyfikacji masy obciążenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obliczanie identyfikacji masy obciążenia
    * @return  List[0]:kod błędu; List[1] : double weight  Masa obciążenia, jednostka kg
    */
    List<Number> FT_PdIdenCompute();

Rejestracja identyfikacji środka ciężkości obciążenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Rejestracja identyfikacji środka ciężkości obciążenia
    * @param  [in] id   Numer układu współrzędnych czujnika, zakres [1~14]
    * @param  [in] index Numer punktu, zakres [1~3]
    * @return  Kod błędu
    */
    int FT_PdCogIdenRecord(int id, int index);

Obliczanie identyfikacji środka ciężkości obciążenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obliczanie identyfikacji środka ciężkości obciążenia
    * @param  [out] cog   Środek ciężkości obciążenia, jednostka mm
    * @return  Kod błędu
    */
    int FT_PdCogIdenCompute(DescTran cog);

Przykład kodu identyfikacji obciążenia czujnika siły
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestFTLoadCompute(Robot robot)
    {
        DescTran tr1=new DescTran(0,0,0);
        robot.SetForceSensorPayload(0);
        robot.SetForceSensorPayloadCog(tr1);

        int company = 24;
        int device = 0;
        int softversion = 0;
        int bus = 1;
        int index = 1;

        DeviceConfig con=new DeviceConfig(company, device, softversion, bus);
        robot.FT_SetConfig(con);
        robot.Sleep(1000);
        robot.FT_GetConfig(con);
        robot.Sleep(1000);

        robot.FT_Activate(0);
        robot.Sleep(1000);
        robot.FT_Activate(1);
        robot.Sleep(1000);

        robot.Sleep(1000);
        robot.FT_SetZero(0);
        robot.Sleep(1000);

        ForceTorque ft=new ForceTorque(0,0,0,0,0,0);
        robot.FT_GetForceTorqueOrigin(0, ft);
        robot.FT_SetZero(1);
        robot.Sleep(1000);

        DescPose tcoord = new DescPose();
        tcoord.tran.z = 35.0;
        robot.SetToolCoord(10, tcoord, 1, 0, 0, 0);

        robot.FT_PdIdenRecord(10);
        robot.Sleep(1000);

        List<Number> weight =new ArrayList<>();
        weight=robot.FT_PdIdenCompute();

        DescPose desc_p1=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_p2=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose desc_p3=new DescPose(-327.622, 402.230, 320.402, -178.067, 2.127, -46.207);

        robot.MoveCart(desc_p1, 0, 0, 100.0, 100.0, 100.0, -1.0, -1);
        robot.Sleep(1000);
        robot.FT_PdCogIdenRecord(10, 1);
        robot.MoveCart(desc_p2, 0, 0, 100.0, 100.0, 100.0, -1.0, -1);
        robot.Sleep(1000);
        robot.FT_PdCogIdenRecord(10, 2);
        robot.MoveCart(desc_p3, 0, 0, 100.0, 100.0, 100.0, -1.0, -1);
        robot.Sleep(1000);
        robot.FT_PdCogIdenRecord(10, 3);
        robot.Sleep(1000);
        DescTran cog=new DescTran(0,0,0);
        robot.FT_PdCogIdenCompute(cog);

        robot.CloseRPC();
        return 0;
    }

Ochrona przed kolizją
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Ochrona przed kolizją
    * @param  [in] flag 0-wyłącz ochronę przed kolizją, 1-włącz ochronę przed kolizją
    * @param  [in] sensor_id Numer czujnika siły
    * @param  [in] select  Wybór, czy wykrywać kolizję dla sześciu stopni swobody, 0-nie wykrywaj, 1-wykrywaj
    * @param  [in] ft   Siła/moment kolizji, fx, fy, fz, tx, ty, tz
    * @param  [in] max_threshold Maksymalny próg
    * @param  [in] min_threshold Minimalny próg
    * @note   Zakres wykrywania siły/momentu: (ft-min_threshold, ft+max_threshold)
    * @return  Kod błędu
    */
    int FT_Guard(int flag, int sensor_id, Object[] select, ForceTorque ft, Object[] max_threshold, Object[] min_threshold);

Przykład kodu ochrony przed kolizją
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void main(String[] args)
    {
        Robot robot = new Robot();
        robot.SetReconnectParam(true,20,500);
        robot.LoggerInit(FrLogType.DIRECT, FrLogLevel.INFO, "D://log", 10, 10);
        int rtn = robot.RPC("192.168.58.2");
        if(rtn == 0)
        {
            System.out.println("rpc połączenie success");
        }
        else
        {
            System.out.println("rpc połączenie fail");
            return ;
        }
        byte flag = 1;
        byte sensor_id = 8;
        Object[] select = { 1, 0, 0, 0, 0, 0 };
        Object[] max_threshold = { 5.0, 0.01, 0.01, 0.01, 0.01, 0.01 };
        Object[] min_threshold = { 3.0, 0.01, 0.01, 0.01, 0.01, 0.01 };

        ForceTorque ft = new ForceTorque(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);
        DescPose  desc_p1, desc_p2, desc_p3;
        desc_p1 = new DescPose(-14.404,-455.283,319.847,-172.935,25.141,-68.097);
        desc_p2 = new DescPose(-107.999,-599.174,285.939,153.472,12.686,-71.284);
        desc_p3 = new DescPose(6.586,-704.897,309.638,178.909,-27.759,-70.479);

        int rtn =  robot.FT_Guard(flag, sensor_id, select, ft, max_threshold, min_threshold);
        System.out.println("FT_Guard start rtn {rtn}");
        robot.MoveCart(desc_p1, 0, 0, 20, 100.0f, 100.0f, -1.0f, -1);
        robot.MoveCart(desc_p2, 0, 0, 20, 100.0f, 100.0f, -1.0f, -1);
        robot.MoveCart(desc_p3, 0, 0, 20, 100.0f, 100.0f, -1.0f, -1);
    }

Sterowanie stałą siłą
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Sterowanie stałą siłą
    * @param  flag 0-wyłącz sterowanie stałą siłą, 1-włącz sterowanie stałą siłą
    * @param  sensor_id Numer czujnika siły
    * @param  select  Wybór, czy wykrywać kolizję dla sześciu stopni swobody, 0-nie wykrywaj, 1-wykrywaj
    * @param  ft   Siła/moment kolizji, fx, fy, fz, tx, ty, tz
    * @param  ft_pid Parametry PID siły, parametry PID momentu
    * @param  adj_sign Sterowanie uruchamianiem/zatrzymywaniem adaptacyjnym, 0-wyłącz, 1-włącz
    * @param  ILC_sign Sterowanie uruchamianiem/zatrzymywaniem ILC, 0-zatrzymaj, 1-trening, 2-praktyka
    * @param  max_dis Maksymalna odległość regulacji, jednostka mm
    * @param  max_ang Maksymalny kąt regulacji, jednostka deg
    * @param  M Parametry masy rx, ry [0.1-10], domyślnie 2
    * @param  B Parametry tłumienia rx, ry [0.1-50], domyślnie 8
    * @param  threshold Próg uruchomienia rx, ry [0-10], domyślnie 0.2
    * @param  adjustCoeff Współczynnik regulacji momentu rx, ry [0-1], domyślnie 1
    * @param  polishRadio Promień szlifowania, jednostka mm
    * @param  filter_Sign Flaga włączenia filtracji 0-wył.; 1-wł., domyślnie wył.
    * @param  posAdapt_sign Flaga włączenia dostosowania postawy 0-wył.; 1-wł., domyślnie wył.
    * @param  isNoBlock Flaga blokowania, 0-blokuj; 1-nie blokuj
    * @return  Kod błędu
    */
    public int FT_Control(int flag, int sensor_id, int[] select, ForceTorque ft, double[] ft_pid, int adj_sign, int ILC_sign, double max_dis, double max_ang,double[] M,double[] B, double[] threshold, double[] adjustCoeff, double polishRadio,int filter_Sign, int posAdapt_sign, int isNoBlock)

Przykład kodu sterowania stałą siłą z tłumieniem
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestFTControlWithAdjustCoeff(Robot robot)
    {
        int sensor_id = 10;
        int[] select = { 0,0,1,0,0,0 };
        double[] ft_pid = { 0.0008, 0.0, 0.0, 0.0, 0.0, 0.0 };
        int adj_sign = 0;
        int ILC_sign = 0;
        double max_dis = 1000.0;
        double max_ang = 20;
        ForceTorque ft = new ForceTorque(0.0,0,0,0,0,0);
        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);
        JointPos j1=new JointPos(80.765, -98.795, 106.548, -97.734, -89.999, 94.842);
        JointPos j2=new JointPos(43.067, -84.429, 92.620, -98.175, -90.011, 57.144);
        DescPose desc_p1=new DescPose(5.009, -547.463, 262.053, -179.999, -0.019, 75.923);
        DescPose desc_p2=new DescPose(-347.966, -547.463, 262.048, -180.000, -0.019, 75.923);
        DescPose offset_pos=new DescPose(0, 0, 0, 0, 0, 0);
        double[] M = { 2.0, 2.0 };
        double[] B = { 15.0, 15.0 };
        double[] threshold = {1.0, 1.0};
        double[] adjustCoeff = {1.0, 0.8};
        double polishRadio = 0.0;
        int filter_Sign = 0;
        int posAdapt_sign = 1;
        int isNoBlock;
        ft.fz = -10.0;
        while(true)
        {
            int rtn = robot.FT_Control(1, sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, M, B, threshold, adjustCoeff, 0, 0, 1, 0);
            System.out.printf("FT_Control start rtn is %d\n", rtn);
            robot.MoveL(j1, desc_p1, 1, 0, 100.0, 100.0, 100.0, -1.0, 0, epos, 0, 0, offset_pos, 0,0, 0,10);
            robot.MoveL(j2, desc_p2, 1, 0, 100.0, 100.0, 100.0, -1.0, 0, epos, 0, 0, offset_pos, 0,0, 0,10);
            rtn = robot.FT_Control(0, sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, M, B, threshold, adjustCoeff, 0, 0, 1, 0);
            System.out.printf("FT_Control end rtn is %d\n", rtn);
        }
    }

Wstawianie obrotowe
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Wstawianie obrotowe
    * @param rcs Układ odniesienia, 0-układ współrzędnych narzędzia, 1-układ współrzędnych bazowych
    * @param angVelRot Prędkość kątowa obrotu, jednostka deg/s
    * @param ft  Próg siły/momentu, fx, fy, fz, tx, ty, tz, zakres [0~100]
    * @param max_angle Maksymalny kąt obrotu, jednostka deg
    * @param orn Kierunek siły/momentu, 1-wzdłuż osi Z, 2-wokół osi Z
    * @param max_angAcc Maksymalne przyspieszenie kątowe obrotu, jednostka deg/s^2, tymczasowo nieużywane, domyślnie 0
    * @param rotorn  Kierunek obrotu, 1-zgodnie z ruchem wskazówek zegara, 2-przeciwnie do ruchu wskazówek zegara
    * @param strategy Strategia postępowania w przypadku niewykrycia siły/momentu, 0-zgłoś błąd; 1-ostrzeżenie, kontynuuj ruch
    * @return  Kod błędu
    */
    public int FT_RotInsertion(int rcs, double angVelRot, double ft, double max_angle, int orn, double max_angAcc, int rotorn, int strategy)

Przykład kodu wstawiania obrotowego z czujnikiem siły robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestMove(Robot robot)
    {
        int rtn=-1;
        JointPos j1=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j2=new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
        JointPos j3=new JointPos(-29.777, -84.536, 109.275, -114.075, -86.655, 74.257);
        JointPos j4=new JointPos(-31.154, -95.317, 94.276, -88.079, -89.740, 74.256);
        DescPose desc_pos1=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_pos2=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose desc_pos3=new DescPose(-487.434, 154.362, 308.576, 176.600, 0.268, -14.061);
        DescPose desc_pos4=new DescPose(-443.165, 147.881, 480.951, 179.511, -0.775, -15.409);
        DescPose offset_pos=new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);
        int tool = 0;
        int user = 0;
        double vel = 100.0;
        double acc = 100.0;
        double ovl = 100.0;
        double oacc = 100.0;
        double blendT = 0.0;
        double blendR = 0.0;
        int flag = 0;
        int search = 0;
        int blendMode = 0;
        int velAccMode = 0;
        robot.SetSpeed(20);
        rtn = robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        System.out.printf("movej errcode:%d\n", rtn);
        rtn = robot.MoveL(j2, desc_pos2, tool, user, vel, acc, ovl, blendR, blendMode, epos, search, flag, offset_pos, oacc, velAccMode,0,10);
        System.out.printf("movel errcode:%d\n", rtn);
        rtn = robot.MoveC(j3, desc_pos3, tool, user, vel, acc, epos, flag, offset_pos, j4, desc_pos4, tool, user, vel, acc, epos, flag, offset_pos, ovl, blendR, oacc, velAccMode);
        System.out.printf("movec errcode:%d\n", rtn);
        rtn = robot.MoveJ(j2, desc_pos2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        System.out.printf("movej errcode:%d\n", rtn);
        rtn = robot.Circle(j3, desc_pos3, tool, user, vel, acc, epos, j1, desc_pos1, tool, user, vel, acc, epos, ovl, flag, offset_pos, oacc, -1, velAccMode);
        System.out.printf("circle errcode:%d\n", rtn);
        rtn = robot.MoveCart(desc_pos4, tool, user, vel, acc, ovl, blendT, -1);
        System.out.printf("MoveCart errcode:%d\n", rtn);
        rtn = robot.MoveJ(j1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        System.out.printf("movej errcode:%d\n", rtn);
        rtn = robot.MoveL(desc_pos2, tool, user, vel, acc, ovl, blendR, blendMode, epos, search, flag, offset_pos, -1, velAccMode,0,10);
        System.out.printf("movel errcode:%d\n", rtn);
        rtn = robot.MoveC(desc_pos3, tool, user, vel, acc, epos, flag, offset_pos, desc_pos4, tool, user, vel, acc, epos, flag, offset_pos, ovl, blendR, -1, velAccMode);
        System.out.printf("movec errcode:%d\n", rtn);
        rtn = robot.MoveJ(j2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        System.out.printf("movej errcode:%d\n", rtn);
        rtn = robot.Circle(desc_pos3, tool, user, vel, acc, epos, desc_pos1, tool, user, vel, acc, epos, ovl, flag, offset_pos, oacc, blendR, -1, velAccMode);
        System.out.printf("circle errcode:%d\n", rtn);
        return 0;
    }

Włączenie sterowania podatnego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Włączenie sterowania podatnego
    * @param  [in] p Współczynnik regulacji pozycji lub współczynnik podatności
    * @param  [in] force Próg siły włączenia podatności, jednostka N
    * @return  Kod błędu
    */
    int FT_ComplianceStart(double p, double force);

Wyłączenie sterowania podatnego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Wyłączenie sterowania podatnego
    * @return  Kod błędu
    */
    int FT_ComplianceStop();

Przykład kodu sterowania podatnego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestCompliance(Robot robot)
    {
        DescTran tr1=new DescTran(0,0,0);
        robot.SetForceSensorPayload(0);
        robot.SetForceSensorPayloadCog(tr1);

        int company = 24;
        int device = 0;
        int softversion = 0;
        int bus = 1;
        int index = 1;

        DeviceConfig con=new DeviceConfig(company, device, softversion, bus);
        robot.FT_SetConfig(con);
        robot.Sleep(1000);
        robot.FT_GetConfig(con);

        robot.Sleep(1000);

        robot.FT_Activate(0);
        robot.Sleep(1000);
        robot.FT_Activate(1);
        robot.Sleep(1000);

        robot.Sleep(1000);
        robot.FT_SetZero(0);
        robot.Sleep(1000);

        int flag = 1;
        int sensor_id = 1;
        Object[] select =new Object[] { 1,1,1,0,0,0 };
        Object[] ft_pid =new Object[] { 0.0005,0.0,0.0,0.0,0.0,0.0 };
        int adj_sign = 0;
        int ILC_sign = 0;
        double max_dis = 100.0;
        double max_ang = 0.0;

        ForceTorque ft=new ForceTorque(0,0,0,0,0,0);
        DescPose  offset_pos=new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);


        JointPos j1=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j2=new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
        DescPose desc_p1=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_p2=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);

        ft.fx = -10.0;
        ft.fy = -10.0;
        ft.fz = -10.0;
        robot.FT_Control(flag, sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
        double p = 0.00005;
        double force = 30.0;
        int rtn = robot.FT_ComplianceStart(p, force);

        int count = 15;
        while (count>0)
        {
            robot.MoveL(j1, desc_p1, 0, 0, 100.0, 180.0, 100.0, -1.0,0, epos, 0, 1, offset_pos,0,10);
            robot.MoveL(j2, desc_p2, 0, 0, 100.0, 180.0, 100.0, -1.0,0, epos, 0, 0, offset_pos,0,10);
            count -= 1;
        }
        robot.FT_ComplianceStop();
        flag = 0;
        robot.FT_Control(flag, sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);

        robot.CloseRPC();
        return 0;
    }

Inicjalizacja filtracji dynamicznej identyfikacji obciążenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Inicjalizacja filtracji dynamicznej identyfikacji obciążenia
    * @return Kod błędu
    */
    int LoadIdentifyDynFilterInit();

Inicjalizacja zmiennych dynamicznych identyfikacji obciążenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Inicjalizacja zmiennych dynamicznych identyfikacji obciążenia
    * @return Kod błędu
    */
    int LoadIdentifyDynVarInit();

Program główny identyfikacji obciążenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Program główny identyfikacji obciążenia
    * @param [in] joint_torque Moment stawów
    * @param [in] joint_pos Pozycja stawów
    * @param [in] t Okres próbkowania
    * @return Kod błędu
    */
    int LoadIdentifyMain(Object[] joint_torque, Object[] joint_pos, double t);

Pobieranie wyniku identyfikacji obciążenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera wynik identyfikacji obciążenia
    * @param [in] gain
    * @return List[0]:kod błędu; List[1] : double weight masa obciążenia; List[2]: x środek ciężkości obciążenia X mm; List[3] : y środek ciężkości obciążenia Y mm; List[2]: z środek ciężkości obciążenia Z mm
    */
    List<Number> LoadIdentifyGetResult(Object[] gain);

Przykład kodu identyfikacji obciążenia robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestIdentify(Robot robot)
    {
        int retval = 0;

        retval = robot.LoadIdentifyDynFilterInit();

        retval = robot.LoadIdentifyDynVarInit();

        JointPos posJ = new JointPos(0,0,0,0,0,0);
        DescPose posDec = new DescPose(0,0,0,0,0,0);
        List<Number> joint_toq=new ArrayList<>();
        robot.GetActualJointPosDegree( posJ);
        posJ.J2 = posJ.J2 + 10;
        joint_toq=robot.GetJointTorques(0);

        Object[] gain =new Object[] { 0,0.05,0,0,0,0,0,0.02,0,0,0,0 };
        double weight = 0;
        DescTran load_pos=new DescTran(0,0,0);
        List<Number> num=new ArrayList<>();
        num = robot.LoadIdentifyGetResult(gain);

        robot.CloseRPC();
        return 0;

    }

Wspomaganie przeciągania przez czujnik siły
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-v1.0.6-3.8.3

.. code-block:: Java
    :linenos:

    /**
    * @brief Wspomaganie przeciągania przez czujnik siły
    * @param [in] status Stan sterowania, 0-wyłączone; 1-włączone
    * @param [in] asaptiveFlag Flaga włączenia adaptacji, 0-wyłączona; 1-włączona
    * @param [in] interfereDragFlag Flaga przeciągania w obszarze interferencji, 0-wyłączona; 1-włączona
    * @param [in] ingularityConstraintsFlag Strategia punktów osobliwych, 0-omijanie; 1-przechodzenie
    * @param [in] forceCollisionFlag Flaga wykrywania kolizji robota podczas wspomaganego przeciągania; 0-wyłączona; 1-włączona
    * @param [in] M Współczynnik bezwładności
    * @param [in] B Współczynnik tłumienia
    * @param [in] K Współczynnik sztywności
    * @param [in] F Próg sześcioosiowej siły przeciągania
    * @param [in] Fmax Maksymalne ograniczenie siły przeciągania Nm
    * @param [in] Vmax Maksymalne ograniczenie prędkości stawów °/s
    * @return Kod błędu
    */
    int EndForceDragControl(int status, int asaptiveFlag, int interfereDragFlag,int ingularityConstraintsFlag, int forceCollisionFlag, Object[] M, Object[] B, Object[] K, Object[] F, double Fmax, double Vmax)

Pobieranie stanu przełącznika przeciągania dla czujnika siły
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera stan przełącznika przeciągania dla czujnika siły
    * @return List[0]:kod błędu; List[1] : dragState Stan sterowania wspomaganiem przeciągania przez czujnik siły, 0-wyłączone; 1-włączone; List[1] : sixDimensionalDragState Stan sterowania wspomaganiem przeciągania przez siłę sześcioosiową, 0-wyłączone; 1-włączone
    */
    List<Integer> GetForceAndTorqueDragState();

Automatyczne włączanie czujnika siły po wyczyszczeniu błędu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Automatyczne włączanie czujnika siły po wyczyszczeniu błędu
    * @param [in] status Stan sterowania, 0-wyłączone; 1-włączone
    * @return Kod błędu
    */
    int SetForceSensorDragAutoFlag(int status)

Przykład kodu wspomagania przeciągania przez czujnik siły
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestEndForceDragCtrl(Robot robot)
    {
        DescTran tr1=new DescTran(0,0,0);
        robot.SetForceSensorPayload(0);
        robot.SetForceSensorPayloadCog(tr1);

        robot.SetForceSensorDragAutoFlag(1);

        Object[] M =new Object[] { 15.0, 15.0, 15.0, 0.5, 0.5, 0.1 };
        Object[] B =new Object[] { 150.0, 150.0, 150.0, 5.0, 5.0, 1.0 };
        Object[] K =new Object[] { 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 };
        Object[] F =new Object[] { 10.0, 10.0, 10.0, 1.0, 1.0, 1.0 };
        robot.EndForceDragControl(1, 0, 0, 0, M, B, K, F, 50, 100);

        robot.Sleep(10000);

        int dragState = 0;
        int sixDimensionalDragState = 0;
        List<Integer> state=new ArrayList<>();
        state=robot.GetForceAndTorqueDragState();

        robot.EndForceDragControl(0, 0, 0, 0, M, B, K, F, 50, 100);
        return 0;
    }

Ustawianie przełącznika i parametrów mieszanego przeciągania z wykorzystaniem siły sześcioosiowej i impedancji stawów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia przełącznik i parametry mieszanego przeciągania z wykorzystaniem siły sześcioosiowej i impedancji stawów
    * @param [in] status Stan sterowania, 0-wyłączone; 1-włączone
    * @param [in] impedanceFlag Flaga włączenia impedancji, 0-wyłączona; 1-włączona
    * @param [in] lamdeGain Wzmocnienie przeciągania
    * @param [in] KGain Wzmocnienie sztywności
    * @param [in] BGain Wzmocnienie tłumienia
    * @param [in] dragMaxTcpVel Maksymalne ograniczenie prędkości liniowej końcówki podczas przeciągania
    * @param [in] dragMaxTcpOriVel Maksymalne ograniczenie prędkości kątowej końcówki podczas przeciągania
    * @return Kod błędu
    */
    int ForceAndJointImpedanceStartStop(int status, int impedanceFlag, Object[] lamdeGain, Object[] KGain, Object[] BGain, double dragMaxTcpVel, double dragMaxTcpOriVel);

Przykład kodu mieszanego przeciągania z wykorzystaniem siły sześcioosiowej i impedancji stawów
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestForceAndJointImpedance(Robot robot)
    {
        robot.DragTeachSwitch(1);
        Object[] lamdeDain =new Object[] { 3.0, 2.0, 2.0, 2.0, 2.0, 3.0 };
        Object[] KGain = new Object[]{ 0, 0, 0, 0, 0, 0 };
        Object[] BGain =new Object[] { 150, 150, 150, 5.0, 5.0, 1.0 };
        int rtn = robot.ForceAndJointImpedanceStartStop(1, 0, lamdeDain, KGain, BGain, 1000.0, 180.0);

        robot.Sleep(10000);

        robot.DragTeachSwitch(0);
        rtn = robot.ForceAndJointImpedanceStartStop(0, 0, lamdeDain, KGain, BGain, 1000.0, 180.0);

        robot.CloseRPC();
        return 0;
    }

Sterowanie uruchamianiem/zatrzymywaniem impedancji
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Sterowanie uruchamianiem/zatrzymywaniem impedancji
    * @param [in] status 0: wyłączone; 1: włączone
    * @param [in] workSpace 0-przestrzeń stawów; 1-przestrzeń kartezjańska
    * @param [in] forceThreshold Próg siły wyzwalającej (N)
    * @param [in] m Parametr masy
    * @param [in] b Parametr tłumienia
    * @param [in] k Parametr sztywności
    * @param [in] maxV Maksymalna prędkość liniowa (mm/s)
    * @param [in] maxVA Maksymalne przyspieszenie liniowe (mm/s2)
    * @param [in] maxW Maksymalna prędkość kątowa (°/s)
    * @param [in] maxWA Maksymalne przyspieszenie kątowe (°/s2)
    * @return Kod błędu
    */
    public int ImpedanceControlStartStop(int status, int workSpace, double[] forceThreshold, double[] m, double[] b, double[] k, double maxV, double maxVA, double maxW, double maxWA)

Przykład kodu sterowania uruchamianiem/zatrzymywaniem impedancji robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestImpedanceControl(Robot robot)
    {
        JointPos j1=new JointPos(102.622, -135.990, 120.769, -73.950, -90.848, 35.507);
        JointPos j2=new JointPos(93.674, -80.062, 82.947, -92.199, -90.967, 26.559);
        DescPose desc_pos1=new DescPose(136.552, -149.799, 449.532, 179.817, -1.172, 157.123);
        DescPose desc_pos2=new DescPose(136.540, -561.048, 449.542, 179.819, -1.172, 157.122);
        DescPose offset_pos=new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);
        int tool = 0;
        int user = 0;
        double vel = 100.0;
        double acc = 200.0;
        double ovl = 100.0;
        double blendT = -1.0;
        double blendR = -1.0;
        int flag = 0;
        int search = 0;
        robot.SetSpeed(20);
        int company = 17;
        int device = 0;
        int softversion = 0;
        int bus = 1;
        DeviceConfig con=new DeviceConfig(company, device, softversion, bus);
        robot.FT_SetConfig(con);
        robot.Sleep(1000);
        robot.FT_GetConfig(con);
        System.out.println("FT config:"+con.company+","+con.device+","+con.softwareVersion+"con"+ con.bus);
        robot.Sleep(1000);
        robot.FT_Activate(0);
        robot.Sleep(1000);
        robot.FT_Activate(1);
        robot.Sleep(1000);
        robot.Sleep(1000);
        robot.FT_SetZero(0);
        robot.Sleep(1000);
        robot.FT_SetZero(1);
        robot.Sleep(1000);
        double[] forceThreshold = { 30,30,30,5,5,5 };
        double[] m= { 0.1,0.1,0.1,0.02,0.02,0.02 };
        double[] b = { 1,1,1,0.08,0.08,0.08 };
        double[] k = { 0,0,0,0,0,0 };
        int rtn = robot.ImpedanceControlStartStop(1, 1, forceThreshold, m, b, k, 1000, 500, 100, 100);
        System.out.println("ImpedanceControlStartStop errcode:"+ rtn);
        rtn = robot.MoveL(desc_pos1, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1,0,-1, 1);
        rtn = robot.MoveL(desc_pos2, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1,0,-1, 1);
        rtn = robot.MoveL(desc_pos1, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1,0,-1, 1);
        rtn = robot.MoveL(desc_pos2, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1,0,-1, 1);
        rtn = robot.MoveL(desc_pos1, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1,0,-1, 1);
        rtn = robot.MoveL(desc_pos2, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1,0,-1, 1);
        System.out.println("movel errcode:"+ rtn);
        robot.ImpedanceControlStartStop(0, 1, forceThreshold, m, b, k, 1000, 500, 100, 100);
        robot.CloseRPC();
        return 0;
    }

Włączanie funkcji kompensacji momentu i współczynnik kompensacji
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Włączanie funkcji kompensacji momentu i współczynnik kompensacji
    * @param status Przełącznik, 0-wyłączone; 1-włączone
    * @param torqueCoeff Współczynniki kompensacji momentu dla J1-J6 [0-1]
    * @return Kod błędu
    */
    public int SetCoderCompenParams(int status, double[] torqueCoeff)