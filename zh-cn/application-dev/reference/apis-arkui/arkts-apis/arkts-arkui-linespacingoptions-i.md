# LineSpacingOptions

设置文本的行间距，是否仅在行与行之间生效。

**起始版本：** 20

<!--Device-unnamed-declare interface LineSpacingOptions--><!--Device-unnamed-declare interface LineSpacingOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onlyBetweenLines

```TypeScript
onlyBetweenLines?: boolean
```

文本的行间距是否仅在行与行之间生效。

当设置为true时，行间距仅适用于行与行之间，首行上方和尾行下方无额外的行间距。当设置为false时，首行上方和尾行下方均会存在行间距。

默认值：false

**类型：** boolean

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-LineSpacingOptions-onlyBetweenLines?: boolean--><!--Device-LineSpacingOptions-onlyBetweenLines?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

