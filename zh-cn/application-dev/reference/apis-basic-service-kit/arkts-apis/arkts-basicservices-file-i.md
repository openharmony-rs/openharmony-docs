# File

[UploadConfig](arkts-basicservices-uploadconfig-i.md)中的文件列表。

**起始版本：** 6

**系统能力：** SystemCapability.MiscServices.Download

## filename

```TypeScript
filename: string
```

multipart提交时，请求头中的文件名。

**类型：** string

**起始版本：** 6

**系统能力：** SystemCapability.MiscServices.Download

## name

```TypeScript
name: string
```

multipart提交时，表单项目的名称，缺省为file。

**类型：** string

**起始版本：** 6

**系统能力：** SystemCapability.MiscServices.Download

## type

```TypeScript
type: string
```

文件的内容类型，默认根据文件名或路径的后缀获取。

**类型：** string

**起始版本：** 6

**系统能力：** SystemCapability.MiscServices.Download

## uri

```TypeScript
uri: string
```

文件的本地存储路径。

仅支持"internal://cache/"，即调用方（传入的context）对应的缓存路径context.cacheDir。

示例：internal://cache/path/to/file.txt

**类型：** string

**起始版本：** 6

**系统能力：** SystemCapability.MiscServices.Download

