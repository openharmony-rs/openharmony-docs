# BeautyQuery (System API)

```TypeScript
interface BeautyQuery
```

Provides APIs to obtain and set the beauty effect.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## getSupportedBeautyRange

```TypeScript
getSupportedBeautyRange(type: BeautyType): Array<number>
```

Obtains the levels that can be set a beauty type. The beauty levels vary according to the device type. The following table is only an example.

| Input Parameter | Example Return Value | Return Value Description |  
| ----------------| ---- | ---------|  
| AUTO | [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10] |Beauty levels supported when **type** is set to **AUTO**. The value **0** * means that beauty mode is disabled, and other positive values mean the corresponding automatic beauty levels. |
| [SKIN_SMOOTH](arkts-camera-camera-beautytype-e-sys.md) | [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10] | Beauty levels supported when **type** is set to **SKIN_SMOOTH**. The value * **0** means that the skin smoothing feature is disabled, and other positive values mean the corresponding skin smoothing levels. |
| [FACE_SLENDER](arkts-camera-camera-beautytype-e-sys.md) | [0, 1, 2, 3, 4, 5] | Beauty levels supported when **type** is set to **FACE_SLENDER**. The value **0** means that * the face slimming feature is disabled, and other positive values mean the corresponding face slimming levels. |
| [SKIN_TONE](arkts-camera-camera-beautytype-e-sys.md) | [-1, 16242611] | Beauty levels supported when **type** is set to **SKIN_TONE**. The value **-1** means that the skin tone perfection feature is disabled. Other non-negative values mean the skin tone perfection levels represented by RGB,<br> for example, 16242611, which is 0xF7D7B3 in hexadecimal format, where F7, D7, and B3 represent the values of the R channel, G channel, and B channel, respectively. |

**Since:** 11

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [BeautyType](arkts-camera-camera-beautytype-e-sys.md) | Yes | Beauty type. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;number&gt; | Array of levels supported. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config, only throw in session usage. |

**Examples**

```TypeScript
function getSupportedBeautyRange(portraitPhotoSession: camera.PortraitPhotoSession): Array<number> {
  let beautyTypes: Array<camera.BeautyType> = portraitPhotoSession.getSupportedBeautyTypes();
  if (beautyTypes === undefined || beautyTypes.length <= 0) {
    return [];
  }
  let beautyLevels: Array<number> = portraitPhotoSession.getSupportedBeautyRange(beautyTypes[0]);
  return beautyLevels;
}
```

## getSupportedBeautyTypes

```TypeScript
getSupportedBeautyTypes(): Array<BeautyType>
```

Obtains the supported beauty types.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[BeautyType](arkts-camera-camera-beautytype-e-sys.md)&gt; | Array of beauty types supported. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config, only throw in session usage. |

**Examples**

```TypeScript
function getSupportedBeautyTypes(portraitPhotoSession: camera.PortraitPhotoSession): Array<camera.BeautyType> {
  let beautyTypes: Array<camera.BeautyType> = portraitPhotoSession.getSupportedBeautyTypes();
  return beautyTypes;
}
```

## getSupportedPortraitThemeTypes

```TypeScript
getSupportedPortraitThemeTypes(): Array<PortraitThemeType>
```

Gets supported portrait theme type.

**Since:** 14

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[PortraitThemeType](arkts-camera-camera-portraitthemetype-e-sys.md)&gt; | Lists of portrait theme types |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config, only throw in session usage. |

## isPortraitThemeSupported

```TypeScript
isPortraitThemeSupported(): boolean
```

Checks whether portrait theme is supported.

**Since:** 14

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Is portrait theme supported. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config, only throw in session usage. |
