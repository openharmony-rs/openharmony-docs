# AVCallState

通话状态相关属性。@interface AVCallState [since 11 - 11]

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## muted

```TypeScript
muted: boolean
```

表示通话mic是否静音。 true表示是静音，false表示不是静音。

**类型：** boolean

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## state

```TypeScript
state: CallState
```

当前通话状态。

**类型：** CallState

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core
