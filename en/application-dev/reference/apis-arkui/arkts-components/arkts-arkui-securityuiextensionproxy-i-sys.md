# SecurityUIExtensionProxy (System API)

Implements a **SecurityUIExtensionProxy** instance for the component host to send data to, subscribe to, or unsubscribe from the started ability through the connection established between the two parties.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## off('asyncReceiverRegister')

```TypeScript
off(type: 'asyncReceiverRegister', callback?: Callback<UIExtensionProxy>): void
```

Unsubscribes from the callback triggered for the asynchronous registration of the started ability. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'asyncReceiverRegister' | Yes | The value is fixed to **asyncReceiverRegister**, indicating unsubscription from the callback triggered for asynchronous registration of the extended ability. |
| callback | [Callback](arkts-arkui-callback-i.md)&lt;[UIExtensionProxy](arkts-arkui-uiextensionproxy-i-sys.md)&gt; | No | Callback function. If this parameter is left empty, it means unsubscribing from all callbacks triggered after **UIExtensionAbility**'s asynchronous registration. If this parameter is not empty, it means unsubscribing from callbacks corresponding to **type**. |

## off('syncReceiverRegister')

```TypeScript
off(type: 'syncReceiverRegister', callback?: Callback<UIExtensionProxy>): void
```

Unsubscribes from the callback triggered for the synchronous registration of the started ability. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'syncReceiverRegister' | Yes | The value is fixed to **syncReceiverRegister**, indicating unsubscription to the asynchronous registration of the extension ability. |
| callback | [Callback](arkts-arkui-callback-i.md)&lt;[UIExtensionProxy](arkts-arkui-uiextensionproxy-i-sys.md)&gt; | No | Callback to unsubscribe from. If this parameter is left empty, it means unsubscribing from all callbacks triggered after **UIExtensionAbility**'s synchronous registration. |

## on('asyncReceiverRegister')

```TypeScript
on(type: 'asyncReceiverRegister', callback: Callback<UIExtensionProxy>): void
```

Subscribes to the callback triggered for asynchronous registration of the started ability. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'asyncReceiverRegister' | Yes | The value is fixed to **asyncReceiverRegister**, indicating a subscription to the callback triggered for asynchronous registration of the extended ability. |
| callback | [Callback](arkts-arkui-callback-i.md)&lt;[UIExtensionProxy](arkts-arkui-uiextensionproxy-i-sys.md)&gt; | Yes | Callback triggered after the extension ability registers a [setReceiveDataCallback](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c-sys.md#setreceivedatacallback). |

## on('syncReceiverRegister')

```TypeScript
on(type: 'syncReceiverRegister', callback: Callback<UIExtensionProxy>): void
```

Subscribes to the callback triggered for synchronous registration of the started ability. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'syncReceiverRegister' | Yes | The value is fixed to **syncReceiverRegister**, indicating subscription to the asynchronous registration of the extension ability. |
| callback | [Callback](arkts-arkui-callback-i.md)&lt;[UIExtensionProxy](arkts-arkui-uiextensionproxy-i-sys.md)&gt; | Yes | Callback triggered after the extension ability registers a [setReceiveDataForResultCallback](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c-sys.md#setreceivedataforresultcallback). |

## send

```TypeScript
send(data: Record<string, Object>): void
```

Asynchronously sends data to the ability started by the component host through the connection established between the two parties.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | Record&lt;string, Object&gt; | Yes | Data to be asynchronously sent to the started **UIExtensionAbility**. |

## sendSync

```TypeScript
sendSync(data: Record<string, Object>): Record<string, Object>
```

Synchronously sends data to the ability started by the component host through the connection established between the two parties.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | Record&lt;string, Object&gt; | Yes | Data to be synchronously sent to the started **UIExtensionAbility**. |

**Return value:**

| Type | Description |
| --- | --- |
| Record&lt;string, Object&gt; | Data returned by the extension ability. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [100011](../errorcode-uiextension.md#100011-no-synchronous-callback-registered) | No callback has been registered to response this request. |
| [100012](../errorcode-uiextension.md#100012-data-transfer-failure) | Transferring data failed. |
