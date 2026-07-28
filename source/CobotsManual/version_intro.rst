Wersja V3.9.8
-----------------

Data: 2026-07-27

- **Zoptymalizowano ruch śledzenia taśmy transportowej**:
    Ścieżka: Teach Program -> Polecenia Taśmy.

    Opis: 1. Optymalizacja ustawień punktu wyzwalania IO i punktu początkowego programu; 2. Optymalizacja wielokrotnego wyzwalania sygnałów IO podczas ruchu.

- **Zoptymalizowano ładowanie web dla dużych programów LUA i podprogramów**:
    Ścieżka: Teach Program -> Importuj Program.

    Opis: Przesyłanie dużych plików programów LUA (powyżej 50 MB) do ładowania i wykonywania.

- **Zoptymalizowano polecenia ustawiania/pobierania narzędzi robota, układów współrzędnych przedmiotu i obciążenia**:
    Ścieżka: Ustawienia Początkowe -> Narzędzia, Układy Współrzędnych Przedmiotu, Obciążenie.

    Opis: Parametry układów współrzędnych i obciążenia mogą być normalnie ustawiane i pobierane poprzez interfejs poleceń portu 8080, SDK i WebApp.

- **Dodano funkcje związane z SmartTool**:
    Ścieżka: Ustawienia Początkowe -> Urządzenia PerYferyjne -> Rękojeść Spawalnicza.

    Opis: 1. Reset pamięci przycisków IO po wyczyszczeniu lub utworzeniu nowego programu; 2. Dodano wybór numeru procesu dla 3 generowanych instrukcji związanych z rozpoczęciem łuku oraz usunięto limit czasu oczekiwania dla rozpoczęcia łuku; 3. Dodano funkcję globalnego czyszczenia punktów z resetem numeru sekwencji po czyszczeniu; 4. Usunięto ograniczenie dotyczące powtarzalnej konfiguracji PTP, LIN i ARC.

- **Dodano obsługę pięciopalczastej dłoni**:
    Ścieżka: Ustawienia Początkowe -> Urządzenia PerYferyjne -> Dłoń.

    Opis: Dodano adapter Lua dla końcówki robota do pięciopalczastej dłoni.

- **Dodano adaptację impedancji stawów FR3-WML dla przeciągania**:
    Ścieżka: Aplikacje Pomocnicze -> Aplikacje Narzędziowe -> Blokada Przeciągania.

    Opis: Dostosowano parametry hybrydowego przeciągania z siłą sześcioosiową i impedancją stawów dla FR3-WML w celu umożliwienia funkcji przeciągania.

Wersja V3.9.7
-----------------

Data: 2026-06-25

- **Zoptymalizowano japoński pakiet językowy oprogramowania**:

    Opis: Zoptymalizowano zawartość tłumaczenia japońskiego pakietu językowego.

- **Zoptymalizowano parametry ścieżki dla programów LUA robota**:

    Opis: Wejście pliku wymaga teraz tylko nazwy; ścieżka nie jest już potrzebna.

- **Zoptymalizowano funkcję splotu (weaving) dla nowych przejść spline-linia-łuk**:
    Ścieżka: Aplikacje Pomocnicze -> Pakiet Procesów -> Biblioteka Eksperta Spawalniczego -> Nowe Spawanie z Splotem na Spline.

    Opis: Dostosowano funkcję splotu do nowej funkcji przejścia spline-linia-łuk.

- **Zoptymalizowano funkcję ochrony miękkich ograniczeń (soft limit) przegubów**:
    Ścieżka: Ustawienia Początkowe -> Podstawowe -> Przeguby -> Miękkie Ograniczenia.

    Opis: Zoptymalizowano współczynniki sztywności i tłumienia dla miękkich ograniczeń każdego przegubu.

- **Dodano funkcję drukowania (print) dla programów LUA robota**:
    Ścieżka: Program Teach Pendant -> Funkcja Drukowania.

    Opis: Podgląd w czasie rzeczywistym niestandardowych informacji drukowanych z programów LUA.

- **Dodano adapter Lua dla końcówki robota do trójpalczastej dłoni**:
    Ścieżka: Ustawienia Początkowe -> Urządzenia PerYferyjne -> Przyssawka.

    Opis: 1. Dodano adapter dla przyssawki i trójpalczastej dłoni na końcówce robota; 2. Zoptymalizowano istniejący otwarty protokół Lua dla końcówki robota.

- **Dodano funkcję zgłaszania błędów przy upadku przedmiotu z chwytaka**:
    Ścieżka: Ustawienia Początkowe -> Urządzenia PerYferyjne -> Chwytak.

    Opis: Dodano zgłaszanie błędu przy upadku detalu z chwytaka; ruch zostaje zatrzymany po zgłoszeniu.

- **Dodano funkcję sprzężenia zwrotnego dla zadziałania zabezpieczenia przed zwarciem 24V w module DO szafy sterowniczej szerokiego napięcia**:

    Opis: Dodano zabezpieczenie przed zwarciem i komunikat błędu.

Wersja V3.9.6
-------------

Data: 2026-05-26

- **Optymalizacja funkcji ruchu matrycowego**:
    Ścieżka: Aplikacje pomocnicze -> Pakiety procesowe -> Ruch matrycowy.

    Opis: Optymalizacja funkcji zestawu instrukcji ruchu matrycowego.

- **Optymalizacja funkcji redukcji prędkości DI**:
    Ścieżka: Ustawienia początkowe -> Podstawowe -> Ustawienia I/O.

    Opis: 1. Po wyzwoleniu sygnału DI, proces regulacji prędkości jest płynny, bez wstrząsów i zacięć; 2. Ścieżka końcówki robota nie zmienia się przed i po regulacji prędkości; 3. Brak błędów i przerw podczas regulacji prędkości wyzwalanej przez DI; 4. Natychmiastowe zatrzymanie po wyzwoleniu zatrzymania przez DI, bez błędów.

- **Dodanie funkcji adaptacji komunikacji lasera spawalniczego robota**:
    Ścieżka: Ustawienia początkowe -> Urządzenia peryferyjne -> Spawarka.

    Opis: 1. Dodanie w WebAPP ustawień związanych z laserem spawalniczym, debugowania, instrukcji generowania programu lua; 2. Dodanie parametrów związanych z laserem spawalniczym; 3. Opracowanie programu adaptacyjnego PLC.

- **Dodanie adaptacji protokołu EIP/CClink-IE dla karty FRJ-PCIeN-EIP/CC/PN-RJ-V10**:
    Ścieżka: Ustawienia początkowe -> Urządzenia peryferyjne -> Komunikacja kartą.

    Opis: 1. Obsługa konfigurowalnego cyklu komunikacyjnego; 2. Obsługa pobierania stanu połączenia magistrali; 3. Zgodność z protokołami EIP i CC.

Wersja V3.9.5
-------------

Data: 2026-04-24

- **Optymalizacja funkcji kontrolera**:
    Ścieżka: Ustawienia ogólne -> Ustawienia sieci; Program nauczania -> Programowanie.

    Opis: 1. Błąd walidacji podczas konfiguracji tego samego adresu IP dla ETH0 i ETH1; 2. Optymalizacja wyświetlania koloru numeru bieżącej linii programu.

- **Optymalizacja prędkości FR30**:

    Opis: Zwiększenie prędkości roboczej.

- **Optymalizacja funkcji oscylacji łuku**:
    Ścieżka: Program nauczania -> Programowanie -> Instrukcja łuku.

    Opis: Umożliwienie ruchu z oscylacją.

- **Optymalizacja funkcji SetTrajectoryJSpeed – brak zacięć podczas debugowania**:

    Opis: Podczas procesu regulacji prędkości instrukcji, prędkość robota nie spada do zera podczas przełączania prędkości.

- **Optymalizacja obsługi trybu edycji instrukcji programu Lua w module programowania**:
    Ścieżka: Program nauczania -> Programowanie.

    Opis: Optymalizacja umożliwiająca precyzyjne dopasowanie i wyświetlanie treści instrukcji.

- **Dodanie adaptacji protokołów PN/Ecat/EIP/cclink dla karty FRJ-PCIeN-EC-RJ-V20**:
    Ścieżka: Ustawienia początkowe -> Urządzenia peryferyjne -> Komunikacja kartą.

    Opis: 1. Obsługa aktualizacji/pobierania oprogramowania sprzętowego online; 2. Obsługa konfigurowalnego cyklu komunikacyjnego; 3. Obsługa pobierania stanu połączenia magistrali.

- **Dodanie instrukcji kontrolera**:
    Ścieżka: Program nauczania -> Programowanie; Ustawienia początkowe -> Bezpieczeństwo -> Bezpieczne zatrzymanie.

    Opis: 1. Dodanie opcji typu przesunięcia układu współrzędnych przedmiotu w instrukcjach ruchu; 2. Dodanie funkcji bezpiecznego zatrzymania; 3. Dodanie instrukcji odczytu DO, AO dla wejść/wyjść skrzynki sterowniczej, końcowych i rozszerzonych.

- **Dodanie funkcji konfiguracji sygnału DO po awaryjnym zatrzymaniu skrzynki sterowniczej**:
    Ścieżka: Ustawienia początkowe -> Podstawowe -> DO.

    Opis: Nowa funkcja konfiguracji sygnału DO po awaryjnym zatrzymaniu skrzynki sterowniczej.

- **Dodanie adaptacji pakietu językowego dla wersji oprogramowania w języku portugalskim**:

    Opis: Dodanie przełączania języka portugalskiego.

Wersja V3.9.4
-------------

Data: 2026-04-08

- **Optymalizacja funkcji odtwarzania trajektorii nauczania TPD**:
    Ścieżka: Program nauczania -> Programowanie -> Instrukcja TPD.

    Opis: 1. Automatyczne generowanie instrukcji lua punktu początkowego; 2. Zabezpieczenie przed błędami przycisku start.

- **Optymalizacja funkcji kopii zapasowej danych Webapp**:

    Opis: Udoskonalenie i optymalizacja funkcji kopii zapasowej danych.

- **Optymalizacja miękkiego limitu i pozycji pakowania dla FR3WML**:

    Opis: Ustawienie zakresu miękkiego limitu dla stawu 3 na ±163°.

- **Optymalizacja funkcji kompensacji pełnych parametrów DH i szybka walidacja**:

    Opis: Kompensacja pełnego modelu parametrów.

- **Dodanie funkcji sterowania impedancją ruchu PTP**:

    Opis: Zwiększenie bezpieczeństwa podczas interakcji robota z człowiekiem.

- **Dodanie funkcji protokołu komunikacyjnego dla urządzenia końcowego głowicy do moksybustii**:
    Ścieżka: Ustawienia początkowe -> Urządzenia peryferyjne -> Transparentna transmisja końcowa.

    Opis: Dodanie adaptacji protokołu komunikacyjnego dla nowego urządzenia końcowego.

- **Dodanie adaptacji pakietu językowego dla wersji oprogramowania w języku niemieckim**:

    Opis: Dodanie przełączania języka niemieckiego.

- **Dodanie funkcji działania instrukcji ruchu servo dla ustawień bezpiecznej prędkości**:
    Ścieżka: Ustawienia początkowe -> Bezpieczeństwo -> Bezpieczna prędkość.

    Opis: Dodanie opcji zatrzymania z błędem i odłączenia po przekroczeniu prędkości w strategii bezpieczeństwa.

- **Dodanie adaptera do routera bezprzewodowego TP-LINK AX3000 dla LA**:

    Opis: Rozwiązanie problemu z brakiem bezprzewodowego dostępu do webApp po ponownym uruchomieniu z wyłączeniem zasilania.

- **Dodanie funkcji oscylacji punktowej**:
    Ścieżka: Program nauczania -> Programowanie -> Instrukcja Weave.

    Opis: Współpraca z zewnętrznym czujnikiem laserowym w celu realizacji funkcji oscylacji punktowej.

Wersja V3.9.3
-------------

Data: 2026-02-11

- **Optymalizacja ustawień prędkości instrukcji ruchu SmartTool**:
    Ścieżka: Ustawienia początkowe -> Urządzenia peryferyjne -> Uchwyt spawalniczy.

    Opis: Zakres ustawiania prędkości dla instrukcji PTP, LIN, ARC został dostosowany do 0-100% (wcześniej górna granica wynosiła 30%).

- **Optymalizacja obserwacji siły zewnętrznej bez czujnika siły i poprawa komfortu przeciągania**:
    Ścieżka: Aplikacje pomocnicze -> Narzędzia aplikacyjne -> Blokada przeciągania.

    Opis: Zwiększenie dokładności obserwacji siły zewnętrznej do ±0,5 N.

- **Optymalizacja mechanizmu ponownego łączenia mastera Modbus TCP**:
    Ścieżka: Program nauczania -> Programowanie -> Modbus TCP.

    Opis: Dodanie logiki wstrzymania.

- **Dodanie funkcji instrukcji debugowania osi rozszerzonej**:
    Ścieżka: Ustawienia początkowe -> Urządzenia peryferyjne -> Oś rozszerzona.

    Opis: Implementacja odwrotnej transformacji robota w układzie współrzędnych osi rozszerzonej oraz ruchu ServoCart z osią rozszerzoną.

- **Dodanie funkcji konfigurowalnego stanu resetowania DO po wstrzymaniu/wznowieniu**:
    Ścieżka: Ustawienia początkowe -> Urządzenia peryferyjne -> Uchwyt spawalniczy.

    Opis: Opcjonalne ustawienie, czy stan wyjścia DO po wznowieniu ruchu ma być zgodny ze stanem sprzed wstrzymania.

Wersja V3.9.2
-------------

Data: 2026-01-26

- **Optymalizacja przeciągania nauczania w pętli pozycyjnej czujnika momentu obrotowego stawu**:
    Ścieżka: Aplikacje pomocnicze -> Narzędzia aplikacyjne -> Blokada przeciągania.

    Opis: Rozwiązanie problemu niewystarczającej dokładności pozycjonowania podczas przeciągania między stawami w ciągu 2 sekund.

- **Optymalizacja karty rozszerzającej**:

    Opis: Optymalizacja mechanizmu synchronizacji danych dla rozszerzonego DO.

- **Optymalizacja funkcji śledzenia łuku**:
    Ścieżka: Ustawienia początkowe -> Urządzenia peryferyjne -> Spawarka.

    Opis: Dodanie możliwości zbierania prądu spawania w czasie rzeczywistym poprzez protokół otwarty urządzeń peryferyjnych Modbus TCP.

- **Optymalizacja funkcji resetowania adresu IP kontrolera i fizycznego panelu operatorskiego**:
    Ścieżka: Ustawienia systemowe -> Sieć.

    Opis: ① Dodanie funkcji resetowania IP kontrolera w webrecovery, wymagającej podwójnego potwierdzenia; ② Dodanie funkcji resetowania IP w fizycznym panelu operatorskim; ③ Dodanie możliwości resetowania IP fizycznego panelu operatorskiego za pomocą przycisków fizycznych przy braku połączenia, adres IP panelu operatorskiego to 192.168.58.77.

- **Dodanie konfiguracji nowego modelu robota FR3C**:

    Opis: Zakres ruchu stawów jest zgodny z serią FR3, ramiona górne i dolne są zgodne z WMS, ładowność znamionowa 3 kg.

- **Dodanie funkcji interferencji sześcianu**:
    Ścieżka: Ustawienia początkowe -> Bezpieczeństwo -> Strefa interferencji -> Interferencja sześcianu.

    Opis: Implementacja jednoczesnej kontroli interferencji dla co najmniej 4 sześcianów, z możliwością konfiguracji wyjścia CO odpowiadającego sygnałowi interferencji.

- **Dodanie rozszerzenia funkcji modułu slave_interpret (protokół PROFINET) oraz funkcji wyświetlania I/O w ilości Web**:
    Ścieżka: Ustawienia początkowe -> Urządzenia peryferyjne -> Komunikacja kartą -> Aktualizacja karty.

    Opis: Dodanie aktualizacji oprogramowania sprzętowego EtherCAT dla karty Jiyuan, detekcji komunikacji PLC, konfigurowalnego cyklu oraz funkcji wyświetlania pełnych I/O w Web (protokół PROFINET).

- **Dodanie funkcji protokołu otwartego smarttool**:
    Ścieżka: Ustawienia początkowe -> Urządzenia peryferyjne -> Uchwyt spawalniczy.

    Opis: ① Dodanie tworzenia, analizy i przetwarzania sygnałów detekcyjnych programu smarttool opartego na protokole otwartym, dodanie funkcji zabezpieczającej przycisków „Cofnij, Usuń”. ② Dodanie funkcji automatycznego generowania dla konfiguracji przycisków protokołu otwartego smarttool.

- **Dodanie wzajemnej zgodności pakietów kopii zapasowych wersji oprogramowania QX i LA**:
    Ścieżka: Aplikacje pomocnicze -> Narzędzia aplikacyjne -> Kopia zapasowa danych.

    Opis: ① QX obsługuje i może w pełni zaimportować pakiety kopii zapasowych LA, LA obsługuje i może w pełni zaimportować pakiety kopii zapasowych QX; ② Zgodność z pakietami kopii zapasowych od wersji v3.8.7 wzwyż.

- **Dodanie konfigurowalnych parametrów dla końcowego CI i CI kontrolera**:
    Ścieżka: Ustawienia początkowe -> Podstawowe -> Ustawienia I/O -> DI.

    Opis: Implementacja możliwości konfiguracji przerwania ruchu dla końcowego CI, synchronizacja części konfigurowalnych funkcji CI kontrolera.

- **Dodanie funkcji śledzenia serwo z danymi laserowymi robota**:
    Ścieżka: Ustawienia początkowe -> Urządzenia peryferyjne -> Liniowy czujnik laserowy.

    Opis: Implementacja bezpośredniego śledzenia przez robota na podstawie danych z czujnika laserowego.

- **Dodanie funkcji konfiguracji panelu operatorskiego**:

    Opis: ① Przyciski F1-F4 na panelu operatorskim obsługują konfigurację niestandardowych funkcji w interfejsie WEB; ② Tryb niestandardowy przełącznika kluczykowego może być skonfigurowany jako tryb przeciągania.

Wersja V3.9.1
-------------

Data: 2025-12-30

- **Funkcja rejestrowania przez robota w tle zdarzeń awarii i alarmów**:

    Opis: Możliwość rejestrowania informacji o awariach i alarmach podczas wylogowania z interfejsu użytkownika, z możliwością przeglądania po ponownym zalogowaniu.

- **Dodanie funkcji ruchu względnego z bieżącej pozycji dla instrukcji PTP, LIN oraz dodanie funkcji dodawania instrukcji ServoJ w WebApp**:
    Ścieżka: Program nauczania -> Programowanie -> Instrukcje PTP/LIN.

    Opis: Rozwiązanie problemu złożoności operacji instrukcjami, gdy ramię mechaniczne nie ma punktu nauczania, ale wymagane jest przesunięcie względem bieżącej pozycji – można to zrealizować za pomocą jednej instrukcji.

- **Przełącznik debugowania protokołu otwartego lua końcowego i funkcja walidacji składni**:
    Ścieżka: Ustawienia początkowe -> Urządzenia peryferyjne -> Chwytak, czujnik siły, uchwyt spawalniczy.

    Opis: Obecnie kontroler integruje i dostosowuje protokoły końcowe (chwytak, czujnik siły, uchwyt spawalniczy). Niniejsza optymalizacja umożliwia bezpośrednie zastosowanie w WebAPP do końcówki; webServer dodaje walidację składni lua protokołu, błąd walidacji powoduje bezpośredni komunikat o błędzie; WebAPP dodaje przełącznik debugowania protokołu otwartego lua, w stanie debugowania uruchomienie końcowego lua pomija błędy przekroczenia limitu czasu komunikacji czujnika.

- **Optymalizacja funkcji scenariusza paletyzacji FRCap**:
    Ścieżka: Aplikacje pomocnicze -> Pakiety procesowe -> Paletyzacja.

    Opis: Paletyzacja obsługuje dwa punkty pobierania – po dostarczeniu materiałów z dwóch linii produkcyjnych, robot chwyta materiały kolejno z punktów pobierania na obu liniach i umieszcza je na dwóch odpowiadających im paletach.

- **Optymalizacja funkcji fizycznego panelu operatorskiego**:
    Ścieżka: Ustawienia systemowe -> Ustawienia ogólne -> Sieć.

    Opis: Obecnie klient musi najpierw przełączyć się na webapp, a następnie wejść do własnego interfejsu nadrzędnego, co jest uciążliwe. Po optymalizacji, bez logowania do interfejsu nauczania, obracając fizycznym przełącznikiem kluczykowym, robot może przełączać tryb ręczny/automatyczny.

- **Optymalizacja funkcji kolizji**:
    Ścieżka: Ustawienia początkowe -> Podstawowe -> Stawy -> Poziom kolizji -> Wykrywanie fałszywych alarmów.

    Opis: Nawet przy poziomie kolizji 1 robot może działać z dowolną prędkością i nie zgłasza fałszywych alarmów z powodu dużej prędkości. W przypadku kolizji lub ścisnięcia zgłaszany jest błąd i następuje zatrzymanie.

- **Funkcja kalibracji TCP czujnika fotoelektrycznego**:
    Ścieżka: Ustawienia początkowe -> Podstawowe -> Współrzędne narzędzia -> Automatyczna kalibracja fotoelektryczna.

    Opis: Obsługa automatycznej kalibracji prostego i zakrzywionego uchwytu spawalniczego.

Wersja V3.9.0
-------------

Data: 2025-11-27

- **Zastosowanie głowicy szlifierskiej z kontrolą siły DFC Daru**:
    Ścieżka: Ustawienia początkowe -> Urządzenia peryferyjne -> Szlifowanie -> Głowica szlifierska z kontrolą siły DFC Daru.

    Opis: Adaptacja i testowanie części oprogramowania peryferyjnego inteligentnej elastycznej głowicy szlifierskiej z kontrolą siły DFC, spełniające wymagania adaptacji systemu szlifierskiego DFC.

- **Kalibracja parametrów czujnika momentu obrotowego stawu w całym urządzeniu**:
    Ścieżka: Aplikacje pomocnicze -> Narzędzia aplikacyjne -> Blokada przeciągania -> Przeciąganie całego urządzenia z czujnikiem momentu obrotowego stawu.

    Opis: Uruchomienie ustalonej trajektorii w celu kalibracji parametrów czułości, liniowości, błędu histerezy i powtarzalności czujnika momentu obrotowego stawu.

- **Dodanie funkcji unikania przeregulowania podczas przeciągania nauczania z użyciem czujnika momentu obrotowego stawu**:
    Ścieżka: Aplikacje pomocnicze -> Narzędzia aplikacyjne -> Blokada przeciągania -> Przeciąganie całego urządzenia z czujnikiem momentu obrotowego stawu.

    Opis: Zmniejszenie zjawiska przeregulowania podczas przeciągania w pętli prądowej. Po włączeniu tej funkcji możliwe jest wygodne pozycjonowanie punktowe podczas przeciągania.

- **Funkcja spawania linii przecięcia rur**:
    Ścieżka: Program nauczania -> Programowanie -> Instrukcja linii przecięcia rur.

    Opis: Zapisanie 6 punktów nauczania odpowiednio na przekrojach poprzecznych rury głównej i łączonej, wprowadzenie parametrów takich jak kierunek ruchu, prędkość, przyspieszenie, wartość przesunięcia. Robot może uzyskać trajektorię linii przecięcia powstałej z przecięcia dwóch rur i przeprowadzić spawanie.

- **Dodanie funkcji porównania dla ustawień oczekiwania na wejście analogowe Modbus**:
    Ścieżka: Program nauczania -> Programowanie -> Instrukcje Modbus.

    Opis: Dodanie możliwości porównania dla stanu oczekiwania na wejście analogowe urządzenia podrzędnego.

- **Funkcja jednoklikowej aktualizacji punktu nauczania i wykonania pojedynczego punktu Lin**:
    Ścieżka: Program nauczania -> Punkty nauczania -> Zarządzanie punktami.

    Opis: W interfejsie punktów nauczania, za pomocą paska operacji na samym robocie, aktualizacja bieżącej pozycji robota do odpowiadającego punktu, z możliwością wyboru synchronizacji programu nauczania. Dodano nowy sposób wykonania pojedynczego punktu Lin.

- **Optymalizacja funkcji zapisu punktów w trybie tabeli punktów**:
    Ścieżka: Program nauczania -> Punkty nauczania -> Zarządzanie punktami.

    Opis: Ponowny zapis punktu w trybie tabeli punktów może synchronizować aktualizację programu lua. Optymalizacja rozwiązująca sporadyczne przekroczenie prędkości w trybie redukcji PTP oraz problem z zatrzymaniem ruchu po osiągnięciu pozycji w trybie regulacji prędkości LIN.

- **Plik konfiguracyjny użytkownika**:
    Opis: Optymalizacja problemu z nieudanym ładowaniem pliku konfiguracyjnego użytkownika robota, dodanie funkcji automatycznego ponownego uruchamiania i przywracania kopii zapasowej pliku konfiguracyjnego.

- **Wersja interfejsu web**:
    Opis: Wersja interfejsu web zaktualizowana do 2.0, aktualizacja i optymalizacja interfejsu oprogramowania.

- **Dodanie modelu robota V6.5**:
    Opis: Dzięki optymalizacji sprzętu (reduktory itp.) i algorytmów, zmniejszenie drgań robota i poprawa dokładności trajektorii. Dodano modele robotów FR3, FR5, FR10, FR16, FR20.

- **Dodanie konfiguracji modelu robota FR5C**:
    Opis: Dodanie funkcji konfiguracji modelu robota FR5C w wersji oprogramowania LA.

Wersja V3.8.7
-------------

Data: 2025-10-21

- **Funkcja wykrywania kolizji robota na prostej szynie zębatej**:
    Ścieżka: Ustawienia początkowe -> Podstawowe -> Stawy -> Poziom kolizji -> Wykrywanie kolizji robota na prostej szynie zębatej.

    Opis: Umożliwia awaryjne zatrzymanie szyny w przypadku kolizji podczas ruchu, zwiększając tym samym bezpieczeństwo operacji.

- **Dodanie funkcji ustawiania rzeczywistej prędkości fizycznej dla nowej spirali**:
    Ścieżka: Program nauczania -> Programowanie -> Instrukcja N-Spiral (Nowa spirala).

    Opis: Umożliwia zgodność odcinka jednostajnego prędkości liniowej narzędzia końcowego robota z wartością ustawioną.

- **Funkcja automatycznego załączania po przywróceniu bezpiecznego zatrzymania**:
    Ścieżka: Ustawienia początkowe -> Bezpieczeństwo -> Awaryjne zatrzymanie.

    Opis: Dodanie konfiguracji strategii załączania po resecie awaryjnego zatrzymania w kategorii 1b.

- **Zerowanie z obciążeniem czujnika siły i parametry admitancji dla otwartej zgodności orientacji**:
    Ścieżka: Ustawienia początkowe -> Podstawowe -> Obciążenie, Program nauczania -> Programowanie -> Instrukcja F/T Control.

    Opis: Dodanie parametrów admitancji dla otwartej zgodności orientacji.

- **Dodanie funkcji śledzenia laserowego dla łuku i pełnego okręgu**:

    Opis: Implementacja funkcji śledzenia laserowego w czasie rzeczywistym dla łuku i pełnego okręgu, zmiana orientacji podczas ruchu, możliwość odtwarzania skanowania laserowego dla łuku i pełnego okręgu.

- **Funkcja panelu przyciskowego**:

    Opis: Optymalizacja funkcji resetowania IP panelu przyciskowego w wersji 1.0.

Wersja V3.8.6
-------------

Data: 2025-09-19

- **Dodanie funkcji sterowania impedancją robota**:
    Ścieżka: Program nauczania -> Programowanie -> Instrukcje F/T.

    Opis: Poprzez wykrywanie siły zewnętrznej w czasie rzeczywistym, po osiągnięciu ustawionego progu, robot aktywnie dostosowuje się do siły zewnętrznej, odchylając się od trajektorii ruchu. Gdy siła spadnie poniżej progu, robot wraca na trajektorię, co lepiej realizuje interakcję człowiek-robot.

- **Dodanie funkcji wykrywania momentu obrotowego przed przeciąganiem**:
    Ścieżka: Ustawienia początkowe -> Podstawowe -> Poziom kolizji.

    Opis: Przed wejściem w tryb przeciągania, przeprowadzane jest obliczenie różnicy między instrukcją momentu obrotowego a sprzężeniem zwrotnym dla każdego stawu. W przypadku nieprawidłowej konfiguracji obciążenia lub sposobu instalacji, różnica może przekroczyć próg, uniemożliwiając wejście w tryb przeciągania, co zapobiega utracie kontroli nad robotem po wejściu w tryb przeciągania.

- **Dodanie funkcji spawania z oscylacją niestandardową**:
    Ścieżka: Program nauczania -> Programowanie -> Instrukcja Weave.

    Opis: Użytkownik może samodzielnie zaprojektować wzór oscylacji do spawania z oscylacją.

- **ModbusTCP**:
    Ścieżka: Program nauczania -> Programowanie -> ModbusTCP.

    Opis: Optymalizacja funkcji wykrywania limitu czasu mastera ModbusTCP.

- **Przyssawka pneumatyczna**:
    Ścieżka: Ustawienia początkowe -> Urządzenia peryferyjne -> Przyssawka macierzowa.

    Opis: Optymalizacja funkcji adaptacji strony internetowej dla przyssawki pneumatycznej.

- **Błąd pozycjonowania drutu spawalniczego**:

    Opis: Optymalizacja błędu pozycjonowania drutu spawalniczego w WebAPP – możliwość resetowania.

- **Funkcja konfigurowalnych wejść/wyjść**:

    Opis: Dodanie funkcji konfigurowalnych wejść/wyjść dla FR3C-FR3MT, konfigurowalne wejścia to CI0-CI4, konfigurowalne wyjścia to CO0-CO4.

Wersja V3.8.5
-------------

Data: 2025-08-19

- **Debugowanie sieci Socket**:
    Ścieżka: Program nauczania -> Programowanie -> Debugowanie sieci Socket.

    Opis: Możliwość dodawania, konfigurowania i usuwania konfiguracji połączeń socket. Maksymalna obsługa 4 połączeń socket. Poprzez moduł instrukcji można generować programowanie nauczania: otwieranie połączenia, zamykanie połączenia, wysyłanie danych, odbieranie danych.

- **Funkcja konwersji kodu G wygenerowanego przez CAD na planowanie trajektorii robota**:
    Ścieżka: Aplikacje pomocnicze -> Narzędzia aplikacyjne -> Konwersja kodu G.

    Opis: W oprogramowaniu z funkcjami CAM, takim jak Solidworks, FUSION360, ścieżki obróbki liniowej, łukowej, okręgów, krzywych są konwertowane na plik kodu G, a następnie plik kodu G jest importowany do Web.

- **Dodanie funkcji rzeczywistej prędkości fizycznej dla instrukcji ruchu linii prostej, łuku, pełnego okręgu**:
    Ścieżka: Program nauczania -> Programowanie, Ustawienia początkowe -> Urządzenia peryferyjne -> Uchwyt spawalniczy.

    Opis: Możliwość bezpośredniego zdefiniowania rzeczywistej prędkości fizycznej dla bieżącej instrukcji ruchu.

- **Optymalizacja funkcji regulacji prędkości PTP**:

    Opis: Zapewnienie płynności procesu regulacji prędkości, zmniejszenie wahań prędkości instrukcji w punktach łączenia regulacji.

- **Konfiguracja modelu robota**:

    Opis: Dodanie opcji konfiguracji modelu robota FR30L.

- **Adaptacja skrzynki sterowniczej**:

    Opis: Dodanie adaptacji skrzynki sterowniczej do karty ETMP03E (protokół EtherCAT).

Wersja V3.8.4.1
---------------

Data: 2025-07-30

- **Adaptacja skrzynki sterowniczej do modułu transparentnej transmisji Ethernet oraz funkcja sterowania przyssawką macierzową/chwytakiem**:
    Ścieżka: Ustawienia początkowe -> Urządzenia peryferyjne -> Przyssawka macierzowa.

    Opis: Możliwość sterowania przyssawką macierzową (maksymalnie 20) za pomocą modułu transparentnej transmisji Ethernet na 485, w oparciu o stronę internetową i protokół otwarty urządzeń peryferyjnych.

- **Planowanie trajektorii z wyprzedzeniem robota (wyprzedzenie ze stałą prędkością)**:
    Ścieżka: Program nauczania -> Programowanie, Programowanie graficzne, Programowanie grafem węzłów.

    Opis: Dodanie opcji przełącznika stałej prędkości – po włączeniu robot porusza się ze stałą prędkością z wyprzedzeniem.

- **Optymalizacja funkcji trybu urządzenia podrzędnego skrzynki sterowniczej**:
    Ścieżka: Ustawienia początkowe -> Urządzenia peryferyjne -> Komunikacja kartą, Tryb zdalny.

    Opis: Dodanie adaptacji skrzynki sterowniczej do karty Jiyuan ETMP03E (protokół EtherCAT).

- **Funkcja pobierania pozycji punktu pozycjonowania laserowego**:
    Ścieżka: Ustawienia początkowe -> Urządzenia peryferyjne -> Liniowy czujnik laserowy.

    Opis: Po pomyślnym pozycjonowaniu spoiny laserem, możliwość pobrania danych pozycji przechowywanych w „seamPos” za pomocą instrukcji SDK lub protokołu TCP.

- **Funkcja otwierania prędkości dla FR5 i FR10**:

    Opis: Zwiększenie prędkości liniowej FR5 z 1,0 m/s do 1,7 m/s; prędkości liniowej FR10 z 1,5 m/s do 2,0 m/s.

- **Konfiguracja modelu robota**:

    Opis: Dodanie opcji konfiguracji modelu robota o długim zasięgu ramienia FR5-WML.

- **Optymalizacja aktualizacji oprogramowania**:

    Opis: Skrócenie czasu aktualizacji, zgodność z obniżaniem wersji z wyższej do dowolnej niższej (3.7.6-3.8.4).

- **Optymalizacja przywracania ustawień fabrycznych**:

    Opis: Przywracanie ustawień fabrycznych zachowuje model robota, sztywność, ustawienia dynamiki, wersję panelu przyciskowego itp.

Wersja V3.8.4
-------------

Data: 2025-07-18

- **Implementacja funkcji wygładzania blending dla osi rozszerzonej**:
    Ścieżka: Program nauczania -> Programowanie, Programowanie graficzne, Programowanie grafem węzłów.

    Opis: Implementacja płynnego ruchu między instrukcjami osi rozszerzonej, zwiększenie wydajności pracy.

- **Optymalizacja funkcji trybu urządzenia podrzędnego skrzynki sterowniczej**:
    Ścieżka: Ustawienia początkowe -> Urządzenia peryferyjne -> Komunikacja kartą, Tryb zdalny.

    Opis: Dodanie konfiguracji adresu IP karty, wysyłanie instrukcji LUA z interfejsu, dodanie funkcji automatycznego uruchamiania protokołu urządzenia podrzędnego kontrolera w trybie zdalnym.

- **Adaptacja karty N2L skrzynki sterowniczej dla QX (EtherCAT)**:
    Opis: Karta komunikacyjna magistrali czasu rzeczywistego FAIRINO, karta miniPCIe, obsługuje komunikację protokołem EtherCAT.

- **Ruch JOG robota**:
    Opis: Dodanie funkcji wyjścia stanu CO podczas ruchu JOG robota.

Wersja V3.8.3
-------------

Data: 2025-06-27

- **Funkcja trybu urządzenia podrzędnego skrzynki sterowniczej**:
    Ścieżka: Ustawienia początkowe -> Urządzenia peryferyjne -> Komunikacja kartą.

    Opis: W interfejsie urządzeń peryferyjnych robota dodano moduł konfiguracji komunikacji kartą, umożliwiający interakcję z urządzeniem podrzędnym robota poprzez protokoły EIP, CClink, PN w oparciu o lokalne karty rozszerzające.

- **Dodanie funkcji wykrywania kolizji dla przeciągania wspomaganego czujnikiem siły w trybie ręcznym**:
    Ścieżka: Aplikacje pomocnicze -> Narzędzia aplikacyjne -> Blokada przeciągania -> Blokada wspomagana czujnikiem siły.

    Opis: Po włączeniu funkcji przeciągania wspomaganego czujnikiem siły, gdy robot jest w trybie ręcznym, również uruchamiana jest funkcja wykrywania kolizji, aby uniknąć uszkodzenia urządzenia końcowego.

- **Dodanie funkcji planowania trajektorii z charakterystyką prędkości w kształcie litery T + wygładzanie blending**:
    Ścieżka: Program nauczania -> Programowanie, Programowanie graficzne, Programowanie grafem węzłów.

    Opis: Implementacja płynnego ruchu między instrukcjami ruchu, zwiększenie wydajności pracy.

- **Optymalizacja funkcji interfejsu zapytania o stan w WebApp**:
    Ścieżka: Informacje o stanie -> Zapytanie o stan.

    Opis: Optymalizacja ustawień parametrów zapytania do 6, maksymalny czas przebiegu do 30 sekund, dodanie widoku danych z możliwością kopiowania, dodanie możliwości zmiany nazwy ikony.

- **Optymalizacja siły przeciągania dla wszystkich modeli robotów FR**:
    Ścieżka: Ustawienia początkowe -> Podstawowe -> Stawy -> Kompensacja tarcia -> Kompensacja siły przeciągania.

    Opis: Poprzez dostarczanie momentu kompensacyjnego podczas przeciągania, przeciąganie staje się mniej wymagające siłowo.

- **Optymalizacja funkcji przechowywania dziennika systemowego Web**:
    Opis: Naprawa problemu z nieprawidłowym plikiem dziennika systemowego, ustawienie domyślnego okresu przechowywania dziennika na 7 dni.

Wersja V3.8.2
-------------

Data: 2025-05-29

- **Funkcja adaptacji protokołu otwartego lua końcowego do uchwytu spawalniczego**:
    Ścieżka: Ustawienia początkowe -> Urządzenia peryferyjne -> Uchwyt spawalniczy.

    Opis: Możliwość użycia protokołu otwartego do adaptacji uchwytu spawalniczego smarttool, z obsługą konfiguracji wszystkich parametrów.

- **Dodanie protokołu otwartego dla urządzeń peryferyjnych kontrolera – protokół otwarty spawarki**:
    Ścieżka: Ustawienia początkowe -> Urządzenia peryferyjne -> Spawarka.

    Opis: Możliwość komunikacji i sterowania spawarką za pośrednictwem protokołu otwartego urządzeń peryferyjnych kontrolera (ModbusTCP).

- **Dodanie funkcji wstrzymywania programu LUA**:
    Ścieżka: Program nauczania -> Programowanie.

    Opis: Podczas działania programu nauczania, możliwość wstrzymania w dowolnym wierszu, w tym instrukcji oczekiwania i komunikacyjnych, przy czym czas wstrzymania nie wlicza się do limitu czasu.

- **Dodanie funkcji kształtowania prędkości typu T + Blending**:
    Ścieżka: Program nauczania -> Programowanie, Programowanie graficzne, Programowanie grafem węzłów.

    Opis: Po włączeniu przełącznika kształtowania prędkości typu T, krzywa prędkości staje się płynna. Obecnie obsługiwane typy blending to (PTP-PTP, LIN-LIN, ARC-ARC, LIN-ARC, ARC-LIN).

- **Funkcja adaptacyjnych parametrów FIR + funkcja wstrzymywania i wznawiania FIR**:
    Ścieżka: Program nauczania -> Programowanie, Programowanie graficzne, Programowanie grafem węzłów; Ustawienia początkowe -> Bezpieczeństwo -> Konfiguracja ruchu.

    Opis: Dodanie w funkcji FIR globalnego włączania FIR oraz przełącznika parametrów adaptacyjnych. Po włączeniu, uruchomienie zwykłych instrukcji PTP/LIN/ARC automatycznie przekształca się w planowanie FIR (bez promienia blend).

- **Optymalizacja funkcji Modbus RTU**:
    Ścieżka: Program nauczania -> Programowanie, Programowanie graficzne, Programowanie grafem węzłów; Program nauczania -> Programowanie -> Ustawienia Modbus RTU.

    Opis: Możliwość konfiguracji mastera Modbus RTU w WebApp, konfiguracji prędkości transmisji, trybu parzystości, numeru stacji itp. Możliwość monitorowania wartości w czasie rzeczywistym rejestrów Modbus RTU.

- **Funkcja ochrony miękkim limitem stawu**:
    Ścieżka: Ustawienia początkowe -> Stawy -> Miękki limit.

    Opis: W trybie przeciągania, gdy staw zbliża się do ustawionego miękkiego limitu w interfejsie, pojawia się siła tłumienia, a po usunięciu zewnętrznego momentu obrotowego staw może powrócić do zakresu miękkiego limitu.

- **Funkcja kąta przechyłu bocznego robota podczas oscylacji**:
    Ścieżka: Program nauczania -> Programowanie, Programowanie graficzne, Programowanie grafem węzłów.

    Opis: Obsługa definiowania niestandardowego kąta oscylacji narzędzia końcowego robota wokół kierunku Rx oscylacyjnego układu współrzędnych podczas ruchu oscylacyjnego.

- **Funkcja stopniowego spawania parametrów procesowych**:
    Ścieżka: Program nauczania -> Programowanie, Programowanie graficzne, Programowanie grafem węzłów.

    Opis: Możliwość stopniowej zmiany prędkości posuwu, prądu i napięcia podczas procesu spawania.

- **Funkcja śledzenia łuku z sygnałem analogowym**:
    Ścieżka: Ustawienia początkowe -> Podstawowe -> Ustawienia I/O -> AI.

    Opis: Bezpośrednie połączenie DI, DO, AI, AO skrzynki sterowniczej z portami I/O spawarki w celu realizacji śledzenia łuku opartego na sprzężeniu zwrotnym prądu analogowego.

- **System wtyczek FRCap + funkcja pakietu wtyczek do paletyzacji**:

    Opis: Adaptacja systemu wtyczek FRCap i pakietu wtyczek do paletyzacji dla wersji QX x86. FRCap może współpracować z kontrolerem robota za pośrednictwem dostarczonych oficjalnych interfejsów, lub klient może pisać niestandardowe instrukcje interfejsu i logikę przetwarzania zgodnie z rzeczywistymi potrzebami w celu indywidualnego rozwoju.

- **Model robota i model 3D**:

    Opis: Dodanie konfiguracji modelu robota FR3-C i modelu 3D.

Wersja V3.8.1
-------------

Data: 2025-04-14

- **Optymalizacja funkcji prędkości typu T**:
    Ścieżka: Program nauczania -> Programowanie, Programowanie graficzne, Programowanie grafem węzłów; Ustawienia początkowe -> Moduł podstawowy.

    Opis: Dodanie trybu optymalizacji prędkości trapezowej w konfiguracji ruchu, optymalizacja gwałtowności w fazie uruchamiania i zatrzymywania, zwiększenie przyspieszenia w fazie przyspieszania. Stosowane głównie w warunkach, w których łatwo o kolizję podczas uruchamiania i zatrzymywania oraz w przypadku wyraźnych drgań resztkowych w tych fazach.

- **Optymalizacja funkcji śledzenia taśmociągu**:
    Ścieżka: Aplikacje pomocnicze -> Pakiety procesowe -> Śledzenie taśmociągu.

    Opis: Dodanie funkcji ruchu doganiającego w trybie śledzenia taśmociągu, umożliwiającej definiowanie opóźnienia odległości wyzwalania bez konieczności uczenia ruchu w układzie współrzędnych przedmiotu.

- **Dodanie funkcji sprzężenia zwrotnego impedancji dla strefy interferencji osi**:
    Ścieżka: Ustawienia początkowe -> Bezpieczeństwo -> Strefa interferencji.

    Opis: Podczas przeciągania wspomaganego czujnikiem siły, wejście w strefę interferencji może wywołać efekt sprzężenia zwrotnego impedancji.

- **Funkcja adaptacji uchwytu spawalniczego**:
    Opis: Dodanie adaptacji uchwytu spawalniczego: instalacja uchwytu spawalniczego na końcówce robota umożliwia pisanie programów spawania oraz sterowanie robotem – uruchamianie i zatrzymywanie programu, przełączanie ręczny/automatyczny, przeciąganie itp.

- **Dodanie wyświetlania pierścienia ograniczenia stawu na stronie WEB**:
    Opis: Włączenie funkcji wyświetlania pierścienia ograniczenia umożliwia wyświetlanie pozycji stawu w czasie rzeczywistym.

- **Nowe funkcje SDK**:
    Opis: Dodanie w SDK funkcji pobierania dziennika kontrolera, wszystkich źródeł danych oraz pakietu kopii zapasowej danych.

- **Funkcja rejestrowania informacji o stawach przed i po kolizji**:
    Opis: Rejestrowanie informacji o pozycji, prędkości, przyspieszeniu i momencie obrotowym stawów przed i po kolizji, ułatwiające bezpośrednią analizę przyczyn kolizji na miejscu u klienta.

Wersja V3.8.0
-------------

Data: 2025-03-03

- **Funkcja śledzenia łuku z monotoniczną zmianą przesunięcia i amplitudy oscylacji**:
    Ścieżka: Program nauczania -> Programowanie, Programowanie graficzne, Programowanie grafem węzłów.

    Opis: Szerokość oscylacji w parametrach oscylacji może stopniowo zmieniać się podczas jednego ruchu spawania. Parametr amplitudy na początku segmentu stopniowo przechodzi w amplitudę na końcu segmentu. Środek spawania może aktywnie odchylać się od środka spoiny.

- **Funkcja niestandardowego progu momentu obrotowego wykrywania kolizji**:
    Ścieżka: Program nauczania -> Programowanie, Programowanie graficzne, Programowanie grafem węzłów.

    Opis: Możliwość ustawienia progu momentu obrotowego wykrywania kolizji podczas pracy. Możliwość wyboru progu momentu obrotowego stawu lub progu momentu obrotowego po stronie TCP. Po kolizji informacje takie jak prędkość stawu, przyspieszenie i moment obrotowy są zapisywane w pliku dziennika.

- **Funkcja metody planowania trajektorii z wyprzedzeniem w czasie rzeczywistym**:
    Ścieżka: Program nauczania -> Programowanie, Programowanie graficzne, Programowanie grafem węzłów.

    Opis: Implementacja płynnego łączenia i dopasowywania wielu punktów trajektorii, z prędkością ruchu dostosowującą się adaptacyjnie do krzywizny ścieżki.

- **Opracowanie krzywych obciążenia dla wszystkich modeli serii FR**:
    Opis: Aktualizacja wykresów krzywych obciążenia dla wszystkich modeli serii FR.

- **Optymalizacja logiki przełączania prędkości w trybie redukcji**:
    Opis: W przypadku wystąpienia trybu redukcji, sporadycznie pojawiała się prędkość ruchu znacznie niższa niż prędkość w trybie redukcji – problem został zoptymalizowany i rozwiązany.

- **Optymalizacja punktów nauczania**:
    Opis: Optymalizacja dodawania komunikatów informacyjnych dla punktów nauczania.

- **Funkcja pakietu CNC opartego na FOCAS**:
    Opis: Dodanie funkcji CNC FOCAS.

- **Adaptacja kart do instrukcji urządzenia podrzędnego**:
    Opis: Instrukcje urządzenia podrzędnego dostosowane do kart miniPCIe EnTalk (protokół Profinet, protokół Ethernet/IP, protokół CC-Link IEF Basic) oraz do kart miniPCIe CIFX 9OE-RE/F/PNS (protokół Profinet, protokół Ethernet/IP, protokół Ethercat, protokół CC-Link IEF Basic).

- **Funkcja zwrotna znacznika czasu checkpoint**:
    Opis: Ruch servo J może otrzymać wyniki znacznika czasu, zawierające numer instrukcji oraz znaczniki czasu wysłania, wejścia do kolejki, wyjścia z kolejki i wykonania.

- **Adaptacja czujnika laserowego do protokołu otwartego urządzeń peryferyjnych kontrolera**:
    Opis: Dodanie funkcji komunikacji protokołu otwartego dla urządzenia peryferyjnego lasera.

Wersja V3.7.8
-------------

Data: 2025-01-20

- **Funkcja stałego śledzenia punktowego dla osi rozszerzonej z danymi laserowymi**:
    Ścieżka: Program nauczania -> Programowanie, Programowanie graficzne, Programowanie grafem węzłów; Ustawienia początkowe -> Urządzenia peryferyjne -> Liniowy czujnik laserowy.

    Opis: Głównie do śledzenia punktowego w czasie rzeczywistym dla pozycjonera, umożliwiając kompensację odchylenia przedmiotu rejestrowanego przez laser podczas ruchu osi rozszerzonej na końcówce narzędzia robota.

- **Dodanie i optymalizacja funkcji konfiguracji CI robota**:
    Ścieżka: Ustawienia początkowe -> Podstawowe -> Ustawienia I/O -> DI; Program nauczania -> Programowanie, Programowanie graficzne, Programowanie grafem węzłów.

    Opis: 1. Dodanie funkcji przełączania robota między trybem ręcznym a automatycznym za pomocą poziomu wysokiego/niskiego w konfigurowalnych wejściach CI. Po skonfigurowaniu portu CI jako „Przełączanie ręczny/automatyczny (poziom wysoki/niski)”, gdy sygnał wejściowy na tym porcie jest aktywny, robot automatycznie przełącza się w tryb automatyczny; gdy sygnał wejściowy jest nieaktywny, robot automatycznie przełącza się w tryb ręczny. 2. Po otwarciu programu LUA w WebApp, uruchomienie LUA za pomocą konfigurowalnego CI powoduje automatyczne uruchomienie aktualnie otwartego programu LUA, a nie ostatnio zapisanego programu.

- **Optymalizacja funkcji zapytania o stan w WebApp**:
    Ścieżka: Informacje o stanie -> Zapytanie o stan.

    Opis: Sposób interakcji danych między frontendem a backendem został zmieniony z metody żądań pollingowych frontendu na metodę aktywnego wysyłania danych przez websocket, co zmniejsza wykorzystanie CPU.

- **Funkcja konfigurowalnego wysokiego/niskiego aktywnego poziomu wyjścia DO przy uruchomieniu oprogramowania sprzętowego skrzynki sterowniczej**:
    Ścieżka: Ustawienia początkowe -> Podstawowe -> Ustawienia I/O -> DO.

    Opis: Dodanie konfiguracji „Wyjście DO skrzynki sterowniczej podczas zasilania”. Przed załączeniem robota, wyjścia DO skrzynki sterowniczej mogą być skonfigurowane do wymaganego stanu wysokiego/niskiego poziomu w zależności od konkretnego scenariusza użycia.

- **Funkcja metody planowania trajektorii z wyprzedzeniem w czasie rzeczywistym**:
    Ścieżka: Program nauczania -> Programowanie, Programowanie graficzne, Programowanie grafem węzłów.

    Opis: Dodanie instrukcji „TrajectoryLA”.

- **Funkcja strategii po kolizji oparta na czujniku siły**:
    Ścieżka: Ustawienia początkowe -> Stawy -> Poziom kolizji.

    Opis: Dodanie parametru „Prędkość bezpieczeństwa” w trybie odbicia kolizyjnego.

- **Funkcja automatycznego unoszenia robota po kolizji wykrytej przez czujnik siły**:
    Opis: Implementacja funkcji automatycznego unoszenia robota po wykryciu kolizji przez czujnik siły, z możliwością ograniczenia prędkości podczas unoszenia.

- **Opracowanie krzywych obciążenia dla wszystkich modeli serii FR**:
    Opis: Aktualizacja wykresów krzywych obciążenia dla wszystkich modeli serii FR.

Wersja V3.7.7
-------------

Data: 2024-12-30

- **Funkcja monitorowania w czasie rzeczywistym danych stanu chwytaka**:
    Ścieżka: Ustawienia początkowe -> Urządzenia peryferyjne -> Chwytak -> Monitorowanie stanu.

    Opis: Wyświetlanie w czasie rzeczywistym informacji o stanie chwytaka, takich jak prędkość robocza, moment obrotowy, pozycja.

- **Funkcja zbierania danych awaryjnych kontrolera**:
    Ścieżka: Ustawienia systemowe -> Ustawienia ogólne -> Dane awaryjne.

    Opis: W przypadku wystąpienia awarii robota, takich jak kolizja, błąd punktu instrukcji, kontroler automatycznie rejestruje informacje o stanie robota (pozycja, prędkość itp.) z 15 sekund przed i po awarii. WebApp umożliwia eksport informacji o awarii w formacie .csv, co pomaga w analizie i diagnozowaniu przyczyn awarii.

- **Funkcja unikania i przechodzenia przez punkty osobliwe podczas przeciągania wspomaganego czujnikiem siły**:
    Ścieżka: Aplikacje pomocnicze -> Narzędzia aplikacyjne -> Blokada przeciągania -> Blokada wspomagana czujnikiem siły.

    Opis: 1. W interfejsie przeciągania wspomaganego czujnikiem siły, wybór strategii „unikaj” powoduje generowanie wirtualnej siły podczas zbliżania się robota do punktu osobliwego. 2. Wybór strategii „przechodź” powoduje przełączenie w tryb przeciągania przy zbliżaniu się do punktu osobliwego, a po oddaleniu się od punktu osobliwego powrót do przeciągania wspomaganego czujnikiem siły.

- **Funkcja adaptacji starej dynamiki do instalacji pod dowolnym kątem 360° oraz funkcja importu pakietu kopii zapasowej dostosowująca się do dynamiki**:
    Ścieżka: Ustawienia początkowe -> Podstawowe -> Instalacja; Aplikacje pomocnicze -> Narzędzia aplikacyjne -> Kopia zapasowa danych.

    Opis: Podczas importu pakietu kopii zapasowej dodano walidację typu robota, sposobu instalacji, kąta instalacji i typu konfiguracji dynamiki. W przypadku niezgodności powyższych parametrów wyświetlany jest komunikat zabraniający importu.

- **Funkcja przechodzenia przez punkty osobliwe w trybie automatycznym**:
    Ścieżka: Program nauczania -> Urządzenia peryferyjne -> Instrukcje LIN/ARC.

    Opis: Dodano konfigurację zabezpieczenia ruchu „Przechodzenie przez punkt osobliwy”.

- **Funkcja automatycznej aktualizacji programu LUA odpowiadającego punktowi po zapisie punktu przyciskiem końcowym**:
    Ścieżka: Program nauczania -> Programowanie -> Punkty nauczania.

    Opis: Dodano funkcję automatycznej aktualizacji programu LUA odpowiadającego punktowi po zapisie punktu przyciskiem końcowym.

- **Optymalizacja interfejsu zapytania o stan**:
    Ścieżka: Informacje o stanie -> Zapytanie o stan.

    Opis: Optymalizacja interfejsu użytkownika i interakcji w interfejsie zapytania o stan.

- **Optymalizacja interfejsu WebApp i panelu operatorskiego**:
    Opis: Dodanie interfejsów wyświetlania w języku rosyjskim i chińskim tradycyjnym dla WebApp i panelu operatorskiego.

- **Funkcja optymalizacji wyświetlania interfejsu WebApp**:
    Opis: Dodanie wyświetlania wersji oprogramowania i modelu robota w lewym dolnym rogu interfejsu WebApp.

- **Funkcja śledzenia laserowego dla osi rozszerzonej**:
    Opis: 1. Robot porusza się synchronicznie z zewnętrzną osią, a laser realizuje synchroniczne śledzenie w układzie współrzędnych zewnętrznej osi. 2. Robot porusza się asynchronicznie z zewnętrzną osią, a laser może śledzić w podstawowym układzie współrzędnych robota lub w układzie współrzędnych zewnętrznej osi.

- **Funkcja przeciągania punktu narzędzia oparta na czujniku siły**:
    Opis: W interfejsie web, po ustawieniu układu odniesienia FT jako niestandardowego układu współrzędnych i włączeniu przeciągania wspomaganego czujnikiem siły, robot porusza się wzdłuż ustawionego układu współrzędnych narzędzia.

- **Funkcja CNDE robota**:
    Opis: Klient może za pośrednictwem CNDE pobierać informacje zwrotne o stanie robota i wysyłać dane sterujące do robota (komunikacja UDP). Cykl informacji zwrotnej o stanie można konfigurować (1-200 ms). Treść danych zwrotnych o stanie robota i treść danych wejściowych klienta sterujących robotem można swobodnie konfigurować.

Wersja V3.7.6
-------------

Data: 2024-11-18

- **Optymalizacja układu strony Ustawienia początkowe**:
    Ścieżka: Ustawienia początkowe.

    Opis: Optymalizacja interfejsu ustawiania narzędzi, interfejsu konfiguracji obciążenia oraz wyświetlania ikon niektórych funkcji.

- **Optymalizacja interakcji funkcji konfiguracji osi rozszerzonej urządzeń peryferyjnych WebApp**:
    Ścieżka: Ustawienia początkowe -> Urządzenia peryferyjne -> Oś rozszerzona.

    Opis: Optymalizacja układu i interakcji interfejsu osi rozszerzonej.

- **Optymalizacja funkcji dziennika systemowego**:
    Ścieżka: Informacje o stanie -> Dziennik systemowy.

    Opis: Dodanie podziału dziennika na strony oraz rozróżnienia kategorii szczegółowych operacji dziennika.

- **Funkcja stałej siły szlifowania w kierunkach X i Y**:
    Ścieżka: Program nauczania -> Programowanie -> Zestaw sterowania siłą -> Instrukcja F/T_Control.

    Opis: Dodanie parametru „Promień tarczy szlifierskiej”, umożliwiającego wykonywanie powtarzalnych ruchów liniowych/krzywoliniowych po powierzchni przedmiotu.

- **Funkcja ruchu pobierania punktów laserem**:
    Ścieżka: Aplikacje pomocnicze -> Narzędzia aplikacyjne -> Generowanie punktu przecięcia.

    Opis: Dodanie możliwości użycia instrukcji skryptu lua dla funkcji obliczania współrzędnych punktu przecięcia z trzech i czterech punktów pozycjonujących.

- **Funkcja konfiguracji zewnętrznej osi – wózek o dwóch stopniach swobody**:
    Ścieżka: Ustawienia początkowe -> Urządzenia peryferyjne -> Oś rozszerzona.

    Opis: Dodanie schematu osi rozszerzonej „wózek o dwóch stopniach swobody”. Komunikacja między robotem a PLC odbywa się przez UDP, a PLC steruje wózkiem o dwóch stopniach swobody przez EtherCat.

- **Funkcja metody kalibracji TCP za pomocą narzędzia płytkowego**:
    Ścieżka: Ustawienia początkowe -> Układy współrzędnych -> Współrzędne narzędzia.

    Opis: Dodanie metody kalibracji układu współrzędnych „Kalibracja narzędziem płytkowym”.

- **Funkcja programu robota działającego w tle**:
    Ścieżka: Program nauczania -> Programowanie.

    Opis: Program działający w tle może normalnie pobierać dane z interfejsów I/O, w tym systemowych I/O, modbus, rozszerzonych I/O.

- **Funkcja automatycznego omijania punktów osobliwych trajektorii robota**:
    Ścieżka: Program nauczania -> Programowanie -> Instrukcje linii prostej Lin / łuku Arc.

    Opis: Dodanie konfiguracji zabezpieczenia ruchu „Omijanie punktu osobliwego”.

- **Funkcja adaptacji końcowej chwytaka obrotowego**:
    Ścieżka: Ustawienia początkowe -> Urządzenia peryferyjne -> Chwytak.

    Opis: Dodanie konfiguracji kodów funkcji związanych z chwytakiem obrotowym.

- **Niestandardowe instrukcje urządzenia podrzędnego protokołu**:
    Ścieżka: Tryb zdalny.

    Opis: Dodanie konfiguracji „Protokół urządzenia podrzędnego kontrolera”.

- **Funkcja pozycjonowania drutu spawalniczego przez komunikację UDP**:

    Opis: Robot może sterować uruchamianiem/zatrzymywaniem pozycjonowania drutu spawalniczego oraz pobierać sygnał pomyślnego pozycjonowania drutu spawalniczego za pośrednictwem rozszerzonych wejść/wyjść UDP.

- **Optymalizacja funkcji pakietu kopii zapasowej**:

    Opis: Obsługa importu i używania pakietów danych ze starszych wersji (pakiety danych z QX 3.6.1 i nowszych).

- **Optymalizacja funkcji przywracania ustawień fabrycznych**: Dodanie walidacji plików, zwiększenie stabilności przywracania ustawień fabrycznych systemu.

    Opis: Dodanie walidacji plików, zwiększenie stabilności przywracania ustawień fabrycznych systemu.

- **Optymalizacja funkcji aktualizacji**:

    Opis: Wersje QX 3.6.9 i nowsze można bezpośrednio aktualizować do QX 3.7.6, a po aktualizacji dane użytkownika z bieżącej wersji są zachowywane.

- **Funkcja obniżania wersji strony**:

    Opis: Strona WebApp obsługuje obniżanie wersji do dowolnej wersji od QX 3.6.9 wzwyż, a po obniżeniu wersji dane użytkownika z bieżącej wersji są zachowywane.

Wersja V3.7.5
-------------

Data: 2024-09-30

- **Funkcja regulowanej prędkości kątowej przejścia w pakiecie kątowym**:
    Ścieżka: Program nauczania -> Programowanie -> Instrukcja linii prostej Lin.

    Opis: Dodanie konfiguracji zabezpieczenia ruchu „Regulowana prędkość kątowa punktu przejściowego”.

- **Funkcja spawania wielowarstwowego i wielościeżkowego ze śledzeniem łuku**:
    Ścieżka: Aplikacje pomocnicze -> Pakiety procesowe -> Baza wiedzy spawalniczej -> Spawanie wielowarstwowe i wielościeżkowe.

    Opis: Dodanie konfiguracji „Funkcji oscylacji w pierwszej warstwie” i „Funkcji śledzenia łuku”.

- **Funkcja konfiguracji osi rozszerzonej 485**:
    Ścieżka: Ustawienia początkowe -> Urządzenia peryferyjne -> Oś rozszerzona.

    Opis: Dodanie konfiguracji „Przyspieszenie i zatrzymanie awaryjne”.

- **Funkcja automatycznej kalibracji TCP narzędzia robota (własny sprzęt światłowodowy)**:
    Ścieżka: Ustawienia początkowe -> Podstawowe -> Współrzędne narzędzia.

    Opis: Dodanie kalibracji układu współrzędnych „Automatyczna kalibracja fotoelektryczna”.

- **Funkcja ustawień wielojęzycznych panelu operatorskiego**:
    Ścieżka: Strona logowania.

    Opis: Dodanie konfiguracji „Przełączanie języka”.

Wersja V3.7.4
-------------

Data: 2024-08-09

- **Funkcja oprogramowania protokołu otwartego lua końcowego (część chwytaka)**:
    Ścieżka: Ustawienia początkowe -> Urządzenia peryferyjne -> Chwytak.

    Opis: Dodanie konfiguracji „Włączenie protokołu końcowego”.

- **Funkcja oscylacji skośnej piłokształtnej**:
    Ścieżka: Program nauczania -> Programowanie -> Instrukcja oscylacji Weave.

    Opis: Dodanie konfiguracji parametru „Azymut kierunku oscylacji”.

- **Optymalizacja funkcji pakietu spawalniczego robota**:
    Ścieżka: Ustawienia początkowe -> Urządzenia peryferyjne -> Spawarka -> Konfiguracja spawarki.

    Opis: Dodanie konfiguracji „Parametry procesu spawania”.

- **Funkcja obsługi przekroczenia prędkości stawu w instrukcji Lin**:
    Ścieżka: Program nauczania -> Programowanie -> Instrukcja linii prostej Lin.

    Opis: Dodanie konfiguracji zabezpieczenia ruchu „Ochrona przed przekroczeniem prędkości stawu”.

Wersja V3.7.3
-------------

Data: 2024-06-28

- **Funkcja sterowania robotem z poziomu urządzenia podrzędnego Modbus**:
    Ścieżka: Program nauczania -> Programowanie -> ModbusTCP.

    Opis: Dodanie konfiguracji „Kontroler podrzędny”.

- **Funkcja typu awaryjnego zatrzymania**:
    Ścieżka: Ustawienia początkowe -> Bezpieczeństwo -> Awaryjne zatrzymanie.

    Opis: Dodanie typów zatrzymania „typ 1a, typ 2a, typ 2”.

Wersja V3.7.2
-------------

Data: 2024-06-07

- **Funkcja konfiguracji protokołu otwartego Lua końcowego**:
    Ścieżka: Ustawienia początkowe -> Urządzenia peryferyjne -> Narzędzie końcowe -> Protokół otwarty.

    Opis: Dodanie konfiguracji „Protokół otwarty”.

- **Funkcja instrukcji sterowania ruchem AO**:
    Ścieżka: Program nauczania -> Programowanie.

    Opis: Dodanie „Instrukcji ruchomego AO”.

- **Funkcja mieszanego przeciągania z użyciem 6-osiowej siły i impedancji stawu**:
    Ścieżka: Aplikacje pomocnicze -> Narzędzia aplikacyjne -> Blokada przeciągania.

    Opis: Dodanie „Mieszanego przeciągania z użyciem 6-osiowej siły i impedancji stawu”.

- **Funkcja strategii reakcji po kolizji**:
    Ścieżka: Ustawienia początkowe -> Podstawowe -> Stawy -> Poziom kolizji.

    Opis: Dodanie konfiguracji „Strategia kolizji”.

- **Funkcja pierwszej aktywacji robota**:
    Ścieżka: Ustawienia logowania.

    Opis: Dodanie funkcji weryfikacji pierwszej aktywacji robota.

Wersja V3.7.1
-------------

Data: 2024-05-10

- **Funkcja blokowania interfejsu web**:
    Ścieżka: Ustawienia systemowe -> Informacje niestandardowe.

    Opis: Dodanie konfiguracji „Blokada ekranu interfejsu web”.

- **Funkcja obliczania współrzędnych punktu przecięcia z trzech i czterech punktów do pozycjonowania**:
    Ścieżka: Aplikacje pomocnicze -> Narzędzia aplikacyjne -> Generowanie punktu przecięcia.

    Opis: Dodanie „Funkcji obliczania współrzędnych punktu przecięcia z trzech i czterech punktów do pozycjonowania”.

- **Optymalizacja orientacji ruchu spawania odcinkowego**:
    Ścieżka: Program nauczania -> Programowanie -> Instrukcja Segment.

    Opis: Dodanie konfiguracji „Tryb spawania odcinkowego”.

- **Funkcja wirtualnej ściany oparta na czujniku siły**:
    Ścieżka: Ustawienia początkowe -> Urządzenia peryferyjne -> Czujnik siły; Aplikacje pomocnicze -> Narzędzia aplikacyjne -> Blokada przeciągania.

    Opis: Dodanie parametrów konfiguracyjnych związanych z „czujnikiem siły” w konfiguracji urządzeń peryferyjnych końcowych. Dodanie konfiguracji „Współczynnik bezwładności” w blokadzie wspomaganej czujnikiem siły.

- **Nowa funkcja łącząca SmartTool i czujnik siły**:
    Ścieżka: Ustawienia początkowe -> Urządzenia peryferyjne -> Uchwyt spawalniczy.

    Opis: Dodanie konfiguracji funkcji przycisków.