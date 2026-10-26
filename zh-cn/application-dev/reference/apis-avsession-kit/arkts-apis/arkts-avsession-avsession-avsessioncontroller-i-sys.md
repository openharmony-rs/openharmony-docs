# AVSessionController（系统接口）

```TypeScript
interface AVSessionController
```

AVSessionController控制器可查看会话ID，并可完成对会话发送命令及事件，获取会话元数据，播放状态信息等操作。

> **说明：** 
> 
> - 本Interface首批接口从API version 10开始支持。

**起始版本：** 10

<!--Device-avSession-interface AVSessionController--><!--Device-avSession-interface AVSessionController-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## userId

```TypeScript
readonly userId?: number
```

对应会话所属的userId。取值限定为整数。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVSessionController-readonly userId?: int--><!--Device-AVSessionController-readonly userId?: int-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**系统接口：** 此接口为系统接口。
