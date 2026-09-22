# Portrait

```TypeScript
class Portrait
```

Defines a contact's portrait.

> **NOTE:** 
> 
> Since API version 22, contact portraits can be set in URI or [PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)
> format. (Currently, contact avatars cannot be set through the [addContactViaUI](arkts-contacts-contact-addcontactviaui-f.md) or
> [saveToExistingContactViaUI](arkts-contacts-contact-savetoexistingcontactviaui-f.md) API.)
> 
> URI indicates the address of the contact portrait file that can be accessed, and
> [PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) indicates the [PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)
> object generated based on the contact portrait resource.
> 
> Since API version 22, the profile picture resource can be read through URI. The resource can be opened only in
> [fs.open](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-open-f.md) mode and cannot be directly displayed in the **Image** component using a URI. You need to read
> the resource and display it in [PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) format.

**Since:** 7

**System capability:** SystemCapability.Applications.ContactsData

## Modules to Import

```TypeScript
import { contact } from '@kit.ContactsKit';
```

## photo

```TypeScript
photo?: image.PixelMap
```

Contact portrait in PixelMap format.

**Type:** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Applications.ContactsData

## uri

```TypeScript
uri: string
```

Contact portrait in URI format.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.ContactsData
