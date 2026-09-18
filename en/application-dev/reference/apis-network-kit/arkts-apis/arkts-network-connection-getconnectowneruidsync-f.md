# getConnectOwnerUidSync

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## getConnectOwnerUidSync

```TypeScript
function getConnectOwnerUidSync(protocol: ProtocolType, local: NetAddress, remote: NetAddress): number
```

Queries the UID of the application that initiates a specified network connection. This API returns the result synchronously.

> **NOTE:** 
> 
> - This API can be called only in VPN applications.
> 
> - Set the port numbers of the **local** and **remote** parameters when calling the API. If the port number is not set or is set to 0, the API filters out a set of UIDs that meet the conditions based on other parameters and returns a matched UID.
> 
> - When protocol is set to PROTO_TYPE_UDP, if no UID is found based on the local and remote parameters, the UID is filtered based on the local parameter and the matched UID is returned.
> **Required permission**: ohos.permission.GET_NETWORK_INFO

**Since:** 23

**Required permissions:** ohos.permission.GET_NETWORK_INFO

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| protocol | [ProtocolType](arkts-network-connection-protocoltype-e.md) | Yes | Type of a network protocol. |
| local | [NetAddress](arkts-network-connection-netaddress-i.md) | Yes | Source network address. |
| remote | [NetAddress](arkts-network-connection-netaddress-i.md) | Yes | Destination network address. |

**Return value:**

| Type | Description |
| --- | --- |
| number | UID of an application. If no matching UID is found, -1 is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [2100001](../errorcode-net-connection.md#2100001-invalid-parameter-value) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100301](../errorcode-net-connection.md#2100301-failed-to-authenticate-the-caller-non-vpn-application) | Incorrect usage in non-VPN application. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |

**Examples**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let protocol = connection.ProtocolType.PROTO_TYPE_TCP;
let local: connection.NetAddress = { address: '192.168.1.100', family: 1, port: 6666 };
let remote: connection.NetAddress = { address: '192.168.1.200', family: 1, port: 8888 };
try {
  let uid = connection.getConnectOwnerUidSync(protocol, local, remote);
  console.info(`uid: ${uid}`);
} catch (e) {
  let err = e as BusinessError;
  console.error(`getConnectOwnerUid failed. errorCode: ${err.code} message:${err.message}`);
}
```
