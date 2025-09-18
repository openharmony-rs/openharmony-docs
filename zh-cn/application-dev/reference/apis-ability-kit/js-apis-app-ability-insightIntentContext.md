# @ohos.app.ability.InsightIntentContext (意图执行上下文)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zhangyafei-echo; @linjunjie6-->
<!--Designer: @li-weifeng2-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

本模块提供意图执行上下文，是[意图执行基类](./js-apis-app-ability-insightIntentExecutor.md)和[@InsightIntentEntry的意图执行基类](./js-apis-app-ability-InsightIntentEntryExecutor.md)的属性，为意图执行提供基础能力，例如启动本应用内的[UIAbility组件](./js-apis-app-ability-uiAbility.md)。

> **说明：**
>
> 本模块首批接口从API version 11开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 本模块接口仅可在Stage模型下使用。

## 导入模块

```ts
import { InsightIntentContext } from '@kit.AbilityKit';
```

## InsightIntentContext.startAbility

startAbility(want: Want, callback: AsyncCallback\<void\>): void

启动UIAbility组件，仅支持启动本应用内的UIAbility组件。使用callback异步回调。

**模型约束**：此接口仅可在Stage模型下使用。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | 是 | 启动UIAbility组件的want信息。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当接口调用成功，err为undefined，否则为错误对象。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 16000001 | The specified ability does not exist. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |
| 16000011 | The context does not exist.        |
| 16000012 | The application is controlled.        |
| 16000013 | The application is controlled by EDM.       |
| 16000050 | Internal error. |
| 16000053 | The ability is not on the top of the UI. |
| 16000055 | Installation-free timed out. |
| 16000061 | Operation not supported. |
| 16200001 | The caller has been released. |

**示例：**

  ```ts
  import { InsightIntentExecutor, insightIntent, Want } from '@kit.AbilityKit';
  import { window } from '@kit.ArkUI';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  export default class IntentExecutorImpl extends InsightIntentExecutor {
    onExecuteInUIAbilityForegroundMode(name: string, param: Record<string, Object>,
      pageLoader: window.WindowStage): insightIntent.ExecuteResult {
      let want: Want = {
        bundleName: 'com.ohos.intentExecuteDemo',
        moduleName: 'entry',
        abilityName: 'AnotherAbility',
      };

      try {
        this.context.startAbility(want, (error) => {
          if (error) {
            hilog.error(0x0000, 'testTag', 'Start ability failed with %{public}s', JSON.stringify(error));
          } else {
            hilog.info(0x0000, 'testTag', '%{public}s', 'Start ability succeed');
          }
        })
      } catch (error) {
        hilog.error(0x0000, 'testTag', 'Start ability error caught %{public}s', JSON.stringify(error));
      }

      let result: insightIntent.ExecuteResult = {
        code: 0,
        result: {
          message: 'Execute insight intent succeed.',
        }
      };
      return result;
    }
  }
  ```

## InsightIntentContext.startAbility

startAbility(want: Want): Promise\<void\>

启动UIAbility组件，仅支持启动本应用内的UIAbility组件。使用Promise异步回调。

**模型约束**：此接口仅可在Stage模型下使用。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | 是 | 启动UIAbility组件的want信息。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 16000001 | The specified ability does not exist. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |
| 16000011 | The context does not exist.        |
| 16000012 | The application is controlled.        |
| 16000013 | The application is controlled by EDM.       |
| 16000050 | Internal error. |
| 16000053 | The ability is not on the top of the UI. |
| 16000055 | Installation-free timed out. |
| 16000061 | Operation not supported. |
| 16200001 | The caller has been released. |

**示例：**

  ```ts
  import { InsightIntentExecutor, insightIntent, Want } from '@kit.AbilityKit';
  import { window } from '@kit.ArkUI';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  export default class IntentExecutorImpl extends InsightIntentExecutor {
    async onExecuteInUIAbilityForegroundMode(name: string, param: Record<string, Object>,
      pageLoader: window.WindowStage): Promise<insightIntent.ExecuteResult> {
      let want: Want = {
        bundleName: 'com.ohos.intentExecuteDemo',
        moduleName: 'entry',
        abilityName: 'AnotherAbility',
      };

      try {
        await this.context.startAbility(want);
        hilog.info(0x0000, 'testTag', '%{public}s', 'Start ability finished');
      } catch (error) {
        hilog.error(0x0000, 'testTag', 'Start ability error caught %{public}s', JSON.stringify(error));
      }

      let result: insightIntent.ExecuteResult = {
        code: 0,
        result: {
          message: 'Execute insight intent succeed.',
        }
      };
      return result;
    }
  }
  ```
