# PhotoSelectResult

返回图库选择后的结果集。

**起始版本：** 9

**废弃版本：** 12

**替代接口：** PhotoSelectResult

<!--Device-picker-class PhotoSelectResult--><!--Device-picker-class PhotoSelectResult-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

## 导入模块

```TypeScript
import { picker } from '@kit.CoreFileKit';
```

## isOriginalPhoto

```TypeScript
isOriginalPhoto: boolean
```

返回图库选择后的媒体文件是否为原图。true为原图；false不是原图。

**类型：** boolean

**起始版本：** 9

**废弃版本：** 18

**替代接口：** isOriginalPhoto

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoSelectResult-isOriginalPhoto: boolean--><!--Device-PhotoSelectResult-isOriginalPhoto: boolean-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

## photoUris

```TypeScript
photoUris: Array<string>
```

返回图库选择后的媒体文件的URI数组。此URI数组只能通过临时授权的方式调用接口[photoAccessHelper.getAssets](@ohos.file.photoAccessHelper:photoAccessHelper.PhotoAccessHelper.getAssets(options: FetchOptions, callback: AsyncCallback<FetchResult<PhotoAsset>>))去使用，具体使用方式参见用户文件URI介绍中的[媒体文件URI的使用方式](docroot://file-management/user-file-uri-intro.md#媒体文件uri的使用方式)。

**类型：** Array&lt;string&gt;

**起始版本：** 9

**废弃版本：** 18

**替代接口：** photoUris

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoSelectResult-photoUris: Array<string>--><!--Device-PhotoSelectResult-photoUris: Array<string>-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

