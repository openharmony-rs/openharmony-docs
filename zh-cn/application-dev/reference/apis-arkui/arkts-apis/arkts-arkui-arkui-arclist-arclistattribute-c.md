# ArcListAttribute

除支持通用属性外，还支持以下属性（不支持 [滚动组件通用属性](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#属性)）：

**继承/实现关系：** ArcListAttribute extends CommonMethod<ArcListAttribute>

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

<!--Device-unnamed-export declare class ArcListAttribute--><!--Device-unnamed-export declare class ArcListAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## cachedCount

```TypeScript
cachedCount(count: Optional<number>): ArcListAttribute
```

设置列表中ArcListItem的预加载数量，懒加载场景只会预加载ArcList显示区域外上下各cachedCount行的ArcListItem，非懒加载场景会全部加载。懒加载、非懒加载都只布局ArcList显示区域+ ArcList显示区域外上下各cachedCount行的ArcListItem。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcListAttribute-cachedCount(count: Optional<number>): ArcListAttribute--><!--Device-ArcListAttribute-cachedCount(count: Optional<number>): ArcListAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| count | Optional&lt;number&gt; | 是 | ArcListItem的预加载数量。 &lt;br&gt;默认值：根据屏幕内显示的节点个数设置，最大值为16。 &lt;br&gt;取值范围：[0, +∞) &lt;br&gt;设置为负数时，按1处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcListAttribute](arkts-arkui-arkui-arclist-arclistattribute-c.md) |  |

## chainAnimation

```TypeScript
chainAnimation(enable: Optional<boolean>): ArcListAttribute
```

设置当前ArcList是否启用链式联动动效，开启后列表滑动以及顶部和底部拖拽时会有链式联动的效果。 链式联动效果：ArcList内的ArcListItem间隔一定距离，在基本的滑动交互行为下，主动对象驱动从动对象进行联动，驱动效果遵循弹簧物理动效。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcListAttribute-chainAnimation(enable: Optional<boolean>): ArcListAttribute--><!--Device-ArcListAttribute-chainAnimation(enable: Optional<boolean>): ArcListAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | Optional&lt;boolean&gt; | 是 | 是否启用链式联动动效。仅当边缘效果为EdgeEffect.Spring时，链式联动动效才会生效。 &lt;br&gt;默认值：false，不启用链式联动。true，启用链式联动。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcListAttribute](arkts-arkui-arkui-arclist-arclistattribute-c.md) |  |

## childrenMainSize

```TypeScript
childrenMainSize(size: Optional<ChildrenMainSize>): ArcListAttribute
```

设置ArcList组件的子组件在主轴方向的大小信息。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcListAttribute-childrenMainSize(size: Optional<ChildrenMainSize>): ArcListAttribute--><!--Device-ArcListAttribute-childrenMainSize(size: Optional<ChildrenMainSize>): ArcListAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | Optional&lt;ChildrenMainSize&gt; | 是 | 通过ChildrenMainSize对象向ArcList组件精确提供所有子组件在主轴方向 的大小信息，能够确保ArcList组件在子组件主轴尺寸不统一、子组件的增删变动、以及使用scrollToIndex等场景时，仍能保持其滑动位置的准确性。进而保 证了scrollTo能够精准跳转至指定位置，currentOffset或 offset准确反映当前的滑动位置，且内置滚动条能够实现平滑移动，避免任何跳跃或突变。从API version 23开始，新增offset接口。 &lt;br&gt; **说明：** &lt;br&gt;提供的主轴方向大小必须与子组件实际在主轴方向的大小一致，否则可能导致ArcList组件显示异常。子组件在主轴方向大小发生变化或进行增删操作时，必须通过调用ChildrenMainSize对象的方法在变更后通知 ArcList组件，否则可能导致ArcList组件显示异常。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcListAttribute](arkts-arkui-arkui-arclist-arclistattribute-c.md) |  |

## digitalCrownSensitivity

```TypeScript
digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>): ArcListAttribute
```

设置表冠响应灵敏度。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcListAttribute-digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>): ArcListAttribute--><!--Device-ArcListAttribute-digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>): ArcListAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sensitivity | Optional&lt;CrownSensitivity&gt; | 是 | 表冠响应灵敏度。 &lt;br&gt;默认值：CrownSensitivity.MEDIUM，响应速度适中。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcListAttribute](arkts-arkui-arkui-arclist-arclistattribute-c.md) |  |

## enableScrollInteraction

```TypeScript
enableScrollInteraction(enable: Optional<boolean>): ArcListAttribute
```

设置是否支持滚动手势。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcListAttribute-enableScrollInteraction(enable: Optional<boolean>): ArcListAttribute--><!--Device-ArcListAttribute-enableScrollInteraction(enable: Optional<boolean>): ArcListAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | Optional&lt;boolean&gt; | 是 | 是否支持滚动手势。设置为true时可以通过手指或者鼠标滚动，设置为false时无法通过手指或者鼠标滚动，但不影响控制器 Scroller的滚动接口。 &lt;br&gt;默认值：true |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcListAttribute](arkts-arkui-arkui-arclist-arclistattribute-c.md) |  |

## fadingEdge

```TypeScript
fadingEdge(enable: Optional<boolean>): ArcListAttribute
```

设置是否开启边缘渐隐效果。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcListAttribute-fadingEdge(enable: Optional<boolean>): ArcListAttribute--><!--Device-ArcListAttribute-fadingEdge(enable: Optional<boolean>): ArcListAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | Optional&lt;boolean&gt; | 是 | fadingEdge生效时，会覆盖原组件的`.overlay()`属性。 &lt;br&gt;fadingEdge生效时，建议不在该组件上设置background相关属性，会影响渐隐的显示效果。 &lt;br&gt;fadingEdge生效时，组件会裁剪到边界，设置组件的clip属性为false不生效。 &lt;br&gt;设置为true时开启边缘渐隐效果，设置为false时不开启边缘渐隐效果。 &lt;br&gt;默认值：false |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcListAttribute](arkts-arkui-arkui-arclist-arclistattribute-c.md) |  |

## flingSpeedLimit

```TypeScript
flingSpeedLimit(speed: Optional<number>): ArcListAttribute
```

限制跟手滑动结束后，惯性滚动动效开始时的最大初始速度。设置为小于等于0的值时，按默认值处理。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcListAttribute-flingSpeedLimit(speed: Optional<number>): ArcListAttribute--><!--Device-ArcListAttribute-flingSpeedLimit(speed: Optional<number>): ArcListAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| speed | Optional&lt;number&gt; | 是 | 惯性滚动动效开始时的最大初始速度。设置为小于等于0的值时，按默认值处理。 &lt;br&gt;默认值：9000 &lt;br&gt;单位：vp/s &lt;br&gt;取值范围：(0, +∞) |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcListAttribute](arkts-arkui-arkui-arclist-arclistattribute-c.md) |  |

## friction

```TypeScript
friction(friction: Optional<number>): ArcListAttribute
```

设置摩擦系数，手动滑动滚动区域时生效，仅影响惯性滚动过程。设置为小于等于0的值时，按默认值处理。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcListAttribute-friction(friction: Optional<number>): ArcListAttribute--><!--Device-ArcListAttribute-friction(friction: Optional<number>): ArcListAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| friction | Optional&lt;number&gt; | 是 | 摩擦系数，手动滑动滚动区域时生效，仅影响惯性滚动过程。设置为小于等于0的值时，按默认值处理。 &lt;br&gt;默认值：0.8 &lt;br&gt;取值范围：(0, +∞) |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcListAttribute](arkts-arkui-arkui-arclist-arclistattribute-c.md) |  |

## onDidScroll

```TypeScript
onDidScroll(handler: Optional<OnScrollCallback>): ArcListAttribute
```

列表滑动时触发，返回当前帧滑动的偏移量和当前滑动状态。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcListAttribute-onDidScroll(handler: Optional<OnScrollCallback>): ArcListAttribute--><!--Device-ArcListAttribute-onDidScroll(handler: Optional<OnScrollCallback>): ArcListAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | Optional&lt;OnScrollCallback&gt; | 是 | 列表滑动时触发的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcListAttribute](arkts-arkui-arkui-arclist-arclistattribute-c.md) |  |

## onReachEnd

```TypeScript
onReachEnd(handler: Optional<VoidCallback>): ArcListAttribute
```

列表到达末尾位置时触发。 ArcList边缘效果为弹簧效果时，滑动经过末尾位置时触发一次该事件，回弹返回末尾位置时再触发一次该事件。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcListAttribute-onReachEnd(handler: Optional<VoidCallback>): ArcListAttribute--><!--Device-ArcListAttribute-onReachEnd(handler: Optional<VoidCallback>): ArcListAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | Optional&lt;VoidCallback&gt; | 是 | 列表到达末尾位置时触发。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcListAttribute](arkts-arkui-arkui-arclist-arclistattribute-c.md) |  |

## onReachStart

```TypeScript
onReachStart(handler: Optional<VoidCallback>): ArcListAttribute
```

列表到达起始位置时触发。 当ArcList进行初始化时，若[initialIndex](arkts-arkui-arkui-arclist-arklistoptions-i.md#ArkListOptions)设定为0，将触发一次事件。当ArcList滚动至起始位置，亦会触发一次事件。在ArcList的边缘效果设置为弹簧效果时，滑动经 过起始位置时会触发一次事件，而在回弹返回起始位置时，将再次触发一次事件。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcListAttribute-onReachStart(handler: Optional<VoidCallback>): ArcListAttribute--><!--Device-ArcListAttribute-onReachStart(handler: Optional<VoidCallback>): ArcListAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | Optional&lt;VoidCallback&gt; | 是 | 列表到达起始位置时触发。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcListAttribute](arkts-arkui-arkui-arclist-arclistattribute-c.md) |  |

## onScrollIndex

```TypeScript
onScrollIndex(handler: Optional<ArcScrollIndexHandler>): ArcListAttribute
```

当子组件划入或划出ArcList的显示区域时，将触发此事件。在ArcList初始化时，此事件会被触发一次。当ArcList显示区域内的首个或末个子组件的索引值发生变化，或是显示区域中心的子组件发生变动时，同样会触发此事件。 ArcList的边缘效果为弹簧效果时，在ArcList滑动到边缘后继续滑动以及松手回弹的过程中，不会触发onScrollIndex事件。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcListAttribute-onScrollIndex(handler: Optional<ArcScrollIndexHandler>): ArcListAttribute--><!--Device-ArcListAttribute-onScrollIndex(handler: Optional<ArcScrollIndexHandler>): ArcListAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | Optional&lt;[ArcScrollIndexHandler](arkts-arkui-arcscrollindexhandler-t.md)&gt; | 是 | 有子组件划入或划出ArcList显示区域时触发该回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcListAttribute](arkts-arkui-arkui-arclist-arclistattribute-c.md) |  |

## onScrollStart

```TypeScript
onScrollStart(handler: Optional<VoidCallback>): ArcListAttribute
```

列表滑动开始时触发。手指拖动列表或列表的滚动条触发的滑动开始时，会触发该事件。使用Scroller滑动控制器触发的带动画的滑动，动画开始时会触发该事件。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcListAttribute-onScrollStart(handler: Optional<VoidCallback>): ArcListAttribute--><!--Device-ArcListAttribute-onScrollStart(handler: Optional<VoidCallback>): ArcListAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | Optional&lt;VoidCallback&gt; | 是 | 列表滑动开始时触发。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcListAttribute](arkts-arkui-arkui-arclist-arclistattribute-c.md) |  |

## onScrollStop

```TypeScript
onScrollStop(handler: Optional<VoidCallback>): ArcListAttribute
```

列表滑动停止时触发。手指拖动列表或列表的滚动条触发的滑动，手指离开屏幕后滑动停止时会触发该事件。使用Scroller滑动控制器触发的带动画的滑动，动画停止会触发该事件。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcListAttribute-onScrollStop(handler: Optional<VoidCallback>): ArcListAttribute--><!--Device-ArcListAttribute-onScrollStop(handler: Optional<VoidCallback>): ArcListAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | Optional&lt;VoidCallback&gt; | 是 | 列表滑动停止时触发。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcListAttribute](arkts-arkui-arkui-arclist-arclistattribute-c.md) |  |

## onWillScroll

```TypeScript
onWillScroll(handler: Optional<OnWillScrollCallback>): ArcListAttribute
```

列表滑动时每帧开始前触发，返回当前帧将要滑动的偏移量和当前滑动状态。返回的偏移量为计算得到的将要滑动的偏移量值，并非最终实际滑动偏移。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcListAttribute-onWillScroll(handler: Optional<OnWillScrollCallback>): ArcListAttribute--><!--Device-ArcListAttribute-onWillScroll(handler: Optional<OnWillScrollCallback>): ArcListAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | Optional&lt;OnWillScrollCallback&gt; | 是 | 列表滑动时每帧开始前触发的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcListAttribute](arkts-arkui-arkui-arclist-arclistattribute-c.md) |  |

## scrollBar

```TypeScript
scrollBar(status: Optional<BarState>): ArcListAttribute
```

设置滚动条状态。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcListAttribute-scrollBar(status: Optional<BarState>): ArcListAttribute--><!--Device-ArcListAttribute-scrollBar(status: Optional<BarState>): ArcListAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| status | Optional&lt;BarState&gt; | 是 | 滚动条状态。 &lt;br&gt;默认值：BarState.Auto |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcListAttribute](arkts-arkui-arkui-arclist-arclistattribute-c.md) |  |

## scrollBarColor

```TypeScript
scrollBarColor(color: Optional<ColorMetrics>): ArcListAttribute
```

设置滚动条的颜色。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcListAttribute-scrollBarColor(color: Optional<ColorMetrics>): ArcListAttribute--><!--Device-ArcListAttribute-scrollBarColor(color: Optional<ColorMetrics>): ArcListAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | Optional&lt;[ColorMetrics](../../apis-na/arkts-apis/arkts-na-graphics-colormetrics-c.md)&gt; | 是 | 设置滚动条颜色。 &lt;br&gt;默认值：ColorMetrics.numeric(0xA9FFFFFF) |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcListAttribute](arkts-arkui-arkui-arclist-arclistattribute-c.md) |  |

## scrollBarWidth

```TypeScript
scrollBarWidth(width: Optional<LengthMetrics>): ArcListAttribute
```

设置ArcList滚动条在按压态下的宽度。未设置时，按压态宽度为LengthMetrics.vp(24)。非按压态宽度固定为LengthMetrics.vp(4)，不受该属性影响。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcListAttribute-scrollBarWidth(width: Optional<LengthMetrics>): ArcListAttribute--><!--Device-ArcListAttribute-scrollBarWidth(width: Optional<LengthMetrics>): ArcListAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| width | Optional&lt;[LengthMetrics](../../apis-na/arkts-apis/arkts-na-graphics-lengthmetrics-c.md)&gt; | 是 | ArcList滚动条在按压态下的宽度。 &lt;br&gt;默认值：LengthMetrics.vp(24) &lt;br&gt;非按压态宽度：LengthMetrics.vp(4) &lt;br&gt;设置为负值、undefined等异常值时，按滚动条的普通态宽度处理。 &lt;br&gt;单位：vp |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcListAttribute](arkts-arkui-arkui-arclist-arclistattribute-c.md) |  |

## space

```TypeScript
space(space: Optional<LengthMetrics>): ArcListAttribute
```

设置列表子项之间的间距。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcListAttribute-space(space: Optional<LengthMetrics>): ArcListAttribute--><!--Device-ArcListAttribute-space(space: Optional<LengthMetrics>): ArcListAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| space | Optional&lt;[LengthMetrics](../../apis-na/arkts-apis/arkts-na-graphics-lengthmetrics-c.md)&gt; | 是 | 列表子项之间的间距。 &lt;br&gt;默认值：LengthMetrics.vp(0) &lt;br&gt;ArcList子组件的visibility属性设置为None时不显示，但该子组件上下的space还会生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcListAttribute](arkts-arkui-arkui-arclist-arclistattribute-c.md) |  |

