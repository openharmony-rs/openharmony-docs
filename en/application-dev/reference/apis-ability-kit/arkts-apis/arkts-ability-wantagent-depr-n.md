# wantAgent(WantAgent Module)

```TypeScript
declare namespace wantAgent
```

The WantAgent module provides APIs for creating and comparing WantAgent objects, and obtaining the user ID and bundle name of a WantAgent object.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [wantAgent/wantAgent](arkts-ability-wantagent-n.md)

<!--Device-unnamed-declare namespace wantAgent--><!--Device-unnamed-declare namespace wantAgent-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [cancel](arkts-ability-wantagent-cancel-depr-f.md#cancel1) | Cancels a WantAgent object. This API uses an asynchronous callback to return the result. |
| [cancel](arkts-ability-wantagent-cancel-depr-f.md#cancel2) | Cancels a WantAgent object. This API uses a promise to return the result. |
| [equal](arkts-ability-wantagent-equal-depr-f.md#equal1) | Checks whether two WantAgent objects are equal to determine whether the same operation is from the same application. This API uses an asynchronous callback to return the result. |
| [equal](arkts-ability-wantagent-equal-depr-f.md#equal2) | Checks whether two WantAgent objects are equal to determine whether the same operation is from the same application. This API uses a promise to return the result. |
| [getBundleName](arkts-ability-wantagent-getbundlename-depr-f.md#getbundlename1) | Obtains the bundle name of a WantAgent. |
| [getBundleName](arkts-ability-wantagent-getbundlename-depr-f.md#getbundlename2) | Obtains the bundle name of a WantAgent. |
| [getUid](arkts-ability-wantagent-getuid-depr-f.md#getuid1) | Obtains the user ID of a WantAgent object. This API uses an asynchronous callback to return the result. |
| [getUid](arkts-ability-wantagent-getuid-depr-f.md#getuid2) | Obtains the user ID of a WantAgent object. This API uses a promise to return the result. |
| [getWantAgent](arkts-ability-wantagent-getwantagent-depr-f.md#getwantagent1) | Creates a WantAgent object. If the creation fails, a null WantAgent object is returned. This API uses an asynchronous callback to return the result. |
| [getWantAgent](arkts-ability-wantagent-getwantagent-depr-f.md#getwantagent2) | Creates a WantAgent object. If the creation fails, a null WantAgent object is returned. This API uses a promise to return the result. |
| [trigger](arkts-ability-wantagent-trigger-depr-f.md#trigger) | Triggers a WantAgent object. This API uses an asynchronous callback to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getWant](arkts-ability-wantagent-getwant-depr-f-sys.md#getwant1) | Obtains the Want in a WantAgent object. This API uses an asynchronous callback to return the result. |
| [getWant](arkts-ability-wantagent-getwant-depr-f-sys.md#getwant2) | Obtains the Want in a WantAgent object. This API uses a promise to return the result. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [CompleteData](arkts-ability-wantagent-completedata-depr-i.md) | Describes the data returned by after wantAgent.trigger is called. |

### Enums

| Name | Description |
| --- | --- |
| [OperationType](arkts-ability-wantagent-operationtype-depr-e.md) | Identifies the operation for using a WantAgent, such as starting an ability or sending a common event. |
| [WantAgentFlags](arkts-ability-wantagent-wantagentflags-depr-e.md) | Enumerates flags for using a WantAgent. |
