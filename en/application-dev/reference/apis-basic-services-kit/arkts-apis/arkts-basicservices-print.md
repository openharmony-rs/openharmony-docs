# @ohos.print(Print)

This module provides APIs for printing-related operations, including file printing, print job event monitoring, printer discovery and management, and print job status update. It is applicable to scenarios where printing capabilities need to be integrated into an app.

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
| [addPrinter](arkts-basicservices-print-addprinter-f.md#addprinter-1) | Adds a printer to the system. This API uses a promise to return the result. This API is intended for scenarios where printers or scanners need to be managed, such as the management of the printer drivers, printing management software, third-party printing management software, and cloud printing. |
| [addPrinterToDiscovery](arkts-basicservices-print-addprintertodiscovery-f.md#addprintertodiscovery-1) | Adds a printer to the printer discovery list. This API uses a promise to return the result. |
| [connectPrinter](arkts-basicservices-print-connectprinter-f.md#connectprinter-1) | Connects to a printer by printer ID. This API uses an asynchronous callback to return the result. |
| [connectPrinter](arkts-basicservices-print-connectprinter-f.md#connectprinter-2) | Connects to a printer by printer ID. This API uses a promise to return the result. |
| [getAddedPrinters](arkts-basicservices-print-getaddedprinters-f.md#getaddedprinters-1) | Obtains the list of printers added to the system. This API uses a promise to return the result. |
| [getPrinterInformationById](arkts-basicservices-print-getprinterinformationbyid-f.md#getprinterinformationbyid-1) | Obtains printer information based on the printer ID. This API uses a promise to return the result. |
| [notifyWatermarkComplete](arkts-basicservices-print-notifywatermarkcomplete-f.md#notifywatermarkcomplete-1) | Notifies that watermark processing is complete so that the subsequent printing process can continue. |
| [off('printerChange')](arkts-basicservices-print-off-f.md#offprinterchange) | Unregisters the callback for printer change events. |
| [on('printerChange')](arkts-basicservices-print-on-f.md#onprinterchange) | Registers a listener for the printer change events. This API uses an asynchronous callback to return the result. |
| [print](arkts-basicservices-print-f.md#print-3) | Prints files. The system print preview page is started. This API uses an asynchronous callback to return the result. |
| [print](arkts-basicservices-print-f.md#print-4) | Prints files. The system print preview page is started. This API uses a promise to return the result. |
| [print](arkts-basicservices-print-f.md#print-5) | Prints a file. This API uses a promise to return the result. Currently, only the .pdf file type is supported. When a third-party app needs to pass the file descriptor (FD) to start the system print preview page for printing, this API can be used to pass a **custom PrintDocumentAdapter** value to update the file to be printed. |
| [registerWatermarkCallback](arkts-basicservices-print-registerwatermarkcallback-f.md#registerwatermarkcallback-1) | Registers an event listener for forcible watermark processing. A forcible watermark is the watermark that must be added to printed files according to enterprise management policies. In enterprise management scenarios, when a watermark (such as a company logo or confidentiality level mark) needs to be forcibly added to printed files, you can use this API to register a watermark processing callback. |
| [removePrinterFromDiscovery](arkts-basicservices-print-removeprinterfromdiscovery-f.md#removeprinterfromdiscovery-1) | Removes a printer from the printer discovery list. This API uses a promise to return the result. |
| [startDiscoverPrinter](arkts-basicservices-print-startdiscoverprinter-f.md#startdiscoverprinter-1) | Discovers printers by specifying the extension list. The discovered printers have the specified print extension abilities. If an empty extension list is specified, all extension abilities are loaded. This API uses an asynchronous callback to return the result. When printer discovery is no longer needed, call [stopDiscoverPrinter](arkts-basicservices-print-stopdiscoverprinter-f.md#stopdiscoverprinter-1) to stop the discovery and release system resources. Otherwise, the system will continuously discover printers, consuming system resources. |
| [startDiscoverPrinter](arkts-basicservices-print-startdiscoverprinter-f.md#startdiscoverprinter-2) | Discovers printers by specifying the extension list. The discovered printers have the specified print extension abilities. If an empty extension list is specified, all extension abilities are loaded. This API uses a promise to return the result. When printer discovery is no longer needed, call [stopDiscoverPrinter](arkts-basicservices-print-stopdiscoverprinter-f.md#stopdiscoverprinter-1) to stop the discovery and release system resources. Otherwise, the system will continuously discover printers, consuming system resources. |
| [startPrint](arkts-basicservices-print-startprint-f.md#startprint-1) | Prints a file or binary data. This API uses a promise to return the result. This API directly creates a print job by specifying the target printer ID and print parameters in **PrintJobData**. Call **print.print** to display the system print preview page. |
| [stopDiscoverPrinter](arkts-basicservices-print-stopdiscoverprinter-f.md#stopdiscoverprinter-1) | Stops discovering printers. This API uses an asynchronous callback to return the result. |
| [stopDiscoverPrinter](arkts-basicservices-print-stopdiscoverprinter-f.md#stopdiscoverprinter-2) | Stops discovering printers. This API uses a promise to return the result. |
| [unregisterWatermarkCallback](arkts-basicservices-print-unregisterwatermarkcallback-f.md#unregisterwatermarkcallback-1) | Deregisters an event listener for forcible watermark processing. When an enterprise management app no longer needs to forcibly add watermarks to printed files, you can call this API to unregister the previously registered watermark processing callback. |
| [updatePrinterInDiscovery](arkts-basicservices-print-updateprinterindiscovery-f.md#updateprinterindiscovery-1) | Updates the printer capabilities to the printer discovery list. This API uses a promise to return the result. |
| [updatePrinterInformation](arkts-basicservices-print-updateprinterinformation-f.md#updateprinterinformation-1) | Updates the information of a printer in the system. This API uses a promise to return the result. Currently, only the **alias** and **options** fields of [PrinterInformation](arkts-basicservices-print-printerinformation-i.md) can be updated. |
| [updatePrintJobState](arkts-basicservices-print-updateprintjobstate-f.md#updateprintjobstate-1) | Updates the print job state. This API uses an asynchronous callback to return the result. |
| [updatePrintJobState](arkts-basicservices-print-updateprintjobstate-f.md#updateprintjobstate-2) | Updates the print job state. This API uses a promise to return the result. |
| [print](arkts-basicservices-print-f.md#print-1) | Prints files. This API uses an asynchronous callback to return the result. To start the system print preview page, call the [print](arkts-basicservices-print-f.md#print-3) API and pass in context. |
| [print](arkts-basicservices-print-f.md#print-2) | Prints files. This API uses a promise to return the result. To start the system print preview page, call the [print](arkts-basicservices-print-f.md#print-4) API and pass in context. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [addPrinters](arkts-basicservices-print-addprinters-f-sys.md#addprinters-1) | Adds printers. This API uses an asynchronous callback to return the result. |
| [addPrinters](arkts-basicservices-print-addprinters-f-sys.md#addprinters-2) | Adds printers. This API uses a promise to return the result. |
| [addPrinterToCups](arkts-basicservices-print-addprintertocups-f-sys.md#addprintertocups-1) | Adds a printer to CUPS. This API uses an asynchronous callback to return the result. CUPS is the print service framework in the system, which is used to manage printers and print jobs. |
| [analyzePrintEvents](arkts-basicservices-print-analyzeprintevents-f-sys.md#analyzeprintevents-1) | Analyze print events. |
| [authPrintJob](arkts-basicservices-print-authprintjob-f-sys.md#authprintjob-1) | Authenticate a print job. |
| [authSmbDeviceAsRegisteredUser](arkts-basicservices-print-authsmbdeviceasregistereduser-f-sys.md#authsmbdeviceasregistereduser-1) | Authenticate SMB device as registered user and get available printers. |
| [cancelPrintJob](arkts-basicservices-print-cancelprintjob-f-sys.md#cancelprintjob-1) | Cancels a print job that has been sent to the printer. This API uses an asynchronous callback to return the result. Only an ongoing print job can be canceled. Calling this API for a nonexistent or completed job returns an error. |
| [cancelPrintJob](arkts-basicservices-print-cancelprintjob-f-sys.md#cancelprintjob-2) | Cancels a print job that has been sent to the printer. This API uses a promise to return the result. Only an ongoing print job can be canceled. Calling this API for a nonexistent or completed job returns an error. |
| [checkPreferencesConflicts](arkts-basicservices-print-checkpreferencesconflicts-f-sys.md#checkpreferencesconflicts-1) | Check preferences conflicts. |
| [connectPrinterByIdAndPpd](arkts-basicservices-print-connectprinterbyidandppd-f-sys.md#connectprinterbyidandppd-1) | Connect a printer by the printer ID and ppd. |
| [connectPrinterByIpAndPpd](arkts-basicservices-print-connectprinterbyipandppd-f-sys.md#connectprinterbyipandppd-1) | Connect a printer by the printer IP and ppd. |
| [deletePrinterFromCups](arkts-basicservices-print-deleteprinterfromcups-f-sys.md#deleteprinterfromcups-1) | Deletes a printer from CUPS. This API uses an asynchronous callback to return the result. CUPS is the print service framework in the system, which is used to manage printers and print jobs. |
| [disconnectPrinter](arkts-basicservices-print-disconnectprinter-f-sys.md#disconnectprinter-1) | Disconnects from the specified printer. This API uses an asynchronous callback to return the result. |
| [disconnectPrinter](arkts-basicservices-print-disconnectprinter-f-sys.md#disconnectprinter-2) | Disconnects from the specified printer. This API uses a promise to return the result. |
| [discoverUsbPrinters](arkts-basicservices-print-discoverusbprinters-f-sys.md#discoverusbprinters-1) | Discovers USB printers. This API uses an asynchronous callback to return the result. It returns the discovered USB printer information, and the printer URI can be used to query printer capabilities by calling [queryPrinterCapabilityByUri](arkts-basicservices-print-queryprintercapabilitybyuri-f-sys.md) or to add the printer to CUPS by calling [addPrinterToCups](arkts-basicservices-print-addprintertocups-f-sys.md). |
| [getPrinterDefaultPreferences](arkts-basicservices-print-getprinterdefaultpreferences-f-sys.md#getprinterdefaultpreferences-1) | Get default preferences by printer ID. |
| [getPrinterInfoById](arkts-basicservices-print-getprinterinfobyid-f-sys.md#getprinterinfobyid-1) | Obtains printer information based on the printer ID. This API uses an asynchronous callback to return the result. |
| [getSharedHosts](arkts-basicservices-print-getsharedhosts-f-sys.md#getsharedhosts-1) | Get all available shared hosts. |
| notifyPrintService('spooler_closed_for_cancelled' | 'spooler_closed_for_started') | Notifies the print service that the print preview page is closed. This API uses an asynchronous callback to return the result. This method is used to notify the print service to perform clearance, exit, and other operations after the print preview page is closed. |
| notifyPrintService('spooler_closed_for_cancelled' | 'spooler_closed_for_started') | Notifies the print service that the print preview page is closed. This API uses a promise to return the result. This method is used to notify the print service to perform clearance, exit, and other operations after the print preview page is closed. |
| [notifyPrintServiceEvent](arkts-basicservices-print-notifyprintserviceevent-f-sys.md#notifyprintserviceevent-1) | Notifies the print service of the print app events. This API uses a promise to return the result. This method is used to notify the print service to perform corresponding processing when a lifecycle event such as creation and destruction of a print app occurs. |
| [notifyPrintServiceEvent](arkts-basicservices-print-notifyprintserviceevent-f-sys.md#notifyprintserviceevent-2) | Notifies the print service of the print app events. This API uses a promise to return the result. This method is used to notify the print service based on the print job ID to perform corresponding processing when a lifecycle event such as creation and destruction of a print app occurs. |
| [off('printerStateChange')](arkts-basicservices-print-off-f-sys.md#offprinterstatechange) | Unregisters the listener for printer state change events. This API uses a callback to return the result. |
| [off('jobStateChange')](arkts-basicservices-print-off-f-sys.md#offjobstatechange) | Unregisters the listener for print job state change events. This API uses a callback to return the result. |
| [off('extInfoChange')](arkts-basicservices-print-off-f-sys.md#offextinfochange) | Unregisters the callback for the printer extension information change event. This API uses a callback to return the result. |
| [offPrinterInfoQuery](arkts-basicservices-print-offprinterinfoquery-f-sys.md#offprinterinfoquery-1) | Unregister event callback for the printer info queried. |
| [on('printerStateChange')](arkts-basicservices-print-on-f-sys.md#onprinterstatechange) | Registers a callback for the printer state change event. This API uses a callback to return the result. When the listener is no longer needed, call [print.off('printerStateChange')](arkts-basicservices-print-off-f-sys.md#offprinterstatechange) to unregister the callback. Otherwise, the callback may be continuously triggered, causing memory leak. |
| [on('jobStateChange')](arkts-basicservices-print-on-f-sys.md#onjobstatechange) | Registers a callback for the print job state change event. This API uses a callback to return the result. When the listener is no longer needed, call [print.off('jobStateChange')](arkts-basicservices-print-off-f-sys.md#offjobstatechange) to unregister the callback. Otherwise, the callback may be continuously triggered, causing memory leak. |
| [on('extInfoChange')](arkts-basicservices-print-on-f-sys.md#onextinfochange) | Registers a callback for the printer extension information change event. This API uses a callback to return the result. When the listener is no longer needed, call [print.off('extInfoChange')](arkts-basicservices-print-off-f-sys.md#offextinfochange) to unregister the callback. Otherwise, the callback may be continuously triggered, causing memory leak. |
| [onPrinterInfoQuery](arkts-basicservices-print-onprinterinfoquery-f-sys.md#onprinterinfoquery-1) | Register event callback for the printer info queried. |
| [queryAllActivePrintJobs](arkts-basicservices-print-queryallactiveprintjobs-f-sys.md#queryallactiveprintjobs-1) | Queries all active print jobs. This API uses an asynchronous callback to return the result. |
| [queryAllPrinterExtensionInfos](arkts-basicservices-print-queryallprinterextensioninfos-f-sys.md#queryallprinterextensioninfos-1) | Obtains the information of all installed printer extensions. This API uses an asynchronous callback to return the result. |
| [queryAllPrinterExtensionInfos](arkts-basicservices-print-queryallprinterextensioninfos-f-sys.md#queryallprinterextensioninfos-2) | Obtains the information of all installed printer extensions. This API uses a promise to return the result. |
| [queryAllPrinterPpds](arkts-basicservices-print-queryallprinterppds-f-sys.md#queryallprinterppds-1) | Query all printer ppds. |
| [queryPrinterCapability](arkts-basicservices-print-queryprintercapability-f-sys.md#queryprintercapability-1) | Queries the printer capability. This API uses an asynchronous callback to return the result. The query result can be obtained from **PrinterInfo.capability** in the [on('printerStateChange')](arkts-basicservices-print-on-f-sys.md#onprinterstatechange) event callback. |
| [queryPrinterCapability](arkts-basicservices-print-queryprintercapability-f-sys.md#queryprintercapability-2) | Queries the printer capability. This API uses a promise to return the result. The query result can be obtained from **PrinterInfo.capability** in the [on('printerStateChange')](arkts-basicservices-print-on-f-sys.md#onprinterstatechange) event callback. |
| [queryPrinterCapabilityByUri](arkts-basicservices-print-queryprintercapabilitybyuri-f-sys.md#queryprintercapabilitybyuri-1) | Queries the printer capability by the printer URI. This API uses a promise to return the result. This API can be used to query the capabilities of a printer when the printer URI is known but the printer is not registered locally. It can also be used to discover the capabilities of a USB printer. |
| [queryPrinterInfoByIp](arkts-basicservices-print-queryprinterinfobyip-f-sys.md#queryprinterinfobyip-1) | Query printer info by ip. |
| [queryPrintJobById](arkts-basicservices-print-queryprintjobbyid-f-sys.md#queryprintjobbyid-1) | Queries a print job by ID. This API uses an asynchronous callback to return the result. |
| [queryPrintJobById](arkts-basicservices-print-queryprintjobbyid-f-sys.md#queryprintjobbyid-2) | Queries a print job by ID. This API uses a promise to return the result. |
| [queryPrintJobList](arkts-basicservices-print-queryprintjoblist-f-sys.md#queryprintjoblist-1) | Queries all print jobs. This API uses an asynchronous callback to return the result. |
| [queryPrintJobList](arkts-basicservices-print-queryprintjoblist-f-sys.md#queryprintjoblist-2) | Queries all print jobs. This API uses a promise to return the result. |
| [queryRecommendDriversById](arkts-basicservices-print-queryrecommenddriversbyid-f-sys.md#queryrecommenddriversbyid-1) | Query recommend printer drivers by printer ID. |
| [removePrinters](arkts-basicservices-print-removeprinters-f-sys.md#removeprinters-1) | Removes printers. This API uses an asynchronous callback to return the result. |
| [removePrinters](arkts-basicservices-print-removeprinters-f-sys.md#removeprinters-2) | Removes printers. This API uses a promise to return the result. |
| [requestPrintPreview](arkts-basicservices-print-requestprintpreview-f-sys.md#requestprintpreview-1) | Requests print preview data. This API uses a callback to return the result. |
| [requestPrintPreview](arkts-basicservices-print-requestprintpreview-f-sys.md#requestprintpreview-2) | Requests print preview data. This API uses a promise to return the result. |
| [restartPrintJob](arkts-basicservices-print-restartprintjob-f-sys.md#restartprintjob-1) | Restarts a failed print job. This API uses a promise to return the result. |
| [savePdfFileJob](arkts-basicservices-print-savepdffilejob-f-sys.md#savepdffilejob-1) | Save the pdf file for a print job. |
| [setDefaultPrinter](arkts-basicservices-print-setdefaultprinter-f-sys.md#setdefaultprinter-1) | Sets the default printer. This API uses an asynchronous callback to return the result. It is used in scenarios where the system default printer needs to be specified, such as when a user manually selects a default printer or the system automatically sets the printer used last time as the default printer. |
| [setPrinterPreferences](arkts-basicservices-print-setprinterpreferences-f-sys.md#setprinterpreferences-1) | Sets the printer preferences. This API uses a promise to return the result. |
| [startGettingPrintFile](arkts-basicservices-print-startgettingprintfile-f-sys.md#startgettingprintfile-1) | Starts to obtain the print file. This API uses an asynchronous callback to return the result. After **print()** is executed, **jobId** is created, and [PrintDocumentAdapter](arkts-basicservices-print-printdocumentadapter-i.md) is registered, you can call this function to obtain the actual print file content. |
| [startPrintJob](arkts-basicservices-print-startprintjob-f-sys.md#startprintjob-1) | Starts a print job. This API uses an asynchronous callback to return the result. You can listen for the [on('jobStateChange')](arkts-basicservices-print-on-f-sys.md#onjobstatechange) event to obtain the print job state change. |
| [startPrintJob](arkts-basicservices-print-startprintjob-f-sys.md#startprintjob-2) | Starts a print job. This API uses a promise to return the result. You can listen for the [on('jobStateChange')](arkts-basicservices-print-on-f-sys.md#onjobstatechange) event to obtain the print job state change. |
| [updateExtensionInfo](arkts-basicservices-print-updateextensioninfo-f-sys.md#updateextensioninfo-1) | Updates the printer extension information. This API uses an asynchronous callback to return the result. |
| [updateExtensionInfo](arkts-basicservices-print-updateextensioninfo-f-sys.md#updateextensioninfo-2) | Updates the printer extension information. This API uses a promise to return the result. |
| [updatePrinters](arkts-basicservices-print-updateprinters-f-sys.md#updateprinters-1) | Updates the information of the specified printers. This API uses an asynchronous callback to return the result. |
| [updatePrinters](arkts-basicservices-print-updateprinters-f-sys.md#updateprinters-2) | Updates the information of the specified printers. This API uses a promise to return the result. |
| [updatePrinterState](arkts-basicservices-print-updateprinterstate-f-sys.md#updateprinterstate-1) | Updates the printer state. This API uses an asynchronous callback to return the result. |
| [updatePrinterState](arkts-basicservices-print-updateprinterstate-f-sys.md#updateprinterstate-2) | Updates the printer state. This API uses a promise to return the result. |
| [queryAllPrintJobs](arkts-basicservices-print-queryallprintjobs-f-sys.md#queryallprintjobs-1) | Queries all print jobs. This API uses an asynchronous callback to return the result. |
| [queryAllPrintJobs](arkts-basicservices-print-queryallprintjobs-f-sys.md#queryallprintjobs-2) | Queries all print jobs. This API uses a promise to return the result. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [PpdInfo](arkts-basicservices-print-ppdinfo-i.md) | Defines the PPD file information of the printer driver. |
| [PreviewAttribute](arkts-basicservices-print-previewattribute-i.md) | Defines the print preview attributes. |
| [PrintAttributes](arkts-basicservices-print-printattributes-i.md) | Defines the print attributes. |
| [PrintDocumentAdapter](arkts-basicservices-print-printdocumentadapter-i.md) | Provides information about the document to print. This API must be implemented by a third-party application. This API provides a callback to listen for file rendering and print job status events. You can pass a **PrintDocumentAdapter** instance through the **print.print** API. |
| [PrinterCapabilities](arkts-basicservices-print-printercapabilities-i.md) | Defines the printer capabilities. |
| [PrinterCapability](arkts-basicservices-print-printercapability-i.md) | Defines the printer capabilities. |
| [PrinterInfo](arkts-basicservices-print-printerinfo-i.md) | Defines the printer information. |
| [PrinterInformation](arkts-basicservices-print-printerinformation-i.md) | Defines the printer information. |
| [PrinterPreferences](arkts-basicservices-print-printerpreferences-i.md) | Defines the printer preferences. |
| [PrinterRange](arkts-basicservices-print-printerrange-i.md) | Defines the print range. |
| [PrintJob](arkts-basicservices-print-printjob-i.md) | Defines a print job. |
| [PrintJobData](arkts-basicservices-print-printjobdata-i.md) | Defines a print job. |
| [PrintMargin](arkts-basicservices-print-printmargin-i.md) | Defines the page margins for printing. |
| [PrintPageRange](arkts-basicservices-print-printpagerange-i.md) | Defines the print range. |
| [PrintPageSize](arkts-basicservices-print-printpagesize-i.md) | Defines the size of the printed page. |
| [PrintResolution](arkts-basicservices-print-printresolution-i.md) | Defines the resolution for printing. |
| [PrintTask](arkts-basicservices-print-printtask-i.md) | Defines a callback class for listening for print job status change events (such as blocking, success, failure, and cancellation) during print job execution. After obtaining a **PrintTask** instance using **print.print**, you can register a listener to listen for the status changes of the print job. |
| [SharedHost](arkts-basicservices-print-sharedhost-i.md) | Defines the shared device information. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [PrinterExtensionInfo](arkts-basicservices-print-printerextensioninfo-i-sys.md) | Defines the printer extension information. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [PrinterChangeCallback](arkts-basicservices-print-printerchangecallback-t.md) | Defines a callback that takes the printer event and printer information as parameters. |
| [WatermarkCallback](arkts-basicservices-print-watermarkcallback-t.md) | Callback type used to register an event listener for forcible watermark processing. |

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
| [DefaultPrinterType](arkts-basicservices-print-defaultprintertype-e.md) | Enumerates the methods for determining the default printer. |
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
| [WatermarkHandleResult](arkts-basicservices-print-watermarkhandleresult-e.md) | Enumerates the results of forcible watermark processing. |
