# PhotoSelectOptions

Defines additional options for selecting media assets from Gallery. It inherits from **BaseSelectOptions**. It is used to start the picker of the corresponding user ID space.

**Inheritance/Implementation:** PhotoSelectOptions extends [BaseSelectOptions](arkts-medialibrary-photoaccesshelper-baseselectoptions-c.md)

**Since:** 10

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## themeColor

```TypeScript
themeColor?: CustomColors
```

Theme color

**Type:** [CustomColors](../../apis-arkui/arkts-apis/arkts-arkui-customcolors-t.md)

**Since:** 12

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## userId

```TypeScript
userId?: number
```

ID of the user space to access. The default value is **-1**.

To use it as a parameter of [PhotoViewPicker.select](arkts-medialibrary-photoaccesshelper-photoviewpicker-c.md#select), request the permission **ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS**.

**Type:** number

**Since:** 18

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.
