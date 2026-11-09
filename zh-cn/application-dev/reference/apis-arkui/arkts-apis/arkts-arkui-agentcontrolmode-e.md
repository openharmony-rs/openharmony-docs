# AgentControlMode

```TypeScript
declare enum AgentControlMode
```

定义Agent生成事件的输入管控模式。

Agent生成的事件包括系统Agent生成的事件，以及具有ohos.permission.CONTROL_DEVICE权限的应用注入的事件。管控仅适用于此类Agent生成的输入事件。

**起始版本：** 26.1.0

<!--Device-unnamed-declare enum AgentControlMode--><!--Device-unnamed-declare enum AgentControlMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ALLOW

```TypeScript
ALLOW = 0
```

允许Agent生成的输入操作，无需用户确认。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-AgentControlMode-ALLOW = 0--><!--Device-AgentControlMode-ALLOW = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DENY

```TypeScript
DENY = 1
```

阻止Agent生成的输入操作。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-AgentControlMode-DENY = 1--><!--Device-AgentControlMode-DENY = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
