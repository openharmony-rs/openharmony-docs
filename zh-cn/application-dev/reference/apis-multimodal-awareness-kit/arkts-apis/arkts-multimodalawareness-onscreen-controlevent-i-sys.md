# ControlEvent（系统接口）

控制事件。

**起始版本：** 20

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { onScreen } from '@kit.MultimodalAwarenessKit';
```

## eventType

```TypeScript
eventType: EventType
```

控制事件类型。

**类型：** EventType

**起始版本：** 20

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## hookId

```TypeScript
hookId?: number
```

控制事件对应的hook ID。控制事件要操作的hook ID和该次会话对应的session ID都由某次会话获取的[PageContent](arkts-multimodalawareness-onscreen-pagecontent-i-sys.md)提供。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## sessionId

```TypeScript
sessionId: number
```

控制事件要操作的session ID。控制事件要操作的hook ID和该次会话对应的session ID都由某次会话获取的[PageContent](arkts-multimodalawareness-onscreen-pagecontent-i-sys.md)提供。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## windowId

```TypeScript
windowId: number
```

控制事件要操作的窗口的window ID。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。
