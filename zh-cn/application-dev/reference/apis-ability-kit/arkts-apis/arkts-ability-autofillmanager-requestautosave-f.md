# requestAutoSave

## requestAutoSave

```TypeScript
export function requestAutoSave(context: UIContext, callback?: AutoSaveCallback): void
```

请求保存表单数据。使用callback异步回调。 如果当前表单没有提供表单切换的功能，可以通过此接口保存历史表单输入数据，保存请求完成时会触发该回调。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-autoFillManager-export function requestAutoSave(context: UIContext, callback?: AutoSaveCallback): void--><!--Device-autoFillManager-export function requestAutoSave(context: UIContext, callback?: AutoSaveCallback): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | UI context in which the auto-save operation will be performed. |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Implements callbacks triggered when auto-save is complete. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Get instance id failed;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Parse instance id failed; 3. The second parameter is not of type callback. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
// EntryAbility.ets
import { UIAbility, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window, UIContext } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage): void {
    // 主窗口创建后，为此Ability设置主页面。
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');
    // 创建本地存储实例
    let localStorageData: Record<string, string | common.UIAbilityContext> = {
      'message': "AutoFill Page",
      'context': this.context,
    };
    // 加载页面内容
    let storage = new LocalStorage(localStorageData);
    windowStage.loadContent('pages/Index', storage, (err, data) => {
      if (err && err.code) {
        hilog.error(0x0000, 'testTag', 'Failed to load the content. Cause: %{public}s', JSON.stringify(err) ?? '');
        return;
      }
      // 获取主窗口。
      windowStage.getMainWindow((err: BusinessError, data: window.Window) => {
        let errCode: number = err?.code;
        if (errCode) {
          console.error('Failed to obtain the main window. Cause: ' + JSON.stringify(err));
          return;
        }
        console.info('Succeeded in obtaining the main window. Data: ' + JSON.stringify(data));
        // 获取UIContext实例。
        let uiContext: UIContext = windowStage.getMainWindowSync().getUIContext();
        // 将UIContext存储到AppStorage中，供其他页面访问
        AppStorage.setOrCreate("uiContext", uiContext);
      })
      hilog.info(0x0000, 'testTag', 'Succeeded in loading the content. Data: %{public}s', JSON.stringify(data) ?? '');
    });
  }
}
```

```TypeScript
// Index.ets
import { autoFillManager } from '@kit.AbilityKit';
import { UIContext } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

// 定义自动保存回调
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
  // 获取当前UIContext实例
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
              // 发起保存请求
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

ArkTS-Sta示例：

```TypeScript
'use static'

// EntryAbility.ets
import { UIAbility, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window, UIContext, LocalStorage, PersistentStorage } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage): void {
    // 主窗口创建后，为此Ability设置主页面。
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');
    let localStorageData: Record<string, string | common.UIAbilityContext> = {
      'message': "AutoFill Page",
      'context': this.context,
    };
    let storage = new LocalStorage(localStorageData);
    windowStage.loadContent('pages/Index', storage, (err, data) => {
      if (err) {
        hilog.error(0x0000, 'testTag', 'Failed to load the content. Cause: %{public}s', JSON.stringify(err) ?? '');
        return;
      }
      // 获取主窗口。
      windowStage.getMainWindow((err: BusinessError | null, data: window.Window | undefined) => {
        if (err) {
          console.error(`Failed to obtain the main window. Cause: ${JSON.stringify(err)}`);
          return;
        }
        console.info(`Succeeded in obtaining the main window. Data:  ${JSON.stringify(data)}`);
        // 获取UIContext实例。
        let uiContext: UIContext = windowStage.getMainWindowSync().getUIContext();
        PersistentStorage.persistProp("uiContext", uiContext);
      })
      console.info(`Succeeded in loading the content. Data:  ${JSON.stringify(data)}`);
    });
  }
}
```

```TypeScript
'use static'

// Index.ets
import { autoFillManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { Entry, Component, Button, UIContext, State, GridRow, GridCol, TextInput, InputType } from '@kit.ArkUI';

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
              // 发起保存请求
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

