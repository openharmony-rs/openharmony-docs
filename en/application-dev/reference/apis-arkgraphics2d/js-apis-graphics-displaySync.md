# @ohos.graphics.displaySync (Variable Frame Rate)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @wh_qwe-->
<!--Designer: @wh_qwe-->
<!--Tester: @zhaoxiaoguang2-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=ccdbec13380fdf227c4a20f5bde9cc05c16badee translatedAt=2026-08-24T09:23:48.263Z pushedAt=2026-08-31T12:04:21.610Z -->

Variable frame rate support allows developers to run UI services at a specified frame rate. It is generally used in scenarios where developers draw the UI themselves and have specific requirements for the frame rate. The system adjusts the drawing frequency based on the set expected frame rate, minimum frame rate, and maximum frame rate to meet the requirements of different scenarios.

> **NOTE**
>
> The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { displaySync } from '@kit.ArkGraphics2D';
```

## displaySync.create

create(): DisplaySync

Creates a **DisplaySync** object, through which you can set the frame rate of the custom UI content.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type               | Description                    |
| ------------------ | ------------------------ |
| [DisplaySync](#displaysync) | Returns a DisplaySync object instance, which is used to set the frame rate range, register the frame callback function, and control the start and stop of the callback. |

**Example**

```ts
// Create a DisplaySync object.
let backDisplaySync: displaySync.DisplaySync = displaySync.create();
```

## IntervalInfo

Developers can obtain the timestamp information of frame drawing from the callback function, including the timestamp when the current frame arrives and the targetTimestamp when the next frame is expected to arrive.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name            | Type                                     | Read-only| Optional| Description                                      |
| ---------------- | ----------------------------------------- | ---- | ---- | ------------------------------------------ |
| timestamp | number | No | No | Time when the current frame arrives (in nanoseconds). Monotonically increasing time since system startup. |
| targetTimestamp | number | No | No | Expected arrival time of the next frame (in nanoseconds). Monotonically increasing time since system startup. The value must be greater than timestamp. |

## DisplaySync

An instance for setting the expected frame rate and callback function. It is used to set the expected frame rate range, register the frame callback function, and start and stop the frame callback. Before calling any of the following APIs, you must use [displaySync.create()](#displaysynccreate) to create a DisplaySync instance and then call the corresponding method through this instance.

### setExpectedFrameRateRange

setExpectedFrameRateRange(rateRange: ExpectedFrameRateRange): void

Sets the expected frame rate range. The expected frame rate range is used as a reference for system scheduling, and the system tries to adjust the drawing frame rate within this range. If this API is not called or ExpectedFrameRateRange(0, 0, 0) is passed in, the current frame rate of the application is followed. It is recommended to set the range before calling [start](#start) so that it takes effect immediately. Setting the range after calling [start](#start) also takes effect, but there may be a delay.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name          | Type                                      | Mandatory| Description                         |
| --------------- | ------------------------------------------ | ---- | -----------------------------|
| rateRange | [ExpectedFrameRateRange](../apis-arkui/arkui-ts/ts-explicit-animation.md#expectedframeraterange11) | Yes | Sets the expected frame rate range of DisplaySync, which contains three fields: expected, min, and max, in frames per second (fps). The fields must be non-negative integers, with a value range of [0, the maximum frame rate of the device], and must satisfy min <= expected <= max. If the value is out of the valid range, error code 401 is thrown. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. Or check if ExpectedFrameRateRange is valid. |

**Example**

```ts
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

### on('frame')

on(type: 'frame', callback: Callback\<IntervalInfo\>): void

Subscribes to change events of each frame. After the callback function is registered, you must call [start](#start) to start the DisplaySync object; only then will the system trigger the callback on each frame. This API is used together with [off('frame')](#offframe) to unregister the callback function. The callback function is executed on the UI main thread. The callback frequency is affected by the frame rate range set by [setExpectedFrameRateRange](#setexpectedframeraterange). If the callback takes too long to execute, frame freezing may occur. It is recommended that only lightweight business logic be performed in the callback.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name          | Type                                      | Mandatory| Description                         |
| --------------- | ------------------------------------------ | ---- | -----------------------------|
| type | 'frame' | Yes | Type of the callback to set (only 'frame' is supported). |
| callback | Callback<[IntervalInfo](#intervalinfo)> | Yes | Callback function for subscribing to frame changes. [IntervalInfo](#intervalinfo) contains two attributes: timestamp (the arrival time of the current frame) and targetTimestamp (the expected arrival time of the next frame), both in nanoseconds. |

**Example**

```ts
// Define the callback function.
let callback = (frameInfo: displaySync.IntervalInfo) => {
    console.info("DisplaySync", 'TimeStamp:' + frameInfo.timestamp + ' TargetTimeStamp: ' + frameInfo.targetTimestamp);
}

// Register the callback function.
backDisplaySync?.on("frame", callback)

// Enable the callback function.
backDisplaySync?.start()
```

### off('frame')

off(type: 'frame', callback\?: Callback\<IntervalInfo\>): void

Unsubscribes from change events of each frame. This API is used together with [on('frame')](#onframe). After the unsubscription succeeds, the callback function will no longer be triggered.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name          | Type                                      | Mandatory| Description                         |
| --------------- | ------------------------------------------ | ---- | -----------------------------|
| type | 'frame' | Yes | Type of the callback to set (only 'frame' is supported). |
| callback | Callback<[IntervalInfo](#intervalinfo)> | No | Callback function registered when [on('frame')](#onframe) is called, used to unsubscribe from the callback function. It must be used after the callback has been registered through [on('frame')](#onframe). |

**Example**

```ts
// Define the callback function.
let callback = (frameInfo: displaySync.IntervalInfo) => {
    console.info("DisplaySync", 'TimeStamp:' + frameInfo.timestamp + ' TargetTimeStamp: ' + frameInfo.targetTimestamp);
}

// Register the callback function.
backDisplaySync?.on("frame", callback)

// Unregister the callback function.
backDisplaySync?.off("frame", callback)
```

### start

start(): void

Makes the expected frame rate range set by [setExpectedFrameRateRange](#setexpectedframeraterange) take effect. If a callback function is registered through [on('frame')](#onframe), this API starts requesting VSync signals and triggers the registered callback once per frame. This API is used together with [stop](#stop).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Example**

```ts
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

> **NOTE**
>
> The **start()** API associates the **DisplaySync** object with a UI context and window. If [start](#start) is called on a non-UI page or in an asynchronous callback, an incorrect UI context may be obtained, causing the [start](#start) function to work abnormally. As a result, the callback function cannot be executed and the expected frame rate range cannot take effect.
> In this case, you can use [runScopedTask](../apis-arkui/arkts-apis-uicontext-uicontext.md#runscopedtask) to specify the UI context and ensure that [start](#start) is executed in the correct context.

**Example**

```ts
import { displaySync } from '@kit.ArkGraphics2D';
import { UIContext } from '@kit.ArkUI';

// xxx.ets
@Entry
@Component
struct Index {
  // Create a DisplaySync instance.
  backDisplaySync: displaySync.DisplaySync = displaySync.create();

  aboutToAppear() {
    // Obtain a UIContext instance.
    let uiContext: UIContext = this.getUIContext();
    // Call start() in the current UI context.
    uiContext?.runScopedTask(() => {
      this.backDisplaySync?.start();
    })
  }

  build() {
    // ...
  }
}

```

### stop

stop(): void

Closes the expected frame rate range and stops the callback for each frame. This method must be called after [start](#start). After it is stopped, the DisplaySync configurations (such as the expected frame rate range and callback function) are retained and can be restarted at any time through [start](#start). The [stop](#stop) method disassociates DisplaySync from the UI context and window, and usually no specific UI context is required.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Example**

```ts
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