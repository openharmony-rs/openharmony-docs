# @ohos.app.ability.autoFillManager (AutoFill Framework)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @hanchen45; @Luobniz21-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=9b45198dbdb6f53f8bf0896d62425626f2442690 translatedAt=2026-09-03T10:02:07.841Z pushedAt=2026-09-05T10:47:30.251Z -->

The autoFillManager module provides applications with the AutoFill capability for user information such as accounts, passwords, addresses, and phone numbers.

Unlike the system AutoSave feature triggered by page switching, this feature must be triggered manually by the user. For example, after a user enters an account and password on a website and taps the "Save" button, the corresponding AutoSave operation is triggered.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { autoFillManager } from '@kit.AbilityKit';
```

## OnFillSuccessFn

type OnFillSuccessFn = (viewData: ViewData) => void

Called when a fill request succeeds. The viewData returned by the callback contains the fill data provided by the system, based on which developers can apply the data to the form controls on the current page, for example, filling in the username and password on a login page, or the name and contact information in a shipping address form.

**Since:** 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name     | Type                                              | Mandatory | Description                     |
| -------- | ------------------------------------------------- | -------- | ------------------------------- |
| viewData | [ViewData](js-apis-inner-application-viewData.md) | Yes      | View data information for AutoFill. |

## OnFillFailureFn

type OnFillFailureFn = (result: FillFailureResult) => void

This callback is triggered when a fill request fails. The result returned by the callback contains the failure cause, based on which developers can perform error handling, for example, prompting the user that the fill failed and guiding manual input, or recording a failure log for troubleshooting.

**Since:** 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name | Type                                                                                | Mandatory | Description                   |
| ------ | ----------------------------------------------------------------------------------- | ---- | --------------------- |
| result | [FillFailureResult](js-apis-inner-application-autoFillRequest.md#fillfailureresult) | Yes  | AutoFill failure result. |

## AutoSaveCallback

Callback invoked when the save request is completed.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction:** This API can be used only in the stage model.

### onSuccess

onSuccess(): void

Called when the save request succeeds. Developers can perform subsequent processing at this point, for example, prompting the user that the save is successful or clearing the form.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction:** This API can be used only in the stage model.

**Example**

See [autoFillManager.requestAutoSave](#autofillmanagerrequestautosave).

### onFailure

onFailure(): void

Called when the save request fails. Developers can handle the failure at this point, for example, by prompting the user that the save failed and guiding them to retry.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction:** This API can be used only in the stage model.

**Example**

See [autoFillManager.requestAutoSave](#autofillmanagerrequestautosave).

## AutoFillCallback

Callback invoked when the fill request is completed.

**Since:** 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction:** This API can be used only in the stage model.

### onSuccess

onSuccess: OnFillSuccessFn

Called when a fill request succeeds. The returned viewData contains the data that can be used to fill the form, such as the username and password, shipping address, and so on.

**Since:** 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction:** This API can be used only in the stage model.

**Return value**

| Type                                | Description                            |
| ----------------------------------- | ------------------------------- |
| [OnFillSuccessFn](#onfillsuccessfn) | Callback invoked when a fill request succeeds. It receives the viewData parameter that contains the view data for filling. |

**Example**

See [autoFillManager.requestAutoFill](#autofillmanagerrequestautofill).

### onFailure

onFailure: OnFillFailureFn

Called when the fill request fails.

**Since:** 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction:** This API can be used only in the stage model.

**Return value**

| Type                                | Description                            |
| ----------------------------------- | ------------------------------- |
| [OnFillFailureFn](#onfillfailurefn) | Callback invoked after a fill request fails. It receives the result parameter that contains the failure reason. |

**Example**

See [autoFillManager.requestAutoFill](#autofillmanagerrequestautofill).

> **NOTE**
>
> In the example, the UiContext obtained from AppStorage is obtained in the OnWindowStageCreate lifecycle of EntryAbility (the ability that launches this page) in advance and stored in AppStorage. For details, see [requestAutoSave](#autofillmanagerrequestautosave).

## autoFillManager.requestAutoSave

requestAutoSave(context: UIContext, callback?: AutoSaveCallback): void

Requests to save form data. This API uses an asynchronous callback to return the result.

If the current form does not provide the form switching capability, you can use this API to save the historical form input data. The callback is triggered when the save request is complete.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| context | [UIContext](../apis-arkui/arkts-apis-uicontext-uicontext.md) | Yes | UI context in which the save operation is performed. |
| callback | [AutoSaveCallback](#autosavecallback)  | No | Callback invoked when the save request is complete, used to asynchronously receive the result of the save operation. If this parameter is not passed, the callback is not triggered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).
| ID | Error Message |
| ------- | -------------------------------- |
| 401      | The parameter check failed. Possible causes: 1. Get instance id failed; 2. Parse instance id failed; 3. The second parameter is not of type callback. |
| 16000050 | Internal error. |

**Example**

```ts
// EntryAbility.ets
import { UIAbility, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window, UIContext } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage): void {
    // Main window is created, set main page for this ability
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');
    // Create a local storage instance.
    let localStorageData: Record<string, string | common.UIAbilityContext> = {
      'message': "AutoFill Page",
      'context': this.context,
    };
    let storage = new LocalStorage(localStorageData);
    // Load the page content.
    windowStage.loadContent('pages/Index', storage, (err, data) => {
      if (err && err.code) {
        hilog.error(0x0000, 'testTag', 'Failed to load the content. Cause: %{public}s', JSON.stringify(err) ?? '');
        return;
      }
      // Obtain the main window.
      windowStage.getMainWindow((err: BusinessError, data: window.Window) => {
        if (err?.code) {
          console.error('Failed to obtain the main window. Cause: ' + JSON.stringify(err));
          return;
        }
        console.info('Succeeded in obtaining the main window. Data: ' + JSON.stringify(data));
        // Obtain the UIContext instance.
        let uiContext: UIContext = windowStage.getMainWindowSync().getUIContext();
        // Store the UIContext in AppStorage for access by other pages.
        AppStorage.setOrCreate("uiContext", uiContext);
      })
      hilog.info(0x0000, 'testTag', 'Succeeded in loading the content. Data: %{public}s', JSON.stringify(data) ?? '');
    });
  }
}
```

```ts
// Index.ets
import { autoFillManager } from '@kit.AbilityKit';
import { UIContext } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

let uiContext = AppStorage.get<UIContext>('uiContext');
// Define the AutoSave callback.
let callback: autoFillManager.AutoSaveCallback = {
  onSuccess: () => {
    console.info(`save request on success.`);
  },
  onFailure: () => {
    console.error(`save request on failure.`);
  }
};

@Entry
@Component
struct Index {
  @State userName: string = "";
  @State password: string = "";
  // Obtain the current UIContext instance.
  private uiContext: UIContext = this.getUIContext();
  build() {
    GridRow({ gutter: { y: 20 } }) {
      GridCol({ span: 20 }) {
        TextInput({ placeholder: 'Enter userName', text: this.userName })
          .type(InputType.USER_NAME)
          .width('90%')
          .onChange((value: string) => {
            this.userName = value
          })
      }
      GridCol({ span: 20 }) {
        TextInput({ placeholder: 'Enter password', text: this.password })
          .type(InputType.Password)
          .width('90%')
          .onChange((value: string) => {
            this.password = value
          })
      }
      GridCol({ span: 20 }) {
        Button('requestAutoSave')
          .onClick(() => {
            try {
              // Initiate the save request.
              autoFillManager.requestAutoSave(this.uiContext, callback);
            } catch (error) {
              console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
            }
          })
      }
    }
  }
}
```

## autoFillManager.requestAutoSave

requestAutoSave(context: UIContext, request: SaveRequest, callback?: AutoSaveCallback): void

Requests to save the form data. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name     | Type                                                                    | Mandatory | Description                            |
| -------- | ----------------------------------------------------------------------- | --------- | -------------------------------------- |
| context  | [UIContext](../apis-arkui/arkts-apis-uicontext-uicontext.md)            | Yes       | UI context in which the save operation is performed. |
| request  | [SaveRequest](js-apis-inner-application-autoFillRequest.md#saverequest) | Yes       | AutoSave request information, including the view data to be saved. |
| callback | [AutoSaveCallback](#autosavecallback)                                   | No        | Callback invoked when the save request is complete, used to asynchronously receive the result of the save operation. If this parameter is not passed, the callback is not triggered. |

**Error codes**

For details about the error codes, see [Ability Error Codes](errorcode-ability.md).
| ID | Error Message        |
| ---------| --------------- |
| 16000050 | Internal error. |

**Example**
```ts
// Index.ets
import { autoFillManager } from '@kit.AbilityKit';
import { UIContext } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

// Configure request based on the actual project.
let request: autoFillManager.SaveRequest = {
  viewData: {
    bundleName: "com.example.testBundleName",
    pageUrl: "testPageUrl",
    pageNodeInfos: [
      {
        id: 1,
        autoFillType: autoFillManager.AutoFillType.USER_NAME,
        value: "testValue1",
        placeholder: "testPlaceholder1",
        rect: {
          left: 1,
          top: 1,
          width: 1,
          height: 1,
        },
        isFocus: false
      },
      {
        id: 2,
        autoFillType: autoFillManager.AutoFillType.PASSWORD,
        value: "testValue2",
        placeholder: "testPlaceholder2",
        rect: {
          left: 1,
          top: 1,
          width: 1,
          height: 1,
        },
        isFocus: false
      }
    ],
    pageRect: {
      left: 1,
      top: 1,
      width: 1,
      height: 1
    }
  }
}
// Define the AutoSave callback.
let callback: autoFillManager.AutoSaveCallback = {
  onSuccess: () => {
    console.info(`save request on success.`);
  },
  onFailure: () => {
    console.error(`save request on failure.`);
  }
};

@Entry
@Component
struct Index {
  private uiContext: UIContext = this.getUIContext();
  build() {
    GridRow({ gutter: { y: 20 } }) {
      GridCol({ span: 20 }) {
        Button('requestAutoSave')
          .onClick(() => {
            try {
              // Initiate the save request.
              autoFillManager.requestAutoSave(this.uiContext, request, callback);
            } catch (error) {
              console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
            }
          })
      }
    }
  }
}
```

## autoFillManager.requestAutoFill

requestAutoFill(context: UIContext, request: FillRequest, callback?: AutoFillCallback): void

Requests to fill in form data. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name     | Type                                                                    | Mandatory | Description                            |
| -------- | ----------------------------------------------------------------------- | ---- | ------------------------------- |
| context  | [UIContext](../apis-arkui/arkts-apis-uicontext-uicontext.md)            | Yes  | UI context in which the fill operation is performed. |
| request  | [FillRequest](js-apis-inner-application-autoFillRequest.md#fillrequest) | Yes  | AutoFill request information. |
| callback | [AutoFillCallback](#autofillcallback)                                   | No   | Callback invoked when the fill request is complete, used to asynchronously receive the result of the fill operation. If this parameter is not passed, the callback is not triggered. |

**Error codes**

For details about the error codes, see [Ability Error Codes](errorcode-ability.md).
| ID | Error Message        |
| ---------| --------------- |
| 16000050 | Internal error. |

**Example**
```ts
// Index.ets
import { autoFillManager } from '@kit.AbilityKit';
import { UIContext } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

// Configure request based on the actual project.
let request: autoFillManager.FillRequest = {
  type: autoFillManager.AutoFillType.USER_NAME,
  viewData: {
    bundleName: "com.example.testBundleName",
    pageUrl: "testPageUrl",
    pageNodeInfos: [
      {
        id: 1,
        autoFillType: autoFillManager.AutoFillType.USER_NAME,
        value: "testValue1",
        placeholder: "testPlaceholder1",
        rect: {
          left: 1,
          top: 1,
          width: 1,
          height: 1,
        },
        isFocus: false
      },
      {
        id: 2,
        autoFillType: autoFillManager.AutoFillType.PASSWORD,
        value: "testValue2",
        placeholder: "testPlaceholder2",
        rect: {
          left: 1,
          top: 1,
          width: 1,
          height: 1,
        },
        isFocus: false
      }
    ],
    pageRect: {
      left: 1,
      top: 1,
      width: 1,
      height: 1
    }
  }
}
// Define the AutoFill callback.
let callback: autoFillManager.AutoFillCallback = {
  onSuccess: (viewData: autoFillManager.ViewData) => {
    console.info(`fill request on success, viewData: ${JSON.stringify(viewData)}`);
  },
  onFailure: (result: autoFillManager.FillFailureResult) => {
    console.error(`fill request on failure, result: ${JSON.stringify(result)}`);
  }
};

@Entry
@Component
struct Index {
  private uiContext: UIContext = this.getUIContext();
  build() {
    GridRow({ gutter: { y: 20 } }) {
      GridCol({ span: 20 }) {
        Button('requestAutoFill')
          .onClick(() => {
            try {
              // Initiate the fill request.
              autoFillManager.requestAutoFill(this.uiContext, request, callback);
            } catch (error) {
              console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
            }
          })
      }
    }
  }
}
```

## ViewData

type ViewData = _ViewData.default

View data information for autofill.

**Since:** 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction:** This API can be used only in the stage model.

| Type                                                       | Description                        |
| ---------------------------------------------------------- | --------------------------- |
| [_ViewData](js-apis-inner-application-viewData.md#viewdata-1).default | View data information for AutoFill. |

## PageNodeInfo

type PageNodeInfo = _PageNodeInfo.default

Page node information used for auto-fill.

**Since:** 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction:** This API can be used only in the stage model.

| Type                                                               | Description                        |
| ------------------------------------------------------------------ | --------------------------- |
| [_PageNodeInfo](js-apis-inner-application-pageNodeInfo.md#pagenodeinfo-1).default | Represents the page node information used for auto-fill. |

## FillRequest

type FillRequest = _AutoFillRequest.FillRequest

Auto-fill request information.

**Since:** 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction:** This API can be used only in the stage model.

| Type                                                                                     | Description                    |
| ---------------------------------------------------------------------------------------- | ----------------------- |
| [_AutoFillRequest.FillRequest](js-apis-inner-application-autoFillRequest.md#fillrequest) | Auto-fill request information. |

## SaveRequest

type SaveRequest = _AutoFillRequest.SaveRequest

Auto-save request information.

**Since:** 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction:** This API can be used only in the stage model.

| Type                                                                                     | Description                    |
| ---------------------------------------------------------------------------------------- | ----------------------- |
| [_AutoFillRequest.SaveRequest](js-apis-inner-application-autoFillRequest.md#saverequest) | Represents the auto-save request information. |

## AutoFillRect

type AutoFillRect = _AutoFillRect.default

Rectangular area used for auto-fill.

**Since:** 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction:** This API can be used only in the stage model.

| Type                                                               | Description                        |
| ------------------------------------------------------------------ | --------------------------- |
| [_AutoFillRect](js-apis-inner-application-autoFillRect.md#autofillrect-1).default | Represents the rectangular area used for AutoFill. |

## FillFailureResult

type FillFailureResult = _FillFailureResult

Auto-fill failure result.

**Since:** 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction:** This API can be used only in the stage model.

| Type                                                                                                 | Description                  |
| ---------------------------------------------------------------------------------------------------- | --------------------- |
| [_FillFailureResult](js-apis-inner-application-autoFillRequest.md#fillfailureresult) | Represents the AutoFill failure result. |
