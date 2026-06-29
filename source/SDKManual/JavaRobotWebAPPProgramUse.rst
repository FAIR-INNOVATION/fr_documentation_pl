Użytkowanie programu WebAPP robota
==================================

.. toctree:: 
    :maxdepth: 5

Ustawianie automatycznego ładowania domyślnego programu roboczego przy starcie
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Ustawianie automatycznego ładowania domyślnego programu roboczego przy starcie
    * @param  [in] flag  0-nie ładuj automatycznie domyślnego programu przy starcie, 1-ładuj automatycznie domyślny program przy starcie
    * @param  [in] program_name Nazwa i ścieżka programu roboczego, np. "/fruser/movej.lua", gdzie "/fruser/" to stała ścieżka dla QX, "/usr/local/etc/controller/lua/" to stała ścieżka dla LA
    * @return  Kod błędu
    */
    int LoadDefaultProgConfig(int flag, String program_name); 

Ładowanie określonego programu roboczego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Ładowanie określonego programu roboczego
    * @param  [in] program_name Nazwa i ścieżka programu roboczego, np. "/fruser/movej.lua", gdzie "/fruser/" to stała ścieżka dla QX, "/usr/local/etc/controller/lua/" to stała ścieżka dla LA
    * @return  Kod błędu
    */
    int ProgramLoad(String program_name); 

Pobieranie nazwy załadowanego programu roboczego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Pobieranie nazwy załadowanego programu roboczego
    * @param  [out] program_name program_name[0]: nazwa i ścieżka programu roboczego, np. "/fruser/movej.lua", gdzie "/fruser/" to stała ścieżka dla QX, "/usr/local/etc/controller/lua/" to stała ścieżka dla LA
    * @return  Kod błędu
    */
    int GetLoadedProgram(String[] program_name); 

Pobieranie bieżącego numeru linii wykonania programu roboczego robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Pobieranie bieżącego numeru linii wykonania programu roboczego robota
    * @param  [out] List[0]: kod błędu; List[1]: int line numer linii
    * @return  Kod błędu
    */   
    List<Integer> GetCurrentLine();

Uruchamianie bieżącego załadowanego programu roboczego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Uruchamianie bieżącego załadowanego programu roboczego
    * @return  Kod błędu
    */
    int ProgramRun();

Wstrzymywanie bieżącego uruchomionego programu roboczego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Wstrzymywanie bieżącego uruchomionego programu roboczego
    * @return  Kod błędu
    */ 
    int PauseMotion();

Wznawianie bieżącego wstrzymanego programu roboczego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Wznawianie bieżącego wstrzymanego programu roboczego
    * @return  Kod błędu
    */ 
    int ResumeMotion(); 

Zatrzymywanie bieżącego uruchomionego programu roboczego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Zatrzymywanie bieżącego uruchomionego programu roboczego
    * @return  Kod błędu
    */ 
    int StopMotion();   

Pobieranie stanu wykonania programu roboczego robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief  Pobieranie stanu wykonania programu roboczego robota
    * @param   [out] state 1-program zatrzymany lub brak uruchomionego programu, 2-program działa, 3-program wstrzymany
    * @return  Kod błędu
    */
    public int GetProgramState(int[] state)

Przykład kodu operacji na programie LUA robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestLuaOp(Robot robot)
    {
        String program_name = "Text1.lua";
        String[] loaded_name = new String[]{""};
        int[] state=new int[]{0};
        List<Integer> line=new ArrayList<>();

        robot.Mode(0);
        robot.LoadDefaultProgConfig(0, program_name);
        robot.ProgramLoad(program_name);
        robot.ProgramRun();
        robot.Sleep(1000);
        robot.ProgramPause();
        robot.GetProgramState(state);
        System.out.println("program state:"+ state[0]);
        line=robot.GetCurrentLine();
        System.out.println("current line:"+ line);
        robot.GetLoadedProgram(loaded_name);
        System.out.println("program name:"+ loaded_name[0]);
        robot.Sleep(1000);
        robot.ProgramResume();
        robot.Sleep(1000);
        robot.ProgramStop();
        robot.Sleep(1000);

        robot.CloseRPC();
        return 0;
    }

Pobieranie programu LUA
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Pobieranie programu roboczego
    * @param [in] fileName Nazwa pliku lua do pobrania "test.lua" lub "test.tar.gz"
    * @param [in] savePath Lokalna ścieżka zapisu pliku "D://Down/"
    * @return Kod błędu 
    */
    int LuaDownLoad(String fileName, String savePath);

Usuwanie programu LUA
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Usuwanie programu roboczego
    * @param [in] fileName Nazwa programu roboczego do usunięcia "test.lua"
    * @return Kod błędu 
    */
    int LuaDelete(String fileName);

Pobieranie nazw wszystkich bieżących plików lua
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Pobieranie nazw wszystkich bieżących plików lua
    * @param [out] luaNames Lista nazw programów roboczych
    * @return Kod błędu 
    */
    int GetLuaList(List<String> luaNames);

Przesyłanie programu LUA
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /** 
    * @brief Przesyłanie programu roboczego
    * @param [in] filePath Lokalna ścieżka pliku lua ".../test.lua" lub ".../test.tar.gz"
    * @param [out] errStr Informacja o błędzie
    * @return Kod błędu 
    */
    int LuaUpload(String filePath, String errStr);

Przykład kodu przesyłania i pobierania pliku LUA robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestLUAUpDownLoad(Robot robot)
    {
        List<String> luaNames=new ArrayList<>();
        int rtn = robot.GetLuaList(luaNames);
        System.out.println("res is: "+rtn);
        System.out.println("size is: "+luaNames.size());
        for (int it =1; it < luaNames.size(); it++)
        {
            System.out.println(luaNames.get(it));
        }

        rtn = robot.LuaDownLoad("test.lua", "D://zDOWN/");
        System.out.println("LuaDownLoad rtn is:"+rtn);

        rtn = robot.LuaUpload("D://zUP/XG.lua","");
        System.out.println("LuaUpload rtn is:"+ rtn);

        rtn = robot.LuaDelete("XG.lua");
        System.out.println("LuaDelete rtn is:"+ rtn);

        return 0;
    }