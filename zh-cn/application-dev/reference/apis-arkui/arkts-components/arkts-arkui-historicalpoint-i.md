# HistoricalPoint

历史点信息。

**起始版本：** 10

<!--Device-unnamed-declare interface HistoricalPoint--><!--Device-unnamed-declare interface HistoricalPoint-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## force

```TypeScript
force: number
```

历史点对应触摸事件的压力大小。

默认值：0

取值范围：[0,65535)，压力越大，值越大。

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HistoricalPoint-force: number--><!--Device-HistoricalPoint-force: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size: number
```

历史点对应触摸事件中手指与屏幕的触摸区域大小。

默认值：0

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HistoricalPoint-size: number--><!--Device-HistoricalPoint-size: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## timestamp

```TypeScript
timestamp: number
```

历史点对应触摸事件的时间戳，表示触发事件时距离系统启动的时间间隔。

单位：ns

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HistoricalPoint-timestamp: number--><!--Device-HistoricalPoint-timestamp: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## touchObject

```TypeScript
touchObject: TouchObject
```

历史点对应触摸事件的基础信息。

**类型：** TouchObject

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HistoricalPoint-touchObject: TouchObject--><!--Device-HistoricalPoint-touchObject: TouchObject-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

