# StyledStringChangedListener

属性字符串的文本内容变化监听器。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## onDidChange

```TypeScript
onDidChange?: OnDidChangeCallback
```

文本内容完成变化回调函数。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillChange

```TypeScript
onWillChange?: Callback<StyledStringChangeValue, boolean>
```

文本内容将要变化回调函数。

**类型：** Callback&lt;[StyledStringChangeValue](arkts-arkui-styledstringchangevalue-i.md), boolean&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
