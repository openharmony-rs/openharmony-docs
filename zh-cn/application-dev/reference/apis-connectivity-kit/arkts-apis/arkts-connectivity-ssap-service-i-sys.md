# Service

表示星闪服务。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { ssap } from '@kit.ConnectivityKit';
```

## events

```TypeScript
events?: Event[]
```

表示服务的事件列表。若未配置该字段，则服务不提供任何事件。

**类型：** Event[]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

## methods

```TypeScript
methods?: Method[]
```

表示服务的方法列表。若未配置该字段，则服务不提供任何方法。

**类型：** [Method](arkts-connectivity-ssap-method-i-sys.md)[]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。
