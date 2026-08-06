# WhiteBalance

WhiteBalance继承自[WhiteBalanceQuery]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。 提供了处理设备白平衡的相关功能，包括获取和设置白平衡模式以及白平衡值。

**继承/实现关系：** WhiteBalance extends [WhiteBalanceQuery](arkts-camera-camera-whitebalancequery-i.md)

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-camera-interface WhiteBalance extends WhiteBalanceQuery--><!--Device-camera-interface WhiteBalance extends WhiteBalanceQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## getColorTint

ArkTS-Dyn:
```TypeScript
getColorTint(): number
```

ArkTS-Sta:
```TypeScript
getColorTint(): int
```

获取当前白平衡的色调调节值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-WhiteBalance-getColorTint(): int--><!--Device-WhiteBalance-getColorTint(): int-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 返回当前白平衡色调调节值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## getWhiteBalance

ArkTS-Dyn:
```TypeScript
getWhiteBalance(): number
```

ArkTS-Sta:
```TypeScript
getWhiteBalance(): int
```

获取当前手动白平衡的值。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-WhiteBalance-getWhiteBalance(): int--><!--Device-WhiteBalance-getWhiteBalance(): int-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 返回当前白平衡值，单位为K（Kelvin，温度单位）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12 - 19 |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## getWhiteBalanceGains

```TypeScript
getWhiteBalanceGains(): WhiteBalanceGains
```

Gets RGB white balance gain values.

**起始版本：** 26.1.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.1.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WhiteBalance-getWhiteBalanceGains(): WhiteBalanceGains--><!--Device-WhiteBalance-getWhiteBalanceGains(): WhiteBalanceGains-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | The current RGB white balance gain values. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## getWhiteBalanceMode

```TypeScript
getWhiteBalanceMode(): WhiteBalanceMode
```

获取当前白平衡模式。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-WhiteBalance-getWhiteBalanceMode(): WhiteBalanceMode--><!--Device-WhiteBalance-getWhiteBalanceMode(): WhiteBalanceMode-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 获取当前白平衡模式。若接口调用失败，返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12 - 19 |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## setColorTint

ArkTS-Dyn:
```TypeScript
setColorTint(colorTint: number): void
```

ArkTS-Sta:
```TypeScript
setColorTint(colorTint: int): void
```

设置白平衡的色调调节值。 设置之前需要先检查设备支持配置的白平衡色调调节范围，具体方法请参考[getColorTintRange]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-WhiteBalance-setColorTint(colorTint: int): void--><!--Device-WhiteBalance-setColorTint(colorTint: int): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| colorTint | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 设置手动白平衡色调调节值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## setWhiteBalance

ArkTS-Dyn:
```TypeScript
setWhiteBalance(whiteBalance: number): void
```

ArkTS-Sta:
```TypeScript
setWhiteBalance(whiteBalance: int): void
```

设置手动白平衡值。 设置之前需要先检查设备支持的白平衡值范围，具体方法请参考[getWhiteBalanceRange]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-WhiteBalance-setWhiteBalance(whiteBalance: int): void--><!--Device-WhiteBalance-setWhiteBalance(whiteBalance: int): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| whiteBalance | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 设置手动白平衡值，单位为K（Kelvin，温度单位）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12 - 19 |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## setWhiteBalanceGains

```TypeScript
setWhiteBalanceGains(gains: WhiteBalanceGains): void
```

Sets RGB white balance gain values.

**起始版本：** 26.1.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.1.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WhiteBalance-setWhiteBalanceGains(gains: WhiteBalanceGains): void--><!--Device-WhiteBalance-setWhiteBalanceGains(gains: WhiteBalanceGains): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| gains | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | RGB white balance gain values. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## setWhiteBalanceMode

```TypeScript
setWhiteBalanceMode(mode: WhiteBalanceMode): void
```

设置白平衡模式。设置之前需要先检查设备是否支持指定的白平衡模式，具体方法请参考 [isWhiteBalanceModeSupported]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-WhiteBalance-setWhiteBalanceMode(mode: WhiteBalanceMode): void--><!--Device-WhiteBalance-setWhiteBalanceMode(mode: WhiteBalanceMode): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 白平衡模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12 - 19 |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

