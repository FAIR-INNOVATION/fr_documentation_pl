C#
==============

Niniejszy dokument stanowi dokumentację interfejsu API do wtórnego rozwoju w wersji C#.

.. important::

    Opis jednostek parametrów robota: jednostka pozycji robota to milimetr (mm), jednostka orientacji to stopień (°).

.. important:: 

    1) We wszystkich przykładach kodu, chyba określono inaczej, zakłada się, że robot jest normalnie włączony i załączony.
    2) Wszystkie przykłady kodu w tym dokumencie zakładają, że w przestrzeni roboczej robota nie ma żadnych interferencji.
    3) Podczas rzeczywistych testów należy używać danych z robota na miejscu.
    4) Przed użyciem tego SDK należy znaleźć pakiet „xmlrpcnet” przez NuGet i dodać go do odwołań projektu.


.. toctree:: 
    :numbered: 5
    :maxdepth: 5

    C#VersionIntro
    C#DataStructure
    C#RobotBase
    C#RobotMovement
    C#RobotIO
    C#RobotCommonSettings
    C#RobotSecuritySettings
    C#RobotStatusInquiry
    C#RobotTrajectoryRecurrence
    C#RobotWebAPPProgramUse
    C#RobotPeripherals
    C#RobotForceControl
    C#RobotExtendedAxis
    C#RobotWelding
    C#RobotCnde
    C#RobotOther
    C#Appendix