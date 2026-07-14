# CmsGeneratorOptions

表示生成CMS消息的配置选项。

**起始版本：** 18

**系统能力：** SystemCapability.Security.Cert

## contentDataFormat

```TypeScript
contentDataFormat?: CmsContentDataFormat
```

内容数据的格式。默认为CmsContentDataFormat.BINARY。

**类型：** CmsContentDataFormat

**默认值：** CmsContentDataFormat.BINARY

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Cert

## isDetached

```TypeScript
isDetached?: boolean
```

Cms最终数据是否不包含原始数据。默认为false。true为不包含，false为包含。

**类型：** boolean

**默认值：** false

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Cert

## outFormat

```TypeScript
outFormat?: CmsFormat
```

Cms最终数据的输出格式。默认为DER。

**类型：** CmsFormat

**默认值：** CmsFormat.DER

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Cert

