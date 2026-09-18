# NetAddress

Defines a network address.

**Since:** 8

**System capability:** SystemCapability.Communication.NetManager.Core

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## address

```TypeScript
address: string
```

Network address.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NetManager.Core

## family

```TypeScript
family?: number
```

Address family identifier. The value is **1** for IPv4 and **2** for IPv6. The default value is **1**.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NetManager.Core

## port

```TypeScript
port?: number
```

Port number. The value range is [0, 65535]. The default value is **0**.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NetManager.Core
