# on

## Modules to Import

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { AccessibilityEventType, AccessibilityAction, FocusMoveResultCode, InjectActionType, AccessibilityFocusScene, FocusRuleType, OperateVirtualNodeResult, AccessibilitySourceType } from '@kit.AccessibilityKit';
```

## on('accessibilityStateChange')

```TypeScript
function on(type: 'accessibilityStateChange', callback: Callback<boolean>): void
```

Subscribes to the state changes of the accessibility application. This API uses an asynchronous callback to return the result.

To obtain information about accessibility applications in the system, you are advised to use [accessibility.getAccessibilityExtensionListSync](arkts-accessibility-accessibility-getaccessibilityextensionlistsync-f.md).

> **NOTE:** 
> 
> - The callback parameter for registering a listener must use a named function instead of an anonymous function.Otherwise, a new underlying object is created each time the function is called, causing memory leakage.
> 
> - After calling this method, ensure that [accessibility.off('accessibilityStateChange')](arkts-accessibility-accessibility-off-f.md#offaccessibilitystatechange)is used to unsubscribe before the component instance is destroyed (for example, in the **aboutToDisappear**lifecycle callback). Otherwise, a crash may occur.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'accessibilityStateChange' | Yes | Event type, which is set to **'accessibilityStateChange'** in this API. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. When the accessibility app enabled state changes, the state is notified through this callback. This state is the global accessibility app enabled state. The value **true** indicates that the accessibility app is enabled, and **false** indicates that the accessibility app is disabled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |


## on('touchGuideStateChange')

```TypeScript
function on(type: 'touchGuideStateChange', callback: Callback<boolean>): void
```

Subscribes to the state changes of touch guide mode. This API uses an asynchronous callback to return the result.

To obtain information about accessibility applications in the system, you are advised to use [accessibility.getAccessibilityExtensionListSync](arkts-accessibility-accessibility-getaccessibilityextensionlistsync-f.md).

> **NOTE:** 
> 
> - The callback parameter for registering a listener must use a named function instead of an anonymous function.Otherwise, a new underlying object is created each time the function is called, causing memory leakage.
> 
> - After calling this method, ensure that [accessibility.off('touchGuideStateChange')](arkts-accessibility-accessibility-off-f.md#offtouchguidestatechange)is used to unsubscribe before the component instance is destroyed (for example, in the **aboutToDisappear**lifecycle callback). Otherwise, a crash may occur.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Vision

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'touchGuideStateChange' | Yes | Event type, which is set to **'touchGuideStateChange'** in this API. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | Yes | Callback invoked when the touch browsing enabled state changes. The value **true** indicates that the touch browsing feature is enabled, and **false** indicates that the touch browsing feature is disabled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |


## on('screenReaderStateChange')

```TypeScript
function on(type: 'screenReaderStateChange', callback: Callback<boolean>): void
```

Subscribes to the state changes of screen reader mode. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> - The callback parameter for registering a listener must use a named function instead of an anonymous function.Otherwise, a new underlying object is created each time the function is called, causing memory leakage.
> 
> - After calling this method, ensure that [accessibility.off('screenReaderStateChange')](arkts-accessibility-accessibility-off-f.md#offscreenreaderstatechange)is used to unsubscribe before the component instance is destroyed (for example, in the **aboutToDisappear**lifecycle callback). Otherwise, a crash may occur.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'screenReaderStateChange' | Yes | Event type, which is set to **'screenReaderStateChange'** in this API. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** indicates that the screen reader function is enabled, and **false** indicates that the screen reader function is disabled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |


## on('touchModeChange')

```TypeScript
function on(type: 'touchModeChange', callback: Callback<string>): void
```

Subscribes to the single-tap/double-tap operation mode change event in touch guide mode. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> - The callback parameter for registering a listener must use a named function instead of an anonymous function.Otherwise, a new underlying object is created each time the function is called, causing memory leakage.
> 
> - After calling this method, ensure that [accessibility.off('touchModeChange')](arkts-accessibility-accessibility-off-f.md#offtouchmodechange)is used to unsubscribe before the component instance is destroyed (for example, in the **aboutToDisappear**lifecycle callback). Otherwise, a crash may occur.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'touchModeChange' | Yes | Event type, which is set to **'touchModeChange'** in this API. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;string&gt; | Yes | Callback invoked when the single-tap/double-tap operation mode changes in touch browsing mode. The value 'singleTouchMode' indicates single-tap operation mode, 'doubleTouchMode'indicates double-tap operation mode, and 'none' indicates that touch browsing is not enabled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
