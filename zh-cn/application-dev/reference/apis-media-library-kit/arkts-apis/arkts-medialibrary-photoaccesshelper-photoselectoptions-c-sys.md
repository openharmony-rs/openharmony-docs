# PhotoSelectOptions

图库选择选项子类，继承于BaseSelectOptions。用于拉起对应userId空间的picker。

**继承/实现关系：** PhotoSelectOptions extends [BaseSelectOptions](arkts-medialibrary-photoaccesshelper-baseselectoptions-c.md)

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## themeColor

```TypeScript
themeColor?: CustomColors
```

Theme color

**类型：** [CustomColors](../../apis-arkui/arkts-apis/arkts-arkui-customcolors-t.md)

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## userId

```TypeScript
userId?: number
```

指定访问空间的Id。默认值为-1。当需要作为 [PhotoViewPicker.select](arkts-medialibrary-photoaccesshelper-photoviewpicker-c.md#select) 的选择参数时，请申请ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS。

**类型：** number

**起始版本：** 18

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**示例**

```TypeScript
async function photoPicker() {
    let picker = new photoAccessHelper.PhotoViewPicker();
    let option = new photoAccessHelper.PhotoSelectOptions();
    option.userId = 101;
    picker.select(option);
  }
```
