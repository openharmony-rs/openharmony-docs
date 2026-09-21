# stopCastDeviceDiscovery (System API)

## Modules to Import

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## stopCastDeviceDiscovery

```TypeScript
function stopCastDeviceDiscovery(callback: AsyncCallback<void>): void
```

Stop device discovery.

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | a callback function |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System App. |

**Examples**

```TypeScript
avSession.stopCastDeviceDiscovery(() => {
    console.info('Succeeded in stopping cast device discovery.');
});
```


<a id="stopcastdevicediscovery-1"></a>

## stopCastDeviceDiscovery

```TypeScript
function stopCastDeviceDiscovery(): Promise<void>
```

Stop device discovery.

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise for the result |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System App. |

**Examples**

```TypeScript
avSession.stopCastDeviceDiscovery().then(() => {
  console.info('Succeeded in stopping cast device discovery.');
});
```
