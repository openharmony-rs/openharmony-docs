# startCastDeviceDiscovery (System API)

## Modules to Import

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## startCastDeviceDiscovery

```TypeScript
function startCastDeviceDiscovery(callback: AsyncCallback<void>): void
```

Start device discovery.

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
avSession.startCastDeviceDiscovery(() => {
    console.info('Succeeded in starting cast device discovery.');
});
```

```TypeScript
let filter = 2;
avSession.startCastDeviceDiscovery(filter, () => {
    console.info('Succeeded in starting cast device discovery.');
});
```

```TypeScript
let filter = 2;
let drmSchemes = ['3d5e6d35-9b9a-41e8-b843-dd3c6e72c42c'];
avSession.startCastDeviceDiscovery(filter, drmSchemes).then(() => {
  console.info('Succeeded in starting cast device discovery.');
});
```


## startCastDeviceDiscovery

```TypeScript
function startCastDeviceDiscovery(filter: number, callback: AsyncCallback<void>): void
```

Start device discovery.

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filter | number | Yes | device filter when discovering, can be an union of [ProtocolType](arkts-avsession-avsession-protocoltype-e.md) |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | a callback function |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System App. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |

**Examples**

See [startCastDeviceDiscovery](#startcastdevicediscovery)


## startCastDeviceDiscovery

```TypeScript
function startCastDeviceDiscovery(filter?: number, drmSchemes?: Array<string>): Promise<void>
```

Start device discovery.

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filter | number | No | device filter when discovering, can be an union of [ProtocolType](arkts-avsession-avsession-protocoltype-e.md)<br>**Since:** 12 |
| drmSchemes | Array&lt;string&gt; | No | filter drm-enabled devices which are represented by uuid. It is effective when protocol type is TYPE_CAST_PLUS_STREAM.<br>**Since:** 12 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise for the result |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System App.<br>**Applicable version:** 12 and later |

**Examples**

See [startCastDeviceDiscovery](#startcastdevicediscovery)
