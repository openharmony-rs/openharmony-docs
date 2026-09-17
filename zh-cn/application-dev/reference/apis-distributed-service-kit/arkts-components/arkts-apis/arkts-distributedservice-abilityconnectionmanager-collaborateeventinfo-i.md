# CollaborateEventInfo

协同事件信息。

**起始版本：** 18

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## 导入模块

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## eventMsg

```TypeScript
eventMsg?: string
```

表示协同事件的消息内容。eventType为SEND_FAILURE或COLOR_SPACE_CONVERSION_FAILURE时存在，包含事件相关的详细消息信息。

**类型：** string

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## eventType

```TypeScript
eventType: CollaborateEventType
```

表示协同事件的类型。（0表示SEND_FAILURE，1表示COLOR_SPACE_CONVERSION_FAILURE）。

**类型：** [CollaborateEventType](arkts-distributedservice-abilityconnectionmanager-collaborateeventtype-e.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration
