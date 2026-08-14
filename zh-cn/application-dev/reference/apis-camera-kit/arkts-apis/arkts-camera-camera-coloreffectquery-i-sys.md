# ColorEffectQuery（系统接口）

Provides the API to obtain the color effects supported.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-camera-interface ColorEffectQuery--><!--Device-camera-interface ColorEffectQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## getSupportedColorEffects

```TypeScript
getSupportedColorEffects(): Array<ColorEffectType>
```

Obtains the supported color effects.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ColorEffectQuery-getSupportedColorEffects(): Array<ColorEffectType>--><!--Device-ColorEffectQuery-getSupportedColorEffects(): Array<ColorEffectType>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[ColorEffectType](arkts-camera-camera-coloreffecttype-e-sys.md)&gt; | Array of color effects supported. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

```TypeScript
function getSupportedColorEffects(session: camera.PhotoSessionForSys): Array<camera.ColorEffectType> {
  let colorEffects: Array<camera.ColorEffectType> = session.getSupportedColorEffects();
  return colorEffects;
}
```

