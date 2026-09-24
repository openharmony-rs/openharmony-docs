# isIfaceActive (System API)

## Modules to Import

```TypeScript
import { ethernet } from '@kit.NetworkKit';
```

## isIfaceActive

```TypeScript
function isIfaceActive(iface: string, callback: AsyncCallback<number>): void
```

Checks whether the interface is activated. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.GET_NETWORK_INFO

**System capability:** SystemCapability.Communication.NetManager.Ethernet

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| iface | string | Yes | Interface name. If this parameter is left empty, the API checks for any active network interface. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. The value **1** means that the network interface is active, **0** means that the network interface is inactive, and any other value means that an error has occurred. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2200001](../errorcode-net-ethernet.md#2200001-invalid-parameter-value) | Invalid parameter value. |
| [2200002](../errorcode-net-ethernet.md#2200002-service-connection-failure) | Failed to connect to the service. |
| [2200003](../errorcode-net-ethernet.md#2200003-system-internal-error) | System internal error. |
| [2201005](../errorcode-net-ethernet.md#2201005-device-information-not-exist) | Device information does not exist. |

**Examples**

```TypeScript
import { ethernet } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

ethernet.isIfaceActive("eth0", (error: BusinessError, value: number) => {
  if (error) {
    console.error("whether2Activate callback error = " + JSON.stringify(error));
  } else {
    console.info("whether2Activate callback = " + JSON.stringify(value));
  }
});
```


<a id="isifaceactive-1"></a>

## isIfaceActive

```TypeScript
function isIfaceActive(iface: string): Promise<number>
```

Checks whether the interface is activated. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.GET_NETWORK_INFO

**System capability:** SystemCapability.Communication.NetManager.Ethernet

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| iface | string | Yes | Interface name. If this parameter is left empty, the API checks for any active network interface. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the result. The value **1** means that the network interface is active, **0** means that the network interface is inactive, and any other value means that an error has occurred. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2200001](../errorcode-net-ethernet.md#2200001-invalid-parameter-value) | Invalid parameter value. |
| [2200002](../errorcode-net-ethernet.md#2200002-service-connection-failure) | Failed to connect to the service. |
| [2200003](../errorcode-net-ethernet.md#2200003-system-internal-error) | System internal error. |
| [2201005](../errorcode-net-ethernet.md#2201005-device-information-not-exist) | Device information does not exist. |

**Examples**

```TypeScript
import { ethernet } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

ethernet.isIfaceActive("eth0").then((data: number) => {
  console.info("isIfaceActive promise = " + JSON.stringify(data));
}).catch((error: BusinessError) => {
  console.error("isIfaceActive promise error = " + JSON.stringify(error));
});
```
