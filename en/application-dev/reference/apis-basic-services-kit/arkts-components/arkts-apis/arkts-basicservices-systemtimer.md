# @ohos.systemTimer(System Timer)

The **systemTimer** module provides system timer features. You can use the APIs of this module to implement the alarm clock and other timer services.

**Since:** 7

**System capability:** SystemCapability.MiscServices.Time

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { systemTimer } from '@kit.BasicServicesKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [createTimer](arkts-basicservices-systemtimer-createtimer-f-sys.md) | Creates a timer. This API uses an asynchronous callback to return the result. |
| [createTimer](arkts-basicservices-systemtimer-createtimer-f-sys.md) | Creates a timer. This API uses a promise to return the timer ID. |
| [destroyTimer](arkts-basicservices-systemtimer-destroytimer-f-sys.md) | Destroys a timer. This API uses an asynchronous callback to return the result. |
| [destroyTimer](arkts-basicservices-systemtimer-destroytimer-f-sys.md) | Destroys a timer. This API uses a promise to return the result. |
| [startTimer](arkts-basicservices-systemtimer-starttimer-f-sys.md) | Starts a timer. This API uses an asynchronous callback to return the result. |
| [startTimer](arkts-basicservices-systemtimer-starttimer-f-sys.md) | Starts a timer. This API uses a promise to return the result. |
| [stopTimer](arkts-basicservices-systemtimer-stoptimer-f-sys.md) | Stops the timer. This API uses an asynchronous callback to return the result. |
| [stopTimer](arkts-basicservices-systemtimer-stoptimer-f-sys.md) | Stops a timer. This API uses a promise to return the result. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [TimerOptions](arkts-basicservices-systemtimer-timeroptions-i-sys.md) | Defines the initialization options for the system timer. |
<!--DelEnd-->

<!--Del-->
### Constants(System API)

| Name | Description |
| --- | --- |
| [TIMER_TYPE_EXACT](arkts-basicservices-systemtimer-con-sys.md#timer_type_exact) | Exact type. (If the system time is changed, the offset may be 1s at most.) |
| [TIMER_TYPE_IDLE](arkts-basicservices-systemtimer-con-sys.md#timer_type_idle) | Idle timer type (supported only for system services). |
| [TIMER_TYPE_REALTIME](arkts-basicservices-systemtimer-con-sys.md#timer_type_realtime) | CPU time type. (The start time of the timer cannot be later than the current system time.) |
| [TIMER_TYPE_WAKEUP](arkts-basicservices-systemtimer-con-sys.md#timer_type_wakeup) | Wakeup type. (If the wakeup type is not set, the system does not wake up until it exits the sleep state.) |
<!--DelEnd-->
