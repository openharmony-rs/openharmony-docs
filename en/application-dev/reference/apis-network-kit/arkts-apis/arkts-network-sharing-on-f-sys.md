# on (System API)

## Modules to Import

```TypeScript
import { sharing } from '@kit.NetworkKit';
```

## on('sharingStateChange')

```TypeScript
function on(type: 'sharingStateChange', callback: Callback<boolean>): void
```

Registers the network sharing status change event. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.CONNECTIVITY_INTERNAL

**System capability:** SystemCapability.Communication.NetManager.NetSharing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'sharingStateChange' | Yes | Event type.<br> The value **sharingStateChange** indicates a network sharing status change event. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | Yes | Callback invoked when the network sharing state changes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |

**Examples**

```TypeScript
import { sharing } from '@kit.NetworkKit';

sharing.on('sharingStateChange', (data: boolean) => {
  console.info('on sharingStateChange: ' + JSON.stringify(data));
});
```


## on('interfaceSharingStateChange')

```TypeScript
function on(type: 'interfaceSharingStateChange', callback: Callback<InterfaceSharingStateInfo>): void
```

Subscribes to network sharing state changes of a specified NIC. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.CONNECTIVITY_INTERNAL

**System capability:** SystemCapability.Communication.NetManager.NetSharing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'interfaceSharingStateChange' | Yes | Event type.<br> The value **interfaceSharingStateChange** indicates a network sharing status change event of the NIC. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[InterfaceSharingStateInfo](arkts-network-sharing-interfacesharingstateinfo-i-sys.md)&gt; | Yes | Callback used to return the result. It is called when the network sharing state of a specified NIC changes.<br>**Since:** 11 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |

**Examples**

```TypeScript
import { sharing } from '@kit.NetworkKit';

sharing.on('interfaceSharingStateChange', (data: object) => {
  console.info('on interfaceSharingStateChange:' + JSON.stringify(data));
});
```


## on('sharingUpstreamChange')

```TypeScript
function on(type: 'sharingUpstreamChange', callback: Callback<NetHandle>): void
```

Subscribes to upstream network changes. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.CONNECTIVITY_INTERNAL

**System capability:** SystemCapability.Communication.NetManager.NetSharing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'sharingUpstreamChange' | Yes | Event type.<br> The value **sharingUpstreamChange** indicates an upstream network change event. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[NetHandle](arkts-network-sharing-nethandle-t.md)&gt; | Yes | Callback invoked when the upstream network changes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |

**Examples**

```TypeScript
import { sharing } from '@kit.NetworkKit';

sharing.on('sharingUpstreamChange', (data: object) => {
  console.info('on sharingUpstreamChange:' + JSON.stringify(data));
});
```
