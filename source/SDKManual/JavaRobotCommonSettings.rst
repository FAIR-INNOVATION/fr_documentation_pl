Ustawienia ogólne robota
========================

.. toctree::
    :maxdepth: 5

Ustawianie punktu odniesienia narzędzia - metoda sześciu punktów
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia punkt odniesienia narzędzia - metoda sześciu punktów
    * @param [in] point_num Numer punktu, zakres [1~6]
    * @return Kod błędu
    */
    int SetToolPoint(int point_num);

Obliczanie układu współrzędnych narzędzia -- metoda sześciu punktów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Oblicza układ współrzędnych narzędzia
    * @param [out] tcp_pose Układ współrzędnych narzędzia
    * @return Kod błędu
    */
    int ComputeTool(DescPose tcp_pose);

Ustawianie punktu odniesienia narzędzia - metoda czterech punktów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia punkt odniesienia narzędzia - metoda czterech punktów
    * @param [in] point_num Numer punktu, zakres [1~4]
    * @return Kod błędu
    */
    int SetTcp4RefPoint(int point_num);

Obliczanie układu współrzędnych narzędzia - metoda czterech punktów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Oblicza układ współrzędnych narzędzia
    * @param [out] tcp_pose Układ współrzędnych narzędzia
    * @return Kod błędu
    */
    int ComputeTcp4(DescPose tcp_pose);

Obliczanie układu współrzędnych narzędzia na podstawie informacji o punktach
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Oblicza układ współrzędnych narzędzia na podstawie informacji o punktach
    * @param [in] method Metoda obliczeniowa; 0-metoda czterech punktów; 1-metoda sześciu punktów
    * @param [in] pos Grupa pozycji stawów, długość tablicy 4 dla metody czterech punktów, 6 dla metody sześciu punktów
    * @param [out] tool_pose Wyjściowy układ współrzędnych narzędzia
    * @return Kod błędu
    */
    int ComputeToolCoordWithPoints(int method, JointPos[] pos,DescPose tool_pose);

Ustawianie układu współrzędnych narzędzia
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia układ współrzędnych narzędzia
    * @param [in] id Numer układu współrzędnych, zakres [0~14]
    * @param [in] coord Pozycja i orientacja środka narzędzia względem środka kołnierza końcowego
    * @param [in] type 0-układ współrzędnych narzędzia, 1-układ współrzędnych czujnika
    * @param [in] install Pozycja montażu, 0-koniec robota, 1-na zewnątrz robota
    * @param [in] toolID ID narzędzia
    * @param [in] loadNum Numer obciążenia
    * @return Kod błędu
    */
    int SetToolCoord(int id, DescPose coord, int type, int install, int toolID, int loadNum);

Ustawianie listy układów współrzędnych narzędzia
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia listę układów współrzędnych narzędzia
    * @param [in] id Numer układu współrzędnych, zakres [0~14]
    * @param [in] coord Pozycja i orientacja środka narzędzia względem środka kołnierza końcowego
    * @param [in] type 0-układ współrzędnych narzędzia, 1-układ współrzędnych czujnika
    * @param [in] install Pozycja montażu, 0-koniec robota, 1-na zewnątrz robota
    * @param [in] loadNum Numer obciążenia
    * @return Kod błędu
    */
    int SetToolList(int id, DescPose coord, int type, int install, int loadNum);

Pobieranie bieżącego układu współrzędnych narzędzia
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera bieżący układ współrzędnych narzędzia
    * @param [in] flag 0-blokujący, 1-nieblokujący
    * @param [out] desc_pos Pozycja i orientacja układu współrzędnych narzędzia
    * @return Kod błędu
    */
    int GetTCPOffset(int flag, DescPose desc_pos);

Przykład kodu operacji na układzie współrzędnych narzędzia robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestTCPCompute(Robot robot)
    {
        DescPose p1Desc=new DescPose(186.331, 487.913, 209.850, 149.030, 0.688, -114.347);
        JointPos p1Joint=new JointPos(-127.876, -75.341, 115.417, -122.741, -59.820, 74.300);

        DescPose p2Desc=new DescPose(69.721, 535.073, 202.882, -144.406, -14.775, -89.012);
        JointPos p2Joint=new JointPos(-101.780, -69.828, 110.917, -125.740, -127.841, 74.300);

        DescPose p3Desc=new DescPose(146.861, 578.426, 205.598, 175.997, -36.178, -93.437);
        JointPos p3Joint=new JointPos(-112.851, -60.191, 86.566, -80.676, -97.463, 74.300);

        DescPose p4Desc=new DescPose(136.284, 509.876, 225.613, 178.987, 1.372, -100.696);
        JointPos p4Joint=new JointPos(-116.397, -76.281, 113.845, -128.611, -88.654, 74.299);

        DescPose p5Desc=new DescPose(138.395, 505.972, 298.016, 179.134, 2.147, -101.110);
        JointPos p5Joint=new JointPos(-116.814, -82.333, 109.162, -118.662, -88.585, 74.302);

        DescPose p6Desc=new DescPose(105.553, 454.325, 232.017, -179.426, 0.444, -99.952);
        JointPos p6Joint=new JointPos(-115.649, -84.367, 122.447, -128.663, -90.432, 74.303);

        ExaxisPos exaxisPos=new ExaxisPos(0, 0, 0, 0);
        DescPose offdese=new DescPose(0, 0, 0, 0, 0, 0);

        JointPos[] posJ = { p1Joint , p2Joint , p3Joint , p4Joint , p5Joint , p6Joint };
        DescPose coordRtn =new DescPose() {};
        int rtn = robot.ComputeToolCoordWithPoints(1, posJ, coordRtn);

        robot.MoveJ(p1Joint, p1Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetToolPoint(1);
        robot.MoveJ(p2Joint, p2Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetToolPoint(2);
        robot.MoveJ(p3Joint, p3Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetToolPoint(3);
        robot.MoveJ(p4Joint, p4Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetToolPoint(4);
        robot.MoveJ(p5Joint, p5Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetToolPoint(5);
        robot.MoveJ(p6Joint, p6Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetToolPoint(6);
        rtn = robot.ComputeTool(coordRtn);
        robot.SetToolList(3, coordRtn, 0, 0, 0);

        robot.MoveJ(p1Joint, p1Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(1);
        robot.MoveJ(p2Joint, p2Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(2);
        robot.MoveJ(p3Joint, p3Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(3);
        robot.MoveJ(p4Joint, p4Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(4);
        rtn = robot.ComputeTcp4(coordRtn);

        robot.SetToolCoord(4, coordRtn, 0, 0, 1, 0);

        DescPose getCoord = new DescPose(){};
        rtn = robot.GetTCPOffset(0, getCoord);
        return 0;
    }

Ustawianie punktu odniesienia zewnętrznego narzędzia - metoda trzech punktów
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia punkt odniesienia zewnętrznego narzędzia - metoda trzech punktów
    * @param [in] point_num Numer punktu, zakres [1~3]
    * @return Kod błędu
    */
    int SetExTCPPoint(int point_num);

Obliczanie zewnętrznego układu współrzędnych narzędzia - metoda trzech punktów
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Oblicza zewnętrzny układ współrzędnych narzędzia - metoda trzech punktów
    * @param [out] tcp_pose Zewnętrzny układ współrzędnych narzędzia
    * @return Kod błędu
    */
    int ComputeExTCF(DescPose tcp_pose);

Ustawianie zewnętrznego układu współrzędnych narzędzia
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia zewnętrzny układ współrzędnych narzędzia
    * @param [in] id Numer układu współrzędnych, zakres [0~14]
    * @param [in] etcp Pozycja i orientacja środka narzędzia względem środka kołnierza końcowego
    * @param [in] etool Do ustalenia
    * @return Kod błędu
    */
    int SetExToolCoord(int id, DescPose etcp, DescPose etool);

Ustawianie listy zewnętrznych układów współrzędnych narzędzia
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia listę zewnętrznych układów współrzędnych narzędzia
    * @param [in] id Numer układu współrzędnych, zakres [0~14]
    * @param [in] etcp Pozycja i orientacja środka narzędzia względem środka kołnierza końcowego
    * @param [in] etool Do ustalenia
    * @return Kod błędu
    */
    int SetExToolList(int id, DescPose etcp, DescPose etool);

Przykład kodu operacji na zewnętrznym układzie współrzędnych narzędzia robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestExtCoord(Robot robot)
    {
        DescPose p1Desc=new DescPose(-89.606, 779.517, 193.516, 178.000, 0.476, -92.484);
        JointPos p1Joint=new JointPos(-108.145, -50.137, 85.818, -125.599, -87.946, 74.329);

        DescPose p2Desc=new DescPose(-24.656, 850.384, 191.361, 177.079, -2.058, -95.355);
        JointPos p2Joint=new JointPos(-111.024, -41.538, 69.222, -114.913, -87.743, 74.329);

        DescPose p3Desc=new DescPose(-99.813, 766.661, 241.878, -176.817, 1.917, -91.604);
        JointPos p3Joint=new JointPos(-107.266, -56.116, 85.971, -122.560, -92.548, 74.331);

        robot.GetForwardKin(p1Joint,p1Desc);
        robot.GetForwardKin(p2Joint,p2Desc);
        robot.GetForwardKin(p3Joint,p3Desc);

        ExaxisPos exaxisPos=new ExaxisPos(0, 0, 0, 0);
        DescPose offdese=new DescPose(0, 0, 0, 0, 0, 0);

        DescPose[] posTCP = { p1Desc , p2Desc , p3Desc };
        DescPose coordRtn = new DescPose();

        robot.MoveJ(p1Joint, p1Desc, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetExTCPPoint(1);
        robot.MoveJ(p2Joint, p2Desc, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetExTCPPoint(2);
        robot.MoveJ(p3Joint, p3Desc, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetExTCPPoint(3);
        int rtn = robot.ComputeExTCF(coordRtn);

        robot.SetExToolCoord(1, coordRtn, offdese);
        robot.SetExToolList(1, coordRtn, offdese);
        return 0;
    }

Ustawianie punktu odniesienia układu współrzędnych obiektu - metoda trzech punktów
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia punkt odniesienia obiektu - metoda trzech punktów
    * @param [in] point_num Numer punktu, zakres [1~3]
    * @return Kod błędu
    */
    int SetWObjCoordPoint(int point_num);

Obliczanie układu współrzędnych obiektu
+++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Oblicza układ współrzędnych obiektu
    * @param [in] method Sposób obliczania 0: punkt początkowy - oś X - oś Z  1: punkt początkowy - oś X - płaszczyzna XY
    * @param [in] refFrame Układ odniesienia
    * @param [out] wobj_pose Układ współrzędnych obiektu
    * @return Kod błędu
    */
    int ComputeWObjCoord(int method, int refFrame, DescPose wobj_pose);

Ustawianie układu współrzędnych obiektu
+++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia układ współrzędnych obiektu
    * @param [in] id Numer układu współrzędnych, zakres [1~15]
    * @param [in] coord Pozycja i orientacja układu współrzędnych obiektu względem środka kołnierza końcowego
    * @param [in] refFrame Układ odniesienia
    * @return Kod błędu
    */
    int SetWObjCoord(int id, DescPose coord, int refFrame);

Ustawianie listy układów współrzędnych obiektu
++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia listę układów współrzędnych obiektu
    * @param [in] id Numer układu współrzędnych, zakres [1~15]
    * @param [in] coord Pozycja i orientacja układu współrzędnych obiektu względem środka kołnierza końcowego
    * @param [in] refFrame Układ odniesienia
    * @return Kod błędu
    */
    int SetWObjList(int id, DescPose coord, int refFrame);

Obliczanie układu współrzędnych obiektu na podstawie informacji o punktach
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Oblicza układ współrzędnych obiektu na podstawie informacji o punktach
    * @param [in] method Metoda obliczeniowa; 0: punkt początkowy - oś X - oś Z  1: punkt początkowy - oś X - płaszczyzna XY
    * @param [in] pos Trzy grupy pozycji TCP
    * @param [in] refFrame Układ odniesienia
    * @param [in] tcp_pose Wyjściowy układ współrzędnych obiektu
    * @return Kod błędu
    */
    int ComputeWObjCoordWithPoints(int method, DescPose[] pos, int refFrame,DescPose tcp_pose);

Pobieranie bieżącego układu współrzędnych obiektu
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera bieżący układ współrzędnych obiektu
    * @param [in] flag 0-blokujący, 1-nieblokujący
    * @param [out] desc_pos Pozycja i orientacja układu współrzędnych obiektu
    * @return Kod błędu
    */
    int GetWObjOffset(int flag, DescPose desc_pos);

Przykład kodu operacji na układzie współrzędnych obiektu robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestWobjCoord(Robot robot)
    {
        DescPose p1Desc=new DescPose(-89.606, 779.517, 193.516, 178.000, 0.476, -92.484);
        JointPos p1Joint=new JointPos(-108.145, -50.137, 85.818, -125.599, -87.946, 74.329);

        DescPose p2Desc=new DescPose(-24.656, 850.384, 191.361, 177.079, -2.058, -95.355);
        JointPos p2Joint=new JointPos(-111.024, -41.538, 69.222, -114.913, -87.743, 74.329);

        DescPose p3Desc=new DescPose(-99.813, 766.661, 241.878, -176.817, 1.917, -91.604);
        JointPos p3Joint=new JointPos(-107.266, -56.116, 85.971, -122.560, -92.548, 74.331);

        robot.GetForwardKin(p1Joint,p1Desc);
        robot.GetForwardKin(p2Joint,p2Desc);
        robot.GetForwardKin(p3Joint,p3Desc);

        ExaxisPos exaxisPos=new ExaxisPos(0, 0, 0, 0);
        DescPose offdese=new DescPose(0, 0, 0, 0, 0, 0);

        DescPose[] posTCP =new DescPose[]{p1Desc , p2Desc , p3Desc };
        DescPose coordRtn =new DescPose();
        int rtn = robot.ComputeWObjCoordWithPoints(1, posTCP, 0, coordRtn);

        robot.MoveJ(p1Joint, p1Desc, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetWObjCoordPoint(1);
        robot.MoveJ(p2Joint, p2Desc, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetWObjCoordPoint(2);
        robot.MoveJ(p3Joint, p3Desc, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetWObjCoordPoint(3);
        rtn = robot.ComputeWObjCoord(1, 0, coordRtn);

        robot.SetWObjCoord(1, coordRtn, 0);
        robot.SetWObjList(1, coordRtn, 0);

        DescPose getWobjDesc = new DescPose();
        rtn = robot.GetWObjOffset(0, getWobjDesc);
        return 0;
    }

Ustawianie prędkości globalnej
++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia prędkość globalną
    * @param [in] vel Procent prędkości, zakres [0~100]
    * @return Kod błędu
    */
    int SetSpeed(int vel);

Ustawianie przyspieszenia robota
++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia przyspieszenie robota
    * @param [in] acc Procent przyspieszenia robota
    * @return Kod błędu
    */
    int SetOaccScale(double acc);

Pobieranie domyślnej prędkości robota
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera domyślną prędkość robota
    * @return List[0]:int kod błędu; List[1]: double vel prędkość, jednostka mm/s
    */
    List<Number> GetDefaultTransVel();

Ustawianie masy obciążenia końcówki
+++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia masę obciążenia końcówki
    * @param [in] loadNum Numer obciążenia
    * @param [in] weight Masa obciążenia, jednostka kg
    * @return Kod błędu
    */
    int SetLoadWeight(int loadNum,double weight);

Ustawianie współrzędnych środka ciężkości obciążenia końcówki
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia współrzędne środka ciężkości obciążenia końcówki
    * @param [in] coord Współrzędne środka ciężkości, jednostka mm
    * @return Kod błędu
    */
    int SetLoadCoord(DescTran coord);

Ustawianie współrzędnych środka ciężkości obciążenia końcówki
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
     * @brief Ustawia współrzędne środka ciężkości obciążenia końcówki
     * @param [in] loadNum Numer obciążenia
     * @param [in] coord Współrzędne środka ciężkości, jednostka mm
     * @return Kod błędu
     */
    public int SetLoadCoord(int loadNum, DescTran coord)

Pobieranie masy bieżącego obciążenia
++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera masę bieżącego obciążenia
    * @param [in] flag 0-blokujący, 1-nieblokujący
    * @return List[0]:int kod błędu; List[1]: double weight masa obciążenia, jednostka kg
    */
    List<Number> GetTargetPayload(int flag);

Pobieranie środka ciężkości bieżącego obciążenia
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera środek ciężkości bieżącego obciążenia
    * @param [in] flag 0-blokujący, 1-nieblokujący
    * @param [out] cog Środek ciężkości obciążenia, jednostka mm
    * @return Kod błędu
    */
    int GetTargetPayloadCog(int flag, DescTran cog);

Ustawianie sposobu montażu robota
+++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia sposób montażu robota
    * @param [in] install Sposób montażu, 0-normalny, 1-boczny, 2-odwrócony
    * @return Kod błędu
    */
    int SetRobotInstallPos(int install);

Ustawianie kąta montażu robota
++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia kąt montażu robota, montaż swobodny
    * @param [in] yangle Kąt nachylenia
    * @param [in] zangle Kąt obrotu
    * @return Kod błędu
    */
    int SetRobotInstallAngle(double yangle, double zangle);

Pobieranie kąta montażu robota
++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera kąt montażu robota
    * @return List[0]:kod błędu; List[1]:double yangle kąt nachylenia; List[2]:double zangle kąt obrotu
    */
    public List<Number> GetRobotInstallAngle()

Ustawianie wartości zmiennej systemowej
+++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia wartość zmiennej systemowej
    * @param [in] id Numer zmiennej, zakres [1~20]
    * @param [in] value Wartość zmiennej
    * @return Kod błędu
    */
    int SetSysVarValue(int id, double value);

Pobieranie wartości zmiennej systemowej
+++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera wartość zmiennej systemowej
    * @param [in] id Numer zmiennej systemowej, zakres [1~20]
    * @return List[0]:kod błędu; List[1]:double value wartość zmiennej systemowej
    */
    List<Number> GetSysVarValue(int id);

Przykład kodu ustawień ogólnych robota
++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestLoadInstall(Robot robot)
    {
        for (int i = 1; i < 100; i++)
        {
            robot.SetSpeed(i);
            robot.SetOaccScale(i);
            robot.Sleep(30);
        }

        List<Number> defaultVel=new ArrayList<>();

        defaultVel=robot.GetDefaultTransVel();
        System.out.println("GetDefaultTransVel is:"+ defaultVel.get(1));

        for (int i = 1; i < 21; i++)
        {
            robot.SetSysVarValue(i, i + 0.5);
            robot.Sleep(100);
        }

        for (int i = 1; i < 21; i++)
        {
            float value = 0;
            defaultVel=robot.GetSysVarValue(i);
            System.out.println("sys value :"+i+", is :"+defaultVel.get(1));
            robot.Sleep(100);
        }

        robot.SetLoadWeight(0, 2.5);

        DescTran loadCoord = new DescTran();
        loadCoord.x = 3.0;
        loadCoord.y = 4.0;
        loadCoord.z = 5.0;
        robot.SetLoadCoord(loadCoord);

        robot.Sleep(1000);

        List<Number> getLoad = new ArrayList<>();

        getLoad=robot.GetTargetPayload(0);

        DescTran getLoadTran =new DescTran();
        robot.GetTargetPayloadCog(0, getLoadTran);
        System.out.println("get load is:"+getLoad.get(1)+", get load cog is: "+getLoadTran.x+","+getLoadTran.y+","+getLoadTran.z);

        robot.SetRobotInstallPos(0);
        robot.SetRobotInstallAngle(15.0, 25.0);

        List<Number> angle=new ArrayList<>();
        angle=robot.GetRobotInstallAngle();
        System.out.println("GetRobotInstallAngle x:"+angle.get(1)+";  y:"+angle.get(2));

        robot.CloseRPC();
        return 0;
    }

Przełącznik kompensacji tarcia stawów
+++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Przełącznik kompensacji tarcia stawów
    * @param [in] state 0-wył., 1-wł.
    * @return Kod błędu
    */
    int FrictionCompensationOnOff(int state);

Ustawianie współczynników kompensacji tarcia stawów - montaż normalny
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia współczynniki kompensacji tarcia stawów - montaż normalny
    * @param [in] coeff Współczynniki kompensacji dla sześciu stawów, zakres [0~1]
    * @return Kod błędu
    */
    int SetFrictionValue_level(Object[] coeff);

Ustawianie współczynników kompensacji tarcia stawów - montaż boczny
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia współczynniki kompensacji tarcia stawów - montaż boczny
    * @param [in] coeff Współczynniki kompensacji dla sześciu stawów, zakres [0~1]
    * @return Kod błędu
    */
    int SetFrictionValue_wall(Object[] coeff);

Ustawianie współczynników kompensacji tarcia stawów - montaż odwrócony
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia współczynniki kompensacji tarcia stawów - montaż odwrócony
    * @param [in] coeff Współczynniki kompensacji dla sześciu stawów, zakres [0~1]
    * @return Kod błędu
    */
    int SetFrictionValue_ceiling(Object[] coeff);

Ustawianie współczynników kompensacji tarcia stawów - montaż swobodny
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia współczynniki kompensacji tarcia stawów - montaż swobodny
    * @param [in] coeff Współczynniki kompensacji dla sześciu stawów, zakres [0~1]
    * @return Kod błędu
    */
    int SetFrictionValue_freedom(Object[] coeff);

Przykład kodu ustawiania kompensacji tarcia stawów robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestFriction(Robot robot)
    {

        Object[] lcoeff = { 0.9,0.9,0.9,0.9,0.9,0.9 };
        Object[] wcoeff = { 0.4,0.4,0.4,0.4,0.4,0.4 };
        Object[] ccoeff = { 0.6,0.6,0.6,0.6,0.6,0.6 };
        Object[] fcoeff = { 0.5,0.5,0.5,0.5,0.5,0.5 };

        int rtn = robot.FrictionCompensationOnOff(1);
        System.out.println("FrictionCompensationOnOff rtn is:"+ rtn);

        rtn = robot.SetFrictionValue_level(lcoeff);
        System.out.println("SetFrictionValue_level rtn is:"+ rtn);

        rtn = robot.SetFrictionValue_wall(wcoeff);
        System.out.println("SetFrictionValue_wall rtn is:"+ rtn);

        rtn = robot.SetFrictionValue_ceiling(ccoeff);
        System.out.println("SetFrictionValue_ceiling rtn is:"+ rtn);

        rtn = robot.SetFrictionValue_freedom(fcoeff);
        System.out.println("SetFrictionValue_freedom rtn is:"+ rtn);

        robot.CloseRPC();
        return 0;
    }

Sprawdzanie kodu błędu robota
+++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
     * @brief Sprawdza kod błędu robota
     * @param [out] maincode Główny kod błędu
     * @param [out] subcode Podrzędny kod błędu
     * @return Kod błędu
     */
    int GetRobotErrorCode(int[] maincode, int[] subcode);

Czyszczenie stanu błędu
+++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Czyszczenie stanu błędu
    * @return Kod błędu
    */
    int ResetAllError();

Przykład kodu pobierania stanu usterki robota i czyszczenia błędu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestGetError(Robot robot)
    {
        int[] maincode={0}, subcode={0};
        robot.GetRobotErrorCode(maincode, subcode);

        robot.ResetAllError();

        robot.Sleep(1000);

        robot.GetRobotErrorCode(maincode, subcode);
        return 0;
    }

Ustawianie parametrów monitorowania temperatury i prędkości wentylatora szerokonapięciowej szafy sterowniczej
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.6-3.8.3

.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia parametry monitorowania temperatury i prędkości wentylatora szerokonapięciowej szafy sterowniczej
    * @param [in] enable 0-nie włączaj monitorowania; 1-włącz monitorowanie
    * @param [in] period Okres monitorowania (s), zakres 1-100
    * @return Kod błędu
    */
    int SetWideBoxTempFanMonitorParam(int enable, int period);

Pobieranie parametrów monitorowania temperatury i prędkości wentylatora szerokonapięciowej szafy sterowniczej
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.6-3.8.3

.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera parametry monitorowania temperatury i prędkości wentylatora szerokonapięciowej szafy sterowniczej
    * @return List[0]-kod błędu, List[1]-enable 0-nie włączaj monitorowania; 1-włącz monitorowanie, List[2]-period Okres monitorowania (s), zakres 1-100
    */
    List<Number> GetWideBoxTempFanMonitorParam()

Przykład kodu pobierania temperatury szerokonapięciowej szafy sterowniczej i stanu prądu wentylatora
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestWideVoltageCtrlBoxtemp(Robot robot)
    {
        robot.SetWideBoxTempFanMonitorParam(1, 2);
        List<Number> list=robot.GetWideBoxTempFanMonitorParam();
        System.out.println("GetWideBoxTempFanMonitorParam enable is:"+list.get(1)+", period is:"+list.get(2));
        ROBOT_STATE_PKG pkg=new ROBOT_STATE_PKG();
        for (int i = 0; i < 100; i++)
        {
            pkg=robot.GetRobotRealTimeState();
            System.out.println("robot ctrl box temp is:"+pkg.wideVoltageCtrlBoxTemp+",fan current is:"+pkg.wideVoltageCtrlBoxFanCurrent);
            robot.Sleep(100);
        }

        int rtn = robot.SetWideBoxTempFanMonitorParam(0, 2);

        list=robot.GetWideBoxTempFanMonitorParam();
        for (int i = 0; i < 100; i++)
        {
            pkg=robot.GetRobotRealTimeState();
            System.out.println("robot ctrl box temp is:"+pkg.wideVoltageCtrlBoxTemp+" ,fan current is:"+pkg.wideVoltageCtrlBoxFanCurrent);
            robot.Sleep(100);
        }

        robot.CloseRPC();
        robot.Sleep(2000);
        return 0;
    }

Ustawianie punktu kalibracji ogniskowej
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia punkt kalibracji ogniskowej
    * @param [in] pointNum Numer punktu kalibracji ogniskowej 1-8
    * @param [in] point Współrzędne punktu kalibracji
    * @return Kod błędu
    */
    int SetFocusCalibPoint(int pointNum, DescPose point)

Obliczanie wyniku kalibracji ogniskowej
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:

    /**
    * @brief Oblicza wynik kalibracji ogniskowej
    * @param [in] pointNum Liczba punktów kalibracji
    * @param [in] resultPos Wynik kalibracji XYZ
    * @param [out] accuracy Błąd dokładności kalibracji
    * @return Kod błędu
    */
    int ComputeFocusCalib(int pointNum, DescTran resultPos, double[] accuracy)

Rozpoczęcie śledzenia ogniskowej
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:

    /**
    * @brief Rozpoczęcie śledzenia ogniskowej
    * @param [in] kp Parametr proporcjonalny, domyślnie 50.0
    * @param [in] kpredict Parametr sprzężenia przedniego, domyślnie 19.0
    * @param [in] aMax Maksymalne ograniczenie przyspieszenia kątowego, domyślnie 1440°/s^2
    * @param [in] vMax Maksymalne ograniczenie prędkości kątowej, domyślnie 180°/s
    * @param [in] type Zablokowanie kierunku osi X (0-wektor odniesienia wejściowego; 1-poziomy; 2-pionowy)
    * @return Kod błędu
    */
    int FocusStart(double kp, double kpredict, double aMax, double vMax, int type)

Zatrzymanie śledzenia ogniskowej
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:

    /**
    * @brief Zatrzymanie śledzenia ogniskowej
    * @return Kod błędu
    */
    int FocusEnd()

Ustawianie współrzędnych ogniskowej
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia współrzędne ogniskowej
    * @param pos Współrzędne ogniskowej XYZ
    * @return Kod błędu
    */
    public int SetFocusPosition(DescTran pos)

Przykład kodu śledzenia ogniskowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestFocus(Robot robot){
        DescPose p1Desc=new DescPose(186.331, 487.913, 209.850, 149.030, 0.688, -114.347);
        JointPos p1Joint = new JointPos(-127.876, -75.341, 115.417, -122.741, -59.820, 74.300);

        DescPose p2Desc = new DescPose(69.721, 535.073, 202.882, -144.406, -14.775, -89.012);
        JointPos p2Joint = new JointPos(-101.780, -69.828, 110.917, -125.740, -127.841, 74.300);

        DescPose p3Desc = new DescPose(146.861, 578.426, 205.598, 175.997, -36.178, -93.437);
        JointPos p3Joint = new JointPos(-112.851, -60.191, 86.566, -80.676, -97.463, 74.300);

        DescPose p4Desc = new DescPose(136.284, 509.876, 225.613, 178.987, 1.372, -100.696);
        JointPos p4Joint = new JointPos(-116.397, -76.281, 113.845, -128.611, -88.654, 74.299);

        DescPose p5Desc = new DescPose(138.395, 505.972, 298.016, 179.134, 2.147, -101.110);
        JointPos p5Joint = new JointPos(-116.814, -82.333, 109.162, -118.662, -88.585, 74.302);

        DescPose p6Desc = new DescPose(105.553, 454.325, 232.017, -179.426, 0.444, -99.952);
        JointPos p6Joint = new JointPos(-115.649, -84.367, 122.447, -128.663, -90.432, 74.303);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 100, 0, 0, 0);

        robot.GetForwardKin(p1Joint, p1Desc);
        robot.GetForwardKin(p2Joint,  p2Desc);
        robot.GetForwardKin(p3Joint,  p3Desc);
        robot.GetForwardKin(p4Joint,  p4Desc);
        robot.GetForwardKin(p5Joint,  p5Desc);
        robot.GetForwardKin(p6Joint,  p6Desc);

        robot.MoveJ(p1Joint, p1Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(1);
        robot.MoveJ(p2Joint, p2Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(2);
        robot.MoveJ(p3Joint, p3Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(3);
        robot.MoveJ(p4Joint, p4Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(4);

        DescPose coordRtn = new DescPose(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);
        int rtn = robot.ComputeTcp4( coordRtn);

        robot.SetToolCoord(1, coordRtn, 0, 0, 1, 0);

        robot.GetForwardKin(p1Joint, p1Desc);
        robot.GetForwardKin(p2Joint, p2Desc);
        robot.GetForwardKin(p3Joint, p3Desc);

        robot.SetFocusCalibPoint(1, p1Desc);
        robot.SetFocusCalibPoint(2, p2Desc);
        robot.SetFocusCalibPoint(3, p3Desc);

        DescTran resultPos = new DescTran(0.0, 0.0, 0.0);
        double[] accuracy = {0.0};
        rtn = robot.ComputeFocusCalib(3,  resultPos,  accuracy);
        rtn = robot.SetFocusPosition(resultPos);

        robot.GetForwardKin(p5Joint,  p5Desc);
        robot.GetForwardKin(p6Joint,  p6Desc);

        robot.MoveL(p5Joint, p5Desc, 1, 0, 10, 100, 100, -1, 0, exaxisPos, 0, 1, offdese,0,100);
        robot.MoveL(p6Joint, p6Desc, 1, 0, 10, 100, 100, -1, 0, exaxisPos, 0, 1, offdese,0,100);

        robot.FocusStart(50, 19, 710, 90, 0);
        robot.MoveL(p5Joint, p5Desc, 1, 0, 10, 100, 100, -1, 0, exaxisPos, 0, 1, offdese,0,100);
        robot.MoveL(p6Joint, p6Desc, 1, 0, 10, 100, 100, -1, 0, exaxisPos, 0, 1, offdese,0,100);
        robot.FocusEnd();
    }

Włączenie funkcji kalibracji czułości czujnika momentu stawów
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Włączenie funkcji kalibracji czułości czujnika momentu stawów
    * @param status 0-wyłączone; 1-włączone
    * @return Kod błędu
    */
    public int JointSensitivityEnable(int status)

Zbieranie danych czułości czujnika momentu stawów
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Zbieranie danych czułości czujnika momentu stawów
    * @return Kod błędu
    */
    public int JointSensitivityCollect()

Pobieranie wyniku kalibracji czułości czujnika momentu stawów
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera wynik kalibracji czułości czujnika momentu stawów
    * @param calibResult Czułość stawów j1~j6 [0-1]
    * @param linearity Liniowość stawów j1~j6 [0-1]
    * @return Kod błędu
    */
    public int JointSensitivityCalibration(double calibResult[6], double linearity[6])

Pobieranie błędu histerezy czujnika momentu stawów
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera błąd histerezy czujnika momentu stawów
    * @param hysteresisError Błąd histerezy stawów j1~j6
    * @return Kod błędu
    */
    public int JointHysteresisError(double[] hysteresisError);

Pobieranie powtarzalności czujnika momentu stawów
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera powtarzalność czujnika momentu stawów
    * @param repeatability Powtarzalność czujnika momentu stawów j1~j6
    * @return Kod błędu
    */
    public int JointRepeatability(double[] repeatability);

Ustawianie parametrów czujnika siły stawów
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia parametry czujnika siły stawów
    * @param Parametry obowiązkowe M Współczynniki masy J1-J6 []
    * @param Parametry obowiązkowe B Współczynniki tłumienia J1-J6 []
    * @param Parametry obowiązkowe K Współczynniki sztywności J1-J6 []
    * @param Parametry domyślne threshold Próg sterowania siłą, Nm
    * @param Parametry domyślne sensitivity Czułość, Nm/V, []
    * @param Parametry domyślne setZeroFlag Flaga włączenia funkcji; 0-wyłączone; 1-włączone; 2-rejestracja punktu zerowego w pozycji 1; 3-rejestracja punktu zerowego w pozycji 2
    * @return Kod błędu
    */
    public int SetAdmittanceParams(double[] M, double[] B, double[] K, double[] threshold, double[] sensitivity, int setZeroFlag);

Przykład kodu automatycznej kalibracji czułości czujnika momentu stawów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestSensitivityCalib(Robot robot)
    {
        int rtn = robot.JointSensitivityEnable(0);
        rtn = robot.JointSensitivityEnable(1);
        System.out.printf("JointSensitivityEnable rtn is %d\n", rtn);
        JointPos curJPos = new JointPos();
        robot.GetActualJointPosDegree(curJPos);
        ExaxisPos epos = new ExaxisPos(0,0,0,0);
        DescPose offset_pos =new DescPose(0,0,0,0,0,0 );
        JointPos jointPos1 = new JointPos(curJPos.J1, 0, 0, -90, 0.02, curJPos.J6);
        DescPose descPos1 = new DescPose();
        robot.GetForwardKin(jointPos1, descPos1);
        robot.MoveJ(jointPos1, descPos1, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(200);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 1 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos2 =new JointPos( curJPos.J1, -30, 0, -90, 0.02, curJPos.J6 );
        DescPose descPos2 =new DescPose();
        robot.GetForwardKin(jointPos2, descPos2);
        robot.MoveJ(jointPos2, descPos2, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 2 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos3 = new JointPos( curJPos.J1, -60, 0, -90, 0.02, curJPos.J6 );
        DescPose descPos3 =new DescPose();
        robot.GetForwardKin(jointPos3, descPos3);
        robot.MoveJ(jointPos3, descPos3, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 3 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos4 = new JointPos(curJPos.J1, -90, 0, -90, 0.02, curJPos.J6);
        DescPose descPos4 = new DescPose();
        robot.GetForwardKin(jointPos4, descPos4);
        robot.MoveJ(jointPos4, descPos4, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 4 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos5 = new JointPos(curJPos.J1, -120, 0, -90, 0.02, curJPos.J6);
        DescPose descPos5 = new DescPose();
        robot.GetForwardKin(jointPos5, descPos5);
        robot.MoveJ(jointPos5, descPos5, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 5 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos6 = new JointPos(curJPos.J1, -150, 0, -90, 0.02, curJPos.J6);
        DescPose descPos6 = new DescPose();
        robot.GetForwardKin(jointPos6, descPos6);
        robot.MoveJ(jointPos6, descPos6, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 6 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos7 = new JointPos(curJPos.J1, -180, 0, -90, 0.02, curJPos.J6);
        DescPose descPos7 = new DescPose();
        robot.GetForwardKin(jointPos7, descPos7);
        robot.MoveJ(jointPos7, descPos7, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 7 rtn is %d\n", rtn);
        robot.Sleep(100);
        //skok wsteczny
        robot.MoveJ(jointPos6, descPos6, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 8 rtn is %d\n", rtn);
        robot.Sleep(100);
        robot.MoveJ(jointPos5, descPos5, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 9 rtn is %d\n", rtn);
        robot.Sleep(100);
        robot.MoveJ(jointPos4, descPos4, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 10 rtn is %d\n", rtn);
        robot.Sleep(100);
        robot.MoveJ(jointPos3, descPos3, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 11 rtn is %d\n", rtn);
        robot.Sleep(100);
        robot.MoveJ(jointPos2, descPos2, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 12 rtn is %d\n", rtn);
        robot.Sleep(100);
        robot.MoveJ(jointPos1, descPos1, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(200);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 13 rtn is %d\n", rtn);
        robot.Sleep(100);
        double[] calibResult =new double[6];
        double[] linearity = new double[6];
        rtn = robot.JointSensitivityCalibration(calibResult, linearity);
        System.out.printf("JointSensitivityCalibration rtn is %d\n", rtn);
        rtn = robot.JointSensitivityEnable(0);
        System.out.printf("JointSensitivityEnable rtn is %d\n", rtn);
        System.out.printf("jointSensor Calib result is %f %f %f %f %f %f\njointSensor linearity is %f %f %f %f %f %f\n",
                calibResult[0], calibResult[1], calibResult[2],
                calibResult[3], calibResult[4], calibResult[5],
                linearity[0], linearity[1], linearity[2],
                linearity[3], linearity[4], linearity[5]);
        double[] hysteresisError = {0.0, 0.0, 0.0, 0.0, 0.0, 0.0};
        rtn = robot.JointHysteresisError(hysteresisError);
        System.out.printf("JointHysteresisError result is %f %f %f %f %f %f\n",
                hysteresisError[0], hysteresisError[1], hysteresisError[2],
                hysteresisError[3], hysteresisError[4], hysteresisError[5]);
        double[] repeatability = {0.0, 0.0, 0.0, 0.0, 0.0, 0.0};
        rtn = robot.JointRepeatability(repeatability);
        System.out.printf("JointRepeatability result is %f %f %f %f %f %f\n",
                repeatability[0], repeatability[1], repeatability[2],
                repeatability[3], repeatability[4], repeatability[5]);
        double[] M = {1.0, 1.0, 1.0, 1.0, 1.0, 1.0};
        double[] B = {1.0, 1.0, 1.0, 1.0, 1.0, 1.0};
        double[] K = {0.0, 0.0, 0.0, 0.0, 0.0, 0.0};
        double[] threshold = {1.0, 1.0, 1.0, 1.0, 1.0, 1.0};
        int setZeroFlag = 1;
        rtn = robot.SetAdmittanceParams(M, B, K, threshold, calibResult, setZeroFlag);
        System.out.printf("SetAdmittanceParams rtn is %d\n", rtn);
    }

Pobieranie liczby błędnych ramek 8 portów stacji podrzędnej robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera liczbę błędnych ramek 8 portów stacji podrzędnej robota
    * @param inRecvErr Liczba błędnych ramek odbioru wejściowego
    * @param inCRCErr Liczba błędnych ramek CRC wejściowego
    * @param inTransmitErr Liczba błędnych ramek transmisji wejściowej
    * @param inLinkErr Liczba błędnych ramek łącza wejściowego
    * @param outRecvErr Liczba błędnych ramek odbioru wyjściowego
    * @param outCRCErr Liczba błędnych ramek CRC wyjściowego
    * @param outTransmitErr Liczba błędnych ramek transmisji wyjściowej
    * @param outLinkErr Liczba błędnych ramek łącza wyjściowego
    * @return Kod błędu
    */
    public int GetSlavePortErrCounter(int[] inRecvErr, int[] inCRCErr, int[] inTransmitErr, int[] inLinkErr, int[] outRecvErr, int[] outCRCErr, int[] outTransmitErr, int[] outLinkErr)

Zerowanie licznika błędnych ramek portu stacji podrzędnej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Zerowanie licznika błędnych ramek portu stacji podrzędnej
    * @param slaveID Numer stacji podrzędnej 0~7
    * @return Kod błędu
    */
    public int SlavePortErrCounterClear(int slaveID)

Przykład kodu pobierania błędnych ramek portu stacji podrzędnej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestSlavePortErr(Robot robot)
    {
        ROBOT_STATE_PKG pkg =new ROBOT_STATE_PKG();
        int[] inRecvErr =new int[8];
        int[] inCRCErr =new int[8];
        int[] inTransmitErr =new int[8];
        int[] inLinkErr =new int[8];
        int[] outRecvErr =new int[8];
        int[] outCRCErr =new int[8];
        int[] outTransmitErr =new int[8];
        int[] outLinkErr =new int[8];
        robot.GetSlavePortErrCounter(inRecvErr,  inCRCErr, inTransmitErr, inLinkErr,
                outRecvErr, outCRCErr, outTransmitErr, outLinkErr);
        for (int i = 0; i < 8; i++)
        {
            if (inRecvErr[i] != 0)
            {
                System.out.printf("inRecvErr %d is %d\n", i, inRecvErr[i]);
            }
            if (inCRCErr[i] != 0)
            {
                System.out.printf("inRecvErr %d is %d\n", i, inCRCErr[i]);
            }
            if (inTransmitErr[i] != 0)
            {
                System.out.printf("inRecvErr %d is %d\n", i, inTransmitErr[i]);
            }
            if (inLinkErr[i] != 0)
            {
                System.out.printf("inRecvErr %d is %d\n", i, inLinkErr[i]);
            }
            if (outRecvErr[i] != 0)
            {
                System.out.printf("outRecvErr %d is %d\n", i, outRecvErr[i]);
            }
            if (outCRCErr[i] != 0)
            {
                System.out.printf("outCRCErr %d is %d\n", i, outCRCErr[i]);
            }
            if (outTransmitErr[i] != 0)
            {
                System.out.printf("outTransmitErr %d is %d\n", i, outTransmitErr[i]);
            }
            if (outLinkErr[i] != 0)
            {
                System.out.printf("outLinkErr %d is %d\n", i, outLinkErr[i]);
            }
        }
        System.out.printf("others has no err!\n");
        for (int i = 0; i < 8; i++)
        {
            robot.SlavePortErrCounterClear(i);
        }
        robot.CloseRPC();
    }

Ustawianie współczynników sprzężenia przedniego prędkości dla poszczególnych osi
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ustawia współczynniki sprzężenia przedniego prędkości dla poszczególnych osi
    * @param radio Współczynniki sprzężenia przedniego prędkości dla poszczególnych osi
    * @return Kod błędu
    */
    public int SetVelFeedForwardRatio(double[] radio)

Pobieranie współczynników sprzężenia przedniego prędkości dla poszczególnych osi
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Pobiera współczynniki sprzężenia przedniego prędkości dla poszczególnych osi
    * @param radio Współczynniki sprzężenia przedniego prędkości dla poszczególnych osi
    * @return Kod błędu
    */
    public int GetVelFeedForwardRatio(double[] radio)

Przykład kodu współczynników sprzężenia przedniego prędkości robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestVelFeedForwardRatio(Robot robot)
    {
        double[] setRadio =new double[] { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
        robot.SetVelFeedForwardRatio(setRadio);
        double[] getRadio = new double[]{ 0.0 };
        robot.GetVelFeedForwardRatio(getRadio);
        System.out.printf(" %f %f %f %f %f %f\n", getRadio[0], getRadio[1], getRadio[2], getRadio[3], getRadio[4], getRadio[5]);
        robot.CloseRPC();
    }

Kalibracja TCP czujnika fotoelektrycznego - obliczanie RPY narzędzia
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Kalibracja TCP czujnika fotoelektrycznego - obliczanie RPY narzędzia
    * @param Btool Pozycja kartezjańska robota
    * @param Etool Wartości bieżącego układu współrzędnych narzędzia
    * @param sensor Wartości bieżącego układu współrzędnych czujnika (tymczasowo niedostępne)
    * @param radius Promień ruchu okrężnego mm (tymczasowo niedostępne)
    * @param dz Odległość ruchu w kierunku ujemnym osi Z układu bazowego; gdy dz = 10000, funkcja bezpośrednio zwraca RPY narzędzia
    * @param TCPRPY Wartości RPY narzędzia
    * @return Kod błędu
    */
    public int TCPComputeRPY(DescPose Btool, DescPose Etool, DescPose sensor, double radius, double dz, Rpy TCPRPY)

Kalibracja TCP czujnika fotoelektrycznego - obliczanie XYZ narzędzia
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Kalibracja TCP czujnika fotoelektrycznego - obliczanie XYZ narzędzia
    * @param select 0-obliczanie TCP narzędzia; 1-obliczanie punktu początkowego czujnika; 2-obliczanie orientacji czujnika; 3-bezpośrednie zwrócenie TCP narzędzia; 4-rejestracja bieżącego układu współrzędnych obiektu i narzędzia
    * @param originDirection 0-kierunek X; 1-kierunek Y; 2-kierunek Z
    * @param pos1 Pozycja kartezjańska robota 1
    * @param pos2 Pozycja kartezjańska robota 2
    * @param pos3 Pozycja kartezjańska robota 3
    * @param pos4 Pozycja kartezjańska robota 4
    * @param TCP Wartości XYZ narzędzia
    * @return Kod błędu
    */
    public int TCPComputeXYZ(int select, double originDirection, DescTran pos1, DescTran pos2, DescTran pos3, DescTran pos4, DescTran TCP)

Kalibracja TCP czujnika fotoelektrycznego - rozpoczęcie rejestracji pozycji środka kołnierza końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Kalibracja TCP czujnika fotoelektrycznego - rozpoczęcie rejestracji pozycji środka kołnierza końcowego
    * @return Kod błędu
    */
    public int TCPRecordFlangePosStart()

Kalibracja TCP czujnika fotoelektrycznego - zatrzymanie rejestracji pozycji środka kołnierza końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Kalibracja TCP czujnika fotoelektrycznego - zatrzymanie rejestracji pozycji środka kołnierza końcowego
    * @return Kod błędu
    */
    public int TCPRecordFlangePosEnd()

Kalibracja TCP czujnika fotoelektrycznego - pobieranie pozycji środka końcowego narzędzia
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Kalibracja TCP czujnika fotoelektrycznego - pobieranie pozycji środka końcowego narzędzia
    * @param TCP Pozycja środka narzędzia (x, y, z)
    * @return Kod błędu
    */
    public int TCPGetRecordFlangePos(DescTran TCP)

Kalibracja TCP czujnika fotoelektrycznego
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Kalibracja TCP czujnika fotoelektrycznego
    * @param luaPath Ścieżka programu lua automatycznej kalibracji: dla robota wersji QX - "/fruser/FR_CalibrateTheToolTcp.lua"; dla robota wersji LA - "/usr/local/etc/controller/lua/FR_CalibrateTheToolTcp.lua"
    * @param offset Przesunięcie punktu nauczania (x, y, z) mm
    * @param TCP Układ współrzędnych narzędzia po kalibracji (x, y, z, rx, ry, rz)
    * @return Kod błędu
    */
    public int PhotoelectricSensorTCPCalibration(String luaPath, DescTran offset, DescPose TCP)

Przykład kodu kalibracji TCP czujnika fotoelektrycznego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestPhotoelectricSensorTCPCalib(Robot robot)
    {
        DescTran offset = new DescTran(10.0, 10.0, 3.0 );
        DescPose TCP = new DescPose();
        int rtn = robot.PhotoelectricSensorTCPCalibration("/fruser/FR_CalibrateTheToolTcp.lua", offset, TCP);
        System.out.printf("PhotoelectricSensorTCPCalibration rtn is %d %f %f %f %f %f %f \n", rtn, TCP.tran.x, TCP.tran.y, TCP.tran.z, TCP.rpy.rx, TCP.rpy.ry, TCP.rpy.rz);
        robot.CloseRPC();
        robot.Sleep(9999999);
    }