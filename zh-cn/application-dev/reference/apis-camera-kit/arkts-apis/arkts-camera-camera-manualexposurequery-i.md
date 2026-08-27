# ManualExposureQuery

Provides APIs to obtain the manual exposure range supported.

**起始版本：** 24

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
```

## getExposureBiasStep

```TypeScript
getExposureBiasStep(): number
```

Get exposure bias step.

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | exposure bias step. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed, session or inputdevice maybe abnormal. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## getSupportedExposureDurationRange

```TypeScript
getSupportedExposureDurationRange(): Array<number>
```

Gets the supported manual exposure duration range, units: microseconds.

**起始版本：** 24

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array & lt;number & gt; | The array of manual exposure range. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed, session or inputdevice maybe abnormal. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |
