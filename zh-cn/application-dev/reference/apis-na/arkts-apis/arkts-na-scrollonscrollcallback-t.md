# ScrollOnScrollCallback

```TypeScript
export type ScrollOnScrollCallback = (xOffset: double, yOffset: double, scrollState: ScrollState) => void
```

Scroll滚动时触发的回调。 > **说明：** > 若通过[onScrollFrameBegin]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_事件和[scrollBy]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_方法实现容器嵌套滚动，需设置子滚动节点的 > EdgeEffect为None。如Scroll嵌套List滚动时，List组件的\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ > 属性需设置为EdgeEffect.None。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type ScrollOnScrollCallback = (xOffset: double, yOffset: double, scrollState: ScrollState) => void--><!--Device-unnamed-export type ScrollOnScrollCallback = (xOffset: double, yOffset: double, scrollState: ScrollState) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| xOffset | double | 是 | 相对于上一帧水平方向的偏移量，Scroll中的内容向左滚动时偏移量为正，向右滚动时偏移量为负。\_\_\_HTML\_TAG\_USD\_0\_\_\_单位vp。 \_\_\_HTML\_TAG\_USD\_1\_\_\_单位:vp。 \_\_\_HTML\_TAG\_USD\_2\_\_\_单位:vp。  |
| yOffset | double | 是 | 相对于上一帧竖直方向的偏移量，Scroll中的内容向上滚动时偏移量为正，向下滚动时偏移量为负。\_\_\_HTML\_TAG\_USD\_0\_\_\_单位vp。 \_\_\_HTML\_TAG\_USD\_1\_\_\_单位:vp。 \_\_\_HTML\_TAG\_USD\_2\_\_\_单位:vp。  |
| scrollState | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 当前滚动状态。  |

