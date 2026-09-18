# ContextRecoveryInfo

Describes the information about the context of exiting the PhotoPicker. It can be used during the subsequent launch of the PhotoPicker to restore the state from the previous exit.

**Since:** 21

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## albumUri

```TypeScript
albumUri: string
```

URI of the album in the media library when the user selects an image and exits.

- If the user selects from all images, **albumUri** is a fixed **"allPhotos"** string.  
- If the user exits after selecting from search results, text recommendations, or avatar recommendations, the  
next restoration is not supported, and the returned **albumUri** is an empty string.

The default value is an empty string.

**Type:** string

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## displayName

```TypeScript
displayName: string
```

File name of the top-left image in the grid interface when the user last selected an image. The default value is an empty string.

**Type:** string

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## fileSize

```TypeScript
fileSize?: number
```

File size of the top-left image in the grid interface when the user last selected an image. The default value is **0**. Unit: Byte, The value must be an integer greater than or equal to 0.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## gridLevel

```TypeScript
gridLevel?: GridLevel
```

Level of the grid when the user exits last time.

**Type:** [GridLevel](arkts-medialibrary-photoaccesshelper-gridlevel-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## recommendationType

```TypeScript
recommendationType: number
```

Enumerated value of the recommended content set by the user during the last selection. For details, see [RecommendationType](arkts-medialibrary-photoaccesshelper-recommendationtype-e.md).

If no recommendation was set during the last selection, the default value is **0**.

**Type:** number

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## selectedRecommendationType

```TypeScript
selectedRecommendationType: number
```

Enumerated value of the recommended content selected by the user during the last selection. For details, see [RecommendationType](arkts-medialibrary-photoaccesshelper-recommendationtype-e.md).

If no recommendation was selected during the last selection or **All** was selected, the default value is **0**.

**Type:** number

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## sortRule

```TypeScript
sortRule?: string
```

Sorting rule of the grid interface when the user last selected an image. The default value is an empty string.

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## time

```TypeScript
time: number
```

Time of the top-left image in the grid interface when the user last selected an image.

- For albums sorted by capture time, the capture time is returned.  
- For albums sorted by save time, the save time is returned. The default value is **0**.

Unit: ms, The value must be greater than or equal to 0.

**Type:** number

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## version

```TypeScript
version: number
```

Version number of the state data, used to verify the compatibility of the state information data with the state recovery capability.

The version number must be greater than or equal to 1.0.

**Type:** number

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
