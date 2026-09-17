# ColorEffect (System API)

ColorEffect extends [ColorEffectQuery](arkts-camera-camera-coloreffectquery-i-sys.md) Provides the APIs to obtain and set the lens color effect.

**Inheritance/Implementation:** ColorEffect extends [ColorEffectQuery](arkts-camera-camera-coloreffectquery-i-sys.md)

**Since:** 11

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## getColorEffect

```TypeScript
getColorEffect(): ColorEffectType
```

Obtains the color effect in use.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| [ColorEffectType](arkts-camera-camera-coloreffecttype-e-sys.md) | Color effect. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

**Examples**

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

Sets a color effect. Before the setting, call [getSupportedColorEffects](arkts-camera-camera-coloreffectquery-i-sys.md#getsupportedcoloreffects) to obtain the supported color effects.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [ColorEffectType](arkts-camera-camera-coloreffecttype-e-sys.md) | Yes | The type of color effect. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

**Examples**

```TypeScript
function setColorEffect(session: camera.PhotoSessionForSys, colorEffect: camera.ColorEffectType): void {
  session.setColorEffect(colorEffect);
}
```
