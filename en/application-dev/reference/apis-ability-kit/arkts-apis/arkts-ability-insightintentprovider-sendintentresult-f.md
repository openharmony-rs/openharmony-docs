# sendIntentResult

## Modules to Import

```TypeScript
import { insightIntentProvider } from '@kit.AbilityKit';
```

## sendIntentResult

```TypeScript
function sendIntentResult(instanceId: number, result: insightIntent.IntentResult<T>): Promise<void>
```

If an intent provider needs to proactively send the execution result of an intent at a specific point in the service process, it can first set the [return mode](arkts-ability-insightintent-returnmode-e.md) of the intent execution result to FUNCTION through [setReturnModeForUIAbilityForeground](arkts-ability-app-ability-insightintentcontext-insightintentcontext-c.md#setreturnmodeforuiabilityforeground) or [setReturnModeForUIExtensionAbility](arkts-ability-app-ability-insightintentcontext-insightintentcontext-c.md#setreturnmodeforuiextensionability), and then call this API to send the intent execution result. This API applies to [decorator-type intents](../../../application-models/insight-intent-decorator-development.md) decorated by [@InsightIntentEntry](arkts-ability-app-ability-insightintentdecorator-insightintententry-d.md#insightintententry). This API uses a promise to return the result asynchronously.

After the [return mode](arkts-ability-insightintent-returnmode-e.md) of the intent execution result is set to FUNCTION, the application no longer needs to return the intent execution result through the return value of the onExecute API.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-insightIntentProvider-function sendIntentResult(instanceId: int, result: insightIntent.IntentResult<T>): Promise<void>--><!--Device-insightIntentProvider-function sendIntentResult(instanceId: int, result: insightIntent.IntentResult<T>): Promise<void>-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| instanceId | number | Yes | Unique ID of an intent instance. |
| result | [insightIntent.IntentResult](arkts-ability-insightintent-intentresult-i.md)&lt;T&gt; | Yes | Execution result of the return intent, indicating the data returned to the system entry by this intent execution. |

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
import { insightIntent, InsightIntentEntry, InsightIntentEntryExecutor } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

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
      // Set the return mode of the intent execution result to FUNCTION.
      this.context.setReturnModeForUIAbilityForeground(insightIntent.ReturnMode.FUNCTION);
      console.info('testTag: setReturnModeForUIAbilityForeground success');
    } catch (error) {
      let code = (error as BusinessError).code;
      let msg = (error as BusinessError).message;
      console.error(`testTag: setReturnModeForUIAbilityForeground failed, error code: ${code}, error msg: ${msg}.`);
    }

    try {
      // Pass the intent instance ID to the target page through localStorage.
      let localStorageData: Record<string, number> = {
        'insightId': instanceId,
      };
      let storage: LocalStorage = new LocalStorage(localStorageData);
      // Load the page through pageLoader.
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

Below is an example of proactively sending the intent execution result.

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
      // Proactively return the intent execution result through the sendIntentResult API.
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
