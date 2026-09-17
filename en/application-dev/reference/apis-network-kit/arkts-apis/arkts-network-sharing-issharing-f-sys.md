# isSharing (System API)

## Modules to Import

```TypeScript
import { sharing } from '@kit.NetworkKit';
```

## isSharing

```TypeScript
function isSharing(callback: AsyncCallback<boolean>): void
```

Obtains the current network sharing status. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.CONNECTIVITY_INTERNAL

**System capability:** SystemCapability.Communication.NetManager.NetSharing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** means that network sharing is in progress, and **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [2200002](../errorcode-net-ethernet.md#2200002-service-connection-failure) | Failed to connect to the service. |
| [2200003](../errorcode-net-ethernet.md#2200003-system-internal-error) | System internal error. |
| [2202011](../errorcode-net-sharing.md#2202011-failed-to-obtain-the-network-sharing-configuration) | Cannot get network sharing configuration. |

**Examples**

```TypeScript
import { sharing } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

sharing.isSharing((error: BusinessError, data: boolean) => {
  console.error(JSON.stringify(error));
  console.info(JSON.stringify(data));
});
```

```TypeScript
import { sharing } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

sharing
  .isSharing()
  .then((data: boolean) => {
    console.info(JSON.stringify(data));
  })
  .catch((error: BusinessError) => {
    console.error(JSON.stringify(error));
  });
```


## isSharing

```TypeScript
function isSharing(): Promise<boolean>
```

Obtains the current network sharing status. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.CONNECTIVITY_INTERNAL

**System capability:** SystemCapability.Communication.NetManager.NetSharing

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means that network sharing is in progress, and **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [2200002](../errorcode-net-ethernet.md#2200002-service-connection-failure) | Failed to connect to the service. |
| [2200003](../errorcode-net-ethernet.md#2200003-system-internal-error) | System internal error. |
| [2202011](../errorcode-net-sharing.md#2202011-failed-to-obtain-the-network-sharing-configuration) | Cannot get network sharing configuration. |

**Examples**

See [isSharing](#issharing)
