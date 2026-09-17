# TabContent

The **TabContent** component is used only in the **Tabs** component. It corresponds to the content view of a switched tab page.

> **NOTE**

> - By default, the clip attribute of this component is set to **true**. > If you want to extend the content area to the outside of the component, disable the **clip** attribute first.

## Child Components

This component supports only one child component.

> **NOTE:** 
> 
> Built-in system and custom components, and rendering control types (
> [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md),
> [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md), and
> [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)) are supported.

## TabContent

```TypeScript
TabContent()
```

Creates the **TabContent** component, which represents the content associated with a specific tab.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [BoardStyle](arkts-arkui-boardstyle-i.md) | Represents a board style object. |
| [DrawableTabBarIndicator](arkts-arkui-drawabletabbarindicator-i.md) | Uses an image resource as the indicator. |
| [IndicatorStyle](arkts-arkui-indicatorstyle-i.md) | Represents an indicator style object. |
| [LabelStyle](arkts-arkui-labelstyle-i.md) | Represents a style object for the label text and font. |
| [TabBarIconStyle](arkts-arkui-tabbariconstyle-i.md) | Represents a label icon style object. |
| [TabBarOptions](arkts-arkui-tabbaroptions-i.md) | Defines the options for configuring images and text content on the tabs. |

### Types

| Name | Description |
| --- | --- |
| [DrawableDescriptor](arkts-arkui-drawabledescriptor-t.md) | Defines the input parameter object of the **drawable** attribute in the **DrawableTabBarIndicator** object. |

### Enums

| Name | Description |
| --- | --- |
| [LayoutMode](arkts-arkui-layoutmode-e.md) | Enumerates the layout modes of the images and texts on the bottom tabs. |
| [SelectedMode](arkts-arkui-selectedmode-e.md) | Enumerates the display modes of selected subtabs. |
| [TabVisibility](arkts-arkui-tabvisibility-e.md) | Enumerates the visibility of the tab. |

## Examples

```TypeScript
### Example 1: Implementing Custom Tab Switching Synchronization

This example demonstrates how to use [onAnimationStart](ts-container-tabs.md#onanimationstart11) and [onChange](ts-container-tabs.md#onchange) to implement synchronized switching between the tab bar and tab content.

> NOTE
> 
> The resources used in this example are not located in the src > main > resource directory. Starting from DevEco Studio 6.0.0 Beta2, the resources that are located outside the resources directory are not packaged by default when a project or module is created. To package these resources, go to buildOptions > resOptions > copyCodeResource in the module's build-profile.json5 file, and set enable to true. For details, see the description of [resOptions](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-hvigor-build-profile#section754823013348).


```

```TypeScript
### Example 2: Implementing a Custom Side Tabs

This example demonstrates how to create side tabs using [vertical](./ts-container-tabs.md#vertical) and [barPosition](./ts-container-tabs.md#barposition9).

> NOTE
> 
> The resources used in this example are not located in the src > main > resource directory. Starting from DevEco Studio 6.0.0 Beta2, the resources that are located outside the resources directory are not packaged by default when a project or module is created. To package these resources, go to buildOptions > resOptions > copyCodeResource in the module's build-profile.json5 file, and set enable to true. For details, see the description of [resOptions](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-hvigor-build-profile#section754823013348).


```

```TypeScript
### Example 3: Implementing Different Styles of Tabs

This example demonstrates how to create subtabs, bottom tabs, and side tabs using [SubTabBarStyle](arkts-arkui-subtabbarstyle-c.md) and [BottomTabBarStyle](arkts-arkui-bottomtabbarstyle-c.md).


```

```TypeScript
### Example 4: Setting the Indicator for Subtabs

This example demonstrates how to set the indicator for subtabs using the [indicator](#indicator10) property in SubTabBarStyle.


```

```TypeScript
### Example 5: Setting Adaptive Height for Subtab Text

This example demonstrates how to achieve adaptive height for subtab text using [heightAdaptivePolicy](#labelstyle10).


```

```TypeScript
### Example 6: Setting Basic Attributes for Bottom Tabs

This example demonstrates how to set basic attributes for bottom tabs using [padding](#padding10), [verticalAlign](#verticalalign10), [layoutMode](#layoutmode10), and [symmetricExtensible](arkts-arkui-bottomtabbarstyle-c.md#symmetricextensible).


```

```TypeScript
### Example 7: Setting Text and Icon Colors for Subtabs and Bottom Tabs

This example demonstrates how to change the text color of subtabs and bottom tabs using unselectedColor and selectedColor in [LabelStyle](#labelstyle10) and

how to change the icon color of bottom tabs using unselectedColor and selectedColor in [iconStyle](#iconstyle12).

> NOTE
> 
> The resources used in this example are not located in the src > main > resource directory. Starting from DevEco Studio 6.0.0 Beta2, the resources that are located outside the resources directory are not packaged by default when a project or module is created. To package these resources, go to buildOptions > resOptions > copyCodeResource in the module's build-profile.json5 file, and set enable to true. For details, see the description of [resOptions](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-hvigor-build-profile#section754823013348).


```

```TypeScript
### Example 8: Using Symbol Icons for Bottom Tabs

This example shows how to use symbols as icons in [BottomTabBarStyle](arkts-arkui-bottomtabbarstyle-c.md).


```

```TypeScript
### Example 9: Setting TabBar Using ComponentContent

This example demonstrates how to use ComponentContent to encapsulate component content and set the [TabBar](arkts-arkui-tabcontent-comp-attribute.md#tabbar). The update API of ComponentContent is used to update the TabBar.


```

```TypeScript
### Example 10: Preloading Child Nodes Using ComponentContent

This example demonstrates how to use ComponentContent to set the TabBar and preload child nodes using the [preloadItems](ts-container-tabs.md#preloaditems12) API of TabsController.


```

```TypeScript
### Example 11: Setting the Indicator of a Subtab to an Image

Since API version 22, this example uses the [indicator](#indicator22) attribute in SubTabBarStyle to implement the subtab indicator in image format.
```
