# ScanErrorCode

```TypeScript
enum ScanErrorCode
```

Enumerates the scan error codes.

**Since:** 20

<!--Device-scan-enum ScanErrorCode--><!--Device-scan-enum ScanErrorCode-End-->

**System capability:** SystemCapability.Print.PrintFramework

## SCAN_ERROR_CANCELED

```TypeScript
SCAN_ERROR_CANCELED = 13100005
```

Operation canceled. Check whether **cancelScan** is called or the operation is interrupted by the system.

**Since:** 20

<!--Device-ScanErrorCode-SCAN_ERROR_CANCELED = 13100005--><!--Device-ScanErrorCode-SCAN_ERROR_CANCELED = 13100005-End-->

**System capability:** SystemCapability.Print.PrintFramework

## SCAN_ERROR_COVER_OPEN

```TypeScript
SCAN_ERROR_COVER_OPEN = 13100010
```

The scanner cover is open. Close the cover and try again.

**Since:** 20

<!--Device-ScanErrorCode-SCAN_ERROR_COVER_OPEN = 13100010--><!--Device-ScanErrorCode-SCAN_ERROR_COVER_OPEN = 13100010-End-->

**System capability:** SystemCapability.Print.PrintFramework

## SCAN_ERROR_DEVICE_BUSY

```TypeScript
SCAN_ERROR_DEVICE_BUSY = 13100006
```

The device is busy. Wait until the device is idle and try again.

**Since:** 20

<!--Device-ScanErrorCode-SCAN_ERROR_DEVICE_BUSY = 13100006--><!--Device-ScanErrorCode-SCAN_ERROR_DEVICE_BUSY = 13100006-End-->

**System capability:** SystemCapability.Print.PrintFramework

## SCAN_ERROR_GENERIC_FAILURE

```TypeScript
SCAN_ERROR_GENERIC_FAILURE = 13100001
```

General failure. Check the running status of the scan service and try again.

**Since:** 20

<!--Device-ScanErrorCode-SCAN_ERROR_GENERIC_FAILURE = 13100001--><!--Device-ScanErrorCode-SCAN_ERROR_GENERIC_FAILURE = 13100001-End-->

**System capability:** SystemCapability.Print.PrintFramework

## SCAN_ERROR_INVALID

```TypeScript
SCAN_ERROR_INVALID = 13100007
```

Invalid operation. Check whether the current operation is valid in the scanner state.

**Since:** 20

<!--Device-ScanErrorCode-SCAN_ERROR_INVALID = 13100007--><!--Device-ScanErrorCode-SCAN_ERROR_INVALID = 13100007-End-->

**System capability:** SystemCapability.Print.PrintFramework

## SCAN_ERROR_INVALID_PARAMETER

```TypeScript
SCAN_ERROR_INVALID_PARAMETER = 401
```

Invalid parameter. Check the parameter type and value range.

**Since:** 20

<!--Device-ScanErrorCode-SCAN_ERROR_INVALID_PARAMETER = 401--><!--Device-ScanErrorCode-SCAN_ERROR_INVALID_PARAMETER = 401-End-->

**System capability:** SystemCapability.Print.PrintFramework

## SCAN_ERROR_IO_ERROR

```TypeScript
SCAN_ERROR_IO_ERROR = 13100011
```

I/O error. Check the device I/O connection and try again.

**Since:** 20

<!--Device-ScanErrorCode-SCAN_ERROR_IO_ERROR = 13100011--><!--Device-ScanErrorCode-SCAN_ERROR_IO_ERROR = 13100011-End-->

**System capability:** SystemCapability.Print.PrintFramework

## SCAN_ERROR_JAMMED

```TypeScript
SCAN_ERROR_JAMMED = 13100008
```

Paper jammed. Remove the jammed paper from the scanner and try again.

**Since:** 20

<!--Device-ScanErrorCode-SCAN_ERROR_JAMMED = 13100008--><!--Device-ScanErrorCode-SCAN_ERROR_JAMMED = 13100008-End-->

**System capability:** SystemCapability.Print.PrintFramework

## SCAN_ERROR_NO_DOCS

```TypeScript
SCAN_ERROR_NO_DOCS = 13100009
```

No paper. Place paper in the scanner and try again.

**Since:** 20

<!--Device-ScanErrorCode-SCAN_ERROR_NO_DOCS = 13100009--><!--Device-ScanErrorCode-SCAN_ERROR_NO_DOCS = 13100009-End-->

**System capability:** SystemCapability.Print.PrintFramework

## SCAN_ERROR_NO_MEMORY

```TypeScript
SCAN_ERROR_NO_MEMORY = 13100012
```

Insufficient memory. Release system memory and try again.

**Since:** 20

<!--Device-ScanErrorCode-SCAN_ERROR_NO_MEMORY = 13100012--><!--Device-ScanErrorCode-SCAN_ERROR_NO_MEMORY = 13100012-End-->

**System capability:** SystemCapability.Print.PrintFramework

## SCAN_ERROR_NO_PERMISSION

```TypeScript
SCAN_ERROR_NO_PERMISSION = 201
```

No permission. Request the required permission based on the permission requirements of the corresponding API and declare the permission in the configuration file.

**Since:** 20

<!--Device-ScanErrorCode-SCAN_ERROR_NO_PERMISSION = 201--><!--Device-ScanErrorCode-SCAN_ERROR_NO_PERMISSION = 201-End-->

**System capability:** SystemCapability.Print.PrintFramework

## SCAN_ERROR_NOT_SYSTEM_APPLICATION

```TypeScript
SCAN_ERROR_NOT_SYSTEM_APPLICATION = 202
```

Not a system app. Check whether the app is a system app.

**Since:** 20

<!--Device-ScanErrorCode-SCAN_ERROR_NOT_SYSTEM_APPLICATION = 202--><!--Device-ScanErrorCode-SCAN_ERROR_NOT_SYSTEM_APPLICATION = 202-End-->

**System capability:** SystemCapability.Print.PrintFramework

## SCAN_ERROR_RPC_FAILURE

```TypeScript
SCAN_ERROR_RPC_FAILURE = 13100002
```

RPC failure. Check the RPC communication status and try again.

**Since:** 20

<!--Device-ScanErrorCode-SCAN_ERROR_RPC_FAILURE = 13100002--><!--Device-ScanErrorCode-SCAN_ERROR_RPC_FAILURE = 13100002-End-->

**System capability:** SystemCapability.Print.PrintFramework

## SCAN_ERROR_SERVER_FAILURE

```TypeScript
SCAN_ERROR_SERVER_FAILURE = 13100003
```

Service failure. Check whether the scan service is running properly and try again.

**Since:** 20

<!--Device-ScanErrorCode-SCAN_ERROR_SERVER_FAILURE = 13100003--><!--Device-ScanErrorCode-SCAN_ERROR_SERVER_FAILURE = 13100003-End-->

**System capability:** SystemCapability.Print.PrintFramework

## SCAN_ERROR_UNSUPPORTED

```TypeScript
SCAN_ERROR_UNSUPPORTED = 13100004
```

The operation is not supported. Check whether the current operation is supported by the scanner.

**Since:** 20

<!--Device-ScanErrorCode-SCAN_ERROR_UNSUPPORTED = 13100004--><!--Device-ScanErrorCode-SCAN_ERROR_UNSUPPORTED = 13100004-End-->

**System capability:** SystemCapability.Print.PrintFramework
