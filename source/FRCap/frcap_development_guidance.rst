Przewodnik programisty
======================

.. toctree:: 
   :maxdepth: 6

Środowisko programistyczne i wymagania
--------------------------------------

Środowisko programistyczne musi spełniać co najmniej następującą konfigurację:

- CPU: 1,6 GHz lub szybszy procesor.
- RAM: >= 1 GB (zalecane 2 GB lub więcej).
- ROM: >= 128 GB.
- System operacyjny: Wymagany system Windows 10 lub nowszy, macOS 10.15 lub nowszy, Linux (x64) (Ubuntu, Debian itp.).
- Wersja kontrolera: Sprawdź w WebApp w sekcji „Ustawienia systemowe - Informacje”. W środowisku programistycznym należy rozróżnić QX i LA. W przykładach instrukcji dla środowiska QX należy unikać używania składni ES6+ i innych nowoczesnych funkcji JavaScript.

Zapewniliśmy już kilka interfejsów i modułów, ale aby osiągnąć dobry efekt programistyczny, zaleca się posiadanie pewnej wiedzy na temat rozwoju aplikacji internetowych, najlepiej znajomość następujących technologii:

- HTML, JavaScript/TypeScript, CSS.
- Vue3.
- Vite.
- Node.js.

Narzędzia programistyczne
-------------------------

Zalecamy używanie najnowszego oprogramowania Visual Studio Code (VSCode) do programowania. Aby pobrać, odwiedź oficjalną stronę pobierania VSCode i wybierz odpowiedni system.

Jednocześnie na komputerze lokalnym musi być zainstalowane środowisko uruchomieniowe Node.js. Instalacja Node.js automatycznie instaluje narzędzia takie jak npm, ułatwiając zarządzanie pakietami. Odwiedź oficjalną stronę pobierania Node.js i wybierz wersję v20 dla odpowiedniego systemu.

Podczas programowania w VSCode mogą być również używane następujące wtyczki VSCode, które można zainstalować i skonfigurować według potrzeb.

- Vue.
- ESlint.
- npm Intellisense.
- Vue Language Features (Volar).
- TypeScript Vue Plugin (Volar) lub Vue.volar.
- Tailwind CSS IntelliSense.

Struktura projektu FRCap
------------------------

Struktura plików projektu FRCap:

.. image:: frcap_pictures/012.png
   :width: 3in
   :align: center

.. centered:: Wykres 5-1 Struktura projektu FRCap

- Public:

Folder zasobów publicznych. Podczas procesu budowania pliki wewnątrz nie są przetwarzane, ale kopiowane w całości do katalogu budowania.

Wewnątrz domyślnie znajduje się folder action i logo.svg.

Folder action jest przeznaczony do przechowywania plików logiki backendu interfejsów niestandardowych instrukcji.

Logo.svg to ikona wtyczki.

- Src:

Folder Assets służy głównie do przechowywania zasobów statycznych.

Folder Components służy głównie do przechowywania komponentów.

Folder Utils służy głównie do przechowywania klas narzędziowych.

Kod strony głównej App.vue.

Main.js odpowiada głównie za globalne wprowadzanie zasobów, tworzenie frameworka Vue itp.

Podstawowy plik stylów projektu Style.css.

- Build.bat: Skrypt budowania dla platformy Windows.
- Index.html: Główna struktura interfejsu użytkownika strony.
- Package.json: Plik opisu pakietu i strategie kompilacji.
- Vite.config.js: Plik konfiguracyjny Vite.

Korzystanie z frcap-ui i frcap-api na froncie
----------------------------------------------

Frcap-ui dostarcza kilka kontrolek HTML opakowanych w komponenty Vue, które można zaimportować do projektu w celu użycia, zmniejszając trudność tworzenia interfejsu użytkownika i ilość kodu, zwiększając czytelność kodu. Oczywiście można również wybrać niektóre doskonałe biblioteki komponentów UI typu open source, takie jak Element plus.

Najpierw otwórz terminal w ścieżce projektu i zainstaluj frcap-ui.

.. code-block:: c++
   :linenos:

   npm install frcap-ui -s

Po pomyślnej instalacji zaimportuj frcap-ui do komponentu, który go potrzebuje. Na przykładzie kontrolki przycisku.

.. code-block:: javascript
   :linenos:

   import { AppButton } from 'frcap-ui'

Następnie użyj go w elemencie <template> komponentu.

.. code-block:: c++
   :linenos:

   <AppButton button-text="Start" button-type="primary"></AppButton>

Wyświetl podgląd efektu projektu w przeglądarce.

.. image:: frcap_pictures/009.png
   :width: 6in
   :align: center

.. centered:: Wykres 5-2 Efekt AppButton

Obecnie udostępniamy 4 typowe komponenty kontrolek.

- AppButton: Komponent przycisku.
  
  - buttonType: Typ przycisku, String, odpowiada różnym stylom przycisku. Domyślnie primary.
  
    - primary: Niebieski.
    - secondery: Szary.
    - safety: Zielony.
    - warning: Żółty.
    - serious: Czerwony.
  
  - buttonText: Tekst przycisku, String. Domyślnie „primary”.

- AppInput: Komponent wejściowy.
  
  - Type: Wymagany, String. Domyślnie text. Określa typ pola wejściowego.
  
    - Number: Pole wejściowe liczby.
    - Text: Pole wejściowe tekstu.
  
  - inputLabel: Wymagany, String. Tekst etykiety pola wejściowego.
  - inputUnit: String. Tekst jednostki pola wejściowego.
  - hasUnit: Boolean. Domyślnie false. Wskazuje, czy potrzebny jest tekst jednostki.
  - isEmptyErr: Boolean. Czy pole wejściowe jest puste.
  - isReadonly: Boolean. Czy pole wejściowe jest tylko do odczytu.

- AppSelect: Komponent pola wyboru.
  
  - selectionLabel: Wymagany, String. Tekst etykiety pola wyboru.
  - optionsData: Wymagany, Array. Dane opcji.

- Modal: Komponent okna modalnego.
  
  - show: Boolean. Czy okno modalne jest wyświetlane.
  - title: String. Tytuł okna modalnego.

Aby ułatwić tworzenie niestandardowych instrukcji w FRCap, wbudowaliśmy już żądania HTTP i API w początkowy projekt FRCap pobrany za pomocą „Kreatora tworzenia”. W ten sposób zarówno niestandardowe instrukcje, jak i domyślnie dostarczone instrukcje można umieścić w pliku api.js w frcap-api. Konkretna ścieżka do api.js to „./src/api/api.js”.

Użycie frcap-api jest podobne do frcap-ui, szczegółowo poniżej:

1. Zaimportuj api w pliku komponentu lub innym pliku, który go potrzebuje.

.. code-block:: javascript
   :linenos:

   import api from '@/api/api';

2. Wywołaj domyślnie dostarczone instrukcje w interfejsie.

.. code-block:: c++
   :linenos:

   api.getRobotStatus()

3. Napisz logikę przetwarzania w zwróconym obietnicy (promise).

.. code-block:: c++
   :linenos:

    api.getRobotStatus()
    .then((res) => {
        console.log(res.data);
    })
    .catch((err) => {
        console.error(err);
    });

Programowanie niestandardowych instrukcji backendu
--------------------------------------------------

Przykład operacji na bazie danych (LA)
++++++++++++++++++++++++++++++++++++++

1. Zaimportuj moduł bazy danych

.. code-block:: javascript
   :linenos:

    var node = "/usr/local/etc/node/sys"
    var Sqlite3_Action = require(node + '/better-sqlite3/better-sqlite3.js');
    var sqlite = new Sqlite3_Action();

2. Pobierz zawartość bazy danych punktów

.. code-block:: javascript
   :linenos:

    // Dopasowanie cmd
    case 'get_points':
    // Napisz instrukcję SQL, sortuj według rosnąco numerycznie + rosnąco według pierwszej litery + rosnąco według chińskiego początku, aby zwrócić dane do strony frontendowej do wyświetlenia
    var sql = "select * from points order by name ASC"; 
    var sql_data = sqlite.queryall(DB_POINTS, sql); 
    // Formatowanie danych JSON
    for (var i = 0; i < sql_data.length; i++) {
        response_data[sql_data[i].name] = sql_data[i];
    }
    // Zwróć dane JSON do frontendu
    event_socket.emit('response', res, response_status, response_data);
    break;  

Przykład operacji na bazie danych (QX)
++++++++++++++++++++++++++++++++++++++

.. note:: Wersja QX używa plików w formacie JSON do przechowywania danych.

1. Zaimportuj moduł bazy danych

.. code-block:: javascript
   :linenos:

   var node = "/usr/local/etc/node/sys"
   var sqlite_adapter = require(node + '/jsdb/sqlite_adapter');
   var db = new sqlite_adapter.Database(palletizing_db);

2. Przykład użycia bazy danych
   
.. code-block:: javascript
   :linenos:

   // Wykonaj zapytanie SELECT i pobierz wszystkie wiersze
   var rows = db.queryall('SELECT * FROM box_cfg');
   console.log('result:', rows);

   // Wykonaj zapytanie SELECT i pobierz pojedynczy wiersz
   var row = db.queryget('SELECT * FROM box_cfg WHERE flag=1');
   console.log('result:', row);

   // Wykonaj instrukcję UPDATE
   db.run('UPDATE box_cfg SET height=100 WHERE flag=1', function(err) {
      if (err) {
         console.error('Update failed:', err);
      } else {
         console.log('Update success');
      }
   });

   // Wykonaj sparametryzowane zapytanie
   var params = [100, 200, 300, 1];
   db.run('UPDATE box_cfg SET height=?, width=?, length=? WHERE flag=?', params, function(err) {
      if (err) {
         console.error('update failed:', err);
      } else {
         console.log('update success');
      }
   });

   // Zamknij połączenie z bazą danych
   db.close();

Przykład operacji komunikacji socket
++++++++++++++++++++++++++++++++++++

- Zaimportuj moduł komunikacji socket
   
.. code-block:: javascript
   :linenos:

    var node = "/usr/local/etc/node/sys"
    var Socket_Cmd = require(node + '/socket/socket_cmd');
    var socket_cmd = new Socket_Cmd();

- Wyślij instrukcję ustawiania zmiennych systemowych
  
.. code-block:: javascript
   :linenos:

   // Dopasowanie cmd
   case 511:
   // Pobierz treść wysyłanych danych
   content = data_json.content;
   // Pobierz długość wysyłanych danych
   len = data_json.content.length;
   // Przygotuj dane do wysłania
   send_content = '/f/bIII1III511III' + len + 'III' + content + 'III/b/f'
   // socket send
   socket_cmd.send(send_content);
   // socket recv (zwróć uwagę na rozróżnienie LA/QX)
   // LA Version:
   socket_cmd.recv().then((recv_data)=>{
      response_data = recv_data;
      event_socket.emit('response', res, response_status, response_data);
   }).catch((err)=>{
      console.log(err);
   })
   // QX Version 
   // socket_cmd.recv().then(function(recv_data){
   //     response_data = recv_data;
   //     event_socket.emit('response', res, response_status, response_data);
   // }).catch (function(err){
   //     console.log(err);
   // })
   break;