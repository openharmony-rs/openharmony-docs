# Portrait（系统接口）

```TypeScript
interface Portrait extends PortraitQuery
```

提供人像拍照设置相关接口。

**继承/实现关系：** Portrait extends [PortraitQuery](arkts-camera-camera-portraitquery-i-sys.md)

**起始版本：** 11

<!--Device-camera-interface Portrait extends PortraitQuery--><!--Device-camera-interface Portrait extends PortraitQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## getPortraitEffect

```TypeScript
getPortraitEffect(): PortraitEffect
```

获取当前使用的人像效果。

**起始版本：** 10

<!--Device-Portrait-getPortraitEffect(): PortraitEffect--><!--Device-Portrait-getPortraitEffect(): PortraitEffect-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PortraitEffect](arkts-camera-camera-portraiteffect-e-sys.md) | 人像效果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application.<br>**适用版本：** 11+ |

<!--Del-->
**示例**

```TypeScript
function getPortraitEffect(portraitPhotoSession: camera.PortraitPhotoSession): camera.PortraitEffect {
  let portraitEffect: camera.PortraitEffect = portraitPhotoSession.getPortraitEffect();
  return portraitEffect;
}
```

<!--DelEnd-->

## setPortraitEffect

```TypeScript
setPortraitEffect(effect: PortraitEffect): void
```

设置人像效果。设置前，先通过[getSupportedPortraitEffects](arkts-camera-camera-portraitquery-i-sys.md#getsupportedportraiteffects)获取支持的人像效果，并检查是否支持目标人像效果。

**起始版本：** 10

<!--Device-Portrait-setPortraitEffect(effect: PortraitEffect): void--><!--Device-Portrait-setPortraitEffect(effect: PortraitEffect): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| effect | [PortraitEffect](arkts-camera-camera-portraiteffect-e-sys.md) | 是 | 待设置的人像效果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application.<br>**适用版本：** 11+ |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function setPortraitEffect(portraitPhotoSession: camera.PortraitPhotoSession, portraitEffects: Array<camera.PortraitEffect>): void {
  if (portraitEffects === undefined || portraitEffects.length <= 0) {
    return;
  }
  try {
    portraitPhotoSession.setPortraitEffect(portraitEffects[0]);
  } catch (error) {
    let err = error as BusinessError;
    console.error(`The setPortraitEffect call failed. error code: ${err.code}`);
  }
}
```

<!--DelEnd-->
