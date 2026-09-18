# setDiscoverable (System API)

## Modules to Import

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## setDiscoverable

```TypeScript
function setDiscoverable(enable: boolean, callback: AsyncCallback<void>): void
```

Enable or disable device to be discoverable, used at sink side.

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | true: can be discoverable, false: cannot be discoverable. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | a callback function |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System App. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |

**Examples**

```TypeScript
avSession.setDiscoverable(true, () => {
    console.info('Succeeded in setting discoverable.');
});
```

```TypeScript
avSession.setDiscoverable(true).then(() => {
  console.info('Succeeded in setting discoverable.');
});
```


## setDiscoverable

```TypeScript
function setDiscoverable(enable: boolean): Promise<void>
```

Enable or disable device to be discoverable, used at sink side.

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | true: can be discoverable, false: cannot be discoverable. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise for the result |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System App. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |

**Examples**

See [setDiscoverable](#setdiscoverable)
