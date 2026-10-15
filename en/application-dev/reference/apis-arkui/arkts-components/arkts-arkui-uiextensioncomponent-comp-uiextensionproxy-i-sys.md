# UIExtensionProxy (System API)

```TypeScript
declare interface UIExtensionProxy
```

Used for the component user to send data to the launched Ability and to subscribe to and unsubscribe from the registration events of the extension Ability after a connection is successfully established between the two parties.

**Since:** 10

<!--Device-unnamed-declare interface UIExtensionProxy--><!--Device-unnamed-declare interface UIExtensionProxy-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## off('asyncReceiverRegister')

```TypeScript
off(type: 'asyncReceiverRegister', callback?: Callback<UIExtensionProxy>): void
```

Used in the scenario where the component user unsubscribes from the asynchronous registration event of the launched Ability after a connection is successfully established between the two parties. This method is used together with **on('asyncReceiverRegister')** to cancel the subscription registered through **on('asyncReceiverRegister')**. When it is no longer necessary to listen for the asynchronous registration event (for example, before the component is destroyed), call this method to unsubscribe to avoid the callback being unable to be released.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIExtensionProxy-off(type: 'asyncReceiverRegister', callback?: Callback<UIExtensionProxy>): void--><!--Device-UIExtensionProxy-off(type: 'asyncReceiverRegister', callback?: Callback<UIExtensionProxy>): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'asyncReceiverRegister' | Yes | Event type. The value is **'asyncReceiverRegister'**, which indicates unsubscribing from the asynchronous registration callback of the extension Ability. |
| callback | Callback&lt;[UIExtensionProxy](arkts-arkui-uiextensioncomponent-comp-uiextensionproxy-i-sys.md)&gt; | No | Callback for the asynchronous registration event. If this parameter is left empty, all asynchronous registration callbacks of the extension Ability are unsubscribed.<br> If it is not empty, the corresponding asynchronous registration callback is unsubscribed.<br>**Since:** 18 |

## off('syncReceiverRegister')

```TypeScript
off(type: 'syncReceiverRegister', callback?: Callback<UIExtensionProxy>): void
```

Used in the scenario where the component user unsubscribes from the synchronous registration event of the launched Ability after a connection is successfully established between the two parties. This method is used together with **on('syncReceiverRegister')** to cancel the subscription registered through **on('syncReceiverRegister')**. When it is no longer necessary to listen for the synchronous registration event (for example, before the component is destroyed), call this method to unsubscribe to avoid the callback being unable to be released.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIExtensionProxy-off(type: 'syncReceiverRegister', callback?: Callback<UIExtensionProxy>): void--><!--Device-UIExtensionProxy-off(type: 'syncReceiverRegister', callback?: Callback<UIExtensionProxy>): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'syncReceiverRegister' | Yes | Event type. The value is **'syncReceiverRegister'**, which indicates unsubscribing from the synchronous registration callback of the extension Ability. |
| callback | Callback&lt;[UIExtensionProxy](arkts-arkui-uiextensioncomponent-comp-uiextensionproxy-i-sys.md)&gt; | No | Callback for the synchronous registration event. If this parameter is left empty, it indicates unsubscribing from all callbacks triggered after the synchronous registration of the extension Ability.<br> If this parameter is not empty, it indicates unsubscribing from the corresponding synchronous registration callback.<br>**Since:** 18 |

## on('asyncReceiverRegister')

```TypeScript
on(type: 'asyncReceiverRegister', callback: Callback<UIExtensionProxy>): void
```

Subscribes to asynchronous registration of the started UIExtensionAbility through the connection established between the component host and UIExtensionAbility.

> **NOTE:** 
> **asyncReceiverRegister** and **syncReceiverRegister** subscribe to the asynchronous and synchronous data
> receiving registration events of the extension Ability, respectively. When the extension Ability calls
> **setReceiveDataCallback** to register asynchronous receiving, the **asyncReceiverRegister** callback is
> triggered. When the extension Ability calls **setReceiveDataForResultCallback** to register synchronous
> receiving, the **syncReceiverRegister** callback is triggered. Developers should select the corresponding event
> to subscribe to based on the data receiving mode used by the extension Ability.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIExtensionProxy-on(type: 'asyncReceiverRegister', callback: Callback<UIExtensionProxy>): void--><!--Device-UIExtensionProxy-on(type: 'asyncReceiverRegister', callback: Callback<UIExtensionProxy>): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'asyncReceiverRegister' | Yes | Event type. The value is **'asyncReceiverRegister'**, indicating subscription to the asynchronous registration callback of the extended Ability. |
| callback | Callback&lt;[UIExtensionProxy](arkts-arkui-uiextensioncomponent-comp-uiextensionproxy-i-sys.md)&gt; | Yes | Callback invoked when the extended Ability registers **setReceiveDataCallback**.<br>**Since:** 18 |

## on('syncReceiverRegister')

```TypeScript
on(type: 'syncReceiverRegister', callback: Callback<UIExtensionProxy>): void
```

Subscribes to synchronous registration of the started UIExtensionAbility through the connection established between the component host and UIExtensionAbility.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIExtensionProxy-on(type: 'syncReceiverRegister', callback: Callback<UIExtensionProxy>): void--><!--Device-UIExtensionProxy-on(type: 'syncReceiverRegister', callback: Callback<UIExtensionProxy>): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'syncReceiverRegister' | Yes | Event type. The value is **'syncReceiverRegister'**, indicating subscription to the synchronous registration callback of the extension Ability. |
| callback | Callback&lt;[UIExtensionProxy](arkts-arkui-uiextensioncomponent-comp-uiextensionproxy-i-sys.md)&gt; | Yes | Callback invoked when the extension Ability registers **setReceiveDataForResultCallback**.<br>**Since:** 18 |

## send

```TypeScript
send(data: Record<string, Object>): void
```

Used in the scenario where the component user sends data to the launched Ability after a connection is successfully established between the two parties, providing asynchronous data sending.

> **NOTE:** 
> Both **send** and **sendSync** can be used to send data to the launched Ability. **send** is asynchronous and
> has no return value, and is suitable for scenarios where the reply from the extension Ability is not required.
> **sendSync** is synchronous and can obtain the reply data from the extension Ability, and is suitable for
> scenarios where the processing result needs to be obtained synchronously.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIExtensionProxy-send(data: Record<string, Object>): void--><!--Device-UIExtensionProxy-send(data: Record<string, Object>): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | Record&lt;string, Object&gt; | Yes | Data asynchronously sent to the launched **UIExtensionAbility**. In versions earlier than API version 18, the type of data is Object.<br>**Since:** 18 |

## sendSync

```TypeScript
sendSync(data: Record<string, Object>): Record<string, Object>
```

Used in the scenario where the component user sends data to the launched Ability after a connection is successfully established between the two parties, providing synchronous data sending.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIExtensionProxy-sendSync(data: Record<string, Object>): Record<string, Object>--><!--Device-UIExtensionProxy-sendSync(data: Record<string, Object>): Record<string, Object>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | Record&lt;string, Object&gt; | Yes | Data synchronously sent to the launched **UIExtensionAbility**. Before API version 18, the type of data is Object.<br>**Since:** 18 |

**Return value:**

| Type | Description |
| --- | --- |
| object | data - Data replied by the extension Ability.<br>**Since:** 11 - 17 |
| Record&lt;string, Object&gt; | data - Data replied by the extension Ability.<br>**Since:** 18 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [100011](../errorcode-uiextension.md#100011-no-synchronous-callback-registered) | No callback has been registered to respond to this request. |
| [100012](../errorcode-uiextension.md#100012-data-transfer-failure) | Transferring data failed. |
