# ToolBarV2

```TypeScript
export declare struct ToolBarV2
```

工具栏用于显示当前界面内容的操作选项。它显示在屏幕底部，适合需要为用户提供快速操作入口的场景。普通工具栏最多可以显示五个条目，超过的条目会被收起到“更多”项中，显示在最右侧。它适用于需要对当前页面内容进行快速操作的场景，帮助用户快速访问常用功能，提高操作效率。ToolBarV2支持通过AdvancedToolBarV2Item（继承自ToolBarV2Item）配置高级工具栏项。配置了高级项的工具栏更加灵活，可以自定义标题、溢出菜单、条目分组等。该组件基于[状态管理（V2）](../../../ui/state-management/arkts-state-management-overview.md#state-management-v2)实现。*与[状态管理（V1）](../../../ui/state-management/arkts-state-management-overview.md#state-management-v1)相比，状态管理（V2）增强了对数据对象的深度观察和管理能力，不再局限于组件级别。使用状态管理（V2），开发者可以通过这个组件更灵活地控制工具栏的数据和状态，实现更高效的UI刷新。<br>

> **说明：** 
> 
> - 该组件只能用于Stage模型。
> 
> - 如果[通用属性](../arkts-components/arkts-arkui-common-comp.md)且[通用事件](../arkts-components/arkts-arkui-common-comp.md)为设置给**ToolBarV2**，编译工具链设置会生成一个额外的节点__Common__，并将通用属性或通用事件附加到__Common__，而不是直接应用到**ToolBarV2**本身。这可能导致通用属性或开发者设定的普遍事件不会生效或表现出意料之外的行为。因此，不推荐为**ToolBarV2**设置通用属性和通用事件。
> 
> - 当系统在明暗模式切换时，工具栏的背景颜色不会自动跟随开关。

**Since:** 18

**Decorator:** @ComponentV2

<!--Device-unnamed-export declare struct ToolBarV2--><!--Device-unnamed-export declare struct ToolBarV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ToolBarV2ItemState, ToolBarV2SymbolGlyph, ToolBarV2SymbolGlyphOptions, ToolBarV2ItemText, ToolBarV2ItemTextOptions, ToolBarV2ItemIconType, ToolBarV2ItemImage, ToolBarV2ItemImageOptions, ToolBarV2, ToolBarV2Item, ToolBarV2ItemOptions, ToolBarV2Modifier, ToolBarV2ItemAction, AdvancedToolBarV2Item, AdvancedToolBarV2ItemOptions, AdvancedToolBarV2Modifier, BarBackgroundVisibility, ToolBarV2ItemGroupStyle, ToolBarV2ItemGroupStyleOptions, ToolBarV2ItemPlacement, ToolBarV2OverflowMenuStyle, ToolBarV2PaddingOptions, ToolBarV2StyleConfigs, ToolBarV2StyleOptions, ToolBarV2TitleConfigs, ToolBarV2TitleOptions, ToolBarV2TitleStyle, ToolBarV2TitleStyleOptions, ToolBarV2MaterialStyle } from '@kit.ArkUI';
```

## activatedIndex

```TypeScript
activatedIndex?: number
```

定义toolbarV2激活项的索引，默认值是-1。仅用于ToolBarV2Item组成的普通工具栏。

**Type:** number

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ToolBarV2-activatedIndex?: number--><!--Device-ToolBarV2-activatedIndex?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## advancedToolBarModifier

```TypeScript
advancedToolBarModifier?: AdvancedToolBarV2Modifier
```

定义高级工具栏V2修饰符。合并布局属性、样式配置、和溢出菜单样式到单个修改器中。

**Type:** [AdvancedToolBarV2Modifier](arkts-arkui-arkui-advanced-toolbarv2-advancedtoolbarv2modifier-c.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarV2-advancedToolBarModifier?: AdvancedToolBarV2Modifier--><!--Device-ToolBarV2-advancedToolBarModifier?: AdvancedToolBarV2Modifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## dividerModifier

```TypeScript
dividerModifier?: DividerModifier
```

定义toolbarV2分隔符修改器。仅用于ToolBarV2Item组成的普通工具栏。

**Type:** [DividerModifier](../../apis-default/arkts-apis/arkts-default-arkui-modifier.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ToolBarV2-dividerModifier?: DividerModifier--><!--Device-ToolBarV2-dividerModifier?: DividerModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## toolBarList

```TypeScript
toolBarList: ToolBarV2Item[]
```

定义toolbarV2项目列表。使用ToolBarV2Item可构建普通工具栏。AdvancedToolBarV2Item（继承自ToolBarV2Item）可用于更高级的布局场景，比如标题、溢出菜单以及项目分组。

**Type:** [ToolBarV2Item](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2item-c.md)[]

**Since:** 18

**Decorator:** @Require

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ToolBarV2-toolBarList: ToolBarV2Item[]--><!--Device-ToolBarV2-toolBarList: ToolBarV2Item[]-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## toolBarModifier

```TypeScript
toolBarModifier?: ToolBarV2Modifier
```

定义toolbarV2修改器，仅用于ToolBarV2Item组成的普通工具栏。

**Type:** [ToolBarV2Modifier](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2modifier-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ToolBarV2-toolBarModifier?: ToolBarV2Modifier--><!--Device-ToolBarV2-toolBarModifier?: ToolBarV2Modifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
