# FastScrollMode

```TypeScript
declare enum FastScrollMode
```

枚举滚动到指定索引的快速滚动模式。

**起始版本：** 26.2.0

<!--Device-unnamed-declare enum FastScrollMode--><!--Device-unnamed-declare enum FastScrollMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## NONE

```TypeScript
NONE = 0
```

不启用快速滚动优化。在动画开始前创建并测量所有中间子组件。

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.2.0开始，该接口支持在原子化服务中使用。

<!--Device-FastScrollMode-NONE = 0--><!--Device-FastScrollMode-NONE = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SKIP_CREATE_AND_MEASURE

```TypeScript
SKIP_CREATE_AND_MEASURE = 2
```

快速滚动优化，跳过中间子组件的创建和测量。中间子组件既不会被创建，也不会被测量。该模式提供最大限度的优化性能。但该模式不适用于List多列且ListItem和ListItemGroup同时存在的场景。在此场景下，请使用SKIP_MEASURE。

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.2.0开始，该接口支持在原子化服务中使用。

<!--Device-FastScrollMode-SKIP_CREATE_AND_MEASURE = 2--><!--Device-FastScrollMode-SKIP_CREATE_AND_MEASURE = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SKIP_MEASURE

```TypeScript
SKIP_MEASURE = 1
```

快速滚动优化，跳过中间子组件的测量。中间子组件会被创建但不会被测量。该模式适用于List多列且ListItem和ListItemGroup同时存在的场景。此时ListItem只占一行中的一列，但ListItemGroup会占满一整行，因此List需要创建所有中间子组件来获取这些子组件类型从而计算出目标索引的行位置。

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.2.0开始，该接口支持在原子化服务中使用。

<!--Device-FastScrollMode-SKIP_MEASURE = 1--><!--Device-FastScrollMode-SKIP_MEASURE = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
