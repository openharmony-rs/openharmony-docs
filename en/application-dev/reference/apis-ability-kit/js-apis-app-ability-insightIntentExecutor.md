# @ohos.app.ability.InsightIntentExecutor (Base Class for Intent Execution)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @linjunjie6-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=b3bc27a342923ac4fafa55153b55c4f3b627330f translatedAt=2026-09-03T10:22:12.982Z pushedAt=2026-09-05T10:47:30.403Z -->

The module provides the base class for intent execution. You can use this module to interface with the [InsightIntent framework](../../application-models/insight-intent-overview.md) on the device side and implement intent service logic through [configuration files](../../application-models/insight-intent-config-development.md).

In addition to developing intents via configuration files, intents can also be developed using decorators. For API version 20 and later, you are advised to [develop intents using decorators](../../application-models/insight-intent-decorator-development.md).

> **NOTE**
>
> The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { InsightIntentExecutor } from '@kit.AbilityKit';
```

## InsightIntentExecutor

Base class for intent execution.

### Properties

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name| Type| Read-only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| context | [InsightIntentContext](./js-apis-app-ability-insightIntentContext.md) | No| No| Context for intent execution.|

### onExecuteInUIAbilityForegroundMode

onExecuteInUIAbilityForegroundMode(name: string, param: Record<string, Object>, pageLoader: window.WindowStage): insightIntent.ExecuteResult | Promise<insightIntent.ExecuteResult>

Called during the UIAbility lifecycle when the [UIAbility](./js-apis-app-ability-uiAbility.md) that the intent execution depends on is started in the foreground. Both synchronous calls and asynchronous calls using Promise are supported.

- If the UIAbility is cold started, the UIAbility lifecycle callbacks are triggered in the following sequence during intent execution: [onCreate](./js-apis-app-ability-uiAbility.md#oncreate), [onWindowStageCreate](./js-apis-app-ability-uiAbility.md#onwindowstagecreate), onExecuteInUIAbilityForegroundMode, and [onForeground](./js-apis-app-ability-uiAbility.md#onforeground).
- If the UIAbility is hot started in the background, the UIAbility lifecycle callbacks are triggered in the following sequence during intent execution: [onNewWant](./js-apis-app-ability-uiAbility.md#onnewwant), onExecuteInUIAbilityForegroundMode, and [onForeground](./js-apis-app-ability-uiAbility.md#onforeground).
- If the UIAbility is hot started in the foreground, the UIAbility lifecycle callbacks are triggered in the following sequence during intent execution: onExecuteInUIAbilityForegroundMode.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| name | string | Yes| Intent name.|
| param | Record<string, Object> | Yes| Intent parameter, which is the data passed from the system entry point to the application for this intent execution.|
| pageLoader | [window.WindowStage](../apis-arkui/arkts-apis-window-WindowStage.md) | Yes | WindowStage instance object, which is the same as the windowStage instance of the [onWindowStageCreate](./js-apis-app-ability-uiAbility.md#onwindowstagecreate) interface. It loads the page for intent execution by calling its loadContent method, with the page path string as the parameter. |

**Return value**

| Type| Description|
| -------- | -------- |
| [insightIntent.ExecuteResult](./js-apis-app-ability-insightIntent.md#executeresult) \| Promise<[insightIntent.ExecuteResult](./js-apis-app-ability-insightIntent.md#executeresult)> | Intent execution result, or a Promise object carrying the intent execution result, which represents the data returned to the system entry by this intent execution. |

**Example**

The code snippet below shows the synchronous call that returns the intent execution result:
  ```ts
  import { InsightIntentExecutor, insightIntent } from '@kit.AbilityKit';
  import { window } from '@kit.ArkUI';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  export default class IntentExecutorImpl extends InsightIntentExecutor {
    onExecuteInUIAbilityForegroundMode(name: string, param: Record<string, Object>,
      pageLoader: window.WindowStage): insightIntent.ExecuteResult {
      let result: insightIntent.ExecuteResult;
      if (name !== 'SupportedInsightIntentName') {
        hilog.warn(0x0000, 'testTag', 'Unsupported insight intent %{public}s', name);
        result = {
          // Defined by the developer.
          code: 404,
          result: {
            message: 'Unsupported insight intent.',
          }
        };
        return result;
      }

      // If the developer needs to load the intent content, pages/IntentPage is the intent page.
      pageLoader.loadContent('pages/IntentPage', (err, data) => {
        if (err.code) {
          hilog.error(0x0000, 'testTag', `Failed to load the content. Code: ${err.code}, message: ${err.message}`);
        } else {
          hilog.info(0x0000, 'testTag', '%{public}s', 'Succeeded in loading the content');
        }
      });

      result = {
        code: 0,
        result: {
          message: 'Execute insight intent succeed.',
        }
      };
      return result;
    }
  }
  ```

The code snippet below shows the promise-based asynchronous call that returns the intent execution result:
  ```ts
  import { InsightIntentExecutor, insightIntent } from '@kit.AbilityKit';
  import { window } from '@kit.ArkUI';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  async function executeInsightIntent(param: Record<string, Object>): Promise<insightIntent.ExecuteResult> {
    return new Promise((resolve, reject) => {
      let result: insightIntent.ExecuteResult = {
        code: 0,
        result: {
          message: 'Execute insight intent succeed.',
        }
      };
      resolve(result);
    })
  }

  export default class IntentExecutorImpl extends InsightIntentExecutor {
    // Use the async/await syntax to implement an asynchronous interface, and declare the interface as an asynchronous function with async.
    async onExecuteInUIAbilityForegroundMode(name: string, param: Record<string, Object>,
      pageLoader: window.WindowStage): Promise<insightIntent.ExecuteResult> {
      let result: insightIntent.ExecuteResult;
      if (name !== 'SupportedInsightIntentName') {
        hilog.warn(0x0000, 'testTag', 'Unsupported insight intent %{public}s', name);
        result = {
          // Defined by the developer.
          code: 404,
          result: {
            message: 'Unsupported insight intent.',
          }
        };
        return result;
      }

      result = await executeInsightIntent(param);
      return result;
    }
  }
  ```

### onExecuteInUIAbilityBackgroundMode

onExecuteInUIAbilityBackgroundMode(name: string, param: Record<string, Object>): insightIntent.ExecuteResult | Promise<insightIntent.ExecuteResult>

Called during the UIAbility lifecycle when the [UIAbility](./js-apis-app-ability-uiAbility.md) that the intent execution depends on is started in the background. Both synchronous calls and asynchronous calls using Promise are supported.

- If the UIAbility is cold started, the UIAbility lifecycle callbacks are triggered in the following sequence during intent execution: [onCreate](./js-apis-app-ability-uiAbility.md#oncreate), onExecuteInUIAbilityBackgroundMode, and [onBackground](./js-apis-app-ability-uiAbility.md#onbackground).
- If the UIAbility is hot started, the UIAbility lifecycle callbacks are triggered in the following sequence during intent execution: onExecuteInUIAbilityBackgroundMode.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| name | string | Yes| Intent name.|
| param | Record<string, Object> | Yes| Intent parameter, which is the data passed from the system entry point to the application for this intent execution.|

**Return value**

| Type| Description|
| -------- | -------- |
| [insightIntent.ExecuteResult](./js-apis-app-ability-insightIntent.md#executeresult) \| Promise<[insightIntent.ExecuteResult](./js-apis-app-ability-insightIntent.md#executeresult)> | Intent execution result or a Promise object carrying the intent execution result, indicating the data returned to the system entry for this intent execution. |

**Example**

The code snippet below shows the synchronous call that returns the intent execution result:
  ```ts
  import { InsightIntentExecutor, insightIntent } from '@kit.AbilityKit';

  export default class IntentExecutorImpl extends InsightIntentExecutor {
    onExecuteInUIAbilityBackgroundMode(name: string, param: Record<string, Object>): insightIntent.ExecuteResult {
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

The code snippet below shows the promise-based asynchronous call that returns the intent execution result:
  ```ts
  import { InsightIntentExecutor, insightIntent } from '@kit.AbilityKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  async function executeInsightIntent(param: Record<string, Object>): Promise<insightIntent.ExecuteResult> {
    return new Promise((resolve, reject) => {
      let result: insightIntent.ExecuteResult = {
        code: 0,
        result: {
          message: 'Execute insight intent succeed.',
        }
      };
      resolve(result);
    })
  }

  export default class IntentExecutorImpl extends InsightIntentExecutor {
    // Use the async/await syntax sugar to implement an asynchronous interface, and declare the interface as an asynchronous function with async.
    async onExecuteInUIAbilityBackgroundMode(name: string,
      param: Record<string, Object>): Promise<insightIntent.ExecuteResult> {
      let result: insightIntent.ExecuteResult;
      if (name !== 'SupportedInsightIntentName') {
        hilog.warn(0x0000, 'testTag', 'Unsupported insight intent %{public}s', name);
        result = {
          code: 404,
          result: {
            message: 'Unsupported insight intent.',
          }
        };
        return result;
      }
      result = await executeInsightIntent(param);
      return result;
    }
  }
  ```

### onExecuteInUIExtensionAbility

onExecuteInUIExtensionAbility(name: string, param: Record<string, Object>, pageLoader: UIExtensionContentSession): insightIntent.ExecuteResult | Promise<insightIntent.ExecuteResult>

Called during the UIExtensionAbility lifecycle when the [UIExtensionAbility](./js-apis-app-ability-uiExtensionAbility.md) that the intent execution depends on is started. Both synchronous calls and asynchronous calls using Promise are supported.

- The UIExtensionAbility lifecycle callbacks are triggered in the following sequence during intent execution: [onCreate](./js-apis-app-ability-uiExtensionAbility.md#oncreate), [onSessionCreate](./js-apis-app-ability-uiExtensionAbility.md#onsessioncreate), onExecuteInUIExtensionAbility, and [onForeground](./js-apis-app-ability-uiExtensionAbility.md#onforeground).

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| name | string | Yes| Intent name.|
| param | Record<string, Object> | Yes| Intent parameter, which is the data passed from the system entry point to the application for this intent execution.|
| pageLoader | [UIExtensionContentSession](./js-apis-app-ability-uiExtensionContentSession.md) | Yes | UIExtensionContentSession instance, which is the same as the UIExtensionContentSession instance of the [onSessionCreate](./js-apis-app-ability-uiExtensionAbility.md#onsessioncreate) API. It can be used to load the page for intent execution. |

**Return value**

| Type| Description|
| -------- | -------- |
| [insightIntent.ExecuteResult](./js-apis-app-ability-insightIntent.md#executeresult) \| Promise<[insightIntent.ExecuteResult](./js-apis-app-ability-insightIntent.md#executeresult)> | Intent execution result or a Promise object carrying the intent execution result, indicating the data returned to the system entry for this intent execution. |

**Example**

The code snippet below shows the synchronous call that returns the intent execution result:
  ```ts
  import { InsightIntentExecutor, insightIntent, UIExtensionContentSession } from '@kit.AbilityKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  export default class IntentExecutorImpl extends InsightIntentExecutor {
    onExecuteInUIExtensionAbility(name: string, param: Record<string, Object>,
      pageLoader: UIExtensionContentSession): insightIntent.ExecuteResult {
      let result: insightIntent.ExecuteResult;
      if (name !== 'SupportedInsightIntentName') {
        hilog.warn(0x0000, 'testTag', 'Unsupported insight intent %{public}s', name);
        result = {
          // Defined by the developer.
          code: 404,
          result: {
            message: 'Unsupported insight intent.',
          }
        };
        return result;
      }

      // If the developer needs to load intent content, pages/Index is the intent page.
      pageLoader.loadContent('pages/Index');

      result = {
        code: 0,
        result: {
          message: 'Execute insight intent succeed.',
        }
      };
      return result;
    }
  }
  ```

The code snippet below shows the promise-based asynchronous call that returns the intent execution result:
  ```ts
  import { InsightIntentExecutor, insightIntent, UIExtensionContentSession } from '@kit.AbilityKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  async function executeInsightIntent(param: Record<string, Object>): Promise<insightIntent.ExecuteResult> {
    return new Promise((resolve, reject) => {
      let result: insightIntent.ExecuteResult = {
        code: 0,
        result: {
          message: 'Execute insight intent succeed.',
        }
      };
      resolve(result);
    })
  }

  export default class IntentExecutorImpl extends InsightIntentExecutor {
    // Implement the asynchronous interface using the async/await syntax sugar, and declare the interface as an asynchronous function with async.
    async onExecuteInUIExtensionAbility(name: string, param: Record<string, Object>,
      pageLoader: UIExtensionContentSession): Promise<insightIntent.ExecuteResult> {
      let result: insightIntent.ExecuteResult;
      if (name !== 'SupportedInsightIntentName') {
        hilog.warn(0x0000, 'testTag', 'Unsupported insight intent %{public}s', name);
        result = {
          // Defined by the developer.
          code: 404,
          result: {
            message: 'Unsupported insight intent.',
          }
        };
        return result;
      }

      result = await executeInsightIntent(param);
      return result;
    }
  }
  ```

### onExecuteInServiceExtensionAbility

onExecuteInServiceExtensionAbility(name: string, param: Record<string, Object>): insightIntent.ExecuteResult | Promise<insightIntent.ExecuteResult>

Called during the ServiceExtensionAbility lifecycle when the ServiceExtensionAbility that the intent execution depends on is started. Both synchronous calls and asynchronous calls using Promise are supported.

- The ServiceExtensionAbility lifecycle callbacks are triggered in the following sequence during intent execution: **onCreate**, **onRequest**, and **onExecuteInServiceExtensionAbility**.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| name | string | Yes| Intent name.|
| param | Record<string, Object> | Yes| Intent parameter, which is the data passed from the system entry point to the application for this intent execution.|

**Return value**

| Type| Description|
| -------- | -------- |
| [insightIntent.ExecuteResult](./js-apis-app-ability-insightIntent.md#executeresult) \| Promise<[insightIntent.ExecuteResult](./js-apis-app-ability-insightIntent.md#executeresult)> | Intent execution result, or a Promise object carrying the intent execution result, which represents the data returned to the system entry for this intent execution. |

**Example**

The code snippet below shows the synchronous call that returns the intent execution result:
  ```ts
  import { InsightIntentExecutor, insightIntent } from '@kit.AbilityKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  export default class IntentExecutorImpl extends InsightIntentExecutor {
    onExecuteInServiceExtensionAbility(name: string, param: Record<string, Object>): insightIntent.ExecuteResult {
      let result: insightIntent.ExecuteResult;
      if (name !== 'SupportedInsightIntentName') {
        hilog.warn(0x0000, 'testTag', 'Unsupported insight intent %{public}s', name);
        result = {
          // Defined by the developer.
          code: 404,
          result: {
            message: 'Unsupported insight intent.',
          }
        };
        return result;
      }

      result = {
        code: 0,
        result: {
          message: 'Execute insight intent succeed.',
        }
      };
      return result;
    }
  }
  ```

The code snippet below shows the promise-based asynchronous call that returns the intent execution result:
  ```ts
  import { InsightIntentExecutor, insightIntent } from '@kit.AbilityKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  async function executeInsightIntent(param: Record<string, Object>): Promise<insightIntent.ExecuteResult> {
    return new Promise((resolve, reject) => {
      let result: insightIntent.ExecuteResult = {
        code: 0,
        result: {
          message: 'Execute insight intent succeed.',
        }
      };
      resolve(result);
    })
  }

  export default class IntentExecutorImpl extends InsightIntentExecutor {
    // Implement the asynchronous interface using the async/await syntax sugar, and declare the interface as an asynchronous function with async.
    async onExecuteInServiceExtensionAbility(name: string,
      param: Record<string, Object>): Promise<insightIntent.ExecuteResult> {
      let result: insightIntent.ExecuteResult;
      if (name !== 'SupportedInsightIntentName') {
        hilog.warn(0x0000, 'testTag', 'Unsupported insight intent %{public}s', name);
        result = {
          // Defined by the developer.
          code: 404,
          result: {
            message: 'Unsupported insight intent.',
          }
        };
        return result;
      }

      result = await executeInsightIntent(param);
      return result;
    }
  }
  ```