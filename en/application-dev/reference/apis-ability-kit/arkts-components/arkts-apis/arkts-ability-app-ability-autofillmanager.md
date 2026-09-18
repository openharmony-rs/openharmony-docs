# @ohos.app.ability.autoFillManager

The autoFillManager module provides APIs for saving accounts and passwords.

Unlike the system's auto-save feature that triggers during page transitions, this feature requires manual activation by the user. For example, the user must input their account and password on a website and click the **Save** button to initiate the saving process.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## Modules to Import

```TypeScript
import { autoFillManager } from '@kit.AbilityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [requestAutoFill](arkts-ability-autofillmanager-requestautofill-f.md) | Trigger an auto fill request. |
| [requestAutoSave](arkts-ability-autofillmanager-requestautosave-f.md) | Requests to automatically save the widget data. This API uses an asynchronous callback to return the result. If the current widget does not support widget switching, you can call this API to save historical widget input data. The callback is triggered when the auto-save request is complete. |
| [requestAutoSave](arkts-ability-autofillmanager-requestautosave-f.md) | Trigger an auto save request. |

### Interfaces

| Name | Description |
| --- | --- |
| [AutoFillCallback](arkts-ability-autofillmanager-autofillcallback-i.md) | Auto fill callback. |
| [AutoSaveCallback](arkts-ability-autofillmanager-autosavecallback-i.md) | Implements callbacks triggered when auto-save is complete. |

### Types

| Name | Description |
| --- | --- |
| [AutoFillRect](arkts-ability-autofillmanager-autofillrect-t.md) | Defines the rectangle used for auto-fill. |
| [FillFailureResult](arkts-ability-autofillmanager-fillfailureresult-t.md) | The interface of filling failure result. |
| [FillRequest](arkts-ability-autofillmanager-fillrequest-t.md) | Defines the information about an auto-fill request. |
| [OnFillFailureFn](arkts-ability-autofillmanager-onfillfailurefn-t.md) | Called when auto fill request is failed to be handled. |
| [OnFillSuccessFn](arkts-ability-autofillmanager-onfillsuccessfn-t.md) | Called when auto fill request is successfully handled. |
| [PageNodeInfo](arkts-ability-autofillmanager-pagenodeinfo-t.md) | Defines the page node information used for auto-fill. |
| [SaveRequest](arkts-ability-autofillmanager-saverequest-t.md) | Defines the information about an auto-save request. |
| [ViewData](arkts-ability-autofillmanager-viewdata-t.md) | Defines the view data used for auto-fill. |

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [AutoFillPopupConfig](arkts-ability-autofillmanager-autofillpopupconfig-t-sys.md) | Defines the size and position information of an auto-fill pop-up. |
| [CustomData](arkts-ability-autofillmanager-customdata-t-sys.md) | Defines the custom data. |
| [FillRequestCallback](arkts-ability-autofillmanager-fillrequestcallback-t-sys.md) | Defines the callback for an auto-fill request, which is used to automatically fill in or generate a password. The callback can be used to notify the client of the success or failure of the request. |
| [FillResponse](arkts-ability-autofillmanager-fillresponse-t-sys.md) | Defines the information about the response to an auto-fill request. |
| [PopupSize](arkts-ability-autofillmanager-popupsize-t-sys.md) | Defines the width and height of an auto-fill pop-up. |
| [SaveRequestCallback](arkts-ability-autofillmanager-saverequestcallback-t-sys.md) | Defines the callback for an automatic or a manual saving request. |
| [UpdateRequest](arkts-ability-autofillmanager-updaterequest-t-sys.md) | Defines the information about an auto-update request. |
<!--DelEnd-->
