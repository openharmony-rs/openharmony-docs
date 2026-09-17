# NetConnection

Represents the network connection object type.

> **NOTE:** 
> 
> (1) When the network transitions from unavailable to available, the **netAvailable**, **netCapabilitiesChange**,
> and **netConnectionPropertiesChange** events are triggered.
> 
> (2) If the network transitions from available to unavailable after a **netAvailable** event is received, a
> **netLost** event is triggered.
> 
> (3) If no **netAvailable** event is received, a **netUnavailable** event is directly triggered.
> 
> (4) When the network transitions from Wi-Fi to cellular, a **netLost** event is first triggered to indicate that
> the Wi-Fi network is lost and then a **netAvailable** event is triggered to indicate that the cellular network is
> available.

**Since:** 8

**System capability:** SystemCapability.Communication.NetManager.Core

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## on('netAvailable')

```TypeScript
on(type: 'netAvailable', callback: Callback<NetHandle>): void
```

Registers a listener for **netAvailable** events. Before you call this API, make sure that you have called **register** to add a listener for network status changes. When the listener is no longer needed, call **unregister** to remove it.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'netAvailable' | Yes | Event type. This field has a fixed value of **netAvailable**.<br>**netAvailable**: event indicating that the data network is available. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[NetHandle](arkts-network-connection-nethandle-i.md)&gt; | Yes | Callback used to return the network handle. |

## on('netBlockStatusChange')

```TypeScript
on(type: 'netBlockStatusChange', callback: Callback<NetBlockStatusInfo>): void
```

Registers a listener for **netBlockStatusChange** events. Before you call this API, make sure that you have called **register** to add a listener for network status changes. When the listener is no longer needed, call **unregister** to remove it.

**Since:** 8

**System capability:** SystemCapability.Communication.NetManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'netBlockStatusChange' | Yes | Event type. This field has a fixed value of **netBlockStatusChange**.<br>**netBlockStatusChange**: event indicating a change in the network blocking status. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[NetBlockStatusInfo](arkts-network-connection-netblockstatusinfo-i.md)&gt; | Yes | Callback used to return the result.<br>**Since:** 11 |

## on('netCapabilitiesChange')

```TypeScript
on(type: 'netCapabilitiesChange', callback: Callback<NetCapabilityInfo>): void
```

Registers a listener for **netCapabilitiesChange** events. Before you call this API, make sure that you have called **register** to add a listener for network status changes. When the listener is no longer needed, call **unregister** to remove it.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'netCapabilitiesChange' | Yes | Event type. This field has a fixed value of **netCapabilitiesChange**.<br>**netCapabilitiesChange**: event indicating that the network capabilities have changed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[NetCapabilityInfo](arkts-network-connection-netcapabilityinfo-i.md)&gt; | Yes | Callback used to return the network handle (**netHandle**) and capability information (**netCap**). |

## on('netConnectionPropertiesChange')

```TypeScript
on(type: 'netConnectionPropertiesChange', callback: Callback<NetConnectionPropertyInfo>): void
```

Registers a listener for **netConnectionPropertiesChange** events. Before you call this API, make sure that you have called **register** to add a listener for network status changes. When the listener is no longer needed, call **unregister** to remove it.

**Since:** 8

**System capability:** SystemCapability.Communication.NetManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'netConnectionPropertiesChange' | Yes | Event type. This field has a fixed value of **netConnectionPropertiesChange**.<br>**netConnectionPropertiesChange**: event indicating that network connection properties have changed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[NetConnectionPropertyInfo](arkts-network-connection-netconnectionpropertyinfo-i.md)&gt; | Yes | Callback used to return the result.<br>**Since:** 11 |

## on('netLost')

```TypeScript
on(type: 'netLost', callback: Callback<NetHandle>): void
```

Registers a listener for **netLost** events. Before you call this API, make sure that you have called **register** to add a listener for network status changes. When the listener is no longer needed, call **unregister** to remove it.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'netLost' | Yes | Event type. This field has a fixed value of **netLost**.<br>**netLost**: event indicating that the network is interrupted or normally disconnected. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[NetHandle](arkts-network-connection-nethandle-i.md)&gt; | Yes | Callback used to return the result, which is a **netHandle** object. |

## on('netUnavailable')

```TypeScript
on(type: 'netUnavailable', callback: Callback<void>): void
```

Registers a listener for **netUnavailable** events. Before you call this API, make sure that you have called **register** to add a listener for network status changes. When the listener is no longer needed, call **unregister** to remove it.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'netUnavailable' | Yes | Event type. This field has a fixed value of **netUnavailable**.<br>**netUnavailable**: event indicating that the network is unavailable. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | Yes | Callback used to return the result, which is empty. |

## register

```TypeScript
register(callback: AsyncCallback<void>): void
```

Registers a listener for network status changes. To listen for a specific type of events, call **on** to enable listening and then call **register** to register an event listener.

> **NOTE:** 
> 
> After using the **register** API, you need to call **unregister** to deregister the listener.
> **Required permission**: ohos.permission.GET_NETWORK_INFO

**Since:** 8

**Required permissions:** ohos.permission.GET_NETWORK_INFO

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If a listener for network status changes is registered successfully, **error** is **undefined**. Otherwise, **error** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |
| [2101008](../errorcode-net-connection.md#2101008-callback-already-exists) | The callback already exists. |
| [2101022](../errorcode-net-connection.md#2101022-number-of-requests-exceeding-the-maximum) | The number of requests exceeded the maximum allowed. |

**Examples**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let netCon: connection.NetConnection = connection.createNetConnection();
netCon.register((error: BusinessError) => {
  console.error(JSON.stringify(error));
});
```

## unregister

```TypeScript
unregister(callback: AsyncCallback<void>): void
```

Unregisters the listener for network status changes.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If a listener for network status changes is unregistered successfully, **error** is **undefined**. Otherwise, **error** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied.<br>**Applicable version:** 8 - 11 |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |
| [2101007](../errorcode-net-connection.md#2101007-callback-not-exist) | The callback does not exist. |

**Examples**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let netCon: connection.NetConnection = connection.createNetConnection();
netCon.unregister((error: BusinessError) => {
  console.error(JSON.stringify(error));
});
```
