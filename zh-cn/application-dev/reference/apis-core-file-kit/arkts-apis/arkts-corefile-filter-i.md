# Filter

文件过滤配置项，支持listFile接口使用。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.File.FileIO

## displayName

```TypeScript
displayName?: Array<string>
```

文件名模糊匹配，各个关键词OR关系。当前仅支持通配符*。

**类型：** Array<string>

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.FileManagement.File.FileIO

## excludeMedia

```TypeScript
excludeMedia?: boolean
```

是否排除Media中已有的文件。true：排除Media中已有的文件；false：不排除Media中已有的文件。

**类型：** boolean

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.FileManagement.File.FileIO

## fileSizeOver

```TypeScript
fileSizeOver?: number
```

文件大小匹配，大于指定大小的文件，单位为Byte。

**类型：** number

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.FileManagement.File.FileIO

## lastModifiedAfter

```TypeScript
lastModifiedAfter?: number
```

文件最近修改时间匹配，在指定时间点及之后的文件。

**类型：** number

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.FileManagement.File.FileIO

## mimeType

```TypeScript
mimeType?: Array<string>
```

mime类型完全匹配，各个关键词OR关系。预留字段，暂不支持使用。

**类型：** Array<string>

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.FileManagement.File.FileIO

## suffix

```TypeScript
suffix?: Array<string>
```

文件后缀名完全匹配，各个关键词OR关系。

**类型：** Array<string>

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.FileManagement.File.FileIO

