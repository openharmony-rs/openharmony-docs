# @ohos.nearlink.scan (NearLink Scanning Capability) (System API)
<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @CCCZKing-->
<!--Designer: @lilong32; @CCCZKing-->
<!--Tester: @zhangjiaji111-->
<!--Adviser: @zhang_yixin13-->


This module provides the definition of the NearLink scanning mode.


**Since:** 26.0.0

> **NOTE**
>
> The APIs provided by this module are system APIs.

## Modules to Import

```typescript
import { scan } from '@kit.ConnectivityKit';
```

## ScanMode

Enumerates the scan modes.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

| Name| Value| Description|
| -------- | -------- | -------- |
| SCAN_MODE_LOW_LATENCY | 2 | High-power scan mode. The scan frequency is high, and the power consumption is high.|
