# AISessionEvent

```TypeScript
declare interface AISessionEvent
```

Custom AI session configuration object, used to define the lifecycle callbacks of an AI session, including creation, execution, and destruction.

<!--no_check-->

**Since:** 26.0.0

**System capability:** SystemCapability.Web.Webview.Core

## onCreateAISession

```TypeScript
onCreateAISession: OnCreateAISession
```

Callback function triggered when an AI session is created. Returns **true** to skip the system default behavior, and **false** to continue executing the system default logic.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

## onDestroyAISession

```TypeScript
onDestroyAISession: OnDestroyAISession
```

Callback function triggered when an AI session is destroyed, used to clean up resources associated with the custom AI model.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

## onExecuteAIAction

```TypeScript
onExecuteAIAction: OnExecuteAIAction
```

Callback function triggered when an AI session executes an action.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

## aiSessionType

```TypeScript
aiSessionType: AISessionType
```

AI session type.

**Type:** [AISessionType](arkts-arkweb-web-comp-aisessiontype-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core
