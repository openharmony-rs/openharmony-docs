# ScannerSyncDevice

Defines the device to be synced from the scanner.

**Since:** 20

**System capability:** SystemCapability.Print.PrintFramework

## Modules to Import

```TypeScript
import { scan } from '@kit.BasicServicesKit';
```

## discoveryMode

```TypeScript
discoveryMode: ScannerDiscoveryMode
```

Discovery mode.

**Type:** [ScannerDiscoveryMode](arkts-basicservices-scan-scannerdiscoverymode-e.md)

**Since:** 20

**System capability:** SystemCapability.Print.PrintFramework

## oldScannerId

```TypeScript
oldScannerId?: string
```

Old scanner ID, which is valid only when **syncMode** is set to **update**.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.Print.PrintFramework

## scannerId

```TypeScript
scannerId: string
```

Scanner ID.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.Print.PrintFramework

## syncMode

```TypeScript
syncMode: ScannerSyncMode
```

Sync mode.

**Type:** [ScannerSyncMode](arkts-basicservices-scan-scannersyncmode-e.md)

**Since:** 20

**System capability:** SystemCapability.Print.PrintFramework

## uniqueId

```TypeScript
uniqueId: string
```

Unique ID.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.Print.PrintFramework
