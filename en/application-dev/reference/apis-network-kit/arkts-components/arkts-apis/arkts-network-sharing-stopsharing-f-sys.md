# stopSharing (System API)

## Modules to Import

```TypeScript
import { sharing } from '@kit.NetworkKit';
```

## stopSharing

```TypeScript
function stopSharing(type: SharingIfaceType, callback: AsyncCallback<void>): void
```

Disables sharing of a specified type. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.CONNECTIVITY_INTERNAL

**System capability:** SystemCapability.Communication.NetManager.NetSharing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SharingIfaceType](arkts-network-sharing-sharingifacetype-e-sys.md) | Yes | Sharing type. The value **0** means Wi-Fi hotspot sharing, **1** means USB sharing, and **2** means Bluetooth sharing. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2200001](../errorcode-net-ethernet.md#2200001-invalid-parameter-value) | Invalid parameter value. |
| [2200002](../errorcode-net-ethernet.md#2200002-service-connection-failure) | Failed to connect to the service. |
| [2200003](../errorcode-net-ethernet.md#2200003-system-internal-error) | System internal error. |
| [2202004](../errorcode-net-sharing.md#2202004-shared-iface-unavailable) | Try to share an unavailable iface. |
| [2202005](../errorcode-net-sharing.md#2202005-wi-fi-sharing-failure) | WiFi sharing failed. |
| [2202006](../errorcode-net-sharing.md#2202006-bluetooth-sharing-failure) | Bluetooth sharing failed. |
| [2202011](../errorcode-net-sharing.md#2202011-failed-to-obtain-the-network-sharing-configuration) | Cannot get network sharing configuration. |

**Examples**

```TypeScript
import { sharing } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let SHARING_WIFI = 0;
sharing.stopSharing(SHARING_WIFI, (error: BusinessError) => {
  console.error(JSON.stringify(error));
});
```

```TypeScript
import { sharing } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let SHARING_WIFI = 0;
sharing
  .stopSharing(SHARING_WIFI)
  .then(() => {
    console.info('stop wifi sharing successful');
  })
  .catch((error: BusinessError) => {
    console.error('stop wifi sharing failed');
  });
```


## stopSharing

```TypeScript
function stopSharing(type: SharingIfaceType): Promise<void>
```

Disables sharing of a specified type. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.CONNECTIVITY_INTERNAL

**System capability:** SystemCapability.Communication.NetManager.NetSharing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SharingIfaceType](arkts-network-sharing-sharingifacetype-e-sys.md) | Yes | Sharing type. The value **0** means Wi-Fi hotspot sharing, **1** means USB sharing, and **2** means Bluetooth sharing. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2200001](../errorcode-net-ethernet.md#2200001-invalid-parameter-value) | Invalid parameter value. |
| [2200002](../errorcode-net-ethernet.md#2200002-service-connection-failure) | Failed to connect to the service. |
| [2200003](../errorcode-net-ethernet.md#2200003-system-internal-error) | System internal error. |
| [2202004](../errorcode-net-sharing.md#2202004-shared-iface-unavailable) | Try to share an unavailable iface. |
| [2202005](../errorcode-net-sharing.md#2202005-wi-fi-sharing-failure) | WiFi sharing failed. |
| [2202006](../errorcode-net-sharing.md#2202006-bluetooth-sharing-failure) | Bluetooth sharing failed. |
| [2202011](../errorcode-net-sharing.md#2202011-failed-to-obtain-the-network-sharing-configuration) | Cannot get network sharing configuration. |

**Examples**

See [stopSharing](#stopsharing)
