# @ohos.file.picker(Picker)

The **Picker** module encapsulates APIs such as **DocumentViewPicker**, **AudioViewPicker**, and **PhotoViewPicker** to provide capabilities of selecting and saving files of different types. An application can select the API as required. The APIs of this module must be called in UIAbility. Otherwise, the **FilePicker**, **AudioPicker**, or **PhotoPicker** cannot be started. Chinese characters and non-digit characters in the URI are compiled into the corresponding ASCII code and concatenated to the URI returned by calling these APIs.

**Since:** 9

**System capability:** SystemCapability.FileManagement.UserFileService

## Modules to Import

```TypeScript
import { picker } from '@kit.CoreFileKit';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [AudioSaveOptions](arkts-corefile-picker-audiosaveoptions-c.md) | Defines the options for saving audio clips. |
| [AudioSelectOptions](arkts-corefile-picker-audioselectoptions-c.md) | Defines the options for selecting audio clips. |
| [AudioViewPicker](arkts-corefile-picker-audioviewpicker-c.md) | Provides APIs for selecting and saving audio clips. Before using the APIs of **AudioViewPicker**, you need to create an **AudioViewPicker** instance. |
| [DocumentSaveOptions](arkts-corefile-picker-documentsaveoptions-c.md) | Defines the options for saving documents. |
| [DocumentSelectOptions](arkts-corefile-picker-documentselectoptions-c.md) | Defines the options for selecting documents. |
| [DocumentViewPicker](arkts-corefile-picker-documentviewpicker-c.md) | Provides APIs for selecting and saving documents in different formats. Before using the APIs of **DocumentViewPicker**, you need to create a **DocumentViewPicker** instance. |
| [PhotoSaveOptions](arkts-corefile-picker-photosaveoptions-c.md) | Defines the options for saving images or videos. |
| [PhotoSelectOptions](arkts-corefile-picker-photoselectoptions-c.md) | Defines the options for selecting images or videos. |
| [PhotoSelectResult](arkts-corefile-picker-photoselectresult-c.md) | Defines information about the images or videos selected. |
| [PhotoViewPicker](arkts-corefile-picker-photoviewpicker-c.md) | Provides APIs for selecting and saving images or videos. You are advised to use [PhotoViewPicker of PhotoAccessHelper](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-file-photoaccesshelper.md) to select a file. Before using the APIs of **PhotoViewPicker**, you need to create a **PhotoViewPicker** instance. |

<!--Del-->
### Classes(System API)

| Name | Description |
| --- | --- |
| [DocumentSaveOptions](arkts-corefile-picker-documentsaveoptions-c-sys.md) | Defines the options for saving documents. |
| [DocumentSelectOptions](arkts-corefile-picker-documentselectoptions-c-sys.md) | Defines the options for selecting documents. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [DocumentPickerMode](arkts-corefile-picker-documentpickermode-e.md) | Enumerates the modes for saving documents. |
| [DocumentSelectMode](arkts-corefile-picker-documentselectmode-e.md) | Enumerates the types of documents selected. |
| [MergeTypeMode](arkts-corefile-picker-mergetypemode-e.md) | Enumerates file aggregation types. |
| [PhotoViewMIMETypes](arkts-corefile-picker-photoviewmimetypes-e.md) | Enumerates the media file types that can be selected. |
