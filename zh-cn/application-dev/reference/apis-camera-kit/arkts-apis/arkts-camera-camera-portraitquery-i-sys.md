# PortraitQuery（系统接口）

```TypeScript
interface PortraitQuery
```

查询人像参数。

**起始版本：** 12

<!--Device-camera-interface PortraitQuery--><!--Device-camera-interface PortraitQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## getSupportedPortraitEffects

```TypeScript
getSupportedPortraitEffects(): Array<PortraitEffect>
```

获取支持的人像效果。

**起始版本：** 10

<!--Device-PortraitQuery-getSupportedPortraitEffects(): Array<PortraitEffect>--><!--Device-PortraitQuery-getSupportedPortraitEffects(): Array<PortraitEffect>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[PortraitEffect](arkts-camera-camera-portraiteffect-e-sys.md)&gt; | 支持的人像效果数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application.<br>**适用版本：** 11+ |

<!--Del-->
**示例**

```TypeScript
function getSupportedPortraitEffects(portraitPhotoSession: camera.PortraitPhotoSession): Array<camera.PortraitEffect> {
  let portraitEffects: Array<camera.PortraitEffect> = portraitPhotoSession.getSupportedPortraitEffects();
  return portraitEffects;
}
```

<!--DelEnd-->
