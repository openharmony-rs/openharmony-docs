# @ohos.resourceschedule.systemload(System Load Level Management)

The **systemload** module allows the system to determine the system load level based on the current temperature, load, and scenario, and notifies registered applications of level changes, if any.

**Since:** 12

**System capability:** SystemCapability.ResourceSchedule.SystemLoad

## Modules to Import

```TypeScript
import { systemLoad } from '@kit.BasicServicesKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getLevel](arkts-basicservices-systemload-getlevel-f.md) | Obtains the system load level. This API uses a promise to return the result. |
| [off](arkts-basicservices-systemload-off-f.md#offsystemloadchange) | Disables listening for system load level changes. This API uses an asynchronous callback to return the result. |
| [on](arkts-basicservices-systemload-on-f.md#onsystemloadchange) | Enables listening for system load level changes. This API uses an asynchronous callback to return the result. |

### Enums

| Name | Description |
| --- | --- |
| [SystemLoadLevel](arkts-basicservices-systemload-systemloadlevel-e.md) | Enumerates system load levels. |
