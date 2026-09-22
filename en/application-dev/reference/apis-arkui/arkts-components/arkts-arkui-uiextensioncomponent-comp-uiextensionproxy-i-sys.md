# UIExtensionProxy (System API)

```TypeScript
declare interface UIExtensionProxy
```

Implements a **UIExtensionProxy** instance for the component host to send data to, subscribe to, or unsubscribe from the started UIExtensionAbility through the connection established between the two parties.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## off('asyncReceiverRegister')

```TypeScript
off(type: 'asyncReceiverRegister', callback?: Callback<UIExtensionProxy>): void
```

Unsubscribes from asynchronous registration of the started UIExtensionAbility through the connection established between the component host and UIExtensionAbility.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'asyncReceiverRegister' | Yes | Event type. The value is fixed at **'asyncReceiverRegister'**. |
| callback | Callback&lt;[UIExtensionProxy](arkts-arkui-uiextensioncomponent-comp-uiextensionproxy-i-sys.md)&gt; | No | Callback. If this parameter is left empty, it means unsubscribing from all callbacks triggered after UIExtensionAbility's asynchronous registration.<br> If this parameter is not empty, it means unsubscribing from callbacks corresponding to **type**.<br>**Since:** 18 |

## off('syncReceiverRegister')

```TypeScript
off(type: 'syncReceiverRegister', callback?: Callback<UIExtensionProxy>): void
```

Unsubscribes from synchronous registration of the started UIExtensionAbility through the connection established between the component host and UIExtensionAbility.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'syncReceiverRegister' | Yes | Event type. The value is fixed at **'syncReceiverRegister'**. |
| callback | Callback&lt;[UIExtensionProxy](arkts-arkui-uiextensioncomponent-comp-uiextensionproxy-i-sys.md)&gt; | No | Callback. If this parameter is left empty, it means unsubscribing from all callbacks triggered after UIExtensionAbility's synchronous registration.<br> If this parameter is not empty, it means unsubscribing from callbacks corresponding to **type**.<br>**Since:** 18 |

## on('asyncReceiverRegister')

```TypeScript
on(type: 'asyncReceiverRegister', callback: Callback<UIExtensionProxy>): void
```

Subscribes to asynchronous registration of the started UIExtensionAbility through the connection established between the component host and UIExtensionAbility.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'asyncReceiverRegister' | Yes | Event type. The value is fixed at **'asyncReceiverRegister'**. |
| callback | Callback&lt;[UIExtensionProxy](arkts-arkui-uiextensioncomponent-comp-uiextensionproxy-i-sys.md)&gt; | Yes | Callback. It is triggered after UIExtensionAbility registers the **setReceiveDataCallback** method.<br>**Since:** 18 |

## on('syncReceiverRegister')

```TypeScript
on(type: 'syncReceiverRegister', callback: Callback<UIExtensionProxy>): void
```

Subscribes to synchronous registration of the started UIExtensionAbility through the connection established between the component host and UIExtensionAbility.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'syncReceiverRegister' | Yes | Event type. The value is fixed at **'syncReceiverRegister'**. |
| callback | Callback&lt;[UIExtensionProxy](arkts-arkui-uiextensioncomponent-comp-uiextensionproxy-i-sys.md)&gt; | Yes | Callback. It is triggered after the UIExtensionAbility registers **setReceiveDataForResultCallback**.<br>**Since:** 18 |

## send

```TypeScript
send(data: Record<string, Object>): void
```

Asynchronously sends data from the component host to the started UIExtensionAbility through the connection established between the two parties.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | Record&lt;string, Object&gt; | Yes | Data to be asynchronously sent to the started UIExtensionAbility. In versions earlier than API version 18, the data type is **Object**.<br>**Since:** 18 |

## sendSync

```TypeScript
sendSync(data: Record<string, Object>): Record<string, Object>
```

Synchronously sends data from the component host to the started UIExtensionAbility through the connection established between the two parties.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | Record&lt;string, Object&gt; | Yes | Data to be synchronously sent to the started UIExtensionAbility.<br>**Since:** 18 |

**Return value:**

| Type | Description |
| --- | --- |
| object | data - data transferred from the UIExtensionAbility<br>**Since:** 11 - 17 |
| Record&lt;string, Object&gt; | data - Data transferred from the UIExtensionAbility.<br>**Since:** 18 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [100011](../errorcode-uiextension.md#100011-no-synchronous-callback-registered) | No callback has been registered to respond to this request. |
| [100012](../errorcode-uiextension.md#100012-data-transfer-failure) | Transferring data failed. |
