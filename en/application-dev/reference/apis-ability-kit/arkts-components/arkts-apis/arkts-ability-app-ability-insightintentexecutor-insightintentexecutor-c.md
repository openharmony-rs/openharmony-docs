# InsightIntentExecutor

```TypeScript
declare class InsightIntentExecutor
```

The module provides the base class for intent execution. You can use this module to interface with the [InsightIntent framework](../../../application-models/insight-intent-overview.md) on the device side and implement intent service logic through [configuration files](../../../application-models/insight-intent-config-development.md). In addition to developing intents via configuration files, intents can also be developed using decorators. For API version 20 and later, you are advised to [develop intents using decorators](../../../application-models/insight-intent-decorator-development.md).

**Since:** 11

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { InsightIntentExecutor } from '@kit.AbilityKit';
```

## onExecuteInServiceExtensionAbility

```TypeScript
onExecuteInServiceExtensionAbility(name: string, param: Record<string, Object>):insightIntent.ExecuteResult | Promise<insightIntent.ExecuteResult>
```

Called during the ServiceExtensionAbility lifecycle when the ServiceExtensionAbility that the intent execution depends on is started. Both synchronous calls and asynchronous calls using Promise are supported.

- The ServiceExtensionAbility lifecycle callbacks are triggered in the following sequence during intent execution:  
**onCreate**, **onRequest**, and **onExecuteInServiceExtensionAbility**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Intent name. |
| param | Record&lt;string, Object&gt; | Yes | Intent parameter, which is the data passed from the system entry point to the application for this intent execution. |

**Return value:**

| Type | Description |
| --- | --- |
| [insightIntent.ExecuteResult](arkts-ability-insightintent-executeresult-i.md) &#124; Promise&lt;[insightIntent.ExecuteResult](arkts-ability-insightintent-executeresult-i.md)&gt; | Intent execution result or a Promise object containing the intent execution result, representing the data returned to the system entry point from this intent execution. |

**Examples**

The code snippet below shows the synchronous call that returns the intent execution result:

```TypeScript
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

```TypeScript
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

## onExecuteInUIAbilityBackgroundMode

```TypeScript
onExecuteInUIAbilityBackgroundMode(name: string, param: Record<string, Object>):insightIntent.ExecuteResult | Promise<insightIntent.ExecuteResult>
```

Called during the UIAbility lifecycle when the [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) that the intent execution depends on is started in the background. Both synchronous calls and asynchronous calls using Promise are supported.

- If the UIAbility is cold started, the UIAbility lifecycle callbacks are triggered in the following sequence  
during intent execution: [onCreate](arkts-ability-app-ability-uiability-uiability-c.md#oncreate), onExecuteInUIAbilityBackgroundMode, and [onBackground](arkts-ability-app-ability-uiability-uiability-c.md#onbackground).  
- If the UIAbility is hot started, the UIAbility lifecycle callbacks are triggered in the following sequence during  
intent execution: onExecuteInUIAbilityBackgroundMode.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Intent name. |
| param | Record&lt;string, Object&gt; | Yes | Intent parameter, which is the data passed from the system entry point to the application for this intent execution. |

**Return value:**

| Type | Description |
| --- | --- |
| [insightIntent.ExecuteResult](arkts-ability-insightintent-executeresult-i.md) &#124; Promise&lt;[insightIntent.ExecuteResult](arkts-ability-insightintent-executeresult-i.md)&gt; | Intent execution result or a Promise object containing the intent execution result, representing the data returned to the system entry point from this intent execution. |

**Examples**

The code snippet below shows the synchronous call that returns the intent execution result:

```TypeScript
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

```TypeScript
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

## onExecuteInUIAbilityForegroundMode

```TypeScript
onExecuteInUIAbilityForegroundMode(name: string, param: Record<string, Object>, pageLoader: window.WindowStage):insightIntent.ExecuteResult | Promise<insightIntent.ExecuteResult>
```

Called during the UIAbility lifecycle when the [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) that the intent execution depends on is started in the foreground. Both synchronous calls and asynchronous calls using Promise are supported.

- If the UIAbility is cold started, the UIAbility lifecycle callbacks are triggered in the following sequence  
during intent execution: [onCreate](arkts-ability-app-ability-uiability-uiability-c.md#oncreate), [onWindowStageCreate](arkts-ability-app-ability-uiability-uiability-c.md#onwindowstagecreate), onExecuteInUIAbilityForegroundMode, and [onForeground](arkts-ability-app-ability-uiability-uiability-c.md#onforeground).  
- If the UIAbility is hot started in the background, the UIAbility lifecycle callbacks are triggered in the  
following sequence during intent execution: [onNewWant](arkts-ability-app-ability-uiability-uiability-c.md#onnewwant), onExecuteInUIAbilityForegroundMode, and [onForeground](arkts-ability-app-ability-uiability-uiability-c.md#onforeground).  
- If the UIAbility is hot started in the foreground, the UIAbility lifecycle callbacks are triggered in the  
following sequence during intent execution: onExecuteInUIAbilityForegroundMode.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Intent name. |
| param | Record&lt;string, Object&gt; | Yes | Intent parameter, which is the data passed from the system entry point to the application for this intent execution. |
| pageLoader | [window.WindowStage](../../apis-arkui/arkts-apis/arkts-arkui-window-windowstage-i.md) | Yes | WindowStage instance, which is the same as the WindowStage instance in the [onWindowStageCreate](arkts-ability-app-ability-uiability-uiability-c.md#onwindowstagecreate) API and can be used to load the page for intent execution. |

**Return value:**

| Type | Description |
| --- | --- |
| [insightIntent.ExecuteResult](arkts-ability-insightintent-executeresult-i.md) &#124; Promise&lt;[insightIntent.ExecuteResult](arkts-ability-insightintent-executeresult-i.md)&gt; | Intent execution result or a Promise object containing the intent execution result, representing the data returned to the system entry point from this intent execution. |

**Examples**

The code snippet below shows the synchronous call that returns the intent execution result:

```TypeScript
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

```TypeScript
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

## onExecuteInUIExtensionAbility

```TypeScript
onExecuteInUIExtensionAbility(name: string, param: Record<string, Object>, pageLoader: UIExtensionContentSession):insightIntent.ExecuteResult | Promise<insightIntent.ExecuteResult>
```

Called during the UIExtensionAbility lifecycle when the [UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md) that the intent execution depends on is started. Both synchronous calls and asynchronous calls using Promise are supported.

- The UIExtensionAbility lifecycle callbacks are triggered in the following sequence during intent execution:[onCreate](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md#oncreate), [onSessionCreate](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md#onsessioncreate), onExecuteInUIExtensionAbility, and [onForeground](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md#onforeground).

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Intent name. |
| param | Record&lt;string, Object&gt; | Yes | Intent parameter, which is the data passed from the system entry point to the application for this intent execution. |
| pageLoader | [UIExtensionContentSession](arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c.md) | Yes | UIExtensionContentSession instance, which is the same as the UIExtensionContentSession instance in the [onSessionCreate](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md#onsessioncreate) API and can be used to load the page for intent execution. |

**Return value:**

| Type | Description |
| --- | --- |
| [insightIntent.ExecuteResult](arkts-ability-insightintent-executeresult-i.md) &#124; Promise&lt;[insightIntent.ExecuteResult](arkts-ability-insightintent-executeresult-i.md)&gt; | Intent execution result or a Promise object containing the intent execution result, representing the data returned to the system entry point from this intent execution. |

**Examples**

The code snippet below shows the synchronous call that returns the intent execution result:

```TypeScript
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

```TypeScript
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

## context

```TypeScript
context: InsightIntentContext
```

Context for intent execution.

**Type:** [InsightIntentContext](arkts-ability-app-ability-insightintentcontext-insightintentcontext-c.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
