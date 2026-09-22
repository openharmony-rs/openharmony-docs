# @ohos.app.ability.dialogRequest

The dialogRequest module provides APIs related to modal dialog box processing, including obtaining the request information (used to bind a modal dialog box) and request callback (used to set the request result).

A modal dialog box is a system-level dialog box that blocks interactions such as mouse clicks, keyboard input, and touch events on the underlying page. The page can only be interacted with after the modal dialog box is closed.

> **NOTE:** 
> 
> - The APIs provided by this module are used in ServiceExtensionAbilities. For a ServiceExtensionAbility that implements modal dialog boxes, you can use the APIs to obtain the request information and request callback and return the request result.

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { dialogRequest } from '@kit.AbilityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getRequestCallback](arkts-ability-dialogrequest-getrequestcallback-f.md) | Obtains the request callback from Want. |
| [getRequestInfo](arkts-ability-dialogrequest-getrequestinfo-f.md) |  |

### Interfaces

| Name | Description |
| --- | --- |
| [RequestCallback](arkts-ability-dialogrequest-requestcallback-i.md) | Provides a callback for setting the modal dialog box request result. |
| [RequestInfo](arkts-ability-dialogrequest-requestinfo-i.md) | Indicates the request information of the initiator, which is used as an input parameter for the window to bind a modal dialog box. |
| [RequestResult](arkts-ability-dialogrequest-requestresult-i.md) | Defines the result of the request for the modal dialog box. It contains **ResultCode** and **ResultWant**. |
| [WindowRect](arkts-ability-dialogrequest-windowrect-i.md) | Indicates the attributes of a modal dialog box. |

### Enums

| Name | Description |
| --- | --- |
| [ResultCode](arkts-ability-dialogrequest-resultcode-e.md) | Enumerates the result codes of the request for the modal dialog box. |
