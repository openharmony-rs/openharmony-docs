# @ohos.app.ability.autoFillManager (autoFillManager) (System API)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @hanchen45-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=1e2bfcc9b4f85d9126c23f626a7a73b4bb891227 translatedAt=2026-09-03T10:01:30.542Z pushedAt=2026-09-05T10:47:30.239Z -->

The autoFillManager module provides features such as auto-fill and account/password saving.

Unlike the system's auto-save feature that triggers during page transitions, this feature requires manual activation by the user. For example, the user must input their account and password on a website and click the **Save** button to initiate the saving process.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> This page contains only the system APIs of this module. For details about other public APIs, see [@ohos.app.ability.autoFillManager (auto-fill framework)](js-apis-app-ability-autoFillManager.md).

## Modules to Import

```ts
import { autoFillManager } from '@kit.AbilityKit';
```

## UpdateRequest<sup>12+</sup>

type UpdateRequest = _AutoFillRequest.UpdateRequest

Defines the information about an auto-update request.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction**: This API can be used only in the stage model.

| Type| Description|
| --- | --- |
| [_AutoFillRequest.UpdateRequest](js-apis-inner-application-autoFillRequest-sys.md#updaterequest12) | Represents the update information for auto-fill, used to pass the auto-fill data content to be updated. |

## FillResponse

type FillResponse = _AutoFillRequest.FillResponse

Defines the information about the response to an auto-fill request.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction**: This API can be used only in the stage model.

| Type| Description|
| --- | --- |
| [_AutoFillRequest.FillResponse](js-apis-inner-application-autoFillRequest-sys.md#fillresponse) | Information about the response to an auto-fill request.|

## FillRequestCallback

type FillRequestCallback = _AutoFillRequest.FillRequestCallback

Callback object used for auto-fill or password generation, which notifies the client of success or failure.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction**: This API can be used only in the stage model.

| Type| Description|
| --- | --- |
| [_AutoFillRequest.FillRequestCallback](js-apis-inner-application-autoFillRequest-sys.md#fillrequestcallback) | Callback for an auto-fill request, which is used to automatically fill in or generate a password. The callback can be used to notify the client of the success or failure of the request.|

## SaveRequestCallback

type SaveRequestCallback = _AutoFillRequest.SaveRequestCallback

Callback object for an auto-save or manual save request. It is used to notify the application of the save result after the save operation is complete, including the status information indicating whether the save succeeded or failed.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction**: This API can be used only in the stage model.

| Type| Description|
| --- | --- |
| [_AutoFillRequest.SaveRequestCallback](js-apis-inner-application-autoFillRequest-sys.md#saverequestcallback) | Callback for an automatic or a manual saving request.|

## CustomData<sup>13+</sup>

type CustomData = _CustomData.default

Defines the custom data.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction**: This API can be used only in the stage model.

| Type| Description|
| --- | --- |
| [_CustomData](js-apis-inner-application-customData-sys.md#customdata).default | Custom data. |

## AutoFillPopupConfig<sup>12+</sup>

type AutoFillPopupConfig = _AutoFillPopupConfig.default

Defines the size and position information of an auto-fill pop-up.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction**: This API can be used only in the stage model.

| Type| Description|
| --- | --- |
| [_AutoFillPopupConfig](js-apis-inner-application-autoFillPopupConfig-sys.md#autofillpopupconfig).default | Represents the size and position information of the auto-fill popup. |

## PopupSize<sup>12+</sup>

type PopupSize = _AutoFillPopupConfig.PopupSize

Defines the width and height of an auto-fill pop-up.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction**: This API can be used only in the stage model.

| Type| Description|
| --- | --- |
| [_AutoFillPopupConfig.PopupSize](js-apis-inner-application-autoFillPopupConfig-sys.md#popupsize) | Width and height of the auto-fill pop-up.|
