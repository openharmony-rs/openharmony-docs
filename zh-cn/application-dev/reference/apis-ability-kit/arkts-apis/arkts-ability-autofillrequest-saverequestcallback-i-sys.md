# SaveRequestCallback（系统接口）

自动保存或者手动保存请求回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export interface SaveRequestCallback--><!--Device-unnamed-export interface SaveRequestCallback-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

## onFailure

```TypeScript
onFailure(): void
```

通知保存请求处理失败。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SaveRequestCallback-onFailure(): void--><!--Device-SaveRequestCallback-onFailure(): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |

## 示例

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

```TypeScript
'use static'
// MyAutoFillExtensionAbility.ts
import { AutoFillExtensionAbility, UIExtensionContentSession, autoFillManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { LocalStorage } from '@kit.ArkUI';

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
import { Entry, Column, Text, Button, Row, Component, FontWeight, LocalStorage } from '@kit.ArkUI';

@Entry
@Component
struct SavePage {
  storage: LocalStorage | undefined = this.getUIContext().getSharedLocalStorage();
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
onSuccess(): void
```

通知保存请求已成功处理。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SaveRequestCallback-onSuccess(): void--><!--Device-SaveRequestCallback-onSuccess(): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |

## 示例

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

```TypeScript
'use static'
// MyAutoFillExtensionAbility.ts
import { AutoFillExtensionAbility, UIExtensionContentSession, autoFillManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { LocalStorage } from '@kit.ArkUI';

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

```TypeScript
// SavePage.ets
import { autoFillManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { Entry, Column, Text, Button, Row, Component, FontWeight, LocalStorage } from '@kit.ArkUI';

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

