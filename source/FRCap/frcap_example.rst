Przykład FRCap
==============

.. toctree:: 
   :maxdepth: 6

FAIRINO Palletizer (Paletyzator)
--------------------------------

Po przesłaniu, zarejestrowaniu i włączeniu wtyczki „Paletyzator Palletizer.plugin” z folderu build w projekcie, można jej używać w WebApp.

.. image:: frcap_pictures/011.png
   :width: 6in
   :align: center

.. centered:: Wykres 7.1 Użycie FRCap paletyzatora

Konfiguracja przedmiotu dla paletyzacji
+++++++++++++++++++++++++++++++++++++++

Nazwa instrukcji: palletizing_config_box.

Parametry instrukcji:

.. code-block:: c++
   :linenos:

   /** 
   * @param int length Długość przedmiotu
   * @param int width Szerokość przedmiotu
   * @param int height Wysokość przedmiotu
   * @param int payload Ładowność przedmiotu
   * @param string grip_point Punkt chwytania przedmiotu
   * /

Przykład instrukcji:

.. code-block:: c++
   :linenos:

   {
      cmd: "palletizing_config_box",
      data: {
         length: 800,
         width: 615,
         height: 312,
         payload: 2.34,
         grip_point: "grippoint"
      }
   } 

Informacja zwrotna instrukcji:

.. code-block:: c++
   :linenos:

   /** 
   * @return status:200 "success"
   * @return status:404 "fail"
   */

Konfiguracja palety dla paletyzacji
+++++++++++++++++++++++++++++++++++

Nazwa instrukcji: palletizing_config_pallet.

Parametry instrukcji:

.. code-block:: c++
   :linenos:

   /** 
   * @param int front Przód palety
   * @param int side Bok palety
   * @param int height Wysokość palety
   * @param int left_pallet Włączenie lewej palety
   * @param int right_pallet Włączenie prawej palety
   */

Przykład instrukcji:

.. code-block:: c++
   :linenos:

   {
      cmd: "palletizing_config_pallet",
      data: {
            front: 1200,
            side: 1000,
            height: 110,
            left_pallet: 0,
            right_pallet: 1
         }
   }

Informacja zwrotna instrukcji:

.. code-block:: c++
   :linenos:

   /** 
   * @return status:200 "success"
   * @return status:404 "fail"
   */ 

Konfiguracja zaawansowana paletyzacji
+++++++++++++++++++++++++++++++++++++

Nazwa instrukcji: palletizing_advanced_cfg.

Parametry instrukcji:

.. code-block:: c++
   :linenos:

   /** 
   * @param string height Wysokość podnoszenia punktu chwytania paletyzacji
   * @param string x1 Punkt stopniowy 1 paletyzacji: przesunięcie w kierunku x, jednostka mm
   * @param string y1 Punkt stopniowy 1 paletyzacji: przesunięcie w kierunku y, jednostka mm
   * @param string z1 Punkt stopniowy 1 paletyzacji: przesunięcie w kierunku z, jednostka mm
   * @param string x2 Punkt stopniowy 2 paletyzacji: przesunięcie w kierunku x, jednostka mm
   * @param string y2 Punkt stopniowy 2 paletyzacji: przesunięcie w kierunku y, jednostka mm
   * @param string z2 Punkt stopniowy 2 paletyzacji: przesunięcie w kierunku z, jednostka mm
   * @param string time Czas oczekiwania na przyssanie, jednostka ms
   */ 

Przykład instrukcji:

.. code-block:: c++
   :linenos:

   {
      cmd: "palletizing_advanced_cfg",
      data: {
            height: "1000",
            x1: "100",
            y1: "100",
            z1: "100",
            x2: "10",
            y2: "10",
            z2: "10",
            time: "1"
         }
   }

Informacja zwrotna instrukcji:

.. code-block:: c++
   :linenos:

   /** 
   * @return status:200 "success"
   * @return status:404 "fail"
   */

Konfiguracja wymiarów urządzenia paletyzacyjnego
++++++++++++++++++++++++++++++++++++++++++++++++

Nazwa instrukcji: palletizing_config_device.

Parametry instrukcji:

.. code-block:: c++
   :linenos:

   /** 
   * @param int x Wartość bezwzględna w kierunku x punktu w prawym górnym rogu lewej palety względem podstawowego układu współrzędnych robota
   * @param int y Wartość bezwzględna w kierunku y punktu w prawym górnym rogu lewej palety względem podstawowego układu współrzędnych robota
   * @param int z Wartość bezwzględna w kierunku z punktu w prawym górnym rogu lewej palety względem podstawowego układu współrzędnych robota
   * @param int angle Kąt obrotu robota podczas instalacji
   */ 

Przykład instrukcji:

.. code-block:: c++
   :linenos:

   {
      cmd: "palletizing_config_device",
      data: {
         x: 2400,
         y: 1800,
         z: 120,
         angle: 0   
      }
   }

Informacja zwrotna instrukcji:

.. code-block:: c++
   :linenos:

   /** 
   * @return status:200 "success"
   * @return status:404 "fail"
   */

Konfiguracja trybu paletyzacji
++++++++++++++++++++++++++++++

Nazwa instrukcji: palletizing_config_pattern.

Parametry instrukcji:

.. code-block:: c++
   :linenos:

   /** 
   * @param int layers Liczba warstw paletyzacji
   * @param int box_gap Odstęp między przedmiotami w pikselach, jednostka: mm
   * @param string sequence Sekwencja trybu pracy paletyzacji
   * @param int pattern_b_enable Czy tryb b jest włączony, 1: włączony, 0: nie włączony
   * @param string left_pattern_a Współrzędne kartezjańskie trybu a dla lewego stanowiska
   * @param string left_pattern_b Współrzędne kartezjańskie trybu b dla lewego stanowiska
   * @param string right_pattern_a Współrzędne kartezjańskie trybu a dla prawego stanowiska
   * @param string right_pattern_b Współrzędne kartezjańskie trybu b dla prawego stanowiska
   * @param string origin_pattern_a Współrzędne kartezjańskie początkowego trybu a
   * @param string origin_pattern_b Współrzędne kartezjańskie początkowego trybu b
   */

Przykład instrukcji:

.. code-block:: c++
   :linenos:

   {
      cmd: "palletizing_config_pattern",
      data: {
         layers: 8,
         box_gap: 0,
         sequence: "a,b,a,b,a,b,a,b",
         pattern_b_enable: 1,
         left_pattern_a: "{\"1\": [[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3]]}",
         "left_pattern_b": "{\"1\": [[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3]]}",
         "right_pattern_a": "{\"1\": [[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3]]}",
         "right_pattern_b": "{\"1\": [[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3]]}",
         "origin_pattern_a": "[]",
         "origin_pattern_b": "[]"
      }
   }

Informacja zwrotna instrukcji:

.. code-block:: c++
   :linenos:

   /** 
   * @return status:200 "success"
   * @return status:404 "fail"
   */

Generowanie programu paletyzacji
++++++++++++++++++++++++++++++++

Nazwa instrukcji: generate_palletizing_program.

Parametry instrukcji:

.. code-block:: c++
   :linenos:

   /**
   * @param string palletizing_name Nazwa paletyzacji
   * @param string depalletizing_name Nazwa rozpakowywania
   * @param string flag Czy program paletyzacji lub rozpakowywania ma być wygenerowany, 0 - nie generuj, 1 - generuj
   */ 

Przykład instrukcji:

.. code-block:: c++
   :linenos:

   {
      cmd: "generate_palletizing_program",
      data: {
         palletizing_name: "palletizing_1",
         depalletizing_name:"depalletizing_1",
         flag:"[0,1]"
      }
   }

Informacja zwrotna instrukcji:

.. code-block:: c++
   :linenos:

   /** 
   * @return status:200 "success"
   * @return status:404 "fail"
   */

Pobieranie receptury paletyzacji
++++++++++++++++++++++++++++++++

Nazwa instrukcji: get_palletizing_formula.

Parametry instrukcji:

.. code-block:: c++
   :linenos:

   /** 
   * @param string name Nazwa receptury paletyzacji
   */ 

Przykład instrukcji:

.. code-block:: c++
   :linenos:

   {
      cmd: "get_palletizing_formula",
      data: {
         name: "palletizing_1"
      }
   }

Informacja zwrotna instrukcji:

.. code-block:: c++
   :linenos:

   /** 
   * @return status:200 
   * @param object box_config Konfiguracja przedmiotu
   * @param object pallet_config Konfiguracja palety
   * @param object device_config Pozycja zainstalowanego urządzenia
   * @param object pattern_config Konfiguracja trybu
   * @param object program_config Konfiguracja generowania programu
   * @param object lefttransitionpoint Współrzędne kartezjańskie lewego punktu przejściowego
   * @param object righttransitionpoint Współrzędne kartezjańskie prawego punktu przejściowego
   * @param object advanced_config Konfiguracja zaawansowana
   * @return status:404 "fail"
   */

Przykład informacji zwrotnej instrukcji:

.. code-block:: c++
   :linenos:

   {
      "box_config": {
        "flag": 1,
        "length": 200,
        "width": 400,
        "height": 300,
        "payload": 2.34,
        "grip_point": "grippoint"
      },
      "pallet_config": {
        "flag": 1,
        "front": 1000,
        "side": 1200,
        "height": 110,
         "left_pallet": 0,
         "right_pallet": 1
      },
      "device_config": {
      "flag": 1,
      "x": 2400,
      "y": 1800,
      "z": 120,
      "angle": 0
      },
      "pattern_config": {
      "flag": 1,
      "layers": 8,
      "box_gap": 0,
      "sequence": "a,b,a,b,a,b,a,b",
      "pattern_b_enable": 1,
      "left_pattern_a": "{\"1\": [[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3]]}",
      "left_pattern_b": "{\"1\": [[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3]]}",
      "right_pattern_a": "{\"1\": [[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3]]}",
      "right_pattern_b": "{\"1\": [[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3]]}",
      "origin_pattern_a": "[]",
      "origin_pattern_b": "[]"
      },
      "program_config": {
      "palletizing_name": "palletizing_1",
      "depalletizing_name":"depalletizing_1",
      "flag":"[0,1]"   
      },
      "lefttransitionpoint":{
      "j1":"120",
      "j2":"120",
      "j3":"120",
      "j4":"120",
      "j5":"120",
      "j6":"120"
      },
      "righttransitionpoint":{
      "j1":"120",
      "j2":"120",
      "j3":"120",
      "j4":"120",
      "j5":"120",
      "j6":"120"
      },
      "advanced_config":{
      "height": "1000",
      "x1": "100",
      "y1": "100",
      "z1": "100",
      "x2": "10",
      "y2": "10",
      "z2": "10",
      "time": "1"
      }
   }

Pobieranie listy nazw istniejących receptur paletyzacji
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Nazwa instrukcji: get_palletizing_formula_list.

Parametry instrukcji: brak.

Przykład instrukcji:

.. code-block:: c++
   :linenos:

   {
      cmd: "get_palletizing_formula_list"
   }

Informacja zwrotna instrukcji:

.. code-block:: c++
   :linenos:

   /** 
   * @return status:200 
   * @param Array ${name} Lista nazw paletyzacji
   * @return status:404 "fail"
   */

Przykład informacji zwrotnej instrukcji:

.. code-block:: c++
   :linenos:

   ["palletizing1"]