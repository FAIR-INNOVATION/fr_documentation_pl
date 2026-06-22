Instalacja i zasilanie robota
=============================

.. toctree:: 
   :maxdepth: 6

Instalacja ramienia robota
--------------------------

Podczas montażu robota współpracującego na podstawie montażowej należy użyć odpowiedniej liczby śrub (o klasie wytrzymałości nie niższej niż 8.8), aby dokręcić i zamocować robota na podstawie montażowej. Zaleca się użycie dwóch zgodnych otworów kołkowych na podstawie montażowej w połączeniu z kołkami do pozycjonowania robota, aby zwiększyć dokładność montażu robota i zapobiec przemieszczaniu się robota spowodowanemu kolizjami. Gdy robot ma wysokie wymagania co do dokładności działania, należy obowiązkowo dodać kołki do pozycjonowania robota.

.. centered:: Tabela 1.1-1 Normy części montażowych robota

.. list-table::
   :widths: 80 50 50 50
   :header-rows: 0
   :align: center

   * - **Model robota współpracującego**
     - **Śruby**
     - **Moment dokręcania śrub**
     - **Specyfikacja otworu kołkowego**

   * - FR3
     - 4 sztuki M6
     - ≥10 Nm
     - φ5 mm

   * - FR3-WMS
     - 4 sztuki M6
     - ≥10 Nm
     - φ5 mm

   * - FR3-WML
     - 4 sztuki M6
     - ≥10 Nm
     - φ5 mm

   * - FR3-C
     - 4 sztuki M6
     - ≥10 Nm
     - φ5 mm

   * - FR5-C
     - 4 sztuki M6
     - ≥10 Nm
     - φ5 mm
   
   * - FR5
     - 4 sztuki M8
     - ≥20 Nm
     - φ8 mm

   * - FR10
     - 4 sztuki M8
     - ≥25 Nm
     - φ8 mm

   * - FR16
     - 4 sztuki M8
     - ≥25 Nm
     - φ8 mm

   * - FR20
     - 6 sztuk M10
     - ≥45 Nm
     - φ8 mm

   * - FR30
     - 6 sztuk M10
     - ≥45 Nm
     - φ8 mm

   * - FR30L
     - 6 sztuk M10
     - ≥45 Nm
     - φ8 mm

.. important:: 
   Zaleca się, aby podstawa montażowa robota spełniała następujące wymagania, zapewniając solidne i stabilne zamocowanie robota:
   
   (1) Podstawa montażowa robota musi być wystarczająco wytrzymała i mieć odpowiednią nośność. Powinna wytrzymać co najmniej 5-krotność ciężaru robota i co najmniej 10-krotność momentu obrotowego osi 1.

   (2) Powierzchnia podstawy montażowej robota powinna być płaska, aby zapewnić ścisły kontakt z powierzchnią robota.

   (3) Podstawa montażowa robota powinna być wystarczająco sztywna, solidnie zamocowana i nie może rezonować z robotem.

   (4) Gdy robot i inne elementy poruszają się jednocześnie, podstawa montażowa powinna być odizolowana od innych ruchomych części, nie należy ich mocować razem, aby uniknąć zakłóceń wibracyjnych podczas ruchu.

   (5) Jeśli robot jest zainstalowany na ruchomej platformie lub zewnętrznej osi, przyspieszenie ruchomej platformy lub zewnętrznej osi powinno być tak niskie, jak to możliwe.

Podłączenie skrzynki sterowniczej
------------------------------------

Roboty tej serii mogą być wyposażone w trzy różne skrzynki sterownicze z różnymi wejściami zasilania. Szczegółowe informacje na temat wejścia zasilania skrzynki sterowniczej znajdują się na tabliczce znamionowej skrzynki sterowniczej. Robot wymaga uziemienia elektrycznego. Zewnętrzne połączenia systemu sterowania ramieniem są wykonywane za pomocą wtyczek, które można podłączyć i szybko zainstalować.

A. 30-60 V DC
B. 176-264 V AC ~ 50-60 Hz
C. 100-240 V AC ~ 50-60 Hz

.. note:: Skrzynki sterownicze z wejściem prądu przemiennego są dostępne w dwóch wersjach: wąskiego i szerokiego zakresu napięcia. Zaciski przyłączeniowe i wygląd zewnętrzny skrzynek sterowniczych są identyczne, nie można ich odróżnić samym wyglądem. Należy to potwierdzić na podstawie tabliczki znamionowej skrzynki sterowniczej, a po potwierdzeniu, że nie ma błędów, włączyć zasilanie i uruchomić.

Panel podłączenia robota współpracującego przedstawiono na poniższym wykresie:

.. image:: installation/037.png
   :width: 6in
   :align: center

.. centered:: Wykres 1.2-1 Panel podłączenia skrzynki sterowniczej

Złącze panelu przyciskowego jest domyślnie portem sterowania panelem operatorskim. Adres IP to 192.168.58.2. Użyj kabla sieciowego, aby połączyć złącze panelu przyciskowego z komputerem. Ustaw adres IP komputera na 192.168.58.10 lub w tej samej podsieci. Otwórz przeglądarkę Google Chrome i wprowadź 192.168.58.2, aby uzyskać dostęp do strony panelu operatorskiego.

Poznanie panelu przyciskowego i końcowego LED
---------------------------------------------

Panel przyciskowy
~~~~~~~~~~~~~~~~~

60 panel przyciskowy (POE)(BX01)
++++++++++++++++++++++++++++++++

.. figure:: installation/058.png
	:align: center
	:width: 6in

.. centered:: Wykres 1.3-1 60 panel przyciskowy (POE)

60 panel przyciskowy (POE)(BX02)-V1.0
+++++++++++++++++++++++++++++++++++++

.. image:: installation/059.png
   :width: 6in
   :align: center

.. centered:: Wykres 1.3-2 Panel podłączenia skrzynki sterowniczej

.. centered:: Tabela 1.3-1 Opis przycisków panelu podłączenia skrzynki sterowniczej

.. list-table::
   :widths: 50 200
   :header-rows: 0
   :align: center

   * - **Nazwa przycisku**
     - **Funkcja**

   * - Wyłącznik awaryjny
     - Po naciśnięciu wyłącznika awaryjnego robot przechodzi w stan awaryjnego zatrzymania

   * - Start/Stop
     - Uruchamianie/zatrzymywanie działania programu

   * - Port sieciowy
     - Podłączenie do panelu operatorskiego sieciowego

   * - Wyłączenie
     - Tymczasowo nieaktywne

   * - Zapis punktu
     - Zapis punktu uczenia

   * - Tryb uczenia
     - Wejście/wyjście ze stanu z podłączonym panelem operatorskim

   * - Tryb pracy
     - Przełączanie trybu automatyczny/ręczny

   * - Tryb przeciągania
     - Wejście/wyjście z trybu przeciągania

60 panel przyciskowy (POE)(BX02)-V2.0
+++++++++++++++++++++++++++++++++++++

.. image:: installation/079.png
   :width: 6in
   :align: center

.. centered:: Wykres 1.3-3 Panel podłączenia skrzynki sterowniczej

.. centered:: Tabela 1.3-2 Opis przycisków panelu podłączenia skrzynki sterowniczej

.. list-table::
   :widths: 50 200
   :header-rows: 0
   :align: center

   * - **Nazwa przycisku**
     - **Funkcja**

   * - Wyłącznik awaryjny
     - Po naciśnięciu wyłącznika awaryjnego robot przechodzi w stan awaryjnego zatrzymania

   * - Start/Stop
     - Uruchamianie/zatrzymywanie działania programu

   * - Port sieciowy
     - Podłączenie do panelu operatorskiego sieciowego

   * - Reset IP
     - Resetowanie adresu IP portu sieciowego

   * - Zapis punktu
     - Zapis punktu uczenia

   * - Jedno kliknięcie wyczyszczenia
     - Czyszczenie wszystkich możliwych do usunięcia błędów

   * - Tryb pracy
     - Przełączanie trybu automatyczny/ręczny

   * - Tryb przeciągania
     - Wejście/wyjście z trybu przeciągania

Końcowy LED
~~~~~~~~~~~

.. centered:: Tabela 1.3-3 Definicja końcowego LED

.. list-table::
   :widths: 120 100
   :header-rows: 0
   :align: center

   * - **Funkcja**
     - **Kolor LED**

   * - Gdy komunikacja nie jest nawiązana
     - Naprzemiennie: "wyłączony", "czerwony", "zielony", "niebieski"

   * - Tryb automatyczny
     - Świeci na niebiesko

   * - Tryb ręczny
     - Świeci na zielono

   * - Tryb przeciągania
     - Świeci na biało-błękitnie

   * - Zapis punktu na panelu przyciskowym (tylko podczas korzystania z panelu przyciskowego)
     - Miga na fioletowo dwa razy

   * - Wejście w stan bez podłączonego panelu przyciskowego (tylko podczas korzystania z panelu przyciskowego)
     - Miga na błękitno dwa razy

   * - Rozpoczęcie działania (tylko podczas korzystania z panelu przyciskowego)
     - Miga na niebiesko dwa razy

   * - Zatrzymanie działania (tylko podczas korzystania z panelu przyciskowego)
     - Miga na czerwono dwa razy

   * - Błąd (tylko podczas korzystania z panelu przyciskowego)
     - Świeci na czerwono

   * - Zakończenie kalibracji zera
     - Miga na biało-błękitnie trzy razy

   * - Odłączenie
     - Miga na żółto dwa razy

Włączenie zasilania i załączenie
--------------------------------

Przed włączeniem zasilania upewnij się, że przycisk awaryjnego zatrzymania na panelu przyciskowym jest zwolniony. Naciśnij czerwony przycisk zasilania na skrzynce sterowniczej, aby włączyć zasilanie. Po pomyślnym załączeniu, końcowy dioda LED świeci na zielono.

Wyłączenie zasilania
--------------------

.. important:: 
   Podczas korzystania z tego urządzenia należy bezwzględnie upewnić się, że przed wyłączeniem zasilania wszystkie działające programy zostały zatrzymane, funkcja zapytania o stan została wyłączona, a stan pracy jest ustawiony na "Stopped" (Zatrzymany). Ta czynność ma na celu ochronę urządzenia i bezpieczeństwa przechowywanych danych, zapobiegając utracie danych lub uszkodzeniu systemu spowodowanemu nagłym odcięciem zasilania.

.. image:: installation/078.png
   :width: 6in
   :align: center

.. centered:: Wykres 1.5-1 Przycisk wyłączania zasilania

Bateria pastylkowa skrzynki sterowniczej
----------------------------------------

Częste przyczyny utraty czasu
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Urządzenie to wykorzystuje zewnętrzną baterię pastylkową jako zasilanie rezerwowe dla zegara czasu rzeczywistego (RTC), służącą do podtrzymywania zliczania czasu w przypadku zaniku głównego zasilania.

Jeśli wystąpi utrata czasu (tzn. po ponownym włączeniu zasilania wyświetlana jest nieprawidłowa data), jest to zwykle spowodowane jedną lub kilkoma z następujących przyczyn:

.. list-table::
   :widths: 40 40 60
   :header-rows: 0
   :align: center

   * - **Kategoria przyczyny**
     - **Szczegółowy opis**
     - **Zalecenia dotyczące diagnozowania**

   * - Wyczerpanie baterii pastylkowej
     - Urządzenie nie było używane przez ponad 3 miesiące, co spowodowało naturalne zużycie energii baterii.
     - Zmierz napięcie baterii za pomocą multimetru (po wyjęciu), jeśli napięcie jest niższe niż 2,5 V, baterię należy naładować.

   * - Uszkodzenie baterii
     - Bateria osiągnęła koniec swojego okresu użytkowania.
     - Sprawdź, czy bateria nie przecieka ani nie jest wybrzuszona. Wymień baterię. Model baterii: MS621FE-FL11E, 3 V / 5,5 mAh, nadaje się do ładowania.

   * - Słaby kontakt styków baterii
     - Utlenienie lub odkształcenie styków baterii, lub wstrząsy urządzenia spowodowały chwilowe odłączenie baterii od styków.
     - Sprawdź, czy bateria jest dobrze osadzona w styku, wyczyść styki, zainstaluj baterię ponownie i upewnij się, że jest dobrze zamocowana.

   * - Brak baterii lub bateria włożona odwrotnie
     - Użytkownik nie zainstalował baterii zapasowej lub zainstalował ją z nieprawidłową polaryzacją.
     - | Upewnij się, że bateria jest zainstalowana, a bieguny są prawidłowe (biegun dodatni skierowany do góry).

       .. image:: installation/131.png
          :width: 2in
          :align: center

   * - Awaria obwodu ładowania baterii
     - Ładowalna bateria pastylkowa nie może normalnie przechowywać ładunku.
     - Wymagana jest kontrola obwodu ładowania przez wykwalifikowany personel serwisowy.

.. warning:: Bateria pastylkowa używana w tym urządzeniu to model [MS621FE-FL11E, 3 V / 5,5 mAh, nadaje się do ładowania]. Należy koniecznie postępować zgodnie z odpowiednią procedurą dla tego modelu. Zabrania się instalowania baterii, które nie nadają się do ładowania.

Identyfikacja nieprawidłowości czasu i ręczna kalibracja
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1) Metoda identyfikacji nieprawidłowości
   
Po ponownym włączeniu zasilania robota należy najpierw sprawdzić aktualny czas wyświetlany na stronie urządzenia. Porównaj go z czasem systemowym komputera:

- Jeśli są zgodne, oznacza to, że czas jest prawidłowy i nie są wymagane dalsze działania.

.. image:: installation/132.png
   :width: 4in
   :align: center

.. centered:: Wykres 1.6-1 Nieprawidłowa sytuacja czasu systemowego

- Jeśli nie są zgodne (np. błędna data, duże odchylenie godziny, minut, sekund), oznacza to nieprawidłowość czasu. Należy kontynuować procedurę kalibracji opisaną poniżej.
  
2) Procedura kalibracji

Jeśli potwierdzono nieprawidłowość czasu, wykonaj następujące czynności, aby zsynchronizować czas systemowy:

- Otwórz przeglądarkę i przejdź do WebApp, następnie nawiguj kolejno do: "Ustawienia systemowe -> Ustawienia ogólne -> Czas".

.. image:: installation/133.png
   :width: 6in
   :align: center

.. centered:: Wykres 1.6-2 Interfejs aktualizacji czasu systemowego

- Kliknij przycisk "Aktualizuj" w interfejsie, a system automatycznie zsynchronizuje czas. Po synchronizacji wróć do strony robota, a czas powinien wrócić do normy.

Ładowanie baterii pastylkowej i uwagi dotyczące konserwacji
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1) Warunki ładowania

- Po podłączeniu głównego zasilania urządzenia (220 V AC) obwód ładowania aktywuje się automatycznie.
- Temperatura otoczenia powinna mieścić się w zakresie 0°C ~ 45°C. Wysoka temperatura zmniejsza wydajność ładowania i skraca żywotność baterii.

2) Czas ładowania

- Całkowicie rozładowana bateria potrzebuje około [5 godzin] do pełnego naładowania. W tym czasie funkcja podtrzymania czasu działa prawidłowo.

3) Zakazy

- Nie używaj zewnętrznej ładowarki do ładowania baterii pastylkowej w urządzeniu.
- Nie instaluj baterii, które nie nadają się do ładowania w urządzeniu, ponieważ może to spowodować zagrożenie.

Wymiana i utylizacja baterii
~~~~~~~~~~~~~~~~~~~~~~~~~~~~
1) Okres wymiany

- Zazwyczaj żywotność baterii wynosi ponad [5 lat]. Wymień baterię, jeśli czas jest często tracony.

2) Procedura wymiany

- Odłącz główne zasilanie urządzenia.
- Otwórz górną pokrywę.
- Wyjmij starą baterię, zwracając uwagę na polaryzację.
- Przylutuj nową baterię tego samego modelu (biegun dodatni skierowany do góry).
- Zamknij pokrywę, włącz ponownie zasilanie i skoryguj bieżący czas.

3) Utylizacja

- Nie wrzucaj baterii do ognia ani nie dopuszczaj do kontaktu z wodą.
- Utylizuj zużyte baterie zgodnie z lokalnymi przepisami dotyczącymi segregacji odpadów (baterie pastylkowe często zawierają lit lub metale ciężkie).

Wsparcie techniczne
~~~~~~~~~~~~~~~~~~~

Jeśli problem nie zostanie rozwiązany po wykonaniu powyższych kroków, skontaktuj się z naszym zespołem wsparcia technicznego i podaj następujące informacje:

- Model i numer seryjny urządzenia.
- Używany model baterii (sprawdź napisy na powierzchni baterii).
- Opis usterki (np. natychmiastowa utrata po odcięciu zasilania / utrata po pozostawieniu na noc).