# AVControlCommand

会话接受的命令的对象描述。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-avSession-interface AVControlCommand--><!--Device-avSession-interface AVControlCommand-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## command

```TypeScript
command: AVControlCommandType
```

命令（不同命令对应不同参数）。

**类型：** [AVControlCommandType](arkts-avsession-avsession-avcontrolcommandtype-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVControlCommand-command: AVControlCommandType--><!--Device-AVControlCommand-command: AVControlCommandType-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## commandInfo

```TypeScript
commandInfo?: CommandInfo
```

命令信息。

**类型：** [CommandInfo](arkts-avsession-avsession-commandinfo-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVControlCommand-commandInfo?: CommandInfo--><!--Device-AVControlCommand-commandInfo?: CommandInfo-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## parameter

```TypeScript
parameter?: LoopMode | string | double
```

命令对应的参数。

**类型：** [LoopMode](arkts-avsession-avsession-loopmode-e.md) \| string \| double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVControlCommand-parameter?: LoopMode | string | double--><!--Device-AVControlCommand-parameter?: LoopMode | string | double-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

