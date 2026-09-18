# UIEventObserver

Defines a UI event listener, which is used to listen for various events on the UI, including the display of the **Toast** and **Dialog** components, window change event, and component operation event. An instance can be created using [createUIEventObserver](arkts-test-uitest-driver-c.md#createuieventobserver).

**Since:** 10

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

## Modules to Import

```TypeScript
import { Component, DisplayRotation, Driver, MatchPattern, MouseButton, ON, On, PointerMatrix, ResizeDirection, UIElementInfo, UIEventObserver, UiDirection, UiWindow, WindowMode, Point, WindowFilter, Rect, TouchPadSwipeOptions, InputTextMode, WindowChangeType, ComponentEventType, WindowChangeOptions, ComponentEventOptions, TouchOptions, KeyOptions, PenKey, PenMode, PenKeyOperation, PenKeyOperationOptions } from '@kit.TestKit';
import { UiComponent, UiDriver, BY, By } from '@kit.TestKit';
```

## once('toastShow')

```TypeScript
once(type: 'toastShow', callback: Callback<UIElementInfo>): void
```

Subscribes to events of the toast component. This API uses a callback to return the result.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'toastShow' | Yes | Event type. The value is fixed at **'toastShow'**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[UIElementInfo](arkts-test-uitest-uielementinfo-i.md)&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

## once('dialogShow')

```TypeScript
once(type: 'dialogShow', callback: Callback<UIElementInfo>): void
```

Subscribes to events of the dialog component. This API uses a callback to return the result.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'dialogShow' | Yes | Event type. The value is fixed at **'dialogShow'**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[UIElementInfo](arkts-test-uitest-uielementinfo-i.md)&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

## once('windowChange')

```TypeScript
once(type: 'windowChange', windowChangeType: WindowChangeType, options: WindowChangeOptions, callback: Callback<UIElementInfo>): void
```

Starts listening for window change events of the specified type with extended configuration supported. This API triggers a callback when a specified window change event is detected. This API can be used only in [free windows](../../../windowmanager/window-terminology.md#free-windows) mode.

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'windowChange' | Yes | Type of the event to subscribe to, which can be **windowChange**. This event is triggered when the window changes. |
| windowChangeType | [WindowChangeType](arkts-test-uitest-windowchangetype-e.md) | Yes | Type of the window change event. |
| options | [WindowChangeOptions](arkts-test-uitest-windowchangeoptions-i.md) | Yes | Extended configuration, including the listening timeout interval and the bundle name of the window to be listened for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[UIElementInfo](arkts-test-uitest-uielementinfo-i.md)&gt; | Yes | Callback triggered to return event information when an event occurs. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17000005](../errorcode-uitest.md#17000005-operation-not-supported) | This operation is not supported. |
| [17000007](../errorcode-uitest.md#17000007-parameters-are-invalid) | Parameter verification failed. |

## once('componentEventOccur')

```TypeScript
once(type: 'componentEventOccur', componentEventType: ComponentEventType, options: ComponentEventOptions, callback: Callback<UIElementInfo>): void
```

Starts listening for component operation events of the specified type with extended configuration supported. This API triggers a callback when a specified component operation event is detected.

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'componentEventOccur' | Yes | Type of the event to subscribe to, which can be **componentEventOccur**. This event is triggered when the component operation is detected. |
| componentEventType | [ComponentEventType](arkts-test-uitest-componenteventtype-e.md) | Yes | Type of the component operation event. |
| options | [ComponentEventOptions](arkts-test-uitest-componenteventoptions-i.md) | Yes | Extended configuration, including the listening timeout interval and the matching condition of the component to be listened for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[UIElementInfo](arkts-test-uitest-uielementinfo-i.md)&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17000005](../errorcode-uitest.md#17000005-operation-not-supported) | This operation is not supported. |
| [17000007](../errorcode-uitest.md#17000007-parameters-are-invalid) | Parameter verification failed. |
