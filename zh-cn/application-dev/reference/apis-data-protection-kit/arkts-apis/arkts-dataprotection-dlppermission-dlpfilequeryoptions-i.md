# DlpFileQueryOptions

表示企业DLP文件的查询选项。

**起始版本：** 26.0.0

<!--Device-dlpPermission-export interface DlpFileQueryOptions--><!--Device-dlpPermission-export interface DlpFileQueryOptions-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## 导入模块

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## classificationLabel

```TypeScript
classificationLabel?: string
```

表示企业DLP文件的用户定义分类标签。默认为空。最大长度为255字节，超出此范围抛出错误码19100001。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DlpFileQueryOptions-classificationLabel?: string--><!--Device-DlpFileQueryOptions-classificationLabel?: string-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

