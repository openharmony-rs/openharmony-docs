# @ohos.app.ability.insightIntentProvider (意图提供方管理能力)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @linjunjie6-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

本模块为意图提供方提供管理能力，如主动发送指定意图的执行结果。
> **说明：**
>
> 本模块首批接口从API version 23开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 本模块接口仅可在Stage模型下使用。

## 导入模块

```ts
import { insightIntentProvider } from '@kit.AbilityKit';
```

## insightIntentProvider.sendExecuteResult

sendExecuteResult(instanceId: number, result: insightIntent.ExecuteResult): Promise&lt;void&gt;

如果意图提供方需要在业务处理的特定流程中主动发送意图执行结果，可以先通过[setReturnModeForUIAbilityForeground](./js-apis-app-ability-insightIntentContext.md#insightintentcontextsetreturnmodeforuiabilityforeground23)或[setReturnModeForUIExtensionAbility](./js-apis-app-ability-insightIntentContext.md#insightintentcontextsetreturnmodeforuiextensionability23)将意图执行结果返回形式[ReturnMode](./js-apis-app-ability-insightIntent.md#returnmode23)设置为FUNCTION，然后调用该接口发送意图执行结果，适用于[配置类意图](../../application-models/insight-intent-config-development.md)。使用Promise异步回调。<br/>
意图执行结果返回形式[ReturnMode](./js-apis-app-ability-insightIntent.md#returnmode23)设置为FUNCTION后，应用将无需再通过[onExecuteInUIAbilityForegroundMode接口](./js-apis-app-ability-insightIntentExecutor.md#onexecuteinuiabilityforegroundmode)或[onExecuteInUIExtensionAbility](./js-apis-app-ability-insightIntentExecutor.md#onexecuteinuiextensionability)的返回值返回意图执行结果。

**模型约束**：此接口仅可在Stage模型下使用。

**原子化服务API**：从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**参数：**

  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | [instanceId](./js-apis-app-ability-insightIntentContext.md#属性) | number | 是 | 意图实例唯一ID。 |
  | result | [insightIntent.ExecuteResult](js-apis-app-ability-insightIntent.md#executeresult) | 是 | 返回意图执行结果，表示本次意图执行返回给系统入口的数据。 |

**返回值：**

| 类型             | 说明              |
| -------------- | --------------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码**：

以下错误码详细介绍请参考[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 16000003      | The specified ID does not exist. |
| 16000050      | Internal error. Possible causes: 1. Connect to system service failed; 2.Send restart message to system service failed; 3.System service failed to communicate with dependency module. |

**示例：**

设置意图执行结果延迟返回示例：
```ts
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
```ts
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

## insightIntentProvider.sendIntentResult

sendIntentResult(instanceId: number, result: insightIntent.IntentResult&lt;T&gt;): Promise&lt;void&gt;

如果意图提供方需要在业务处理的特定流程中主动发送意图执行结果，可以先通过[setReturnModeForUIAbilityForeground](./js-apis-app-ability-insightIntentContext.md#insightintentcontextsetreturnmodeforuiabilityforeground23)或[setReturnModeForUIExtensionAbility](./js-apis-app-ability-insightIntentContext.md#insightintentcontextsetreturnmodeforuiextensionability23)将意图执行结果返回形式[ReturnMode](./js-apis-app-ability-insightIntent.md#returnmode23)设置为FUNCTION，然后调用该接口发送意图执行结果。适用于[@InsightIntentEntry](./js-apis-app-ability-InsightIntentDecorator.md#insightintententry)修饰的[装饰器类意图](../../application-models/insight-intent-decorator-development.md)。使用Promise异步回调。<br/>
意图执行结果返回形式[ReturnMode](./js-apis-app-ability-insightIntent.md#returnmode23)设置为FUNCTION后，应用将无需再通过[onExecute接口](./js-apis-app-ability-InsightIntentEntryExecutor.md#onexecute)的返回值返回意图执行结果。

**模型约束**：此接口仅可在Stage模型下使用。

**原子化服务API**：从API version 23开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**参数：**

  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | [instanceId](./js-apis-app-ability-insightIntentContext.md#属性) | number | 是 | 意图实例唯一ID。 |
  | result | [insightIntent.IntentResult\<T>](js-apis-app-ability-insightIntent.md#intentresultt20) | 是 | 返回意图执行结果，表示本次意图执行返回给系统入口的数据。 |

**返回值：**

| 类型             | 说明              |
| -------------- | --------------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码**：

以下错误码详细介绍请参考[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 16000003      | The specified ID does not exist. |
| 16000050      | Internal error. Possible causes: 1. Connect to system service failed; 2.Send restart message to system service failed; 3.System service failed to communicate with dependency module. |

**示例：**

设置意图执行结果延迟返回示例：
```ts
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
```ts
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

## InsightIntentExecutionCallBack

意图执行回调接口，用于注册意图执行前的回调。

**起始版本**：26.1.0

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**原子化服务API**：从API版本26.1.0开始，该接口支持在原子化服务中使用。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| onWillInsightIntentExecuteCallBack | [OnWillInsightIntentExecuteCallBackFn](#onwillinsightintentexecutecallbackfn) | 否 | 是 | 意图执行前的回调。 |

## OnWillInsightIntentExecuteCallBackFn

type OnWillInsightIntentExecuteCallBackFn = (executionInfo: insightIntent.InsightIntentExecutionInfo) => void

意图执行前的回调函数类型。

**起始版本**：26.1.0

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**原子化服务API**：从API版本26.1.0开始，该接口支持在原子化服务中使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| executionInfo | [insightIntent.InsightIntentExecutionInfo](./js-apis-app-ability-insightIntent.md#insightintentexecutioninfo) | 是 | 意图执行信息。 |

## insightIntentProvider.onWillInsightIntentExecute

onWillInsightIntentExecute(callback: InsightIntentExecutionCallBack): void

注册意图执行监听器，在意图执行前触发回调。

**起始版本**：26.1.0

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**原子化服务API**：从API版本26.1.0开始，该接口支持在原子化服务中使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | [InsightIntentExecutionCallBack](#insightintentexecutioncallback) | 是 | 意图执行前触发的回调。 |

**示例：**

  由于回调注册与意图执行可能位于不同文件，这里使用一个跨文件共享的全局单例`CallerInfoStorage`来保存调用方信息。该单例定义在一个单独的文件`CallerInfoStorage.ets`中。

  ```ts
  // CallerInfoStorage.ets
  import { insightIntent } from '@kit.AbilityKit';

  export class CallerInfoStorage {
    private static callerInfo: insightIntent.InsightIntentExecutionInfo | undefined = undefined;

    static setCallerInfo(info: insightIntent.InsightIntentExecutionInfo): void {
      CallerInfoStorage.callerInfo = info;
    }

    static getCallerInfo(): insightIntent.InsightIntentExecutionInfo | undefined {
      return CallerInfoStorage.callerInfo;
    }
  }
  ```

  在`onWillInsightIntentExecute`回调中，将调用方信息写入`CallerInfoStorage`：

  ```ts
  import { AbilityConstant, UIAbility, Want, insightIntent, insightIntentProvider } from '@kit.AbilityKit';
  import { CallerInfoStorage } from './CallerInfoStorage';

  export default class EntryAbility extends UIAbility {
    private executionCallBack: insightIntentProvider.InsightIntentExecutionCallBack = {
      onWillInsightIntentExecuteCallBack: (executionInfo: insightIntent.InsightIntentExecutionInfo) => {
        // 将调用方信息写入全局单例，供其它文件的意图执行逻辑取用
        CallerInfoStorage.setCallerInfo(executionInfo);
      }
    };

    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
      // 在Ability创建时注册意图执行监听器，在意图执行前触发回调
      insightIntentProvider.onWillInsightIntentExecute(this.executionCallBack);
    }
  }
  ```

`onWillInsightIntentExecuteCallBack`在意图执行前触发，可将调用方信息写入全局单例，供意图执行逻辑通过权限管理接口`checkAccessTokenSync`校验调用方权限。对于使用装饰器开发的Function类意图，可在意图定义接口中通过`permissions`字段声明执行该意图所需的权限，实际权限校验由意图提供方在意图执行逻辑中完成，示例如下。

  ```ts
  import { abilityAccessCtrl, InsightIntentFunction, InsightIntentFunctionMethod } from '@kit.AbilityKit';
  import { CallerInfoStorage } from './CallerInfoStorage';

  @InsightIntentFunction()
  export class ClassForFuncDemo {
    @InsightIntentFunctionMethod({
      intentName: 'GetWeather',
      domain: 'LifeDomain',
      intentVersion: '1.0.1',
      displayName: '查询天气',
      displayDescription: '显示天气信息',
      icon: $r('app.media.app_icon'), // $r表示本地图标，需要在资源目录中定义
      llmDescription: 'Get weather of a location',
      // 声明执行该意图所需的权限，实际校验由意图提供方在意图执行逻辑中完成
      permissions: ['ohos.permission.GET_WEATHER'],
      parameters: {
        'type': 'object',
        'title': 'Weather Schema',
        'description': 'A schema for getting weather of a location',
        'properties': {
          'location': {
            'type': 'string',
            'description': 'The city and state, e.g. Hangzhou',
            'minLength': 1
          }
        },
        'required': ['location'],
        'additionalProperties': false
      }
    })
    static getWeather(location: string): string {
      // 从全局单例取出调用方信息，进行权限校验
      const callerInfo = CallerInfoStorage.getCallerInfo();
      if (callerInfo === undefined) {
        console.error('caller info is empty');
        throw new Error('caller info is empty');
      }
      // 将调用方Token ID转换为number后，调用checkAccessTokenSync校验调用方权限
      let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
      const tokenID: number = Number(callerInfo.callerTokenId);
      const grantStatus: abilityAccessCtrl.GrantStatus =
        atManager.checkAccessTokenSync(tokenID, 'ohos.permission.GET_WEATHER');
      if (grantStatus !== abilityAccessCtrl.GrantStatus.PERMISSION_GRANTED) {
        console.error('caller is not allowed to execute this intent');
        throw new Error('caller is not allowed to execute this intent');
      }
      // 校验通过，返回意图执行结果
      console.info(`location: ${location}`);
      return 'The current temperature is 24℃';
    }
  }
  ```

## insightIntentProvider.offWillInsightIntentExecute

offWillInsightIntentExecute(callback?: InsightIntentExecutionCallBack): void

注销意图执行监听器。使用callback异步回调。

**起始版本**：26.1.0

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**原子化服务API**：从API版本26.1.0开始，该接口支持在原子化服务中使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | [InsightIntentExecutionCallBack](#insightintentexecutioncallback) | 否 | 意图执行前触发的回调。传入回调时注销该回调对应的监听器，不传入时默认注销所有意图执行监听器。 |

**示例：**

  ```ts
  import { AbilityConstant, UIAbility, Want, insightIntent, insightIntentProvider } from '@kit.AbilityKit';

  export default class EntryAbility extends UIAbility {
    private executionCallBack: insightIntentProvider.InsightIntentExecutionCallBack = {
      onWillInsightIntentExecuteCallBack: (executionInfo: insightIntent.InsightIntentExecutionInfo) => {
        console.info(`intentName: ${executionInfo.intentName}`);
      }
    };

    onDestroy(): void {
      // 在Ability销毁时注销监听器，避免内存泄漏
      // 若传入已注册的callback，则仅注销该callback对应的监听器
      insightIntentProvider.offWillInsightIntentExecute(this.executionCallBack);
      // 若不传callback，则注销所有意图执行监听器
      insightIntentProvider.offWillInsightIntentExecute();
    }
  }
  ```