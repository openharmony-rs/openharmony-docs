# OnScrollEdgeCallback

```TypeScript
export type OnScrollEdgeCallback = (side: Edge) => void
```

滚动到边缘时触发的回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type OnScrollEdgeCallback = (side: Edge) => void--><!--Device-unnamed-export type OnScrollEdgeCallback = (side: Edge) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| side | [Edge](../../apis-arkui/arkts-apis/arkts-arkui-edge-e.md) | 是 | 滚动到的边缘位置。 |

