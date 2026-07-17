# ScannerSyncDevice

定义扫描仪同步设备的接口。

**起始版本：** 20

<!--Device-scan-interface ScannerSyncDevice--><!--Device-scan-interface ScannerSyncDevice-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## 导入模块

```TypeScript
import { scan } from '@kit.BasicServicesKit';
```

## discoveryMode

```TypeScript
discoveryMode: ScannerDiscoveryMode
```

发现模式。

**类型：** ScannerDiscoveryMode

**起始版本：** 20

<!--Device-ScannerSyncDevice-discoveryMode: ScannerDiscoveryMode--><!--Device-ScannerSyncDevice-discoveryMode: ScannerDiscoveryMode-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## oldScannerId

```TypeScript
oldScannerId?: string
```

旧的扫描仪ID，仅在syncMode为"update"时有效。

**类型：** string

**起始版本：** 20

<!--Device-ScannerSyncDevice-oldScannerId?: string--><!--Device-ScannerSyncDevice-oldScannerId?: string-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## scannerId

```TypeScript
scannerId: string
```

扫描仪ID。

**类型：** string

**起始版本：** 20

<!--Device-ScannerSyncDevice-scannerId: string--><!--Device-ScannerSyncDevice-scannerId: string-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## syncMode

```TypeScript
syncMode: ScannerSyncMode
```

同步模式。

**类型：** ScannerSyncMode

**起始版本：** 20

<!--Device-ScannerSyncDevice-syncMode: ScannerSyncMode--><!--Device-ScannerSyncDevice-syncMode: ScannerSyncMode-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## uniqueId

```TypeScript
uniqueId: string
```

唯一ID。

**类型：** string

**起始版本：** 20

<!--Device-ScannerSyncDevice-uniqueId: string--><!--Device-ScannerSyncDevice-uniqueId: string-End-->

**系统能力：** SystemCapability.Print.PrintFramework

