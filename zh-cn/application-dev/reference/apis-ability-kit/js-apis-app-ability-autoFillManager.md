# @ohos.app.ability.autoFillManager (自动填充框架)

autoFillManager模块提供账号密码保存等功能。

不同于页面切换时触发的系统自动保存功能，该功能需要由用户手动触发。例如用户在网站上输入了账号密码，并点击“保存”按钮，才能触发相应的自动保存操作。

> **说明：**
> 
> 本模块首批接口从API version 11 开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 本模块接口仅可在Stage模型下使用。

## 导入模块

```ts
import { autoFillManager } from '@kit.AbilityKit';
```

## AutoSaveCallback

当保存请求完成时所触发的回调接口。

### onSuccess

onSuccess(): void

当保存请求成功时，该回调被调用。

**原子化服务API**：从API version 12开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**示例：**

参见[AutoSaveCallback.onFailure](#onfailure)。

### onFailure

onFailure(): void

当保存请求失败时，该回调被调用。

**原子化服务API**：从API version 12开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**示例：**

  ```ts
// Index.ets, 含有账号、密码框等组件的页面
import { autoFillManager } from '@kit.AbilityKit';
import { UIContext } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

let uiContext = AppStorage.get<UIContext>("uiContext");
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
  build() {
    Button('requestAutoSave')
      .onClick(() => {
        try {
          // 发起保存请求
          autoFillManager.requestAutoSave(uiContext, callback);
        } catch (error) {
          console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
        }
      })
  }
}
  ```

> **说明：**
>
> 示例中从AppStorage中取得的UiContext为预先在EntryAbility（拉起此页面的Ability）中OnWindowStageCreate生命周期获得，并存储到AppStorage中，具体可参考[requestAutoSave](#autofillmanagerrequestautosave)。

## autoFillManager.requestAutoSave

requestAutoSave(context: UIContext, callback?: AutoSaveCallback): void

请求保存表单数据，使用callback异步回调。
如果当前表单没有提供表单切换的功能，可以通过此接口保存历史表单输入数据，保存请求完成时会触发该回调。

**原子化服务API**：从API version 12开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| context | [UIContext](../apis-arkui/arkts-apis-uicontext-uicontext.md) | 是 | 将在其中执行保存操作的UI上下文。 |
| callback | [AutoSaveCallback](#autosavecallback)  | 否 | 保存请求的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 401      | The parameter check failed. Possible causes: 1. Get instance id failed; 2. Parse instance id failed; 3. The second parameter is not of type callback. |
| 16000050 | Internal error. |

以上错误码详细介绍请参考[元能力子系统错误码](errorcode-ability.md)。

**示例：**

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
    let localStorageData: Record<string, string | common.UIAbilityContext> = {
      'message': "AutoFill Page",
      'context': this.context,
    };
    let storage = new LocalStorage(localStorageData);
    windowStage.loadContent('pages/Index', storage, (err, data) => {
      if (err.code) {
        hilog.error(0x0000, 'testTag', 'Failed to load the content. Cause: %{public}s', JSON.stringify(err) ?? '');
        return;
      }
      // Obtain the main window.
      windowStage.getMainWindow((err: BusinessError, data: window.Window) => {
        let errCode: number = err.code;
        if (errCode) {
          console.error('Failed to obtain the main window. Cause: ' + JSON.stringify(err));
          return;
        }
        console.info('Succeeded in obtaining the main window. Data: ' + JSON.stringify(data));
        // get UIContext instance.
        let uiContext: UIContext = windowStage.getMainWindowSync().getUIContext();
        PersistentStorage.persistProp("uiContext", uiContext);
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

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Text('Hello World')
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
      }

      Button('requestAutoSave')
        .onClick(() => {
          let uiContext = AppStorage.get<UIContext>("uiContext");
          console.info("uiContext: ", JSON.stringify(uiContext));
          try {
            // 发起保存请求
            autoFillManager.requestAutoSave(uiContext, {
              onSuccess: () => {
                console.info(`save request on success.`);
              },
              onFailure: () => {
                console.error(`save request on failure.`);
              }
            });
          } catch (error) {
            console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
          }
        })
        .width('100%')
    }
    .height('100%')
  }
}
  ```
