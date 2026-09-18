# getAddressesByNameWithOptions

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## getAddressesByNameWithOptions

```TypeScript
function getAddressesByNameWithOptions(host: string, option?: QueryOptions): Promise<Array<NetAddress>>
```

Performs the DNS resolution using the current default network based on the specified IP address type. This API uses a promise to return the result.

**Since:** 23

**Required permissions:** ohos.permission.INTERNET

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| host | string | Yes | Host name to resolve. For example, www.example.com. |
| option | [QueryOptions](arkts-network-connection-queryoptions-i.md) | No | Type of the IP address to be queried. The default value is **FAMILY_TYPE_ALL**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[NetAddress](arkts-network-connection-netaddress-i.md)&gt;&gt; | Promise used to return the queried IP address. In the command output, the port field has a fixed value of 0. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [2100001](../errorcode-net-connection.md#2100001-invalid-parameter-value) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |

**Examples**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
let option: connection.QueryOptions = {
  family: connection.FamilyType.FAMILY_TYPE_IPV4
};
connection.getAddressesByNameWithOptions("www.example.com", option).then((data: connection.NetAddress[]) => {
  console.info(`Succeeded to get data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`get ERROR msg: ${JSON.stringify(err)}`)
});
```
