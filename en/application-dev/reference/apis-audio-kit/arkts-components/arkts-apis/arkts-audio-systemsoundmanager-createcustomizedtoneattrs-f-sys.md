# createCustomizedToneAttrs (System API)

## Modules to Import

```TypeScript
import { systemSoundManager } from '@kit.AudioKit';
```

## createCustomizedToneAttrs

```TypeScript
function createCustomizedToneAttrs(): ToneAttrs
```

Create customized tone attributes.

**Since:** 12

**System capability:** SystemCapability.Multimedia.SystemSound.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| [ToneAttrs](arkts-audio-systemsoundmanager-toneattrs-i-sys.md) | Tone attributes created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |

**Examples**

```TypeScript
let toneAttrs: systemSoundManager.ToneAttrs = systemSoundManager.createCustomizedToneAttrs();
```
