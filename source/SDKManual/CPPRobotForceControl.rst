Sterowanie siłą robota
======================

.. toctree::
    :maxdepth: 5

Konfiguracja czujnika siły
+++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Konfiguruje czujnik siły
     * @param  [in] company   Producent czujnika siły, 17-Kunwei Technology, 19-Instytut Kosmiczny 11, 20-Czujnik ATI, 21-Zhongke Midian, 22-Weihang Minxin, 23-NBIT, 24-Xinjingcheng (XJC), 26-NSR
     * @param  [in] device   Numer urządzenia, Kunwei (0-KWR75B), Instytut Kosmiczny 11 (0-MCS6A-200-4), ATI (0-AXIA80-M8), Zhongke Midian (0-MST2010), Weihang Minxin (0-WHC6L-YB-10A), NBIT (0-XLH93003ACS), Xinjingcheng XJC (0-XJC-6F-D82), NSR (0-NSR-FTSensorA)
     * @param  [in] softvesion   Numer wersji oprogramowania, tymczasowo nieużywany, domyślnie 0
     * @param  [in] bus   Pozycja magistrali końcowej, na której zamontowane jest urządzenie, tymczasowo nieużywane, domyślnie 0
     * @return   Kod błędu
     */
    errno_t FT_SetConfig(int company, int device, int softvesion, int bus);

Pobieranie konfiguracji czujnika siły
+++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Pobiera konfigurację czujnika siły
    * @param  [in] company   Producent czujnika siły, do ustalenia
    * @param  [in] device   Numer urządzenia, tymczasowo nieużywany, domyślnie 0
    * @param  [in] softvesion   Numer wersji oprogramowania, tymczasowo nieużywany, domyślnie 0
    * @param  [in] bus   Pozycja magistrali końcowej, na której zamontowane jest urządzenie, tymczasowo nieużywane, domyślnie 0
    * @return   Kod błędu
    */
    errno_t  FT_GetConfig(int *company, int *device, int *softvesion, int *bus);

Aktywacja czujnika siły
++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Aktywuje czujnik siły
    * @param  [in] act   0-reset, 1-aktywacja
    * @return   Kod błędu
    */
    errno_t  FT_Activate(uint8_t act);

Zerowanie czujnika siły
++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Zeruje czujnik siły
    * @param  [in] act   0-usuń punkt zerowy, 1-korekcja zera
    * @return   Kod błędu
    */
    errno_t  FT_SetZero(uint8_t act);

Ustawianie układu odniesienia czujnika siły
+++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ustawia układ odniesienia czujnika siły
    * @param  [in] ref   0-układ współrzędnych narzędzia, 1-układ współrzędnych bazowych
    * @return   Kod błędu
    */
    errno_t  FT_SetRCS(uint8_t ref);

Ustawianie masy obciążenia pod czujnikiem siły
+++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Ustawia masę obciążenia pod czujnikiem siły
     * @param [in] weight Masa obciążenia [kg]
     * @return Kod błędu
     */
    errno_t SetForceSensorPayload(double weight);

Ustawianie środka ciężkości obciążenia pod czujnikiem siły
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Ustawia środek ciężkości obciążenia pod czujnikiem siły
     * @param [in] x Środek ciężkości obciążenia x [mm]
     * @param [in] y Środek ciężkości obciążenia y [mm]
     * @param [in] z Środek ciężkości obciążenia z [mm]
     * @return Kod błędu
     */
    errno_t SetForceSensorPayloadCog(double x, double y, double z);

Pobieranie masy obciążenia pod czujnikiem siły
+++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Pobiera masę obciążenia pod czujnikiem siły
     * @param [in] weight Masa obciążenia [kg]
     * @return Kod błędu
     */
    errno_t GetForceSensorPayload(double& weight);

Pobieranie środka ciężkości obciążenia pod czujnikiem siły
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Pobiera środek ciężkości obciążenia pod czujnikiem siły
     * @param [out] x Środek ciężkości obciążenia x [mm]
     * @param [out] y Środek ciężkości obciążenia y [mm]
     * @param [out] z Środek ciężkości obciążenia z [mm]
     * @return Kod błędu
     */
    errno_t GetForceSensorPayloadCog(double& x, double& y, double& z);

Automatyczne zerowanie czujnika siły
++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Automatyczne zerowanie czujnika siły
     * @param [out] weight Masa czujnika [kg]
     * @param [out] pos Środek ciężkości czujnika [mm]
     * @return Kod błędu
     */
    errno_t ForceSensorAutoComputeLoad(double& weight, DescTran& pos);

Pobieranie danych siły/momentu w układzie odniesienia
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Pobiera dane siły/momentu w układzie odniesienia
    * @param  [out] ft   Siła/moment, fx, fy, fz, tx, ty, tz
    * @return   Kod błędu
    */
    errno_t  FT_GetForceTorqueRCS(ForceTorque *ft);

Pobieranie surowych danych siły/momentu z czujnika siły
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Pobiera surowe dane siły/momentu z czujnika siły
    * @param  [out] ft   Siła/moment, fx, fy, fz, tx, ty, tz
    * @return   Kod błędu
    */
    errno_t  FT_GetForceTorqueOrigin(ForceTorque *ft);

Przykład kodu konfiguracji czujnika siły i automatycznego zerowania
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestFTInit(void)
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      robot.LoggerInit();
      robot.SetLoggerLevel(1);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return -1;
      }
      robot.SetReConnectParam(true, 30000, 500);
      int company = 24;
      int device = 0;
      int softversion = 0;
      int bus = 1;
      int index = 1;
      robot.FT_SetConfig(company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_GetConfig(&company, &device, &softversion, &bus);
      printf("FT config:%d,%d,%d,%d\n", company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_Activate(0);
      robot.Sleep(1000);
      robot.FT_Activate(1);
      robot.Sleep(1000);
      robot.Sleep(1000);
      robot.FT_SetZero(0);
      robot.Sleep(1000);
      ForceTorque ft;
      memset(&ft, 0, sizeof(ForceTorque));
      robot.FT_GetForceTorqueOrigin(0, &ft);
      printf("ft origin:%f,%f,%f,%f,%f,%f\n", ft.fx, ft.fy, ft.fz, ft.tx, ft.ty, ft.tz);
      robot.FT_SetZero(1);
      robot.Sleep(1000);
      DescPose ftCoord = {};
      robot.FT_SetRCS(0, ftCoord);
      robot.SetForceSensorPayload(0.824);
      robot.SetForceSensorPayloadCog(0.778, 2.554, 48.765);
      double weight = 0;
      double x = 0, y = 0, z = 0;
      robot.GetForceSensorPayload(weight);
      robot.GetForceSensorPayloadCog(x, y, z);
      printf("the FT load is %lf, %lf %lf %lf\n", weight, x, y, z);
      robot.SetForceSensorPayload(0);
      robot.SetForceSensorPayloadCog(0, 0, 0);
      double computeWeight = 0;
      DescTran tran = {};
      robot.ForceSensorAutoComputeLoad(weight, tran);
      cout << "the result is weight " << weight << " pos is " << tran.x << " " << tran.y << " " << tran.z << endl;
      robot.CloseRPC();
      return 0;
    }

Rejestracja identyfikacji masy obciążenia
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Rejestracja identyfikacji masy obciążenia
    * @param  [in] id   Numer układu współrzędnych czujnika, zakres [1~14]
    * @return   Kod błędu
    */
    errno_t  FT_PdIdenRecord(int id);

Obliczanie identyfikacji masy obciążenia
++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Obliczanie identyfikacji masy obciążenia
    * @param  [out] weight   Masa obciążenia, jednostka kg
    * @return   Kod błędu
    */
    errno_t  FT_PdIdenCompute(float *weight);

Rejestracja identyfikacji środka ciężkości obciążenia
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Rejestracja identyfikacji środka ciężkości obciążenia
    * @param  [in] id   Numer układu współrzędnych czujnika, zakres [1~14]
    * @param  [in] index Numer punktu, zakres [1~3]
    * @return   Kod błędu
    */
    errno_t  FT_PdCogIdenRecord(int id, int index);

Obliczanie identyfikacji środka ciężkości obciążenia
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Obliczanie identyfikacji środka ciężkości obciążenia
    * @param  [out] cog   Środek ciężkości obciążenia, jednostka mm
    * @return   Kod błędu
    */
    errno_t  FT_PdCogIdenCompute(DescTran *cog);

Przykład kodu identyfikacji obciążenia czujnika siły
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestFTLoadCompute(void)
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      robot.LoggerInit();
      robot.SetLoggerLevel(1);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return -1;
      }
      robot.SetReConnectParam(true, 30000, 500);
      int company = 24;
      int device = 0;
      int softversion = 0;
      int bus = 1;
      int index = 1;
      robot.FT_SetConfig(company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_GetConfig(&company, &device, &softversion, &bus);
      printf("FT config:%d,%d,%d,%d\n", company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_Activate(0);
      robot.Sleep(1000);
      robot.FT_Activate(1);
      robot.Sleep(1000);
      robot.Sleep(1000);
      robot.FT_SetZero(0);
      robot.Sleep(1000);
      ForceTorque ft;
      memset(&ft, 0, sizeof(ForceTorque));
      robot.FT_GetForceTorqueOrigin(0, &ft);
      printf("ft origin:%f,%f,%f,%f,%f,%f\n", ft.fx, ft.fy, ft.fz, ft.tx, ft.ty, ft.tz);
      robot.FT_SetZero(1);
      robot.Sleep(1000);
      DescPose tcoord = {};
      tcoord.tran.z = 35.0;
      robot.SetToolCoord(10, &tcoord, 1, 0, 0, 0);
      robot.FT_PdIdenRecord(10);
      robot.Sleep(1000);
      float weight = 0.0;
      robot.FT_PdIdenCompute(&weight);
      printf("payload weight:%f\n", weight);
      DescPose desc_p1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
      DescPose desc_p2(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
      DescPose desc_p3(-327.622, 402.230, 320.402, -178.067, 2.127, -46.207);
      robot.MoveCart(&desc_p1, 0, 0, 100.0, 100.0, 100.0, -1.0, -1);
      robot.Sleep(1000);
      robot.FT_PdCogIdenRecord(10, 1);
      robot.MoveCart(&desc_p2, 0, 0, 100.0, 100.0, 100.0, -1.0, -1);
      robot.Sleep(1000);
      robot.FT_PdCogIdenRecord(10, 2);
      robot.MoveCart(&desc_p3, 0, 0, 100.0, 100.0, 100.0, -1.0, -1);
      robot.Sleep(1000);
      robot.FT_PdCogIdenRecord(10, 3);
      robot.Sleep(1000);
      DescTran cog;
      memset(&cog, 0, sizeof(DescTran));
      robot.FT_PdCogIdenCompute(&cog);
      printf("cog:%f,%f,%f\n", cog.x, cog.y, cog.z);
      robot.CloseRPC();
      return 0;
    }

Ochrona przed kolizją
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
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
    * @return   Kod błędu
    */
    errno_t  FT_Guard(uint8_t flag, int sensor_id, uint8_t select[6], ForceTorque *ft, float max_threshold[6], float min_threshold[6]);

Przykład kodu ochrony przed kolizją
+++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestFTGuard(void)
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      robot.LoggerInit();
      robot.SetLoggerLevel(1);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return -1;
      }
      robot.SetReConnectParam(true, 30000, 500);
      int company = 24;
      int device = 0;
      int softversion = 0;
      int bus = 1;
      int index = 1;
      robot.FT_SetConfig(company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_GetConfig(&company, &device, &softversion, &bus);
      printf("FT config:%d,%d,%d,%d\n", company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_Activate(0);
      robot.Sleep(1000);
      robot.FT_Activate(1);
      robot.Sleep(1000);
      robot.Sleep(1000);
      robot.FT_SetZero(0);
      robot.Sleep(1000);
      uint8_t sensor_id = 1;
      uint8_t select[6] = { 1,1,1,1,1,1 };
      float max_threshold[6] = { 10.0,10.0,10.0,10.0,10.0,10.0 };
      float min_threshold[6] = { 5.0,5.0,5.0,5.0,5.0,5.0 };
      ForceTorque ft;
      DescPose desc_p1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
      DescPose desc_p2(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
      DescPose desc_p3(-327.622, 402.230, 320.402, -178.067, 2.127, -46.207);
      robot.FT_Guard(1, sensor_id, select, &ft, max_threshold, min_threshold);
      robot.MoveCart(&desc_p1, 0, 0, 100.0, 100.0, 100.0, -1.0, -1);
      robot.MoveCart(&desc_p2, 0, 0, 100.0, 100.0, 100.0, -1.0, -1);
      robot.MoveCart(&desc_p3, 0, 0, 100.0, 100.0, 100.0, -1.0, -1);
      robot.FT_Guard(0, sensor_id, select, &ft, max_threshold, min_threshold);
      robot.CloseRPC();
      return 0;
    }

Sterowanie stałą siłą
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Sterowanie stałą siłą
    * @param [in] flag 0-wyłącz sterowanie stałą siłą, 1-włącz sterowanie stałą siłą
    * @param [in] sensor_id Numer czujnika siły
    * @param [in] select Wybór, czy wykrywać kolizję dla sześciu stopni swobody, 0-nie wykrywaj, 1-wykrywaj
    * @param [in] ft Siła/moment kolizji, fx, fy, fz, tx, ty, tz
    * @param [in] ft_pid Parametry PID siły, parametry PID momentu
    * @param [in] adj_sign Sterowanie uruchamianiem/zatrzymywaniem adaptacyjnym, 0-wyłącz, 1-włącz
    * @param [in] ILC_sign Sterowanie uruchamianiem/zatrzymywaniem ILC, 0-zatrzymaj, 1-trening, 2-praktyka
    * @param [in] max_dis Maksymalna odległość regulacji, jednostka mm
    * @param [in] max_ang Maksymalny kąt regulacji, jednostka deg
    * @param [in] M Parametry masy rx, ry [0.1-10], domyślnie 2
    * @param [in] B Parametry tłumienia rx, ry [0.1-50], domyślnie 8
    * @param [in] threshold Próg uruchomienia rx, ry [0-10], domyślnie 0.2
    * @param [in] adjustCoeff Współczynnik regulacji momentu rx, ry [0-1], domyślnie 1
    * @param [in] polishRadio Promień szlifowania, jednostka mm
    * @param [in] filter_Sign Flaga włączenia filtracji 0-wył.; 1-wł., domyślnie wył.
    * @param [in] posAdapt_sign Flaga włączenia dostosowania postawy 0-wył.; 1-wł., domyślnie wył.
    * @param [in] isNoBlock Flaga blokowania, 0-blokuj; 1-nie blokuj
    * @return Kod błędu
    */
    errno_t FT_Control(uint8_t flag, int sensor_id, uint8_t select[6], ForceTorque* ft, float ft_pid[6], uint8_t adj_sign,
    uint8_t ILC_sign, float max_dis, float max_ang, double M[2], double B[2], double threshold[2], double adjustCoeff[2], double polishRadio = 0.0, int filter_Sign = 0, int posAdapt_sign = 0, int isNoBlock = 0);

Przykład kodu sterowania stałą siłą z tłumieniem
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestFTControlWithAdjustCoeff(void)
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      robot.LoggerInit();
      robot.SetLoggerLevel(1);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return -1;
      }
      robot.SetReConnectParam(true, 30000, 500);
      uint8_t sensor_id = 10;
      uint8_t select[6] = { 0,0,1,0,0,0 };
      float ft_pid[6] = { 0.0008, 0.0, 0.0, 0.0, 0.0, 0.0 };
      uint8_t adj_sign = 0;
      uint8_t ILC_sign = 0;
      float max_dis = 1000.0;
      float max_ang = 20;
      ForceTorque ft = {0.0};
      ExaxisPos epos(0, 0, 0, 0);
      JointPos j1(80.765, -98.795, 106.548, -97.734, -89.999, 94.842);
      JointPos j2(43.067, -84.429, 92.620, -98.175, -90.011, 57.144);
      DescPose desc_p1(5.009, -547.463, 262.053, -179.999, -0.019, 75.923);
      DescPose desc_p2(-347.966, -547.463, 262.048, -180.000, -0.019, 75.923);
      DescPose offset_pos(0, 0, 0, 0, 0, 0);
      double M[2] = { 2.0, 2.0 };
      double B[2] = { 15.0, 15.0 };
      double threshold[2] = {1.0, 1.0};
      double adjustCoeff[2] = {1.0, 0.8};
      double polishRadio = 0.0;
      int filter_Sign = 0;
      int posAdapt_sign = 1;
      int isNoBlock;
      ft.fz = -10.0;
      while(true)
      {
        rtn = robot.FT_Control(1, sensor_id, select, &ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, M, B, threshold, adjustCoeff, 0, 0, 1, 0);
        printf("FT_Control start rtn is %d\n", rtn);
        robot.MoveL(&j1, &desc_p1, 1, 0, 100, 100, 100, -1, 0, &epos, 0, 0, &offset_pos, 200.0, 0);
        robot.MoveL(&j2, &desc_p2, 1, 0, 100, 100, 100, -1, 0, &epos, 0, 0, &offset_pos, 200.0, 0);
        rtn = robot.FT_Control(0, sensor_id, select, &ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, M, B, threshold, adjustCoeff, 0, 0, 1, 0);
        printf("FT_Control end rtn is %d\n", rtn);
      }
      robot.CloseRPC();
      return 0;
    }

Eksploracja po spirali
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Eksploracja po spirali
    * @param  [in] rcs Układ odniesienia, 0-układ współrzędnych narzędzia, 1-układ współrzędnych bazowych
    * @param  [in] dr Posuw promienia na obrót
    * @param  [in] ft Próg siły/momentu, fx, fy, fz, tx, ty, tz, zakres [0~100]
    * @param  [in] max_t_ms Maksymalny czas eksploracji, jednostka ms
    * @param  [in] max_vel Maksymalna prędkość liniowa, jednostka mm/s
    * @return   Kod błędu
    */
    errno_t  FT_SpiralSearch(int rcs, float dr, float ft, float max_t_ms, float max_vel);

Wstawianie obrotowe
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Wstawianie obrotowe
    * @param [in] rcs Układ odniesienia, 0-układ współrzędnych narzędzia, 1-układ współrzędnych bazowych
    * @param [in] angVelRot Prędkość kątowa obrotu, jednostka deg/s
    * @param [in] ft  Próg siły/momentu, fx, fy, fz, tx, ty, tz, zakres [0~100]
    * @param [in] max_angle Maksymalny kąt obrotu, jednostka deg
    * @param [in] orn Kierunek siły/momentu, 1-wzdłuż osi Z, 2-wokół osi Z
    * @param [in] max_angAcc Maksymalne przyspieszenie kątowe obrotu, jednostka deg/s^2, tymczasowo nieużywane, domyślnie 0
    * @param [in] rotorn  Kierunek obrotu, 1-zgodnie z ruchem wskazówek zegara, 2-przeciwnie do ruchu wskazówek zegara
    * @param [in] strategy Strategia postępowania w przypadku niewykrycia siły/momentu, 0-zgłoś błąd; 1-ostrzeżenie, kontynuuj ruch
    * @return Kod błędu
    */
    errno_t FT_RotInsertion(int rcs, float angVelRot, float ft, float max_angle, uint8_t orn, float max_angAcc, uint8_t rotorn, int strategy = 0);

Przykład kodu wstawiania obrotowego z czujnikiem siły
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestMove(void)
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return -1;
        }
        robot.SetReConnectParam(true, 30000, 500);
        JointPos j1(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j2(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
        JointPos j3(-29.777, -84.536, 109.275, -114.075, -86.655, 74.257);
        JointPos j4(-31.154, -95.317, 94.276, -88.079, -89.740, 74.256);
        DescPose desc_pos1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_pos2(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose desc_pos3(-487.434, 154.362, 308.576, 176.600, 0.268, -14.061);
        DescPose desc_pos4(-443.165, 147.881, 480.951, 179.511, -0.775, -15.409);
        DescPose offset_pos(0, 0, 0, 0, 0, 0);
        ExaxisPos epos(0, 0, 0, 0);
        int tool = 0;
        int user = 0;
        float vel = 100.0;
        float acc = 100.0;
        float ovl = 100.0;
        float oacc = 100.0;
        float blendT = 0.0;
        float blendR = 0.0;
        uint8_t flag = 0;
        uint8_t search = 0;
        int blendMode = 0;
        int velAccMode = 0;
        robot.SetSpeed(20);
        rtn = robot.MoveJ(&j1, &desc_pos1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
        printf("movej errcode:%d\n", rtn);
        rtn = robot.MoveL(&j2, &desc_pos2, tool, user, vel, acc, ovl, blendR, blendMode, &epos, search, flag, &offset_pos, oacc, velAccMode);
        printf("movel errcode:%d\n", rtn);
        rtn = robot.MoveC(&j3, &desc_pos3, tool, user, vel, acc, &epos, flag, &offset_pos, &j4, &desc_pos4, tool, user, vel, acc, &epos, flag, &offset_pos, ovl, blendR, oacc, velAccMode);
        printf("movec errcode:%d\n", rtn);
        rtn = robot.MoveJ(&j2, &desc_pos2, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
        printf("movej errcode:%d\n", rtn);
        rtn = robot.Circle(&j3, &desc_pos3, tool, user, vel, acc, &epos, &j1, &desc_pos1, tool, user, vel, acc, &epos, ovl, flag, &offset_pos, oacc, -1, velAccMode);
        printf("circle errcode:%d\n", rtn);
        rtn = robot.MoveCart(&desc_pos4, tool, user, vel, acc, ovl, blendT, -1);
        printf("MoveCart errcode:%d\n", rtn);
        rtn = robot.MoveJ(&j1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
        printf("movej errcode:%d\n", rtn);
        rtn = robot.MoveL(&desc_pos2, tool, user, vel, acc, ovl, blendR, blendMode, &epos, search, flag, &offset_pos, -1, velAccMode);
        printf("movel errcode:%d\n", rtn);
        rtn = robot.MoveC(&desc_pos3, tool, user, vel, acc, &epos, flag, &offset_pos, &desc_pos4, tool, user, vel, acc, &epos, flag, &offset_pos, ovl, blendR, -1, velAccMode);
        printf("movec errcode:%d\n", rtn);
        rtn = robot.MoveJ(&j2, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
        printf("movej errcode:%d\n", rtn);
        rtn = robot.Circle(&desc_pos3, tool, user, vel, acc, &epos, &desc_pos1, tool, user, vel, acc, &epos, ovl, flag, &offset_pos, oacc, blendR, -1, velAccMode);
        printf("circle errcode:%d\n", rtn);
        robot.CloseRPC();
        return 0;
    }

Wstawianie liniowe
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Wstawianie liniowe
    * @param  [in] rcs Układ odniesienia, 0-układ współrzędnych narzędzia, 1-układ współrzędnych bazowych
    * @param  [in] ft  Próg siły/momentu, fx, fy, fz, tx, ty, tz, zakres [0~100]
    * @param  [in] lin_v Prędkość liniowa, jednostka mm/s
    * @param  [in] lin_a Przyspieszenie liniowe, jednostka mm/s^2, tymczasowo nieużywane
    * @param  [in] max_dis Maksymalna odległość wstawiania, jednostka mm
    * @param  [in] linorn  Kierunek wstawiania, 0-kierunek ujemny, 1-kierunek dodatni
    * @return   Kod błędu
    */
    errno_t  FT_LinInsertion(int rcs, float ft, float lin_v, float lin_a, float max_dis, uint8_t linorn);

Przykład kodu dla instrukcji eksploracji po spirali, wstawiania liniowego itp.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestFTSearch(void)
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      robot.LoggerInit();
      robot.SetLoggerLevel(1);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return -1;
      }
      robot.SetReConnectParam(true, 30000, 500);
      int company = 24;
      int device = 0;
      int softversion = 0;
      int bus = 1;
      int index = 1;
      robot.FT_SetConfig(company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_GetConfig(&company, &device, &softversion, &bus);
      printf("FT config:%d,%d,%d,%d\n", company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_Activate(0);
      robot.Sleep(1000);
      robot.FT_Activate(1);
      robot.Sleep(1000);
      robot.Sleep(1000);
      robot.FT_SetZero(0);
      robot.Sleep(1000);
      uint8_t status = 1;
      int sensor_num = 1;
      float gain[6] = { 0.0001,0.0,0.0,0.0,0.0,0.0 };
      uint8_t adj_sign = 0;
      uint8_t ILC_sign = 0;
      float max_dis = 100.0;
      float max_ang = 5.0;
      ForceTorque ft;
      memset(&ft, 0, sizeof(ForceTorque));
      int rcs = 0;
      float dr = 0.7;
      float fFinish = 1.0;
      float t = 60000.0;
      float vmax = 3.0;
      float force_goal = 20.0;
      float lin_v = 0.0;
      float lin_a = 0.0;
      float disMax = 100.0;
      uint8_t linorn = 1;
      float angVelRot = 2.0;
      float forceInsertion = 1.0;
      int angleMax = 45;
      uint8_t orn = 1;
      float angAccmax = 0.0;
      uint8_t rotorn = 1;
      uint8_t select1[6] = { 0,0,1,1,1,0 };
      ft.fz = -10.0;
      robot.FT_Control(status, sensor_num, select1, &ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
      rtn = robot.FT_SpiralSearch(rcs, dr, fFinish, t, vmax);
      printf("FT_SpiralSearch rtn is %d\n", rtn);
      status = 0;
      robot.FT_Control(status, sensor_num, select1, &ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
      uint8_t select2[6] = { 1,1,1,0,0,0 };
      gain[0] = 0.00005;
      ft.fz = -30.0;
      status = 1;
      robot.FT_Control(status, sensor_num, select2, &ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
      rtn = robot.FT_LinInsertion(rcs, force_goal, lin_v, lin_a, disMax, linorn);
      printf("FT_LinInsertion rtn is %d\n", rtn);
      status = 0;
      robot.FT_Control(status, sensor_num, select2, &ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
      uint8_t select3[6] = { 0,0,1,1,1,0 };
      ft.fz = -10.0;
      gain[0] = 0.0001;
      status = 1;
      robot.FT_Control(status, sensor_num, select3, &ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
      rtn = robot.FT_RotInsertion(rcs, angVelRot, forceInsertion, angleMax, orn, angAccmax, rotorn);
      printf("FT_RotInsertion rtn is %d\n", rtn);
      status = 0;
      robot.FT_Control(status, sensor_num, select3, &ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
      uint8_t select4[6] = { 1,1,1,0,0,0 };
      ft.fz = -30.0;
      status = 1;
      robot.FT_Control(status, sensor_num, select4, &ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
      rtn = robot.FT_LinInsertion(rcs, force_goal, lin_v, lin_a, disMax, linorn);
      printf("FT_LinInsertion rtn is %d\n", rtn);
      status = 0;
      robot.FT_Control(status, sensor_num, select4, &ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
      robot.CloseRPC();
      return 0;
    }

Lokalizacja powierzchni
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Lokalizacja powierzchni
    * @param  [in] rcs Układ odniesienia, 0-układ współrzędnych narzędzia, 1-układ współrzędnych bazowych
    * @param  [in] dir  Kierunek ruchu, 1-kierunek dodatni, 2-kierunek ujemny
    * @param  [in] axis Oś ruchu, 1-oś x, 2-oś y, 3-oś z
    * @param  [in] lin_v Prędkość liniowa eksploracji, jednostka mm/s
    * @param  [in] lin_a Przyspieszenie liniowe eksploracji, jednostka mm/s^2, tymczasowo nieużywane, domyślnie 0
    * @param  [in] max_dis Maksymalna odległość eksploracji, jednostka mm
    * @param  [in] ft  Próg siły/momentu zakończenia działania, fx, fy, fz, tx, ty, tz
    * @return   Kod błędu
    */
    errno_t  FT_FindSurface(int rcs, uint8_t dir, uint8_t axis, float lin_v, float lin_a, float max_dis, float ft);

Rozpoczęcie obliczania pozycji płaszczyzny środkowej
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Rozpoczęcie obliczania pozycji płaszczyzny środkowej
    * @return   Kod błędu
    */
    errno_t  FT_CalCenterStart();

Zakończenie obliczania pozycji płaszczyzny środkowej
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Zakończenie obliczania pozycji płaszczyzny środkowej
    * @param  [out] pos Pozy i orientacja płaszczyzny środkowej
    * @return   Kod błędu
    */
    errno_t  FT_CalCenterEnd(DescPose *pos);

Przykład kodu lokalizacji powierzchni
+++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestSurface(void)
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      robot.LoggerInit();
      robot.SetLoggerLevel(1);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return -1;
      }
      robot.SetReConnectParam(true, 30000, 500);
      int company = 24;
      int device = 0;
      int softversion = 0;
      int bus = 1;
      int index = 1;
      robot.FT_SetConfig(company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_GetConfig(&company, &device, &softversion, &bus);
      printf("FT config:%d,%d,%d,%d\n", company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_Activate(0);
      robot.Sleep(1000);
      robot.FT_Activate(1);
      robot.Sleep(1000);
      robot.Sleep(1000);
      robot.FT_SetZero(0);
      robot.Sleep(1000);
      int rcs = 0;
      uint8_t dir = 1;
      uint8_t axis = 1;
      float lin_v = 3.0;
      float lin_a = 0.0;
      float maxdis = 50.0;
      float ft_goal = 2.0;
      DescPose desc_pos(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
      DescPose xcenter(0, 0, 0, 0, 0, 0);
      DescPose ycenter(0, 0, 0, 0, 0, 0);
      ForceTorque ft;
      memset(&ft, 0, sizeof(ForceTorque));
      ft.fx = -2.0;
      robot.MoveCart(&desc_pos, 9, 0, 100.0, 100.0, 100.0, -1.0, -1);
      robot.FT_CalCenterStart();
      robot.FT_FindSurface(rcs, dir, axis, lin_v, lin_a, maxdis, ft_goal);
      robot.MoveCart(&desc_pos, 9, 0, 100.0, 100.0, 100.0, -1.0, -1);
      robot.WaitMs(1000);
      dir = 2;
      robot.FT_FindSurface(rcs, dir, axis, lin_v, lin_a, maxdis, ft_goal);
      robot.FT_CalCenterEnd(&xcenter);
      printf("xcenter:%f,%f,%f,%f,%f,%f\n", xcenter.tran.x, xcenter.tran.y, xcenter.tran.z, xcenter.rpy.rx, xcenter.rpy.ry, xcenter.rpy.rz);
      robot.MoveCart(&xcenter, 9, 0, 60.0, 50.0, 50.0, -1.0, -1);
      robot.FT_CalCenterStart();
      dir = 1;
      axis = 2;
      lin_v = 6.0;
      maxdis = 150.0;
      robot.FT_FindSurface(rcs, dir, axis, lin_v, lin_a, maxdis, ft_goal);
      robot.MoveCart(&desc_pos, 9, 0, 100.0, 100.0, 100.0, -1.0, -1);
      robot.WaitMs(1000);
      dir = 2;
      robot.FT_FindSurface(rcs, dir, axis, lin_v, lin_a, maxdis, ft_goal);
      robot.FT_CalCenterEnd(&ycenter);
      printf("ycenter:%f,%f,%f,%f,%f,%f\n", ycenter.tran.x, ycenter.tran.y, ycenter.tran.z, ycenter.rpy.rx, ycenter.rpy.ry, ycenter.rpy.rz);
      robot.MoveCart(&ycenter, 9, 0, 60.0, 50.0, 50.0, 0.0, -1);
      robot.CloseRPC();
      return 0;
    }

Włączenie sterowania podatnego
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Włączenie sterowania podatnego
    * @param  [in] p Współczynnik regulacji pozycji lub współczynnik podatności
    * @param  [in] force Próg siły włączenia podatności, jednostka N
    * @return   Kod błędu
    */
    errno_t  FT_ComplianceStart(float p, float force);

Wyłączenie sterowania podatnego
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Wyłączenie sterowania podatnego
    * @return   Kod błędu
    */
    errno_t  FT_ComplianceStop();

Przykład kodu sterowania podatnego
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestCompliance(void)
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      robot.LoggerInit();
      robot.SetLoggerLevel(1);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return -1;
      }
      robot.SetReConnectParam(true, 30000, 500);
      int company = 24;
      int device = 0;
      int softversion = 0;
      int bus = 1;
      int index = 1;
      robot.FT_SetConfig(company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_GetConfig(&company, &device, &softversion, &bus);
      printf("FT config:%d,%d,%d,%d\n", company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_Activate(0);
      robot.Sleep(1000);
      robot.FT_Activate(1);
      robot.Sleep(1000);
      robot.Sleep(1000);
      robot.FT_SetZero(0);
      robot.Sleep(1000);
      uint8_t flag = 1;
      int sensor_id = 1;
      uint8_t select[6] = { 1,1,1,0,0,0 };
      float ft_pid[6] = { 0.0005,0.0,0.0,0.0,0.0,0.0 };
      uint8_t adj_sign = 0;
      uint8_t ILC_sign = 0;
      float max_dis = 100.0;
      float max_ang = 0.0;
      ForceTorque ft;
      DescPose offset_pos(0, 0, 0, 0, 0, 0);
      ExaxisPos epos(0, 0, 0, 0);
      memset(&ft, 0, sizeof(ForceTorque));
      JointPos j1(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
      JointPos j2(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
      DescPose desc_p1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
      DescPose desc_p2(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
      ft.fx = -10.0;
      ft.fy = -10.0;
      ft.fz = -10.0;
      robot.FT_Control(flag, sensor_id, select, &ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
      float p = 0.00005;
      float force = 30.0;
      rtn = robot.FT_ComplianceStart(p, force);
      printf("FT_ComplianceStart rtn is %d\n", rtn);
      int count = 15;
      while (count)
      {
        robot.MoveL(&j1, &desc_p1, 0, 0, 100.0, 180.0, 100.0, -1.0, &epos, 0, 1, &offset_pos);
        robot.MoveL(&j2, &desc_p2, 0, 0, 100.0, 180.0, 100.0, -1.0, &epos, 0, 0, &offset_pos);
        count -= 1;
      }
      robot.FT_ComplianceStop();
      printf("FT_ComplianceStop rtn is %d\n", rtn);
      flag = 0;
      robot.FT_Control(flag, sensor_id, select, &ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
      robot.CloseRPC();
      return 0;
    }

Inicjalizacja filtracji dynamicznej identyfikacji obciążenia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Inicjalizacja filtracji dynamicznej identyfikacji obciążenia
    * @return Kod błędu
    */
    errno_t LoadIdentifyDynFilterInit();

Inicjalizacja zmiennych dynamicznych identyfikacji obciążenia
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Inicjalizacja zmiennych dynamicznych identyfikacji obciążenia
    * @return Kod błędu
    */
    errno_t LoadIdentifyDynVarInit();

Program główny identyfikacji obciążenia
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Program główny identyfikacji obciążenia
    * @param [in] joint_torque Moment stawów
    * @param [in] joint_pos Pozycja stawów
    * @param [in] t Okres próbkowania
    * @return Kod błędu
    */
    errno_t LoadIdentifyMain(double joint_torque[6], double joint_pos[6], double t);

Pobieranie wyniku identyfikacji obciążenia
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Pobieranie wyniku identyfikacji obciążenia
    * @param [in] gain
    * @param [out] weight Masa obciążenia
    * @param [out] cog Środek ciężkości obciążenia
    * @return Kod błędu
    */
    errno_t LoadIdentifyGetResult(double gain[12], double *weight, DescTran *cog);

Przykład kodu identyfikacji obciążenia robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestIdentify(void)
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      robot.LoggerInit();
      robot.SetLoggerLevel(1);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return -1;
      }
      robot.SetReConnectParam(true, 30000, 500);
      int retval = 0;
      retval = robot.LoadIdentifyDynFilterInit();
      printf("LoadIdentifyDynFilterInit retval is: %d \n", retval);
      retval = robot.LoadIdentifyDynVarInit();
      printf("LoadIdentifyDynVarInit retval is: %d \n", retval);
      JointPos posJ = {};
      DescPose posDec = {};
      float joint_toq[6] = { 0.0 };
      robot.GetActualJointPosDegree(0, &posJ);
      posJ.jPos[1] = posJ.jPos[1] + 10;
      robot.GetJointTorques(0, joint_toq);
      joint_toq[1] = joint_toq[1] + 2;
      double tmpTorque[6] = { 0.0 };
      for (int i = 0; i < 6; i++)
      {
        tmpTorque[i] = joint_toq[i];
      }
      retval = robot.LoadIdentifyMain(tmpTorque, posJ.jPos, 1);
      printf("LoadIdentifyMain retval is: %d \n", retval);
      double gain[12] = { 0,0.05,0,0,0,0,0,0.02,0,0,0,0 };
      double weight = 0;
      DescTran load_pos;
      memset(&load_pos, 0, sizeof(DescTran));
      retval = robot.LoadIdentifyGetResult(gain, &weight, &load_pos);
      printf("LoadIdentifyGetResult retval is: %d ; weight is %f cog is %f %f %f \n", retval, weight, load_pos.x, load_pos.y, load_pos.z);
      robot.CloseRPC();
      return 0;
    }

Wspomaganie przeciągania przez czujnik siły
++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.2.0-3.8.0

.. code-block:: c++
    :linenos:

    /**
    * @brief  Wspomaganie przeciągania przez czujnik siły
    * @param  [in] status Stan sterowania, 0-wyłączone; 1-włączone
    * @param  [in] asaptiveFlag Flaga włączenia adaptacji, 0-wyłączona; 1-włączona
    * @param  [in] interfereDragFlag Flaga przeciągania w obszarze interferencji, 0-wyłączona; 1-włączona
    * @param  [in] ingularityConstraintsFlag Strategia punktów osobliwych, 0-omijanie; 1-przechodzenie
    * @param  [in] forceCollisionFlag Flaga wykrywania kolizji robota podczas wspomaganego przeciągania; 0-wyłączona; 1-włączona
    * @param  [in] M Współczynnik bezwładności
    * @param  [in] B Współczynnik tłumienia
    * @param  [in] K Współczynnik sztywności
    * @param  [in] F Próg sześcioosiowej siły przeciągania
    * @param  [in] Fmax Maksymalne ograniczenie siły przeciągania
    * @param  [in] Vmax Maksymalne ograniczenie prędkości stawów
    * @return   Kod błędu
    */
    errno_t EndForceDragControl(int status, int asaptiveFlag, int interfereDragFlag, int ingularityConstraintsFlag, int forceCollisionFlag, std::vector<double> M, std::vector<double> B, std::vector<double> K, std::vector<double> F, double Fmax, double Vmax);

Pobieranie stanu przełącznika przeciągania dla czujnika siły
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Pobiera stan przełącznika przeciągania dla czujnika siły
     * @param [out] dragState Stan sterowania wspomaganiem przeciągania przez czujnik siły, 0-wyłączone; 1-włączone
     * @param [out] sixDimensionalDragState Stan sterowania wspomaganiem przeciągania przez siłę sześcioosiową, 0-wyłączone; 1-włączone
     * @return Kod błędu
     */
    errno_t GetForceAndTorqueDragState(int& dragState, int& sixDimensionalDragState);

Automatyczne włączanie czujnika siły po wyczyszczeniu błędu
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Automatyczne włączanie czujnika siły po wyczyszczeniu błędu
     * @param [in] status Stan sterowania, 0-wyłączone; 1-włączone
     * @return Kod błędu
     */
    errno_t SetForceSensorDragAutoFlag(int status);

Przykład kodu wspomagania przeciągania przez czujnik siły
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     int TestEndForceDragCtrl(void)
     {
         ROBOT_STATE_PKG pkg = {};
         FRRobot robot;
         robot.LoggerInit();
         robot.SetLoggerLevel(1);
         int rtn = robot.RPC("192.168.58.2");
         if (rtn != 0)
         {
             return -1;
         }
         robot.SetReConnectParam(true, 30000, 500);
         robot.SetForceSensorDragAutoFlag(1);
         vector <double> M = { 15.0, 15.0, 15.0, 0.5, 0.5, 0.1 };
         vector <double> B = { 150.0, 150.0, 150.0, 5.0, 5.0, 1.0 };
         vector <double> K = { 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 };
         vector <double> F = { 10.0, 10.0, 10.0, 1.0, 1.0, 1.0 };
         robot.EndForceDragControl(1, 0, 0, 0, 1, M, B, K, F, 50, 100);
         robot.Sleep(5000);
         int dragState = 0;
         int sixDimensionalDragState = 0;
         robot.GetForceAndTorqueDragState(dragState, sixDimensionalDragState);
         printf("the drag state is %d %d \n", dragState, sixDimensionalDragState);
         robot.EndForceDragControl(0, 0, 0, 0, 1, M, B, K, F, 50, 100);
         robot.CloseRPC();
         return 0;
     }

Ustawianie przełącznika i parametrów mieszanego przeciągania z wykorzystaniem siły sześcioosiowej i impedancji stawów
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Ustawia przełącznik i parametry mieszanego przeciągania z wykorzystaniem siły sześcioosiowej i impedancji stawów
     * @param [in] status Stan sterowania, 0-wyłączone; 1-włączone
     * @param [in] impedanceFlag Flaga włączenia impedancji, 0-wyłączona; 1-włączona
     * @param [in] lamdeDain Wzmocnienie przeciągania
     * @param [in] KGain Wzmocnienie sztywności
     * @param [in] BGain Wzmocnienie tłumienia
     * @param [in] dragMaxTcpVel Maksymalne ograniczenie prędkości liniowej końcówki podczas przeciągania
     * @param [in] dragMaxTcpOriVel Maksymalne ograniczenie prędkości kątowej końcówki podczas przeciągania
     * @return Kod błędu
     */
    errno_t ForceAndJointImpedanceStartStop(int status, int impedanceFlag, std::vector<double> lamdeDain, std::vector<double> KGain, std::vector<double> BGain, double dragMaxTcpVel, double dragMaxTcpOriVel);

Przykład kodu mieszanego przeciągania z wykorzystaniem siły sześcioosiowej i impedancji stawów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    int TestForceAndJointImpedance(void)
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      robot.LoggerInit();
      robot.SetLoggerLevel(1);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return -1;
      }
      robot.SetReConnectParam(true, 30000, 500);
      robot.DragTeachSwitch(1);
      vector <double> lamdeDain = { 3.0, 2.0, 2.0, 2.0, 2.0, 3.0 };
      vector <double> KGain = { 0, 0, 0, 0, 0, 0 };
      vector <double> BGain = { 150, 150, 150, 5.0, 5.0, 1.0 };
      rtn = robot.ForceAndJointImpedanceStartStop(1, 0, lamdeDain, KGain, BGain, 1000, 180);
      printf("ForceAndJointImpedanceStartStop rtn is %d\n", rtn);
      robot.Sleep(5000);
      robot.DragTeachSwitch(0);
      rtn = robot.ForceAndJointImpedanceStartStop(0, 0, lamdeDain, KGain, BGain, 1000, 180);
      printf("ForceAndJointImpedanceStartStop rtn is %d\n", rtn);
      robot.CloseRPC();
      return 0;
    }

Sterowanie uruchamianiem/zatrzymywaniem impedancji
++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
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
    errno_t ImpedanceControlStartStop(int status, int workSpace, double forceThreshold[6], double m[6], double b[6], double k[6], double maxV, double maxVA, double maxW, double maxWA);

Przykład kodu sterowania uruchamianiem/zatrzymywaniem impedancji robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    int TestImpedanceControl()
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      uint8_t ctrl[20];
      uint8_t state;
      int pressVlaue;
      int error;
      robot.CloseRPC();
      robot.LoggerInit();
      robot.SetLoggerLevel(1);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return 0;
      }
      robot.SetReConnectParam(true, 30000, 500);
      JointPos j1(102.622, -135.990, 120.769, -73.950, -90.848, 35.507);
      JointPos j2(93.674, -80.062, 82.947, -92.199, -90.967, 26.559);
      DescPose desc_pos1(136.552, -149.799, 449.532, 179.817, -1.172, 157.123);
      DescPose desc_pos2(136.540, -561.048, 449.542, 179.819, -1.172, 157.122);
      DescPose offset_pos(0, 0, 0, 0, 0, 0);
      ExaxisPos epos(0, 0, 0, 0);
      int tool = 0;
      int user = 0;
      float vel = 100.0;
      float acc = 200.0;
      float ovl = 100.0;
      float blendT = -1.0;
      float blendR = -1.0;
      uint8_t flag = 0;
      uint8_t search = 0;
      robot.SetSpeed(20);
      int company = 17;
      int device = 0;
      int softversion = 0;
      int bus = 1;
      robot.FT_SetConfig(company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_GetConfig(&company, &device, &softversion, &bus);
      printf("FT config:%d,%d,%d,%d\n", company, device, softversion, bus);
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
      double forceThreshold[6] = { 30,30,30,5,5,5 };
      double m[6] = { 0.1,0.1,0.1,0.02,0.02,0.02 };
      double b[6] = { 1,1,1,0.08,0.08,0.08 };
      double k[6] = { 0,0,0,0,0,0 };
      rtn = robot.ImpedanceControlStartStop(1, 1, forceThreshold, m, b, k, 1000, 500, 100, 100);
      printf("ImpedanceControlStartStop errcode:%d\n", rtn);
      rtn = robot.MoveL(&desc_pos1, tool, user, vel, acc, ovl, blendR, 0, &epos, search, flag, &offset_pos, -1, 1);
      rtn = robot.MoveL(&desc_pos2, tool, user, vel, acc, ovl, blendR, 0, &epos, search, flag, &offset_pos, -1, 1);
      rtn = robot.MoveL(&desc_pos1, tool, user, vel, acc, ovl, blendR, 0, &epos, search, flag, &offset_pos, -1, 1);
      rtn = robot.MoveL(&desc_pos2, tool, user, vel, acc, ovl, blendR, 0, &epos, search, flag, &offset_pos, -1, 1);
      printf("movel errcode:%d\n", rtn);
      robot.ImpedanceControlStartStop(0, 1, forceThreshold, m, b, k, 1000, 500, 100, 100);
      robot.CloseRPC();
      return 0;
    }

Włączanie funkcji kompensacji momentu i współczynnik kompensacji
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Włączanie funkcji kompensacji momentu i współczynnik kompensacji
    * @param [in] status Przełącznik, 0-wyłączone; 1-włączone
    * @param [in] torqueCoeff Współczynniki kompensacji momentu dla J1-J6 [0-1]
    * @return Kod błędu
    */
    errno_t SerCoderCompenParams(int status, double torqueCoeff[6]);