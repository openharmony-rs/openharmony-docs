# @ohos.runningLock(RunningLock)

The **runningLock** module provides APIs for creating, querying, holding, and releasing running locks. A running lock enables the proximity sensor to turn on or off the screen, or prevents the device from entering sleep mode when the screen is off. For details about the running lock types, see [RunningLockType](arkts-basicservices-runninglock-runninglocktype-e.md).

**Since:** 7

**System capability:** SystemCapability.PowerManager.PowerManager.Core

## Modules to Import

```TypeScript
import { runningLock } from '@kit.BasicServicesKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [create](arkts-basicservices-runninglock-create-f.md) | Creates a [RunningLock](arkts-basicservices-runninglock-runninglock-c.md) object. This API uses an asynchronous callback to return the result. |
| [create](arkts-basicservices-runninglock-create-f.md) | Creates a [RunningLock](arkts-basicservices-runninglock-runninglock-c.md) object. This API uses a promise to return the result. |
| [createRunningLock](arkts-basicservices-runninglock-createrunninglock-f.md) | Creates a [RunningLock](arkts-basicservices-runninglock-runninglock-c.md) object. This API uses an asynchronous callback to return the result. |
| [createRunningLock](arkts-basicservices-runninglock-createrunninglock-f.md) | Creates a [RunningLock](arkts-basicservices-runninglock-runninglock-c.md) object. This API uses a promise to return the result. |
| [isRunningLockTypeSupported](arkts-basicservices-runninglock-isrunninglocktypesupported-f.md) | Checks whether a specified type of [RunningLock](arkts-basicservices-runninglock-runninglock-c.md) is supported. This API uses an asynchronous callback to return the result. |
| [isRunningLockTypeSupported](arkts-basicservices-runninglock-isrunninglocktypesupported-f.md) | Checks whether a specified type of [RunningLock](arkts-basicservices-runninglock-runninglock-c.md) is supported. This API uses a promise to return the result. |
| [isSupported](arkts-basicservices-runninglock-issupported-f.md) | Checks whether a specified type of [RunningLock](arkts-basicservices-runninglock-runninglock-c.md) is supported. |

### Classes

| Name | Description |
| --- | --- |
| [RunningLock](arkts-basicservices-runninglock-runninglock-c.md) | Defines a **RunningLock** object. |

### Enums

| Name | Description |
| --- | --- |
| [RunningLockType](arkts-basicservices-runninglock-runninglocktype-e.md) | Enumerates the types of **RunningLock** objects. |
