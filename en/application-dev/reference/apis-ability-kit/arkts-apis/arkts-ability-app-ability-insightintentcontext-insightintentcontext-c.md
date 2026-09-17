# InsightIntentContext

The module provides the context for intent execution. It is used as a property in both the [intent execution base class](arkts-ability-app-ability-insightintentexecutor-insightintentexecutor-c.md) and [base class decorated with @InsightIntentEntry](arkts-ability-app-ability-insightintententryexecutor-insightintententryexecutor-c.md), offering essential capabilities for intent implementation, for example, starting [UIAbility components](arkts-ability-app-ability-uiability-uiability-c.md) within the same application.

**Since:** 11

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { InsightIntentContext } from '@kit.AbilityKit';
```

## setReturnModeForUIAbilityForeground

```TypeScript
setReturnModeForUIAbilityForeground(returnMode: insightIntent.ReturnMode): void
```

Sets the return mode of the intent execution result. This API is applicable to intents with the execution mode set to [UI_ABILITY_FOREGROUND](arkts-ability-insightintent-executemode-e.md).

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| returnMode | [insightIntent.ReturnMode](arkts-ability-insightintent-returnmode-e.md) | Yes | Return mode of the intent execution result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. Possible causes: 1.The context is not insightIntentContext; 2.The context is not for UIAbility foreground insight intent execute mode. |

**Examples**

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
      this.context.setReturnModeForUIAbilityForeground(insightIntent.ReturnMode.FUNCTION);
    } catch (error) {
      const err: BusinessError = error as BusinessError;
      console.error(`Failed to setReturnModeForUIAbilityForeground. Code: ${err.code}, message: ${err.message}`);
    }

    let localStorageData: Record<string, number> = {
      'insightId': this.context.instanceId,
    };
    let storage: LocalStorage = new LocalStorage(localStorageData);
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

## setReturnModeForUIExtensionAbility

```TypeScript
setReturnModeForUIExtensionAbility(returnMode: insightIntent.ReturnMode): void
```

Sets the return mode of the intent execution result. This API is applicable to intents with the execution mode set to [UI_EXTENSION_ABILITY](arkts-ability-insightintent-executemode-e.md).

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| returnMode | [insightIntent.ReturnMode](arkts-ability-insightintent-returnmode-e.md) | Yes | Return mode of the intent execution result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. Possible causes: 1.The context is not insightIntentContext; 2.The context is not for UIExtensionAbility insight intent execute mode. |

**Examples**

```TypeScript
import { InsightIntentExecutor, insightIntent, UIExtensionContentSession } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

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
      let code = (error as BusinessError).code;
      let msg = (error as BusinessError).message;
      console.error(`testTag setReturnModeForUIExtensionAbility fail, error code: ${code}, error msg: ${msg}.`);
    }

    try {
      let localStorageData: Record<string, number> = {
        'insightId': this.context.instanceId,
      };
      let storage: LocalStorage = new LocalStorage(localStorageData);
      storage.setOrCreate('session', pageLoader);
      pageLoader.loadContent('pages/UIExtensionPage', storage);
    } catch (err) {
      const error: BusinessError = err as BusinessError;
      console.error(`Failed to loadContent. Code: ${error.code}, message: ${error.message}`);
    }
    return result;
  }
}
```

## startAbility

```TypeScript
startAbility(want: Want, callback: AsyncCallback<void>): void
```

Starts a UIAbility. This API can only be used to start UIAbility components within the same application. This API uses an asynchronous callback to return the result.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information for starting the UIAbility. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-ability-start-or-stop-failure-in-wukong-mode) | An ability cannot be started or stopped in Wukong mode. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000012](../errorcode-ability.md#16000012-application-under-control) | The application is controlled. |
| [16000013](../errorcode-ability.md#16000013-application-controlled-by-edm) | The application is controlled by EDM. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-ability-not-in-the-foreground) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-installation-free-timeout) | Installation-free timed out. |
| [16000061](../errorcode-ability.md#16000061-unsupported-operation) | Operation not supported. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | The caller has been released. |

**Examples**

```TypeScript
import { InsightIntentExecutor, insightIntent, Want } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class IntentExecutorImpl extends InsightIntentExecutor {
  onExecuteInUIAbilityForegroundMode(name: string, param: Record<string, Object>,
    pageLoader: window.WindowStage): insightIntent.ExecuteResult {
    let want: Want = {
      bundleName: 'com.ohos.intentExecuteDemo', // This is only an example. Replace it with the actual bundle name in real development.
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
      const err: BusinessError = error as BusinessError;
      console.error(`Failed to start ability. Code: ${err.code}, message: ${err.message}`);
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

```TypeScript
import { InsightIntentExecutor, insightIntent, Want } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class IntentExecutorImpl extends InsightIntentExecutor {
  async onExecuteInUIAbilityForegroundMode(name: string, param: Record<string, Object>,
    pageLoader: window.WindowStage): Promise<insightIntent.ExecuteResult> {
    let want: Want = {
      bundleName: 'com.ohos.intentExecuteDemo', // This is only an example. In actual use, developers need to replace it with the real bundle name.
      moduleName: 'entry',
      abilityName: 'AnotherAbility',
    };

    try {
      await this.context.startAbility(want);
      hilog.info(0x0000, 'testTag', '%{public}s', 'Start ability finished');
    } catch (error) {
      const err: BusinessError = error as BusinessError;
      console.error(`Failed to start ability. Code: ${err.code}, message: ${err.message}`);
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

## startAbility

```TypeScript
startAbility(want: Want): Promise<void>
```

Starts a UIAbility. This API can only be used to start UIAbility components within the same application. This API uses a promise to return the result.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information for starting the UIAbility. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-ability-start-or-stop-failure-in-wukong-mode) | An ability cannot be started or stopped in Wukong mode. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000012](../errorcode-ability.md#16000012-application-under-control) | The application is controlled. |
| [16000013](../errorcode-ability.md#16000013-application-controlled-by-edm) | The application is controlled by EDM. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-ability-not-in-the-foreground) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-installation-free-timeout) | Installation-free timed out. |
| [16000061](../errorcode-ability.md#16000061-unsupported-operation) | Operation not supported. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | The caller has been released. |

**Examples**

See [startAbility](#startability)

## instanceId

```TypeScript
instanceId: number
```

Unique ID of an intent instance. Its execution result can be returned through [insightIntentProvider.sendExecuteResult] [sendExecuteResult](arkts-ability-insightintentprovider-sendexecuteresult-f.md) and [insightIntentProvider.sendIntentResult] [sendIntentResult](arkts-ability-insightintentprovider-sendintentresult-f.md).

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
