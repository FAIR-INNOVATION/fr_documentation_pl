Ustawienia ogólne robota
========================

.. toctree:: 
    :maxdepth: 5

Ustawienie punktu odniesienia narzędzia - metoda sześciopunktowa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Ustawia punkt odniesienia narzędzia - metoda sześciopunktowa
     * @param [in] point_num Numer punktu, zakres [1~6] 
     * @return Kod błędu
     */
    errno_t SetToolPoint(int point_num);

Obliczenie układu współrzędnych narzędzia
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Oblicza układ współrzędnych narzędzia
     * @param [out] tcp_pose Układ współrzędnych narzędzia
     * @return Kod błędu
     */
    errno_t ComputeTool(DescPose *tcp_pose);

Ustawienie punktu odniesienia narzędzia - metoda czteropunktowa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Ustawia punkt odniesienia narzędzia - metoda czteropunktowa
     * @param [in] point_num Numer punktu, zakres [1~4] 
     * @return Kod błędu
     */
    errno_t SetTcp4RefPoint(int point_num);

Obliczenie układu współrzędnych narzędzia
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Oblicza układ współrzędnych narzędzia
     * @param [out] tcp_pose Układ współrzędnych narzędzia
     * @return Kod błędu
     */
    errno_t ComputeTcp4(DescPose *tcp_pose);

Obliczenie układu współrzędnych narzędzia na podstawie punktów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.8-3.7.8

.. code-block:: c++
    :linenos:

    /**
     * @brief Oblicza układ współrzędnych narzędzia na podstawie punktów
     * @param [in] method Metoda obliczeniowa; 0-metoda czteropunktowa; 1-metoda sześciopunktowa
     * @param [in] pos Grupa pozycji stawów, długość tablicy 4 dla metody czteropunktowej, długość 6 dla metody sześciopunktowej
     * @param [out] coord Wynik układu współrzędnych narzędzia
     * @return Kod błędu
     */
    errno_t ComputeToolCoordWithPoints(int method, JointPos pos[], DescPose& coord);

Ustawienie układu współrzędnych narzędzia
+++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief  Ustawia układ współrzędnych narzędzia
     * @param  [in] id Numer układu współrzędnych, zakres [0~14]
     * @param  [in] coord  Pozycja środka narzędzia względem środka kołnierza końcowego
     * @param  [in] type  0-układ współrzędnych narzędzia, 1-układ współrzędnych czujnika
     * @param  [in] install Pozycja instalacji, 0-koniec robota, 1-na zewnątrz robota
     * @param  [in] toolID ID narzędzia
     * @param  [in] loadNum Numer obciążenia
     * @return  Kod błędu
     */
    errno_t SetToolCoord(int id, DescPose *coord, int type, int install, int toolID, int loadNum);

Ustawienie listy układów współrzędnych narzędzia
++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief  Ustawia listę układów współrzędnych narzędzia
     * @param  [in] id Numer układu współrzędnych, zakres [0~14]
     * @param  [in] coord  Pozycja środka narzędzia względem środka kołnierza końcowego
     * @param  [in] type  0-układ współrzędnych narzędzia, 1-układ współrzędnych czujnika
     * @param  [in] install Pozycja instalacji, 0-koniec robota, 1-na zewnątrz robota
     * @param  [in] loadNum Numer obciążenia
     * @return  Kod błędu
     */
    errno_t SetToolList(int id, DescPose *coord, int type, int install, int loadNum);

Pobranie bieżącego układu współrzędnych narzędzia
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Pobiera bieżący układ współrzędnych narzędzia
    * @param  [in] flag 0-blokujący, 1-nieblokujący
    * @param  [out] desc_pos Pozycja i orientacja układu współrzędnych narzędzia
    * @return  Kod błędu
    */
    errno_t GetTCPOffset(uint8_t flag, DescPose *desc_pos);

Przykład kodu operacji na układzie współrzędnych narzędzia robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     int TestTCPCompute(void)
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
         DescPose p1Desc(186.331, 487.913, 209.850, 149.030, 0.688, -114.347);
         JointPos p1Joint(-127.876, -75.341, 115.417, -122.741, -59.820, 74.300);
         DescPose p2Desc(69.721, 535.073, 202.882, -144.406, -14.775, -89.012);
         JointPos p2Joint(-101.780, -69.828, 110.917, -125.740, -127.841, 74.300);
         DescPose p3Desc(146.861, 578.426, 205.598, 175.997, -36.178, -93.437);
         JointPos p3Joint(-112.851, -60.191, 86.566, -80.676, -97.463, 74.300);
         DescPose p4Desc(136.284, 509.876, 225.613, 178.987, 1.372, -100.696);
         JointPos p4Joint(-116.397, -76.281, 113.845, -128.611, -88.654, 74.299);
         DescPose p5Desc(138.395, 505.972, 298.016, 179.134, 2.147, -101.110);
         JointPos p5Joint(-116.814, -82.333, 109.162, -118.662, -88.585, 74.302);
         DescPose p6Desc(105.553, 454.325, 232.017, -179.426, 0.444, -99.952);
         JointPos p6Joint(-115.649, -84.367, 122.447, -128.663, -90.432, 74.303);
         ExaxisPos exaxisPos(0, 0, 0, 0);
         DescPose offdese(0, 0, 0, 0, 0, 0);
         JointPos posJ[6] = { p1Joint , p2Joint , p3Joint , p4Joint , p5Joint , p6Joint };
         DescPose coordRtn = {};
         rtn = robot.ComputeToolCoordWithPoints(1, posJ, coordRtn);
         printf("ComputeToolCoordWithPoints    %d  coord is %f %f %f %f %f %f \n", rtn, coordRtn.tran.x, coordRtn.tran.y, coordRtn.tran.z, coordRtn.rpy.rx, coordRtn.rpy.ry, coordRtn.rpy.rz);
         robot.MoveJ(&p1Joint, &p1Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetToolPoint(1);
         robot.MoveJ(&p2Joint, &p2Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetToolPoint(2);
         robot.MoveJ(&p3Joint, &p3Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetToolPoint(3);
         robot.MoveJ(&p4Joint, &p4Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetToolPoint(4);
         robot.MoveJ(&p5Joint, &p5Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetToolPoint(5);
         robot.MoveJ(&p6Joint, &p6Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetToolPoint(6);
         rtn = robot.ComputeTool(&coordRtn);
         printf("6 Point ComputeTool        %d  coord is %f %f %f %f %f %f \n", rtn, coordRtn.tran.x, coordRtn.tran.y, coordRtn.tran.z, coordRtn.rpy.rx, coordRtn.rpy.ry, coordRtn.rpy.rz);
         robot.SetToolList(1, &coordRtn, 0, 0, 0);
         robot.MoveJ(&p1Joint, &p1Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetTcp4RefPoint(1);
         robot.MoveJ(&p2Joint, &p2Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetTcp4RefPoint(2);
         robot.MoveJ(&p3Joint, &p3Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetTcp4RefPoint(3);
         robot.MoveJ(&p4Joint, &p4Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetTcp4RefPoint(4);
         rtn = robot.ComputeTcp4(&coordRtn);
         printf("4 Point ComputeTool        %d  coord is %f %f %f %f %f %f \n", rtn, coordRtn.tran.x, coordRtn.tran.y, coordRtn.tran.z, coordRtn.rpy.rx, coordRtn.rpy.ry, coordRtn.rpy.rz);
         robot.SetToolCoord(2, &coordRtn, 0, 0, 1, 0);
         DescPose getCoord = {};
         rtn = robot.GetTCPOffset(0, &getCoord);
         printf("GetTCPOffset    %d  coord is %f %f %f %f %f %f \n", rtn, coordRtn.tran.x, coordRtn.tran.y, coordRtn.tran.z, coordRtn.rpy.rx, coordRtn.rpy.ry, coordRtn.rpy.rz);
         robot.CloseRPC();
         return 0;
     }

Ustawienie punktu odniesienia zewnętrznego narzędzia - metoda sześciopunktowa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Ustawia punkt odniesienia zewnętrznego narzędzia - metoda sześciopunktowa
     * @param [in] point_num Numer punktu, zakres [1~4] 
     * @return Kod błędu
     */
    errno_t SetExTCPPoint(int point_num);

Obliczenie zewnętrznego układu współrzędnych narzędzia
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Oblicza zewnętrzny układ współrzędnych narzędzia
     * @param [out] tcp_pose Zewnętrzny układ współrzędnych narzędzia
     * @return Kod błędu
     */
    errno_t ComputeExTCF(DescPose *tcp_pose);  

Ustawianie Zewnętrznego Układu Współrzędnych Narzędzia
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v3.9.8

.. code-block:: c++
    :linenos:

    /**
    * @brief  Ustawia zewnętrzny układ współrzędnych narzędzia
    * @param  [in] id Numer układu współrzędnych, 20-39 odpowiadają zewnętrznym układom współrzędnych narzędzi 0-19
    * @param  [in] etcp  Pozycja punktu centralnego narzędzia względem środka kołnierza końcówki
    * @param  [in] etool  Pozycja układu współrzędnych przedmiotu zamontowanego na końcówce robota
    * @return  Kod błędu
    */
    errno_t  SetExToolCoord(int id, DescPose *etcp, DescPose *etool);

Ustawianie Listy Zewnętrznych Układów Współrzędnych Narzędzi
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v3.9.8

.. code-block:: c++
    :linenos:

    /**
    * @brief  Ustawia listę zewnętrznych układów współrzędnych narzędzi
    * @param  [in] id Numer układu współrzędnych, 20-39 odpowiadają zewnętrznym układom współrzędnych narzędzi 0-19
    * @param  [in] etcp  Pozycja punktu centralnego narzędzia względem środka kołnierza końcówki
    * @param  [in] etool  Pozycja układu współrzędnych przedmiotu zamontowanego na końcówce robota
    * @return  Kod błędu
    */
    errno_t  SetExToolList(int id, DescPose *etcp, DescPose *etool);

Przykład Kodu Operacji na Zewnętrznym Układzie Współrzędnych Narzędzia Robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v3.9.8

.. code-block:: c++
    :linenos:

    int TestExtCoord(void)
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
        DescPose p1Desc(-89.606, 779.517, 193.516, 178.000, 0.476, -92.484);
        JointPos p1Joint(-108.145, -50.137, 85.818, -125.599, -87.946, 74.329);
        DescPose p2Desc(-24.656, 850.384, 191.361, 177.079, -2.058, -95.355);
        JointPos p2Joint(-111.024, -41.538, 69.222, -114.913, -87.743, 74.329);
        DescPose p3Desc(-99.813, 766.661, 241.878, -176.817, 1.917, -91.604);
        JointPos p3Joint(-107.266, -56.116, 85.971, -122.560, -92.548, 74.331);
        ExaxisPos exaxisPos(0, 0, 0, 0);
        DescPose offdese(0, 0, 0, 0, 0, 0);
        DescPose posTCP[3] = { p1Desc , p2Desc , p3Desc };
        DescPose coordRtn = {};
        robot.MoveJ(&p1Joint, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
        robot.SetExTCPPoint(1);
        robot.MoveJ(&p2Joint, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
        robot.SetExTCPPoint(2);
        robot.MoveJ(&p3Joint, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
        robot.SetExTCPPoint(3);
        rtn = robot.ComputeExTCF(&coordRtn);
        printf("ComputeExTCF          %d coord is %f %f %f %f %f %f \n", rtn, coordRtn.tran.x, coordRtn.tran.y, coordRtn.tran.z, coordRtn.rpy.rx, coordRtn.rpy.ry, coordRtn.rpy.rz);
        robot.SetExToolCoord(21, &coordRtn, &offdese);
        robot.SetExToolList(21, &coordRtn, &offdese);
        robot.CloseRPC();
        return 0;
    }

Ustawienie punktu odniesienia przedmiotu - metoda trzypunktowa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Ustawia punkt odniesienia przedmiotu - metoda trzypunktowa
     * @param [in] point_num Numer punktu, zakres [1~3] 
     * @return Kod błędu
     */
    errno_t SetWObjCoordPoint(int point_num);

Obliczenie układu współrzędnych przedmiotu
++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief  Oblicza układ współrzędnych przedmiotu
     * @param [in] method Metoda obliczeniowa 0: początek - oś X - oś Z  1: początek - oś X - płaszczyzna XY
     * @param [in] refFrame Układ odniesienia
     * @param [out] wobj_pose Układ współrzędnych przedmiotu
     * @return Kod błędu
     */
    errno_t ComputeWObjCoord(int method, int refFrame, DescPose *wobj_pose);

Ustawienie układu współrzędnych przedmiotu
++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief  Ustawia układ współrzędnych przedmiotu
     * @param  [in] id Numer układu współrzędnych, zakres [0~14]
     * @param  [in] coord  Pozycja układu współrzędnych przedmiotu względem środka kołnierza końcowego
     * @param  [in] refFrame Układ odniesienia
     * @return  Kod błędu
     */
    errno_t SetWObjCoord(int id, DescPose *coord, int refFrame);

Ustawienie listy układów współrzędnych przedmiotu
+++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief  Ustawia listę układów współrzędnych przedmiotu
     * @param  [in] id Numer układu współrzędnych, zakres [0~14]
     * @param  [in] coord  Pozycja układu współrzędnych przedmiotu względem środka kołnierza końcowego
     * @param  [in] refFrame Układ odniesienia
     * @return  Kod błędu
     */
    errno_t SetWObjList(int id, DescPose *coord, int refFrame);

Obliczenie układu współrzędnych przedmiotu na podstawie punktów
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.8-3.7.8

.. code-block:: c++
    :linenos:

    /**
     * @brief Oblicza układ współrzędnych przedmiotu na podstawie punktów
     * @param [in] method Metoda obliczeniowa; 0: początek - oś X - oś Z  1: początek - oś X - płaszczyzna XY
     * @param [in] pos Trzy grupy pozycji TCP
     * @param [in] refFrame Układ odniesienia
     * @param [out] coord Wynik układu współrzędnych narzędzia
     * @return Kod błędu
     */
    errno_t ComputeWObjCoordWithPoints(int method, DescPose pos[], int refFrame, DescPose& coord);

Pobranie bieżącego układu współrzędnych przedmiotu
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Pobiera bieżący układ współrzędnych przedmiotu
    * @param  [in] flag 0-blokujący, 1-nieblokujący
    * @param  [out] desc_pos Pozycja i orientacja układu współrzędnych przedmiotu
    * @return  Kod błędu
    */   
    errno_t GetWObjOffset(uint8_t flag, DescPose *desc_pos);

Przykład kodu operacji na układzie współrzędnych przedmiotu robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     int TestWobjCoord(void)
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
         DescPose p1Desc(-89.606, 779.517, 193.516, 178.000, 0.476, -92.484);
         JointPos p1Joint(-108.145, -50.137, 85.818, -125.599, -87.946, 74.329);
         DescPose p2Desc(-24.656, 850.384, 191.361, 177.079, -2.058, -95.355);
         JointPos p2Joint(-111.024, -41.538, 69.222, -114.913, -87.743, 74.329);
         DescPose p3Desc(-99.813, 766.661, 241.878, -176.817, 1.917, -91.604);
         JointPos p3Joint(-107.266, -56.116, 85.971, -122.560, -92.548, 74.331);
         ExaxisPos exaxisPos(0, 0, 0, 0);
         DescPose offdese(0, 0, 0, 0, 0, 0);
         DescPose posTCP[3] = { p1Desc , p2Desc , p3Desc };
         DescPose coordRtn = {};
         rtn = robot.ComputeWObjCoordWithPoints(1, posTCP, 0, coordRtn);
         printf("ComputeWObjCoordWithPoints    %d  coord is %f %f %f %f %f %f \n", rtn, coordRtn.tran.x, coordRtn.tran.y, coordRtn.tran.z, coordRtn.rpy.rx, coordRtn.rpy.ry, coordRtn.rpy.rz);
         robot.MoveJ(&p1Joint, &p1Desc, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetWObjCoordPoint(1);
         robot.MoveJ(&p2Joint, &p2Desc, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetWObjCoordPoint(2);
         robot.MoveJ(&p3Joint, &p3Desc, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetWObjCoordPoint(3);
         rtn = robot.ComputeWObjCoord(1, 0, &coordRtn);
         printf("ComputeWObjCoord                   %d  coord is %f %f %f %f %f %f \n", rtn, coordRtn.tran.x, coordRtn.tran.y, coordRtn.tran.z, coordRtn.rpy.rx, coordRtn.rpy.ry, coordRtn.rpy.rz);
         robot.SetWObjCoord(1, &coordRtn, 0);
         robot.SetWObjList(1, &coordRtn, 0);
         DescPose getWobjDesc = {};
         rtn = robot.GetWObjOffset(0, &getWobjDesc);
         printf("GetWObjOffset                   %d  coord is %f %f %f %f %f %f \n", rtn, coordRtn.tran.x, coordRtn.tran.y, coordRtn.tran.z, coordRtn.rpy.rx, coordRtn.rpy.ry, coordRtn.rpy.rz);
         robot.CloseRPC();
         return 0;
     }

Ustawienie prędkości globalnej
++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ustawia prędkość globalną
    * @param  [in] vel  Procent prędkości, zakres [0~100]
    * @return  Kod błędu
    */
    errno_t SetSpeed(int vel);

Ustawienie przyspieszenia robota
++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Ustawia przyspieszenie robota
     * @param [in] acc Procent przyspieszenia robota
     * @return Kod błędu
     */
    errno_t SetOaccScale(double acc);

Pobranie domyślnej prędkości robota
+++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Pobiera domyślną prędkość robota
    * @param  [out] vel  Prędkość, jednostka mm/s
    * @return  Kod błędu
    */   
    errno_t GetDefaultTransVel(float *vel);
    
Ustawienie masy ładunku końcowego
++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.8-3.7.8

.. code-block:: c++
    :linenos:

    /**
     * @brief  Ustawia masę ładunku końcowego
     * @param  [in] loadNum Numer obciążenia
     * @param  [in] weight  Masa ładunku, jednostka kg
     * @return  Kod błędu
     */
    errno_t SetLoadWeight(int loadNum = 0, float weight);

Ustawienie współrzędnych środka ciężkości ładunku końcowego
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia współrzędne środka ciężkości ładunku końcowego
    * @param [in] loadNum Numer obciążenia
    * @param [in] coord Współrzędne środka ciężkości, jednostka mm
    * @return Kod błędu
    */
    errno_t SetLoadCoord(int loadNum, DescTran* coord);

Pobranie masy bieżącego ładunku
+++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Pobiera masę bieżącego ładunku
    * @param  [in] flag 0-blokujący, 1-nieblokujący
    * @param  [out] weight Masa ładunku, jednostka kg
    * @return  Kod błędu
    */
    errno_t GetTargetPayload(uint8_t flag, float *weight);

Pobranie środka ciężkości bieżącego ładunku
+++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Pobiera środek ciężkości bieżącego ładunku
    * @param  [in] flag 0-blokujący, 1-nieblokujący
    * @param  [out] cog Środek ciężkości ładunku, jednostka mm
    * @return  Kod błędu
    */   
    errno_t GetTargetPayloadCog(uint8_t flag, DescTran *cog);

Ustawienie sposobu instalacji robota
++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ustawia sposób instalacji robota
    * @param  [in] install  Sposób instalacji, 0-instalacja normalna, 1-instalacja boczna, 2-instalacja odwrócona
    * @return  Kod błędu
    */
    errno_t SetRobotInstallPos(uint8_t install);   

Ustawienie kąta instalacji robota
+++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ustawia kąt instalacji robota, instalacja swobodna
    * @param  [in] yangle  Kąt nachylenia
    * @param  [in] zangle  Kąt obrotu
    * @return  Kod błędu
    */
    errno_t SetRobotInstallAngle(double yangle, double zangle);

Pobranie kąta instalacji robota
++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Pobiera kąt instalacji robota
    * @param  [out] yangle Kąt nachylenia
    * @param  [out] zangle Kąt obrotu
    * @return  Kod błędu
    */
    errno_t GetRobotInstallAngle(float *yangle, float *zangle);

Ustawienie wartości zmiennej systemowej
+++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ustawia wartość zmiennej systemowej
    * @param  [in] id  Numer zmiennej, zakres [1~20]
    * @param  [in] value Wartość zmiennej
    * @return  Kod błędu
    */
    errno_t SetSysVarValue(int id, float value);

Pobranie wartości zmiennej systemowej
+++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Pobiera wartość zmiennej systemowej
    * @param  [in] id Numer zmiennej systemowej, zakres [1~20]
    * @param  [out] value  Wartość zmiennej systemowej
    * @return  Kod błędu
    */
    errno_t GetSysVarValue(int id, float *value);

Przykład kodu ustawień ogólnych robota
++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     int TestLoadInstall(void)
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
         for (int i = 1; i < 100; i++)
         {
             robot.SetSpeed(i);
             robot.SetOaccScale(i);
             robot.Sleep(30);
         }
         float defaultVel = 0.0;
         robot.GetDefaultTransVel(&defaultVel);
         printf("GetDefaultTransVel is %f\n", defaultVel);
         for (int i = 1; i < 21; i++)
         {
             robot.SetSysVarValue(i, i + 0.5);
             robot.Sleep(100);
         }
         for (int i = 1; i < 21; i++)
         {
             float value = 0;
             robot.GetSysVarValue(i, &value);
             printf("sys value  %d is :%f\n", i, value);
             robot.Sleep(100);
         }
         robot.SetLoadWeight(0, 2.5);
         DescTran loadCoord = {};
         loadCoord.x = 3.0;
         loadCoord.y = 4.0;
         loadCoord.z = 5.0;
         robot.SetLoadCoord(&loadCoord);
         robot.Sleep(1000);
         float getLoad = 0.0;
         robot.GetTargetPayload(0, &getLoad);
         DescTran getLoadTran = {};
         robot.GetTargetPayloadCog(0, &getLoadTran);
         printf("get load is %f; get load cog is %f %f %f\n", getLoad, getLoadTran.x, getLoadTran.y, getLoadTran.z);
         robot.SetRobotInstallPos(0);
         robot.SetRobotInstallAngle(15.0, 25.0);
         float anglex = 0.0;
         float angley = 0.0;
         robot.GetRobotInstallAngle(&anglex, &angley);
         printf("GetRobotInstallAngle x:  %f;  y:  %f\n", anglex, angley);
         robot.CloseRPC();
         return 0;
     }

Przełącznik kompensacji tarcia stawów
+++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Przełącznik kompensacji tarcia stawów
    * @param  [in] state  0-wył., 1-wł.
    * @return  Kod błędu
    */
    errno_t FrictionCompensationOnOff(uint8_t state);

Ustawienie współczynnika kompensacji tarcia stawów - instalacja normalna
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ustawia współczynnik kompensacji tarcia stawów - instalacja normalna
    * @param  [in] coeff Współczynniki kompensacji dla sześciu stawów, zakres [0~1]
    * @return  Kod błędu
    */
    errno_t SetFrictionValue_level(float coeff[6]);

Ustawienie współczynnika kompensacji tarcia stawów - instalacja boczna
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ustawia współczynnik kompensacji tarcia stawów - instalacja boczna
    * @param  [in] coeff Współczynniki kompensacji dla sześciu stawów, zakres [0~1]
    * @return  Kod błędu
    */
    errno_t SetFrictionValue_wall(float coeff[6]);

Ustawienie współczynnika kompensacji tarcia stawów - instalacja odwrócona
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ustawia współczynnik kompensacji tarcia stawów - instalacja odwrócona
    * @param  [in] coeff Współczynniki kompensacji dla sześciu stawów, zakres [0~1]
    * @return  Kod błędu
    */
    errno_t SetFrictionValue_ceiling(float coeff[6]);

Ustawienie współczynnika kompensacji tarcia stawów - instalacja swobodna
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ustawia współczynnik kompensacji tarcia stawów - instalacja swobodna
    * @param  [in] coeff Współczynniki kompensacji dla sześciu stawów, zakres [0~1]
    * @return  Kod błędu
    */
    errno_t SetFrictionValue_freedom(float coeff[6]);

Przykład kodu ustawiania kompensacji tarcia stawów robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestFriction(void)
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
       float lcoeff[6] = { 0.9,0.9,0.9,0.9,0.9,0.9 };
       float wcoeff[6] = { 0.4,0.4,0.4,0.4,0.4,0.4 };
       float ccoeff[6] = { 0.6,0.6,0.6,0.6,0.6,0.6 };
       float fcoeff[6] = { 0.5,0.5,0.5,0.5,0.5,0.5 };
       rtn = robot.FrictionCompensationOnOff(1);
       printf("FrictionCompensationOnOff rtn is %d\n", rtn);
       rtn = robot.SetFrictionValue_level(lcoeff);
       printf("SetFrictionValue_level rtn is %d\n", rtn);
       rtn = robot.SetFrictionValue_wall(wcoeff);
       printf("SetFrictionValue_wall rtn is %d\n", rtn);
       rtn = robot.SetFrictionValue_ceiling(ccoeff);
       printf("SetFrictionValue_ceiling rtn is %d\n", rtn);
       rtn = robot.SetFrictionValue_freedom(fcoeff);
       printf("SetFrictionValue_freedom rtn is %d\n", rtn);
       robot.CloseRPC();
       return 0;
    }

Pobranie kodu błędu robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Pobiera kod błędu robota
     * @param  [out] maincode   Główny kod błędu
     * @param  [out] subcode    Podrzędny kod błędu
     * @return  Kod błędu
     */ 
    errno_t GetRobotErrorCode(int *maincode, int *subcode);

Wyczyść błędy
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Czyści stany błędów
    * @return  Kod błędu
    */
    errno_t ResetAllError();

Przykład kodu pobierania stanu awaryjnego i czyszczenia błędów robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestGetError(void)
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
       int maincode, subcode;
       robot.GetRobotErrorCode(&maincode, &subcode);
       printf("robot maincode is %d; subcode is %d\n", maincode, subcode);
       robot.ResetAllError();
       robot.Sleep(1000);
       robot.GetRobotErrorCode(&maincode, &subcode);
       printf("robot maincode is %d; subcode is %d\n", maincode, subcode);
       robot.CloseRPC();
       return 0;
    }

Ustawienie parametrów monitorowania temperatury i prądu wentylatora skrzynki sterowniczej szerokiego napięcia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia parametry monitorowania temperatury i prądu wentylatora skrzynki sterowniczej szerokiego napięcia
    * @param [in] enable 0-nie włączaj monitorowania; 1-włącz monitorowanie
    * @param [in] period Okres monitorowania (s), zakres 1-100
    * @return Kod błędu
    */
    errno_t SetWideBoxTempFanMonitorParam(int enable, int period);
    
Pobranie parametrów monitorowania temperatury i prądu wentylatora skrzynki sterowniczej szerokiego napięcia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera parametry monitorowania temperatury i prądu wentylatora skrzynki sterowniczej szerokiego napięcia
    * @param [out] enable 0-nie włączaj monitorowania; 1-włącz monitorowanie
    * @param [out] period Okres monitorowania (s), zakres 1-100
    * @return Kod błędu
    */
    errno_t GetWideBoxTempFanMonitorParam(int &enable, int &period);
    
Przykład kodu pobierania temperatury i prądu wentylatora skrzynki sterowniczej szerokiego napięcia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     int TestWideVoltageCtrlBoxtemp(void)
     {
         ROBOT_STATE_PKG pkg = {};
         FRRobot robot;
         robot.LoggerInit();
         robot.SetLoggerLevel(1);
         int rtn = robot.RPC("192.168.58.2");
         printf("robot rpc rtn is %d\n", rtn);
         if (rtn != 0)
         {
             return -1;
         }
         robot.SetReConnectParam(true, 30000, 500);
         robot.SetWideBoxTempFanMonitorParam(1, 2);
         int enable = 0;
         int period = 0;
         robot.GetWideBoxTempFanMonitorParam(enable, period);
         printf("GetWideBoxTempFanMonitorParam enable is %d   period is %d\n", enable, period);
         for (int i = 0; i < 100; i++)
         {
             robot.GetRobotRealTimeState(&pkg);
             printf("robot ctrl box temp is %f,  fan current is %d\n", pkg.wideVoltageCtrlBoxTemp, pkg.wideVoltageCtrlBoxFanCurrent);
             robot.Sleep(100);
         }
         rtn = robot.SetWideBoxTempFanMonitorParam(0, 2);
         printf("SetWideBoxTempFanMonitorParam rtn is %d\n", rtn);
         enable = 0;
         period = 0;
         robot.GetWideBoxTempFanMonitorParam(enable, period);
         printf("GetWideBoxTempFanMonitorParam enable is %d   period is %d\n", enable, period);
         for (int i = 0; i < 100; i++)
         {
             robot.GetRobotRealTimeState(&pkg);
             printf("robot ctrl box temp is %f,  fan current is %d\n", pkg.wideVoltageCtrlBoxTemp, pkg.wideVoltageCtrlBoxFanCurrent);
             robot.Sleep(100);
         }
         robot.CloseRPC();
         robot.Sleep(2000);
         return 0;
     }
         
Obliczenie wyniku kalibracji ogniska
++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Oblicza wynik kalibracji ogniska
    * @param [in] pointNum Liczba punktów kalibracji
    * @param [out] resultPos Wynik kalibracji XYZ
    * @param [out] accuracy Błąd dokładności kalibracji
    * @return Kod błędu
    */
    errno_t ComputeFocusCalib(int pointNum, DescTran& resultPos, float& accuracy);
         
Ustawienie współrzędnych ogniska
++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia współrzędne ogniska
    * @param [in] pos Współrzędne ogniska XYZ
    * @return Kod błędu
    */
    errno_t SetFocusPosition(DescTran pos);
         
Rozpoczęcie śledzenia ogniska
+++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Rozpoczyna śledzenie ogniska
    * @param [in] kp Parametr proporcjonalny, domyślnie 50.0
    * @param [in] kpredict Parametr sprzężenia przedniego, domyślnie 19.0
    * @param [in] aMax Maksymalne ograniczenie przyspieszenia kątowego, domyślnie 1440°/s²
    * @param [in] vMax Maksymalne ograniczenie prędkości kątowej, domyślnie 180°/s
    * @param [in] type Zablokowanie kierunku osi X (0-odniesienie do wektora wejściowego; 1-poziomo; 2-pionowo)
    * @return Kod błędu
    */
    errno_t FocusStart(double kp, double kpredict, double aMax, double vMax, int type);
         
Zatrzymanie śledzenia ogniska
+++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Zatrzymuje śledzenie ogniska
    * @return Kod błędu
    */
    errno_t FocusEnd();

Przykład kodu śledzenia ogniska robota
++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestFocus()
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
      DescPose p1Desc(186.331, 487.913, 209.850, 149.030, 0.688, -114.347);
      JointPos p1Joint(-127.876, -75.341, 115.417, -122.741, -59.820, 74.300);
      DescPose p2Desc(69.721, 535.073, 202.882, -144.406, -14.775, -89.012);
      JointPos p2Joint(-101.780, -69.828, 110.917, -125.740, -127.841, 74.300);
      DescPose p3Desc(146.861, 578.426, 205.598, 175.997, -36.178, -93.437);
      JointPos p3Joint(-112.851, -60.191, 86.566, -80.676, -97.463, 74.300);
      DescPose p4Desc(136.284, 509.876, 225.613, 178.987, 1.372, -100.696);
      JointPos p4Joint(-116.397, -76.281, 113.845, -128.611, -88.654, 74.299);
      DescPose p5Desc(138.395, 505.972, 298.016, 179.134, 2.147, -101.110);
      JointPos p5Joint(-116.814, -82.333, 109.162, -118.662, -88.585, 74.302);
      DescPose p6Desc(105.553, 454.325, 232.017, -179.426, 0.444, -99.952);
      JointPos p6Joint(-115.649, -84.367, 122.447, -128.663, -90.432, 74.303);
      ExaxisPos exaxisPos(0, 0, 0, 0);
      DescPose offdese(0, 0, 100, 0, 0, 0);
      robot.MoveJ(&p1Joint, &p1Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
      robot.SetTcp4RefPoint(1);
      robot.MoveJ(&p2Joint, &p2Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
      robot.SetTcp4RefPoint(2);
      robot.MoveJ(&p3Joint, &p3Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
      robot.SetTcp4RefPoint(3);
      robot.MoveJ(&p4Joint, &p4Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
      robot.SetTcp4RefPoint(4);
      DescPose coordRtn = {};
      rtn = robot.ComputeTcp4(&coordRtn);
      printf("4 Point ComputeTool    %d coord is %f %f %f %f %f %f \n", rtn, coordRtn.tran.x, coordRtn.tran.y, coordRtn.tran.z, coordRtn.rpy.rx, coordRtn.rpy.ry, coordRtn.rpy.rz);
      robot.SetToolCoord(1, &coordRtn, 0, 0, 1, 0);
      robot.GetForwardKin(&p1Joint, &p1Desc);
      robot.GetForwardKin(&p2Joint, &p2Desc);
      robot.GetForwardKin(&p3Joint, &p3Desc);
      robot.SetFocusCalibPoint(1, p1Desc);
      robot.SetFocusCalibPoint(2, p2Desc);
      robot.SetFocusCalibPoint(3, p3Desc);
      DescTran resultPos = {};
      float accuracy = 0.0;
      rtn = robot.ComputeFocusCalib(3, resultPos, accuracy);
      printf("ComputeFocusCalib coord is %d %f %f %f accuracy is %f\n", rtn, resultPos.x, resultPos.y, resultPos.z, accuracy);
      rtn = robot.SetFocusPosition(resultPos);
      robot.GetForwardKin(&p5Joint, &p5Desc);
      robot.GetForwardKin(&p6Joint, &p6Desc);
      robot.MoveL(&p5Joint, &p5Desc, 1, 0, 10, 100, 100, -1, 0, &exaxisPos, 0, 1, &offdese);
      robot.MoveL(&p6Joint, &p6Desc, 1, 0, 10, 100, 100, -1, 0, &exaxisPos, 0, 1, &offdese);
      robot.FocusStart(50, 19, 710, 90, 0);
      robot.MoveL(&p5Joint, &p5Desc, 1, 0, 10, 100, 100, -1, 0, &exaxisPos, 0, 1, &offdese);
      robot.MoveL(&p6Joint, &p6Desc, 1, 0, 10, 100, 100, -1, 0, &exaxisPos, 0, 1, &offdese);
      robot.FocusEnd();
      robot.CloseRPC();
      return 0;
    }

Włączenie funkcji kalibracji czułości czujnika momentu obrotowego stawu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Włączenie funkcji kalibracji czułości czujnika momentu obrotowego stawu
    * @param [in] status 0-wyłączone; 1-włączone
    * @return  Kod błędu
    */
    errno_t JointSensitivityEnable(int status);

Zbieranie danych czułości czujnika momentu obrotowego stawu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Zbieranie danych czułości czujnika momentu obrotowego stawu
    * @return Kod błędu
    */
    errno_t JointSensitivityCollect();
    

Pobranie wyniku kalibracji czułości czujnika momentu obrotowego stawu
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera wynik kalibracji czułości czujnika momentu obrotowego stawu
    * @param [out] calibResult Czułość stawów j1~j6 [0-1]
    * @param [out] linearity Liniowość stawów j1~j6 [0-1]
    * @return Kod błędu
    */
    errno_t JointSensitivityCalibration(double calibResult[6], double linearity[6]);

Pobranie błędu histerezy czujnika momentu obrotowego stawu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera błąd histerezy czujnika momentu obrotowego stawu
    * @param [out] hysteresisError Błąd histerezy stawów j1~j6
    * @return Kod błędu
    */
    errno_t JointHysteresisError(double hysteresisError[6]);
    
Pobranie powtarzalności czujnika momentu obrotowego stawu
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:
    
    /**
    * @brief Pobiera powtarzalność czujnika momentu obrotowego stawu
    * @param [out] repeatability Powtarzalność czujnika momentu obrotowego stawów j1~j6
    * @return Kod błędu
    */
    errno_t JointRepeatability(double repeatability[6]);
    
Ustawienie parametrów czujnika siły stawu
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia parametry czujnika siły stawu
    * @param [in] M Współczynniki masy J1-J6 [0.001 ~ 10]
    * @param [in] B Współczynniki tłumienia J1-J6 [0.001 ~ 10]
    * @param [in] K Współczynniki sztywności J1-J6 [0.001 ~ 10]
    * @param [in] threshold Próg sterowania siłą, Nm
    * @param [in] sensitivity Czułość, Nm/V, [0 ~ 10]
    * @param [in] setZeroFlag Bit flagi włączenia funkcji; 0-wyłączone; 1-włączone; 2-rejestracja zera w pozycji 1; 3-rejestracja zera w pozycji 2
    * @return Kod błędu
    */
    errno_t SetAdmittanceParams(double M[6], double B[6], double K[6], double threshold[6], double sensitivity[6], int setZeroFlag);

Przykład kodu automatycznej kalibracji czułości czujnika momentu obrotowego stawu
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestSensitivityCalib()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        robot.SetReConnectParam(true, 30000, 500);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return 0;
        }
        rtn = robot.JointSensitivityEnable(0);
        rtn = robot.JointSensitivityEnable(1);
        printf("JointSensitivityEnable rtn is %d\n", rtn);
        JointPos curJPos = {};
        robot.GetActualJointPosDegree(0, &curJPos);
        ExaxisPos epos = { 0,0,0,0 };
        DescPose offset_pos = { 0,0,0,0,0,0 };
        JointPos jointPos1 = { curJPos.jPos[0], 0, 0, -90, 0.02, curJPos.jPos[5] };
        DescPose descPos1 = {};
        robot.GetForwardKin(&jointPos1, &descPos1);
        robot.MoveJ(&jointPos1, &descPos1, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(200);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 1 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos2 = { curJPos.jPos[0], -30, 0, -90, 0.02, curJPos.jPos[5] };
        DescPose descPos2 = {};
        robot.GetForwardKin(&jointPos2, &descPos2);
        robot.MoveJ(&jointPos2, &descPos2, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 2 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos3 = { curJPos.jPos[0], -60, 0, -90, 0.02, curJPos.jPos[5] };
        DescPose descPos3 = {};
        robot.GetForwardKin(&jointPos3, &descPos3);
        robot.MoveJ(&jointPos3, &descPos3, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 3 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos4 = { curJPos.jPos[0], -90, 0, -90, 0.02, curJPos.jPos[5] };
        DescPose descPos4 = {};
        robot.GetForwardKin(&jointPos4, &descPos4);
        robot.MoveJ(&jointPos4, &descPos4, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 4 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos5 = { curJPos.jPos[0], -120, 0, -90, 0.02, curJPos.jPos[5] };
        DescPose descPos5 = {};
        robot.GetForwardKin(&jointPos5, &descPos5);
        robot.MoveJ(&jointPos5, &descPos5, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 5 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos6 = { curJPos.jPos[0], -150, 0, -90, 0.02, curJPos.jPos[5] };
        DescPose descPos6 = {};
        robot.GetForwardKin(&jointPos6, &descPos6);
        robot.MoveJ(&jointPos6, &descPos6, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 6 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos7 = { curJPos.jPos[0], -180, 0, -90, 0.02, curJPos.jPos[5] };
        DescPose descPos7 = {};
        robot.GetForwardKin(&jointPos7, &descPos7);
        robot.MoveJ(&jointPos7, &descPos7, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 7 rtn is %d\n", rtn);
        robot.Sleep(100);
        //-------------------
        robot.MoveJ(&jointPos6, &descPos6, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 8 rtn is %d\n", rtn);
        robot.Sleep(100);
        robot.MoveJ(&jointPos5, &descPos5, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 9 rtn is %d\n", rtn);
        robot.Sleep(100);
        robot.MoveJ(&jointPos4, &descPos4, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 10 rtn is %d\n", rtn);
        robot.Sleep(100);
        robot.MoveJ(&jointPos3, &descPos3, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 11 rtn is %d\n", rtn);
        robot.Sleep(100);
        robot.MoveJ(&jointPos2, &descPos2, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 12 rtn is %d\n", rtn);
        robot.Sleep(100);
        robot.MoveJ(&jointPos1, &descPos1, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(200);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 13 rtn is %d\n", rtn);
        robot.Sleep(100);
        double calibResult[6] = { 0.0 };
        double linearity[6] = { 0.0 };
        rtn = robot.JointSensitivityCalibration(calibResult, linearity);
        printf("JointSensitivityCalibration rtn is %d\n", rtn);
        rtn = robot.JointSensitivityEnable(0);
        printf("JointSensitivityEnable rtn is %d\n", rtn);
        printf("jointSensor Calib result is %f %f %f %f %f %f\njointSensor linearity is %f %f %f %f %f %f\n", 
            calibResult[0], calibResult[1], calibResult[2], 
            calibResult[3], calibResult[4], calibResult[5], 
            linearity[0], linearity[1], linearity[2],
            linearity[3], linearity[4], linearity[5]);
        double hysteresisError[6] = { 0.0 };
        rtn = robot.JointHysteresisError(hysteresisError);
        printf("JointHysteresisError result is %f %f %f %f %f %f\n",
            hysteresisError[0], hysteresisError[1], hysteresisError[2],
            hysteresisError[3], hysteresisError[4], hysteresisError[5]);
        double repeatability[6] = { 0.0 };
        rtn = robot.JointRepeatability(repeatability);
        printf("JointRepeatability result is %f %f %f %f %f %f\n",
            repeatability[0], repeatability[1], repeatability[2],
            repeatability[3], repeatability[4], repeatability[5]);
        double M[6] = { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
        double B[6] = { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
        double K[6] = { 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 };
        double threshold[6] = { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
        int setZeroFlag = 1;
        rtn = robot.SetAdmittanceParams(M, B, K, threshold, calibResult, setZeroFlag);
        printf("SetAdmittanceParams rtn is %d\n", rtn);
        robot.CloseRPC();
    }
    
Pobranie liczby błędnych ramek dla 8 portów stacji podrzędnych robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera liczbę błędnych ramek dla 8 portów stacji podrzędnych robota
    * @param [out] inRecvErr Liczba błędnych ramek odebranych na wejściu 
    * @param [out] inCRCErr Liczba błędnych ramek CRC na wejściu 
    * @param [out] inTransmitErr Liczba błędnych ramek przesłanych na wejściu 
    * @param [out] inLinkErr Liczba błędnych ramek łącza na wejściu 
    * @param [out] outRecvErr Liczba błędnych ramek odebranych na wyjściu
    * @param [out] outCRCErr Liczba błędnych ramek CRC na wyjściu
    * @param [out] outTransmitErr Liczba błędnych ramek przesłanych na wyjściu
    * @param [out] outLinkErr Liczba błędnych ramek łącza na wyjściu
    * @return Kod błędu
    */
    errno_t GetSlavePortErrCounter(int inRecvErr[8], int inCRCErr[8], int inTransmitErr[8], int inLinkErr[8], int outRecvErr[8], int outCRCErr[8], int outTransmitErr[8], int outLinkErr[8]);

Zerowanie licznika błędnych ramek portu stacji podrzędnej
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Zeruje licznik błędnych ramek portu stacji podrzędnej
    * @param [in] slaveID Numer stacji podrzędnej 0~7
    * @return Kod błędu
    */
    errno_t SlavePortErrCounterClear(int slaveID);
    
Przykład kodu pobierania błędnych ramek portów stacji podrzędnych
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestSlavePortErr()
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
        int inRecvErr[8] = {0.0}; 
        int inCRCErr[8] = { 0.0 };
        int inTransmitErr[8] = { 0.0 };
        int inLinkErr[8] = { 0.0 };
        int outRecvErr[8] = { 0.0 };
        int outCRCErr[8] = { 0.0 };
        int outTransmitErr[8] = { 0.0 };
        int outLinkErr[8] = { 0.0 };
        robot.GetSlavePortErrCounter(inRecvErr,  inCRCErr, inTransmitErr, inLinkErr,
            outRecvErr, outCRCErr, outTransmitErr, outLinkErr);
        for (int i = 0; i < 8; i++)
        {
            if (inRecvErr[i] != 0)
            {
                printf("inRecvErr %d is %d\n", i, inRecvErr[i]);
            }
            if (inCRCErr[i] != 0)
            {
                printf("inRecvErr %d is %d\n", i, inCRCErr[i]);
            }
            if (inTransmitErr[i] != 0)
            {
                printf("inRecvErr %d is %d\n", i, inTransmitErr[i]);
            }
            if (inLinkErr[i] != 0)
            {
                printf("inRecvErr %d is %d\n", i, inLinkErr[i]);
            }
            if (outRecvErr[i] != 0)
            {
                printf("outRecvErr %d is %d\n", i, outRecvErr[i]);
            }
            if (outCRCErr[i] != 0)
            {
                printf("outCRCErr %d is %d\n", i, outCRCErr[i]);
            }
            if (outTransmitErr[i] != 0)
            {
                printf("outTransmitErr %d is %d\n", i, outTransmitErr[i]);
            }
            if (outLinkErr[i] != 0)
            {
                printf("outLinkErr %d is %d\n", i, outLinkErr[i]);
            }
        }
        printf("others has no err!\n");
        for (int i = 0; i < 8; i++)
        {
            robot.SlavePortErrCounterClear(i);
        }
        robot.CloseRPC();
        return 0;
    }

Ustawienie współczynnika sprzężenia przedniego prędkości dla każdej osi
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Ustawia współczynnik sprzężenia przedniego prędkości dla każdej osi
    * @param [in] radio Współczynnik sprzężenia przedniego prędkości dla każdej osi
    * @return Kod błędu
    */
    errno_t SetVelFeedForwardRatio(double radio[6]);

Pobranie współczynnika sprzężenia przedniego prędkości dla każdej osi
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera współczynnik sprzężenia przedniego prędkości dla każdej osi
    * @param [out] radio Współczynnik sprzężenia przedniego prędkości dla każdej osi
    * @return Kod błędu
    */
    errno_t GetVelFeedForwardRatio(double radio[6]);

Przykład kodu współczynnika sprzężenia przedniego prędkości robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestVelFeedForwardRatio()
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
        double setRadio[6] = { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
        robot.SetVelFeedForwardRatio(setRadio);
        double getRadio[6] = { 0.0 };
        robot.GetVelFeedForwardRatio(getRadio);
        printf(" %f %f %f %f %f %f\n", getRadio[0], getRadio[1], getRadio[2], getRadio[3], getRadio[4], getRadio[5]);
        robot.CloseRPC();
        return 0;
    }

Kalibracja TCP czujnika fotoelektrycznego - obliczenie RPY narzędzia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Kalibracja TCP czujnika fotoelektrycznego - obliczenie RPY narzędzia
    * @param [in] Btool Pozycja kartezjańska robota
    * @param [in] Etool Bieżące wartości układu współrzędnych narzędzia
    * @param [in] senser Bieżące wartości układu współrzędnych czujnika (jeszcze nieudostępnione)
    * @param [in] radius Promień ruchu po okręgu mm (jeszcze nieudostępnione)
    * @param [in] dz Odległość ruchu wzdłuż ujemnego kierunku osi Z podstawowego układu współrzędnych; gdy dz = 10000, funkcja bezpośrednio zwraca RPY narzędzia
    * @param [out] TCPRPY Wartości RPY narzędzia
    * @return Kod błędu
    */
    errno_t TCPComputeRPY(DescPose Btool, DescPose Etool, DescPose sensor, double radius, double dz, Rpy& TCPRPY);

Kalibracja TCP czujnika fotoelektrycznego - obliczenie XYZ narzędzia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Kalibracja TCP czujnika fotoelektrycznego - obliczenie XYZ narzędzia
    * @param [in] select 0-oblicz TCP narzędzia; 1-oblicz początek czujnika; 2-oblicz orientację czujnika; 3-bezpośrednio zwróć TCP narzędzia; 4-zapisz bieżący układ współrzędnych przedmiotu i narzędzia
    * @param [in] originDirection 0-kierunek X; 1-kierunek Y; 2-kierunek Z
    * @param [in] pos1 Pozycja kartezjańska robota 1
    * @param [in] pos2 Pozycja kartezjańska robota 2
    * @param [in] pos3 Pozycja kartezjańska robota 3
    * @param [in] pos4 Pozycja kartezjańska robota 4
    * @param [out] TCP Wartości XYZ narzędzia
    * @return Kod błędu
    */
    errno_t TCPComputeXYZ(int select, double originDirection, DescTran pos1, DescTran pos2, DescTran pos3, DescTran pos4, DescTran& TCP);

Kalibracja TCP czujnika fotoelektrycznego - rozpoczęcie rejestracji pozycji środka kołnierza końcowego
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Kalibracja TCP czujnika fotoelektrycznego - rozpoczęcie rejestracji pozycji środka kołnierza końcowego
    * @return Kod błędu
    */
    errno_t TCPRecordFlangePosStart();

Kalibracja TCP czujnika fotoelektrycznego - zatrzymanie rejestracji pozycji środka kołnierza końcowego
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Kalibracja TCP czujnika fotoelektrycznego - zatrzymanie rejestracji pozycji środka kołnierza końcowego
    * @return Kod błędu
    */
    errno_t TCPRecordFlangePosEnd();

Kalibracja TCP czujnika fotoelektrycznego - pobranie pozycji środka narzędzia końcowego
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Kalibracja TCP czujnika fotoelektrycznego - pobranie pozycji środka narzędzia końcowego
    * @param [out] TCP Pozycja środka narzędzia (x,y,z)
    * @return Kod błędu
    */
    errno_t TCPGetRecordFlangePos(DescTran& TCP);

Kalibracja TCP czujnika fotoelektrycznego
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Kalibracja TCP czujnika fotoelektrycznego
    * @param [in] luaPath Ścieżka programu lua automatycznej kalibracji: "FR_CalibrateTheToolTcp.lua"
    * @param [in] offset Przesunięcie punktu nauczania (x,y,z) mm
    * @param [out] TCP Układ współrzędnych narzędzia po kalibracji (x,y,z,rx,ry,rz)
    * @return Kod błędu
    */
    errno_t PhotoelectricSensorTCPCalibration(std::string luaPath, DescTran offset, DescPose& TCP);

Przykład kodu kalibracji TCP czujnika fotoelektrycznego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestPhotoelectricSensorTCPCalib(void)
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
        DescTran offset = { 10.0, 10.0, 3.0 };
        DescPose TCP = {};
        rtn = robot.PhotoelectricSensorTCPCalibration("FR_CalibrateTheToolTcp.lua", offset, TCP);
        printf("PhotoelectricSensorTCPCalibration rtn is  %d %f %f %f %f %f %f \n", rtn, TCP.tran.x, TCP.tran.y, TCP.tran.z, TCP.rpy.rx, TCP.rpy.ry, TCP.rpy.rz);
        robot.CloseRPC();
        robot.Sleep(9999999);
        return 0;
    }
    
Ustawianie Prędkości Globalnej w Czasie Rzeczywistym
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia prędkość globalną w czasie rzeczywistym
    * @param [in] vel Procent prędkości, zakres [0~100]
    * @return Kod błędu
    */
    errno_t SetSpeedInstant(int vel);