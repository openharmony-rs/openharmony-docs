# Macro

```TypeScript
interface Macro extends MacroQuery
```

**Macro** inherits from [MacroQuery](arkts-camera-camera-macroquery-i.md).

It provides the API to enable macro photography.

**Inheritance/Implementation:** Macro extends [MacroQuery](arkts-camera-camera-macroquery-i.md)

**Since:** 19

<!--Device-camera-interface Macro extends MacroQuery--><!--Device-camera-interface Macro extends MacroQuery-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## enableMacro

```TypeScript
enableMacro(enabled: boolean): void
```

Enables or disables macro photography.

> **NOTE:** 
> 
> Before calling this API, call [isMacroSupported](arkts-camera-camera-macroquery-i.md#ismacrosupported) to check whether the
> current device supports macro photography.

**Since:** 19

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-Macro-enableMacro(enabled: boolean): void--><!--Device-Macro-enableMacro(enabled: boolean): void-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether to enable macro photography. **true** to enable, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application.<br>**Applicable version:** 11 - 18 |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |
| [7400102](../errorcode-camera.md#7400102-invalid-operation) | Operation not allowed.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
function enableMacro(photoSession: camera.PhotoSession): void {
  let isSupported: boolean = photoSession.isMacroSupported();
  if (isSupported) {
    photoSession.enableMacro(true);
  }
}
```
