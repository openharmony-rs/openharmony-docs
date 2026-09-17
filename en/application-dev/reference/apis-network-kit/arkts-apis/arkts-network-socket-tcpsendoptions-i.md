# TCPSendOptions

Defines the parameters for sending data over a TCP socket connection.

**Since:** 7

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## data

```TypeScript
data: string | ArrayBuffer
```

Data to send.

**Type:** string &#124; ArrayBuffer

**Since:** 7

**System capability:** SystemCapability.Communication.NetStack

## encoding

```TypeScript
encoding?: string
```

Character encoding format. The options are as follows: **UTF-8**, **UTF-16BE**, **UTF-16LE**, **UTF-16**, **US-ASCII**, and **ISO-8859-1**. The default value is **UTF-8**.

**Type:** string

**Since:** 7

**System capability:** SystemCapability.Communication.NetStack
