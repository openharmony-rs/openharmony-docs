# @ohos.scan

This module provides JavaScript APIs of the scan framework for discovering and connecting to scanners.

> **NOTE:** 
> 
> This topic describes only public APIs provided by the module.

**Since:** 20

**System capability:** SystemCapability.Print.PrintFramework

## Modules to Import

```TypeScript
import { scan } from '@kit.BasicServicesKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [cancelScan](arkts-basicservices-scan-cancelscan-f.md) | Cancels scanning. This API uses a promise to return the result. |
| [closeScanner](arkts-basicservices-scan-closescanner-f.md) | Closes a scanner. This API uses a promise to return the result. |
| [exit](arkts-basicservices-scan-exit-f.md) | Exits the scan service. This API uses a promise to return the result. |
| [getPictureScanProgress](arkts-basicservices-scan-getpicturescanprogress-f.md) | Obtains the progress of scanning a picture. This API uses a promise to return the result. |
| [getScannerCurrentSetting](arkts-basicservices-scan-getscannercurrentsetting-f.md) | Obtains the current scanner settings. This API uses a promise to return the result. |
| [getScannerParameter](arkts-basicservices-scan-getscannerparameter-f.md) | Obtains scanner parameters. This API uses a promise to return the result. |
| [init](arkts-basicservices-scan-init-f.md) | Initializes the scan service. This API uses a promise to return the result. |
| [off](arkts-basicservices-scan-off-f.md#offscandevicefound) | Unregisters a callback used to listen for the scanner discovery event. This API uses an asynchronous callback to return the result. |
| [off](arkts-basicservices-scan-off-f.md#offscandevicesync) | Unregisters a callback used to listen for the scanner sync event. This API uses an asynchronous callback to return the result. |
| [on](arkts-basicservices-scan-on-f.md#onscandevicefound) | Registers a callback used to listen for the scanner discovery event. This API uses an asynchronous callback to return the result. |
| [on](arkts-basicservices-scan-on-f.md#onscandevicesync) | Registers a callback used to listen for the scanner sync event. This API uses an asynchronous callback to return the result. |
| [openScanner](arkts-basicservices-scan-openscanner-f.md) | Opens a scanner. This API uses a promise to return the result. |
| [setScanAutoOption](arkts-basicservices-scan-setscanautooption-f.md) | Sets the scan option to auto mode. This API uses a promise to return the result. |
| [setScannerParameter](arkts-basicservices-scan-setscannerparameter-f.md) | Sets scanner parameters. This API uses a promise to return the result. |
| [startScan](arkts-basicservices-scan-startscan-f.md) | Starts scanning. This API uses a promise to return the result. |
| [startScannerDiscovery](arkts-basicservices-scan-startscannerdiscovery-f.md) | Starts scanner discovery. This API uses a promise to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [addScanner](arkts-basicservices-scan-addscanner-f-sys.md) | Adds a scanner. This API uses a promise to return the result. |
| [deleteScanner](arkts-basicservices-scan-deletescanner-f-sys.md) | Deletes a scanner. This API uses a promise to return the result. |
| [getAddedScanners](arkts-basicservices-scan-getaddedscanners-f-sys.md) | Obtains the added scanners. This API uses a promise to return the result. |
| [off](arkts-basicservices-scan-off-f-sys.md#offscandeviceadd) | Unregisters the callback used to listen for the scanner addition event. This API uses an asynchronous callback to return the result. |
| [off](arkts-basicservices-scan-off-f-sys.md#offscandevicedel) | Unregisters the callback used to listen for the scanner deletion event. This API uses an asynchronous callback to return the result. |
| [on](arkts-basicservices-scan-on-f-sys.md#onscandeviceadd) | Registers a callback used to listen for the scanner addition event. This API uses an asynchronous callback to return the result. |
| [on](arkts-basicservices-scan-on-f-sys.md#onscandevicedel) | Registers a callback used to listen for the scanner deletion event. This API uses an asynchronous callback to return the result. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [PictureScanProgress](arkts-basicservices-scan-picturescanprogress-i.md) | Defines the progress of scanning pictures. |
| [Range](arkts-basicservices-scan-range-i.md) | Defines the range. |
| [ScannerDevice](arkts-basicservices-scan-scannerdevice-i.md) | Defines the scanner. |
| [ScannerOptionValue](arkts-basicservices-scan-scanneroptionvalue-i.md) | Defines the scanner option value. |
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
| [ScannerSyncMode](arkts-basicservices-scan-scannersyncmode-e.md) | Enumerates the scanner sync codes. |
