Format protokołu ramki danych CNDE
==================================

Protokół komunikacyjny CNDE robota współpracującego jest następujący. Zarówno dane wysyłane przez klienta do robota, jak i dane zwracane przez robota do klienta muszą być zgodne z tym protokołem. Protokół rozróżnia różne funkcje ramek danych za pomocą typu ramki. Definicje typów ramek podano w Tabeli 2-2. Różne typy ramek odpowiadają różnym treściom danych. Szczegółowe definicje treści danych podano w Tabelach 3-1 do 3-7.

.. centered:: Tabela 2-1 Format ramki danych CNDE robota

.. list-table::
   :widths: 20 20 20 20 20 20 20
   :header-rows: 0
   :align: center
   :class: sheet-center

   * - **Nazwa**
     - **Nagłówek ramki**
     - **Licznik ramki**
     - **Typ ramki**
     - **Długość danych**
     - **Treść**
     - **Stopka ramki**
   
   * - **Długość (bajt)**
     - 2
     - 1
     - 1
     - 2
     - --
     - 2
   
   * - **Treść**
     - 0x5A5A
     - 0 ~ 255
     - 0 ~ 8
     - Liczba bajtów „Treści danych”
     - Treść ramki danych
     - 0xA5A5

.. centered:: Tabela 2-2 Typy ramek danych CNDE robota

.. list-table::
   :widths: 40 20 40
   :header-rows: 0
   :align: center
   :class: sheet-center

   * - **Typ**
     - **Wartość**
     - **Kierunek ramki danych**

   * - Ramka konfiguracji wejść (konfiguracja sterowania)
     - 0x00
     - Klient -> Robot

   * - Ramka konfiguracji wyjść (konfiguracja stanu)
     - 0x01
     - Klient -> Robot

   * - Uruchomienie wyjścia CNDE
     - 0x02
     - Klient -> Robot

   * - Zatrzymanie wyjścia CNDE
     - 0x03
     - Klient -> Robot

   * - Ramka danych wyjściowych (dane stanu)
     - 0x04
     - Robot -> Klient

   * - Ramka danych wejściowych (dane sterowania)
     - 0x05
     - Klient -> Robot

   * - Komunikat ostrzegawczy typu string
     - 0x06
     - Klient -> Robot, Robot -> Klient

   * - Ustawienie numeru wersji protokołu CNDE robota
     - 0x07
     - Klient -> Robot

   * - Pobranie wersji oprogramowania i oprogramowania sprzętowego robota
     - 0x08
     - Klient -> Robot, Robot -> Klient