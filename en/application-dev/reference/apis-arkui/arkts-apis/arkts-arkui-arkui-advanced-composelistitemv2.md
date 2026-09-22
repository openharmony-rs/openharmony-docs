# @ohos.arkui.advanced.ComposeListItemV2

## Modules to Import

```TypeScript
import { ComposeListItemV2, ContentItemV2, ContentItemV2Options, IconTypeV2, OperateButtonV2, OperateButtonV2Options, OperateCheckV2, OperateCheckV2Options, OperateIconV2, OperateIconV2Options, OperateItemV2, OperateItemV2Options } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [ContentItemV2](arkts-arkui-arkui-advanced-composelistitemv2-contentitemv2-c.md) | Declare ContentItemV2 |
| [OperateButtonV2](arkts-arkui-arkui-advanced-composelistitemv2-operatebuttonv2-c.md) | Declare type OperateButtonV2 |
| [OperateCheckV2](arkts-arkui-arkui-advanced-composelistitemv2-operatecheckv2-c.md) | Declare type OperateCheckV2 |
| [OperateIconV2](arkts-arkui-arkui-advanced-composelistitemv2-operateiconv2-c.md) | Declare type OperateIconV2 |
| [OperateItemV2](arkts-arkui-arkui-advanced-composelistitemv2-operateitemv2-c.md) | Declare OperateItemV2 |

### Structs

| Name | Description |
| --- | --- |
| [ComposeListItemV2](arkts-arkui-arkui-advanced-composelistitemv2-composelistitemv2-s.md) | Declare ComposeListItemV2 |

### Interfaces

| Name | Description |
| --- | --- |
| [ContentItemV2Options](arkts-arkui-arkui-advanced-composelistitemv2-contentitemv2options-i.md) | Declare interface ContentItemV2Options |
| [OperateButtonV2Options](arkts-arkui-arkui-advanced-composelistitemv2-operatebuttonv2options-i.md) | Declare interface OperateButtonV2Options |
| [OperateCheckV2Options](arkts-arkui-arkui-advanced-composelistitemv2-operatecheckv2options-i.md) | Declare interface OperateCheckV2Options |
| [OperateIconV2Options](arkts-arkui-arkui-advanced-composelistitemv2-operateiconv2options-i.md) | Declare interface OperateIconV2Options |
| [OperateItemV2Options](arkts-arkui-arkui-advanced-composelistitemv2-operateitemv2options-i.md) | Declare interface OperateItemV2Options |

### Enums

| Name | Description |
| --- | --- |
| [IconTypeV2](arkts-arkui-arkui-advanced-composelistitemv2-icontypev2-e.md) | Declare enum IconTypeV2 |

### Types

| Name | Description |
| --- | --- |
| [OnActionCallback](arkts-arkui-onactioncallback-t.md) | Callback function when operate the icon. |
| [OnChangeCallback](arkts-arkui-onchangecallback-t.md) | Callback function when operate the checkbox/switch/radio. |

## Examples

### Example 1: Setting a Simple List Item

Since API version 26.0.0, a simple list item with a primary title, secondary title, description, right button, and text can be implemented through the ComposeListItemV2 component API.

```TypeScript
// This example demonstrates the basic functionality of this component, including left and right elements.
import { IconTypeV2, ComposeListItemV2, ContentItemV2, OperateItemV2, OperateIconV2 } from '@kit.ArkUI';

@Entry
@ComponentV2
struct ComposeListItemV2Example {
  build(): void {
    Column() {
      List() {
        ListItem() {
          ComposeListItemV2({
            contentItemV2: new ContentItemV2({
              iconStyle: IconTypeV2.NORMAL_ICON,
              icon: $r('sys.media.ohos_app_icon'),
              primaryText: 'Two-line list',
              secondaryText: 'Secondary text',
              description: 'Description text'
            }),
            operateItemV2: new OperateItemV2({
              icon: new OperateIconV2({
                value: $r('sys.media.ohos_app_icon'),
                action: () => {
                  this.getUIContext().getPromptAction().showToast({
                    message: 'icon'
                  });
                }
              }),
              text: 'Right text'
            })
          })
        }
      }
    }
  }
}
```

### Example 2: Setting Custom Announcements for Different Right Elements of the List Item

Since API version 26.0.0, custom screen reader announcement text can be implemented for the right icons, buttons, and radio buttons of a list item by setting the accessibilityText, accessibilityDescription, and accessibilityLevel attributes.

```TypeScript
import {
  IconTypeV2,
  ComposeListItemV2,
  ContentItemV2,
  OperateItemV2,
  OperateCheckV2,
  OperateButtonV2,
  OperateIconV2
} from '@kit.ArkUI';

@Entry
@ComponentV2
struct ComposeListItemV2Example {
  build(): void {
    Column() {
      List() {
        ListItem() {
          ComposeListItemV2({
            contentItemV2: new ContentItemV2({
              iconStyle: IconTypeV2.NORMAL_ICON,
              icon: $r('sys.media.ohos_app_icon'),
              primaryText: 'Two-line list',
              secondaryText: 'Secondary text',
              description: 'Description text'
            }),
            operateItemV2: new OperateItemV2({
              radio: new OperateCheckV2({
                accessibilityText: 'Radio button', // The screen reader announces 'radio button' for this radio button.
                accessibilityDescription: 'Unselected', // The screen reader announces this radio button as 'unselected'.
                accessibilityLevel: 'yes'  // This item can be focused by the accessibility screen reader.
              })
            })
          })
        }

        ListItem() {
          ComposeListItemV2({
            contentItemV2: new ContentItemV2({
              iconStyle: IconTypeV2.NORMAL_ICON,
              icon: $r('sys.media.ohos_app_icon'),
              primaryText: 'Two-line list',
              secondaryText: 'Secondary text',
              description: 'Description text'
            }),
            operateItemV2: new OperateItemV2({
              button: new OperateButtonV2({
                text: 'OK',
                accessibilityText: 'This is a button',
                accessibilityDescription: 'Double-tap to activate',
                accessibilityLevel: 'no'  // This button cannot be recognized by the screen reader service.
              })
            })
          })
        }

        ListItem() {
          ComposeListItemV2({
            contentItemV2: new ContentItemV2({
              iconStyle: IconTypeV2.NORMAL_ICON,
              icon: $r('sys.media.ohos_app_icon'),
              primaryText: 'Two-line list',
              secondaryText: 'Secondary text',
              description: 'Description text'
            }),
            operateItemV2: new OperateItemV2({
              icon: new OperateIconV2({
                value: $r('sys.media.ohos_app_icon'),
                action: () => {
                  this.getUIContext().getPromptAction().showToast({
                    message: 'icon'
                  });
                },
                accessibilityText: 'This is an icon', // The screen reader announcement text for this icon is 'This is an icon.'
                accessibilityDescription: 'Double tap to open more options', // The screen reader announcement description for this icon is 'Double tap to open more options.'
                accessibilityLevel: 'yes'  // This item can be focused by the accessibility screen reader.
              })
            })
          })
        }
      }
    }
  }
}
```

### Example 3: Setting Symbol Icons

Since API version 26.0.0, you can set symbol icon parameters through the attribute API symbolStyle of ContentItemV2, OperateItemV2, and OperateIconV2.

```TypeScript
import {
  IconTypeV2,
  ComposeListItemV2,
  ContentItemV2,
  OperateItemV2,
  OperateIconV2,
  SymbolGlyphModifier
} from '@kit.ArkUI';

@Entry
@ComponentV2
struct ComposeListItemV2Example {
  build(): void {
    Column() {
      List() {
        ListItem() {
          ComposeListItemV2({
            contentItemV2: new ContentItemV2({
              iconStyle: IconTypeV2.NORMAL_ICON,
              icon: $r('sys.symbol.house'),
              primaryText: 'Two-line list',
              secondaryText: 'Secondary text',
              description: 'Description text'
            }),
            operateItemV2: new OperateItemV2({
              image: $r('sys.symbol.car'),
            })
          })
        }

        ListItem() {
          ComposeListItemV2({
            contentItemV2: new ContentItemV2({
              iconStyle: IconTypeV2.NORMAL_ICON,
              icon: $r('sys.symbol.house'),
              symbolStyle: new SymbolGlyphModifier($r('sys.symbol.bell')).fontColor([Color.Red]),
              primaryText: 'Two-line list',
              secondaryText: 'Secondary text',
              description: 'Description text'
            }),
            operateItemV2: new OperateItemV2({
              image: $r('sys.symbol.car'),
              symbolStyle: new SymbolGlyphModifier($r('sys.symbol.heart')).fontColor([Color.Pink]),
            })
          })
        }

        ListItem() {
          ComposeListItemV2({
            contentItemV2: new ContentItemV2({
              iconStyle: IconTypeV2.NORMAL_ICON,
              icon: $r('sys.symbol.house'),
              symbolStyle: new SymbolGlyphModifier($r('sys.symbol.bell')).fontColor([Color.Blue]),
              primaryText: 'Two-line list',
              secondaryText: 'Secondary text',
              description: 'Description text.'
            }),
            operateItemV2: new OperateItemV2({
              icon: new OperateIconV2({
                value: $r('sys.symbol.car'),
                symbolStyle: new SymbolGlyphModifier($r('sys.symbol.heart')).fontColor([Color.Orange]),
                action: () => {
                  this.getUIContext().getPromptAction().showToast({
                    message: 'icon'
                  });
                }
              })
            })
          })
        }
      }
    }
  }
}
```
