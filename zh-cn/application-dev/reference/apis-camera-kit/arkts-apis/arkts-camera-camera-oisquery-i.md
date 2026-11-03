# OISQuery

```TypeScript
interface OISQuery
```

提供了与光学防抖（OIS）相关的查询能力。

**起始版本：** 24

<!--Device-camera-interface OISQuery--><!--Device-camera-interface OISQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## getCurrentCustomOISBias

```TypeScript
getCurrentCustomOISBias(oisAxis: OISAxes): number
```

获取指定光学防抖轴当前的自定义偏置值。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务中使用。

<!--Device-OISQuery-getCurrentCustomOISBias(oisAxis: OISAxes): double--><!--Device-OISQuery-getCurrentCustomOISBias(oisAxis: OISAxes): double-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| oisAxis | [OISAxes](arkts-camera-camera-oisaxes-e.md) | 是 | 指定的光学防抖轴。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 当前的自定义偏置值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed, the inputDevice or the session is abnormal. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## getCurrentOISMode

```TypeScript
getCurrentOISMode(): OISMode
```

获取当前的光学防抖模式。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务中使用。

<!--Device-OISQuery-getCurrentOISMode(): OISMode--><!--Device-OISQuery-getCurrentOISMode(): OISMode-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [OISMode](arkts-camera-camera-oismode-e.md) | 当前的光学防抖模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed, the inputDevice or the session is abnormal. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## getSupportedOISBiasRange

```TypeScript
getSupportedOISBiasRange(oisAxis: OISAxes): Array<number>
```

获取指定光学防抖轴支持的偏置范围。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务中使用。

<!--Device-OISQuery-getSupportedOISBiasRange(oisAxis: OISAxes): Array<double>--><!--Device-OISQuery-getSupportedOISBiasRange(oisAxis: OISAxes): Array<double>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| oisAxis | [OISAxes](arkts-camera-camera-oisaxes-e.md) | 是 | 指定的光学防抖轴。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;number&gt; | 支持的偏置范围。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed, the inputDevice or the session is abnormal. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## getSupportedOISBiasStep

```TypeScript
getSupportedOISBiasStep(oisAxis: OISAxes): number
```

获取指定光学防抖轴支持的偏置步长。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务中使用。

<!--Device-OISQuery-getSupportedOISBiasStep(oisAxis: OISAxes): double--><!--Device-OISQuery-getSupportedOISBiasStep(oisAxis: OISAxes): double-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| oisAxis | [OISAxes](arkts-camera-camera-oisaxes-e.md) | 是 | 指定的光学防抖轴。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 支持的偏置步长。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed, the inputDevice or the session is abnormal. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## isOISModeSupported

```TypeScript
isOISModeSupported(mode: OISMode): boolean
```

检查是否支持指定的光学防抖模式。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务中使用。

<!--Device-OISQuery-isOISModeSupported(mode: OISMode): boolean--><!--Device-OISQuery-isOISModeSupported(mode: OISMode): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [OISMode](arkts-camera-camera-oismode-e.md) | 是 | 指定的光学防抖模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示是否支持指定的光学防抖模式。true表示支持，false表示不支持。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed, the inputDevice or the session is abnormal. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
