# FormInfo（系统接口）

图库卡片相关信息。

**起始版本：** 23

<!--Device-photoAccessHelper-interface FormInfo--><!--Device-photoAccessHelper-interface FormInfo-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## formId

```TypeScript
formId: string
```

卡片的ID，由图库创建卡片时提供。

**类型：** string

**起始版本：** 23

<!--Device-FormInfo-formId: string--><!--Device-FormInfo-formId: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## uri

```TypeScript
uri: string
```

卡片绑定的图片的uri。创建卡片时uri可为空或图片的uri，移除卡片时uri不做校验，传空即可。

**类型：** string

**起始版本：** 23

<!--Device-FormInfo-uri: string--><!--Device-FormInfo-uri: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

