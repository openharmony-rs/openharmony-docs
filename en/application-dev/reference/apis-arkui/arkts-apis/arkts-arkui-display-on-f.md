# on

## Modules to Import

```TypeScript
import { display } from '@kit.ArkUI';
```

## on('add' | 'remove' | 'change')

```TypeScript
function on(type: 'add' | 'remove' | 'change', callback: Callback<number>): void
```

Subscribes to display changes.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'add' &#124; 'remove' &#124; 'change' | Yes | Event type.<br>- **add**, indicating the display addition event. Example: event that a display is connected.<br>- **remove**, indicating the display removal event. Example: event that a display is disconnected.<br>- **change**, indicating the display change event. Example: event that the display orientation is changed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | Yes | Callback used to return the ID of the display, which is an integer. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |


## on('add' | 'remove' | 'change')

```TypeScript
function on(type: 'add' | 'remove' | 'change', callback: Callback<number>): void
```

Subscribes to display changes.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'add' &#124; 'remove' &#124; 'change' | Yes | Event type.<br>- **add**, indicating the display addition event. Example: event that a display is connected.<br>- **remove**, indicating the display removal event. Example: event that a display is disconnected.<br>- **change**, indicating the display change event. Example: event that the display orientation is changed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | Yes | Callback used to return the ID of the display, which is an integer. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |


## on('add' | 'remove' | 'change')

```TypeScript
function on(type: 'add' | 'remove' | 'change', callback: Callback<number>): void
```

Subscribes to display changes.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'add' &#124; 'remove' &#124; 'change' | Yes | Event type.<br>- **add**, indicating the display addition event. Example: event that a display is connected.<br>- **remove**, indicating the display removal event. Example: event that a display is disconnected.<br>- **change**, indicating the display change event. Example: event that the display orientation is changed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | Yes | Callback used to return the ID of the display, which is an integer. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |


## on('foldStatusChange')

```TypeScript
function on(type: 'foldStatusChange', callback: Callback<FoldStatus>): void
```

Subscribes to fold status change events of the foldable device.

To subscribe to display mode change events of foldable devices, use [display.on('foldDisplayModeChange')](#onfolddisplaymodechange).

The two are different. In terms of timing, the fold status changes first, and the bottom layer matches the display mode status based on the fold status.

To check whether the content is displayed on the inner or outer screen of the foldable device, use [display.on('foldDisplayModeChange')](#onfolddisplaymodechange).

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'foldStatusChange' | Yes | Event type. The event **'foldStatusChange'** is triggered when the fold status of the device changes. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[FoldStatus](arkts-arkui-display-foldstatus-e.md)&gt; | Yes | Callback used to return the fold status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [1400003](../errorcode-display.md#1400003-abnormal-display-manager-service) | This display manager service works abnormally. |


## on('foldAngleChange')

```TypeScript
function on(type: 'foldAngleChange', callback: Callback<Array<number>>): void
```

Subscribes to folding angle change events of the foldable device. Note that there are two folding angles for dual- fold axis devices. When oriented with the charging port at the bottom, the hinges are identified from right to left as the first and second fold axes, respectively.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'foldAngleChange' | Yes | Event type. The event **'foldAngleChange'** is triggered when the folding angle of the device changes. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;number&gt;&gt; | Yes | Callback used to return the folding angle (0�C180 degrees). For dual- fold axis devices, the array contains two angles. The first value represents the folding angle of the first fold axis, while the second value represents the folding angle of the second fold axis. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [1400003](../errorcode-display.md#1400003-abnormal-display-manager-service) | This display manager service works abnormally. |


## on('captureStatusChange')

```TypeScript
function on(type: 'captureStatusChange', callback: Callback<boolean>): void
```

Subscribes to events indicating the status of the device's screen content is being captured.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'captureStatusChange' | Yes | Event type. The event **'captureStatusChange'** is triggered when the screen capture status changes. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result indicating whether the device's screen content is being captured. **true** is returned when screen content is being captured (including active screen capture, casting, recording, or the creation of a virtual screen that could be captured). **false** is returned when screen content is no longer being captured. In the case of screen capture, **true** is returned only once. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [1400003](../errorcode-display.md#1400003-abnormal-display-manager-service) | This display manager service works abnormally. |


## on('foldDisplayModeChange')

```TypeScript
function on(type: 'foldDisplayModeChange', callback: Callback<FoldDisplayMode>): void
```

Subscribes to display mode change events of the foldable device.

To subscribe to fold status change events of foldable devices, use [display.on('foldStatusChange')](#onfoldstatuschange).

The two are different. In terms of timing, the fold status changes first, and the bottom layer matches the display mode status based on the fold status.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'foldDisplayModeChange' | Yes | Event type. The event **'foldDisplayModeChange'** is triggered when the display mode of the device changes. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[FoldDisplayMode](arkts-arkui-display-folddisplaymode-e.md)&gt; | Yes | Callback used to return the display mode. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [1400003](../errorcode-display.md#1400003-abnormal-display-manager-service) | This display manager service works abnormally. |


## on('brightnessInfoChange')

```TypeScript
function on(type: 'brightnessInfoChange', callback: BrightnessCallback<number, BrightnessInfo>): void
```

Subscribes to events related to screen brightness information changes. If the screen does not support HDR, the **currentHeadroom** and **maxHeadroom** fields in the [BrightnessInfo](arkts-arkui-display-brightnessinfo-i.md) object use the default values. For virtual screens, the **sdrNits** field in the BrightnessInfo object uses the default value.

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'brightnessInfoChange' | Yes | Event type. The value is fixed at **'brightnessInfoChange'**, indicating that the screen brightness information is changed. |
| callback | [BrightnessCallback](arkts-arkui-display-brightnesscallback-t.md)&lt;number, [BrightnessInfo](arkts-arkui-display-brightnessinfo-i.md)&gt; | Yes | Callback used to return the display ID (parameter 1) and the corresponding screen brightness information (parameter 2). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [1400003](../errorcode-display.md#1400003-abnormal-display-manager-service) | This display manager service works abnormally. |
| [1400004](../errorcode-display.md#1400004-parameter-error) | Parameter error. Possible cause: 1. Invalid parameter range. |
