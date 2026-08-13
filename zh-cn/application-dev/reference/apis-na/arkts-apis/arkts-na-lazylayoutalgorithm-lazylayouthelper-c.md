# LazyLayoutHelper

懒布局算法的帮助器类，为懒布局提供布局方向和视图位置信息。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export declare class LazyLayoutHelper--><!--Device-unnamed-export declare class LazyLayoutHelper-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getLazyLayoutDirection

```TypeScript
getLazyLayoutDirection(): LazyLayoutDirection
```

获取懒加载布局方向。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LazyLayoutHelper-getLazyLayoutDirection(): LazyLayoutDirection--><!--Device-LazyLayoutHelper-getLazyLayoutDirection(): LazyLayoutDirection-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LazyLayoutDirection](arkts-na-lazylayoutalgorithm-lazylayoutdirection-e.md) | The lazy layout direction. |

## getViewEnd

```TypeScript
getViewEnd(): int
```

获取可见视图的结束位置。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LazyLayoutHelper-getViewEnd(): int--><!--Device-LazyLayoutHelper-getViewEnd(): int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | The end position of the visible view. &lt;br&gt;Unit: px. |

## getViewStart

```TypeScript
getViewStart(): int
```

获取可见视图的起始位置。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LazyLayoutHelper-getViewStart(): int--><!--Device-LazyLayoutHelper-getViewStart(): int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | The start position of the visible view. &lt;br&gt;Unit: px. |

## setAdjustedOffset

```TypeScript
setAdjustedOffset(offset: int): void
```

设置懒加载布局调整偏移量。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LazyLayoutHelper-setAdjustedOffset(offset: int): void--><!--Device-LazyLayoutHelper-setAdjustedOffset(offset: int): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | int | 是 | 设置要的调整偏移值。 &lt;br&gt;单位:单位：px。 |

## setChildrenInactive

```TypeScript
setChildrenInactive(children: int[]): void
```

设置子项不活动。 如果子组件是通过ForEach或不带virtualScroll的Repeat生成的，将其设置为inactive后，将不会显示。 如果子组件是通过LazyForEach或者通过带virtualScroll的Repeat来生成的，将其设置为非活动状态后将被销毁或回收。 带有virtualScroll的LazyForEach和Repeat只支持连续活动的子组件，在两个活动的子组件之间设置子组件为inactive不会生效。 布局在显示区域之外的子组件将自动设置为非活动状态。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LazyLayoutHelper-setChildrenInactive(children: int[]): void--><!--Device-LazyLayoutHelper-setChildrenInactive(children: int[]): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| children | int[] | 是 | 要设置非活动状态的子组件的索引。 |

