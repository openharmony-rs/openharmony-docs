# ScrollOnScrollCallback

```TypeScript
declare type ScrollOnScrollCallback = (xOffset: number, yOffset: number, scrollState: ScrollState) => void
```

Scroll滚动时触发的回调。

<p><strong>说明</strong><br>若通过onScrollFrameBegin事件和scrollBy方法实现容器嵌套滚动，需设置子滚动节点的EdgeEffect为None。如Scroll嵌套List滚动时，List组件的edgeEffect属性需设置为EdgeEffect.None。</p>

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type ScrollOnScrollCallback = (xOffset: number, yOffset: number, scrollState: ScrollState) => void--><!--Device-unnamed-declare type ScrollOnScrollCallback = (xOffset: number, yOffset: number, scrollState: ScrollState) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| xOffset | number | 是 | 相对于上一帧水平方向的偏移量，Scroll中的内容向左滚动时偏移量为正，向右滚动时偏移量为负。 <br>单位vp  |
| yOffset | number | 是 | 相对于上一帧竖直方向的偏移量，Scroll中的内容向上滚动时偏移量为正，向下滚动时偏移量为负。 <br>单位vp  |
| scrollState | [ScrollState](arkts-arkui-scrollstate-e.md) | 是 | 当前滚动状态。  |

