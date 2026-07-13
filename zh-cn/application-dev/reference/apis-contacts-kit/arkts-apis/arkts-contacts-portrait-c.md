# Portrait

联系人的头像类。

> **说明：**
>
> 从API version 22开始，支持通过uri和[PixelMap](../../apis-image-kit/arkts-apis/arkts-image-pixelmap-i.md)格式设置联系人头像资源(暂不支持通过
> [addContactViaUI](arkts-contacts-addcontactviaui-f.md#addcontactviaui-1)、
> [saveToExistingContactViaUI](arkts-contacts-savetoexistingcontactviaui-f.md#savetoexistingcontactviaui-1)接口设置)。
>
> uri为可访问的联系人头像文件地址，[PixelMap](../../apis-image-kit/arkts-apis/arkts-image-pixelmap-i.md)为通过联系人头像资源生成的
> [PixelMap](../../apis-image-kit/arkts-apis/arkts-image-pixelmap-i.md)对象。
>
> 从API version 22开始，支持通过uri格式读取联系人头像资源，该格式仅支持以
> [fs.open](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-open-f.md#open-1)方式打开，无法直接在Image组件内显示，需读取后转换为
> [PixelMap](../../apis-image-kit/arkts-apis/arkts-image-pixelmap-i.md)格式显示。

**起始版本：** 7

**系统能力：** SystemCapability.Applications.ContactsData

## photo

```TypeScript
photo?: image.PixelMap
```

PixelMap格式的联系人头像。

**类型：** image.PixelMap

**起始版本：** 22

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

## uri

```TypeScript
uri: string
```

uri格式联系人头像。

**类型：** string

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

