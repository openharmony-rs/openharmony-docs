# WhiteBalanceQuery（系统接口）

提供了查询设备对指定的白平衡模式是否支持，以及获取设备支持的白平衡模式范围的方法。

**起始版本：** 23

<!--Device-camera-interface WhiteBalanceQuery--><!--Device-camera-interface WhiteBalanceQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
import { cameraPicker } from '@kit.CameraKit';
```

## getWhiteBalanceRange

```TypeScript
getWhiteBalanceRange(): Array<int>
```

获取手动白平衡模式下，白平衡值的范围。

**起始版本：** 23

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-WhiteBalanceQuery-getWhiteBalanceRange(): Array<int>--><!--Device-WhiteBalanceQuery-getWhiteBalanceRange(): Array<int>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;int&gt; | 用于获取手动白平衡值的可调范围，如[2800，10000]，单位为K（Kelvin，温度单位），实际情况根据底层能力返回为准。若接口调用失败，返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.<br>**适用版本：** 12 - 19 |

## isWhiteBalanceGainsSupported

```TypeScript
isWhiteBalanceGainsSupported(): boolean
```

Checks whether the RGB gain is supported.

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WhiteBalanceQuery-isWhiteBalanceGainsSupported(): boolean--><!--Device-WhiteBalanceQuery-isWhiteBalanceGainsSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Check result for the support of the RGB gain. **true** if supported, **false** otherwise. If the operation fails, an error code defined in [CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## isWhiteBalanceModeSupported

```TypeScript
isWhiteBalanceModeSupported(mode: WhiteBalanceMode): boolean
```

检测是否支持当前传入的白平衡模式。

**起始版本：** 23

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-WhiteBalanceQuery-isWhiteBalanceModeSupported(mode: WhiteBalanceMode): boolean--><!--Device-WhiteBalanceQuery-isWhiteBalanceModeSupported(mode: WhiteBalanceMode): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [WhiteBalanceMode](arkts-camera-camera-whitebalancemode-e-sys.md) | 是 | 白平衡模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示是否支持白平衡模式。true表示支持，false表示不支持。若接口调用失败，返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.<br>**适用版本：** 12 - 19 |

