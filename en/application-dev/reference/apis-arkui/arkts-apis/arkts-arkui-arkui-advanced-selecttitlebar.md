# @ohos.arkui.advanced.SelectTitleBar

## Modules to Import

```TypeScript
import { SelectTitleBar, SelectTitleBarMenuItem } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [SelectTitleBarMenuItem](arkts-arkui-arkui-advanced-selecttitlebar-selecttitlebarmenuitem-c.md) | Declaration of the menu item on the right side. |

### Structs

| Name | Description |
| --- | --- |
| [SelectTitleBar](arkts-arkui-arkui-advanced-selecttitlebar-selecttitlebar-s.md) | The **SelectTitleBar** component represents a drop-down menu title bar used for switching between pages of different levels (configured with the **Back** button). |

## Examples

### Example 1: Implementing a Simple Drop-down Menu Title Bar

This example demonstrates how to implement a simple drop-down menu title bar with various configurations, including one with a back arrow and one with a right-side menu item list.



```TypeScript
import { SelectTitleBar, Prompt, SelectTitleBarMenuItem } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  // Define an array of menu items for the right side of the title bar.
  private menuItems: Array<SelectTitleBarMenuItem> =
    [
      {
        // Resource for the menu icon.
        value: $r('sys.media.ohos_save_button_filled'),
        // Enable the image.
        isEnabled: true,
        // Action triggered when the menu item is clicked.
        action: () => Prompt.showToast({ message: 'show toast index 1' }),
      },
      {
        value: $r('sys.media.ohos_ic_public_copy'),
        isEnabled: true,
        action: () => Prompt.showToast({ message: 'show toast index 2' }),
      },
      {
        value: $r('sys.media.ohos_ic_public_edit'),
        isEnabled: true,
        action: () => Prompt.showToast({ message: 'show toast index 3' }),
      },
      {
        value: $r('sys.media.ohos_ic_public_remove'),
        isEnabled: true,
        action: () => Prompt.showToast({ message: 'show toast index 4' }),
      },
    ]

  build() {
    Row() {
      Column() {
        Divider().height(2).color(0xCCCCCC)
        SelectTitleBar({
          // Define items in the drop-down list.
          options: [
            { value: 'All photos' },
            { value: 'Local (device)' },
            { value: 'Local (memory card)'}
          ],
          // Initially select the first item in the drop-down list.
          selected: 0,
          // Function triggered when the item is selected.
          onSelected: (index) => Prompt.showToast({ message: 'page index ' + index }),
          // Hide the back arrow on the left.
          hidesBackButton: true,
        })
        Divider().height(2).color(0xCCCCCC)
        SelectTitleBar({
          options: [
            { value: 'All photos' },
            { value: 'Local (device)' },
            { value: 'Local (memory card)' },
          ],
          selected: 0,
          onSelected: (index) => Prompt.showToast({ message: 'page index ' + index }),
          hidesBackButton: false,
        })
        Divider().height(2).color(0xCCCCCC)
        SelectTitleBar({
          options: [
            { value: 'All photos' },
            { value: 'Local (device)' },
            { value: 'Local (memory card)' },
          ],
          selected: 1,
          onSelected: (index) => Prompt.showToast({ message: 'page index ' + index }),
          subtitle: 'example@example.com',
        })
        Divider().height(2).color(0xCCCCCC)
        SelectTitleBar({
          options: [
            { value: 'All photos' },
            { value: 'Local (device)' },
            { value: 'Local (memory card)' },
          ],
          selected: 1,
          onSelected: (index) => Prompt.showToast({ message: 'page index ' + index }),
          subtitle: 'example@example.com',
          menuItems: [{ isEnabled: true, value: $r('sys.media.ohos_save_button_filled'),
            action: () => Prompt.showToast({ message: 'show toast index 1' }),
          }],
        })
        Divider().height(2).color(0xCCCCCC)
        SelectTitleBar({
          options: [
            { value: 'All photos' },
            { value: 'Local (device)' },
            { value: 'Local (memory card)' },
          ],
          selected: 0,
          onSelected: (index) => Prompt.showToast({ message: 'page index ' + index }),
          subtitle: 'example@example.com',
          menuItems: this.menuItems,
          badgeValue: 99,
          hidesBackButton: true,
        })
        Divider().height(2).color(0xCCCCCC)
      }.width('100%')
    }.height('100%')
  }
}
```

### Example 2: Implementing Screen Reader Announcement for the Custom Button on the Right Side

This example customizes the screen reader announcement text by setting the accessibilityText, accessibilityDescription, and accessibilityLevel properties of the custom button on the right side of the title bar. This functionality is supported since API version 18.



```TypeScript
import { SelectTitleBar, Prompt, SelectTitleBarMenuItem } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  // Define an array of menu items for the right side of the title bar.
  private menuItems: Array<SelectTitleBarMenuItem> =
    [
      {
        // Resource for the menu icon.
        value: $r('sys.media.ohos_save_button_filled'),
        // Enable the image.
        isEnabled: true,
        // Action triggered when the menu item is clicked.
        action: () => Prompt.showToast({ message: 'show toast index 1' }),
        // The screen reader will prioritize this text over the label.
        accessibilityText: 'Save',
        // The screen reader can focus on this item.
        accessibilityLevel: 'yes',
        // The screen reader will ultimately announce this text.
        accessibilityDescription: 'Tap to save the current content',
      },
      {
        value: $r('sys.media.ohos_ic_public_copy'),
        isEnabled: true,
        action: () => Prompt.showToast({ message: 'show toast index 2' }),
        accessibilityText: 'Copy',
        // The screen reader will not focus on this item.
        accessibilityLevel: 'no',
        accessibilityDescription: 'Tap to copy the current content',
      },
      {
        value: $r('sys.media.ohos_ic_public_edit'),
        isEnabled: true,
        action: () => Prompt.showToast({ message: 'show toast index 3' }),
        accessibilityText: 'Edit',
        accessibilityLevel: 'yes',
        accessibilityDescription: 'Tap to edit the current content',
      },
      {
        value: $r('sys.media.ohos_ic_public_remove'),
        isEnabled: true,
        action: () => Prompt.showToast({ message: 'show toast index 4' }),
        accessibilityText: 'Remove',
        accessibilityLevel: 'yes',
        accessibilityDescription: 'Tap to remove the current content',
      }
    ]

  build() {
    Row() {
      Column() {
        Divider().height(2).color(0xCCCCCC)
        SelectTitleBar({
          // Define items in the drop-down list.
          options: [
            { value: 'All photos' },
            { value: 'Local (device)' },
            { value: 'Local (memory card)' },
          ],
          // Initially select the first item in the drop-down list.
          selected: 0,
          // Function triggered when the item is selected.
          onSelected: (index) => Prompt.showToast({ message: 'page index ' + index }),
          // Hide the back arrow on the left.
          hidesBackButton: true,
        })
        Divider().height(2).color(0xCCCCCC)
        SelectTitleBar({
          options: [
            { value: 'All photos' },
            { value: 'Local (device)' },
            { value: 'Local (memory card)' },
          ],
          selected: 0,
          onSelected: (index) => Prompt.showToast({ message: 'page index ' + index }),
          hidesBackButton: false,
        })
        Divider().height(2).color(0xCCCCCC)
        SelectTitleBar({
          options: [
            { value: 'All photos' },
            { value: 'Local (device)' },
            { value: 'Local (memory card)' },
          ],
          selected: 1,
          onSelected: (index) => Prompt.showToast({ message: 'page index ' + index }),
          subtitle: 'example@example.com',
        })
        Divider().height(2).color(0xCCCCCC)
        SelectTitleBar({
          options: [
            { value: 'All photos' },
            { value: 'Local (device)' },
            { value: 'Local (memory card)' },
          ],
          selected: 1,
          onSelected: (index) => Prompt.showToast({ message: 'page index ' + index }),
          subtitle: 'example@example.com',
          menuItems: [{ isEnabled: true, value: $r('sys.media.ohos_save_button_filled'),
            action: () => Prompt.showToast({ message: 'show toast index 1' }),
          }],
        })
        Divider().height(2).color(0xCCCCCC)
        SelectTitleBar({
          options: [
            { value: 'All photos' },
            { value: 'Local (device)' },
            { value: 'Local (memory card)' },
          ],
          selected: 0,
          onSelected: (index) => Prompt.showToast({ message: 'page index ' + index }),
          subtitle: 'example@example.com',
          menuItems: this.menuItems,
          badgeValue: 99,
          hidesBackButton: true,
        })
        Divider().height(2).color(0xCCCCCC)
      }.width('100%')
    }.height('100%')
  }
}
```

### Example 3: Setting the Symbol Icon

This example demonstrates how to use symbolStyle in SelectTitleBarMenuItem to set custom symbol icons. This functionality is supported since API version 18.

```TypeScript
import { SelectTitleBar, Prompt, SelectTitleBarMenuItem, SymbolGlyphModifier } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  // Define an array of menu items for the right side of the title bar.
  private menuItems: Array<SelectTitleBarMenuItem> =
    [
      {
        // Image resource. (When both value and symbolStyle are set, symbolStyle takes precedence.)
        value: $r('sys.media.ohos_save_button_filled'),
        // Symbol icon resource. (Takes precedence over value.)
        symbolStyle: new SymbolGlyphModifier($r('sys.symbol.save')),
        // Enable the image.
        isEnabled: true,
        // Action triggered when the menu item is clicked.
        action: () => Prompt.showToast({ message: 'show toast index 1' }),
        // The screen reader will prioritize this text over the label.
        accessibilityText: 'Save',
        // The screen reader can focus on this item.
        accessibilityLevel: 'yes',
        // The screen reader will ultimately announce this text.
        accessibilityDescription: 'Tap to save the current content',
      },
      {
        value: $r('sys.media.ohos_ic_public_copy'),
        symbolStyle: new SymbolGlyphModifier($r('sys.symbol.car')),
        isEnabled: true,
        action: () => Prompt.showToast({ message: 'show toast index 2' }),
        accessibilityText: 'Copy',
        // The screen reader will not focus on this item.
        accessibilityLevel: 'no',
        accessibilityDescription: 'Tap to copy the current content',
      },
      {
        value: $r('sys.media.ohos_ic_public_edit'),
        symbolStyle: new SymbolGlyphModifier($r('sys.symbol.ai_edit')),
        isEnabled: true,
        action: () => Prompt.showToast({ message: 'show toast index 3' }),
        accessibilityText: 'Edit',
        accessibilityLevel: 'yes',
        accessibilityDescription: 'Tap to edit the current content',
      },
      {
        value: $r('sys.media.ohos_ic_public_remove'),
        symbolStyle: new SymbolGlyphModifier($r('sys.symbol.remove_songlist')),
        isEnabled: true,
        action: () => Prompt.showToast({ message: 'show toast index 4' }),
        accessibilityText: 'Remove',
        accessibilityLevel: 'yes',
        accessibilityDescription: 'Tap to remove the current content',
      }
    ]

  build() {
    Row() {
      Column() {
        Divider().height(2).color(0xCCCCCC)
        SelectTitleBar({
          // Define items in the drop-down list.
          options: [
            { value: 'All photos' },
            { value: 'Local (device)' },
            { value: 'Local (memory card)' },
          ],
          // Initially select the first item in the drop-down list.
          selected: 0,
          // Function triggered when the item is selected.
          onSelected: (index) => Prompt.showToast({ message: 'page index ' + index }),
          // Hide the back arrow on the left.
          hidesBackButton: true,
        })
        Divider().height(2).color(0xCCCCCC)
        SelectTitleBar({
          options: [
            { value: 'All photos' },
            { value: 'Local (device)' },
            { value: 'Local (memory card)' },
          ],
          selected: 0,
          onSelected: (index) => Prompt.showToast({ message: 'page index ' + index }),
          hidesBackButton: false,
        })
        Divider().height(2).color(0xCCCCCC)
        SelectTitleBar({
          options: [
            { value: 'All photos' },
            { value: 'Local (device)' },
            { value: 'Local (memory card)' },
          ],
          selected: 1,
          onSelected: (index) => Prompt.showToast({ message: 'page index ' + index }),
          subtitle: 'example@example.com',
        })
        Divider().height(2).color(0xCCCCCC)
        SelectTitleBar({
          options: [
            { value: 'All photos' },
            { value: 'Local (device)' },
            { value: 'Local (memory card)' },
          ],
          selected: 1,
          onSelected: (index) => Prompt.showToast({ message: 'page index ' + index }),
          subtitle: 'example@example.com',
          menuItems: [{
            isEnabled: true, value: $r('sys.media.ohos_save_button_filled'),
            action: () => Prompt.showToast({ message: 'show toast index 1' }),
          }],
        })
        Divider().height(2).color(0xCCCCCC)
        SelectTitleBar({
          options: [
            { value: 'All photos' },
            { value: 'Local (device)' },
            { value: 'Local (memory card)' },
          ],
          selected: 0,
          onSelected: (index) => Prompt.showToast({ message: 'page index ' + index }),
          subtitle: 'example@example.com',
          menuItems: this.menuItems,
          badgeValue: 99,
          hidesBackButton: true,
        })
        Divider().height(2).color(0xCCCCCC)
      }.width('100%')
    }.height('100%')
  }
}
```
