# DisplaySync

An object that implements the setting of the frame rate and callback. It provides APIs for you to set the frame rate, register a callback, and start/stop the callback. Before calling any of the following APIs, you must use [displaySync.create()](arkts-arkgraphics2d-displaysync-create-f.md) to create a **DisplaySync** instance.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { displaySync } from '@kit.ArkGraphics2D';
```

## off('frame')

```TypeScript
off(type: 'frame', callback?: Callback<IntervalInfo>): void
```

Unsubscribes from change events of each frame.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'frame' | Yes | Event type. The value is fixed at **'frame'**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[IntervalInfo](arkts-arkgraphics2d-displaysync-intervalinfo-i.md)&gt; | No | Callback used for unsubscription. If no value is passed in, all subscriptions to the specified event are canceled. |

## on('frame')

```TypeScript
on(type: 'frame', callback: Callback<IntervalInfo>): void
```

Subscribes to change events of each frame.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'frame' | Yes | Event type. The value is fixed at **'frame'**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[IntervalInfo](arkts-arkgraphics2d-displaysync-intervalinfo-i.md)&gt; | Yes | Callback used for subscription. |

## setExpectedFrameRateRange

```TypeScript
setExpectedFrameRateRange(rateRange: ExpectedFrameRateRange) : void
```

Sets the expected frame rate range.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rateRange | ExpectedFrameRateRange | Yes | Expected frame rate range. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. or check if ExpectedFrameRateRange is valid. |

**Examples**

```TypeScript
// Define the expected frame rate range.
let range: ExpectedFrameRateRange = {
  expected: 10, // Expected frame rate
  min: 0, // Minimum frame rate
  max: 120 // Maximum frame rate
};

// Set the expected frame rate range for DisplaySync.
backDisplaySync?.setExpectedFrameRateRange(range)

// Apply the expected frame rate range.
backDisplaySync?.start()
```

## start

```TypeScript
start(): void
```

Starts callback for each frame.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

```TypeScript
// Define the expected frame rate range.
let range: ExpectedFrameRateRange = {
  expected: 10, // expected frame rate
  min: 0, // minimum frame rate
  max: 120 // maximum frame rate
};
// Set the expected frame rate range of DisplaySync.
backDisplaySync?.setExpectedFrameRateRange(range)

// Define the callback function.
let callback = (frameInfo: displaySync.IntervalInfo) => {
    console.info("DisplaySync", 'TimeStamp:' + frameInfo.timestamp + ' TargetTimeStamp: ' + frameInfo.targetTimestamp);
}

// Register the callback function.
backDisplaySync?.on("frame", callback)

// Apply the expected frame rate range and start the per-frame callback.
backDisplaySync?.start()
```

```TypeScript
> NOTE
> 
> The start() API associates the DisplaySync object with a UI context and window. If [start](#start) is called on a non-UI page or in an asynchronous callback, an incorrect UI context may be obtained, causing the [start](#start) function to work abnormally. As a result, the callback function cannot be executed and the expected frame rate range cannot take effect.In this case, you can use [runScopedTask](../apis-arkui/arkts-apis-uicontext-uicontext.md#runscopedtask) to specify the UI context and ensure that [start](#start) is executed in the correct context.
```

## stop

```TypeScript
stop(): void
```

Stops callback for each frame.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

```TypeScript
// Define the expected frame rate range.
let range: ExpectedFrameRateRange = {
  expected: 10, // Expected frame rate.
  min: 0, // Minimum frame rate.
  max: 120 // Maximum frame rate.
};

// Set the expected frame rate range of DisplaySync.
backDisplaySync?.setExpectedFrameRateRange(range)

// Define the callback function.
let callback = (frameInfo: displaySync.IntervalInfo) => {
    console.info("DisplaySync", 'TimeStamp:' + frameInfo.timestamp + ' TargetTimeStamp: ' + frameInfo.targetTimestamp);
}

// Register the callback function.
backDisplaySync?.on("frame", callback)

// Apply the expected frame rate range and start the per-frame callback.
backDisplaySync?.start()

// ...

// Stop applying the expected frame rate range and stop the per-frame callback.
backDisplaySync?.stop()
```
