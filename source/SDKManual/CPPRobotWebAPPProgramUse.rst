Użycie programu WebAPP robota
=============================

.. toctree::
    :maxdepth: 5

Ustawianie automatycznego ładowania domyślnego programu roboczego przy uruchomieniu
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ustawia automatyczne ładowanie domyślnego programu roboczego przy uruchomieniu
    * @param  [in] flag  0-nie ładuj automatycznie domyślnego programu przy uruchomieniu, 1-ładuj automatycznie domyślny program przy uruchomieniu
    * @param  [in] program_name Nazwa i ścieżka programu roboczego, np. "/fruser/movej.lua", gdzie "/fruser/" to stała ścieżka dla QX, "/usr/local/etc/controller/lua/" to stała ścieżka dla LA
    * @return  Kod błędu
    */
    errno_t  LoadDefaultProgConfig(uint8_t flag, char program_name[64]);

Ładowanie określonego programu roboczego
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ładuje określony program roboczy
    * @param  [in] program_name Nazwa i ścieżka programu roboczego, np. "/fruser/movej.lua", gdzie "/fruser/" to stała ścieżka dla QX, "/usr/local/etc/controller/lua/" to stała ścieżka dla LA
    * @return  Kod błędu
    */
    errno_t  ProgramLoad(char program_name[64]);

Pobieranie nazwy załadowanego programu roboczego
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Pobiera nazwę załadowanego programu roboczego
    * @param  [out] program_name Nazwa i ścieżka programu roboczego, np. "/fruser/movej.lua", gdzie "/fruser/" to stała ścieżka dla QX, "/usr/local/etc/controller/lua/" to stała ścieżka dla LA
    * @return  Kod błędu
    */
    errno_t  GetLoadedProgram(char program_name[64]);

Pobieranie numeru linii wykonywanego programu roboczego robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Pobiera numer linii wykonywanego programu roboczego robota
    * @param  [out] line  Numer linii
    * @return  Kod błędu
    */
    errno_t  GetCurrentLine(int *line);

Uruchamianie aktualnie załadowanego programu roboczego
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Uruchamia aktualnie załadowany program roboczy
    * @return  Kod błędu
    */
    errno_t  ProgramRun();

Wstrzymywanie aktualnie uruchomionego programu roboczego
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Wstrzymuje aktualnie uruchomiony program roboczy
    * @return  Kod błędu
    */
    errno_t  ProgramPause();

Wznawianie aktualnie wstrzymanego programu roboczego
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Wznawia aktualnie wstrzymany program roboczy
    * @return  Kod błędu
    */
    errno_t  ProgramResume();

Zatrzymywanie aktualnie uruchomionego programu roboczego
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Zatrzymuje aktualnie uruchomiony program roboczy
    * @return  Kod błędu
    */
    errno_t  ProgramStop();

Pobieranie stanu wykonania programu roboczego robota
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Pobiera stan wykonania programu roboczego robota
    * @param  [out]  state 1-program zatrzymany lub brak uruchomionego programu, 2-program w trakcie wykonywania, 3-program wstrzymany
    * @return  Kod błędu
    */
    errno_t  GetProgramState(uint8_t *state);

Przykład kodu operacji na programie LUA robota
++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestLuaOp(void)
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
      char program_name[64] = "/fruser/test.lua";
      char loaded_name[64] = "";
      uint8_t state;
      int line;
      robot.Mode(0);
      robot.LoadDefaultProgConfig(0, program_name);
      robot.ProgramLoad(program_name);
      robot.ProgramRun();
      robot.Sleep(1000);
      robot.ProgramPause();
      robot.GetProgramState(&state);
      printf("program state:%u\n", state);
      robot.GetCurrentLine(&line);
      printf("current line:%d\n", line);
      robot.GetLoadedProgram(loaded_name);
      printf("program name:%s\n", loaded_name);
      robot.Sleep(1000);
      robot.ProgramResume();
      robot.Sleep(1000);
      robot.ProgramStop();
      robot.Sleep(1000);
      robot.CloseRPC();
      return 0;
    }

Pobieranie pliku Lua
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.2.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera plik Lua
    * @param [in] fileName Nazwa pliku lua do pobrania, np.: "test.lua"
    * @param [in] savePath Lokalna ścieżka zapisu pliku, np.: "D://Down/"
    * @return Kod błędu
    */
    errno_t LuaDownLoad(std::string fileName, std::string savePath);

Usuwanie pliku Lua
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.2.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Usuwa plik Lua
    * @param [in] fileName Nazwa pliku lua do usunięcia, np.: "test.lua"
    * @return Kod błędu
    */
    errno_t LuaDelete(std::string fileName);

Pobieranie listy wszystkich bieżących nazw plików Lua
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.2.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Pobiera listę wszystkich bieżących nazw plików Lua
    * @param [out] luaNames Lista nazw plików lua
    * @return Kod błędu
    */
    errno_t GetLuaList(std::list<std::string>* luaNames);

Przesyłanie pliku Lua
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.2.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Przesyła plik Lua
    * @param [in] filePath Ścieżka lokalnego pliku lua
    * @return Kod błędu
    */
    errno_t LuaUpload(std::string filePath);

Przykład kodu przesyłania i pobierania pliku LUA robota
+++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestLUAUpDownLoad(void)
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
      list<std::string> luaNames;
      rtn = robot.GetLuaList(&luaNames);
      std::cout << "res is: " << rtn << std::endl;
      std::cout << "size is: " << luaNames.size() << std::endl;
      for (auto it = luaNames.begin(); it != luaNames.end(); it++)
      {
        std::cout << it->c_str() << std::endl;
      }
      rtn = robot.LuaDownLoad("test.lua", "D://zDOWN/");
      printf("LuaDownLoad rtn is %d\n", rtn);
      rtn = robot.LuaUpload("D://zUP/airlab.lua");
      printf("LuaUpload rtn is %d\n", rtn);
      rtn = robot.LuaDelete("test.lua");
      printf("LuaDelete rtn is %d\n", rtn);
      robot.CloseRPC();
      return 0;
    }