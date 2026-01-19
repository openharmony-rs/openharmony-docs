# @ohos.app.ability.insightIntentProvider (Intent Provider Management)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @linjunjie6-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

This module provides management capabilities for intent providers, such as proactively sending the execution result of a specified intent.
> **NOTE**
>
> The initial APIs of this module are supported since API version 23. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { insightIntentProvider } from '@kit.AbilityKit';
```

## insightIntentProvider.sendExecuteResult

sendExecuteResult(instanceId: number, result: insightIntent.ExecuteResult): Promise&lt;void&gt;

If an intent provider needs to proactively send the execution result of an intent at a specific point in the service process, it can first set the [return mode of the intent execution result](./js-apis-app-ability-insightIntent.md#returnmode23) to **FUNCTION** by calling [setReturnModeForUIAbilityForeground](./js-apis-app-ability-insightIntentContext.md#insightintentcontextsetreturnmodeforuiabilityforeground23) or [setReturnModeForUIExtensionAbility](./js-apis-app-ability-insightIntentContext.md#insightintentcontextsetreturnmodeforuiextensionability23). Then, it can call this API to send the intent execution result. This is applicable for [configuration-type intents](../../application-models/insight-intent-config-development.md). Proactively sends the intent execution result. This API uses a promise to return the result.<br>
After setting the [return mode of the intent execution result](./js-apis-app-ability-insightIntent.md#returnmode23) to **FUNCTION**, the application no longer needs to return the intent execution result through the return value of [onExecuteInUIAbilityForegroundMode](./js-apis-app-ability-insightIntentExecutor.md#onexecuteinuiabilityforegroundmode) or [onExecuteInUIExtensionAbility](./js-apis-app-ability-insightIntentExecutor.md#onexecuteinuiextensionability).

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | [instanceId](./js-apis-app-ability-insightIntentContext.md#properties)| number | Yes| Unique ID of an intent instance.|
  | result | [insightIntent.ExecuteResult](js-apis-app-ability-insightIntent.md#executeresult) | Yes| Intent execution result, representing the data returned to the system entry for this intent execution.|

**Return value**

| Type            | Description             |
| -------------- | --------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| -------- | -------- |
| 16000003      | The specified ID does not exist. |
| 16000050      | Internal error. Possible causes: 1. Connect to system service failed; 2.Send restart message to system service failed; 3.System service failed to communicate with dependency module. |

**Example**

Below is an example of setting the return mode of the intent execution result to **FUNCTION**.
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
      // Set the return mode of the intent execution result to FUNCTION.
      this.context.setReturnModeForUIAbilityForeground(insightIntent.ReturnMode.FUNCTION);
    } catch (error) {
      let code = (error as BusinessError).code;
      let msg = (error as BusinessError).message;
      console.error(`testTag setReturnModeForUIExtensionAbility fail, error code: ${code}, error msg: ${msg}.`);
    }
    // Pass the intent instance ID to the target page through localStorage.
    let localStorageData: Record<string, number> = {
      'insightId': this.context.instanceId,
    };
    let storage: LocalStorage = new LocalStorage(localStorageData);
    // Load the page through pageLoader.
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

Below is an example of proactively sending the intent execution result.
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
                console.info('testTag setExecuteResult success');
              })
              .catch((error: BusinessError) => {
                console.error(`testTag setExecuteResult fail1, error code: ${error.code}, error msg: ${error.message}.`);
              });
          } catch (e) {
            let code = (e as BusinessError).code;
            let msg = (e as BusinessError).message;
            console.error(`testTag setExecuteResult fail2, error code: ${code}, error msg: ${msg}`);
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

If an intent provider needs to proactively send the execution result of an intent at a specific point in the service process, it can first set the [return mode of the intent execution result](./js-apis-app-ability-insightIntent.md#returnmode23) to **FUNCTION** by calling [setReturnModeForUIAbilityForeground](./js-apis-app-ability-insightIntentContext.md#insightintentcontextsetreturnmodeforuiabilityforeground23) or [setReturnModeForUIExtensionAbility](./js-apis-app-ability-insightIntentContext.md#insightintentcontextsetreturnmodeforuiextensionability23). Then, it can call this API to send the intent execution result. This is applicable for [intents decorated](../../application-models/insight-intent-decorator-development.md) with [@InsightIntentEntry](./js-apis-app-ability-InsightIntentDecorator.md#insightintententry). Proactively sends the intent execution result. This API uses a promise to return the result.<br>
After setting the [return mode of the intent execution result](./js-apis-app-ability-insightIntent.md#returnmode23) to **FUNCTION**, the application no longer needs to return the intent execution result through the return value of [onExecute](./js-apis-app-ability-InsightIntentEntryExecutor.md#onexecute).

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | [instanceId](./js-apis-app-ability-insightIntentContext.md#properties)| number | Yes| Unique ID of an intent instance.|
  | result | [insightIntent.IntentResult](js-apis-app-ability-insightIntent.md#intentresultt20) | Yes| Intent execution result, representing the data returned to the system entry for this intent execution.|

**Return value**

| Type            | Description             |
| -------------- | --------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| -------- | -------- |
| 16000003      | The specified ID does not exist. |
| 16000050      | Internal error. Possible causes: 1. Connect to system service failed; 2.Send restart message to system service failed; 3.System service failed to communicate with dependency module. |

**Example**

Below is an example of setting the return mode of the intent execution result to **FUNCTION**.
```ts
import { insightIntent, InsightIntentEntry, InsightIntentEntryExecutor } from '@kit.AbilityKit';

class PlayVideoResultDef {
  resultCode: number = 0;
  resultMsg: string = '';
  someInvalid1: string | undefined = undefined;
  someInvalid2: string | null = null;
}

// Play the video.
@InsightIntentEntry({
  intentName: 'PlayVideo',
  domain: 'VideosDomain',
  intentVersion: '1.0.2',
  displayName: 'Play video',
  displayDescription: 'Intent to play video',
  schema: 'PlayVideo',
  icon: $r('app.media.background'),
  llmDescription: 'Intent to play video',
  keywords: ['Video playback', 'Play video', 'PlayVideo'],
  abilityName: 'EntryAbility1',
  executeMode: [insightIntent.ExecuteMode.UI_ABILITY_FOREGROUND],
})
export default class PlayVideo extends InsightIntentEntryExecutor<PlayVideoResultDef> {
  entityId: string = 'zhz';
  episodeId: string = '50';
  episodeNumber: number = 12;

  onExecute(): Promise<insightIntent.IntentResult<PlayVideoResultDef>> {
    console.log('testTag', 'PlayVideo onExecute success')
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
      // Set the return mode of the intent execution result to FUNCTION.
      this.context.setReturnModeForUIAbilityForeground(insightIntent.ReturnMode.FUNCTION);
      console.info('testTag: setReturnModeForUIAbilityForeground success');
    } catch (error) {
      let code = (error as BusinessError).code;
      let msg = (error as BusinessError).message;
      console.error(`testTag: setReturnModeForUIAbilityForeground faild, error code: ${code}, error msg: ${msg}.`);
    }

    try {
      // Pass the intent instance ID to the target page through localStorage.
      let localStorageData: Record<string, number> = {
        'insightId': instanceId,
      };
      let storage: LocalStorage = new LocalStorage(localStorageData);
      // Load the page through pageLoader.
      this.windowStage?.loadContent('pages/Index', storage);
      console.log('testTag', 'Succeeded in loading the content1')
    } catch (err) {
      let code = (err as BusinessError).code;
      let msg = (err as BusinessError).message;
      console.log(`testTag loadContent error code: ${code}, error msg: ${msg}.`);
    }
    return Promise.resolve(result);
  }
}
```

Below is an example of proactively sending the intent execution result.
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
      // Return the intent execution result using the sendExecuteResult API.
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
