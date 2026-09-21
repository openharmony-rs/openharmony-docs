# Navigation properties/events

```TypeScript
declare class NavigationAttribute extends CommonMethod<NavigationAttribute>
```

In addition to the universal attributes, the following attributes are supported.

**Inheritance/Implementation:** NavigationAttribute extends CommonMethod<NavigationAttribute>

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backButtonIcon

```TypeScript
backButtonIcon(value: string | PixelMap | Resource | SymbolGlyphModifier)
```

Sets the icon of the back button in the title bar.

> **NOTE:** 
> 
> The following are not allowed: modify the icon size through the **fontSize** attribute of the
> **SymbolGlyphModifier** object, change the animation effects through the **effectStrategy** attribute, or change
> the type of animation effects through the **symbolEffect** attribute.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string &#124; [PixelMap](arkts-arkui-common-comp-pixelmap-t.md) &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) &#124; [SymbolGlyphModifier](arkts-arkui-common-comp-symbolglyphmodifier-t.md) | Yes | Icon of the back button in the title bar.<br>**Since:** 12 |

<a id="backbuttonicon-1"></a>

## backButtonIcon

```TypeScript
backButtonIcon(icon: string | PixelMap | Resource | SymbolGlyphModifier, accessibilityText?: ResourceStr)
```

Sets the icon and accessibility text for the back button on the title bar.

> **NOTE:** 
> 
> This API cannot be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).
> 
> The following are not allowed: modify the icon size through the **fontSize** attribute of the
> **SymbolGlyphModifier** object, change the animation effects through the **effectStrategy** attribute, or change
> the type of animation effects through the **symbolEffect** attribute.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| icon | string &#124; [PixelMap](arkts-arkui-common-comp-pixelmap-t.md) &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) &#124; [SymbolGlyphModifier](arkts-arkui-common-comp-symbolglyphmodifier-t.md) | Yes | Icon of the back button in the title bar. |
| accessibilityText | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | No | Accessibility text for the back button.<br>Default value: **back** when the system language is English. |

## configuration

```TypeScript
configuration(config: NavigationConfiguration)
```

Sets Navigation configuration.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [NavigationConfiguration](arkts-arkui-navigation-comp-navigationconfiguration-i.md) | Yes | Navigation configuration options. |

## customNavContentTransition

```TypeScript
customNavContentTransition(delegate: (from: NavContentInfo, to: NavContentInfo, operation: NavigationOperation)
    => NavigationAnimatedTransition | undefined)
```

Defines the callback of the custom transition animation.

> **NOTE:** 
> 
> This API can be called in [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 20.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| delegate | (from: NavContentInfo, to: NavContentInfo, operation: NavigationOperation)     =&gt; NavigationAnimatedTransition &#124; undefined | Yes | Defines the callback of the custom transition animation.<br>from: Destination page to exit.<br>to: Destination page to enter.<br>operation: Transition type.<br> **NavigationAnimatedTransition**: protocol object for custom transition animations.<br>**undefined**: undefined, executing the default transition animation effect. |

## divider

```TypeScript
divider(style: NavigationDividerStyle | null)
```

Sets the divider style in the split-column mode of the **Navigation** component.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [NavigationDividerStyle](arkts-arkui-navigation-comp-navigationdividerstyle-i.md) &#124; null | Yes | Sets the divider style of the split-column layout.<br> - null: The divider is hidden. |

## enableDragBar

```TypeScript
enableDragBar(isEnabled: Optional<boolean>)
```

Sets whether to display a drag bar in split-column scenarios. This attribute has no effect on PCs/2-in-1 devices.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isEnabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable the drag bar. By default, there is no drag bar.<br> **true**: yes; **false**: no<br>If the input parameter is invalid, the value **false** is used. |

## enableModeChangeAnimation

```TypeScript
enableModeChangeAnimation(isEnabled: Optional<boolean>)
```

Sets whether to enable the animation for switching between single- and split-column modes.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isEnabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable the animation for switching between single- and split- column modes.<br>**true**: yes; **false**: no<br>If the input parameter is invalid, the value **true** is used. |

## enableToolBarAdaptation

```TypeScript
enableToolBarAdaptation(enable: Optional<boolean>)
```

Sets whether to enable toolbar adaptation ([toolbarConfiguration](#toolbarconfiguration)) for the **Navigation** and **NavDestination** components. If this feature is disabled, the bottom toolbar ([toolbarConfiguration](#toolbarconfiguration)) will no longer be moved into the menu in the upper right corner of the page. This API does not apply to custom menus; using it requires defining the [menu](#menus) via the [NavigationMenuItem](arkts-arkui-navigation-comp-navigationmenuitem-i.md) API.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable toolbar adaptation.<br>Default value: **true**<br>**true**: Enable toolbar adaptation.<br>**false**: Disable toolbar adaptation. |

## enableVisibilityLifecycleWithContentCover

```TypeScript
enableVisibilityLifecycleWithContentCover(isEnabled: Optional<boolean>)
```

Sets whether to enable the linkage between the [onShown](arkts-arkui-navdestination-comp-attribute.md#onshown) and [onHidden](arkts-arkui-navdestination-comp-attribute.md#onhidden) lifecycle callbacks of the NavDestination page and the full-modal triggering.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isEnabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable the linkage between the **onShown** and **onHidden** lifecycle callbacks of the NavDestination page and the full-modal triggering.<br>Default value: **true**<br> **true**: When a full-modal page is shown, the current **NavDestination** page triggers **onHidden**. When the full-modal pages is dismissed, the page triggers **onShown**.<br>**false**: The **onShown** and **onHidden** callbacks of the **NavDestination** page are not triggered by the showing or dismissing of a full-modal page. |

## hideBackButton

```TypeScript
hideBackButton(value: boolean)
```

Sets whether to hide the back button in the title bar. The back button takes effect only when [titleMode](#titlemode) is set to **NavigationTitleMode.Mini**.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to hide the back button in the title bar.<br>**true**: Hide the back button in the title bar.<br>**false**: Show the back button in the title bar.<br>If the input parameter is invalid, the value **false** is used. |

## hideNavBar

```TypeScript
hideNavBar(value: boolean)
```

Sets whether to hide the navigation page. If the value is set to **true**, the navigation bar, including the title bar, content area, and toolbar, will be hidden. In this case, if the navigation destination page is in the routing stack, it is moved to the top of the stack and displayed. Otherwise, a blank page is displayed.

From API version 9 to API version 10, this attribute takes effect only in split-column mode. Since API version 11, this attribute takes effect in all display modes.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to hide the navigation page.<br>**true**: yes<br>**false**: no<br>If the input parameter is invalid, the value **false** is used. |

## hideTitleBar

```TypeScript
hideTitleBar(value: boolean)
```

Specifies whether to hide the title bar.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to hide the title bar.<br>**true**: yes<br>**false**: no<br>If the input parameter is invalid, the value **false** is used. |

<a id="hidetitlebar-1"></a>

## hideTitleBar

```TypeScript
hideTitleBar(hide: boolean, animated: boolean)
```

Specifies whether to hide the title bar. Compared with [hideTitleBar](#hidetitlebar), this API adds the capability to control whether to animate the visibility change of the title bar.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hide | boolean | Yes | Whether to hide the title bar.<br>**true**: yes<br>**false**: no<br>If the input parameter is invalid, the value **false** is used. |
| animated | boolean | Yes | Whether to animate the visibility change.<br>**true**: yes<br> **false**: no<br>If the input parameter is invalid, the value **false** is used. |

## hideToolBar

```TypeScript
hideToolBar(value: boolean)
```

Specifies whether to hide the toolbar.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to hide the toolbar.<br>**true**: Hide the toolbar. <br>**false**: Display the toolbar.<br>If the input parameter is invalid, the value **false** is used. |

<a id="hidetoolbar-1"></a>

## hideToolBar

```TypeScript
hideToolBar(hide: boolean, animated: boolean)
```

Specifies whether to hide the toolbar. Compared with [hideToolBar](#hidetoolbar), this API adds the capability to control whether to animate the visibility change of the toolbar.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hide | boolean | Yes | Whether to hide the toolbar.<br>**true**: Hide the toolbar. <br>**false**: Display the toolbar.<br>If the input parameter is invalid, the value **false** is used. |
| animated | boolean | Yes | Whether to animate the visibility change.<br>**true**: yes<br>**false**: no<br>If the input parameter is invalid, the value **false** is used. |

## ignoreLayoutSafeArea

```TypeScript
ignoreLayoutSafeArea(types?: Array<LayoutSafeAreaType>, edges?: Array<LayoutSafeAreaEdge>)
```

Ignores the layout safe area by allowing the component to extend into the non-safe areas of the screen.

> **NOTE:** 
> 
> - Prerequisites for the **ignoreLayoutSafeArea** attribute to take effect:
> 
> When **LayoutSafeAreaType.SYSTEM** is set, the component can extend into the non-safe area if its boundaries
> overlap with it.
> 
> - If the component extends into the non-safe area, events triggered within that area (such as click events) might be intercepted by the system. This allows the system to prioritize responses to system components such as the status bar.
> 
> - To allow a component to extend into non-safe areas, the title bar and toolbar must be hidden or set to [STACK](arkts-arkui-navigation-comp-barstyle-e.md) mode.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| types | Array&lt;[LayoutSafeAreaType](arkts-arkui-common-comp-layoutsafeareatype-e.md)&gt; | No | Types of non-safe areas to extend into.<br>Default value:<br> [LayoutSafeAreaType.SYSTEM] |
| edges | Array&lt;[LayoutSafeAreaEdge](arkts-arkui-common-comp-layoutsafeareaedge-e.md)&gt; | No | Edges for expanding the safe area.<br> Default value:<br> [LayoutSafeAreaEdge.TOP, LayoutSafeAreaEdge.BOTTOM] |

## menus

```TypeScript
menus(value: Array<NavigationMenuItem> | CustomBuilder)
```

Sets the menu items in the upper right corner of the page. If this attribute is not set, no menu item is displayed. When the value type is Array&lt;[NavigationMenuItem](arkts-arkui-navigation-comp-navigationmenuitem-i.md)&gt;, the menu shows a maximum of three icons in portrait mode and a maximum of five icons in landscape mode, with excess icons (if any) placed under the automatically generated **More** icon.

> **NOTE:** 
> 
> The following are not allowed: modify the icon size through the **fontSize** attribute of the
> **SymbolGlyphModifier** object, change the animation effects through the **effectStrategy** attribute, or change
> the type of animation effects through the **symbolEffect** attribute.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Array&lt;[NavigationMenuItem](arkts-arkui-navigation-comp-navigationmenuitem-i.md)&gt; &#124; [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) | Yes | Menu items in the upper right corner of the page. |

<a id="menus-1"></a>

## menus

```TypeScript
menus(items: Array<NavigationMenuItem> | CustomBuilder, options?: NavigationMenuOptions)
```

Sets the menu items in the upper right corner of the page. If this attribute is not set, no menu item is displayed. Compared with [menus](#menus), this API adds menu options. When the value type is Array&lt;[NavigationMenuItem](arkts-arkui-navigation-comp-navigationmenuitem-i.md)&gt;, the menu shows a maximum of three icons in portrait mode and a maximum of five icons in landscape mode, with excess icons (if any) placed under the automatically generated **More** icon.

> **NOTE:** 
> 
> This API cannot be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).
> 
> The following are not allowed: modify the icon size through the **fontSize** attribute of the
> **SymbolGlyphModifier** object, change the animation effects through the **effectStrategy** attribute, or change
> the type of animation effects through the **symbolEffect** attribute.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| items | Array&lt;[NavigationMenuItem](arkts-arkui-navigation-comp-navigationmenuitem-i.md)&gt; &#124; [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) | Yes | Menu items in the upper right corner of the page. |
| options | [NavigationMenuOptions](arkts-arkui-navigation-comp-navigationmenuoptions-i.md) | No | Configuration options for menu items in the upper right corner of the page. |

## minContentWidth

```TypeScript
minContentWidth(value: Dimension)
```

Minimum width of the navigation bar content area (effective in split-column mode).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) | Yes | Minimum width of the content area on the navigation page.<br>Default value: **360**<br>Unit: vp<br>**undefined**: No action is taken, and the minimum width of the navigation page remains consistent with the default value.<br>Breakpoint calculation in Auto mode: default 600 vp = minNavBarWidth (240 vp) + minContentWidth (360 vp) |

## mode

```TypeScript
mode(value: NavigationMode)
```

Sets the display mode of the navigation page.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [NavigationMode](arkts-arkui-navigation-comp-navigationmode-e.md) | Yes | Display mode of the navigation page.<br>Default value: **NavigationMode.Auto**<br>At the default settings, the component adapts to a single column or two columns based on the component width. |

## navBarPosition

```TypeScript
navBarPosition(value: NavBarPosition)
```

Sets the position of the navigation page. It takes effect only when [mode](#mode) is set to **NavigationMode.Auto** or **NavigationMode.Split**.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [NavBarPosition](arkts-arkui-navigation-comp-navbarposition-e.md) | Yes | Position of the navigation page.<br>Default value: **NavBarPosition.Start** |

## navBarWidth

```TypeScript
navBarWidth(value: Length)
```

Set the width of the navigation page. It takes effect only when [mode](#mode) is set to **NavigationMode.Auto** or **NavigationMode.Split**.

Since API version 18, this attribute supports two-way binding through [!!](../../../ui/state-management/arkts-new-binding.md).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Width of the navigation page.<br>Default value: **240**<br>Unit: vp<br>**undefined**: No action is taken, and the navigation page width remains consistent with the default value. |

## navBarWidthRange

```TypeScript
navBarWidthRange(value: [Dimension, Dimension])
```

Sets the minimum and maximum widths of the navigation page (effective in split-column mode). When this API is not used, the minimum width defaults to 240 vp, and the maximum width defaults to 40% of the component width (not exceeding 432 vp). When dragging the divider changes the navigation page width, the content area will be compressed.

Divider dragging range:

| Condition| Dragging Range |  
| ----| ----------- |  
|Both **navBarWidthRange** and **minContentWidth** are set.| Range set by **navBarWidthRange**if the value set by **minContentWidth** is satisfied|

|Neither **navBarWidthRange** nor **minContentWidth** is set.| Default minimum and maximum ranges of **navBarWidthRange**|

|Only the **navBarWidthRange** attribute is set.| Range set by **navBarWidthRange**,where the maximum dragging range cannot exceed the default value of **minContentWidth**|

|Only the **minContentWidth** attribute is set.| Default minimum and maximum ranges of **navBarWidthRange**|  
|Only the **navBarWidth** attribute is set.| Dragging not supported|

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Dimension, Dimension] | Yes | Minimum and maximum widths of the navigation page. If an invalid value is set, the default value is used. |

## navDestination

```TypeScript
navDestination(builder: (name: string, param: unknown) => void)
```

Creates a **NavDestination** component. The builder receives the **name** and **param** parameters for constructing the **NavDestination** component. The builder must return a single root node. The builder can have only one root node. In the builder, a layer of custom components can wrap the **NavDestination** component. However, no attributes or events can be set for these custom components. Otherwise, only blank content is displayed.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| builder | (name: string, param: unknown) =&gt; void | Yes | Builder for a **NavDestination** component. **name**: name of the **NavDestination** page. **param**: detailed parameters for the custom **NavDestination** page. The **unknown** type can be replaced with a user-defined type. |

## onNavBarStateChange

```TypeScript
onNavBarStateChange(callback: (isVisible: boolean) => void)
```

Callback invoked when the navigation page visibility status changes.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (isVisible: boolean) =&gt; void | Yes | Whether the navigation bar is visible. The value **true** means that the navigation bar is visible, and **false** means the opposite.<br>**Since:** 10 |

## onNavigationModeChange

```TypeScript
onNavigationModeChange(callback: (mode: NavigationMode) => void)
```

Triggered when the **Navigation** component is displayed for the first time or its display mode switches between single-column and split-column.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (mode: NavigationMode) =&gt; void | Yes | **NavigationMode.Split**: The component is displayed in split-column mode.<br> **NavigationMode.Stack**: The component is displayed in single-column mode. |

## onTitleModeChange

```TypeScript
onTitleModeChange(callback: (titleMode: NavigationTitleMode) => void)
```

Triggered when [titleMode](#titlemode) is set to **NavigationTitleMode.Free** and the title bar mode changes as content scrolls.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (titleMode: NavigationTitleMode) =&gt; void | Yes | Title mode.<br>**Since:** 10 |

## recoverable

```TypeScript
recoverable(recoverable: Optional<boolean>)
```

Sets whether the **Navigation** component is recoverable. If set to recoverable, when the application process exits unexpectedly and restarts, the **Navigation** component can be automatically re-created and its routing stack restored to the state at the time of the unexpected exit.

> **NOTE:** 
> 
> 1. For this API to work properly, you must first set the universal attribute [id](arkts-arkui-common-comp-commonmethod-c.md#id) of the
> **Navigation** component.
> 
> 2. This API must be used together with the [recoverable](arkts-arkui-navdestination-comp-attribute.md#recoverable) API of
> **NavDestination**.
> 
> 3. Non-serializable information, such as non-serializable parameters and custom **onPop**, is discarded and cannot be restored during the recovery process.
> 
> 4. If an application is terminated due to insufficient system resources after it is switched to the background,any page configured as recoverable will be automatically restored when the application is revived to the foreground. For details, see [UIAbility Backup and Restore](../../../application-models/ability-recover-guideline.md). For the usage example,see [Example 18: Setting Navigation as Recoverable](../../../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#example-18-setting-navigation-as-recoverable).

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| recoverable | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether the **Navigation** component is recoverable. By default, it is not recoverable.<br>**true**: yes<br>**false**: no<br>If the input parameter is invalid, the value **false** is used. |

## splitPlaceholder

```TypeScript
splitPlaceholder(placeholder: ComponentContent)
```

Sets a default placeholder page for the right column in the **Navigation** component's split-column mode. The placeholder page is for UI display only and cannot receive focus or respond to events.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| placeholder | ComponentContent | Yes | Default placeholder page for the right column in the **Navigation** component's split-column mode. |

## subTitle

```TypeScript
subTitle(value: string)
```

Sets the page subtitle.

> **NOTE:** 

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [title](#title)

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string | Yes | Page subtitle. |

## systemBarStyle

```TypeScript
systemBarStyle(style: Optional<SystemBarStyle>)
```

Sets the style of the system status bar when the home page of the **Navigation** component is displayed.

> **NOTE:** 
> 
> 1. Avoid using the **systemBarStyle** attribute in conjunction with the status bar style APIs in the **Window**module, such as [setWindowSystemBarProperties](../../../reference/apis-arkui/arkts-apis-window-Window.md#setwindowsystembarproperties9).
> 
> 
> 2. When you first set the **systemBarStyle** attribute for a **Navigation** or **NavDestination** component, the current status bar style is saved for potential future restoration.
> 
> 3. **Navigation** always uses the status bar style defined by the home page (when no **NavDestination** exists in the routing stack) or the top **NavDestination** in the stack.
> 
> 4. If the home page or any top **NavDestination** page has a valid **systemBarStyle** set, that style will be used. If no style is set, and there is a previously saved style available, the saved style will be used. If no style has been set or saved, no changes will be made.
> 
> 5. In [Split](arkts-arkui-navigation-comp-navigationmode-e.md) mode, if there is no **NavDestination** in the content area, the settings of the **Navigation** home page will apply. Otherwise, the settings of the top **NavDestination** page on the routing stack will apply.
> 
> 6. The **systemBarStyle** attribute is effective only for the main page of the main window.
> 
> 7. The set style will only take effect if the **Navigation** component spans the entire page. If it does not, and there is a previously saved style available, the saved style will be used instead.
> 
> 8. When different styles are set for pages, the new style takes effect at the start of the page transition.
> 
> 9. The status bar style set by **Navigation** or **NavDestination** does not apply in non-fullscreen windows.
> 
> This API can be called in [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 20.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[SystemBarStyle](arkts-arkui-navigation-comp-systembarstyle-t.md)&gt; | Yes | Style of the system status bar. |

## title

```TypeScript
title(value: ResourceStr | CustomBuilder | NavigationCommonTitle | NavigationCustomTitle, options?: NavigationTitleOptions)
```

Sets the page title.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 12.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) &#124; [NavigationCommonTitle](arkts-arkui-navigation-comp-navigationcommontitle-i.md) &#124; [NavigationCustomTitle](arkts-arkui-navigation-comp-navigationcustomtitle-i.md) | Yes | Page title. When the NavigationCustomTitle type is used to set the height, [titleMode](#titlemode) does not take effect.<br>When the title string is too long:<br>- If no subtitle is set, the string is scaled down, wrapped in two lines, and then clipped.<br> - If a subtitle is set, the subtitle is scaled down and then clipped.<br>**Since:** 10 |
| options | [NavigationTitleOptions](arkts-arkui-navigation-comp-navigationtitleoptions-i.md) | No | Defines the title bar options. Title bar options include the background color, background blur style, blur options, background properties, layout style, and padding at the start and end of the title bar, as well as main title attribute modifier, subtitle attribute modifier, and whether to respond when the device is in semi-folded mode..<br>**Since:** 11 |

## titleMode

```TypeScript
titleMode(value: NavigationTitleMode)
```

Sets the display mode of the page title bar.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [NavigationTitleMode](arkts-arkui-navigation-comp-navigationtitlemode-e.md) | Yes | Display mode of the page title bar.<br>Default value: **NavigationTitleMode.Free** |

## toolBar

```TypeScript
toolBar(value: object | CustomBuilder)
```

Sets the content of the toolbar. If this attribute is not set, no toolbar is displayed. Toolbar items are evenly distributed on the bottom toolbar, with text and icons evenly spaced in each content area. If any item contains overlong text and there are fewer than five items, the toolbar will reduce the text size progressively, wrap the text over two lines if necessary, and then clip the text to fit.

**object**

**Since:** 8

**Deprecated since:** 10

**Substitutes:** [toolbarConfiguration](#toolbarconfiguration)

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | object &#124; [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) | Yes | Content of the toolbar. |

## toolbarConfiguration

```TypeScript
toolbarConfiguration(value: Array<ToolbarItem> | CustomBuilder, options?: NavigationToolbarOptions)
```

Sets the content of the toolbar. If this attribute is not set, no toolbar is displayed.

> **NOTE:** 
> 
> This API can be called in [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 20.
> 
> The following are not allowed: modify the icon size through the **fontSize** attribute of the
> **SymbolGlyphModifier** object, change the animation effects through the **effectStrategy** attribute, or change
> the type of animation effects through the **symbolEffect** attribute.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Array&lt;[ToolbarItem](arkts-arkui-navigation-comp-toolbaritem-i.md)&gt; &#124; [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) | Yes | Content of the toolbar. When configured with Array&lt;[ToolbarItem](arkts-arkui-navigation-comp-toolbaritem-i.md)&gt;, the toolbar follows the rules below:<br>Toolbar items are evenly distributed on the bottom toolbar, with text and icons evenly spaced in each content area.<br>In portrait mode, the toolbar shows a maximum of five icons, with any additional icons placed into an automatically generated **More** icon. In landscape mode, toolbar behavior depends on the display mode: <br>- If the display mode is [Split](arkts-arkui-navigation-comp-navigationmode-e.md), the toolbar maintains the portrait mode. <br>- If the display mode is [Stack](arkts-arkui-navigation-comp-navigationmode-e.md), the toolbar must be used together with Array&lt;[NavigationMenuItem](arkts-arkui-navigation-comp-navigationmenuitem-i.md)&gt; of the **menus** attribute; in this configuration, the bottom toolbar is automatically hidden, and all items on the toolbar are relocated to the menu in the upper right corner of the screen.<br>When configured with [CustomBuilder](../../../reference/apis-arkui/arkui-ts/ts-types.md#custombuilder8), the toolbar does not follow the above rules. |
| options | [NavigationToolbarOptions](arkts-arkui-navigation-comp-navigationtoolbaroptions-i.md) | No | Toolbar options. Toolbar options include the background color, background blur style and blur option, background properties, and layout mode of the toolbar, as well as whether to hide the toolbar text, and options for the toolbar's more button menu..<br>**Since:** 11 |
