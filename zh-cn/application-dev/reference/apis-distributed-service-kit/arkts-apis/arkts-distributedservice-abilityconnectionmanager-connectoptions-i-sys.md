# ConnectOptions

应用连接时所需的连接选项。

**起始版本：** 18

<!--Device-abilityConnectionManager-interface ConnectOptions--><!--Device-abilityConnectionManager-interface ConnectOptions-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## 导入模块

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## needReceiveStream

```TypeScript
needReceiveStream?: boolean
```

Receive Stream Data Configuration Options. WiFi needs to be turned on.

**类型：** boolean

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ConnectOptions-needReceiveStream?: boolean--><!--Device-ConnectOptions-needReceiveStream?: boolean-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。

## needSendStream

```TypeScript
needSendStream?: boolean
```

Send Stream Data Configuration Options. WiFi needs to be turned on.

**类型：** boolean

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ConnectOptions-needSendStream?: boolean--><!--Device-ConnectOptions-needSendStream?: boolean-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。

