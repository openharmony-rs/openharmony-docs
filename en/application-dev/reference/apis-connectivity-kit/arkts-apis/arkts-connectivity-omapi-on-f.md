# on

## Modules to Import

```TypeScript
import { omapi } from '@kit.ConnectivityKit';
```

## on('stateChanged')

```TypeScript
function on(type: 'stateChanged', callback: Callback<ServiceState>): void
```

Enables listening for service status change events.

Call this API to register a callback after you use [omapi.newSEService](arkts-connectivity-omapi-newseservice-f.md#newseserviceservicestate) or [omapi.createService](arkts-connectivity-omapi-createservice-f.md) to create a service.

**Since:** 18

**System capability:** SystemCapability.Communication.SecureElement

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'stateChanged' | Yes | Event type. It has a fixed value of **stateChanged**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ServiceState](arkts-connectivity-omapi-servicestate-e.md)&gt; | Yes | Callback used to return the SE service state. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
