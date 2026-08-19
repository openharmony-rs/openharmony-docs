# NetUidPolicyInfo（系统接口）

注册网络UID策略变化的回调函数。

**起始版本：** 11

<!--Device-policy-export interface NetUidPolicyInfo--><!--Device-policy-export interface NetUidPolicyInfo-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { policy } from '@kit.NetworkKit';
```

## policy

```TypeScript
policy: NetUidPolicy
```

UID指定了在后台模式下网络访问的策略。

**类型：** [NetUidPolicy](arkts-network-policy-netuidpolicy-e-sys.md)

**起始版本：** 11

<!--Device-NetUidPolicyInfo-policy: NetUidPolicy--><!--Device-NetUidPolicyInfo-policy: NetUidPolicy-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

## uid

```TypeScript
uid: int
```

流量警告的阈值，默认：DATA_USAGE_UNKNOWN。

**类型：** int

**起始版本：** 11

<!--Device-NetUidPolicyInfo-uid: int--><!--Device-NetUidPolicyInfo-uid: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

