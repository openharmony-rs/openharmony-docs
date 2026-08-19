# FlashQuery

提供了查询设备的闪光灯状态和模式的能力。 > **说明：** > > - 本Interface的起始版本为API version 12。接口在API version 12发生兼容变更，保留了内层元素的起始版本信息，会出现外层元素@since版本号大于内层元素的情况，不影响接口使用。

**起始版本：** 23

<!--Device-camera-interface FlashQuery--><!--Device-camera-interface FlashQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
import { cameraPicker } from '@kit.CameraKit';
```

## hasFlash

```TypeScript
hasFlash(): boolean
```

检测是否有闪光灯，返回是否支持闪光灯。

**起始版本：** 23

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-FlashQuery-hasFlash(): boolean--><!--Device-FlashQuery-hasFlash(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示设备是否支持闪光灯。true表示支持闪光灯，false表示不支持闪光灯。 <br>如果返回false，则[isFlashModeSupported]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |

## isFlashModeSupported

```TypeScript
isFlashModeSupported(flashMode: FlashMode): boolean
```

检测闪光灯模式是否支持。

**起始版本：** 23

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-FlashQuery-isFlashModeSupported(flashMode: FlashMode): boolean--><!--Device-FlashQuery-isFlashModeSupported(flashMode: FlashMode): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| flashMode | [FlashMode](arkts-camera-camera-flashmode-e.md) | 是 | 指定闪光灯模式。传参为null或者undefined，作为0处理，闪光灯关闭。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检测表示支持该闪光灯模式。true表示支持，false表示不支持。接口调用失败会抛出相应错误码并返回undefined，错误码类型 [CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |

