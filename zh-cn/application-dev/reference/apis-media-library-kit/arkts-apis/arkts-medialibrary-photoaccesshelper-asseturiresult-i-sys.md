# AssetUriResult（系统接口）

```TypeScript
interface AssetUriResult
```

媒体资产URI的操作结果信息。

**起始版本：** 26.1.0

<!--Device-photoAccessHelper-interface AssetUriResult--><!--Device-photoAccessHelper-interface AssetUriResult-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## isSuccess

```TypeScript
readonly isSuccess: boolean
```

操作是否成功。true表示成功，false表示失败，失败时resultUri为空字符串。

**类型：** boolean

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AssetUriResult-readonly isSuccess: boolean--><!--Device-AssetUriResult-readonly isSuccess: boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## originalUri

```TypeScript
readonly originalUri: string
```

操作对应的原始资产URI。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AssetUriResult-readonly originalUri: string--><!--Device-AssetUriResult-readonly originalUri: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## resultUri

```TypeScript
readonly resultUri: string
```

操作结果对应的资产URI。操作失败时为空字符串。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AssetUriResult-readonly resultUri: string--><!--Device-AssetUriResult-readonly resultUri: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。
