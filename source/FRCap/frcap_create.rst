Kreator tworzenia
=================

.. toctree:: 
   :maxdepth: 6

„Kreator tworzenia” to narzędzie w FRCap-Tools, które umożliwia szybkie i wygodne zainicjowanie projektu FRCap poprzez wprowadzenie niewielkiej liczby parametrów.

Konfiguracja parametrów
-----------------------

Do utworzenia FRCap potrzebne są głównie dwa rodzaje parametrów: podstawowe informacje o FRCap oraz konfiguracje na różnych poziomach. Zostaną one opisane poniżej.

Informacje podstawowe
+++++++++++++++++++++

Informacje podstawowe obejmują „Nazwę wtyczki”, „Autora wtyczki” i „Opis wtyczki”.

Nazwa wtyczki:

- Pole obowiązkowe.
- Brak ograniczeń co do wprowadzanych znaków i długości. Nie wolno wprowadzać spacji.
- Zaleca się, aby nazwa nie przekraczała 7 znaków CJK (chiński, japoński, koreański itp.), 10 wielkich liter łacińskich lub 14 małych liter łacińskich (angielski, francuski itp.).
- Przykłady zalecane:

  - Paletyzator Palletizer
  - Oprogramowanie technologii szlifowania
  - Konfiguracja urządzenia
  - WITAJ FRCAP

Autor wtyczki:

- Pole obowiązkowe.
- Brak ograniczeń co do wprowadzanych znaków i długości. Można wprowadzić np. swoje imię i nazwisko, nazwę firmy itp.
- Przykłady zalecane:

  - Zhang San
  - Franklin Peter
  - FAIR Innovation (Suzhou) Robot Systems Co., Ltd.

Opis wtyczki:

- Pole nieobowiązkowe.
- Brak ograniczeń co do wprowadzanych znaków i długości. Wystarczy krótki opis wtyczki.

Konfiguracja zaawansowana
-------------------------

Typ wtyczki:

- Pole obowiązkowe.
- Dostępne opcje to „Konfiguracja” i „Aplikacja”.
- „Konfiguracja” jest zalecana do implementacji FRCap dla stosunkowo prostych konfiguracji i operacji sterowania, takich jak ustawianie parametrów, operacje przycisków itp. Po zaimportowaniu jest używana w WebApp w „Aplikacje pomocnicze” -> „FRCap”.
- „Aplikacja” jest zalecana do implementacji FRCap dla złożonych scenariuszy procesowych, takich jak paletyzacja, technologia spawania itp. Po zaimportowaniu jest używana bezpośrednio w „Aplikacje pomocnicze” w WebApp.

Ikona wtyczki:

- Pole nieobowiązkowe.
- Ikona może być logo firmy lub dowolną ikoną, którą użytkownik chce użyć. Należy zwrócić uwagę na prawa autorskie. Firma nie ponosi odpowiedzialności za jakiekolwiek problemy z prawami autorskimi z jakiegokolwiek powodu.
- Jeśli użytkownik nie prześle ikony, w wyeksportowanym projekcie FRCap domyślnie używane jest logo „FAIRINO” firmy. Można je zastąpić w folderze public w katalogu projektu. Ikona ta służy wyłącznie do celów poglądowych. Nie należy używać logo „FAIRINO” bezpośrednio w żadnych komercyjnych scenariuszach.

Pobieranie
----------

Po zakończeniu konfiguracji wszystkich powyższych parametrów i pomyślnym utworzeniu FRCap, nastąpi przekierowanie do strony pobierania. Należy potwierdzić, że nazwa jest prawidłowa, aby pobrać utworzony projekt FRCap na komputer lokalny w celu dalszego rozwoju i budowy.

Pobrana wtyczka jest w formacie kompresji „.tar.gz”.

W systemie Windows zaleca się użycie oprogramowania 7-Zip do dekompresji.

W systemie Linux można użyć następującej instrukcji w terminalu do dekompresji.

.. code-block:: c++
   :linenos:

    tar -zxvf frcap_{FRCapName}.tar.gz