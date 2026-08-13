# EventCallbackInfo

回调方法的接收信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-abilityConnectionManager-interface EventCallbackInfo--><!--Device-abilityConnectionManager-interface EventCallbackInfo-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## data

```TypeScript
data?: ArrayBuffer
```

表示接收的字节流。

**类型：** ArrayBuffer

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EventCallbackInfo-data?: ArrayBuffer--><!--Device-EventCallbackInfo-data?: ArrayBuffer-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## msg

```TypeScript
msg?: string
```

表示接收的消息。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EventCallbackInfo-msg?: string--><!--Device-EventCallbackInfo-msg?: string-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## reason

```TypeScript
reason?: DisconnectReason
```

表示断连原因。

**类型：** [DisconnectReason](arkts-distributedservice-abilityconnectionmanager-disconnectreason-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EventCallbackInfo-reason?: DisconnectReason--><!--Device-EventCallbackInfo-reason?: DisconnectReason-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## sessionId

```TypeScript
sessionId: int
```

表示当前事件对应的协同会话ID。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EventCallbackInfo-sessionId: int--><!--Device-EventCallbackInfo-sessionId: int-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

