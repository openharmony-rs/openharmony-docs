# @ohos.atomicservice.AtomicServiceNavigation(This section describes the interfaces used by AtomicServiceNavigation)

## Child Components

Supported

Since API version 10, you are advised to use [NavPathStack](../arkts-components/arkts-arkui-navpathstack-c.md) for page routing.

## Modules to Import

```TypeScript
import { AtomicServiceNavigation, NavDestinationBuilder, MixMode, GradientAlpha, BackgroundTheme, TitleBarType, SideBarOptions, TitleOptions, GradientBackground } from '@kit.ArkUI';
```

## Summary

### Structs

| Name | Description |
| --- | --- |
| [AtomicServiceNavigation](arkts-arkui-atomicservice-atomicservicenavigation-atomicservicenavigation-s.md) | **AtomicServiceNavigation** is a component that serves as the root container of a page. By default, it includes a title bar, content area, and toolbar. The content area switches between the home page content (child components of NavDestination) and non-home page content through routing. |

### Interfaces

| Name | Description |
| --- | --- |
| [GradientBackground](arkts-arkui-atomicservice-atomicservicenavigation-gradientbackground-i.md) | Provides options for setting gradient colors for branding. |
| [SideBarOptions](arkts-arkui-atomicservice-atomicservicenavigation-sidebaroptions-i.md) | Defines sidebar options. |
| [TitleOptions](arkts-arkui-atomicservice-atomicservicenavigation-titleoptions-i.md) | Title bar options. |

### Enums

| Name | Description |
| --- | --- |
| [BackgroundTheme](arkts-arkui-atomicservice-atomicservicenavigation-backgroundtheme-e.md) | Enumerates the navigation bar background themes. |
| [GradientAlpha](arkts-arkui-atomicservice-atomicservicenavigation-gradientalpha-e.md) | Enumerates the opacity levels of the navigation bar background. |
| [MixMode](arkts-arkui-atomicservice-atomicservicenavigation-mixmode-e.md) | Provides options for background color blending modes. |
| [TitleBarType](arkts-arkui-atomicservice-atomicservicenavigation-titlebartype-e.md) | Enumerates the title bar types. The default type is **ROUND_ICON**. |

### Types

| Name | Description |
| --- | --- |
| [NavDestinationBuilder](arkts-arkui-navdestinationbuilder-t.md) | Defines the content of the **NavDestination** component. |

## Examples

```TypeScript
### Example 1: Setting the Layout and Gradient Background

This example demonstrates the basic style and gradient background of AtomicServiceNavigation.


```

```TypeScript
### Example 2: Implementing the Drawer Style with Custom Layouts for Wide-Screen Scenarios

This example sets the drawer mode in wide-screen scenarios (width greater than 600 vp) and inserts custom layouts into the title bar.


```

```TypeScript
### Example 3: Configuring the Sidebar

This example sets the sidebar background color and content style.
```
