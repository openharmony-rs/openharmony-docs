# NetworkMatchRule（系统接口）

网络标识，用来确定设置哪一个网络

**起始版本：** 10

<!--Device-policy-export interface NetworkMatchRule--><!--Device-policy-export interface NetworkMatchRule-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { policy } from '@kit.NetworkKit';
```

## identity

```TypeScript
identity: string
```

计量蜂窝网络中配合simId联合使用。 以太网和wifi网络单独使用。 用于标记类型。

**类型：** string

**起始版本：** 10

<!--Device-NetworkMatchRule-identity: string--><!--Device-NetworkMatchRule-identity: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

## netType

```TypeScript
netType: NetBearType
```

网络类型。

**类型：** NetBearType

**起始版本：** 10

<!--Device-NetworkMatchRule-netType: NetBearType--><!--Device-NetworkMatchRule-netType: NetBearType-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

## simId

```TypeScript
simId: string
```

计量蜂窝网络的SIM卡的标识值。 以太网和wifi网络不会用到。

**类型：** string

**起始版本：** 10

<!--Device-NetworkMatchRule-simId: string--><!--Device-NetworkMatchRule-simId: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

