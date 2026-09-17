# OperationItem

Describes the settings for filtering media files.

**Since:** 22

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## field

```TypeScript
field?: PhotoKeys
```

Column name in the data table.

Currently, only the following key fields are supported: **URI**, **PHOTO_TYPE**, **DISPLAY_NAME**, **SIZE**, **DURATION**, **WIDTH**, **HEIGHT**, **ORIENTATION**, **FAVORITE**, **TITLE**, **POSITION**, **PHOTO_SUBTYPE**, **DYNAMIC_RANGE_TYPE**, **COVER_POSITION**, **BURST_KEY**, **LCD_SIZE**, **THM_SIZE**, **DETAIL_TIME**, **MEDIA_SUFFIX**, **OWNER_ALBUM_ID**, **ASPECT_RATIO** and **DATE_TAKEN_MS**.

When [select](arkts-medialibrary-photoaccesshelper-photoviewpicker-c.md#select) is used to set this parameter, an invalid field results in error code 401. When [@ohos.file.PhotoPickerComponent (PhotoPickerComponent)](arkts-medialibrary-file-photopickercomponent-photopickercomponent-s.md) is used to set this parameter, an invalid field does not trigger the **onPickerControllerReady** callback.

This field is not involved in non-conditional predicates such as **and**, **or**, **beginWrap**, and **endWrap**.

**Type:** [PhotoKeys](arkts-medialibrary-photoaccesshelper-photokeys-e.md)

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## operationType

```TypeScript
operationType: OperationType
```

Predicates.

**Type:** [OperationType](arkts-medialibrary-photoaccesshelper-operationtype-e.md)

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## value

```TypeScript
value?: Array<OperationValueType>
```

Values needed for matching different predicates.

This field is not involved in non-conditional predicates such as **and**, **or**, **beginWrap**, and **endWrap**.

The maximum length is 10; if exceeded, only the first 10 values are considered.

**Type:** Array&lt;[OperationValueType](arkts-medialibrary-photoaccesshelper-operationvaluetype-t.md)&gt;

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
