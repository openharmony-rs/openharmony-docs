# SymbolSpan

SymbolSpan作为Text组件的子组件，用于在文本中显示系统预置的图标小符号（Symbol图标）。支持设置颜色、大小、粗细、渲染策略和动效策略等属性，适用于需要在文本中嵌入图标符号的场景，如状态指示、功能标识等。 SymbolSpan仅支持系统预置的symbol资源，可继承父组件Text的属性设置。 > **说明：** > > - 该组件支持继承父组件Text的属性，即如果子组件未设置属性且父组件设置属性，则继承父组件设置的全部属性。 > > - SymbolSpan拖拽不会置灰显示。

## 子组件 不支持子组件。

## SymbolSpan

```TypeScript
SymbolSpan(value: Resource)
```

定义SymbolSpan组件构造函数。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-SymbolSpanInterface-(value: Resource): SymbolSpanAttribute--><!--Device-SymbolSpanInterface-(value: Resource): SymbolSpanAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Resource | 是 | SymbolSpan组件的资源引用，如 \$r('sys.symbol.ohos_wifi')。仅支持系统预置的symbol资源，引用非symbol资源将显示异常。 |

## 汇总

