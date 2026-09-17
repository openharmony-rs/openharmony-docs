# ConnectResult

连接的结果。

**起始版本：** 18

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## 导入模块

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## errorCode

```TypeScript
errorCode?: ConnectErrorCode
```

表示连接错误码。连接失败时存在，用于标识具体的错误原因。连接成功时不存在。

**类型：** [ConnectErrorCode](arkts-distributedservice-abilityconnectionmanager-connecterrorcode-e.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## isConnected

```TypeScript
isConnected: boolean
```

true表示连接成功；false表示连接失败，具体原因请查看errorCode字段或reason字段。

**类型：** boolean

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## reason

```TypeScript
reason?: string
```

表示拒绝连接的原因，仅在连接被拒绝时返回。该值为对端应用调用reject接口时传入的reason参数，用于告知本端拒绝的具体原因。连接成功或未被拒绝时无此字段。

**类型：** string

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration
