Ustawienia ogólne robota
========================

.. toctree:: 
    :maxdepth: 5

Ustawienie punktu odniesienia narzędzia - metoda sześciopunktowa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Ustawia punkt odniesienia narzędzia - metoda sześciopunktowa 
    * @param [in] point_num Numer punktu, zakres [1~6] 
    * @return Kod błędu 
    */ 
    int SetToolPoint(int point_num); 

Obliczenie układu współrzędnych narzędzia - metoda sześciopunktowa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Oblicza układ współrzędnych narzędzia
    * @param [out] tcp_pose Układ współrzędnych narzędzia
    * @return Kod błędu 
    */ 
    int ComputeTool(ref DescPose tcp_pose); 

Ustawienie punktu odniesienia narzędzia - metoda czteropunktowa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Ustawia punkt odniesienia narzędzia - metoda czteropunktowa 
    * @param [in] point_num Numer punktu, zakres [1~4] 
    * @return Kod błędu 
    */ 
    int SetTcp4RefPoint(int point_num);

Obliczenie układu współrzędnych narzędzia - metoda czteropunktowa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Oblicza układ współrzędnych narzędzia
    * @param [out] tcp_pose Układ współrzędnych narzędzia
    * @return Kod błędu 
    */ 
    int ComputeTcp4(ref DescPose tcp_pose);

Ustawienie układu współrzędnych narzędzia
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ustawia układ współrzędnych narzędzia
    * @param  [in] id Numer układu współrzędnych, zakres [0~14]
    * @param  [in] coord  Pozycja środka narzędzia względem środka kołnierza końcowego
    * @param  [in] type  0-układ współrzędnych narzędzia, 1-układ współrzędnych czujnika
    * @param  [in] install Pozycja instalacji, 0-koniec robota, 1-na zewnątrz robota
    * param   [in] toolID ID narzędzia
    * @param  [in] loadNum Numer obciążenia
    * @return  Kod błędu
    */
    int SetToolCoord(int id, DescPose coord, int type, int install,int toolID, int loadNum);

Obliczenie układu współrzędnych narzędzia na podstawie punktów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Oblicza układ współrzędnych narzędzia na podstawie punktów
    * @param [in] method Metoda obliczeniowa; 0-metoda czteropunktowa; 1-metoda sześciopunktowa
    * @param [in] pos Grupa pozycji stawów, długość tablicy 4 dla metody czteropunktowej, długość 6 dla metody sześciopunktowej
    * @return Kod błędu
    */

    int ComputeToolCoordWithPoints(int method, JointPos[] pos, ref DescPose coordRtn)  

Ustawienie listy układów współrzędnych narzędzia
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
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
    int SetToolList(int id, DescPose coord, int type, int install, int loadNum);  

Pobranie bieżącego układu współrzędnych narzędzia
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera bieżący układ współrzędnych narzędzia
    * @param  [in] flag 0-blokujący, 1-nieblokujący
    * @param  [out] desc_pos Pozycja i orientacja układu współrzędnych narzędzia
    * @return  Kod błędu
    */
    int GetTCPOffset(byte flag, ref DescPose desc_pos); 

Przykład kodu operacji na układzie współrzędnych narzędzia robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button18_Click(object sender, EventArgs e)
    {
        DescPose p1Desc = new DescPose(186.331f, 487.913f, 209.850f, 149.030f, 0.688f, -114.347f);
        JointPos p1Joint = new JointPos(-127.876f, -75.341f, 115.417f, -122.741f, -59.820f, 74.300f);

        DescPose p2Desc = new DescPose(69.721f, 535.073f, 202.882f, -144.406f, -14.775f, -89.012f);
        JointPos p2Joint = new JointPos(-101.780f, -69.828f, 110.917f, -125.740f, -127.841f, 74.300f);

        DescPose p3Desc = new DescPose(146.861f, 578.426f, 205.598f, 175.997f, -36.178f, -93.437f);
        JointPos p3Joint = new JointPos(-112.851f, -60.191f, 86.566f, -80.676f, -97.463f, 74.300f);

        DescPose p4Desc = new DescPose(136.284f, 509.876f, 225.613f, 178.987f, 1.372f, -100.696f);
        JointPos p4Joint = new JointPos(-116.397f, -76.281f, 113.845f, -128.611f, -88.654f, 74.299f);

        DescPose p5Desc = new DescPose(138.395f, 505.972f, 298.016f, 179.134f, 2.147f, -101.110f);
        JointPos p5Joint = new JointPos(-116.814f, -82.333f, 109.162f, -118.662f, -88.585f, 74.302f);

        DescPose p6Desc = new DescPose(105.553f, 454.325f, 232.017f, -179.426f, 0.444f, -99.952f);
        JointPos p6Joint = new JointPos(-115.649f, -84.367f, 122.447f, -128.663f, -90.432f, 74.303f);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        JointPos[] posJ = new JointPos[] { p1Joint, p2Joint, p3Joint, p4Joint, p5Joint, p6Joint };
        DescPose coordRtn = new DescPose();
        int rtn = robot.ComputeToolCoordWithPoints(1, posJ, ref coordRtn);
        Console.WriteLine($"ComputeToolCoordWithPoints    {rtn}  coord is {coordRtn.tran.x} {coordRtn.tran.y} {coordRtn.tran.z} {coordRtn.rpy.rx} {coordRtn.rpy.ry} {coordRtn.rpy.rz}");

        robot.MoveJ( p1Joint,  p1Desc, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetToolPoint(1);
        robot.MoveJ( p2Joint,  p2Desc, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetToolPoint(2);
        robot.MoveJ( p3Joint,  p3Desc, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetToolPoint(3);
        robot.MoveJ( p4Joint,  p4Desc, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetToolPoint(4);
        robot.MoveJ( p5Joint,  p5Desc, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetToolPoint(5);
        robot.MoveJ( p6Joint,  p6Desc, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetToolPoint(6);
        rtn = robot.ComputeTool(ref coordRtn);
        Console.WriteLine($"6 Point ComputeTool        {rtn}  coord is {coordRtn.tran.x} {coordRtn.tran.y} {coordRtn.tran.z} {coordRtn.rpy.rx} {coordRtn.rpy.ry} {coordRtn.rpy.rz}");
        robot.SetToolList(1,  coordRtn, 0, 0, 0);

        robot.MoveJ( p1Joint,  p1Desc, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetTcp4RefPoint(1);
        robot.MoveJ( p2Joint,  p2Desc, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetTcp4RefPoint(2);
        robot.MoveJ( p3Joint,  p3Desc, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetTcp4RefPoint(3);
        robot.MoveJ( p4Joint,  p4Desc, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetTcp4RefPoint(4);
        rtn = robot.ComputeTcp4(ref coordRtn);
        Console.WriteLine($"4 Point ComputeTool        {rtn}  coord is {coordRtn.tran.x} {coordRtn.tran.y} {coordRtn.tran.z} {coordRtn.rpy.rx} {coordRtn.rpy.ry} {coordRtn.rpy.rz}");

        robot.SetToolCoord(2, coordRtn, 0, 0, 1, 0);

        DescPose getCoord = new DescPose();
        rtn = robot.GetTCPOffset(0, ref getCoord);
        Console.WriteLine($"GetTCPOffset    {rtn}  coord is {coordRtn.tran.x} {coordRtn.tran.y} {coordRtn.tran.z} {coordRtn.rpy.rx} {coordRtn.rpy.ry} {coordRtn.rpy.rz}");
    }

Ustawienie punktu odniesienia zewnętrznego narzędzia - metoda trzypunktowa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Ustawia punkt odniesienia zewnętrznego narzędzia - metoda trzypunktowa 
    * @param [in] point_num Numer punktu, zakres [1~3] 
    * @return Kod błędu 
    */ 
    int SetExTCPPoint(int point_num); 

Obliczenie zewnętrznego układu współrzędnych narzędzia - metoda trzypunktowa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:
    
    /** 
    * @brief Oblicza zewnętrzny układ współrzędnych narzędzia - metoda trzypunktowa
    * @param [out] tcp_pose Zewnętrzny układ współrzędnych narzędzia
    * @return Kod błędu 
    */ 
    int ComputeExTCF(ref DescPose tcp_pose); 

Ustawienie zewnętrznego układu współrzędnych narzędzia
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia zewnętrzny układ współrzędnych narzędzia 
    * @param [in] id Numer układu współrzędnych, zakres [0~14] 
    * @param [in] etcp Pozycja środka narzędzia względem środka kołnierza końcowego 
    * @param [in] etool Do określenia 
    * @return Kod błędu 
    */
    int SetExToolCoord(int id, DescPose etcp, DescPose etool); 

Ustawienie listy zewnętrznych układów współrzędnych narzędzia
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ustawia listę zewnętrznych układów współrzędnych narzędzia
    * @param  [in] id Numer układu współrzędnych, zakres [0~14] 
    * @param  [in] etcp  Pozycja środka narzędzia względem środka kołnierza końcowego
    * @param  [in] etool  Do określenia
    * @return  Kod błędu
    */
    int SetExToolList(int id, DescPose etcp, DescPose etool); 

Obliczenie układu współrzędnych przedmiotu na podstawie punktów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Oblicza układ współrzędnych przedmiotu na podstawie punktów
    * @param [in] method Metoda obliczeniowa; 0: początek - oś X - oś Z  1: początek - oś X - płaszczyzna XY
    * @param [in] pos Trzy grupy pozycji TCP
    * @param [in] refFrame Układ odniesienia
    * @return Kod błędu
    */
    int ComputeWObjCoordWithPoints(int method, DescPose[] pos, int refFrame, ref DescPose coordRtn)

Przykład kodu operacji na zewnętrznym układzie współrzędnych narzędzia robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button20_Click(object sender, EventArgs e)
    {
        DescPose p1Desc = new DescPose(-89.606f, 779.517f, 193.516f, 178.000f, 0.476f, -92.484f);
        JointPos p1Joint = new JointPos(-108.145f, -50.137f, 85.818f, -125.599f, -87.946f, 74.329f);

        DescPose p2Desc = new DescPose(-24.656f, 850.384f, 191.361f, 177.079f, -2.058f, -95.355f);
        JointPos p2Joint = new JointPos(-111.024f, -41.538f, 69.222f, -114.913f, -87.743f, 74.329f);

        DescPose p3Desc = new DescPose(-99.813f, 766.661f, 241.878f, -176.817f, 1.917f, -91.604f);
        JointPos p3Joint = new JointPos(-107.266f, -56.116f, 85.971f, -122.560f, -92.548f, 74.331f);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        DescPose[] posTCP = new DescPose[] { p1Desc, p2Desc, p3Desc };
        DescPose coordRtn = new DescPose();

        robot.MoveJ( p1Joint,  p1Desc, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetExTCPPoint(1);
        robot.MoveJ( p2Joint,  p2Desc, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetExTCPPoint(2);
        robot.MoveJ( p3Joint,  p3Desc, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetExTCPPoint(3);
        int rtn = robot.ComputeExTCF(ref coordRtn);
        Console.WriteLine($"ComputeExTCF                   {rtn}  coord is {coordRtn.tran.x} {coordRtn.tran.y} {coordRtn.tran.z} {coordRtn.rpy.rx} {coordRtn.rpy.ry} {coordRtn.rpy.rz}");

        robot.SetExToolCoord(1,  coordRtn,  offdese);
        robot.SetExToolList(1,  coordRtn,  offdese);
    }

Ustawienie punktu odniesienia układu współrzędnych przedmiotu - metoda trzypunktowa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Ustawia punkt odniesienia przedmiotu - metoda trzypunktowa 
    * @param [in] point_num Numer punktu, zakres [1~3]  
    * @return Kod błędu 
    */ 
    int SetWObjCoordPoint(int point_num); 

Obliczenie układu współrzędnych przedmiotu
+++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Oblicza układ współrzędnych przedmiotu
    * @param [in] method Metoda obliczeniowa 0: początek - oś X - oś Z  1: początek - oś X - płaszczyzna XY
    * @param [in] refFrame Układ odniesienia
    * @param [out] wobj_pose Układ współrzędnych przedmiotu
    * @return Kod błędu
    */
    int ComputeWObjCoord(int method, int refFrame, ref DescPose wobj_pose); 

Ustawienie układu współrzędnych przedmiotu
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ustawia układ współrzędnych przedmiotu
    * @param  [in] id Numer układu współrzędnych, zakres [1~15]
    * @param  [in] coord  Pozycja układu współrzędnych przedmiotu względem środka kołnierza końcowego
    * @param  [in] refFrame Układ odniesienia
    * @return  Kod błędu
    */
    int SetWObjCoord(int id, DescPose coord, int refFrame);

Ustawienie listy układów współrzędnych przedmiotu
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ustawia listę układów współrzędnych przedmiotu
    * @param  [in] id Numer układu współrzędnych, zakres [0~14] 
    * @param  [in] coord  Pozycja układu współrzędnych przedmiotu względem środka kołnierza końcowego
    * @param  [in] refFrame Układ odniesienia
    * @return  Kod błędu
    */    
    int SetWObjList(int id, DescPose coord, int refFrame);

Pobranie bieżącego układu współrzędnych przedmiotu
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera bieżący układ współrzędnych przedmiotu
    * @param  [in] flag 0-blokujący, 1-nieblokujący
    * @param  [out] desc_pos Pozycja i orientacja układu współrzędnych przedmiotu
    * @return  Kod błędu
    */   
    int GetWObjOffset(byte flag, ref DescPose desc_pos); 

Przykład kodu operacji na układzie współrzędnych przedmiotu robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button19_Click(object sender, EventArgs e)
    {
        DescPose p1Desc = new DescPose(-89.606, 779.517, 193.516, 178.000, 0.476, -92.484);
        JointPos p1Joint = new JointPos(-108.145, -50.137, 85.818, -125.599, -87.946, 74.329);

        DescPose p2Desc = new DescPose(-24.656, 850.384, 191.361, 177.079, -2.058, -95.355);
        JointPos p2Joint = new JointPos(-111.024, -41.538, 69.222, -114.913, -87.743, 74.329);

        DescPose p3Desc = new DescPose(-99.813, 766.661, 241.878, -176.817, 1.917, -91.604);
        JointPos p3Joint = new JointPos(-107.266, -56.116, 85.971, -122.560, -92.548, 74.331);

        robot.GetForwardKin(p1Joint,ref p1Desc);
        robot.GetForwardKin(p2Joint,ref p2Desc);
        robot.GetForwardKin(p3Joint, ref p3Desc);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        DescPose[] posTCP = new DescPose[] { p1Desc, p2Desc, p3Desc };
        DescPose coordRtn = new DescPose();
        int rtn = robot.ComputeWObjCoordWithPoints(1, posTCP, 0, ref coordRtn);
        Console.WriteLine($"ComputeWObjCoordWithPoints    {rtn}  coord is {coordRtn.tran.x} {coordRtn.tran.y} {coordRtn.tran.z} {coordRtn.rpy.rx} {coordRtn.rpy.ry} {coordRtn.rpy.rz}");

        robot.MoveJ( p1Joint,  p1Desc, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetWObjCoordPoint(1);
        robot.MoveJ( p2Joint,  p2Desc, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetWObjCoordPoint(2);
        robot.MoveJ( p3Joint,  p3Desc, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetWObjCoordPoint(3);
        rtn = robot.ComputeWObjCoord(1, 0, ref coordRtn);
        Console.WriteLine($"ComputeWObjCoord                   {rtn}  coord is {coordRtn.tran.x} {coordRtn.tran.y} {coordRtn.tran.z} {coordRtn.rpy.rx} {coordRtn.rpy.ry} {coordRtn.rpy.rz}");

        robot.SetWObjCoord(1,  coordRtn, 0);
        robot.SetWObjList(1,  coordRtn, 0);

        DescPose getWobjDesc = new DescPose();
        rtn = robot.GetWObjOffset(0, ref getWobjDesc);
        Console.WriteLine($"GetWObjOffset                   {rtn}  coord is {coordRtn.tran.x} {coordRtn.tran.y} {coordRtn.tran.z} {coordRtn.rpy.rx} {coordRtn.rpy.ry} {coordRtn.rpy.rz}");   
    } 

Ustawienie prędkości globalnej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ustawia prędkość globalną
    * @param  [in]  vel  Procent prędkości, zakres [0~100]
    * @return  Kod błędu
    */
    int SetSpeed(int vel); 

Ustawienie przyspieszenia robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia przyspieszenie robota
    * @param [in] acc Procent przyspieszenia robota
    * @return Kod błędu
    */
    int SetOaccScale(double acc)

Pobranie domyślnej prędkości robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera domyślną prędkość robota
    * @param  [out]  vel  Prędkość, jednostka mm/s
    * @return  Kod błędu
    */   
    int GetDefaultTransVel(ref double vel); 

Ustawienie masy ładunku końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ustawia masę ładunku końcowego
    * @param  [in] loadNum Numer obciążenia
    * @param  [in] weight  Masa ładunku, jednostka kg
    * @return  Kod błędu
    */
    int SetLoadWeight(int loadNum, float weight)

Ustawienie współrzędnych środka ciężkości ładunku końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ustawia współrzędne środka ciężkości ładunku końcowego
    * @param  [in] coord Współrzędne środka ciężkości, jednostka mm
    * @return  Kod błędu
    */
    int SetLoadCoord(DescTran coord); 

Pobranie masy bieżącego ładunku
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera masę bieżącego ładunku
    * @param  [in] flag 0-blokujący, 1-nieblokujący
    * @param  [out] weight Masa ładunku, jednostka kg
    * @return  Kod błędu
    */
    int GetTargetPayload(byte flag, ref double weight); 

Pobranie środka ciężkości bieżącego ładunku
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera środek ciężkości bieżącego ładunku
    * @param  [in] flag 0-blokujący, 1-nieblokujący
    * @param  [out] cog Środek ciężkości ładunku, jednostka mm
    * @return  Kod błędu
    */   
    int GetTargetPayloadCog(byte flag, ref DescTran cog);

Ustawienie sposobu instalacji robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ustawia sposób instalacji robota
    * @param  [in] install  Sposób instalacji, 0-instalacja normalna, 1-instalacja boczna, 2-instalacja odwrócona
    * @return  Kod błędu
    */
    int SetRobotInstallPos(byte install); 

Ustawienie kąta instalacji robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ustawia kąt instalacji robota, instalacja swobodna
    * @param  [in] yangle  Kąt nachylenia
    * @param  [in] zangle  Kąt obrotu
    * @return  Kod błędu
    */
    int SetRobotInstallAngle(double yangle, double zangle); 

Pobranie kąta instalacji robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera kąt instalacji robota
    * @param  [out] yangle Kąt nachylenia
    * @param  [out] zangle Kąt obrotu
    * @return  Kod błędu
    */
    int GetRobotInstallAngle(ref double yangle, ref double zangle); 

Ustawienie wartości zmiennej systemowej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ustawia wartość zmiennej systemowej
    * @param  [in]  id  Numer zmiennej, zakres [1~20]
    * @param  [in]  value Wartość zmiennej
    * @return  Kod błędu
    */
    int SetSysVarValue(int id, double value); 

Pobranie wartości zmiennej systemowej
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera wartość zmiennej systemowej
    * @param  [in] id Numer zmiennej systemowej, zakres [1~20]
    * @param  [out] value  Wartość zmiennej systemowej
    * @return  Kod błędu
    */
    int GetSysVarValue(int id, ref double value); 

Przykład kodu ustawień ogólnych robota
++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button21_Click(object sender, EventArgs e)
    {
        for (int i = 1; i < 100; i++)
        {
            robot.SetSpeed(i);
            robot.SetOaccScale(i);
            Thread.Sleep(30);
        }

        double defaultVel = 0.0f;
        robot.GetDefaultTransVel(ref defaultVel);
        Console.WriteLine($"GetDefaultTransVel is {defaultVel}");

        for (int i = 1; i < 21; i++)
        {
            robot.SetSysVarValue(i, i + 0.5f);
            Thread.Sleep(100);
        }

        for (int i = 1; i < 21; i++)
        {
            double value = 0;
            robot.GetSysVarValue(i, ref value);
            Console.WriteLine($"sys value  {i} is :{value}");
            Thread.Sleep(100);
        }

        robot.SetLoadWeight(0, 2.5f);

        DescTran loadCoord = new DescTran();
        loadCoord.x = 3.0f;
        loadCoord.y = 4.0f;
        loadCoord.z = 5.0f;
        robot.SetLoadCoord( loadCoord);

        Thread.Sleep(1000);

        double getLoad = 0.0f;
        robot.GetTargetPayload(0, ref getLoad);

        DescTran getLoadTran = new DescTran();
        robot.GetTargetPayloadCog(0, ref getLoadTran);
        Console.WriteLine($"get load is {getLoad}; get load cog is {getLoadTran.x} {getLoadTran.y} {getLoadTran.z}");

        robot.SetRobotInstallPos(0);
        robot.SetRobotInstallAngle(15.0f, 25.0f);

        double anglex = 0.0f;
        double angley = 0.0f;
        robot.GetRobotInstallAngle(ref anglex, ref angley);
        Console.WriteLine($"GetRobotInstallAngle x:  {anglex};  y:  {angley}");
    }

Przełącznik kompensacji tarcia stawów
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Przełącznik kompensacji tarcia stawów 
    * @param [in] state 0-wył., 1-wł. 
    * @return Kod błędu 
    */ 
    int FrictionCompensationOnOff(byte state); 

Ustawienie współczynnika kompensacji tarcia stawów - instalacja normalna
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ustawia współczynnik kompensacji tarcia stawów - instalacja normalna
    * @param  [in]  coeff Współczynniki kompensacji dla sześciu stawów, zakres [0~1]
    * @return  Kod błędu
    */
    int SetFrictionValue_level(double[] coeff);

Ustawienie współczynnika kompensacji tarcia stawów - instalacja boczna
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ustawia współczynnik kompensacji tarcia stawów - instalacja boczna
    * @param  [in]  coeff Współczynniki kompensacji dla sześciu stawów, zakres [0~1]
    * @return  Kod błędu
    */
    int SetFrictionValue_wall(double[] coeff); 

Ustawienie współczynnika kompensacji tarcia stawów - instalacja odwrócona
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ustawia współczynnik kompensacji tarcia stawów - instalacja odwrócona
    * @param  [in]  coeff Współczynniki kompensacji dla sześciu stawów, zakres [0~1]
    * @return  Kod błędu
    */
    int SetFrictionValue_ceiling(double[] coeff);

Ustawienie współczynnika kompensacji tarcia stawów - instalacja swobodna
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ustawia współczynnik kompensacji tarcia stawów - instalacja swobodna
    * @param  [in]  coeff Współczynniki kompensacji dla sześciu stawów, zakres [0~1]
    * @return  Kod błędu
    */
    int SetFrictionValue_freedom(double[] coeff);
       
Przykład kodu ustawiania kompensacji tarcia stawów robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnRobotSafetySet_Click(object sender, EventArgs e)
    {
        double[] lcoeff = { 0.9f, 0.9f, 0.9f, 0.9f, 0.9f, 0.9f };
        double[] wcoeff = { 0.4f, 0.4f, 0.4f, 0.4f, 0.4f, 0.4f };
        double[] ccoeff = { 0.6f, 0.6f, 0.6f, 0.6f, 0.6f, 0.6f };
        double[] fcoeff = { 0.5f, 0.5f, 0.5f, 0.5f, 0.5f, 0.5f };

        int rtn = robot.FrictionCompensationOnOff(1);
        Console.WriteLine($"FrictionCompensationOnOff rtn is{rtn}");

        rtn = robot.SetFrictionValue_level(lcoeff);
        Console.WriteLine($"SetFrictionValue_level rtn is {rtn}");

        rtn = robot.SetFrictionValue_wall(wcoeff);
        Console.WriteLine($"SetFrictionValue_wall rtn is{rtn}");

        rtn = robot.SetFrictionValue_ceiling(ccoeff);
        Console.WriteLine($"SetFrictionValue_ceiling rtn is {rtn}");

        rtn = robot.SetFrictionValue_freedom(fcoeff);
        Console.WriteLine($"SetFrictionValue_freedom rtn is {rtn}");
    }

Pobranie kodu błędu robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Pobiera kod błędu robota 
    * @param [out] maincode   Główny kod błędu
    * @param [out] subcode    Podrzędny kod błędu
    * @return Kod błędu 
    */ 
    int GetRobotErrorCode(ref int maincode, ref int subcode);

Wyczyść błędy
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Czyści stany błędów
    * @return  Kod błędu
    */
    int ResetAllError(); 

Przykład kodu pobierania stanu awaryjnego i czyszczenia błędów robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnRobotSafetySet_Click(object sender, EventArgs e)
    {
        int maincode=0, subcode=0;
        robot.GetRobotErrorCode(ref maincode, ref subcode);
        Console.WriteLine($"robot maincode is{maincode};  subcode is {subcode}" );

        robot.ResetAllError();

        Thread.Sleep(1000);

        robot.GetRobotErrorCode(ref maincode, ref subcode);
        Console.WriteLine($"robot maincode is{maincode};  subcode is{subcode}");
    }

Ustawienie parametrów monitorowania temperatury i prędkości wentylatora skrzynki sterowniczej szerokiego napięcia
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia parametry monitorowania temperatury i prędkości wentylatora skrzynki sterowniczej szerokiego napięcia
    * @param [in] enable 0-nie włączaj monitorowania; 1-włącz monitorowanie
    * @param [in] period Okres monitorowania (s), zakres 1-100
    * @return Kod błędu
    */
    int SetWideBoxTempFanMonitorParam(int enable, int period);

Pobranie parametrów monitorowania temperatury i prędkości wentylatora skrzynki sterowniczej szerokiego napięcia
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Pobiera parametry monitorowania temperatury i prędkości wentylatora skrzynki sterowniczej szerokiego napięcia
    * @param [out] enable 0-nie włączaj monitorowania; 1-włącz monitorowanie
    * @param [out] period Okres monitorowania (s), zakres 1-100
    * @return Kod błędu
    */
    int GetWideBoxTempFanMonitorParam(ref int enable, ref int period);

Przykład kodu
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3
    
.. code-block:: c#
    :linenos:

    private void button46_Click(object sender, EventArgs e)
    {
        var pkg = new ROBOT_STATE_PKG(); 
        robot.SetWideBoxTempFanMonitorParam(1, 2);    
        int enable = 0;
        int period = 0;
        robot.GetWideBoxTempFanMonitorParam(ref enable, ref period);
        Console.WriteLine($"GetWideBoxTempFanMonitorParam enable is {enable}   period is {period}");  
        for (int i = 0; i < 100; i++)
        {
            robot.GetRobotRealTimeState(ref pkg);
            Console.WriteLine($"robot ctrl box temp is {pkg.wideVoltageCtrlBoxTemp}, fan current is {pkg.wideVoltageCtrlBoxFanVel}");
            Thread.Sleep(100);
        }       
        int rtn = robot.SetWideBoxTempFanMonitorParam(0, 2);
        Console.WriteLine($"SetWideBoxTempFanMonitorParam rtn is {rtn}");       
        enable = 0;
        period = 0;
        robot.GetWideBoxTempFanMonitorParam(ref enable, ref period);
        Console.WriteLine($"GetWideBoxTempFanMonitorParam enable is {enable}   period is {period}");  
        for (int i = 0; i < 100; i++)
        {
            robot.GetRobotRealTimeState(ref pkg);
            Console.WriteLine($" robot ctrl box temp is {pkg.wideVoltageCtrlBoxTemp}, fan current is {pkg.wideVoltageCtrlBoxFanVel}");
            Thread.Sleep(100);
        }
    }

Ustawienie punktu kalibracji ogniska
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia punkt kalibracji ogniska
    * @param [in] pointNum Numer punktu kalibracji ogniska 1-8
    * @param [in] point Współrzędne punktu kalibracji
    * @return Kod błędu
    */
    int SetFocusCalibPoint(int pointNum, DescPose point);

Ustawienie współrzędnych ogniska
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia współrzędne ogniska
    * @param [in] pos Współrzędne ogniska XYZ
    * @return Kod błędu
    */
    int SetFocusPosition(DescTran pos);

Rozpoczęcie śledzenia ogniska
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Rozpoczyna śledzenie ogniska
    * @param [in] kp Parametr proporcjonalny, domyślnie 50.0
    * @param [in] kpredict Parametr sprzężenia przedniego, domyślnie 19.0
    * @param [in] aMax Maksymalne ograniczenie przyspieszenia kątowego, domyślnie 1440°/s^2
    * @param [in] vMax Maksymalne ograniczenie prędkości kątowej, domyślnie 180°/s
    * @param [in] type Zablokowanie kierunku osi X (0-odniesienie do wektora wejściowego; 1-poziomo; 2-pionowo)
    * @return Kod błędu
    */
    int FocusStart(double kp, double kpredict, double aMax, double vMax, int type);

Zatrzymanie śledzenia ogniska
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Zatrzymuje śledzenie ogniska
    * @return Kod błędu
    */
    int FocusEnd();

Przykład kodu śledzenia ogniska
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4
    
.. code-block:: c#
    :linenos:

    private void button81_Click(object sender, EventArgs e)
    {
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
        robot.GetForwardKin(p1Joint,ref p1Desc);
        robot.GetForwardKin(p2Joint, ref p2Desc);
        robot.GetForwardKin(p3Joint, ref p3Desc);
        robot.GetForwardKin(p4Joint, ref p4Desc);
        robot.GetForwardKin(p5Joint, ref p5Desc);
        robot.GetForwardKin(p6Joint, ref p6Desc);
        robot.MoveJ(p1Joint, p1Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(1);
        robot.MoveJ(p2Joint, p2Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(2);
        robot.MoveJ(p3Joint, p3Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(3);
        robot.MoveJ(p4Joint, p4Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(4);
        DescPose coordRtn = new DescPose(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);
        int rtn = robot.ComputeTcp4(ref coordRtn);
        Console.WriteLine($"4 Point ComputeTool      {rtn} coord is {coordRtn.tran.x} ,{coordRtn.tran.y} ,{coordRtn.tran.z} ,{coordRtn.rpy.rx} ,{coordRtn.rpy.ry} ,{coordRtn.rpy.rz} ");
        robot.SetToolCoord(1, coordRtn, 0, 0, 1, 0);
        robot.GetForwardKin(p1Joint, ref p1Desc);
        robot.GetForwardKin(p2Joint, ref p2Desc);
        robot.GetForwardKin(p3Joint, ref p3Desc);
        robot.SetFocusCalibPoint(1, p1Desc);
        robot.SetFocusCalibPoint(2, p2Desc);
        robot.SetFocusCalibPoint(3, p3Desc);
        DescTran resultPos = new DescTran(0.0, 0.0, 0.0);
        double accuracy = 0.0;
        rtn = robot.ComputeFocusCalib(3, ref resultPos, ref accuracy);
        Console.WriteLine($"ComputeFocusCalib coord is  {rtn},{ resultPos.x} ,{ resultPos.y}, { resultPos.z}, accuracy is {accuracy} ");
        rtn = robot.SetFocusPosition(resultPos);
        robot.GetForwardKin(p5Joint, ref p5Desc);
        robot.GetForwardKin(p6Joint, ref p6Desc);
        robot.MoveL(p5Joint, p5Desc, 1, 0, 10, 100, 100, -1, 0, exaxisPos, 0, 1, offdese);
        robot.MoveL(p6Joint, p6Desc, 1, 0, 10, 100, 100, -1, 0, exaxisPos, 0, 1, offdese);
        robot.FocusStart(50, 19, 710, 90, 0);
        robot.MoveL(p5Joint, p5Desc, 1, 0, 10, 100, 100, -1, 0, exaxisPos, 0, 1, offdese);
        robot.MoveL(p6Joint, p6Desc, 1, 0, 10, 100, 100, -1, 0, exaxisPos, 0, 1, offdese);
        robot.FocusEnd();
    }

Włączenie funkcji kalibracji czułości czujnika momentu obrotowego stawu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Włączenie funkcji kalibracji czułości czujnika momentu obrotowego stawu
    * @param [in] status 0-wyłączone; 1-włączone
    * @return  Kod błędu
    */
    public int JointSensitivityEnable(int status);

Zbieranie danych czułości czujnika momentu obrotowego stawu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Zbieranie danych czułości czujnika momentu obrotowego stawu
    * @return Kod błędu
    */
    public int JointSensitivityCollect();

Pobranie wyniku kalibracji czułości czujnika momentu obrotowego stawu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Pobiera wynik kalibracji czułości czujnika momentu obrotowego stawu
    * @param [out] calibResult Czułość stawów j1~j6 [0-1]
    * @param [out] linearity Liniowość stawów j1~j6 [0-1]
    * @return Kod błędu
    */
    public int JointSensitivityCalibration(double calibResult[6], double linearity[6]);

Pobranie błędu histerezy czujnika momentu obrotowego stawu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Pobiera błąd histerezy czujnika momentu obrotowego stawu
    * @param [out] hysteresisError Błąd histerezy stawów j1~j6
    * @return Kod błędu
    */
    public int JointHysteresisError(ref double[] hysteresisError);
    
Pobranie powtarzalności czujnika momentu obrotowego stawu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:
    
    /**
    * @brief Pobiera powtarzalność czujnika momentu obrotowego stawu
    * @param [out] repeatability Powtarzalność czujnika momentu obrotowego stawów j1~j6
    * @return Kod błędu
    */
    public int JointRepeatability(ref double[] repeatability);
    
Ustawienie parametrów czujnika siły stawu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
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
    public int SetAdmittanceParams(double[] M, double[] B, double[] K, double[] threshold, double[] sensitivity, int setZeroFlag);

Przykład kodu automatycznej kalibracji czułości czujnika momentu obrotowego stawu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7
    
.. code-block:: c#
    :linenos:

    public int TestSensitivityCalib()
    {
        int rtn; 
        rtn = robot.JointSensitivityEnable(0);
        rtn = robot.JointSensitivityEnable(1);
        Console.WriteLine($"JointSensitivityEnable rtn is {rtn}");

        JointPos curJPos = new JointPos(0, 0, 0, 0, 0, 0);
        robot.GetActualJointPosDegree(0, ref curJPos);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        JointPos[] jointPoses = new JointPos[]
        {
            new JointPos(curJPos.jPos[0], 0, 0, -90, 0.02, curJPos.jPos[5]),
            new JointPos(curJPos.jPos[0], -30, 0, -90, 0.02, curJPos.jPos[5]),
            new JointPos(curJPos.jPos[0], -60, 0, -90, 0.02, curJPos.jPos[5]),
            new JointPos(curJPos.jPos[0], -90, 0, -90, 0.02, curJPos.jPos[5]),
            new JointPos(curJPos.jPos[0], -120, 0, -90, 0.02, curJPos.jPos[5]),
            new JointPos(curJPos.jPos[0], -150, 0, -90, 0.02, curJPos.jPos[5]),
            new JointPos(curJPos.jPos[0], -180, 0, -90, 0.02, curJPos.jPos[5])
        };
        for (int i = 0; i < jointPoses.Length; i++)
        {
            DescPose descPos = new DescPose(0, 0, 0, 0, 0, 0);
            robot.GetForwardKin(jointPoses[i], ref descPos);
            robot.MoveJ(jointPoses[i], descPos, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);

            Thread.Sleep(i == 0 ? 200 : 100);
            rtn = robot.JointSensitivityCollect();
            Console.WriteLine($"JointSensitivityCollect {i + 1} rtn is {rtn}");
            Thread.Sleep(100);
        }

        for (int i = jointPoses.Length - 2; i >= 0; i--)
        {
            DescPose descPos = new DescPose();
            robot.GetForwardKin(jointPoses[i], ref descPos);
            robot.MoveJ(jointPoses[i], descPos, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
            Thread.Sleep(100);
            rtn = robot.JointSensitivityCollect();
            Console.WriteLine($"JointSensitivityCollect {jointPoses.Length + (jointPoses.Length - 1 - i)} rtn is {rtn}");
            Thread.Sleep(100);
        }
        double[] calibResult = new double[6];
        double[] linearity = new double[6];
        rtn = robot.JointSensitivityCalibration(ref calibResult, ref linearity);
        Console.WriteLine($"JointSensitivityCalibration rtn is {rtn}");
        rtn = robot.JointSensitivityEnable(0);
        Console.WriteLine($"JointSensitivityEnable rtn is {rtn}");
        Console.WriteLine($"jointSensor Calib result is {calibResult[0]:F6} {calibResult[1]:F6} {calibResult[2]:F6} {calibResult[3]:F6} {calibResult[4]:F6} {calibResult[5]:F6}");
        Console.WriteLine($"jointSensor linearity is {linearity[0]:F6} {linearity[1]:F6} {linearity[2]:F6} {linearity[3]:F6} {linearity[4]:F6} {linearity[5]:F6}"); 
        double[] hysteresisError = new double[6];
        rtn = robot.JointHysteresisError(ref hysteresisError);
        Console.WriteLine($"JointHysteresisError result is {hysteresisError[0]:F6} {hysteresisError[1]:F6} {hysteresisError[2]:F6} {hysteresisError[3]:F6} {hysteresisError[4]:F6} {hysteresisError[5]:F6}");   
        double[] repeatability = new double[6];
        rtn = robot.JointRepeatability(ref repeatability);
        Console.WriteLine($"JointRepeatability result is {repeatability[0]:F6} {repeatability[1]:F6} {repeatability[2]:F6} {repeatability[3]:F6} {repeatability[4]:F6} {repeatability[5]:F6}");
        double[] M = new double[6] { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
        double[] B = new double[6] { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
        double[] K = new double[6] { 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 };
        double[] threshold = new double[6] { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
        int setZeroFlag = 1;
        rtn = robot.SetAdmittanceParams(M, B, K, threshold, calibResult, setZeroFlag);
        Console.WriteLine($"SetAdmittanceParams rtn is {rtn}");
        robot.CloseRPC();
        return 0;
    }

Pobranie liczby błędnych ramek dla 8 portów stacji podrzędnych robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7
    
.. code-block:: c#
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
    public int GetSlavePortErrCounter(ref int[] inRecvErr,ref int[] inCRCErr,ref int[] inTransmitErr,ref int[] inLinkErr,ref int[] outRecvErr,ref int[] outCRCErr,ref int[] outTransmitErr,ref int[] outLinkErr);

Zerowanie licznika błędnych ramek portu stacji podrzędnej
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Zeruje licznik błędnych ramek portu stacji podrzędnej
    * @param [in] slaveID Numer stacji podrzędnej 0~7
    * @return Kod błędu
    */
    public int SlavePortErrCounterClear(int slaveID);

Przykład kodu pobierania błędnych ramek portów stacji podrzędnych
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7
    
.. code-block:: c#
    :linenos:

    public void TestSlavePortErr()
    {
        int[] inRecvErr = new int[8];
        int[] inCRCErr = new int[8];
        int[] inTransmitErr = new int[8];
        int[] inLinkErr = new int[8];
        int[] outRecvErr = new int[8];
        int[] outCRCErr = new int[8];
        int[] outTransmitErr = new int[8];
        int[] outLinkErr = new int[8];

        robot.GetSlavePortErrCounter(ref inRecvErr, ref inCRCErr, ref inTransmitErr, ref inLinkErr,
            ref outRecvErr, ref outCRCErr, ref outTransmitErr, ref outLinkErr);

        for (int i = 0; i < 8; i++)
        {
            if (inRecvErr[i] != 0)
            {
                Console.WriteLine($"inRecvErr {i} is {inRecvErr[i]}");
            }

            if (inCRCErr[i] != 0)
            {
                Console.WriteLine($"inCRCErr {i} is {inCRCErr[i]}");
            }

            if (inTransmitErr[i] != 0)
            {
                Console.WriteLine($"inTransmitErr {i} is {inTransmitErr[i]}");
            }

            if (inLinkErr[i] != 0)
            {
                Console.WriteLine($"inLinkErr {i} is {inLinkErr[i]}");
            }

            if (outRecvErr[i] != 0)
            {
                Console.WriteLine($"outRecvErr {i} is {outRecvErr[i]}");
            }

            if (outCRCErr[i] != 0)
            {
                Console.WriteLine($"outCRCErr {i} is {outCRCErr[i]}");
            }

            if (outTransmitErr[i] != 0)
            {
                Console.WriteLine($"outTransmitErr {i} is {outTransmitErr[i]}");
            }

            if (outLinkErr[i] != 0)
            {
                Console.WriteLine($"outLinkErr {i} is {outLinkErr[i]}");
            }
        }
        Console.WriteLine("others has no err!");

        for (int i = 0; i < 8; i++)
        {
            robot.SlavePortErrCounterClear(i);
        }

        robot.CloseRPC();
    }

Ustawienie współczynnika sprzężenia przedniego prędkości dla każdej osi
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Ustawia współczynnik sprzężenia przedniego prędkości dla każdej osi
    * @param [in] radio Współczynnik sprzężenia przedniego prędkości dla każdej osi
    * @return Kod błędu
    */
    public int SetVelFeedForwardRatio(double radio[6]);

Pobranie współczynnika sprzężenia przedniego prędkości dla każdej osi
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Pobiera współczynnik sprzężenia przedniego prędkości dla każdej osi
    * @param [out] radio Współczynnik sprzężenia przedniego prędkości dla każdej osi
    * @return Kod błędu
    */
    public int GetVelFeedForwardRatio(ref double radio[6]);

Przykład kodu pobierania błędnych ramek portów stacji podrzędnych
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7
    
.. code-block:: c#
    :linenos:

    public void TestVelFeedForwardRatio()
    {

        double[] setRadio = new double[6] { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
        robot.SetVelFeedForwardRatio(setRadio);
        double[] getRadio = new double[6] { 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 };
        robot.GetVelFeedForwardRatio(ref getRadio);
        Console.WriteLine($" {getRadio[0]:F6} {getRadio[1]:F6} {getRadio[2]:F6} {getRadio[3]:F6} {getRadio[4]:F6} {getRadio[5]:F6}");
    }

Kalibracja TCP czujnika fotoelektrycznego - obliczenie RPY narzędzia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Kalibracja TCP czujnika fotoelektrycznego - obliczenie RPY narzędzia
    * @param [in] Btool Pozycja kartezjańska robota
    * @param [in] Etool Bieżące wartości układu współrzędnych narzędzia
    * @param [in] sensor Bieżące wartości układu współrzędnych czujnika (jeszcze nieudostępnione)
    * @param [in] radius Promień ruchu po okręgu mm (jeszcze nieudostępnione)
    * @param [in] dz Odległość ruchu wzdłuż ujemnego kierunku osi Z podstawowego układu współrzędnych; gdy dz = 10000, funkcja bezpośrednio zwraca RPY narzędzia
    * @param [out] TCPRPY Wartości RPY narzędzia
    * @return Kod błędu
    */
    public int TCPComputeRPY(DescPose Btool, DescPose Etool, DescPose sensor, double radius, double dz, out Rpy TCPRPY);

Kalibracja TCP czujnika fotoelektrycznego - obliczenie XYZ narzędzia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
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
    public int TCPComputeXYZ(int select, double originDirection, DescTran pos1, DescTran pos2,DescTran pos3, DescTran pos4, out DescTran TCP);

Kalibracja TCP czujnika fotoelektrycznego - rozpoczęcie rejestracji pozycji środka kołnierza końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Kalibracja TCP czujnika fotoelektrycznego - rozpoczęcie rejestracji pozycji środka kołnierza końcowego
    * @return Kod błędu
    */
    errno_t TCPRecordFlangePosStart();

Kalibracja TCP czujnika fotoelektrycznego - zatrzymanie rejestracji pozycji środka kołnierza końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Kalibracja TCP czujnika fotoelektrycznego - zatrzymanie rejestracji pozycji środka kołnierza końcowego
    * @return Kod błędu
    */
    public int TCPRecordFlangePosEnd();

Kalibracja TCP czujnika fotoelektrycznego - pobranie pozycji środka narzędzia końcowego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Kalibracja TCP czujnika fotoelektrycznego - pobranie pozycji środka narzędzia końcowego
    * @param [out] TCP Pozycja środka narzędzia (x,y,z)
    * @return Kod błędu
    */
    public int TCPGetRecordFlangePos(out DescTran TCP);

Kalibracja TCP czujnika fotoelektrycznego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Kalibracja TCP czujnika fotoelektrycznego
    * @param [in] luaPath Ścieżka programu lua automatycznej kalibracji: dla robota wersji QX - "/fruser/FR_CalibrateTheToolTcp.lua"; dla robota wersji LA - "/usr/local/etc/controller/lua/FR_CalibrateTheToolTcp.lua"
    * @param [in] offsetX Przesunięcie punktu nauczania (x,y,z) mm
    * @param [out] TCP Układ współrzędnych narzędzia po kalibracji (x,y,z,rx,ry,rz)
    * @return Kod błędu
    */
    public int PhotoelectricSensorTCPCalibration(string luaPath, DescTran offset, out DescPose TCP);

Przykład kodu kalibracji TCP czujnika fotoelektrycznego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public void TestPhotoelectricSensorTCPCalib()
    {
        ROBOT_STATE_PKG pkg =new ROBOT_STATE_PKG();
        DescTran offset = new DescTran( 10.0, 10.0, 3.0 );
        DescPose TCP = new DescPose();
        int rtn = robot.PhotoelectricSensorTCPCalibration("/fruser/FR_CalibrateTheToolTcp.lua", offset, out TCP);
        Console.WriteLine($"PhotoelectricSensorTCPCalibration : {rtn}");
        Console.WriteLine($"Współrzędne TCP narzędzia: X={TCP.tran.x:F3}, Y={TCP.tran.y:F3}, Z={TCP.tran.z:F3}");
        Console.WriteLine($"Orientacja RPY narzędzia: RX={TCP.rpy.rx:F3}, RY={TCP.rpy.ry:F3}, RZ={TCP.rpy.rz:F3}");
    }