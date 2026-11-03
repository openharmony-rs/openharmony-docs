# @ohos.telephony.observer (Telephony Service Status Listening)
<!--Kit: Telephony Kit-->
<!--Subsystem: Telephony-->
<!--Owner: @shao-yikai-->
<!--Designer: @wnazgul-->
<!--Tester: @jiang_99-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=28c751e3c051ae3710d8f965399ae98fa2c6ca64 translatedAt=2026-11-03T03:58:10.353Z pushedAt=2026-11-03T09:27:27.766Z nl=1 -->

This module provides subscription management. The events that can be subscribed to or unsubscribed from include network status changes, signal status changes, call status changes, cellular data link connection status, uplink and downlink data flow status of cellular data services, and SIM status changes.

> **NOTE**
>
> The initial APIs of this module are supported since API version 6. Newly added APIs will be marked with a superscript to indicate their earliest API version.


## Modules to Import

```ts
import { observer } from '@kit.TelephonyKit';
```

## NetworkState

type NetworkState = radio.NetworkState

Network registration status.

**System capability:** SystemCapability.Telephony.StateRegistry

|       Type       |            Description             |
| ---------------- | --------------------------- |
| [radio.NetworkState](js-apis-radio.md#networkstate) | Network registration status. |

## SignalInformation

type SignalInformation = radio.SignalInformation

Network signal strength information object.

**System capability:** SystemCapability.Telephony.StateRegistry

|       Type       |          Description           |
| ---------------- | ------------------------------ |
| [radio.SignalInformation](js-apis-radio.md#signalinformation) | Network signal strength information object. |


## DataConnectState

type DataConnectState = data.DataConnectState

Describes the cellular data link connection status.

**System capability:** SystemCapability.Telephony.StateRegistry

|       Type       |            Description             |
| ---------------- | --------------------------- |
| [data.DataConnectState](js-apis-telephony-data.md#dataconnectstate) | Describes the cellular data link connection status. |


## RatType

type RatType = radio.RadioTechnology

Radio access technology.

**System capability:** SystemCapability.Telephony.StateRegistry

|       Type       |            Description             |
| ---------------- | --------------------------- |
| [radio.RadioTechnology](js-apis-radio.md#radiotechnology) | Radio access technology. |


## DataFlowType

type DataFlowType = data.DataFlowType

Describes the cellular data flow type.

**System capability:** SystemCapability.Telephony.StateRegistry

|       Type       |            Description             |
| ---------------- | --------------------------- |
| [data.DataFlowType](js-apis-telephony-data.md#dataflowtype) | Describes the cellular data flow type. |


## CallState

type CallState = call.CallState

Call status code.

**System capability:** SystemCapability.Telephony.StateRegistry

| Type | Description |
| ---------------- | --------------------------- |
| [call.CallState](js-apis-call.md#callstate) | Call status code (during the outgoing call process, only the CALL_STATE_OFFHOOK status is notified). |


## CCallState<sup>23+</sup>

type CCallState = call.CCallState

Carrier call status code.

**System capability:** SystemCapability.Telephony.StateRegistry

|       Type       |            Description             |
| ---------------- | --------------------------- |
| [call.CCallState](js-apis-call.md#ccallstate23) | Call status code (carrier call status code). |


## CardType

type CardType = sim.CardType

Card type.

**System capability:** SystemCapability.Telephony.StateRegistry

|       Type       |            Description             |
| ---------------- | --------------------------- |
| [sim.CardType](js-apis-sim.md#cardtype7) | Card type. |


## SimState

type SimState = sim.SimState

SIM card status.

**System capability**: SystemCapability.Telephony.StateRegistry

|       Type       |            Description             |
| ---------------- | --------------------------- |
| [sim.SimState](js-apis-sim.md#simstate) | SIM card status. |

## TelCallState<sup>21+</sup>

type TelCallState = call.TelCallState

Call status code.

**System capability:** SystemCapability.Telephony.StateRegistry

|       Type       |            Description             |
| ---------------- | --------------------------- |
| [call.TelCallState](js-apis-call.md#telcallstate21) | Call status code (during the outgoing call process, notifies the called number status **TEL_CALL_STATE_OFFHOOK** and the call connected status **TEL_CALL_STATE_CONNECTED**). |


## observer.on('networkStateChange')

on\(type: \'networkStateChange\', callback: Callback\<NetworkState\>\): void

Subscribes to the network status change event. This API uses an asynchronous callback.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**System capability:** SystemCapability.Telephony.StateRegistry

**Parameters**

| Name     | Type                                                      | Mandatory | Description                                                              |
| -------- | --------------------------------------------------------- | ---- | ---------------------------------------------------------------- |
| type     | string                                                    | Yes  | Network status change event. The value is fixed to 'networkStateChange'.                 |
| callback | Callback\<[NetworkState](js-apis-radio.md#networkstate)\> | Yes  | Callback invoked to return the network status object. For details, see [NetworkState](js-apis-radio.md#networkstate) in radio.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Telephony Subsystem Error Codes](errorcode-telephony.md).

| ID |                  Error Message                    |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**Example**

```ts
try {
    observer.on('networkStateChange', (data: observer.NetworkState) => {
        console.info("on networkStateChange, data:" + JSON.stringify(data));
    });
} catch (err) {
    console.error(`observer.on networkStateChange failed: ${JSON.stringify(err)}`);
}
```


## observer.on('networkStateChange')

on\(type: \'networkStateChange\', options: ObserverOptions, callback: Callback\<NetworkState\>\): void

Subscribes to the network status change event of the specified card slot. This API uses an asynchronous callback.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**System capability**: SystemCapability.Telephony.StateRegistry

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | --------------------------------------------------------- | ---- | ---------------------------------------------------------------- |
| type     | string                                                    | Yes  | Network status change event. This parameter is fixed to 'networkStateChange'. |
| options  | [ObserverOptions](#observeroptions11)                     | Yes  | Optional parameters for telephony-related event subscription. |
| callback | Callback\<[NetworkState](js-apis-radio.md#networkstate)\> | Yes  | Callback function used to return the network status object. For details, see [NetworkState](js-apis-radio.md#networkstate) in radio. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Telephony Subsystem Error Codes](errorcode-telephony.md).

| ID |                  Error Message                    |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**Example**

```ts
// Set the subscription parameters and specify card slot ID 0 (card slot 1).
let options: observer.ObserverOptions = {
    slotId: 0
}
// Subscribe to the network status change event of the specified card slot.
observer.on('networkStateChange', options, (data: observer.NetworkState) => {
    console.info("on networkStateChange, data:" + JSON.stringify(data));
});
```


## observer.off('networkStateChange')

off\(type: \'networkStateChange\', callback?: Callback\<NetworkState\>\): void

Unsubscribes from the network status change event. This API uses a callback as an asynchronous method.

> **NOTE**
>
> You can pass the callback specified in on to unsubscribe from a single subscription, or omit the callback to clear all subscriptions.

**System capability:** SystemCapability.Telephony.StateRegistry

**Parameters**

| Name     | Type                                                      | Mandatory | Description                                                         |
| -------- | --------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                                                    | Yes  | Network status change event. This parameter is fixed at 'networkStateChange'.                 |
| callback | Callback\<[NetworkState](js-apis-radio.md#networkstate)\> | No   | Callback for the network status change event. It returns the network status object. For details, see [NetworkState](js-apis-radio.md#networkstate) in radio. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Telephony Subsystem Error Codes](errorcode-telephony.md).

| ID |                  Error Message                    |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**Example**

```ts
let callback: (data: observer.NetworkState) => void = (data: observer.NetworkState) => {
    console.info("on networkStateChange, data:" + JSON.stringify(data));
}
observer.on('networkStateChange', callback);
// You can pass the callback specified in on to unsubscribe from a single subscription, or omit the callback to clear all subscriptions.
observer.off('networkStateChange', callback);
observer.off('networkStateChange');
```

## observer.on('signalInfoChange')

on\(type: \'signalInfoChange\', callback: Callback\<Array\<SignalInformation\>\>): void

Subscribes to the signal status change event. This API uses an asynchronous callback to return the result.

**System capability:** SystemCapability.Telephony.StateRegistry

**Parameters**

| Name     | Type                                                         | Mandatory | Description                                                         |
| -------- | ------------------------------------------------------------ | --------- | ----------------------------------------------------------- |
| type     | string                                                       | Yes       | Signal status change event. The value is fixed at 'signalInfoChange'.              |
| callback | Callback\<Array\<[SignalInformation](js-apis-radio.md#signalinformation)\>\> | Yes       | Callback invoked to return the signal strength object. For details, see [SignalInformation](js-apis-radio.md#signalinformation) in radio. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Telephony Subsystem Error Codes](errorcode-telephony.md).

| ID |                  Error Message                     |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**Example**

```ts
import { radio } from '@kit.TelephonyKit';

observer.on('signalInfoChange', (data: Array<radio.SignalInformation>) => {
    console.info("on signalInfoChange, data:" + JSON.stringify(data));
});
```


## observer.on('signalInfoChange')

on\(type: \'signalInfoChange\', options: ObserverOptions, callback: Callback\<Array\<SignalInformation\>\>): void

Subscribes to the signal status change event of the specified card slot. This API uses a callback as an asynchronous method.

**System capability:** SystemCapability.Telephony.StateRegistry

**Parameters**

| Name     | Type                                                         | Mandatory | Description                                                         |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------------- |
| type     | string                                                       | Yes  | Signal status change event. The value is fixed at 'signalInfoChange'.              |
| options  | [ObserverOptions](#observeroptions11)                        | Yes  | Optional parameters for telephony-related event subscription.                                   |
| callback | Callback\<Array\<[SignalInformation](js-apis-radio.md#signalinformation)\>\> | Yes  | Callback function used to return the signal strength object. For details, see [SignalInformation](js-apis-radio.md#signalinformation) of radio. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Telephony Service Error Codes](errorcode-telephony.md).

| ID |                  Error Message                    |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**Example**

```ts
import { radio } from '@kit.TelephonyKit';

let options: observer.ObserverOptions = {
    slotId: 0
}
observer.on('signalInfoChange', options, (data: Array<radio.SignalInformation>) => {
    console.info("on signalInfoChange, data:" + JSON.stringify(data));
});
```


## observer.off('signalInfoChange')

off\(type: \'signalInfoChange\', callback?: Callback\<Array\<SignalInformation\>\>): void

Unsubscribes from the signal status change event. This API uses a callback as an asynchronous method.

> **NOTE**
>
> You can pass the callback in **on** to unsubscribe from a single subscription, or omit the callback to clear all subscriptions.

**System capability:** SystemCapability.Telephony.StateRegistry

**Parameters**

| Name     | Type                                                         | Mandatory | Description                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Signal status change event. This parameter is fixed to **'signalInfoChange'**.              |
| callback | Callback\<Array\<[SignalInformation](js-apis-radio.md#signalinformation)\>\> | No   | Callback for the signal status change event, used to return the signal strength object. For details, see [SignalInformation](js-apis-radio.md#signalinformation) in radio. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Telephony Error Codes](errorcode-telephony.md).

| ID |                  Error Message                    |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**Example**

```ts
import { radio } from '@kit.TelephonyKit';

let callback: (data: Array<radio.SignalInformation>) => void = (data: Array<radio.SignalInformation>) => {
    console.info("on signalInfoChange, data:" + JSON.stringify(data));
}
observer.on('signalInfoChange', callback);
// You can pass the callback in on to unsubscribe from a single subscription, or omit the callback to clear all subscriptions.
observer.off('signalInfoChange', callback);
observer.off('signalInfoChange');
```


## observer.on('callStateChange')

on(type: 'callStateChange', callback: Callback\<CallStateInfo\>): void

Subscribes to the call status change event. This API uses an asynchronous callback.

**System capability:** SystemCapability.Telephony.StateRegistry

**Parameters**

| Name     | Type                                           | Mandatory | Description                                                        |
| -------- | --------------------------------------------- | --------- | ----------------------------------------------------------- |
| type     | string                                        | Yes       | Call status change event. The value is fixed at "callStateChange".                |
| callback | Callback\<[CallStateInfo](#callstateinfo11)\> | Yes       | Callback invoked to return the call status information object.<br>The application can obtain CallStateInfo.<br>Among them, a third-party application can obtain only the call status in state. The number is controlled by system permissions and is available only to system applications. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Telephony Subsystem Error Codes](errorcode-telephony.md).

| ID |                  Error Message                    |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**Example**

```ts
observer.on('callStateChange', (data: observer.CallStateInfo) => {
    console.info("on callStateChange, data:" + JSON.stringify(data));
});
```


## observer.on('callStateChange')

on(type: 'callStateChange', options: ObserverOptions, callback: Callback\<CallStateInfo\>): void

Subscribes to the call status change event. This API uses an asynchronous callback to return the result.

**System capability:** SystemCapability.Telephony.StateRegistry

**Parameters**

| Name     | Type                                                         | Mandatory | Description                                                         |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------------- |
| type     | string                                                       | Yes  | Call status change event. The value is fixed at "callStateChange".               |
| options  | [ObserverOptions](#observeroptions11)                        | Yes  | Optional telephony-related event subscription parameters.                                  |
| callback | Callback\<[CallStateInfo](#callstateinfo11)\>                | Yes  | Callback invoked to return the call status information object.<br>The application can obtain CallStateInfo.<br>Among them, a third-party application can obtain only the call status (state). The number is controlled by system permissions and is available only to system applications. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Telephony Subsystem Error Codes](errorcode-telephony.md).

| ID |                  Error Message                    |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**Example**

```ts
let options: observer.ObserverOptions = {
    slotId: 0
}
observer.on('callStateChange', options, (data: observer.CallStateInfo) => {
    console.info("on callStateChange, data:" + JSON.stringify(data));
});
```


## observer.off('callStateChange')

off(type: 'callStateChange', callback?: Callback\<CallStateInfo\>): void

Unsubscribes from the call status change event. This API uses a callback as an asynchronous method.

> **NOTE**
>
> You can pass the callback specified in on to unsubscribe from a single subscription, or omit the callback to clear all subscriptions.

**System capability:** SystemCapability.Telephony.StateRegistry

**Parameters**

| Name     | Type                                                         | Mandatory | Description                                                         |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------------- |
| type     | string                                                       | Yes  | Call status change event. This parameter has a fixed value of **callStateChange**.               |
| callback | Callback\<[CallStateInfo](#callstateinfo11)\>                | No   | Callback for the call status change event.<br>A third-party app can obtain only the call status. The number is controlled by system permissions and is available only to system apps. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Telephony Subsystem Error Codes](errorcode-telephony.md).

| ID |                  Error Message                    |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**Example**

```ts
let callback: (data: observer.CallStateInfo) => void = (data: observer.CallStateInfo) => {
    console.info("on callStateChange, data:" + JSON.stringify(data));
}
observer.on('callStateChange', callback);
// You can pass the callback specified in on to unsubscribe from a single subscription, or omit the callback to clear all subscriptions.
observer.off('callStateChange', callback);
observer.off('callStateChange');
```


## observer.on('callStateChangeEx')<sup>21+</sup>

on(type: 'callStateChangeEx', callback: Callback\<TelCallState\>, options?: ObserverOptions): void

Subscribes to the call status change extension event. This API uses an asynchronous callback to return the result.

**System capability:** SystemCapability.Telephony.StateRegistry

**Parameters**

| Name     | Type                                          | Mandatory | Description                                                        |
| -------- | --------------------------------------------- | --------- | ----------------------------------------------------------- |
| type     | string                                        | Yes       | Call status change event. This parameter has a fixed value of **callStateChangeEx**.                |
| callback | Callback\<[TelCallState](js-apis-call.md#telcallstate21)\> | Yes       | Callback used to return the call status object.<br>The app can obtain **TelCallState**.<br> |
| options  | [ObserverOptions](#observeroptions11)         | No        | Optional telephony-related event subscription parameter, which specifies the card slot ID of the event subscription. The default value is the ID of the current default data card slot. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Telephony Subsystem Error Codes](errorcode-telephony.md).

| ID |                  Error Message                    |
| -------- | -------------------------------------------- |
| 8800001  | Invalid parameter value.                     |
| 8800002  | Service connection failed.                   |
| 8800003  | System internal error.                       |
| 8800999  | Unknown error.                               |

**Example**

```ts
import { call } from '@kit.TelephonyKit';

// Define the callback for the call status change extension event.
let callback: (data: call.TelCallState) => void = (data: call.TelCallState) => {
    console.info("on callStateChangeEx, data:" + JSON.stringify(data));
}
// Set the subscription parameters and specify the card slot ID.
let options: observer.ObserverOptions = {
    slotId: 0
}

try {
    // Subscribe to the call status change extension event (specified card slot).
    observer.on('callStateChangeEx', callback, options);
    // Subscribe to the call status change extension event (no card slot specified; listen to all card slots).
    observer.on('callStateChangeEx', callback);
} catch (err) {
    console.error(`observer.on callStateChangeEx failed: ${JSON.stringify(err)}`);
}
```


## observer.off('callStateChangeEx')<sup>21+</sup>

off(type: 'callStateChangeEx', callback?: Callback\<TelCallState\>): void

Unsubscribes from the call status change extension event. This API uses an asynchronous callback.

> **NOTE**
>
> You can pass the callback specified in **on** to unsubscribe from a single subscription, or omit the callback to clear all subscriptions.

**System capability:** SystemCapability.Telephony.StateRegistry

**Parameters**

| Name     | Type                                                         | Mandatory | Description                                                         |
| -------- | ------------------------------------------------------------ | --------- | ----------------------------------------------------------- |
| type     | string                                                       | Yes       | Call status change event. This parameter has a fixed value of **callStateChangeEx**.               |
| callback | Callback\<[TelCallState](js-apis-call.md#telcallstate21)\>                | No        | Callback for the call status change event. For details, see [TelCallState](js-apis-call.md#telcallstate21) in **call**.<br> |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Telephony Subsystem Error Codes](errorcode-telephony.md).

| ID |                  Error Message                    |
| -------- | -------------------------------------------- |
| 8800001  | Invalid parameter value.                     |
| 8800002  | Service connection failed.                   |
| 8800003  | System internal error.                       |
| 8800999  | Unknown error.                               |

**Example**

```ts
import { call } from '@kit.TelephonyKit';
let callback: (data: call.TelCallState) => void = (data: call.TelCallState) => {
    console.info("on callStateChangeEx, data:" + JSON.stringify(data));
}
observer.on('callStateChangeEx', callback);
// You can pass the callback specified in on to unsubscribe from a single subscription, or omit the callback to clear all subscriptions.
observer.off('callStateChangeEx', callback);
observer.off('callStateChangeEx');
```


## observer.on('cellularDataConnectionStateChange')<sup>7+</sup>

on\(type: 'cellularDataConnectionStateChange', callback: Callback\<DataConnectionStateInfo\>\): void

Subscribes to the cellular data link connection status. This API uses an asynchronous callback.

**System capability:** SystemCapability.Telephony.StateRegistry

**Parameters**

| Name     | Type                               | Mandatory | Description                                                                 |
| -------- | --------------------------------- | --------- | --------------------------------------------------------------------------- |
| type     | string                            | Yes       | Cellular data link connection status change event. The value is fixed to 'cellularDataConnectionStateChange'. |
| callback | Callback\<[DataConnectionStateInfo](#dataconnectionstateinfo11)\>  | Yes       | Callback invoked to return the cellular data link connection status information object. For details, see [DataConnectState](js-apis-telephony-data.md#dataconnectstate) in data and [RadioTechnology](js-apis-radio.md#radiotechnology) in radio. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Telephony Subsystem Error Codes](errorcode-telephony.md).

| ID |                  Error Message                    |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**Example**

```ts
observer.on('cellularDataConnectionStateChange', (data: observer.DataConnectionStateInfo) => {
    console.info("on cellularDataConnectionStateChange, data:" + JSON.stringify(data));
});
```


## observer.on('cellularDataConnectionStateChange')<sup>7+</sup>

on\(type: 'cellularDataConnectionStateChange', options: ObserverOptions, callback: Callback\<DataConnectionStateInfo\>\): void

Subscribes to the cellular data link connection status of the specified card slot. This API uses an asynchronous callback to return the result.

**System capability:** SystemCapability.Telephony.StateRegistry

**Parameters**

| Name     | Type                                                         | Mandatory | Description                                                         |
| -------- | ------------------------------------------------------------ | --------- | ------------------------------------------------------------ |
| type     | string                                                       | Yes       | Cellular data link connection status event. This parameter is fixed to 'cellularDataConnectionStateChange'. |
| options  | [ObserverOptions](#observeroptions11)                        | Yes       | Optional parameters for telephony-related event subscription. |
| callback | Callback\<[DataConnectionStateInfo](#dataconnectionstateinfo11)\> | Yes       | Callback invoked to return the cellular data link connection status information object. For details about data, see [DataConnectState](js-apis-telephony-data.md#dataconnectstate) and [RadioTechnology](js-apis-radio.md#radiotechnology). |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Telephony Subsystem Error Codes](errorcode-telephony.md).

| ID |                  Error Message                    |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**Example**

```ts
let options: observer.ObserverOptions = {
    slotId: 0
}
observer.on('cellularDataConnectionStateChange', options, (data: observer.DataConnectionStateInfo) => {
    console.info("on cellularDataConnectionStateChange, data:" + JSON.stringify(data));
});
```


## observer.off('cellularDataConnectionStateChange')<sup>7+</sup>

off\(type: 'cellularDataConnectionStateChange',  callback?: Callback\<DataConnectionStateInfo\>\): void

Unsubscribes from the cellular data link connection status change event. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> You can pass the callback specified in on to unsubscribe from a single subscription, or omit the callback to clear all subscriptions.

**System capability:** SystemCapability.Telephony.StateRegistry

**Parameters**

| Name     | Type                                                         | Mandatory | Description                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Cellular data link connection status change event. This parameter is fixed to 'cellularDataConnectionStateChange'. |
| callback | Callback\<[DataConnectionStateInfo](#dataconnectionstateinfo11)\> | No   | Callback for the cellular data link connection status change event. For details about data, see [DataConnectState](js-apis-telephony-data.md#dataconnectstate) and [RadioTechnology](js-apis-radio.md#radiotechnology). |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Telephony Subsystem Error Codes](errorcode-telephony.md).

| ID |                  Error Message                    |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**Example**

```ts
let callback: (data: observer.DataConnectionStateInfo) => void = (data: observer.DataConnectionStateInfo) => {
    console.info("on cellularDataConnectionStateChange, data:" + JSON.stringify(data));
}
observer.on('cellularDataConnectionStateChange', callback);
// You can pass the callback specified in on to unsubscribe from a single subscription, or omit the callback to clear all subscriptions.
observer.off('cellularDataConnectionStateChange', callback);
observer.off('cellularDataConnectionStateChange');
```


## observer.on('cellularDataFlowChange')<sup>7+</sup>

on\(type: 'cellularDataFlowChange', callback: Callback\<DataFlowType\>\): void

Subscribes to the uplink and downlink data flow status of the cellular data service. This API uses an asynchronous callback to return the result.

**System capability:** SystemCapability.Telephony.StateRegistry

**Parameters**

| Name     | Type                                                         | Mandatory | Description                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Uplink and downlink data flow status event of the cellular data service. This parameter is fixed at 'cellularDataFlowChange'.         |
| callback | Callback\<[DataFlowType](js-apis-telephony-data.md#dataflowtype)\> | Yes   | Callback invoked to return the data flow status object. For details about data, see [DataFlowType](js-apis-telephony-data.md#dataflowtype). |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Telephony Subsystem Error Codes](errorcode-telephony.md).

| ID |                  Error Message                    |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**Example**

```ts
import { data } from '@kit.TelephonyKit';

observer.on('cellularDataFlowChange', (data: data.DataFlowType) => {
    console.info("on cellularDataFlowChange, data:" + JSON.stringify(data));
});
```


## observer.on('cellularDataFlowChange')<sup>7+</sup>

on\(type: 'cellularDataFlowChange', options: ObserverOptions,  callback: Callback\<DataFlowType\>\): void

Subscribes to the uplink and downlink data flow status of the cellular data service on the specified card slot. This API uses an asynchronous callback to return the result.

**System capability:** SystemCapability.Telephony.StateRegistry

**Parameters**

| Name   | Type                                                       | Mandatory | Description                                                         |
| -------- | ---------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                                                     | Yes   | Event of the uplink and downlink data flow status of the cellular data service. The value is fixed to 'cellularDataFlowChange'.         |
| options   | [ObserverOptions](#observeroptions11)                     | Yes   | Optional parameter for telephony-related event subscription.                                                   |
| callback | Callback\<[DataFlowType](js-apis-telephony-data.md#dataflowtype)\> | Yes   | Callback function used to return the data flow status object. For details, see [DataFlowType](js-apis-telephony-data.md#dataflowtype) in data. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Telephony Service Error Codes](errorcode-telephony.md).

| ID |                  Error Message                    |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**Example**

```ts
import { data } from '@kit.TelephonyKit';

let options: observer.ObserverOptions = {
    slotId: 0
}
observer.on('cellularDataFlowChange', options, (data: data.DataFlowType) => {
    console.info("on cellularDataFlowChange, data:" + JSON.stringify(data));
});
```


## observer.off('cellularDataFlowChange')<sup>7+</sup>

off\(type: 'cellularDataFlowChange', callback?: Callback\<DataFlowType\>\): void

Unsubscribes from the uplink and downlink data flow status of the cellular data service. This API uses a callback as an asynchronous method.

> **NOTE**
>
> You can pass the callback specified in on to unsubscribe from a single subscription, or omit the callback to clear all subscriptions.

**System capability:** SystemCapability.Telephony.StateRegistry

**Parameters**

| Name     | Type                                                                | Mandatory | Description                                                         |
| -------- | ------------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                             | Yes  | Event of the uplink and downlink data flow status of the cellular data service. This parameter is fixed to 'cellularDataFlowChange'.   |
| callback | Callback\<[DataFlowType](js-apis-telephony-data.md#dataflowtype)\> | No   | Callback for the data flow status change event. It returns the data flow status object. For details, see [DataFlowType](js-apis-telephony-data.md#dataflowtype) in data. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Telephony Error Codes](errorcode-telephony.md).

| ID |                  Error Message                    |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**Example**

```ts
import { data } from '@kit.TelephonyKit';

let callback: (data: data.DataFlowType) => void = (data: data.DataFlowType) => {
    console.info("on cellularDataFlowChange, data:" + JSON.stringify(data));
}
observer.on('cellularDataFlowChange', callback);
// Pass the callback specified in on to unsubscribe from a single subscription, or omit the callback to clear all subscriptions.
observer.off('cellularDataFlowChange', callback);
observer.off('cellularDataFlowChange');
```


## observer.on('simStateChange')<sup>7+</sup>

on\(type: 'simStateChange', callback: Callback\<SimStateData\>\): void

Subscribes to the SIM card status change event. This API uses an asynchronous callback to return the result.

>**NOTE**
>
> This API does not include the SIM card activation status. For details, see [sim.isSimActive](js-apis-sim.md#simissimactive7).

**System capability:** SystemCapability.Telephony.StateRegistry

**Parameters**

| Name     | Type                                                         | Mandatory | Description                                                         |
| -------- | ------------------------------------------------------------ | --------- | ----------------------------------------------------------- |
| type     | string                                                       | Yes       | SIM card status change event. This parameter has a fixed value of **simStateChange**. |
| callback | Callback\<[SimStateData](#simstatedata7)\> | Yes       | Callback used to return the card status data object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Telephony Error Codes](errorcode-telephony.md).

| ID |                 Error Message                     |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**Example**

```ts
observer.on('simStateChange', (data: observer.SimStateData) => {
    console.info("on simStateChange, data:" + JSON.stringify(data));
});
```


## observer.on('simStateChange')<sup>7+</sup>

on\(type: 'simStateChange', options: ObserverOptions, callback: Callback\<SimStateData\>\): void

Subscribes to the SIM card status change event of the specified card slot. This API uses an asynchronous callback to return the result.

**System capability:** SystemCapability.Telephony.StateRegistry

**Parameters**

| Name   | Type                                                         | Mandatory | Description                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes   |SIM card status change event. This parameter has a fixed value of **simStateChange**.                 |
| options   | [ObserverOptions](#observeroptions11)                       | Yes   | Optional parameters for telephony-related event subscription.                                  |
| callback | Callback\<[SimStateData](#simstatedata7)\> | Yes   | Callback used to return the card status data object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Telephony Subsystem Error Codes](errorcode-telephony.md).

| ID |                 Error Message                     |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**Example**

```ts
let options: observer.ObserverOptions = {
    slotId: 0
}
observer.on('simStateChange', options, (data: observer.SimStateData) => {
    console.info("on simStateChange, data:" + JSON.stringify(data));
});
```


## observer.off('simStateChange')<sup>7+</sup>

off\(type: 'simStateChange', callback?: Callback\<SimStateData\>\): void

Unsubscribes from the SIM status change event. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> You can pass the callback specified in **on** to unsubscribe from a single subscription, or omit the callback to clear all subscriptions.

**System capability**: SystemCapability.Telephony.StateRegistry

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type | string | Yes | SIM status change event. This parameter has a fixed value of **simStateChange**. |
| callback | Callback\<[SimStateData](#simstatedata7)\> | No | Callback for the SIM status change event. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Telephony Subsystem Error Codes](errorcode-telephony.md).

| ID |                 Error Message                     |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**Example**

```ts
let callback: (data: observer.SimStateData) => void = (data: observer.SimStateData) => {
    console.info("on simStateChange, data:" + JSON.stringify(data));
}
observer.on('simStateChange', callback);
// Pass the callback specified in on to unsubscribe from a single subscription, or omit the callback to clear all subscriptions.
observer.off('simStateChange', callback);
observer.off('simStateChange');
```

## observer.on('iccAccountInfoChange')<sup>10+</sup>

on\(type: 'iccAccountInfoChange', callback: Callback\<void\>\): void

Subscribes to the card account change event. This API uses a callback as an asynchronous method.

**System capability:** SystemCapability.Telephony.StateRegistry

**Parameters**

| Name     | Type                                                         | Mandatory | Description                                                         |
| -------- | ------------------------------------------------------------ | --------- | ------------------------------------------------------------ |
| type     | string                                                       | Yes       | Card account change event. This parameter has a fixed value of **iccAccountInfoChange**.                 |
| callback | Callback\<void\> | Yes       | Callback invoked when the card account changes. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Telephony Subsystem Error Codes](errorcode-telephony.md).

| ID |                 Error Message                     |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**Example**

```ts
observer.on('iccAccountInfoChange', () => {
    console.info("on iccAccountInfoChange success");
});
```


## observer.off('iccAccountInfoChange')<sup>10+</sup>

off\(type: 'iccAccountInfoChange', callback?: Callback\<void\>\): void

Unsubscribes from the ICC account information change event. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> You can pass the callback specified in on to unsubscribe from a single subscription, or omit the callback to clear all subscriptions.

**System capability**: SystemCapability.Telephony.StateRegistry

**Parameters**

| Name     | Type                                                         | Mandatory | Description                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | ICC account information change event. This parameter has a fixed value of **iccAccountInfoChange**.                 |
| callback | Callback\<void\> | No   | Callback for the ICC account information change event. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Telephony Subsystem Error Codes](errorcode-telephony.md).

| ID |                 Error Message                     |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**Example**

```ts
let callback: () => void = () => {
    console.info("on iccAccountInfoChange success");
}
observer.on('iccAccountInfoChange', callback);
// Pass the callback specified in on to unsubscribe from a single subscription, or omit the callback to clear all subscriptions.
observer.off('iccAccountInfoChange', callback);
observer.off('iccAccountInfoChange');
```


## observer.onGetSimActiveState<sup>23+</sup>

onGetSimActiveState\(slotId: number, callback: Callback\<boolean\>\): void

Subscribes to the SIM card activation status change. This API uses an asynchronous callback to return the result.

**Required Permission:** ohos.permission.GET_TELEPHONY_STATE

**System capability:** SystemCapability.Telephony.StateRegistry

**Parameters**

| Name   | Type                                                         | Mandatory | Description                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| slotId   | number            | Yes    | Card slot ID.<br>- **0**: card slot 1.<br>- **1**: card slot 2.    |
|callback  | Callback&lt;boolean&gt;|Yes| Callback used to return whether the SIM card is activated.<br>- **true**: activated.<br>- **false**: not activated.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Telephony Subsystem Error Codes](errorcode-telephony.md).

| ID |                 Error Message                     |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                         |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

let sislotId = 0;
let simActiveState: Callback<boolean> = (isSimActive: boolean) => {
    console.info(`simActiveState slotId ${JSON.stringify(isSimActive)}`);
}
observer.onGetSimActiveState(sislotId, simActiveState);
```

## observer.offGetSimActiveState<sup>23+</sup>

offGetSimActiveState\(callback?: Callback\<boolean\>\): void

Unsubscribes from the SIM card activation status change event. This API uses an asynchronous callback to return the result.

**Required Permission:** ohos.permission.GET_TELEPHONY_STATE

**System capability:** SystemCapability.Telephony.StateRegistry

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;boolean&gt; | No | Callback for the SIM card activation status change event. It returns whether the SIM card is activated.<br>- **true**: activated.<br>- **false**: not activated. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Telephony Service Error Codes](errorcode-telephony.md).

| ID |                 Error Message                     |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                        |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Service connection failed.                   |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

let simActiveState: Callback<boolean> = (isSimActive: boolean) => {
    console.info(`simActiveState slotId ${JSON.stringify(isSimActive)}`);
}
observer.offGetSimActiveState(simActiveState);
```

## observer.onCCallStateChange<sup>23+</sup>

onCCallStateChange\(callback: Callback\<CCallStateInfo\>, options?: ObserverOptions): void

Subscribes to the carrier call status change event and obtains the call number. This API uses an asynchronous callback.

**System capability:** SystemCapability.Telephony.StateRegistry

**Required permission:** ohos.permission.MANAGE_CALL_FOR_DEVICES

**Parameters**

|     Name            |          Type      | Mandatory | Description                                    |
| ------------------- | ------------------| ---- | --------------------------------------- |
| callback | Callback\<[CCallStateInfo](js-apis-observer.md#ccallstateinfo23)\> | Yes   | Callback used to return the call status information object.<br>The app can obtain **CCallStateInfo**.<br> |
| options  | [ObserverOptions](#observeroptions11)                  | No | Optional parameter for telephony-related event subscription, which specifies the card slot ID for the event subscription. The default value is the ID of the current default data card slot.                |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Telephony Subsystem Error Codes](errorcode-telephony.md).

| ID |                 Error Message                     |
| -------- | -------------------------------------------- |
| 201      | Permission denied                         |
| 8800001  | Invalid parameter value.                     |
| 8800002  | Service connection failed.                   |
| 8800003  | System internal error.                       |
| 8800999  | Unknown error.                               |

**Example**

```ts
import { call, observer } from '@kit.TelephonyKit';

// Define the carrier call status change callback.
let callback: (data: observer.CCallStateInfo) => void = (data: observer.CCallStateInfo) => {
    console.info("onCCallStateChange, data:" + JSON.stringify(data));
};
// Set the subscription parameters and specify the card slot ID.
let options: observer.ObserverOptions = {
    slotId: 0
};

try {
    // Listen for the carrier call status (specified card slot).
    observer.onCCallStateChange(callback, options);
    // Listen for the carrier call status (without specifying a card slot).
    observer.onCCallStateChange(callback);
} catch (err) {
    console.error(`observer.onCCallStateChange failed: ${JSON.stringify(err)}`);
}
```

## observer.offCCallStateChange<sup>23+</sup>

offCCallStateChange\(callback?: Callback\<CCallStateInfo\>\): void

Unsubscribes from the carrier call status change event and obtains the call number. This API uses an asynchronous callback.

> **NOTE**
>
> You can specify a callback in **on** to unregister a single callback or unregister all callbacks without specifying a callback.

**System capability:** SystemCapability.Telephony.StateRegistry

**Required permission:** ohos.permission.MANAGE_CALL_FOR_DEVICES

**Parameters**

| Name | Type | Mandatory | Description |
| ------------------- | ------------------| ---- | --------------------------------------- |
| callback | Callback\<[CCallStateInfo](js-apis-observer.md#ccallstateinfo23)\> | No | Callback for the carrier call status change event.<br>The app can obtain **CCallStateInfo**.<br>If this parameter is not passed, all subscriptions to the carrier call status are canceled. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Telephony Error Codes](errorcode-telephony.md).

| ID |                 Error Message                     |
| -------- | -------------------------------------------- |
| 201      | Permission denied                         |
| 8800001  | Invalid parameter value.                     |
| 8800002  | Service connection failed.                   |
| 8800003  | System internal error.                       |
| 8800999  | Unknown error.                               |

**Example**

```ts
import { observer } from '@kit.TelephonyKit';

let callback: (data: observer.CCallStateInfo) => void = (data: observer.CCallStateInfo) => {
    console.info("onCCallStateChange, data:" + JSON.stringify(data));
}

observer.offCCallStateChange(callback);
observer.offCCallStateChange();
```

## observer.onCommunicationStateChange

onCommunicationStateChange\(callback: Callback\<boolean\>, options?:ObserverOptions\): void

Subscribes to the 5A network status change event. This API uses an asynchronous callback to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability:** SystemCapability.Telephony.StateRegistry

**Required permission**: ohos.permission.GET_NETWORK_INFO

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | Callback\<boolean\> | Yes | Callback invoked to return the 5A status. The value **true** indicates that the 5A status is enabled, and the value **false** indicates that the 5A status is disabled. |
| options | [ObserverOptions](#observeroptions11) | No | Optional telephony-related event subscription parameter, which specifies the card slot ID for the event subscription. The default value is the ID of the current default data card slot. |


**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Telephony Error Codes](errorcode-telephony.md).

| ID |                 Error Message                     |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |

**Example**

```ts
// Set the subscription parameters and specify the card slot ID.
let options: observer.ObserverOptions = {
    slotId: 0
}
// Define the callback for the 5A network status change.
let callback: Callback<boolean> = (isCommunicationStateOn: boolean) => {
    console.info(`communicationStateChanged ${JSON.stringify(isCommunicationStateOn)}`);
}
try {
    // Subscribe to the 5A network status change event.
    observer.onCommunicationStateChange(callback, options);
} catch (err) {
    console.error(`observer.onCommunicationStateChange failed: ${JSON.stringify(err)}`);
}
```

## observer.offCommunicationStateChange

offCommunicationStateChange\(callback: Callback\<boolean\>, options?:ObserverOptions\): void

Unsubscribes from the 5A network status change event. This API uses an asynchronous callback.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability:** SystemCapability.Telephony.StateRegistry

**Required permission**: ohos.permission.GET_NETWORK_INFO

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | Callback\<boolean\> | Yes | Callback for the 5A network status change event. The value **true** indicates that the 5A status is enabled, and **false** indicates that the 5A status is disabled. |
| options | [ObserverOptions](#observeroptions11) | No | Optional telephony-related event subscription parameter, which specifies the card slot ID for the event subscription. The default value is the ID of the current default data card slot. |


**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Telephony Subsystem Error Codes](errorcode-telephony.md).

| ID |                 Error Message                     |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |

**Example**

```ts
let options: observer.ObserverOptions = {
    slotId: 0
}
let callback: Callback<boolean> = (isCommunicationStateOn: boolean) => {
    console.info(`communicationStateChanged ${JSON.stringify(isCommunicationStateOn)}`);
}
observer.onCommunicationStateChange(callback, options);
observer.offCommunicationStateChange(callback, options);
```

## observer.onVoIPStateChange

onVoIPStateChange\(callback: Callback\<VoIPCallStateInfo\>\): void

Subscribes to the VoIP call status change event. This API uses an asynchronous callback to return the result.

**Since:** 26.0.1

**Required Permissions:** ohos.permission.MANAGE_CALL_FOR_DEVICES

**System capability:** SystemCapability.Telephony.StateRegistry

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | --------------------------------------------------------- | ---- | ---------------------------------------------------------------- |
| callback | Callback\<[VoIPCallStateInfo](#voipcallstateinfo)\> | Yes | Callback used to return the VoIP call status information. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Telephony Error Codes](errorcode-telephony.md).

| ID |                  Error Message                    |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 8800002  | Service connection failed.                   |
| 8800003  | System internal error.                       |

**Example**

```ts
import { observer } from '@kit.TelephonyKit';

let callback: (data: observer.VoIPCallStateInfo) => void = (data: observer.VoIPCallStateInfo) => {
  console.info(`onVoIPStateChange, appName: ${data.appName}, contactName: ${data.contactName}, ` +
    `callType: ${data.callType}, callState: ${data.callState} ` +
    `isVoiceAnswerSupported: ${data.isVoiceAnswerSupported}`);
}

// Subscribe to the third-party VoIP call status change.
try {
  observer.onVoIPStateChange(callback);
} catch (err) {
  console.error(`observer.onVoIPStateChange failed: ${JSON.stringify(err)}`);
}
```

## observer.offVoIPStateChange

offVoIPStateChange\(callback?: Callback\<VoIPCallStateInfo\>\): void

Unsubscribes from the VoIP call status change event. This API uses an asynchronous callback to return the result.

**Since:** 26.0.1

**Required Permissions:** ohos.permission.MANAGE_CALL_FOR_DEVICES

**System capability:** SystemCapability.Telephony.StateRegistry

**Parameters**

|  Name  |                              Type                         | Mandatory |                            Description                                   |
| -------- | --------------------------------------------------------- | ---- | ---------------------------------------------------------------- |
| callback | Callback\<[VoIPCallStateInfo](#voipcallstateinfo)\> | No   | Callback for the VoIP call status change event. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Telephony Subsystem Error Codes](errorcode-telephony.md).

| ID |                  Error Message                    |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 8800002  | Service connection failed.                   |
| 8800003  | System internal error.                       |

**Example**

```ts
import { observer } from '@kit.TelephonyKit';

let callback: (data: observer.VoIPCallStateInfo) => void = (data: observer.VoIPCallStateInfo) => {
  console.info(`onVoIPStateChange, appName: ${data.appName}, contactName: ${data.contactName}, ` +
    `callType: ${data.callType}, callState: ${data.callState} ` +
    `isVoiceAnswerSupported: ${data.isVoiceAnswerSupported}`);
}

// Unsubscribe: specify a callback to unsubscribe from a single subscription.
try {
  observer.offVoIPStateChange(callback);
} catch (err) {
  console.error(`observer.offVoIPStateChange failed: ${JSON.stringify(err)}`);
}

// Unsubscribe: unsubscribe from all subscriptions without parameters.
try {
  observer.offVoIPStateChange();
} catch (err) {
  console.error(`observer.offVoIPStateChange failed: ${JSON.stringify(err)}`);
}
```

## VoIPCallStateInfo

Defines the VoIP call status information.

**Since:** 26.0.1

**System capability:** SystemCapability.Telephony.StateRegistry

| Name | Type                                   |  Read-Only | Optional | Description |
| ----- |--------------------------------------| ----- | ---- | -----|
|  appName  | string |  No  |  No  | Name of the VoIP app. |
| contactName | string  |  No  |  No  | Name of the contact of the VoIP call. |
| callType | [VoIPCallType](#voipcalltype)  |  No  |  No  | Type of the VoIP call. |
| callState | [VoIPCallState](#voipcallstate)  |  No  |  No  | State of the VoIP call. |
| isVoiceAnswerSupported | boolean  |  No  |  No  | Whether the VoIP app supports answering the current call as a voice call.<br>- **true**: supports answering the current call as a voice call.<br>- **false**: does not support answering the current call as a voice call. |

## VoIPCallType

Enumerates the VoIP call types.

**Since:** 26.0.1

**System capability:** SystemCapability.Telephony.StateRegistry

| Name        | Value   | Description              |
| ----------- | ---- | ----------------- |
| VOICE   | 0    | Voice call.            |
| VIDEO     | 1    | Video call.           |

## VoIPCallState

Defines the VoIP call status.  

**Since:** 26.0.1

**System capability:** SystemCapability.Telephony.StateRegistry

| Name        | Value   | Description              |
| ----------- | ---- | ----------------- |
| IDLE           | 0    | VoIP call idle.            |
| INCOMING       | 1    | VoIP call incoming.           |
| OUTGOING       | 2    | VoIP call outgoing.       |
| DIALING        | 3    | VoIP call dialing.       |
| ANSWERED       | 4    | VoIP incoming call answered by the user.       |
| ACTIVE         | 5    | VoIP call active.       |
| HOLDING        | 6    | VoIP call on hold.       |
| DISCONNECTING  | 7    | VoIP call disconnecting.       |
| DISCONNECTED   | 8    | VoIP call disconnected.       |

## LockReason<sup>8+</sup>

SIM card lock type.

**System capability:** SystemCapability.Telephony.StateRegistry

| Name        | Value   | Description              |
| ----------- | ---- | ----------------- |
| SIM_NONE    | 0    | No lock.            |
| SIM_PIN     | 1    | PIN lock.           |
| SIM_PUK     | 2    | PUK lock.           |
| SIM_PN_PIN  | 3    | Network PIN lock.       |
| SIM_PN_PUK  | 4    | Network PUK lock.       |
| SIM_PU_PIN  | 5    | Subnet PIN lock.       |
| SIM_PU_PUK  | 6    | Subnet PUK lock.       |
| SIM_PP_PIN  | 7    | Service provider PIN lock. |
| SIM_PP_PUK  | 8    | Service provider PUK lock. |
| SIM_PC_PIN  | 9    | Corporate PIN lock.       |
| SIM_PC_PUK  | 10   | Corporate PUK lock.       |
| SIM_SIM_PIN | 11   | SIM PIN lock.       |
| SIM_SIM_PUK | 12   | SIM PUK lock.       |


## SimStateData<sup>7+</sup>

SIM card type and status.

**System capability:** SystemCapability.Telephony.StateRegistry

|     Name             |                 Type                 | Read-Only | Optional | Description |
| -------------------- | ------------------------------------ | --------- | -------- | -------------------------------------------------------- |
| type                 | [CardType](js-apis-sim.md#cardtype7) | No        | No       | SIM card type. |
| state                | [SimState](js-apis-sim.md#simstate)  | No        | No       | SIM card status. |
| reason<sup>8+</sup>  | [LockReason](#lockreason8)           | No        | No       | SIM card lock type. |


## CallStateInfo<sup>11+</sup>

Describes the call status information.

**System capability:** SystemCapability.Telephony.StateRegistry

|     Name             |                  Type                    | Read-Only | Optional | Description     |
| ------------------- | -------------------------------------- | ---- | ---- | -------- |
| state               | [CallState](js-apis-call.md#callstate) | No   | No   | Call status. |
| number              | string                                 | No   | No   | Phone number. This parameter is controlled by system permissions and available only to system apps. Third-party apps cannot obtain it. |


## CCallStateInfo<sup>23+</sup>

Call status information.

**System capability:** SystemCapability.Telephony.StateRegistry

|     Name            |                 Type                    | Read-Only | Optional | Description     |
| ------------------- | -------------------------------------- | ---- | ---- | -------- |
| state               | [CCallState](js-apis-call.md#ccallstate23) | No   | No   | Call status. |
| teleNumber              | string                                 | No   | No   | Phone number. |


## DataConnectionStateInfo<sup>11+</sup>

Information about the data connection status.

**System capability**: SystemCapability.Telephony.StateRegistry


| Name | Type                                   |  Read-Only | Optional | Description |
| ----- |--------------------------------------| ----- | ---- | -----|
|  state   | [DataConnectState](js-apis-telephony-data.md#dataconnectstate) |  No  |  No  | Data connection status. |
| network | [RatType](#rattype)  |  No  |  No  | Network type. |

## ObserverOptions<sup>11+</sup>

Optional parameters for telephony-related event subscription.

**System capability:** SystemCapability.Telephony.StateRegistry

| Name | Type | Read-Only | Optional | Description |
| ------------------- | ------------------| ---- | ---- | --------------------------------------- |
| slotId | number | No | No | Card slot ID.<br>- **0**: slot 1<br>- **1**: slot 2 |
