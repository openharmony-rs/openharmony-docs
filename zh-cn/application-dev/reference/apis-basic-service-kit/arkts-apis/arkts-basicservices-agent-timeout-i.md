# Timeout

任务的超时配置。任务处于等待状态的时间不参与计算，上传下载任务会存在以下任务等待的原因: [WaitingReason&lt;sup&gt;20+&lt;/sup&gt;](arkts-basicservices-agent-waitingreason-e.md#WaitingReason) 。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-agent-interface Timeout--><!--Device-agent-interface Timeout-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## connectionTimeout

```TypeScript
connectionTimeout?: int
```

任务连接超时时间，单位为秒。连接超时是指客户端与服务器建立连接的最大耗时。若不设置则使用默认值60秒，允许设置的最小值为1秒。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Timeout-connectionTimeout?: int--><!--Device-Timeout-connectionTimeout?: int-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## totalTimeout

```TypeScript
totalTimeout?: int
```

任务总超时时间，单位为秒。总超时包括建立连接、发送请求和接收响应的全部时间。未指定时使用默认值604800秒（1周）。允许设置的最小值为1秒，最大值为604800秒（1周）。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Timeout-totalTimeout?: int--><!--Device-Timeout-totalTimeout?: int-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

