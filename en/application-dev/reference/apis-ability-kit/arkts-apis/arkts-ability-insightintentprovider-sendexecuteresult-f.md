# sendExecuteResult

## Modules to Import

```TypeScript
import { insightIntentProvider } from '@kit.AbilityKit';
```

## sendExecuteResult

```TypeScript
function sendExecuteResult(instanceId: number, result: insightIntent.ExecuteResult): Promise<void>
```

If an intent provider needs to proactively send the execution result of an intent at a specific point in the service process, it can first set the [return mode](arkts-ability-insightintent-returnmode-e.md) of the intent execution result to FUNCTION through [setReturnModeForUIAbilityForeground](arkts-ability-app-ability-insightintentcontext-insightintentcontext-c.md#setreturnmodeforuiabilityforeground) or [setReturnModeForUIExtensionAbility](arkts-ability-app-ability-insightintentcontext-insightintentcontext-c.md#setreturnmodeforuiextensionability), and then call this API to send the intent execution result. This API applies to [configuration-type intents](../../../application-models/insight-intent-config-development.md). This API uses a promise to return the result asynchronously.

After the [return mode](arkts-ability-insightintent-returnmode-e.md) of the intent execution result is set to FUNCTION, the application no longer needs to return the intent execution result through the return value of the [onExecuteInUIAbilityForegroundMode API](arkts-ability-app-ability-insightintentexecutor-insightintentexecutor-c.md#onexecuteinuiabilityforegroundmode) or [onExecuteInUIExtensionAbility](arkts-ability-app-ability-insightintentexecutor-insightintentexecutor-c.md#onexecuteinuiextensionability).

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-insightIntentProvider-function sendExecuteResult(instanceId: int, result: insightIntent.ExecuteResult): Promise<void>--><!--Device-insightIntentProvider-function sendExecuteResult(instanceId: int, result: insightIntent.ExecuteResult): Promise<void>-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| instanceId | number | Yes | Unique ID of an intent instance. |
| result | [insightIntent.ExecuteResult](arkts-ability-insightintent-executeresult-i.md) | Yes | Intent execution result, representing the data returned to the system entry for this intent execution. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [16000003](../errorcode-ability.md#16000003-id-does-not-exist) | The specified ID does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. Possible causes: 1. Connect to system service failed; 2.Send restart message to system service failed; 3.System service failed to communicate with dependency module. |

**Examples**

Below is an example of setting the return mode of the intent execution result to FUNCTION.

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
      // Set the return mode of the intent execution result to FUNCTION.
      this.context.setReturnModeForUIAbilityForeground(insightIntent.ReturnMode.FUNCTION);
    } catch (error) {
      let code = (error as BusinessError).code;
      let msg = (error as BusinessError).message;
      console.error(`testTag setReturnModeForUIAbilityForeground fail, error code: ${code}, error msg: ${msg}.`);
    }
    // Pass the intent instance ID to the target page through localStorage.
    let localStorageData: Record<string, number> = {
      'insightId': this.context.instanceId,
    };
    let storage: LocalStorage = new LocalStorage(localStorageData);
    // Load the page through pageLoader.
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

Below is an example of proactively sending the intent execution result.

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
      // Return the intent execution result using the sendExecuteResult API.
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
