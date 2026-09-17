# MediaAssetsChangeRequest

批量资产变更请求。

**继承/实现关系：** MediaAssetsChangeRequest implements [MediaChangeRequest](arkts-medialibrary-photoaccesshelper-mediachangerequest-i.md)

**起始版本：** 26.0.0

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## constructor

```TypeScript
constructor(assets: Array<PhotoAsset>)
```

构造函数。用于初始化批量资产变更请求。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assets | Array&lt;[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)&gt; | 是 | 需要变更的资产数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 14000011 | System inner fail |

## setFavorite

```TypeScript
setFavorite(favoriteState: boolean): void
```

批量将文件设置为收藏文件。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| favoriteState | boolean | 是 | 是否设置为收藏文件， true：设置为收藏文件；false：取消收藏。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 14000011 | System inner fail |
