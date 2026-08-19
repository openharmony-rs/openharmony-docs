# Select

提供下拉选择菜单，让用户在多个选项间选择。Select组件支持设置选项图标、自定义样式、分割线等，适用于需要在有限空间内展示多个选项供用户选择的场景。 > **说明：**

## 子组件 无

## Select

```TypeScript
Select(options: Array<SelectOption>)
```

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SelectInterface-(options: Array<SelectOption>): SelectAttribute--><!--Device-SelectInterface-(options: Array<SelectOption>): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | Array&lt;SelectOption&gt; | 是 | 设置下拉选项。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [MenuItemConfiguration](arkts-arkui-menuitemconfiguration-i.md) | 开发者需要自定义class实现ContentModifier接口。继承自CommonConfiguration。 |
| [MenuOutlineOptions](arkts-arkui-menuoutlineoptions-i.md) | 下拉菜单框的外描边参数对象。 |

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

