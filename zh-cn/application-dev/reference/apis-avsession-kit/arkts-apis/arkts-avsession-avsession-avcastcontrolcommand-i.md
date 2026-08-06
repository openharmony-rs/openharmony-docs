# AVCastControlCommand

投播控制器接受的命令的对象描述。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-avSession-interface AVCastControlCommand--><!--Device-avSession-interface AVCastControlCommand-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

## command

```TypeScript
command: AVCastControlCommandType
```

命令。每种命令对应的参数不同，具体的对应关系可查阅[AVCastControlCommandType]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。

**类型：** AVCastControlCommandType

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastControlCommand-command: AVCastControlCommandType--><!--Device-AVCastControlCommand-command: AVCastControlCommandType-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

## parameter

```TypeScript
parameter?: media.PlaybackSpeed | double | string | LoopMode
```

命令对应的参数。

**类型：** media.PlaybackSpeed \| double \| string \| LoopMode

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastControlCommand-parameter?: media.PlaybackSpeed | double | string | LoopMode--><!--Device-AVCastControlCommand-parameter?: media.PlaybackSpeed | double | string | LoopMode-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

