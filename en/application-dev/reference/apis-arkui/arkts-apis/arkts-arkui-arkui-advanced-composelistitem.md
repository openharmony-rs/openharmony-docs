# @ohos.arkui.advanced.ComposeListItem

## Child Components

Not supported

## Events

The [universal events](../arkts-components/arkts-arkui-common-comp.md#common) are not supported.

## Modules to Import

```TypeScript
import { ComposeListItem, ContentItem, IconType, OperateButton, OperateCheck, OperateIcon, OperateItem } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [ContentItem](arkts-arkui-arkui-advanced-composelistitem-contentitem-c.md) | Defines elements for the left and center areas of the **ComposeListItem** component. |
| [OperateButton](arkts-arkui-arkui-advanced-composelistitem-operatebutton-c.md) | Defines the type of the button element on the right of the **ComposeListItem** component. |
| [OperateCheck](arkts-arkui-arkui-advanced-composelistitem-operatecheck-c.md) | Defines the type where the element on the right of the **ComposeListItem** component is **Switch**, **CheckBox**, or **Radio**. |
| [OperateIcon](arkts-arkui-arkui-advanced-composelistitem-operateicon-c.md) | Defines the type of the icon element on the right of the **ComposeListItem** component. |
| [OperateItem](arkts-arkui-arkui-advanced-composelistitem-operateitem-c.md) | Defines the type of the element on the right of the **ComposeListItem** component. |

### Structs

| Name | Description |
| --- | --- |
| [ComposeListItem](arkts-arkui-arkui-advanced-composelistitem-composelistitem-s.md) | The **ComposeListItem** component is a container that presents a series of items arranged in a column with the same width. You can use it to present data of the same type in a multiple and coherent row style, for example, images or text. |

### Enums

| Name | Description |
| --- | --- |
| [IconType](arkts-arkui-arkui-advanced-composelistitem-icontype-e.md) | Defines the icon type of the element on the left of the **ComposeListItem** component. |

## Examples

### Example 1: Configuring a Simple List Item

This example demonstrates how to create a simple list item that includes a primary text, a secondary text, a description, and a button with accompanying text on the right.



```TypeScript
// This example demonstrates the basic functionality of the component, including the use of elements on the left and right.
import { IconType, ComposeListItem } from '@kit.ArkUI';

@Entry
@Component
struct ComposeListItemExample {
  build() {
    Column() {
      List() {
        ListItem() {
          ComposeListItem({
            contentItem: ({
              iconStyle: IconType.NORMAL_ICON,
              icon: $r('sys.media.ohos_app_icon'),
              primaryText: 'Double-line list',
              secondaryText: 'Secondary text',
              description: 'Description'
            }),
            operateItem: ({
              icon: {
                value: $r('sys.media.ohos_app_icon'),
                action: () => {
                  this.getUIContext().getPromptAction().showToast({
                    message: 'icon'
                  });
                } },
              text: 'Text on the right'
            })
          })
        }
      }
    }
  }
}
```

### Example 2: Implementing Screen Reader Announcement for Right-Side Elements

This example shows how to use the accessibilityText, accessibilityDescription, and accessibilityLevel properties to customize the screen reader announcements for different right-side elements such as icons, buttons, and radio buttons in a list item. This functionality is supported since API version 18.



```TypeScript
import { IconType, ComposeListItem } from '@kit.ArkUI';
@Entry
@Component
struct ComposeListItemExample {
  build() {
    Column() {
      List() {
        ListItem() {
          ComposeListItem({
            contentItem: ({
              iconStyle: IconType.NORMAL_ICON,
              icon: $r('sys.media.ohos_app_icon'),
              primaryText: 'Double-line list',
              secondaryText: 'Secondary text',
              description: 'Description'
            }),
            operateItem: ({
              radio: {
                accessibilityText: 'Radio button', // Screen reader announcement for the radio button.
                accessibilityDescription: 'Unselected', // Description read by the screen reader when the radio button is unselected.
                accessibilityLevel: 'yes'  // Configure this element to be focused by accessibility screen readers.
              }
            })
          })
        }

        ListItem() {
          ComposeListItem({
            contentItem: ({
              iconStyle: IconType.NORMAL_ICON,
              icon: $r('sys.media.ohos_app_icon'),
              primaryText: 'Double-line list',
              secondaryText: 'Secondary text',
              description: 'Description'
            }),
            operateItem: ({
              button: {
                text: 'OK',
                accessibilityText: 'This is a button',
                accessibilityDescription: 'Double tap to activate',
                accessibilityLevel: 'no'  // Configure this button to be unrecognizable by screen reader services.
              }
            })
          })
        }

        ListItem() {
          ComposeListItem({
            contentItem: ({
              iconStyle: IconType.NORMAL_ICON,
              icon: $r('sys.media.ohos_app_icon'),
              primaryText: 'Double-line list',
              secondaryText: 'Secondary text',
              description: 'Description'
            }),
            operateItem: ({
              icon: {
                value: $r('sys.media.ohos_app_icon'),
                action: () => {
                  this.getUIContext().getPromptAction().showToast({
                    message: 'icon'
                  });
                },
                accessibilityText: 'This is an icon', // Screen reader announcement for the icon.
                accessibilityDescription: 'Double-tap to show the toast', // Description read by screen reader for the icon action.
                accessibilityLevel: 'yes'  // Configure this element to be focused by accessibility screen readers.
              }
            })
          })
        }
      }
    }
  }
}
```

### Example 3: Setting the Symbol Icon

This example demonstrates how to use symbolStyle in ContentItem, OperateItem, and OperateIcon to set custom symbol icons. This functionality is supported since API version 18.

```TypeScript
import { IconType, ComposeListItem, SymbolGlyphModifier } from '@kit.ArkUI';
@Entry
@Component
struct ComposeListItemExample {
  build() {
    Column() {
      List() {
        ListItem() {
          ComposeListItem({
            contentItem: ({
              iconStyle: IconType.NORMAL_ICON,
              icon: $r('sys.symbol.house'),
              primaryText: 'Double-line list',
              secondaryText: 'Secondary text',
              description: 'Description'
            }),
            operateItem: ({
              image: $r('sys.symbol.car'),
            })
          })
        }

        ListItem() {
          ComposeListItem({
            contentItem: ({
              iconStyle: IconType.NORMAL_ICON,
              icon: $r('sys.symbol.house'),
              symbolStyle: new SymbolGlyphModifier($r('sys.symbol.bell')).fontColor([Color.Red]),
              primaryText: 'Double-line list',
              secondaryText: 'Secondary text',
              description: 'Description'
            }),
            operateItem: ({
              image: $r('sys.symbol.car'),
              symbolStyle: new SymbolGlyphModifier($r('sys.symbol.heart')).fontColor([Color.Pink]),
            })
          })
        }

        ListItem() {
          ComposeListItem({
            contentItem: ({
              iconStyle: IconType.NORMAL_ICON,
              icon: $r('sys.symbol.house'),
              symbolStyle: new SymbolGlyphModifier($r('sys.symbol.bell')).fontColor([Color.Blue]),
              primaryText: 'Double-line list',
              secondaryText: 'Secondary text',
              description: 'Description'
            }),
            operateItem: ({
              icon: {
                value: $r('sys.symbol.car'),
                symbolStyle: new SymbolGlyphModifier($r('sys.symbol.heart')).fontColor([Color.Orange]),
                action: () => {
                  this.getUIContext().getPromptAction().showToast({
                    message: 'icon'
                  });
                }
              }
            })
          })
        }
      }
    }
  }
}
```
