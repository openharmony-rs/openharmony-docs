# wantAgent(WantAgent Module)

The WantAgent module provides APIs for creating and comparing WantAgent objects, and obtaining the user ID and bundle name of a WantAgent object.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [wantAgent/wantAgent](arkts-ability-wantagent-n.md)

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getBundleName](arkts-ability-wantagent-getbundlename-depr-f.md#getbundlename) | Obtains the bundle name of a WantAgent. |
| [getBundleName](arkts-ability-wantagent-getbundlename-depr-f.md#getbundlename) | Obtains the bundle name of a WantAgent. |
| [getUid](arkts-ability-wantagent-getuid-depr-f.md#getuid) | Obtains the UID of a WantAgent. |
| [getUid](arkts-ability-wantagent-getuid-depr-f.md#getuid) | Obtains the UID of a WantAgent. |
| [cancel](arkts-ability-wantagent-cancel-depr-f.md#cancel) | Cancel a WantAgent. Only the application that creates the WantAgent can cancel it. |
| [cancel](arkts-ability-wantagent-cancel-depr-f.md#cancel) | Cancel a WantAgent. Only the application that creates the WantAgent can cancel it. |
| [trigger](arkts-ability-wantagent-trigger-depr-f.md#trigger) | Triggers a WantAgent. |
| [equal](arkts-ability-wantagent-equal-depr-f.md#equal) | Checks whether two WantAgent objects are equal. |
| [equal](arkts-ability-wantagent-equal-depr-f.md#equal) | Checks whether two WantAgent objects are equal. |
| [getWantAgent](arkts-ability-wantagent-getwantagent-depr-f.md#getwantagent) | Obtains a WantAgent object. |
| [getWantAgent](arkts-ability-wantagent-getwantagent-depr-f.md#getwantagent) | Obtains a WantAgent object. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getWant](arkts-ability-wantagent-getwant-depr-f-sys.md#getwant) | Obtains the [Want](arkts-ability-app-ability-want-want-c.md) of an [WantAgent](arkts-ability-wantagent-depr-t.md#wantagent). |
| [getWant](arkts-ability-wantagent-getwant-depr-f-sys.md#getwant) | Obtains the [Want](arkts-ability-app-ability-want-want-c.md) of an [WantAgent](arkts-ability-wantagent-depr-t.md#wantagent). |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [CompleteData](arkts-ability-wantagent-completedata-depr-i.md) | Describes the data returned by after wantAgent.trigger is called. |

### Enums

| Name | Description |
| --- | --- |
| [WantAgentFlags](arkts-ability-wantagent-wantagentflags-depr-e.md) | Enumerates flags for using a WantAgent. |
| [OperationType](arkts-ability-wantagent-operationtype-depr-e.md) | Identifies the operation for using a WantAgent, such as starting an ability or sending a common event. |
