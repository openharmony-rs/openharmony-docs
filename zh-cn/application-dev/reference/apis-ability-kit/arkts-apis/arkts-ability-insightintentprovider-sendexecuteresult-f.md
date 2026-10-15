# sendExecuteResult

## 导入模块

```TypeScript
import { insightIntentProvider } from '@kit.AbilityKit';
```

## sendExecuteResult

```TypeScript
function sendExecuteResult(instanceId: number, result: insightIntent.ExecuteResult): Promise<void>
```

如果意图提供方需要在业务处理的特定流程中主动发送意图执行结果，可以先通过[setReturnModeForUIAbilityForeground接口](arkts-ability-app-ability-insightintentcontext-insightintentcontext-c.md#setreturnmodeforuiabilityforeground)或[setReturnModeForUIExtensionAbility接口](arkts-ability-app-ability-insightintentcontext-insightintentcontext-c.md#setreturnmodeforuiextensionability)将意图执行结果返回形式[ReturnMode](arkts-ability-insightintent-returnmode-e.md)设置为FUNCTION，然后调用该接口发送意图执行结果，适用于[配置类意图](../../../application-models/insight-intent-config-development.md)。使用Promise异步回调。

意图执行结果返回形式[ReturnMode](arkts-ability-insightintent-returnmode-e.md)设置为FUNCTION后，应用将无需再通过[onExecuteInUIAbilityForegroundMode接口](arkts-ability-app-ability-insightintentexecutor-insightintentexecutor-c.md#onexecuteinuiabilityforegroundmode)或[onExecuteInUIExtensionAbility接口](arkts-ability-app-ability-insightintentexecutor-insightintentexecutor-c.md#onexecuteinuiextensionability)的返回值返回意图执行结果。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

<!--Device-insightIntentProvider-function sendExecuteResult(instanceId: int, result: insightIntent.ExecuteResult): Promise<void>--><!--Device-insightIntentProvider-function sendExecuteResult(instanceId: int, result: insightIntent.ExecuteResult): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| instanceId | number | 是 | 意图实例唯一ID。 |
| result | [insightIntent.ExecuteResult](arkts-ability-insightintent-executeresult-i.md) | 是 | 返回意图执行结果，表示本次意图执行返回给系统入口的数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000003](../errorcode-ability.md#16000003-指定的id不存在) | The specified ID does not exist. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. Possible causes: 1. Connect to system service failed; 2.Send restart message to system service failed; 3.System service failed to communicate with dependency module. |

**示例**

设置意图执行结果延迟返回示例：

```TypeScript
import { InsightIntentExecutor, insightIntent } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class InsightIntentExecutorUI extends InsightIntentExecutor {
  onExecuteInUIAbilityForegroundMode(name: string, param: Record<string, Object>,
    pageLoader: window.WindowStage): insightIntent.ExecuteResult {
    hilog.info(0x0000, 'testTag', 'onExecuteInUIAbilityForegroundMode %{public}s', name);
    let result: insightIntent.ExecuteResult;
    result = {
      code: 0,
      result: {
        message: 'Unsupported insight intent.',
      },
    };
    try {
      // 设置意图执行结果的返回形式为延迟返回
      this.context.setReturnModeForUIAbilityForeground(insightIntent.ReturnMode.FUNCTION);
    } catch (error) {
      let code = (error as BusinessError).code;
      let msg = (error as BusinessError).message;
      console.error(`testTag setReturnModeForUIAbilityForeground fail, error code: ${code}, error msg: ${msg}.`);
    }
    // 将意图实例的id通过localStorage传入目标页面中
    let localStorageData: Record<string, number> = {
      'insightId': this.context.instanceId,
    };
    let storage: LocalStorage = new LocalStorage(localStorageData);
    // 通过pageLoader加载页面
    pageLoader.loadContent('pages/UIAbilityIndex', storage, (err, data) => {
      if (err.code) {
        hilog.error(0x0000, 'testTag', 'Failed to load the content. Cause: %{public}s', JSON.stringify(err));
      } else {
        hilog.info(0x0000, 'testTag', '%{public}s', 'Succeeded in loading the content');
      }
    });
    return result;
  }
}
```

主动发送意图执行结果示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { insightIntent, insightIntentProvider } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  storage: LocalStorage | undefined = this.getUIContext().getSharedLocalStorage();
  insightId: number | undefined = this.storage?.get<number>('insightId');

  build() {
    Column() {
      // 通过sendExecuteResult接口主动返回意图执行结果
      Button('insightIntentProvider sendExecuteResult')
        .onClick(() => {
          try {
            let result: insightIntent.ExecuteResult;
            result = {
              code: 0,
              result: {
                message: 'Unsupported insight intent.',
              },
            };
            insightIntentProvider.sendExecuteResult(this.insightId, result)
              .then(() => {
                console.info('testTag sendExecuteResult success');
              })
              .catch((error: BusinessError) => {
                console.error(`testTag sendExecuteResult fail 1, error code: ${error.code}, error msg: ${error.message}.`);
              });
          } catch (e) {
            let code = (e as BusinessError).code;
            let msg = (e as BusinessError).message;
            console.error(`testTag sendExecuteResult fail 2, error code: ${code}, error msg: ${msg}`);
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}
```
