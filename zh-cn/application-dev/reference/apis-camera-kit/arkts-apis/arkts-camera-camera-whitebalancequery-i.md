# WhiteBalanceQuery

提供了查询设备对指定的白平衡模式是否支持，以及获取设备支持的白平衡模式范围的方法。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-camera-interface WhiteBalanceQuery--><!--Device-camera-interface WhiteBalanceQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## getColorTintRange

ArkTS-Dyn:
```TypeScript
getColorTintRange(): Array<number>
```

ArkTS-Sta:
```TypeScript
getColorTintRange(): Array<int>
```

获取支持配置的白平衡色调调节范围。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-WhiteBalanceQuery-getColorTintRange(): Array<int>--><!--Device-WhiteBalanceQuery-getColorTintRange(): Array<int>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: Array&lt;number&gt;  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：Array&lt;int&gt; | 用于获取色调调节值的可调范围。若接口调用失败，返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |

## getWhiteBalanceRange

ArkTS-Dyn:
```TypeScript
getWhiteBalanceRange(): Array<number>
```

ArkTS-Sta:
```TypeScript
getWhiteBalanceRange(): Array<int>
```

获取手动白平衡模式下，白平衡值的范围。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-WhiteBalanceQuery-getWhiteBalanceRange(): Array<int>--><!--Device-WhiteBalanceQuery-getWhiteBalanceRange(): Array<int>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: Array&lt;number&gt;  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：Array&lt;int&gt; | 用于获取手动白平衡值的可调范围，如[2800，10000]，单位为K（Kelvin，温度单位），实际情况根据底层能力返回为准。若接口调用失败，返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12 - 19 |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |

## isWhiteBalanceGainsSupported

```TypeScript
isWhiteBalanceGainsSupported(): boolean
```

Checks whether the RGB gain is supported.

**起始版本：** 26.1.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.1.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WhiteBalanceQuery-isWhiteBalanceGainsSupported(): boolean--><!--Device-WhiteBalanceQuery-isWhiteBalanceGainsSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Check result for the support of the RGB gain. **true** if supported, **false** |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## isWhiteBalanceModeSupported

```TypeScript
isWhiteBalanceModeSupported(mode: WhiteBalanceMode): boolean
```

检测是否支持当前传入的白平衡模式。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-WhiteBalanceQuery-isWhiteBalanceModeSupported(mode: WhiteBalanceMode): boolean--><!--Device-WhiteBalanceQuery-isWhiteBalanceModeSupported(mode: WhiteBalanceMode): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 白平衡模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示是否支持白平衡模式。true表示支持，false表示不支持。若接口调用失败，返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12 - 19 |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |

