Opis API
=========================

.. toctree:: 
   :maxdepth: 6

Instrukcje act
--------------

Wszystkie poniższe instrukcje act używają metody POST, a URL to /action/act.

Zapisz punkt uczenia
++++++++++++++++++++

Nazwa instrukcji: save_point.

Parametry instrukcji:

.. code-block:: c++
    :linenos:

    /** 
    * @param string name Nazwa zapisywanego punktu uczenia
    * @param string speed Prędkość
    * @param string elbow_speed Prędkość łokcia
    * @param string acc Przyspieszenie
    * @param string elbow_acc Przyspieszenie łokcia
    * @param string toolnum Numer narzędzia
    * @param string workpiecenum Numer przedmiotu
    */ 

Przykład instrukcji:

.. code-block:: c++
    :linenos:

    {
        cmd: "save_point",
        data:{
            name: "point1",
            speed: "100",
            elbow_speed: "100",
            acc: "100",
            elbow_acc: "100",
            toolnum: "1",
            workpiecenum: "1"
        }
    }

Informacja zwrotna instrukcji:

.. code-block:: c++
    :linenos:

    /** 
    * @return status:200 "success"
    * @return status:404 "fail"
    */ 

Instrukcje sta
--------------

Wszystkie poniższe instrukcje sta używają metody POST, a URL to /action/sta.

Pobierz dane stanu robota
+++++++++++++++++++++++++

Nazwa instrukcji: basic.

Parametry instrukcji: brak.

Przykład instrukcji:

.. code-block:: c++
    :linenos:

    {
        cmd: "basic",
    }

Informacja zwrotna instrukcji:

.. code-block:: c++
    :linenos:

    /** 
    * @return status:200 
    * @param object joints Pozycje stawów
    * @param object tcp Pozycja i orientacja kartezjańska
    * @param array exAxisPos Pozycja zewnętrznej osi
    * @return status:404 "fail"
    */
    {
        joints: {
            j1: "90",
            j2: "90",
            j3: "90",
            j4: "90",
            j5: "90",
            j6: "90",
        },
        tcp: {
            x: "100",
            x: "100",
            z: "100",
            rx: "90",
            ry: "90",
            rz: "90",
        },
        exAxisPos: [0,0,0,0]
    }

Instrukcje get
--------------

Wszystkie poniższe instrukcje get używają metody POST, a URL to /action/get.

Pobierz punkty uczenia
++++++++++++++++++++++

Nazwa instrukcji: get_points().

Parametry instrukcji: brak.

Przykład instrukcji:

.. code-block:: c++
    :linenos:

    {
        cmd: "get_points"
    }

Informacja zwrotna instrukcji:

.. code-block:: c++
    :linenos:

    /** 
    * @return status:200 "success"
    * @param ${point_name}: object Informacje o punkcie uczenia
    * @return status:404 "fail"
    */ 

Przykład informacji zwrotnej instrukcji:

.. code-block:: c++
    :linenos:

    {
        "localpoint1": {
            "name":"localpoint1",
            "elbow_speed":"1",
            "elbow_acc":"1",
            "x": "1",
            "y": "1",
            "z": "1",
            "rx": "1",
            "ry": "1",
            "rz": "1",
            "j1": "1",
            "j2": "1",
            "j3": "1",
            "j4": "1",
            "j5": "1",
            "j6": "1",
            "toolnum": "1",
            "workpiecenum": "1",
            "speed": "1",
            "acc": "1",
            "E1": "1",
            "E2: "1",
            "E3": "1",
            "E4": "1"
        }
    }

Pobierz konfigurację systemu
++++++++++++++++++++++++++++

Nazwa instrukcji: get_syscfg().

Parametry instrukcji: brak.

Przykład instrukcji:

.. code-block:: c++
    :linenos:

    {
        cmd: "get_syscfg"
    }

Informacja zwrotna instrukcji:

.. code-block:: c++
    :linenos:

    /** 
    * @return status:200 "success"
    * @param string log_count Maksymalna liczba dni przechowywania logów
    * @param string language Aktualnie używany pakiet językowy
    * @param string lifespan Czas przekroczenia limitu
    * * @return status:404 "fail"
    */ 

Przykład informacji zwrotnej instrukcji:

.. code-block:: c++
    :linenos:

    {
        log_count:"10",
        language:"zh",
        lifespan:"1800"
    }

Instrukcje set
--------------

Wszystkie poniższe instrukcje set używają metody POST, a URL to /action/set.

Instrukcja ustawiania zmiennych systemowych
+++++++++++++++++++++++++++++++++++++++++++

Nazwa instrukcji: 511.

Parametry instrukcji:

.. code-block:: c++
    :linenos:

    /** 
    * @param int index Numer zmiennej systemowej: 1-20 
    * @param int value Wartość zmiennej systemowej 
    */ 

Przykład instrukcji:

.. code-block:: c++
    :linenos:

    {
        cmd: 511,
        data:{
            content:"SetSysVarValue(2,1)"
        }
    }

Informacja zwrotna instrukcji:

.. code-block:: c++
    :linenos:

    /** 
    * @return status:200 1: sukces, 0: porażka
    * @return status:404 "fail"
    */ 

Przykład informacji zwrotnej instrukcji:

.. code-block:: c++
    :linenos:

    1

Instrukcja pobierania zmiennych systemowych
+++++++++++++++++++++++++++++++++++++++++++

Nazwa instrukcji: 512.

Parametry instrukcji:

.. code-block:: c++
    :linenos:

    /** 
    * @param int index Numer zmiennej systemowej: 1-20 
    * /

Przykład instrukcji:

.. code-block:: c++
    :linenos:

    {
        cmd: 512,
        data:{
            content:"GetSysVarValue(2)"
        }
    }

Informacja zwrotna instrukcji:

.. code-block:: c++
    :linenos:

    /** 
    * @return status:200
    * @param int value Wartość zmiennej systemowej 
    * @return status:404 "fail"
    * /

Przykład informacji zwrotnej instrukcji:

.. code-block:: c++
    :linenos:

    1

Instrukcje better-sqlite3
--------------------------

Zapytanie o pierwszy wiersz w bazie danych
++++++++++++++++++++++++++++++++++++++++++

Parametry instrukcji:

.. code-block:: c++
    :linenos:

    /**
    * @param string db_name Nazwa bazy danych (zawierająca ścieżkę bezwzględną) 
    * @param string sql Instrukcja SQL
    * @return string result Znaleziony pierwszy wiersz
    */

Treść instrukcji:

.. code-block:: c++
    :linenos:

    queryget(string db_name, string sql);

Zapytanie o wszystkie rekordy w bazie danych
++++++++++++++++++++++++++++++++++++++++++++

Parametry instrukcji:

.. code-block:: c++
    :linenos:

    /**
    * @param string db_name Nazwa bazy danych (zawierająca ścieżkę bezwzględną)
    * @param string sql Instrukcja SQL
    * @return string result Wszystkie znalezione rekordy
    */

Treść instrukcji:

.. code-block:: c++
    :linenos:

    queryall(string db_name, string sql);

Wykonanie instrukcji bazy danych
++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @param string db_name Nazwa bazy danych (zawierająca ścieżkę bezwzględną)
    * @param string sql Instrukcja SQL
    * @param object obj Parametry wymagane do wykonania instrukcji SQL
    * @return \
    */

Parametry instrukcji:

.. code-block:: c++
    :linenos:

    exec(string db_name, string sql, object obj);

Treść instrukcji:

Instrukcje socket
-----------------

socket send
++++++++++++++++++++++

Parametry instrukcji:

.. code-block:: c++
    :linenos:

    /**
    * @param string send_content Treść wysyłana w komunikacji socket
    * @return \
    */

Treść instrukcji:

.. code-block:: c++
    :linenos:

    socket_cmd.send(string send_content);//8065
    socket_file.send(string send_content);//8067

socket recv
+++++++++++++++++++++

Parametry instrukcji:

.. code-block:: c++
    :linenos:

    /**
    * @return string recv_content Treść odpowiedzi komunikacji socket
    */

Treść instrukcji:

.. code-block:: c++
    :linenos:

    socket_cmd.recv();//8065
    socket_file.recv();//8067

Instrukcje operacji na plikach
------------------------------

Zapis treści do pliku
++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @param String filename Ścieżka pliku
    * @param string content Treść do zapisania
    * @return true/false
    */

    write(filename, content);

Odczyt treści pliku
++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @param String filename Ścieżka pliku
    * @param string content Treść do zapisania
    * @return String Treść pliku
    */

    read(filename);

Modyfikacja uprawnień pliku
++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:
    
    /**
    * @param String filename Ścieżka pliku
    * @param Number mode Tryb uprawnień (np. 0644)
    * @return true/false
    */

    chmod(filename, mode);

Odczyt zawartości katalogu, w tym podkatalogów
+++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:
    
    /**
    * @param String path Ścieżka pliku
    * @return Array Tablica nazw plików
    */

    readdir(path);

Instrukcje kompresji i dekompresji
----------------------------------

.. note:: 
    Rozróżnienie między wersją LA a QX:

    Import modułu LA: var execSync = require('child_process').execSync;

    Import modułu QX: var tar_utils = require('/usr/local/etc/node/sys/tools/tar_utils');

Utworzenie skompresowanego pliku tar.gz
++++++++++++++++++++++++++++++++++++++++

Przykład utworzenia skompresowanego pliku tar.gz (LA):

.. code-block:: javascript
    :linenos:
    
    var cmd = 'cd / && tar -zcvf ' + FILENAME + '-C ' + DIR;
    execSync(cmd);
    
Opis instrukcji tworzenia skompresowanego pliku tar.gz (QX):

.. code-block:: c++
    :linenos:
    
    /**
    * @param {Array|String} sourcePaths Tablica ścieżek źródłowych plików/katalogów lub pojedyncza ścieżka
    * @param String targetFile Ścieżka docelowego pliku kompresji
    * @param Function callback Funkcja zwrotna, parametr (error) 
    * @param String basePath Ścieżka podstawowa, domyślnie '/'
    * @return \
    */

    createTarGz(sourcePaths, targetFile, callback, basePath);

Dekompresja pliku tar.gz
++++++++++++++++++++++++++++++++

Przykład dekompresji pliku tar.gz (LA):

.. code-block:: javascript
    :linenos:

    var cmd = 'cd / && tar -zxvf ' + FILENAME;
    execSync(cmd);

Opis instrukcji dekompresji pliku tar.gz (QX):

.. code-block:: c++
    :linenos:
    
    /**
    * @param String sourceFile Ścieżka źródłowego pliku kompresji
    * @param String targetDir Docelowy katalog dekompresji
    * @param Function callback Funkcja zwrotna, parametr (error) 
    * @return \
    */
    extractTarGz(sourceFile, targetDir, callback);