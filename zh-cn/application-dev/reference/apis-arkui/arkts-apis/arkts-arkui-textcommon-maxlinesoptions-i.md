# MaxLinesOptions

配置TextArea组件，文本超长时的显示效果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface MaxLinesOptions--><!--Device-unnamed-export declare interface MaxLinesOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## overflowMode

```TypeScript
overflowMode?: MaxLinesMode
```

`overflowMode`可配置[TextArea](../../../reference/apis-arkui/arkui-ts/ts-basic-components-textarea.md)组件的非内联模式。当超出设置的 `maxLines`最大行数时，会启用滚动效果。需同时配置 [textOverflow](../../../reference/apis-arkui/arkui-ts/ts-basic-components-textarea.md#textoverflow12)，且仅当 `textOverflow`为None或Clip时，`MaxLinesMode`才能生效。默认情况下，`MaxLinesMode`的值为Clip，超出`maxLines`后文本会被截断。

**类型：** [MaxLinesMode](arkts-arkui-textcommon-maxlinesmode-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MaxLinesOptions-overflowMode?: MaxLinesMode--><!--Device-MaxLinesOptions-overflowMode?: MaxLinesMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

