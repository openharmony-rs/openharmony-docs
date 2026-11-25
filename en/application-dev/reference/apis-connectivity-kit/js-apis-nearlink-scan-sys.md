# @ohos.nearlink.scan (NearLink Scanning Capability) (System API)
<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @CCCZKing-->
<!--Designer: @lilong32; @CCCZKing-->
<!--Tester: @zhangjiaji111-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=dd305c3d6ada98668c2c88e9eede4ef19139d4fc translatedAt=2026-11-23T02:29:04.637Z pushedAt=2026-11-24T11:58:19.030Z nl=1 -->


This module provides the definition of the NearLink scanning mode.


**Since**: 26.0.0

> **NOTE**
>
> This page contains only the system APIs of this module. For details about other public APIs, see [@ohos.nearlink.scan (NearLink Scanning Capability)](js-apis-nearlink-scan.md).

## Modules to Import

```typescript
import { scan } from '@kit.ConnectivityKit';
```

## ScanMode

Enumerates the scan modes.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

| Name | Value | Description |
| -------- | -------- | -------- |
| SCAN_MODE_LOW_LATENCY | 2 | High-power scan mode. The scan frequency is high, and the power consumption is high. |
