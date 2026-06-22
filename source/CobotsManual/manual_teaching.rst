Ręczne uczenie robota
=====================

Ręczne uczenie i zapisywanie punktów uczenia
--------------------------------------------

Ręczne uczenie obejmuje dwa sposoby:

- 1. Przytrzymanie przycisku przeciągania na końcówce w celu wykonania przeciągania uczącego;
- 2. Punktowanie w trójwymiarowej symulacji robota -> operacje na obiekcie trójwymiarowym.

Po wyuczeniu pozycji docelowej można zapisać punkt uczenia w "Funkcje dodatkowe robota" -> "Zapis punktu uczenia". Podczas zapisywania punktu uczenia, układ współrzędnych tego punktu uczenia jest układem współrzędnych aktualnie stosowanym przez robota.

.. image:: teaching_pendant_software/056.png
   :width: 6in
   :align: center

.. centered:: Wykres 4.1‑1 Ręczne uczenie

Przeglądanie informacji o punktach uczenia
------------------------------------------

Kliknięcie "Program uczenia" -> "Punkty uczenia" spowoduje wyświetlenie wszystkich zapisanych informacji o punktach uczenia. Bieżący tryb punktów dzieli się na "Tryb systemowy" i "Tryb tabeli punktów".

W tym interfejsie można importować i eksportować pliki punktów uczenia. Po wybraniu punktu uczenia i kliknięciu przycisku "Usuń" można usunąć informacje o tym punkcie. Wartości x, y, z, rx, ry, rz i v punktu uczenia można modyfikować. Wprowadź nowe wartości, zaznacz pole wyboru po lewej stronie, a następnie kliknij przycisk "Modyfikuj" u góry, aby zmodyfikować informacje o punkcie uczenia.

Kliknięcie przycisku "Rozpocznij działanie" spowoduje uruchomienie pojedynczego punktu uczenia lokalnego, przesuwając robota do pozycji tego punktu. Ponadto użytkownik może wyszukiwać punkty uczenia według nazwy.

.. image:: points/001.png
   :width: 6in
   :align: center

.. centered:: Wykres 4.2‑1 Interfejs zarządzania punktami uczenia

.. important:: 
    Zmodyfikowane wartości x, y, z, rx, ry, rz punktu uczenia nie mogą przekraczać zakresu roboczego robota.