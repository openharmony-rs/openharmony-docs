# PhotoSelectOptions

Defines additional options for selecting media assets from Gallery. It inherits from **BaseSelectOptions**. It is used to start the picker of the corresponding user ID space.

**Inheritance/Implementation:** PhotoSelectOptions extends [BaseSelectOptions](arkts-medialibrary-photoaccesshelper-baseselectoptions-c.md)

**Since:** 10

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## completeButtonText

```TypeScript
completeButtonText?: CompleteButtonText
```

Text displayed on the complete button.

The complete button is located in the lower-right corner of the page. It is used by users to signify that they have finished selecting images.

**Type:** [CompleteButtonText](arkts-medialibrary-photoaccesshelper-completebuttontext-e.md)

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## contextRecoveryInfo

```TypeScript
contextRecoveryInfo?: ContextRecoveryInfo
```

Information for restoring the PhotoPicker's state from the last exit.

When the selection process is complete, the PhotoPicker returns **contextRecoveryInfo** to the application. The application can then use the information to restore the PhotoPicker's state and the last viewed grid interface the next time it starts the PhotoPicker.

**Type:** [ContextRecoveryInfo](arkts-medialibrary-photoaccesshelper-contextrecoveryinfo-c.md)

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isDestroyedWithNavigation

```TypeScript
isDestroyedWithNavigation?: boolean
```

Whether destruction with Navigation is supported. **true** if supported, **false** otherwise. The default value is **false**.

**Type:** boolean

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isEditSupported

```TypeScript
isEditSupported?: boolean
```

Whether the image can be edited. **true** if editable, **false** otherwise.

**Type:** boolean

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isOriginalSupported

```TypeScript
isOriginalSupported?: boolean
```

Whether to display the button for selecting the original image. **true** to display, **false** otherwise. The default value is **false**.

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isReturnToPhotoBrowserEnabled

```TypeScript
isReturnToPhotoBrowserEnabled?: boolean
```

Whether to automatically switch to the full image preview mode after a photo is taken in single-selection mode. **true** means to switch, and **false** means the opposite. The default value is **false**.

Note: This parameter takes effect only when [SingleSelectionMode](arkts-medialibrary-photoaccesshelper-singleselectionmode-e.md) is set to **BROWSER_MODE** or **BROWSER_AND_SELECT_MODE** and [BaseSelectOptions.isPreviewForSingleSelectionSupported](arkts-medialibrary-photoaccesshelper-baseselectoptions-c.md) is set to **true**.

**Type:** boolean

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isSelectionNumberVisible

```TypeScript
isSelectionNumberVisible?: boolean
```

Support displaying index numbers.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isSelectionOrderAdjustable

```TypeScript
isSelectionOrderAdjustable?: boolean
```

Support selection order adjustment.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## maxPhotoSelectNumber

```TypeScript
maxPhotoSelectNumber?: number
```

Maximum number of photos that can be selected.

A maximum of 500 photos can be selected. The default value is **500**.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## maxVideoSelectNumber

```TypeScript
maxVideoSelectNumber?: number
```

Maximum number of videos that can be selected.

A maximum of 500 videos can be selected. The default value is **500**.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## pickerColorMode

```TypeScript
pickerColorMode?: PickerColorMode
```

Picker color mode. Dark/light color mode of all content within the Picker. The default value is `PickerColorMode.AUTO`, which follows the system's dark/light color mode.

**Type:** [PickerColorMode](arkts-medialibrary-photoaccesshelper-pickercolormode-e.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## subWindowName

```TypeScript
subWindowName?: string
```

Name of the child window.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
