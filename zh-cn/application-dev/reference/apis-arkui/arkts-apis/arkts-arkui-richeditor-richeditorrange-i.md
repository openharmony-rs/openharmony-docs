# RichEditorRange

定义RichEditor的范围。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface RichEditorRange--><!--Device-unnamed-export declare interface RichEditorRange-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## end

```TypeScript
end?: int
```

需要更新样式的文本结束位置，省略或者超出文本范围时表示无穷大。

**类型：** int

**默认值：** text length

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorRange-end?: int--><!--Device-RichEditorRange-end?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start?: int
```

需要更新样式的文本起始位置，省略或者设置负值时表示从0开始。

**类型：** int

**默认值：** 0

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorRange-start?: int--><!--Device-RichEditorRange-start?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

