# MakerNoteHuaweiMetadata

MakerNoteHuaweiMetadata implements Metadata

Photo metadata from Huawei cameras.

**Inheritance/Implementation:** MakerNoteHuaweiMetadata implements [Metadata](arkts-image-image-metadata-i.md)

**Since:** 23

**System capability:** SystemCapability.Multimedia.Image.Core

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## clone

```TypeScript
clone(): Promise<MakerNoteHuaweiMetadata>
```

Clones [MakerNoteHuaweiMetadata](arkts-image-image-makernotehuaweimetadata-c.md) metadata. This API returns the result asynchronously through a promise.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[MakerNoteHuaweiMetadata](arkts-image-image-makernotehuaweimetadata-c.md)&gt; | Promise used to return the **MakerNoteHuaweiMetadata** metadata instance if metadata is successfully obtained. |

## createInstance

```TypeScript
static createInstance(): MakerNoteHuaweiMetadata
```

Returns an empty [MakerNoteHuaweiMetadata](arkts-image-image-makernotehuaweimetadata-c.md) instance.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

**Return value:**

| Type | Description |
| --- | --- |
| [MakerNoteHuaweiMetadata](arkts-image-image-makernotehuaweimetadata-c.md) | Empty **MakerNoteHuaweiMetadata** instance. |

## getAllProperties

```TypeScript
getAllProperties(): Promise<Record<string, string | null>>
```

Obtains all properties and their values from the image metadata. This API returns the result asynchronously through a promise.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Record&lt;string, string &#124; null&gt;&gt; | Promise used to return the values of all properties. |

## getBlob

```TypeScript
getBlob(): Promise<ArrayBuffer>
```

Obtains the metadata in binary format. This API uses a promise to return the result.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;ArrayBuffer&gt; | Promise that returns the binary data of the metadata. |

## getProperties

```TypeScript
getProperties(key: Array<string>): Promise<Record<string, string | null>>
```

Obtains the property values from image metadata. This API returns the result asynchronously through a promise.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | Array&lt;string&gt; | Yes | Names of the properties to query. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Record&lt;string, string &#124; null&gt;&gt; | Promise used to return the obtained image metadata property values. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7600202](../errorcode-image.md#7600202-unsupported-metadata-readwrite-operation) | Unsupported metadata. Possible causes: unsupported metadata type. |

## setBlob

```TypeScript
setBlob(blob: ArrayBuffer): Promise<void>
```

Replaces the current metadata with binary data. This API uses a promise to return the result.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| blob | ArrayBuffer | Yes | Binary data used to replace the metadata. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7600206](../errorcode-image.md#7600206-invalid-parameter) | Invalid parameter. Possible causes: The blob is empty or has a length of 0. |

## setProperties

```TypeScript
setProperties(records: Record<string, string | null>): Promise<void>
```

Sets the values of specified properties in image metadata in batches. This API returns the result asynchronously through a promise.

For details about the properties, see [PropertyKey](arkts-image-image-propertykey-e.md).

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| records | Record&lt;string, string &#124; null&gt; | Yes | Array containing key-value pairs representing properties and their corresponding values of the **MakerNoteHuaweiMetadata** object to be modified. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7600202](../errorcode-image.md#7600202-unsupported-metadata-readwrite-operation) | Unsupported metadata. Possible causes: unsupported metadata type. |

## burstNumber

```TypeScript
burstNumber?: number
```

Number of burst shots. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## captureMode

```TypeScript
captureMode?: number
```

Capture mode. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## cloudLabel

```TypeScript
cloudLabel?: string
```

Cloud enhancement label.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## faceConfidences

```TypeScript
faceConfidences?: number[]
```

Confidences of a specified number of faces.

**Type:** number[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## faceCount

```TypeScript
faceCount?: number
```

Number of faces. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## faceSmileScores

```TypeScript
faceSmileScores?: number[]
```

Smile scores of a specified number of faces.

**Type:** number[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## focusMode

```TypeScript
focusMode?: FocusMode
```

Lens focus control policy, which determines how the camera adjusts the focal length.

**Type:** [FocusMode](arkts-image-image-focusmode-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## isCloudEnhanced

```TypeScript
isCloudEnhanced?: boolean
```

Whether the image has been cloud-enhanced. **true** indicates yes; **false** indicates no.

**Type:** boolean

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## isFrontCamera

```TypeScript
isFrontCamera?: boolean
```

Whether to use the front camera. **true** indicates yes; **false** indicates no.

**Type:** boolean

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## isWindSnapshot

```TypeScript
isWindSnapshot?: boolean
```

Whether the wind snapshot mode is used. **true** indicates yes; **false** indicates no. This mode is a specialized photography mode designed for capturing fast-moving subjects or scenes prone to blurring, such as in windy conditions or when photographing moving objects.

**Type:** boolean

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## isXmageSupported

```TypeScript
isXmageSupported?: boolean
```

Whether XMAGE is supported. **true** indicates yes; **false** indicates no.

**Type:** boolean

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## physicalAperture

```TypeScript
physicalAperture?: number
```

Physical aperture, in fNumber. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## pitchAngle

```TypeScript
pitchAngle?: number
```

Pitch angle. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## rollAngle

```TypeScript
rollAngle?: number
```

Horizontal pan angle. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## sceneBeachConfidence

```TypeScript
sceneBeachConfidence?: number
```

Capture scene: beach confidence. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## sceneBlueSkyConfidence

```TypeScript
sceneBlueSkyConfidence?: number
```

Capture scene: blue sky confidence. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## sceneFlowersConfidence

```TypeScript
sceneFlowersConfidence?: number
```

Capture scene: flower confidence. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## sceneFoodConfidence

```TypeScript
sceneFoodConfidence?: number
```

Capture scene: food confidence. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## sceneGreenPlantConfidence

```TypeScript
sceneGreenPlantConfidence?: number
```

Capture scene: green plant confidence. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## sceneNightConfidence

```TypeScript
sceneNightConfidence?: number
```

Capture scene: night scene confidence. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## sceneSnowConfidence

```TypeScript
sceneSnowConfidence?: number
```

Capture scene: snow confidence. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## sceneStageConfidence

```TypeScript
sceneStageConfidence?: number
```

Capture scene: stage performance confidence. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## sceneSunsetConfidence

```TypeScript
sceneSunsetConfidence?: number
```

Capture scene: sunset confidence. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## sceneTextConfidence

```TypeScript
sceneTextConfidence?: number
```

Capture scene: text confidence. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## sceneVersion

```TypeScript
sceneVersion?: number
```

Version number of the scene recognition algorithm. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## xmageBottom

```TypeScript
xmageBottom?: number
```

Vertical coordinate of the bottom boundary of the effective content area (excluding the watermark coverage area) on the original image, relative to the top-left origin of the image. The unit is px. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## xmageColorMode

```TypeScript
xmageColorMode?: XmageColorMode
```

XMAGE color mode.

**Type:** [XmageColorMode](arkts-image-image-xmagecolormode-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## xmageLeft

```TypeScript
xmageLeft?: number
```

Horizontal coordinate of the left boundary of the effective content area (excluding the watermark coverage area) on the original image, relative to the top-left origin of the image. The unit is px. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## xmageRight

```TypeScript
xmageRight?: number
```

Horizontal coordinate of the right boundary of the effective content area (excluding the watermark coverage area) on the original image, relative to the top-left origin of the image. The unit is px. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## xmageTop

```TypeScript
xmageTop?: number
```

Vertical coordinate of the top boundary of the effective content area (excluding the watermark coverage area) on the original image, relative to the top-left origin of the image. The unit is px. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## xmageWatermarkMode

```TypeScript
xmageWatermarkMode?: number
```

XMAGE watermark mode. For details, see Constants. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core
