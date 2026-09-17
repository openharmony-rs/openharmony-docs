# PeerInfo

应用协同信息。

**起始版本：** 18

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## 导入模块

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## abilityName

```TypeScript
abilityName: string
```

对端应用的组件名，用于标识要连接的UIAbility组件。需与对端应用的abilityName保持一致。

**类型：** string

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## bundleName

```TypeScript
bundleName: string
```

对端应用的包名，用于唯一标识要连接的应用。需与对端应用的bundleName保持一致。

**类型：** string

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## deviceId

```TypeScript
deviceId: string
```

对端设备的网络ID，用于标识要连接的远程设备。可通过分布式设备管理接口getAvailableDeviceListSync获取。

**类型：** string

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## moduleName

```TypeScript
moduleName: string
```

对端应用的模块名，用于标识要连接的应用模块。通常为'entry'或其他自定义模块名。

**类型：** string

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## serviceName

```TypeScript
serviceName?: string
```

应用设置的服务名称。若设置此值，需与createAbilityConnectionSession接口的serviceName参数保持一致。不设置此值时，使用默认服务名称。

**类型：** string

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration
