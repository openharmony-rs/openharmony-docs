# AVCastControlCommand

投播控制器接受的命令的对象描述。

**起始版本：** 10

<!--Device-avSession-interface AVCastControlCommand--><!--Device-avSession-interface AVCastControlCommand-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## command

```TypeScript
command: AVCastControlCommandType
```

命令。每种命令对应的参数不同，具体的对应关系可查阅[AVCastControlCommandType](arkts-avsession-avsession-avcastcontrolcommandtype-t.md)。

**类型：** AVCastControlCommandType

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastControlCommand-command: AVCastControlCommandType--><!--Device-AVCastControlCommand-command: AVCastControlCommandType-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

## parameter

```TypeScript
parameter?: media.PlaybackSpeed | number | string | LoopMode
```

命令对应的参数。

**类型：** media.PlaybackSpeed | number | string | LoopMode

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastControlCommand-parameter?: media.PlaybackSpeed | double | string | LoopMode--><!--Device-AVCastControlCommand-parameter?: media.PlaybackSpeed | double | string | LoopMode-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

