# InsightIntentExecutor

The module provides the base class for intent execution. You can use this module to interface with the [InsightIntent framework](../../../application-models/insight-intent-overview.md) on the device side and implement intent service logic through [configuration files](../../../application-models/insight-intent-config-development.md). In addition to developing intents via configuration files, intents can also be developed using decorators. For API version 20 and later, you are advised to [develop intents using decorators](../../../application-models/insight-intent-decorator-development.md).

**Since:** 11

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { InsightIntentExecutor } from '@kit.AbilityKit';
```

## onExecuteInServiceExtensionAbility

```TypeScript
onExecuteInServiceExtensionAbility(name: string, param: Record<string, Object>):
    insightIntent.ExecuteResult | Promise<insightIntent.ExecuteResult>
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

```TypeScript
The code snippet below shows the synchronous call that returns the intent execution result:
```

```TypeScript
The code snippet below shows the promise-based asynchronous call that returns the intent execution result:
```

## onExecuteInUIAbilityBackgroundMode

```TypeScript
onExecuteInUIAbilityBackgroundMode(name: string, param: Record<string, Object>):
    insightIntent.ExecuteResult | Promise<insightIntent.ExecuteResult>
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

```TypeScript
The code snippet below shows the synchronous call that returns the intent execution result:
```

```TypeScript
The code snippet below shows the promise-based asynchronous call that returns the intent execution result:
```

## onExecuteInUIAbilityForegroundMode

```TypeScript
onExecuteInUIAbilityForegroundMode(name: string, param: Record<string, Object>, pageLoader: window.WindowStage):
    insightIntent.ExecuteResult | Promise<insightIntent.ExecuteResult>
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

```TypeScript
The code snippet below shows the synchronous call that returns the intent execution result:
```

```TypeScript
The code snippet below shows the promise-based asynchronous call that returns the intent execution result:
```

## onExecuteInUIExtensionAbility

```TypeScript
onExecuteInUIExtensionAbility(name: string, param: Record<string, Object>, pageLoader: UIExtensionContentSession):
    insightIntent.ExecuteResult | Promise<insightIntent.ExecuteResult>
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

```TypeScript
The code snippet below shows the synchronous call that returns the intent execution result:
```

```TypeScript
The code snippet below shows the promise-based asynchronous call that returns the intent execution result:
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
