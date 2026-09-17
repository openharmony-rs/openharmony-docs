# getSharingState (System API)

## Modules to Import

```TypeScript
import { sharing } from '@kit.NetworkKit';
```

## getSharingState

```TypeScript
function getSharingState(type: SharingIfaceType, callback: AsyncCallback<SharingIfaceState>): void
```

Obtains the network sharing state of the specified type. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.CONNECTIVITY_INTERNAL

**System capability:** SystemCapability.Communication.NetManager.NetSharing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SharingIfaceType](arkts-network-sharing-sharingifacetype-e-sys.md) | Yes | Sharing type. The value **0** means Wi-Fi hotspot sharing, **1** means USB sharing, and **2** means Bluetooth sharing. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[SharingIfaceState](arkts-network-sharing-sharingifacestate-e-sys.md)&gt; | Yes | Callback used to return the network sharing state. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2200001](../errorcode-net-ethernet.md#2200001-invalid-parameter-value) | Invalid parameter value. |
| [2200002](../errorcode-net-ethernet.md#2200002-service-connection-failure) | Failed to connect to the service. |
| [2200003](../errorcode-net-ethernet.md#2200003-system-internal-error) | System internal error. |

**Examples**

```TypeScript
import { sharing } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let SHARING_WIFI = 0;
sharing.getSharingState(SHARING_WIFI, (error: BusinessError, data: sharing.SharingIfaceState) => {
  console.error(JSON.stringify(error));
  console.info(JSON.stringify(data));
});
```

```TypeScript
import { sharing } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let SHARING_WIFI = 0;
sharing
  .getSharingState(SHARING_WIFI)
  .then((data: sharing.SharingIfaceState) => {
    console.info(JSON.stringify(data));
  })
  .catch((error: BusinessError) => {
    console.error(JSON.stringify(error));
  });
```


## getSharingState

```TypeScript
function getSharingState(type: SharingIfaceType): Promise<SharingIfaceState>
```

Obtains the network sharing state of the specified type. This API uses a promise to return the result.

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
| Promise&lt;[SharingIfaceState](arkts-network-sharing-sharingifacestate-e-sys.md)&gt; | Promise used to return the network sharing state. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2200001](../errorcode-net-ethernet.md#2200001-invalid-parameter-value) | Invalid parameter value. |
| [2200002](../errorcode-net-ethernet.md#2200002-service-connection-failure) | Failed to connect to the service. |
| [2200003](../errorcode-net-ethernet.md#2200003-system-internal-error) | System internal error. |

**Examples**

See [getSharingState](#getsharingstate)
