# Session

```TypeScript
interface Session
```

会话类，保存一次相机运行所需要的所有资源[CameraInput](arkts-camera-camera-camerainput-i.md)、[CameraOutput](arkts-camera-camera-cameraoutput-i.md)，并向相机设备申请完成相机功能（录像，拍照）。

**起始版本：** 11

<!--Device-camera-interface Session--><!--Device-camera-interface Session-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## getActiveParameter

```TypeScript
getActiveParameter(key: string): string
```

获取相机元数据中指定键的当前生效值。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Session-getActiveParameter(key: string): string--><!--Device-Session-getActiveParameter(key: string): string-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 相机元数据中的标签名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 相机元数据中该键的当前生效值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## getCameraOutputCapabilities

```TypeScript
getCameraOutputCapabilities(camera: CameraDevice): Array<CameraOutputCapability>
```

获取支持相机输出能力集合。

**起始版本：** 13

<!--Device-Session-getCameraOutputCapabilities(camera: CameraDevice): Array<CameraOutputCapability>--><!--Device-Session-getCameraOutputCapabilities(camera: CameraDevice): Array<CameraOutputCapability>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| camera | [CameraDevice](arkts-camera-camera-cameradevice-i.md) | 是 | 相机设备。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[CameraOutputCapability](arkts-camera-camera-cameraoutputcapability-i.md)&gt; | 输出能力数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## getParameters

```TypeScript
getParameters(key: string): Array<string>
```

获取相机元数据中指定键的值。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Session-getParameters(key: string): Array<string>--><!--Device-Session-getParameters(key: string): Array<string>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 相机元数据中的标签名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 相机元数据中该键对应的值数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## getSupportedKeys

```TypeScript
getSupportedKeys(): Array<string>
```

获取相机元数据中支持的键。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Session-getSupportedKeys(): Array<string>--><!--Device-Session-getSupportedKeys(): Array<string>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 相机元数据中支持的键数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## setParameters

```TypeScript
setParameters(kvpairs: Record<string, string>): void
```

设置会话的键值对参数。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Session-setParameters(kvpairs: Record<string, string>): void--><!--Device-Session-setParameters(kvpairs: Record<string, string>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| kvpairs | Record&lt;string, string&gt; | 是 | 相机元数据中标签名和值的键值对。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## setUsage

```TypeScript
setUsage(usage: UsageType, enabled: boolean): void
```

设置会话的使用类型。

**起始版本：** 13

<!--Device-Session-setUsage(usage: UsageType, enabled: boolean): void--><!--Device-Session-setUsage(usage: UsageType, enabled: boolean): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| usage | [UsageType](arkts-camera-camera-usagetype-e-sys.md) | 是 | 拍照会话使用类型。 |
| enabled | boolean | 是 | 是否为会话启用该使用类型。true表示启用，false表示不启用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |
