# sendIntentResult

## 导入模块

```TypeScript
import { insightIntentProvider } from '@kit.AbilityKit';
```

## sendIntentResult

```TypeScript
function sendIntentResult(instanceId: number, result: insightIntent.IntentResult<T>): Promise<void>
```

如果意图提供方需要在业务处理的特定流程中主动发送意图执行结果，可以先通过[setReturnModeForUIAbilityForeground接口](arkts-ability-app-ability-insightintentcontext-insightintentcontext-c.md#setreturnmodeforuiabilityforeground)或[setReturnModeForUIExtensionAbility接口](arkts-ability-app-ability-insightintentcontext-insightintentcontext-c.md#setreturnmodeforuiextensionability)将意图执行结果返回形式[ReturnMode](arkts-ability-insightintent-returnmode-e.md)设置为FUNCTION，然后调用该接口发送意图执行结果。适用于[@InsightIntentEntry](arkts-ability-app-ability-insightintentdecorator-insightintententry-d.md#insightintententry)修饰的[装饰器类意图](../../../application-models/insight-intent-decorator-development.md)。使用Promise异步回调。

意图执行结果返回形式[ReturnMode](arkts-ability-insightintent-returnmode-e.md)设置为FUNCTION后，应用将无需再通过onExecute接口的返回值返回意图执行结果。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

<!--Device-insightIntentProvider-function sendIntentResult(instanceId: int, result: insightIntent.IntentResult<T>): Promise<void>--><!--Device-insightIntentProvider-function sendIntentResult(instanceId: int, result: insightIntent.IntentResult<T>): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| instanceId | number | 是 | 意图实例唯一ID。 |
| result | [insightIntent.IntentResult](arkts-ability-insightintent-intentresult-i.md)&lt;T&gt; | 是 | 返回意图执行结果，表示本次意图执行返回给系统入口的数据。 |

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
import { insightIntent, InsightIntentEntry, InsightIntentEntryExecutor } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class PlayVideoResultDef {
  resultCode: number = 0;
  resultMsg: string = '';
  someInvalid1: string | undefined = undefined;
  someInvalid2: string | null = null;
}

// 播放视频
@InsightIntentEntry({
  intentName: 'PlayVideo',
  domain: 'VideosDomain',
  intentVersion: '1.0.2',
  displayName: '播放视频',
  displayDescription: '播放视频意图',
  schema: 'PlayVideo',
  icon: $r('app.media.background'),
  llmDescription: '播放视频意图',
  keywords: ['视频播放', '播放视频', 'PlayVideo'],
  abilityName: 'EntryAbility1',
  executeMode: [insightIntent.ExecuteMode.UI_ABILITY_FOREGROUND],
})
export default class PlayVideo extends InsightIntentEntryExecutor<PlayVideoResultDef> {

  onExecute(): Promise<insightIntent.IntentResult<PlayVideoResultDef>> {
    console.info('testTag', 'PlayVideo onExecute success')
    let result: insightIntent.IntentResult<PlayVideoResultDef> = {
      code: 0,
      result: {
        resultCode: 0x0000,
        resultMsg: 'Callback PlayVideo Success',
        someInvalid1: undefined,
        someInvalid2: null
      }
    }
    let instanceId: number = this.context.instanceId;
    try {
      // 设置意图执行结果的返回形式为延迟返回
      this.context.setReturnModeForUIAbilityForeground(insightIntent.ReturnMode.FUNCTION);
      console.info('testTag: setReturnModeForUIAbilityForeground success');
    } catch (error) {
      let code = (error as BusinessError).code;
      let msg = (error as BusinessError).message;
      console.error(`testTag: setReturnModeForUIAbilityForeground failed, error code: ${code}, error msg: ${msg}.`);
    }

    try {
      // 将意图实例的id通过localStorage传入目标页面中
      let localStorageData: Record<string, number> = {
        'insightId': instanceId,
      };
      let storage: LocalStorage = new LocalStorage(localStorageData);
      // 通过pageLoader加载页面
      this.windowStage?.loadContent('pages/Index', storage);
      console.info('testTag', 'Succeeded in loading the content1')
    } catch (err) {
      let code = (err as BusinessError).code;
      let msg = (err as BusinessError).message;
      console.error(`testTag loadContent error code: ${code}, error msg: ${msg}.`);
    }
    return Promise.resolve(result);
  }
}
```

主动发送意图执行结果示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { insightIntent, insightIntentProvider } from '@kit.AbilityKit';

class PlayVideoResultDef {
  resultCode: number = 0;
  resultMsg: string = '';
  someInvalid1: string | undefined = undefined;
  someInvalid2: string | null = null;
}

@Entry
@Component
struct Index {
  storage: LocalStorage | undefined = this.getUIContext().getSharedLocalStorage();
  insightId: number | undefined = this.storage?.get<number>('insightId');

  build() {
    Column() {
      // 通过sendIntentResult接口主动返回意图执行结果
      Button('insightIntentProvider sendIntentResult')
        .onClick(() => {
          try {
            let result: insightIntent.IntentResult<PlayVideoResultDef> = {
              code: 0,
              result: {
                resultCode: 123,
                resultMsg: 'Function PlayVideo Success',
                someInvalid1: undefined,
                someInvalid2: null
              }
            }
            insightIntentProvider.sendIntentResult(this.insightId, result)
              .then(() => {
                console.info('testTag sendIntentResult success');
              })
              .catch((error: BusinessError) => {
                console.error(`testTag sendIntentResult error, error code: ${error.code}, error msg: ${error.message}.`);
              });
          } catch (error) {
            let code = (error as BusinessError).code;
            let msg = (error as BusinessError).message;
            console.error(`testTag sendIntentResult fail, error code: ${code}, error msg: ${msg}.`);
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}
```
