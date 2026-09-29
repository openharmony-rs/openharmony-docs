# Method (System API)

```TypeScript
interface Method
```

Represents a method of the service.

**Since:** 26.0.0

<!--Device-ssap-interface Method--><!--Device-ssap-interface Method-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { ssap } from '@kit.ConnectivityKit';
```

## methodUuid

```TypeScript
methodUuid: string
```

Method UUID. The data format is the same as that of **serviceUuid**.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-Method-methodUuid: string--><!--Device-Method-methodUuid: string-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

**System API:** This is a system API.

## parameter

```TypeScript
parameter?: ArrayBuffer
```

Method parameters. The data format is defined by the specific service. By default, this field is not used if not set.

**Type:** ArrayBuffer

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-Method-parameter?: ArrayBuffer--><!--Device-Method-parameter?: ArrayBuffer-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

**System API:** This is a system API.

## result

```TypeScript
result?: ArrayBuffer
```

Return value of the method. The data format is defined by the specific service. By default, this field is not used if not set.

**Type:** ArrayBuffer

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-Method-result?: ArrayBuffer--><!--Device-Method-result?: ArrayBuffer-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

**System API:** This is a system API.

## serviceUuid

```TypeScript
serviceUuid: string
```

NearLink service UUID, which is a string of 36 characters. The value consists of 32 hexadecimal digits and four hyphens (-), for example, **FFFFFFFF-1234-5678-ABCD-000000001234**, which indicates a 128-bit ID. The value cannot be set to a standard NearLink UUID.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-Method-serviceUuid: string--><!--Device-Method-serviceUuid: string-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

**System API:** This is a system API.
