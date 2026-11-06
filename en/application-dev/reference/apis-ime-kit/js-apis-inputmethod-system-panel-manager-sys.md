# @ohos.inputMethodSystemPanelManager (Input Method System Panel Manager) (System API)
<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @codexu62-->
<!--Designer: @zhaolinglan-->
<!--Tester: @murphy84-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=bd0f7f0d2b5cbb7da282700783b226eef5361df4 translatedAt=2026-11-03T04:26:24.653Z pushedAt=2026-11-03T12:08:25.482Z nl=1 -->

The @ohos.inputMethodSystemPanelManager module is an input method system panel management module for system applications. It is used for communication and state synchronization between the input method system panel and the system preset input method application.

This module is a system API module that provides a bidirectional communication channel between the input method system panel (a system-level panel component) and the system preset input method application. Through this module, the system panel can sense input method state changes, receive private commands sent by the input method application, and send private commands to the input method application.

This module provides three core capabilities: 1) establish a communication channel between the system panel and the input method application through `connectSystemChannel`; 2) subscribe to system panel state changes (including input type, panel flag, panel raised state, and function button requirements) through `onSystemPanelStatusChange`, based on which the system panel adaptively adjusts its own layout; 3) implement bidirectional private data communication between the system panel and the input method application through `onSystemPrivateCommand`/`sendPrivateCommand`, which is used to transmit custom commands and configuration data.

This module is used when developing the input method system panel (a system-level panel component). When the system panel needs to work with the system preset input method application, it must first call `connectSystemChannel` to establish the channel, and then subscribe to state change and private command events.

The core open capabilities of this module are carried by the following key types:

| Interface/Enum | Description |
|---|---|
| SystemPanelStatus | System panel state information, describing the current system panel's input type (InputMethodInputType), panel flag (PanelFlag), panel raised state, and function button requirements. When the input method state changes, the system panel adjusts its own layout by subscribing to this state. |
| InputMethodInputType | Input type enumeration, identifying the input modes supported by the system panel, including no input, camera input, secure input, voice input, and floating voice input, corresponding to different input scenarios and panel layouts. |
| CommandDataType | Private data type union (number, string, boolean), used to define the specific types of parameters in private command communication. |

The core functions of this module are provided directly through namespace-level functions, without the need to obtain an instance object:

- Private data command communication: bidirectional custom data transmission between the system panel and the input method application. The system panel can send private commands to the input method application through [sendPrivateCommand](#inputmethodsystempanelmanagersendprivatecommand), and receive private commands sent by the input method application through [onSystemPrivateCommand](#inputmethodsystempanelmanageronsystemprivatecommand). The private data channel is often used by device-level vendors to implement custom input method functions on specific devices.
- Panel state synchronization: the system panel subscribes to and obtains panel state change notifications through [onSystemPanelStatusChange](#inputmethodsystempanelmanageronsystempanelstatuschange), including input type, panel flag, bottom elevation state, and function button requirements.

The relationship between this module and other modules of the input method framework is as follows:

- [@ohos.inputMethodEngine](js-apis-inputmethodengine.md): targets input method applications and provides the input method server capabilities. On the input method application side, [inputMethodEngine.on('privateCommand')](js-apis-inputmethodengine.md#onprivatecommand12) is used to receive private commands sent by the system panel, and [inputMethodEngine.sendPrivateCommand](js-apis-inputmethodengine.md#sendprivatecommand12) (the TextInputClient method) is used to send private commands to a text box or a system component.
- [@ohos.inputMethod.Panel](js-apis-inputmethod-panel.md): defines the panel attribute types [PanelFlag](js-apis-inputmethod-panel.md#panelflag) and [PanelType](js-apis-inputmethod-panel.md#paneltype). The SystemPanelStatus of this module references the PanelFlag type.
- @ohos.inputMethodSystemPanelManager (this module): targets the system panel and provides the communication and state synchronization capabilities between the system panel and the input method application.

Typical calling process: [connectSystemChannel](#inputmethodsystempanelmanagerconnectsystemchannel) (establish a communication channel) → [onSystemPrivateCommand](#inputmethodsystempanelmanageronsystemprivatecommand) / [onSystemPanelStatusChange](#inputmethodsystempanelmanageronsystempanelstatuschange) (subscribe to events) → [sendPrivateCommand](#inputmethodsystempanelmanagersendprivatecommand) (send a private command). Before using the communication and subscription APIs of this module, you must call connectSystemChannel first to establish the system channel connection.

Using this module requires the coordination of multiple APIs: first call `connectSystemChannel` to establish the communication channel -> then subscribe to the state change and private command events -> process the state data and private commands in the event callbacks -> send commands to the input method application through `sendPrivateCommand`.

```javascript
// The following is pseudocode that illustrates the calling logic.

// 1. Connect the system channel (must be called before other operations).
inputMethodSystemPanelManager.connectSystemChannel();

// 2. Subscribe to the system panel state change event.
inputMethodSystemPanelManager.onSystemPanelStatusChange((status) => {
  // Adjust the panel layout based on status.inputType (camera/secure/voice, etc.).
  // Switch the panel state based on status.panelFlag (fixed/floating/candidate).
  // Determine whether to elevate the bottom based on status.isPanelRaised.
  // Determine whether to display the function button based on status.needFuncButton.
});

// 3. Subscribe to the private command sent by the input method application.
inputMethodSystemPanelManager.onSystemPrivateCommand((commandData) => {
  // Handle the custom command sent by the input method application.
});

// 4. Send a private command to the input method application.
inputMethodSystemPanelManager.sendPrivateCommand({ 'key1': 1, 'key2': 'value' });

// 5. Unsubscribe when no longer needed.
inputMethodSystemPanelManager.offSystemPanelStatusChange();
inputMethodSystemPanelManager.offSystemPrivateCommand();
```

> **NOTE**
>
> `connectSystemChannel` must be called before subscribing to events and sending commands. Otherwise, the related operations will return error code 12800026 because the channel is not connected.

**Model restriction:** This API can be used only in the stage model.

**System API:** This is a system API.

**Since:** 26.0.0

## Importing Modules

```ts
import { inputMethodSystemPanelManager } from '@kit.IMEKit';
```

## SystemPanelStatus

System panel state information, used to describe the input type, panel flag, raised state, and function button requirement of the current system panel. When the system panel state changes, subscribers are notified through [onSystemPanelStatusChange](#inputmethodsystempanelmanageronsystempanelstatuschange).

**System capability:** SystemCapability.MiscServices.InputMethodFramework

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| inputType | [InputMethodInputType](#inputmethodinputtype) | No | No | Input type of the input method, indicating the input mode in which the current system panel is.<br>Usage scenario: when the panel behavior or layout needs to be adjusted based on different input modes, use this attribute to determine the current input type.<br>Post-use effect: different inputType values correspond to different panel interaction behaviors. For example, in the SECURITY_INPUT type, the panel enters the secure input mode. |
| panelFlag | [PanelFlag](js-apis-inputmethod-panel.md#panelflag) | No | No | Panel flag of the input method soft keyboard panel, indicating the display state of the panel (fixed, floating, or candidate).<br>Usage scenario: when the layout or interaction behavior needs to be adjusted based on the panel display state, use this attribute.<br>Post-use effect: different panelFlag values correspond to different panel display forms: FLAG_FIXED indicates that the panel is fixed at the bottom of the screen, FLAG_FLOATING indicates that the panel is displayed in a floating manner, and FLAG_CANDIDATE indicates that the panel is a candidate word window.<br>Coordination/constraint relationship between related parameters: panelFlag is currently used only for panels of the SOFT_KEYBOARD type. |
| isPanelRaised | boolean | No | No | Whether the system panel needs bottom elevation. The value true indicates that the panel needs bottom elevation (the bottom area of the panel is shifted upward to leave space for other UI elements below), and false indicates that it does not.<br>Usage scenario: when other UI elements (such as a navigation bar or toolbar) need to be displayed below the system panel, set this attribute to true to raise the bottom of the panel and prevent the panel from covering the content below.<br>Post-use effect: when set to true, the bottom area of the panel is shifted upward; when set to false, the panel is displayed normally without elevation. |
| needFuncButton | boolean | No | No | Whether the system panel needs a function button. The value true indicates that the panel needs to display function buttons (such as operation buttons for settings and switching input methods), and false indicates that it does not.<br>Usage scenario: when a shortcut function entry needs to be provided on the panel, set this attribute to true to display the function button in the panel area.<br>Post-use effect: when set to true, the function button area is displayed on the panel; when set to false, the function button area is not displayed on the panel. |

## InputMethodInputType

Enumerates the input types used to indicate the input modes supported by the system panel. Different input types correspond to different input scenarios and panel layouts.

**System capability:** SystemCapability.MiscServices.InputMethodFramework

| Name | Value | Description |
| -------- | -- | -------- |
| NONE | -1 | No input type, indicating that the system panel is not in any specific input mode.<br>Usage scenario: used when the system panel is in the default or unknown input state. |
| CAMERA_INPUT | 0 | Camera input type, indicating that the system is in camera input mode.<br>Usage scenario: used for scenarios such as capture input, for example, scanning text or objects with the camera for input.<br>Post-use effect: the panel switches to camera input mode and interacts with camera-related functions. |
| SECURITY_INPUT | 1 | Secure input type, indicating that the system panel is in secure input mode.<br>Usage scenario: used for sensitive information input scenarios such as passwords and verification codes, where the system enables the secure input protection mechanism.<br>Post-use effect: the panel enters secure input mode, and the input content is not recorded or cached, preventing sensitive information leakage. |
| VOICE_INPUT | 2 | Voice input type, indicating that the system panel is in voice input mode.<br>Usage scenario: used for speech-to-text input scenarios, where the user inputs by voice.<br>Post-use effect: the panel switches to voice input mode and displays the voice input interaction UI (such as the microphone button and voice recognition status). |
| FLOATING_VOICE_INPUT | 3 | Floating voice input type, indicating that the system panel is in floating voice input mode.<br>Usage scenario: compared with VOICE_INPUT, this type provides the voice input function in the form of a floating window, and is suitable for scenarios where voice input is required without occupying a fixed panel area.<br>Post-use effect: the panel displays the voice input interaction UI in the form of a floating window without occupying a fixed panel area. |

## CommandDataType

type CommandDataType = number | string | boolean

Indicates the data type of the value in a private data command. The specific type of an API parameter depends on its function. The key is the command name (of the string type), and the value is the command data value (of the number, string, or boolean type).

**System capability:** SystemCapability.MiscServices.InputMethodFramework

| Type | Description |
| -------- | -------- |
| number | Number type, used to indicate numeric command data, such as switch status codes and configuration parameter values. |
| string | String type, used to indicate text command data, such as command identifiers, text content, and path information. |
| boolean | Boolean type, used to indicate switch command data, such as the enabled/disabled state of a function. |

## inputMethodSystemPanelManager.onSystemPrivateCommand

onSystemPrivateCommand(callback: Callback&lt;Record&lt;string, CommandDataType&gt;&gt;): void

Subscribes to the event of the system preset input method application sending private data commands. When the input method application sends a private command to the system component through [inputMethodEngine.sendPrivateCommand](js-apis-inputmethodengine.md#sendprivatecommand12) (TextInputClient method), the system panel receives the command data through this callback.

Usage scenario: use this API when the system panel needs to receive private data commands (such as custom configurations and state notifications) from the input method application.

Post-use effect: after a successful subscription, whenever the input method application sends a private command, the system panel receives the command data in the Record&lt;string, CommandDataType&gt; format through the callback.

Prerequisite: you must call [connectSystemChannel](#inputmethodsystempanelmanagerconnectsystemchannel) first to establish the system channel connection.

Coordination/constraint relationship between related APIs: this API is the private command receiving API on the system panel side, corresponding to [inputMethodEngine.sendPrivateCommand](js-apis-inputmethodengine.md#sendprivatecommand12) (sender) and [inputMethodEngine.on('privateCommand')](js-apis-inputmethodengine.md#onprivatecommand12) (receiver on the input method application side) on the input method application side. Private command communication direction: input method application → system panel.

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| callback | Callback&lt;Record&lt;string, [CommandDataType](#commanddatatype)&gt;&gt;| Yes | Callback invoked when the input method application sends a private data command.<br>Usage scenario: This callback must be provided to process the private command data sent by the input method application.<br>Post-use effect: When the callback is triggered, the parameter is in the Record<string, CommandDataType> format, where the key is the command name and the value is the command data value (supporting number, string, and boolean types).<br>Note: The data format in the callback is a key-value pair mapping. Developers need to determine the command type based on the key value and execute the corresponding logic. |

**Error codes**

For details about the following error codes, see [Universal Error Code Reference](../errorcode-universal.md).

| ID | Error Message |
| -------- | -------- |
| 202 | Permission verification failed. A non-system application calls a system API. |

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

offSystemPrivateCommand(callback?: Callback&lt;Record&lt;string, CommandDataType&gt;&gt;): void

Unsubscribes from the event of the system preset input method application sending private data commands.

Usage scenario: use this API when the system panel no longer needs to receive private command notifications from the input method application, for example, when the panel is closed or exits.

Coordination/constraint relationship between related APIs: after unsubscribing, the callback previously registered through [onSystemPrivateCommand](#inputmethodsystempanelmanageronsystemprivatecommand) will no longer be triggered.

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| callback | Callback&lt;Record&lt;string, [CommandDataType](#commanddatatype)&gt;&gt; | No | Callback for the private command event.<br>Usage scenario: when a specific callback to be unsubscribed is passed in, only the subscription of that callback is canceled.<br>Default value: when no callback is passed in, all subscribed onSystemPrivateCommand callbacks are canceled.<br>Note: it is recommended to pass in the reference of the specific callback to be unsubscribed, to avoid canceling all callbacks and thereby removing the callbacks of other subscribers. |

**Error codes**

For details about the following error codes, see [Universal Error Code Reference](../errorcode-universal.md).

| ID | Error Message |
| -------- | -------- |
| 202 | Permission verification failed. A non-system application calls a system API. |

**Example**

```ts
try {
  inputMethodSystemPanelManager.offSystemPrivateCommand();
} catch (err) {
  console.error(`Failed to unsubscribe from private command. Code: ${err.code}, Message: ${err.message}`);
}
```

## inputMethodSystemPanelManager.onSystemPanelStatusChange

onSystemPanelStatusChange(callback: Callback&lt;SystemPanelStatus&gt;): void

Subscribes to the system panel state change event. When the input type, panel flag, bottom elevation state, or function button requirement of the system panel changes, the callback is triggered to notify the subscriber.

Usage scenario: use this API when the system panel needs to perceive its own state changes and make corresponding adjustments, such as switching the panel layout based on the input type or adjusting the display form based on the panel flag.

Post-use effect: after a successful subscription, whenever the system panel state changes, the system passes the latest [SystemPanelStatus](#systempanelstatus) object through the callback, which contains the current input type, panel flag, bottom elevation state, and function button requirement.

Prerequisite: call [connectSystemChannel](#inputmethodsystempanelmanagerconnectsystemchannel) first to establish the system channel connection.

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| callback | Callback&lt;[SystemPanelStatus](#systempanelstatus)&gt;| Yes | Callback invoked when the system panel state changes.<br>Usage scenario: this callback must be provided to handle the panel state change notification.<br>Post-use effect: when the callback is triggered, the parameter is a [SystemPanelStatus](#systempanelstatus) object, and developers can adjust the layout and behavior of the panel based on the values of its attributes. |

**Error codes**

For details about the following error codes, see [Universal Error Code Reference](../errorcode-universal.md).

| ID | Error message |
| -------- | -------- |
| 202 | Permission verification failed. A non-system application calls a system API. |

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

offSystemPanelStatusChange(callback?: Callback&lt;SystemPanelStatus&gt;): void

Unsubscribes from the system panel state change event.

Usage scenario: Use this API when the system panel no longer needs to receive panel state change notifications, for example, when the panel is closed or exits.

Coordination/constraint relationship between related APIs: After unsubscribing, the callback previously registered through [onSystemPanelStatusChange](#inputmethodsystempanelmanageronsystempanelstatuschange) will no longer be triggered.

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| callback | Callback&lt;[SystemPanelStatus](#systempanelstatus)&gt;| No | Callback for the system panel state change event.<br>Usage scenario: When a specific callback to be unsubscribed is passed in, only the subscription of that callback is canceled.<br>Default value: If no callback is passed in, all subscribed onSystemPanelStatusChange callbacks are canceled.<br>Note: It is recommended to pass in the reference of the specific callback to be unsubscribed to avoid canceling all callbacks, which would also remove the callbacks of other subscribers. |

**Error codes**

For details about the following error codes, see [Universal Error Code Reference](../errorcode-universal.md).

| ID | Error Message |
| -------- | -------- |
| 202 | Permission verification failed. A non-system application calls a system API. |

**Example**

```ts
try {
  inputMethodSystemPanelManager.offSystemPanelStatusChange();
} catch (err) {
  console.error(`Failed to unsubscribe from panel status change. Code: ${err.code}, Message: ${err.message}`);
}
```

## inputMethodSystemPanelManager.sendPrivateCommand

sendPrivateCommand(commandData: Record&lt;string, CommandDataType&gt;): Promise&lt;void&gt;

Sends a private command to the system preset input method application. This API uses a promise to return the result asynchronously.

Meaning/function: The system panel sends custom private data commands to the system preset input method application. The data format is a key-value pair mapping (Record<string, CommandDataType>).

Usage scenario: Use this API when the system panel needs to send private data such as custom configuration commands and state notifications to the input method application. The private data channel is a communication mechanism between the system preset input method application and specific system components, and is commonly used by device-level vendors to implement custom input method functions on specific devices.

Post-use effect: After the call, the private command data is sent to the current system preset input method application. The input method application can receive this command data through [inputMethodEngine.on('privateCommand')](js-apis-inputmethodengine.md#onprivatecommand12).

Prerequisite: You must first call [connectSystemChannel](#inputmethodsystempanelmanagerconnectsystemchannel) to establish the system channel connection.

Coordination/constraint relationship between related APIs: This API is the private command sending API on the system panel side, corresponding to [inputMethodEngine.on('privateCommand')](js-apis-inputmethodengine.md#onprivatecommand12) (the receiving end) on the input method application side. The private command communication direction is: system panel → input method application.

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| commandData | Record&lt;string, [CommandDataType](#commanddatatype)&gt; | Yes | Command data to send, in the format of a key-value pair mapping, where the key is the command name (string type) and the value is the command data value (number, string, or boolean type).<br>Usage scenario: used to transmit custom communication data between the system panel and the input method application.<br>Value range: the total size is up to 32 KB, and the number of key-value pairs is up to 5. If this range is exceeded, error code 12800026 is returned.<br>Note: pay attention to the constraints and limitations on the amount of data transferred over IPC. The total amount of data transferred at the IPC layer in a single API call equals the amount of data sent by the application side plus the necessary data required for system-layer processing. Therefore, the actual maximum amount of data that can be sent is less than 32 KB. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. It is resolved when the command is sent successfully, and rejected with a BusinessError object when the command fails to be sent. |

**Error codes**

For details about the following error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Code Reference](../errorcode-universal.md).

| ID | Error Message |
| -------- | -------- |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 12800026 | input method system panel error. Possible causes: 1. the system panel not connected. 2. ipc failed due to the large amount of data transferred or other reasons. 3. the caller is not system panel. |

**Example**

```ts
try {
  let commandData: Record<string, CommandDataType> = {
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

connectSystemChannel(): Promise&lt;void&gt;

Connects the system channel to establish communication between the input method system panel and the system preset input method application. Only the system preset input method panel is allowed to call this API.

Meaning/Function: Establishes the communication channel between the system panel and the system preset input method application, providing the connection basis for subsequent private command sending/receiving and panel state synchronization.

Usage scenario: When the system panel needs to perform private command communication or panel state synchronization with the system preset input method application, this API must be called first to establish the communication channel.

Post-use effect: After the connection succeeds, the communication channel between the system panel and the input method application is established. Subsequently, APIs such as [sendPrivateCommand](#inputmethodsystempanelmanagersendprivatecommand), [onSystemPrivateCommand](#inputmethodsystempanelmanageronsystemprivatecommand), and [onSystemPanelStatusChange](#inputmethodsystempanelmanageronsystempanelstatuschange) can be called for data communication and state synchronization.

Prerequisite: The ohos.permission.CONNECT_IME_ABILITY permission is required, and the caller must be a system application and the system preset input method panel.

Coordination/constraint relationship between related APIs: This API is the prerequisite for using other communication APIs of this module. The channel must be established by calling connectSystemChannel before APIs such as [sendPrivateCommand](#inputmethodsystempanelmanagersendprivatecommand), [onSystemPrivateCommand](#inputmethodsystempanelmanageronsystemprivatecommand), and [onSystemPanelStatusChange](#inputmethodsystempanelmanageronsystempanelstatuschange) can be used.

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Required permissions:** ohos.permission.CONNECT_IME_ABILITY

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. It is resolved when the connection succeeds, and rejected with a BusinessError object when it fails. |

**Error codes**

For details about the following error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Code Reference](../errorcode-universal.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
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
