# SendRequestResult

Defines the response to the request.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [RequestResult](arkts-ipc-rpc-requestresult-i.md)

**System capability:** SystemCapability.Communication.IPC.Core

## Modules to Import

```TypeScript
import { rpc } from '@kit.IPCKit';
```

## code

```TypeScript
code: number
```

Message code.

**Type:** number

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [code](arkts-ipc-rpc-requestresult-i.md#code)

**System capability:** SystemCapability.Communication.IPC.Core

## data

```TypeScript
data: MessageParcel
```

**MessageParcel** object sent to the remote process.

**Type:** [MessageParcel](arkts-ipc-rpc-messageparcel-c.md)

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [data](arkts-ipc-rpc-requestresult-i.md#data)

**System capability:** SystemCapability.Communication.IPC.Core

## errCode

```TypeScript
errCode: number
```

Error code.

**Type:** number

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [errCode](arkts-ipc-rpc-requestresult-i.md#errcode)

**System capability:** SystemCapability.Communication.IPC.Core

## reply

```TypeScript
reply: MessageParcel
```

**MessageParcel** object returned by the remote process.

**Type:** [MessageParcel](arkts-ipc-rpc-messageparcel-c.md)

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [reply](arkts-ipc-rpc-requestresult-i.md#reply)

**System capability:** SystemCapability.Communication.IPC.Core
