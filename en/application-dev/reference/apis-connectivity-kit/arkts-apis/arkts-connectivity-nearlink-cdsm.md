# @ohos.nearlink.cdsm(CDSM Capability)

This module provides the coordinated devices set management (CDSM) capability for NearLink, including querying and subscribing to the coordinated devices set information of NearLink.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

## Modules to Import

```TypeScript
import { cdsm } from '@kit.ConnectivityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createCdsmClient](arkts-connectivity-cdsm-createcdsmclient-f.md) | Creates a CDSM client instance. |

### Interfaces

| Name | Description |
| --- | --- |
| [CdsmClient](arkts-connectivity-cdsm-cdsmclient-i.md) | Defines a CDSM client class, which provides APIs for obtaining the CDSM information of a remote device. |
| [CdsmInfo](arkts-connectivity-cdsm-cdsminfo-i.md) | Represents the CDSM information. |
| [CdsmMemberInfo](arkts-connectivity-cdsm-cdsmmemberinfo-i.md) | Represents the information about member devices in the coordinated devices set. |

### Enums

| Name | Description |
| --- | --- |
| [CdsmConnectionState](arkts-connectivity-cdsm-cdsmconnectionstate-e.md) | Enumerates the connection states of member devices in a coordinated device set. |
