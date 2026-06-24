# DocumentSaveOptions

文档保存选项。

**起始版本：** 9

**系统能力：** SystemCapability.FileManagement.UserFileService

## themeColor

```TypeScript
themeColor?: CustomColors
```

主题色参数, 默认为空，跟随FilePicker应用颜色。当themeColor设置为特定的主题色属性
（[brand, fontPrimary, compBackgroundEmphasize, iconFourth](@ohos.arkui.theme:Colors)）时，
被拉起的FilePicker应用将适配传入的主题色参数的效果。

该接口在Phone设备中可正常调用，在其他设备中无效果。

**类型：** CustomColors

**起始版本：** 18

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

