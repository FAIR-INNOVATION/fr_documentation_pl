Zapytanie o stan robota
=======================

.. toctree::
    :maxdepth: 5

Pobieranie bieżącej pozycji stawów (kąt)
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Pobiera bieżącą pozycję stawów (kąt)
    * @param  [in] flag 0-blokujący, 1-nieblokujący
    * @param  [out] jPos Pozycje sześciu stawów, jednostka deg
    * @return  Kod błędu
    */
    errno_t  GetActualJointPosDegree(uint8_t flag, JointPos *jPos);

Pobieranie prędkości sprzężenia zwrotnego stawów
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Pobiera prędkość sprzężenia zwrotnego stawów - deg/s
     * @param  [in] flag 0-blokujący, 1-nieblokujący
     * @param  [out] speed Prędkości sześciu stawów
     * @return  Kod błędu
     */
    errno_t  GetActualJointSpeedsDegree(uint8_t flag, float speed[6]);

Pobieranie przyspieszenia sprzężenia zwrotnego stawów
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Pobiera przyspieszenie sprzężenia zwrotnego stawów - deg/s^2
     * @param  [in] flag 0-blokujący, 1-nieblokujący
     * @param  [out] acc Przyspieszenia sześciu stawów
     * @return  Kod błędu
     */
    errno_t  GetActualJointAccDegree(uint8_t flag, float acc[6]);

Pobieranie prędkości wypadkowej zadanej TCP
+++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Pobiera prędkość wypadkową zadaną TCP
     * @param  [in] flag 0-blokujący, 1-nieblokujący
     * @param  [out] tcp_speed Prędkość liniowa
     * @param  [out] ori_speed Prędkość kątowa
     * @return  Kod błędu
     */
    errno_t  GetTargetTCPCompositeSpeed(uint8_t flag, float *tcp_speed, float *ori_speed);

Pobieranie prędkości wypadkowej sprzężenia zwrotnego TCP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Pobiera prędkość wypadkową sprzężenia zwrotnego TCP
     * @param  [in] flag 0-blokujący, 1-nieblokujący
     * @param  [out] tcp_speed Prędkość liniowa
     * @param  [out] ori_speed Prędkość kątowa
     * @return  Kod błędu
     */
    errno_t  GetActualTCPCompositeSpeed(uint8_t flag, float *tcp_speed, float *ori_speed);

Pobieranie prędkości zadanej TCP
++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Pobiera prędkość zadaną TCP
     * @param  [in] flag 0-blokujący, 1-nieblokujący
     * @param  [out] speed Prędkość [x, y, z, rx, ry, rz]
     * @return  Kod błędu
     */
    errno_t  GetTargetTCPSpeed(uint8_t flag, float speed[6]);

Pobieranie prędkości sprzężenia zwrotnego TCP
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Pobiera prędkość sprzężenia zwrotnego TCP
     * @param  [in] flag 0-blokujący, 1-nieblokujący
     * @param  [out] speed Prędkość [x, y, z, rx, ry, rz]
     * @return  Kod błędu
     */
    errno_t  GetActualTCPSpeed(uint8_t flag, float speed[6]);

Pobieranie bieżącej pozy i orientacji narzędzia
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Pobiera bieżącą pozy i orientację narzędzia
    * @param  [in] flag  0-blokujący, 1-nieblokujący
    * @param  [out] desc_pos  Pozy i orientacja narzędzia
    * @return  Kod błędu
    */
    errno_t  GetActualTCPPose(uint8_t flag, DescPose *desc_pos);

Pobieranie numeru bieżącego układu współrzędnych narzędzia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Pobiera numer bieżącego układu współrzędnych narzędzia
    * @param  [in] flag  0-blokujący, 1-nieblokujący
    * @param  [out] id  Numer układu współrzędnych narzędzia
    * @return  Kod błędu
    */
    errno_t  GetActualTCPNum(uint8_t flag, int *id);

Pobieranie numeru bieżącego układu współrzędnych obiektu
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Pobiera numer bieżącego układu współrzędnych obiektu
    * @param  [in] flag  0-blokujący, 1-nieblokujący
    * @param  [out] id  Numer układu współrzędnych obiektu
    * @return  Kod błędu
    */
    errno_t  GetActualWObjNum(uint8_t flag, int *id);

Pobieranie bieżącej pozy i orientacji kołnierza końcowego
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Pobiera bieżącą pozy i orientację kołnierza końcowego
    * @param  [in] flag  0-blokujący, 1-nieblokujący
    * @param  [out] desc_pos  Pozy i orientacja kołnierza
    * @return  Kod błędu
    */
    errno_t  GetActualToolFlangePose(uint8_t flag, DescPose *desc_pos);

Pobieranie bieżącego momentu stawów
+++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera bieżący moment stawów
    * @param  [in] flag 0-blokujący, 1-nieblokujący
    * @param  [out] torques Momenty stawów
    * @return  Kod błędu
    */
    errno_t  GetJointTorques(uint8_t flag, float torques[6]);

Pobieranie czasu systemowego
++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Pobiera czas systemowy
    * @param  [out] t_ms Jednostka ms
    * @return  Kod błędu
    */
    errno_t  GetSystemClock(float *t_ms);

Sprawdzanie, czy ruch robota został zakończony
++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Sprawdza, czy ruch robota został zakończony
    * @param  [out]  state  0-niezakończony, 1-zakończony
    * @return  Kod błędu
    */
    errno_t  GetRobotMotionDone(uint8_t *state);

Sprawdzanie długości bufora kolejki ruchu robota
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Sprawdza długość bufora kolejki ruchu robota
     * @param  [out]  len  Długość bufora
     * @return  Kod błędu
     */
    errno_t  GetMotionQueueLength(int *len);

Pobieranie stanu awaryjnego zatrzymania robota
++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera stan awaryjnego zatrzymania robota
    * @param [out] state Stan awaryjnego zatrzymania, 0-brak, 1-awaryjne zatrzymanie
    * @return Kod błędu
    */
    errno_t GetRobotEmergencyStopState(uint8_t *state);

Pobieranie stanu komunikacji SDK z robotem
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera stan komunikacji SDK z robotem
    * @param [out] state Stan komunikacji, 0-komunikacja normalna, 1-komunikacja nieprawidłowa
    */
    errno_t GetSDKComState(int *state);

Pobieranie sygnału bezpiecznego zatrzymania
+++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera sygnał bezpiecznego zatrzymania
    * @param [out] si0_state Sygnał bezpiecznego zatrzymania SI0, 0-nieaktywny, 1-aktywny
    * @param [out] si1_state Sygnał bezpiecznego zatrzymania SI1, 0-nieaktywny, 1-aktywny
    */
    errno_t GetSafetyStopState(uint8_t *si0_state, uint8_t *si1_state);

Pobieranie temperatury sterownika stawów robota (℃)
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera temperaturę sterownika stawów robota (℃)
    * @return Kod błędu
    */
    errno_t GetJointDriverTemperature(double temperature[]);

Pobieranie momentu sterownika stawów robota (Nm)
++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera moment sterownika stawów robota (Nm)
    * @return Kod błędu
    */
    errno_t GetJointDriverTorque(double torque[]);

Pobieranie struktury stanu robota w czasie rzeczywistym
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera strukturę stanu robota w czasie rzeczywistym
    * @param [out] pkg Struktura stanu robota w czasie rzeczywistym
    * @return Kod błędu
    */
    errno_t GetRobotRealTimeState(ROBOT_STATE_PKG *pkg);

Przykład kodu zapytania o stan robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestGetStatus(void)
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
      float yangle, zangle;
      robot.GetRobotInstallAngle(&yangle, &zangle);
      printf("yangle:%f,zangle:%f\n", yangle, zangle);
      JointPos j_deg = {};
      robot.GetActualJointPosDegree(0, &j_deg);
      printf("joint pos deg:%f,%f,%f,%f,%f,%f\n", j_deg.jPos[0], j_deg.jPos[1], j_deg.jPos[2], j_deg.jPos[3], j_deg.jPos[4], j_deg.jPos[5]);
      float jointSpeed[6] = { 0.0 };
      robot.GetActualJointSpeedsDegree(0, jointSpeed);
      printf("joint speeds deg:%f,%f,%f,%f,%f,%f\n", jointSpeed[0], jointSpeed[1], jointSpeed[2], jointSpeed[3], jointSpeed[4], jointSpeed[5]);
      float jointAcc[6] = { 0.0 };
      robot.GetActualJointAccDegree(0, jointAcc);
      printf("joint acc deg:%f,%f,%f,%f,%f,%f\n", jointAcc[0], jointAcc[1], jointAcc[2], jointAcc[3], jointAcc[4], jointAcc[5]);
      float tcp_speed = 0.0;
      float ori_speed = 0.0;
      robot.GetTargetTCPCompositeSpeed(0, &tcp_speed, &ori_speed);
      printf("GetTargetTCPCompositeSpeed tcp %f; ori %f\n", tcp_speed, ori_speed);
      robot.GetActualTCPCompositeSpeed(0, &tcp_speed, &ori_speed);
      printf("GetActualTCPCompositeSpeed tcp %f; ori %f\n", tcp_speed, ori_speed);
      float targetSpeed[6] = { 0.0 };
      robot.GetTargetTCPSpeed(0, targetSpeed);
      printf("GetTargetTCPSpeed %f,%f,%f,%f,%f,%f\n", targetSpeed[0], targetSpeed[1], targetSpeed[2], targetSpeed[3], targetSpeed[4], targetSpeed[5]);
      float actualSpeed[6] = { 0.0 };
      robot.GetActualTCPSpeed(0, actualSpeed);
      printf("GetTargetTCPSpeed %f,%f,%f,%f,%f,%f\n", actualSpeed[0], actualSpeed[1], actualSpeed[2], actualSpeed[3], actualSpeed[4], actualSpeed[5]);
      DescPose tcp = {};
      robot.GetActualTCPPose(0, &tcp);
      printf("tcp pose:%f,%f,%f,%f,%f,%f\n", tcp.tran.x, tcp.tran.y, tcp.tran.z, tcp.rpy.rx, tcp.rpy.ry, tcp.rpy.rz);
      DescPose flange = {};
      robot.GetActualToolFlangePose(0, &flange);
      printf("flange pose:%f,%f,%f,%f,%f,%f\n", flange.tran.x, flange.tran.y, flange.tran.z, flange.rpy.rx, flange.rpy.ry, flange.rpy.rz);
      int id = 0;
      robot.GetActualTCPNum(0, &id);
      printf("tcp num:%d\n", id);
      robot.GetActualWObjNum(0, &id);
      printf("wobj num:%d\n", id);
      float jtorque[6] = { 0.0 };
      robot.GetJointTorques(0, jtorque);
      printf("torques:%f,%f,%f,%f,%f,%f\n", jtorque[0], jtorque[1], jtorque[2], jtorque[3], jtorque[4], jtorque[5]);
      float t_ms = 0.0;
      robot.GetSystemClock(&t_ms);
      printf("system clock:%f\n", t_ms);
      int config = 0;
      robot.GetRobotCurJointsConfig(&config);
      printf("joint config:%d\n", config);
      uint8_t motionDone = 0;
      robot.GetRobotMotionDone(&motionDone);
      printf("GetRobotMotionDone :%d\n", motionDone);
      int len = 0;
      robot.GetMotionQueueLength(&len);
      printf("GetMotionQueueLength :%d\n", len);
      uint8_t emergState = 0;
      robot.GetRobotEmergencyStopState(&emergState);
      printf("GetRobotEmergencyStopState :%d\n", emergState);
      int comstate = 0;
      robot.GetSDKComState(&comstate);
      printf("GetSDKComState :%d\n", comstate);
      uint8_t si0_state, si1_state;
      robot.GetSafetyStopState(&si0_state, &si1_state);
      printf("GetSafetyStopState :%d %d\n", si0_state, si1_state);
      double temp[6] = { 0.0 };
      robot.GetJointDriverTemperature(temp);
      printf("Temperature:%f,%f,%f,%f,%f,%f\n", temp[0], temp[1], temp[2], temp[3], temp[4], temp[5]);
      double torque[6] = { 0.0 };
      robot.GetJointDriverTorque(torque);
      printf("torque:%f,%f,%f,%f,%f,%f\n", torque[0], torque[1], torque[2], torque[3], torque[4], torque[5]);
      robot.GetRobotRealTimeState(&pkg);
      robot.CloseRPC();
      return 0;
    }

Rozwiązanie odwrotnej kinematyki
++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Rozwiązanie odwrotnej kinematyki
    * @param  [in] type 0-pozycja absolutna (układ bazowy), 1-pozycja przyrostowa (układ bazowy), 2-pozycja przyrostowa (układ narzędzia)
    * @param  [in] desc_pos Pozy i orientacja kartezjańska
    * @param  [in] config Konfiguracja przestrzeni stawów, [-1]-obliczenia w oparciu o bieżącą pozycję stawów, [0~7]-obliczenia zgodnie z określoną konfiguracją przestrzeni stawów
    * @param  [out] joint_pos Pozycja stawów
    * @return  Kod błędu
    */
    errno_t  GetInverseKin(int type, DescPose *desc_pos, int config, JointPos *joint_pos);

Rozwiązanie odwrotnej kinematyki (z pozycją odniesienia)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Rozwiązanie odwrotnej kinematyki, z uwzględnieniem zadanej pozycji stawów
    * @param  [in] type 0-pozycja absolutna (układ bazowy), 1-pozycja przyrostowa (układ bazowy), 2-pozycja przyrostowa (układ narzędzia)
    * @param  [in] desc_pos Pozy i orientacja kartezjańska
    * @param  [in] joint_pos_ref Referencyjna pozycja stawów
    * @param  [out] joint_pos Pozycja stawów
    * @return  Kod błędu
    */
    errno_t  GetInverseKinRef(int type, DescPose *desc_pos, JointPos *joint_pos_ref, JointPos *joint_pos);

Rozwiązanie odwrotnej kinematyki z pozycją osi rozszerzonej w przestrzeni kartezjańskiej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Rozwiązanie odwrotnej kinematyki z pozycją osi rozszerzonej w przestrzeni kartezjańskiej
    * @param [in] type 0-pozycja absolutna (układ bazowy), 1-pozycja przyrostowa (układ bazowy), 2-pozycja przyrostowa (układ narzędzia)
    * @param [in] desc_pos Pozy i orientacja kartezjańska
    * @param [in] exaxis Pozycja osi rozszerzonej
    * @param [in] tool Numer narzędzia
    * @param [in] workPiece Numer obiektu
    * @param [out] joint_pos Pozycja stawów
    * @return Kod błędu
    */
    errno_t GetInverseKinExaxis(int type, DescPose desc_pos, ExaxisPos exaxis, int tool, int workPiece, JointPos& joint_pos);

Przykład kodu rozwiązania odwrotnej kinematyki z pozycją osi rozszerzonej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestInverseKinExaxis()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return 0;
        }
        robot.SetReConnectParam(true, 30000, 500);
        DescPose desc(99.957, -0.002, 29.994, -176.569, -6.757, -167.462);
        ExaxisPos exaxis(100.0, 0.0, 0.0, 0.0);
        JointPos jointPos = {};
        DescPose offsetPos = {};
        robot.GetRobotRealTimeState(&pkg);
        int toolnum = pkg.tool;
        int workPcsNum = pkg.user;
        robot.GetInverseKinExaxis(0, desc, exaxis, toolnum, workPcsNum, jointPos);
        printf("GetInverseKinExaxis joint is %f, %f, %f, %f, %f, %f\n", jointPos.jPos[0], jointPos.jPos[1], jointPos.jPos[2], jointPos.jPos[3], jointPos.jPos[4], jointPos.jPos[5]);
        robot.ExtAxisMove(exaxis, 100, -1);
        robot.MoveJ(&jointPos, &desc, toolnum, workPcsNum, 100.0, 100.0, 100.0, &exaxis, -1, 0, &offsetPos);
        robot.CloseRPC();
        robot.Sleep(9999999);
        return 0;
    }

Sprawdzanie, czy odwrotna kinematyka ma rozwiązanie
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Sprawdza, czy odwrotna kinematyka ma rozwiązanie, z uwzględnieniem zadanej pozycji stawów
    * @param  [in] type 0-pozycja absolutna (układ bazowy), 1-pozycja przyrostowa (układ bazowy), 2-pozycja przyrostowa (układ narzędzia)
    * @param  [in] desc_pos Pozy i orientacja kartezjańska
    * @param  [in] joint_pos_ref Referencyjna pozycja stawów
    * @param  [out] result 0-brak rozwiązania, 1-jest rozwiązanie
    * @return  Kod błędu
    */
    errno_t  GetInverseKinHasSolution(int type, DescPose *desc_pos, JointPos *joint_pos_ref, uint8_t *result);

Rozwiązanie prostej kinematyki
++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Rozwiązanie prostej kinematyki
    * @param  [in] joint_pos Pozycja stawów
    * @param  [out] desc_pos Pozy i orientacja kartezjańska
    * @return  Kod błędu
    */
    errno_t  GetForwardKin(JointPos *joint_pos, DescPose *desc_pos);

Przykład kodu obliczeń prostej i odwrotnej kinematyki robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestInverseKin(void)
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
      DescPose desc_pos1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
      JointPos inverseRtn = {};
      robot.GetInverseKin(0, &desc_pos1, -1, &inverseRtn);
      printf("dcs1 GetInverseKin rtn is %f %f %f %f %f %f \n", inverseRtn.jPos[0], inverseRtn.jPos[1], inverseRtn.jPos[2], inverseRtn.jPos[3], inverseRtn.jPos[4], inverseRtn.jPos[5]);
      robot.GetInverseKinRef(0, &desc_pos1, &j1, &inverseRtn);
      printf("dcs1 GetInverseKinRef rtn is %f %f %f %f %f %f \n", inverseRtn.jPos[0], inverseRtn.jPos[1], inverseRtn.jPos[2], inverseRtn.jPos[3], inverseRtn.jPos[4], inverseRtn.jPos[5]);
      uint8_t hasResut = 0;
      robot.GetInverseKinHasSolution(0, &desc_pos1, &j1, &hasResut);
      printf("dcs1 GetInverseKinRef result %d\n", hasResut);
      DescPose forwordResult = {};
      robot.GetForwardKin(&j1, &forwordResult);
      printf("jpos1 forwordResult rtn is %f %f %f %f %f %f \n", forwordResult.tran.x, forwordResult.tran.y, forwordResult.tran.z, forwordResult.rpy.rx, forwordResult.rpy.ry, forwordResult.rpy.rz);
      robot.CloseRPC();
      return 0;
    }

Zapytanie o dane punktu nauczania w zarządzaniu nauczaniem robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Zapytanie o dane punktu nauczania w zarządzaniu nauczaniem robota
     * @param  [in]  name  Nazwa punktu
     * @param  [out]  data   Dane punktu
     * @return  Kod błędu
     */
    errno_t  GetRobotTeachingPoint(char name[64], float data[20]);

Pobieranie wartości kompensacji parametrów DH robota
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera wartości kompensacji parametrów DH robota
    * @param [out] dhCompensation Wartości kompensacji parametrów DH robota (mm) [cmpstD1, cmpstA2, cmpstA3, cmpstD4, cmpstD5, cmpstD6]
    * @return Kod błędu
    */
    errno_t GetDHCompensation(double dhCompensation[6]);

Pobieranie numeru seryjnego szafy sterowniczej
++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.1-3.8.1

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera numer seryjny szafy sterowniczej
    * @param [out] SNCode Numer seryjny szafy sterowniczej
    * @return Kod błędu
    */
    errno_t GetRobotSN(std::string& SNCode);

Przykład kodu zapytania o dane punktu nauczania w zarządzaniu nauczaniem robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestGetTeachPoint(void)
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
      char name[64] = "P1";
      float data[20] = { 0 };
      rtn = robot.GetRobotTeachingPoint(name, data);
      printf(" %d name is: %s \n", rtn, name);
      for (int i = 0; i < 20; i++)
      {
        printf("data is: %f \n", data[i]);
      }
      int que_len = 0;
      rtn = robot.GetMotionQueueLength(&que_len);
      printf("GetMotionQueueLength rtn is: %d, queue length is: %d \n", rtn, que_len);
      double dh[6] = { 0 };
      int retval = 0;
      retval = robot.GetDHCompensation(dh);
      cout << "retval is: " << retval << endl;
      cout << "dh is: " << dh[0] << " " << dh[1] << " " << dh[2] << " " << dh[3] << " " << dh[4] << " " << dh[5] << endl;
      string SN = "";
      robot.GetRobotSN(SN);
      cout << "robot SN is " << SN << endl;
      robot.CloseRPC();
      return 0;
    }

Pobieranie Układu Współrzędnych Narzędzia według ID
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v3.9.8
    
.. code-block:: c++
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
    errno_t GetToolCoordWithID(int id, DescPose& coord, int& type, int& install, int& toolID, int& loadNo);

Pobieranie Układu Współrzędnych Przedmiotu według ID
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v3.9.8
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera układ współrzędnych przedmiotu według ID
    * @param [in] id Numer układu współrzędnych przedmiotu
    * @param [out] coord Wartości układu współrzędnych
    * @param [out] refFrame Referencyjny układ współrzędnych
    * @return Kod błędu
    */
    errno_t GetWObjCoordWithID(int id, DescPose& coord, int& refFrame);
    
Pobieranie Zewnętrznego Układu Współrzędnych Narzędzia według ID
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v3.9.8
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera zewnętrzny układ współrzędnych narzędzia według ID
    * @param [in] id Numer zewnętrznego układu współrzędnych narzędzia, 20-39 odpowiadają zewnętrznym układom współrzędnych narzędzi 0-19
    * @param [out] coord Pozycja TCP stałego narzędzia zewnętrznego na robocie
    * @param [out] tcoord Pozycja układu współrzędnych przedmiotu zamontowanego na końcówce robota
    * @return Kod błędu
    */
    errno_t GetExToolCoordWithID(int id, DescPose& coord, DescPose& tcoord);
    
Pobieranie Układu Współrzędnych Osi Rozszerzonej według ID
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v3.9.8
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera układ współrzędnych osi rozszerzonej według ID
    * @param [in] id Numer zewnętrznego układu współrzędnych narzędzia
    * @param [out] coord Wartości układu współrzędnych
    * @param [out] axisCoordNum Numer osi rozszerzonej; bit0-bit3 odpowiadają osiom rozszerzonym 1-4; np. wartość axisCoordNum 3 odpowiada osiom rozszerzonym [1, 2]
    * @param [out] calibFlag Flaga kalibracji; 0-niekalibrowany; 1-kalibrowany
    * @return Kod błędu
    */
    errno_t GetExAxisCoordWithID(int id, DescPose& coord, int& axisCoordNum, int& calibFlag);

Pobieranie masy i środka ciężkości obciążenia według numeru
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera masę i środek ciężkości obciążenia według numeru
    * @param [in] id Numer obciążenia
    * @param [out] weight Masa obciążenia
    * @param [out] cog Środek ciężkości obciążenia
    * @return Kod błędu
    */
    errno_t GetTargetPayloadWithID(int id, double& weight, DescTran& cog);

Pobieranie bieżącego układu współrzędnych narzędzia
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera bieżący układ współrzędnych narzędzia
    * @param [out] coord Wartości układu współrzędnych
    * @return Kod błędu
    */
    errno_t GetCurToolCoord(DescPose& coord);

Pobieranie bieżącego układu współrzędnych obiektu
+++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera bieżący układ współrzędnych obiektu
    * @param [out] coord Wartości układu współrzędnych
    * @return Kod błędu
    */
    errno_t GetCurWObjCoord(DescPose& coord);

Pobieranie bieżącego zewnętrznego układu współrzędnych narzędzia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera bieżący zewnętrzny układ współrzędnych narzędzia
    * @param [out] coord Wartości układu współrzędnych
    * @return Kod błędu
    */
    errno_t GetCurExToolCoord(DescPose& coord);

Pobieranie bieżącego układu współrzędnych osi rozszerzonej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera bieżący układ współrzędnych osi rozszerzonej
    * @param [out] coord Wartości układu współrzędnych
    * @return Kod błędu
    */
    errno_t GetCurExAxisCoord(DescPose& coord);

Przykład kodu pobierania układów współrzędnych i obciążenia robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    int TestCoord()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return 0;
        }
        robot.SetReConnectParam(true, 30000, 500);
        robot.Sleep(2000);
        int id = 1;
        DescPose toolCoord = {};
        DescPose extoolCoord = {};
        DescPose exworkpieceCoord = {};
        DescPose wobjCoord = {};
        DescPose exAxisCoord = {};
        int type = 0, install = 0, toolID = 0, loadNo = 0;
        robot.GetToolCoordWithID(id, toolCoord, type, install, toolID, loadNo);
        printf("GetToolCoordWithID %d, %f %f %f %f %f %f,  type = %d, install = %d, toolID = %d, loadNo = %d\n", id,
            toolCoord.tran.x, toolCoord.tran.y, toolCoord.tran.z,
            toolCoord.rpy.rx, toolCoord.rpy.ry, toolCoord.rpy.rz, type, install, toolID, loadNo);
        int refFrame = 0;
        robot.GetWObjCoordWithID(id, wobjCoord, refFrame);
        printf("GetWObjCoordWithID %d, %f %f %f %f %f %f, refFrame = %d\n", id,
            wobjCoord.tran.x, wobjCoord.tran.y, wobjCoord.tran.z,
            wobjCoord.rpy.rx, wobjCoord.rpy.ry, wobjCoord.rpy.rz, refFrame);
        robot.GetExToolCoordWithID(21, extoolCoord, exworkpieceCoord);
        printf("GetExToolCoordWithID %d, %f %f %f %f %f %f\n", id,
            extoolCoord.tran.x, extoolCoord.tran.y, extoolCoord.tran.z,
            extoolCoord.rpy.rx, extoolCoord.rpy.ry, extoolCoord.rpy.rz,
            exworkpieceCoord.tran.x, exworkpieceCoord.tran.y, exworkpieceCoord.tran.z,
            exworkpieceCoord.rpy.rx, exworkpieceCoord.rpy.ry, exworkpieceCoord.rpy.rz);
        int axisCoordNum = 0, calibFlag = 0;
        robot.GetExAxisCoordWithID(id, exAxisCoord, axisCoordNum, calibFlag);
        printf("GetExAxisCoordWithID %d, %f %f %f %f %f %f, axisCoordNum = %d, calibFlag = %d\n", id,
            exAxisCoord.tran.x, exAxisCoord.tran.y, exAxisCoord.tran.z,
            exAxisCoord.rpy.rx, exAxisCoord.rpy.ry, exAxisCoord.rpy.rz, axisCoordNum, calibFlag);
        double weight = 0.0;
        DescTran cog = {};
        robot.GetTargetPayloadWithID(id, weight, cog);
        printf("GetTargetPayloadWithID %d, %f %f %f %f\n", id, weight,
            cog.x, cog.y, cog.z);
        robot.GetCurToolCoord(toolCoord);
        printf("GetCurToolCoord %f %f %f %f %f %f\n",
            toolCoord.tran.x, toolCoord.tran.y, toolCoord.tran.z,
            toolCoord.rpy.rx, toolCoord.rpy.ry, toolCoord.rpy.rz);
        robot.GetCurWObjCoord(wobjCoord);
        printf("GetCurWObjCoord %f %f %f %f %f %f\n",
            wobjCoord.tran.x, wobjCoord.tran.y, wobjCoord.tran.z,
            wobjCoord.rpy.rx, wobjCoord.rpy.ry, wobjCoord.rpy.rz);
        robot.GetCurExToolCoord(extoolCoord);
        printf("GetExToolCoordWithID %f %f %f %f %f %f\n",
            extoolCoord.tran.x, extoolCoord.tran.y, extoolCoord.tran.z,
            extoolCoord.rpy.rx, extoolCoord.rpy.ry, extoolCoord.rpy.rz);
        robot.GetCurExAxisCoord(exAxisCoord);
        printf("GetCurExAxisCoord %f %f %f %f %f %f\n",
            exAxisCoord.tran.x, exAxisCoord.tran.y, exAxisCoord.tran.z,
            exAxisCoord.rpy.rx, exAxisCoord.rpy.ry, exAxisCoord.rpy.rz);
        float weightT = 0.0;
        DescTran cogT = {};
        robot.GetTargetPayload(0, &weightT);
        robot.GetTargetPayloadCog(0, &cogT);
        printf("GetTargetPayload %f %f %f %f\n", weightT,
            cogT.x, cogT.y, cogT.z);
        DescPose coordSet(0, 1, 2, 3, 4, 5);
        robot.SetToolCoord(1, &coordSet, 0, 0, 1, 0);
        robot.SetWObjCoord(1, &coordSet, 0);
        robot.SetLoadWeight(1, 1.3);
        //DescTran cog = {};
        cog.x = 10;
        cog.y = 20;
        cog.z = 30;
        robot.SetLoadCoord(1, &cog);
        DescPose etcp(0, 0, 100, 0, 0, 0);
        DescPose etool(0, 0, 50, 0, 0, 0);
        rtn = robot.SetExToolCoord(21, &etcp, &etool);
        printf("SetExToolCoord rtn is %d\n", rtn);
        robot.ExtAxisActiveECoordSys(1, 1, coordSet, 1);
        robot.CloseRPC();
        return 0;
    }