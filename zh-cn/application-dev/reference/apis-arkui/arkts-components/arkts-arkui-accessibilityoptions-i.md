# AccessibilityOptions

Defines the struct of AccessibilityOptions.

**起始版本：** 14

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityPreferred

```TypeScript
accessibilityPreferred?: boolean
```

accessibilityPreferred -在连接子组件字符串时，是否应该优先考虑accessibilityText。

**类型：** boolean

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## actionControllerId

```TypeScript
actionControllerId?: string
```

通过该可选参数指定特定ID的子组件，配置AccessibilityGroup的容器组件进行无障碍聚合后，如果触发无障碍的控制操作时，会将操作转发给该特定类型的子组件。从而聚合屏幕朗读下的点击事件，避免需要对子组件单独进行聚焦。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## actionControllerRoleType

```TypeScript
actionControllerRoleType?: AccessibilityRoleType
```

stateControllerRoleType - 通过该可选参数指定特定类型的子组件，配置AccessibilityGroup的容器组件进行无障碍聚合后，如果触发无障碍的控制操作时，会将操作转发给该特定类型的子组件。从而聚合屏幕朗读下的点击事件，避免需要对子组件单独进行聚焦。

**类型：** AccessibilityRoleType

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## stateControllerId

```TypeScript
stateControllerId?: string
```

stateControllerId -通过该可选参数指定特定ID的子组件，配置AccessibilityGroup的容器组件进行无障碍聚合后，会将该子组件的选中状态和状态播报文本作为聚合组件的状态和播报文本。从而聚合屏幕朗读下的状态播报，避免需要对子组件单独进行聚焦。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## stateControllerRoleType

```TypeScript
stateControllerRoleType?: AccessibilityRoleType
```

stateControllerRoleType - 通过该可选参数指定特定类型的子组件，配置AccessibilityGroup的容器组件进行无障碍聚合后，会将该子组件的选中状态和状态播报文本作为聚合组件的状态和播报文本。从而聚合屏幕朗读下的状态播报，避免需要对子组件单独进行聚焦。

**类型：** AccessibilityRoleType

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

