# SendRequestResult

```TypeScript
interface SendRequestResult
```

Defines the response to the request.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [RequestResult](arkts-ipc-rpc-requestresult-i.md)

<!--Device-rpc-interface SendRequestResult--><!--Device-rpc-interface SendRequestResult-End-->

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

<!--Device-SendRequestResult-code: number--><!--Device-SendRequestResult-code: number-End-->

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

<!--Device-SendRequestResult-data: MessageParcel--><!--Device-SendRequestResult-data: MessageParcel-End-->

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

<!--Device-SendRequestResult-errCode: number--><!--Device-SendRequestResult-errCode: number-End-->

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

<!--Device-SendRequestResult-reply: MessageParcel--><!--Device-SendRequestResult-reply: MessageParcel-End-->

**System capability:** SystemCapability.Communication.IPC.Core
