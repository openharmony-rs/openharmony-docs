# ResultInfo（系统接口）

复制操作的结果信息。

**起始版本：** 26.0.0

<!--Device-photoAccessHelper-interface ResultInfo--><!--Device-photoAccessHelper-interface ResultInfo-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## code

```TypeScript
readonly code: int
```

复制操作的结果码。异常返回错误码23800151和23800301。

**类型：** int

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ResultInfo-readonly code: int--><!--Device-ResultInfo-readonly code: int-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## result

```TypeScript
readonly result: Array<string|null>
```

复制操作的结果信息。

**类型：** Array&lt;string \| null&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ResultInfo-readonly result: Array<string|null>--><!--Device-ResultInfo-readonly result: Array<string|null>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

