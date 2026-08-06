# DocumentSaveOptions

文档保存选项。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

<!--Device-picker-class DocumentSaveOptions--><!--Device-picker-class DocumentSaveOptions-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

## themeColor

```TypeScript
themeColor?: CustomColors
```

主题色参数, 默认为空，跟随FilePicker应用颜色。当themeColor设置为特定的主题色属性 （[brand, fontPrimary, compBackgroundEmphasize, iconFourth]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_）时， 被拉起的FilePicker应用将适配传入的主题色参数的效果。 该接口在Phone设备中可正常调用，在其他设备中无效果。

**类型：** CustomColors

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-DocumentSaveOptions-themeColor?: CustomColors--><!--Device-DocumentSaveOptions-themeColor?: CustomColors-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

