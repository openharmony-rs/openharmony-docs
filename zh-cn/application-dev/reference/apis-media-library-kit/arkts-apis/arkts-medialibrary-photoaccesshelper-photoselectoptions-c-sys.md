# PhotoSelectOptions

图库选择选项子类，继承于BaseSelectOptions。用于拉起对应userId空间的picker。

**继承/实现关系：** PhotoSelectOptions extends [BaseSelectOptions](arkts-medialibrary-photoaccesshelper-baseselectoptions-c.md#baseselectoptions)

**起始版本：** 26.0.0

**ArkTS模式：** 起始版本为26.0.0。

**废弃版本：** -1

<!--Device-photoAccessHelper-class PhotoSelectOptions--><!--Device-photoAccessHelper-class PhotoSelectOptions-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## themeColor

```TypeScript
themeColor?: CustomColors
```

Theme color

**类型：** [CustomColors](../../apis-arkui/arkts-apis/arkts-arkui-customcolors-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 起始版本为26.0.0。

**废弃版本：** -1

<!--Device-PhotoSelectOptions-themeColor?: CustomColors--><!--Device-PhotoSelectOptions-themeColor?: CustomColors-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## userId

```TypeScript
userId?: int
```

指定访问空间的Id。默认值为-1。 当需要作为 [PhotoViewPicker.select](arkts-medialibrary-photoaccesshelper-photoviewpicker-c.md#select) 的选择参数时，请申请ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS。

**类型：** int

**起始版本：** 26.0.0

**ArkTS模式：** 起始版本为26.0.0。

**废弃版本：** -1

<!--Device-PhotoSelectOptions-userId?: int--><!--Device-PhotoSelectOptions-userId?: int-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

