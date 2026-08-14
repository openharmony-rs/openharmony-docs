# AccessibilityOptions

Defines the struct of AccessibilityOptions.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface AccessibilityOptions--><!--Device-unnamed-export declare interface AccessibilityOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityPreferred

```TypeScript
accessibilityPreferred?: boolean
```

若accessibilityPreferred设置为true，则深度遍历每个子节点时优先选择该子节点的无障碍文本accessibilityText。 若无障碍文本为空则选择本身Text文本，最终将拼接完成的文本设置给accessibilityText与Text都为空的父节点。 若accessibilityPreferred设置为false，表示不启用此功能。 默认值：false

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AccessibilityOptions-accessibilityPreferred?: boolean--><!--Device-AccessibilityOptions-accessibilityPreferred?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## actionControllerId

```TypeScript
actionControllerId?: string
```

指定特定唯一标识ID的子组件。配置 accessibilityGroup 的容器组件进行无障碍聚合后，如果触发无障碍的控制操作时，会将操作转发给该特定标识的子组件。从而聚合屏幕朗读下的点击事件，避免需要对子组件单独进行聚焦。 **说明：** 如果聚合组件内有多个相同类型的子组件，则以组件树上该聚合组件下的第一个查找到的子组件为控制组件。 当前只支持无障碍点击操作。 如果与actionControllerRoleType同时配置，则优先匹配ID一致的组件。 不支持跨进程嵌入式组件内的特定类型，例如：卡片、EmbeddedUIExtension。 默认值：无指定组件

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AccessibilityOptions-actionControllerId?: string--><!--Device-AccessibilityOptions-actionControllerId?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## actionControllerRoleType

```TypeScript
actionControllerRoleType?: AccessibilityRoleType
```

指定特定类型的子组件。配置 accessibilityGroup 的容器组件进行无障碍聚合后，如果触发无障碍的控制操作时，会将操作转发给该特定类型的子组件。从而聚合屏幕朗读下的点击事件，避免需要对子组件单独进行聚焦。 **说明：** 如果聚合组件内有多个相同类型的子组件，则以组件树上该聚合组件下的第一个查找到的子组件为控制组件。 当前只支持无障碍点击操作。 不支持跨进程嵌入式组件内的特定类型，例如：卡片、EmbeddedUIExtension。 默认值：无指定组件

**类型：** [AccessibilityRoleType](../../apis-arkui/arkts-components/arkts-arkui-accessibilityroletype-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AccessibilityOptions-actionControllerRoleType?: AccessibilityRoleType--><!--Device-AccessibilityOptions-actionControllerRoleType?: AccessibilityRoleType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## stateControllerId

```TypeScript
stateControllerId?: string
```

指定特定唯一标识ID的子组件。配置 accessibilityGroup 的容器组件进行无障碍聚合后，会将该特定标识的子组件的选中状态和状态播报文本作为聚合组件的状态和播报文本。从而聚合屏幕朗读下的状态播报，避免需要对子组件单独进行聚焦。 **说明：** 如果聚合组件内有多个相同类型的子组件，则以组件树上该聚合组件下的第一个查找到的子组件为控制组件。 如果与stateControllerRoleType同时配置，则优先匹配ID一致的组件。 不支持跨进程嵌入式组件内的特定类型，例如：卡片、EmbeddedUIExtension。 默认值：无指定组件

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AccessibilityOptions-stateControllerId?: string--><!--Device-AccessibilityOptions-stateControllerId?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## stateControllerRoleType

```TypeScript
stateControllerRoleType?: AccessibilityRoleType
```

指定特定类型的子组件。配置 accessibilityGroup 的容器组件进行无障碍聚合后，会将该特定类型的子组件的选中状态和状态播报文本作为聚合组件的状态和播报文本。从而聚合屏幕朗读下的状态播报，避免需要对子组件单独进行聚焦。 **说明：** 如果聚合组件内有多个相同类型的子组件，则以组件树上该聚合组件下的第一个查找到的子组件为控制组件。 不支持跨进程嵌入式组件内的特定类型，例如：卡片、EmbeddedUIExtension。 默认值：无指定组件

**类型：** [AccessibilityRoleType](../../apis-arkui/arkts-components/arkts-arkui-accessibilityroletype-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AccessibilityOptions-stateControllerRoleType?: AccessibilityRoleType--><!--Device-AccessibilityOptions-stateControllerRoleType?: AccessibilityRoleType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

