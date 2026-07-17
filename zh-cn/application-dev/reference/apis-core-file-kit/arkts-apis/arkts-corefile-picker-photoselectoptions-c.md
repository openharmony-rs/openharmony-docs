# PhotoSelectOptions

图库选择选项。

**起始版本：** 9

**废弃版本：** 12

**替代接口：** PhotoSelectOptions

<!--Device-picker-class PhotoSelectOptions--><!--Device-picker-class PhotoSelectOptions-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

## 导入模块

```TypeScript
import { picker } from '@kit.CoreFileKit';
```

## MIMEType

```TypeScript
MIMEType?: PhotoViewMIMETypes
```

可选择的媒体文件类型。若无此参数，则默认为图片和视频类型。

**类型：** PhotoViewMIMETypes

**起始版本：** 9

**废弃版本：** 18

**替代接口：** MIMEType

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoSelectOptions-MIMEType?: PhotoViewMIMETypes--><!--Device-PhotoSelectOptions-MIMEType?: PhotoViewMIMETypes-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

## maxSelectNumber

```TypeScript
maxSelectNumber?: number
```

选择媒体文件数量的最大值，默认值为50，最大值为500。

**类型：** number

**起始版本：** 9

**废弃版本：** 18

**替代接口：** maxSelectNumber

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoSelectOptions-maxSelectNumber?: number--><!--Device-PhotoSelectOptions-maxSelectNumber?: number-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

