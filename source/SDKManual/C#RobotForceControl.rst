Sterowanie siłą robota
======================

.. toctree:: 
    :maxdepth: 5

Konfiguracja czujnika siły
+++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Konfiguruje czujnik siły
    * @param  [in] company  Producent czujnika siły, 17-Kunwei Technology
    * @param  [in] device  Numer urządzenia, tymczasowo nieużywane, domyślnie 0
    * @param  [in] softvesion  Numer wersji oprogramowania, tymczasowo nieużywane, domyślnie 0
    * @param  [in] bus Pozycja magistrali, na której zawieszono urządzenie, tymczasowo nieużywane, domyślnie 0
    * @return  Kod błędu
    */
    int FT_SetConfig(int company, int device, int softvesion, int bus); 

Pobranie konfiguracji czujnika siły 
++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Pobiera konfigurację czujnika siły 
    * @param [out] deviceID Numer czujnika siły 
    * @param [out] company Producent czujnika siły, 17-Kunwei Technology, 19-Chińskie Akademia Technologii Kosmicznych, 20-ATI sensor, 21-Zhongke Midian, 22-Weihang Minxin
    * @param [out] device  Numer urządzenia, Kunwei(0-KWR75B), Chińska Akademia Technologii Kosmicznych(0-MCS6A-200-4), ATI(0-AXIA80-M8), Zhongke Midian(0-MST2010), Weihang Minxin(0-WHC6L-YB-10A) 
    * @param [out] softvesion Numer wersji oprogramowania, tymczasowo nieużywane, domyślnie 0 
    * @return Kod błędu 
    */ 
    int FT_GetConfig(ref int deviceID, ref int company, ref int device, ref int softvesion); 

Aktywacja czujnika siły
++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Aktywacja czujnika siły
    * @param  [in] act  0-reset, 1-aktywacja
    * @return  Kod błędu
    */
    int FT_Activate(byte act); 

Zerowanie czujnika siły
++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Zerowanie czujnika siły
    * @param  [in] act  0-usunięcie zera, 1-korekta zera
    * @return  Kod błędu
    */
    int FT_SetZero(byte act); 

Ustawienie odniesienia układu współrzędnych czujnika siły
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ustawia odniesienie układu współrzędnych czujnika siły
    * @param  [in] ref  0-układ współrzędnych narzędzia, 1-układ współrzędnych podstawy
    * @return  Kod błędu
    */
    int FT_SetRCS(byte type); 

Ustawienie masy ładunku pod czujnikiem siły
+++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief  Ustawia masę ładunku pod czujnikiem siły
    * @param  [in] weight Masa ładunku, kg
    * @return  Kod błędu
    */
    int SetForceSensorPayLoad(double weight);

Ustawienie środka ciężkości ładunku pod czujnikiem siły
+++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief  Ustawia środek ciężkości ładunku pod czujnikiem siły
    * @param  [in] x Środek ciężkości ładunku x, mm 
    * @param  [in] y Środek ciężkości ładunku y, mm
    * @param  [in] z Środek ciężkości ładunku z, mm
    * @return  Kod błędu
    */
    int SetForceSensorPayLoadCog(double x, double y, double z);

Pobranie masy ładunku pod czujnikiem siły
+++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera masę ładunku pod czujnikiem siły
    * @param  [in] weight Masa ładunku, kg
    * @return  Kod błędu
    */
    int GetForceSensorPayLoad(ref double weight);

Pobranie środka ciężkości ładunku pod czujnikiem siły
+++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera środek ciężkości ładunku pod czujnikiem siły
    * @param  [out] x Środek ciężkości ładunku x, mm 
    * @param  [out] y Środek ciężkości ładunku y, mm
    * @param  [out] z Środek ciężkości ładunku z, mm
    * @return  Kod błędu
    */
    int GetForceSensorPayLoadCog(ref double x, ref double y, ref double z);

Automatyczne zerowanie czujnika siły
++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief  Automatyczne zerowanie czujnika siły
    * @param  [out] weight Masa czujnika, kg 
    * @param  [out] pos Środek ciężkości czujnika, mm
    * @return  Kod błędu
    */
    int ForceSensorAutoComputeLoad(ref double weight, ref DescTran pos);

Pobranie danych siły/momentu w odniesieniu do układu współrzędnych
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera dane siły/momentu w odniesieniu do układu współrzędnych
    * @param  [out] ft  Siła/moment, fx, fy, fz, tx, ty, tz
    * @return  Kod błędu
    */   
    int FT_GetForceTorqueRCS(byte flag, ref ForceTorque ft); 

Pobranie surowych danych siły/momentu czujnika siły
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera surowe dane siły/momentu czujnika siły
    * @param  [out] ft  Siła/moment, fx, fy, fz, tx, ty, tz
    * @return  Kod błędu
    */   
    int FT_GetForceTorqueOrigin(byte flag, ref ForceTorque ft); 

Przykład kodu konfiguracji czujnika siły i automatycznego zerowania
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button54_Click(object sender, EventArgs e)
    {
        int company = 24;
        int device = 0;
        int softversion = 0;
        int bus = 1;
        int index = 1;

        robot.FT_SetConfig(company, device, softversion, bus);
        Thread.Sleep(1000);
        robot.FT_GetConfig(ref company, ref device, ref softversion, ref bus);
        Console.WriteLine($"FT config:{company},{device},{softversion},{bus}");
        Thread.Sleep(1000);

        robot.FT_Activate(0);
        Thread.Sleep(1000);
        robot.FT_Activate(1);
        Thread.Sleep(1000);

        Thread.Sleep(1000);
        robot.FT_SetZero(0);
        Thread.Sleep(1000);

        ForceTorque ft = new ForceTorque(0, 0, 0, 0, 0, 0);
        robot.FT_GetForceTorqueOrigin(0, ref ft);
        Console.WriteLine($"ft origin:{ft.fx},{ft.fy},{ft.fz},{ft.tx},{ft.ty},{ft.tz}");
        robot.FT_SetZero(1);
        Thread.Sleep(1000);

        DescPose ftCoord = new DescPose(0, 0, 0, 0, 0, 0);
        robot.FT_SetRCS(0, ftCoord);

        robot.SetForceSensorPayLoad(0.824);
        robot.SetForceSensorPayLoadCog(0.778, 2.554, 48.765);
        double weight = 0;
        double x = 0, y = 0, z = 0;
        robot.GetForceSensorPayLoad(ref weight);
        robot.GetForceSensorPayLoadCog(ref x, ref y, ref z);
        Console.WriteLine($"the FT load is {weight}, {x} {y} {z}");

        robot.SetForceSensorPayLoad(0);
        robot.SetForceSensorPayLoadCog(0, 0, 0);

        double computeWeight = 0;
        DescTran tran = new DescTran(0, 0, 0);
        robot.ForceSensorAutoComputeLoad(ref weight, ref tran);
        Console.WriteLine($"the result is weight {weight} pos is {tran.x} {tran.y} {tran.z}");

    } 

Rejestracja identyfikacji masy ładunku
++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Rejestracja identyfikacji masy ładunku
    * @param  [in] id  Numer układu współrzędnych czujnika, zakres [1~14]
    * @return  Kod błędu
    */
    int FT_PdIdenRecord(int id);

Obliczenie identyfikacji masy ładunku
+++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obliczenie identyfikacji masy ładunku
    * @param  [out] weight  Masa ładunku, jednostka kg
    * @return  Kod błędu
    */   
    int FT_PdIdenCompute(ref double weight);

Rejestracja identyfikacji środka ciężkości ładunku
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Rejestracja identyfikacji środka ciężkości ładunku
    * @param  [in] id  Numer układu współrzędnych czujnika, zakres [1~14]
    * @param  [in] index Numer punktu, zakres [1~3]
    * @return  Kod błędu
    */
    int FT_PdCogIdenRecord(int id, int index); 

Obliczenie identyfikacji środka ciężkości ładunku
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obliczenie identyfikacji środka ciężkości ładunku
    * @param  [out] cog  Środek ciężkości ładunku, jednostka mm
    * @return  Kod błędu
    */   
    int FT_PdCogIdenCompute(ref DescTran cog);

Przykład kodu identyfikacji obciążenia czujnika siły
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnFTPdCog_Click(object sender, EventArgs e)
    {
        int company = 24, device = 0, softversion = 0, bus = 1;

        robot.FT_SetConfig(company, device, softversion, bus);
        Thread.Sleep(1000);
        robot.FT_GetConfig(ref company, ref device, ref softversion, ref bus);
        Console.WriteLine($"FT config: {company}, {device}, {softversion}, {bus}");
        Thread.Sleep(1000);

        robot.FT_Activate(0);
        Thread.Sleep(1000);
        robot.FT_Activate(1);
        Thread.Sleep(1000);

        Thread.Sleep(1000);
        robot.FT_SetZero(0);
        Thread.Sleep(1000);

        ForceTorque ft = new ForceTorque(0,0,0,0,0,0);
        robot.FT_GetForceTorqueOrigin(0, ref ft);
        Console.WriteLine($"ft origin: {ft.fx}, {ft.fy}, {ft.fz}, {ft.tx}, {ft.ty}, {ft.tz}");
        robot.FT_SetZero(1);
        Thread.Sleep(1000);

        DescPose tcoord = new DescPose(0, 0, 35.0, 0, 0, 0);
        robot.SetToolCoord(10, tcoord, 1, 0, 0, 0);

        robot.FT_PdIdenRecord(10);
        Thread.Sleep(1000);

        double weight = 0.0f;
        robot.FT_PdIdenCompute(ref weight);
        Console.WriteLine($"payload weight: {weight}");

        DescPose desc_p1 = new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_p2 = new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose desc_p3 = new DescPose(-327.622, 402.230, 320.402, -178.067, 2.127, -46.207);

        robot.MoveCart( desc_p1, 0, 0, 100.0f, 100.0f, 100.0f, -1.0f, -1);
        Thread.Sleep(1000);
        robot.FT_PdCogIdenRecord(10, 1);
        robot.MoveCart( desc_p2, 0, 0, 100.0f, 100.0f, 100.0f, -1.0f, -1);
        Thread.Sleep(1000);
        robot.FT_PdCogIdenRecord(10, 2);
        robot.MoveCart( desc_p3, 0, 0, 100.0f, 100.0f, 100.0f, -1.0f, -1);
        Thread.Sleep(1000);
        robot.FT_PdCogIdenRecord(10, 3);

        DescTran cog = new DescTran(0,0,0);
        robot.FT_PdCogIdenCompute(ref cog);
        Console.WriteLine($"cog: {cog.x}, {cog.y}, {cog.z}");
    }

Ochrona przed kolizją
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ochrona przed kolizją
    * @param  [in] flag 0-wyłącz ochronę przed kolizją, 1-włącz ochronę przed kolizją
    * @param  [in] sensor_id Numer czujnika siły
    * @param  [in] select  Wybór, czy sześć stopni swobody ma wykrywać kolizję, 0-nie wykrywa, 1-wykrywa
    * @param  [in] ft  Siła/moment kolizji, fx, fy, fz, tx, ty, tz
    * @param  [in] max_threshold Maksymalny próg
    * @param  [in] min_threshold Minimalny próg
    * @note   Zakres wykrywania siły/momentu: (ft - min_threshold, ft + max_threshold)
    * @return  Kod błędu
    */   
    int FT_Guard(int flag, int sensor_id, int[] select, ForceTorque ft, double[] max_threshold, double[] min_threshold); 

Przykład kodu ochrony przed kolizją
++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnFTGuard_Click(object sender, EventArgs e)
    {
        int company = 24, device = 0, softversion = 0, bus = 1;

        robot.FT_SetConfig(company, device, softversion, bus);
        Thread.Sleep(1000);
        robot.FT_GetConfig(ref company, ref device, ref softversion, ref bus);
        Console.WriteLine($"FT config: {company}, {device}, {softversion}, {bus}");
        Thread.Sleep(1000);

        robot.FT_Activate(0);
        Thread.Sleep(1000);
        robot.FT_Activate(1);
        Thread.Sleep(1000);

        Thread.Sleep(1000);
        robot.FT_SetZero(0);
        Thread.Sleep(1000);

        byte sensor_id = 1;
        int[] select = { 1, 1, 1, 1, 1, 1 };
        double[] max_threshold = { 10.0f, 10.0f, 10.0f, 10.0f, 10.0f, 10.0f };
        double[] min_threshold = { 5.0f, 5.0f, 5.0f, 5.0f, 5.0f, 5.0f };

        ForceTorque ft = new ForceTorque();
        DescPose desc_p1 = new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_p2 = new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose desc_p3 = new DescPose(-327.622, 402.230, 320.402, -178.067, 2.127, -46.207);

        robot.FT_Guard(1, sensor_id, select,  ft, max_threshold, min_threshold);
        robot.MoveCart( desc_p1, 0, 0, 100.0f, 100.0f, 100.0f, -1.0f, -1);
        robot.MoveCart( desc_p2, 0, 0, 100.0f, 100.0f, 100.0f, -1.0f, -1);
        robot.MoveCart( desc_p3, 0, 0, 100.0f, 100.0f, 100.0f, -1.0f, -1);

        robot.FT_Guard(0, sensor_id, select, ft, max_threshold, min_threshold);
    }

Sterowanie stałą siłą
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7
    
.. code-block:: c#
    :linenos:

    /**
    * @brief  Sterowanie stałą siłą
    * @param  [in] flag 0-wyłącz sterowanie stałą siłą, 1-włącz sterowanie stałą siłą
    * @param  [in] sensor_id Numer czujnika siły
    * @param  [in] select  Wybór, czy sześć stopni swobody ma wykrywać kolizję, 0-nie wykrywa, 1-wykrywa
    * @param  [in] ft  Siła/moment kolizji, fx, fy, fz, tx, ty, tz
    * @param  [in] ft_pid Parametry pid siły, parametry pid momentu
    * @param  [in] adj_sign Sterowanie uruchamianiem/zatrzymywaniem adaptacji, 0-wyłączone, 1-włączone
    * @param  [in] ILC_sign Sterowanie uruchamianiem/zatrzymywaniem ILC, 0-zatrzymaj, 1-trening, 2-praktyka
    * @param  [in] max_dis Maksymalna odległość regulacji, jednostka mm
    * @param  [in] max_ang Maksymalny kąt regulacji, jednostka deg
    * @param  [in] M Parametry masy rx, ry [0.1-10], domyślnie 2
    * @param  [in] B Parametry tłumienia rx, ry [0.1-50], domyślnie 8
    * @param  [in] threshold Próg uruchomienia rx, ry [0-10], domyślnie 0.2
    * @param  [in] adjustCoeff Współczynnik regulacji momentu rx, ry [0-1], domyślnie 1
    * @param  [in] polishRadio Promień szlifowania, jednostka mm
    * @param  [in] filter_Sign Znacznik włączenia filtrowania 0-wył.; 1-wł., domyślnie wyłączone
    * @param  [in] posAdapt_sign Znacznik włączenia zgodności orientacji 0-wył.; 1-wł., domyślnie wyłączone
    * @param  [in] isNoBlock Znacznik blokowania, 0-blokujące; 1-nieblokujące
    * @return  Kod błędu
    */
    public int FT_Control(byte flag, int sensor_id, byte[] select, ForceTorque ft, float[] ft_pid,byte adj_sign, byte ILC_sign, float max_dis, float max_ang,double[] M, double[] B, double[] threshold, double[] adjustCoeff,double polishRadio, int filter_Sign, int posAdapt_sign, int isNoBlock)

Przykład kodu sterowania stałą siłą z tłumieniem
++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7
    
.. code-block:: c#
    :linenos:

    public void TestFTControlWithAdjustCoeff()
    {
        int rtn;
        int sensor_id = 10;
        byte[] select = new byte[6] { 0, 0, 1, 0, 0, 0 };
        float[] ft_pid = new float[6] { 0.0008f, 0.0f, 0.0f, 0.0f, 0.0f, 0.0f };
        byte adj_sign = 0;
        byte ILC_sign = 0;
        float max_dis = 1000.0f;
        float max_ang = 20.0f;
        ForceTorque ft = new ForceTorque();
        ft.fz = -10.0f;
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        JointPos j1 = new JointPos(80.765f, -98.795f, 106.548f, -97.734f, -89.999f, 94.842f);
        JointPos j2 = new JointPos(43.067f, -84.429f, 92.620f, -98.175f, -90.011f, 57.144f);
        DescPose desc_p1 = new DescPose(5.009f, -547.463f, 262.053f, -179.999f, -0.019f, 75.923f);
        DescPose desc_p2 = new DescPose(-347.966f, -547.463f, 262.048f, -180.000f, -0.019f, 75.923f);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        double[] M = new double[2] { 2.0, 2.0 };
        double[] B = new double[2] { 15.0, 15.0 };
        double[] threshold = new double[2] { 1.0, 1.0 };
        double[] adjustCoeff = new double[2] { 1.0, 0.8 };
        double polishRadio = 0.0;
        int filter_Sign = 0;
        int posAdapt_sign = 1;
        int isNoBlock = 0;
        while (true)
        {
            rtn = robot.FT_Control(1, sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, M, B, threshold, adjustCoeff, 0, 0, 1, 0);
            Console.WriteLine($"FT_Control start rtn is {rtn}");
            robot.MoveL(j1, desc_p1, 1, 0, 100, 100, 100, -1, 0, epos, 0, 0, offset_pos, 0, 0, 10);
            robot.MoveL(j2, desc_p2, 1, 0, 100, 100, 100, -1, 0, epos, 0, 0, offset_pos, 0, 0, 10);
            rtn = robot.FT_Control(0, sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, M, B, threshold, adjustCoeff, 0, 0, 1, 0);
            Console.WriteLine($"FT_Control end rtn is {rtn}");
        }
    }

Wstawianie obrotowe
+++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Wstawianie obrotowe
    * @param [in] rcs Układ odniesienia, 0-układ współrzędnych narzędzia, 1-układ współrzędnych podstawy
    * @param [in] angVelRot Prędkość kątowa obrotu, jednostka deg/s
    * @param [in] ft Próg siły/momentu, fx, fy, fz, tx, ty, tz, zakres [0~100]
    * @param [in] max_angle Maksymalny kąt obrotu, jednostka deg
    * @param [in] orn Kierunek siły/momentu, 1-wzdłuż osi Z, 2-wokół osi Z
    * @param [in] max_angAcc Maksymalne przyspieszenie kątowe, jednostka deg/s², tymczasowo nieużywane, domyślnie 0
    * @param [in] rotorn Kierunek obrotu, 1-zgodnie z ruchem wskazówek zegara, 2-przeciwnie do ruchu wskazówek zegara
    * @param [in] strategy Strategia postępowania przy niewykryciu siły/momentu, 0-zgłoś błąd; 1-ostrzeżenie, kontynuuj ruch
    * @return Kod błędu
    */
    public int FT_RotInsertion(int rcs, double angVelRot, double ft, double max_angle, int orn, double max_angAcc, int rotorn, int strategy)

Wstawianie Liniowe
+++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief  Wstawianie liniowe
    * @param  [in] rcs Referencyjny układ współrzędnych, 0-układ narzędzia, 1-układ podstawy
    * @param  [in] ft  Próg siły/momentu obrotowego, fx,fy,fz,tx,ty,tz, zakres [0~100]
    * @param  [in] lin_v Prędkość liniowa, jednostka mm/s
    * @param  [in] lin_a Przyspieszenie liniowe, jednostka mm/s^2, tymczasowo nieużywane
    * @param  [in] max_dis Maksymalna odległość wstawiania, jednostka mm
    * @param  [in] linorn  Kierunek wstawiania, 0-kierunek ujemny, 1-kierunek dodatni
    * @return  Kod błędu
    */
    public int FT_LinInsertion(int rcs, float ft, float lin_v, float lin_a, float max_dis, byte linorn)

Przykład Kodu Wstawiania Rotacyjnego z Czujnikiem Siły
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    public void TestRotInsert()
    {
        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
        int rtn;

        float forceInsertion = 5.0f; // Próg siły lub momentu (0~100), jednostka N lub Nm
        int angleMax = 300; // Maksymalny kąt obrotu, jednostka °
        byte orn = 1; // Kierunek siły, 1-fz, 2-mz
        float angAccmax = 0; // Maksymalne przyspieszenie kątowe obrotu, jednostka °/s^2, tymczasowo nieużywane
        byte status = 1;  // Flaga włączenia sterowania stałą siłą, 0-wył., 1-wł.
        int sensor_num = 11; // Numer czujnika siły
        float[] gain = { 0.0001f, 0.0f, 0.0f, 0.0f, 0.0f, 0.0f };  // Próg maksymalny
        byte adj_sign = 0;  // Status start/stop adaptacyjny, 0-wył., 1-wł.
        byte ILC_sign = 0;  // Status start/stop sterowania ILC, 0-stop, 1-trening, 2-operacyjny
        float max_dis = 1000.0f;  // Maksymalna odległość regulacji
        float max_ang = 20.0f;  // Maksymalny kąt regulacji
        ForceTorque ft = new ForceTorque();
        int rcs = 0;  // Referencyjny układ współrzędnych, 0-układ narzędzia, 1-układ podstawy
        float angVelRot = 1.0f;  // Prędkość kątowa obrotu, jednostka °/s
        byte rotorn = 1; // Kierunek obrotu, 1-zgodnie z ruchem wskazówek zegara, 2-przeciwnie
        JointPos j1 = new JointPos(100.968, -108.678, 126.166, -106.630, -93.253, 19.584);
        DescPose desc_p1 = new DescPose(159.473, -316.570, 334.560, -179.718, -3.352, 171.400);
        ExaxisPos epos = new ExaxisPos(0.0f, 0.0f, 0.0f, 0.0f);
        DescPose offset_pos = new DescPose(0.0f, 0.0f, 0.0f, 0.0f, 0.0f, 0.0f);

        robot.MoveL(j1, desc_p1, 2, 0, 100.0f, 180.0f, 100.0f, -1.0f, 0, epos, (byte)0, (byte)1, offset_pos);

        byte[] select3 = { 0, 0, 1, 0, 0, 0 };
        ft.fz = -5.0f;
        gain[0] = 0.0001f;
        status = 1;
        robot.FT_Control(status, sensor_num, select3, ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
        rtn = robot.FT_LinInsertion(rcs, 10, 1, 1, 100, 1);
        Console.WriteLine("FT_LinInsertion rtn is " + rtn);
        robot.FT_Control(0, sensor_num, select3, ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);

        ft.fz = -30.0f;
        robot.FT_Control(1, sensor_num, select3, ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
        rtn = robot.FT_RotInsertion(rcs, angVelRot, forceInsertion, angleMax, orn, angAccmax, rotorn, 0);
        Console.WriteLine("FT_RotInsertion rtn is " + rtn);
        robot.FT_Control(0, sensor_num, select3, ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);

        rtn = robot.FT_LinInsertion(0, 40, 3, 0, 100, 1);
        Console.WriteLine("FT_LinInsertion retract rtn is " + rtn);

        Thread.Sleep(1000);
        robot.GetRobotRealTimeState(ref pkg);
        Console.WriteLine("robot errcode " + pkg.main_code + "  " + pkg.sub_code);
    }

Przykład kodu wstawiania obrotowego czujnika siły robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    public void TestMove()
    {
        int rtn;
        JointPos j1 = new JointPos(-11.904f, -99.669f, 117.473f, -108.616f, -91.726f, 74.256f);
        JointPos j2 = new JointPos(-45.615f, -106.172f, 124.296f, -107.151f, -91.282f, 74.255f);
        JointPos j3 = new JointPos(-29.777f, -84.536f, 109.275f, -114.075f, -86.655f, 74.257f);
        JointPos j4 = new JointPos(-31.154f, -95.317f, 94.276f, -88.079f, -89.740f, 74.256f);
        DescPose desc_pos1 = new DescPose(-419.524f, -13.000f, 351.569f, -178.118f, 0.314f, 3.833f);
        DescPose desc_pos2 = new DescPose(-321.222f, 185.189f, 335.520f, -179.030f, -1.284f, -29.869f);
        DescPose desc_pos3 = new DescPose(-487.434f, 154.362f, 308.576f, 176.600f, 0.268f, -14.061f);
        DescPose desc_pos4 = new DescPose(-443.165f, 147.881f, 480.951f, 179.511f, -0.775f, -15.409f);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        int tool = 0;
        int user = 0;
        float vel = 100.0f;
        float acc = 100.0f;
        float ovl = 100.0f;
        float oacc = 100.0f;
        float blendT = 0.0f;
        float blendR = 0.0f;
        byte flag = 0;
        byte search = 0;
        int blendMode = 0;
        int velAccMode = 0;
        robot.SetSpeed(20);
        rtn = robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        Console.WriteLine($"movej errcode:{rtn}");
        rtn = robot.MoveL(j2, desc_pos2, tool, user, vel, acc, ovl, blendR, blendMode, epos, search, flag, offset_pos, oacc, velAccMode,0,10);
        Console.WriteLine($"movel errcode:{rtn}");
        rtn = robot.MoveC(j3, desc_pos3, tool, user, vel, acc, epos, flag, offset_pos,j4, desc_pos4, tool, user, vel, acc, epos, flag, offset_pos, ovl, blendR, oacc, velAccMode);
        Console.WriteLine($"movec errcode:{rtn}");
        rtn = robot.MoveJ(j2, desc_pos2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        Console.WriteLine($"movej errcode:{rtn}");
        rtn = robot.Circle(j3, desc_pos3, tool, user, vel, acc, epos,j1, desc_pos1, tool, user, vel, acc, epos,ovl, flag, offset_pos, oacc, -1, velAccMode);
        Console.WriteLine($"circle errcode:{rtn}");
        rtn = robot.MoveCart(desc_pos4, tool, user, vel, acc, ovl, blendT, -1);
        Console.WriteLine($"MoveCart errcode:{rtn}");
        rtn = robot.MoveJ(j1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        Console.WriteLine($"movej errcode:{rtn}");
        rtn = robot.MoveL(desc_pos2, tool, user, vel, acc, ovl, blendR, blendMode, epos, search, flag, offset_pos, -1, velAccMode);
        Console.WriteLine($"movel errcode:{rtn}");
        rtn = robot.MoveC(desc_pos3, tool, user, vel, acc, epos, flag, offset_pos,desc_pos4, tool, user, vel, acc, epos, flag, offset_pos,ovl, blendR, -1, velAccMode);
        Console.WriteLine($"movec errcode:{rtn}");
        rtn = robot.MoveJ(j2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        Console.WriteLine($"movej errcode:{rtn}");
        rtn = robot.Circle(desc_pos3, tool, user, vel, acc, epos, desc_pos1, tool, user, vel, acc, epos,ovl, flag, offset_pos, oacc, blendR, -1, velAccMode);
        Console.WriteLine($"circle errcode:{rtn}");
    }

Rozpoczęcie sterowania podatnego
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Rozpoczęcie sterowania podatnego
    * @param  [in] p Współczynnik regulacji pozycji lub współczynnik podatności
    * @param  [in] force Próg siły włączenia podatności, jednostka N
    * @return  Kod błędu
    */   
    int FT_ComplianceStart(float p, float force);

Zatrzymanie sterowania podatnego
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Zatrzymanie sterowania podatnego
    * @return  Kod błędu
    */   
    int FT_ComplianceStop(); 

Przykład kodu sterowania podatnego
++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnComplience_Click(object sender, EventArgs e)
    {
        int company = 24, device = 0, softversion = 0, bus = 1;
        robot.FT_SetConfig(company, device, softversion, bus);
        Thread.Sleep(1000);
        robot.FT_GetConfig(ref company, ref device, ref softversion, ref bus);
        Console.WriteLine($"FT config: {company}, {device}, {softversion}, {bus}");
        Thread.Sleep(1000);

        robot.FT_Activate(0);
        Thread.Sleep(1000);
        robot.FT_Activate(1);
        Thread.Sleep(1000);

        robot.FT_SetZero(0);
        Thread.Sleep(1000);

        byte flag = 1;
        int sensor_id = 1;
        int[] select = { 1, 1, 1, 0, 0, 0 };
        double[] ft_pid = { 0.0005f, 0.0f, 0.0f, 0.0f, 0.0f, 0.0f };
        byte adj_sign = 0, ILC_sign = 0;
        float max_dis = 100.0f, max_ang = 0.0f;

        ForceTorque ft = new ForceTorque { fx = -10.0, fy = -10.0, fz = -10.0 };
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);

        JointPos j1 = new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j2 = new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
        DescPose desc_p1 = new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_p2 = new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);

        robot.FT_Control(flag, (byte)sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang);
        float p = 0.00005f;
        float force = 30.0f;
        int rtn = robot.FT_ComplianceStart(p, force);
        Console.WriteLine($"FT_ComplianceStart rtn is {rtn}");

        int count = 5;
        while (count-- > 0)
        {
        robot.MoveL(j1, desc_p1, 0, 0, 100.0f, 180.0f, 100.0f, -1.0f, epos, 0, 1, offset_pos);
        robot.MoveL(j2, desc_p2, 0, 0, 100.0f, 180.0f, 100.0f, -1.0f, epos, 0, 0, offset_pos);
        }

        robot.FT_ComplianceStop();
        Console.WriteLine($"FT_ComplianceStop rtn is {rtn}");

        flag = 0;
        robot.FT_Control(flag, (byte)sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang);
    }

Inicjalizacja filtra dynamicznego identyfikacji obciążenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Inicjalizacja filtra dynamicznego identyfikacji obciążenia
    * @return Kod błędu
    */
    int LoadIdentifyDynFilterInit();

Inicjalizacja zmiennych dynamicznych identyfikacji obciążenia
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Inicjalizacja zmiennych dynamicznych identyfikacji obciążenia
    * @return Kod błędu
    */
    int LoadIdentifyDynVarInit();

Główny program identyfikacji obciążenia
+++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Główny program identyfikacji obciążenia
    * @param [in] joint_torque Moment obrotowy stawu
    * @param [in] joint_pos Pozycja stawu
    * @param [in] t Okres próbkowania
    * @return Kod błędu
    */
    int LoadIdentifyMain(double[] joint_torque, double[] joint_pos, double t);

Pobranie wyniku identyfikacji obciążenia
++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Pobiera wynik identyfikacji obciążenia
    * @param [in] gain  Współczynnik członu grawitacyjnego double[6], współczynnik członu odśrodkowego double[6]
    * @param [out] weight Masa ładunku
    * @param [out] cog Środek ciężkości ładunku
    * @return Kod błędu
    */
    int LoadIdentifyGetResult(double[] gain, ref double weight, ref DescTran cog);

Przykład kodu identyfikacji obciążenia robota
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button74_Click(object sender, EventArgs e)
    {
        int rtn;
        int retval = 0;

        retval = robot.LoadIdentifyDynFilterInit();
        Console.WriteLine("LoadIdentifyDynFilterInit retval is: " + retval);

        retval = robot.LoadIdentifyDynVarInit();
        Console.WriteLine("LoadIdentifyDynVarInit retval is: " + retval);

        JointPos posJ = new JointPos(0,0,0,0,0,0);
        DescPose posDec = new DescPose(0, 0, 0, 0, 0, 0);
        double[] joint_toq = new double[6] { 0.0f, 0.0f, 0.0f, 0.0f, 0.0f, 0.0f };
        robot.GetActualJointPosDegree(0, ref posJ);
        posJ.jPos[1] = posJ.jPos[1] + 10;
        robot.GetJointTorques(0, joint_toq);
        joint_toq[1] = joint_toq[1] + 2;

        double[] tmpTorque = new double[6] { 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 };
        for (int i = 0; i < 6; i++)
        {
            tmpTorque[i] = joint_toq[i];
        }

        retval = robot.LoadIdentifyMain(tmpTorque, posJ.jPos, 1);
        Console.WriteLine("LoadIdentifyMain retval is: " + retval);

        double[] gain = new double[12] { 0, 0.05, 0, 0, 0, 0, 0, 0.02, 0, 0, 0, 0 };
        double weight = 0;
        DescTran load_pos = new DescTran(0, 0, 0);
        retval = robot.LoadIdentifyGetResult(gain, ref weight, ref load_pos);
        Console.WriteLine("LoadIdentifyGetResult retval is: {0}; weight is {1} cog is {2} {3} {4}", retval, weight, load_pos.x, load_pos.y, load_pos.z);
    }

Przeciąganie wspomagane czujnikiem siły
++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3
    
.. code-block:: c#
    :linenos:

    /**
    * @brief  Przeciąganie wspomagane czujnikiem siły
    * @param  [in] status Stan sterowania, 0-wyłączone; 1-włączone
    * @param  [in] asaptiveFlag Znacznik włączenia adaptacji, 0-wyłączony; 1-włączony
    * @param  [in] interfereDragFlag Znacznik przeciągania w strefie interferencji, 0-wyłączony; 1-włączony
    * @param  [in] ingularityConstraintsFlag Strategia punktu osobliwego, 0-unikanie; 1-przechodzenie
    * @param  [in] forceCollisionFlag Znacznik wykrywania kolizji robota podczas przeciągania wspomaganego; 0-wyłączony; 1-włączony
    * @param  [in] M Współczynnik bezwładności
    * @param  [in] B Współczynnik tłumienia
    * @param  [in] K Współczynnik sztywności
    * @param  [in] F Sześcioosiowy próg siły przeciągania
    * @param  [in] Fmax Maksymalne ograniczenie siły przeciągania Nm
    * @param  [in] Vmax Maksymalne ograniczenie prędkości stawu °/s
    * @return  Kod błędu
    */
    int EndForceDragControl(int status, int asaptiveFlag, int interfereDragFlag,int ingularityConstraintsFlag,int forceCollisionFlag, double[] M, double[] B, double[] K, double[] F, double Fmax, double Vmax);
    
Pobranie stanu przełącznika przeciągania czujnika siły
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera stan przełącznika przeciągania czujnika siły
    * @param  [out] dragState Stan sterowania przeciąganiem wspomaganym czujnikiem siły, 0-wyłączone; 1-włączone
    * @param  [out] sixDimensionalDragState Stan sterowania przeciąganiem wspomaganym sześcioosiową siłą, 0-wyłączone; 1-włączone
    * @return  Kod błędu
    */
    int GetForceAndTorqueDragState(ref int dragState, ref int sixDimensionalDragState);

Automatyczne włączanie czujnika siły po wyczyszczeniu błędu
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Automatyczne włączanie czujnika siły po wyczyszczeniu błędu
    * @param  [in] status Stan sterowania, 0-wyłączone; 1-włączone
    * @return  Kod błędu
    */
    int SetForceSensorDragAutoFlag(int status);

Przykład kodu przeciągania wspomaganego czujnikiem siły
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button61_Click(object sender, EventArgs e)
    {
        robot.SetForceSensorDragAutoFlag(1);
        double[] M = { 15.0, 15.0, 15.0, 0.5, 0.5, 0.1 };
        double[] B = { 150.0, 150.0, 150.0, 5.0, 5.0, 1.0 };
        double[] K = { 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 };
        double[] F = { 10.0, 10.0, 10.0, 1.0, 1.0, 1.0 };

        robot.EndForceDragControl(1, 0, 0, 0, M, B, K, F, 50, 100);
        robot.WaitMs(5000);

        int dragState = 0;
        int sixDimensionalDragState = 0;
        robot.GetForceAndTorqueDragState(ref dragState, ref sixDimensionalDragState);
        Console.WriteLine($"the drag state is {dragState} {sixDimensionalDragState}");

        robot.EndForceDragControl(0, 0, 0, 0, M, B, K, F, 50, 100);
    }

Ustawienie przełącznika i parametrów mieszanego przeciągania z użyciem 6-osiowej siły i impedancji stawu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief  Ustawienie przełącznika i parametrów mieszanego przeciągania z użyciem 6-osiowej siły i impedancji stawu
    * @param  [in] status Stan sterowania, 0-wyłączone; 1-włączone
    * @param  [in] impedanceFlag Znacznik włączenia impedancji, 0-wyłączony; 1-włączony
    * @param  [in] lamdeDain Wzmocnienie przeciągania
    * @param  [in] KGain Wzmocnienie sztywności
    * @param  [in] BGain Wzmocnienie tłumienia
    * @param  [in] dragMaxTcpVel Maksymalne ograniczenie prędkości liniowej końcówki podczas przeciągania
    * @param  [in] dragMaxTcpOriVel Maksymalne ograniczenie prędkości kątowej końcówki podczas przeciągania
    * @return  Kod błędu
    */
    int ForceAndJointImpedanceStartStop(int status, int impedanceFlag, double[] lamdeDain, double[] KGain, double[] BGain, double dragMaxTcpVel, double dragMaxTcpOriVel);

Przykład kodu przeciągania wspomaganego czujnikiem siły
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button62_Click(object sender, EventArgs e)
    {
        robot.DragTeachSwitch(1);
        double[] lambdaGain = { 3.0, 2.0, 2.0, 2.0, 2.0, 3.0 };
        double[] kGain = { 0, 0, 0, 0, 0, 0 };
        double[] bGain = { 150, 150, 150, 5.0, 5.0, 1.0 };
        int rtn = robot.ForceAndJointImpedanceStartStop(1, 0, lambdaGain, kGain, bGain, 1000, 180);
        Console.WriteLine($"ForceAndJointImpedanceStartStop rtn is {rtn}");
        Thread.Sleep(5000); 
        robot.DragTeachSwitch(0);
        rtn = robot.ForceAndJointImpedanceStartStop(0, 0, lambdaGain, kGain, bGain, 1000, 180);
        Console.WriteLine($"ForceAndJointImpedanceStartStop rtn is {rtn}");
    }

Sterowanie uruchamianiem/zatrzymywaniem impedancji
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
    * @brief Sterowanie uruchamianiem/zatrzymywaniem impedancji
    * @param [in] status 0: wyłączone; 1-włączone
    * @param [in] workSpace 0-przestrzeń stawów; 1-przestrzeń kartezjańska
    * @param [in] forceThreshold Próg siły wyzwalającej (N)
    * @param [in] m Parametr masy
    * @param [in] b Parametr tłumienia
    * @param [in] k Parametr sztywności
    * @param [in] maxV Maksymalna prędkość liniowa (mm/s)
    * @param [in] maxVA Maksymalne przyspieszenie liniowe (mm/s²)
    * @param [in] maxW Maksymalna prędkość kątowa (°/s)
    * @param [in] maxWA Maksymalne przyspieszenie kątowe (°/s²)
    * @return Kod błędu
    */
    public int ImpedanceControlStartStop(int status, int workSpace, double[] forceThreshold, double[] m, double[] b, double[] k, double maxV, double maxVA, double maxW, double maxWA)

Przykład kodu sterowania uruchamianiem/zatrzymywaniem impedancji robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:

    public void TestImpedanceControl()
    { 
        int[] ctrl = new int[20];
        int state;
        int pressValue;
        int error;
        int rtn;
        JointPos j1 = new JointPos(102.622, -135.990, 120.769, -73.950, -90.848, 35.507);
        JointPos j2 = new JointPos(93.674, -80.062, 82.947, -92.199, -90.967, 26.559);
        DescPose desc_pos1 = new DescPose(136.552, -149.799, 449.532, 179.817, -1.172, 157.123);
        DescPose desc_pos2 = new DescPose(136.540, -561.048, 449.542, 179.819, -1.172, 157.122);
    
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
    
        int tool = 0;
        int user = 0;
        float vel = 100.0f;
        float acc = 200.0f;
        float ovl = 100.0f;
        float blendT = -1.0f;
        float blendR = -1.0f;
    
        byte flag = 0;
    
        byte search = 0;
        robot.SetSpeed(20);
        int company = 17;
        int device = 0;
        int softversion = 0;
        int bus = 1;
        robot.FT_SetConfig(company, device, softversion, bus);
        Thread.Sleep(1000);
        robot.FT_GetConfig(ref company, ref device, ref softversion, ref bus);
        Console.WriteLine($"FT config:{company},{device},{softversion},{bus}");
        Thread.Sleep(1000);
    
        robot.FT_Activate(0);
        Thread.Sleep(1000);
        robot.FT_Activate(1);
        Thread.Sleep(1000);
        Thread.Sleep(1000);
        robot.FT_SetZero(0);
        Thread.Sleep(1000);
        robot.FT_SetZero(1);
        Thread.Sleep(1000);
    
        double[] forceThreshold = new double[] { 30, 30, 30, 5, 5, 5 };
        double[] m = new double[] { 0.1, 0.1, 0.1, 0.02, 0.02, 0.02 };
        double[] b = new double[] { 1, 1, 1, 0.08, 0.08, 0.08 };
        double[] k = new double[] { 0, 0, 0, 0, 0, 0 };
        rtn = robot.ImpedanceControlStartStop(1, 1, forceThreshold, m, b, k, 1000, 500, 100, 100);
        Console.WriteLine($"ImpedanceControlStartStop errcode:{rtn}");
        rtn = robot.MoveL(desc_pos1, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1, 0);
        rtn = robot.MoveL(desc_pos2, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1, 0);
        rtn = robot.MoveL(desc_pos1, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1, 0);
        rtn = robot.MoveL(desc_pos2, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1, 0);
        rtn = robot.MoveL(desc_pos1, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1, 0);
        rtn = robot.MoveL(desc_pos2, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1, 0);
        Console.WriteLine($"movel errcode:{rtn}");
        robot.ImpedanceControlStartStop(0, 1, forceThreshold, m, b, k, 1000, 500, 100, 100);
    }

Włączenie funkcji kompensacji momentu obrotowego i współczynnika kompensacji
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Włączenie funkcji kompensacji momentu obrotowego i współczynnika kompensacji
    * @param [in] status Przełącznik, 0-wyłączony; 1-włączony
    * @param [in] torqueCoeff Współczynniki kompensacji momentu J1-J6 [0-1]
    * @return Kod błędu
    */
    public int SetCoderCompenParams(int status, double[] torqueCoeff)

Pozycjonowanie Powierzchni
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pozycjonowanie powierzchni
    * @param  [in] rcs Referencyjny układ współrzędnych, 0-układ narzędzia, 1-układ podstawy
    * @param  [in] dir  Kierunek ruchu, 1-kierunek dodatni, 2-kierunek ujemny
    * @param  [in] axis Oś ruchu, 1-oś x, 2-oś y, 3-oś z
    * @param  [in] lin_v Prędkość liniowa poszukiwania, jednostka mm/s
    * @param  [in] lin_a Przyspieszenie liniowe poszukiwania, jednostka mm/s^2, tymczasowo nieużywane, domyślnie 0
    * @param  [in] max_dis Maksymalna odległość poszukiwania, jednostka mm
    * @param  [in] ft  Próg siły/momentu zakończenia ruchu, fx,fy,fz,tx,ty,tz
    * @return  Kod błędu
    */
    public int FT_FindSurface(int rcs, byte dir, byte axis, float lin_v, float lin_a, float max_dis, float ft)

Rozpoczęcie Obliczania Pozycji Płaszczyzny Środkowej
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief  Rozpoczęcie obliczania pozycji płaszczyzny środkowej
    * @return  Kod błędu
    */
    public int FT_CalCenterStart()

Zakończenie Obliczania Pozycji Płaszczyzny Środkowej
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief  Zakończenie obliczania pozycji płaszczyzny środkowej
    * @param  [out] pos Pozycja płaszczyzny środkowej
    * @return  Kod błędu
    */
    public int FT_CalCenterEnd(ref DescPose pos)

Przykład Kodu Pozycjonowania Powierzchni
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    private void button59_Click(object sender, EventArgs e)
    {
        int company = 22;
        int device = 0;
        int softversion = 0;
        int bus = 1;

        robot.FT_SetConfig(company, device, softversion, bus);
        Thread.Sleep(1000);
        robot.FT_GetConfig(ref company, ref device, ref softversion, ref bus);
        Console.WriteLine("FT config:" + company + "," + device + "," + softversion + "," + bus);
        Thread.Sleep(1000);

        robot.FT_Activate(0);
        Thread.Sleep(1000);
        robot.FT_Activate(1);
        Thread.Sleep(1000);

        Thread.Sleep(1000);
        robot.FT_SetZero(0);
        Thread.Sleep(1000);

        int rcs = 0;
        byte dir = 1;
        byte axis = 1;
        float lin_v = 15.0f;
        float lin_a = 0.0f;
        float maxdis = 500.0f;
        float ft_goal = 2.0f;
        DescPose desc_pos = new DescPose(-419.524f, -13.000f, 351.569f, -178.118f, 0.314f, 3.833f);
        DescPose xcenter = new DescPose(0, 0, 0, 0, 0, 0);
        DescPose ycenter = new DescPose(0, 0, 0, 0, 0, 0);

        ForceTorque ft = new ForceTorque();

        ft.fx = -2.0f;

        robot.MoveCart(desc_pos, 1, 0, 100.0f, 100.0f, 100.0f, -1.0f, -1);

        robot.FT_CalCenterStart();
        robot.FT_FindSurface(rcs, dir, axis, lin_v, lin_a, maxdis, ft_goal);
        robot.MoveCart(desc_pos, 1, 0, 100.0f, 100.0f, 100.0f, -1.0f, -1);
        robot.WaitMs(1000);

        dir = 2;
        robot.FT_FindSurface(rcs, dir, axis, lin_v, lin_a, maxdis, ft_goal);
        robot.FT_CalCenterEnd(ref xcenter);
        Console.WriteLine("xcenter:" + xcenter.tran.x + "," + xcenter.tran.y + "," + xcenter.tran.z + "," + xcenter.rpy.rx + "," + xcenter.rpy.ry + "," + xcenter.rpy.rz);
        robot.MoveCart(xcenter, 1, 0, 60.0f, 50.0f, 50.0f, -1.0f, -1);

        robot.FT_CalCenterStart();
        dir = 1;
        axis = 2;
        lin_v = 6.0f;
        maxdis = 150.0f;
        robot.FT_FindSurface(rcs, dir, axis, lin_v, lin_a, maxdis, ft_goal);
        robot.MoveCart(desc_pos, 1, 0, 100.0f, 100.0f, 100.0f, -1.0f, -1);
        robot.WaitMs(1000);

        dir = 2;
        robot.FT_FindSurface(rcs, dir, axis, lin_v, lin_a, maxdis, ft_goal);
        robot.FT_CalCenterEnd(ref ycenter);
        Console.WriteLine("ycenter:" + ycenter.tran.x + "," + ycenter.tran.y + "," + ycenter.tran.z + "," + ycenter.rpy.rx + "," + ycenter.rpy.ry + "," + ycenter.rpy.rz);
        robot.MoveCart(ycenter, 1, 0, 60.0f, 50.0f, 50.0f, 0.0f, -1);

    }

Ustawianie Przesunięcia Splotu w Czasie Rzeczywistym
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ustawianie przesunięcia splotu w czasie rzeczywistym
    * @param [in] offset Przesunięcie w czasie rzeczywistym [mm, °]
    * @return  Kod błędu
    */
    public int SetWeaveOffsetRT(DescPose offset)

Przykład Kodu Prędkości i Przesunięcia Splotu w Czasie Rzeczywistym
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:   

    public void TestWeaveSpeedAndOffset()
    {
        Console.WriteLine("============================================================");
        Console.WriteLine("  Weave Speed and Offset Test");
        Console.WriteLine("============================================================");

        if (robot == null)
        {
            Console.WriteLine("ERROR: Robot not connected!");
            return;
        }

        int rtn;
        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);

        JointPos j1 = new JointPos(5.027, -84.331, -75.139, -103.690, 86.379, 20.794);
        DescPose d1 = new DescPose(324.752, -83.339, 366.314, -172.321, -0.936, -106.047);

        JointPos j2 = new JointPos(-35.335, -117.598, -57.174, -95.234, 90.001, -19.560);
        DescPose d2 = new DescPose(324.999, -355.439, 260.000, 179.995, 0.003, -105.775);

        JointPos j3 = new JointPos(59.787, -117.594, -57.183, -95.222, 90.006, 75.562);
        DescPose d3 = new DescPose(324.998, 355.441, 260.002, 179.995, 0.003, -105.775);

        // ---- Step 1: MoveJ to start point ----
        Console.WriteLine("\nStep 1: MoveJ to start point");
        rtn = robot.MoveJ(j1, d1, 1, 0, 100, 100, 50, epos, -1, 0, offset_pos);
        Console.WriteLine("  MoveJ(j1) rtn={0}", rtn);
        Thread.Sleep(500);

        // ---- Step 2: MoveJ to weave entry ----
        Console.WriteLine("\nStep 2: MoveJ to weave entry point");
        rtn = robot.MoveJ(j2, d2, 1, 0, 100, 100, 50, epos, -1, 0, offset_pos);
        Console.WriteLine("  MoveJ(j2) rtn={0}", rtn);
        Thread.Sleep(500);

        // ---- Step 3: WeaveStart, launch weave MoveL thread ----
        Console.WriteLine("\nStep 3: WeaveStart + MoveL in background thread");
        robot.WeaveStart(0);

        bool weaveRunning = true;
        Thread weaveThread = new Thread(() =>
        {
            rtn = robot.MoveL(j3, d3, 1, 0, 100, 100, 5, -1, 0, epos, 0, 0, offset_pos, 5, 0, 0, 10);
            Console.WriteLine("  MoveL(weave) thread finished, rtn={0}", rtn);
            weaveRunning = false;
        });
        weaveThread.IsBackground = true;
        weaveThread.Start();
        Thread.Sleep(500);  // Wait for motion to start

        // ---- Step 4: Speed test (main thread, weave MoveL in background) ----
        Console.WriteLine("\nStep 4: SetSpeed test during weaving");
        int[] speedValues = { 20, 50, 80, 30, 60, 10 };
        foreach (int speed in speedValues)
        {
            if (!weaveRunning) break;
            rtn = robot.SetSpeedInstant(speed);
            robot.GetRobotRealTimeState(ref pkg);
            Console.WriteLine("  SetSpeed({0}) -> rtn={1}, TCP_CmpSpeed={2}", speed, rtn, pkg.target_TCP_CmpSpeed);
            Thread.Sleep(5000);
        }


        Thread.Sleep(5000);
        // ---- Step 5: SetWeaveOffsetRT offset test (main thread, weave MoveL in background) ----
        Console.WriteLine("\nStep 5: SetWeaveOffsetRT test (50 iterations, delta=0.1)");
        double accumOffset = 0.0;
        for (int i = 0; i < 50 && weaveRunning; i++)
        {
            accumOffset += 0.1;
            DescPose weaveOffset = new DescPose(0, 0, accumOffset, 0, 0, 0);
            rtn = robot.SetWeaveOffsetRT(weaveOffset);
            robot.GetRobotRealTimeState(ref pkg);
            Console.WriteLine("  [{0}/50] SetWeaveOffsetRT(x={1:F1}) -> rtn={2}, TCP_pos=({3:F2},{4:F2},{5:F2})",
                i + 1, accumOffset, rtn,
                pkg.tl_cur_pos[0], pkg.tl_cur_pos[1], pkg.tl_cur_pos[2]);
            Thread.Sleep(100);
        }

        // ---- Step 6: Wait for weave MoveL, then WeaveEnd ----
        Console.WriteLine("\nStep 6: Wait for weave MoveL, then WeaveEnd");
        weaveThread.Join();
        robot.WeaveEnd(0);
        Thread.Sleep(500);

        // ---- Step 7: MoveL back to start ----
        Console.WriteLine("\nStep 7: MoveL back to start");
        rtn = robot.MoveL(j1, d1, 1, 0, 100, 100, 50, -1, 0, epos, 0, 0, offset_pos, 50, 0, 0, 10);
        Console.WriteLine("  MoveL(back) rtn={0}", rtn);

        robot.GetRobotRealTimeState(ref pkg);
        Console.WriteLine("\n  Final robot state: main_code={0}, sub_code={1}", pkg.main_code, pkg.sub_code);
        Console.WriteLine("============================================================");
        Console.WriteLine("  Weave Speed and Offset Test Complete");
        Console.WriteLine("============================================================");
    }