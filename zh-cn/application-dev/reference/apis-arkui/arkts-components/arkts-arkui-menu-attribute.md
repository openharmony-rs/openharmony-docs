# Menu属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

**继承/实现关系：** MenuAttribute extends [CommonMethod<MenuAttribute>](CommonMethod<MenuAttribute>)

**起始版本：** 9

<!--Device-unnamed-declare class MenuAttribute extends CommonMethod<MenuAttribute>--><!--Device-unnamed-declare class MenuAttribute extends CommonMethod<MenuAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## font

```TypeScript
font(value: Font)
```

统一设置Menu中所有文本的尺寸。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-MenuAttribute-font(value: Font): MenuAttribute--><!--Device-MenuAttribute-font(value: Font): MenuAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Font](../arkts-apis/arkts-arkui-arkui-uicontext-font-c.md) | 是 | Menu中所有文本的尺寸。<br/>默认值：<br/>{<br/> size: 16,<br/> family: 'HarmonyOS Sans',<br/>weight: FontWeight.Medium,<br/> style: FontStyle.Normal<br/>} |

## fontColor

```TypeScript
fontColor(value: ResourceColor)
```

统一设置Menu中所有文本的颜色。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-MenuAttribute-fontColor(value: ResourceColor): MenuAttribute--><!--Device-MenuAttribute-fontColor(value: ResourceColor): MenuAttribute-End-->

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
> 从API version 9开始支持，从API version 10开始废弃，建议使用[font](MenuAttribute#font)代替。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** font

<!--Device-MenuAttribute-fontSize(value: Length): MenuAttribute--><!--Device-MenuAttribute-fontSize(value: Length): MenuAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | Menu中所有文本的尺寸，Length为number类型时，使用fp单位。不支持设置百分比。 |

## menuItemDivider

```TypeScript
menuItemDivider(options: DividerStyleOptions | undefined)
```

设置menuItem分割线样式，不设置该属性则不展示分割线。

startMargin + endMargin 超过组件宽度后startMargin和endMargin会被置0。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MenuAttribute-menuItemDivider(options: DividerStyleOptions | undefined): MenuAttribute--><!--Device-MenuAttribute-menuItemDivider(options: DividerStyleOptions | undefined): MenuAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | DividerStyleOptions \| undefined | 是 | 设置menuItem分割线样式。<br />-strokeWidth：分割线的线宽。<br />-color：分割线的颜色。<br />-startMargin：分割线与menuItem侧边起始端的距离。<br />-endMargin：分割线与menuItem侧边结束端的距离。<br />-mode：分割线的模式，默认值为FLOATING_ABOVE_MENU。 |

## menuItemGroupDivider

```TypeScript
menuItemGroupDivider(options: DividerStyleOptions | undefined)
```

设置menuItemGroup上下分割线的样式，不设置该属性则默认展示分割线。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MenuAttribute-menuItemGroupDivider(options: DividerStyleOptions | undefined): MenuAttribute--><!--Device-MenuAttribute-menuItemGroupDivider(options: DividerStyleOptions | undefined): MenuAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | DividerStyleOptions \| undefined | 是 | 设置menuItemGroup顶部和底部分割线样式。<br />-strokeWidth：分割线的线宽，默认值是1px。<br />-color：分割线的颜色，默认值是 #33000000。<br />-startMargin：分割线与menuItemGroup侧边起始端的距离，默认为16vp，单位为vp。<br />-endMargin：分割线与menuItemGroup侧边结束端的距离，默认为16vp，单位为vp。<br />-mode：分割线的模式，默认值为FLOATING_ABOVE_MENU。 |

## radius

```TypeScript
radius(value: Dimension | BorderRadiuses)
```

设置Menu边框圆角半径。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-MenuAttribute-radius(value: Dimension | BorderRadiuses): MenuAttribute--><!--Device-MenuAttribute-radius(value: Dimension | BorderRadiuses): MenuAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Dimension \| BorderRadiuses | 是 | Menu边框圆角半径。<br/>默认值：2in1设备上默认值为8vp，其他设备上默认值为20vp。<br/> 从API version12开始，当水平方向两个圆角半径之和的最大值大于菜单宽度，或垂直方向两个圆角半径之和的最大值大于菜单高度时，菜单四个圆角均采用菜单默认圆角半径值。<br/>当设置Dimension类型且传参为异常值时，菜单圆角取默认值。<br/>当设置BorderRadiuses类型且传参为异常值时，菜单默认没有圆角。 |

## subMenuExpandSymbol

```TypeScript
subMenuExpandSymbol(symbol: SymbolGlyphModifier)
```

设置Menu子菜单展开符号。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-MenuAttribute-subMenuExpandSymbol(symbol: SymbolGlyphModifier): MenuAttribute--><!--Device-MenuAttribute-subMenuExpandSymbol(symbol: SymbolGlyphModifier): MenuAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| symbol | [SymbolGlyphModifier](arkts-arkui-symbolglyphmodifier-t.md) | 是 | Menu子菜单展开符号。<br/>1、子菜单的展开样式为SubMenuExpandingMode.SIDE_EXPAND时，不显示展开符号。<br/>2、子菜单的展开样式为SubMenuExpandingMode.EMBEDDED_EXPAND时，展开时展开符号会顺时针旋转180°。<br/>默认值：`$r('sys.symbol.chevron_down').fontSize('24vp')` <br/>3、子菜单的展开样式为SubMenuExpandingMode.STACK_EXPAND时，展开时展开符号会顺时针旋转90°。<br/>默认值：`$r('sys.symbol.chevron_forward').fontSize('20vp').padding('2vp')` |

## subMenuExpandingMode

```TypeScript
subMenuExpandingMode(mode: SubMenuExpandingMode)
```

设置Menu子菜单展开样式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MenuAttribute-subMenuExpandingMode(mode: SubMenuExpandingMode): MenuAttribute--><!--Device-MenuAttribute-subMenuExpandingMode(mode: SubMenuExpandingMode): MenuAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [SubMenuExpandingMode](arkts-arkui-menu-submenuexpandingmode-e.md) | 是 | Menu子菜单展开样式。<br/>默认值：SubMenuExpandingMode.SIDE_EXPAND |

