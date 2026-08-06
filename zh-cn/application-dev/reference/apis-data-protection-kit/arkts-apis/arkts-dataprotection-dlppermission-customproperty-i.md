# CustomProperty

表示自定义策略。

**起始版本：** 21

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

<!--Device-dlpPermission-export interface CustomProperty--><!--Device-dlpPermission-export interface CustomProperty-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## enterprise

```TypeScript
enterprise: string
```

表示企业定制策略的JSON字符串。长度不超过2\_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_22\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_字节，超出此范围抛出错误码401。

**类型：** string

**起始版本：** 21

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

<!--Device-CustomProperty-enterprise: string--><!--Device-CustomProperty-enterprise: string-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## options

```TypeScript
options?: DlpFileQueryOptions
```

企业DLP文件的查询选项，默认为空。

**类型：** DlpFileQueryOptions

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomProperty-options?: DlpFileQueryOptions--><!--Device-CustomProperty-options?: DlpFileQueryOptions-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

