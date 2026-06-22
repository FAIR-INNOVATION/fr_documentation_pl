Szybkie programowanie robota
============================

Wprowadzenie do prostych instrukcji ruchu
-----------------------------------------

**Polecenie PTP**: Kliknij ikonę "Punkt-punkt", aby przejść do interfejsu edycji polecenia PTP.

Można wybrać punkt docelowy. Ustawienie czasu wygładzenia przejścia umożliwia ciągły ruch od tego punktu do następnego. Ustawienie przesunięcia umożliwia wybór przesunięcia względem podstawowego układu współrzędnych lub względem układu współrzędnych narzędzia, a następnie pojawia się okno ustawień wartości przesunięcia x, y, z, rx, ry, rz. Konkretna ścieżka PTP jest optymalną ścieżką automatycznie planowaną przez kontroler ruchu. Po kliknięciu "Dodaj" i "Zastosuj" instrukcja może zostać zapisana.

.. image:: teaching_pendant_software/055.png
   :width: 6in
   :align: center

.. centered:: Wykres 5.1‑1 Interfejs polecenia PTP

**Polecenie Lin**: Kliknij ikonę "Linia prosta", aby przejść do interfejsu edycji polecenia Lin.

Funkcja tej instrukcji jest podobna do instrukcji "PTP", ale ścieżka do punktu docelowego w tej instrukcji jest linią prostą.

.. image:: teaching_pendant_software/057.png
   :width: 6in
   :align: center

.. centered:: Wykres 5.1‑2 Interfejs polecenia Lin

Operacje na plikach programu
----------------------------

Użyj paska narzędzi u góry drzewa programu, aby modyfikować drzewo programu.

.. note:: 
   .. image:: coding/006.png
      :height: 0.75in
      :align: left

   Nazwa: **Otwórz**
   
   Funkcja: Otwiera plik programu użytkownika

.. note:: 
   .. image:: coding/007.png
      :height: 0.75in
      :align: left

   Nazwa: **Nowy**
   
   Funkcja: Wybiera szablon i tworzy nowy plik programu
   
.. note:: 
   .. image:: coding/008.png
      :height: 0.75in
      :align: left

   Nazwa: **Importuj**
   
   Funkcja: Importuje plik do folderu programów użytkownika

.. note:: 
   .. image:: coding/009.png
      :height: 0.75in
      :align: left

   Nazwa: **Eksportuj**
   
   Funkcja: Eksportuje plik programu użytkownika na komputer lokalny

.. note:: 
   .. image:: coding/010.png
      :height: 0.75in
      :align: left

   Nazwa: **Zapisz**
   
   Funkcja: Zapisuje edytowaną treść pliku.

.. note:: 
   .. image:: coding/011.png
      :height: 0.75in
      :align: left

   Nazwa: **Zapisz jako**
   
   Funkcja: Zmienia nazwę pliku i zapisuje go w folderze programów użytkownika lub programów szablonowych

.. note:: 
   .. image:: coding/012.png
      :height: 0.75in
      :align: left

   Nazwa: **Kopiuj**
   
   Funkcja: Kopiuje węzeł i umożliwia użycie go w innych operacjach (np. wklejenie go w inne miejsce w drzewie programu)

.. note:: 
   .. image:: coding/013.png
      :height: 0.75in
      :align: left

   Nazwa: **Wklej**
   
   Funkcja: Umożliwia wklejenie wcześniej wyciętego lub skopiowanego węzła

.. note:: 
   .. image:: coding/014.png
      :height: 0.75in
      :align: left

   Nazwa: **Wytnij**
   
   Funkcja: Wycina węzeł i umożliwia użycie go w innych operacjach (np. wklejenie go w inne miejsce w drzewie programu)

.. note:: 
   .. image:: coding/015.png
      :height: 0.75in
      :align: left

   Nazwa: **Usuń**
   
   Funkcja: Usuwa węzeł z drzewa programu

.. note:: 
   .. image:: coding/016.png
      :height: 0.75in
      :align: left

   Nazwa: **Przesuń w górę**
   
   Funkcja: Przesuwa węzeł w górę

.. note:: 
   .. image:: coding/017.png
      :height: 0.75in
      :align: left

   Nazwa: **Przesuń w dół**
   
   Funkcja: Przesuwa węzeł w dół

.. note:: 
   .. image:: coding/018.png
      :height: 0.75in
      :align: left

   Nazwa: **Przełącz tryb edycji**
   
   Funkcja: Przełącza między trybem drzewa programu a trybem edycji lua

Tworzenie i uruchamianie programu
---------------------------------

Po lewej stronie głównie dodaje się polecenia programu. Kliknij ikonę nad słowem kluczowym, aby przejść do szczegółowego interfejsu dodawania polecenia programu po prawej stronie. Operacje dodawania polecenia programu do pliku dzielą się głównie na dwa typy:

- 1. Otwórz odpowiednią instrukcję i kliknij przycisk "Zastosuj", aby dodać tę instrukcję do programu.
- 2. Najpierw kliknij przycisk "Dodaj", wtedy polecenie nie zostało jeszcze zapisane w pliku programu, a następnie kliknij "Zastosuj", aby zapisać polecenie w pliku.

Drugi sposób pojawia się głównie w przypadku wielokrotnego wysyłania instrukcji tego samego typu. Dla tego typu poleceń dodaliśmy funkcję przycisku "Dodaj" i wyświetlania treści dodanych instrukcji. Kliknięcie przycisku "Dodaj" umożliwia dodanie jednej instrukcji. Wszystkie dodane instrukcje są wyświetlane. Kliknięcie "Zastosuj" zapisuje dodane instrukcje do aktualnie otwartego pliku po prawej stronie.

Kliknij przycisk start, aby uruchomić program; kliknij przycisk stop, aby zatrzymać działanie programu; kliknij przycisk wstrzymaj/wznów, aby wstrzymać/wznowić program. Podczas działania programu aktualnie wykonywany węzeł programu jest podświetlony na zielono.

W trybie ręcznym, kliknięcie pierwszej ikony po prawej stronie węzła umożliwia robotowi samodzielne wykonanie tej instrukcji. Druga ikona umożliwia edycję treści tego węzła.

.. image:: coding/001.png
   :width: 6in
   :align: center

.. centered:: Wykres 5.3‑1 Interfejs drzewa programu