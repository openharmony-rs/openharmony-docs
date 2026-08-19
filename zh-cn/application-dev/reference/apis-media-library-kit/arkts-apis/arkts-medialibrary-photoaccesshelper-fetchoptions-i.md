# FetchOptions

检索条件。

**起始版本：** 23

<!--Device-photoAccessHelper-interface FetchOptions--><!--Device-photoAccessHelper-interface FetchOptions-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## fetchColumns

```TypeScript
fetchColumns: Array<string>
```

检索条件，指定列名查询。 对于照片，如果该参数为空，默认查询'uri'、'media_type'、'subtype'和'display_name'，使用[get](arkts-medialibrary-photoaccesshelper-photoasset-i.md#get)接口获取当 前对象的其他属性时将会报错。示例：fetchColumns: ['uri', 'title']。 对于相册，如果该参数为空，默认查询'uri'和'album_name'。

**类型：** Array&lt;string&gt;

**起始版本：** 23

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-FetchOptions-fetchColumns: Array<string>--><!--Device-FetchOptions-fetchColumns: Array<string>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## predicates

```TypeScript
predicates: dataSharePredicates.DataSharePredicates
```

谓词查询，显示过滤条件。

**类型：** dataSharePredicates.DataSharePredicates

**起始版本：** 23

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-FetchOptions-predicates: dataSharePredicates.DataSharePredicates--><!--Device-FetchOptions-predicates: dataSharePredicates.DataSharePredicates-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

