# ConnectOptions

应用连接时所需的连接选项。

**起始版本：** 18

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## 导入模块

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## needSendData

```TypeScript
needSendData?: boolean
```

是否需要传输数据。传入true表示需要传输数据（可调用sendMessage和sendData方法），传入false表示不需要传输数据。不传入时默认为false。

**类型：** boolean

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## parameters

```TypeScript
parameters?: Record<string, string>
```

配置连接所需的额外信息。当需要传递自定义参数到对端设备时传入此参数，例如身份标识、业务标识等。不传入时不传递额外信息。

**类型：** Record&lt;string, string&gt;

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## startOptions

```TypeScript
startOptions?: StartOptionParams
```

应用启动选项。START_IN_FOREGROUND（值为0）表示将对端应用启动至前台，适合需要用户交互的场景。不传入时使用系统默认启动配置。

**类型：** [StartOptionParams](arkts-distributedservice-abilityconnectionmanager-startoptionparams-e.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration
