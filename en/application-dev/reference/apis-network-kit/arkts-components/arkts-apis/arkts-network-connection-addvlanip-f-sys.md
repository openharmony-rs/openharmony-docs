# addVlanIp (System API)

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## addVlanIp

```TypeScript
function addVlanIp(ifName: string, vlanId: number, address: LinkAddress): Promise<void>
```

Adds a specified IP address and subnet mask for the VLAN specified by **vlanId** on an Ethernet NIC. This API uses a promise to return the result.

> **NOTE:** 
> 
> - Currently, this API supports only the PC. For other device types, the error code 2100002 is returned when this API is called.

**Since:** 23

**Required permissions:** ohos.permission.CONNECTIVITY_INTERNAL

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ifName | string | Yes | NIC name. |
| vlanId | number | Yes | VLAN ID. The value range is [0, 4094]. |
| address | [LinkAddress](arkts-network-connection-linkaddress-i.md) | Yes | Network link information. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Nonsystem applications use system APIs. |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |
| [2100400](../errorcode-net-connection.md#2100400-incorrect-nic-name-non-ethernet) | The input network interface name is incorrect. |

**Examples**

```TypeScript
import { connection } from '@kit.NetworkKit';

let ifName = "eth0";
let vlanId = 1;
let netAddress: connection.NetAddress = {
  address: '192.168.1.1',
  family: 1,
  port: 8080
}
let address: connection.LinkAddress = {
  address: netAddress,
  prefixLength: 24
}
connection.addVlanIp(ifName, vlanId, address).then(() => {
  console.info(`Add vlan ip success`);
}).catch((error: BusinessError) => {
  console.error(`Failed to add vlan ip. Code:${error.code}, message:${error.message}`);
});
```
