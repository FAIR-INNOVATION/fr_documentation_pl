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
       | 2. W interfejsie FieldBusSlaveWriteAO() zmieniono typ zapisywanej wartości na double, gdzie AO0~AO15 są typu całkowitego, a AO16~AO31 są typu zmiennoprzecinkowego;
       | 3. W interfejsie FieldBusSlaveReadAI() zmieniono typ odczytywanej wartości na double, gdzie AI0~AI15 są typu całkowitego, a AI16~AI31 są typu zmiennoprzecinkowego;
       | 4. Aktualizacja typu struktury sprzężenia zwrotnego stanu robota;
       | 5. Dodano typ wyliczeniowy konfiguracji sprzężenia zwrotnego stanu robota;
       | 6. Dodano interfejs SetRobotRealtimeStateConfig() do konfiguracji sprzężenia zwrotnego stanu CNDE robota;
       | 7. Dodano interfejs AddRobotRealtimeState() do dodawania stanu robota w konfiguracji stanu CNDE;
       | 8. Dodano interfejs DeleteRobotRealtimeState() do usuwania stanu robota w konfiguracji stanu CNDE;
       | 9. Dodano interfejs SetRobotRealtimeStatePeriod() do ustawiania okresu sprzężenia zwrotnego stanu CNDE;
       | 10. Dodano interfejs GetRobotRealtimeStateConfig() do pobierania wszystkich bieżących stanów i okresu sprzężenia zwrotnego stanu CNDE.

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
       | 11. W strukturze parametrów nowej spirali SpiralParam dodano tryb parametrów prędkości i przyspieszenia.

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
     - | 1. W instrukcjach MoveL(), MoveC(), Circle() dodano parametr velAccParamMode;
       | 2. Dodano interfejsy MoveJ(), SplinePTP(), ExtAxisSyncMoveJ() do automatycznych obliczeń kinematyki prostej;
       | 3. W interfejsie LoadTrajectoryLA() dodano parametr włączający Look-Ahead ze stałą prędkością;
       | 4. Dodano interfejsy MoveL(), MoveC(), Circle(), NewSplinePoint(), NewSpiral(), ExtAxisSyncMoveL(), ExtAxisSyncMoveC() do automatycznych obliczeń kinematyki odwrotnej;
       | 5. Dodano interfejsy sterowania przyssawką SetSuckerCtrl(), GetSuckerState(), WaitSuckerState() oraz interfejs strategii ruchu synchronicznego SetExAxisRobotPlan();
       | 6. Dodano interfejsy sterowania w trybie węzła podrzędnego robota: OpenLuaUpload(), GetFieldBusConfig(), FieldBusSlaveWriteDO(), FieldBusSlaveWriteAO(), FieldBusSlaveReadDI(), FieldBusSlaveReadAI(), FieldBusSlaveWaitDI(), FieldBusSlaveWaitAI().

   * - V3.8.4
     - 2025-07-17
     - | 1. W interfejsie ExtAxisMove() dodano parametr wygładzania blend;
       | 2. Dodano interfejs SetFocusCalibPoint();
       | 3. Dodano interfejs ComputeFocusCalib();
       | 4. Dodano interfejs SetFocusPosition();
       | 5. Dodano interfejs FocusStart();
       | 6. Dodano interfejs FocusEnd();
       | 7. Dodano interfejs SetJointFirmwareUpgrade();
       | 8. Dodano interfejs SetCtrlFirmwareUpgrade();
       | 9. Dodano interfejs SetEndFirmwareUpgrade();
       | 10. Dodano interfejs JointAllParamUpgrade();
       
   * - V3.8.3
     - 2025-06-24
     - | 1. W interfejsie Circle() dodano parametr procentu przyspieszenia i promienia wygładzania;
       | 2. W interfejsie EndForceDragControl() dodano parametr flagi wykrywania kolizji robota podczas przeciągania wspomaganego;
       | 3. W interfejsie ServoJ() dodano parametr ID instrukcji;
       | 4. Dodano interfejs SetWideBoxTempFanMonitorParam();
       | 5. Dodano interfejs GetWideBoxTempFanMonitorParam();
       | 6. W strukturze stanu dodano dane temperatury skrzynki kontrolnej i prądu wentylatora.
              
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
                     
   * - V3.8.0
     - 2025-02-12
     - | 1. W interfejsie EndForceDragControl() dodano parametr unikania punktu osobliwego;
       | 2. W interfejsie ArcWeldTraceControl() dodano parametr przesunięcia;
       | 3. Dodano interfejs WeaveChangeStart();
       | 4. Dodano interfejs WeaveChangeEnd();
       | 5. Dodano interfejs LoadTrajectoryLA();
       | 6. Dodano interfejs MoveTrajectoryLA();
       | 7. Dodano interfejs CustomCollisionDetectionStart();
       | 8. Dodano interfejs CustomCollisionDetectionEnd();