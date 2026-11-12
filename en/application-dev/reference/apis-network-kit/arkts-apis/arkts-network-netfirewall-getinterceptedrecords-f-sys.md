# getInterceptedRecords (System API)

## Modules to Import

```TypeScript
import { netFirewall } from '@kit.NetworkKit';
```

## getInterceptedRecords

```TypeScript
function getInterceptedRecords(userId: number, requestParam: RequestParam): Promise<InterceptedRecordPage>
```

Obtains the interception records by **userId**. You need to specify the pagination query parameters. This API uses a promise to return the result.

**Since:** 14

**Required permissions:** ohos.permission.GET_NET_FIREWALL

<!--Device-netFirewall-function getInterceptedRecords(userId: int, requestParam: RequestParam): Promise<InterceptedRecordPage>--><!--Device-netFirewall-function getInterceptedRecords(userId: int, requestParam: RequestParam): Promise<InterceptedRecordPage>-End-->

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | Yes | User ID. The value must be an existing user ID in the system. |
| requestParam | [RequestParam](arkts-network-netfirewall-requestparam-i.md) | Yes | Query parameter. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[InterceptedRecordPage](arkts-network-netfirewall-interceptedrecordpage-i-sys.md)&gt; | Promise used to return the list of intercepted records. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-invalid-parameter-value) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Operation failed. Cannot connect to service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |
| [29400000](../errorcode-net-netfirewall.md#29400000-specified-user-does-not-exist) | The specified user does not exist. |

<!--Del-->
**Examples**

```TypeScript
import { netFirewall } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let interceptRecordParam: netFirewall.RequestParam = {
  page: 1,
  pageSize: 10,
  orderField: netFirewall.NetFirewallOrderField.ORDER_BY_RECORD_TIME,
  orderType: netFirewall.NetFirewallOrderType.ORDER_DESC
};
netFirewall.getInterceptedRecords(100, interceptRecordParam).then((result: netFirewall.InterceptedRecordPage) => {
  console.info("result:", JSON.stringify(result));
}, (error: BusinessError) => {
  console.error("get intercept records failed: " + JSON.stringify(error));
});
```

<!--DelEnd-->
