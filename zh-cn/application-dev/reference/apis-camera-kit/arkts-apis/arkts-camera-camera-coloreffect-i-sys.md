# ColorEffect（系统接口）

```TypeScript
interface ColorEffect extends ColorEffectQuery
```

ColorEffect 继承 [ColorEffectQuery](arkts-camera-camera-coloreffectquery-i-sys.md)提供获取和设置镜头色彩效果的接口。

**继承/实现关系：** ColorEffect extends [ColorEffectQuery](arkts-camera-camera-coloreffectquery-i-sys.md)

**起始版本：** 11

<!--Device-camera-interface ColorEffect extends ColorEffectQuery--><!--Device-camera-interface ColorEffect extends ColorEffectQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## getColorEffect

```TypeScript
getColorEffect(): ColorEffectType
```

获取当前使用的色彩效果。

**起始版本：** 11

<!--Device-ColorEffect-getColorEffect(): ColorEffectType--><!--Device-ColorEffect-getColorEffect(): ColorEffectType-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColorEffectType](arkts-camera-camera-coloreffecttype-e-sys.md) | 色彩效果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

<!--Del-->
**示例**

```TypeScript
function getColorEffect(session: camera.PhotoSessionForSys): camera.ColorEffectType {
  let colorEffect: camera.ColorEffectType = session.getColorEffect();
  return colorEffect;
}
```

<!--DelEnd-->

## setColorEffect

```TypeScript
setColorEffect(type: ColorEffectType): void
```

设置色彩效果。设置前，请先调用[getSupportedColorEffects](arkts-camera-camera-coloreffectquery-i-sys.md#getsupportedcoloreffects) 获取支持的色彩效果。

**起始版本：** 11

<!--Device-ColorEffect-setColorEffect(type: ColorEffectType): void--><!--Device-ColorEffect-setColorEffect(type: ColorEffectType): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [ColorEffectType](arkts-camera-camera-coloreffecttype-e-sys.md) | 是 | 色彩效果类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

<!--Del-->
**示例**

```TypeScript
function setColorEffect(session: camera.PhotoSessionForSys, colorEffect: camera.ColorEffectType): void {
  session.setColorEffect(colorEffect);
}
```

<!--DelEnd-->
