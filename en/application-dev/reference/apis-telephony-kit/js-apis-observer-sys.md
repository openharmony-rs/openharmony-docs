# @ohos.telephony.observer (Telephony Status Observer) (System API)
<!--Kit: Telephony Kit-->
<!--Subsystem: Telephony-->
<!--Owner: @shao-yikai-->
<!--Designer: @wnazgul-->
<!--Tester: @jiang_99-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=a64e73c35f7fb6dab50a7c26545aed09dc775fc0 translatedAt=2026-11-03T03:53:51.522Z pushedAt=2026-11-03T09:10:25.895Z nl=1 -->

This module provides event subscription management functions. With the APIs provided by this module, you can register or unregister an observer that listens cell information events (for the SIM card in the specified slot).

> **NOTE**
>
> The initial APIs of this module are supported since API version 6. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> This page contains only the system APIs of this module. For details about other public APIs, see [@ohos.telephony.observer (Telephony State Observation)](js-apis-observer.md).

## Modules to Import

```ts
import { observer } from '@kit.TelephonyKit';
```


## observer.on('cellInfoChange')<sup>8+</sup>

on\(type: \'cellInfoChange\', callback: Callback\<Array\<CellInformation\>\>\): void

Subscribes to the cell information change event. This API uses an asynchronous callback to return the result. It applies to scenarios where the cell information changes of base stations need to be obtained, such as assisted positioning in location services, network signal quality monitoring, and base station handover tracking.

**System API**: This is a system API.

**Required permissions**: ohos.permission.LOCATION and ohos.permission.APPROXIMATELY_LOCATION

**System capability**: SystemCapability.Telephony.StateRegistry

**Parameters**

| Name  | Type                                                     | Mandatory| Description                                     |
| -------- | --------------------------------------------------------- | ---- |------------------------------------------|
| type     | string                                                    | Yes  | Cell information change event. This field has a fixed value of **cellInfoChange**.|
| callback | Callback\<Array\<[CellInformation](js-apis-radio.md#cellinformation8)\>\> | Yes  | Callback used to return the result.               |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Telephony Error Codes](errorcode-telephony.md).

| ID|                  Error Message                   |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 202      | Non-system applications use system APIs.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**Example**

```ts
import { observer, radio } from '@kit.TelephonyKit';
import { radio } from '@kit.TelephonyKit';

// Subscribe to the cell information change event.
try {
  observer.on('cellInfoChange', (data: Array<radio.CellInformation>) => {
      console.info("on cellInfoChange, data:" + JSON.stringify(data));
  });
} catch (err) {
  console.error(`observer.on failed, err: ${JSON.stringify(err)}`);
}
```


## observer.on('cellInfoChange')<sup>8+</sup>(Specified Slot)

on\(type: \'cellInfoChange\', options: ObserverOptions, callback: Callback\<Array\<CellInformation\>\>\): void

Subscribes to the cell information change event of a specified slot. This API uses an asynchronous callback. It applies to applications that need to listen for cell information changes of a specified slot in multi-SIM scenarios, for example, a dual-SIM device that separately monitors the base station signal quality and location services of different carriers.

**System API**: This is a system API.

**Required permissions**: ohos.permission.LOCATION and ohos.permission.APPROXIMATELY_LOCATION

**System capability**: SystemCapability.Telephony.StateRegistry

**Parameters**

| Name| Type                                              | Mandatory| Description                                     |
| ------ |--------------------------------------------------| ---- |--------------------------------------------|
| type     | string                                           | Yes  | Cell information change event. This field has a fixed value of **cellInfoChange**.|
| options  | [ObserverOptions](js-apis-observer.md#observeroptions11)            | Yes   | Event subscription options, which can specify the slot ID (**slotId**) to subscribe to and other information.                |
| callback | Callback\<Array\<[CellInformation](js-apis-radio.md#cellinformation8)\>\> | Yes  | Callback used to return the result.      |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Telephony Error Codes](errorcode-telephony.md).

| ID|                  Error Message                   |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 202      | Non-system applications use system APIs.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**Example**

```ts
import { observer, radio } from '@kit.TelephonyKit';
import { radio } from '@kit.TelephonyKit';

// Set the subscription parameters and specify the slot.
let options: observer.ObserverOptions = {
    slotId: 0
}
// Subscribe to the cell information change event of the specified slot.
try {
  observer.on('cellInfoChange', options, (data: Array<radio.CellInformation>) => {
      console.info("on cellInfoChange, data:" + JSON.stringify(data));
  });
} catch (err) {
  console.error(`observer.on failed, err: ${JSON.stringify(err)}`);
}
```


## observer.off('cellInfoChange')<sup>8+</sup>

off\(type: \'cellInfoChange\', callback?: Callback\<Array\<CellInformation\>\>\): void

Unsubscribes from the cell information change event.

> **NOTE**
>
>You can pass the **callback** in **on** to cancel a subscription. You can also cancel all subscriptions without specifying **callback**.

**System API**: This is a system API.

**System capability**: SystemCapability.Telephony.StateRegistry

**Parameters**

| Name  | Type                                                     | Mandatory| Description                                                        |
| -------- | --------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                                                    | Yes  | Cell information change event. This field has a fixed value of **cellInfoChange**.                                           |
| callback | Callback\<Array\<[CellInformation](js-apis-radio.md#cellinformation8)\>\> | No | Unsubscribes from the specified callback. If a callback in **on** is specified, the specified callback is unregistered. If this parameter is left empty, all callbacks are unregistered. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Telephony Error Codes](errorcode-telephony.md).

| ID|                  Error Message                   |
| -------- | -------------------------------------------- |
| 202      | Non-system applications use system APIs.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**Example**

```ts
import { observer, radio } from '@kit.TelephonyKit';
import { radio } from '@kit.TelephonyKit';

let callback: (data: Array<radio.CellInformation>) => void = (data: Array<radio.CellInformation>) => {
    console.info("on cellInfoChange, data:" + JSON.stringify(data));
}
try {
  observer.on('cellInfoChange', callback);
  // You can specify a callback in **on** to unregister the specified callback or unregister all callbacks without specifying a callback.
  observer.off('cellInfoChange', callback);
  observer.off('cellInfoChange');
} catch (err) {
  console.error(`observer on/off failed, err: ${JSON.stringify(err)}`);
}

```

