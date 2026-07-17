# SnapshotOptions

定义截图额外选项。

**起始版本：** 12

<!--Device-componentSnapshot-interface SnapshotOptions--><!--Device-componentSnapshot-interface SnapshotOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { componentSnapshot } from '@kit.ArkUI';
```

## colorMode

```TypeScript
colorMode?: ColorModeOptions
```

指定截图使用的色彩空间。

默认值：{colorSpace: SRGB, isAuto: false}

**类型：** ColorModeOptions

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-SnapshotOptions-colorMode?: ColorModeOptions--><!--Device-SnapshotOptions-colorMode?: ColorModeOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## dynamicRangeMode

```TypeScript
dynamicRangeMode?: DynamicRangeModeOptions
```

指定截图使用的动态范围模式。

默认值：{dynamicRangeMode: STANDARD, isAuto: false}

**类型：** DynamicRangeModeOptions

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-SnapshotOptions-dynamicRangeMode?: DynamicRangeModeOptions--><!--Device-SnapshotOptions-dynamicRangeMode?: DynamicRangeModeOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## region

```TypeScript
region?: SnapshotRegionType
```

指定截图的矩形区域范围，默认为整个组件。

**类型：** SnapshotRegionType

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-SnapshotOptions-region?: SnapshotRegionType--><!--Device-SnapshotOptions-region?: SnapshotRegionType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scale

```TypeScript
scale?: number
```

指定截图时图形侧绘制pixelmap的缩放比例，比例过大时截图时间会变长，或者截图可能会失败。

取值范围：[0, +∞)，当小于等于0时按默认情况处理。

默认值：1

**说明：**

请不要截取过大尺寸的图片，截图不建议超过屏幕尺寸的大小。当要截取的图片目标长宽超过底层限制时，截图会返回失败，不同设备的底层限制不同。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SnapshotOptions-scale?: number--><!--Device-SnapshotOptions-scale?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## waitUntilRenderFinished

```TypeScript
waitUntilRenderFinished?: boolean
```

设置是否强制系统在截图前等待所有绘制指令执行完毕。true表示强制系统在截图前等待所有绘制指令执行完毕，false表示不强制系统在截图前等待所有绘制指令执行完毕。该选项可尽可能确保截图内容是最新的状态，应尽量开启。需要注意的是，开启后接口可能需要更长的时间返回，具体的时间依赖页面当时时刻需要重绘区域的大小。

默认值：false

**类型：** boolean

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SnapshotOptions-waitUntilRenderFinished?: boolean--><!--Device-SnapshotOptions-waitUntilRenderFinished?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

