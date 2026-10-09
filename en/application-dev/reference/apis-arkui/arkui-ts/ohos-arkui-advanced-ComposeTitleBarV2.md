# ComposeTitleBarV2

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangrunsen-->
<!--Designer: @YanSanzo-->
<!--Tester: @ybhou1993-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=ca610c3b31eac2a84ffac21a107ce522b473feb1 translatedAt=2026-08-28T01:31:05.169Z pushedAt=2026-08-28T09:09:11.041Z -->

The **ComposeTitleBarV2** component is a title bar that supports setting a title, an avatar (optional), and a subtitle (optional). It can be used on primary pages, secondary pages, and higher-level UIs to configure the back button.

This component is implemented based on [state management V2](../../../ui/state-management/arkts-state-management-overview.md#state-management-v2). Compared with [state management V1](../../../ui/state-management/arkts-state-management-overview.md#state-management-v1), state management V2 delivers enhanced capabilities for deep observation and management of data objects, and is no longer limited to the component level. With state management V2, you can more flexibly control the data and state of the title bar through this component, achieving more efficient UI refresh.

> **NOTE**
>
> - This component can only be used in the stage model.
>
> - If [universal attributes](ts-component-general-attributes.md) and [universal events](ts-component-general-events.md) are set for **ComposeTitleBarV2**, the compilation toolchain will generate an additional node \_\_Common\_\_ and attach the universal attributes or universal events to \_\_Common\_\_, rather than directly applying them to **ComposeTitleBarV2** itself. This may cause the configured universal attributes or universal events to fail to take effect or behave unexpectedly. Therefore, it is not recommended to set universal attributes and universal events for **ComposeTitleBarV2**.

**Since:** 26.0.0

## Modules to Import

```ts
import { ComposeTitleBarV2, ComposeTitleBarV2MenuItem } from '@kit.ArkUI';
```

## Child Components

None

## ComposeTitleBarV2

ComposeTitleBarV2({item?: ComposeTitleBarV2MenuItem, title: ResourceStr, subtitle?: ResourceStr, menuItems?: Array&lt;ComposeTitleBarV2MenuItem&gt;})

The **ComposeTitleBarV2** component is a title bar that supports setting a title, an avatar (optional), a subtitle (optional), and menu items on the right (optional). It can be used on primary pages, secondary pages, and higher-level UIs to configure the back button and quick operations.

> **NOTE**
> 
> The input parameter cannot be **undefined**, that is, **ComposeTitleBarV2(undefined)** is not allowed.

**Since:** 26.0.0

**Decorator:** @ComponentV2

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

| Name | Type | Mandatory | Decorator Type | Description |
| -------- | -------- | -------- | -------- | -------- |
| item | [ComposeTitleBarV2MenuItem](#composetitlebarv2menuitem) | No | \@Param | Single menu item used for the avatar on the left side. When not set, no avatar is displayed on the left side. When used as the **item** attribute, this menu item is displayed only as an avatar, and the **isEnabled**, **action**, and **symbolStyle** attributes are not supported. |
| title | [ResourceStr](ts-types.md#resourcestr) | Yes | \@Param | Title. |
| subtitle | [ResourceStr](ts-types.md#resourcestr) | No | \@Param | Subtitle. When not set, no subtitle is displayed. |
| menuItems | Array&lt;[ComposeTitleBarV2MenuItem](#composetitlebarv2menuitem)&gt; | No | \@Param | List of menu items on the right side. When not set, no menu items are displayed on the right side of the title bar. |

## ComposeTitleBarV2MenuItem

Defines a menu item class used to define the avatar on the left or the menu items on the right of the title bar. When used as the **item** attribute, this menu item is displayed only as an avatar and, because it does not support interaction, the **isEnabled**, **action**, and **symbolStyle** attributes cannot be set. When used as the **menuItems** attribute, this menu item supports all attributes.

**Decorator:** @ObservedV2

### Attributes

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| value | [ResourceStr](ts-types.md#resourcestr) | No | No | Icon resource.<br/>**Decorator:** @Trace |
| symbolStyle | [SymbolGlyphModifier](ts-universal-attributes-attribute-symbolglyphmodifier.md#symbolglyphmodifier) | No | Yes | Symbol icon resource, which takes precedence over **value**. This attribute is not supported for the avatar on the left of the item. When it is not set, the **value** attribute is used as the icon resource.<br/>**Decorator:** @Trace |
| label | [ResourceStr](ts-types.md#resourcestr) | No | Yes | Icon label description. When it is not set, the icon label is not displayed.<br/>**Decorator:** @Trace |
| isEnabled | boolean | No | Yes | Whether to enable the item. The value **true** means enabled, and **false** means disabled. This attribute is not supported for the item attribute. Default value: **true**.<br/>**Decorator:** @Trace |
| action | [OnActionCallback](#onactioncallback) | No | Yes | Closure invoked when the item is triggered. The item parameter does not support triggering the action event. When it is not set, no action is triggered.<br/>**Decorator:** @Trace |
| accessibilityLevel | string | No | Yes | Accessibility level of the custom button on the right of the title bar. This attribute controls whether the current item can be recognized by accessibility services.<br/>Supported values:<br/>**"auto"**: The attribute value of the current component is converted to **"yes"** or **"no"** based on the situation.<br/>**"yes"**: The current component can be recognized by accessibility services.<br/>**"no"**: The current component cannot be recognized by accessibility services.<br/>**"no-hide-descendants"**: The current component and all its child components cannot be recognized by accessibility services.<br/>Default value: **"auto"**.<br/>**Decorator:** @Trace |
| accessibilityText | [ResourceStr](ts-types.md#resourcestr) | No | Yes | When a component does not contain a text attribute, it is not announced when selected by the screen reader. Developers can set accessibility text for components that do not contain text information, so that the text content is announced when the component is selected by the screen reader.<br/>**Decorator:** @Trace |
| accessibilityDescription | [ResourceStr](ts-types.md#resourcestr) | No | Yes | Accessibility description of the custom button. This attribute is not supported for the avatar on the left of the item. This description is used to explain the current component to users in detail. Developers should provide a relatively detailed text description for this attribute to help users understand the action to be performed and its possible consequences, especially when such consequences cannot be directly inferred from the component's attributes and accessibility text alone. If a component has both a text attribute and an accessibility description attribute, the system first announces the text attribute and then the content of the accessibility description attribute when the component is selected.<br/>**Decorator:** @Trace |

### constructor

constructor(params?: ComposeTitleBarV2MenuItemParams)

A constructor used to create a **ComposeTitleBarV2MenuItem** object.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| params | [ComposeTitleBarV2MenuItemParams](#composetitlebarv2menuitemparams) | No | Menu item parameter object. |

## ComposeTitleBarV2MenuItemParams

Defines the menu item parameters for creating a **ComposeTitleBarV2MenuItem** instance.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| value | [ResourceStr](ts-types.md#resourcestr) | No | No | Icon resource.|
| symbolStyle | [SymbolGlyphModifier](ts-universal-attributes-attribute-symbolglyphmodifier.md#symbolglyphmodifier) | No | Yes | Symbol icon resource, which has a higher priority than **value**. The avatar on the left of the item does not support this attribute. If this attribute is not set, the **value** attribute is used as the icon resource. |
| label | [ResourceStr](ts-types.md#resourcestr) | No | Yes | Icon label description. |
| isEnabled | boolean | No | Yes | Whether the menu item is enabled. The value **true** indicates that the menu item is enabled and can be interacted with normally, and **false** indicates that the menu item is disabled, grayed out, and cannot be interacted with. |
| action | [OnActionCallback](#onactioncallback) | No | Yes | Action closure invoked when the menu item is triggered. The **item** parameter does not support triggering the action event. If this attribute is not set, no action is triggered. |
| accessibilityLevel | string | No | Yes | Accessibility level of the custom button, which controls whether the current item can be recognized by the accessibility service.<br/>Supported values:<br/>**"auto"**: The attribute value of the current component is converted to **"yes"** or **"no"** based on the situation.<br/>**"yes"**: The current component can be recognized by the accessibility service.<br/>**"no"**: The current component cannot be recognized by the accessibility service.<br/>**"no-hide-descendants"**: The current component and all its child components cannot be recognized by the accessibility service.<br/>Default value: **"auto"** |
| accessibilityText | [ResourceStr](ts-types.md#resourcestr) | No | Yes | Accessibility text of the custom button on the right of the title bar. The avatar on the left of the item does not support this attribute. When the component does not contain a text attribute, the screen reader does not announce anything when this component is selected. After the accessibility text is set, the screen reader announces the text content when this component is selected. |
| accessibilityDescription | [ResourceStr](ts-types.md#resourcestr) | No | Yes | Accessibility description of the custom button on the right of the title bar. The avatar on the left of the item does not support this attribute. This description is used to explain to users in detail the operation of the current component and its possible consequences. When the component has both a text attribute and an accessibility description attribute, the system announces the text attribute first and then the accessibility description.<br/>Default value: **"Double-tap to activate."** |

## OnActionCallback

type OnActionCallback = () => void

Defines the callback triggered when a menu item is tapped.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

## Events

Setting the [universal events](ts-component-general-events.md) is not recommended.

## Examples

### Example 1: Setting a Simple Title Bar

Since API version 26.0.0, the **ComposeTitleBarV2** API can be used to implement a simple title bar. This example demonstrates the basic usage of **ComposeTitleBarV2**.

```ts
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

<!--Del--> <!--DelEnd-->

### Example 2: Setting a Right-side Custom Button Announcement

Since API version 26.0.0, you can customize the text announced by the screen reader by configuring the following attribute APIs for the right-side custom buttons of the title bar: **accessibilityText**, **accessibilityDescription**, and **accessibilityLevel**.

```ts
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

<!--Del--> <!--DelEnd-->

### Example 3: Setting a Symbol Icon

Since API version 26.0.0, a symbol icon can be configured by setting the **symbolStyle** attribute API of **ComposeTitleBarV2MenuItem**.

```ts
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

<!--Del--> <!--DelEnd-->