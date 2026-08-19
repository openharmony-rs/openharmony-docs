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

## isLcdFlashSupported

```TypeScript
isLcdFlashSupported(): boolean
```

Checks whether the LCD flash is supported.

**起始版本：** 23

<!--Device-FlashQuery-isLcdFlashSupported(): boolean--><!--Device-FlashQuery-isLcdFlashSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Check result for the support of the LCD flash. **true** if supported, **false** otherwise. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

**示例**

```TypeScript
function isLcdFlashSupported(nightPhotoSession: camera.NightPhotoSession): boolean {
  return nightPhotoSession.isLcdFlashSupported();
}
```

