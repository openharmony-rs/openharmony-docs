# SendRequestResult

发送请求的响应结果。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [RequestResult](arkts-ipc-rpc-requestresult-i.md)

<!--Device-rpc-interface SendRequestResult--><!--Device-rpc-interface SendRequestResult-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

## 导入模块

```TypeScript
import { rpc } from '@kit.IPCKit';
```

## code

```TypeScript
code: number
```

消息代码。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [code](arkts-ipc-rpc-requestresult-i.md#code)

<!--Device-SendRequestResult-code: number--><!--Device-SendRequestResult-code: number-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

## data

```TypeScript
data: MessageParcel
```

发送给对端进程的MessageParcel对象。

**类型：** [MessageParcel](arkts-ipc-rpc-messageparcel-c.md)

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [data](arkts-ipc-rpc-requestresult-i.md#data)

<!--Device-SendRequestResult-data: MessageParcel--><!--Device-SendRequestResult-data: MessageParcel-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

## errCode

```TypeScript
errCode: number
```

错误码。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [errCode](arkts-ipc-rpc-requestresult-i.md#errcode)

<!--Device-SendRequestResult-errCode: number--><!--Device-SendRequestResult-errCode: number-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

## reply

```TypeScript
reply: MessageParcel
```

对端进程返回的MessageParcel对象。

**类型：** [MessageParcel](arkts-ipc-rpc-messageparcel-c.md)

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [reply](arkts-ipc-rpc-requestresult-i.md#reply)

<!--Device-SendRequestResult-reply: MessageParcel--><!--Device-SendRequestResult-reply: MessageParcel-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

