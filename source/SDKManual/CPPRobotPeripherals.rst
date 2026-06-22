Urządzenia peryferyjne robota
=============================

.. toctree::
    :maxdepth: 5

Konfiguracja chwytaka
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Konfiguruje chwytak
    * @param  [in] company   Producent chwytaka, do ustalenia
    * @param  [in] device   Numer urządzenia, tymczasowo nieużywany, domyślnie 0
    * @param  [in] softvesion   Numer wersji oprogramowania, tymczasowo nieużywany, domyślnie 0
    * @param  [in] bus   Pozycja magistrali końcowej, na której zamontowane jest urządzenie, tymczasowo nieużywane, domyślnie 0
    * @return   Kod błędu
    */
    errno_t  SetGripperConfig(int company, int device, int softvesion, int bus);

Pobieranie konfiguracji chwytaka
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Pobiera konfigurację chwytaka
    * @param  [in] company   Producent chwytaka, do ustalenia
    * @param  [in] device   Numer urządzenia, tymczasowo nieużywany, domyślnie 0
    * @param  [in] softvesion   Numer wersji oprogramowania, tymczasowo nieużywany, domyślnie 0
    * @param  [in] bus   Pozycja magistrali końcowej, na której zamontowane jest urządzenie, tymczasowo nieużywane, domyślnie 0
    * @return   Kod błędu
    */
    errno_t  GetGripperConfig(int *company, int *device, int *softvesion, int *bus);

Aktywacja chwytaka
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Aktywuje chwytak
    * @param  [in] index   Numer chwytaka
    * @param  [in] act   0-reset, 1-aktywacja
    * @return   Kod błędu
    */
    errno_t  ActGripper(int index, uint8_t act);

Sterowanie chwytakiem
+++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief  Steruje chwytakiem
     * @param  [in] index   Numer chwytaka
     * @param  [in] pos   Procent pozycji, zakres [0~100]
     * @param  [in] vel   Procent prędkości, zakres [0~100]
     * @param  [in] force   Procent momentu, zakres [0~100]
     * @param  [in] max_time   Maksymalny czas oczekiwania, zakres [0~30000], jednostka ms
     * @param  [in] block   0-blokujące, 1-nieblokujące
     * @param  [in] type Typ chwytaka, 0-chwytak równoległy; 1-chwytak obrotowy
     * @param  [in] rotNum Liczba obrotów
     * @param  [in] rotVel Procent prędkości obrotowej [0-100]
     * @param  [in] rotTorque Procent momentu obrotowego [0-100]
     * @return   Kod błędu
     */
    errno_t MoveGripper(int index, int pos, int vel, int force, int max_time, uint8_t block, int type, double rotNum, int rotVel, int rotTorque);

Pobieranie stanu ruchu chwytaka
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Pobiera stan ruchu chwytaka
     * @param  [out] fault   0-brak błędu, 1-jest błąd
     * @param  [out] staus   0-ruch niezakończony, 1-ruch zakończony
     * @return   Kod błędu
     */
    errno_t  GetGripperMotionDone(uint16_t *fault, uint8_t *status);

Pobieranie stanu aktywacji chwytaka
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Pobiera stan aktywacji chwytaka
     * @param  [out] fault   0-brak błędu, 1-jest błąd
     * @param  [out] status  bit0~bit15 odpowiadają numerom chwytaka 0~15, bit=0 oznacza nieaktywny, bit=1 oznacza aktywny
     * @return   Kod błędu
     */
    errno_t  GetGripperActivateStatus(uint16_t *fault, uint16_t *status);

Pobieranie pozycji chwytaka
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Pobiera pozycję chwytaka
     * @param  [out] fault   0-brak błędu, 1-jest błąd
     * @param  [out] position   Procent pozycji, zakres 0~100%
     * @return   Kod błędu
     */
    errno_t  GetGripperCurPosition(uint16_t *fault, uint8_t *position);

Pobieranie prędkości chwytaka
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Pobiera prędkość chwytaka
     * @param  [out] fault   0-brak błędu, 1-jest błąd
     * @param  [out] speed   Procent prędkości, zakres 0~100%
     * @return   Kod błędu
     */
    errno_t  GetGripperCurSpeed(uint16_t *fault, int8_t *speed);

Pobieranie prądu chwytaka
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Pobiera prąd chwytaka
     * @param  [out] fault   0-brak błędu, 1-jest błąd
     * @param  [out] current   Procent prądu, zakres 0~100%
     * @return   Kod błędu
     */
    errno_t  GetGripperCurCurrent(uint16_t *fault, int8_t *current);

Pobieranie napięcia chwytaka
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Pobiera napięcie chwytaka
     * @param  [out] fault   0-brak błędu, 1-jest błąd
     * @param  [out] voltage   Napięcie, jednostka 0.1V
     * @return   Kod błędu
     */
    errno_t  GetGripperVoltage(uint16_t *fault, int *voltage);

Pobieranie temperatury chwytaka
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Pobiera temperaturę chwytaka
     * @param  [out] fault   0-brak błędu, 1-jest błąd
     * @param  [out] temp   Temperatura, jednostka ℃
     * @return   Kod błędu
     */
    errno_t  GetGripperTemp(uint16_t *fault, int *temp);

Obliczanie punktu przedchwytania - wizja
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Oblicza punkt przedchwytania - wizja
     * @param  [in] desc_pos   Pozy i orientacja kartezjańska punktu chwytania
     * @param  [in] zlength   Przesunięcie w osi Z
     * @param  [in] zangle   Przesunięcie obrotu wokół osi Z
     * @return   Kod błędu
     */
    errno_t  ComputePrePick(DescPose *desc_pos, double zlength, double zangle, DescPose *pre_pos);

Obliczanie punktu wycofania - wizja
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Oblicza punkt wycofania - wizja
     * @param  [in] desc_pos   Pozy i orientacja kartezjańska punktu chwytania
     * @param  [in] zlength   Przesunięcie w osi Z
     * @param  [in] zangle   Przesunięcie obrotu wokół osi Z
     * @return   Kod błędu
     */
    errno_t  ComputePostPick(DescPose *desc_pos, double zlength, double zangle, DescPose *post_pos);

Przykład kodu operacji chwytakiem robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestGripper(void)
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
      int company = 4;
      int device = 0;
      int softversion = 0;
      int bus = 2;
      int index = 2;
      int act = 0;
      int max_time = 30000;
      uint8_t block = 0;
      uint8_t status;
      uint16_t fault;
      uint16_t active_status = 0;
      uint8_t current_pos = 0;
      int8_t current = 0;
      int voltage = 0;
      int temp = 0;
      int8_t speed = 0;
      robot.SetGripperConfig(company, device, softversion, bus);
      std::this_thread::sleep_for(std::chrono::milliseconds(1000));
      robot.GetGripperConfig(&company, &device, &softversion, &bus);
      printf("gripper config:%d,%d,%d,%d\n", company, device, softversion, bus);
      robot.ActGripper(index, act);
      std::this_thread::sleep_for(std::chrono::milliseconds(1000));
      act = 1;
      robot.ActGripper(index, act);
      std::this_thread::sleep_for(std::chrono::milliseconds(1000));
      robot.MoveGripper(index, 100, 50, 50, max_time, block, 0, 0, 0, 0);
      std::this_thread::sleep_for(std::chrono::milliseconds(1000));
      robot.MoveGripper(index, 0, 50, 0, max_time, block, 0, 0, 0, 0);
      robot.GetGripperMotionDone(&fault, &status);
      printf("motion status:%u,%u\n", fault, status);
      robot.GetGripperActivateStatus(&fault, &active_status);
      printf("gripper active fault is: %u, status is: %u\n", fault, active_status);
      robot.GetGripperCurPosition(&fault, &current_pos);
      printf("fault is:%u, current position is: %u\n", fault, current_pos);
      robot.GetGripperCurCurrent(&fault, &current);
      printf("fault is:%u, current current is: %d\n", fault, current);
      robot.GetGripperVoltage(&fault, &voltage);
      printf("fault is:%u, current voltage is: %d \n", fault, voltage);
      robot.GetGripperTemp(&fault, &temp);
      printf("fault is:%u, current temperature is: %d\n", fault, temp);
      robot.GetGripperCurSpeed(&fault, &speed);
      printf("fault is:%u, current speed is: %d\n", fault, speed);
      int retval = 0;
      DescPose prepick_pose = {};
      DescPose postpick_pose = {};
      DescPose p1Desc(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
      DescPose p2Desc(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
      retval = robot.ComputePrePick(&p1Desc, 10, 0, &prepick_pose);
      printf("ComputePrePick retval is: %d\n", retval);
      printf("xyz is: %f, %f, %f; rpy is: %f, %f, %f\n", prepick_pose.tran.x, prepick_pose.tran.y, prepick_pose.tran.z, prepick_pose.rpy.rx, prepick_pose.rpy.ry, prepick_pose.rpy.rz);
      retval = robot.ComputePostPick(&p2Desc, -10, 0, &postpick_pose);
      printf("ComputePostPick retval is: %d\n", retval);
      printf("xyz is: %f, %f, %f; rpy is: %f, %f, %f\n", postpick_pose.tran.x, postpick_pose.tran.y, postpick_pose.tran.z, postpick_pose.rpy.rx, postpick_pose.rpy.ry, postpick_pose.rpy.rz);
      robot.CloseRPC();
      return 0;
    }

Pobieranie liczby obrotów chwytaka obrotowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 3.7.6

.. code-block:: c++
    :linenos:

    /**
     * @brief  Pobiera liczbę obrotów chwytaka obrotowego
     * @param  [out] fault   0-brak błędu, 1-jest błąd
     * @param  [out] num   Liczba obrotów
     * @return   Kod błędu
     */
    errno_t GetGripperRotNum(uint16_t* fault, double* num);

Pobieranie prędkości obrotowej chwytaka obrotowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: V3.7.6

.. code-block:: c++
    :linenos:

    /**
     * @brief  Pobiera prędkość obrotową chwytaka obrotowego
     * @param  [out] fault   0-brak błędu, 1-jest błąd
     * @param  [out] speed   Procent prędkości obrotowej
     * @return   Kod błędu
     */
    errno_t GetGripperRotSpeed(uint16_t* fault, int* speed);

Pobieranie momentu obrotowego chwytaka obrotowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: V3.7.6

.. code-block:: c++
    :linenos:

    /**
     * @brief  Pobiera moment obrotowy chwytaka obrotowego
     * @param  [out] fault   0-brak błędu, 1-jest błąd
     * @param  [out] torque   Procent momentu obrotowego
     * @return   Kod błędu
     */
    errno_t GetGripperRotTorque(uint16_t* fault, int* torque);

Przykład kodu pobierania stanu chwytaka obrotowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestRotGripperState(void)
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
      uint16_t fault = 0;
      double rotNum = 0.0;
      int rotSpeed = 0;
      int rotTorque = 0;
      robot.GetGripperRotNum(&fault, &rotNum);
      robot.GetGripperRotSpeed(&fault, &rotSpeed);
      robot.GetGripperRotTorque(&fault, &rotTorque);
      printf("gripper rot num : %lf, gripper rotSpeed : %d, gripper rotTorque : %d\n", rotNum, rotSpeed, rotTorque);
      robot.CloseRPC();
      return 0;
    }

Uruchamianie, zatrzymywanie przenośnika
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Uruchamia, zatrzymuje przenośnik
    * @param [in] status Stan, 1-uruchom, 0-zatrzymaj
    * @return Kod błędu
    */
    errno_t ConveyorStartEnd(uint8_t status);

Rejestracja punktu detekcji IO
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Rejestruje punkt detekcji IO
    * @return Kod błędu
    */
    errno_t ConveyorPointIORecord();

Rejestracja punktu A
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Rejestruje punkt A
    * @return Kod błędu
    */
    errno_t ConveyorPointARecord();

Rejestracja punktu odniesienia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Rejestruje punkt odniesienia
    * @return Kod błędu
    */
    errno_t ConveyorRefPointRecord();

Rejestracja punktu B
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Rejestruje punkt B
    * @return Kod błędu
    */
    errno_t ConveyorPointBRecord();

Detekcja IO przedmiotu na przenośniku
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Detekcja IO przedmiotu na przenośniku
    * @param [in] max_t Maksymalny czas detekcji, jednostka ms
    * @return Kod błędu
    */
    errno_t ConveyorIODetect(int max_t);

Pobieranie bieżącej pozycji przedmiotu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera bieżącą pozycję przedmiotu
    * @param [in] mode
    * @return Kod błędu
    */
    errno_t ConveyorGetTrackData(int mode);

Rozpoczęcie śledzenia przenośnika
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Rozpoczęcie śledzenia przenośnika
    * @param [in] status Stan, 1-uruchom, 0-zatrzymaj
    * @return Kod błędu
    */
    errno_t ConveyorTrackStart(uint8_t status);

Zatrzymanie śledzenia przenośnika
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Zatrzymanie śledzenia przenośnika
    * @return Kod błędu
    */
    errno_t ConveyorTrackEnd();

Konfiguracja parametrów przenośnika
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.2.1-3.8.1

.. code-block:: c++
    :linenos:

    /**
    * @brief Konfiguruje parametry przenośnika
    * @param [in] para[0] Kanał enkodera 1~2
    * @param [in] para[1] Liczba impulsów enkodera na obrót
    * @param [in] para[2] Odległość przesunięcia przenośnika na jeden obrót enkodera
    * @param [in] para[3] Numer układu współrzędnych obiektu dla funkcji śledzenia ruchu, dla śledzenia chwytania i śledzenia TPD ustaw na 0
    * @param [in] para[4] Czy z wizją 0-bez 1-z
    * @param [in] para[5] Współczynnik prędkości dla opcji śledzenia chwytania przenośnika (1-100), dla innych opcji domyślnie 1
    * @param [in] followType Typ śledzenia ruchu, 0-śledzenie ruchu; 1-śledzenie doganiające
    * @param [in] startDis Dla śledzenia doganiającego, odległość początkowa śledzenia, -1: automatyczne obliczenie (po dojechaniu przedmiotu pod robota), jednostka mm, wartość domyślna 0
    * @param [in] endDis Dla śledzenia doganiającego, odległość końcowa śledzenia, jednostka mm, wartość domyślna 100
    * @return Kod błędu
    */
    errno_t ConveyorSetParam(float para[6], int followType = 0, int startDis = 0, int endDis = 100);

Kompensacja punktu chwytania przenośnika
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.2.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Kompensacja punktu chwytania przenośnika
     * @param [in] cmp Pozycja kompensacji double[3]{x, y, z}
     * @return Kod błędu
     */
    errno_t ConveyorCatchPointComp(double cmp[3]);

Ruch liniowy przenośnika
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Ruch liniowy przenośnika
    * @param [in] status Stan, 1-uruchom, 0-zatrzymaj
    * @return Kod błędu
    */
    errno_t TrackMoveL(char name[32], int tool, int wobj, float vel, float acc, float ovl, float blendR, uint8_t flag, uint8_t type);

Detekcja wejścia komunikacyjnego przenośnika
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.1-3.8.1

.. code-block:: c++
    :linenos:

    /**
    * @brief Detekcja wejścia komunikacyjnego przenośnika
    * @param [in] timeout Czas oczekiwania na timeout w ms
    * @return Kod błędu
    */
    errno_t ConveyorComDetect(int timeout);

Wyzwolenie detekcji wejścia komunikacyjnego przenośnika
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.1-3.8.1

.. code-block:: c++
    :linenos:

    /**
    * @brief Wyzwolenie detekcji wejścia komunikacyjnego przenośnika
    * @return Kod błędu
    */
    errno_t ConveyorComDetectTrigger();

Przykładowy program operacji przenośnikiem robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestConveyor(void)
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
      retval = robot.ConveyorStartEnd(1);
      printf("ConveyorStartEnd retval is: %d\n", retval);
      retval = robot.ConveyorPointIORecord();
      printf("ConveyorPointIORecord retval is: %d\n", retval);
      retval = robot.ConveyorPointARecord();
      printf("ConveyorPointARecord retval is: %d\n", retval);
      retval = robot.ConveyorRefPointRecord();
      printf("ConveyorRefPointRecord retval is: %d\n", retval);
      retval = robot.ConveyorPointBRecord();
      printf("ConveyorPointBRecord retval is: %d\n", retval);
      retval = robot.ConveyorStartEnd(0);
      printf("ConveyorStartEnd retval is: %d\n", retval);
      retval = 0;
      float param[6] = { 1,10000,200,0,0,20 };
      retval = robot.ConveyorSetParam(param);
      printf("ConveyorSetParam retval is: %d\n", retval);
      double cmp[3] = { 0.0, 0.0, 0.0 };
      retval = robot.ConveyorCatchPointComp(cmp);
      printf("ConveyorCatchPointComp retval is: %d\n", retval);
      int index = 1;
      int max_time = 30000;
      uint8_t block = 0;
      retval = 0;
      DescPose p1Desc(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
      DescPose p2Desc(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
      retval = robot.MoveCart(&p1Desc, 1, 0, 100.0, 100.0, 100.0, -1.0, -1);
      printf("MoveCart retval is: %d\n", retval);
      retval = robot.WaitMs(1);
      printf("WaitMs retval is: %d\n", retval);
      retval = robot.ConveyorIODetect(10000);
      printf("ConveyorIODetect retval is: %d\n", retval);
      retval = robot.ConveyorGetTrackData(1);
      printf("ConveyorGetTrackData retval is: %d\n", retval);
      retval = robot.ConveyorTrackStart(1);
      printf("ConveyorTrackStart retval is: %d\n", retval);
      retval = robot.TrackMoveL("cvrCatchPoint", 1, 0, 100, 100, 100, -1.0, 0, 0);
      printf("TrackMoveL retval is: %d\n", retval);
      retval = robot.MoveGripper(index, 51, 40, 30, max_time, block, 0, 0, 0, 0);
      printf("MoveGripper retval is: %d\n", retval);
      retval = robot.TrackMoveL("cvrRaisePoint", 1, 0, 100, 100, 100, -1.0, 0, 0);
      printf("TrackMoveL retval is: %d\n", retval);
      retval = robot.ConveyorTrackEnd();
      printf("ConveyorTrackEnd retval is: %d\n", retval);
      robot.MoveCart(&p2Desc, 1, 0, 100.0, 100.0, 100.0, -1.0, -1);
      retval = robot.MoveGripper(index, 100, 40, 10, max_time, block, 0, 0, 0, 0);
      printf("MoveGripper retval is: %d\n", retval);
      rtn = robot->ConveyorComDetect(1000 * 10);
      printf("ConveyorComDetect rtn is: %d\n", rtn);
      robot.Sleep(2000);
      rtn = robot->ConveyorComDetectTrigger();
      printf("ConveyorComDetectTrigger rtn is: %d\n", rtn);
      robot.CloseRPC();
      return 0;
    }

Konfiguracja czujnika końcówki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Konfiguruje czujnik końcówki
    * @param [in] idCompany Producent, 18-JUNKONG; 25-HUIDE
    * @param [in] idDevice Typ, 0-JUNKONG/RYR6T.V1.0
    * @param [in] idSoftware Wersja oprogramowania, 0-J1.0/HuiDe1.0 (tymczasowo niedostępne)
    * @param [in] idBus Pozycja montażu, 1-port końcówki 1; 2-port końcówki 2...8-port końcówki 8 (tymczasowo niedostępne)
    * @return Kod błędu
    */
    errno_t AxleSensorConfig(int idCompany, int idDevice, int idSoftware, int idBus);

Pobieranie konfiguracji czujnika końcówki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Pobiera konfigurację czujnika końcówki
     * @param [out] idCompany Producent, 18-JUNKONG; 25-HUIDE
     * @param [out] idDevice Typ, 0-JUNKONG/RYR6T.V1.0
     * @return Kod błędu
     */
    errno_t AxleSensorConfigGet(int& idCompany, int& idDevice);

Aktywacja czujnika końcówki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Aktywuje czujnik końcówki
     * @param [in] actFlag 0-reset; 1-aktywacja
     * @return Kod błędu
     */
    errno_t AxleSensorActivate(int actFlag);

Zapis do rejestru czujnika końcówki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Zapis do rejestru czujnika końcówki
     * @param [in] devAddr Numer adresu urządzenia 0-255
     * @param [in] regHAddr Wysoki bajt adresu rejestru
     * @param [in] regLAddr Niski bajt adresu rejestru
     * @param [in] regNum Liczba rejestrów 0-255
     * @param [in] data1 Wartość do zapisu w rejestrze 1
     * @param [in] data2 Wartość do zapisu w rejestrze 2
     * @param [in] isNoBlock 0-blokujące; 1-nieblokujące
     * @return Kod błędu
     */
    errno_t AxleSensorRegWrite(int devAddr, int regHAddr, int regLAddr, int regNum, int data1, int data2, int isNoBlock);

Przykład kodu czujnika końcówki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestAxleSensor(void)
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
      robot.AxleSensorConfig(18, 0, 0, 1);
      int company = -1;
      int type = -1;
      robot.AxleSensorConfigGet(company, type);
      printf("company is %d, type is %d\n", company, type);
      rtn = robot.AxleSensorActivate(1);
      printf("AxleSensorActivate rtn is %d\n", rtn);
      robot.Sleep(1000);
      rtn = robot.AxleSensorRegWrite(1, 4, 6, 1, 0, 0, 0);
      printf("AxleSensorRegWrite rtn is %d\n", rtn);
      robot.CloseRPC();
      return 0;
    }

Pobieranie protokołu urządzeń peryferyjnych robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera protokół urządzeń peryferyjnych robota
    * @param [out] protocol Numer protokołu urządzeń peryferyjnych robota 4096-karta sterowania osią rozszerzoną; 4097-ModbusSlave; 4098-ModbusMaster
    * @return Kod błędu
    */
    errno_t GetExDevProtocol(int *protocol);

Ustawianie protokołu urządzeń peryferyjnych robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia protokół urządzeń peryferyjnych robota
    * @param [in] protocol Numer protokołu urządzeń peryferyjnych robota 4096-karta sterowania osią rozszerzoną; 4097-ModbusSlave; 4098-ModbusMaster
    * @return Kod błędu
    */
    errno_t SetExDevProtocol(int protocol);

Przykładowy program ustawiania protokołu urządzeń peryferyjnych robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    int TestExDevProtocol(void)
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
      int protocol = 4096;
      rtn = robot.SetExDevProtocol(protocol);
      std::cout << "SetExDevProtocol rtn " << rtn << std::endl;
      rtn = robot.GetExDevProtocol(&protocol);
      std::cout << "GetExDevProtocol rtn " << rtn << " protocol is: " << protocol << std::endl;
      robot.CloseRPC();
      return 0;
    }

Pobieranie parametrów komunikacji końcówki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera parametry komunikacji końcówki
    * @param param Parametry komunikacji końcówki
    * @return  Kod błędu
    */
    errno_t GetAxleCommunicationParam(AxleComParam* param);

Ustawianie parametrów komunikacji końcówki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia parametry komunikacji końcówki
    * @param param  Parametry komunikacji końcówki
    * @return  Kod błędu
    */
    errno_t SetAxleCommunicationParam(AxleComParam param);

Ustawianie typu transferu plików na końcówce
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia typ transferu plików na końcówce
    * @param type 1-plik aktualizacyjny MCU; 2-plik LUA
    * @return  Kod błędu
    */
    errno_t SetAxleFileType(int type);

Ustawianie włączenia wykonania LUA na końcówce
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia włączenie wykonania LUA na końcówce
    * @param enable 0-nie włączaj; 1-włączaj
    * @return  Kod błędu
    */
    errno_t SetAxleLuaEnable(int enable);

Przywracanie po błędzie pliku LUA na końcówce
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Przywracanie po błędzie pliku LUA na końcówce
    * @param status 0-nie przywracaj; 1-przywróć
    * @return  Kod błędu
    */
    errno_t SetRecoverAxleLuaErr(int status);

Pobieranie stanu włączenia wykonania LUA na końcówce
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera stan włączenia wykonania LUA na końcówce
    * @param status status[0]: 0-niewłączone; 1-włączone
    * @return  Kod błędu
    */
    errno_t GetAxleLuaEnableStatus(int status[]);

Ustawianie typu włączanego urządzenia końcowego LUA na końcówce
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia typ włączanego urządzenia końcowego LUA na końcówce
    * @param forceSensorEnable Stan włączenia czujnika siły, 0-nie włączaj; 1-włączaj
    * @param gripperEnable Stan włączenia chwytaka, 0-nie włączaj; 1-włączaj
    * @param IOEnable Stan włączenia urządzenia IO, 0-nie włączaj; 1-włączaj
    * @return  Kod błędu
    */
    errno_t SetAxleLuaEnableDeviceType(int forceSensorEnable, int gripperEnable, int IOEnable);

Pobieranie typu włączanego urządzenia końcowego LUA na końcówce
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera typ włączanego urządzenia końcowego LUA na końcówce
    * @param enable enable[0]:forceSensorEnable Stan włączenia czujnika siły, 0-nie włączaj; 1-włączaj
    * @param enable enable[1]:gripperEnable Stan włączenia chwytaka, 0-nie włączaj; 1-włączaj
    * @param enable enable[2]:IOEnable Stan włączenia urządzenia IO, 0-nie włączaj; 1-włączaj
    * @return  Kod błędu
    */
    errno_t GetAxleLuaEnableDeviceType(int* forceSensorEnable, int* gripperEnable, int* IOEnable);

Pobieranie aktualnie skonfigurowanego urządzenia końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera aktualnie skonfigurowane urządzenie końcowe
    * @param forceSensorEnable Numer włączonego urządzenia czujnika siły 0-niewłączone; 1-włączone
    * @param gripperEnable Numer włączonego urządzenia chwytaka, 0-nie włączaj; 1-włączaj
    * @param IODeviceEnable Numer włączonego urządzenia IO, 0-nie włączaj; 1-włączaj
    * @return  Kod błędu
    */
    errno_t GetAxleLuaEnableDevice(int forceSensorEnable[], int gripperEnable[], int IODeviceEnable[]);

Ustawianie włączenia funkcji sterowania ruchem chwytaka
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia włączenie funkcji sterowania ruchem chwytaka
    * @param id Numer urządzenia chwytaka
    * @param func func[0]-włączenie chwytaka; func[1]-inicjalizacja chwytaka; 2-ustawienie pozycji; 3-ustawienie prędkości; 4-ustawienie momentu; 6-odczyt stanu chwytaka; 7-odczyt stanu inicjalizacji; 8-odczyt kodu błędu; 9-odczyt pozycji; 10-odczyt prędkości; 11-odczyt momentu
    * @return  Kod błędu
    */
    errno_t SetAxleLuaGripperFunc(int id, int func[]);

Pobieranie włączenia funkcji sterowania ruchem chwytaka
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera włączenie funkcji sterowania ruchem chwytaka
    * @param id Numer urządzenia chwytaka
    * @param func func[0]-włączenie chwytaka; func[1]-inicjalizacja chwytaka; 2-ustawienie pozycji; 3-ustawienie prędkości; 4-ustawienie momentu; 6-odczyt stanu chwytaka; 7-odczyt stanu inicjalizacji; 8-odczyt kodu błędu; 9-odczyt pozycji; 10-odczyt prędkości; 11-odczyt momentu
    * @return  Kod błędu
    */
    errno_t GetAxleLuaGripperFunc(int id, int func[]);

Zapis pliku stacji podrzędnej Ethercat robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Zapis pliku stacji podrzędnej Ethercat robota
    * @param type Typ pliku stacji podrzędnej, 1-aktualizacja pliku stacji podrzędnej; 2-aktualizacja pliku konfiguracji stacji podrzędnej
    * @param slaveID Numer stacji podrzędnej
    * @param fileName Nazwa przesyłanego pliku
    * @return  Kod błędu
    */
    errno_t SlaveFileWrite(int type, int slaveID, std::string fileName);

Przesyłanie pliku otwartego protokołu Lua końcówki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Przesyła plik otwartego protokołu Lua końcówki
    * @param filePath Ścieżka lokalnego pliku lua ".../AXLE_LUA_End_DaHuan.lua"
    * @return Kod błędu
    */
    errno_t AxleLuaUpload(std::string filePath);

Wejście stacji podrzędnej Ethercat robota w tryb boot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Wejście stacji podrzędnej Ethercat robota w tryb boot
    * @return  Kod błędu
    */
    errno_t SetSysServoBootMode();

Przykład kodu operacji na pliku LUA końcówki robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestAxleLua(void)
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
      robot.AxleLuaUpload("D://zUP/AXLE_LUA_End_DaHuan.lua");
      AxleComParam param(7, 8, 1, 0, 5, 3, 1);
      robot.SetAxleCommunicationParam(param);
      AxleComParam getParam;
      robot.GetAxleCommunicationParam(&getParam);
      printf("GetAxleCommunicationParam param is %d %d %d %d %d %d %d\n", getParam.baudRate, getParam.dataBit, getParam.stopBit, getParam.verify, getParam.timeout, getParam.timeoutTimes, getParam.period);
      robot.SetAxleLuaEnable(1);
      int luaEnableStatus = 0;
      robot.GetAxleLuaEnableStatus(&luaEnableStatus);
      robot.SetAxleLuaEnableDeviceType(0, 1, 0);
      int forceEnable = 0;
      int gripperEnable = 0;
      int ioEnable = 0;
      robot.GetAxleLuaEnableDeviceType(&forceEnable, &gripperEnable, &ioEnable);
      printf("GetAxleLuaEnableDeviceType param is %d %d %d\n", forceEnable, gripperEnable, ioEnable);
      int func[16] = { 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1 };
      robot.SetAxleLuaGripperFunc(1, func);
      int getFunc[16] = { 0 };
      robot.GetAxleLuaGripperFunc(1, getFunc);
      int getforceEnable[16] = { 0 };
      int getgripperEnable[16] = { 0 };
      int getioEnable[16] = { 0 };
      robot.GetAxleLuaEnableDevice(getforceEnable, getgripperEnable, getioEnable);
      printf("\ngetforceEnable status : ");
      for (int i = 0; i < 16; i++)
      {
        printf("%d,", getforceEnable[i]);
      }
      printf("\ngetgripperEnable status : ");
      for (int i = 0; i < 16; i++)
      {
        printf("%d,", getgripperEnable[i]);
      }
      printf("\ngetioEnable status : ");
      for (int i = 0; i < 16; i++)
      {
        printf("%d,", getioEnable[i]);
      }
      printf("\n");
      robot.ActGripper(1, 0);
      robot.Sleep(2000);
      robot.ActGripper(1, 1);
      robot.Sleep(2000);
      robot.MoveGripper(1, 90, 10, 100, 50000, 0, 0, 0, 0, 0);
      int pos = 0;
      while (true)
      {
        robot.GetRobotRealTimeState(&pkg);
        printf("gripper pos is %u\n", pkg.gripper_position);
        robot.Sleep(100);
      }
      robot.CloseRPC();
      return 0;
    }

Pobieranie stanu przycisków SmartTool
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera stan przycisków SmartTool
    * @param [out] state Stan przycisków uchwytu SmartTool; (bit0:0-komunikacja normalna; 1-komunikacja rozłączona; bit1-cofnij operację; bit2-wyczyść program;
    bit3-przycisk A; bit4-przycisk B; bit5-przycisk C; bit6-przycisk D; bit7-przycisk E; bit8-przycisk IO; bit9-ręczny/automatyczny; bit10-start)
    * @return Kod błędu
    */
    errno_t GetSmarttoolBtnState(int& state);

Przykład kodu dla przycisków SmartTool
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int main(void)
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;

      robot.LoggerInit();
      robot.SetLoggerLevel(1);
      int rtn = robot.RPC("192.168.58.2");
      robot.SetReConnectParam(true, 30000, 500);

      while (true)
      {
        int btn = 0;
        robot.GetSmarttoolBtnState(btn);
        cout << "smarttool " << std::bitset<sizeof(btn) * 8>(btn) << endl;

        Sleep(100);
      }
    }

Sterowanie macierzą przyssawek
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Steruje macierzą przyssawek
    * @param [in] slaveID Numer stacji podrzędnej
    * @param [in] len Długość
    * @param [in] ctrlValue Wartość sterująca
    * @return Kod błędu
    */
    errno_t FRRobot::SetSuckerCtrl(uint8_t slaveID, uint8_t len, uint8_t ctrlValue[20]);

Pobieranie stanu macierzy przyssawek
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera stan macierzy przyssawek
    * @param [in] slaveID Numer stacji podrzędnej
    * @param [out] state Stan przyssania 0-zwolniony obiekt 1-wykryto przedmiot, przyssanie udane 2-brak przyssania do przedmiotu 3-przedmiot oderwany
    * @param [out] pressValue Bieżący poziom próżni, jednostka kPa
    * @param [out] error Bieżący kod błędu przyssawki
    * @return Kod błędu
    */
    errno_t FRRobot::GetSuckerState(uint8_t slaveID, uint8_t* state, int* pressValue, int* error);

Oczekiwanie na stan przyssawki
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Oczekuje na stan przyssawki
    * @param [in] slaveID Numer stacji podrzędnej
    * @param [in] state Stan przyssania 0-zwolniony obiekt 1-wykryto przedmiot, przyssanie udane 2-brak przyssania do przedmiotu 3-przedmiot oderwany
    * @param [in] ms Maksymalny czas oczekiwania
    * @return Kod błędu
    */
    errno_t FRRobot::WaitSuckerState(uint8_t slaveID, uint8_t state, int ms);

Przykład kodu instrukcji sterowania macierzą przyssawek
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    void testSucker()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        uint8_t ctrl[20];
        uint8_t state;
        int pressVlaue;
        int error;

        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return;
        }
        robot.SetReConnectParam(true, 30000, 500);
        // Przesyłanie i ładowanie pliku otwartego protokołu
        robot.OpenLuaUpload("E://Projekt/SDK urządzeń peryferyjnych/CtrlDev_sucker.lua");
        robot.Sleep(2000);
        robot.SetCtrlOpenLUAName(1, "CtrlDev_sucker.lua");
        robot.UnloadCtrlOpenLUA(1);
        robot.LoadCtrlOpenLUA(1);
        robot.Sleep(1000);

        // Sterowanie przyssawką w trybie broadcast, przyssanie z maksymalną siłą
        ctrl[0] = 1;
        robot.SetSuckerCtrl(0, 1, ctrl);

        // Cykliczne monitorowanie stanu przyssawki 1 i 12
        for (int i = 0; i < 100; i++)
        {
            robot.GetSuckerState(1, &state, &pressVlaue, &error);
            printf("sucker1 state is %d, pressVlaue is %d, error num is %d\n", state, pressVlaue, error);
            robot.GetSuckerState(12, &state, &pressVlaue, &error);
            printf("sucker12 state is %d, pressVlaue is %d, error num is %d\n", state, pressVlaue, error);
            robot.Sleep(100);
        }

        // Oczekiwanie, czy przyssawka 1 jest w stanie przyssania do przedmiotu, czas oczekiwania 100 ms
        int ret = robot.WaitSuckerState(1, 1, 100);
        printf("WaitSuckerState result is  %d\n", ret);

        // Wyłączenie przyssawek 1 i 12 w trybie unicast
        ctrl[0] = 3;
        robot.SetSuckerCtrl(1, 1, ctrl);
        robot.SetSuckerCtrl(12, 1, ctrl);

        robot.CloseRPC();
    }

Przesyłanie pliku LUA otwartego protokołu urządzeń peryferyjnych
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
     * @brief Przesyła plik Lua
     * @param [in] filePath Ścieżka lokalnego pliku lua
     * @return Kod błędu
     */
    errno_t OpenLuaUpload(std::string filePath);

Pobieranie parametrów płyty stacji podrzędnej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief  Pobiera parametry płyty stacji podrzędnej
    * @param  [out] type  0-Ethercat, 1-CClink, 3-Ethercat, 4-EIP
    * @param  [out] version  Wersja protokołu
    * @param  [out] connState  0-niepołączony 1-połączony
    * @return   Kod błędu
    */
    errno_t GetFieldBusConfig(uint8_t* type, uint8_t* version, uint8_t* connState);

Zapis DO stacji podrzędnej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief  Zapisuje DO stacji podrzędnej
    * @param  [in] DOIndex  Numer DO
    * @param  [in] writeNum  Liczba do zapisu
    * @param  [in] status[8] Wartości do zapisu, maksymalnie 8
    * @return   Kod błędu
    */
    errno_t FieldBusSlaveWriteDO(uint8_t DOIndex, uint8_t writeNum, uint8_t status[8]);

Zapis AO stacji podrzędnej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief  Zapisuje AO stacji podrzędnej
    * @param  [in] AOIndex  Numer AO
    * @param  [in] writeNum  Liczba do zapisu
    * @param  [in] status[8] Wartości do zapisu, maksymalnie 8
    * @return   Kod błędu
    */
    errno_t FieldBusSlaveWriteAO(uint8_t AOIndex, uint8_t writeNum, double status[8]);

Odczyt DI stacji podrzędnej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief  Odczytuje DI stacji podrzędnej
    * @param  [in] DOIndex  Numer DI
    * @param  [in] readNum  Liczba do odczytu
    * @param  [out] status[8] Odczytane wartości, maksymalnie 8
    * @return   Kod błędu
    */
    errno_t FieldBusSlaveReadDI(uint8_t DOIndex, uint8_t readNum, uint8_t status[8]);

Odczyt AI stacji podrzędnej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief  Odczytuje AI stacji podrzędnej
    * @param  [in] AOIndex  Numer AI
    * @param  [in] readNum  Liczba do odczytu
    * @param  [out] status[8] Odczytane wartości, maksymalnie 8
    * @return   Kod błędu
    */
    errno_t FieldBusSlaveReadAI(uint8_t AIIndex, uint8_t readNum, double status[8]);

Oczekiwanie na wejście rozszerzone DI
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Oczekuje na wejście rozszerzone DI
    * @param [in] DIIndex Numer DI
    * @param [in] status 0-niski poziom; 1-wysoki poziom
    * @param [in] waitMs Maksymalny czas oczekiwania (ms)
    * @return Kod błędu
    */
    errno_t FRRobot::FieldBusSlaveWaitDI(uint8_t DIIndex, bool status, int waitMs);

Oczekiwanie na wejście rozszerzone AI
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Oczekuje na wejście rozszerzone AI
    * @param [in] AIIndex Numer AI
    * @param [in] waitType 0-większe niż; 1-mniejsze niż
    * @param [in] value Wartość AI
    * @param [in] waitMs Maksymalny czas oczekiwania (ms)
    * @return Kod błędu
    */
    errno_t FRRobot::FieldBusSlaveWaitAI(uint8_t AIIndex, uint8_t waitType, double value, int waitMs);

Przykład kodu instrukcji interfejsu w trybie stacji podrzędnej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    void testFieldBusBoard()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        uint8_t type = 0, version = 0, connState = 0;
        uint8_t ctrl[8];
        double ctrlAO[8];
        static uint8_t DI[8];
        static double AI[8];
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return;
        }
        robot.SetReConnectParam(true, 30000, 500);
        // Przesyłanie i ładowanie pliku otwartego protokołu
        robot.OpenLuaUpload("E://Projekt/SDK urządzeń peryferyjnych/CtrlDev_field.lua");
        robot.Sleep(2000);
        robot.SetCtrlOpenLUAName(3, "CtrlDev_field.lua");
        robot.UnloadCtrlOpenLUA(3);
        robot.LoadCtrlOpenLUA(3);
        robot.Sleep(8000);

        // Pobranie typu protokołu, wersji oprogramowania i stanu połączenia z PLC płyty stacji podrzędnej
        robot.GetFieldBusConfig(&type, &version, &connState);
        printf("type is %d, version is %d,connState is %d\n", type, version, connState);

        // Zapis DO0 = 1, DO1 = 0, DO2 = 1
        ctrl[0] = 0;
        ctrl[1] = 1;
        ctrl[2] = 1;
        robot.FieldBusSlaveWriteDO(0, 3, ctrl);

        // Zapis AO2 = 0x1000
        ctrlAO[0] = 0x1005;
        robot.FieldBusSlaveWriteAO(2, 1, ctrlAO);

        // Cykliczne monitorowanie DI0~DI3 AI0~AI2
        for (int i = 0; i < 100; i++)
        {
            robot.FieldBusSlaveReadDI(0, 4, DI);
            printf("DI0 is %d, DI1 is %d,DI2 is %d,DI3 is %d\n", DI[0], DI[1], DI[2], DI[3]);
            robot.FieldBusSlaveReadAI(0, 3, AI);
            printf("AI0 is %d, AI1 is %d,AI2 is %d\n", AI[0], AI[1], AI[2]);
            robot.Sleep(10);
        }

        // Oczekiwanie, czy DI0 ma wartość 1, czas oczekiwania 100 ms, wydruk wyniku
        int ret = robot.FieldBusSlaveWaitDI(0, 1, 100);
        printf("FieldBusSlaveWaitDI result is  %d\n", ret);

        // Oczekiwanie, czy AI0 jest większe niż 400, czas oczekiwania 100 ms, wydruk wyniku
        ret = robot.FieldBusSlaveWaitAI(0,0,400.00,100);
        printf("FieldBusSlaveWaitAI result is  %d\n", ret);

        robot.CloseRPC();
    }

Włączanie/wyłączanie urządzenia peryferyjnego lasera
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
     * @brief Funkcja włączania/wyłączania urządzenia peryferyjnego lasera
     * @param [in] OnOff 0-wyłącz 1-włącz
     * @param [in] weldId ID spoiny, domyślnie 0
     * @return Kod błędu
     */
    errno_t LaserTrackingLaserOnOff(int OnOff,int weldId);

Rozpoczynanie/zatrzymywanie śledzenia laserowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
     * @brief Funkcja rozpoczynania/zatrzymywania śledzenia laserowego
     * @param [in] OnOff 0-zatrzymaj 1-rozpocznij
     * @param [in] coordId Numer układu współrzędnych narzędzia urządzenia peryferyjnego lasera
     * @return Kod błędu
     */
    errno_t LaserTrackingTrackOnOff(int OnOff, int coordId);

Rozpoczynanie lokalizacji laserowej - stały kierunek
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
    * @brief Lokalizacja laserowa - stały kierunek
    * @param [in] direction 0-x+ 1-x- 2-y+ 3-y- 4-z+ 5-z-
    * @param [in] vel Prędkość, jednostka %
    * @param [in] distance Maksymalna odległość lokalizacji, jednostka mm
    * @param [in] timeout Czas timeoutu lokalizacji, jednostka ms
    * @param [in] posSensorNum Numer narzędzia skalibrowanego lasera
    * @return Kod błędu
    */
    errno_t LaserTrackingSearchStart_xyz(int direction, int vel, int distance, int timeout, int posSensorNum);

Rozpoczynanie lokalizacji laserowej - kierunek dowolnego punktu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
     * @brief Lokalizacja laserowa - dowolny kierunek
     * @param [in] directionPoint Współrzędne xyz punktu wejściowego lokalizacji
     * @param [in] vel Prędkość, jednostka %
     * @param [in] distance Maksymalna odległość lokalizacji, jednostka mm
     * @param [in] timeout Czas timeoutu lokalizacji, jednostka ms
     * @param [in] posSensorNum Numer narzędzia skalibrowanego lasera
     * @return Kod błędu
     */
    errno_t LaserTrackingSearchStart_point(DescTran directionPoint, int vel, int distance, int timeout, int posSensorNum);

Zakończenie lokalizacji laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
     * @brief Zakończenie lokalizacji laserowej
     * @return Kod błędu
     */
    errno_t LaserTrackingSearchStop();

Konfiguracja parametrów sieciowych lasera
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
     * @brief Konfiguruje parametry sieciowe lasera
     * @param [in] ip Adres IP urządzenia peryferyjnego lasera
     * @param [in] port Numer portu urządzenia peryferyjnego lasera
     * @return Kod błędu
     */
    errno_t LaserTrackingSensorConfig(std::string ip, int port);

Konfiguracja okresu próbkowania urządzenia peryferyjnego lasera
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
    * @brief Konfiguruje okres próbkowania urządzenia peryferyjnego lasera
    * @param [in] period Okres próbkowania urządzenia peryferyjnego lasera, jednostka ms
    * @return Kod błędu
    */
    errno_t LaserTrackingSensorSamplePeriod(int period);

Ładowanie sterownika urządzenia peryferyjnego lasera
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
     * @brief Ładowanie sterownika urządzenia peryferyjnego lasera
     * @param [in] type Typ protokołu sterownika urządzenia peryferyjnego lasera 101-Rui niu 102-Chuang xiang 103-Quan shi 104-Tong zhou 105-Ao tai
     * @return Kod błędu
     */
    errno_t LoadPosSensorDriver(int type);

Zwalnianie sterownika urządzenia peryferyjnego lasera
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
     * @brief Zwalnianie sterownika urządzenia peryferyjnego lasera
     * @return Kod błędu
     */
    errno_t UnLoadPosSensorDriver();

Rejestracja trajektorii spoiny laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
    * @brief Rejestracja trajektorii spoiny laserowej
    * @param [in] status 0-zatrzymaj rejestrację 1-śledzenie w czasie rzeczywistym 2-rozpocznij rejestrację
    * @param [in] delayTime Czas opóźnienia, jednostka ms
    * @return Kod błędu
    */
    errno_t LaserSensorRecord1(int status, int delayTime);

Odtwarzanie trajektorii spoiny laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
     * @brief Odtwarzanie trajektorii spoiny laserowej
     * @param [in] delayTime Czas opóźnienia, jednostka ms
     * @param [in] speed Prędkość, jednostka %
     * @return Kod błędu
     */
    errno_t LaserSensorReplay(int delayTime, double speed);

Odtwarzanie śledzenia laserowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
     * @brief Odtwarzanie śledzenia laserowego
     * @return Kod błędu
     */
    errno_t MoveLTR();

Rejestracja i odtwarzanie trajektorii spoiny laserowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
    * @brief Rejestracja i odtwarzanie trajektorii spoiny laserowej
    * @param [in] delayMode Tryb 0-czas opóźnienia 1-odległość opóźnienia
    * @param [in] delayTime Czas opóźnienia, jednostka ms
    * @param [in] delayDisExAxisNum Numer osi rozszerzonej dla odległości opóźnienia
    * @param [in] delayDis Odległość opóźnienia, jednostka mm
    * @param [in] sensitivePara Współczynnik czułości kompensacji
    * @param [in] trackMode Typ śledzenia punktowego. 0-ruch asynchroniczny osi rozszerzonej; 1-robot
    * @param [in] triggerMode Sposób wyzwalania śledzenia punktowego. 0-czas śledzenia; 1-IO
    * @param [in] runTime Czas śledzenia punktowego robota (s)
    * @param [in] speed Prędkość, jednostka %
    * @return Kod błędu
    */
    errno_t LaserSensorRecordandReplay(int delayMode, int delayTime, int delayDisExAxisNum, double delayDis, double sensitivePara, int trackMode, int triggerMode, double runTime, double speed);

Ruch do punktu początkowego zarejestrowanej spoiny
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
    * @brief Ruch do punktu początkowego zarejestrowanej spoiny
    * @param [in] moveType 0-moveJ 1-moveL
    * @param [in] ovl Prędkość, jednostka %
    * @return Kod błędu
    */
    errno_t MoveToLaserRecordStart(int moveType, double ovl);

Ruch do punktu końcowego zarejestrowanej spoiny
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
    * @brief Ruch do punktu końcowego zarejestrowanej spoiny
    * @param [in] moveType 0-moveJ 1-moveL
    * @param [in] ovl Prędkość, jednostka %
    * @return Kod błędu
    */
    errno_t MoveToLaserRecordEnd(int moveType, double ovl);

Ruch do punktu lokalizacji czujnika laserowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
    * @brief Ruch do punktu lokalizacji czujnika laserowego
    * @param [in] moveFlag Typ ruchu: 0-PTP; 1-LIN
    * @param [in] ovl Współczynnik skalowania prędkości, 0-100
    * @param [in] dataFlag Wybór danych bufora spoiny: 0-wykonaj dane planowania; 1-wykonaj dane rejestracji
    * @param [in] plateType Typ blachy: 0-falista; 1-trapezowa; 2-ogrodzeniowa; 3-beczka po oleju; 4-falista stal pancerna
    * @param [in] trackOffectType Typ przesunięcia czujnika laserowego: 0-bez przesunięcia; 1-przesunięcie w układzie bazowym; 2-przesunięcie w układzie narzędzia; 3-przesunięcie w surowych danych lasera
    * @param [in] offset Wartość przesunięcia
    * @return Kod błędu
    */
    errno_t MoveToLaserSeamPos(int moveFlag, double ovl, int dataFlag, int plateType, int trackOffectType, DescPose offset);

Pobieranie współrzędnych punktu lokalizacji czujnika laserowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera informacje o współrzędnych punktu lokalizacji czujnika laserowego
    * @param [in] trackOffectType Typ przesunięcia czujnika laserowego: 0-bez przesunięcia; 1-przesunięcie w układzie bazowym; 2-przesunięcie w układzie narzędzia; 3-przesunięcie w surowych danych lasera
    * @param [in] offset Wartość przesunięcia
    * @param [out] jPos Pozycja stawów [°]
    * @param [out] descPos Pozycja kartezjańska [mm]
    * @param [out] tool Układ współrzędnych narzędzia
    * @param [out] user Układ współrzędnych obiektu
    * @param [out] exaxis Pozycja osi rozszerzonej [mm]
    * @return Kod błędu
    */
    errno_t GetLaserSeamPos(int trackOffectType, DescPose offset, JointPos& jPos, DescPose& descPos, int& tool, int& user, ExaxisPos& exaxis);

Przykład kodu konfiguracji parametrów i debugowania urządzenia peryferyjnego lasera
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    void testLaserConfig()
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
            return;
        }
        robot.SetReConnectParam(true, 30000, 500);
        // Ustawienie adresu IP i numeru portu
        robot.LaserTrackingSensorConfig("192.168.58.20", 5020);
        // Ustawienie okresu próbkowania
        robot.LaserTrackingSensorSamplePeriod(20);
        // Załadowanie sterownika
        robot.LoadPosSensorDriver(101);
        // Wyłączenie urządzenia peryferyjnego lasera
        robot.LaserTrackingLaserOnOff(0,0);
        robot.Sleep(3000);
        // Włączenie urządzenia peryferyjnego lasera
        robot.LaserTrackingLaserOnOff(1, 0);
        robot.CloseRPC();
    }

Przykład kodu skanowania trajektorii laserowej i odtwarzania trajektorii
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    void testLaserRecordAndReplay()
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
            return;
        }
        robot.SetReConnectParam(true, 30000, 500);

        // Przesyłanie i ładowanie pliku otwartego protokołu
        robot.OpenLuaUpload("E://openlua/CtrlDev_laser_ruiniu-0117.lua");
        robot.Sleep(2000);
        robot.SetCtrlOpenLUAName(0, "CtrlDev_laser_ruiniu-0117.lua");
        robot.UnloadCtrlOpenLUA(0);
        robot.LoadCtrlOpenLUA(0);
        robot.Sleep(8000);
        int cnt = 1;
        while(cnt<31)
        {
            // Ruch do punktu początkowego skanowania
            JointPos startjointPos(56.205, -117.951, 141.872, -118.149, -94.217, -122.176);
            DescPose startdescPose(-97.552, -282.855, 26.675, 174.182, -1.338, -91.707);
            ExaxisPos exaxisPos(0, 0, 0, 0);
            DescPose offdese(0, 0, 0, 0, 0, 0);
            robot.MoveL(&startjointPos, &startdescPose, 1, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese, 1, 1);
            // Rozpoczęcie rejestracji trajektorii
            robot.LaserSensorRecord1(2, 10);
            // Ruch do punktu końcowego rejestracji
            JointPos endjointPos(68.809, -87.100, 121.120, -127.233, -95.038, -109.555);
            DescPose enddescPose(-103.555, -464.234, 13.076, 174.179, -1.344, -91.709);
            robot.MoveL(&endjointPos, &enddescPose, 1, 0, 30, 100, 100, -1, &exaxisPos, 0, 0, &offdese, 1, 1);
            // Zatrzymanie rejestracji
            robot.LaserSensorRecord1(0, 10);
            // Ruch do punktu początkowego zarejestrowanej spoiny
            robot.MoveToLaserRecordStart(1, 30);
            // Rozpoczęcie odtwarzania trajektorii
            robot.LaserSensorReplay(10, 100);
            robot.MoveLTR();
            // Zatrzymanie odtwarzania trajektorii
            robot.LaserSensorRecord1(0, 10);
            printf("Laserowe skanowanie + test stabilności odtwarzania trajektorii, %d raz\n", cnt);
            cnt++;
        }
        robot.CloseRPC();
    }

Przykład kodu lokalizacji laserowej i śledzenia w czasie rzeczywistym
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    void testLasertrack()
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
            return;
        }
        robot.SetReConnectParam(true, 30000, 500);

        // Przesyłanie i ładowanie pliku otwartego protokołu
        robot.OpenLuaUpload("E://openlua/CtrlDev_laser_ruiniu-0117.lua");
        robot.Sleep(2000);
        robot.SetCtrlOpenLUAName(0, "CtrlDev_laser_ruiniu-0117.lua");
        robot.UnloadCtrlOpenLUA(0);
        robot.LoadCtrlOpenLUA(0);
        robot.Sleep(8000);
        int cnt = 1;
        while (cnt < 2)
        {
            // Ruch do punktu początkowego lokalizacji
            JointPos startjointPos(58.337, -119.628, 146.037, -116.358, -92.224, -117.654);
            DescPose startdescPose(-53.375, -255.363, 0.919, 178.054, 1.077, -94.026);
            ExaxisPos exaxisPos(0, 0, 0, 0);
            DescPose offdese(0, 0, 0, 0, 0, 0);
            DescTran directionPoint;
            robot.MoveL(&startjointPos, &startdescPose, 1, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese, 1, 1);

            // Rozpoczęcie lokalizacji w kierunku -y
            int ret = robot.LaserTrackingSearchStart_xyz(3, 100, 300, 1000, 2);
            robot.LaserTrackingSearchStop();
            // Jeśli lokalizacja się powiodła
            if (ret == 0)
            {
                // Ruch do punktu lokalizacji
                robot.MoveToLaserSeamPos(1, 30, 0, 0, 0, offdese);
                // Rozpoczęcie śledzenia laserowego wzdłuż punktu lokalizacji
                robot.LaserTrackingTrackOnOff(1, 2);
                JointPos endjointPos(70.580, -90.918, 126.593, -125.154, -92.162, -105.403);
                DescPose enddescPose(-53.375, -419.020, 0.920, 178.054, 1.076, -94.026);
                robot.MoveL(&endjointPos, &enddescPose, 1, 0, 20, 100, 100, -1, &exaxisPos, 0, 0, &offdese, 1, 1);
                // Zatrzymanie śledzenia
                robot.LaserTrackingTrackOnOff(0, 2);

            }
            cnt++;
        }
        robot.CloseRPC();
    }

Przykład kodu synchronizacji śledzenia laserowego z osią rozszerzoną i robotem
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
    :linenos:

    void testLasertrackandExitAxis()
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
            return;
        }
        robot.SetReConnectParam(true, 30000, 500);

        ExaxisPos startexaxisPos = { 0,0,0,0 };
        ExaxisPos seamexaxisPos = { -10,0,0,0 };
        ExaxisPos endexaxisPos = { -30, 0, 0, 0 };
        DescPose offdese = { 0, 0, 0, 0, 0, 0 };
        JointPos seamjointPos(0, 0, 0, 0, 0, 0);
        DescPose seamdescPose(0, 0, 0, 0, 0, 0);

        int cnt = 1;
        while (cnt < 31)
        {
            // Ruch do punktu początkowego lokalizacji
            JointPos startjointPos(58.337, -119.628, 146.037, -116.358, -92.224, -117.654);
            DescPose startdescPose(-53.375, -255.363, 0.919, 178.054, 1.077, -94.026);
            robot.ExtAxisSyncMoveJ(startjointPos, startdescPose, 1, 0, 100, 100, 100, startexaxisPos, -1, 0, offdese);

            // Rozpoczęcie lokalizacji w kierunku -y
            int ret = robot.LaserTrackingSearchStart_xyz(3, 100, 300, 1000, 2);
            robot.LaserTrackingSearchStop();
            int tool = 0;
            int user = 0;
            robot.GetLaserSeamPos(0, offdese, seamjointPos, seamdescPose, tool, user, startexaxisPos);
            printf("%f, %f, %f,%f, %f, %f,%f, %f, %f,%f, %f, %f\n", seamjointPos.jPos[0], seamjointPos.jPos[1], seamjointPos.jPos[2], seamjointPos.jPos[3], seamjointPos.jPos[4], seamjointPos.jPos[5], seamdescPose.tran.x, seamdescPose.tran.y, seamdescPose.tran.z, seamdescPose.rpy.rx, seamdescPose.rpy.ry, seamdescPose.rpy.rz);

            // Jeśli lokalizacja się powiodła
            if (ret == 0)
            {
                // Synchroniczny ruch robota i osi rozszerzonej do punktu lokalizacji
                robot.ExtAxisSyncMoveJ(seamjointPos, seamdescPose, 1, 0, 100, 100, 100, seamexaxisPos, -1, 0, offdese);

                // Rozpoczęcie śledzenia laserowego wzdłuż punktu lokalizacji z synchronizacją ruchu osi rozszerzonej
                robot.LaserTrackingTrackOnOff(1, 2);
                JointPos endjointPos(70.580, -90.918, 126.593, -125.154, -92.162, -105.403);
                DescPose enddescPose(-53.375, -419.020, 0.920, 178.054, 1.076, -94.026);
                robot.ExtAxisSyncMoveL(endjointPos, enddescPose, 1, 0, 20, 100, 100, -1, endexaxisPos, 0, offdese);;
                // Zatrzymanie śledzenia
                robot.LaserTrackingTrackOnOff(0, 2);
            }
            cnt++;
            printf("Synchronizacja śledzenia laserowego z osią rozszerzoną i robotem, %d raz\n", cnt);
        }
        robot.CloseRPC();
    }

Włączanie/wyłączanie funkcji transmisji przez końcówkę
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Włączanie/wyłączanie funkcji transmisji przez końcówkę
    * @param [in] mode 0-wyłącz, 1-włącz
    * @return Kod błędu
    */
    errno_t SetAxleGenComEnable(int mode);

Wysyłanie i odbieranie danych nieokresowych w funkcji transmisji przez końcówkę
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Wysyłanie i odbieranie danych nieokresowych w funkcji transmisji przez końcówkę
    * @param [in] lenSnd Długość wysyłanych danych
    * @param [in] sndBuff Dane do wysłania
    * @param [in] lenRcv Wybór długości odbieranych danych
    * @param [out] rcvBuff Odebrane dane odpowiedzi
    * @return Kod błędu
    */
    errno_t SndRcvAxleGenComCmdData(int lenSnd, int sndBuff[130], int lenRcv, int rcvData[130]);

Przykład kodu komunikacji danych nieokresowych dla głowicy terapeutycznej Beiyikang opartej na funkcji transmisji przez końcówkę
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int testAxleGenCom()
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
      int led_on[6] = { 0xAB, 0xBA, 0x12, 0x01, 0x01, 0x79 };
      int led_off[6] = { 0xAB, 0xBA, 0x12, 0x01, 0x00, 0x78 };
      int version[5] = { 0xAB, 0xBA, 0x11, 0x00, 0x76 };
      int state[6] = { 0xAB, 0xBA, 0x1B, 0x01, 0xAA, 0x2B };
      int cycleState[6] = { 0xAB, 0xBA, 0x12, 0x01, 0x00, 0x78 };
      int rcvdata[16] = {0};
      int ret = 0;
      int cnt = 1;
      JointPos p1Joint(88.708, -86.178, 140.989, -141.825, -89.162, -49.879);
      DescPose p1Desc(188.007, -377.850, 260.207, 178.715, 2.823, -131.466);
      JointPos p2Joint(112.131, -75.554, 126.989, -139.027, -88.044, -26.477);
      DescPose p2Desc(368.003, -377.848, 260.211, 178.715, 2.823, -131.465);
      ExaxisPos exaxisPos(0, 0, 0, 0);
      DescPose offdese(0, 0, 0, 0, 0, 0);
      // Włączenie funkcji transmisji przez końcówkę
      robot.SetAxleGenComEnable(1);
      robot.SetAxleLuaEnable(1);
      while (cnt <= 10000)
      {
        // Odczytanie numeru wersji
        ret = robot.SndRcvAxleGenComCmdData(5, version, 10, rcvdata);
        printf(" hard version : %d,hard code:%d, soft version:%d %d, soft code:%d \n", rcvdata[4], rcvdata[5], rcvdata[6] ,rcvdata[7], rcvdata[8]);
        if (ret != 0)
        {
          break;
        }
        robot.Sleep(1000);
        // Odczytanie stanu obecności głowicy terapeutycznej
        ret = robot.SndRcvAxleGenComCmdData(6, state, 6, rcvdata);
        printf(" state : %d \n", rcvdata[4]);
        robot.Sleep(1000);
        // Włączenie lasera głowicy terapeutycznej
        ret = robot.SndRcvAxleGenComCmdData(6, led_on, 6, rcvdata);
        printf("led on rcv data is: %d, %d, %d, %d, %d, %d  \n", rcvdata[0], rcvdata[1], rcvdata[2], rcvdata[3], rcvdata[4], rcvdata[5]);
        robot.MoveJ(&p1Joint, &p1Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
        robot.Sleep(4000);
        // Wyłączenie lasera głowicy terapeutycznej
        ret = robot.SndRcvAxleGenComCmdData(6, led_off, 6, rcvdata);
        printf("led off rcv data is: %d, %d, %d, %d, %d, %d \n", rcvdata[0], rcvdata[1], rcvdata[2], rcvdata[3], rcvdata[4], rcvdata[5]);
        robot.MoveJ(&p2Joint, &p2Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
        robot.Sleep(1000);
        printf("***********************complate No. %d SDK test*****************************\n", cnt);
        cnt++;
      }
      robot.CloseRPC();
    }

Pobieranie pliku Lua otwartego protokołu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera plik Lua otwartego protokołu
    * @param [in] fileName Nazwa pliku otwartego protokołu "CtrlDev_XXX.lua"
    * @param [in] savePath Ścieżka zapisu pliku otwartego protokołu
    * @return Kod błędu
    */
    errno_t OpenLuaDownload(std::string fileName, std::string savePath);

Usuwanie pliku Lua otwartego protokołu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Usuwa plik Lua otwartego protokołu
    * @param [in] fileName Nazwa pliku otwartego protokołu Lua do usunięcia "CtrlDev_XXX.lua"
    * @return Kod błędu
    */
    errno_t OpenLuaDelete(std::string fileName);

Usuwanie wszystkich plików Lua otwartego protokołu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Usuwa wszystkie pliki Lua otwartego protokołu
    * @return Kod błędu
    */
    errno_t AllOpenLuaDelete();

Przykład kodu przesyłania, pobierania i usuwania otwartego protokołu urządzeń peryferyjnych sterownika
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestCtrlOpenLuaOperate()
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
        rtn = robot.OpenLuaUpload("D://zUP/openlua/CtrlDev_WELDING_A.lua");
        printf("OpenLuaUpload rtn is %d\n", rtn);
        rtn = robot.OpenLuaUpload("D://zUP/openlua/CtrlDev_SWDPOLISH.lua");
        printf("OpenLuaUpload rtn is %d\n", rtn);
        rtn = robot.OpenLuaDownload("CtrlDev_WELDING_A.lua", "D://zDOWN/");
        printf("OpenLuaDownload rtn is %d\n", rtn);
        rtn = robot.OpenLuaDownload("CtrlDev_SWDPOLISH.lua", "D://zDOWN/");
        printf("OpenLuaDownload rtn is %d\n", rtn);
        rtn = robot.SetCtrlOpenLUAName(0, "CtrlDev_WELDING_A.lua");
        printf("SetCtrlOpenLUAName rtn is %d\n", rtn);
        rtn = robot.SetCtrlOpenLUAName(1, "CtrlDev_SWDPOLISH.lua");
        printf("SetCtrlOpenLUAName rtn is %d\n", rtn);
        std::string name[4] = {};
        rtn = robot.GetCtrlOpenLUAName(name);
        printf("ctrl open lua names : %s, %s, %s, %s\n", name[0].c_str(), name[1].c_str(), name[2].c_str(), name[3].c_str());
        rtn = robot.LoadCtrlOpenLUA(1);
        printf("LoadCtrlOpenLUA rtn is %d\n", rtn);
        robot.Sleep(2000);
        rtn = robot.UnloadCtrlOpenLUA(1);
        printf("UnloadCtrlOpenLUA rtn is %d\n", rtn);
        rtn = robot.OpenLuaDelete("CtrlDev_WELDING_A.lua");
        printf("OpenLuaDelete rtn is %d\n", rtn);
        rtn = robot.AllOpenLuaDelete();
        printf("AllOpenLuaDelete rtn is %d\n", rtn);
        robot.CloseRPC();
        robot.Sleep(1000);
        return 0;
    }