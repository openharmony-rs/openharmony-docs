# @ohos.app.ability.dialogRequest (dialogRequest Module)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zhu-feimo-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=1e2bfcc9b4f85d9126c23f626a7a73b4bb891227 translatedAt=2026-09-03T10:14:55.475Z pushedAt=2026-09-05T10:47:30.379Z -->

The dialogRequest module provides the capability of handling modal dialogs, including obtaining RequestInfo (used to bind a modal dialog) and obtaining RequestCallback (used to set the return result). It applies to scenarios where a system-level modal dialog needs to be displayed across applications and the interaction events of the page below the dialog need to be intercepted. The requesting application can securely launch the modal dialog of another application and receive the processing result.

A modal dialog is a system dialog that intercepts mouse, keyboard, touchscreen, and other events on the page below it. The page can be operated only after the dialog is destroyed.

> **NOTE**
>
>  - The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>  - The APIs of this module can be used in ServiceExtensionAbility. If a ServiceExtensionAbility implements a modal dialog, the APIs of this module can be used to obtain the RequestInfo and RequestCallback of the requester and return the request result.

## Modules to Import

```ts
import { dialogRequest } from '@kit.AbilityKit';
```

## dialogRequest.getRequestInfo

getRequestInfo(want: Want): RequestInfo

Obtains the RequestInfo of the requester from the Want.

> **NOTE**
>
> This API can be used in ServiceExtensionAbility. If ServiceExtensionAbility implements a modal dialog, the RequestInfo of the requester can be obtained from the Want. In other scenarios, no return value can be obtained by using this API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name | Type   | Mandatory | Description                        |
| ---- | ------ | ---- | --------------------------- |
| want  | [Want](js-apis-app-ability-want.md) | Yes   | Want information passed in when the requester requests a dialog box. |

**Return value**

| Type   | Description                     |
| ------ | ------------------------ |
| [RequestInfo](#requestinfo) | RequestInfo of the requester, used to bind a modal dialog. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { AbilityConstant, UIAbility, Want, dialogRequest } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      // Obtain the RequestInfo of the requester.
      let requestInfo = dialogRequest.getRequestInfo(want);
    } catch (err) {
      console.error(`Failed to getRequestInfo. Code: ${err.code}, message: ${err.message}`);
    }
  }
}
```

## dialogRequest.getRequestCallback

getRequestCallback(want: Want): RequestCallback

Obtains the RequestCallback of the requester from the Want.

> **NOTE**
>
> This API can be used in ServiceExtensionAbility. If ServiceExtensionAbility implements a modal dialog, the RequestCallback of the requester can be obtained from the Want. In other scenarios, no return value can be obtained by using this API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name | Type   | Mandatory | Description                        |
| ---- | ------ | ---- | --------------------------- |
| want  | [Want](js-apis-app-ability-want.md) | Yes   | Want information passed in when the requester requests a dialog box. |

**Return value**

| Type   | Description                     |
| ------ | ------------------------ |
| [RequestCallback](#requestcallback) | RequestCallback of the requester, used to set the return result. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { AbilityConstant, UIAbility, Want, dialogRequest } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      // Obtain the RequestCallback of the requester.
      let requestCallback = dialogRequest.getRequestCallback(want);
    } catch (err) {
      console.error(`Failed to getRequestCallback. Code: ${err.code}, message: ${err.message}`);
    }
  }
}
```

## WindowRect<sup>10+</sup>

Represents the properties of a modal dialog.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name | Type | Read-only | Optional | Description |
| ---- | ------ | ---- | ----| --------------------------- |
| left  | number | No  | No | X coordinate of the upper left corner of the modal dialog border. |
| top  | number | No   | No | Y coordinate of the upper left corner of the modal dialog border. |
| width  | number | No   | No | Width of the modal dialog, in px. |
| height  | number | No   | No | Height of the modal dialog, in px. |

## RequestInfo

Defines the request information of the initiator, which is used as an input parameter for binding a modal dialog box to a window.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name      | Type       | Read-only | Optional   | Description     |
| ------------ | --------| ------ | ----- | ----------------- |
| windowRect<sup>10+</sup>   | [WindowRect](#windowrect10)    | No | Yes  | Attributes of the modal dialog box. Pass this parameter when you need to customize the position and size of the modal dialog box; if not passed, the system default position and size are used.  |

**Example**

```ts
import { AbilityConstant, UIAbility, Want, dialogRequest } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      // Obtain the RequestInfo of the requester.
      let requestInfo = dialogRequest.getRequestInfo(want);
      console.info(`getRequestInfo windowRect=, ${JSON.stringify(requestInfo.windowRect)}` );
    } catch (err) {
      console.error(`Failed to getRequestInfo. Code: ${err.code}, message: ${err.message}`);
    }
  }
}
```

## ResultCode

Enumerates the result codes of a modal dialog request.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name      | Value          | Description     |
| ------------ | ------------------ | ---------------------- |
| RESULT_OK            | 0          | Success.          |
| RESULT_CANCEL        | 1          | Failure.          |

## RequestResult

Request result of a modal dialog, including the result code ResultCode and Want information.

### Properties

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| result | [ResultCode](#resultcode) | No | No | Result code of the request, used to determine whether the request is successful. |
| want<sup>10+</sup> | [Want](js-apis-app-ability-want.md)  | No | Yes | Want information, such as the ability name and bundle name. If this parameter is not passed, it is empty by default. |

## RequestCallback

Callback interface used to set the request result of a modal dialog.

**Model restriction:** This API can be used only in the stage model.

### RequestCallback.setRequestResult

setRequestResult(result: RequestResult): void

Sets the request result. After the user completes the modal dialog operation, this API returns the operation result (such as confirmation, cancellation, and user input data) to the requester through RequestCallback to complete the request response process.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| result | [RequestResult](#requestresult) | Yes | Request result information of the modal dialog. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { AbilityConstant, UIAbility, Want, dialogRequest } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      // Obtain the RequestCallback of the requester from Want.
      let requestCallback = dialogRequest.getRequestCallback(want);
      let myResult: dialogRequest.RequestResult = {
        result : dialogRequest.ResultCode.RESULT_CANCEL,
      };
      // Set the request result of the modal dialog.
      requestCallback.setRequestResult(myResult);
    } catch (err) {
      console.error(`Failed to setRequestResult. Code: ${err.code}, message: ${err.message}`);
    }
  }
}
```