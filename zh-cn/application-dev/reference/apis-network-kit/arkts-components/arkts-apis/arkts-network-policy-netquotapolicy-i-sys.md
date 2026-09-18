# NetQuotaPolicy（系统接口）

计量网络策略。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { policy } from '@kit.NetworkKit';
```

## networkMatchRule

```TypeScript
networkMatchRule: NetworkMatchRule
```

网络标识，用来确定设置哪一个网络。

**类型：** [NetworkMatchRule](arkts-network-policy-networkmatchrule-i-sys.md)

**起始版本：** 10

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

## quotaPolicy

```TypeScript
quotaPolicy: QuotaPolicy
```

具体的计量网络策略。

**类型：** [QuotaPolicy](arkts-network-policy-quotapolicy-i-sys.md)

**起始版本：** 10

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。
