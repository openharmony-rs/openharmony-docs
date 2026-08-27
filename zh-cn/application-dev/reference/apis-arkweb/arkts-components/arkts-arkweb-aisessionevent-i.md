# AISessionEvent

自定义AI会话配置对象，用于定义AI会话的生命周期回调，包括创建、执行和销毁。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## onCreateAISession

```TypeScript
onCreateAISession: OnCreateAISession
```

AI会话创建时触发的回调函数。返回`true`跳过系统默认行为，返回`false`继续执行系统默认逻辑。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core

## onDestroyAISession

```TypeScript
onDestroyAISession: OnDestroyAISession
```

AI会话销毁时触发的回调函数，用于清理与自定义AI模型关联的资源。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core

## onExecuteAIAction

```TypeScript
onExecuteAIAction: OnExecuteAIAction
```

AI会话执行操作时触发的回调函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core

## aiSessionType

```TypeScript
aiSessionType: AISessionType
```

AI会话类型。

**类型：** [AISessionType](arkts-arkweb-aisessiontype-e.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core
