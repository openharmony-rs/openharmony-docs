# AutoFillRequest (System API)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @hanchen45; @Luobniz21-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=e2c3267fc728379ed661f6395560cc18d085c54a translatedAt=2026-09-03T11:47:10.270Z pushedAt=2026-09-05T10:47:30.694Z -->

The module provides page data and callbacks when a callback is triggered for the AutoFillExtensionAbility.

> **NOTE**
>
> The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> This page contains only the system APIs of this module. For details about other public APIs, see [AutoFillRequest](js-apis-inner-application-autoFillRequest.md).

## Modules to Import

```ts
import { autoFillManager } from '@kit.AbilityKit';
```

## FillRequest

Defines the information about an auto-fill request.

**System capability**: SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction:** This API can be used only in the stage model.

| Name       | Type                | Read-Only| Optional| Description                                                        |
| ----------- | -------------------- | ---- | ---- | ------------------------------------------------------------ |
| customData<sup>13+</sup>    | [CustomData](js-apis-inner-application-customData-sys.md)               | No  | No  | Custom data.            |
| isPopup<sup>12+</sup>    | boolean               | No  | No  | Whether a dialog box is displayed for the auto-fill request.<br>**true**: A dialog box is displayed<br>**false**: A modal window is displayed             |

## UpdateRequest<sup>12+</sup>

Defines the information about an auto-update request.

**System capability**: SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction:** This API can be used only in the stage model.

| Name       | Type                | Read-Only| Optional| Description                                                        |
| ----------- | -------------------- | ---- | ---- | ------------------------------------------------------------ |
| viewData    | [ViewData](js-apis-inner-application-viewData-sys.md)               | No   | No   | Page data, including the node information, field attributes, corresponding values, and other structural information of the page.    |

## FillResponse

Defines the information about the response to an auto-fill request.

**System capability**: SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction:** This API can be used only in the stage model.

| Name       | Type                | Read-Only| Optional| Description                                                        |
| ----------- | -------------------- | ---- | ---- | ------------------------------------------------------------ |
| viewData    | [ViewData](js-apis-inner-application-viewData-sys.md)               | No   | No   | Page data, including structural information such as the node information, field attributes, and corresponding values of the page.    |

## FillRequestCallback

Implements callbacks for an auto-fill request, which is used to automatically fill in or generate a password. The callbacks can be used to notify the client of the success or failure of the request.

**Model restriction:** This API can be used only in the stage model.

### onSuccess

onSuccess(response: FillResponse): void

Called when an auto-fill request is successfully processed.

**System capability**: SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | ------------------------------ |
| response | [FillResponse](#fillresponse)  | Yes | Auto-fill response information, which contains the filled page data and related status information, and is used to notify the client of the result of the auto-fill operation. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 202  | Permission denied, non-system app called system api. |
| 401  | Mandatory parameters are left unspecified. |
| 16000050 | Internal error. |

**Example**

```ts
// MyAutoFillExtensionAbility.ts
import { AutoFillExtensionAbility, UIExtensionContentSession, autoFillManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class MyAutoFillExtensionAbility extends AutoFillExtensionAbility {
  onFillRequest(session: UIExtensionContentSession,
    request: autoFillManager.FillRequest,
    callback: autoFillManager.FillRequestCallback) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'autofill onFillRequest');
    try {
      // Initialize LocalStorage.
      let storageData: Record<string, string | autoFillManager.FillRequestCallback | autoFillManager.ViewData> = {
        'fillCallback': callback,
        'message': 'AutoFill Page',
        'viewData': request.viewData,
      }
      let storage_fill = new LocalStorage(storageData);
      if (session) {
        session.loadContent('pages/AutoFillPage', storage_fill);
      } else {
        hilog.error(0x0000, 'testTag', '%{public}s', 'session is null');
      }
    } catch (err) {
      hilog.error(0x0000, 'testTag', '%{public}s', 'failed to load content');
    }
  }
}
```

```ts
// AutoFillPage.ets
import { autoFillManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@Component
struct AutoFillPage {
  storage: LocalStorage | undefined = this.getUIContext().getSharedLocalStorage();
  // Pass fillCallback and viewData to LocalStorage through the onFillRequest callback of AutoFillExtensionAbility.
  fillCallback: autoFillManager.FillRequestCallback | undefined =
    this.storage?.get<autoFillManager.FillRequestCallback>('fillCallback');
  viewData: autoFillManager.ViewData | undefined = this.storage?.get<autoFillManager.ViewData>('viewData');

  build() {
    Row() {
      Column() {
        Text('AutoFill Page')
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
      }

      Button('onSuccess')
        .onClick(() => {
          if (this.viewData) {
            this.viewData.pageNodeInfos[0].value = 'user1';
            this.viewData.pageNodeInfos[1].value = 'user1 password';
            this.viewData.pageNodeInfos[2].value = 'user1 generate new password';
            hilog.info(0x0000, 'testTag', 'autofill success with viewData: %{public}s', JSON.stringify(this.viewData));
            try {
              this.fillCallback?.onSuccess({ viewData: this.viewData });
            } catch (error) {
              console.error(`catch error, code: ${(error as BusinessError).code},
                  message: ${(error as BusinessError).message}`);
            }
          }
        })
        .width('100%')
    }
    .height('100%')
  }
}
```

### onFailure

onFailure(): void

Called when an auto-fill request fails to be processed.

**System capability**: SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction:** This API can be used only in the stage model.

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 202 | Permission denied, non-system app called system api. |
| 16000050 | Internal error. |

**Example**

```ts
// MyAutoFillExtensionAbility.ts
import { AutoFillExtensionAbility, UIExtensionContentSession, autoFillManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class MyAutoFillExtensionAbility extends AutoFillExtensionAbility {
  onFillRequest(session: UIExtensionContentSession,
    request: autoFillManager.FillRequest,
    callback: autoFillManager.FillRequestCallback) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'autofill onFillRequest');
    try {
      let storageData: Record<string, string | autoFillManager.FillRequestCallback | autoFillManager.ViewData> = {
        'fillCallback': callback,
        'message': 'AutoFill Page',
        'viewData': request.viewData,
      }
      let storage_fill = new LocalStorage(storageData);
      if (session) {
        session.loadContent('pages/AutoFill Page', storage_fill);
      } else {
        hilog.error(0x0000, 'testTag', '%{public}s', 'session is null');
      }
    } catch (err) {
      hilog.error(0x0000, 'testTag', '%{public}s', 'failed to load content');
    }
  }
}
```

```ts
// AutoFillPage.ets
import { autoFillManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@Component
struct AutoFillPage {
  storage: LocalStorage | undefined = this.getUIContext().getSharedLocalStorage();
  // Pass fillCallback to LocalStorage through the onFillRequest callback of AutoFillExtensionAbility.
  fillCallback: autoFillManager.FillRequestCallback | undefined =
    this.storage?.get<autoFillManager.FillRequestCallback>('fillCallback');
  
  build() {
    Row() {
      Column() {
        Text('AutoFill Page')
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
      }

      Button('onFailure')
        .onClick(() => {
          hilog.info(0x0000, 'testTag', 'autofill failure');
          try {
            this.fillCallback?.onFailure();
          } catch (error) {
            console.error(`catch error, code: ${(error as BusinessError).code},
              message: ${(error as BusinessError).message}`);
          }
        })
        .width('100%')
    }
    .height('100%')
  }
}
```

### onCancel

onCancel(fillContent?: string): void

Called when an auto-fill request is canceled.

**System capability**: SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name                   | Type  | Mandatory| Description                |
| ------------------------- | ------ | ---- | -------------------- |
| fillContent | string | No | Fill content returned to the input method framework after notification auto-fill is canceled. If this parameter is not passed or is undefined, an empty string is returned. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 202  | Permission denied, non-system app called system api. |
| 401  | Parameter error. Possible causes: 1. The input parameter is not valid parameter;2. Mandatory parameters are left unspecified. <br>Applicable version: 12+|
| 16000050 | Internal error. |

**Example**

```ts
// MyAutoFillExtensionAbility.ts
import { AutoFillExtensionAbility, UIExtensionContentSession, autoFillManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class MyAutoFillExtensionAbility extends AutoFillExtensionAbility {
  onFillRequest(session: UIExtensionContentSession,
    request: autoFillManager.FillRequest,
    callback: autoFillManager.FillRequestCallback) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'autofill onFillRequest');
    try {
      let storageData: Record<string, string | autoFillManager.FillRequestCallback | autoFillManager.ViewData> = {
        'fillCallback': callback,
        'message': 'AutoFill Page',
        'viewData': request.viewData,
      }
      let storage_fill = new LocalStorage(storageData);
      if (session) {
        session.loadContent('pages/AutoFillPage', storage_fill);
      } else {
        hilog.error(0x0000, 'testTag', '%{public}s', 'session is null');
      }
    } catch (err) {
      hilog.error(0x0000, 'testTag', '%{public}s', 'failed to load content');
    }
  }
}
```

```ts
// AutoFillPage.ets
import { autoFillManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@Component
struct AutoFillPage {
  storage: LocalStorage | undefined = this.getUIContext().getSharedLocalStorage();
  // fillCallback is passed into LocalStorage by the onFillRequest callback of AutoFillExtensionAbility.
  fillCallback: autoFillManager.FillRequestCallback | undefined =
    this.storage?.get<autoFillManager.FillRequestCallback>('fillCallback');

  build() {
    Row() {
      Column() {
        Text('AutoFill Page')
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
      }

      Button('onCancel')
        .onClick(() => {
          hilog.info(0x0000, 'testTag', 'autofill cancel');
          try {
            this.fillCallback?.onCancel();
          } catch (error) {
            console.error(`catch error, code: ${(error as BusinessError).code},
                message: ${(error as BusinessError).message}`);
          }
        })
        .width('100%')
    }
    .height('100%')
  }
}
```

### setAutoFillPopupConfig<sup>12+</sup>

setAutoFillPopupConfig(autoFillPopupConfig: AutoFillPopupConfig ): void

Sets the size and position of an auto-fill pop-up.

**System capability**: SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | ------------------------------ |
| autoFillPopupConfig | [AutoFillPopupConfig](js-apis-inner-application-autoFillPopupConfig-sys.md) | Yes| Size and position of the auto-fill pop-up.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 202  | Permission denied, non-system app called system api. |
| 401  | Mandatory parameters are left unspecified. |
| 16000050 | Internal error. |

**Example**

```ts
// MyAutoFillExtensionAbility.ts
import { AutoFillExtensionAbility, UIExtensionContentSession, autoFillManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class AutoFillAbility extends AutoFillExtensionAbility {
  storage: LocalStorage = new LocalStorage();

  onCreate(): void {
    hilog.info(0x0000, 'testTag', '%{public}s', 'autofill onCreate');
  }

  onDestroy(): void {
    hilog.info(0x0000, 'testTag', '%{public}s', 'autofill onDestroy');
  }

  onSessionDestroy(session: UIExtensionContentSession) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'autofill onSessionDestroy');
    hilog.info(0x0000, 'testTag', 'session content: %{public}s', `session: ${JSON.stringify(session)}.`);
  }

  onForeground(): void {
    hilog.info(0x0000, 'testTag', '%{public}s', 'autofill onForeground');
  }

  onBackground(): void {
    hilog.info(0x0000, 'testTag', '%{public}s', 'autofill onBackground');
  }

  onUpdateRequest(request: autoFillManager.UpdateRequest): void {
    hilog.info(0x0000, 'testTag', '%{public}s', 'autofill onUpdateRequest');
    console.info(`get fill request viewData: ${JSON.stringify(request.viewData)}.`);
    let fillCallback = this.storage.get<autoFillManager.FillRequestCallback>('fillCallback');

    if (fillCallback) {
      try {
        hilog.info(0x0000, 'testTag',
          `pageNodeInfos.value: ${JSON.stringify(request.viewData.pageNodeInfos[0].value)}.`);
        fillCallback.setAutoFillPopupConfig({
          popupSize: {
            width: 400 + request.viewData.pageNodeInfos[0].value.length * 10,
            height: 200 + request.viewData.pageNodeInfos[0].value.length * 10
          },
          placement: autoFillManager.PopupPlacement.TOP
        });
      } catch (err) {
        let code = (err as BusinessError).code;
        let msg = (err as BusinessError).message;
        hilog.info(0x0000, 'testTag', `autoFillPopupConfig failed, error code: ${code}, error msg: ${msg}.`);
      }
    }
  }

  onFillRequest(session: UIExtensionContentSession, request: autoFillManager.FillRequest,
    callback: autoFillManager.FillRequestCallback) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'autofill onFillRequest');
    hilog.info(0x0000, 'testTag', 'Fill RequestCallback: %{public}s ', JSON.stringify(callback));
    console.info(`testTag. Get fill request viewData: ${JSON.stringify(request.viewData)}.`);
    console.info(`testTag. Get fill request type: ${JSON.stringify(request.type)}.`);

    try {
      // Initialize LocalStorage to store the save callback.
      let localStorageData: Record<string, string | autoFillManager.FillRequestCallback | autoFillManager.ViewData | autoFillManager.AutoFillType> =
        {
          'message': 'AutoFill Page',
          'fillCallback': callback,
          'viewData': request.viewData,
          'autoFillType': request.type
        }
      let storage_fill = new LocalStorage(localStorageData);
      console.info(`testTag. Session: ${JSON.stringify(session)}.`);
      let size: autoFillManager.PopupSize = {
        width: 400,
        height: 200
      };
      callback.setAutoFillPopupConfig({
        popupSize: size
      });
      session.loadContent('pages/SelectorList', storage_fill);
    } catch (err) {
      let code = (err as BusinessError).code;
      let msg = (err as BusinessError).message;
      hilog.error(0x0000, 'testTag', '%{public}s',
        `autofill failed to load content, error code: ${code}, error msg: ${msg}.`);
    }
  }

  onSaveRequest(session: UIExtensionContentSession, request: autoFillManager.SaveRequest,
    callback: autoFillManager.SaveRequestCallback) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'autofill onSaveRequest');
    try {
      // Initialize LocalStorage to store the save callback.
      let localStorageData: Record<string, string | autoFillManager.SaveRequestCallback> = {
        'message': 'AutoFill Page',
        'saveCallback': callback
      };
      let storage_save = new LocalStorage(localStorageData);
      if (session) {
        session.loadContent('pages/SavePage', storage_save);
      } else {
        hilog.error(0x0000, 'testTag', '%{public}s', 'session is null');
      }
    } catch (err) {
      hilog.error(0x0000, 'testTag', '%{public}s', 'failed to load content');
    }
  }
}
```

## SaveRequestCallback

Implements callbacks for an automatic or a manual saving request.

**Model restriction:** This API can be used only in the stage model.

### SaveRequestCallback.onSuccess

onSuccess(): void

Called when a saving request is successfully processed.

**System capability**: SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction:** This API can be used only in the stage model.

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 202 | Permission denied, non-system app called system api. |
| 16000050 | Internal error. |

**Example**

```ts
// MyAutoFillExtensionAbility.ts
import { AutoFillExtensionAbility, UIExtensionContentSession, autoFillManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class MyAutoFillExtensionAbility extends AutoFillExtensionAbility {
  onSaveRequest(session: UIExtensionContentSession,
    request: autoFillManager.SaveRequest,
    callback: autoFillManager.SaveRequestCallback) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'onSaveRequest');
    try {
      let storageData: Record<string, string | autoFillManager.SaveRequestCallback | autoFillManager.ViewData> = {
        'message': 'AutoFill Page',
        'saveCallback': callback,
        'viewData': request.viewData
      };
      let storage_save = new LocalStorage(storageData);
      if (session) {
        session.loadContent('pages/SavePage', storage_save);
      } else {
        hilog.error(0x0000, 'testTag', '%{public}s', 'session is null');
      }
    } catch (err) {
      hilog.error(0x0000, 'testTag', '%{public}s', 'failed to load content');
    }
  }
}
```

```ts
// SavePage.ets
import { autoFillManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@Component
struct SavePage {
  storage: LocalStorage | undefined = this.getUIContext().getSharedLocalStorage();
  // Pass saveCallback into LocalStorage via the onSaveRequest callback of AutoFillExtensionAbility.
  saveCallback: autoFillManager.SaveRequestCallback | undefined =
    this.storage?.get<autoFillManager.SaveRequestCallback>('saveCallback');

  build() {
    Row() {
      Column() {
        Text('SavePage')
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
      }

      Button('onSuccess')
        .onClick(() => {
          hilog.info(0x0000, 'testTag', 'autosave success');
          try {
            this.saveCallback?.onSuccess();
          } catch (error) {
            console.error(`catch error, code: ${(error as BusinessError).code},
                message: ${(error as BusinessError).message}`);
          }
        })
        .width('100%')
    }
    .height('100%')
  }
}
```

### SaveRequestCallback.onFailure

onFailure(): void

Called when a saving request fails to be processed.

**System capability**: SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction:** This API can be used only in the stage model.

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 202 | Permission denied, non-system app called system api. |
| 16000050 | Internal error. |

**Example**

```ts
// MyAutoFillExtensionAbility.ts
import { AutoFillExtensionAbility, UIExtensionContentSession, autoFillManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class MyAutoFillExtensionAbility extends AutoFillExtensionAbility {
  onSaveRequest(session: UIExtensionContentSession,
    request: autoFillManager.SaveRequest,
    callback: autoFillManager.SaveRequestCallback) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'onSaveRequest');
    try {
      let storageData: Record<string, string | autoFillManager.SaveRequestCallback | autoFillManager.ViewData> = {
        'message': 'AutoFill Page',
        'saveCallback': callback,
        'viewData': request.viewData
      }
      let storage_save = new LocalStorage(storageData);
      if (session) {
        session.loadContent('pages/SavePage', storage_save);
      } else {
        hilog.error(0x0000, 'testTag', '%{public}s', 'session is null');
      }
    } catch (err) {
      hilog.error(0x0000, 'testTag', '%{public}s', 'failed to load content');
    }
  }
}
```

```ts
// SavePage.ets
import { autoFillManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@Component
struct SavePage {
  storage: LocalStorage | undefined = this.getUIContext().getSharedLocalStorage();
  // Pass saveCallback into LocalStorage via the onSaveRequest callback of AutoFillExtensionAbility.
  saveCallback: autoFillManager.SaveRequestCallback | undefined =
    this.storage?.get<autoFillManager.SaveRequestCallback>('saveCallback');

  build() {
    Row() {
      Column() {
        Text('Save Page')
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
      }

      Button('onFailure')
        .onClick(() => {
          hilog.error(0x0000, 'testTag', 'autofill onFailure');
          try {
            this.saveCallback?.onFailure();
          } catch (error) {
            console.error(`catch error, code: ${(error as BusinessError).code},
              message: ${(error as BusinessError).message}`);
          }
        })
        .width('100%')
    }
    .height('100%')
  }
}
```
