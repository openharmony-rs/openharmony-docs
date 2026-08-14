# FrameNodeOptions

FrameNode选项，可设置FrameNode是否支持多线程操作。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export declare interface FrameNodeOptions--><!--Device-unnamed-export declare interface FrameNodeOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## supportMultiThread

```TypeScript
supportMultiThread?: boolean
```

FrameNode是否支持多线程操作。 true表示支持多线程操作，该节点可以在多线程场景中使用。 false或不设置表示不支持多线程操作。 默认为false。

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNodeOptions-supportMultiThread?: boolean--><!--Device-FrameNodeOptions-supportMultiThread?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

