# SymbolSpan

SymbolSpan作为Text组件的子组件，用于在文本中显示系统预置的图标小符号（Symbol图标）。支持设置颜色、大小、粗细、渲染策略和动效策略等属性，适用于需要在文本中嵌入图标符号的场景，如状态指示、功能标识等。SymbolSpan仅支持系统预置的symbol资源，可继承父组件Text的属性设置。

> **说明：** > > - 该组件支持继承父组件Text的属性，即如果子组件未设置属性且父组件设置属性，则继承父组件设置的全部属性。 > > - SymbolSpan拖拽不会置灰显示。

## 子组件

不支持子组件。

## SymbolSpan

```TypeScript
SymbolSpan(value: Resource)
```

定义SymbolSpan组件构造函数。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Resource](../arkts-apis/arkts-arkui-resource-t.md) | 是 | SymbolSpan组件的资源引用，如 &#36;r('sys.symbol.ohos_wifi')。仅支持系统预置的symbol资源，引用非symbol资源将显示异常。 |

## 汇总

## 示例

```TypeScript
### 示例1（设置渲染和动效策略）

从API version 11开始，该示例通过[renderingStrategy](#renderingstrategy)、[effectStrategy](#effectstrategy)属性展示了不同的渲染和动效策略。


```

```TypeScript
### 示例2（设置动态属性）

从API version 12开始，该示例通过[attributeModifier](#attributemodifier12)属性创建指定样式图标。


```

```TypeScript
### 示例3（设置字体粗细）

该示例通过[fontWeight](#fontweight-1)属性展示SymbolSpan不同粗细配置下的效果：第一行图标小符号展示启用可变字重后，分别设置字重值为220和660的效果；第二行图标小符号展示在将设备的系统字体粗细设置为粗体后，分别设置跟随和不跟随设备的字体粗细级别自动更新的效果。

从API版本26.0.0开始，新增[fontWeight](#fontweight-1)属性。
```
