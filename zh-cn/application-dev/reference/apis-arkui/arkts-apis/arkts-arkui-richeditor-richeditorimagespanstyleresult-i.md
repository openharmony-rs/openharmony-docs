# RichEditorImageSpanStyleResult

后端返回的图片样式信息。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface RichEditorImageSpanStyleResult--><!--Device-unnamed-export declare interface RichEditorImageSpanStyleResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## layoutStyle

```TypeScript
layoutStyle?: RichEditorLayoutStyle
```

图片布局风格。

**类型：** [RichEditorLayoutStyle](arkts-arkui-richeditor-richeditorlayoutstyle-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorImageSpanStyleResult-layoutStyle?: RichEditorLayoutStyle--><!--Device-RichEditorImageSpanStyleResult-layoutStyle?: RichEditorLayoutStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## objectFit

```TypeScript
objectFit: ImageFit
```

图片缩放类型。

**类型：** [ImageFit](arkts-arkui-imagefit-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorImageSpanStyleResult-objectFit: ImageFit--><!--Device-RichEditorImageSpanStyleResult-objectFit: ImageFit-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size: [
        int,
        int
    ]
```

图片的宽度和高度，单位为px。默认值：size的默认值与objectFit的值有关，不同的objectFit值对应的size默认值也不同。objectFit的值为Cover时，图片高度为组件高度减去组件上下内边距，图片宽度为组 件宽度减去组件左右内边距。

**类型：** [         int,         int     ]

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorImageSpanStyleResult-size: [        int,        int    ]--><!--Device-RichEditorImageSpanStyleResult-size: [        int,        int    ]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## verticalAlign

```TypeScript
verticalAlign: ImageSpanAlignment
```

图片垂直对齐方式。

**类型：** [ImageSpanAlignment](arkts-arkui-imagespanalignment-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorImageSpanStyleResult-verticalAlign: ImageSpanAlignment--><!--Device-RichEditorImageSpanStyleResult-verticalAlign: ImageSpanAlignment-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

