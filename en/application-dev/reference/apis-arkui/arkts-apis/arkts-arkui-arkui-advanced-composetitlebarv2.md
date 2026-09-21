# @ohos.arkui.advanced.ComposeTitleBarV2

## Modules to Import

```TypeScript
import { ComposeTitleBarV2, ComposeTitleBarV2MenuItem, ComposeTitleBarV2MenuItemParams } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [ComposeTitleBarV2MenuItem](arkts-arkui-arkui-advanced-composetitlebarv2-composetitlebarv2menuitem-c.md) | Declaration of the menu item on the right side. |

### Structs

| Name | Description |
| --- | --- |
| [ComposeTitleBarV2](arkts-arkui-arkui-advanced-composetitlebarv2-composetitlebarv2-s.md) | Declaration of the composable title bar. Composable title bar represents a common title bar that contains a title, subtitle (optional), and profile picture (optional). It can come with a Back button for switching between pages of different levels. |

### Interfaces

| Name | Description |
| --- | --- |
| [ComposeTitleBarV2MenuItemParams](arkts-arkui-arkui-advanced-composetitlebarv2-composetitlebarv2menuitemparams-i.md) | Options for creating a menu item instance. |

### Types

| Name | Description |
| --- | --- |
| [OnActionCallback](arkts-arkui-onactioncallback-t.md) | Declare the type of callback function when clicking on this menu item. |

## Examples

### Example 1: Setting a Simple Title Bar

Since API version 26.0.0, the ComposeTitleBarV2 API can be used to implement a simple title bar. This example demonstrates the basic usage of ComposeTitleBarV2.

```TypeScript
import { ComposeTitleBarV2, ComposeTitleBarV2MenuItem, Prompt } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  // Define the right-side menu item list.
  @Local menuItems: Array<ComposeTitleBarV2MenuItem> = [
    new ComposeTitleBarV2MenuItem({
      // Menu icon resource.
      value: $r('sys.media.ohos_save_button_filled'),
      // Enable the icon.
      isEnabled: true,
      // Trigger an event when the menu is tapped.
      action: () => Prompt.showToast({ message: 'icon 1' }),
    }),
    new ComposeTitleBarV2MenuItem({
      value: $r('sys.media.ohos_ic_public_copy'),
      isEnabled: true,
      action: () => Prompt.showToast({ message: 'icon 2' }),
    }),
    new ComposeTitleBarV2MenuItem({
      value: $r('sys.media.ohos_ic_public_edit'),
      isEnabled: true,
      action: () => Prompt.showToast({ message: 'icon 3' }),
    }),
    new ComposeTitleBarV2MenuItem({
      value: $r('sys.media.ohos_ic_public_remove'),
      isEnabled: true,
      action: () => Prompt.showToast({ message: 'icon 4' }),
    }),
  ]

  build(): void {
    Row() {
      Column() {
        // Divider.
        Divider().height(2).color(0xCCCCCC)
        ComposeTitleBarV2({
          title: 'Title.',
          subtitle: 'Subtitle.',
          menuItems: this.menuItems.slice(0, 1),
        })
        Divider().height(2).color(0xCCCCCC)
        ComposeTitleBarV2({
          title: 'Title.',
          subtitle: 'Subtitle',
          menuItems: this.menuItems.slice(0, 2),
        })
        Divider().height(2).color(0xCCCCCC)
        ComposeTitleBarV2({
          title: 'Title',
          subtitle: 'Subtitle',
          menuItems: this.menuItems,
        })
        Divider().height(2).color(0xCCCCCC)
        // Define the title bar with an avatar.
        ComposeTitleBarV2({
          menuItems: [
            new ComposeTitleBarV2MenuItem({
              isEnabled: true,
              value: $r('sys.media.ohos_save_button_filled'),
              action: () => Prompt.showToast({ message: 'icon' }),
            })
          ],
          title: 'Title',
          subtitle: 'Subtitle',
          item: new ComposeTitleBarV2MenuItem({
            isEnabled: true,
            value: $r('sys.media.ohos_app_icon')
          })
        })
        Divider().height(2).color(0xCCCCCC)
      }
    }.height('100%')
  }
}
```

### Example 2: Setting a Right-side Custom Button Announcement

Since API version 26.0.0, you can customize the text announced by the screen reader by configuring the following attribute APIs for the right-side custom buttons of the title bar: accessibilityText, accessibilityDescription, and accessibilityLevel.

```TypeScript
import { ComposeTitleBarV2, ComposeTitleBarV2MenuItem, Prompt } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  // Define the right-side menu item list.
  @Local menuItems: Array<ComposeTitleBarV2MenuItem> = [
    new ComposeTitleBarV2MenuItem({
      // Menu icon resource.
      value: $r('sys.media.ohos_save_button_filled'),
      // Enable the icon.
      isEnabled: true,
      // Trigger an event when the menu is tapped.
      action: () => Prompt.showToast({ message: 'icon 1' }),
      // Text announced by the screen reader, with a higher priority than the label.
      accessibilityText: 'Save',
      // Whether the screen reader can focus on this element.
      accessibilityLevel: 'yes',
      // Description text announced last by the screen reader.
      accessibilityDescription: 'Tap to save the icon.',
    }),
    new ComposeTitleBarV2MenuItem({
      value: $r('sys.media.ohos_ic_public_copy'),
      isEnabled: true,
      action: () => Prompt.showToast({ message: 'icon 2' }),
      accessibilityText: 'Copy',
      // Set to "no" to prevent the screen reader from focusing.
      accessibilityLevel: 'no',
      accessibilityDescription: 'Tap to copy the icon',
    }),
    new ComposeTitleBarV2MenuItem({
      value: $r('sys.media.ohos_ic_public_edit'),
      isEnabled: true,
      action: () => Prompt.showToast({ message: 'icon 3' }),
      accessibilityText: 'Edit',
      accessibilityLevel: 'yes',
      accessibilityDescription: 'Tap to edit the icon',
    }),
    new ComposeTitleBarV2MenuItem({
      value: $r('sys.media.ohos_ic_public_remove'),
      isEnabled: true,
      action: () => Prompt.showToast({ message: 'icon 4' }),
      accessibilityText: 'Remove',
      accessibilityLevel: 'yes',
      accessibilityDescription: 'Tap to remove the icon',
    }),
  ]

  build(): void {
    Row() {
      Column() {
        // Divider line.
        Divider().height(2).color(0xCCCCCC)
        ComposeTitleBarV2({
          title: 'Title',
          subtitle: 'Subtitle',
          menuItems: this.menuItems.slice(0, 1),
        })
        Divider().height(2).color(0xCCCCCC)
        ComposeTitleBarV2({
          title: 'Title',
          subtitle: 'Subtitle',
          menuItems: this.menuItems.slice(0, 2),
        })
        Divider().height(2).color(0xCCCCCC)
        ComposeTitleBarV2({
          title: 'Title',
          subtitle: 'Subtitle',
          menuItems: this.menuItems,
        })
        Divider().height(2).color(0xCCCCCC)
        // Define a title bar with an avatar.
        ComposeTitleBarV2({
          menuItems: [
            new ComposeTitleBarV2MenuItem({
              isEnabled: true,
              value: $r('sys.media.ohos_save_button_filled'),
              action: () => Prompt.showToast({ message: 'icon' }),
            })
          ],
          title: 'Title',
          subtitle: 'Subtitle',
          item: new ComposeTitleBarV2MenuItem({
            isEnabled: true,
            value: $r('sys.media.ohos_app_icon'),
          }),
        })
        Divider().height(2).color(0xCCCCCC)
      }
    }.height('100%')
  }
}
```

### Example 3: Setting a Symbol Icon

Since API version 26.0.0, a symbol icon can be configured by setting the symbolStyle attribute API of ComposeTitleBarV2MenuItem.

```TypeScript
import { ComposeTitleBarV2, ComposeTitleBarV2MenuItem, Prompt, SymbolGlyphModifier } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  // Define the right-side menu item list.
  @Local menuItems: Array<ComposeTitleBarV2MenuItem> = [
    new ComposeTitleBarV2MenuItem({
      // Menu image resource.
      value: $r('sys.symbol.house'),
      // Menu symbol icon, which takes priority over value.
      symbolStyle: new SymbolGlyphModifier($r('sys.symbol.bell')).fontColor([Color.Red]),
      // Enable the icon.
      isEnabled: true,
      // Trigger an event when the menu is tapped.
      action: () => Prompt.showToast({ message: 'symbol icon 1' }),
    }),
    new ComposeTitleBarV2MenuItem({
      value: $r('sys.symbol.house'),
      isEnabled: true,
      action: () => Prompt.showToast({ message: 'symbol icon 2' }),
    }),
    new ComposeTitleBarV2MenuItem({
      value: $r('sys.symbol.car'),
      symbolStyle: new SymbolGlyphModifier($r('sys.symbol.heart')).fontColor([Color.Pink]),
      isEnabled: true,
      action: () => Prompt.showToast({ message: 'symbol icon 3' }),
    }),
    new ComposeTitleBarV2MenuItem({
      value: $r('sys.symbol.car'),
      isEnabled: true,
      action: () => Prompt.showToast({ message: 'symbol icon 4' }),
    }),
  ]

  build(): void {
    Row() {
      Column() {
        // Divider.
        Divider().height(2).color(0xCCCCCC)
        ComposeTitleBarV2({
          title: 'Title.',
          subtitle: 'Subtitle.',
          menuItems: this.menuItems.slice(0, 1),
        })
        Divider().height(2).color(0xCCCCCC)
        ComposeTitleBarV2({
          title: 'Title',
          subtitle: 'Subtitle',
          menuItems: this.menuItems.slice(0, 2),
        })
        Divider().height(2).color(0xCCCCCC)
        ComposeTitleBarV2({
          title: 'Title',
          subtitle: 'Subtitle',
          menuItems: this.menuItems,
        })
        Divider().height(2).color(0xCCCCCC)
        // Define a title bar with an avatar.
        ComposeTitleBarV2({
          menuItems: [
            new ComposeTitleBarV2MenuItem({
              isEnabled: true,
              value: $r('sys.symbol.heart'),
              action: () => Prompt.showToast({ message: 'symbol icon 1' }),
            })
          ],
          title: 'Title',
          subtitle: 'Subtitle',
          item: new ComposeTitleBarV2MenuItem({
            isEnabled: true,
            value: $r('sys.media.ohos_app_icon'),
          }),
        })
        Divider().height(2).color(0xCCCCCC)
      }
    }.height('100%')
  }
}
```
