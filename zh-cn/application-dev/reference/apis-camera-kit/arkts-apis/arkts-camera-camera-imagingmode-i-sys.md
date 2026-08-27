# ImagingMode（系统接口）

Implements imaging mode.

**继承/实现关系：** ImagingMode extends [ImagingModeQuery](arkts-camera-camera-imagingmodequery-i-sys.md)

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
```

## getImagingMode

```TypeScript
getImagingMode(): CameraImagingMode
```

Gets current imaging mode.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CameraImagingMode](arkts-camera-camera-cameraimagingmode-e-sys.md) | The current imaging mode. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## setImagingMode

```TypeScript
setImagingMode(mode: CameraImagingMode): void
```

Sets imaging mode.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [CameraImagingMode](arkts-camera-camera-cameraimagingmode-e-sys.md) | 是 | Target imaging mode. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
