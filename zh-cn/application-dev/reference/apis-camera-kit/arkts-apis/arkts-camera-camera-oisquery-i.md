# OISQuery

OIS (Optical Image Stabilization) query interface.

**起始版本：** 24

<!--Device-camera-interface OISQuery--><!--Device-camera-interface OISQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
import { cameraPicker } from '@kit.CameraKit';
```

## getCurrentCustomOISBias

```TypeScript
getCurrentCustomOISBias(oisAxis: OISAxes): double
```

Gets the current custom bias value for the specified OIS axis.

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-OISQuery-getCurrentCustomOISBias(oisAxis: OISAxes): double--><!--Device-OISQuery-getCurrentCustomOISBias(oisAxis: OISAxes): double-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| oisAxis | [OISAxes](arkts-camera-camera-oisaxes-e.md) | 是 | The OIS axis |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | The current bias value. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed, the inputDevice or the session is abnormal. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## getCurrentOISMode

```TypeScript
getCurrentOISMode(): OISMode
```

Gets the current OIS mode.

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-OISQuery-getCurrentOISMode(): OISMode--><!--Device-OISQuery-getCurrentOISMode(): OISMode-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [OISMode](arkts-camera-camera-oismode-e.md) | The current OIS mode. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed, the inputDevice or the session is abnormal. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## getSupportedOISBiasRange

```TypeScript
getSupportedOISBiasRange(oisAxis: OISAxes): Array<double>
```

Gets the supported bias range for the specified OIS axis.

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-OISQuery-getSupportedOISBiasRange(oisAxis: OISAxes): Array<double>--><!--Device-OISQuery-getSupportedOISBiasRange(oisAxis: OISAxes): Array<double>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| oisAxis | [OISAxes](arkts-camera-camera-oisaxes-e.md) | 是 | The OIS axis. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;double&gt; | The bias range. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed, the inputDevice or the session is abnormal. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## getSupportedOISBiasStep

```TypeScript
getSupportedOISBiasStep(oisAxis: OISAxes): double
```

Gets the bias step for the specified OIS axis.

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-OISQuery-getSupportedOISBiasStep(oisAxis: OISAxes): double--><!--Device-OISQuery-getSupportedOISBiasStep(oisAxis: OISAxes): double-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| oisAxis | [OISAxes](arkts-camera-camera-oisaxes-e.md) | 是 | The OIS axis. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | The bias step value. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed, the inputDevice or the session is abnormal. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## isOISModeSupported

```TypeScript
isOISModeSupported(mode: OISMode): boolean
```

Checks if the specified OIS mode is supported.

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-OISQuery-isOISModeSupported(mode: OISMode): boolean--><!--Device-OISQuery-isOISModeSupported(mode: OISMode): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [OISMode](arkts-camera-camera-oismode-e.md) | 是 | The OIS mode to check. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Whether the mode is supported. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed, the inputDevice or the session is abnormal. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

