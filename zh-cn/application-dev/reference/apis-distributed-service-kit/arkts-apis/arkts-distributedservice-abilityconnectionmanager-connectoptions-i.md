# ConnectOptions

应用连接时所需的连接选项。

**起始版本：** 18

<!--Device-abilityConnectionManager-interface ConnectOptions--><!--Device-abilityConnectionManager-interface ConnectOptions-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## 导入模块

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## needSendData

```TypeScript
needSendData?: boolean
```

true代表需要传输数据，false代表不需要传输数据。

**类型：** boolean

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ConnectOptions-needSendData?: boolean--><!--Device-ConnectOptions-needSendData?: boolean-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## parameters

```TypeScript
parameters?: Record<string, string>
```

配置连接所需的额外信息。

**类型：** Record&lt;string, string&gt;

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ConnectOptions-parameters?: Record<string, string>--><!--Device-ConnectOptions-parameters?: Record<string, string>-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## startOptions

```TypeScript
startOptions?: StartOptionParams
```

配置应用启动选项。

**类型：** StartOptionParams

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ConnectOptions-startOptions?: StartOptionParams--><!--Device-ConnectOptions-startOptions?: StartOptionParams-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

