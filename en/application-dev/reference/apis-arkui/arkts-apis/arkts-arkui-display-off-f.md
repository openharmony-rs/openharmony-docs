# off

## Modules to Import

```TypeScript
import { display } from '@kit.ArkUI';
```

## off('add' | 'remove' | 'change')

```TypeScript
function off(type: 'add' | 'remove' | 'change', callback?: Callback<number>): void
```

Unsubscribes from display changes.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'add' &#124; 'remove' &#124; 'change' | Yes | Event type.<br>- **add**, indicating the display addition event. Example: event that a display is connected.<br>- **remove**, indicating the display removal event. Example: event that a display is disconnected.<br>- **change**, indicating the display change event. Example: event that the display orientation is changed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | No | Callback used to return the ID of the display, which is an integer. If this parameter is not specified, all subscriptions to the specified event are canceled.<br>**Since:** 20 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Examples**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

// Unregister all the callbacks that have been registered through on().
display.off('remove');

let callback: Callback<number> = (data: number) => {
  console.info(`Succeeded in unregistering the callback for display remove. Data: ${data}`);
};
// Unregister the specified callback.
display.off('remove', callback);
```


## off('add' | 'remove' | 'change')

```TypeScript
function off(type: 'add' | 'remove' | 'change', callback?: Callback<number>): void
```

Unsubscribes from display changes.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'add' &#124; 'remove' &#124; 'change' | Yes | Event type.<br>- **add**, indicating the display addition event. Example: event that a display is connected.<br>- **remove**, indicating the display removal event. Example: event that a display is disconnected.<br>- **change**, indicating the display change event. Example: event that the display orientation is changed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | No | Callback used to return the ID of the display, which is an integer. If this parameter is not specified, all subscriptions to the specified event are canceled.<br>**Since:** 20 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Examples**

See off


## off('add' | 'remove' | 'change')

```TypeScript
function off(type: 'add' | 'remove' | 'change', callback?: Callback<number>): void
```

Unsubscribes from display changes.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'add' &#124; 'remove' &#124; 'change' | Yes | Event type.<br>- **add**, indicating the display addition event. Example: event that a display is connected.<br>- **remove**, indicating the display removal event. Example: event that a display is disconnected.<br>- **change**, indicating the display change event. Example: event that the display orientation is changed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | No | Callback used to return the ID of the display, which is an integer. If this parameter is not specified, all subscriptions to the specified event are canceled.<br>**Since:** 20 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Examples**

See off


## off('foldStatusChange')

```TypeScript
function off(type: 'foldStatusChange', callback?: Callback<FoldStatus>): void
```

Unsubscribes from fold status change events of the foldable device.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'foldStatusChange' | Yes | Event type. The event **'foldStatusChange'** is triggered when the fold status of the device changes. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[FoldStatus](arkts-arkui-display-foldstatus-e.md)&gt; | No | Callback used to return the fold status. If this parameter is not specified, all subscriptions to the specified event are canceled.<br>**Since:** 20 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [1400003](../errorcode-display.md#1400003-abnormal-display-manager-service) | This display manager service works abnormally. |

**Examples**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

// Unregister all the callbacks that have been registered through on().
display.off('foldStatusChange');

let callback: Callback<display.FoldStatus> = (data: display.FoldStatus) => {
  console.info(`unregistering FoldStatus changes callback. Data: ${data}`);
};
// Unregister the specified callback.
display.off('foldStatusChange', callback);
```


## off('foldAngleChange')

```TypeScript
function off(type: 'foldAngleChange', callback?: Callback<Array<number>>): void
```

Unsubscribes from folding angle change events of the foldable device.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'foldAngleChange' | Yes | Event type. The event **'foldAngleChange'** is triggered when the folding angle of the device changes. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;number&gt;&gt; | No | Callback used to return the folding angle (0�C180 degrees). If this parameter is not specified, all subscriptions to the specified event are canceled.<br>**Since:** 20 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [1400003](../errorcode-display.md#1400003-abnormal-display-manager-service) | This display manager service works abnormally. |

**Examples**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

// Unregister all the callbacks that have been registered through on().
display.off('foldAngleChange');

let callback: Callback<Array<number>> = (angles: Array<number>) => {
  console.info('Listening fold angles length: ' + angles.length);
};
// Unregister the specified callback.
display.off('foldAngleChange', callback);
```


## off('captureStatusChange')

```TypeScript
function off(type: 'captureStatusChange', callback?: Callback<boolean>): void
```

Unsubscribes from events indicating the status of the device's screen content is being captured.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'captureStatusChange' | Yes | Event type. The event **'captureStatusChange'** is triggered when the screen capture status changes. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | No | Callback used to return the result indicating whether the device's screen content is being captured. **true** is returned when screen content is being captured (including active screen capture, casting, recording, or the creation of a virtual screen that could be captured). **false** is returned when screen content is no longer being captured. In the case of screen capture, **true** is returned only once. If this parameter is not specified, all subscriptions to the specified event are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [1400003](../errorcode-display.md#1400003-abnormal-display-manager-service) | This display manager service works abnormally. |

**Examples**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

// Unregister all the callbacks that have been registered through on().
display.off('captureStatusChange');

let callback: Callback<boolean> = (captureStatus: boolean) => {
  console.info('Listening capture status: ' + captureStatus);
};
// Unregister the specified callback.
display.off('captureStatusChange', callback);
```


## off('foldDisplayModeChange')

```TypeScript
function off(type: 'foldDisplayModeChange', callback?: Callback<FoldDisplayMode>): void
```

Unsubscribes from display mode change events of the foldable device.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'foldDisplayModeChange' | Yes | Event type. The event **'foldDisplayModeChange'** is triggered when the display mode of the device changes. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[FoldDisplayMode](arkts-arkui-display-folddisplaymode-e.md)&gt; | No | Callback used to return the display mode. If this parameter is not specified, all subscriptions to the specified event are canceled.<br>**Since:** 20 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [1400003](../errorcode-display.md#1400003-abnormal-display-manager-service) | This display manager service works abnormally. |

**Examples**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

// Unregister all the callbacks that have been registered through on().
display.off('foldDisplayModeChange');

let callback: Callback<display.FoldDisplayMode> = (data: display.FoldDisplayMode) => {
  console.info(`unregistering FoldDisplayMode changes callback. Data: ${data}`);
};
// Unregister the specified callback.
display.off('foldDisplayModeChange', callback);
```


## off('brightnessInfoChange')

```TypeScript
function off(type: 'brightnessInfoChange', callback?: BrightnessCallback<number, BrightnessInfo>): void
```

Unsubscribes from events related to screen brightness information changes.

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'brightnessInfoChange' | Yes | Event type. The value is fixed at **'brightnessInfoChange'**, indicating that the screen brightness information is changed. |
| callback | [BrightnessCallback](arkts-arkui-display-brightnesscallback-t.md)&lt;number, [BrightnessInfo](arkts-arkui-display-brightnessinfo-i.md)&gt; | No | Callback used to return the display ID (parameter 1) and the corresponding screen brightness information (parameter 2). If this parameter is not specified, all subscriptions to the specified event are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [1400003](../errorcode-display.md#1400003-abnormal-display-manager-service) | This display manager service works abnormally. |
| [1400004](../errorcode-display.md#1400004-parameter-error) | Parameter error. Possible cause: 1. Invalid parameter range. |

**Examples**

```TypeScript
let callback: display.BrightnessCallback<number, display.BrightnessInfo> = (id: number, data: display.BrightnessInfo) => {
  console.info(`Listening enabled ${id}. Data: ${JSON.stringify(data)}`);
};
try {
  display.off('brightnessInfoChange', callback);
} catch (error) {
  console.error(`Failed to unregister brightnessInfoChange listener. Code: ${error.code}, message: ${error.message}`);
}
```
