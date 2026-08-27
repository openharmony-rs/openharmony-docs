# FillRequestCallback（系统接口）

自动填充或者生成密码时的回调对象，可以通过此回调通知客户端成功或者失败。

**起始版本：** 11

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

## onCancel

```TypeScript
onCancel(fillContent?: string): void
```

通知自动填充已被取消。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fillContent | string | 否 | 表示通知自动填充取消后，返回给输入法框架的填充内容。<br>**起始版本：** 12 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  1.The input parameter is not valid parameter;  2. Mandatory parameters are left unspecified.<br>**适用版本：** 12+ |

**示例**

```TypeScript
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

```TypeScript
// AutoFillPage.ets
import { autoFillManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@Component
struct AutoFillPage {
  storage: LocalStorage | undefined = this.getUIContext().getSharedLocalStorage();
  // fillCallback由AutoFillExtensionAbility的onFillRequest回调传入LocalStorage
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

## onFailure

```TypeScript
onFailure(): void
```

通知自动填充请求已失败。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例**

```TypeScript
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

```TypeScript
// AutoFillPage.ets
import { autoFillManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@Component
struct AutoFillPage {
  storage: LocalStorage | undefined = this.getUIContext().getSharedLocalStorage();
  // fillCallback由AutoFillExtensionAbility的onFillRequest回调传入LocalStorage
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

```TypeScript
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

```TypeScript
// SavePage.ets
import { autoFillManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@Component
struct SavePage {
  storage: LocalStorage | undefined = this.getUIContext().getSharedLocalStorage();
  // saveCallback由AutoFillExtensionAbility的onSaveRequest回调传入LocalStorage
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

## onSuccess

```TypeScript
onSuccess(response: FillResponse): void
```

通知自动填充请求已成功完成。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| response | [FillResponse](arkts-ability-autofillrequest-fillresponse-i-sys.md) | 是 | 自动填充响应信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Mandatory parameters are left unspecified. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例**

```TypeScript
// MyAutoFillExtensionAbility.ts
import { AutoFillExtensionAbility, UIExtensionContentSession, autoFillManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class MyAutoFillExtensionAbility extends AutoFillExtensionAbility {
  onFillRequest(session: UIExtensionContentSession,
    request: autoFillManager.FillRequest,
    callback: autoFillManager.FillRequestCallback) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'autofill onFillRequest');
    try {
      // 初始化LocalStorage
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

```TypeScript
// AutoFillPage.ets
import { autoFillManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@Component
struct AutoFillPage {
  storage: LocalStorage | undefined = this.getUIContext().getSharedLocalStorage();
  // fillCallback和viewData由AutoFillExtensionAbility的onFillRequest回调传入LocalStorage
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

## setAutoFillPopupConfig

```TypeScript
setAutoFillPopupConfig(autoFillPopupConfig: AutoFillPopupConfig): void
```

动态调整气泡弹窗的尺寸和位置。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| autoFillPopupConfig | [AutoFillPopupConfig](arkts-ability-autofillpopupconfig-i-sys.md) | 是 | 气泡弹窗尺寸和位置信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Mandatory parameters are left unspecified. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例**

```TypeScript
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
      // 初始化LocalStorage，存储保存回调
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
      // 初始化LocalStorage，存储保存回调
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
