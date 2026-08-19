# AISessionEvent

Custom AI session model integration for Web components. Users can define custom AI session behaviors via this interface.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare interface AISessionEvent--><!--Device-unnamed-export declare interface AISessionEvent-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## aiSessionType

```TypeScript
aiSessionType: AISessionType
```

The type of AI session.

**类型：** [AISessionType](arkts-na-web-aisessiontype-e.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AISessionEvent-aiSessionType: AISessionType--><!--Device-AISessionEvent-aiSessionType: AISessionType-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## onCreateAISession

```TypeScript
onCreateAISession: OnCreateAISession
```

Triggered when an AI session is created. Allows custom model initialization and result handling. Return `true` to bypass the default system behavior; return `false` to proceed with the default logic.

**类型：** [OnCreateAISession](arkts-na-oncreateaisession-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AISessionEvent-onCreateAISession: OnCreateAISession--><!--Device-AISessionEvent-onCreateAISession: OnCreateAISession-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## onDestroyAISession

```TypeScript
onDestroyAISession: OnDestroyAISession
```

Triggered when an AI session is destroyed. Used for cleaning up resources associated with custom AI models.

**类型：** [OnDestroyAISession](arkts-na-ondestroyaisession-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AISessionEvent-onDestroyAISession: OnDestroyAISession--><!--Device-AISessionEvent-onDestroyAISession: OnDestroyAISession-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## onExecuteAIAction

```TypeScript
onExecuteAIAction: OnExecuteAIAction
```

Triggered when executing an AI session action. Enables custom implementation of AI model execution.

**类型：** [OnExecuteAIAction](arkts-na-onexecuteaiaction-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AISessionEvent-onExecuteAIAction: OnExecuteAIAction--><!--Device-AISessionEvent-onExecuteAIAction: OnExecuteAIAction-End-->

**系统能力：** SystemCapability.Web.Webview.Core

