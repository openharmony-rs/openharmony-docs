# Portrait

联系人的头像类。

> **说明：**
> 
> 从API version 22开始，支持通过uri和[PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)格式设置联系人头像资源(暂不支持通过
> [addContactViaUI](arkts-contacts-contact-addcontactviaui-f.md)、
> [saveToExistingContactViaUI](arkts-contacts-contact-savetoexistingcontactviaui-f.md)接口设置)。
> 
> uri为可访问的联系人头像文件地址，[PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)为通过联系人头像资源生成的
> [PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)对象。
> 
> 从API version 22开始，支持通过uri格式读取联系人头像资源，该格式仅支持以
> [fs.open](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-open-f.md)方式打开，无法直接在Image组件内显示，需读取后转换为
> [PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)格式显示。

**起始版本：** 7

**系统能力：** SystemCapability.Applications.ContactsData

## 导入模块

```TypeScript
import { contact } from '@kit.ContactsKit';
```

## photo

```TypeScript
photo?: image.PixelMap
```

PixelMap格式的联系人头像。

**类型：** image.PixelMap

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

## uri

```TypeScript
uri: string
```

uri格式联系人头像。

**类型：** string

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

**示例**

使用JSON格式创建数据。

```TypeScript
import { contact } from '@kit.ContactsKit';
import { image } from '@kit.ImageKit';

async function SetPortraitUri(uri: string) {
  let portrait: contact.Portrait = {
    uri: uri
  };
}

async function SetPortraitPixelMap(photo: image.PixelMap) {
  let portrait: contact.Portrait = {
    uri: '',
    photo: photo
  };
}
```
