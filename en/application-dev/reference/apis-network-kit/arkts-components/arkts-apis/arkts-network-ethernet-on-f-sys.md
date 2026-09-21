# on (System API)

## Modules to Import

```TypeScript
import { ethernet } from '@kit.NetworkKit';
```

## on('interfaceStateChange')

```TypeScript
function on(type: 'interfaceStateChange', callback: Callback<InterfaceStateInfo>): void
```

Registers the observer for NIC hot swap events. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.GET_NETWORK_INFO

**System capability:** SystemCapability.Communication.NetManager.Ethernet

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'interfaceStateChange' | Yes | Event type. The value is **interfaceStateChange**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[InterfaceStateInfo](arkts-network-ethernet-interfacestateinfo-i-sys.md)&gt; | Yes | Callback used to return the result.<br>**Since:** 11 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |

**Examples**

```TypeScript
import { ethernet } from '@kit.NetworkKit';

ethernet.on('interfaceStateChange', (data: object) => {
  console.info('on interfaceSharingStateChange: ' + JSON.stringify(data));
});
```
