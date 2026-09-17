# @ohos.print

The **print** module provides APIs for basic print operations.

**Since:** 10

**System capability:** SystemCapability.Print.PrintFramework

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [addPrinter](arkts-basicservices-print-addprinter-f.md) | Add a printer to system. |
| [addPrinterToDiscovery](arkts-basicservices-print-addprintertodiscovery-f.md) | Adds a printer to the printer discovery list. This API uses a promise to return the result. |
| [connectPrinter](arkts-basicservices-print-connectprinter-f.md) | Connects to a printer by printer ID. This API uses an asynchronous callback to return the result. |
| [connectPrinter](arkts-basicservices-print-connectprinter-f.md) | Connects to a printer by printer ID. This API uses a promise to return the result. |
| [getAddedPrinters](arkts-basicservices-print-getaddedprinters-f.md) | Obtains the list of printers added to the system. This API uses a promise to return the result. |
| [getPrinterInformationById](arkts-basicservices-print-getprinterinformationbyid-f.md) | Obtains printer information based on the printer ID. This API uses a promise to return the result. |
| [notifyWatermarkComplete](arkts-basicservices-print-notifywatermarkcomplete-f.md) | Notify watermark complete. |
| [off](arkts-basicservices-print-off-f.md#offprinterchange) | Unregisters the listener for printer state change events. This API uses a callback to return the result. |
| [on](arkts-basicservices-print-on-f.md#onprinterchange) | Registers a listener for the printer change events. This API uses a callback to return the result. |
| [print](arkts-basicservices-print-f.md) | Prints files. This API uses an asynchronous callback to return the result. To start the system print preview page, call the [print](arkts-basicservices-print-f.md) API and pass in context. |
| [print](arkts-basicservices-print-f.md) | Prints files. This API uses a promise to return the result. To start the system print preview page, call the [print](arkts-basicservices-print-f.md) API and pass in context. |
| [print](arkts-basicservices-print-f.md) | Prints files. This API uses an asynchronous callback to return the result. |
| [print](arkts-basicservices-print-f.md) | Prints files. This API uses a promise to return the result. |
| [print](arkts-basicservices-print-f.md) | Prints a file. This API uses a promise to return the result. |
| [registerWatermarkCallback](arkts-basicservices-print-registerwatermarkcallback-f.md) | Register to listen for watermark handling. |
| [removePrinterFromDiscovery](arkts-basicservices-print-removeprinterfromdiscovery-f.md) | Removes a printer from the printer discovery list. This API uses a promise to return the result. |
| [startDiscoverPrinter](arkts-basicservices-print-startdiscoverprinter-f.md) | Discovers printers by specifying the extension list. The discovered printers contain the specified print extension abilities. If an empty extension list is specified, all extension abilities are loaded. This API uses an asynchronous callback to return the result. |
| [startDiscoverPrinter](arkts-basicservices-print-startdiscoverprinter-f.md) | Discovers printers by specifying the extension list. The discovered printers contain the specified print extension abilities. If an empty extension list is specified, all extension abilities are loaded. This API uses a promise to return the result. |
| [startPrint](arkts-basicservices-print-startprint-f.md) | Prints a file or binary data. This API uses a promise to return the result. |
| [stopDiscoverPrinter](arkts-basicservices-print-stopdiscoverprinter-f.md) | Stops discovering printers. This API uses an asynchronous callback to return the result. |
| [stopDiscoverPrinter](arkts-basicservices-print-stopdiscoverprinter-f.md) | Stops discovering printers. This API uses a promise to return the result. |
| [unregisterWatermarkCallback](arkts-basicservices-print-unregisterwatermarkcallback-f.md) | Unregister to listen for watermark handling. |
| [updatePrinterInDiscovery](arkts-basicservices-print-updateprinterindiscovery-f.md) | Updates the printer capabilities to the printer discovery list. This API uses a promise to return the result. |
| [updatePrinterInformation](arkts-basicservices-print-updateprinterinformation-f.md) | Updates the information of a printer in the system. This API uses a promise to return the result. Currently, only the **alias** and **options** fields of [PrinterInformation](arkts-basicservices-print-printerinformation-i.md) can be updated. |
| [updatePrintJobState](arkts-basicservices-print-updateprintjobstate-f.md) | Updates the print job state. This API uses an asynchronous callback to return the result. |
| [updatePrintJobState](arkts-basicservices-print-updateprintjobstate-f.md) | Updates the print job state. This API uses a promise to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [addPrinters](arkts-basicservices-print-addprinters-f-sys.md) | Adds printers. This API uses an asynchronous callback to return the result. |
| [addPrinters](arkts-basicservices-print-addprinters-f-sys.md) | Adds printers. This API uses a promise to return the result. |
| [addPrinterToCups](arkts-basicservices-print-addprintertocups-f-sys.md) | Add a printer to cups. |
| [analyzePrintEvents](arkts-basicservices-print-analyzeprintevents-f-sys.md) | Analyze print events. |
| [authPrintJob](arkts-basicservices-print-authprintjob-f-sys.md) | Authenticate a print job. |
| [authSmbDeviceAsRegisteredUser](arkts-basicservices-print-authsmbdeviceasregistereduser-f-sys.md) | Authenticate SMB device as registered user and get available printers. |
| [cancelPrintJob](arkts-basicservices-print-cancelprintjob-f-sys.md) | Cancels the specified print job, which is on the print queue of the printer. This API uses an asynchronous callback to return the result. |
| [cancelPrintJob](arkts-basicservices-print-cancelprintjob-f-sys.md) | Cancels the specified print job, which is on the print queue of the printer. This API uses a promise to return the result. |
| [checkPreferencesConflicts](arkts-basicservices-print-checkpreferencesconflicts-f-sys.md) | Check preferences conflicts. |
| [connectPrinterByIdAndPpd](arkts-basicservices-print-connectprinterbyidandppd-f-sys.md) | Query recommend printer drivers by printer ID. |
| [connectPrinterByIpAndPpd](arkts-basicservices-print-connectprinterbyipandppd-f-sys.md) | Connect a printer by the printer IP and ppd. |
| [deletePrinterFromCups](arkts-basicservices-print-deleteprinterfromcups-f-sys.md) | Delete a printer from cups. |
| [disconnectPrinter](arkts-basicservices-print-disconnectprinter-f-sys.md) | Disconnects from the specified printer. This API uses an asynchronous callback to return the result. |
| [disconnectPrinter](arkts-basicservices-print-disconnectprinter-f-sys.md) | Disconnects from the specified printer. This API uses a promise to return the result. |
| [discoverUsbPrinters](arkts-basicservices-print-discoverusbprinters-f-sys.md) | Discovers USB printers. This API uses a promise to return the result. |
| [getPrinterDefaultPreferences](arkts-basicservices-print-getprinterdefaultpreferences-f-sys.md) | Get default preferences by printer ID. |
| [getPrinterInfoById](arkts-basicservices-print-getprinterinfobyid-f-sys.md) | Obtains printer information based on the printer ID. This API uses a promise to return the result. |
| [getSharedHosts](arkts-basicservices-print-getsharedhosts-f-sys.md) | Get all available shared hosts. |
| [notifyPrintService](arkts-basicservices-print-notifyprintservice-f-sys.md) | Notifies the print service of the spooler shutdown information. This API uses an asynchronous callback to return the result. |
| [notifyPrintService](arkts-basicservices-print-notifyprintservice-f-sys.md) | Notifies the print service of the spooler shutdown information. This API uses a promise to return the result. |
| [notifyPrintServiceEvent](arkts-basicservices-print-notifyprintserviceevent-f-sys.md) | Notifies the print service of the print application events. This API uses a promise to return the result. |
| [notifyPrintServiceEvent](arkts-basicservices-print-notifyprintserviceevent-f-sys.md) | Notifies the print service of the print application events. This API uses a promise to return the result. |
| [off](arkts-basicservices-print-off-f-sys.md#offprinterstatechange) | Unregisters the listener for printer state change events. This API uses a callback to return the result. |
| [off](arkts-basicservices-print-off-f-sys.md#offjobstatechange) | Unregisters the listener for print job state change events. This API uses a callback to return the result. |
| [off](arkts-basicservices-print-off-f-sys.md#offextinfochange) | Unregisters the listener for printer extension information change events. This API uses a callback to return the result. |
| [offPrinterInfoQuery](arkts-basicservices-print-offprinterinfoquery-f-sys.md) | Unregister event callback for the printer info queried. |
| [on](arkts-basicservices-print-on-f-sys.md#onprinterstatechange) | Registers a listener for printer state change events. This API uses a callback to return the result. |
| [on](arkts-basicservices-print-on-f-sys.md#onjobstatechange) | Registers a listener for print job state change events. This API uses a callback to return the result. |
| [on](arkts-basicservices-print-on-f-sys.md#onextinfochange) | Registers a listener for printer extension information change events. This API uses a callback to return the result. |
| [onPrinterInfoQuery](arkts-basicservices-print-onprinterinfoquery-f-sys.md) | Register event callback for the printer info queried. |
| [queryAllActivePrintJobs](arkts-basicservices-print-queryallactiveprintjobs-f-sys.md) | Queries all active print jobs. This API uses a promise to return the result. |
| [queryAllPrinterExtensionInfos](arkts-basicservices-print-queryallprinterextensioninfos-f-sys.md) | Obtains the information of all installed printer extensions. This API uses an asynchronous callback to return the result. |
| [queryAllPrinterExtensionInfos](arkts-basicservices-print-queryallprinterextensioninfos-f-sys.md) | Obtains the information of all installed printer extensions. This API uses a promise to return the result. |
| [queryAllPrinterPpds](arkts-basicservices-print-queryallprinterppds-f-sys.md) | Query all printer ppds. |
| [queryAllPrintJobs](arkts-basicservices-print-queryallprintjobs-f-sys.md) | Queries all print jobs. This API uses an asynchronous callback to return the result. |
| [queryAllPrintJobs](arkts-basicservices-print-queryallprintjobs-f-sys.md) | Queries all print jobs. This API uses a promise to return the result. |
| [queryPrinterCapability](arkts-basicservices-print-queryprintercapability-f-sys.md) | Queries the printer capability. This API uses an asynchronous callback to return the result. |
| [queryPrinterCapability](arkts-basicservices-print-queryprintercapability-f-sys.md) | Queries the printer capability. This API uses a promise to return the result. |
| [queryPrinterCapabilityByUri](arkts-basicservices-print-queryprintercapabilitybyuri-f-sys.md) | Query printer capabilityies by printer uri. |
| [queryPrinterInfoByIp](arkts-basicservices-print-queryprinterinfobyip-f-sys.md) | Query printer info by ip. |
| [queryPrintJobById](arkts-basicservices-print-queryprintjobbyid-f-sys.md) | Queries a print job by ID. This API uses an asynchronous callback to return the result. |
| [queryPrintJobById](arkts-basicservices-print-queryprintjobbyid-f-sys.md) | Queries a print job by ID. This API uses a promise to return the result. |
| [queryPrintJobList](arkts-basicservices-print-queryprintjoblist-f-sys.md) | Queries all print jobs. This API uses an asynchronous callback to return the result. |
| [queryPrintJobList](arkts-basicservices-print-queryprintjoblist-f-sys.md) | Queries all print jobs. This API uses a promise to return the result. |
| [queryRecommendDriversById](arkts-basicservices-print-queryrecommenddriversbyid-f-sys.md) | Query recommend printer drivers by printer ID. |
| [removePrinters](arkts-basicservices-print-removeprinters-f-sys.md) | Removes printers. This API uses an asynchronous callback to return the result. |
| [removePrinters](arkts-basicservices-print-removeprinters-f-sys.md) | Removes printers. This API uses a promise to return the result. |
| [requestPrintPreview](arkts-basicservices-print-requestprintpreview-f-sys.md) | Requests print preview data. This API uses a callback to return the result. |
| [requestPrintPreview](arkts-basicservices-print-requestprintpreview-f-sys.md) | Requests print preview data. This API uses a promise to return the result. |
| [restartPrintJob](arkts-basicservices-print-restartprintjob-f-sys.md) | Restarts a print job that has been finished before. This API uses a promise to return the result. |
| [savePdfFileJob](arkts-basicservices-print-savepdffilejob-f-sys.md) | Save the pdf file for a print job. |
| [setDefaultPrinter](arkts-basicservices-print-setdefaultprinter-f-sys.md) | Sets the default printer. This API uses a promise to return the result. |
| [setPrinterPreferences](arkts-basicservices-print-setprinterpreferences-f-sys.md) | Sets the printer preferences. This API uses a promise to return the result. |
| [startGettingPrintFile](arkts-basicservices-print-startgettingprintfile-f-sys.md) | Starts to obtain the print file. This API uses an asynchronous callback to return the result. |
| [startPrintJob](arkts-basicservices-print-startprintjob-f-sys.md) | Starts the specified print job. This API uses an asynchronous callback to return the result. |
| [startPrintJob](arkts-basicservices-print-startprintjob-f-sys.md) | Starts the specified print job. This API uses a promise to return the result. |
| [updateExtensionInfo](arkts-basicservices-print-updateextensioninfo-f-sys.md) | Updates the printer extension information. This API uses an asynchronous callback to return the result. |
| [updateExtensionInfo](arkts-basicservices-print-updateextensioninfo-f-sys.md) | Updates the printer extension information. This API uses a promise to return the result. |
| [updatePrinters](arkts-basicservices-print-updateprinters-f-sys.md) | Updates information about the specified printers. This API uses an asynchronous callback to return the result. |
| [updatePrinters](arkts-basicservices-print-updateprinters-f-sys.md) | Updates information about the specified printers. This API uses a promise to return the result. |
| [updatePrinterState](arkts-basicservices-print-updateprinterstate-f-sys.md) | Updates the printer state. This API uses an asynchronous callback to return the result. |
| [updatePrinterState](arkts-basicservices-print-updateprinterstate-f-sys.md) | Updates the printer state. This API uses a promise to return the result. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [PpdInfo](arkts-basicservices-print-ppdinfo-i.md) | defines ppd info. |
| [PreviewAttribute](arkts-basicservices-print-previewattribute-i.md) | Defines the print preview attributes. |
| [PrintAttributes](arkts-basicservices-print-printattributes-i.md) | Defines the print attributes. |
| [PrintDocumentAdapter](arkts-basicservices-print-printdocumentadapter-i.md) | Provides information about the document to print. This API must be implemented by a third-party application. |
| [PrinterCapabilities](arkts-basicservices-print-printercapabilities-i.md) | Defines the printer capabilities. |
| [PrinterCapability](arkts-basicservices-print-printercapability-i.md) | Defines the printer capabilities. |
| [PrinterInfo](arkts-basicservices-print-printerinfo-i.md) | Provides the printer information. |
| [PrinterInformation](arkts-basicservices-print-printerinformation-i.md) | Defines the printer information. |
| [PrinterPreferences](arkts-basicservices-print-printerpreferences-i.md) | Defines the printer preferences. |
| [PrinterRange](arkts-basicservices-print-printerrange-i.md) | Defines the print range. |
| [PrintJob](arkts-basicservices-print-printjob-i.md) | Defines a print job. |
| [PrintJobData](arkts-basicservices-print-printjobdata-i.md) | Defines a print job. |
| [PrintMargin](arkts-basicservices-print-printmargin-i.md) | Defines the page margins for printing. |
| [PrintPageRange](arkts-basicservices-print-printpagerange-i.md) | Defines the print range. |
| [PrintPageSize](arkts-basicservices-print-printpagesize-i.md) | Defines the size of the printed page. |
| [PrintResolution](arkts-basicservices-print-printresolution-i.md) | Defines the resolution for printing. |
| [PrintTask](arkts-basicservices-print-printtask-i.md) | Implements event listeners for print jobs. |
| [SharedHost](arkts-basicservices-print-sharedhost-i.md) | Interface defining shared device information |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [PrinterExtensionInfo](arkts-basicservices-print-printerextensioninfo-i-sys.md) | Provides the printer extension information. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [ApplicationEvent](arkts-basicservices-print-applicationevent-e.md) | Enumerates print application events. |
| [DefaultPrinterType](arkts-basicservices-print-defaultprintertype-e.md) | Enumerates default printer types. |
| [DocFlavor](arkts-basicservices-print-docflavor-e.md) | Enumerates the data source types for printing. |
| [PrintColorMode](arkts-basicservices-print-printcolormode-e.md) | Enumerates the color modes. |
| [PrintDirectionMode](arkts-basicservices-print-printdirectionmode-e.md) | Enumerates the print direction modes. |
| [PrintDocumentAdapterState](arkts-basicservices-print-printdocumentadapterstate-e.md) | Enumerates the print job states. |
| [PrintDocumentFormat](arkts-basicservices-print-printdocumentformat-e.md) | Enumerates the data formats. |
| [PrintDuplexMode](arkts-basicservices-print-printduplexmode-e.md) | Enumerates the duplex modes. |
| [PrinterEvent](arkts-basicservices-print-printerevent-e.md) | Enumerates printer-related events. |
| [PrintErrorCode](arkts-basicservices-print-printerrorcode-e.md) | Enumerates the print error codes. |
| [PrinterState](arkts-basicservices-print-printerstate-e.md) | Enumerates the printer states. |
| [PrinterStatus](arkts-basicservices-print-printerstatus-e.md) | Enumerates the printer states. |
| [PrintFileCreationState](arkts-basicservices-print-printfilecreationstate-e.md) | Enumerates the print file creation status. |
| [PrintJobState](arkts-basicservices-print-printjobstate-e.md) | Enumerates the print job states. |
| [PrintJobSubState](arkts-basicservices-print-printjobsubstate-e.md) | Enumerates the print job substates. |
| [PrintOrientationMode](arkts-basicservices-print-printorientationmode-e.md) | Enumerates the print directions. |
| [PrintPageType](arkts-basicservices-print-printpagetype-e.md) | Enumerates the print page types. |
| [PrintQuality](arkts-basicservices-print-printquality-e.md) | Enumerates the print qualities. |
| [WatermarkHandleResult](arkts-basicservices-print-watermarkhandleresult-e.md) | Watermark handling result. |

### Types

| Name | Description |
| --- | --- |
| [PrinterChangeCallback](arkts-basicservices-print-printerchangecallback-t.md) | Defines a callback that takes the printer event and printer information as parameters. |
| [WatermarkCallback](arkts-basicservices-print-watermarkcallback-t.md) | Defines the callback type used in registering to listen for watermark handling. The value of jobId indicates the print job ID. The value of fd indicates the fd. |

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [PrinterInfoQueryCallback](arkts-basicservices-print-printerinfoquerycallback-t-sys.md) | Defines the callback type used in registering to listen for printerInfoQuery event. The value of printerInfo indicates the printer info. The value of ppdInfo indicates all the printer ppd info. |
<!--DelEnd-->
