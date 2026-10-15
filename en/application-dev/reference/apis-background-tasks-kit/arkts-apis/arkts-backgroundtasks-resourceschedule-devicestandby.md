# @ohos.resourceschedule.deviceStandby(Device Standby)

Provides methods for managing device standby, including the methods for querying standby status and exemption list.

@namespace deviceStandby

**Since:** 10

<!--Device-unnamed-declare namespace deviceStandby--><!--Device-unnamed-declare namespace deviceStandby-End-->

**System capability:** SystemCapability.ResourceSchedule.DeviceStandby

## Modules to Import

```TypeScript
import { deviceStandby } from '@kit.BackgroundTasksKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getExemptedApps](arkts-backgroundtasks-devicestandby-getexemptedapps-f-sys.md#getexemptedapps1) | Returns the information about the specified exempted application. |
| [getExemptedApps](arkts-backgroundtasks-devicestandby-getexemptedapps-f-sys.md#getexemptedapps2) | Returns the information about the specified exempted application. |
| [releaseExemptionResource](arkts-backgroundtasks-devicestandby-releaseexemptionresource-f-sys.md#releaseexemptionresource) | Releases exemption resources. |
| [requestExemptionResource](arkts-backgroundtasks-devicestandby-requestexemptionresource-f-sys.md#requestexemptionresource) | Requests exemption resources. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [ExemptedAppInfo](arkts-backgroundtasks-devicestandby-exemptedappinfo-i-sys.md) | Information about an exempted application. |
| [ResourceRequest](arkts-backgroundtasks-devicestandby-resourcerequest-i-sys.md) | The request of standby resources. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [ResourceType](arkts-backgroundtasks-devicestandby-resourcetype-e-sys.md) | The type of exemption resources requested by the application. |
<!--DelEnd-->
