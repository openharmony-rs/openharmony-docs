# GalleryFormInfo（系统接口）

图库卡片相关信息。

**起始版本：** 18

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## assetUris

```TypeScript
assetUris?: Array<string>
```

卡片绑定的图片或相册的uri集合。

创建和更新卡片时，assetUris不可为空。

单次创建或更新卡片时，assetUris中的uri个数如果超出500个，则只创建或更新500个uri的监听，超出500个后的uri不会被注册。

移除卡片时，assetUris可省略。

**类型：** Array&lt;string&gt;

**起始版本：** 18

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## formId

```TypeScript
formId: string
```

卡片的ID，由图库创建卡片时提供。

**类型：** string

**起始版本：** 18

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。
