# RichEditorBuilderSpanOptions

设置builder插入的偏移位置和样式。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## accessibilitySpanOptions

```TypeScript
accessibilitySpanOptions?: AccessibilitySpanOptions
```

无障碍朗读功能属性。缺省时，取[AccessibilitySpanOptions](../arkts-apis/arkts-arkui-accessibilityspanoptions-i.md)的默认值。

**类型：** [AccessibilitySpanOptions](../arkts-apis/arkts-arkui-accessibilityspanoptions-i.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: number
```

添加builder的位置。取值范围：[0, 所有内容长度]。省略或当值小于0或大于所有内容长度时，添加到所有内容最后面。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
