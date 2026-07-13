# @ohos.file.picker

选择器(Picker)是一个封装DocumentViewPicker、AudioViewPicker、PhotoViewPicker的API模块，具有选择与保存的能力。
应用可以选择使用以下API来实现文件的选择和保存的功能。该类接口，需要应用在界面UIAbility中调用，否则无法拉起FilePicker应用、
AudioPicker应用或PhotoPicker应用。调用本模块接口返回的URI数组，
URI中的中文及非数字字母的特殊字符会被编码为对应的ASCII码并拼接到URI中。

> **说明：**
>
> 该模块接口从API version 9开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。

**起始版本：** 9

**系统能力：** SystemCapability.FileManagement.UserFileService

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [AudioSaveOptions](arkts-corefile-audiosaveoptions-c.md) | 音频保存选项。 |
| [AudioSelectOptions](arkts-corefile-audioselectoptions-c.md) | 音频选择选项。 |
| [AudioViewPicker](arkts-corefile-audioviewpicker-c.md) | 音频选择器对象，用来支撑选择和保存音频类文件等用户场景。在使用前，需要先创建AudioViewPicker实例。 |
| [DocumentSaveOptions](arkts-corefile-documentsaveoptions-c.md) | 文档保存选项。 |
| [DocumentSelectOptions](arkts-corefile-documentselectoptions-c.md) | 文档选择选项。 |
| [DocumentViewPicker](arkts-corefile-documentviewpicker-c.md) | 文件选择器对象，用来支撑选择和保存各种格式文档。在使用前，需要先创建DocumentViewPicker实例。 |
| [PhotoSaveOptions](arkts-corefile-photosaveoptions-c.md) | 图片或视频的保存选项。 |
| [PhotoSelectOptions](arkts-corefile-photoselectoptions-c.md) | 图库选择选项。 |
| [PhotoSelectResult](arkts-corefile-photoselectresult-c.md) | 返回图库选择后的结果集。 |
| [PhotoViewPicker](arkts-corefile-photoviewpicker-c.md) | 图库选择器对象，用来支撑选择图片/视频和保存图片/视频等用户场景。选择文件推荐使用[PhotoAccessHelper的PhotoViewPicker](@ohos.file.photoAccessHelper:photoAccessHelper)。在使用前，需要先创建PhotoViewPicker实例。 |

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DocumentSaveOptions](arkts-corefile-documentsaveoptions-c-sys.md) | 文档保存选项。 |
| [DocumentSelectOptions](arkts-corefile-documentselectoptions-c-sys.md) | 文档选择选项。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [DocumentPickerMode](arkts-corefile-documentpickermode-e.md) | Enumerates the modes for saving documents. |
| [DocumentSelectMode](arkts-corefile-documentselectmode-e.md) | Enumerates the types of documents selected. |
| [MergeTypeMode](arkts-corefile-mergetypemode-e.md) | Enumerates file aggregation types. |
| [PhotoViewMIMETypes](arkts-corefile-photoviewmimetypes-e.md) | Enumerates the media file types that can be selected. |

