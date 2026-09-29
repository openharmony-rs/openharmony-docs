# DataParams

```TypeScript
interface DataParams
```

Defines the parameters for port data sending and receiving.

**Since:** 26.0.0

<!--Device-dataTransfer-interface DataParams--><!--Device-dataTransfer-interface DataParams-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

## Modules to Import

```TypeScript
import { dataTransfer } from '@kit.ConnectivityKit';
```

## address

```TypeScript
address: string
```

NearLink address of a remote device. The address format is **11:22:33:AA:BB:FF**.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DataParams-address: string--><!--Device-DataParams-address: string-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

## data

```TypeScript
data: ArrayBuffer
```

Data packet. When this parameter is used in [dataTransfer.writeData](arkts-connectivity-datatransfer-writedata-f.md), it indicates the data to be sent. When the parameter is used in [dataTransfer.onReadData](arkts-connectivity-datatransfer-onreaddata-f.md), it indicates the received data.

**Type:** ArrayBuffer

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DataParams-data: ArrayBuffer--><!--Device-DataParams-data: ArrayBuffer-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

## uuid

```TypeScript
uuid: string
```

NearLink service UUID, which is a string of 36 characters. The value consists of 32 hexadecimal digits and four hyphens (-), for example, **FFFFFFFF-1234-5678-ABCD-000000001234**, which indicates a 128-bit ID. The value cannot be set to a standard NearLink UUID.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DataParams-uuid: string--><!--Device-DataParams-uuid: string-End-->

**System capability:** SystemCapability.Communication.NearLink.Base
