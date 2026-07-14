# UploadRequestOptions

**起始版本：** 3

**废弃版本：** 9

**替代接口：** [UploadConfig](arkts-basicservices-uploadconfig-i.md)

**系统能力：** SystemCapability.MiscServices.Upload

## complete

```TypeScript
complete?: () => void
```

Called when the execution is completed.

**类型：** () => void

**起始版本：** 3

**废弃版本：** 9

**替代接口：** on

**系统能力：** SystemCapability.MiscServices.Upload

## data

```TypeScript
data?: Array<RequestData>
```

Form data in the request body.

**类型：** Array<RequestData>

**起始版本：** 3

**废弃版本：** 9

**替代接口：** data

**系统能力：** SystemCapability.MiscServices.Upload

## fail

```TypeScript
fail?: (data: any, code: number) => void
```

Called when uploading fails.

**类型：** (data: any, code: number) => void

**起始版本：** 3

**废弃版本：** 9

**替代接口：** on

**系统能力：** SystemCapability.MiscServices.Upload

## files

```TypeScript
files: Array<RequestFile>
```

List of files to upload, which is submitted through multipart/form-data.

**类型：** Array<RequestFile>

**起始版本：** 3

**废弃版本：** 9

**替代接口：** data

**系统能力：** SystemCapability.MiscServices.Upload

## header

```TypeScript
header?: Object
```

Request header.

**类型：** Object

**起始版本：** 3

**废弃版本：** 9

**替代接口：** headers

**系统能力：** SystemCapability.MiscServices.Upload

## method

```TypeScript
method?: string
```

Request methods available: POST and PUT. The default value is POST.

**类型：** string

**起始版本：** 3

**废弃版本：** 9

**替代接口：** method

**系统能力：** SystemCapability.MiscServices.Upload

## success

```TypeScript
success?: (data: UploadResponse) => void
```

Called when the files are uploaded successfully.

**类型：** (data: UploadResponse) => void

**起始版本：** 3

**废弃版本：** 9

**替代接口：** on

**系统能力：** SystemCapability.MiscServices.Upload

## url

```TypeScript
url: string
```

Resource URL.

**类型：** string

**起始版本：** 3

**废弃版本：** 9

**替代接口：** url

**系统能力：** SystemCapability.MiscServices.Upload

