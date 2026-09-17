# ConnectOptions

应用连接时所需的连接选项。

**起始版本：** 18

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## 导入模块

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## needReceiveStream

```TypeScript
needReceiveStream?: boolean
```

true表示需要接收流（当本端需要从对端接收视频流时选择），false表示不需要接收流（当本端只发送不接收时选择）。默认值为false。

**类型：** boolean

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。

## needSendStream

```TypeScript
needSendStream?: boolean
```

true表示需要发送流（当本端需要向对端发送视频流时选择），false表示不需要发送流（当本端只接收不发送时选择）。默认值为false。

**类型：** boolean

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。
