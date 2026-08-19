# NestedScrollOptions

[nestedScroll](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#nestedscroll11)属性参数对象。

**起始版本：** 23

<!--Device-unnamed-declare interface NestedScrollOptions--><!--Device-unnamed-declare interface NestedScrollOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## scrollBackward

```TypeScript
scrollBackward: NestedScrollMode
```

滚动组件往起始端滚动时的嵌套滚动选项。NestedScrollMode.SELF_ONLY表示仅自身滚动，不与父组件联动；NestedScrollMode.SELF_FIRST表示自身先滚动，自身滚动到边缘后父组件滚动； NestedScrollMode.PARENT_FIRST表示父组件先滚动，父组件滚动到边缘后自身滚动。

**类型：** NestedScrollMode

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NestedScrollOptions-scrollBackward: NestedScrollMode--><!--Device-NestedScrollOptions-scrollBackward: NestedScrollMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scrollForward

```TypeScript
scrollForward: NestedScrollMode
```

滚动组件往末尾端滚动时的嵌套滚动选项。NestedScrollMode.SELF_ONLY表示仅自身滚动，不与父组件联动；NestedScrollMode.SELF_FIRST表示自身先滚动，自身滚动到边缘后父组件滚动； NestedScrollMode.PARENT_FIRST表示父组件先滚动，父组件滚动到边缘后自身滚动。

**类型：** NestedScrollMode

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NestedScrollOptions-scrollForward: NestedScrollMode--><!--Device-NestedScrollOptions-scrollForward: NestedScrollMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

