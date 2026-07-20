# RichEditorChangeValue

图文变化信息。

**起始版本：** 12

<!--Device-unnamed-declare interface RichEditorChangeValue--><!--Device-unnamed-declare interface RichEditorChangeValue-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## changeReason

```TypeScript
changeReason?: TextChangeReason
```

组件内容变化的原因，用于标识触发内容变化的操作类型（如用户输入、粘贴、剪切等），需通过注册onWillChange回调获取。开发者可根据changeReason的值在onWillChange回调中针对不同变化原因做出相应处理决策。字段缺省值为undefined。

**类型：** TextChangeReason

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorChangeValue-changeReason?: TextChangeReason--><!--Device-RichEditorChangeValue-changeReason?: TextChangeReason-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

