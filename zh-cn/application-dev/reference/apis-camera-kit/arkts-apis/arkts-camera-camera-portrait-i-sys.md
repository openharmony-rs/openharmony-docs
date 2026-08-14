# Portrait（系统接口）

Portrait: inherits from [PortraitQuery](arkts-camera-camera-portraitquery-i-sys.md#PortraitQuery（系统接口）). Provides the APIs for portrait photo settings.

**继承/实现关系：** Portrait extends [PortraitQuery](arkts-camera-camera-portraitquery-i-sys.md#PortraitQuery（系统接口）)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-camera-interface Portrait--><!--Device-camera-interface Portrait-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## getPortraitEffect

```TypeScript
getPortraitEffect(): PortraitEffect
```

Obtains the portrait effect in use.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Portrait-getPortraitEffect(): PortraitEffect--><!--Device-Portrait-getPortraitEffect(): PortraitEffect-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PortraitEffect](arkts-camera-camera-portraiteffect-e-sys.md) | Portrait effect. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.<br>**适用版本：** 11+ |

## 示例

```TypeScript
function getPortraitEffect(portraitPhotoSession: camera.PortraitPhotoSession): camera.PortraitEffect {
  let portraitEffect: camera.PortraitEffect = portraitPhotoSession.getPortraitEffect();
  return portraitEffect;
}
```

## setPortraitEffect

```TypeScript
setPortraitEffect(effect: PortraitEffect): void
```

Sets a portrait effect. Before the setting, use [getSupportedPortraitEffects](arkts-camera-camera-portraitquery-i-sys.md#getSupportedPortraitEffects) to obtain the supported portrait effects and check whether the target portrait effect is supported.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Portrait-setPortraitEffect(effect: PortraitEffect): void--><!--Device-Portrait-setPortraitEffect(effect: PortraitEffect): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| effect | [PortraitEffect](arkts-camera-camera-portraiteffect-e-sys.md) | 是 | Effect Portrait effect to set. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.<br>**适用版本：** 11+ |

## 示例

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

