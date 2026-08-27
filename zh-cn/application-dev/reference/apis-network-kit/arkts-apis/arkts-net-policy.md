# @ohos.net.policy(网络策略管理)

本模块提供网络策略管理能力，采用防火墙技术对用户使用数据流量进行控制管理。

> **说明：**
> 
> 本模块首批接口从 API version 10 开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.NetManager.Core

## 导入模块

```TypeScript
import { policy } from '@kit.NetworkKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getNetAccessPolicy(网络策略管理)](arkts-network-policy-getnetaccesspolicy-f.md) | 查询自身应用的联网策略（是否允许使用蜂窝、Wi-Fi网络上网），可在设备中“设置 & gt; 移动网络 & gt; 流量管理 & gt; 应用联网”中查看。使用Promise异步回调。 |
| [showAppNetPolicySettings(网络策略管理)](arkts-network-policy-showappnetpolicysettings-f.md) | 当需要设置当前应用能否使用Wi-Fi/蜂窝联网时，调用该接口可以打开当前应用的联网设置界面，以设置应用的联网权限。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getBackgroundPolicyByUid(网络策略管理)](arkts-network-policy-getbackgroundpolicybyuid-f-sys.md) | 获取指定 uid 是否能访问后台网络，使用 callback 异步回调。 |
| [getBackgroundPolicyByUid(网络策略管理)](arkts-network-policy-getbackgroundpolicybyuid-f-sys.md) | 获取指定 uid 能否访问后台网络，使用 Promise 异步回调。 |
| [getDeviceIdleTrustlist(网络策略管理)](arkts-network-policy-getdeviceidletrustlist-f-sys.md) | 获取休眠模式白名单所包含的 uid，使用 callback 异步回调。 |
| [getDeviceIdleTrustlist(网络策略管理)](arkts-network-policy-getdeviceidletrustlist-f-sys.md) | 获取休眠模式白名单所包含的 uid，使用 Promise 异步回调。 |
| [getNetQuotaPolicies(网络策略管理)](arkts-network-policy-getnetquotapolicies-f-sys.md) | 获取计量网络策略，使用 callback 异步回调。 |
| [getNetQuotaPolicies(网络策略管理)](arkts-network-policy-getnetquotapolicies-f-sys.md) | 获取计量网络策略，使用 Promise 异步回调。 |
| [getNetworkAccessPolicy(网络策略管理)](arkts-network-policy-getnetworkaccesspolicy-f-sys.md) | 获取指定 uid 能否访问网络策略，使用 Promise 异步回调。 |
| [getNetworkAccessPolicy(网络策略管理)](arkts-network-policy-getnetworkaccesspolicy-f-sys.md) | 获取当前用户下所有应用 app 能否访问网络策略信息，使用 Promise 异步回调。 |
| [getPolicyByUid(网络策略管理)](arkts-network-policy-getpolicybyuid-f-sys.md) | 通过应用 uid 获取对应访问网络策略，使用 callback 异步回调。 |
| [getPolicyByUid(网络策略管理)](arkts-network-policy-getpolicybyuid-f-sys.md) | 通过应用 uid 获取对应访问网络策略，使用 Promise 异步回调。 |
| [getPowerSaveTrustlist(网络策略管理)](arkts-network-policy-getpowersavetrustlist-f-sys.md) | 获取省电模式白名单所包含的 uid 数组，使用 callback 异步回调。 |
| [getPowerSaveTrustlist(网络策略管理)](arkts-network-policy-getpowersavetrustlist-f-sys.md) | 获取休眠模式白名单所包含的 uid 数组，使用 Promise 异步回调。 |
| [getUidsByPolicy(网络策略管理)](arkts-network-policy-getuidsbypolicy-f-sys.md) | 通过策略获取跟策略匹配的所有 uid，使用 callback 异步回调。 |
| [getUidsByPolicy(网络策略管理)](arkts-network-policy-getuidsbypolicy-f-sys.md) | 通过策略获取跟策略匹配的所有 uid，使用 Promise 异步回调。 |
| [isBackgroundAllowed(网络策略管理)](arkts-network-policy-isbackgroundallowed-f-sys.md) | 获取当前应用是否允许后台访问网络，使用 callback 异步回调。 |
| [isBackgroundAllowed(网络策略管理)](arkts-network-policy-isbackgroundallowed-f-sys.md) | 获取当前应用是否允许后台访问网络，使用 Promise 异步回调。 |
| [isUidNetAllowed(网络策略管理)](arkts-network-policy-isuidnetallowed-f-sys.md) | 判断对应 uid 能否访问计量或非计量网络，使用 callback 异步回调。 |
| [isUidNetAllowed(网络策略管理)](arkts-network-policy-isuidnetallowed-f-sys.md) | 判断对应 uid 能否访问计量或非计量网络，使用 Promise 异步回调。 |
| [isUidNetAllowed(网络策略管理)](arkts-network-policy-isuidnetallowed-f-sys.md) | 获取对应 uid 能否访问指定的 iface 的网络，使用 callback 异步回调。 |
| [isUidNetAllowed(网络策略管理)](arkts-network-policy-isuidnetallowed-f-sys.md) | 获取对应 uid 能否访问指定的 iface 的网络，使用 Promise 异步回调。 |
| off(网络策略管理) | 注销 policy 发生改变时的回调，使用 callback 异步回调。 |
| off(网络策略管理) | 注销 rule 发生改变时的回调，使用 callback 异步回调。 |
| off(网络策略管理) | 注销计量 iface 发生改变时的回调，使用 callback 异步回调。 |
| off(网络策略管理) | 注销计量网络策略发生改变时的回调，使用 callback 异步回调。 |
| off(网络策略管理) | 注销后台网络策略发生改变时的回调，使用 callback 异步回调。 |
| on(网络策略管理) | 注册 policy 发生改变时的回调，使用 callback 异步回调。 |
| on(网络策略管理) | 注册 rule 发生改变时的回调，使用 callback 异步回调。 |
| on(网络策略管理) | 注册计量 iface 发生改变时的回调，使用 callback 异步回调。 |
| on(网络策略管理) | 注册计量网络策略发生改变时的回调，使用 callback 异步回调。 |
| on(网络策略管理) | 注册后台网络策略发生改变时的回调，使用 callback 异步回调。 |
| [resetPolicies(网络策略管理)](arkts-network-policy-resetpolicies-f-sys.md) | 重置对应 sim 卡 id 的蜂窝网络、后台网络策略、防火墙策略、应用对应的策略，使用 callback 异步回调。 |
| [resetPolicies(网络策略管理)](arkts-network-policy-resetpolicies-f-sys.md) | 重置对应 sim 卡 id 的蜂窝网络、后台网络策略、防火墙策略、应用对应的策略，使用 Promise 异步回调。 |
| [restoreAllPolicies(网络策略管理)](arkts-network-policy-restoreallpolicies-f-sys.md) | 根据指定的SIM卡识别码，恢复所有网络管理相关的策略配置，如UID策略、配额策略、防火墙规则等。 |
| [setBackgroundAllowed(网络策略管理)](arkts-network-policy-setbackgroundallowed-f-sys.md) | 设置是否允许后台应用访问网络，使用 callback 异步回调。 |
| [setBackgroundAllowed(网络策略管理)](arkts-network-policy-setbackgroundallowed-f-sys.md) | 设置是否允许后台应用访问网络，使用 Promise 异步回调。 |
| [setDeviceIdleTrustlist(网络策略管理)](arkts-network-policy-setdeviceidletrustlist-f-sys.md) | 设置多个 uid 是否在休眠防火墙的白名单，使用 callback 异步回调。 |
| [setDeviceIdleTrustlist(网络策略管理)](arkts-network-policy-setdeviceidletrustlist-f-sys.md) | 设置多个 uid 是否在休眠防火墙的白名单，使用 Promise 异步回调。 |
| [setNetQuotaPolicies(网络策略管理)](arkts-network-policy-setnetquotapolicies-f-sys.md) | 设置计量网络策略，使用 callback 异步回调。 |
| [setNetQuotaPolicies(网络策略管理)](arkts-network-policy-setnetquotapolicies-f-sys.md) | 设置计量网络策略，使用 Promise 异步回调。 |
| [setNetworkAccessPolicy(网络策略管理)](arkts-network-policy-setnetworkaccesspolicy-f-sys.md) | 设置指定 uid 应用能否能访问网络的策略，使用 Promise 异步回调。 |
| [setPolicyByUid(网络策略管理)](arkts-network-policy-setpolicybyuid-f-sys.md) | 设置对应 uid 应用是否能够访问计量网络的策略，使用 callback 异步回调。 |
| [setPolicyByUid(网络策略管理)](arkts-network-policy-setpolicybyuid-f-sys.md) | 设置对应 uid 应用是否能够访问计量网络的策略，使用 Promise 异步回调。 |
| [setPowerSaveTrustlist(网络策略管理)](arkts-network-policy-setpowersavetrustlist-f-sys.md) | 设置指定 uid 应用是否在省电防火墙的白名单，使用 callback 异步回调。 |
| [setPowerSaveTrustlist(网络策略管理)](arkts-network-policy-setpowersavetrustlist-f-sys.md) | 设置指定 uid 应用是否在省电防火墙的白名单，使用 Promise 异步回调。 |
| [updateRemindPolicy(网络策略管理)](arkts-network-policy-updateremindpolicy-f-sys.md) | 更新提醒策略，使用 callback 异步回调。 |
| [updateRemindPolicy(网络策略管理)](arkts-network-policy-updateremindpolicy-f-sys.md) | 更新提醒策略，使用 Promise 异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [NetAccessPolicy(网络策略管理)](arkts-network-policy-netaccesspolicy-i.md) | 应用联网策略信息。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [NetQuotaPolicy(网络策略管理)](arkts-network-policy-netquotapolicy-i-sys.md) | 计量网络策略。 |
| [NetUidPolicyInfo(网络策略管理)](arkts-network-policy-netuidpolicyinfo-i-sys.md) | 注册网络UID策略变化的回调函数。 |
| [NetUidRuleInfo(网络策略管理)](arkts-network-policy-netuidruleinfo-i-sys.md) | 生成网络唯一标识。 |
| [NetworkAccessPolicy(网络策略管理)](arkts-network-policy-networkaccesspolicy-i-sys.md) | 应用对应的连接网络的策略。 |
| [NetworkMatchRule(网络策略管理)](arkts-network-policy-networkmatchrule-i-sys.md) | 网络标识，用来确定设置哪一个网络 |
| [QuotaPolicy(网络策略管理)](arkts-network-policy-quotapolicy-i-sys.md) | 计量网络策略 |
| [UidNetworkAccessPolicy(网络策略管理)](arkts-network-policy-uidnetworkaccesspolicy-i-sys.md) | 应用标识以及对应应用连接网络的策略。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [LimitAction(网络策略管理)](arkts-network-policy-limitaction-e-sys.md) | 限制动作。 |
| [NetBackgroundPolicy(网络策略管理)](arkts-network-policy-netbackgroundpolicy-e-sys.md) | 后台网络策略。 |
| [NetUidPolicy(网络策略管理)](arkts-network-policy-netuidpolicy-e-sys.md) | 应用对应的网络策略。 |
| [NetUidRule(网络策略管理)](arkts-network-policy-netuidrule-e-sys.md) | 计量网络规则。 |
| [RemindType(网络策略管理)](arkts-network-policy-remindtype-e-sys.md) | 提醒类型。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [NetBearType(网络策略管理)](arkts-network-policy-netbeartype-t.md) | 网络类型。 |
