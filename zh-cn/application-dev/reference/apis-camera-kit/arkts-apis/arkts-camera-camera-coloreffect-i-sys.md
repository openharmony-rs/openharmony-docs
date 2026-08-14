# ColorEffect（系统接口）

ColorEffect extends [ColorEffectQuery](arkts-camera-camera-coloreffectquery-i-sys.md#ColorEffectQuery（系统接口）) Provides the APIs to obtain and set the lens color effect.

**继承/实现关系：** ColorEffect extends [ColorEffectQuery](arkts-camera-camera-coloreffectquery-i-sys.md#ColorEffectQuery（系统接口）)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-camera-interface ColorEffect--><!--Device-camera-interface ColorEffect-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## getColorEffect

```TypeScript
getColorEffect(): ColorEffectType
```

Obtains the color effect in use.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ColorEffect-getColorEffect(): ColorEffectType--><!--Device-ColorEffect-getColorEffect(): ColorEffectType-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColorEffectType](arkts-camera-camera-coloreffecttype-e-sys.md) | Color effect. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

```TypeScript
function getColorEffect(session: camera.PhotoSessionForSys): camera.ColorEffectType {
  let colorEffect: camera.ColorEffectType = session.getColorEffect();
  return colorEffect;
}
```

## setColorEffect

```TypeScript
setColorEffect(type: ColorEffectType): void
```

Sets a color effect. Before the setting, call [getSupportedColorEffects](arkts-camera-camera-coloreffectquery-i-sys.md#getSupportedColorEffects) to obtain the supported color effects.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ColorEffect-setColorEffect(type: ColorEffectType): void--><!--Device-ColorEffect-setColorEffect(type: ColorEffectType): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [ColorEffectType](arkts-camera-camera-coloreffecttype-e-sys.md) | 是 | The type of color effect. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

```TypeScript
function setColorEffect(session: camera.PhotoSessionForSys, colorEffect: camera.ColorEffectType): void {
  session.setColorEffect(colorEffect);
}
```

