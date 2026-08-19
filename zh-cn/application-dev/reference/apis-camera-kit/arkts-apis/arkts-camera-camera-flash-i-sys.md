# Flash

Flash继承自[FlashQuery](arkts-camera-camera-flashquery-i.md)。 闪光灯类，对设备闪光灯操作。

**继承/实现关系：** Flash extends [FlashQuery](arkts-camera-camera-flashquery-i.md)

**起始版本：** 23

<!--Device-camera-interface Flash--><!--Device-camera-interface Flash-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
import { cameraPicker } from '@kit.CameraKit';
```

## enableLcdFlash

```TypeScript
enableLcdFlash(enabled: boolean): void
```

Enables or disables the LCD flash. Before the setting, call [isLcdFlashSupported](arkts-camera-camera-flashquery-i-sys.md#islcdflashsupported) to check whether the device supports the LCD flash.

**起始版本：** 23

<!--Device-Flash-enableLcdFlash(enabled: boolean): void--><!--Device-Flash-enableLcdFlash(enabled: boolean): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | Whether to enable or disable the LCD flash. **true** to enable, **false** otherwise. If null or undefined is passed, it is treated as 0 and the LCD flash is disabled. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function enableLcdFlash(session: camera.PhotoSessionForSys | camera.VideoSessionForSys | camera.NightPhotoSession): void {
  try {
    session.enableLcdFlash(true);
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The setFlashMode call failed. error code: ${err.code}`);
  }
}
```

