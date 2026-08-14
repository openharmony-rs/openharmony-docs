# OnScrollFrameBeginCallback

```TypeScript
export type OnScrollFrameBeginCallback = (offset: double, state: ScrollState) => OnScrollFrameBeginHandlerResult
```

Scroll每帧滚动前触发的回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type OnScrollFrameBeginCallback = (offset: double, state: ScrollState) => OnScrollFrameBeginHandlerResult--><!--Device-unnamed-export type OnScrollFrameBeginCallback = (offset: double, state: ScrollState) => OnScrollFrameBeginHandlerResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | double | 是 | 即将发生的滑动量，单位vp。 |
| state | [ScrollState](../../apis-arkui/arkts-components/arkts-arkui-scrollstate-e.md) | 是 | 当前滑动状态。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [OnScrollFrameBeginHandlerResult](arkts-na-scroll-onscrollframebeginhandlerresult-i.md) | 返回实际滑动量。 |

