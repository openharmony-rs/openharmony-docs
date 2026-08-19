# SurfaceConfig

用于描述XComponent持有的Surface在渲染时是否需要被视为不透明。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface SurfaceConfig--><!--Device-unnamed-export declare interface SurfaceConfig-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isOpaque

```TypeScript
isOpaque?: boolean
```

XComponent持有的Surface在渲染时是否需要被视为不透明，未设置时默认取值为false， 即在渲染时会应用Surface中绘制内容像素的透明度。 true：表示需要被视为不透明；false：表示不需要被视为不透明。 默认值：false

**类型：** boolean

**默认值：** false

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SurfaceConfig-isOpaque?: boolean--><!--Device-SurfaceConfig-isOpaque?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

