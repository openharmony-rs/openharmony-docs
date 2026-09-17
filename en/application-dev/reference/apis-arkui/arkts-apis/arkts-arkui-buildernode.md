# BuilderNode

## Summary

### Classes

| Name | Description |
| --- | --- |
| [BuilderNode](arkts-arkui-buildernode-c.md) | The **BuilderNode** module provides APIs for a BuilderNode – a custom node that can be used to mount built-in components. A BuilderNode can be used only as a leaf node. For details, see [BuilderNode Development](../../../ui/arkts-user-defined-arktsNode-builderNode.md). For best practices, see [Dynamic Component Creation: Dynamically Adding, Updating, and Deleting Components](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-ui-dynamic-operations#section153921947151012). |
| [ReactiveBuilderNode](arkts-arkui-buildernode-reactivebuildernode-c.md) | **ReactiveBuilderNode** uses the stateless UI method [@Builder](../../../ui/state-management/arkts-builder.md) to generate a component tree and holds the root node of the component tree. A ReactiveBuilderNode cannot be defined as a state variable. FrameNode held in **ReactiveBuilderNode** is used only to mount the ReactiveBuilderNode as a child node to another FrameNode. Undefined behavior may occur if you set attributes or perform operations on subnodes of the FrameNode held by the ReactiveBuilderNode. Therefore, after you have obtained a RenderNode through the [getFrameNode](arkts-arkui-buildernode-c.md#getframenode) method of the ReactiveBuilderNode and the [getRenderNode](arkts-arkui-framenode-c.md#getrendernode) method of the FrameNode, avoid setting the attributes or operating the subnodes through APIs of [RenderNode](arkts-arkui-rendernode-c.md). |

### Interfaces

| Name | Description |
| --- | --- |
| [BuildOptions](arkts-arkui-buildernode-buildoptions-i.md) | Defines the optional build options. |
| [RenderOptions](arkts-arkui-buildernode-renderoptions-i.md) | Provides optional parameters for creating a BuilderNode. |

### Enums

| Name | Description |
| --- | --- |
| [NodeRenderType](arkts-arkui-buildernode-noderendertype-e.md) | Enumerates the node rendering types. |

### Types

| Name | Description |
| --- | --- |
| [InputEventType](arkts-arkui-inputeventtype-t.md) | Defines the type of input event to be dispatched. For details, see [postInputEvent](arkts-arkui-buildernode-c.md#postinputevent). |

## Examples

```TypeScript
### Example 1: Handling Mouse Events in BuilderNode

This example demonstrates the end-to-end process for intercepting mouse events in a custom component and performing coordinate conversion. The component reads local x- and y-coordinates through the [onMouse](../arkui-ts/ts-universal-mouse-key.md#onmouse) callback, then uses vp2px to convert relative coordinates to pixel coordinates based on the offset obtained from FrameNode.getPositionToParent(). The windowX, windowY, displayX, and displayY values in [MouseEvent](../arkui-ts/ts-universal-mouse-key.md#mouseevent) are updated accordingly. Finally, the converted mouse event is posted to child nodes through rootNode.postInputEvent(event).


```

```TypeScript
### Example 2: Handling Touch Events in BuilderNode

This example demonstrates the end-to-end process for intercepting touch events in a custom component and transforming touch point coordinates. The implementation: 1. iterates through changedTouches and touches arrays of [TouchEvent](../arkui-ts/ts-universal-events-touch.md#touchevent) in the [onTouch](../arkui-ts/ts-universal-events-touch.md#ontouch) callback; 2. for each touch point, adds the component offset to the X and Y coordinates and converts the result to pixels using vp2px; 3. updates the windowX, windowY, displayX, and displayY values of each touch point; 4. posts the processed touch event to child nodes using rootNode.postInputEvent(event).


```

```TypeScript
### Example 3: Handling Axis Events in BuilderNode

This example demonstrates the end-to-end process for intercepting wheel or trackpad axis events in a custom component and performing coordinate conversion. The implementation: 1. obtains relative X and Y coordinates from the [onAxisEvent](../arkui-ts/ts-universal-events-axis.md#onaxisevent) callback; 2. adds the component offset and converts the result to pixels using vp2px; 3. updates the windowX, windowY, displayX, and displayY values in AxisEvent; 4. posts the transformed axis event to child nodes using rootNode.postInputEvent(event).


```

```TypeScript
### Example 4: Passing a BuilderNode Shared localStorage Instance

This example demonstrates how to pass an external [localStorage](../arkui-ts/ts-state-management.md#localstorage9) instance to a BuilderNode through the build method. In this case, all custom components mounted on the BuilderNode share this localStorage.
```

```TypeScript
### Example 5: Configuring the BuilderNode for Cross-Boundary @Provide-@Consume Communication

Set enableProvideConsumeCrossing in [BuildOptions](arkts-arkui-buildernode-buildoptions-i.md) of the BuilderNode to true to implement two-way synchronization between the @Consume decorated variable of the custom component inside the BuilderNode and the @Provide decorated variable outside the BuilderNode.


```

```TypeScript
### Example 6: Configuring the BuilderNode for Cross-Boundary @Provider-@Consumer Communication

> NOTE
> 
> Since API version 23, cross-BuilderNode pairing of @Provider and @Consumer is supported.

Set enableProvideConsumeCrossing in [BuildOptions](arkts-arkui-buildernode-buildoptions-i.md) of the BuilderNode to true to support two-way synchronization between the @Consumer decorated state variable of the custom component inside the BuilderNode and the @Provider decorated state variable outside the BuilderNode.


```

```TypeScript
### Example 7: Synchronization Relationship Changes During BuilderNode Mounting and Unmounting

> NOTE
> 
> Since API version 23, cross-BuilderNode pairing of @Provider and @Consumer is supported.

This example demonstrates how the synchronization relationship between @Consumer and @Provider changes when a BuilderNode is mounted to or unmounted from the component tree.
```

```TypeScript
### Example 8: Implementing Synchronization Relationship Changes When BuilderNode Is Mounted to Another Component Tree

> NOTE
> 
> Since API version 23, cross-BuilderNode pairing of @Provider and @Consumer is supported.

This example demonstrates how the synchronization relationship between @Consumer and @Provider changes when a BuilderNode is mounted to a different component tree.
```

```TypeScript
### Example 9: Implementing Synchronization Relationship Changes in Nested BuilderNode Scenarios

> NOTE
> 
> Since API version 23, cross-BuilderNode pairing of @Provider and @Consumer is supported.

This example demonstrates how the synchronization relationship between @Consumer and @Provider changes when BuilderNodes are nested.
```

```TypeScript
### Example 10: Understanding the Synchronization Relationship When @Consumer Components Have Child Components Under BuilderNode

> NOTE
> 
> Since API version 23, cross-BuilderNode pairing of @Provider and @Consumer is supported.

This example demonstrates the synchronization relationship between @Consumer and @Provider when the custom component containing @Consumer is located under BuilderNode and has child components.
```

```TypeScript
### Example 11: Understanding the Synchronization Relationship in the @Provider-@Consumer-BuilderNode-@Consumer Component Tree

> NOTE
> 
> Since API version 23, cross-BuilderNode pairing of @Provider and @Consumer is supported.

This example demonstrates the synchronization relationship between @Consumer and @Provider in a component tree structured as @Provider-@Consumer-BuilderNode-@Consumer.
```

```TypeScript
### Example 12: Understanding the Synchronization Relationship in the @Provider-BuilderNode-@Provider-@Consumer Component Tree

> NOTE
> 
> Since API version 23, cross-BuilderNode pairing of @Provider and @Consumer is supported.

This example demonstrates the synchronization relationship between @Consumer and @Provider in a component tree structured as @Provider-BuilderNode-@Provider-@Consumer.
```

```TypeScript
### Example 13: Handling Mouse Events in ReactiveBuilderNode

The functionality demonstrated in this example is supported starting from API version 22.

This example demonstrates the end-to-end process for intercepting mouse events in a custom component and performing coordinate conversion. The component reads the local X and Y coordinates through the [onMouse](../arkui-ts/ts-universal-mouse-key.md#onmouse) callback, calls [vp2px](./arkts-apis-uicontext-uicontext.md#vp2px12) to convert the relative coordinates to pixel coordinates based on the offset obtained by FrameNode.getPositionToParent(), and updates windowX, windowY, displayX, and displayY of [MouseEvent](../arkui-ts/ts-universal-mouse-key.md#mouseevent). Finally, the component uses rootNode.postInputEvent to post the converted mouse event to the child node for handling.


```

```TypeScript
### Example 14: Handling Touch Events in ReactiveBuilderNode

The functionality demonstrated in this example is supported starting from API version 22.

This example demonstrates the end-to-end process for intercepting touch events in a custom component and transforming touch point coordinates. In the [onTouch](../arkui-ts/ts-universal-events-touch.md#ontouch) callback, iterate through the changedTouches and touches arrays of [TouchEvent](../arkui-ts/ts-universal-events-touch.md#touchevent), add the component offset to the X and Y coordinates of each touch point, call [vp2px](./arkts-apis-uicontext-uicontext.md#vp2px12) to convert the coordinates to pixels, and update windowX/windowY and displayX/displayY. Finally, rootNode.postInputEvent is used to post the converted touch event to the child node for handling.


```

```TypeScript
### Example 15: Handling Axis Events in ReactiveBuilderNode

The functionality demonstrated in this example is supported starting from API version 22.

This example demonstrates the end-to-end process for intercepting wheel or trackpad axis events in a custom component and performing coordinate conversion. In the [onAxisEvent](../arkui-ts/ts-universal-events-axis.md#onaxisevent) callback, obtain the relative X and Y coordinates of the axis event, add the component offset, call [vp2px](./arkts-apis-uicontext-uicontext.md#vp2px12) to convert the coordinates to pixels, update the windowX/windowY and displayX/displayY of the axis event, and use rootNode.postInputEvent to post the converted axis event to the child node for handling.


```

```TypeScript
### Example 16: Handling Mouse Events with Competition Strategies in BuilderNode

The postInputEventWithStrategy API is added since API version 24.

This example demonstrates the end-to-end process for intercepting mouse events in a custom component and performing coordinate conversion. The component reads the current touch point coordinates (x/y) through the [onMouse](../arkui-ts/ts-universal-mouse-key.md#onmouse) callback, and calls [vp2px](./arkts-apis-uicontext-uicontext.md#vp2px12) to convert the relative coordinates to pixel coordinates based on the offset obtained from FrameNode.getPositionToParent. It then updates windowX, windowY, displayX, and displayY of [MouseEvent](../arkui-ts/ts-universal-mouse-key.md#mouseevent). The component selects a [gesture competition strategy](../arkui-ts/ts-appendix-enums.md#competitionstrategy24), and posts the converted mouse event to child nodes through rootNode.postInputEventWithStrategy for processing.
```

```TypeScript
### Example 17: Handling Touch Events with Competition Strategies in BuilderNode

The postInputEventWithStrategy API is added since API version 24.

This example demonstrates the end-to-end process for intercepting touch events in a custom component and transforming touch point coordinates. In the [onTouch](../arkui-ts/ts-universal-events-touch.md#ontouch) callback, traverse the changedTouches and touches arrays of [TouchEvent](../arkui-ts/ts-universal-events-touch.md#touchevent), add the component offset to the X and Y coordinates of each touch point, call [vp2px](./arkts-apis-uicontext-uicontext.md#vp2px12) to convert the coordinates to pixels, and update windowX, windowY, displayX, and displayY of each touch point. Select a [gesture competition strategy](../arkui-ts/ts-appendix-enums.md#competitionstrategy24), and post the converted touch event to child nodes through rootNode.postInputEventWithStrategy for processing.
```

```TypeScript
### Example 18: Handling Axis Events with Competition Strategies in BuilderNode

The postInputEventWithStrategy API is added since API version 24.

This example demonstrates the end-to-end process for intercepting wheel or trackpad axis events in a custom component and performing coordinate conversion. In the [onAxisEvent](../arkui-ts/ts-universal-events-axis.md#onaxisevent) callback, obtain the relative X and Y coordinates of the event, add the component offset to the coordinates, call [vp2px](./arkts-apis-uicontext-uicontext.md#vp2px12) to convert the coordinates to pixel coordinates, update windowX, windowY, displayX, and displayY of AxisEvent, select [a gesture competition strategy](../arkui-ts/ts-appendix-enums.md#competitionstrategy24), and use rootNode.postInputEventWithStrategy to post the converted axis event to child nodes for processing.
```
