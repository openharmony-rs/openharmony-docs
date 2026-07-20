# SymbolSpan

作为Text组件的子组件，用于显示图标小符号的组件。

> **说明：**

> - 本模块接口仅可在Stage模型下使用。
>
> - 该组件支持继承父组件Text的属性，即如果子组件未设置属性且父组件设置属性，则继承父组件设置的全部属性。
>
> - SymbolSpan拖拽不会置灰显示。

## 子组件

不支持子组件。

## SymbolSpan

```TypeScript
SymbolSpan(value: Resource)
```

定义SymbolSpan组件构造函数。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-SymbolSpanInterface-(value: Resource): SymbolSpanAttribute--><!--Device-SymbolSpanInterface-(value: Resource): SymbolSpanAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md) | 是 | SymbolSpan组件的资源名，如 $r('sys.symbol.ohos_wifi')。  |

## 汇总

