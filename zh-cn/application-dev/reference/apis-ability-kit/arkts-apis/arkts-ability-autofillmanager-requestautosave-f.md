# requestAutoSave

## 导入模块

```TypeScript
import { autoFillManager } from '@kit.AbilityKit';
```

<a id="requestautosave"></a>
## requestAutoSave

```TypeScript
export function requestAutoSave(context: UIContext, callback?: AutoSaveCallback): void
```

请求保存表单数据。使用callback异步回调。如果当前表单没有提供表单切换的功能，可以通过此接口保存历史表单输入数据，保存请求完成时会触发该回调。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-autoFillManager-export function requestAutoSave(context: UIContext, callback?: AutoSaveCallback): void--><!--Device-autoFillManager-export function requestAutoSave(context: UIContext, callback?: AutoSaveCallback): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [UIContext](../../apis-arkui/arkts-components/arkts-arkui-uicontext-t.md) | 是 | UI context in which the auto-save operation will be performed. |
| callback | [AutoSaveCallback](arkts-ability-autofillmanager-autosavecallback-i.md) | 否 | Implements callbacks triggered when auto-save is complete. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Get instance id failed;<br>2. Parse instance id failed; 3. The second parameter is not of type callback. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例：**

```TypeScript
// EntryAbility.ets
import { UIAbility, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window, UIContext } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage): void {
    // Main window is created, set main page for this ability
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');
    // 创建本地存储实例
    let localStorageData: Record<string, string | common.UIAbilityContext> = {
      'message': "AutoFill Page",
      'context': this.context,
    };
    let storage = new LocalStorage(localStorageData);
    // 加载页面内容
    windowStage.loadContent('pages/Index', storage, (err, data) => {
      if (err && err.code) {
        hilog.error(0x0000, 'testTag', 'Failed to load the content. Cause: %{public}s', JSON.stringify(err) ?? '');
        return;
      }
      // 获取主窗口
      windowStage.getMainWindow((err: BusinessError, data: window.Window) => {
        if (err?.code) {
          console.error('Failed to obtain the main window. Cause: ' + JSON.stringify(err));
          return;
        }
        console.info('Succeeded in obtaining the main window. Data: ' + JSON.stringify(data));
        // 获取UIContext实例
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

let uiContext = AppStorage.get<UIContext>('uiContext');
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

