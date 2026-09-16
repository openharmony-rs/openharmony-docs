# Checkbox

提供多选框组件，用于在多个选项中进行选择。

> **说明：** > > API version 11开始，Checkbox默认样式由圆角方形变为圆形。

## 子组件

无

## Checkbox

```TypeScript
Checkbox(options?: CheckboxOptions)
```

提供多选框组件，用于在多个选项中进行选择。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [CheckboxOptions](arkts-arkui-checkboxoptions-i.md) | 否 | 配置多选框的参数。不传入该参数时，多选框使用默认配置。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [CheckBoxConfiguration](arkts-arkui-checkboxconfiguration-i.md) | 开发者需要自定义class实现ContentModifier接口。继承自[CommonConfiguration](arkts-arkui-commonconfiguration-i.md)。 |
| [CheckboxOptions](arkts-arkui-checkboxoptions-i.md) | 多选框的信息。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnCheckboxChangeCallback](arkts-arkui-oncheckboxchangecallback-t.md) | 选中的状态。 |

## 示例

```TypeScript
### 示例1（设置多选框形状）

该示例通过配置CheckBoxShape实现圆形和圆角方形多选框样式。


```

```TypeScript
### 示例2（设置多选框颜色）

该示例通过配置mark实现自定义多选框的颜色。


```

```TypeScript
### 示例3（自定义多选框样式）

该示例通过[contentModifier](#contentmodifier12)属性实现自定义多选框样式，自定义样式实现了一个五边形多选框。选中时，内部显示红色三角图案，标题显示"选中"；取消选中时，红色三角图案消失，标题显示"非选中"。


```

```TypeScript
### 示例4（设置文本多选框样式）

该示例通过配置indicatorBuilder实现选中样式为Text。


```

```TypeScript
### 示例5（获取多选框选中信息）

该示例通过选中Checkbox以及CheckboxGroup多选框来获取选中的信息。


```

```TypeScript
### 示例6（设置滑动多选）

该示例通过设置手势事件实现Checkbox滑动多选。
```
