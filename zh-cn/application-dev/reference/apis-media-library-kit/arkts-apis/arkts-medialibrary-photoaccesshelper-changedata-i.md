# ChangeData

监听器回调函数的返回值。

**起始版本：** 23

<!--Device-photoAccessHelper-interface ChangeData--><!--Device-photoAccessHelper-interface ChangeData-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## extraUris

```TypeScript
extraUris: Array<string>
```

相册中变动文件的uri数组。可能为undefined，使用前需要检查是否为undefined。

**类型：** Array&lt;string&gt;

**起始版本：** 23

<!--Device-ChangeData-extraUris: Array<string>--><!--Device-ChangeData-extraUris: Array<string>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## type

```TypeScript
type: NotifyType
```

ChangeData的通知类型。

**类型：** NotifyType

**起始版本：** 23

<!--Device-ChangeData-type: NotifyType--><!--Device-ChangeData-type: NotifyType-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## uris

```TypeScript
uris: Array<string>
```

相同[NotifyType](arkts-medialibrary-photoaccesshelper-notifytype-e.md)的所有uri，可以是PhotoAsset或Album。

**类型：** Array&lt;string&gt;

**起始版本：** 23

<!--Device-ChangeData-uris: Array<string>--><!--Device-ChangeData-uris: Array<string>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

