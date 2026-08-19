# BlobOptions

定义Blob相关的options参数。

**起始版本：** 23

<!--Device-buffer-interface BlobOptions--><!--Device-buffer-interface BlobOptions-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { buffer } from '@kit.ArkTS';
```

## endings

```TypeScript
endings?: string
```

含义为结束符'\n'的字符串如何被输出，为'transparent'或'native'。native代表行结束符会跟随系统。'transparent'代表会保持Blob中保存的结束符不变。 此参数非必填，默认值为'transparent'。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-BlobOptions-endings?: string--><!--Device-BlobOptions-endings?: string-End-->

**系统能力：** SystemCapability.Utils.Lang

## type

```TypeScript
type?: string
```

Blob的内容类型。其目的是让类型传达数据的MIME媒体类型，但是不执行类型格式的验证。此参数非必填，默认参数为''。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-BlobOptions-type?: string--><!--Device-BlobOptions-type?: string-End-->

**系统能力：** SystemCapability.Utils.Lang

