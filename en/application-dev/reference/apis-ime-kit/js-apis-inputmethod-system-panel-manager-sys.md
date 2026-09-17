# @ohos.inputMethodSystemPanelManager (Input Method System Panel Manager) (System API)
<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @codexu62-->
<!--Designer: @andeszhang-->
<!--Tester: @murphy84-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=4c244f2ed12456a4c6059eccff764e442d7872b9 translatedAt=2026-09-02T11:45:53.288Z pushedAt=2026-09-09T10:04:35.136Z -->

The **@ohos.inputMethodSystemPanelManager** module is an input method system panel management module for system applications. It is used for communication and state synchronization between the input method system panel and the system preset input method application.

This module is a system API module that provides a bidirectional communication channel between the input method system panel (a system-level panel component) and the system preset input method application. Through this module, the system panel can sense input method state changes, receive private commands sent by the input method application, and send private commands to the input method application.

This module provides three core capabilities: (1) establish a communication channel between the system panel and the input method application through `connectSystemChannel`; (2) subscribe to system panel state changes (including input type, panel flag, panel bring-up state, and function button requirements) through `onSystemPanelStatusChange`, based on which the system panel adaptively adjusts its own layout; (3) implement bidirectional private data communication between the system panel and the input method application through `onSystemPrivateCommand`/`sendPrivateCommand`, which is used to transmit custom commands and configuration data.

Use this module when developing the input method system panel (a system-level panel component). When the system panel needs to work with the system preset input method application, call `connectSystemChannel` first to establish the channel, and then subscribe to state changes and private command events. This module can be called only by system applications and supports only the stage model.

Core open capabilities of this module are provided by the key types below:

| Interface/Enum | Description |
|---|---|
| SystemPanelStatus | System panel state information, which describes the input type (**InputMethodInputType**), panel flag (**PanelFlag**), panel bring-up state, and function button requirements of the current system panel. When the input method state changes, the system panel adjusts its own layout by subscribing to this state. |
| InputMethodInputType | Input type enumeration, which identifies the input modes supported by the system panel, including no input, camera input, secure input, voice input, and floating voice input, corresponding to different input scenarios and panel layouts. |
| CommandDataType | Union type of private data types (number, string, Boolean), used to define the specific types of parameters in private command communication. |

Core features of this module are provided directly through namespace-level functions, without the need to obtain an instance object:

- Private command communication: bidirectional custom data transmission between the system panel and the input method application. The system panel can send private commands to the input method application through [sendPrivateCommand](#inputmethodsystempanelmanagersendprivatecommand), and receive private commands sent by the input method application through [onSystemPrivateCommand](#inputmethodsystempanelmanageronsystemprivatecommand). The private data channel is often used by device-level vendors to implement custom input method features on specific devices.
- Panel state synchronization: the system panel subscribes to and obtains panel state change notifications through [onSystemPanelStatusChange](#inputmethodsystempanelmanageronsystempanelstatuschange), including input type, panel flag, bottom elevation state, and function button requirements.

The relationship between this module and other modules in the input method framework is as follows:

- [@ohos.inputMethodEngine](js-apis-inputmethodengine.md): provides input method service capabilities for input method applications. On the input method application side, private commands sent by the system panel are received through [inputMethodEngine.on('privateCommand')](js-apis-inputmethodengine.md#onprivatecommand12), and private commands are sent to the text box or system component through [inputMethodEngine.sendPrivateCommand](js-apis-inputmethodengine.md#sendprivatecommand12) (the **TextInputClient** method).
- [@ohos.inputMethod.Panel](js-apis-inputmethod-panel.md): defines the panel attribute types [PanelFlag](js-apis-inputmethod-panel.md#panelflag) and [PanelType](js-apis-inputmethod-panel.md#paneltype). The **SystemPanelStatus** of this module references the **PanelFlag** type.
- **@ohos.inputMethodSystemPanelManager** (this module): Oriented to the system panel, provides communication and state synchronization between the system panel and the input method application.

Typical call flow: [connectSystemChannel](#inputmethodsystempanelmanagerconnectsystemchannel) (establish a communication channel) → [onSystemPrivateCommand](#inputmethodsystempanelmanageronsystemprivatecommand)/[onSystemPanelStatusChange](#inputmethodsystempanelmanageronsystempanelstatuschange) (subscribe to events) → [sendPrivateCommand](#inputmethodsystempanelmanagersendprivatecommand) (send a private command). Before using the communication and subscription APIs of this module, you must call **connectSystemChannel** first to establish the system channel connection.

Using this module requires the cooperation of multiple APIs: first call `connectSystemChannel` to establish a communication channel -> subscribe to state changes and private command events -> process state data and private commands in event callbacks -> send commands to the input method application through `sendPrivateCommand`.

```javascript
// The following is pseudocode for illustrating the call logic.

// 1. Connect the system channel (call this API before performing other operations).
inputMethodSystemPanelManager.connectSystemChannel();

// 2. Subscribe to system panel state change events.
inputMethodSystemPanelManager.onSystemPanelStatusChange((status) => {
  // Adjust the panel layout based on status.inputType (camera/secure/voice, etc.).
  // Switch the panel state based on status.panelFlag (fixed/floating/candidate).
  // Determine whether to apply bottom elevation based on status.isPanelRaised.
  // Determine whether to display the function button based on status.needFuncButton.
});

// 3. Subscribe to private commands sent by the input method application.
inputMethodSystemPanelManager.onSystemPrivateCommand((commandData) => {
  // Process custom commands sent by the input method application.
});

// 4. Send a private command to the input method application.
inputMethodSystemPanelManager.sendPrivateCommand({ 'key1': 1, 'key2': 'value' });

// 5. Unsubscribe from registered listeners when the listeners are no longer required.
inputMethodSystemPanelManager.offSystemPanelStatusChange();
inputMethodSystemPanelManager.offSystemPrivateCommand();
```

> **Note:**
>
> `connectSystemChannel` must be called before event subscription and command sending. Otherwise, the related operations will return error code 12800026 because the channel is not connected.

**Since**: 26.0.0

## Modules to Import

```ts
import { inputMethodSystemPanelManager } from '@kit.IMEKit';
```

## SystemPanelStatus

System panel state information, used to describe the input type, panel flag, raised state, and function button requirements of the current system panel. When the system panel state changes, subscribers are notified through the [onSystemPanelStatusChange](#inputmethodsystempanelmanageronsystempanelstatuschange) API.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| inputType | [InputMethodInputType](#inputmethodinputtype) | No | No | Input type of the input method, indicating the input mode that the current system panel is in.<br>Usage scenarios: Use this attribute to determine the current input type when the panel behavior or layout needs to be adjusted based on different input modes.<br>Use effect: Different **inputType** values correspond to different panel interaction behaviors. For example, under the **SECURITY_INPUT** type, the panel enters secure input mode. |
| panelFlag | [PanelFlag](js-apis-inputmethod-panel.md#panelflag) | No | No | Panel flag of the input method soft keyboard panel, indicating the display state of the panel (fixed, floating, or candidate word state).<br>Usage scenarios: Use this attribute when the layout or interaction behavior needs to be adjusted based on the panel display state.<br>Use effect: Different **panelFlag** values correspond to different panel display forms: **FLAG_FIXED** indicates that the panel is fixed at the bottom of the screen, **FLAG_FLOATING** indicates that the panel is displayed in a floating manner, and **FLAG_CANDIDATE** indicates that the panel is a candidate word window.<br>Usage with related parameters: **panelFlag** is currently used only for panels of the **SOFT_KEYBOARD** type. |
| isPanelRaised | boolean | No | No | Whether the system panel needs bottom elevation. **true** indicates that the panel needs bottom elevation (the bottom area of the panel shifts upward to leave space for other UI elements below), and **false** indicates that the panel does not need bottom elevation.<br>Usage scenarios: When there are other UI elements below the system panel (such as a navigation bar and toolbar) that need to be displayed, set this attribute to **true** to raise the bottom of the panel and prevent the panel from covering the content below.<br>Use effect: When the value is set to **true**, the bottom area of the panel shifts upward; when the value is set to **false**, the panel is displayed normally without elevation. |
| needFuncButton | boolean | No | No | Whether the system panel needs a function button. **true** indicates that the panel needs to display a function button (such as operation buttons for settings, switching input methods, etc.), and **false** indicates that it does not need to display a function button.<br>Usage scenarios: When a shortcut function entry needs to be provided on the panel, set this attribute to **true** to display the function button in the panel area.<br>Use effect: When the value is set to **true**, the function button area is displayed on the panel; when the value is set to **false**, the function button area is not displayed on the panel. |

## InputMethodInputType

Enumerates input types, which are used to identify the input modes supported by the system panel. Different input types correspond to different input scenarios and panel layouts.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

| Name| Value| Description|
| -------- | -------- | -------- |
| NONE | -1 | No input type, indicating that the system panel is not in any specific input mode.<br>Usage scenarios: Use this value when the system panel is in the default or unknown input state. |
| CAMERA_INPUT | 0 | Camera input type, indicating that the system is in camera input mode.<br>Usage scenarios: Used for scenarios such as capture-based input, for example, scanning text or objects through the camera for input.<br>Use effect: The panel switches to camera input mode and interacts with camera-related functions. |
| SECURITY_INPUT | 1 | Secure input type, indicating that the system panel is in secure input mode.<br>Usage scenarios: Used for sensitive information input scenarios such as passwords and verification codes, where the system enables the secure input protection mechanism.<br>Use effect: The panel enters secure input mode, and the input content is not recorded or cached, preventing sensitive information leaks. |
| VOICE_INPUT | 2 | Voice input type, indicating that the system panel is in voice input mode.<br>Usage scenarios: Used for voice-to-text input scenarios, where the user inputs through voice.<br>Use effect: The panel switches to voice input mode and displays voice input-related interaction interfaces (such as the microphone button and voice recognition status). |
| FLOATING_VOICE_INPUT | 3 | Floating voice input type, indicating that the system panel is in floating voice input mode.<br>Usage scenarios: Compared with **VOICE_INPUT**, this type provides the voice input function in the form of a floating window, suitable for scenarios where voice input is required without occupying a fixed panel area.<br>Use effect: The panel displays the voice input interaction interface in the form of a floating window without occupying a fixed panel area. |

## CommandDataType

type CommandDataType = number | string | boolean

Indicates the data type of the value in a private command. The specific type of the API parameter depends on its function. The key is the command name (string type), and the value is the command data value (supporting number, string, or Boolean types).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

| Type| Description|
| -------- | -------- |
| number | Number type, used to indicate numeric command data, such as switch state codes and configuration parameter values. |
| string | String type, used to indicate text command data, such as command identifiers, text content, and path information. |
| boolean | Boolean type, used to indicate switch command data, such as function enabled/disabled states. |

## inputMethodSystemPanelManager.onSystemPrivateCommand

onSystemPrivateCommand(callback: Callback&lt;Record&lt;string, CommandDataType&gt;&gt;): void

Subscribes to events that the system preset input method application sends a private command. When the input method application sends a private command to the system component through [inputMethodEngine.sendPrivateCommand](js-apis-inputmethodengine.md#sendprivatecommand12) (**TextInputClient** method), the system panel receives the command data through this callback.

Usage scenarios: Use this API when the system panel needs to receive private commands (such as custom configurations and status notifications) from the input method application.

Use effect: After the subscription succeeds, whenever the input method application sends a private command, the system panel receives the command data in the **Record<string, CommandDataType>** format through the callback.

Preconditions: You must call [connectSystemChannel](#inputmethodsystempanelmanagerconnectsystemchannel) first to establish the system channel connection.

Usage with related APIs: This API receives private commands on the system panel side, corresponding to [inputMethodEngine.sendPrivateCommand](js-apis-inputmethodengine.md#sendprivatecommand12) (sender) and [inputMethodEngine.on('privateCommand')](js-apis-inputmethodengine.md#onprivatecommand12) (receiver on the input method application side) on the input method application side. Private command communication direction: input method application → system panel.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | Callback&lt;Record&lt;string, [CommandDataType](#commanddatatype)&gt;&gt;| Yes | Callback triggered when the input method application sends a private command.<br>Usage scenarios: This callback must be provided to process the private command data sent by the input method application.<br>Use effect: When the callback is triggered, the parameter is in the **Record<string, CommandDataType>** format, where key is the command name and value is the command data value (supporting number, string, and Boolean types).<br>Note: The data format in the callback is a key-value pair mapping. You need to determine the command type based on the key value and execute the corresponding logic. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
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

offSystemPrivateCommand(callback?: Callback&lt;Record&lt;string, CommandDataType&gt;&gt;): void

Unsubscribes from events that the system preset input method application sends a private command.

Usage scenarios: Use this API when the system panel no longer needs to receive private command notifications from the input method application, for example, when the panel is closed or exits.

Usage with related APIs: After the subscription is canceled, the callback previously registered through [onSystemPrivateCommand](#inputmethodsystempanelmanageronsystemprivatecommand) will no longer be triggered.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | Callback&lt;Record&lt;string, [CommandDataType](#commanddatatype)&gt;&gt; | No | Callback.<br>Usage scenarios: When a specific callback to be unsubscribed is passed in, only the subscription of that callback is canceled.<br>Default value: When the callback is not passed in, all subscribed **onSystemPrivateCommand** callbacks are canceled.<br>Note: It is recommended that you pass in the reference of the specific callback function to be unsubscribed, to avoid canceling all callbacks and thereby removing the callbacks of other subscribers as well. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
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

onSystemPanelStatusChange(callback: Callback&lt;SystemPanelStatus&gt;): void

Subscribes to system panel state change events. When the input type, panel flag, bottom elevation state, or function button requirement of the system panel changes, the callback is triggered.

Usage scenarios: Use this API when the system panel needs to perceive its own state changes and make corresponding adjustments (such as switching the panel layout based on the input type and adjusting the display form based on the panel flag).

Use effect: After the subscription succeeds, whenever the system panel state changes, the system passes the latest [SystemPanelStatus](#systempanelstatus) object through the callback, including the current input type, panel flag, bottom elevation state, and function button requirements.

Preconditions: You must call [connectSystemChannel](#inputmethodsystempanelmanagerconnectsystemchannel) first to establish the system channel connection.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | Callback&lt;[SystemPanelStatus](#systempanelstatus)&gt;| Yes | Callback triggered when the system panel state changes.<br>Usage scenarios: This callback function must be provided to handle panel state change notifications.<br>Use effect: When the callback is triggered, the parameter is a [SystemPanelStatus](#systempanelstatus) object, and you can adjust the panel layout and behavior based on the values of its properties. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
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

offSystemPanelStatusChange(callback?: Callback&lt;SystemPanelStatus&gt;): void

Unsubscribes from system panel state change events.

Usage scenarios: Use this API when the system panel no longer needs to receive panel state change notifications, such as when the panel is closed or exits.

Usage with related APIs: After unsubscribing, the callback previously registered through [onSystemPanelStatusChange](#inputmethodsystempanelmanageronsystempanelstatuschange) will no longer be triggered.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | Callback&lt;[SystemPanelStatus](#systempanelstatus)&gt;| No | Callback.<br>Usage scenarios: when a specific callback function to be unsubscribed is passed in, only the subscription of that callback is canceled.<br>Default value: when the value is not passed in, all subscribed **onSystemPanelStatusChange** callbacks are canceled.<br>Note: it is recommended that you pass in the reference of the specific callback function to be unsubscribed, to avoid canceling all callbacks and thereby removing the callbacks of other subscribers as well. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
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

sendPrivateCommand(commandData: Record&lt;string, CommandDataType&gt;): Promise&lt;void&gt;

Sends a private command to the system preset input method application. This API uses a promise to return the result asynchronously.

Meaning/Function: The system panel sends custom private commands to the system preset input method application. The data format is a key-value pair mapping (**Record<string, CommandDataType>**).

Usage scenarios: Use this API when the system panel needs to send custom configuration commands, state notifications, and other private data to the input method application. The private data channel is a communication mechanism between the system preset input method application and specific system components, and is commonly used by device-level vendors to implement custom input method functions on specific devices.

Use effect: After the call, the private command data is sent to the current system preset input method application. The input method application can receive this command data through [inputMethodEngine.on('privateCommand')](js-apis-inputmethodengine.md#onprivatecommand12).

Preconditions: You must call [connectSystemChannel](#inputmethodsystempanelmanagerconnectsystemchannel) first to establish the system channel connection.

Usage with related APIs: This API is the private command sending API on the system panel side, corresponding to [inputMethodEngine.on('privateCommand')](js-apis-inputmethodengine.md#onprivatecommand12) (the receiving end) on the input method application side. Private command communication direction: system panel → input method application.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| commandData | Record&lt;string, [CommandDataType](#commanddatatype)&gt; | Yes | Command data to send, in the format of a key-value pair mapping, where key is the command name (string type) and value is the command data value (supporting number, string, or Boolean type).<br>Usage scenarios: used to transmit custom communication data between the system panel and the input method application.<br>Value range: the total size is up to 32 KB, and the number of key-value pairs is up to 5. If this range is exceeded, error code 12800026 is returned.<br>Note: pay attention to the constraints and limitations on the amount of IPC-transmitted data. The total amount of data transmitted at the IPC layer in a single API call equals the amount of data sent by the application side plus the necessary amount of data required for system-layer processing. Therefore, the actual maximum amount of data that can be sent is less than 32 KB. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise object with no return result. It is resolved when the command is sent successfully, and rejected with a **BusinessError** object on failure. |

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 202 | not system application. |
| 12800026 | input method system panel error. Possible causes: 1. system panel not connected. 2. ipc failed due to large amount of data transferred or other reasons. 3. the caller is not system panel. |

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

Usage scenarios: When the system panel needs to perform private command communication or panel state synchronization with the system preset input method application, this API must be called first to establish the communication channel.

Use effect: After the connection is successful, the communication channel between the system panel and the input method application is established. Subsequently, APIs such as [sendPrivateCommand](#inputmethodsystempanelmanagersendprivatecommand), [onSystemPrivateCommand](#inputmethodsystempanelmanageronsystemprivatecommand), and [onSystemPanelStatusChange](#inputmethodsystempanelmanageronsystempanelstatuschange) can be called for data communication and state synchronization.

Preconditions: The **ohos.permission.CONNECT_IME_ABILITY** permission is required, and the caller must be a system application and a system preset input method panel.

Usage with related APIs: This API is the prerequisite for using other communication APIs of this module. You must call **connectSystemChannel** first to establish the channel before using APIs such as [sendPrivateCommand](#inputmethodsystempanelmanagersendprivatecommand), [onSystemPrivateCommand](#inputmethodsystempanelmanageronsystemprivatecommand), and [onSystemPanelStatusChange](#inputmethodsystempanelmanageronsystempanelstatuschange).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API**: This is a system API.

**Required permissions**: ohos.permission.CONNECT_IME_ABILITY

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise object with no return result. It is resolved when the connection succeeds, and rejected with a **BusinessError** object when the connection fails. |

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
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
