# off

## Modules to Import

```TypeScript
import { continueManager } from '@kit.AbilityKit';
```

## off('prepareContinue')

```TypeScript
function off(type: 'prepareContinue', context: Context, callback?: AsyncCallback<ContinueResultInfo>): void
```

Unregisters the callback used to obtain the quick start result when an application is launched quickly. This API uses an asynchronous callback to return the result.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'prepareContinue' | Yes | The value is fixed at **prepareContinue**. |
| context | [Context](arkts-ability-context-c.md) | Yes | Context of the ability. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ContinueResultInfo](arkts-ability-continuemanager-continueresultinfo-i.md)&gt; | No | Callback used to return the result. If the callback is unregistered, **err** is undefined, and **ContinueResultInfo** is the callback unregistration result. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [16300501](../errorcode-DistributedSchedule.md#16300501-the-system-ability-works-abnormally) | the system ability work abnormally. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want, continueManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG: string = '[MigrationAbility]';
const DOMAIN_NUMBER: number = 0xFF00;

export default class MigrationAbility extends UIAbility {

    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        hilog.info(DOMAIN_NUMBER, TAG, '%{public}s', 'Ability onCreate');

        // 1. Quick start is configured. Trigger the lifecycle callback when the application is launched immediately.
        if (launchParam.launchReason === AbilityConstant.LaunchReason.PREPARE_CONTINUATION) {
            // Unregister the callback used to obtain the quick start result.
            try {
              continueManager.off('prepareContinue', this.context, (err, continueResultInfo) => {
                if (err.code != 0) {
                  hilog.error(DOMAIN_NUMBER, TAG, 'unregister failed, cause: %{public}s', JSON.stringify(err));
                  return;
                }
                hilog.info(DOMAIN_NUMBER, TAG, 'unregister finished, %{public}s', JSON.stringify(continueResultInfo));
              });
            } catch (e) {
              hilog.error(DOMAIN_NUMBER, TAG, 'unregister failed, cause: %{public}s', JSON.stringify(e));
            }
            // If the application migration data is large, add a loading page here (displaying a loading indicator, etc.).
            // Handle issues such as custom application redirection and timing.
            // ...
        }
    }
}
```
