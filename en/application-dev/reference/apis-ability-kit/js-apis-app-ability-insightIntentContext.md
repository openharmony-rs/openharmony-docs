# @ohos.app.ability.InsightIntentContext (Intent Execution Context)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @linjunjie6-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

The module provides the context for intent execution. It is used as a property in both the [intent execution base class](./js-apis-app-ability-insightIntentExecutor.md) and [base class decorated with @InsightIntentEntry](./js-apis-app-ability-InsightIntentEntryExecutor.md), offering essential capabilities for intent implementation, for example, starting [UIAbility components](./js-apis-app-ability-uiAbility.md) within the same application.

> **NOTE**
>
> The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { InsightIntentContext } from '@kit.AbilityKit';
```

## Properties

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| instanceId<sup>23+</sup> | number | No| No| Unique ID of an intent instance. Its execution result can be returned through [insightIntentProvider.sendExecuteResult](./js-apis-app-ability-insightIntentProvider.md#insightintentprovidersendexecuteresult) and [insightIntentProvider.sendIntentResult](./js-apis-app-ability-insightIntentProvider.md#insightintentprovidersendintentresult).|

**Example**

  ```ts
  import { InsightIntentExecutor, insightIntent, insightIntentProvider } from '@kit.AbilityKit';
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
        // Return the intent execution result using the unique ID of the intent instance.
        insightIntentProvider.sendExecuteResult(this.context.instanceId, result)
          .then(() => {
            console.info('testTag setExecuteResult success');
          })
          .catch((error: BusinessError) => {
            console.error('testTag setExecuteResult fail1, error code: ${JSON.stringify(error)}');
          });
      } catch (e) {
        let code = (e as BusinessError).code;
        let msg = (e as BusinessError).message;
        console.error('testTag setExecuteResult fail2, error code: ${JSON.stringify(code)}, error msg: ${JSON.stringify(msg)}');
      }
      return result;
    }
  }
  ```

## InsightIntentContext.startAbility

startAbility(want: Want, callback: AsyncCallback\<void\>): void

Starts a UIAbility. This API can only be used to start UIAbility components within the same application. This API uses an asynchronous callback to return the result.

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes| Want information for starting the UIAbility.|
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
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

**Example**

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

Starts a UIAbility. This API can only be used to start UIAbility components within the same application. This API uses a promise to return the result.

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes| Want information for starting the UIAbility.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
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

**Example**

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

## InsightIntentContext.setReturnModeForUIAbilityForeground<sup>23+</sup>

setReturnModeForUIAbilityForeground(returnMode: insightIntent.ReturnMode): void

Sets the return mode of the intent execution result. This API is applicable to intents with the execution mode set to [UI_ABILITY_FOREGROUND](./js-apis-app-ability-insightIntent.md#executemode).

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| returnMode | [insightIntent.ReturnMode](./js-apis-app-ability-insightIntent.md#returnmode23) | Yes| Return mode of the intent execution result.|

**Error codes**

For details about the error codes, see [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| -------- | -------- |
| 16000011      | The context does not exist. Possible causes: 1.The context is not insightIntentContext; 2.The context is not for UIAbility foreground insight intent execute mode. |

**Example**

  ```ts
  import { InsightIntentExecutor, insightIntent } from '@kit.AbilityKit';
  import { window } from '@kit.ArkUI';
  import { hilog } from '@kit.PerformanceAnalysisKit';
  
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
        this.context.setReturnModeForUIAbilityForeground(insightIntent.ReturnMode.FUNCTION);
      } catch (error) {
        console.error('testTag setReturnModeForUIAbilityForeground fail, error code: ${JSON.stringify(error)}');
      }
  
      let localStorageData: Record<string, number> = {
        'insightId': this.context.instanceId,
      };
      let storage: LocalStorage = new LocalStorage(localStorageData);
      pageLoader.loadContent('pages/UiabilityIndex', storage, (err, data) => {
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

## InsightIntentContext.setReturnModeForUIExtensionAbility<sup>23+</sup>

setReturnModeForUIExtensionAbility(returnMode: insightIntent.ReturnMode): void

Sets the return mode of the intent execution result. This API is applicable to intents with the execution mode set to [UI_EXTENSION_ABILITY](./js-apis-app-ability-insightIntent.md#executemode).

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| returnMode | [insightIntent.ReturnMode](./js-apis-app-ability-insightIntent.md#returnmode23) | Yes| Return mode of the intent execution result.|

**Error codes**

For details about the error codes, see [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| -------- | -------- |
| 16000011      | The context does not exist. Possible causes: 1.The context is not insightIntentContext; 2.The context is not for UIExtensionAbility insight intent execute mode. |

**Example**

  ```ts
  import { InsightIntentExecutor, insightIntent, UIExtensionContentSession } from '@kit.AbilityKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  export default class InsightIntentExecutorUI extends InsightIntentExecutor {
    onExecuteInUIExtensionAbility(name: string, param: Record<string, Object>,
      pageLoader: UIExtensionContentSession): insightIntent.ExecuteResult {
      hilog.info(0x0000, 'testTag', 'onExecuteInUIExtensionAbility %{public}s', name);
      let result: insightIntent.ExecuteResult;
      result = {
        code: 0,
        result: {
          message: 'Unsupported insight intent.',
        },
      };
      try {
        this.context.setReturnModeForUIExtensionAbility(insightIntent.ReturnMode.FUNCTION)
      } catch (error) {
        console.error('testTag setReturnModeForUIExtensionAbility fail, error code: ${JSON.stringify(error)}');
      }

      try {
        let localStorageData: Record<string, number> = {
          'insightId': this.context.instanceId,
        };
        let storage: LocalStorage = new LocalStorage(localStorageData);
        storage.setOrCreate('session', pageLoader);
        pageLoader.loadContent('pages/UiextensionPage', storage);
      } catch (err) {
        console.log('testTag loadContent error: ' + JSON.stringify(err));
      }
      return result;
    }
  }
  ```
