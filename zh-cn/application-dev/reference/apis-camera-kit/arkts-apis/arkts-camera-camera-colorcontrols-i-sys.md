# ColorControls（系统接口）

```TypeScript
interface ColorControls extends ColorControlsQuery
```

实现色彩控制功能。它继承自[ColorControlsQuery](arkts-camera-camera-colorcontrolsquery-i-sys.md).

**继承/实现关系：** ColorControls extends [ColorControlsQuery](arkts-camera-camera-colorcontrolsquery-i-sys.md)

**起始版本：** 26.0.1

<!--Device-camera-interface ColorControls extends ColorControlsQuery--><!--Device-camera-interface ColorControls extends ColorControlsQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## getRGBBias

```TypeScript
getRGBBias(): RGBBias
```

获取RGB偏置值。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColorControls-getRGBBias(): RGBBias--><!--Device-ColorControls-getRGBBias(): RGBBias-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 当前RGB偏置值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## getSaturation

```TypeScript
getSaturation(): number
```

获取饱和度值。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColorControls-getSaturation(): double--><!--Device-ColorControls-getSaturation(): double-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 当前饱和度值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## setRGBBias

```TypeScript
setRGBBias(bias: RGBBias): void
```

设置RGB偏置值。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColorControls-setRGBBias(bias: RGBBias): void--><!--Device-ColorControls-setRGBBias(bias: RGBBias): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bias | [RGBBias](arkts-camera-camera-rgbbias-i-sys.md) | 是 | RGB偏置值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## setSaturation

```TypeScript
setSaturation(val: number): void
```

设置饱和度值。在进行设置前，需调用[isSaturationSupported](arkts-camera-camera-colorcontrolsquery-i-sys.md#issaturationsupported)检查当前设备是否支持饱和度调整。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColorControls-setSaturation(val: double): void--><!--Device-ColorControls-setSaturation(val: double): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | number | 是 | 要应用的饱和度值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
