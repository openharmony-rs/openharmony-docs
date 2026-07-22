# MenuItem属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

**继承/实现关系：** MenuItemAttribute extends [CommonMethod<MenuItemAttribute>](CommonMethod<MenuItemAttribute>)

**起始版本：** 9

<!--Device-unnamed-declare class MenuItemAttribute extends CommonMethod<MenuItemAttribute>--><!--Device-unnamed-declare class MenuItemAttribute extends CommonMethod<MenuItemAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## contentFont

```TypeScript
contentFont(value: Font)
```

设置菜单项中内容信息的字体样式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-MenuItemAttribute-contentFont(value: Font): MenuItemAttribute--><!--Device-MenuItemAttribute-contentFont(value: Font): MenuItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Font](../arkts-apis/arkts-arkui-arkui-uicontext-font-c.md) | 是 | 菜单项中内容信息的字体样式。 |

## contentFontColor

```TypeScript
contentFontColor(value: ResourceColor)
```

设置菜单项中内容信息的字体颜色。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-MenuItemAttribute-contentFontColor(value: ResourceColor): MenuItemAttribute--><!--Device-MenuItemAttribute-contentFontColor(value: ResourceColor): MenuItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 菜单项中内容信息的字体颜色。<br />默认值：'#E5000000' |

## labelFont

```TypeScript
labelFont(value: Font)
```

设置菜单项中标签信息的字体样式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-MenuItemAttribute-labelFont(value: Font): MenuItemAttribute--><!--Device-MenuItemAttribute-labelFont(value: Font): MenuItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Font](../arkts-apis/arkts-arkui-arkui-uicontext-font-c.md) | 是 | 菜单项中标签信息的字体样式。 |

## labelFontColor

```TypeScript
labelFontColor(value: ResourceColor)
```

设置菜单项中标签信息的字体颜色。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-MenuItemAttribute-labelFontColor(value: ResourceColor): MenuItemAttribute--><!--Device-MenuItemAttribute-labelFontColor(value: ResourceColor): MenuItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 菜单项中标签信息的字体颜色。<br />默认值：'#99000000' |

## onChange

```TypeScript
onChange(callback: (selected: boolean) => void)
```

当选中状态发生变化时，触发该回调。只有手动触发且MenuItem状态改变时才会触发onChange回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-MenuItemAttribute-onChange(callback: (selected: boolean) => void): MenuItemAttribute--><!--Device-MenuItemAttribute-onChange(callback: (selected: boolean) => void): MenuItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (selected: boolean) =&gt; void | 是 | 选中状态发生变化时，触发该回调。<br />true：未选中切换为选中；false：选中切换为未选中。 |

## selectIcon

```TypeScript
selectIcon(value: boolean | ResourceStr | SymbolGlyphModifier)
```

设置当菜单项被选中时，是否显示被选中的图标。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-MenuItemAttribute-selectIcon(value: boolean | ResourceStr | SymbolGlyphModifier): MenuItemAttribute--><!--Device-MenuItemAttribute-selectIcon(value: boolean | ResourceStr | SymbolGlyphModifier): MenuItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| ResourceStr \| SymbolGlyphModifier | 是 | 菜单项被选中时，是否显示被选中的图标。<br/>true：显示默认的对勾图标；false：不显示图标。<br/>ResourceStr：显示指定的图标。<br/>SymbolGlyphModifier：显示指定的HMSymbol图标。<br/>默认值：false<br>**起始版本：** 12 |

## selected

```TypeScript
selected(value: boolean)
```

设置菜单项是否选中。

从API version 10开始，该参数支持[$$](../../../ui/state-management/arkts-two-way-sync.md)双向绑定变量。

从API version 18开始，该参数支持[!!](../../../ui/state-management/arkts-new-binding.md#系统组件参数双向绑定)双向绑定变量。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-MenuItemAttribute-selected(value: boolean): MenuItemAttribute--><!--Device-MenuItemAttribute-selected(value: boolean): MenuItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 菜单项是否选中。<br/>true：菜单项被选中；false：菜单项不被选中。<br />默认值：false |

## subMenuBuilder

```TypeScript
subMenuBuilder(builder: CustomBuilder)
```

Create the submenu for custom menu item.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-MenuItemAttribute-subMenuBuilder(builder: CustomBuilder): MenuItemAttribute--><!--Device-MenuItemAttribute-subMenuBuilder(builder: CustomBuilder): MenuItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | [CustomBuilder](arkts-arkui-custombuilder-t.md) | 是 | Indicates the builder function for submenu. |

