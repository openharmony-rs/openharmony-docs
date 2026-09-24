# wantAgent(WantAgent Module)

```TypeScript
declare namespace wantAgent
```

The WantAgent module encapsulates a [Want](arkts-ability-app-ability-want-want-c.md) object, enabling an application to trigger a WantAgent object to perform specified operations (such as starting an ability or publishing a common event) at a future time.

The module provides the APIs for creating a WantAgent object, obtaining the bundle name and UID of the application to which a WantAgent object belongs, proactively triggering a WantAgent object, and checking whether two WantAgent objects are the same. A typical use scenario of WantAgent is notification processing. For example, when a user touches a notification, the [trigger](arkts-ability-wantagent-trigger-f.md) API of WantAgent is triggered and the target application is started. For details, see [Notification](../../../notification/notification-with-wantagent.md).

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { wantAgent, WantAgent } from '@kit.AbilityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getBundleName](arkts-ability-wantagent-getbundlename-f.md#getbundlename) | Obtains the bundle name of a WantAgent object. This API uses an asynchronous callback to return the result. |
| [getBundleName](arkts-ability-wantagent-getbundlename-f.md#getbundlename-1) | Obtains the bundle name of a WantAgent object. This API uses a promise to return the result. |
| [getUid](arkts-ability-wantagent-getuid-f.md#getuid) | Obtains the user ID of a WantAgent object. This API uses an asynchronous callback to return the result. |
| [getUid](arkts-ability-wantagent-getuid-f.md#getuid-1) | Obtains the user ID of a WantAgent object. This API uses a promise to return the result. |
| [cancel](arkts-ability-wantagent-cancel-f.md#cancel) | Cancels a WantAgent object. This API uses an asynchronous callback to return the result. |
| [cancel](arkts-ability-wantagent-cancel-f.md#cancel-1) | Cancels a WantAgent object. This API uses a promise to return the result. |
| [trigger](arkts-ability-wantagent-trigger-f.md) | Proactively triggers a WantAgent object. This API uses an asynchronous callback to return the result. |
| [equal](arkts-ability-wantagent-equal-f.md#equal) | Checks whether two WantAgent objects are equal, so as to determine whether the same operation is from the same application. This API uses an asynchronous callback to return the result. |
| [equal](arkts-ability-wantagent-equal-f.md#equal-1) | Checks whether two WantAgent objects are equal, so as to determine whether the same operation is from the same application. This API uses a promise to return the result. |
| [getWantAgent](arkts-ability-wantagent-getwantagent-f.md#getwantagent) | Obtains a WantAgent object. This API uses an asynchronous callback to return the result. If the creation fails, a null WantAgent object is returned. |
| [getWantAgent](arkts-ability-wantagent-getwantagent-f.md#getwantagent-1) | Obtains a WantAgent object. This API uses a promise to return the result. If the creation fails, a null WantAgent object is returned. |
| [getOperationType](arkts-ability-wantagent-getoperationtype-f.md#getoperationtype) | Obtains the operation type of a WantAgent object. This API uses an asynchronous callback to return the result. |
| [getOperationType](arkts-ability-wantagent-getoperationtype-f.md#getoperationtype-1) | Obtains the operation type of a WantAgent object. This API uses a promise to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getWant](arkts-ability-wantagent-getwant-f-sys.md#getwant) | Obtains the Want in a WantAgent object. This API uses an asynchronous callback to return the result. |
| [getWant](arkts-ability-wantagent-getwant-f-sys.md#getwant-1) | Obtains the Want in a WantAgent object. This API uses a promise to return the result. |
| [triggerAsync](arkts-ability-wantagent-triggerasync-f-sys.md) | Asynchronously triggers a predefined operation encration encapsulated in a Wantagent with specified trigger information. If the specified wantAgent is local, you need to apply for permission: ohos.permission.TRIGGER_LOCAL_WANTAGENT permission. |
| [setWantAgentMultithreading](arkts-ability-wantagent-setwantagentmultithreading-f-sys.md) | Enables or disables the WantAgent multithreading feature. |
| [createLocalWantAgent](arkts-ability-wantagent-createlocalwantagent-f-sys.md) | Create a local WantAgent object. The WantAgent created by this interface stores data on the client side and is not managed by the WantAgent servcer. If this WantAgent object is passed across processes, its contained data will be serialized and transmitted to the target process. |
| [isLocalWantAgent](arkts-ability-wantagent-islocalwantagent-f-sys.md) | Checks whether the specified WantAgent is local. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [CompleteData](arkts-ability-wantagent-completedata-i.md) | Describes the data returned by the operation of proactive triggering a WantAgent object. |

### Types

| Name | Description |
| --- | --- |
| [TriggerInfo](arkts-ability-wantagent-triggerinfo-t.md) | Defines the TriggerInfo object. |
| [WantAgentInfo](arkts-ability-wantagent-wantagentinfo-t.md) | Defines the WantAgentInfo object. |

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [LocalWantAgentInfo](arkts-ability-wantagent-localwantagentinfo-t-sys.md) | Provides the information required to create a local WantAgent. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [WantAgentFlags](arkts-ability-wantagent-wantagentflags-e.md) | Enumerates the flags used by the WantAgent objects. |
| [OperationType](arkts-ability-wantagent-operationtype-e.md) | Enumerates the operation types of the WantAgent objects. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [OperationType](arkts-ability-wantagent-operationtype-e-sys.md) | Enumerates the operation types of the WantAgent objects. |
<!--DelEnd-->
