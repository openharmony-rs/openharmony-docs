# DynamicSyncScene

Represents a dynamic synchronization scene.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class DynamicSyncScene--><!--Device-unnamed-export declare class DynamicSyncScene-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getFrameRateRange

```TypeScript
getFrameRateRange(): ExpectedFrameRateRange
```

Gets the FrameRateRange of the DynamicSyncScene.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DynamicSyncScene-getFrameRateRange(): ExpectedFrameRateRange--><!--Device-DynamicSyncScene-getFrameRateRange(): ExpectedFrameRateRange-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ExpectedFrameRateRange](arkts-na-common-expectedframeraterange-i.md) | The range of frameRate. |

## setFrameRateRange

```TypeScript
setFrameRateRange(range: ExpectedFrameRateRange): void
```

Sets the FrameRateRange of the DynamicSyncScene.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DynamicSyncScene-setFrameRateRange(range: ExpectedFrameRateRange): void--><!--Device-DynamicSyncScene-setFrameRateRange(range: ExpectedFrameRateRange): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| range | [ExpectedFrameRateRange](arkts-na-common-expectedframeraterange-i.md) | 是 | The range of frameRate. |

