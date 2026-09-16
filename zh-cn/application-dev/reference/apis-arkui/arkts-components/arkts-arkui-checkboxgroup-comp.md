# CheckboxGroup

多选框群组，用于控制多选框全选或取消全选状态。适用于需要批量管理多个Checkbox选择状态的场景，如列表项批量选择、表单全选等，可简化用户操作，提升交互体验。

> **说明：**

## 子组件

无

## CheckboxGroup

```TypeScript
CheckboxGroup(options?: CheckboxGroupOptions)
```

创建多选框群组，用于控制群组内Checkbox的全选或取消全选状态，具有相同group值的Checkbox和CheckboxGroup属于同一群组。

在结合带缓存功能的组件使用时（如List），未被创建的Checkbox选中状态需要应用手动控制。详细示例请参考示例4。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [CheckboxGroupOptions](arkts-arkui-checkboxgroupoptions-i.md) | 否 | 配置多选框群组参数。<br> 未设置时，按照CheckboxGroupOptions中各参数的默认值配置。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [CheckBoxGroupConfiguration](arkts-arkui-checkboxgroupconfiguration-i.md) | 开发者必须自定义此类以实现ContentModifier接口，使用方法见[contentModifier](arkts-arkui-checkboxgroup-comp-attribute.md#contentmodifier)。 |
| [CheckboxGroupOptions](arkts-arkui-checkboxgroupoptions-i.md) | 多选框群组的信息。 |
| [CheckboxGroupResult](arkts-arkui-checkboxgroupresult-i.md) | 多选框群组的名称和状态。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnCheckboxGroupChangeCallback](arkts-arkui-oncheckboxgroupchangecallback-t.md) | 多选框群组的信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [SelectStatus](arkts-arkui-selectstatus-e.md) | 多选框群组的选中状态。 |

## 示例

```TypeScript
### 示例1（设置多选框群组）

该示例用于控制多选框群组的全选或取消全选状态。


```

```TypeScript
### 示例2（自定义勾选样式）

该示例通过配置CheckboxGroup的mark属性，实现自定义多选框群组的勾选样式。


```

```TypeScript
### 示例3（自定义多选框样式）

该示例通过[contentModifier](#contentmodifier21)属性实现了自定义复选框群组样式的功能。自定义样式实现了一个五边形复选框群组，如果全部选中，内部会出现红色三角图案，标题会显示全选字样；如果部分选中，三角图案显示蓝色，标题会显示部分选中字样；如果未选中，三角图案消失，标题会显示未选中。

从API version 21开始，支持contentModifier属性。


```

```TypeScript
### 示例4（设置全选）

该示例展示了在结合带缓存功能的组件（如List）使用时，手动控制未被创建的Checkbox选中状态。
```
