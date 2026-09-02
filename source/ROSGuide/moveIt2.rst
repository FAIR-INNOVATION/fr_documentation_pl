Wprowadzenie do wtyczki
+++++++++++++++++++++++
Wtyczka FAIRINO MoveIt2 to wtyczka zapewniająca wsparcie dla sterowania ruchem i planowania trajektorii robotów FAIRINO. Dzięki wtyczce FAIRINO MoveIt2 można realizować złożone funkcje, takie jak sterowanie ruchem robota, planowanie trajektorii, rozwiązywanie odwrotnej kinematyki i wykrywanie kolizji w czasie rzeczywistym. Nadaje się ona do różnych scenariuszy zastosowań ramion mechanicznych, takich jak przemysł, spawanie, produkcja, automatyczny załadunek i rozładunek, paletyzacja, medycyna itp.

Szybki start
++++++++++++
W tym rozdziale opisano, jak skonfigurować środowisko uruchomieniowe aplikacji.

Zaleca się używanie systemu Ubuntu 22.04 LTS (Jammy). Po zakończeniu instalacji systemu można zainstalować ROS2. Zalecana wersja to ros2-humble. Instrukcję instalacji ROS2 można znaleźć pod adresem: https://docs.ros.org/en/humble/index.html.

Instalacja i konfiguracja pakietu wtyczki FAIRINO MoveIt2
---------------------------------------------------------

Klonowanie wtyczki FAIRINO MoveIt2
""""""""""""""""""""""""""""""""""
Sklonuj wtyczkę FAIRINO MoveIt2 do katalogu lokalnego, a następnie przejdź do katalogu docelowego `cd`. Główne pliki obejmują `fairino_msgs` – pakiet typów danych do transmisji danych robota FAIRINO; `fairino_hardware` – pakiet wtyczki `fairino_hardware` robota FAIRINO;

`fairino_robot/fairino_description` – pakiet wyglądu i plików urdf robota FAIRINO;

`fairino_robot/fairino3mt_v6_moveit2_config`, `fairino_robot/fairino3_v6_moveit2_config`, `fairino_robot/fairino5_v6_moveit2_config`, `fairino_robot/fairino10_v6_moveit2_config`, `fairino_robot/fairino16_v6_moveit2_config`, `fairino_robot/fairino20_v6_moveit2_config`, `fairino_robot/fairino30_v6_moveit2_config` – pakiety konfiguracyjne moveit2 robotów FAIRINO, `fairino_robot/fairino_mtc_demo` – przykładowy pakiet kodu mtc robota FAIRINO.

.. image:: img/fairino_harware_001.png
    :width: 6in
    :align: center
.. image:: img/fairino_harware_002.png
    :width: 6in
    :align: center

Kompilacja pakietów funkcjonalnych
""""""""""""""""""""""""""""""""""

Kompilacja pakietu funkcjonalnego `fairino_msgs`

.. code-block:: shell
    :linenos:

    cd ros2_ws
    colcon build --packages-select fairino_msgs
    source install/setup.bash

Kompilacja pakietu funkcjonalnego `fairino_hardware`

.. code-block:: shell
    :linenos:

    cd ros2_ws
    colcon build --packages-select fairino_hardware
    source install/setup.bash

Kompilacja pakietu funkcjonalnego `fairino_description`

.. code-block:: shell
    :linenos:

    cd ros2_ws
    colcon build --packages-select fairino_description
    source install/setup.bash

Kompilacja pakietu konfiguracyjnego moveit2 robota FAIRINO, na przykładzie `fairino5_v6_moveit2_config`

.. code-block:: shell
    :linenos:

    cd ros2_ws
    colcon build --packages-select fairino5_v6_moveit2_config
    source install/setup.bash

Kompilacja przykładowego pakietu kodu `fairino_mtc_demo` robota FAIRINO. Jeśli ten przykładowy pakiet kodu nie znajduje się w oficjalnym obszarze roboczym `ros2_ws`, skontaktuj się z działem obsługi posprzedażowej w celu jego uzyskania.

.. code-block:: shell
    :linenos:

    cd ros2_ws
    colcon build --packages-select fairino_mtc_demo
    source install/setup.bash

Konfiguracja modelu Moveit2 ramienia mechanicznego FAIRINO
----------------------------------------------------------

Jeśli nie chcesz używać oficjalnie dostarczonego pakietu konfiguracyjnego `moveit2_config` robota, możesz skonfigurować niestandardowy pakiet konfiguracyjny `moveit2_config` robota za pomocą `moveit_setup_assistant`.

Tworzenie obszaru roboczego
""""""""""""""""""""""""""""""""""
Utwórz obszar roboczy i pakiet funkcjonalny

.. code-block:: shell
    :linenos:

    mkdir -p test_fa_ws/src
    cd test_fa_ws/src
    mkdir fairino5_v6_robot_moveit_config
    cd ..
    cd ..

Kompilacja pakietu funkcjonalnego i wykonanie `source`

.. code-block:: shell
    :linenos:

    colcon build
    source install/setup.bash

Uruchomienie `moveit_setup_assistant` w celu konfiguracji robota

.. code-block:: shell
    :linenos:

    ros2 launch moveit_setup_assistant setup_assistant.launch.py

Konfiguracja robota
""""""""""""""""""""""""""""""""""

Uruchomienie interfejsu konfiguracji
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
W katalogu `test_fa_ws` otwórz terminal. W interfejsie konfiguracji wybierz „Create New Moveit Configuration Package”, aby utworzyć nowy pakiet konfiguracyjny moveit.

.. image:: img/fairino_harware_003.png
    :width: 6in
    :align: center

Następnie wybierz plik opisu robota, czyli plik `.urdf`, a następnie wybierz „Load Files”, aby załadować model robota. Po prawej stronie wyświetli się załadowany model robota.

.. image:: img/fairino_harware_004.png
    :width: 6in
    :align: center

Konfiguracja Self-Collisions
^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Self-Collisions to ustawienia kolizji robota. Kliknij „Generate Collision Matrix”, aby automatycznie wygenerować macierz kolizji stawów. Spowoduje to usunięcie kolizji między parami stykających się łączników oraz między łącznikami, które nigdy się nie stykają, konfigurując w ten sposób macierz kolizji stawów robota, aby uniknąć obliczania kolizji na powierzchniach styku. Kliknij „Generate Collision Matrix”, aby automatycznie wygenerować.

.. image:: img/fairino_harware_005.png
    :width: 6in
    :align: center

Konfiguracja Virtual Joints
^^^^^^^^^^^^^^^^^^^^^^^^^^^
Virtual Joints to wirtualne osie robota. Gdy robot jest zamontowany na ruchomej platformie, należy ustawić dla niego wirtualne osie. Ustaw nazwę wirtualnej osi, łącznik podrzędny, typ stawu itp. Gdy ruchoma platforma się porusza, wirtualna oś porusza się synchronicznie, wprawiając w ruch robota, umożliwiając mu poruszanie się wraz z ruchomą platformą. W tym przypadku robot zostanie umieszczony bezpośrednio w układzie współrzędnych świata i nazwany `virtual_joints`.

.. image:: img/fairino_harware_006.png
    :width: 6in
    :align: center

Konfiguracja Planning Groups
^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Planning Groups to grupy planowania robota. Łączą one stawy, które muszą być brane pod uwagę podczas obliczeń kinematycznych, w ramach tej samej grupy planowania w celu przeprowadzenia ujednoliconych obliczeń kinematyki prostej i odwrotnej. Na przykład, umieszczając robota na wózku AGV, a następnie instalując uchwyt na końcówce robota, można przypisać cztery stawy wózka AGV do jednej grupy planowania, sześć stawów robota do jednej grupy planowania, a jeden staw uchwytu do jednej grupy planowania do obliczeń kinematycznych.

Ponieważ w tym przypadku nie ma uchwytu, dodana zostanie tylko grupa stawów robota, czyli grupa `arm`. Najpierw dodaj grupę `arm`. W sekcji Kinematic Solver wybierz `kdl_kinematics_plugin/KDLKinematicsPlugin`. Następnie dla Group Default Planner wybierz `TRRT`. Następnie kliknij „Add Joints”, aby dodać stawy do tej grupy planowania.

.. image:: img/fairino_harware_007.png
    :width: 6in
    :align: center

Stawy `arm` można zaznaczyć wiele, przytrzymując klawisz Shift, kliknąć '>', aby dodać, a następnie kliknąć „Save”, aby zapisać.

.. image:: img/fairino_harware_008.png
    :width: 6in
    :align: center

Zdefiniowana grupa planowania wygląda następująco:

.. image:: img/fairino_harware_009.png
    :width: 6in
    :align: center

Konfiguracja Robot Poses
^^^^^^^^^^^^^^^^^^^^^^^^
Robot Poses to wstępnie ustawione pozy robota. Definiują one pewne wstępnie ustawione pozy dla każdej grupy planowania. Dla grupy `arm` zdefiniuj pozycję `home`. Tę pozycję można wybrać dowolnie.

.. image:: img/fairino_harware_010.png
    :width: 6in
    :align: center

Robot Poses umożliwia zdefiniowanie wstępnie ustawionych pozycji dla każdej grupy planowania. Jeśli robot posiada uchwyt, można dodać grupę planowania uchwytu w sekcji Planning Groups, a następnie podczas ustawiania pozycji w Robot Poses można ustawić wstępnie ustawione pozycje dla uchwytu.

Konfiguracja End Effectors
^^^^^^^^^^^^^^^^^^^^^^^^^^
End Effectors to mechanizmy końcowe robota. Grupa planowania mechanizmu końcowego to `hand`. Domyślnie łącznikiem nadrzędnym jest `panda_link8`. Ponieważ w tym przypadku nie ma mechanizmu końcowego, ten krok można pominąć.

ros2_control URDF Modifications
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
ros2_control URDF Modifications służy głównie do ustawiania typów danych stawów wysyłanych i odbieranych w sprzężeniu zwrotnym. Można wybrać jeden z trzech typów: pozycja, prędkość, moment obrotowy. W tym przypadku zarówno wysyłane, jak i odbierane dane stawów są ustawione na sterowanie pozycją. Następnie kliknij „Add interfaces”.

.. image:: img/fairino_harware_011.png
    :width: 6in
    :align: center

.. important:: 

   - Uwaga:

    Wybór typu danych stawów musi być zgodny z późniejszą wtyczką `fairino_hardware`. Zgodnie z danymi przesyłanymi przez wtyczkę `fairino_hardware` wybierz typ danych stawów do wysłania i sprzężenia zwrotnego. Ponieważ wtyczka `fairino_hardware` sterująca rzeczywistym ruchem robota używa typu danych `position`, w tym przypadku zarówno wysyłane, jak i odbierane dane stawów są ustawione na sterowanie pozycją.

ROS 2 Controllers
^^^^^^^^^^^^^^^^^
ROS 2 Controllers służy głównie do wygenerowania pliku `ros2_controllers.yaml`. Plik ten ustawia częstotliwość publikacji, nazwy stawów, nazwy kontrolerów, typy kontrolerów itp. Skonfiguruj ROS 2 Controllers, aby skonfigurować kontroler dla każdej grupy planowania. Kliknij „Auto Add JointTrajectoryController Controllers For Each Planning Group”.

.. image:: img/fairino_harware_012.png
    :width: 6in
    :align: center

Moveit Controllers
^^^^^^^^^^^^^^^^^^
Moveit Controllers służy głównie do wygenerowania pliku `moveit_controllers`. Plik ten ustawia nazwy kontrolerów, typy kontrolerów itp. Należy pamiętać, że nazwy kontrolerów w `moveit_controllers` muszą być takie same jak nazwy kontrolerów w `ros2_controllers`, w przeciwnym razie nie będą działać poprawnie.

Ponadto, gdy nazwy kontrolerów w `moveit_controllers` są takie same jak nazwy kontrolerów w `ros2_controllers`, typy kontrolerów w `moveit_controllers` zostaną automatycznie odwzorowane na typy kontrolerów w `ros2_controllers`. Pozwala to na przesyłanie danych sterujących przez `moveit_controllers` do `ros2_controllers`, a następnie przez wtyczki w `ros2_controllers` do napędzania rzeczywistego ruchu robota.

.. image:: img/fairino_harware_013.png
    :width: 6in
    :align: center

Launch Files
^^^^^^^^^^^^
Skonfiguruj Launch Files. Można użyć domyślnej konfiguracji.

.. image:: img/fairino_harware_014.png
    :width: 6in
    :align: center

Informacje o autorze
^^^^^^^^^^^^^^^^^^^^
.. image:: img/fairino_harware_015.png
    :width: 6in
    :align: center

Generowanie plików Launch
^^^^^^^^^^^^^^^^^^^^^^^^^
Wygeneruj pliki Launch. Wybierz lokalizację generowania. W tym przypadku w ścieżce pliku `test_fa_ws/src` utwórz folder `fairino5_v6_robot_moveit_config` do przechowywania plików konfiguracyjnych, a następnie wybierz „Generate”.

.. image:: img/fairino_harware_016.png
    :width: 6in
    :align: center

Ponieważ w tym przypadku konfiguracja była już przeprowadzona wcześniej, jeśli jest to konfiguracja początkowa, część „Check files you want to be generated” będzie wyświetlona w kolorze czarnym, co oznacza, że można wygenerować pliki Launch.

Uruchomienie Launch
"""""""""""""""""""
Po zakończeniu konfiguracji można przystąpić do kompilacji pakietu funkcjonalnego. Niestandardowy pakiet konfiguracyjny moveit2 robota może zastąpić oficjalny pakiet konfiguracyjny moveit2 robota FAIRINO, umożliwiając kompatybilność wtyczek z niestandardowymi robotami użytkownika.

.. code-block:: shell
    :linenos:

    colcon build --packages-select fairino5_v6_robot_moveit_config
    source install/setup.bash

Następnie uruchom właśnie skonfigurowany plik Launch

.. code-block:: shell
    :linenos:

    ros2 launch fairino5_v6_robot_moveit_config demo.launch.py

Wyświetli się interfejs `rviz2` po zakończeniu konfiguracji.

.. image:: img/fairino_harware_017.png
    :width: 6in
    :align: center

Użycie Moveit2
""""""""""""""
Po otwarciu skonfigurowanego pakietu można ustawić docelową pozycję robota, przeciągając niebieską kulę na końcówce robota w prawym oknie 3D. Następnie można zmienić orientację końcówki robota za pomocą trzech kółek: czerwonego, zielonego i niebieskiego.

.. image:: img/fairino_harware_018.png
    :width: 6in
    :align: center

Kliknij przycisk „Plan” po lewej stronie, aby zaplanować trajektorię ruchu robota.

.. image:: img/fairino_harware_019.png
    :width: 6in
    :align: center

Kliknij przycisk „Execute” po lewej stronie, aby wprawić robota w ruch zgodnie z zaplanowaną trajektorią do docelowej pozycji i orientacji.

.. image:: img/fairino_harware_020.png
    :width: 6in
    :align: center

Przycisk „Plan&Execute” po zaplanowaniu trajektorii automatycznie steruje ruchem robota.

Następnie kliknij zakładkę „Joints”. Można zmienić docelową pozycję robota, zmieniając kąty poszczególnych stawów, a następnie za pomocą przycisków „Plan”, „Execute”, „Plan&Execute” wprawić robota w ruch.

.. image:: img/fairino_harware_021.png
    :width: 6in
    :align: center

Pakiet Funkcjonalności Adaptacji Robotów Produkcyjnych do Środowiska Symulacyjnego Gazebo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Wprowadzenie
------------------------------------------------------------

Ten projekt dostarcza pakiety funkcjonalności symulacyjnych dla robotów współpracujących z serii FR o 6 stopniach swobody w środowisku symulacyjnym Gazebo Classic, zaimplementowane w oparciu o architekturę ROS2 Humble i ros2_control. Każdy robot odpowiada niezależnemu pakietowi ROS2, który wykorzystuje standardowy interfejs sprzętowy GazeboSystem ros2_control, obsługujący sterowanie stawami i sprzężenie zwrotne stanu stawów. Domyślna nazwa przestrzeni roboczej w tym podręczniku to FR_Gazebo_ws; w przypadku własnej nazwy należy ją odpowiednio zastąpić.

Obsługiwane Modele (11 Pakietów Funkcjonalności)
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

Tabela 1-1 Odpowiedniość Obsługiwanych Modeli i Pakietów Funkcjonalności

.. list-table::
   :widths: 50 50
   :header-rows: 0
   :align: center

   * - **Model** 
     - **Pakiet Funkcjonalności**

   * - FR3
     - fr3v6_ros2_control

   * - FR5
     - fr5v6_ros2_control

   * - FR10
     - fr10v6_ros2_control

   * - FR16
     - fr16v6_ros2_control

   * - FR20
     - fr20v6_ros2_control

   * - FR30
     - fr30v6_ros2_control

   * - FR3C
     - fr3c_ros2_control

   * - FR5C
     - fr5c_ros2_control

   * - FR5WML
     - fr5l_ros2_control

   * - FR3WML
     - fr3wml_ros2_control

   * - FR3WMS
     - fr3wms_ros2_control

Główne Cechy
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

- Ujednolicona Nomenklatura Stawów: Wszystkie modele mają 6 obrotowych stawów, nazwanych j1 ~ j6, w kolejności: podstawa → ramię → łokieć → nadgarstek1 → nadgarstek2 → nadgarstek3.
- Ujednolicony Interfejs Sterowania: Polecenia trajectory_msgs/msg/JointTrajectory (sterowanie pozycją) są wysyłane przez temat /joint_trajectory_controller/joint_trajectory.
- Sprzężenie Zwrotne Stanu Stawów: Kąty stawów są przekazywane w czasie rzeczywistym przez temat joint_states pod przestrzenią nazw każdego modelu.
- Skrypty Demonstracyjne: Każdy pakiet funkcjonalności zawiera skrypt *_demo.py, który automatycznie czeka na gotowość kontrolera, a następnie demonstruje ruch każdego stawu.

.. image:: img/039.png
    :width: 6in
    :align: center

.. centered:: Rysunek 1-1 Efekt Ładowania Robota w Środowisku Symulacyjnym Gazebo

Wymagania Środowiskowe
------------------------------

System Operacyjny
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

Ubuntu 22.04 LTS (oficjalnie wspierana wersja dla ROS 2 Humble).

Zależności Programowe
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

Tabela 2-1 Lista Zależności Programowych

.. list-table::
   :widths: 30 30 40
   :header-rows: 0
   :align: center

   * - **Oprogramowanie/Komponent** 
     - **Wersja/Opis**
     - **Ścieżka Instalacji**

   * - ROS 2
     - Humble
     - /opt/ros/humble

   * - Gazebo
     - Gazebo Classic 11 (gzserver / gzclient)
     - Instalowane z gazebo_ros

   * - Przestrzeń Robocza Źródłowa ros2_control
     - Zawiera ros2_control, gazebo_ros2_control, ros2_controllers, controller_manager, joint_trajectory_controller, joint_state_broadcaster, itp.
     - ~/ros2_control_ws

   * - Python 3
     - Do uruchamiania skryptów launch i demo
     - Wbudowany w system
		
.. note:: Pakiety gazebo_ros2_control, joint_trajectory_controller, joint_state_broadcaster i inne wymagane przez ten projekt pochodzą ze skompilowanej ze źródeł przestrzeni roboczej ~/ros2_control_ws (repozytorium ros-controls). Przed uruchomieniem/kompilacją należy zasilić tę przestrzeń roboczą; w przeciwnym razie wystąpią błędy "nie znaleziono kontrolera/wtyczki". Zaleca się również użycie domyślnego typu kompilacji, aby uniknąć problemów z ładowaniem wtyczek spowodowanych symbolami debugowania.

Kroki Instalacji i Kompilacji Pakietów Funkcjonalności
------------------------------------------------------------------------------------------

Przygotowanie: Sprawdzenie Przestrzeni Roboczej ros2_control
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

Sprawdzić, czy ~/ros2_control_ws istnieje i został skompilowany (zawiera repozytorium ros-controls). Jeśli już istnieje, przejść bezpośrednio do Sekcji 3.2. Jeśli trzeba go skonfigurować, wykonać następujące polecenia:

.. centered:: Kod 3-1 Konfiguracja Przestrzeni Roboczej ros2_control
    
.. code-block:: console

    # 1. Utworzyć przestrzeń roboczą i pobrać kod źródłowy ros-controls
    mkdir -p ~/ros2_control_ws/src
    cd ~/ros2_control_ws/src
    git clone https://github.com/ros-controls/ros2_control -b humble

    # 2. Skompilować (ROS 2 Humble musi być już zasilony)
    source /opt/ros/humble/setup.bash
    cd ~/ros2_control_ws
    rosdep install --from-paths src --ignore-src -r -y
    colcon build
    source ~/ros2_control_ws/install/setup.bash

Klonowanie Repozytorium
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

Najpierw sklonować lokalnie pakiety adaptacyjne Gazebo, w tym fr3c_ros2_control, fr3v6_ros2_control, fr3wml_ros2_control, fr3wms_ros2_control, fr5c_ros2_control, fr5l_ros2_control, fr5v6_ros2_control, fr10v6_ros2_control, fr16v6_ros2_control, fr20v6_ros2_control, fr30v6_ros2_control. Utworzyć folder FR_Gazebo_ws/src i sklonować powyższe pakiety do katalogu src.

.. image:: img/040.png
    :width: 6in
    :align: center

.. centered:: Rysunek 3-1 Pakiety Adaptacyjne Robota w Katalogu src

Kompilacja Przestrzeni Roboczej
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

Wszystkie pakiety w tym projekcie są pakietami plikowymi (instalują tylko URDF/launch/config/meshes).

.. centered:: Kod 3-2 Kompilacja Przestrzeni Roboczej FR_Gazebo_ws
    
.. code-block:: console

    # 1. Załadować środowiska w kolejności (kolejność nie może być odwrócona)
    source /opt/ros/humble/setup.bash
    source ~/ros2_control_ws/install/setup.bash

    # 2. Wejść do przestrzeni roboczej i skompilować
    cd ~/FR_Gazebo_ws
    colcon build

    # 3. Po kompilacji załadować środowisko przestrzeni roboczej
    source ~/FR_Gazebo_ws/install/setup.bash

Weryfikacja Wyniku Kompilacji
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

Po pomyślnej kompilacji wszystkie 11 pakietów funkcjonalności powinno pojawić się w katalogu install/:

Kod 3-3 Weryfikacja Wyniku Kompilacji
    
.. code-block:: console

    ls ~/FR_Gazebo_ws/install
    # Powinno pokazać: fr3v6_ros2_control  fr5v6_ros2_control  fr10v6_ros2_control  ... łącznie 11

.. image:: img/041.png
    :width: 6in
    :align: center

.. centered:: Rysunek 3-2 Wyjście Terminala Pomyślnej Kompilacji

Instrukcje Użytkowania
------------------------------------------------------------------------------------------

Uruchamianie Symulacji (Na Przykładzie FR5)
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

.. centered:: Kod 4-1 Uruchamianie Symulacji FR5
    
.. code-block:: console

    # 1. Załadować środowiska w kolejności
    cd ~/FR_Gazebo_ws
    source /opt/ros/humble/setup.bash
    source ~/ros2_control_ws/install/setup.bash
    source ~/FR_Gazebo_ws/install/setup.bash

    # 2. Uruchomić (launch automatycznie uruchomi gzserver/gzclient, wygeneruje robota i załaduje kontrolery. Jeśli trzeba wyczyścić stare procesy, patrz uwaga na końcu Sekcji 4.2)
    ros2 launch fr5v6_ros2_control spawn_fr5v6.launch.py
    
Podczas uruchamiania, launch automatycznie będzie czekać na gotowość controller_manager przed załadowaniem kontrolerów. Poniższy log oznacza gotowość. Jeśli "Successfully loaded" nie pojawi się po więcej niż 3 minutach, patrz Sekcja 5.2 w celu sprawdzenia kolejności zasilania środowisk:

.. centered:: Kod 4-2 Log Pomyślnego Załadowania Kontrolera
    
.. code-block:: console

    Successfully loaded controller joint_trajectory_controller into state active

.. image:: img/042.png
    :width: 6in
    :align: center

.. centered:: Rysunek 4-1 Log Terminala Pomyślnego Załadowania Kontrolera

.. image:: img/043.png
    :width: 6in
    :align: center

.. centered:: Rysunek 4-2 Początkowa Pozycja Robota w Interfejsie Gazebo

Tabela Odniesienia Poleceń Uruchamiania dla Wszystkich Modeli
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

Proces operacyjny jest taki sam dla wszystkich modeli, różnią się tylko nazwa pakietu, nazwa pliku launch i przestrzeń nazw:

Tabela 4-1 Tabela Odniesienia Poleceń Uruchamiania dla Wszystkich Modeli

.. list-table::
   :widths: 20 40 20 20
   :header-rows: 0
   :align: center

   * - **Model** 
     - **Polecenie Uruchamiania**
     - **Przestrzeń Nazw**
     - **Temat Stanu Stawów**

   * - FR3 
     - ros2 launch fr3v6_ros2_control spawn_fr3v6.launch.py
     - fr3v6
     - /fr3v6/joint_states

   * - FR5 
     - ros2 launch fr5v6_ros2_control spawn_fr5v6.launch.py
     - fr5v6
     - /fr5v6/joint_states

   * - FR10 
     - ros2 launch fr10v6_ros2_control spawn_fr10v6.launch.py
     - fr10v6
     - /fr10v6/joint_states

   * - FR16 
     - ros2 launch fr16v6_ros2_control spawn_fr16v6.launch.py
     - fr16v6
     - /fr16v6/joint_states

   * - FR20 
     - ros2 launch fr20v6_ros2_control spawn_fr20v6.launch.py
     - fr20v6
     - /fr20v6/joint_states

   * - FR30 
     - ros2 launch fr30v6_ros2_control spawn_fr30v6.launch.py
     - fr30v6
     - /fr30v6/joint_states

   * - FR3C 
     - ros2 launch fr3c_ros2_control spawn_fr3c.launch.py
     - fr3c
     - /fr3c/joint_states

   * - FR3WML 
     - ros2 launch fr3wml_ros2_control spawn_FR3WML.launch.py
     - fr3wml
     - /fr3wml/joint_states

   * - FR3WMS 
     - ros2 launch fr3wms_ros2_control spawn_FR3WMS.launch.py
     - fr3wms
     - /fr3wms/joint_states

   * - FR5C 
     - ros2 launch fr5c_ros2_control spawn_fr5c.launch.py
     - fr5c
     - /fr5c/joint_states

   * - FR5WML 
     - ros2 launch fr5l_ros2_control spawn_fr5l.launch.py
     - fr5l
     - /fr5l/joint_states
			
.. note:: Tylko jeden model może być uruchomiony jednocześnie. Aby przełączyć, należy najpierw zamknąć bieżący proces Gazebo (pkill -9 gzserver; pkill -9 gzclient); w przeciwnym razie nowa instancja nie uruchomi się z powodu konfliktów portów.

Sterowanie Ręczne (Wysyłanie Docelowych Stawów)
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

Po gotowości kontrolera, wysłać docelowe stawy (6 kątów stawów w radianach) do /joint_trajectory_controller/joint_trajectory:

.. centered:: Kod 4-3 Ręczne Wysyłanie Poleceń Trajektorii Stawów
    
.. code-block:: console

    # Przesunięcie do docelowych stawów [1.57, -0.78, -1.57, -1.2, 1.57, 1.3] (jednostka: radiany)
    ros2 topic pub --once /joint_trajectory_controller/joint_trajectory \
    trajectory_msgs/msg/JointTrajectory \
    "{joint_names: [j1,j2,j3,j4,j5,j6],
        points: [{positions: [1.57, -0.78, -1.57, -1.2, 1.57, 1.3],
                time_from_start: {sec: 2, nanosec: 0}}]}"

    # Powrót do pozycji zerowej
    ros2 topic pub --once /joint_trajectory_controller/joint_trajectory \
    trajectory_msgs/msg/JointTrajectory \
    "{joint_names: [j1,j2,j3,j4,j5,j6],
        points: [{positions: [0.0, 0.0, 0.0, 0.0, 0.0, 0.0],
                time_from_start: {sec: 2, nanosec: 0}}]}"

.. note:: Wzór przeliczeniowy kątów: radiany = stopnie × π / 180. Popularne wartości: 90° ≈ 1.5708, −90° ≈ −1.5708, 100° ≈ 1.7453.

Uruchamianie Skryptów Demonstracyjnych
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

Każdy pakiet funkcjonalności zawiera skrypt demonstracyjny, który automatycznie czeka na gotowość controller_manager, a następnie wykonuje ruch wahadłowy 0→±90° dla każdego stawu:

.. centered:: Kod 4-4 Uruchamianie Skryptu Demonstracyjnego
    
.. code-block:: console

    # Na przykładzie FR5 (dla innych modeli zastąpić nazwę pakietu w ścieżce skryptu)
    python3 ~/FR_Gazebo_ws/src/fr5v6_ros2_control/scripts/fr5v6_demo.py

Tabela 4-2 Tabela Odniesienia Ścieżek Skryptów Demonstracyjnych dla Wszystkich Modeli

.. list-table::
   :widths: 30 70
   :header-rows: 0
   :align: center

   * - **Model** 
     - **Ścieżka Skryptu Demonstracyjnego**

   * - FR3
     - ~/FR_Gazebo_ws/src/fr3v6_ros2_control/scripts/fr3v6_demo.py

   * - FR5
     - ~/FR_Gazebo_ws/src/fr5v6_ros2_control/scripts/fr5v6_demo.py

   * - FR10
     - ~/FR_Gazebo_ws/src/fr10v6_ros2_control/scripts/fr10v6_demo.py

   * - FR16
     - ~/FR_Gazebo_ws/src/fr16v6_ros2_control/scripts/fr16v6_demo.py

   * - FR20
     - ~/FR_Gazebo_ws/src/fr20v6_ros2_control/scripts/fr20v6_demo.py

   * - FR30
     - ~/FR_Gazebo_ws/src/fr30v6_ros2_control/scripts/fr30v6_demo.py

   * - FR3C
     - ~/FR_Gazebo_ws/src/fr3c_ros2_control/scripts/fr3c_demo.py

   * - FR3WML
     - ~/FR_Gazebo_ws/src/fr3wml_ros2_control/scripts/fr3wml_demo.py

   * - FR3WMS
     - ~/FR_Gazebo_ws/src/fr3wms_ros2_control/scripts/fr3wms_demo.py

   * - FR5C
     - ~/FR_Gazebo_ws/src/fr5c_ros2_control/scripts/fr5c_demo.py

   * - FR5WML
     - ~/FR_Gazebo_ws/src/fr5l_ros2_control/scripts/fr5l_demo.py

.. image:: img/044.png
    :width: 6in
    :align: center

.. centered:: Rysunek 4-3 Pozycja Robota Podczas Działania Skryptu Demonstracyjnego

Monitorowanie Stanu Stawów
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

.. centered:: Kod 4-5 Monitorowanie Stanu Stawów
    
.. code-block:: console
        
    # Wyświetlanie kątów stawów w czasie rzeczywistym
    ros2 topic echo /joint_states

.. image:: img/045.png
    :width: 6in
    :align: center

.. centered:: Rysunek 4-4 Wyjście Stanu Stawów w Czasie Rzeczywistym

Częste Problemy
------------------------------------------------------------------------------------------

Konflikt Portów / Gazebo nie otwiera się przy uruchamianiu
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

- Przyczyna: Poprzedni proces Gazebo nie został zakończony, zajmując port.
- Rozwiązanie: Przed uruchomieniem wyczyścić pozostałe procesy: pkill -9 gzserver; pkill -9 gzclient

Zawieszenie na "Waiting for controller_manager..." przez ponad 2 minuty
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

- Przyczyna: controller_manager nie jest gotowy, często ponieważ ~/ros2_control_ws/install/setup.bash nie został zasilony, lub ładowanie siatek jest zbyt wolne.
- Rozwiązanie: Najpierw wyjść Ctrl+C; potwierdzić, że trzy środowiska zostały zasilone w kolejności (ros2 → ros2_control_ws → FR_Gazebo_ws).

Robot nie porusza się przy ręcznym wysyłaniu poleceń
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

- Przyczyna: Najprawdopodobniej problem z synchronizacją; polecenie zostało wysłane zanim kontroler wszedł w stan aktywny i zostało odrzucone.
- Rozwiązanie: Potwierdzić, że terminal wyświetla "Successfully loaded controller joint_trajectory_controller into state active" przed wysłaniem poleceń sterowania; lub bezpośrednio użyć skryptu demo z Sekcji 4.4.

Błąd: nie znaleziono wtyczki joint_trajectory_controller/gazebo_ros2_control
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

- Przyczyna: Zależności związane z ros2_control nie zostały załadowane.
- Rozwiązanie: Potwierdzić, że ~/ros2_control_ws/install/setup.bash został zasilony; i potwierdzić, że kolejność ładowania w ~/.bashrc lub bieżącym terminalu to ROS → ros2_control_ws → ta przestrzeń robocza.

Brakujące Komponenty / Niekompletne Stawy po Załadowaniu Robota
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

- Przyczyna: Brakuje plików siatek odniesionych w URDF.
- Rozwiązanie: Potwierdzić, że katalog meshes/ odpowiedniego pakietu funkcjonalności istnieje i jest kompletny.

Czy można uruchomić dwa modele jednocześnie?
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

- Nie. Wiele instancji symulacyjnych będzie konkurować o ten sam port Gazebo; należy uruchamiać tylko jeden model naraz.

Wtyczka `fairino_hardware` (niestandardowy pakiet konfiguracyjny moveit robota)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Wtyczka `fairino_hardware` jest warstwą pośredniczącą łączącą moveit z robotem. Za pośrednictwem wtyczki `fairino_hardware` `move_group` wysyła plan ruchu do `moveit_control`, który następnie przekazuje go do `ros2_control`. `ros2_control` z kolei za pośrednictwem wtyczki `fairino_hardware` wprawia w ruch rzeczywistego robota. Ponadto wtyczka `fairino_hardware` odbiera również dane zwrotne z rzeczywistego robota, umożliwiając synchronizację modelu robota w interfejsie symulacji `rviz2` z rzeczywistym robotem. Dzięki temu użytkownik może za pośrednictwem interfejsu `rviz2` wprawiać w ruch rzeczywistego robota.

Ponadto dzięki implementacji wtyczki `fairino_hardware` roboty FAIRINO mogą zostać włączone do struktury sterowania `ros2_control`, co umożliwia ich zgodność z pakietami firm trzecich opartymi na `ros2_control`.

W wtyczce `fairino_hardware` dostosowanej do wersji oprogramowania ramienia mechanicznego V3.8.3 dodano tryb momentu obrotowego oraz interfejs momentu obrotowego instrukcji, umożliwiając ramieniu mechanicznemu przejście w tryb momentu i odbieranie instrukcji momentu obrotowego.

Kompilacja wtyczki `fairino_hardware`
----------------------------------------------------------------------------------------

Skompiluj pakiet funkcjonalny wtyczki `fairino_hardware` w oficjalnie dostarczonym pakiecie funkcjonalnym `ros2_ws`. Po kompilacji, zgodnie z poprzednią sekcją dotyczącą kompilacji pakietu funkcjonalnego wtyczki `fairino_hardware`, w ścieżce

.. code-block:: shell
    :linenos:

    ros2_ws/install/fairino_hardware/lib/fairino_hardware

powinien znajdować się wygenerowany plik `.so` wtyczki `libfairino_hardware.so`, co oznacza pomyślną kompilację wtyczki.

Należy pamiętać, że nazwy stawów robota w wtyczce `fairino_hardware` muszą być takie same jak nazwy stawów robota skonfigurowane w `moveit2`. W niniejszej wtyczce `fairino_hardware` nazwy sześciu stawów robota, od pozycji podstawy do końcówki, to odpowiednio `j1`, `j2`, `j3`, `j4`, `j5`, `j6`. Dlatego podczas konfiguracji robota w `moveit2` należy nazwać stawy robota jako `j1`, `j2`, `j3`, `j4`, `j5`, `j6`.

Użycie wtyczki `fairino_hardware`
----------------------------------------------------------------------------------------

Jeśli używany jest niestandardowy pakiet konfiguracyjny moveit robota, przejdź do katalogu

.. code-block:: shell
    :linenos:

    /home/fairino/test_fa_ws/install/fairino5_v6_robot_moveit_config/share/fairino5_v6_robot_moveit_config/config

i znajdź plik `fairino5_v6_robot.ros2_control.xacro`. W trzeciej linii tego pliku zmień parametr

.. code-block:: shell
    :linenos:

    use_fake_hardware:=false

na

.. code-block:: shell
    :linenos:

    use_fake_hardware:=true

Zgodnie z późniejszą instrukcją warunkową `if`, ustawienie `use_fake_hardware` na `true` oznacza włączenie wtyczki `fairino_hardware/FairinoHardwareInterface`. Zapisz plik i wyjdź.

.. image:: img/fairino_harware_022.png
    :width: 6in
    :align: center

Nazwa wtyczki „fairino_hardware/FairinoHardwareInterface” to nazwa ustawiona dla wtyczki hardware. Można ją sprawdzić w pliku `fairino_hardware.xml` w katalogu `/home/fairino/ros2_ws/src/fairino_hardware`.

.. image:: img/fairino_harware_023.png
    :width: 6in
    :align: center

Należy pamiętać, że parametr `robot_control_mode` w trzeciej linii pliku określa, jakie interfejsy instrukcji zostaną udostępnione podczas ładowania wtyczki. Parametr ten reprezentuje tryb sterowania: 0 to tryb sterowania pozycją, wtyczka udostępni interfejs `position`; 1 to tryb sterowania momentem, wtyczka udostępni interfejs `effort`. Wersja demonstracyjna dla interfejsu sterowania momentem zostanie prawdopodobnie wydana w pakiecie funkcjonalnym `fairino_hardware` dostosowanym do wersji oprogramowania ramienia mechanicznego V3.8.5.

Obecny kontroler Moveit2 obsługuje tylko tryb sterowania pozycją. Nie należy ustawiać `robot_control_mode` na 1.

Uruchomienie wtyczki
----------------------------------------------------------------------------------------
Otwórz terminal, przejdź do obszaru roboczego `ros2_ws` i wykonaj `source`, aby dodać wtyczkę `fairino_hardware`. Można również dodać tę ścieżkę do pliku „~/.bashrc”, ale nie jest to zalecane.

.. code-block:: shell
    :linenos:

    cd ros2_ws
    source install/setup.bash

Następnie wróć do katalogu głównego, przejdź do obszaru roboczego `test_fa_ws` i wykonaj `source`, a następnie uruchom plik `demo.launch.py`.

.. code-block:: shell
    :linenos:

    cd ..
    cd test_fa_ws
    source install/setup.bash
    ros2 launch fairino5_v6_robot_moveit_config demo.launch.py

Wynik działania
----------------------------------------------------------------------------------------
Po uruchomieniu pliku `demo.launch.py` interfejs `rviz2` będzie wyglądał następująco:

.. image:: img/fairino_harware_024.png
    :width: 6in
    :align: center

Główna różnica w porównaniu z interfejsem uruchomieniowym w sekcji 3.3.1 polega na początkowej pozycji robota. W tym przypadku, dzięki dodaniu wtyczki `fairino_hardware`, która odbiera w czasie rzeczywistym stany stawów rzeczywistego robota i przekazuje je przez `ros2_control` do `move_group`, steruje ona pozycją robota symulowanego w interfejsie `rviz2`, osiągając synchronizację między rzeczywistym robotem a robotem symulowanym w `rviz2`.

W tym momencie rzeczywista pozycja robota wygląda następująco:

.. image:: img/fairino_harware_025.png
    :width: 3in
    :align: center

Teraz można wprawić w ruch rzeczywistego robota za pośrednictwem interfejsu `rviz2`. Przeciągnij niebieską kulę na końcówce robota w interfejsie `rviz2`, aby przesunąć końcówkę robota do pozycji docelowej. Następnie przeciągnij kółka w kolorze czerwonym, zielonym i niebieskim na końcówce robota, aby zmienić jej orientację. Następnie kliknij przycisk „Planning&Execute” po lewej stronie, aby zaplanować trajektorię ruchu i wprawić robota w ruch. Zauważysz, że rzeczywisty robot i symulowany robot w interfejsie `rviz2` poruszają się synchronicznie, zatrzymując się w docelowej pozycji i orientacji.

Poniższy rysunek przedstawia sterowanie za pomocą interfejsu `rviz2` zarówno rzeczywistym robotem, jak i symulowanym robotem w interfejsie `rviz2`, aby dotarły do docelowej pozycji i orientacji:

.. image:: img/fairino_harware_026.png
    :width: 6in
    :align: center

.. image:: img/fairino_harware_027.png
    :width: 3in
    :align: center

W ten sposób można za pomocą `moveit2` sterować synchronicznym ruchem rzeczywistego robota i symulowanego robota w interfejsie `rviz2`.

Przykładowy pakiet kodu mtc
+++++++++++++++++++++++++++

Wprowadzenie do przykładowego pakietu kodu mtc
---------------------------------------------------
Przykładowy pakiet kodu mtc dostarcza przebudowany interfejs `rviz2` wykorzystujący `moveit2` i wtyczkę `fairino_hardware`. Zastępuje on oryginalną zakładkę MotionPlanning zakładką Motion Planning Tasks, służącą do wyświetlania poszczególnych etapów ruchu robota. Interfejs `rviz2` można edytować za pomocą pliku „mtc.rviz” znajdującego się w ścieżce

.. code-block:: shell
    :linenos:

    ros2_ws/install/fairino_mtc_demo/share/fairino_mtc_demo/launch

Użytkownik może edytować plik „mtc.rviz”, aby dostosować interfejs `rviz2` do swoich potrzeb funkcjonalnych.

Ponadto przykładowy pakiet kodu mtc dostarcza przykładu, w którym robot za pomocą `moveit2` i wtyczki `fairino_hardware` cyklicznie chwyta cel. Na podstawie tego przykładu użytkownik może dowiedzieć się, jak lepiej wykorzystywać `moveit2` i wtyczkę `fairino_hardware` do interakcji z rzeczywistym robotem za pomocą kodu. Na tej podstawie użytkownik może przeprowadzić indywidualne dostosowania zgodne z własnymi potrzebami.

Kompilacja przykładowego pakietu kodu mtc
---------------------------------------------------

Klonowanie przykładowego pakietu kodu mtc
"""""""""""""""""""""""""""""""""""""""""
Sklonuj oficjalnie dostarczony przykładowy pakiet kodu mtc „fairino_robot” do katalogu `src` w obszarze roboczym `ros2_ws`.

Wybór modelu robota
"""""""""""""""""""
W oficjalnie dostarczonym przykładowym pakiecie kodu mtc, w pliku `mtc_demo_env.launch.py` w katalogu

.. code-block:: shell
    :linenos:

    ros2_ws/src/fairino_robot/fairino_mtc_demo/launch

wybierz model robota. Zmodyfikuj linie 9, 10 i 11 tego pliku, aby dopasować je do modelu robota, który ma zostać ustawiony.

.. image:: img/fairino_harware_030.png
    :width: 6in
    :align: center

Szczegółowe nazewnictwo modeli robotów można znaleźć w katalogu

.. code-block:: shell
    :linenos:

    ros2_ws/src/fairino_robot/

w pakietach funkcjonalnych poszczególnych modeli robotów.

.. image:: img/fairino_harware_031.png
    :width: 3in
    :align: center

Kompilacja przykładowego pakietu kodu mtc
"""""""""""""""""""""""""""""""""""""""""

Kompilacja pakietu funkcjonalnego `fairino_description`
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Otwórz terminal, przejdź do katalogu `ros2_ws` i skompiluj pakiet funkcjonalny `fairino_description`, a następnie wykonaj `source`.

.. code-block:: shell
    :linenos:

    cd ros2_ws
    colcon build --packages-select fairino_description
    source install/setup.bash

Kompilacja pakietu funkcjonalnego robota
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
W katalogu `ros2_ws` skompiluj pakiet funkcjonalny odpowiadający modelowi robota. Na przykładzie robota FAIRINO5

.. code-block:: shell
    :linenos:

    colcon build --packages-select fairino5_v6_moveit2_config
    source install/setup.bash

Następnie należy dodać wtyczkę `fairino_hardware` do synchronizacji z rzeczywistym robotem. Przejdź do katalogu

.. code-block:: shell
    :linenos:

    ros2_ws/install/fairino5_v6_moveit2_config/share/fairino5_v6_moveit2_config/config

i znajdź plik `fairino5_v6_robot.ros2_control.xacro`. W 9. linii tego pliku zastąp

.. code-block:: shell
    :linenos:

    <plugin>mock_components/GenericSystem</plugin>

przez

.. code-block:: shell
    :linenos:

    <plugin>fairino_hardware/FairinoHardwareInterface</plugin>

Zapisz i wyjdź.

.. image:: img/fairino_harware_032.png
    :width: 6in
    :align: center

Kompilacja pakietu funkcjonalnego `fairino_mtc_demo`
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Skompiluj pakiet funkcjonalny `fairino_mtc_demo` i wykonaj `source`.

.. code-block:: shell
    :linenos:

    colcon build --packages-select fairino_mtc_demo
    source install/setup.bash

Uruchomienie przykładowego pakietu kodu mtc
---------------------------------------------------

Interfejs `rviz2`
"""""""""""""""""
Uruchom plik `mtc_demo_env.launch.py`, aby otworzyć dostosowany interfejs `rviz2`. Zakładka Motion Planning Tasks służy do wyświetlania niestandardowych etapów ruchu robota.

.. code-block:: shell
    :linenos:

    cd ros2_ws
    source install/setup.bash
    ros2 launch fairino_mtc_demo mtc_demo_env.launch.py

.. image:: img/fairino_harware_033.png
    :width: 6in
    :align: center

.. image:: img/fairino_harware_034.png
    :width: 3in
    :align: center

Ruch robota
"""""""""""
Otwórz nowy terminal, przejdź do katalogu `ros2_ws` i wykonaj `source`, a następnie uruchom plik `mtc_demo_app.launch.py`, aby wykonać ruch robota.

.. code-block:: shell
    :linenos:

    cd ros2_ws
    source install/setup.bash
    ros2 launch fairino_mtc_demo mtc_demo_app.launch.py

W zakładce Motion Planning Tasks w interfejsie `rviz2` zostaną wyświetlone poszczególne etapy ruchu robota, a rzeczywisty robot i symulowany robot w interfejsie `rviz2` będą poruszać się synchronicznie.

.. image:: img/fairino_harware_035.png
    :width: 6in
    :align: center

.. image:: img/fairino_harware_036.png
    :width: 3in
    :align: center

Uwagi
++++++++++++++++++++++++++++++

Synchronizacja wersji wtyczki `fairino_hardware`
---------------------------------------------------

Użycie wtyczki `fairino_hardware` wymaga, aby jej wersja była zgodna z wersją robota FAIRINO.

Wtyczka `fairino_hardware` odbiera dane zwrotne z robota FAIRINO i konwertuje je na typ danych instrukcji określony przez `ros2_control`, a następnie konwertuje dane ruchu robota wysyłane przez `ros2_control` na ramki danych specyficzne dla robota FAIRINO.

Z tego powodu zgodność typu danych wtyczki `fairino_hardware` z typem danych robota FAIRINO jest kluczowa. Różne wersje wtyczki i robota mogą prowadzić do różnych typów danych. Dlatego przed właściwym debugowaniem wtyczki `fairino_hardware` należy upewnić się, że wersja robota FAIRINO jest zgodna z wersją wtyczki `fairino_hardware`. W przeciwnym razie robot FAIRINO musi zostać zaktualizowany.

- Najpierw można sprawdzić bieżące wersje robota w interfejsie „WebAPP -> Ustawienia systemowe -> Informacje” robota FAIRINO.

.. image:: img/fairino_harware_037.png
    :width: 6in
    :align: center

- Następnie przygotuj oficjalnie dostarczony pakiet oprogramowania robota. Wejdź do interfejsu „WebAPP -> Aplikacje pomocnicze -> Robot -> Aktualizacja systemu” robota FAIRINO, kliknij przycisk „Wybierz plik”, wybierz przygotowany pakiet aktualizacyjny oprogramowania robota odpowiadający wersji wtyczki `fairino_hardware`, wybierz „Prześlij pakiet aktualizacyjny” i poczekaj na zakończenie aktualizacji oprogramowania.

- Po zakończeniu aktualizacji system poprosi o ponowne uruchomienie robota. Przełącz przełącznik na skrzynce sterowniczej robota do pozycji wyłączenia, odczekaj około 25 sekund, a następnie włącz robota. W ten sposób aktualizacja wersji oprogramowania robota zostanie zakończona, umożliwiając kompilację i użycie wtyczki `fairino_hardware`.

.. image:: img/fairino_harware_038.png
    :width: 6in
    :align: center

Potencjalne problemy
---------------------------------------------------
Problem z ładowaniem modelu robota po prawej stronie podczas konfiguracji pakietu robota.
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
Rozwiązanie: Ten błąd może wynikać z nieprawidłowej ścieżki w pliku .urdf. Można go rozwiązać, modyfikując ścieżkę w pliku .urdf i kopiując folder `meshes` do katalogu `install/test_moveit/share/test_moveit` w obszarze roboczym.

Błąd po wygenerowaniu pakietu podczas uruchamiania.
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
Rozwiązanie: Usuń „[”capabilities”]” z 203 linii w pliku `launches.py`: `default_value=moveit_config.moveit_capabilities["capabilities"]`.

Podsumowanie
++++++++++++++++++++++++++++++
Niniejsza instrukcja opisuje instalację, konfigurację i używanie wtyczki MoveIt2; instalację i używanie wtyczki `fairino_hardware` w celu synchronizacji ruchu symulowanego robota `rviz2` z rzeczywistym robotem; oraz kompilację i uruchomienie przykładowego pakietu kodu mtc, umożliwiającego realizację niestandardowych funkcji za pomocą `moveit2` i wtyczki `fairino_hardware`.

Mamy nadzieję, że dzięki temu podręcznikowi użytkownicy zyskają pełniejsze zrozumienie wtyczek MoveIt2 i `fairino_hardware` i będą mogli lepiej dostosowywać funkcje robota FAIRINO do swoich indywidualnych potrzeb.