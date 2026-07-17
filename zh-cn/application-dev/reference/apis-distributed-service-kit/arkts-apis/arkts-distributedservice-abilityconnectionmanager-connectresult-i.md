# ConnectResult

连接的结果。

**起始版本：** 18

<!--Device-abilityConnectionManager-interface ConnectResult--><!--Device-abilityConnectionManager-interface ConnectResult-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## 导入模块

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## errorCode

```TypeScript
errorCode?: ConnectErrorCode
```

表示连接错误码。

**类型：** ConnectErrorCode

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ConnectResult-errorCode?: ConnectErrorCode--><!--Device-ConnectResult-errorCode?: ConnectErrorCode-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## isConnected

```TypeScript
isConnected: boolean
```

true表示连接成功，false表示连接失败。

**类型：** boolean

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ConnectResult-isConnected: boolean--><!--Device-ConnectResult-isConnected: boolean-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## reason

```TypeScript
reason?: string
```

表示拒绝连接的原因。

**类型：** string

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ConnectResult-reason?: string--><!--Device-ConnectResult-reason?: string-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

