# Flash（系统接口）

```TypeScript
interface Flash extends FlashQuery
```

闪光灯类，对设备闪光灯操作。

**继承/实现关系：** Flash extends [FlashQuery](arkts-camera-camera-flashquery-i.md)

**起始版本：** 11

<!--Device-camera-interface Flash extends FlashQuery--><!--Device-camera-interface Flash extends FlashQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## enableLcdFlash

```TypeScript
enableLcdFlash(enabled: boolean): void
```

使能或去使能 LCD 闪光灯。

设置前，先通过[isLcdFlashSupported](arkts-camera-camera-flashquery-i-sys.md#islcdflashsupported)检查设备是否支持 LCD 闪光灯。

**起始版本：** 13

<!--Device-Flash-enableLcdFlash(enabled: boolean): void--><!--Device-Flash-enableLcdFlash(enabled: boolean): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 是否使能 LCD 闪光灯。**true**表示使能，**false**表示去使能。传参为null或者undefined，作为0处理，LCD 闪光灯关闭。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

<!--Del-->
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

<!--DelEnd-->
