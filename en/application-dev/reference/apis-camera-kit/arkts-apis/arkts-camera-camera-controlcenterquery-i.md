# ControlCenterQuery

```TypeScript
interface ControlCenterQuery
```

ControlCenterQuery is used to check whether the camera controller is supported.

**Since:** 20

<!--Device-camera-interface ControlCenterQuery--><!--Device-camera-interface ControlCenterQuery-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## getSupportedEffectTypes

```TypeScript
getSupportedEffectTypes(): Array<ControlCenterEffectType>
```

Obtains the effect types supported by the camera controller.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-ControlCenterQuery-getSupportedEffectTypes(): Array<ControlCenterEffectType>--><!--Device-ControlCenterQuery-getSupportedEffectTypes(): Array<ControlCenterEffectType>-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[ControlCenterEffectType](arkts-camera-camera-controlcentereffecttype-e.md)&gt; | Array of effect types supported. |

**Examples**

```TypeScript
function getSupportedEffectTypes(videoSession: camera.VideoSession): Array<camera.ControlCenterEffectType> {
    let effectTypes: Array<camera.ControlCenterEffectType> = [];
    effectTypes = videoSession.getSupportedEffectTypes();
    return effectTypes;
}
```

## isControlCenterSupported

```TypeScript
isControlCenterSupported(): boolean
```

Checks whether the camera controller is supported.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-ControlCenterQuery-isControlCenterSupported(): boolean--><!--Device-ControlCenterQuery-isControlCenterSupported(): boolean-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for the support of the camera controller. **true** if supported, **false** otherwise. |

**Examples**

```TypeScript
function isControlCenterSupported(videoSession: camera.VideoSession): boolean {
    let isSupported: boolean = videoSession.isControlCenterSupported();
    return isSupported;
}
```
