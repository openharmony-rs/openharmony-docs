# NetUidRuleInfo（系统接口）

生成网络唯一标识。

**起始版本：** 11

<!--Device-policy-export interface NetUidRuleInfo--><!--Device-policy-export interface NetUidRuleInfo-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { policy } from '@kit.NetworkKit';
```

## rule

```TypeScript
rule: NetUidRule
```

规定一个UID访问计量网络还是非计量网络。

**类型：** [NetUidRule](arkts-network-policy-netuidrule-e-sys.md)

**起始版本：** 11

<!--Device-NetUidRuleInfo-rule: NetUidRule--><!--Device-NetUidRuleInfo-rule: NetUidRule-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

## uid

```TypeScript
uid: int
```

流量警告的阈值，默认：DATA_USAGE_UNKNOWN。

**类型：** int

**起始版本：** 11

<!--Device-NetUidRuleInfo-uid: int--><!--Device-NetUidRuleInfo-uid: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

