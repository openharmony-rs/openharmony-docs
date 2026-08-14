# DynamicSyncScene

Represents a dynamic synchronization scene.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-unnamed-export class DynamicSyncScene--><!--Device-unnamed-export class DynamicSyncScene-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getFrameRateRange

```TypeScript
getFrameRateRange(): ExpectedFrameRateRange
```

Gets the FrameRateRange of the DynamicSyncScene.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DynamicSyncScene-getFrameRateRange(): ExpectedFrameRateRange--><!--Device-DynamicSyncScene-getFrameRateRange(): ExpectedFrameRateRange-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ExpectedFrameRateRange](../../apis-na/arkts-apis/arkts-na-common-expectedframeraterange-i.md) | The range of frameRate. |

## setFrameRateRange

```TypeScript
setFrameRateRange(range: ExpectedFrameRateRange): void
```

Sets the FrameRateRange of the DynamicSyncScene.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DynamicSyncScene-setFrameRateRange(range: ExpectedFrameRateRange): void--><!--Device-DynamicSyncScene-setFrameRateRange(range: ExpectedFrameRateRange): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| range | [ExpectedFrameRateRange](../../apis-na/arkts-apis/arkts-na-common-expectedframeraterange-i.md) | 是 | The range of frameRate. |

