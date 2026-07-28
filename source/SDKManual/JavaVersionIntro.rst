Informacje o aktualizacji wersji
================================

.. toctree:: 
    :maxdepth: 5

.. list-table::
   :widths: 10 10 30
   :header-rows: 0
   :align: center

   * - **Numer wersji**
     - **Data**
     - **Opis aktualizacji**

   * - V3.9.8
     - 2026-07-27
     - | 1. Zaktualizowano strukturę zwrotną statusu robota o bieżący status wykonania programu LUA robota: 0 - program nie jest uruchomiony; 1 - program jest uruchomiony (włączając program wstrzymany);
       | 2. Zaktualizowano opisy parametrów dla interfejsów SetExToolCoord() i SetExToolList() do ustawiania zewnętrznego układu współrzędnych narzędzia i listy układów współrzędnych narzędzi. Numery zewnętrznych układów współrzędnych narzędzi zostały zaktualizowane na 20-39. Zaktualizowano przykłady kodu dla operacji na zewnętrznych układach współrzędnych narzędzi.
       | 3. Dodano możliwość pobierania parametrów typu narzędzia, pozycji instalacji, ID narzędzia i numeru obciążenia do interfejsu GetToolCoordWithID() do pobierania parametrów układu współrzędnych narzędzia.
       | 4. Dodano możliwość pobierania parametrów referencyjnego układu współrzędnych do interfejsu GetWObjCoordWithID() do pobierania parametrów układu współrzędnych przedmiotu.
       | 5. Dodano możliwość pobierania parametrów pozy układu współrzędnych przedmiotu montowanego na końcówce robota do interfejsu GetExToolCoordWithID() do pobierania parametrów zewnętrznego układu współrzędnych narzędzia.
       | 6. Dodano możliwość pobierania numeru osi rozszerzonej i parametrów flagi kalibracji do interfejsu GetExAxisCoordWithID() do pobierania parametrów układu współrzędnych osi rozszerzonej.
       | 7. Dodano ustawienia parametrów prędkości bezpieczeństwa stawów robota do interfejsu SetVelReducePara() do ustawiania prędkości bezpieczeństwa robota.
       | 8. Dodano przykład pobierania trybu sterowania spawarką do przykładu kodu konfiguracji parametrów spawania.
       | 9. Dodano przykłady kodu do pobierania konfiguracji funkcji rozszerzonych DI i rozszerzonych DO do przykładu kodu konfiguracji rozszerzonych sygnałów spawania IO.
       | 10. Dodano nowy przykład kodu do ustawiania prędkości bezpieczeństwa stawów robota;
       | 11. Dodano nowy interfejs WaitStationaryMotionDone() do oczekiwania na zakończenie ruchu pustego w miejscu;
       | 12. Dodano nowy interfejs SetStationaryTrackPara() do konfiguracji parametrów śledzenia w miejscu na taśmie transportowej, wraz z przykładem kodu śledzenia w miejscu na taśmie transportowej;
       | 13. Dodano nowe interfejsy WorkPieceTrsfStart() i WorkPieceTrsfEnd() do rozpoczynania i kończenia transformacji układu współrzędnych przedmiotu, wraz z przykładem kodu transformacji układu współrzędnych przedmiotu.
       | 14. Dodano interfejs GetWeldMachineCtrlMode() do pobierania trybu sterowania spawarką.
       | 15. Dodano interfejsy GetExtDIConfig() i GetExtDOConfig() do pobierania konfiguracji funkcji rozszerzonych DI i rozszerzonych DO.

   * - V3.9.7
     - 2026-06-25
     - | 1. Parametry PhotoelectricSensorTCPCalibration() mogą teraz dostosowywać się do nazw plików bez ścieżki;
       | 2. Parametry LoadTrajectoryJ() mogą teraz dostosowywać się do nazw plików bez ścieżki;
       | 3. Parametry LoadTrajectoryLA() mogą teraz dostosowywać się do nazw plików bez ścieżki;
       | 4. Parametry LoadDefaultProgConfig() mogą teraz dostosowywać się do nazw plików bez ścieżki;
       | 5. Parametry ProgramLoad() mogą teraz dostosowywać się do nazw plików bez ścieżki;
       | 6. Dodano parametr statusu włączenia dłoni do interfejsu SetAxleLuaEnableDeviceType();
       | 7. Dodano parametr statusu włączenia dłoni do interfejsu GetAxleLuaEnableDeviceType();
       | 8. Zmodyfikowano interfejsy do pobierania typów włączenia urządzeń końcówki aktualnie skonfigurowanych oraz sterowania ruchem chwytaka;
       | 9. Dodano włączenie i kody funkcji dla dłoni;
       | 10. Dodano interfejs SetDexterousHandsMove() do sterowania ruchem dłoni;
       | 11. Dodano interfejs SetDexterousHandsAct() do sterowania resetem i aktywacją dłoni;
       | 12. Dodano interfejs ClearDexterousHandsError() do czyszczenia błędów dłoni;
       | 13. Dodano interfejs SetDexterousHandsFunc() do ustawiania włączonych funkcji sterowania ruchem dłoni;
       | 14. Dodano interfejs GetDexterousHandsFunc() do pobierania włączonych funkcji sterowania ruchem dłoni;
       | 15. Dodano interfejsy do ustawiania i pobierania parametrów powrotu do punktu zerowego cyklu po zakończeniu splotu;
       | 16. Dodano interfejs SetWeaveOffsetRT() do ustawiania przesunięcia splotu w czasie rzeczywistym oraz interfejs SetSpeedInstant() do ustawiania prędkości w czasie rzeczywistym.

   * - V3.9.6
     - 2026-05-26
     - | 1. Aktualizacja struktury sprzężenia zwrotnego stanu robota, dodano stan numeru układu współrzędnych osi rozszerzenia;
       | 2. Aktualizacja typu wyliczeniowego konfiguracji sprzężenia zwrotnego stanu robota, dodano wyliczenie konfiguracji numeru układu współrzędnych osi rozszerzenia;
       | 3. Dodano interfejs ExtAxisGetParamConfig() do pobierania konfiguracji parametrów UDP osi rozszerzenia.
       | 4. Dodano interfejs ServoJV() do ruchu w trybie serwo prędkościowym w przestrzeni przegubów robota.
       | 5. Dodano interfejs ServoMITStart() do rozpoczęcia sterowania MIT przegubów robota.
       | 6. Dodano interfejs ServoMITEnd() do zakończenia sterowania MIT przegubów robota.
       | 7. Dodano interfejs ServoMIT() do sterowania MIT przegubów robota.
       | 8. Dodano interfejs SetLaserWeldingParam() do konfiguracji parametrów spawania laserowego robota.
       | 9. Dodano interfejs SetLaserWeldingStartEnd() do ustawiania rozpoczęcia/zatrzymania spawania laserowego robota.
       | 10. Dodano interfejs SetLaserWeldingEnable() do włączania/wyłączania spawarki laserowej.
       | 11. Dodano interfejs ResetLaserWeldingErr() do resetowania błędów spawarki laserowej.
       | 12. Dodano interfejs GetLaserWeldingRunningState() do pobierania stanu pracy spawarki laserowej.
       | 13. Dodano interfejs GetLaserWeldingErrState() do pobierania stanu awarii spawarki laserowej.
       | 14. Dodano interfejs GetLaserWeldingParamTarget() do pobierania parametrów konfiguracyjnych spawania laserowego.
       | 15. Dodano interfejs GetLaserWeldingParamActual() do pobierania aktualnie obowiązujących parametrów konfiguracyjnych spawarki laserowej.
       | 16. Dodano interfejs SetLaserWeldingEnableExtDoNum() do konfiguracji rozszerzonego portu DO włączania spawarki laserowej.
       | 17. Dodano interfejs SetLaserWeldingStartExtDoNum() do konfiguracji rozszerzonego portu DO uruchamiania spawarki laserowej.
       | 18. Dodano interfejs SetLaserWeldingErrResetExtDoNum() do konfiguracji rozszerzonego portu DO resetowania błędów spawarki laserowej.
       | 19. Dodano interfejs SetLaserWeldingRunningStateExtDiNum() do konfiguracji rozszerzonego portu DI stanu pracy (stanu wiązki) spawarki laserowej.
       | 20. Dodano interfejs SetLaserWeldingErrStateExtDiNum() do konfiguracji rozszerzonego portu DI stanu awarii spawarki laserowej.

   * - V3.9.5
     - 2026-04-24
     - | 1. W interfejsie SetTrajectoryJSpeed() dodano tryby: tryb zmniejszania prędkości i bezpośrednie przełączanie;
       | 2. Aktualizacja typu struktury sprzężenia zwrotnego stanu robota;
       | 3. Dodano typ wyliczeniowy konfiguracji sprzężenia zwrotnego stanu robota;
       | 4. Dodano klasę wyniku konfiguracji sprzężenia zwrotnego stanu robota;
       | 5. Dodano interfejs SetRobotRealtimeStateConfig() do konfiguracji sprzężenia zwrotnego stanu CNDE robota;
       | 6. Dodano interfejs AddRobotRealtimeState() do dodawania stanu robota w konfiguracji stanu CNDE;
       | 7. Dodano interfejs DeleteRobotRealtimeState() do usuwania stanu robota w konfiguracji stanu CNDE;
       | 8. Dodano interfejs SetRobotRealtimeStatePeriod() do ustawiania okresu sprzężenia zwrotnego stanu CNDE;
       | 9. Dodano interfejs GetRobotRealtimeStateConfig() do pobierania wszystkich bieżących stanów i okresu sprzężenia zwrotnego stanu CNDE.

   * - V3.9.4
     - 2026-03-25
     - | 1. W interfejsie ServoJTStart() dodano parametr wyboru typu komunikacji, obsługa XMLPRC/UDP;
       | 2. W interfejsie ServoJTEnd() dodano parametr wyboru typu komunikacji, obsługa XMLPRC/UDP;
       | 3. W interfejsie ServoJT() dodano parametr wyboru typu komunikacji, obsługa XMLPRC/UDP;
       | 4. W interfejsie ServoMoveStart() dodano parametr wyboru typu komunikacji, obsługa XMLPRC/UDP;
       | 5. W interfejsie ServoMoveEnd() dodano parametr wyboru typu komunikacji, obsługa XMLPRC/UDP;
       | 6. W interfejsie ServoJ() dodano parametr wyboru typu komunikacji, obsługa XMLPRC/UDP;
       | 7. W interfejsie SetWeldMachineCtrlMode() dodano parametr wyboru trybu sterowania;
       | 8. W interfejsie ExtDevGetUDPComParam() dodano pobieranie parametru komunikacji UDP: czy automatycznie ponownie połączyć po ponownym uruchomieniu skrzynki kontrolnej;
       | 9. Dodano interfejs SetAxleGenComEnable() do włączania ogólnej funkcji przezroczystej transmisji końcowej;
       | 10. Dodano interfejs SndRcvAxleGenComCmdData() do wysyłania danych aperiodycznych przez końcówkę i oczekiwania na odpowiedź;
       | 11. Dodano interfejs SetRobotStopOnComDisc() do ustawiania zatrzymania robota po rozłączeniu komunikacji portu;
       | 12. Dodano interfejs GetRobotStopOnComDisc() do pobierania parametrów zatrzymania robota po rozłączeniu komunikacji portu;
       | 13. Dodano interfejs SetDIConfig() do ustawiania funkcji konfigurowalnego portu CI skrzynki kontrolnej;
       | 14. Dodano interfejs GetDIConfig() do pobierania funkcji konfigurowalnego portu CI skrzynki kontrolnej;
       | 15. Dodano interfejs SetDOConfig() do ustawiania funkcji konfigurowalnego portu CO skrzynki kontrolnej;
       | 16. Dodano interfejs GetDOConfig() do pobierania funkcji konfigurowalnego portu CO skrzynki kontrolnej;
       | 17. Dodano interfejs SetToolDIConfig() do ustawiania funkcji konfigurowalnego portu End-CI końcówki;
       | 18. Dodano interfejs GetToolDIConfig() do pobierania funkcji konfigurowalnego portu End-CI końcówki;
       | 19. Dodano interfejs SetDIConfigLevel() do ustawiania stanu aktywnego konfigurowalnego CI skrzynki kontrolnej;
       | 20. Dodano interfejs GetDIConfigLevel() do pobierania stanu aktywnego konfigurowalnego CI skrzynki kontrolnej;
       | 21. Dodano interfejs SetDOConfigLevel() do ustawiania stanu aktywnego konfigurowalnego CO skrzynki kontrolnej;
       | 22. Dodano interfejs GetDOConfigLevel() do pobierania stanu aktywnego konfigurowalnego CO skrzynki kontrolnej;
       | 23. Dodano interfejs SetToolDIConfigLevel() do ustawiania stanu aktywnego konfigurowalnego CI końcówki;
       | 24. Dodano interfejs GetToolDIConfigLevel() do pobierania stanu aktywnego konfigurowalnego CI końcówki;
       | 25. Dodano interfejs SetStandardDILevel() do ustawiania stanu aktywnego standardowego DI skrzynki kontrolnej;
       | 26. Dodano interfejs GetStandardDILevel() do pobierania stanu aktywnego standardowego DI skrzynki kontrolnej;
       | 27. Dodano interfejs SetStandardDOLevel() do ustawiania stanu aktywnego standardowego DO skrzynki kontrolnej;
       | 28. Dodano interfejs GetStandardDOLevel() do pobierania stanu aktywnego standardowego DO skrzynki kontrolnej;
       | 29. Dodano interfejs SetExAxisCmdDoneTimeUDP() do ustawiania czasu zakończenia pozycjonowania osi rozszerzenia;
       | 30. Dodano interfejs OpenLuaDownload() do pobierania pliku Lua protokołu otwartego;
       | 31. Dodano interfejs OpenLuaDelete() do usuwania pliku Lua protokołu otwartego;
       | 32. Dodano interfejs AllOpenLuaDelete() do usuwania pliku Lua protokołu otwartego;
       | 33. Dodano interfejs SendUDPFrameUDP() do wysyłania ramki instrukcji;
       | 34. Dodano interfejs SetCmdRpyCallback() do ustawiania funkcji zwrotnej wyniku wykonania instrukcji wysłanej przez SDK przez UDP;
       | 35. Dodano interfejs SetVelReducePara() do ustawiania parametrów bezpiecznej prędkości;
       | 36. Dodano interfejs OriginPointWeaveStart() do rozpoczęcia wahadła w punkcie stałym;
       | 37. Dodano interfejs OriginPointWeaveEnd() do zakończenia wahadła w punkcie stałym;
       | 38. Dodano interfejs SetUserLEDColor() do ustawiania niestandardowego koloru lampki końcówki robota przez użytkownika;
       | 39. Dodano interfejs MoveToTPDStart() do ruchu do punktu początkowego rejestracji trajektorii TPD;
   
   * - V3.9.3
     - 2026-02-11
     - | 1. W interfejsie ServoCart() dodano parametr osi rozszerzenia;
       | 2. W interfejsie SetOutputResetCtlBoxDO() dodano parametr stanu DO sprzed resetu do ponownego załadowania po wznowieniu po wstrzymaniu;
       | 3. W interfejsie SetOutputResetCtlBoxAO() dodano parametr stanu DO sprzed resetu do ponownego załadowania po wznowieniu po wstrzymaniu;
       | 4. W interfejsie SetOutputResetAxleDO() dodano parametr stanu DO sprzed resetu do ponownego załadowania po wznowieniu po wstrzymaniu;
       | 5. W interfejsie SetOutputResetAxleAO() dodano parametr stanu DO sprzed resetu do ponownego załadowania po wznowieniu po wstrzymaniu;
       | 6. W interfejsie SetOutputResetExtDO() dodano parametr stanu DO sprzed resetu do ponownego załadowania po wznowieniu po wstrzymaniu;
       | 7. W interfejsie SetOutputResetExtAO() dodano parametr stanu DO sprzed resetu do ponownego załadowania po wznowieniu po wstrzymaniu;
       | 8. W interfejsie SetOutputResetSmartToolDO() dodano parametr stanu DO sprzed resetu do ponownego załadowania po wznowieniu po wstrzymaniu;
       | 9. Dodano interfejs GetInverseKinExaxis() do rozwiązywania kinematyki odwrotnej z uwzględnieniem pozycji osi rozszerzenia.
       
   * - V3.9.2
     - 2026-01-26
     - | 1. W interfejsie FT_RotInsertion() dodano parametr strategii postępowania przy niewykryciu siły/momentu;
       | 2. W interfejsie LaserSensorRecordandReplay() dodano parametry związane ze śledzeniem punktowym robota;
       | 3. Dodano interfejs MoveStationary();
       | 4. Dodano interfejs TCPComputeRPY();
       | 5. Dodano interfejs TCPComputeXYZ();
       | 6. Dodano interfejs TCPRecordFlangePosStart();
       | 7. Dodano interfejs TCPRecordFlangePosEnd();
       | 8. Dodano interfejs TCPGetRecordFlangePos();
       | 9. Dodano interfejs PhotoelectricSensorTCPCalibration().

   * - V3.9.1
     - 2025-12-25
     - | 1. W interfejsie MoveL() dodano parametr współczynnika skalowania prędkości oacc / parametr przyspieszenia fizycznego;
       | 2. W interfejsie MoveC() dodano parametr współczynnika skalowania prędkości oacc / parametr przyspieszenia fizycznego;
       | 3. W interfejsie Circle() zoptymalizowano opis parametrów dotyczących prędkości fizycznej i przyspieszenia fizycznego;
       | 4. Dodano przeciążoną funkcję FT_Control() z parametrami progu uruchomienia rx, ry i współczynnika regulacji momentu;
       | 5. Dodano interfejs SerCoderCompenParams();
       
   * - V3.9.0
     - 2025-11-26
     - | 1. W interfejsie JointSensitivityCalibration() dodano zwracanie liniowości przegubów j1~j6;
       | 2. Dodano interfejs JointHysteresisError();
       | 3. Dodano interfejs JointRepeatability();
       | 4. Dodano interfejs SetAdmittanceParams();
       | 5. Dodano interfejs MoveToIntersectLineStart();
       | 6. Dodano interfejs MoveIntersectLine();
       
   * - V3.8.7
     - 2025-10-21
     - | 1. W interfejsie FT_Control() dodano parametry masy i tłumienia;
       | 2. Dodano interfejs JointSensitivityCalibration();
       | 3. Dodano interfejs JointSensitivityCollect();
       | 4. Dodano interfejs MotionQueueClear();
       | 5. Dodano interfejs GetSlavePortErrCounter();
       | 6. Dodano interfejs SlavePortErrCounterClear();
       | 7. Dodano interfejs SetVelFeedForwardRatio();
       | 8. Dodano interfejs GetVelFeedForwardRatio();
       | 9. Dodano interfejs RobotMCULogCollect();
       | 10. W strukturze stanu dodano licznik instrukcji ServoJ oraz dane pozycji docelowej ostatniej instrukcji;
       | 11. W strukturze parametrów nowej spirali SpiralParam dodano tryb parametrów prędkości i przyspieszenia;

   * - V3.8.6
     - 2025-09-19
     - | 1. W interfejsie SetLoadCoord() dodano parametr numeru obciążenia;
       | 2. Dodano interfejs LaserTrackingLaserOnOff();
       | 3. Dodano interfejs LaserTrackingTrackOnOff();
       | 4. Dodano interfejs LaserTrackingSearchStart_xyz();
       | 5. Dodano interfejs LaserTrackingSearchStart_point();
       | 6. Dodano interfejs LaserTrackingSearchStop();
       | 7. Dodano interfejs LaserTrackingSensorConfig();
       | 8. Dodano interfejs LaserTrackingSensorSamplePeriod();
       | 9. Dodano interfejs LoadPosSensorDriver();
       | 10. Dodano interfejs UnLoadPosSensorDriver();
       | 11. Dodano interfejs LaserSensorRecord1();
       | 12. Dodano interfejs LaserSensorReplay();
       | 13. Dodano interfejs MoveLTR();
       | 14. Dodano interfejs LaserSensorRecordandReplay();
       | 15. Dodano interfejs MoveToLaserRecordStart();
       | 16. Dodano interfejs MoveToLaserRecordEnd();
       | 17. Dodano interfejs MoveToLaserSeamPos();
       | 18. Dodano interfejs GetLaserSeamPos();
       | 19. Dodano interfejs ImpedanceControlStartStop();
       | 20. Dodano interfejs GetToolCoordWithID();
       | 21. Dodano interfejs GetWObjCoordWithID();
       | 22. Dodano interfejs GetExToolCoordWithID();
       | 23. Dodano interfejs GetExAxisCoordWithID();
       | 24. Dodano interfejs GetTargetPayloadWithID();
       | 25. Dodano interfejs GetExAxisCoordWithID();
       | 26. Dodano interfejs GetCurWObjCoord();
       | 27. Dodano interfejs GetCurExToolCoord();
       | 28. Dodano interfejs GetCurExToolCoord();
       | 29. Dodano interfejs KernelUpgrade();
       | 30. Dodano interfejs GetKernelUpgradeResult();
       | 31. Dodano interfejs CustomWeaveSetPara();
       | 32. Dodano interfejs CustomWeaveGetPara();
       | 33. W strukturze stanu dodano układy współrzędnych narzędzia, przedmiotu, zewnętrznego narzędzia, osi rozszerzenia oraz dane masy i środka ciężkości obciążenia.

   * - V3.8.5
     - 2025-08-20
     - | 1. Dodano interfejs OpenLuaUpload();
       | 2. Dodano interfejs GetFieldBusConfig();
       | 3. Dodano interfejs FieldBusSlaveWriteDO();
       | 4. Dodano interfejs FieldBusSlaveWriteAO();
       | 5. Dodano interfejs FieldBusSlaveReadDI();
       | 6. Dodano interfejs FieldBusSlaveReadAI();
       | 7. Dodano interfejs FieldBusSlaveWaitDI();
       | 8. Dodano interfejs FieldBusSlaveWaitAI();
       | 9. Dodano interfejs SetSuckerCtrl();
       | 10. Dodano interfejs GetSuckerState();
       | 11. Dodano interfejs WaitSuckerState();
       | 12. Dodano interfejs MoveL() z trybem parametrów prędkości i przyspieszenia velAccParamMode;
       | 13. Dodano przeciążoną funkcję 1 MoveL();
       | 14. Dodano przeciążoną funkcję 2 MoveL();
       | 15. Dodano interfejs MoveC() z trybem parametrów prędkości i przyspieszenia velAccParamMode;
       | 16. Dodano przeciążoną funkcję 1 MoveC();
       | 17. Dodano interfejs Circle() z trybem parametrów prędkości i przyspieszenia velAccParamMode;
       | 18. Dodano przeciążoną funkcję 1 Circle();
       | 19. Dodano interfejs SetExAxisRobotPlan();

   * - V3.8.4
     - 2025-07-17
     - | 1. W interfejsie ExtAxisMove() dodano parametr wygładzania blend;
       | 2. Dodano interfejs SetFocusCalibPoint();
       | 3. Dodano interfejs ComputeFocusCalib();
       | 4. Dodano interfejs FocusStart();
       | 5. Dodano interfejs FocusEnd();
       | 6. Dodano interfejs SetFocusPosition();
       | 7. Dodano interfejs SetEncoderUpgrade();
       | 8. Dodano interfejs SetJointFirmwareUpgrade();
       | 9. Dodano interfejs SetCtrlFirmwareUpgrade();
       | 10. Dodano interfejs SetEndFirmwareUpgrade();
       | 11. Dodano interfejs JointAllParamUpgrade();
       
   * - V3.8.3
     - 2025-06-24
     - | 1. W interfejsie Circle() dodano parametr procentu przyspieszenia i promienia wygładzania;
       | 2. W interfejsie EndForceDragControl() dodano parametr flagi wykrywania kolizji robota podczas przeciągania wspomaganego;
       | 3. W interfejsie ServoJ() dodano parametr ID instrukcji;
       | 4. Dodano interfejs SetSSHScpCmd();
       | 5. Dodano interfejs SetWideBoxTempFanMonitorParam();
       | 6. Dodano interfejs GetWideBoxTempFanMonitorParam();
       | 7. W strukturze stanu dodano dane temperatury skrzynki kontrolnej i prądu wentylatora;
              
   * - V3.8.2
     - 2025-06-13
     - | 1. W interfejsie WeaveSetPara() dodano parametr kąta pochylenia bocznego kierunku wahadła (odchylenie wokół osi X wahadła);
       | 2. W interfejsie WeaveChangeStart() dodano parametry numeru wahadła, prędkości początkowej spawania i prędkości końcowej spawania;
       | 3. W interfejsie ExtDevSetUDPComParam() dodano parametr automatycznego ustanawiania połączenia po ponownym uruchomieniu zasilania;
       | 4. W interfejsie SetCollisionDetectionMethod() dodano wybór sposobu progu poziomu kolizji;
       | 5. W interfejsie PtpFIRPlanningStart() dodano ekstremalną wartość zrywu dla ujednoliconych przegubów;
       | 6. Dodano interfejs WeldingSetVoltageGradualChangeStart();
       | 7. Dodano interfejs WeldingSetVoltageGradualChangeEnd();
       | 8. Dodano interfejs WeldingSetCurrentGradualChangeStart();
       | 9. Dodano interfejs WeldingSetCurrentGradualChangeEnd();
       | 10. Dodano interfejs ArcWeldTraceAIChannelCurrent();
       | 11. Dodano interfejs ArcWeldTraceAIChannelVoltage();
       | 12. Dodano interfejs ArcWeldTraceCurrentPara();
       | 13. Dodano interfejs ArcWeldTraceVoltagePara();
       | 14. Dodano interfejs GetSmarttoolBtnState();
       | 15. Dodano interfejs ExtAxisGetCoord();
                     
   * - V3.8.1
     - 2025-04-24
     - | 1. W interfejsie ConveyorSetParam() dodano parametry typu śledzenia ruchu, odległości początkowej śledzenia i odległości końcowej śledzenia;
       | 2. Dodano interfejs AccSmoothStart();
       | 3. Dodano interfejs AccSmoothEnd();
       | 4. Dodano interfejs RbLogDownload();
       | 5. Dodano interfejs AllDataSourceDownload();
       | 6. Dodano interfejs DataPackageDownload();
       | 7. Dodano interfejs GetRobotSN();
       | 8. Dodano interfejs ShutDownRobotOS();
       | 9. Dodano interfejs ConveyorComDetect();
       | 10. Dodano interfejs ConveyorComDetectTrigger();