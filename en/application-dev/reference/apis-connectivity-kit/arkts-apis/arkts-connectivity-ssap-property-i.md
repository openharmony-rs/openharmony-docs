# Property

Represents a service Property.

**Since:** 26.0.0

**System capability:** SystemCapability.Communication.NearLink.Base

## Modules to Import

```TypeScript
import { ssap } from '@kit.ConnectivityKit';
```

## descriptors

```TypeScript
descriptors?: PropertyDescriptor[]
```

Descriptors of the current property. By default, this field is not used if not set.

**Type:** PropertyDescriptor[]

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

## operation

```TypeScript
operation?: number
```

Operation modes supported by the property. The default value is **READABLE|WRITE_NO_RESPONSE**, indicating that the property is readable and writable and no response is required. To enable a property to support an operation, you need to assign a value to this field, for example, **READABLE | WRITE_NO_RESPONSE | NOTIFY**. The value range is [0, 15]. For details about the operation corresponding to each bit, see [Operation](arkts-connectivity-ssap-operation-e.md). The value should be an integer.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

## propertyUuid

```TypeScript
propertyUuid: string
```

Property UUID, in the same format as **serviceUuid**.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

## serviceUuid

```TypeScript
serviceUuid: string
```

NearLink service UUID, which is a string of 36 characters. The value consists of 32 hexadecimal digits and four hyphens (-), for example, **FFFFFFFF-1234-5678-ABCD-000000001234**, which indicates a 128-bit identifier. Standard NearLink UUIDs are not allowed.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

## value

```TypeScript
value: ArrayBuffer
```

Data value of a property.

**Type:** ArrayBuffer

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base
