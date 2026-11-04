# @ohos.distributedHardware.mechanicManager (Mechanic Manager) (System API)
<!--Kit: Mechanic Kit-->
<!--Subsystem: Mechanic-->
<!--Owner: @qxqxqxqxqx-->
<!--Designer: @peter__1024-->
<!--Tester: @Aullar-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=7a7787dea69325544e583e433b8d199ef2b91839 translatedAt=2026-11-04T02:14:10.958Z pushedAt=2026-11-04T03:24:28.563Z nl=1 -->

The **mechanicManager** module provides the mechanic device interaction capabilities, such as connection management, device control, and monitoring.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 20. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - This topic describes only the system APIs provided by the module. For details about its public APIs, see [@ohos.distributedHardware.mechanicManager (Mechanic Manager)](js-apis-mechanicManager.md).

## Modules to Import

```js
import { mechanicManager } from '@kit.MechanicKit';
```

## mechanicManager.setUserOperation

setUserOperation(operation: Operation, mac: string, params: string): void

Sets the the user operation, such as connection or disconnection.

**Required permissions**: ohos.permission.CONNECT_MECHANIC_HARDWARE

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

**Parameters**

| Name    | Type                   | Mandatory| Description  |
| ---------- | ---------------------- | ---- | ----- |
| operation | [Operation](#operation) | Yes| Operation type.|
| mac | string | Yes| MAC address of the mechanic device.|
| params | string | Yes| Operation parameters.|

**Error codes**

For details about the error codes, see [Mechanic Manager Error Codes](errorcode-mechanic.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | ------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 33300001 | Service exception. |

**Example**

```ts
console.info('User operate');
mechanicManager.setUserOperation(mechanicManager.Operation.CONNECT, "58:51:9e:e7:79:6d", "operatingParams");
console.info('User operation was successful');
```

## mechanicManager.setCameraTrackingLayout

setCameraTrackingLayout(trackingLayout: CameraTrackingLayout): void

Sets the camera tracking layout of the current mechanic device.

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

**Parameters**

| Name    | Type                   | Mandatory| Description  |
| ---------- | ---------------------- | ---- | ----- |
| trackingLayout | [CameraTrackingLayout](js-apis-mechanicManager.md#cameratrackinglayout) | Yes| Camera tracking layout.|

**Error codes**

For details about the error codes, see [Mechanic Manager Error Codes](errorcode-mechanic.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ----------------- |
| 202 | Not system application. |
| 33300001 | Service exception. |
| 33300002 | Device not connected. |
| 33300003 | Feature not supported. |

**Example**

```ts
console.info('Set layout');
mechanicManager.setCameraTrackingLayout(mechanicManager.CameraTrackingLayout.LEFT);
console.info('Set layout successful');
```

## mechanicManager.rotate

rotate(mechId: number, angles: RotationAngles, duration: number): Promise\<Result>

Rotates a mechanic device to the relative angles. This API uses a promise to return the result.

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

**Parameters**

| Name    | Type                   | Mandatory| Description  |
| ---------- | ---------------------- | ---- | ----- |
| mechId | number | Yes| ID of the mechanic device.|
| angles | [RotationAngles](#rotationangles) | Yes| Rotation angle relative to the current position.|
| duration | number | Yes| Rotation duration, in milliseconds.|

**Return value**

| Type                                       | Description       |
| ------------------------------------------- | --------- |
| Promise\<[Result](#result)> | Promise used to return the rotation result.|

**Error codes**

For details about the error codes, see [Mechanic Manager Error Codes](errorcode-mechanic.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ----------------- |
| 202 | Not system application. |
| 33300001 | Service exception. |
| 33300002 | Device not connected. |

**Example**

```ts
console.info('Start rotate');
let degree: mechanicManager.RotationAngles = {
  yaw: 0.1 * Math.PI,
  roll: 0.0,
  pitch: 0.0
}
mechanicManager.rotate(0, degree, 500)
  .then((result: mechanicManager.Result) => {
    console.info(`'Rotate result:' ${result}`);
  });
console.info('End rotation');
```

## mechanicManager.rotateToEulerAngles

rotateToEulerAngles(mechId: number, angles: EulerAngles, duration: number): Promise\<Result>

Rotates a mechanic device to the absolute angles. This API uses a promise to return the result.

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

**Parameters**

| Name    | Type                   | Mandatory| Description  |
| ---------- | ---------------------- | ---- | ----- |
| mechId | number | Yes| ID of the mechanic device.|
| angles | [EulerAngles](#eulerangles) | Yes| Absolute angle.|
| duration | number | Yes| Rotation duration, in milliseconds.|

**Return value**

| Type                                       | Description       |
| ------------------------------------------- | --------- |
| Promise\<[Result](#result)> | Promise used to return the rotation result.|

**Error codes**

For details about the error codes, see [Mechanic Manager Error Codes](errorcode-mechanic.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ----------------- |
| 202 | Not system application. |
| 33300001 | Service exception. |
| 33300002 | Device not connected. |

**Example**

```ts
let degree: mechanicManager.EulerAngles = {
  yaw: 0.9 * Math.PI,
  roll: 0.9 * Math.PI,
  pitch: 0.9 * Math.PI
}
mechanicManager.rotateToEulerAngles(0, degree, 500)
  .then((result: mechanicManager.Result) => {
    console.info(`'Rotate result:' ${result}`);
  });
console.info('End rotation');
```

## mechanicManager.getMaxRotationTime

getMaxRotationTime(mechId: number): number

Obtains the maximum duration for continuous rotation of a mechanic device.

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

**Parameters**

| Name    | Type                   | Mandatory| Description  |
| ---------- | ---------------------- | ---- | ----- |
| mechId | number | Yes| ID of the mechanic device.|

**Return value**

| Type                                       | Description       |
| ------------------------------------------- | --------- |
| number | Maximum rotation duration, in milliseconds.|

**Error codes**

For details about the error codes, see [Mechanic Manager Error Codes](errorcode-mechanic.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message |
| -------- | -------- |
| 202 | Not system application. |
| 33300001 | Service exception. |
| 33300002 | Device not connected. |

**Example**

```ts
console.info('Query maximum rotation time');
let maxTime = mechanicManager.getMaxRotationTime(0);
console.info(`'Query maximum rotation time successful, maximum time:' ${maxTime}`);
```

## mechanicManager.getMaxRotationSpeed

getMaxRotationSpeed(mechId: number): RotationSpeed

Obtains the maximum rotation speed of a mechanic device.

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

**Parameters**

| Name    | Type                   | Mandatory| Description  |
| ---------- | ---------------------- | ---- | ----- |
| mechId | number | Yes| ID of the mechanic device.|

**Return value**

| Type                                       | Description       |
| ------------------------------------------- | --------- |
| [RotationSpeed](#rotationspeed) | Maximum rotation speed (absolute value).|

**Error codes**

For details about the error codes, see [Mechanic Manager Error Codes](errorcode-mechanic.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ----------------- |
| 202 | Not system application. |
| 33300001 | Service exception. |
| 33300002 | Device not connected. |

**Example**

```ts
console.info('Query rotation speed');
let speedLimit: mechanicManager.RotationSpeed = mechanicManager.getMaxRotationSpeed(0);
console.info(`'Query rotation speed successful, speed limit information:' ${speedLimit}`);
```

## mechanicManager.rotateBySpeed

rotateBySpeed(mechId: number, speed: RotationSpeed, duration: number): Promise\<Result>

Rotates the current body at the specified speed. This API uses a promise to return the result.

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

**Parameters**

| Name    | Type                   | Mandatory| Description  |
| ---------- | ---------------------- | ---- | ----- |
| mechId | number | Yes| ID of the mechanic device.|
| speed | [RotationSpeed](#rotationspeed) | Yes| Specified rotation speed. If the specified value is greater than the value returned by **getMaxRotationSpeed**, the value returned by **getMaxRotationSpeed** is used by default.|
| duration | number | Yes| Rotation duration, in milliseconds. If the specified value is greater than the value returned by **getMaxRotationTime**, the value returned by **getMaxRotationTime** is used by default.|

**Return value**

| Type                                       | Description       |
| ------------------------------------------- | --------- |
| Promise\<[Result](#result)> | Promise used to return the rotation result.|

**Error codes**

For details about the error codes, see [Mechanic Manager Error Codes](errorcode-mechanic.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ----------------- |
| 202 | Not system application. |
| 33300001 | Service exception. |
| 33300002 | Device not connected. |

**Example**

```ts
console.info('Start rotate');
let degree: mechanicManager.RotationSpeed = {
  yawSpeed: 3 * Math.PI,
  rollSpeed: 3 * Math.PI,
  pitchSpeed: 3 * Math.PI
}
mechanicManager.rotateBySpeed(0, degree, 500)
  .then((result) => {
    console.info(`'Rotate result:' ${result}`);
  });
console.info('Rotate finish');
```

## mechanicManager.stopMoving

stopMoving(mechId: number): Promise\<void>

Stops movement of a mechanic device. This API uses a promise to return the result.

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

**Parameters**

| Name    | Type                   | Mandatory| Description  |
| ---------- | ---------------------- | ---- | ----- |
| mechId | number | Yes| ID of the mechanic device.|

**Return value**

| Type                                       | Description       |
| ------------------------------------------- | --------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Mechanic Manager Error Codes](errorcode-mechanic.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ----------------- |
| 202 | Not system application. |
| 33300001 | Service exception. |
| 33300002 | Device not connected. |

**Example**

```ts
console.info('Stop moving');
mechanicManager.stopMoving(0)
  .then(() => {
    console.info('Get stop complete');
  });
console.info('Stop succeeded');
```

## mechanicManager.getCurrentAngles

getCurrentAngles(mechId: number): EulerAngles

Obtains the current rotation angle of a mechanic device relative to the initial position.

> **NOTE**
>
> The coordinates of the initial position are (0, 0, 0).

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

**Parameters**

| Name    | Type                   | Mandatory| Description  |
| ---------- | ---------------------- | ---- | ----- |
| mechId | number | Yes| ID of the mechanic device.|

**Return value**

| Type                                       | Description       |
| ------------------------------------------- | --------- |
| [EulerAngles](#eulerangles) | Current rotation angle of the mechanic device.|

**Error codes**

For details about the error codes, see [Mechanic Manager Error Codes](errorcode-mechanic.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ----------------- |
| 202 | Not system application. |
| 33300001 | Service exception. |
| 33300002 | Device not connected. |

**Example**

```ts
console.info('Query current location');
let currentAngles: mechanicManager.EulerAngles = mechanicManager.getCurrentAngles(0);
console.info(`'Query current location, location:' ${currentAngles}`);
```

## mechanicManager.getRotationLimits

getRotationLimits(mechId: number): RotationLimits

Obtains the maximum rotation angle of a mechanic device relative to the initial position.

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

**Parameters**

| Name    | Type                   | Mandatory| Description  |
| ---------- | ---------------------- | ---- | ----- |
| mechId | number | Yes| ID of the mechanic device.|

**Return value**

| Type                                       | Description       |
| ------------------------------------------- | --------- |
| [RotationLimits](#rotationlimits) | Maximum rotation angle.|

**Error codes**

For details about the error codes, see [Mechanic Manager Error Codes](errorcode-mechanic.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ----------------- |
| 202 | Not system application. |
| 33300001 | Service exception. |
| 33300002 | Device not connected. |

**Example**

```ts
console.info('Query rotation limit information');
let degreeLimit: mechanicManager.RotationLimits = mechanicManager.getRotationLimits(0);
console.info(`'Query the rotation limit information successfully, limit information:' ${degreeLimit}`);
```

## mechanicManager.on('rotationAxesStatusChange')

on(type: 'rotationAxesStatusChange', callback: Callback\<RotationAxesStateChangeInfo>): void

Registers a callback listener for rotation axis state change events. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

**Parameters**

| Name    | Type                   | Mandatory| Description  |
| ---------- | ---------------------- | ---- | ----- |
| type | 'rotationAxesStatusChange' | Yes| Event type. The value **rotationAxesStatusChange** indicates a rotation axis state change.|
| callback | Callback\<[RotationAxesStateChangeInfo](#rotationaxesstatechangeinfo)> | Yes| Callback used to return the rotation axis state change.|

**Error codes**

For details about the error codes, see [Mechanic Manager Error Codes](errorcode-mechanic.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ----------------- |
| 202 | Not system application. |
| 33300001 | Service exception. |

**Example**

```ts
console.info('Register Axis Status listener');
mechanicManager.on("rotationAxesStatusChange", (result: mechanicManager.RotationAxesStateChangeInfo) => {
  console.info(`'result:' ${result}`);
});
console.info('Successful registration');
```

## mechanicManager.off('rotationAxesStatusChange')

off(type: 'rotationAxesStatusChange', callback?: Callback\<RotationAxesStateChangeInfo>): void

Unregisters the callback listener for rotation axis state changes. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

**Parameters**

| Name    | Type                   | Mandatory| Description  |
| ---------- | ---------------------- | ---- | ----- |
| type | 'rotationAxesStatusChange' | Yes| Event type. The value **rotationAxesStatusChange** indicates a rotation axis state change.|
| callback | Callback\<[RotationAxesStateChangeInfo](#rotationaxesstatechangeinfo)> | No|  Callback to unregister. If this parameter is not specified, all callbacks for the specified type of events are unregistered.|

**Error codes**

For details about the error codes, see [Mechanic Manager Error Codes](errorcode-mechanic.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ----------------- |
| 202 | Not system application. |
| 33300001 | Service exception. |

**Example**

```ts
console.info('Unregister Axis Status listener');
mechanicManager.off("rotationAxesStatusChange", (result: mechanicManager.RotationAxesStateChangeInfo) => {
  console.info(`'result:' ${result}`);
});
console.info('Unregister successfully');
```

## mechanicManager.getRotationAxesStatus

getRotationAxesStatus(mechId: number): RotationAxesStatus

Obtains the rotation axis status of the current mechanic device.

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

**Parameters**

| Name    | Type                   | Mandatory| Description  |
| ---------- | ---------------------- | ---- | ----- |
| mechId | number | Yes| ID of the mechanic device.|

**Return value**

| Type                                       | Description       |
| ------------------------------------------- | --------- |
| [RotationAxesStatus](#rotationaxesstatus) | Rotation axis status.|

**Error codes**

For details about the error codes, see [Mechanic Manager Error Codes](errorcode-mechanic.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ----------------- |
| 202 | Not system application. |
| 33300001 | Service exception. |
| 33300002 | Device not connected. |

**Example**

```ts
console.info('Query the rotation axis status');
let axisStatus: mechanicManager.RotationAxesStatus = mechanicManager.getRotationAxesStatus(0);
console.info(`'Query the rotation axis status successfully, axis state:' ${axisStatus}`);
```

## mechanicManager.searchTarget<sup>21+</sup>
searchTarget(target: TargetInfo, params: SearchParams): Promise\<SearchResult>

Rotates the mechanical body 360 degrees to search for the target. This API uses a promise to return the result.

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

**Parameters**
| Name    | Type                   | Mandatory| Description  |
| ---------- | ---------------------- | ---- | ----- |
| target | [TargetType](#targettype21) | Yes| Target face information.|
| params | [SearchParams](#searchparams21) | Yes| Search direction.|

**Return value**

| Type                                       | Description       |
| ------------------------------------------- | --------- |
| Promise\<[SearchResult](#searchresult21)> | Promise used to return the search result.|

**Error codes**

For details about the error codes, see [Mechanic Manager Error Codes](errorcode-mechanic.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ----------------- |
| 202 | Not system application. |
| 33300001 | Service exception. |
| 33300002 | Device not connected. |
| 33300003 | Feature not supported. |
| 33300004 | Camera not opened. |

**Example**

```ts
let targetInfo: mechanicManager.TargetInfo = {
    targetType: mechanicManager.TargetType.HUMAN_FACE
};
let searchParams: mechanicManager.SearchParams = {
    direction: mechanicManager.SearchDirection.DEFAULT
}
mechanicManager.searchTarget(targetInfo,
    searchParams).then((searchResult) => {
    console.info(`'result:' ${searchResult}`);
});
```

## mechanicManager.move

move(mechId: number, params: MoveParams): Promise&lt;Result&gt;

Moves a mechanic device with the specified parameters.
  
**Since:** 26.0.0

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

**Parameters**

| Name     | Type                    | Mandatory | Description   |
| ---------- | ---------------------- | ---- | ----- |
| mechId | number | Yes | ID of the mechanic device. |
| params | [MoveParams](#moveparams) | Yes | Movement parameters. |

**Return value**

| Type                                        | Description        |
| ------------------------------------------- | --------- |
| Promise&lt;[Result](#result)&gt; | Promise used to return the movement execution result. |

**Error codes**

For details about the error codes, see [Mechanic Manager Error Codes](errorcode-mechanic.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message           |
| -------- | ----------------- |
| 202 | Not system application. |
| 33300001 | Service exception. |
| 33300002 | Device not connected. |
| 33300003 | Feature not supported. |

**Example**

```ts
let mechId: number = 0;
let moveParams: mechanicManager.MoveParams = {
    distance: 0,
    angle: 0,
    speedGear: undefined,
    mode: undefined
};
try {
  mechanicManager.move(mechId, moveParams).then((result: mechanicManager.Result) => {
    console.info(`'result:' ${result}`);
  });
} catch (e) {
  console.error(`Code is ${e.code}, message is ${e.message}`);
}
```

## mechanicManager.moveBySpeed

moveBySpeed(mechId: number, params: SpeedParams, duration: number): Promise&lt;Result&gt;

Moves a mechanic device at a specific speed.

**Since:** 26.0.0

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

**Parameters**

| Name     | Type                    | Mandatory | Description   |
| ---------- | ---------------------- | ---- | ----- |
| mechId | number | Yes | ID of the mechanic device. |
| params | [SpeedParams](#speedparams) | Yes | Movement parameters. |
| duration | number | Yes | Movement duration, in ms. |

**Return value**

| Type                                        | Description        |
| ------------------------------------------- | --------- |
| Promise&lt;[Result](#result)&gt;| Promise used to return the movement execution result. |

**Error codes**

For details about the error codes, see [Mechanic Manager Error Codes](errorcode-mechanic.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message           |
| -------- | ----------------- |
| 202 | Not system application. |
| 33300001 | Service exception. |
| 33300002 | Device not connected. |
| 33300003 | Feature not supported. |

**Example**

```ts
let mechId: number = 0;
let speedParams: mechanicManager.SpeedParams = {
    speed: 0,
    angle: 0,
    mode: undefined
};
let duration: number = 1;
try {
  mechanicManager.moveBySpeed(mechId, speedParams, duration).then((result: mechanicManager.Result) => {
    console.info(`'result:' ${result}`);
  });
} catch (e) {
  console.error(`Code is ${e.code}, message is ${e.message}`);
}
```

## mechanicManager.turnBySpeed

turnBySpeed(mechId: number, angleSpeed: number, duration: number): Promise&lt;Result&gt;

Rotates in place at a fixed speed.

**Since:** 26.0.0

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

**Parameters**

| Name     | Type                    | Mandatory | Description   |
| ---------- | ---------------------- | ---- | ----- |
| mechId | number | Yes | ID of the mechanic device. |
| angleSpeed | number | Yes | Angular speed. |
| duration | number | Yes | Rotation duration, in ms. |

**Return value**

| Type                                        | Description        |
| ------------------------------------------- | --------- |
| Promise&lt;[Result](#result)&gt;| Promise used to return the rotation result. |

**Error codes**

For details about the error codes, see [Mechanic Manager Error Codes](errorcode-mechanic.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message           |
| -------- | ----------------- |
| 202 | Not system application. |
| 33300001 | Service exception. |
| 33300002 | Device not connected. |
| 33300003 | Feature not supported. |

**Example**

```ts
let mechId: number = 0;
let angleSpeed: number = 1.2;
let duration: number = 1;
try {
  mechanicManager.turnBySpeed(mechId, angleSpeed, duration).then((result: mechanicManager.Result) => {
    console.info(`'result:' ${result}`);
  });
} catch (e) {
  console.error(`Code is ${e.code}, message is ${e.message}`);
}
```

## mechanicManager.isSupportAction

isSupportAction(mechId: number, actionType: ActionType): boolean

Checks whether a specific action is supported.

**Since:** 26.0.0

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

**Parameters**

| Name     | Type                    | Mandatory | Description   |
| ---------- | ---------------------- | ---- | ----- |
| mechId | number | Yes | ID of the mechanic device. |
| actionType | [ActionType](#actiontype) | Yes | Action sequence type. |

**Return value**

| Type                                        | Description        |
| ------------------------------------------- | --------- |
| boolean | Whether the specific action is supported. true indicates supported, and false indicates not supported. |

**Error codes**

For details about the error codes, see [Mechanic Manager Error Codes](errorcode-mechanic.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message           |
| -------- | ----------------- |
| 202 | Not system application. |
| 33300001 | Service exception. |
| 33300002 | Device not connected. |

**Example**

```ts
let mechId: number = 0;
let actionType = mechanicManager.ActionType.HEAD_UP;
try {
  let isSupported = mechanicManager.isSupportAction(mechId, actionType);
  console.info(`isSupported: ${isSupported}`);
} catch (e) {
  console.error(`Code is ${e.code}, message is ${e.message}`);
}
```

## mechanicManager.doAction

doAction(mechId: number, actionType: ActionType): Promise&lt;Result&gt;

Executes an action sequence.

**Since:** 26.0.0

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

**Parameters**

| Name     | Type                    | Mandatory | Description   |
| ---------- | ---------------------- | ---- | ----- |
| mechId | number | Yes | ID of the mechanic device. |
| actionType | [ActionType](#actiontype) | Yes | Action sequence type.|

**Return value**

| Type                                        | Description        |
| ------------------------------------------- | --------- |
| Promise&lt;[Result](#result)&gt;| Promise object used to return the execution result. |

**Error codes**

For details about the error codes, see [Mechanic Manager Error Codes](errorcode-mechanic.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message           |
| -------- | ----------------- |
| 202 | Not system application. |
| 33300001 | Service exception. |
| 33300002 | Device not connected. |
| 33300003 | Feature not supported. |

**Example**

```ts
let mechId: number = 0;
let actionType = mechanicManager.ActionType.HEAD_UP;
try {
  mechanicManager.doAction(mechId, actionType).then((result: mechanicManager.Result) => {
    console.info(`'result:' ${result}`);
  });
} catch (e) {
  console.error(`Code is ${e.code}, message is ${e.message}`);
}
```

## mechanicManager.subscribe

subscribe(events: MechEventType[], callback: Callback&lt;MechEvent&gt;): void

Subscribes to mechanic device events.

**Since:** 26.0.0

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

**Parameters**

| Name     | Type                    | Mandatory | Description   |
| ---------- | ---------------------- | ---- | ----- |
| events | [MechEventType](#mecheventtype) | Yes | List of events to subscribe to. |
| callback | Callback&lt;[MechEvent](#mechevent)&gt; | Yes | Callback invoked to return the subscribed mechanic device events. |

**Error codes**

For details about the error codes, see [Mechanic Manager Error Codes](errorcode-mechanic.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message           |
| -------- | ----------------- |
| 202 | Not system application. |
| 33300001 | Service exception. |
| 33300002 | Device not connected. |
| 33300003 | Feature not supported. |

**Example**

```ts
let eventsSet: Set<mechanicManager.MechEventType> = new Set();
let events = Array.from(eventsSet);
try {
  mechanicManager.subscribe(events, (event: mechanicManager.MechEvent) => {
    console.info('subscribe callback');
  });
} catch (e) {
  console.error(`Code is ${e.code}, message is ${e.message}`);
}
```

## mechanicManager.unSubscribe

unSubscribe(events: MechEventType[]): void

Unsubscribes from the event.

**Since:** 26.0.0

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

**Parameters**

| Name     | Type                    | Mandatory | Description   |
| ---------- | ---------------------- | ---- | ----- |
| events | [MechEventType](#mecheventtype) | Yes | List of events to subscribe to. |

**Error codes**

For details about the error codes, see [Mechanic Manager Error Codes](errorcode-mechanic.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message           |
| -------- | ----------------- |
| 202 | Not system application. |
| 33300001 | Service exception. |
| 33300002 | Device not connected. |
| 33300003 | Feature not supported. |

**Example**

```ts
let eventsSet: Set<mechanicManager.MechEventType> = new Set();
let events = Array.from(eventsSet);
try {
  mechanicManager.unSubscribe(events);
} catch (e) {
  console.error(`Code is ${e.code}, message is ${e.message}`);
}
```

## mechanicManager.connectDevice

connectDevice(addrInfo: AddressInfo, params: ConnectParam): Promise&lt;AttachStateChangeInfo&gt;

Connects to a device based on the address.

**Since:** 26.0.0

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

**Parameters**

| Name     | Type                    | Mandatory | Description   |
| ---------- | ---------------------- | ---- | ----- |
| addrInfo | [AddressInfo](#addressinfo) | Yes | Address information. |
| params | [ConnectParam](#connectparam) | Yes | Operation parameters. |

**Return value**

| Type                                        | Description        |
| ------------------------------------------- | --------- |
| Promise&lt;[AttachStateChangeInfo](#attachstatechangeinfo)&gt;| Promise used to return the device attachment state. |

**Error codes**

For details about the error codes, see [Mechanic Manager Error Codes](errorcode-mechanic.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message           |
| -------- | ----------------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 33300001 | Service exception. |

**Example**

```ts
let addrInfo: mechanicManager.AddressInfo = {
  address: '123',
  addressType: mechanicManager.AddressType.BLE_ADDR
}
let params: mechanicManager.ConnectParam = {
  deviceName: "deviceName",
  custdata: '123',
  identifier: Number('0x551b9225')
}
try {
  mechanicManager.connectDevice(addrInfo, params)
    .then((info: mechanicManager.AttachStateChangeInfo) => {
      console.info(`connectDevice -- info: ${JSON.stringify(info)}`);
  });
} catch (e) {
  console.error(`Code is ${e.code}, message is ${e.message}`);
}
```

## mechanicManager.disconnectDevice

disconnectDevice(mechId: number): Promise&lt;Result&gt;

Disconnects a device based on the mechanic device ID.

**Since:** 26.0.0

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

**Parameters**

| Name     | Type                    | Mandatory | Description   |
| ---------- | ---------------------- | ---- | ----- |
| mechId | number | Yes | ID of the mechanic device. |

**Return value**

| Type                                        | Description        |
| ------------------------------------------- | --------- |
| Promise&lt;[Result](#result)&gt;| Promise object used to return the execution result. |

**Error codes**

For details about the error codes, see [Mechanic Manager Error Codes](errorcode-mechanic.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message           |
| -------- | ----------------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 33300001 | Service exception. |

**Example**

```ts
let mechId: number = 0;
try {
  mechanicManager.disconnectDevice(mechId).then((result: mechanicManager.Result) => {
    console.info(`'result:' ${result}`);
  });
} catch (e) {
  console.error(`Code is ${e.code}, message is ${e.message}`);
}
```

## RotationAngles

Defines the rotation angle relative to the current position.

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

| Name  | Type| Read-Only| Optional| Description|
| ----- | ---- | ---- | --- | --- |
| yaw | number | No| Yes| Yaw angle, in radians. The value range is [-2\*Math.PI, 2\*Math.PI].|
| roll | number | No| Yes| Roll angle, in radians. The value range is [-2\*Math.PI, 2\*Math.PI].|
| pitch | number | No| Yes| Pitch angle, in radians. The value range is [-2\*Math.PI, 2\*Math.PI].|

## EulerAngles

Defines the absolute Euler angle relative to the initial position.

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

| Name  | Type| Read-Only| Optional| Description|
| ----- | ---- | ---- | --- | --- |
| yaw | number | No| Yes| Yaw angle, in radians. The value range is [-2\*Math.PI, 2\*Math.PI].|
| roll | number | No| Yes| Roll angle, in radians. The value range is [-2\*Math.PI, 2\*Math.PI].|
| pitch | number | No| Yes| Pitch angle, in radians. The value range is [-2\*Math.PI, 2\*Math.PI].|

## RotationSpeed

Defines the rotation speed. A negative value indicates clockwise rotation, and a positive value indicates anticlockwise rotation.

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

| Name  | Type| Read-Only| Optional| Description|
| ----- | ---- | ---- | --- | --- |
| yawSpeed | number | No| Yes| Yaw speed, in radians per second.|
| rollSpeed | number | No| Yes| Roll speed, in radians per second.|
| pitchSpeed | number | No| Yes| Pitch speed, in radians per second.|

## RotationLimits

Defines the limit of the rotation angle relative to the initial position.

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

| Name  | Type| Read-Only| Optional| Description|
| ----- | ---- | ---- | --- | --- |
| negativeYawMax | number | No| No| Maximum yaw rotation angle (negative direction). The value range is [-2\*Math.PI, 0], in radians. If the value is less than or equal to **-2\*Math.PI**, there is no limitation on the rotation angle.|
| positiveYawMax | number | No| No| Maximum yaw rotation angle (positive direction). The value range is [0, 2\*Math.PI], in radians. If the value is greater than or equal to **2\*Math.PI**, there is no limitation on the rotation angle.|
| negativeRollMax | number | No| No| Maximum roll rotation angle (negative direction), in radians. The value range is [–2 x Math.PI, 0]. If the value is less than or equal to **-2\*Math.PI**, there is no limitation on the rotation angle.|
| positiveRollMax | number | No| No| Maximum roll rotation angle (positive direction), in radians. The value range is [0, 2 x Math.PI]. If the value is greater than or equal to **2\*Math.PI**, there is no limitation on the rotation angle.|
| negativePitchMax | number | No| No| Maximum pitch rotation angle (negative direction), in radians. The value range is [–2 x Math.PI, 0]. If the value is less than or equal to **-2\*Math.PI**, there is no limitation on the rotation angle.|
| positivePitchMax | number | No| No| Maximum pitch rotation angle (positive direction), in radians. The value range is [0, 2 x Math.PI]. If the value is greater than or equal to **2\*Math.PI**, there is no limitation on the rotation angle.|

## RotationAxesStatus

Enumerates the rotation axis states.

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

| Name  | Type| Read-Only| Optional| Description|
| ----- | ---- | ---- | --- | --- |
| yawEnabled | boolean | No| No| Whether the yaw axis is enabled. The value **true** indicates that the yaw axis is enabled, and the value **false** indicates the opposite.|
| rollEnabled | boolean | No| No| Whether the roll axis is enabled. The value **true** indicates that the roll axis is enabled, and the value **false** indicates the opposite.|
| pitchEnabled | boolean | No| No| Whether the pitch axis is enabled. The value **true** indicates that the pitch axis is enabled, and the value **false** indicates the opposite.|
| yawLimited | [RotationAxisLimited](#rotationaxislimited) | No| Yes| Yaw axis limited.|
| rollLimited | [RotationAxisLimited](#rotationaxislimited) | No| Yes| Roll axis limited.|
| pitchLimited | [RotationAxisLimited](#rotationaxislimited) | No| Yes| Pitch axis limited.|

## RotationAxisLimited

Enumerates the rotation axis limit states.

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

| Name        | Value | Description             |
| ----------- | ---- | --------------- |
| NOT_LIMITED | 0 | Unlimited.|
| NEGATIVE_LIMITED | 1 | Rotation is restricted in the negative direction and allowed in the positive direction.|
| POSITIVE_LIMITED | 2 | Rotation is restricted in the positive direction and allowed in the negative direction.|

## RotationAxesStateChangeInfo

Defines the rotation axis state change information.

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

| Name  | Type| Read-Only| Optional| Description|
| ----- | ---- | ---- | --- | --- |
| mechId | number | No| No| ID of the mechanic device.|
| status | [RotationAxesStatus](#rotationaxesstatus)| No| No| Rotation axis status.|

## Operation

Enumerates user operations.

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

| Name        | Value | Description             |
| ----------- | ---- | --------------- |
| CONNECT | 0 | Connection.|
| DISCONNECT | 1 | Disconnection.|

## Result

Enumerates the rotation results.

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

| Name        | Value | Description             |
| ----------- | ---- | --------------- |
| COMPLETED | 0 | Completed.|
| INTERRUPTED | 1 | Interrupted.|
| LIMITED | 2 | Restricted by the maximum rotation angle.|
| TIMEOUT | 3 | Operation timeout.|
| TERMINATE_OBSTACLE<sup>26.0.0+<sup> | 4 | Terminated due to an obstacle. |
| TERMINATE_CLIFF<sup>26.0.0+<sup> | 5 | Terminated due to a cliff. |
| SYSTEM_ERROR | 100 | System error.|

## TargetType<sup>21+</sup>

Enumerates the target face information.

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

| Name| Type| Value | Description|
| ----------- | ------|---- | --------------- |
| HUMAN_FACE | int | 0 | Target face information.|

## SearchDirection<sup>21+</sup>

Default search direction.

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

| Name| Type| Value | Description|
| ----------- | ------|---- | --------------- |
| DEFAULT | int | 0 | Default direction. |
| LEFTWARD | int | 1 | Leftward, that is, clockwise.|
| RIGHTWARD | int | 2 | Rightward, that is, counterclockwise.|
  
## TargetInfo<sup>21+</sup>

Information about the search target.

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

| Name  | Type| Read-Only| Optional| Description|
| ----- | ---- | ---- | --- | --- |
| targetType | [TargetType](#targettype21) | No| No| Information about the search target.|

## SearchParams<sup>21+</sup>

Specifies the search direction.

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

| Name  | Type| Read-Only| Optional| Description|
| ----- | ---- | ---- | --- | --- |
| direction | [SearchDirection](#searchdirection21) | No| No| Search direction.|

## SearchResult<sup>21+</sup>

Displays the execution result of the search command.

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

| Name  | Type| Read-Only| Optional| Description|
| ----- | ---- | ---- | --- | --- |
| targetCount | number | No| No| Number of found targets.|

## MoveParams

Device movement parameters.

**Since:** 26.0.0

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

| Name  | Type| Read-Only| Optional| Description|
| ----- | ---- | ---- | --- | --- |
| distance | number | No| No| Movement distance (the value is restricted to an integer).|
| angle | number | No| No| Rotation angle.|
| speedGear | [SpeedGear](#speedgear) | No| Yes| Speed gear.|
| mode | [MarchingMode](#marchingmode) | No| Yes| Movement mode.|

## SpeedParams

Speed control parameters.

**Since:** 26.0.0

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

| Name   | Type | Read-Only | Optional | Description|
| ----- | ---- | ---- | --- | --- |
| speed | number | No | No | Rotation or movement speed (value restricted to an integer).|
| angle | number | No | No | Rotation angle.|
| mode | [MarchingMode](#marchingmode) | No | Yes | Movement mode.|

## SpeedGear

Enumerates the speed gears.

**Since:** 26.0.0

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

| Name | Type | Value | Description |
| ----------- | ------|---- | --------------- |
| LOW_SPEED  | int | 0 | Low speed gear. |
| MIDDLE_SPEED  | int | 1 | Middle speed gear, which is the default value. |
| HIGH_SPEED   | int | -1 | High speed gear. |

## MarchingMode

Enumerates the marching modes.

**Since:** 26.0.0

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

| Name | Type | Value | Description |
| ----------- | ------|---- | --------------- |
| TURN_THEN_MOVE  | int | 0 | Turns first and then moves. |
| TURNING_MOVING  | int | 1 | Moves while turning. |

## ActionType

Enumerates the action sequence types.

**Since:** 26.0.0

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

| Name | Type | Value | Description |
| ----------- | ------|---- | --------------- |
| LANDSCAPE_PORTRAIT_SWITCH  | int | 0 | Landscape/portrait rotation. |
| PATROL_MODE  | int | 1 | Patrol mode. |
| GREET_MODE  | int | 2 | Greeting mode. |
| HEAD_UP  | int | 3 | Head up. |
| HEAD_UP_SLIGHTLY  | int | 4 | Head slightly up. |
| EYE_LEVEL  | int | 5 | Eye level. |
| HEAD_DOWN_SLIGHTLY  | int | 6 | Head slightly down. |
| HEAD_DOWN  | int | 7 | Head fully down. |
| HEAD_WIGGLE  | int | 8 | Head wiggle. |
| NOD  | int | 9 | Nod. |
| HEAD_SHAKE  | int | 10 | Head shake. |
| HEAD_TURN_TO_BASE  | int | 11 | Head returns to the base. |
| BASE_TURN_TO_HEAD  | int | 12 | Base returns to the head. |
| FRONT_TO_BACK_FLIP  | int | 13 | Gimbal flips front to back. |
| HAPPY  | int | 1000 | Happy. |
| ANGRY  | int | 1001 | Angry. |
| SAD  | int | 1002 | Sad. |
| SCARED  | int | 1003 | Scared. |
| DANCE  | int | 2000 | Dance. |
| ACTING_CUTE  | int | 2001 | Acting cute. |
| CELEBRATE  | int | 2002 | Celebrate. |
| WAKEUP  | int | 2003 | Wake up. |
| SLEEP  | int | 2004 | Sleep. |
| LOW_POWER  | int | 2005 | Low power. |
| THINKING  | int | 2006 | Thinking. |

## MechEvent

Defines the mechanic device events.

**Since:** 26.0.0

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

| Name   | Type | Read-Only | Optional | Description|
| ----- | ---- | ---- | --- | --- |
| mechId | number | No | No | ID of the mechanic device. |
| event | [MechEventType](#mecheventtype) | No | No | Event type. |

## MechEventType

Defines the mechanic device events.

**Since:** 26.0.0

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

| Name | Type | Value | Description |
| ----------- | ------|---- | --------------- |
| DEVICE_ADSORBED  | int | 0 | Adsorption event. |
| DEVICE_UNADSORBED  | int | 1 | Non-adsorption event. |
| REACH_CLIFF  | int | 2 | A cliff is encountered during movement. |
| REACH_OBSTACLE  | int | 3 | An obstacle is encountered during movement. |
| LOW_POWER  | int | 4 | The device is low on power. |

## AddressInfo

Defines the accessory device information.

**Since:** 26.0.0

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

| Name   | Type | Read-Only | Optional | Description|
| ----- | ---- | ---- | --- | --- |
| address | string | No | No | Accessory device address. |
| addressType | [AddressType](#addresstype) | No | No | Address type. |

## AddressType

Enumerates the address types of a mechanic device.

**Since:** 26.0.0

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

| Name | Type | Value | Description |
| ----------- | ------|---- | --------------- |
| BLE_ADDR  | int | 0 | Bluetooth address type of the mechanic device. |

## ConnectParam

Defines the connection parameters.

**Since:** 26.0.0

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

| Name   | Type | Read-Only | Optional | Description |
| ----- | ---- | ---- | --- | --- |
| deviceName | string | No | Yes | Mechanic device name. |
| identifier | number | No | Yes | Current device identifier (restricted to an integer). |
| custdata | string | No | No | Data carried when the device is discovered. |

## AttachStateChangeInfo

Defines the connection parameters.

**Since:** 26.0.0

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

| Name   | Type | Read-Only | Optional | Description|
| ----- | ---- | ---- | --- | --- |
| state | [AttachState](#attachstate) | No | No | Attachment state. |
| mechInfo | [MechInfo](#mechinfo) | No | No | Mechanic device information. |

## AttachState

Enumerates the attachment states of a mechanic device.

**Since:** 26.0.0

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

| Name | Type | Value | Description |
| ----------- | ------|---- | --------------- |
| ATTACHED  | int | 0 | Device attached. |
| DETACHED  | int | 1 | Device detached. |

## MechInfo

Mechanic device information.

**Since:** 26.0.0

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

| Name   | Type | Read-Only | Optional | Description|
| ----- | ---- | ---- | --- | --- |
| mechId | number | No | No | ID of the mechanic device. |
| mechInfo | [MechDeviceType](#mechdevicetype) | No | No | Mechanic device type. |
| mechName | string | No | No | Mechanic device name. |

## MechDeviceType

Enumerates the mechanic device types.

**Since:** 26.0.0

**System capability**: SystemCapability.Mechanic.Core

**System API**: This is a system API.

| Name | Type | Value | Description |
| ----------- | ------|---- | --------------- |
| GIMBAL_DEVICE  | int | 0 | Gimbal device type. |
| DESKTOP_GIMBAL_DEVICE  | int | 1 | Desktop gimbal. |
| WHEELED_BASE_DEVICE  | int | 2 | Wheeled base. |
| POCKET_GIMBAL_CAMERA_DEVICE  | int | 3 | Pocket gimbal camera. |