# EditableTitleBarV2

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangrunsen-->
<!--Designer: @YanSanzo-->
<!--Tester: @ybhou1993-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=ca610c3b31eac2a84ffac21a107ce522b473feb1 translatedAt=2026-08-28T01:34:11.285Z pushedAt=2026-08-28T09:09:19.439Z -->

The editable title bar is suitable for multi-select or content editing screens. Generally, a cancel icon is placed on the left and a save button on the right. It supports left icon configuration, title configuration, avatar display, menu item customization, save button control, and style customization, helping developers quickly build a unified editable title bar.

This component is implemented based on [state management V2](../../../ui/state-management/arkts-state-management-overview.md#state-management-v2). Compared with [state management V1](../../../ui/state-management/arkts-state-management-overview.md#state-management-v1), state management V2 delivers enhanced capabilities for deep observation and management of data objects, and is no longer limited to the component level. With state management V2, you can more flexibly control the data and state of the editable title bar through this component, achieving more efficient UI refresh.

> **NOTE**
>
> - This component can only be used in the stage model.
>
> - If [universal attributes](ts-component-general-attributes.md) and [universal events](ts-component-general-events.md) are set for **EditableTitleBarV2**, the compilation toolchain will generate an additional node \_\_Common\_\_ and mount the universal attributes or universal events on \_\_Common\_\_, rather than directly applying them to **EditableTitleBarV2** itself. This may cause the set universal attributes or universal events to not take effect or behave unexpectedly. Therefore, it is not recommended to set universal attributes and universal events on **EditableTitleBarV2**.

**Since:** 26.0.0

## Modules to Import

```ts
import { EditableTitleBarV2 } from '@kit.ArkUI';
```

## Child Components

None

## EditableTitleBarV2

EditableTitleBarV2({leftIcon?: EditableLeftIconV2, title: ResourceStr | EditableTitleV2, imageItem?: EditableTitleBarItemV2, menuItems?: Array&lt;EditableTitleBarMenuItemV2&gt;, saveButton?: EditableSaveButtonV2, options: EditableTitleBarStyleV2})

Defines an editable title bar, which is suitable for multi-select or content editing screens. Generally, a cancel icon is placed on the left and a save button on the right. It supports left icon configuration, title configuration, avatar display, menu item customization, save button control, and style customization, helping developers quickly build a unified editable title bar.

> **NOTE**
>
> - The input parameter object cannot be **undefined**, that is, **EditableTitleBarV2(undefined)** is not allowed.
>
> - If multiple operable areas of the title bar are set as the default focus, the first one in display order among those areas will be the default focus.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Decorator:** @ComponentV2

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

| Name | Type | Mandatory | Decorator Type | Description |
| -------- | -------- | -------- | -------- | -------- |
| leftIcon | [EditableLeftIconV2](#editablelefticonv2) | No | \@Param | Left icon configuration. Pass this parameter when a back or cancel icon needs to be displayed on the left side of the title bar. If not passed, the default value is used and no left icon is displayed.<br/>Default value: **undefined**. |
| title | [ResourceStr](ts-types.md#resourcestr) \| [EditableTitleV2](#editabletitlev2) | Yes | \@Param | Title content, which can be a string or an object. When a string is passed, only the main title is displayed. When an **EditableTitleV2** object is passed, both the main title and subtitle can be configured.<br/>Default value: **new EditableTitleV2()**, indicating that the title content is empty. |
| imageItem | [EditableTitleBarItemV2](#editabletitlebaritemv2) | No | \@Param | Menu item for the left avatar. Pass this parameter when an avatar needs to be displayed on the left side of the title bar. If not passed, the default value is used and no avatar is displayed.<br/>Default value: **undefined**.<br/>**Note:** The left avatar does not support accessibility attribute configuration. |
| menuItems | Array&lt;[EditableTitleBarMenuItemV2](#editabletitlebarmenuitemv2)&gt; | No | \@Param | List of menu items on the right. Pass this parameter when custom action buttons need to be displayed on the right side of the title bar. If not passed, the default value is used and no menu items are displayed on the right.<br/>**Note:** A maximum of 3 menu items can be configured. If a save button is also configured, a maximum of 2 menu items can be configured. Menu items exceeding the quantity limit are not displayed.<br/>Default value: **undefined**. |
| saveButton | [EditableSaveButtonV2](#editablesavebuttonv2) | No | \@Param | Save button configuration. Pass this parameter when you need to control the visibility of the save button on the right side of the title bar, set its default focus, or configure the callback triggered upon saving. If not passed, the default value is used and the save button is displayed. If **menuItems** is also configured, a maximum of 2 menu items can be configured.<br/>Default value: **undefined**, indicating that the save button is displayed. |
| options | [EditableTitleBarStyleV2](#editabletitlebarstylev2) | Yes | \@Param | Title bar style and layout configuration. Pass this parameter when you need to customize the title bar background, safe area, margins, and other styles. If not passed, the default value is used and the default title bar style is applied.<br/>Default value: **new EditableTitleBarStyleV2()**. |

## OnActionCallback

type OnActionCallback = () => void

Defines the callback for the tap event.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

## EditableLeftIconTypeV2

Enumerates the left icon types.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

| Name | Value | Description |
| -------- | -------- | -------- |
| Back | 0 | Back icon type. Tapping it performs the route back operation by default. |
| Cancel | 1 | Cancel icon type. Tapping it performs no default operation, and a custom callback is required. |

## EditableLeftIconV2Options

Defines the left icon configuration options.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| iconType | [EditableLeftIconTypeV2](#editablelefticontypev2) | No | Yes | Type of the left icon, which determines the style and default click behavior of the left icon. For the Back type, the route back operation is performed by default when clicked. For the Cancel type, no default operation is performed when clicked, and a custom callback is required.<br/>Default value: **EditableLeftIconTypeV2.Back**. |
| defaultFocus | boolean | No | Yes | Whether to obtain focus by default.<br/>**true**: Obtains focus.<br/>**false**: Does not obtain focus.<br/>Default value: **false**.<br/>If multiple operable areas of the title bar are set as the default focus, the first operable area in display order among those set as the default focus is the default focus. |
| onAction | [OnActionCallback](#onactioncallback) | No | Yes | Callback triggered when the left icon is tapped. If not set, the Back type performs route return by default, and the Cancel type has no operation. |

## EditableLeftIconV2

Defines the left icon configuration class, which is decorated with **@ObservedV2** and supports state observation.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Decorator:** @ObservedV2

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| iconType | [EditableLeftIconTypeV2](#editablelefticontypev2) | No | No | Type of the left icon, which determines the style and default tap behavior of the left icon. When the type is Back, route return is performed by default on tap. When the type is Cancel, there is no default operation on tap, and a custom callback must be configured through the **onAction** attribute.<br/>Default value: **EditableLeftIconTypeV2.Back**.<br/>**Decorator:** @Trace |
| defaultFocus | boolean | No | No | Whether to obtain focus by default.<br/>**true**: Obtains focus.<br/>**false**: Does not obtain focus.<br/>Default value: **false**. If multiple operable areas in the title bar are set as the default focus, the first one in display order among the operable areas set as the default focus is the default focus.<br/>**Decorator:** @Trace |
| onAction | [OnActionCallback](#onactioncallback) | No | Yes | Callback triggered when the left icon is tapped. If not set, the Back type performs route return by default, and the Cancel type has no operation.<br/>**Decorator:** @Trace |

### constructor

constructor(options?: EditableLeftIconV2Options)

A constructor used to create an **EditableLeftIconV2** instance.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ---- | ---- | ---- |
| options | [EditableLeftIconV2Options](#editablelefticonv2options) | No | Options for the left icon configuration.<br/>Default value: **undefined**. If this parameter is not passed, the default configuration is used. |

## EditableTitleV2Options

Defines the title configuration options.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| mainTitle | [ResourceStr](ts-types.md#resourcestr) | No | Yes | Primary title content.<br/>Default value: **''**, which means the title content is empty. |
| subTitle | [ResourceStr](ts-types.md#resourcestr) | No | Yes | Subtitle content. Pass this parameter when supplementary information needs to be displayed below the title.<br/>Default value: **undefined**, which means no subtitle is displayed. |

## EditableTitleV2

Defines the title configuration class, which is decorated with **@ObservedV2** and supports state observation.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Decorator:** @ObservedV2

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| mainTitle | [ResourceStr](ts-types.md#resourcestr) | No | No | Main title content.<br/>Default value: **''**, indicating that the title content is empty.<br/>**Decorator:** @Trace |
| subTitle | [ResourceStr](ts-types.md#resourcestr) | No | Yes | Subtitle content. Pass this parameter when supplementary information needs to be displayed below the title.<br/>Default value: **undefined**, indicating that the subtitle is not displayed.<br/>**Decorator:** @Trace |

### constructor

constructor(options?: EditableTitleV2Options)

A constructor used to create an **EditableTitleV2** instance.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ---- | ---- | ---- |
| options | [EditableTitleV2Options](#editabletitlev2options) | No | Title configuration options.<br/>Default value: undefined. If this parameter is not passed, the default value of each attribute is used. |

## EditableTitleBarMenuItemV2Options

Defines the menu item configuration options.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| value | [ResourceStr](ts-types.md#resourcestr) | No | Yes | Icon resource, which supports Symbol or Image. When both value and **symbolStyle** are set, **symbolStyle** takes effect and value does not.<br/>Default value: **''** |
| symbolStyle | [SymbolGlyphModifier](ts-universal-attributes-attribute-symbolglyphmodifier.md#symbolglyphmodifier) | No | Yes | Modifier for the Symbol icon style. Pass this parameter when a Symbol icon is used and its style needs to be customized. It takes precedence over value.<br/>Default value: **undefined**, which means no Symbol icon style modifier is set. |
| isEnabled | boolean | No | Yes | Whether to enable an item.<br/>Default value: **true**, meaning to enable.<br/>When **isEnabled** is **false**, the item is disabled. |
| label | [ResourceStr](ts-types.md#resourcestr) | No | Yes | Label text of the long-press dialog box.<br/>Default value: **undefined**, which means no label is displayed. |
| action | [OnActionCallback](#onactioncallback) | No | Yes | Callback invoked when the menu item is tapped.<br/>Default value: **undefined**, which means no response when tapped. |
| accessibilityLevel | string | No | Yes | Accessibility level, which controls whether the current item can be recognized by the accessibility service.<br/>Supported values:<br/>**"auto"**: The current component is converted to **"yes"** or **"no"** depending on the situation.<br/>**"yes"**: The current component can be recognized by the accessibility service.<br/>**"no"**: The current component cannot be recognized by the accessibility service.<br/>**"no-hide-descendants"**: The current component and all its child components cannot be recognized by the accessibility service.<br/>If a value outside the preceding range is passed in, it is processed as **"auto"**.<br/>Default value: **"auto"** |
| accessibilityText | [ResourceStr](ts-types.md#resourcestr) | No | Yes | Accessibility text for the screen reader. When the component does not contain a text attribute, setting this attribute enables the screen reader to announce the accessibility text when the component is selected.<br/>Default value: If **label** is set, the default value is the content of the label attribute of the current item; otherwise, the default value is **" "**. |
| accessibilityDescription | [ResourceStr](ts-types.md#resourcestr) | No | Yes | Accessibility description, which explains in detail the operation of the current component and its possible consequences to the user. If the component has both a text attribute and an accessibility description attribute, the system announces the text attribute first and then the accessibility description attribute when the component is selected.<br/>Default value: **"Single-tap with one finger to execute."**  |
| defaultFocus | boolean | No | Yes | Whether to obtain focus by default.<br/>**true**: The component obtains focus.<br/>**false**: The component does not obtain focus.<br/>Default value: **false**.<br/>When using the **defaultFocus** attribute, set the **isEnabled** attribute to **true** in advance; otherwise, the **defaultFocus** value is recognized as **false**. If multiple operable areas in the title bar are set as the default focus, the first one in display order among the operable areas set as the default focus is the default focus. |

## EditableTitleBarMenuItemV2

Defines the menu item configuration class, which is decorated with **@ObservedV2** and supports state observation.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Decorator:** @ObservedV2

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| value | [ResourceStr](ts-types.md#resourcestr) | No | No | Icon resource, which supports a Symbol type icon or an Image type icon. When both **value** and **symbolStyle** are set, **symbolStyle** takes effect and **value** does not.<br/>Default value: **''**.<br/>**Decorator:** @Trace |
| symbolStyle | [SymbolGlyphModifier](ts-universal-attributes-attribute-symbolglyphmodifier.md#symbolglyphmodifier) | No | Yes | Symbol icon style modifier. When both **value** and **symbolStyle** are set, **symbolStyle** takes effect and **value** does not.<br/>Default value: **undefined**, meaning that no Symbol icon style modifier is set.<br/>**Decorator:** @Trace |
| isEnabled | boolean | No | No | Whether to enable an item.<br/>Default value: **true**, meaning to enable.<br/>When **isEnabled** is **false**, the item is disabled.<br/>**Decorator:** @Trace |
| label | [ResourceStr](ts-types.md#resourcestr) | No | Yes | Label text of the long-press dialog box.<br/>Default value: **undefined**, meaning that no label is displayed.<br/>**Decorator:** @Trace |
| action | [OnActionCallback](#onactioncallback) | No | Yes | Callback invoked when the menu item is tapped. If it is not set, no response is triggered on tap.<br/>Default value: **undefined**.<br/>**Decorator:** @Trace |
| accessibilityLevel | string | No | No | Accessibility level, which controls whether the current item can be recognized by the accessibility service.<br/>Supported values:<br/>**"auto"**: The attribute value of the current component is converted to **"yes"** or **"no"** as appropriate.<br/>**"yes"**: The current component can be recognized by the accessibility service.<br/>**"no"**: The current component cannot be recognized by the accessibility service.<br/>**"no-hide-descendants"**: The current component and all its child components cannot be recognized by the accessibility service.<br/>If a value outside the preceding range is passed in, it is processed as **"auto"**.<br/>Default value: **"auto"**.<br/>**Decorator:** @Trace |
| accessibilityText | [ResourceStr](ts-types.md#resourcestr) | No | Yes | Accessibility text for the screen reader. When the component does not contain a text attribute, setting this attribute enables the screen reader to announce the accessibility text when the component is selected.<br/>Default value: the content of the **label** attribute of the current item if **label** is set; otherwise, **" "**.<br/>**Decorator:** @Trace |
| accessibilityDescription | [ResourceStr](ts-types.md#resourcestr) | No | Yes | Accessibility description, which explains in detail the operation of the current component and its possible consequences to users. If the component has both a text attribute and an accessibility description attribute, the system announces the text attribute first and then the accessibility description attribute when the component is selected.<br/>Default value: **"Single-finger double-tap to execute"**.<br/>**Decorator:** @Trace |
| defaultFocus | boolean | No | No | Whether to set the item as the default focus.<br/>**true**: The item obtains focus.<br/>**false**: The item does not obtain focus.<br/>Default value: **false**.<br/>If multiple operable areas in the title bar are set as the default focus, the first operable area in display order among those set as the default focus is used as the default focus.<br/>When using the **defaultFocus** attribute, set the **isEnabled** attribute to **true** in advance; otherwise, the **defaultFocus** value is recognized as **false**.<br/>**Decorator:** @Trace |

### constructor

constructor(options?: EditableTitleBarMenuItemV2Options)

A constructor used to create an **EditableTitleBarMenuItemV2** instance.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| options | [EditableTitleBarMenuItemV2Options](#editabletitlebarmenuitemv2options) | No | Menu item configuration options.<br/>Default value: **undefined**, which means that when this parameter is not passed, each attribute uses its default value. |

## EditableTitleBarItemV2

type EditableTitleBarItemV2 = EditableTitleBarMenuItemV2

Defines the type alias of the left avatar item. The left avatar does not support configuring accessibility attributes.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

| Type | Description |
| -------- | -------- |
| [EditableTitleBarMenuItemV2](#editabletitlebarmenuitemv2) | Single menu item type of the left avatar. Accessibility attributes are not supported. |

## EditableTitleBarItemV2Options

type EditableTitleBarItemV2Options = EditableTitleBarMenuItemV2Options

Defines the type alias of the left avatar item configuration options.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

| Type | Description |
| -------- | -------- |
| [EditableTitleBarMenuItemV2Options](#editabletitlebarmenuitemv2options) | Configuration option type for a single menu item of the left avatar. Accessibility attributes are not supported. |

## EditableSaveButtonV2Options

Defines the save button configuration options.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| isRequired | boolean | No | Yes | Whether to display the save button.<br/>**true**: yes.<br/>**false**: no.<br/>Default value: **true**. |
| defaultFocus | boolean | No | Yes | Whether to obtain focus by default.<br/>**true**: yes.<br/>**false**: no.<br/>Default value: **false**. |
| onAction | [OnActionCallback](#onactioncallback) | No | Yes | Callback triggered when the save button is tapped. If not set, no response occurs when the button is tapped. |

## EditableSaveButtonV2

Defines the save button configuration class, which is decorated by **@ObservedV2** and supports state observation.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Decorator:** @ObservedV2

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| isRequired | boolean | No | No | Whether to display the save button.<br/>**true**: yes.<br/>**false**: no.<br/>Default value: **true**.<br/>**Decorator:** @Trace |
| defaultFocus | boolean | No | No | Whether to obtain focus by default.<br/>**true**: yes.<br/>**false**: no.<br/>Default value: **false**.<br/>If multiple operable areas in the title bar are set as the default focus, the first operable area in display order among those set as the default focus is the default focus.<br/>**Decorator:** @Trace |
| onAction | [OnActionCallback](#onactioncallback) | No | Yes | Callback triggered when the save button is tapped. If not set, tapping the button does not respond.<br/>**Decorator:** @Trace |

### constructor

constructor(options?: EditableSaveButtonV2Options)

A constructor used to create an **EditableSaveButtonV2** instance.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| options | [EditableSaveButtonV2Options](#editablesavebuttonv2options) | No | Save button configuration options.<br/>Default value: **undefined**, which means the default configuration is used when this parameter is not passed. |

## EditableTitleBarStyleV2Options

Defines the title bar style configuration options.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| backgroundColor | [ResourceColor](ts-types.md#resourcecolor) | No | Yes | Background color of the title bar.<br/>Default value: **'#00000000'**, indicating a transparent background.  |
| backgroundBlurStyle | [BlurStyle](ts-universal-attributes-background.md#blurstyle9) | No | Yes | Background blur style of the title bar. Pass this parameter when a background blur effect is needed for the title bar. If it is not passed, no blur effect is applied.<br/>Default value: **BlurStyle.NONE**, indicating no blur effect. |
| safeAreaTypes | Array&lt;[SafeAreaType](ts-universal-attributes-expand-safe-area.md#safeareatype)&gt; | No | Yes | Types of the expanded safe area. Pass this parameter when the title bar needs to be extended to a specific safe area. If it is not passed, the title bar is extended only to the system safe area.<br/>Default value: **[SafeAreaType.SYSTEM]** |
| safeAreaEdges | Array&lt;[SafeAreaEdge](ts-universal-attributes-expand-safe-area.md#safeareaedge)&gt; | No | Yes | Edges of the expanded safe area. Pass this parameter when the safe area expansion direction needs to be customized. If it is not passed, the safe area is expanded upward by default.<br/>Default value: **[SafeAreaEdge.TOP]** |
| contentMargin | [LocalizedMargin](ts-types.md#localizedmargin12) | No | Yes | Outer margin of the title bar. Negative values are not supported (they do not take effect).<br/>Default value:<br/>**{<br/>start: LengthMetrics.resource(\$r('sys.float.margin_left')),<br/>end: LengthMetrics.resource(\$r('sys.float.margin_right'))<br/>}**. |

## EditableTitleBarStyleV2

Defines the title bar style configuration class, which is decorated with **@ObservedV2** and supports state observation.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Decorator:** @ObservedV2

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| backgroundColor | [ResourceColor](ts-types.md#resourcecolor) | No | Yes | Background color of the title bar.<br/>Default value: **'#00000000'**, indicating a transparent background.<br/>**Decorator:** @Trace  |
| backgroundBlurStyle | [BlurStyle](ts-universal-attributes-background.md#blurstyle9) | No | Yes | Background blur style of the title bar.<br/>Default value: **BlurStyle.NONE**, indicating no blur effect.<br/>**Decorator:** @Trace  |
| safeAreaTypes | Array&lt;[SafeAreaType](ts-universal-attributes-expand-safe-area.md#safeareatype)&gt; | No | Yes | Types of the expanded safe area.<br/>Default value: **[SafeAreaType.SYSTEM]**.<br/>**Decorator:** @Trace  |
| safeAreaEdges | Array&lt;[SafeAreaEdge](ts-universal-attributes-expand-safe-area.md#safeareaedge)&gt; | No | Yes | Edges of the expanded safe area.<br/>Default value: **[SafeAreaEdge.TOP]**.<br/>**Decorator:** @Trace  |
| contentMargin | [LocalizedMargin](ts-types.md#localizedmargin12) | No | Yes | Outer margin of the title bar. Negative values are not supported. If a negative value is set, it does not take effect.<br/>Default value:<br/>**{<br/>start: LengthMetrics.resource(\$r('sys.float.margin_left')),<br/>end: LengthMetrics.resource(\$r('sys.float.margin_right'))<br/>}**.<br/>**Decorator:** @Trace |

### constructor

constructor(options?: EditableTitleBarStyleV2Options)

A constructor used to create an **EditableTitleBarStyleV2** instance.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| options | [EditableTitleBarStyleV2Options](#editabletitlebarstylev2options) | No | Options for the title bar style.<br/>Default value: **undefined**, which means the default configuration is used when this parameter is not passed. |

## Events

It is not recommended to set [universal events](ts-component-general-events.md), as they may not take effect or may not work as expected.

## Examples

### Example 1: Custom Title Bar of the Right-Side Icon

This example uses the **EditableTitleBarV2** API to display the left icon, main title, and custom right icon area of an editable title bar.

**EditableTitleBarV2** is supported since API version 26.0.0.

```ts
import { Prompt } from '@kit.ArkUI';
import {
  EditableLeftIconTypeV2,
  EditableTitleBarV2,
  EditableLeftIconV2,
  EditableTitleBarMenuItemV2,
  EditableSaveButtonV2,
  EditableTitleBarStyleV2
} from '@kit.ArkUI';

@Entry
@ComponentV2
struct EditableTitleBarV2Demo01 {
  build(): void {
    Row() {
      Column() {
        Divider().height(2).color(0xCCCCCC)
        // Left: cancel button. Right: save button.
        EditableTitleBarV2({
          leftIcon: new EditableLeftIconV2({
            iconType: EditableLeftIconTypeV2.Cancel,
            onAction: () => {
              Prompt.showToast({ message: 'on cancel' });
            }
          }),
          title: 'Edit page',
          menuItems: [],
          saveButton: new EditableSaveButtonV2({
            onAction: () => {
              Prompt.showToast({ message: 'on save' });
            }
          }),
          options: new EditableTitleBarStyleV2({
            safeAreaTypes: []
          })
        })
        Divider().height(2).color(0xCCCCCC)
        // Left: back button. Right: custom cancel button (disabled) and save button.
        EditableTitleBarV2({
          leftIcon: new EditableLeftIconV2({
            iconType: EditableLeftIconTypeV2.Back
          }),
          title: 'Edit page',
          menuItems: [
            new EditableTitleBarMenuItemV2({
              value: $r('sys.media.ohos_ic_public_cancel'),
              isEnabled: false,
              action: () => {
                Prompt.showToast({ message: 'show toast index 2' });
              }
            })
          ],
          saveButton: new EditableSaveButtonV2({
            onAction: () => {
              Prompt.showToast({ message: 'on save' });
            }
          })
        })
        Divider().height(2).color(0xCCCCCC)
      }.width('100%')
    }.height('100%')
  }
}
```

<!--Del--> <!--DelEnd-->

### Example 2: Title Bar with Avatar and Blur Background

This example uses the EditableTitleBarV2 interfaces such as leftIcon, title, and saveButton to implement an editable title bar with blur background, avatar display, hidden right-side save button and custom title bar margins.

**EditableTitleBarV2** is supported since API version 26.0.0.

```ts
import { LengthMetrics, Prompt } from '@kit.ArkUI';
import {
  EditableLeftIconTypeV2,
  EditableTitleBarV2,
  EditableLeftIconV2,
  EditableTitleV2,
  EditableTitleBarStyleV2,
  EditableTitleBarMenuItemV2,
  EditableSaveButtonV2
} from '@kit.ArkUI';

@Entry
@Component
struct EditableTitleBarV2Demo02 {
  @State titleBarMargin: LocalizedMargin = {
    start: LengthMetrics.vp(35),
    end: LengthMetrics.vp(35),
  };

  build(): void {
    Row() {
      Column() {
        EditableTitleBarV2({
          leftIcon: new EditableLeftIconV2({
            iconType: EditableLeftIconTypeV2.Cancel,
          }),
          title: new EditableTitleV2({
            mainTitle: 'Title',
            subTitle: 'Subtitle',
          }),
          // Set the background blur effect.
          options: new EditableTitleBarStyleV2({
            backgroundBlurStyle: BlurStyle.COMPONENT_THICK,
          }),
          saveButton: new EditableSaveButtonV2({
            onAction: () => {
              Prompt.showToast({ message: "on save" });
            },
          })
        })
        Divider().height(2).color(0xCCCCCC);
        EditableTitleBarV2({
          leftIcon: new EditableLeftIconV2({
            iconType: EditableLeftIconTypeV2.Cancel,
          }),
          title: new EditableTitleV2({
            mainTitle: 'Title',
            subTitle: 'Subtitle',
          }),
          // Disable the save button on the right.
          saveButton: new EditableSaveButtonV2({
            isRequired: false
          })
        })
        Divider().height(2).color(0xCCCCCC);
        EditableTitleBarV2({
          leftIcon: new EditableLeftIconV2({
            iconType: EditableLeftIconTypeV2.Back,
            onAction: () => {
              this.getUIContext()?.getRouter()?.back();
            },
          }),
          title: new EditableTitleV2({
            mainTitle: 'Title',
            subTitle: 'Subtitle',
          }),
          // Disable the save button on the right.
          saveButton: new EditableSaveButtonV2({
            isRequired: false
          })
        })
        Divider().height(2).color(0xCCCCCC);
        EditableTitleBarV2({
          leftIcon: new EditableLeftIconV2({
            iconType: EditableLeftIconTypeV2.Back,
            // Action triggered when the Back icon on the left is tapped.
            onAction: () => {
              this.getUIContext()?.getRouter()?.back();
            },
          }),
          title: new EditableTitleV2({
            mainTitle: 'Title',
            subTitle: 'Subtitle',
          }),
          menuItems: [
            new EditableTitleBarMenuItemV2({
              value: $r('sys.media.ohos_ic_public_remove'),
              isEnabled: true,
              action: () => {
                Prompt.showToast({ message: "show toast index 1" });
              }
            })
          ],
          // Disable the save button on the right.
          saveButton: new EditableSaveButtonV2({
            isRequired: false
          })
        })
        Divider().height(2).color(0xCCCCCC);
        EditableTitleBarV2({
          leftIcon: new EditableLeftIconV2({
            iconType: EditableLeftIconTypeV2.Back,
            onAction: () => {
              this.getUIContext()?.getRouter()?.back();
            },
          }),
          title: new EditableTitleV2({
            mainTitle: 'Title',
            subTitle: 'Subtitle',
          }),
          // Set the clickable avatar.
          imageItem: new EditableTitleBarMenuItemV2({
            value: $r('sys.media.ohos_ic_normal_white_grid_image'),
            isEnabled: true,
            action: () => {
              Prompt.showToast({ message: "show toast index 2" });
            }
          }),
          // Configuration of the right-side icons.
          menuItems: [
            new EditableTitleBarMenuItemV2({
              value: $r('sys.media.ohos_ic_public_remove'),
              isEnabled: true,
              action: () => {
                Prompt.showToast({ message: "show toast index 3" });
              }
            })
          ],
          options: new EditableTitleBarStyleV2({
            // Set the margin of the title bar.
            contentMargin: this.titleBarMargin,
          })
        })
      }
    }
  }
}
```

<!--Del--> <!--DelEnd-->

### Example 3: Custom Button Announcement on the Right

This example uses the right-side custom button attributes such as **accessibilityText** and **accessibilityDescription** of the **EditableTitleBarV2** API to customize the screen reader announcement text of the editable title bar.

The **EditableTitleBarV2** API is supported since API version 26.0.0.

```ts
import { Prompt } from '@kit.ArkUI';
import {
  EditableLeftIconTypeV2,
  EditableTitleBarV2,
  EditableLeftIconV2,
  EditableTitleV2,
  EditableTitleBarMenuItemV2,
  EditableSaveButtonV2
} from '@kit.ArkUI';

@Entry
@Component
struct EditableTitleBarV2Demo03 {
  build(): void {
    Row() {
      Column() {
        Divider().height(2).color(0xCCCCCC)
        EditableTitleBarV2({
          leftIcon: new EditableLeftIconV2({
            iconType: EditableLeftIconTypeV2.Cancel,
            onAction: () => {
              Prompt.showToast({ message: 'on cancel' });
            },
          }),
          title: 'Edit page',
          menuItems: [],
          saveButton: new EditableSaveButtonV2({
            onAction: () => {
              Prompt.showToast({ message: 'on save' });
            }
          })
        })
        Divider().height(2).color(0xCCCCCC)
        EditableTitleBarV2({
          // Avatar and custom button are unavailable.
          leftIcon: new EditableLeftIconV2({
            iconType: EditableLeftIconTypeV2.Back,
            onAction: () => {
              this.getUIContext()?.getRouter()?.back();
            },
          }),
          title: new EditableTitleV2({
            mainTitle: 'Title',
            subTitle: 'Subtitle',
          }),
          imageItem: new EditableTitleBarMenuItemV2({
            value: $r('sys.media.ohos_ic_normal_white_grid_image'),
            isEnabled: true,
            action: () => {
              Prompt.showToast({ message: "show toast index 1" });
            }
          }),
          menuItems: [
            new EditableTitleBarMenuItemV2({
              value: $r('sys.media.ohos_ic_public_remove'),
              label: 'Cancel',
              isEnabled: false,
              accessibilityText: 'Delete',
              accessibilityDescription: 'Tap to delete',
              action: () => {
                Prompt.showToast({ message: "show toast index 2" });
              }
            })
          ],
        })
        Divider().height(2).color(0xCCCCCC)
      }
    }
  }
}
```

<!--Del--> <!--DelEnd-->

### Example 4: Setting the Left Icon as the Default Focus

In the focus state, this example uses the **defaultFocus** attribute of [EditableLeftIconV2](#editablelefticonv2) configured through the **EditableTitleBarV2** API to enable the left icon on the editable title bar to obtain focus by default.

The **EditableTitleBarV2** API is supported since API version 26.0.0.

```ts
import { Prompt } from '@kit.ArkUI';
import { EditableLeftIconTypeV2, EditableTitleBarV2, EditableLeftIconV2, EditableSaveButtonV2 } from '@kit.ArkUI';

@Entry
@Component
struct EditableTitleBarV2Demo04 {
  build(): void {
    Column() {
      EditableTitleBarV2({
        leftIcon: new EditableLeftIconV2({
          iconType: EditableLeftIconTypeV2.Back,
          defaultFocus: true, // Set the left icon to obtain focus by default.
        }),
        title: 'Edit page',
        menuItems: [],
        saveButton: new EditableSaveButtonV2({
          onAction: () => {
            Prompt.showToast({ message: 'on save' });
          }
        }),
      })
    }
    .height('100%')
    .width('100%')
  }
}
```

<!--Del--> <!--DelEnd-->

### Example 5: Setting the Right Custom Icon as the Default Focus

In the focus state, this example uses the right icon attribute **defaultFocus** of **EditableTitleBarV2** to enable the right icon on the editable title bar to obtain focus by default.

The **EditableTitleBarV2** API is supported since API version 26.0.0.

```ts
import { Prompt } from '@kit.ArkUI';
import {
  EditableLeftIconTypeV2,
  EditableTitleBarV2,
  EditableLeftIconV2,
  EditableTitleV2,
  EditableTitleBarMenuItemV2
} from '@kit.ArkUI';

@Entry
@Component
struct EditableTitleBarV2Demo05 {
  build(): void {
    Column() {
      EditableTitleBarV2({
        leftIcon: new EditableLeftIconV2({
          iconType: EditableLeftIconTypeV2.Back,
          onAction: () => {
            this.getUIContext()?.getRouter()?.back();
          },
        }),
        title: new EditableTitleV2({
          mainTitle: 'Title',
          subTitle: 'Subtitle',
        }),
        // Right icon configuration
        menuItems: [
          new EditableTitleBarMenuItemV2({
            value: $r('sys.media.ohos_ic_public_remove'),
            isEnabled: true,
            action: () => {
              Prompt.showToast({ message: "show toast index 1" });
            }
          }),
          new EditableTitleBarMenuItemV2({
            value: $r('sys.media.ohos_ic_public_remove'),
            isEnabled: true,
            defaultFocus: true,
            action: () => {
              Prompt.showToast({ message: "show toast index 2" });
            }
          })
        ],
      })
    }
    .height('100%')
    .width('100%')
  }
}
```

<!--Del--> <!--DelEnd-->

### Example 6: Setting a Symbol Icon

This example implements the custom symbol icon feature of the editable title bar through the **symbolStyle** attribute of the **EditableTitleBarV2** component.

The **EditableTitleBarV2** API is supported since API version 26.0.0.

```ts
import { Prompt, SymbolGlyphModifier } from '@kit.ArkUI';
import {
  EditableLeftIconTypeV2,
  EditableTitleBarV2,
  EditableLeftIconV2,
  EditableTitleV2,
  EditableTitleBarMenuItemV2
} from '@kit.ArkUI';

@Entry
@Component
struct EditableTitleBarV2Demo06 {
  build(): void {
    Row() {
      Column() {
        Divider().height(2).color(0xCCCCCC)
        EditableTitleBarV2({
          leftIcon: new EditableLeftIconV2({
            iconType: EditableLeftIconTypeV2.Cancel
          }),
          title: new EditableTitleV2({
            mainTitle: 'Title',
            subTitle: 'Subtitle',
          }),
          // Right icon configuration.
          menuItems: [
            new EditableTitleBarMenuItemV2({
              value: $r('sys.symbol.house'),
              isEnabled: true,
              action: () => {
                Prompt.showToast({ message: 'show toast index 2' });
              }
            }),
            new EditableTitleBarMenuItemV2({
              value: $r('sys.symbol.car'),
              isEnabled: false
            })
          ]
        })
        Divider().height(2).color(0xCCCCCC)
        EditableTitleBarV2({
          leftIcon: new EditableLeftIconV2({
            iconType: EditableLeftIconTypeV2.Back
          }),
          title: new EditableTitleV2({
            mainTitle: 'Title.',
            subTitle: 'Subtitle.',
          }),
          // Set the clickable avatar.
          imageItem: new EditableTitleBarMenuItemV2({
            value: $r('sys.media.ohos_app_icon'),
            isEnabled: true,
            action: () => {
              Prompt.showToast({ message: "show toast index 1" });
            }
          }),
          // Right icon configuration.
          menuItems: [
            new EditableTitleBarMenuItemV2({
              value: $r('sys.symbol.house'),
              symbolStyle: new SymbolGlyphModifier($r('sys.symbol.bell')).fontColor([Color.Red]),
              isEnabled: true,
              action: () => {
                Prompt.showToast({ message: 'show toast index 2' });
              }
            }),
            new EditableTitleBarMenuItemV2({
              value: $r('sys.symbol.car'),
              symbolStyle: new SymbolGlyphModifier($r('sys.symbol.heart')).fontColor([Color.Blue]),
              isEnabled: false,
            })
          ]
        })
        Divider().height(2).color(0xCCCCCC)
      }.width('100%')
    }.height('100%')
  }
}
```

<!--Del--> <!--DelEnd-->