# ScrollOnWillScrollCallback

```TypeScript
export type ScrollOnWillScrollCallback = (xOffset: double, yOffset: double, scrollState: ScrollState, scrollSource: ScrollSource) => (undefined | OffsetResult)
```

Scroll滚动前触发的回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type ScrollOnWillScrollCallback = (xOffset: double, yOffset: double, scrollState: ScrollState, scrollSource: ScrollSource) => (undefined | OffsetResult)--><!--Device-unnamed-export type ScrollOnWillScrollCallback = (xOffset: double, yOffset: double, scrollState: ScrollState, scrollSource: ScrollSource) => (undefined | OffsetResult)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| xOffset | double | 是 | 相对于上一帧水平方向的偏移量，Scroll中的内容向左滚动时偏移量为正，向右滚动时偏移量为负。\_\_\_HTML\_TAG\_USD\_0\_\_\_单位vp。  |
| yOffset | double | 是 | 相对于上一帧竖直方向的偏移量，Scroll中的内容向上滚动时偏移量为正，向下滚动时偏移量为负。\_\_\_HTML\_TAG\_USD\_0\_\_\_单位vp。  |
| scrollState | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 当前滚动状态。  |
| scrollSource | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 当前滚动操作的来源。  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| (undefined \| OffsetResult) | the remain offset for the Scroll, |

