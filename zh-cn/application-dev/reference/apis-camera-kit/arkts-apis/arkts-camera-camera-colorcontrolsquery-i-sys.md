# ColorControlsQuery（系统接口）

```TypeScript
interface ColorControlsQuery
```

设备色彩控制查询对象。

**起始版本：** 26.0.1

<!--Device-camera-interface ColorControlsQuery--><!--Device-camera-interface ColorControlsQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## isRGBBiasSupported

```TypeScript
isRGBBiasSupported(): boolean
```

检查是否支持RGB偏移。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColorControlsQuery-isRGBBiasSupported(): boolean--><!--Device-ColorControlsQuery-isRGBBiasSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查RGB偏置支持的结果。true表示支持，false表示不支持。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## isSaturationSupported

```TypeScript
isSaturationSupported(): boolean
```

检查是否支持饱和度。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColorControlsQuery-isSaturationSupported(): boolean--><!--Device-ColorControlsQuery-isSaturationSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查对饱和度的支持结果。true表示支持，false表示不支持。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
