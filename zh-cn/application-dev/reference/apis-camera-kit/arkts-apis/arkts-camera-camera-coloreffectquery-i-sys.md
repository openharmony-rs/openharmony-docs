# ColorEffectQuery（系统接口）

```TypeScript
interface ColorEffectQuery
```

提供获取支持的色彩效果的接口。

**起始版本：** 12

<!--Device-camera-interface ColorEffectQuery--><!--Device-camera-interface ColorEffectQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## getSupportedColorEffects

```TypeScript
getSupportedColorEffects(): Array<ColorEffectType>
```

获取支持的色彩效果。

**起始版本：** 11

<!--Device-ColorEffectQuery-getSupportedColorEffects(): Array<ColorEffectType>--><!--Device-ColorEffectQuery-getSupportedColorEffects(): Array<ColorEffectType>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[ColorEffectType](arkts-camera-camera-coloreffecttype-e-sys.md)&gt; | 支持的色彩效果数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |

<!--Del-->
**示例**

```TypeScript
function getSupportedColorEffects(session: camera.PhotoSessionForSys): Array<camera.ColorEffectType> {
  let colorEffects: Array<camera.ColorEffectType> = session.getSupportedColorEffects();
  return colorEffects;
}
```

<!--DelEnd-->
