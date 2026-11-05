# @ohos.runningLock(RunningLock)

The **runningLock** module provides APIs for creating, querying, holding, and releasing running locks. A running lock enables the proximity sensor to turn on or off the screen, or prevents the device from entering sleep mode when the screen is off. For details about the running lock types, see [RunningLockType](arkts-basicservices-runninglock-runninglocktype-e.md).

**Since:** 7

<!--Device-unnamed-declare namespace runningLock--><!--Device-unnamed-declare namespace runningLock-End-->

**System capability:** SystemCapability.PowerManager.PowerManager.Core

## Modules to Import

```TypeScript
import { runningLock } from '@kit.BasicServicesKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [create](arkts-basicservices-runninglock-create-f.md#create-1) | Creates a [RunningLock](arkts-basicservices-runninglock-runninglock-c.md) object. This API uses an asynchronous callback to return the result. After a lock object is created, you need to call the hold() method to lock and hold the lock to make the lock function take effect. You are not advised to invoke create concurrently in multiple Worker/TaskPools to create lock objects. |
| [create](arkts-basicservices-runninglock-create-f.md#create-2) | Creates a [RunningLock](arkts-basicservices-runninglock-runninglock-c.md) object. This API uses a promise to return the result. After a lock object is created, you need to call the hold() method to lock and hold the lock to make the lock function take effect. You are not advised to invoke create concurrently in multiple Worker/TaskPools to create lock objects. |
| [isSupported](arkts-basicservices-runninglock-issupported-f.md#issupported-1) | Checks whether a specified type of [RunningLock](arkts-basicservices-runninglock-runninglock-c.md) is supported. |
| [createRunningLock](arkts-basicservices-runninglock-createrunninglock-f.md#createrunninglock-1) | Creates a [RunningLock](arkts-basicservices-runninglock-runninglock-c.md) object. This API uses an asynchronous callback to return the result. |
| [createRunningLock](arkts-basicservices-runninglock-createrunninglock-f.md#createrunninglock-2) | Creates a [RunningLock](arkts-basicservices-runninglock-runninglock-c.md) object. This API uses a promise to return the result. |
| [isRunningLockTypeSupported](arkts-basicservices-runninglock-isrunninglocktypesupported-f.md#isrunninglocktypesupported-1) | Checks whether a specified type of [RunningLock](arkts-basicservices-runninglock-runninglock-c.md) is supported. This API uses an asynchronous callback to return the result. |
| [isRunningLockTypeSupported](arkts-basicservices-runninglock-isrunninglocktypesupported-f.md#isrunninglocktypesupported-2) | Checks whether a specified type of [RunningLock](arkts-basicservices-runninglock-runninglock-c.md) is supported. This API uses a promise to return the result. |

### Classes

| Name | Description |
| --- | --- |
| [RunningLock](arkts-basicservices-runninglock-runninglock-c.md) | The lock that prevents the system from sleeping or enanles the proximity sensor to control screen on/off. Different types of locks have diffrent functions. For details, see RunningLockType. This API must be used together with [create]{@liink runninglockcreate9} to create a lock, hold to hold the lock, and unhold to release the lock. For details, see the example. A RunningLock object cannot be shared among multiple Worker or TaskPool threads. The hold(), unhold(), and isHolding() methods of the same RunningLock instance must be called in the same thread. If the methods are called in different threads, the lock status may be inconsistent and no error will be reported. After the power service restarts unexpectedly, the craeted RunningLock object is still valid, but the service restart scenario and call the hold() method again if necessary. When the JS object of a RunningLock is garbage collected, the lock held by the underlying layer is automatically released. To hold the lock for a long time, keep the reference to the RunningLock object. |

### Enums

| Name | Description |
| --- | --- |
| [RunningLockType](arkts-basicservices-runninglock-runninglocktype-e.md) | Enumerates the types of **RunningLock** objects. |
