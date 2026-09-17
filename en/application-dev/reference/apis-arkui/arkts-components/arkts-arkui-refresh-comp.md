# Refresh

The **Refresh** component is a container that provides the pull-to-refresh feature.

> **NOTE** > > - This component is supported since API version 8. Updates will be marked with a superscript to indicate their > earliest API version. > > - Since API version 12, this component provides linkage with a vertically scrolling Swiper and > [Web](../../../reference/apis-arkui/arkui-js/js-components-basic-web.md) components. When the > loop attribute of Swiper is set to **true**, the **Refresh** > component cannot provide linkage with Swiper. > > - When the **Refresh** component is nested with a List component whose content size is smaller than > the component itself, and there are other components in between, gestures may be intercepted by the intermediate > components, preventing the pull-to-refresh effect. In such cases, set the [alwaysEnabled](arkts-arkui-edgeeffectoptions-i.md) > parameter to **true** to allow List to respond to gestures and drive the **Refresh** component > through nested scrolling for the pull-to-refresh effect. For details, see > [Example 9: Implementing Pull-to-Refresh in the Non-Full-Screen Scenario](../../../reference/apis-arkui/arkui-ts/ts-container-refresh.md#example-9-implementing-pull-to-refresh-in-the-non-full-screen-scenario). > > - The component has been bound with gestures to implement functions such as follow-up scrolling. If you need to add > custom gestures, refer to Gesture Blocking Enhancement. > > - Pull-to-refresh cannot be triggered by mouse click-and-drag operations.

## Child Components

This component supports only one child component.

Since API version 11, this component's child component moves down with the pull-down gesture.

## Refresh

```TypeScript
Refresh(value: RefreshOptions)
```

Creates a **Refresh** container.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [RefreshOptions](arkts-arkui-refreshoptions-i.md) | Yes | Parameters of the **Refresh** component. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [RefreshOptions](arkts-arkui-refreshoptions-i.md) | Defines the options of the **Refresh** component. |

### Enums

| Name | Description |
| --- | --- |
| [RefreshStatus](arkts-arkui-refreshstatus-e.md) | Enumerates the states of a refresh operation. |

## Examples

```TypeScript
### Example 1: Using the Default Refreshing Style

This example implements a Refresh component with its refreshing area in the default style.


```

```TypeScript
### Example 2: Setting the Text Displayed in the Refreshing Area

This example shows how to set the text displayed in the refreshing area using the [promptText](arkts-arkui-refreshoptions-i.md) parameter.


```

```TypeScript
### Example 3: Customizing the Refreshing Area Content with builder

This example shows how to customize the content displayed in the refreshing area using the [builder](arkts-arkui-refreshoptions-i.md) parameter.


```

```TypeScript
### Example 4: Customizing the Refreshing Area Content with refreshingContent

This example shows how to customize the content displayed in the refreshing area using the [refreshingContent](arkts-arkui-refreshoptions-i.md) parameter.


```

```TypeScript
### Example 5: Implementing the Maximum Pull-down Distance

This example shows how to use the [pullDownRatio](arkts-arkui-refresh-comp-attribute.md#pulldownratio) attribute and the [onOffsetChange](#onoffsetchange12) event to implement the maximum pull-down distance.


```

```TypeScript
### Example 6: Implementing Pull-Down-to-Refresh and Pull-Up-to-Load-More

This example demonstrates how to combine the Refresh component with the [List](ts-container-list.md) component to implement pull-down-to-refresh and pull-up-to-load-more features.


```

```TypeScript
### Example 7: Setting the Maximum Pull-Down Distance

This example demonstrates how to set the maximum pull-down distance using the [maxPullDownDistance](arkts-arkui-refresh-comp-attribute.md#maxpulldowndistance) attribute, supported since API version 20.


```

```TypeScript
### Example 8: Disabling Pull-to-Refresh

This example demonstrates how to disable pull-to-refresh using the [pullDownRatio](arkts-arkui-refresh-comp-attribute.md#pulldownratio) attribute.


```

```TypeScript
### Example 9: Implementing Pull-to-Refresh in the Non-Full-Screen Scenario

When calling [edgeEffect](ts-container-scrollable-common.md#edgeeffect11), set [alwaysEnabled](ts-container-scrollable-common.md#edgeeffectoptions11) of the options parameter to true to implement the pull-to-refresh effect of the Refresh component when the content is less than one screen.


```

```TypeScript
### Example 10: Pull-Up Without Cancelling Refresh

This example uses the [pullUpToCancelRefresh](arkts-arkui-refresh-comp-attribute.md#pulluptocancelrefresh) API to configure pull-up without canceling refresh.

The pullUpToCancelRefresh API is supported since API version 23.
```
