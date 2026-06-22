Omówienie
++++++++++
Szybka architektura frcobot_ros jest pokazana na poniższym rysunku. Strona robota współpracującego udostępnia serwer XMLRPC i serwer TCP.

- Serwer XMLRPC udostępnia głównie API instrukcji robota do realizacji funkcji ruchu robota i pobierania wartości stanu.
- Serwer TCP sprzężenia zwrotnego stanu zapewnia informację zwrotną o stanie robota w czasie rzeczywistym, z okresem sprzężenia zwrotnego wynoszącym 8 ms.

Na komputerze użytkownika zainstalowano ROS i Moveit!, skompilowano frcobot_ros. W każdym pakiecie funkcjonalnym frcobot_ros znajdują się biblioteki lib API robota oraz klient TCP komunikujący się z serwerem informacji zwrotnej o stanie robota we frcobot_hw, który pobiera dane informacji zwrotnej o stanie robota.

.. figure:: img/frcobot_ros.png
    :width: 6in
    :align: center

Instalacja
++++++++++
W tym rozdziale opisano, jak zbudować frcobot_ros oraz wymagane środowisko instalacyjne.

Wymagania środowiskowe
----------------------

Zalecane środowisko dla frcobot_ros jest następujące:

.. note:: 
    - Ubuntu 18.04 LTS Bionic Beaver i ROS Melodic Morenia
    - Ubuntu 20.04 LTS Focal Fossa i ROS Noetic Ninjemys

Poniższe instrukcje dotyczą systemu Ubuntu 20.04 LTS i ROS Noetic Ninjemys. W przypadku korzystania z Melodic, należy zastąpić ``noetic`` w podanych poleceniach przez ``melodic``.

Wymagania instalacyjne ROS
--------------------------
Po zainstalowaniu systemu Ubuntu, `zainstaluj i skonfiguruj środowisko ROS Noetic <https://wiki.ros.org/noetic/Installation/Ubuntu>`__.

Po skonfigurowaniu ROS Noetic, zainstaluj następujące wymagane środowisko:

.. code-block:: shell
    :linenos:

    echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
    source ~/.bashrc
    sudo apt-get install -y \
        ros-noetic-rosparam-shortcuts \
        ros-noetic-ros-control \
        ros-noetic-ros-controllers \
        ros-noetic-moveit \
        libxmlrpcpp-dev

Kompilacja pakietów ROS
-----------------------
Po prawidłowej instalacji i konfiguracji ROS Noetic, utwórz obszar roboczy Catkin w wybranym katalogu.

.. code-block:: shell
    :linenos:

    mkdir -p ~/catkin_ws/src
    cd ~/catkin_ws
    catkin_init_workspace src

Następnie sklonuj bibliotekę frcobot_ros z Gitee.

.. code-block:: shell
    :linenos:

    cd ~/catkin_ws/src
    git clone https://gitee.com/fair-innovation/frcobot_ros.git

Zbuduj pakiety frcobot_ros

.. code-block::  shell
    :linenos:

    cd ~/catkin_ws
    catkin_make
    echo "source ~/catkin_ws/devel/setup.bash" >> ~/.bashrc
    source ~/.bashrc

Jeśli pojawią się błędy, sprawdź, czy wszystkie pakiety z wymagań instalacyjnych ROS zostały pomyślnie zainstalowane. Po zakończeniu kompilacji skopiuj biblioteki lib do środowiska lib ROS (ścieżka: /opt/ros/noetic/lib), aby program mógł działać poprawnie.

.. code-block:: shell
    :linenos:

    # Tutaj domyślna ścieżka catkin_ws to „~”. W przypadku innej ścieżki, zmień „~” na rzeczywistą ścieżkę
    sudo cp ~/catkin_ws/src/frcobot_ros/frcobot_hw/lib/* /opt/ros/noetic/lib

Szybki start
++++++++++++

frcobot_hw
----------
frcobot_hw udostępnia głównie podstawowe funkcje komunikacji z robotem współpracującym.

.. note:: 
    - Zawiera komunikaty zwrotne o stanie robota współpracującego
    - Udostępnia przykładowe instrukcje sterowania robotem współpracującym
    - Udostępnia węzeł informacji zwrotnej o stanie robota współpracującego i Topic
    - Możliwe jest szybkie uruchomienie węzła stanu i przykładowych instrukcji za pomocą pliku launch

Zawartość frcobot_hw.launch jest następująca:

.. code-block:: xml
    :linenos:

    <launch>

        <!-- params -->
        <param name="robot_ip" type="string" value="192.168.58.2"/>
        <param name="robot_port" type="int" value="8083"/>

        <!-- frcobot status node -->
        <node pkg="frcobot_hw" type="frcobot_status_node" name="frcobot_status_node" output="screen" />

        <!-- frcobot control demo -->
        <node pkg="frcobot_hw" type="frcobot_cmd_demo" name="frcobot_cmd_demo" output="screen" />
        
    </launch>

.. important:: 

    - ``robot_ip`` i ``robot_port`` muszą być zgodne z adresem IP i portem sterowanego robota współpracującego.
    - Domyślny adres IP robota z fabryki to 192.168.58.2, a port informacji zwrotnej o stanie użytkownika to 8083.

Za pomocą następującego polecenia można szybko uruchomić funkcję węzła informacji zwrotnej o stanie robota i przykładowe instrukcje.

.. code-block:: shell
    :linenos:

    roslaunch frcobot_hw frcobot_hw.launch

Otwórz nowy terminal, a za pomocą następującego polecenia możesz wyświetlić i sprawdzić dane informacji zwrotnej o stanie w czasie rzeczywistym.

.. code-block:: shell
    :linenos:

    rostopic echo /frcobot_status