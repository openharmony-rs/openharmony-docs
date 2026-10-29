# @ohos.arkui.advanced.ToolBarV2

## Modules to Import

```TypeScript
import { ToolBarV2ItemState, ToolBarV2SymbolGlyph, ToolBarV2SymbolGlyphOptions, ToolBarV2ItemText, ToolBarV2ItemTextOptions, ToolBarV2ItemIconType, ToolBarV2ItemImage, ToolBarV2ItemImageOptions, ToolBarV2, ToolBarV2Item, ToolBarV2ItemOptions, ToolBarV2Modifier, ToolBarV2ItemAction, AdvancedToolbarV2Item, AdvancedToolbarV2ItemOptions, AdvancedToolBarV2Modifier, BarBackgroundVisibility, ToolbarV2ItemGroupStyle, ToolbarV2ItemGroupStyleOptions, ToolbarV2ItemPlacement, ToolbarV2OverflowMenuStyle, ToolbarV2PaddingOptions, ToolbarV2StyleConfigs, ToolbarV2StyleOptions, ToolbarV2TitleConfigs, ToolbarV2TitleOptions, ToolbarV2TitleStyle, ToolbarV2TitleStyleOptions } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [AdvancedToolbarV2Item](arkts-arkui-arkui-advanced-toolbarv2-advancedtoolbarv2item-c.md) | Defines the advanced toolbar item. |
| [AdvancedToolBarV2Modifier](arkts-arkui-arkui-advanced-toolbarv2-advancedtoolbarv2modifier-c.md) | Advanced modifier for ToolBarV2. Merges layout attributes, style configs, and overflow menu style into a single modifier class. |
| [ToolBarV2Item](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2item-c.md) | Defines an item in the toolbar. |
| [ToolbarV2ItemGroupStyle](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemgroupstyle-c.md) | Defines the style configuration for toolbar item group. |
| [ToolBarV2ItemImage](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemimage-c.md) | Defines the icon content of a toolbar item. |
| [ToolBarV2ItemText](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemtext-c.md) | Defines the text of a toolbar item. |
| [ToolBarV2Modifier](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2modifier-c.md) | Provides methods for setting the toolbar height (**height**), background color (**backgroundColor**), left and right padding (**padding**, which takes effect only when the number of items is fewer than five), and whether to display the pressed state effect (**stateEffect**). |
| [ToolbarV2StyleConfigs](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2styleconfigs-c.md) | Defines the style configuration for the toolbar. |
| [ToolBarV2SymbolGlyph](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2symbolglyph-c.md) | Defines the icon symbol options. |
| [ToolbarV2TitleConfigs](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2titleconfigs-c.md) | Title configuration. When not provided, no title is rendered. |
| [ToolbarV2TitleStyle](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2titlestyle-c.md) | Title text style configuration. |

<!--Del-->
### Classes(System API)

| Name | Description |
| --- | --- |
| [ToolbarV2StyleConfigs](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2styleconfigs-c-sys.md) | Defines the style configuration for the toolbar. |
<!--DelEnd-->

### Structs

| Name | Description |
| --- | --- |
| [ToolBarV2](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2-s.md) | The toolbar is used to display action options for the current screen content. It is displayed at the bottom of the screen and is suitable for scenarios where quick action entries need to be provided to users. A maximum of five entries can be displayed at the bottom. Any excess entries are collapsed into a "More" item, which is displayed on the far right. It is suitable for scenarios where quick operations on the current page content are needed, helping users quickly access common functions and improving operation efficiency.<br> ToolbarV2 supports configuring advanced toolbar items via `AdvancedToolbarV2Item` (which extends `ToolBarV2Item`). A toolbar with configured advanced items is more flexible, allowing you to customize titles, overflow menus, item grouping, and more. This component is implemented based on [state management (V2)](../../../ui/state-management/arkts-state-management-overview.md#state-management-v2). Compared with [state management (V1)](../../../ui/state-management/arkts-state-management-overview.md#state-management-v1), state management (V2) enhances the deep observation and management capabilities of data objects, no longer limited to the component level. With state management (V2), developers can more flexibly control the data and state of the toolbar through this component, achieving more efficient UI refresh. <br> |

### Interfaces

| Name | Description |
| --- | --- |
| [AdvancedToolbarV2ItemOptions](arkts-arkui-arkui-advanced-toolbarv2-advancedtoolbarv2itemoptions-i.md) | Declare the options of AdvancedToolbarV2Item. |
| [ToolbarV2ItemGroupStyleOptions](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemgroupstyleoptions-i.md) | Defines the constructor options for ToolbarV2ItemGroupStyle. |
| [ToolBarV2ItemImageOptions](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemimageoptions-i.md) | Defines the options for initializing a **ToolBarV2ItemImage** object. |
| [ToolBarV2ItemOptions](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemoptions-i.md) | Defines the options for initializing a **ToolBarV2Item** object. |
| [ToolBarV2ItemTextOptions](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemtextoptions-i.md) | Defines the options for initializing a **ToolBarV2ItemText** object. |
| [ToolbarV2OverflowMenuStyle](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2overflowmenustyle-i.md) | Style configuration for the overflow menu popup. |
| [ToolbarV2PaddingOptions](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2paddingoptions-i.md) | Toolbar padding configuration along the main axis. |
| [ToolbarV2StyleOptions](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2styleoptions-i.md) | Defines the constructor options for ToolbarV2StyleConfigs. |
| [ToolBarV2SymbolGlyphOptions](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2symbolglyphoptions-i.md) | Defines the attributes of the symbol icon. |
| [ToolbarV2TitleOptions](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2titleoptions-i.md) | Defines the constructor options for ToolbarV2TitleConfigs. |
| [ToolbarV2TitleStyleOptions](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2titlestyleoptions-i.md) | Defines the constructor options for ToolbarV2TitleStyle. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [ToolbarV2StyleOptions](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2styleoptions-i-sys.md) | Defines the constructor options for ToolbarV2StyleConfigs. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [ToolBarV2ItemAction](arkts-arkui-toolbarv2itemaction-t.md) | Defines the callback for the click event of a toolbar item. |
| [ToolBarV2ItemIconType](arkts-arkui-toolbarv2itemicontype-t.md) | Defines the union type for the icon content of a toolbar item. |

### Enums

| Name | Description |
| --- | --- |
| [BarBackgroundVisibility](arkts-arkui-arkui-advanced-toolbarv2-barbackgroundvisibility-e.md) | Defines the toolbar background visibility. |
| [ToolbarV2ItemPlacement](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemplacement-e.md) | Defines the placement position of a toolbar item within the toolbar. |
| [ToolBarV2ItemState](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemstate-e.md) | Enumerates the states of the toolbar item. |

## Examples

### Example 1: Setting Toolbar Items to Different States

This example shows the various display effects when the state property of toolbar items is set to ENABLE, DISABLE, or ACTIVATE.



```TypeScript
import { ToolBarV2ItemImage, ToolBarV2ItemState, ToolBarV2ItemText, ToolBarV2Item, ToolBarV2 } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local toolbarList: ToolBarV2Item[] = []

  aboutToAppear() {
    this.toolbarList.push(new ToolBarV2Item({
      content: new ToolBarV2ItemText(
        {
          text: Long long long long long'
        }
      ),
      icon: new ToolBarV2ItemImage({
        src: $r('sys.media.ohos_ic_public_share')
      }),
      action: () => {
      },
    }))
    this.toolbarList.push(
      new ToolBarV2Item({
        content: new ToolBarV2ItemText(
          {
            text: 'Copy'
          }
        ),
        icon: new ToolBarV2ItemImage({
          src: $r('sys.media.ohos_ic_public_copy')
        }),
        action: () => {
        },
        state: ToolBarV2ItemState.DISABLE
      })
    )
    this.toolbarList.push(
      new ToolBarV2Item({
        content: new ToolBarV2ItemText(
          {
            text: 'Paste'
          }
        ),
        icon: new ToolBarV2ItemImage({
          src: $r('sys.media.ohos_ic_public_paste')
        }),
        action: () => {
        },
        state: ToolBarV2ItemState.ACTIVATE
      })
    )
    this.toolbarList.push(
      new ToolBarV2Item({
        content: new ToolBarV2ItemText(
          {
            text: 'All'
          }
        ),
        icon: new ToolBarV2ItemImage({
          src: $r('sys.media.ohos_ic_public_select_all')
        }),
        action: () => {
        },
      })
    )
    this.toolbarList.push(
      new ToolBarV2Item({
        content: new ToolBarV2ItemText(
          {
            text: 'Share'
          }
        ),
        icon: new ToolBarV2ItemImage({
          src: $r('sys.media.ohos_ic_public_share')
        }),
        action: () => {
        },
      })
    )
    this.toolbarList.push(
      new ToolBarV2Item({
        content: new ToolBarV2ItemText(
          {
            text: 'Share'
          }
        ),
        icon: new ToolBarV2ItemImage({
          src: $r('sys.media.ohos_ic_public_share')
        }),
        action: () => {
        },
      })
    )
  }

  build() {
    Row() {
      Stack() {
        Column() {
          ToolBarV2({
            activatedIndex: 2,
            toolBarList: this.toolbarList,
          })
        }
      }.align(Alignment.Bottom)
      .width('100%').height('100%')
    }
  }
}
```

### Example 2: Customizing the Toolbar Style

This example demonstrates how to customize the toolbar's height, background color, and pressed state effect using ToolBarV2Modifier.



```TypeScript
import {
  SymbolGlyphModifier,
  DividerModifier,
  LengthMetrics,
  ColorMetrics,
  ToolBarV2Item,
  ToolBarV2Modifier,
  ToolBarV2ItemText,
  ToolBarV2ItemImage,
  ToolBarV2,
  ToolBarV2ItemState,
  ToolBarV2SymbolGlyph
} from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local toolbarList: ToolBarV2Item[] = [];
  private toolBarModifier: ToolBarV2Modifier =
    new ToolBarV2Modifier().height(LengthMetrics.vp(52))
      .backgroundColor(ColorMetrics.resourceColor(Color.Transparent))
      .stateEffect(false);
  @Local dividerModifier: DividerModifier = new DividerModifier().height(0);

  aboutToAppear() {
    this.toolbarList.push(
      new ToolBarV2Item({
        content: new ToolBarV2ItemText({
          text: 'Long long long long long long long long text',
          activatedColor: ColorMetrics.resourceColor($r('sys.color.font_primary'))
        }),
        icon: new ToolBarV2SymbolGlyph({
          normal: new SymbolGlyphModifier($r('sys.symbol.ohos_star')).fontColor([Color.Green]),
          activated: new SymbolGlyphModifier($r('sys.symbol.ohos_star')).fontColor([Color.Red]),
        }),
        action: () => {
        },
        state: ToolBarV2ItemState.ACTIVATE,
      })
    )
    this.toolbarList.push(
      new ToolBarV2Item({
        content: new ToolBarV2ItemText({
          text: 'Copy',
          activatedColor: ColorMetrics.resourceColor('#ffec5d5d')
        }),
        icon: new ToolBarV2ItemImage({
          src: $r('sys.media.ohos_ic_public_copy'),
          color: ColorMetrics.resourceColor('#ff18cb53'),
          activatedColor: ColorMetrics.resourceColor('#ffec5d5d'),
        }),
        action: () => {
        },
        state: ToolBarV2ItemState.DISABLE,
      }))
    this.toolbarList.push(
      new ToolBarV2Item({
        content: new ToolBarV2ItemText({
          text: 'Paste',
          color: ColorMetrics.resourceColor('#ff18cb53')
        }),
        icon: new ToolBarV2ItemImage({
          src: $r('sys.media.ohos_ic_public_paste'),
        }),
        action: () => {
        },
        state: ToolBarV2ItemState.ACTIVATE,
      })
    )
    this.toolbarList.push(
      new ToolBarV2Item({
        content: new ToolBarV2ItemText({
          text: 'All',
        }),
        icon: new ToolBarV2ItemImage({
          src: $r('sys.media.ohos_ic_public_select_all'),
        }),
        action: () => {
        },
        state: ToolBarV2ItemState.ACTIVATE,
      }))
    this.toolbarList.push(
      new ToolBarV2Item({
        content: new ToolBarV2ItemText({
          text: 'Share',
        }),
        icon: new ToolBarV2ItemImage({
          src: $r('sys.media.ohos_ic_public_share'),
        }),
        action: () => {
        },
      }))
    this.toolbarList.push(
      new ToolBarV2Item({
        content: new ToolBarV2ItemText({
          text: 'Share',
        }),
        icon: new ToolBarV2ItemImage({
          src: $r('sys.media.ohos_ic_public_share'),
        }),
        action: () => {
        },
      })
    )
  }

  build() {
    Row() {
      Stack() {
        Column() {
          ToolBarV2({
            toolBarModifier: this.toolBarModifier,
            dividerModifier: this.dividerModifier,
            activatedIndex: 0,
            toolBarList: this.toolbarList,
          })
            .height(52)
        }
      }.align(Alignment.Bottom)
      .width('100%').height('100%')
    }
  }
}
```

### Example 3: Implementing Screen Reader Announcement

This example customizes the screen reader announcement text by setting the accessibilityText, accessibilityDescription, and accessibilityLevel properties of the toolbar item.

```TypeScript
import {
  DividerModifier,
  LengthMetrics,
  ColorMetrics,
  ToolBarV2Item,
  ToolBarV2Modifier,
  ToolBarV2ItemText,
  ToolBarV2ItemImage,
  ToolBarV2,
  ToolBarV2ItemState,
} from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local toolbarList: ToolBarV2Item[] = [];
  private toolBarModifier: ToolBarV2Modifier =
    new ToolBarV2Modifier().height(LengthMetrics.vp(52))
      .backgroundColor(ColorMetrics.resourceColor(Color.Transparent))
      .stateEffect(false);
  @Local dividerModifier: DividerModifier = new DividerModifier().height(0);

  aboutToAppear() {
    this.toolbarList.push(
      new ToolBarV2Item({
        content: new ToolBarV2ItemText({
          text: Long long long long long'
        }),
        icon: new ToolBarV2ItemImage({
          src: $r('sys.media.ohos_ic_public_share')
        }),
        action: () => {
        },
        accessibilityText: 'Clip', // Screen reader announcement text for the item.
        accessibilityDescription: 'Double-tap to clip', // Screen reader announcement description for the item.
        accessibilityLevel: 'yes'  // Configure this element to be focused by accessibility screen readers.
      })
    )
    this.toolbarList.push(
      new ToolBarV2Item({
        content: new ToolBarV2ItemText({
          text: 'Copy',
        }),
        icon: new ToolBarV2ItemImage({
          src: $r('sys.media.ohos_ic_public_copy'),
        }),
        action: () => {
        },
        state: ToolBarV2ItemState.DISABLE,
        accessibilityLevel: 'no'  // Configure this element not to be focused by accessibility screen readers.
      }))
    this.toolbarList.push(
      new ToolBarV2Item({
        content: new ToolBarV2ItemText({
          text: 'Paste',
        }),
        icon: new ToolBarV2ItemImage({
          src: $r('sys.media.ohos_ic_public_paste'),
        }),
        action: () => {
        },
        state: ToolBarV2ItemState.ACTIVATE,
      })
    )
    this.toolbarList.push(
      new ToolBarV2Item({
        content: new ToolBarV2ItemText({
          text: 'All',
        }),
        icon: new ToolBarV2ItemImage({
          src: $r('sys.media.ohos_ic_public_select_all'),
        }),
        action: () => {
        },
      }))
    this.toolbarList.push(
      new ToolBarV2Item({
        content: new ToolBarV2ItemText({
          text: 'Share',
        }),
        icon: new ToolBarV2ItemImage({
          src: $r('sys.media.ohos_ic_public_share'),
        }),
        action: () => {
        },
      }))
    this.toolbarList.push(
      new ToolBarV2Item({
        content: new ToolBarV2ItemText({
          text: 'Share',
        }),
        icon: new ToolBarV2ItemImage({
          src: $r('sys.media.ohos_ic_public_share'),
        }),
        action: () => {
        },
      })
    )
  }

  build() {
    Row() {
      Stack() {
        Column() {
          ToolBarV2({
            toolBarModifier: this.toolBarModifier,
            dividerModifier: this.dividerModifier,
            activatedIndex: 0,
            toolBarList: this.toolbarList,
          })
            .height(52)
        }
      }.align(Alignment.Bottom)
      .width('100%').height('100%')
    }
  }
}
```
