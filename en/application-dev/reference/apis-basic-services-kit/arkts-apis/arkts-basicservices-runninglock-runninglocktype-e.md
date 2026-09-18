# RunningLockType

Enumerates the types of **RunningLock** objects.

**Since:** 7

**System capability:** SystemCapability.PowerManager.PowerManager.Core

## BACKGROUND

```TypeScript
BACKGROUND = 1
```

A lock that prevents the system from entering sleep mode when the screen is off.

**NOTE:** 

This parameter is supported since API version 7 and deprecated since API version 10.

**Since:** 7

**Deprecated since:** 10

**System capability:** SystemCapability.PowerManager.PowerManager.Core

## PROXIMITY_SCREEN_CONTROL

```TypeScript
PROXIMITY_SCREEN_CONTROL = 2
```

A lock that enables the proximity sensor and turns on or off the screen based on the distance between the sensor and the obstacle.

**Since:** 7

**System capability:** SystemCapability.PowerManager.PowerManager.Core

## BACKGROUND_USER_IDLE

```TypeScript
BACKGROUND_USER_IDLE = 129
```

A background lock that prevents the system from automatically entering sleep mode when the user is inactive for a period of time. Note: This lock cannot prevent the system from entering the forced sleep state in scenarios such as closing the PC lid. The user must listen for the [COMMON_EVENT_ENTER_FORCE_SLEEP](../../../reference/apis-basic-services-kit/common_event/commonEventManager-definitions.md#common_event_enter_force_sleep12) event and release this lock after receiving the event. The behavior of this lock varies with devices. For details about how to use this type of lock, see [Preventing the Idle System from Entering Sleep Mode](../../../basic-services/powermgr/runningLock/runningLock-dev.md).

**Since:** 23

**System capability:** SystemCapability.PowerManager.PowerManager.Core
