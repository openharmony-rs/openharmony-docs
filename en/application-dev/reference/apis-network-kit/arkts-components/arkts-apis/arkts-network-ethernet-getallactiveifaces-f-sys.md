# getAllActiveIfaces (System API)

## Modules to Import

```TypeScript
import { ethernet } from '@kit.NetworkKit';
```

## getAllActiveIfaces

```TypeScript
function getAllActiveIfaces(callback: AsyncCallback<Array<string>>): void
```

Obtains the active network interface. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.GET_NETWORK_INFO

**System capability:** SystemCapability.Communication.NetManager.Ethernet

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;string&gt;&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [2200002](../errorcode-net-ethernet.md#2200002-service-connection-failure) | Failed to connect to the service. |
| [2200003](../errorcode-net-ethernet.md#2200003-system-internal-error) | System internal error. |

**Examples**

```TypeScript
import { ethernet } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

ethernet.getAllActiveIfaces((error: BusinessError, value: string[]) => {
  if (error) {
    console.error("getAllActiveIfaces callback error = " + JSON.stringify(error));
  } else {
    console.info("getAllActiveIfaces callback value.length = " + JSON.stringify(value.length));
    for (let i = 0; i < value.length; i++) {
      console.info("getAllActiveIfaces callback = " + JSON.stringify(value[i]));
    }
  }
});
```

```TypeScript
import { ethernet } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

ethernet.getAllActiveIfaces().then((data: string[]) => {
  console.info("getAllActiveIfaces promise data.length = " + JSON.stringify(data.length));
  for (let i = 0; i < data.length; i++) {
    console.info("getAllActiveIfaces promise  = " + JSON.stringify(data[i]));
  }
}).catch((error:BusinessError) => {
  console.error("getAllActiveIfaces promise error = " + JSON.stringify(error));
});
```


## getAllActiveIfaces

```TypeScript
function getAllActiveIfaces(): Promise<Array<string>>
```

Obtains the active network interface. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.GET_NETWORK_INFO

**System capability:** SystemCapability.Communication.NetManager.Ethernet

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [2200002](../errorcode-net-ethernet.md#2200002-service-connection-failure) | Failed to connect to the service. |
| [2200003](../errorcode-net-ethernet.md#2200003-system-internal-error) | System internal error. |

**Examples**

See [getAllActiveIfaces](#getallactiveifaces)
