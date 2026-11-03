# @ohos.scan(Scan)

This module provides JavaScript APIs of the scan framework, which support scanner discovery and management, scanning execution, and device event listening. It is applicable to scenarios where an app needs to integrate a scanner for digital document collection and device management.

> **NOTE:** 
> 
> This topic describes only public APIs provided by the module.

**Since:** 20

<!--Device-unnamed-declare namespace scan--><!--Device-unnamed-declare namespace scan-End-->

**System capability:** SystemCapability.Print.PrintFramework

## Modules to Import

```TypeScript
import { scan } from '@kit.BasicServicesKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [cancelScan](arkts-basicservices-scan-cancelscan-f.md#cancelscan-1) | Cancels scanning. This API uses a promise to return the result. This method can be called only after scanning starts. |
| [closeScanner](arkts-basicservices-scan-closescanner-f.md#closescanner-1) | Closes a scanner. This API uses a promise to return the result. After a scanner is closed, you cannot obtain or set parameters for the scanner or perform scanning operations on the scanner. To use the scanner again, call **openScanner()**. |
| [exit](arkts-basicservices-scan-exit-f.md#exit-1) | Exits the scan service. This API uses a promise to return the result. After the scan service exits, other scan methods are unavailable. To use them again, call **init()** again. |
| [getPictureScanProgress](arkts-basicservices-scan-getpicturescanprogress-f.md#getpicturescanprogress-1) | Obtains the progress of scanning a picture. This API uses a promise to return the result. This method can be called only after scanning starts. |
| [getScannerCurrentSetting](arkts-basicservices-scan-getscannercurrentsetting-f.md#getscannercurrentsetting-1) | Obtains the current scanner settings. This API uses a promise to return the result. This method can be called only after the scanner is opened by calling **openScanner()**. |
| [getScannerParameter](arkts-basicservices-scan-getscannerparameter-f.md#getscannerparameter-1) | Obtains scanner parameters. This API uses a promise to return the result. This method can be called only after the scanner is opened by calling **openScanner()**. Your app can use this method to obtain the parameter index (**optionIndex**), which is used to call methods such as **setScannerParameter**, **setScanAutoOption**, and **getScannerCurrentSetting**. |
| [init](arkts-basicservices-scan-init-f.md#init-1) | Initializes the scan service. This API must be called before other scanning APIs. This API uses a promise to return the result. After using the service, call **exit()** to exit the scan service and release resources. |
| [off('scanDeviceFound')](arkts-basicservices-scan-off-f.md#offscandevicefound) | Unregisters a callback used to listen for the scanner discovery event. |
| [off('scanDeviceSync')](arkts-basicservices-scan-off-f.md#offscandevicesync) | Unregisters a callback used to listen for the scanner sync event. |
| [on('scanDeviceFound')](arkts-basicservices-scan-on-f.md#onscandevicefound) | Registers a callback to listen for the scanner discovery event. This callback is triggered when a new scanner is discovered by calling **startScannerDiscovery**. This API uses an asynchronous callback to return the result. |
| [on('scanDeviceSync')](arkts-basicservices-scan-on-f.md#onscandevicesync) | Registers a callback to listen for the scanner sync event. This callback is triggered when the scanner status changes (for example, the scanner ID changes or the scanner goes offline), notifying the app to update the scanner list. This API uses an asynchronous callback to return the result. This API is applicable to scenarios where your app needs to continuously track scanner status changes, for example, updating local device information when a scanner is reconnected. |
| [openScanner](arkts-basicservices-scan-openscanner-f.md#openscanner-1) | Opens a scanner. This API can be used only after initialization is complete by calling **init()**. This API uses a promise to return the result. After using the scanner, call **closeScanner()** to close the scanner and release resources. |
| [setScanAutoOption](arkts-basicservices-scan-setscanautooption-f.md#setscanautooption-1) | Sets the scan option to auto mode, in which the scanner automatically determines the value of this option. This API uses a promise to return the result. This method can be called only after the scanner is opened by calling **openScanner()**. |
| [setScannerParameter](arkts-basicservices-scan-setscannerparameter-f.md#setscannerparameter-1) | Sets scanner parameters. This API uses a promise to return the result. This method can be called only after the scanner is opened by calling **openScanner()**. |
| [startScan](arkts-basicservices-scan-startscan-f.md#startscan-1) | Starts scanning. This API uses a promise to return the result. This method can be called only after the scanner is opened by calling **openScanner()**. During the scanning, you can call **getPictureScanProgress()** to obtain the scanning progress. To cancel the scanning, call **cancelScan()**. |
| [startScannerDiscovery](arkts-basicservices-scan-startscannerdiscovery-f.md#startscannerdiscovery-1) | Starts scanner discovery. The discovered scanner information is returned through the **on('scanDeviceFound')** event callback. This API can be used only after initialization is complete by calling **init()**. This API uses a promise to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [addScanner](arkts-basicservices-scan-addscanner-f-sys.md#addscanner-1) | Adds a scanner. This is a system API. This method can be used to discover and add a scanner based on the specified discovery mode. After the scanner is added, the **scanDeviceAdd event** is triggered. You can use **on('scanDeviceAdd')** to listen for the device addition event. This API uses a promise to return the result. |
| [deleteScanner](arkts-basicservices-scan-deletescanner-f-sys.md#deletescanner-1) | Deletes a scanner. This is a system API. This method can be used to remove a scanner when it is offline or no longer needed. After the scanner is deleted, the **scanDeviceDel** event is triggered. You can use **on('scanDeviceDel')** to listen for the device deletion event. This API uses a promise to return the result. |
| [getAddedScanners](arkts-basicservices-scan-getaddedscanners-f-sys.md#getaddedscanners-1) | Obtains the added scanners. This is a system API. This API can be used to query the list of available scanners for users to select one. This API uses a promise to return the result. |
| [off('scanDeviceAdd')](arkts-basicservices-scan-off-f-sys.md#offscandeviceadd) | Unregisters the callback used to listen for the scanner addition event. This is a system API. |
| [off('scanDeviceDel')](arkts-basicservices-scan-off-f-sys.md#offscandevicedel) | Unregisters the callback used to listen for the scanner deletion event. This is a system API. |
| [on('scanDeviceAdd')](arkts-basicservices-scan-on-f-sys.md#onscandeviceadd) | Registers a callback used to listen for the scanner addition event. This is a system API. This callback is triggered when a scanner is successfully added and returns the information of the added scanner. This API uses an asynchronous callback to return the result. |
| [on('scanDeviceDel')](arkts-basicservices-scan-on-f-sys.md#onscandevicedel) | Registers a callback used to listen for the scanner deletion event. This is a system API. This callback is triggered when a scanner is deleted and returns the information of the deleted scanner. This API uses an asynchronous callback to return the result. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [PictureScanProgress](arkts-basicservices-scan-picturescanprogress-i.md) | Defines the progress of scanning pictures. |
| [Range](arkts-basicservices-scan-range-i.md) | Defines the range. |
| [ScannerDevice](arkts-basicservices-scan-scannerdevice-i.md) | Defines the scanner. |
| [ScannerOptionValue](arkts-basicservices-scan-scanneroptionvalue-i.md) | Defines the scanner option value. When the constraint type of the option is **SCAN_CONSTRAINT_STRING_LIST**, the option value must be a string in the **optionConstraintString** set. |
| [ScannerParameter](arkts-basicservices-scan-scannerparameter-i.md) | Defines the scanner parameters. |
| [ScannerSyncDevice](arkts-basicservices-scan-scannersyncdevice-i.md) | Defines the device to be synced from the scanner. |

### Enums

| Name | Description |
| --- | --- |
| [ConstraintType](arkts-basicservices-scan-constrainttype-e.md) | Enumerates the parameter constraint types. |
| [OptionValueType](arkts-basicservices-scan-optionvaluetype-e.md) | Enumerates the option value types. |
| [PhysicalUnit](arkts-basicservices-scan-physicalunit-e.md) | Enumerates the physical units. |
| [ScanErrorCode](arkts-basicservices-scan-scanerrorcode-e.md) | Enumerates the scan error codes. |
| [ScannerDiscoveryMode](arkts-basicservices-scan-scannerdiscoverymode-e.md) | Enumerates the scanner discovery modes. |
| [ScannerSyncMode](arkts-basicservices-scan-scannersyncmode-e.md) | Enumerates the scanner sync modes. |
