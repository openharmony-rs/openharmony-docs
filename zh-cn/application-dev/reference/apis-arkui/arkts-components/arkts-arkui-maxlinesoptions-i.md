# MaxLinesOptions

配置TextArea组件，文本超长时的显示效果。

**起始版本：** 20

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## overflowMode

```TypeScript
overflowMode?: MaxLinesMode
```

`overflowMode`可配置[TextArea](arkts-arkui-textarea.md)组件的非内联模式。当超出设置的`maxLines`最大行数时，会启用滚动效果。需同时配置
[textOverflow](TextAreaAttribute#textOverflow)，且仅当`textOverflow`为None或Clip时，`MaxLinesMode`才能生效。默认情况下，
`MaxLinesMode`的值为Clip，超出`maxLines`后文本会被截断。

**类型：** MaxLinesMode

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

