# ManualFocus

ManualFocus object.

**继承/实现关系：** ManualFocus extends [ManualFocusQuery](arkts-camera-camera-manualfocusquery-i.md)

**起始版本：** 24

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
```

## getFocusDistance

```TypeScript
getFocusDistance(): number
```

Gets current focus distance, ranging from 0.0 to 1.0, with 0.0 being shortest distance at which the lens can focus and 1.0 the furthest. The default value is 1.0.

**起始版本：** 24

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | The current focus distance. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.<br>**适用版本：** 12 - 23 |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed, the inputDevice or the session is abnormal.<br>**适用版本：** 24+ |

## setFocusDistance

```TypeScript
setFocusDistance(distance: number): void
```

Sets focus distance. Possible distance values range from 0.0 to 1.0, with 0.0 being shortest distance at which the lens can focus and 1.0 the furthest. The default value is 1.0.

**起始版本：** 24

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| distance | number | 是 | Focus distance. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.<br>**适用版本：** 12 - 23 |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect.<br>**适用版本：** 12 - 23 |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed, the inputDevice or the session is abnormal.<br>**适用版本：** 24+ |
