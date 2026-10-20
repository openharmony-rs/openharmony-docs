# @ohos.print

The **print** module provides APIs for basic print operations.

**Since:** 10

<!--Device-unnamed-declare namespace print--><!--Device-unnamed-declare namespace print-End-->

**System capability:** SystemCapability.Print.PrintFramework

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [addPrinter](arkts-basicservices-print-addprinter-f.md#addprinter) | Add a printer to system. |
| [addPrinterToDiscovery](arkts-basicservices-print-addprintertodiscovery-f.md#addprintertodiscovery) | Adds a printer to the printer discovery list. This API uses a promise to return the result. |
| [connectPrinter](arkts-basicservices-print-connectprinter-f.md#connectprinter) | Connects to a printer by printer ID. This API uses an asynchronous callback to return the result. |
| [connectPrinter](arkts-basicservices-print-connectprinter-f.md#connectprinter) | Connects to a printer by printer ID. This API uses a promise to return the result. |
| [getAddedPrinters](arkts-basicservices-print-getaddedprinters-f.md#getaddedprinters) | Obtains the list of printers added to the system. This API uses a promise to return the result. |
| [getPrinterInformationById](arkts-basicservices-print-getprinterinformationbyid-f.md#getprinterinformationbyid) | Obtains printer information based on the printer ID. This API uses a promise to return the result. |
| [notifyWatermarkComplete](arkts-basicservices-print-notifywatermarkcomplete-f.md#notifywatermarkcomplete) | Notify watermark complete. |
| [off('printerChange')](arkts-basicservices-print-off-f.md#offprinterchange) | Unregisters the listener for printer state change events. This API uses a callback to return the result. |
| [on('printerChange')](arkts-basicservices-print-on-f.md#onprinterchange) | Registers a listener for the printer change events. This API uses a callback to return the result. |
| [print](arkts-basicservices-print-f.md#print) | Prints files. This API uses an asynchronous callback to return the result. |
| [print](arkts-basicservices-print-f.md#print) | Prints files. This API uses a promise to return the result. |
| [print](arkts-basicservices-print-f.md#print) | Prints a file. This API uses a promise to return the result. |
| [registerWatermarkCallback](arkts-basicservices-print-registerwatermarkcallback-f.md#registerwatermarkcallback) | Register to listen for watermark handling. |
| [removePrinterFromDiscovery](arkts-basicservices-print-removeprinterfromdiscovery-f.md#removeprinterfromdiscovery) | Removes a printer from the printer discovery list. This API uses a promise to return the result. |
| [startDiscoverPrinter](arkts-basicservices-print-startdiscoverprinter-f.md#startdiscoverprinter) | Discovers printers by specifying the extension list. The discovered printers contain the specified print extension abilities. If an empty extension list is specified, all extension abilities are loaded. This API uses an asynchronous callback to return the result. |
| [startDiscoverPrinter](arkts-basicservices-print-startdiscoverprinter-f.md#startdiscoverprinter) | Discovers printers by specifying the extension list. The discovered printers contain the specified print extension abilities. If an empty extension list is specified, all extension abilities are loaded. This API uses a promise to return the result. |
| [startPrint](arkts-basicservices-print-startprint-f.md#startprint) | Prints a file or binary data. This API uses a promise to return the result. |
| [stopDiscoverPrinter](arkts-basicservices-print-stopdiscoverprinter-f.md#stopdiscoverprinter) | Stops discovering printers. This API uses an asynchronous callback to return the result. |
| [stopDiscoverPrinter](arkts-basicservices-print-stopdiscoverprinter-f.md#stopdiscoverprinter) | Stops discovering printers. This API uses a promise to return the result. |
| [unregisterWatermarkCallback](arkts-basicservices-print-unregisterwatermarkcallback-f.md#unregisterwatermarkcallback) | Unregister to listen for watermark handling. |
| [updatePrinterInDiscovery](arkts-basicservices-print-updateprinterindiscovery-f.md#updateprinterindiscovery) | Updates the printer capabilities to the printer discovery list. This API uses a promise to return the result. |
| [updatePrinterInformation](arkts-basicservices-print-updateprinterinformation-f.md#updateprinterinformation) | Updates the information of a printer in the system. This API uses a promise to return the result. Currently, only the **alias** and **options** fields of [PrinterInformation](arkts-basicservices-print-printerinformation-i.md) can be updated. |
| [updatePrintJobState](arkts-basicservices-print-updateprintjobstate-f.md#updateprintjobstate) | Updates the print job state. This API uses an asynchronous callback to return the result. |
| [updatePrintJobState](arkts-basicservices-print-updateprintjobstate-f.md#updateprintjobstate) | Updates the print job state. This API uses a promise to return the result. |
| [print](arkts-basicservices-print-f.md#print) | Prints files. This API uses an asynchronous callback to return the result. To start the system print preview page, call the [print](arkts-basicservices-print-f.md#print) API and pass in context. |
| [print](arkts-basicservices-print-f.md#print) | Prints files. This API uses a promise to return the result. To start the system print preview page, call the [print](arkts-basicservices-print-f.md#print) API and pass in context. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [addPrinters](arkts-basicservices-print-addprinters-f-sys.md#addprinters) | Adds printers. This API uses an asynchronous callback to return the result. |
| [addPrinters](arkts-basicservices-print-addprinters-f-sys.md#addprinters) | Adds printers. This API uses a promise to return the result. |
| [addPrinterToCups](arkts-basicservices-print-addprintertocups-f-sys.md#addprintertocups) | Add a printer to cups. |
| [analyzePrintEvents](arkts-basicservices-print-analyzeprintevents-f-sys.md#analyzeprintevents) | Analyze print events. |
| [authPrintJob](arkts-basicservices-print-authprintjob-f-sys.md#authprintjob) | Authenticate a print job. |
| [authSmbDeviceAsRegisteredUser](arkts-basicservices-print-authsmbdeviceasregistereduser-f-sys.md#authsmbdeviceasregistereduser) | Authenticate SMB device as registered user and get available printers. |
| [cancelPrintJob](arkts-basicservices-print-cancelprintjob-f-sys.md#cancelprintjob) | Cancels the specified print job, which is on the print queue of the printer. This API uses an asynchronous callback to return the result. |
| [cancelPrintJob](arkts-basicservices-print-cancelprintjob-f-sys.md#cancelprintjob) | Cancels the specified print job, which is on the print queue of the printer. This API uses a promise to return the result. |
| [checkPreferencesConflicts](arkts-basicservices-print-checkpreferencesconflicts-f-sys.md#checkpreferencesconflicts) | Check preferences conflicts. |
| [connectPrinterByIdAndPpd](arkts-basicservices-print-connectprinterbyidandppd-f-sys.md#connectprinterbyidandppd) | Query recommend printer drivers by printer ID. |
| [connectPrinterByIpAndPpd](arkts-basicservices-print-connectprinterbyipandppd-f-sys.md#connectprinterbyipandppd) | Connect a printer by the printer IP and ppd. |
| [deletePrinterFromCups](arkts-basicservices-print-deleteprinterfromcups-f-sys.md#deleteprinterfromcups) | Delete a printer from cups. |
| [disconnectPrinter](arkts-basicservices-print-disconnectprinter-f-sys.md#disconnectprinter) | Disconnects from the specified printer. This API uses an asynchronous callback to return the result. |
| [disconnectPrinter](arkts-basicservices-print-disconnectprinter-f-sys.md#disconnectprinter) | Disconnects from the specified printer. This API uses a promise to return the result. |
| [discoverUsbPrinters](arkts-basicservices-print-discoverusbprinters-f-sys.md#discoverusbprinters) | Discovers USB printers. This API uses a promise to return the result. |
| [getPrinterDefaultPreferences](arkts-basicservices-print-getprinterdefaultpreferences-f-sys.md#getprinterdefaultpreferences) | Get default preferences by printer ID. |
| [getPrinterInfoById](arkts-basicservices-print-getprinterinfobyid-f-sys.md#getprinterinfobyid) | Obtains printer information based on the printer ID. This API uses a promise to return the result. |
| [getSharedHosts](arkts-basicservices-print-getsharedhosts-f-sys.md#getsharedhosts) | Get all available shared hosts. |
| notifyPrintService('spooler_closed_for_cancelled' | 'spooler_closed_for_started') | Notifies the print service of the spooler shutdown information. This API uses an asynchronous callback to return the result. |
| notifyPrintService('spooler_closed_for_cancelled' | 'spooler_closed_for_started') | Notifies the print service of the spooler shutdown information. This API uses a promise to return the result. |
| [notifyPrintServiceEvent](arkts-basicservices-print-notifyprintserviceevent-f-sys.md#notifyprintserviceevent) | Notifies the print service of the print application events. This API uses a promise to return the result. |
| [notifyPrintServiceEvent](arkts-basicservices-print-notifyprintserviceevent-f-sys.md#notifyprintserviceevent) | Notifies the print service of the print application events. This API uses a promise to return the result. |
| [off('printerStateChange')](arkts-basicservices-print-off-f-sys.md#offprinterstatechange) | Unregisters the listener for printer state change events. This API uses a callback to return the result. |
| [off('jobStateChange')](arkts-basicservices-print-off-f-sys.md#offjobstatechange) | Unregisters the listener for print job state change events. This API uses a callback to return the result. |
| [off('extInfoChange')](arkts-basicservices-print-off-f-sys.md#offextinfochange) | Unregisters the listener for printer extension information change events. This API uses a callback to return the result. |
| [offPrinterInfoQuery](arkts-basicservices-print-offprinterinfoquery-f-sys.md#offprinterinfoquery) | Unregister event callback for the printer info queried. |
| [on('printerStateChange')](arkts-basicservices-print-on-f-sys.md#onprinterstatechange) | Registers a listener for printer state change events. This API uses a callback to return the result. |
| [on('jobStateChange')](arkts-basicservices-print-on-f-sys.md#onjobstatechange) | Registers a listener for print job state change events. This API uses a callback to return the result. |
| [on('extInfoChange')](arkts-basicservices-print-on-f-sys.md#onextinfochange) | Registers a listener for printer extension information change events. This API uses a callback to return the result. |
| [onPrinterInfoQuery](arkts-basicservices-print-onprinterinfoquery-f-sys.md#onprinterinfoquery) | Register event callback for the printer info queried. |
| [queryAllActivePrintJobs](arkts-basicservices-print-queryallactiveprintjobs-f-sys.md#queryallactiveprintjobs) | Queries all active print jobs. This API uses a promise to return the result. |
| [queryAllPrinterExtensionInfos](arkts-basicservices-print-queryallprinterextensioninfos-f-sys.md#queryallprinterextensioninfos) | Obtains the information of all installed printer extensions. This API uses an asynchronous callback to return the result. |
| [queryAllPrinterExtensionInfos](arkts-basicservices-print-queryallprinterextensioninfos-f-sys.md#queryallprinterextensioninfos) | Obtains the information of all installed printer extensions. This API uses a promise to return the result. |
| [queryAllPrinterPpds](arkts-basicservices-print-queryallprinterppds-f-sys.md#queryallprinterppds) | Query all printer ppds. |
| [queryPrinterCapability](arkts-basicservices-print-queryprintercapability-f-sys.md#queryprintercapability) | Queries the printer capability. This API uses an asynchronous callback to return the result. |
| [queryPrinterCapability](arkts-basicservices-print-queryprintercapability-f-sys.md#queryprintercapability) | Queries the printer capability. This API uses a promise to return the result. |
| [queryPrinterCapabilityByUri](arkts-basicservices-print-queryprintercapabilitybyuri-f-sys.md#queryprintercapabilitybyuri) | Query printer capabilityies by printer uri. |
| [queryPrinterInfoByIp](arkts-basicservices-print-queryprinterinfobyip-f-sys.md#queryprinterinfobyip) | Query printer info by ip. |
| [queryPrintJobById](arkts-basicservices-print-queryprintjobbyid-f-sys.md#queryprintjobbyid) | Queries a print job by ID. This API uses an asynchronous callback to return the result. |
| [queryPrintJobById](arkts-basicservices-print-queryprintjobbyid-f-sys.md#queryprintjobbyid) | Queries a print job by ID. This API uses a promise to return the result. |
| [queryPrintJobList](arkts-basicservices-print-queryprintjoblist-f-sys.md#queryprintjoblist) | Queries all print jobs. This API uses an asynchronous callback to return the result. |
| [queryPrintJobList](arkts-basicservices-print-queryprintjoblist-f-sys.md#queryprintjoblist) | Queries all print jobs. This API uses a promise to return the result. |
| [queryRecommendDriversById](arkts-basicservices-print-queryrecommenddriversbyid-f-sys.md#queryrecommenddriversbyid) | Query recommend printer drivers by printer ID. |
| [removePrinters](arkts-basicservices-print-removeprinters-f-sys.md#removeprinters) | Removes printers. This API uses an asynchronous callback to return the result. |
| [removePrinters](arkts-basicservices-print-removeprinters-f-sys.md#removeprinters) | Removes printers. This API uses a promise to return the result. |
| [requestPrintPreview](arkts-basicservices-print-requestprintpreview-f-sys.md#requestprintpreview) | Requests print preview data. This API uses a callback to return the result. |
| [requestPrintPreview](arkts-basicservices-print-requestprintpreview-f-sys.md#requestprintpreview) | Requests print preview data. This API uses a promise to return the result. |
| [restartPrintJob](arkts-basicservices-print-restartprintjob-f-sys.md#restartprintjob) | Restarts a print job that has been finished before. This API uses a promise to return the result. |
| [savePdfFileJob](arkts-basicservices-print-savepdffilejob-f-sys.md#savepdffilejob) | Save the pdf file for a print job. |
| [setDefaultPrinter](arkts-basicservices-print-setdefaultprinter-f-sys.md#setdefaultprinter) | Sets the default printer. This API uses a promise to return the result. |
| [setPrinterPreferences](arkts-basicservices-print-setprinterpreferences-f-sys.md#setprinterpreferences) | Sets the printer preferences. This API uses a promise to return the result. |
| [startGettingPrintFile](arkts-basicservices-print-startgettingprintfile-f-sys.md#startgettingprintfile) | Starts to obtain the print file. This API uses an asynchronous callback to return the result. |
| [startPrintJob](arkts-basicservices-print-startprintjob-f-sys.md#startprintjob) | Starts the specified print job. This API uses an asynchronous callback to return the result. |
| [startPrintJob](arkts-basicservices-print-startprintjob-f-sys.md#startprintjob) | Starts the specified print job. This API uses a promise to return the result. |
| [updateExtensionInfo](arkts-basicservices-print-updateextensioninfo-f-sys.md#updateextensioninfo) | Updates the printer extension information. This API uses an asynchronous callback to return the result. |
| [updateExtensionInfo](arkts-basicservices-print-updateextensioninfo-f-sys.md#updateextensioninfo) | Updates the printer extension information. This API uses a promise to return the result. |
| [updatePrinters](arkts-basicservices-print-updateprinters-f-sys.md#updateprinters) | Updates information about the specified printers. This API uses an asynchronous callback to return the result. |
| [updatePrinters](arkts-basicservices-print-updateprinters-f-sys.md#updateprinters) | Updates information about the specified printers. This API uses a promise to return the result. |
| [updatePrinterState](arkts-basicservices-print-updateprinterstate-f-sys.md#updateprinterstate) | Updates the printer state. This API uses an asynchronous callback to return the result. |
| [updatePrinterState](arkts-basicservices-print-updateprinterstate-f-sys.md#updateprinterstate) | Updates the printer state. This API uses a promise to return the result. |
| [queryAllPrintJobs](arkts-basicservices-print-queryallprintjobs-f-sys.md#queryallprintjobs) | Queries all print jobs. This API uses an asynchronous callback to return the result. |
| [queryAllPrintJobs](arkts-basicservices-print-queryallprintjobs-f-sys.md#queryallprintjobs) | Queries all print jobs. This API uses a promise to return the result. |
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
