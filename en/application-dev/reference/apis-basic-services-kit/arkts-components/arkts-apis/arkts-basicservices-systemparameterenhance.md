# @ohos.systemParameterEnhance(System Parameter)

System Parameter is a simple and easy-to-use key-value pair access interface provided for system services. Each system service can define system parameters to describe its status information, or change the behavior of the system service through system parameters. Its basic operation primitives are get and set. You can query the value of a system parameter through get, and modify the value of a system parameter through set. For details about the design principles and definitions of system parameters, see [System Parameter](../../../../device-dev/subsystems/subsys-boot-init-sysparam.md).

> **NOTE:** 
> 
> - The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The APIs of this module are system APIs.
> - Since system parameters are internal information and control parameters of each system service, each system parameter has its own DAC and MAC access control permissions. Third-party applications cannot use such APIs.

**Since:** 9

**System capability:** SystemCapability.Startup.SystemInfo

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { systemParameterEnhance } from '@kit.BasicServicesKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [get](arkts-basicservices-systemparameterenhance-get-f-sys.md#get) | Obtains a value of the specified key. This API uses an asynchronous callback to return the result. |
| [get](arkts-basicservices-systemparameterenhance-get-f-sys.md#get-1) | Obtains a value of the specified key. This API uses an asynchronous callback to return the result. |
| [get](arkts-basicservices-systemparameterenhance-get-f-sys.md#get-2) | Obtains a value of the specified key. This API uses a promise to return the result. |
| [getSync](arkts-basicservices-systemparameterenhance-getsync-f-sys.md) | Obtains the value of the specified system parameter key. |
| [set](arkts-basicservices-systemparameterenhance-set-f-sys.md#set) | Sets a value of the specified key. This API uses an asynchronous callback to return the result. |
| [set](arkts-basicservices-systemparameterenhance-set-f-sys.md#set-1) | Sets a value of the specified key. This API uses a promise to return the result. |
| [setSync](arkts-basicservices-systemparameterenhance-setsync-f-sys.md) | Sets a value for the specified key. |
<!--DelEnd-->
