# FlashQuery

```TypeScript
interface FlashQuery
```

提供了查询设备的闪光灯状态和模式的能力。

> **说明：** 
> 
> - 本Interface的起始版本为API版本12。接口在API版本12发生兼容变更，保留了内层元素的起始版本信息，会出现外层元素@since版本号大于内层元素的情况，不影响接口使用。

**起始版本：** 12

<!--Device-camera-interface FlashQuery--><!--Device-camera-interface FlashQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## isLcdFlashSupported

```TypeScript
isLcdFlashSupported(): boolean
```

检测是否支持LCD闪光灯。

**起始版本：** 12

<!--Device-FlashQuery-isLcdFlashSupported(): boolean--><!--Device-FlashQuery-isLcdFlashSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检测是否支持LCD闪光灯的结果。**true**表示支持，**false**表示不支持。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |

<!--Del-->
**示例**

```TypeScript
function isLcdFlashSupported(nightPhotoSession: camera.NightPhotoSession): boolean {
  return nightPhotoSession.isLcdFlashSupported();
}
```

<!--DelEnd-->
