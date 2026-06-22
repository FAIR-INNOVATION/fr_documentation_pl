Ustawianie parametrów robota
============================

Ustawienie sposobu instalacji
-----------------------------

Domyślnym sposobem instalacji robota jest instalacja pozioma. Gdy sposób instalacji robota zostanie zmieniony, należy niezwłocznie ustawić rzeczywisty sposób instalacji robota w menu "Ustawienia początkowe" -> "Podstawowe" -> "Instalacja", aby zapewnić prawidłowe działanie robota.

Biorąc pod uwagę bardziej elastyczne i bogate scenariusze wdrażania robota, udostępniliśmy funkcję swobodnej instalacji. Użytkownik klika "Ustawienia początkowe" -> "Podstawowe" -> "Instalacja", aby przejść do strony ustawiania sposobu instalacji robota. Ręczna regulacja kąta "Nachylenie podstawy" i "Obrót podstawy" spowoduje odpowiednie wyświetlenie efektu instalacji w modelu trójwymiarowym. Po modyfikacji kliknij przycisk "Zastosuj", aby zakończyć ustawianie sposobu instalacji robota.

.. image:: teaching_pendant_software/026.png
   :width: 6in
   :align: center
   
.. centered:: Wykres 3.1-1 Instalacja robota

.. important::
    Po zakończeniu instalacji robota należy prawidłowo ustawić sposób instalacji robota. W przeciwnym razie wpłynie to na funkcję przeciągania robota oraz funkcję wykrywania kolizji.

Ustawienie obciążenia końcówki
------------------------------

W "Ustawienia początkowe" -> "Podstawowe" -> "Obciążenie", w typie identyfikacji "Identyfikacja trajektorii", przejdź do interfejsu ustawiania obciążenia końcówki.

.. note:: 
   .. image:: base/071.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nazwa: **Przycisk Zastosuj**
   
   Funkcja: Kliknięcie powoduje zastosowanie masy obciążenia i współrzędnych środka ciężkości odpowiadających numerowi obciążenia

.. note:: 
   .. image:: base/072.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nazwa: **Przycisk Modyfikuj**
   
   Funkcja: Kliknięcie otwiera/zamyka interfejs ruchu identyfikacyjnego

.. note:: 
   .. image:: base/073.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nazwa: **Przycisk Zmień nazwę**
   
   Funkcja: Zmienia nazwę obciążenia

.. note:: 
   .. image:: base/074.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nazwa: **Przycisk Wyczyść**
   
   Funkcja: Czyści bieżące informacje o obciążeniu (masa obciążenia i współrzędne środka ciężkości są zerowane)

Podczas konfigurowania obciążenia końcówki można bezpośrednio wprowadzić masę narzędzia końcowego oraz odpowiadające mu współrzędne środka ciężkości X, Y i Z, a następnie kliknąć przycisk "Zastosuj", aby je ustawić.

Jednocześnie można kliknąć przycisk "Edytuj", aby otworzyć interfejs "Ruch identyfikacyjny" i przeprowadzić automatyczną identyfikację obciążenia. Po zakończeniu identyfikacji należy zastosować wyniki.

.. important:: 
    Masa obciążenia nie może przekraczać maksymalnego zakresu obciążenia robota. Obciążenia dla poszczególnych modeli są następujące:

   - FR3: 3 kg

   - FR5: 5 kg

   - FR10: 10 kg

   - FR16: 16 kg
   
   - FR20: 20 kg
   
   - FR30: 30 kg

   Zakres ustawiania współrzędnych środka ciężkości wynosi 0-1000, jednostka mm.

.. image:: base/016.png
   :width: 4in
   :align: center

.. centered:: Wykres 3.2-1 Schemat ustawiania obciążenia
    
.. important:: 
    Po zamontowaniu obciążenia na końcówce robota należy prawidłowo ustawić masę obciążenia końcówki oraz współrzędne środka ciężkości. W przeciwnym razie wpłynie to na funkcję przeciągania robota oraz funkcję wykrywania kolizji.

Ustawienie współrzędnych narzędzia
----------------------------------

W menu "Ustawienia początkowe" -> "Podstawowe" -> "Współrzędne narzędzia" przejdź do strony współrzędnych narzędzia.

.. note:: 
   .. image:: base/071.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nazwa: **Przycisk Zastosuj**
   
   Funkcja: Kliknięcie powoduje zastosowanie układu współrzędnych narzędzia

.. note:: 
   .. image:: base/072.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nazwa: **Przycisk Modyfikuj**
   
   Funkcja: Kliknięcie otwiera/zamyka interfejs kalibracji układu współrzędnych

.. note:: 
   .. image:: base/073.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nazwa: **Przycisk Zmień nazwę**
   
   Funkcja: Zmienia nazwę układu współrzędnych narzędzia

.. note:: 
   .. image:: base/074.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nazwa: **Przycisk Wyczyść**
   
   Funkcja: Czyści bieżące informacje o współrzędnych narzędzia

Współrzędne narzędzia umożliwiają modyfikację, czyszczenie i zastosowanie współrzędnych narzędzia. Na liście rozwijanej układów współrzędnych narzędzia, po wybraniu odpowiedniego układu współrzędnych, poniżej wyświetlone zostaną odpowiadające mu wartości współrzędnych (nazwa układu współrzędnych może być dostosowana przez użytkownika), typ narzędzia oraz pozycja instalacji (wyświetlana tylko dla narzędzi typu czujnikowego). Po wybraniu układu współrzędnych kliknij przycisk "Zastosuj", a aktualnie używany układ współrzędnych narzędzia zmieni się na wybrany układ współrzędnych, jak pokazano poniżej.

.. image:: base/001.png
   :width: 4in
   :align: center
   
.. centered:: Wykres 3.3-1 Ustawianie współrzędnych narzędzia

Kliknij "Modyfikuj", aby ponownie ustawić układ współrzędnych narzędzia o danym numerze zgodnie z instrukcjami. Metody kalibracji narzędzia dzielą się na metodę czteropunktową i metodę sześciopunktową. Metoda czteropunktowa kalibruje tylko TCP narzędzia, czyli pozycję środka punktu narzędzia, a jego orientacja jest domyślnie zgodna z orientacją końcówki. Metoda sześciopunktowa dodaje dwa punkty do metody czteropunktowej w celu kalibracji orientacji narzędzia.

.. image:: base/002.png
   :width: 4in
   :align: center

.. centered:: Wykres 3.3-2 Kalibracja układu współrzędnych narzędzia

.. important:: 
    1. Po zamontowaniu narzędzia na końcówce konieczna jest kalibracja i zastosowanie układu współrzędnych narzędzia. W przeciwnym razie pozycja i orientacja środka punktu narzędzia podczas wykonywania przez robota instrukcji ruchu nie będą zgodne z oczekiwanymi wartościami.

    2. Układ współrzędnych narzędzia jest zwykle używany jako toolcoord1~toolcoord19. Zastosowanie toolcoord0 oznacza, że środek TCP narzędzia znajduje się w środku kołnierza końcówki. Podczas kalibracji układu współrzędnych narzędzia należy najpierw zastosować układ współrzędnych narzędzia do toolcoord0, a następnie wybrać inny układ współrzędnych narzędzia do kalibracji i zastosowania.