# @ohos.UiTest

The **UiTest** module provides UI automation test capabilities, such as component search and operation, coordinate
 clicking/sliding, key injections, screenshot, window management, multi-finger operations, and mouse/stylus/touchpad
 operations.
 This module provides the following functions:

- [On<sup>9+</sup>](arkts-test-uitest-on-c.md): provides UI component feature description APIs for component filtering and matching.
 - [Component<sup>9+</sup>](arkts-test-uitest-component-c.md): represents a component on the UI and provides APIs for obtaining
 component attributes, clicking a component, scrolling to search for a component, and text injection.
 - [Driver<sup>9+</sup>](arkts-test-uitest-driver-c.md): works as the entry class and provides APIs for features such as component
 matching/search, key injection, coordinate clicking/sliding, and screenshot.
 - [UiWindow<sup>9+</sup>](arkts-test-uitest-uiwindow-c.md): represents a window object on the UI and provides APIs for obtaining window attributes,
 dragging windows, and adjusting window sizes.
 - [By<sup>(deprecated)</sup>](arkts-test-uitest-con.md#by): provides UI component feature description APIs for component filtering and
 matching. This API is supported since API version 8 and deprecated since API version 9.
 You are advised to use [On](arkts-test-uitest-on-c.md) instead.
 - [UiComponent<sup>(deprecated)</sup>](arkts-test-uitest-uicomponent-c.md): represents a component on the UI and provides APIs for
 obtaining component attributes, clicking a component, scrolling to search for a component, and text injection.
 This API is supported since API version 8 and deprecated since API version 9.
 You are advised to use [Component<sup>9+</sup>](arkts-test-uitest-component-c.md) instead.
 - [UiDriver<sup>(deprecated)</sup>](arkts-test-uitest-uidriver-c.md): works as the entry class and provides APIs for features such as
 component matching/search, key injection, coordinate clicking/sliding, and screenshot.
 This API is supported since API version 8 and deprecated since API version 9.
 You are advised to use [Driver<sup>9+</sup>](arkts-test-uitest-driver-c.md) instead.

> **NOTE**
 >
 > - The APIs of this module can be used only in [UITest](../../../application-test/uitest-guidelines.md).
 >
 > - The APIs of this module do not support concurrent calls.



## Modules to Import

```TypeScript
import { Component, DisplayRotation, Driver, MatchPattern, MouseButton, ON, On, PointerMatrix, ResizeDirection, UIElementInfo, UIEventObserver, UiDirection, UiWindow, WindowMode, Point, WindowFilter, Rect, TouchPadSwipeOptions, InputTextMode, WindowChangeType, ComponentEventType, WindowChangeOptions, ComponentEventOptions, TouchOptions, KeyOptions, PenKey, PenMode, PenKeyOperation, PenKeyOperationOptions } from '@kit.TestKit';
import { UiComponent, UiDriver, BY, By } from '@kit.TestKit';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [By](arkts-test-uitest-by-c.md) | The UiTest framework provides a wide range of UI component feature description APIs in the **By** class to filter and match components. |
| [Component](arkts-test-uitest-component-c.md) | Represents a component on the UI and provides APIs for obtaining component attributes, clicking a component, scrolling to search for a component, and text injection. All APIs provided in this class use a promise to return the result and must be invoked using **await**. |
| [Driver](arkts-test-uitest-driver-c.md) | The **Driver** class is the main entrance of the UiTest framework. This class provides APIs for features such as component matching/search, key injection, coordinate clicking/sliding, and screenshot. All APIs provided by this class, except **Driver.create()** and **Driver.createUIEventObserver()**, use an asynchronous method (promise) to return the result and must be invoked using **await**. |
| [On](arkts-test-uitest-on-c.md) | Since API version 9, the UiTest framework provides a wide range of UI component feature description APIs in the **On** class to filter and match components. |
| [PointerMatrix](arkts-test-uitest-pointermatrix-c.md) | Implements a **PointerMatrix** object that stores coordinates and behaviors of each action of each finger in a multi-touch operation. After creating an object using create, use [setPoint](arkts-test-uitest-pointermatrix-c.md#setpoint) to set the coordinates of each finger at each step. Then pass the coordinates to [injectMultiPointerAction](arkts-test-uitest-driver-c.md#injectmultipointeraction) to perform a multi-finger operation. |
| [UiComponent](arkts-test-uitest-uicomponent-c.md) | In **UiTest**, the **UiComponent** class represents a component on the UI and provides APIs for obtaining component attributes, clicking a component, scrolling to search for a component, and text injection. All APIs provided in this class use a promise to return the result and must be invoked using **await**. |
| [UiDriver](arkts-test-uitest-uidriver-c.md) | The **UiDriver** class is the main entry to the UiTest framework. It provides APIs for features such as component matching/search, key injection, coordinate clicking/sliding, and screenshot. All APIs provided by this class, except **UiDriver.create()**, use a promise to return the result and must be invoked using **await**. |
| [UiWindow](arkts-test-uitest-uiwindow-c.md) | The **UiWindow** class represents a window on the UI and provides APIs for obtaining window attributes, dragging a window, and adjusting the window size. All APIs provided in this class use a promise to return the result and must be invoked using **await**. |

### Interfaces

| Name | Description |
| --- | --- |
| [ComponentEventOptions](arkts-test-uitest-componenteventoptions-i.md) | Describes the extended configuration of component operation event listening, which is used to specify the listening process configuration and event filtering conditions. |
| [InputTextMode](arkts-test-uitest-inputtextmode-i.md) | Describes the text input mode. |
| [KeyOptions](arkts-test-uitest-keyoptions-i.md) | Represents the options for key operations. |
| [PenKeyOperationOptions](arkts-test-uitest-penkeyoperationoptions-i.md) | Pen key operation options. |
| [Point](arkts-test-uitest-point-i.md) | Represents the point on the device screen. |
| [Rect](arkts-test-uitest-rect-i.md) | Represents the rectangle area on the device screen. |
| [TouchOptions](arkts-test-uitest-touchoptions-i.md) | Common options for touch operations. |
| [TouchPadSwipeOptions](arkts-test-uitest-touchpadswipeoptions-i.md) | Describes information about the touchpad swipe gesture option. |
| [UIElementInfo](arkts-test-uitest-uielementinfo-i.md) | Provides information about the UI event. |
| [UIEventObserver](arkts-test-uitest-uieventobserver-i.md) | Defines a UI event listener, which is used to listen for various events on the UI, including the display of the **Toast** and **Dialog** components, window change event, and component operation event. An instance can be created using [createUIEventObserver](arkts-test-uitest-driver-c.md#createuieventobserver). |
| [WindowChangeOptions](arkts-test-uitest-windowchangeoptions-i.md) | Describes the extended configuration of window change event listening, which is used to specify the listening process configuration and event filtering conditions. |
| [WindowFilter](arkts-test-uitest-windowfilter-i.md) | Provides the flag attributes of this window. |

### Enums

| Name | Description |
| --- | --- |
| [ComponentEventType](arkts-test-uitest-componenteventtype-e.md) | Enumerates the component operation event types that can be listened for. |
| [DisplayRotation](arkts-test-uitest-displayrotation-e.md) | Describes the display rotation of the device. |
| [MatchPattern](arkts-test-uitest-matchpattern-e.md) | Enumerates the match patterns supported for component attributes. |
| [MouseButton](arkts-test-uitest-mousebutton-e.md) | Describes the injected simulated mouse button. |
| [PenKey](arkts-test-uitest-penkey-e.md) | Pen key type enum. |
| [PenKeyOperation](arkts-test-uitest-penkeyoperation-e.md) | Pen key operation type enum. |
| [PenMode](arkts-test-uitest-penmode-e.md) | Pen mode enum. |
| [ResizeDirection](arkts-test-uitest-resizedirection-e.md) | Enumerates the directions in which a window can be resized. |
| [UiDirection](arkts-test-uitest-uidirection-e.md) | Describes the direction of a UI operation such as fling. |
| [WindowChangeType](arkts-test-uitest-windowchangetype-e.md) | Enumerates the window change event types that can be listened for. |
| [WindowMode](arkts-test-uitest-windowmode-e.md) | Enumerates the window modes. |

### Constants

| Name | Description |
| --- | --- |
| [BY](arkts-test-uitest-con.md#by) | The static builder for building [By](arkts-test-uitest-by-c.md)object conveniently,usage example:BY.text('txt').enabled(true). |
| [ON](arkts-test-uitest-con.md#on) | The static builder for building [On](arkts-test-uitest-on-c.md)object conveniently,usage example:ON.text('txt').enabled(true). |
