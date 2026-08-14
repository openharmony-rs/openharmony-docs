# RequestResult

发送请求的响应结果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-rpc-interface RequestResult--><!--Device-rpc-interface RequestResult-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

## code

```TypeScript
code: int
```

消息代码。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-RequestResult-code: int--><!--Device-RequestResult-code: int-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

## data

```TypeScript
data: MessageSequence
```

发送给对端进程的MessageSequence对象。

**类型：** [MessageSequence](arkts-ipc-rpc-messagesequence-c.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-RequestResult-data: MessageSequence--><!--Device-RequestResult-data: MessageSequence-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

## errCode

```TypeScript
errCode: int
```

错误码。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-RequestResult-errCode: int--><!--Device-RequestResult-errCode: int-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

## reply

```TypeScript
reply: MessageSequence
```

对端进程返回的MessageSequence对象。

**类型：** [MessageSequence](arkts-ipc-rpc-messagesequence-c.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-RequestResult-reply: MessageSequence--><!--Device-RequestResult-reply: MessageSequence-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

