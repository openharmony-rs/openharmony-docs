# CustomProperty

表示自定义策略。

**起始版本：** 21

**系统能力：** SystemCapability.Security.DataLossPrevention

## 导入模块

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## enterprise

```TypeScript
enterprise: string
```

表示企业定制策略的JSON字符串。长度不超过2&lt;sup&gt;22&lt;/sup&gt;字节，超出此范围抛出错误码401。

**类型：** string

**起始版本：** 21

**系统能力：** SystemCapability.Security.DataLossPrevention

## options

```TypeScript
options?: DlpFileQueryOptions
```

企业DLP文件的查询选项，默认为空。

**类型：** [DlpFileQueryOptions](arkts-dataprotection-dlppermission-dlpfilequeryoptions-i.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.DataLossPrevention
