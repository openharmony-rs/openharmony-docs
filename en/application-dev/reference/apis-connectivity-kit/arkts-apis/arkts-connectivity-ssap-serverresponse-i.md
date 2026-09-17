# ServerResponse

Defines a response to a client request.

**Since:** 26.0.0

**System capability:** SystemCapability.Communication.NearLink.Base

## Modules to Import

```TypeScript
import { ssap } from '@kit.ConnectivityKit';
```

## address

```TypeScript
address: string
```

Client device address. The address format is **11:22:33:AA:BB:FF**.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

## requestId

```TypeScript
requestId: number
```

Request ID. The value range is [0, 65535]. The ID must be the same as the value of **requestId** in the received [PropertyReadRequest](arkts-connectivity-ssap-propertyreadrequest-i.md) or [PropertyWriteRequest](arkts-connectivity-ssap-propertywriterequest-i.md), which is used to associate the request with the response.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

## value

```TypeScript
value: ArrayBuffer
```

Data value of the response.

**Type:** ArrayBuffer

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base
