# Select

提供下拉选择菜单，让用户在多个选项间选择。Select组件支持设置选项图标、自定义样式、分割线等，适用于需要在有限空间内展示多个选项供用户选择的场景。

> **说明：**

## 子组件

无

## Select

```TypeScript
Select(options: Array<SelectOption>)
```

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | Array&lt;[SelectOption](arkts-arkui-selectoption-i.md)&gt; | 是 | 设置下拉选项。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [MenuItemConfiguration](arkts-arkui-menuitemconfiguration-i.md) | 开发者需要自定义class实现ContentModifier接口。继承自[CommonConfiguration](arkts-arkui-commonconfiguration-i.md)。 |
| [MenuOutlineOptions](arkts-arkui-menuoutlineoptions-i.md) | 下拉菜单框的外描边参数对象。 |
| [SelectOption](arkts-arkui-selectoption-i.md) | 下拉菜单项的信息。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnSelectCallback](arkts-arkui-onselectcallback-t.md) | 下拉菜单选中某一项时触发的回调函数类型定义。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ArrowPosition](arkts-arkui-arrowposition-e.md) | 箭头的位置。 |
| [AvoidanceMode](arkts-arkui-avoidancemode-e.md) | 下拉菜单避让模式的枚举选项。 |
| [MenuAlignType](arkts-arkui-menualigntype-e.md) | 下拉菜单的对齐方式。 |

## 示例

```TypeScript
### 示例1（设置下拉菜单）

该示例通过配置[SelectOption](#selectoption对象说明)实现下拉菜单，并从API version 19开始通过设置[avoidance](arkts-arkui-select-comp-attribute.md#avoidance)属性实现菜单的避让方式。


```

```TypeScript
### 示例2（设置symbol类型图标）

该示例实现了一个下拉菜单中图片为Symbol的Select组件，并从API version 19开始通过设置[avoidance](arkts-arkui-select-comp-attribute.md#avoidance)属性实现菜单的避让方式。


```

```TypeScript
### 示例3（自定义下拉菜单）

该示例实现了一个自定义下拉菜单选项的Select组件。自定义下拉菜单选项样式为“文本 + Symbol图片 + 空白间隔 + 文本 + 绘制三角形”，点击菜单选项后Select组件显示菜单选项的文本内容。


```

```TypeScript
### 示例4（设置分割线样式）

该示例通过配置divider的DividerOptions类型实现分割线样式的下拉菜单，并从API version 19开始通过设置[avoidance](arkts-arkui-select-comp-attribute.md#avoidance)属性实现菜单的避让方式。


```

```TypeScript
### 示例5（设置无分割线样式）

该示例通过配置divider为null实现无分割线样式的下拉菜单，并从API version 19开始通过设置[avoidance](arkts-arkui-select-comp-attribute.md#avoidance)属性实现菜单的避让方式。


```

```TypeScript
### 示例6（设置Select中文本和箭头样式）

从API version 20开始，该示例通过[textModifier](#textmodifier20)和[arrowModifier](arkts-arkui-select-comp-attribute.md#arrowmodifier)属性设置文本以及箭头样式。


```

```TypeScript
### 示例7（设置Select下拉菜单选中和非选中项文本样式）

从API version 20开始，该示例通过[optionTextModifier](arkts-arkui-select-comp-attribute.md#optiontextmodifier)和[selectedOptionTextModifier](arkts-arkui-select-comp-attribute.md#selectedoptiontextmodifier)属性设置下拉菜单选中和非选中项文本样式。


```

```TypeScript
### 示例8（设置分割线模式）

从API version 19开始，该示例通过配置[DividerStyleOptions](ts-types.md#dividerstyleoptions12)的mode属性设置分割线模式。


```

```TypeScript
### 示例9（设置Select下拉菜单外描边样式）

从API version 20开始该示例通过配置menuOutline的width和color属性设置下拉菜单外描边样式。


```

```TypeScript
### 示例10（设置Select弹出菜单避让软键盘）

该示例通过调用[keyboardAvoidMode](#keyboardavoidmode23)和[minKeyboardAvoidDistance](#minkeyboardavoiddistance23)接口，实现下拉菜单避让软键盘并自定义避让软键盘的最小距离。

从API version 23开始，新增keyboardAvoidMode、minKeyboardAvoidDistance接口。


```

```TypeScript
### 示例11（设置Select和下拉菜单沉浸光感效果）

该示例通过调用[menuSystemMaterial](arkts-arkui-select-comp-attribute.md#menusystemmaterial)接口设置下拉菜单的系统材质，实现沉浸光感效果；通过[SystemUiMaterial](ts-universal-attributes-image-effect.md#systemuimaterial)接口设置Select组件的系统材质，实现沉浸光感效果。

该示例配图为高算力设备强档效果，组件沉浸光感效果会根据设备算力与用户在系统中设置的沉浸光感效果自适应调整，开发者无需额外适配。

从API版本26.0.0开始，新增menuSystemMaterial接口。
```
