# @ohos.boardInfo

The **boardInfo** module provides board-level hardware information query, including CPU, board, and BIOS information. It is applicable to scenarios such as device identification, asset management, and compatibility check. This information cannot be configured by developers.

> **NOTE:** 
> 
> The initial APIs of this module are supported since API version 26.0.1. Newly added APIs
> will be marked with a superscript to indicate their earliest API version.
> The APIs of this module will start a temporary process during execution. When the system
> load is high, blocking risks may occur. To ensure the responsiveness of the application
> main thread, avoid calling these APIs in the main thread. Hardware information is
> device-specific and fixed. You can cache it locally after the first retrieval to avoid
> repeated calls and improve performance.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-unnamed-declare namespace boardInfo--><!--Device-unnamed-declare namespace boardInfo-End-->

**System capability:** SystemCapability.Startup.BoardInfo

## Modules to Import

```TypeScript
import { boardInfo } from '@kit.BasicServicesKit';
```

## Summary

### Constants

| Name | Description |
| --- | --- |
| [biosDate](arkts-basicservices-boardinfo-con.md#biosdate) | BIOS release date. |
| [biosVendor](arkts-basicservices-boardinfo-con.md#biosvendor) | BIOS vendor. |
| [biosVersion](arkts-basicservices-boardinfo-con.md#biosversion) | BIOS version. |
| [boardName](arkts-basicservices-boardinfo-con.md#boardname) | Board product name. |
| [boardSn](arkts-basicservices-boardinfo-con.md#boardsn) | Board serial number. |
| [boardVendor](arkts-basicservices-boardinfo-con.md#boardvendor) | board vendor. |
| [cpuArch](arkts-basicservices-boardinfo-con.md#cpuarch) | CPU architecture. |
| [cpuId](arkts-basicservices-boardinfo-con.md#cpuid) | CPU ID. |
| [cpuVendor](arkts-basicservices-boardinfo-con.md#cpuvendor) | CPU vendor information. |
