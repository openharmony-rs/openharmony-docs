# Basic Services Kit (Basic Services)
<!--Kit: Common-->
<!--Subsystem: Common-->
<!--Owner: @fang-jinxu-->
<!--Designer: @lingminghw-->
<!--Tester: @RayShih-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=8ee0eefda2c8f7c51afc8d61427d4e7289d6c89f translatedAt=2026-11-12T05:22:22.718Z pushedAt=2026-11-12T12:30:20.409Z nl=1 -->

- ArkTS API<!--basic-services-arkts-->
  - Account Management<!--account-management-arkts-->
    - [@ohos.account.appAccount (Application Account Management)](js-apis-appAccount.md)
    - [@ohos.account.distributedAccount (Distributed Account Management)](js-apis-distributed-account.md)
    - [@ohos.account.osAccount (System Account Management)](js-apis-osAccount.md)
    - [@ohos.account.osAccount.authorization (OS Account Authorization Manager)](js-apis-osAccount-authorization.md)
    <!--Del-->
    - [@ohos.account.distributedAccount (Distributed Account Management)(System API)](js-apis-distributed-account-sys.md)
    - [@ohos.account.osAccount (System Account Management)(System API)](js-apis-osAccount-sys.md)
    <!--DelEnd-->
    - [OS Account Constraints](appendix-osAccount-constraints.md)
    - [OS Account Privilege List](appendix-osAccount-authorization-privileges.md)
  - Device Management<!--device-management-arkts-->
    - [@ohos.batteryInfo (Battery Information)](js-apis-battery-info.md)
    - [@ohos.boardInfo (Board Hardware Information)](js-apis-board-info.md)
    - [@ohos.busManager.serial (Serial Port Communication Management)](js-apis-busmanager-serial.md)
    - [@ohos.deviceInfo (Device Information)](js-apis-device-info.md)
    - [@ohos.power (Power Management)](js-apis-power.md)
    - [@ohos.runningLock (RunningLock)](js-apis-runninglock.md)
    - [@ohos.thermal (Thermal Management)](js-apis-thermal.md)
    - [@ohos.usbManager (USB Management)](js-apis-usbManager.md)
    - [@ohos.usbManager.serial (Serial Port Management)](js-apis-serialManager.md)
    <!--Del-->
    - [@ohos.batteryInfo (Battery Information)(System API)](js-apis-battery-info-sys.md)
    - [@ohos.batteryStatistics (Power Consumption Statistics)(System API)](js-apis-batteryStatistics-sys.md)
    - [@ohos.brightness (Screen Brightness)(System API)](js-apis-brightness-sys.md)
    - [@ohos.busManager.serial (Serial Port Communication Management)(System API)](js-apis-busmanager-serial-sys.md)
    - [@ohos.charger (Charger Type)(System API)](js-apis-charger-sys.md)
    - [@ohos.deviceAttest (Device Attestation)(System API)](js-apis-deviceAttest-sys.md)
    - [@ohos.power (System Power Management)(System API)](js-apis-power-sys.md)
    - [@ohos.systemCapability (System Capability)(System API)](js-apis-system-capability-sys.md)
    - [@ohos.systemParameterEnhance (System Parameter)(System API)](js-apis-system-parameterEnhance-sys.md)
    - [@ohos.screenLock (Lock Screen Management)(System API)](js-apis-screen-lock-sys.md)
    - [@ohos.usbManager (USB Management)(System API)](js-apis-usbManager-sys.md)
    - [@ohos.usbManager.serial (Serial Port Management)(System API)](js-apis-serialManager-sys.md)
    - [@ohos.update (Upgrade)(System API)](js-apis-update-sys.md)
    <!--DelEnd-->
  - Data File Processing<!--data-file-processing-arkts-->
    - [@ohos.app.ability.PrintExtensionAbility (Print Extension Capability)](js-apis-app-ability-PrintExtensionAbility.md)
    - [PrintExtensionContext](js-apis-PrintExtensionContext.md)
    - [@ohos.pasteboard (Clipboard)](js-apis-pasteboard.md)
    - [@ohos.print (Print)](js-apis-print.md)
    - [@ohos.scan (Scan)](js-apis-scan.md)
    - [@ohos.request (Upload and Download)](js-apis-request.md)
    - [@ohos.request.cacheDownload (Cache Download)](js-apis-request-cacheDownload.md)
    - [@ohos.zlib (Zip Module)](js-apis-zlib.md)
    - [@ohos.selectionInput.SelectionExtensionAbility (Text Selection Extension Capability)](js-apis-selectionInput-selectionExtensionAbility.md)
    - [@ohos.selectionInput.SelectionExtensionContext (Text Selection Extension Context)](js-apis-selectionInput-selectionExtensionContext.md)
    - [@ohos.selectionInput.selectionManager (Text Selection Management)](js-apis-selectionInput-selectionManager.md)
    - [@ohos.selectionInput.SelectionPanel (Text Selection Panel)](js-apis-selectionInput-selectionPanel.md)
    <!--Del-->
    - [@ohos.app.ability.PrintExtensionAbility (Print Extension Capability)(System API)](js-apis-app-ability-PrintExtensionAbility-sys.md)
    - [@ohos.print (Print)(System API)](js-apis-print-sys.md)
    - [@ohos.scan (Scan)(System API)](js-apis-scan-sys.md)
    - [@ohos.request (Upload and Download)(System API)](js-apis-request-sys.md)
    <!--DelEnd-->
  - Process and Thread Communication<!--process-thread-communi-arkts-->
    - [System-defined Common Event](common_event/commonEventManager-definitions.md)
    <!--Del-->
    - [System Common Event (System API)](common_event/commonEventManager-definitions-sys.md)
    <!--DelEnd-->
    - [@ohos.commonEventManager (Common Event Module)](js-apis-commonEventManager.md)
    - [@ohos.events.emitter (Emitter)](js-apis-emitter.md)
    <!--Del-->
    - [@ohos.commonEventManager (Common Event Module)(System Application)](js-apis-commonEventManager-sys.md)
    - [@ohos.application.StaticSubscriberExtensionAbility (StaticSubscriberExtensionAbility)(System API)](js-apis-application-staticSubscriberExtensionAbility-sys.md)
    - [@ohos.application.StaticSubscriberExtensionContext (StaticSubscriberExtensionContext)(System API)](js-apis-application-StaticSubscriberExtensionContext-sys.md)
    <!--DelEnd-->
    - commonEvent<!--commonevent-->
      - [CommonEventData](js-apis-inner-commonEvent-commonEventData.md)
      - [CommonEventPublishData](js-apis-inner-commonEvent-commonEventPublishData.md)
      - [CommonEventSubscriber](js-apis-inner-commonEvent-commonEventSubscriber.md)
      - [CommonEventSubscribeInfo](js-apis-inner-commonEvent-commonEventSubscribeInfo.md)
  - Other<!--basic-services-others-->
    <!--Del-->
    - [@ohos.ai.intelligentVoice (Intelligent Voice)(System API)](js-apis-intelligentVoice-sys.md)
    <!--DelEnd-->
    - [@ohos.base (Common Callback Information)](js-apis-base.md)
    - [@ohos.annotation (Annotation)](js-apis-annotation.md)
    - [@ohos.customization.customConfig (Custom Configuration)](js-apis-customization-customConfig.md)
    - [@ohos.settings (Settings activation Item Name)](js-apis-settings.md)
    - [@ohos.settingsLite (Settings Information)](js-apis-settings-lite.md)
    - [@ohos.wallpaper (Wallpaper)](js-apis-wallpaper.md)
    - [@ohos.resourceschedule.systemload (Performance, Power, and Thermal Fusion Level)](js-apis-resourceschedule-systemload.md)
    - [@ohos.systemDateTime (System Time and Time Zone)](js-apis-date-time.md)
    - [@ohos.intelligentScene (Scenario Mode)](js-apis-intelligentScene.md)
    <!--Del-->
    - [@ohos.configPolicy (Configuration Policy)(System API)](js-apis-configPolicy-sys.md)
    - [@ohos.settings (Settings activation Item Name)(System API)](js-apis-settings-sys.md)
    - [@ohos.systemDateTime (System Time and Time Zone)(System API)](js-apis-system-date-time-sys.md)<!--DelEnd-->
     <!--Del-->
    - [@ohos.wallpaper (Wallpaper)(System API)](js-apis-wallpaper-sys.md)
    - [@ohos.WallpaperExtensionAbility (WallpaperExtensionAbility)(System API)](js-apis-WallpaperExtensionAbility-sys.md)
    - [@ohos.systemTimer (System Timer)(System API)](js-apis-system-timer-sys.md)
    <!--DelEnd-->
  - Deprecated APIs<!--basic-services-arkts-dep-->
    - [System Common Event Definition](common_event/commonEvent-definitions.md)
    - [@ohos.commonEvent (Common Event Module)](js-apis-commonEvent.md)
    - [@ohos.usb (USB Management)](js-apis-usb-deprecated.md)
    - [@system.brightness (Screen Brightness)](js-apis-system-brightness.md)
    - [@system.battery (Battery Information)](js-apis-system-battery.md)
    - [@system.device (Device Information)](js-apis-system-device.md)
    - [@system.request (Upload and Download)](js-apis-system-request.md)
    - [@ohos.screenLock (Lock Screen Management)](js-apis-screen-lock.md)
    <!--Del-->
    - [@ohos.commonEvent (Common Event Module)(System Application)](js-apis-commonEvent-sys.md)
    - [@ohos.usb (USB Management)(System API)](js-apis-usb-deprecated-sys.md)
    - [@ohos.systemParameter (System Property)(System API)](js-apis-system-parameter-sys.md)
    <!--DelEnd-->
    - [@ohos.systemTime (System Time and Time Zone)](js-apis-system-time.md)
- C API<!--basic-services-c-->
  - Module<!--basic-services-module-->
    - [OH_CommonEvent](capi-oh-commonevent.md)
    - [DeviceInfo](capi-deviceinfo.md)
    - [OsAccount](capi-osaccount.md)
    - [OH_BatteryInfo](capi-oh-batteryinfo.md)
    - [Scan](capi-oh-scan.md)
    - [Print](capi-oh-print.md)
    - [Pasteboard](capi-pasteboard.md)
    - [TimeService](capi-timeservice.md)
    - [UsbManager](capi-usbmanager.md)
  - Header Files<!--basic-services-headerfile-->
    - [deviceinfo.h](capi-deviceinfo-h.md)
    - [ohbattery_info.h](capi-ohbattery-info-h.md)
    - [oh_commonevent.h](capi-oh-commonevent-h.md)
    - [oh_commonevent_support.h](capi-oh-commonevent-support-h.md)
    - [oh_pasteboard.h](capi-oh-pasteboard-h.md)
    - [oh_pasteboard_err_code.h](capi-oh-pasteboard-err-code-h.md)
    - [os_account.h](capi-os-account-h.md)
    - [os_account_common.h](capi-os-account-common-h.md)
    - [ohprint.h](capi-ohprint-h.md)
    - [ohscan.h](capi-ohscan-h.md)
    - [time_service.h](capi-time-service-h.md)
    - [ohusb_manager.h](capi-ohusb-manager-h.md)
  - Structs<!--basic-services-struct-->
    - [CommonEvent_SubscribeInfo](capi-oh-commonevent-commonevent-subscribeinfo.md)
    - [CommonEvent_PublishInfo](capi-oh-commonevent-commonevent-publishinfo.md)
    - [CommonEvent_RcvData](capi-oh-commonevent-commonevent-rcvdata.md)
    - [Pasteboard_ProgressInfo](capi-pasteboard-progressinfo.md)
    - [Pasteboard_GetDataParams](capi-pasteboard-getdataparams.md)
    - [OH_PasteboardObserver](capi-pasteboard-oh-pasteboardobserver.md)
    - [OH_Pasteboard](capi-pasteboard-oh-pasteboard.md)
    - [Print_Margin](capi-oh-print-print-margin.md)
    - [Print_PageSize](capi-oh-print-print-pagesize.md)
    - [Print_Range](capi-oh-print-print-range.md)
    - [Print_DefaultValue](capi-oh-print-print-defaultvalue.md)
    - [Print_PrinterCapability](capi-oh-print-print-printercapability.md)
    - [Print_PrinterInfo](capi-oh-print-print-printerinfo.md)
    - [Print_PrintJob](capi-oh-print-print-printjob.md)
    - [Print_Property](capi-oh-print-print-property.md)
    - [Print_PropertyList](capi-oh-print-print-propertylist.md)
    - [Print_Resolution](capi-oh-print-print-resolution.md)
    - [Print_StringList](capi-oh-print-print-stringlist.md)
    - [Print_PrintAttributes](capi-oh-print-print-printattributes.md)
    - [Print_PrintDocCallback](capi-oh-print-print-printdoccallback.md)
    - [Scan_ScannerDevice](capi-oh-scan-scan-scannerdevice.md)
    - [Scan_PictureScanProgress](capi-oh-scan-scan-picturescanprogress.md)
    - [Scan_ScannerOptions](capi-oh-scan-scan-scanneroptions.md)
    - [OH_UsbManager_UsbConfig](capi-usbmanager-oh-usbmanager-usbconfig.md)
    - [OH_UsbManager_UsbDevice](capi-usbmanager-oh-usbmanager-usbdevice.md)
    - [OH_UsbManager_UsbEndpoint](capi-usbmanager-oh-usbmanager-usbendpoint.md)
    - [OH_UsbManager_UsbInterface](capi-usbmanager-oh-usbmanager-usbinterface.md)
    - [OH_UsbManager_UsbPipe](capi-usbmanager-oh-usbmanager-usbpipe.md)
- Error Code<!--basic-services-arkts-errcode-->
  - [USB Service Error Code](errorcode-usb.md)
  - [Serial Port Management Error Code](errorcode-busmanager-serial.md)
  - [RunningLock Error Code](errorcode-runninglock.md)
  - [zlib Subsystem Error Code](errorcode-zlib.md)
  <!--Del-->
  - [Battery Information Error Code](errorcode-battery-info.md)
  - [Power Consumption Statistics Error Code](errorcode-batteryStatistics.md)
  <!--DelEnd-->
  - [Clipboard Error Code](errorcode-pasteboard.md)
  <!--Del-->
  - [Screen Brightness Error Code](errorcode-brightness.md)
  <!--DelEnd-->
  - [Thermal Management Error Code](errorcode-thermal.md)
  - [Upload and Download Error Code](errorcode-request.md)
  - [Time and Time Zone Service Error Code](errorcode-time.md)
  - [Common Event Error Code](errorcode-CommonEventService.md)
  <!--Del-->
  - [System Parameter Error Code](errorcode-system-parameterV9.md)
  <!--DelEnd-->
  - [System Power Management Error Code](errorcode-power.md)
  - [Account Management Error Code](errorcode-account.md)
  <!--Del-->
  - [Upgrade Error Code](errorcode-update.md)
  <!--DelEnd-->
  - [Print Service Error Code](errorcode-print.md)
  - [Settings activation Item Error Code](errorcode-settings.md)
  - [Text Selection Service Error Code](errorcode-selection.md)
  - [Scenario Mode Error Code](errorcode-intelligentScene.md)
  <!--Del-->
  - [Lock Screen Service Error Code](errorcode-screenlock.md)
  - [Device Attestation Error Code](errorcode-deviceAttest.md)
  - [Intelligent Voice Error Code](errorcode-intelligentVoice.md)
  <!--DelEnd-->
  - [deviceInfo Error Code](errorcode-device-info.md)