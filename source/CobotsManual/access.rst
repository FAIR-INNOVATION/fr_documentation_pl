Logowanie do WebApp
=====================

.. toctree:: 
   :maxdepth: 6

Interfejs logowania do WebApp
----------------------------------------

1. Włącz skrzynkę sterowniczą i podłącz kabel sieciowy do komputera PC;
2. Na komputerze PC otwórz przeglądarkę chrome i wejdź na docelowy adres URL 192.168.58.2;
3. Wprowadź nazwę użytkownika i hasło, a następnie kliknij „Zaloguj”, aby uzyskać dostęp do WebApp.

Domyślna nazwa użytkownika to admin, hasło to 123.

.. figure:: teaching_pendant_software/001.png
   :width: 6in
   :align: center

.. centered:: Wykres 2.1‑1 Interfejs logowania

Proste poznanie interfejsu WebApp
-------------------------------------

Po pomyślnym zalogowaniu system przechodzi do „Interfejsu początkowego”, który zawiera głównie:

1. Logo FAIRINO;
2. Przycisk zwijania paska menu;
3. Pasek menu;
4. Obszar sterowania robotem;
5. Obszar stanu robota;
6. Symulacja 3D robota – operacje w scenie 3D;
7. Symulacja 3D robota – operacje na samym robocie;
8. Funkcje dodatkowe robota;
9. Stan robota i funkcji dodatkowych.

Poniżej znajduje się schemat początkowego interfejsu systemu:

.. image:: teaching_pendant_software/002.png
   :align: center
   :width: 6in

.. centered:: Wykres 2.2‑1 Schemat początkowego interfejsu systemu

Obszar sterowania
~~~~~~~~~~~~~~~~~~

.. note:: 
   .. image:: teaching_pendant_software/064.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nazwa: **Przycisk otwierania programu示教**
   
   Funkcja: Otwiera program示教 do programowania, programowania graficznego i programowania z użyciem grafów węzłów.

.. note:: 
   .. image:: teaching_pendant_software/003.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nazwa: **Przycisk włączenia zasilania**
   
   Funkcja: Włącza robota.

.. note:: 
   .. image:: teaching_pendant_software/004.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nazwa: **Przycisk Start**
   
   Funkcja: Przesyła i uruchamia program示教.

.. note:: 
   .. image:: teaching_pendant_software/005.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nazwa: **Przycisk Stop**
   
   Funkcja: Zatrzymuje aktualnie działający program示教.

.. note:: 
   .. image:: teaching_pendant_software/006.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nazwa: **Przycisk Wstrzymaj/Wznów**
   
   Funkcja: Wstrzymuje i wznawia aktualny program示教.

.. important::
   Instrukcja wstrzymania na końcu programu nie może być oceniona.

Pasek stanu
~~~~~~~~~~~~~

.. note:: 
   .. image:: teaching_pendant_software/011.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nazwa: **Stan błędu działania robota**
   
   Funkcja: Robot działa z błędem; gdy nie ma błędu, jest ukryty.

.. note:: 
   .. image:: teaching_pendant_software/007.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nazwa: **Stan robota**
   
   Funkcja: Stopped - zatrzymany, Running - działa, Pause - wstrzymany, Drag - przeciąganie.

.. note:: 
   .. image:: teaching_pendant_software/010.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nazwa: **Układ narzędzia robota, układ przedmiotu, układ dodatkowej osi i numer obciążenia**
   
   Funkcja: Lewy górny – bieżący numer układu narzędzia, prawy górny – bieżący numer układu przedmiotu, lewy dolny – bieżący numer układu dodatkowej osi, prawy dolny – bieżący numer obciążenia.

.. note:: 
   .. image:: teaching_pendant_software/009.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nazwa: **Procent prędkości roboczej**
   
   Funkcja: Prędkość robota podczas pracy w bieżącym trybie.

.. note:: 
   .. image:: teaching_pendant_software/012.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nazwa: **Tryb automatyczny**
   
   Funkcja: Automatyczny tryb pracy robota. Po przełączeniu z ręcznego na automatyczny i ustawieniu prędkości globalnej, prędkość globalna zostanie automatycznie dostosowana do ustawionej prędkości.

.. note:: 
   .. image:: teaching_pendant_software/013.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nazwa: **Tryb ręczny**
   
   Funkcja: Ręczny tryb robota, umożliwiający示教 robota.

.. note:: 
   .. image:: teaching_pendant_software/065.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nazwa: **Przycisk zwijania/rozwijania stanu robota**
   
   Funkcja: Zwijanie/rozwijanie informacji o: układzie narzędzia, układzie przedmiotu, układzie dodatkowej osi, obciążeniu, stanie przeciągania robota, trybie lokalnym/zdalnym, stanie połączenia robota, trybie BOOT i informacji o koncie.

Po kliknięciu przycisku zwijania można wyświetlić następujące informacje o stanie.

.. note:: 
   .. image:: teaching_pendant_software/008.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nazwa: **Numer układu narzędzia**
   
   Funkcja: Wyświetla bieżący numer używanego układu narzędzia.

.. note:: 
   .. image:: teaching_pendant_software/027.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nazwa: **Numer układu przedmiotu**
   
   Funkcja: Wyświetla bieżący numer używanego układu przedmiotu.
   
.. note:: 
   .. image:: teaching_pendant_software/028.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nazwa: **Numer układu dodatkowej osi**
   
   Funkcja: Wyświetla bieżący numer używanego układu dodatkowej osi.

.. note:: 
   .. image:: teaching_pendant_software/066.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nazwa: **Obciążenie**
   
   Funkcja: Wyświetla aktualną masę obciążenia oraz współrzędne środka ciężkości X, Y, Z.

.. note:: 
   .. image:: teaching_pendant_software/014.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nazwa: **Stan przeciągania robota**
   
   Funkcja: Robot może być obecnie przeciągany.

.. note:: 
   .. image:: teaching_pendant_software/015.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nazwa: **Stan przeciągania robota**
   
   Funkcja: Robot nie może być obecnie przeciągany.

.. note:: 
   .. image:: teaching_pendant_software/068.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nazwa: **Tryb lokalny robota**
   
   Funkcja: Robot jest aktualnie sterowany przez skrzynkę sterowniczą.

.. note:: 
   .. image:: teaching_pendant_software/067.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nazwa: **Tryb zdalny robota**
   
   Funkcja: Robot może być obecnie sterowany tylko przez PLC.

.. note:: 
   .. image:: teaching_pendant_software/017.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nazwa: **Stan połączenia**
   
   Funkcja: Robot jest podłączony.

.. note:: 
   .. image:: teaching_pendant_software/016.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nazwa: **Stan rozłączenia**
   
   Funkcja: Robot nie jest podłączony.

.. note:: 
   .. image:: teaching_pendant_software/018.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nazwa: **Informacje o koncie**
   
   Funkcja: Wyświetla nazwę użytkownika, uprawnienia oraz opcję wylogowania.