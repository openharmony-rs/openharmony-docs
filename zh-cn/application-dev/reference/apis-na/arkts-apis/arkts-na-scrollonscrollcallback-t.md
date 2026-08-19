# ScrollOnScrollCallback

```TypeScript
export type ScrollOnScrollCallback = (xOffset: double, yOffset: double, scrollState: ScrollState) => void
```

Scroll滚动时触发的回调。 > **说明：** > 若通过onScrollFrameBegin事件和[scrollBy](arkts-na-scroll-scroller-c.md#scrollby)方法实现容器嵌套滚动，需设置子滚动节点的 > EdgeEffect为None。如Scroll嵌套List滚动时，List组件的[edgeEffect](../../../reference/apis-arkui/arkui-ts/ts-container-list.md#edgeeffect) > 属性需设置为EdgeEffect.None。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type ScrollOnScrollCallback = (xOffset: double, yOffset: double, scrollState: ScrollState) => void--><!--Device-unnamed-export type ScrollOnScrollCallback = (xOffset: double, yOffset: double, scrollState: ScrollState) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| xOffset | double | 是 | 相对于上一帧水平方向的偏移量，Scroll中的内容向左滚动时偏移量为正，向右滚动时偏移量为负。<br/>单位vp。 <br>单位:vp。 <br>单位:vp。 |
| yOffset | double | 是 | 相对于上一帧竖直方向的偏移量，Scroll中的内容向上滚动时偏移量为正，向下滚动时偏移量为负。<br/>单位vp。 <br>单位:vp。 <br>单位:vp。 |
| scrollState | [ScrollState](../../apis-arkui/arkts-components/arkts-arkui-scrollstate-e.md) | 是 | 当前滚动状态。 |

