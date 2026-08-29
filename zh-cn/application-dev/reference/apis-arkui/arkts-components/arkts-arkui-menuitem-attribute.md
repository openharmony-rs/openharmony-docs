# MenuItem属性/事件

除支持通用属性外，还支持以下属性：

**继承/实现关系：** MenuItemAttribute extends CommonMethod\<MenuItemAttribute>

**起始版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## contentFont

```TypeScript
contentFont(value: Font)
```

设置菜单项中内容信息的字体样式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Font | 是 | 菜单项中内容信息的字体样式。 |

## contentFontColor

```TypeScript
contentFontColor(value: ResourceColor)
```

设置菜单项中内容信息的字体颜色。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 菜单项中内容信息的字体颜色。默认值：'#E5000000' |

## labelFont

```TypeScript
labelFont(value: Font)
```

设置菜单项中标签信息的字体样式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Font | 是 | 菜单项中标签信息的字体样式。 |

## labelFontColor

```TypeScript
labelFontColor(value: ResourceColor)
```

设置菜单项中标签信息的字体颜色。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 菜单项中标签信息的字体颜色。默认值：'#99000000' |

## onChange

```TypeScript
onChange(callback: (selected: boolean) => void)
```

当选中状态发生变化时，触发该回调。只有手动触发且MenuItem状态改变时才会触发onChange回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (selected: boolean) =&gt; void | 是 | 当前菜单项是否被选中。true：当前菜单项已选中；false：当前菜单项未选中。 |

## selected

```TypeScript
selected(value: boolean)
```

设置菜单项是否选中。从API version 10开始，该参数支持[\$\$](../../../ui/state-management/arkts-two-way-sync.md)双向绑定变量。从API version 18开始，该参数支持[!!](../../../ui/state-management/arkts-new-binding.md#系统组件参数双向绑定)双向绑定变量。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 菜单项是否选中。true：菜单项被选中；false：菜单项不被选中。默认值：false |

## selectIcon

```TypeScript
selectIcon(value: boolean | ResourceStr | SymbolGlyphModifier)
```

设置当菜单项被选中时，菜单项图标的显示方式。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) \| SymbolGlyphModifier | 是 | 菜单项被选中时的图标显示方式。true：显示默认的对勾图标；false：不显示图标。ResourceStr：显示指定的图标。SymbolGlyphModifier：显示指定的HMSymbol图标。默认值：false<br>**起始版本：** 12 |

## subMenuBuilder

```TypeScript
subMenuBuilder(builder: CustomBuilder)
```

Create the submenu for custom menu item.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | [CustomBuilder](arkts-arkui-custombuilder-t.md) | 是 | Indicates the builder function for submenu. |
