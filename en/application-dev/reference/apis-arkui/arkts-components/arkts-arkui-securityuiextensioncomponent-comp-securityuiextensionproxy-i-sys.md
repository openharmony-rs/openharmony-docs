# SecurityUIExtensionProxy (System API)

```TypeScript
declare interface SecurityUIExtensionProxy
```

Used to send data to the launched **Ability** and subscribe to and unsubscribe from event callbacks after a successful connection is established.

**Since:** 26.0.0

<!--Device-unnamed-declare interface SecurityUIExtensionProxy--><!--Device-unnamed-declare interface SecurityUIExtensionProxy-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## off('asyncReceiverRegister')

```TypeScript
off(type: 'asyncReceiverRegister', callback?: Callback<UIExtensionProxy>): void
```

Unsubscribes from the callback triggered when the launched **Ability** performs asynchronous registration. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SecurityUIExtensionProxy-off(type: 'asyncReceiverRegister', callback?: Callback<UIExtensionProxy>): void--><!--Device-SecurityUIExtensionProxy-off(type: 'asyncReceiverRegister', callback?: Callback<UIExtensionProxy>): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'asyncReceiverRegister' | Yes | Fixed value **'asyncReceiverRegister'**, used to unsubscribe from the callback triggered when the launched **Ability** performs asynchronous registration. |
| callback | Callback&lt;[UIExtensionProxy](arkts-arkui-uiextensioncomponent-comp-uiextensionproxy-i-sys.md)&gt; | No | Callback function. If this parameter is left empty, all callbacks for asynchronous registration are unsubscribed. If it is not empty, the specified callback for asynchronous registration is unsubscribed. |

## off('syncReceiverRegister')

```TypeScript
off(type: 'syncReceiverRegister', callback?: Callback<UIExtensionProxy>): void
```

Unsubscribes from the callback triggered when the launched **Ability** performs synchronous registration. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SecurityUIExtensionProxy-off(type: 'syncReceiverRegister', callback?: Callback<UIExtensionProxy>): void--><!--Device-SecurityUIExtensionProxy-off(type: 'syncReceiverRegister', callback?: Callback<UIExtensionProxy>): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'syncReceiverRegister' | Yes | Fixed value **'syncReceiverRegister'**, used to unsubscribe from the callback triggered when the launched **Ability** performs synchronous registration. |
| callback | Callback&lt;[UIExtensionProxy](arkts-arkui-uiextensioncomponent-comp-uiextensionproxy-i-sys.md)&gt; | No | Callback function. If it is empty, unsubscribes from all synchronously registered callbacks. If it is not empty, unsubscribes from the specified synchronously registered callback. |

## on('asyncReceiverRegister')

```TypeScript
on(type: 'asyncReceiverRegister', callback: Callback<UIExtensionProxy>): void
```

After a successful connection is established, subscribes to the callback triggered when the launched **Ability** performs asynchronous registration. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SecurityUIExtensionProxy-on(type: 'asyncReceiverRegister', callback: Callback<UIExtensionProxy>): void--><!--Device-SecurityUIExtensionProxy-on(type: 'asyncReceiverRegister', callback: Callback<UIExtensionProxy>): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'asyncReceiverRegister' | Yes | Fixed value **'asyncReceiverRegister'**, which indicates the callback triggered when the launched **Ability** performs asynchronous registration. |
| callback | Callback&lt;[UIExtensionProxy](arkts-arkui-uiextensioncomponent-comp-uiextensionproxy-i-sys.md)&gt; | Yes | Callback triggered after the launched **Ability** registers [setReceiveDataCallback](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c-sys.md#setreceivedatacallback). |

## on('syncReceiverRegister')

```TypeScript
on(type: 'syncReceiverRegister', callback: Callback<UIExtensionProxy>): void
```

After a successful connection is established, subscribes to the callback triggered when the launched **Ability** performs synchronous registration. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SecurityUIExtensionProxy-on(type: 'syncReceiverRegister', callback: Callback<UIExtensionProxy>): void--><!--Device-SecurityUIExtensionProxy-on(type: 'syncReceiverRegister', callback: Callback<UIExtensionProxy>): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'syncReceiverRegister' | Yes | Fixed value **'syncReceiverRegister'**, which indicates the callback triggered when the launched **Ability** performs synchronous registration. |
| callback | Callback&lt;[UIExtensionProxy](arkts-arkui-uiextensioncomponent-comp-uiextensionproxy-i-sys.md)&gt; | Yes | Callback function. Callback triggered after the launched **Ability** registers [setReceiveDataForResultCallback](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c-sys.md#setreceivedataforresultcallback). |

## send

```TypeScript
send(data: Record<string, Object>): void
```

Used to send data to the launched **Ability** after a successful connection is established, providing asynchronous sending capability. The data will be received and processed by the extension **Ability** through [setReceiveDataCallback](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c-sys.md#setreceivedatacallback).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SecurityUIExtensionProxy-send(data: Record<string, Object>): void--><!--Device-SecurityUIExtensionProxy-send(data: Record<string, Object>): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | Record&lt;string, Object&gt; | Yes | Data asynchronously sent to the launched **Ability**. |

## sendSync

```TypeScript
sendSync(data: Record<string, Object>): Record<string, Object>
```

Sends data to the launched **Ability** after a successful connection is established. The data will be processed by the launched **Ability** through **setReceiveDataForResultCallback** and the result will be returned.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SecurityUIExtensionProxy-sendSync(data: Record<string, Object>): Record<string, Object>--><!--Device-SecurityUIExtensionProxy-sendSync(data: Record<string, Object>): Record<string, Object>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | Record&lt;string, Object&gt; | Yes | Data synchronously sent to the launched **Ability**. |

**Return value:**

| Type | Description |
| --- | --- |
| Record&lt;string, Object&gt; | Response data returned by the launched **Ability** after processing the synchronous send request. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [100011](../errorcode-uiextension.md#100011-no-synchronous-callback-registered) | No callback has been registered to respond to this request. |
| [100012](../errorcode-uiextension.md#100012-data-transfer-failure) | Transferring data failed. |
