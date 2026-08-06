# Flash

Flash继承自[FlashQuery]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。 闪光灯类，对设备闪光灯操作。

**继承/实现关系：** Flash extends [FlashQuery](arkts-camera-camera-flashquery-i.md)

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-camera-interface Flash extends FlashQuery--><!--Device-camera-interface Flash extends FlashQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## enableLcdFlash

```TypeScript
enableLcdFlash(enabled: boolean): void
```

Enables or disables the LCD flash. Before the setting, call [isLcdFlashSupported]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ to check whether the device supports the LCD flash.

**起始版本：** 13

**ArkTS模式：** ArkTS-Dyn起始版本为13；ArkTS-Sta起始版本为23。

<!--Device-Flash-enableLcdFlash(enabled: boolean): void--><!--Device-Flash-enableLcdFlash(enabled: boolean): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | Whether to enable or disable the LCD flash. **true** to enable, **false** otherwise.If null or undefined is passed, it is treated as 0 and the LCD flash is disabled. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

**示例：**

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

