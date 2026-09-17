# DataType

Enumerates the types of data sent from **PickerController** to the **PhotoPickerComponent**.

**Since:** 12

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## SET_SELECTED_URIS

```TypeScript
SET_SELECTED_URIS = 1
```

Sends a list of selected items to instruct the **PhotoPickerComponent** to refresh the selection status. A string array needs to be passed in.

For example, after an image is deleted from an application's page, the application calls **setData()** to notify the **PhotoPickerComponent** of the remaining selected items. Then, the **PhotoPickerComponent** refreshes the check box status.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## SET_ALBUM_URI

```TypeScript
SET_ALBUM_URI = 2
```

Sends the selected album to instruct the **PhotoPickerComponent** to refresh the album data. A string array needs to be passed in.

For example, after an album is selected from an application's page, the application calls **setData** to notify the **PhotoPickerComponent** of the URI of the selected album. Then, the **PhotoPickerComponent** refreshes the album data.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## SET_SELECTED_INFO

```TypeScript
SET_SELECTED_INFO = 3
```

Sends the URI of the selected file and the index of the selected **PhotoPickerComponent**. If the index of a **PhotoPickerComponent** matches the one provided in the parameter, the selected file is automatically highlighted in that **PhotoPickerComponent**.

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## SET_BADGE_CONFIGS

```TypeScript
SET_BADGE_CONFIGS = 4
```

Sends the badge configurations, which are of the [badgeConfig](arkts-medialibrary-file-photopickercomponent-badgeconfig-c.md) type and include a list of data with badge types and corresponding file URIs. Once configured, the badge of the configured type is displayed in the specified file.

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## SET_ITEM_CLICK_RESULT

```TypeScript
SET_ITEM_CLICK_RESULT = 5
```

Result of the click, which is of the [ClickResult](arkts-medialibrary-file-photopickercomponent-clickresult-c.md) type.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
