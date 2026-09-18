# @ohos.distributedHardware.hardwareManager(Distributed Hardware Manager)

The **hardwareManager** module provides the capability of controlling distributed hardware, including pausing, resuming, and stopping the distributed hardware service on the controlled device.

> **NOTE:** 

> The APIs provided by this module are system APIs.

@namespace hardwareManager

**Since:** 11

**System capability:** SystemCapability.DistributedHardware.DistributedHardwareFWK

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { hardwareManager } from '@kit.DistributedServiceKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [pauseDistributedHardware](arkts-distributedservice-hardwaremanager-pausedistributedhardware-f-sys.md) | Pauses the distributed hardware service on the controlled device. This API uses a promise to return the result. |
| [resumeDistributedHardware](arkts-distributedservice-hardwaremanager-resumedistributedhardware-f-sys.md) | Resumes the distributed hardware service on the controlled device. This API uses a promise to return the result. |
| [stopDistributedHardware](arkts-distributedservice-hardwaremanager-stopdistributedhardware-f-sys.md) | Stops the distributed hardware service on the controlled device. This API uses a promise to return the result. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [HardwareDescriptor](arkts-distributedservice-hardwaremanager-hardwaredescriptor-i-sys.md) | Represents the distributed hardware information. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [DistributedHardwareErrorCode](arkts-distributedservice-hardwaremanager-distributedhardwareerrorcode-e-sys.md) | Enumerates the error codes used for the distributed hardware. |
| [DistributedHardwareType](arkts-distributedservice-hardwaremanager-distributedhardwaretype-e-sys.md) | Enumerates the types of the distributed hardware. |
<!--DelEnd-->
