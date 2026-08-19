# ExposureMeteringMode（系统接口）

枚举，曝光测光模式。

**起始版本：** 23

<!--Device-camera-enum ExposureMeteringMode--><!--Device-camera-enum ExposureMeteringMode-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## MATRIX

```TypeScript
MATRIX = 0
```

矩阵测光模式。对画面广泛区域进行测光，适合拍摄自然风光。

**起始版本：** 23

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-ExposureMeteringMode-MATRIX = 0--><!--Device-ExposureMeteringMode-MATRIX = 0-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## CENTER

```TypeScript
CENTER = 1
```

中心测光模式。对整个画面进行测光，但最大比重分配给中央区域，适合拍摄人像。

**起始版本：** 23

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-ExposureMeteringMode-CENTER = 1--><!--Device-ExposureMeteringMode-CENTER = 1-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## SPOT

```TypeScript
SPOT = 2
```

点测光模式。对画面测光点周围约2.5%进行测光，专注于特定微小区域的光线，如被摄主体的眼睛。

**起始版本：** 23

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-ExposureMeteringMode-SPOT = 2--><!--Device-ExposureMeteringMode-SPOT = 2-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## CENTER_HIGHLIGHT_WEIGHTED

```TypeScript
CENTER_HIGHLIGHT_WEIGHTED = 3
```

Center-weighted and highlight metering mode. This mode focuses on the highlight area near the center of the screen.

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExposureMeteringMode-CENTER_HIGHLIGHT_WEIGHTED = 3--><!--Device-ExposureMeteringMode-CENTER_HIGHLIGHT_WEIGHTED = 3-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

