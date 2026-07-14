# DecorationOptions

文本装饰线样式的额外配置选项对象说明。

**起始版本：** 20

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableMultiType

```TypeScript
enableMultiType?: boolean
```

是否开启多装饰线显示。

默认值：undefined。设置为true开启，设置为false/undefined关闭。

所有需要显示的装饰线都必须启用此选项，在这些装饰线的交集区域显示多装饰线效果，样式、颜色和粗细将采用最后设置的装饰线的效果。

**类型：** boolean

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

