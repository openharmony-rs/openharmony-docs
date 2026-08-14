# ConnectResult

客户端调用connect()后，返回的连接结果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-linkEnhance-interface ConnectResult--><!--Device-linkEnhance-interface ConnectResult-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## deviceId

```TypeScript
deviceId: string
```

对端设备ID，成功返回对端设备的deviceId，失败返回空字符串。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ConnectResult-deviceId: string--><!--Device-ConnectResult-deviceId: string-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## reason

```TypeScript
reason: int
```

连接成功返回0，连接失败返回错误码： - 32390200：表示客户端连接超时。 - 32390201：表示服务端服务未启动。 - 32390300：表示内部错误。 更多关于错误码的详细介绍请参考[增强连接错误码](../../apis-distributedservice-kit/errorcode-link-enhance.md)。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ConnectResult-reason: int--><!--Device-ConnectResult-reason: int-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## success

```TypeScript
success: boolean
```

连接结果，true表示连接成功，false表示连接失败。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ConnectResult-success: boolean--><!--Device-ConnectResult-success: boolean-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

