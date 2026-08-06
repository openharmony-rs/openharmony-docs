# UploadResponse

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 9

**替代接口：** [@ohos.request:request.UploadConfig](arkts-basicservices-request-uploadconfig-i.md)

<!--Device-unnamed-export interface UploadResponse--><!--Device-unnamed-export interface UploadResponse-End-->

**系统能力：** SystemCapability.MiscServices.Upload

## code

```TypeScript
code: number
```

服务器返回的HTTP状态码。

**类型：** number

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 9

**替代接口：** ohos.request.agent.HttpResponse.statusCode

<!--Device-UploadResponse-code: number--><!--Device-UploadResponse-code: number-End-->

**系统能力：** SystemCapability.MiscServices.Upload

## data

```TypeScript
data: string
```

服务器返回的内容。根据返回头内容中的type决定该值的类型。

**类型：** string

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 9

**替代接口：** ohos.request.agent.Progress.extras

<!--Device-UploadResponse-data: string--><!--Device-UploadResponse-data: string-End-->

**系统能力：** SystemCapability.MiscServices.Upload

## headers

```TypeScript
headers: Object
```

服务器返回的返回头内容。

**类型：** Object

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 9

**替代接口：** ohos.request.agent.HttpResponse.headers

<!--Device-UploadResponse-headers: Object--><!--Device-UploadResponse-headers: Object-End-->

**系统能力：** SystemCapability.MiscServices.Upload

