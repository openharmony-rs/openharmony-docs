# removeCustomDnsRule

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## removeCustomDnsRule

```TypeScript
function removeCustomDnsRule(host: string, callback: AsyncCallback<void>): void
```

Removes the custom DNS rules of the specified host from the current application. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> You can call [addCustomDnsRule](arkts-network-connection-addcustomdnsrule-f.md) to add a custom rule.

**Since:** 11

**Required permissions:** ohos.permission.INTERNET

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Communication.NetManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| host | string | Yes | Name of the host for which DNS rules are to be deleted. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the DNS rules are removed successfully, **error** is **undefined**. Otherwise, **error** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-invalid-parameter-value) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |

**Examples**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.removeCustomDnsRule("xxxx", (error: BusinessError, data: void) => {
  if (error) {
    console.error(`Failed to remove custom dns rule. Code:${error.code}, message:${error.message}`);
    return;
  }
  console.info("Succeeded to get data: " + JSON.stringify(data));
})
```


<a id="removecustomdnsrule-1"></a>

## removeCustomDnsRule

```TypeScript
function removeCustomDnsRule(host: string): Promise<void>
```

Removes the custom DNS rules of the specified host from the current application. This API uses a promise to return the result.

> **NOTE:** 
> 
> You can call [addCustomDnsRule](arkts-network-connection-addcustomdnsrule-f.md) to add a custom rule.

**Since:** 11

**Required permissions:** ohos.permission.INTERNET

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Communication.NetManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| host | string | Yes | Name of the host for which DNS rules are to be deleted. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-invalid-parameter-value) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |

**Examples**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.removeCustomDnsRule("xxxx").then(() => {
    console.info("success");
}).catch((error: BusinessError) => {
    console.error(JSON.stringify(error));
})
```
