Używanie programu WebAPP robota
===============================

.. toctree:: 
    :maxdepth: 5

Ustawienie automatycznego ładowania domyślnego programu roboczego przy starcie
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ustawia automatyczne ładowanie domyślnego programu roboczego przy starcie
    * @param  [in] flag  0-nie ładuj automatycznie domyślnego programu przy starcie, 1-ładuj automatycznie domyślny program przy starcie
    * @param  [in] program_name Nazwa i ścieżka programu roboczego, np. "/fruser/movej.lua", gdzie "/fruser/" to stała ścieżka dla QX, a "/usr/local/etc/controller/lua/" to stała ścieżka dla LA
    * @return  Kod błędu
    */
    int LoadDefaultProgConfig(byte flag, string program_name); 

Ładowanie określonego programu roboczego
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ładuje określony program roboczy
    * @param  [in] program_name Nazwa i ścieżka programu roboczego, np. "/fruser/movej.lua", gdzie "/fruser/" to stała ścieżka dla QX, a "/usr/local/etc/controller/lua/" to stała ścieżka dla LA
    * @return  Kod błędu
    */
    int ProgramLoad(string program_name); 

Pobranie nazwy załadowanego programu roboczego
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera nazwę załadowanego programu roboczego
    * @param  [out] program_name Nazwa i ścieżka programu roboczego, np. "/fruser/movej.lua", gdzie "/fruser/" to stała ścieżka dla QX, a "/usr/local/etc/controller/lua/" to stała ścieżka dla LA
    * @return  Kod błędu
    */
    int GetLoadedProgram(ref string program_name); 

Pobranie bieżącego numeru linii wykonywanego programu roboczego robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera bieżący numer linii wykonywanego programu roboczego robota
    * @param  [out] line  Numer linii
    * @return  Kod błędu
    */   
    int GetCurrentLine(ref int line);

Uruchomienie aktualnie załadowanego programu roboczego
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Uruchamia aktualnie załadowany program roboczy
    * @return  Kod błędu
    */
    int ProgramRun();

Wstrzymanie aktualnie działającego programu roboczego
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Wstrzymuje aktualnie działający program roboczy
    * @return  Kod błędu
    */ 
    int ProgramPause();

Wznowienie aktualnie wstrzymanego programu roboczego
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Wznawia aktualnie wstrzymany program roboczy
    * @return  Kod błędu
    */ 
    int ProgramResume(); 

Zatrzymanie aktualnie działającego programu roboczego
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Zatrzymuje aktualnie działający program roboczy
    * @return  Kod błędu
    */ 
    int ProgramStop();   

Pobranie stanu wykonania programu roboczego robota
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pobiera stan wykonania programu roboczego robota
    * @param  [out]  state 1-program zatrzymany lub brak działającego programu, 2-program działa, 3-program wstrzymany
    * @return  Kod błędu
    */
    int GetProgramState(ref byte state);

Przykład kodu operacji na programie LUA robota
++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnWebApp_Click(object sender, EventArgs e)
    {
        string program_name = "/fruser/Text1.lua";
        string loaded_name = "";
        byte state=0;
        int line=0;

        robot.Mode(0);
        robot.LoadDefaultProgConfig(0, program_name);
        robot.ProgramLoad(program_name);
        robot.ProgramRun();
        Thread.Sleep(1000);
        robot.ProgramPause();
        robot.GetProgramState(ref state);
        Console.WriteLine("program state:{0}\n", state);
        robot.GetCurrentLine(ref line);
        Console.WriteLine("current line:{0}\n", line);
        robot.GetLoadedProgram(ref loaded_name);
        Console.WriteLine("program name:{0}\n", loaded_name);
        Thread.Sleep(1000);
        robot.ProgramResume();
        Thread.Sleep(1000);
        robot.ProgramStop();
        Thread.Sleep(1000);
    }

Pobranie pliku Lua
++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.5

.. code-block:: c#
    :linenos:

    /** 
    * @brief Pobiera plik Lua
    * @param [in] fileName Program roboczy do pobrania "test.lua" lub "test.tar.gz"
    * @param [in] savePath Lokalna ścieżka zapisu programu roboczego "D://Down/"
    * @return Kod błędu 
    */
    public int LuaDownLoad(string fileName, string savePath);

Przesłanie pliku Lua
++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.5

.. code-block:: c#
    :linenos:

    /** 
    * @brief Przesyła plik Lua
    * @param [in] filePath Lokalna ścieżka programu roboczego ".../test.lua" lub ".../test.tar.gz"
    * @param [out] errStr Informacja o błędzie
    * @return Kod błędu 
    */
    public int LuaUpload(string filePath, ref string errStr);

Usunięcie pliku Lua
++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.5

.. code-block:: c#
    :linenos:

    /** 
    * @brief Usuwa plik Lua
    * @param [in] fileName Nazwa programu roboczego do usunięcia "test.lua"
    * @return Kod błędu 
    */
    public int LuaDelete(string fileName);

Pobranie listy wszystkich bieżących nazw plików Lua
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.5

.. code-block:: c#
    :linenos:

    /** 
    * @brief Pobiera listę wszystkich bieżących nazw plików Lua
    * @param [out] luaNames Lista nazw programów roboczych
    * @return Kod błędu 
    */
    public int GetLuaList(ref List<string> luaNames) ;

Przykład kodu przesyłania i pobierania pliku Lua robota
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.5

.. code-block:: c#
    :linenos:

    private void btnUploadLua_Click(object sender, EventArgs e)
    {
        int rtn;
        List<string> luaNames = new List<string>();
        rtn = robot.GetLuaList(ref luaNames);
        Console.WriteLine("res is: {0}", rtn);
        Console.WriteLine("size is: {0}", luaNames.Count);
        foreach (var name in luaNames)
        {
        Console.WriteLine(name);
        }
        rtn = robot.LuaDownLoad("TT.lua", "D://zDOWN/");
        Console.WriteLine("LuaDownLoad rtn is {0}", rtn);
        string errStr = "";
        Thread.Sleep(2000);

        rtn = robot.LuaUpload("D://zUP/airlab.lua", ref errStr);
        Console.WriteLine("LuaUpload rtn is {0}", errStr);
        Thread.Sleep(2000);
        rtn = robot.LuaDelete("TT.lua");
        Console.WriteLine("LuaDelete rtn is {0}", rtn);
    }