# ToneHapticsAttrs (System API)

```TypeScript
interface ToneHapticsAttrs
```

Haptics attributes in tone scenario.

**Since:** 14

<!--Device-systemSoundManager-interface ToneHapticsAttrs--><!--Device-systemSoundManager-interface ToneHapticsAttrs-End-->

**System capability:** SystemCapability.Multimedia.SystemSound.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { systemSoundManager } from '@kit.AudioKit';
```

## getFileName

```TypeScript
getFileName(): string
```

Get file name of haptics.

**Since:** 14

<!--Device-ToneHapticsAttrs-getFileName(): string--><!--Device-ToneHapticsAttrs-getFileName(): string-End-->

**System capability:** SystemCapability.Multimedia.SystemSound.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| string | Haptics title. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |

**Examples**

```TypeScript
toneHapticsAttrs.getFileName();
```

## getGentleFileName

```TypeScript
getGentleFileName(): string | null
```

Get file name of gentle haptics.

**Since:** 22

<!--Device-ToneHapticsAttrs-getGentleFileName(): string | null--><!--Device-ToneHapticsAttrs-getGentleFileName(): string | null-End-->

**System capability:** SystemCapability.Multimedia.SystemSound.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| string &#124; null | Haptics file name or null if not gentle haptics not exist. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |

**Examples**

```TypeScript
toneHapticsAttrs.getGentleFileName();
```

## getGentleTitle

```TypeScript
getGentleTitle(): string | null
```

Get title of gentle haptics.

**Since:** 22

<!--Device-ToneHapticsAttrs-getGentleTitle(): string | null--><!--Device-ToneHapticsAttrs-getGentleTitle(): string | null-End-->

**System capability:** SystemCapability.Multimedia.SystemSound.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| string &#124; null | Haptics title or null if not gentle haptics not exist. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |

**Examples**

```TypeScript
toneHapticsAttrs.getGentleTitle();
```

## getGentleUri

```TypeScript
getGentleUri(): string | null
```

Get gentle haptics URI.

**Since:** 22

<!--Device-ToneHapticsAttrs-getGentleUri(): string | null--><!--Device-ToneHapticsAttrs-getGentleUri(): string | null-End-->

**System capability:** SystemCapability.Multimedia.SystemSound.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| string &#124; null | Haptics URI or null if not gentle haptics not exist. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |

**Examples**

```TypeScript
toneHapticsAttrs.getGentleUri();
```

## getTitle

```TypeScript
getTitle(): string
```

Get title of haptics.

**Since:** 14

<!--Device-ToneHapticsAttrs-getTitle(): string--><!--Device-ToneHapticsAttrs-getTitle(): string-End-->

**System capability:** SystemCapability.Multimedia.SystemSound.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| string | Haptics title. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |

**Examples**

```TypeScript
toneHapticsAttrs.getTitle();
```

## getUri

```TypeScript
getUri(): string
```

Get haptics uri.

**Since:** 14

<!--Device-ToneHapticsAttrs-getUri(): string--><!--Device-ToneHapticsAttrs-getUri(): string-End-->

**System capability:** SystemCapability.Multimedia.SystemSound.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| string | Haptics uri. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |

**Examples**

```TypeScript
toneHapticsAttrs.getUri();
```
