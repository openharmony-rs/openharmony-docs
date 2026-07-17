# DocumentSelectOptions

文档选择选项。

**起始版本：** 9

<!--Device-picker-class DocumentSelectOptions--><!--Device-picker-class DocumentSelectOptions-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

## 导入模块

```TypeScript
import { picker } from '@kit.CoreFileKit';
```

## themeColor

```TypeScript
themeColor?: CustomColors
```

主题色参数, 默认为空，跟随FilePicker应用颜色。当themeColor设置为特定的主题色属性（[brand, fontPrimary, compBackgroundEmphasize, iconFourth](../../apis-arkui/arkts-apis/arkts-arkui-arkui-theme-colors-i.md)）时，被拉起的FilePicker应用将适配传入的主题色参数的效果。

该接口在Phone设备中可正常调用，在其他设备中无效果。

**类型：** CustomColors

**起始版本：** 18

<!--Device-DocumentSelectOptions-themeColor?: CustomColors--><!--Device-DocumentSelectOptions-themeColor?: CustomColors-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

