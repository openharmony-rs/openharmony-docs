# WhiteBalance

WhiteBalance继承自[WhiteBalanceQuery](arkts-camera-camera-whitebalancequery-i.md)。提供了处理设备白平衡的相关功能，包括获取和设置白平衡模式以及白平衡值。

**继承/实现关系：** WhiteBalance extends [WhiteBalanceQuery](arkts-camera-camera-whitebalancequery-i.md)

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
```

## getWhiteBalanceGains

```TypeScript
getWhiteBalanceGains(): WhiteBalanceGains
```

Gets RGB white balance gain values.

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WhiteBalanceGains](arkts-camera-camera-whitebalancegains-i-sys.md) | The current RGB white balance gain values. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## setWhiteBalanceGains

```TypeScript
setWhiteBalanceGains(gains: WhiteBalanceGains): void
```

Sets RGB white balance gain values.

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| gains | [WhiteBalanceGains](arkts-camera-camera-whitebalancegains-i-sys.md) | 是 | RGB white balance gain values. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
