# setNetworkAccessPolicy (System API)

## Modules to Import

```TypeScript
import { policy } from '@kit.NetworkKit';
```

## setNetworkAccessPolicy

```TypeScript
function setNetworkAccessPolicy(uid: number, policy: NetworkAccessPolicy, isReconfirmed?: boolean): Promise<void>
```

Sets whether the application with the specified UID can access the network. This API uses a promise to return the result.

**Since:** 12

**Required permissions:** ohos.permission.MANAGE_NET_STRATEGY

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uid | number | Yes | Unique app ID, which is a positive integer within the int32_t range. |
| policy | [NetworkAccessPolicy](arkts-network-policy-networkaccesspolicy-i-sys.md) | Yes | Network policy. |
| isReconfirmed | boolean | No | Whether reconfirmation is required. The value **true** indicates that reconfirmation is not required and no dialog box is displayed. The value **false** indicates that reconfirmation is required and a dialog box is displayed when the application accesses the network. The default value is **false**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. If the operation is successful, no value is returned. If the operation fails, an error message is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-invalid-parameter-value) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accessPolicy: policy.NetworkAccessPolicy = {
  allowWiFi: false,
  allowCellular: true,
}
policy
  .setNetworkAccessPolicy(11111, accessPolicy)
  .then(() => {
    console.info('setNetworkAccessPolicy success');
  })
  .catch((error: BusinessError) => {
    console.error(JSON.stringify(error));
  });
```
