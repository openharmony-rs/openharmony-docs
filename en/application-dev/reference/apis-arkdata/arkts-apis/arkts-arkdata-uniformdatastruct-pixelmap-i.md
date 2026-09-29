# PixelMap

```TypeScript
interface PixelMap
```

Represents data of the pixel map type defined by the system.

**Since:** 15

<!--Device-uniformDataStruct-interface PixelMap--><!--Device-uniformDataStruct-interface PixelMap-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## Modules to Import

```TypeScript
import { uniformDataStruct } from '@kit.ArkData';
```

## details

```TypeScript
details?: Record<string, number | string | Uint8Array>
```

Object of the dictionary type used to describe the icon. The key is of the string type, and the value can be a number, a string, or a Uint8Array. By default, it is an empty dictionary object.

**Type:** Record&lt;string, number &#124; string &#124; Uint8Array&gt;

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

<!--Device-PixelMap-details?: Record<string, int | long | double | string | Uint8Array>--><!--Device-PixelMap-details?: Record<string, int | long | double | string | Uint8Array>-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## pixelMap

```TypeScript
pixelMap: image.PixelMap
```

Binary data of the pixel map.

**Type:** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

<!--Device-PixelMap-pixelMap: image.PixelMap--><!--Device-PixelMap-pixelMap: image.PixelMap-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## uniformDataType

```TypeScript
readonly uniformDataType: 'openharmony.pixel-map'
```

Uniform data type, which has a fixed value of **openharmony.pixel-map**. For details, see [UniformDataType](arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md).

**Type:** 'openharmony.pixel-map'

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

<!--Device-PixelMap-readonly uniformDataType: 'openharmony.pixel-map'--><!--Device-PixelMap-readonly uniformDataType: 'openharmony.pixel-map'-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
