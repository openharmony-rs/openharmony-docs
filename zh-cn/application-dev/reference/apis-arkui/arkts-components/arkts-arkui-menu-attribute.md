# Menu属性/事件

除支持通用属性外，还支持以下属性：

**继承/实现关系：** MenuAttribute extends CommonMethod\<MenuAttribute>

**起始版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## font

```TypeScript
font(value: Font)
```

统一设置Menu中所有文本的字体样式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Font | 是 | Menu中所有文本的字体样式。默认值：{size: 16,family: 'HarmonyOS Sans',weight: FontWeight.Medium,style: FontStyle.Normal} |

## fontColor

```TypeScript
fontColor(value: ResourceColor)
```

统一设置Menu中所有文本的颜色。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | Menu中所有文本的颜色。 |

## fontSize

```TypeScript
fontSize(value: Length)
```

统一设置Menu中所有文本的尺寸。

> **说明：**
> 
> 从API version 9开始支持，从API version 10开始废弃，建议使用[font](#font)代替。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [font](#font)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | Menu中所有文本的尺寸，Length为number类型时，使用fp单位。不支持设置百分比。 |

## menuItemDivider

```TypeScript
menuItemDivider(options: DividerStyleOptions | undefined)
```

设置MenuItem分割线样式，不设置该属性则不展示分割线。startMargin + endMargin超过组件宽度后startMargin和endMargin会被置0。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DividerStyleOptions](../arkts-apis/arkts-arkui-dividerstyleoptions-i.md) \| undefined | 是 | 设置MenuItem分割线样式。   -strokeWidth：分割线的线宽，默认值是1px。   -color：分割线的颜色，默认值是#33000000。   -startMargin：分割线与MenuItem侧边起始端的距离，默认为16vp，单位为vp。   -endMargin：分割线与MenuItem侧边结束端的距离，默认为16vp，单位为vp。   -mode：分割线的模式，默认值为FLOATING_ABOVE_MENU。   startMargin + endMargin超过组件宽度后startMargin和endMargin会被置0。 |

## menuItemGroupDivider

```TypeScript
menuItemGroupDivider(options: DividerStyleOptions | undefined)
```

设置MenuItemGroup顶部和底部分割线的样式，不设置该属性则默认展示分割线。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DividerStyleOptions](../arkts-apis/arkts-arkui-dividerstyleoptions-i.md) \| undefined | 是 | 设置MenuItemGroup顶部和底部分割线样式。   -strokeWidth：分割线的线宽，默认值是1px。   -color：分割线的颜色，默认值是#33000000。   -startMargin：分割线与MenuItemGroup侧边起始端的距离，默认为16vp，单位为vp。   -endMargin：分割线与MenuItemGroup侧边结束端的距离，默认为16vp，单位为vp。   -mode：分割线的模式，默认值为FLOATING_ABOVE_MENU。   startMargin + endMargin超过组件宽度后startMargin和endMargin会被置0。 |

## radius

```TypeScript
radius(value: Dimension | BorderRadiuses)
```

设置Menu边框圆角半径。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) \| [BorderRadiuses](../arkts-apis/arkts-arkui-borderradiuses-t.md) | 是 | Menu边框圆角半径。默认值：2in1设备上默认值为8vp，其他设备上默认值为20vp。从API version 12开始，当水平方向两个圆角半径之和的最大值大于菜单宽度，或垂直方向两个圆角半径之和的最大值大于菜单高度时，菜单四个圆角均采用菜单默认圆角半径值。当设置Dimension类型且传参为异常值时，菜单圆角取默认 值。当设置BorderRadiuses类型且传参为异常值时，菜单默认没有圆角。 |

## subMenuExpandingMode

```TypeScript
subMenuExpandingMode(mode: SubMenuExpandingMode)
```

设置Menu子菜单展开样式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [SubMenuExpandingMode](arkts-arkui-submenuexpandingmode-e.md) | 是 | Menu子菜单展开样式。默认值：SubMenuExpandingMode.SIDE_EXPAND |

## subMenuExpandSymbol

```TypeScript
subMenuExpandSymbol(symbol: SymbolGlyphModifier)
```

设置Menu子菜单展开符号。仅在SubMenuExpandingMode.EMBEDDED_EXPAND或SubMenuExpandingMode.STACK_EXPAND模式下显示，SubMenuExpandingMode.SIDE_EXPAND模式下不显示。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| symbol | SymbolGlyphModifier | 是 | Menu子菜单展开符号。1、子菜单的展开样式为SubMenuExpandingMode.SIDE_EXPAND时，不显示展开符号。2、子菜单的展开样式为SubMenuExpandingMode.EMBEDDED_EXPAND时，展开时展开符号会顺时针旋转180°。默认值： `\\$r('sys.symbol.chevron_down').fontSize('24vp')` 3、子菜单的展开样式为SubMenuExpandingMode.STACK_EXPAND时，展开时展开符号会顺 时针旋转90°。默认值：`\\$r('sys.symbol.chevron_forward').fontSize('20vp').padding('2vp')` |
