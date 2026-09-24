# ScreenCaptureMonitor (System API)

```TypeScript
interface ScreenCaptureMonitor
```

A class that provides APIs to query and monitor the system screen recorder status. Before calling any API, you must use getScreenCaptureMonitor() to obtain a ScreenCaptureMonitor instance.

**Since:** 18

**System capability:** SystemCapability.Multimedia.Media.AVScreenCapture

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## off('systemScreenRecorder')

```TypeScript
off(type: 'systemScreenRecorder', callback?: Callback<ScreenCaptureEvent>): void
```

Unsubscribes from state change events of the system screen recorder.

**Since:** 18

**System capability:** SystemCapability.Multimedia.Media.AVScreenCapture

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'systemScreenRecorder' | Yes | Event type, which is **'systemScreenRecorder'** in this case. This event is triggered when the state of the system screen recorder changes. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ScreenCaptureEvent](arkts-media-media-screencaptureevent-e-sys.md)&gt; | No | Callback invoked when the event is triggered, where ScreenCaptureEvent indicates the new state. If this parameter is not specified, the last subscription event is canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System App. |

## on('systemScreenRecorder')

```TypeScript
on(type: 'systemScreenRecorder', callback: Callback<ScreenCaptureEvent>): void
```

Subscribes to state change events of the system screen recorder. From the ScreenCaptureEvent event reported, you can determine whether the system screen recorder is working.

**Since:** 18

**System capability:** SystemCapability.Multimedia.Media.AVScreenCapture

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'systemScreenRecorder' | Yes | Event type, which is **'systemScreenRecorder'** in this case. This event is triggered when the state of the system screen recorder changes. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ScreenCaptureEvent](arkts-media-media-screencaptureevent-e-sys.md)&gt; | Yes | Callback invoked when the event is triggered, where ScreenCaptureEvent indicates the new state. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System App. |

**Examples**

```TypeScript
// This event is reported when the state of the system screen recorder changes.
screenCaptureMonitor.on('systemScreenRecorder', (event: media.ScreenCaptureEvent) => { 
  // Set the 'systemScreenRecorder' event callback.
  console.info(`system ScreenRecorder event: ${event}`);
})
```

## isSystemScreenRecorderWorking

```TypeScript
readonly isSystemScreenRecorderWorking: boolean
```

Whether the system screen recorder is working.

**Type:** boolean

**Since:** 18

**System capability:** SystemCapability.Multimedia.Media.AVScreenCapture

**System API:** This is a system API.
