# LazyLayoutHelper

懒加载布局辅助类，提供布局方向和可视区域位置信息。

**起始版本：** 26.0.0

<!--Device-unnamed-export class LazyLayoutHelper--><!--Device-unnamed-export class LazyLayoutHelper-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getLazyLayoutDirection

```TypeScript
getLazyLayoutDirection(): LazyLayoutDirection
```

获取懒加载布局方向。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LazyLayoutHelper-getLazyLayoutDirection(): LazyLayoutDirection--><!--Device-LazyLayoutHelper-getLazyLayoutDirection(): LazyLayoutDirection-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LazyLayoutDirection](arkts-arkui-lazylayoutalgorithm-lazylayoutdirection-e.md) | 懒加载布局方向。 |

## getViewEnd

```TypeScript
getViewEnd(): number
```

获取可视区域的结束位置。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LazyLayoutHelper-getViewEnd(): int--><!--Device-LazyLayoutHelper-getViewEnd(): int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 可视区域的结束位置。<br>单位：px。 |

## getViewStart

```TypeScript
getViewStart(): number
```

获取可视区域的起始位置。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LazyLayoutHelper-getViewStart(): int--><!--Device-LazyLayoutHelper-getViewStart(): int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 可视区域的起始位置。<br>单位：px。 |

## setAdjustedOffset

```TypeScript
setAdjustedOffset(offset: number): void
```

设置懒加载的调整偏移量。

在布局列数、间距等参数变化场景下，需要调用该接口调整偏移量以保持可视区域第一个子组件相对位置保持不变。

以垂直方向布局为例，当布局方向为LazyLayoutDirection.FORWARD时，该接口设置的偏移量为容器上边界的调整量，当布局方向为LazyLayoutDirection.BACKWARD时，该接口设置的偏移量为容器下边界的调整量。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LazyLayoutHelper-setAdjustedOffset(offset: int): void--><!--Device-LazyLayoutHelper-setAdjustedOffset(offset: int): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 是 | 设置的调整偏移量，往内容末尾端调整为正，往内容起始端调整为负。单位：px。 |

## setChildrenInactive

```TypeScript
setChildrenInactive(children: number[]): void
```

设置子组件为非激活状态。

如果子组件是通过[ForEach](../@internal/component/ets/for_each)或[Repeat](arkts-arkui-repeat-con.md#repeat)（未启用[virtualScroll](arkts-arkui-repeat-repeatattribute-c.md#virtualscroll-1)）生成的，设置为非激活状态后将不显示。

如果子组件是通过[LazyForEach](../@internal/component/ets/lazy_for_each)或[Repeat](arkts-arkui-repeat-con.md#repeat)（启用[virtualScroll](arkts-arkui-repeat-repeatattribute-c.md#virtualscroll-1)）生成的，设置为非激活状态后将销毁或回收。

[LazyForEach](../@internal/component/ets/lazy_for_each)或[Repeat](arkts-arkui-repeat-con.md#repeat)（启用[virtualScroll](arkts-arkui-repeat-repeatattribute-c.md#virtualscroll-1)）只支持连续的激活子组件；在两个激活子组件之间设置子组件为非激活状态不会生效。

布局在可视区域外的子组件会自动设置为非激活状态。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LazyLayoutHelper-setChildrenInactive(children: int[]): void--><!--Device-LazyLayoutHelper-setChildrenInactive(children: int[]): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| children | number[] | 是 | 设置为非激活状态的子组件索引数组。 |

