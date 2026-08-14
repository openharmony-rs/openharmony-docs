# WhiteBalance（系统接口）

WhiteBalance继承自[WhiteBalanceQuery](arkts-camera-camera-whitebalancequery-i.md#WhiteBalanceQuery（系统接口）)。 提供了处理设备白平衡的相关功能，包括获取和设置白平衡模式以及白平衡值。

**继承/实现关系：** WhiteBalance extends [WhiteBalanceQuery](arkts-camera-camera-whitebalancequery-i.md#WhiteBalanceQuery（系统接口）)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-camera-interface WhiteBalance--><!--Device-camera-interface WhiteBalance-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## getWhiteBalance

```TypeScript
getWhiteBalance(): int
```

获取当前手动白平衡的值。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-WhiteBalance-getWhiteBalance(): int--><!--Device-WhiteBalance-getWhiteBalance(): int-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回当前白平衡值，单位为K（Kelvin，温度单位）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.<br>**适用版本：** 12 - 19 |

## getWhiteBalanceGains

```TypeScript
getWhiteBalanceGains(): WhiteBalanceGains
```

Gets RGB white balance gain values.

**起始版本：** 26.1.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.1.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WhiteBalance-getWhiteBalanceGains(): WhiteBalanceGains--><!--Device-WhiteBalance-getWhiteBalanceGains(): WhiteBalanceGains-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WhiteBalanceGains](arkts-camera-camera-whitebalancegains-i-sys.md) | The current RGB white balance gain values. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## getWhiteBalanceMode

```TypeScript
getWhiteBalanceMode(): WhiteBalanceMode
```

获取当前白平衡模式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-WhiteBalance-getWhiteBalanceMode(): WhiteBalanceMode--><!--Device-WhiteBalance-getWhiteBalanceMode(): WhiteBalanceMode-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WhiteBalanceMode](arkts-camera-camera-whitebalancemode-e-sys.md) | 获取当前白平衡模式。若接口调用失败，返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.<br>**适用版本：** 12 - 19 |

## setWhiteBalance

```TypeScript
setWhiteBalance(whiteBalance: int): void
```

设置手动白平衡值。 设置之前需要先检查设备支持的白平衡值范围，具体方法请参考[getWhiteBalanceRange](arkts-camera-camera-whitebalancequery-i-sys.md#getWhiteBalanceRange)。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-WhiteBalance-setWhiteBalance(whiteBalance: int): void--><!--Device-WhiteBalance-setWhiteBalance(whiteBalance: int): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| whiteBalance | int | 是 | 设置手动白平衡值，单位为K（Kelvin，温度单位）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.<br>**适用版本：** 12 - 19 |

## setWhiteBalanceGains

```TypeScript
setWhiteBalanceGains(gains: WhiteBalanceGains): void
```

Sets RGB white balance gain values.

**起始版本：** 26.1.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.1.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WhiteBalance-setWhiteBalanceGains(gains: WhiteBalanceGains): void--><!--Device-WhiteBalance-setWhiteBalanceGains(gains: WhiteBalanceGains): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| gains | [WhiteBalanceGains](arkts-camera-camera-whitebalancegains-i-sys.md) | 是 | RGB white balance gain values. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## setWhiteBalanceMode

```TypeScript
setWhiteBalanceMode(mode: WhiteBalanceMode): void
```

设置白平衡模式。设置之前需要先检查设备是否支持指定的白平衡模式，具体方法请参考 [isWhiteBalanceModeSupported](arkts-camera-camera-whitebalancequery-i-sys.md#isWhiteBalanceModeSupported)。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-WhiteBalance-setWhiteBalanceMode(mode: WhiteBalanceMode): void--><!--Device-WhiteBalance-setWhiteBalanceMode(mode: WhiteBalanceMode): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [WhiteBalanceMode](arkts-camera-camera-whitebalancemode-e-sys.md) | 是 | 白平衡模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.<br>**适用版本：** 12 - 19 |

