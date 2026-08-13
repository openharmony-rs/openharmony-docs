# StreamParam（系统接口）

Streaming configuration parameters.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-abilityConnectionManager-interface StreamParam--><!--Device-abilityConnectionManager-interface StreamParam-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。

## bitrate

```TypeScript
bitrate?: int
```

视频码率，默认80(kbps)。仅在发送端有效。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StreamParam-bitrate?: int--><!--Device-StreamParam-bitrate?: int-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。

## colorSpaceConversionTarget

```TypeScript
colorSpaceConversionTarget?: colorSpaceManager.ColorSpace
```

转换的目标色彩空间。目前仅支持BT709_LIMIT。 如果发送端的视频格式为HDR且需要在传输时转换为SDR，则应设置此参数。

**类型：** colorSpaceManager.ColorSpace

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StreamParam-colorSpaceConversionTarget?: colorSpaceManager.ColorSpace--><!--Device-StreamParam-colorSpaceConversionTarget?: colorSpaceManager.ColorSpace-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。

## name

```TypeScript
name: string
```

流名称，接收端必须与发送端保持一致。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StreamParam-name: string--><!--Device-StreamParam-name: string-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。

## role

```TypeScript
role: StreamRole
```

流传输角色，可以是接收流或发送流。

**类型：** [StreamRole](arkts-distributedservice-abilityconnectionmanager-streamrole-e-sys.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StreamParam-role: StreamRole--><!--Device-StreamParam-role: StreamRole-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。

