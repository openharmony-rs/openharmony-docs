# MetadataOutput

metadata流。继承[CameraOutput](arkts-camera-camera-cameraoutput-i.md)。

**继承/实现关系：** MetadataOutput extends [CameraOutput](arkts-camera-camera-cameraoutput-i.md)

**起始版本：** 23

<!--Device-camera-interface MetadataOutput--><!--Device-camera-interface MetadataOutput-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
import { cameraPicker } from '@kit.CameraKit';
```

## addMetadataObjectTypes

```TypeScript
addMetadataObjectTypes(types: Array<MetadataObjectType>): void
```

新增需要上报的检测对象类型。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-MetadataOutput-addMetadataObjectTypes(types: Array<MetadataObjectType>): void--><!--Device-MetadataOutput-addMetadataObjectTypes(types: Array<MetadataObjectType>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| types | Array&lt;[MetadataObjectType](arkts-camera-camera-metadataobjecttype-e.md)&gt; | 是 | metadata流类型信息，通过getSupportedOutputCapability接口获取。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.<br>**适用版本：** 13 - 22 |

## removeMetadataObjectTypes

```TypeScript
removeMetadataObjectTypes(types: Array<MetadataObjectType>): void
```

删除需要上报的检测对象类型。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-MetadataOutput-removeMetadataObjectTypes(types: Array<MetadataObjectType>): void--><!--Device-MetadataOutput-removeMetadataObjectTypes(types: Array<MetadataObjectType>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| types | Array&lt;[MetadataObjectType](arkts-camera-camera-metadataobjecttype-e.md)&gt; | 是 | metadata流类型信息，通过getSupportedOutputCapability接口获取。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.<br>**适用版本：** 13 - 22 |

