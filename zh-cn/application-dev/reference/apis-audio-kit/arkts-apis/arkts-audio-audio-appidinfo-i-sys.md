# AppIdInfo（系统接口）

应用ID信息，包含应用的UID（标识应用身份）、PID（标识运行中的进程）、Token ID（用于常规身份识别与权限校验）和FullToken ID（携带应用完整身份权限信息，用于原始应用溯源与全链路权限校验）。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## appFullTokenId

```TypeScript
appFullTokenId: number
```

应用FullToken ID，携带应用完整身份权限信息，用于原始应用溯源与全链路权限校验。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

## appPid

```TypeScript
appPid: number
```

应用PID，用于标识运行中的进程。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

## appTokenId

```TypeScript
appTokenId: number
```

应用Token ID，用于常规身份识别与权限校验。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

## appUid

```TypeScript
appUid: number
```

应用UID，用于标识应用身份。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。
