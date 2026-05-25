# @ohos.inputMethodSystemPanelManager (Input Method System Panel Manager) (System API)
<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @codexu62-->
<!--Designer: @andeszhang-->
<!--Tester: @murphy84-->
<!--Adviser: @zhang_yixin13-->

This module provides the input method system panel management functions, which are used for communication and state synchronization between the input method system panel and the system-default input method application.

**Since**: 26.0.0

> **NOTE**
>
> The APIs provided by this module are system APIs.
>
> This module supports only the stage model.

## Modules to Import

```ts
import { inputMethodSystemPanelManager } from '@kit.IMEKit';
```

## SystemPanelStatus

Describes the system panel state information.

It describes the input type, panel flag, bring-up state, and whether function buttons are required. When the system panel state changes, the [onSystemPanelStatusChange](#inputmethodsystempanelmanageronsystempanelstatuschange) API is called to notify the subscriber.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| inputType | [InputMethodInputType](#inputmethodinputtype) | No| No| Input type of the input method.|
| panelFlag | [PanelFlag](js-apis-inputmethod-panel.md#panelflag) | No| No| Panel flag of the input method soft keyboard panel, indicating the panel's display state (fixed, floating, or candidate state).|
| isPanelRaised | boolean | No| No| Whether the system panel requires bottom elevation. The value **true** indicates yes, and the value **false** indicates no.|
| needFuncButton | boolean | No| No| Whether the system panel requires a function button. The value **true** indicates yes, and the value **false** indicates no.|

## InputMethodInputType

Enumerates input types,

which are used to identify the input modes supported by the system panel. Different input types correspond to different input scenarios and panel layouts.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

| Name| Value| Description|
| -------- | -------- | -------- |
| NONE | -1 | No input.|
| CAMERA_INPUT | 0 | Camera input, indicating that the system is in camera input mode. This type is typically used for capture input scenarios.|
| SECURITY_INPUT | 1 | Security input, indicating that the system panel is in secure input mode. This type is used for entering sensitive information such as passwords.|
| VOICE_INPUT | 2 | Voice input, indicating that the system panel is in voice input mode. This type is used for voice-to-text input.|
| FLOATING_VOICE_INPUT | 3 | Floating voice input, indicating that the system panel is in floating voice input mode and provides the voice input function in a floating window.|

## CommandDataType

type CommandDataType = number | string | boolean

Describes the private data type, which varies depending on its function.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

| Type| Description|
| -------- | -------- |
| number | Number.|
| string | String.|
| boolean | Boolean.|

## inputMethodSystemPanelManager.onSystemPrivateCommand

onSystemPrivateCommand(callback: Callback\<Record\<string, CommandDataType\>\>): void

Subscribes to events that the system-default input method application sends a private data command.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | Callback\<Record\<string, [CommandDataType](#commanddatatype)\>\> | Yes| Callback function, which is triggered when the input method application or system service sends a private data command.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message|
| -------- | -------- |
| 202 | not system application. |

**Example**

```ts
try {
  inputMethodSystemPanelManager.onSystemPrivateCommand((data) => {
    console.info('Received private command: ' + JSON.stringify(data));
  });
} catch (err) {
  console.error(`Failed to subscribe to private command. Code: ${err.code}, Message: ${err.message}`);
}
```

## inputMethodSystemPanelManager.offSystemPrivateCommand

offSystemPrivateCommand(callback?: Callback\<Record\<string, CommandDataType\>\>): void

Unsubscribes from events that the system-default input method application sends a private data command.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | Callback\<Record\<string, [CommandDataType](#commanddatatype)\>\> | No| Callback function. If this parameter is left empty, all callbacks will be unsubscribed from.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message|
| -------- | -------- |
| 202 | not system application. |

**Example**

```ts
try {
  inputMethodSystemPanelManager.offSystemPrivateCommand();
} catch (err) {
  console.error(`Failed to unsubscribe from private command. Code: ${err.code}, Message: ${err.message}`);
}
```

## inputMethodSystemPanelManager.onSystemPanelStatusChange

onSystemPanelStatusChange(callback: Callback\<SystemPanelStatus\>): void

Subscribes to system panel state change events.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | Callback\<[SystemPanelStatus](#systempanelstatus)\> | Yes| Callback function, which is triggered when the system panel state changes.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message|
| -------- | -------- |
| 202 | not system application. |

**Example**

```ts
try {
  inputMethodSystemPanelManager.onSystemPanelStatusChange((status) => {
    console.info('Panel status changed: ' + JSON.stringify(status));
  });
} catch (err) {
  console.error(`Failed to subscribe to panel status change. Code: ${err.code}, Message: ${err.message}`);
}
```

## inputMethodSystemPanelManager.offSystemPanelStatusChange

offSystemPanelStatusChange(callback?: Callback\<SystemPanelStatus\>): void

Unsubscribes from system panel state change events.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | Callback\<[SystemPanelStatus](#systempanelstatus)\> | No| Callback function. If this parameter is left empty, all callbacks will be unsubscribed from.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message|
| -------- | -------- |
| 202 | not system application. |

**Example**

```ts
try {
  inputMethodSystemPanelManager.offSystemPanelStatusChange();
} catch (err) {
  console.error(`Failed to unsubscribe from panel status change. Code: ${err.code}, Message: ${err.message}`);
}
```

## inputMethodSystemPanelManager.sendPrivateCommand

sendPrivateCommand(commandData: Record\<string, CommandDataType\>): Promise\<void\>

Sends a private command to the system-default input method application.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| commandData | Record\<string, [CommandDataType](#commanddatatype)\> | Yes| Command data to be sent. The maximum size is 32 KB, and a maximum of five commands are allowed.|

**Returns**

| Type| Description|
| -------- | -------- |
| Promise\<void\> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message|
| -------- | -------- |
| 202 | not system application. |
| 12800026 | input method system panel error. Possible causes: 1. system panel not connected. 2. ipc failed due to large amount of data transferred or other reasons. 3. the caller is not system panel. |

**Example**

```ts
try {
  let commandData: Record<string, inputMethodSystemPanelManager.CommandDataType> = {
    'key1': 1,
    'key2': true,
    'key3': '123',
  };
  inputMethodSystemPanelManager.sendPrivateCommand(commandData).then(() => {
    console.info('Private command sent successfully');
  }).catch((e: BusinessError) => {
    console.error(`Failed to send private command. Code: ${e.code}, Message: ${e.message}`);
  })
} catch (e) {
  console.error(`Failed to send private command. Code: ${e.code}, Message: ${e.message}`);
}
```

## inputMethodSystemPanelManager.connectSystemChannel

connectSystemChannel(): Promise\<void\>

Connects to the system channel for communication between the input method system panel and the system-default input method application. This API can be called only by the input method system panel.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API**: This is a system API.

**Required permissions**: ohos.permission.CONNECT_IME_ABILITY

**Returns**

| Type| Description|
| -------- | -------- |
| Promise\<void\> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message|
| -------- | -------- |
| 201 | permissions check fails. |
| 202 | not system application. |
| 12800008 | input method manager service error. Possible causes: a system error, such as null pointer, IPC exception. |
| 12800026  | input method system panel error. Possible causes: 1. the system panel not connected.2. ipc failed due to the large amount of data transferred or other reasons. 3. the caller is not system panel.|

**Example**

```ts
try {
  inputMethodSystemPanelManager.connectSystemChannel().then(() => {
    console.info('System channel connected successfully');
  }).catch((e: BusinessError) => {
    console.error(`Failed to connect system channel. Code: ${e.code}, Message: ${e.message}`);
  })
} catch (e) {
  console.error(`Failed to connect system channel. Code: ${e.code}, Message: ${e.message}`);
}
```
