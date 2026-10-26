# @ohos.security.securityGuard(This module provides the capabilities to security guard.)

Provides security event management and security model management. Based on event information, you will be able to analyze the running status of devices.

**起始版本：** 12

<!--Device-unnamed-declare namespace securityGuard--><!--Device-unnamed-declare namespace securityGuard-End-->

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { securityGuard } from '@kit.SecurityGuardKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [createAuthProvider](arkts-securityguard-securityguard-createauthprovider-f-sys.md#createauthprovider-1) | 创建 AuthProvider 会话。同一进程最多 1 个 Provider 实例，全局最多 16 个。成功后 onClientStatusChanged 回调可收到已有客户端的信息。 |
| [destroyAuthProvider](arkts-securityguard-securityguard-destroyauthprovider-f-sys.md#destroyauthprovider-1) | 销毁 AuthProvider 会话。 |
| [getModelResult](arkts-securityguard-securityguard-getmodelresult-f-sys.md#getmodelresult-1) | Request security model result from security guard. |
| [off('securityEventOccur')](arkts-securityguard-securityguard-off-f-sys.md#offsecurityeventoccur) | Unsubscribe the security event. |
| [on('securityEventOccur')](arkts-securityguard-securityguard-on-f-sys.md#onsecurityeventoccur) | Subscribe the security event. |
| [querySecurityEvent](arkts-securityguard-securityguard-querysecurityevent-f-sys.md#querysecurityevent-1) | Query security event information from security guard. |
| [reportSecurityEvent](arkts-securityguard-securityguard-reportsecurityevent-f-sys.md#reportsecurityevent-1) | Report security information to the security guard. |
| [startSecurityEventCollector](arkts-securityguard-securityguard-startsecurityeventcollector-f-sys.md#startsecurityeventcollector-1) | start the collector to collect data |
| [stopSecurityEventCollector](arkts-securityguard-securityguard-stopsecurityeventcollector-f-sys.md#stopsecurityeventcollector-1) | stop the collector. |
| [updatePolicyFile](arkts-securityguard-securityguard-updatepolicyfile-f-sys.md#updatepolicyfile-1) | Update the policy file. |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AuthClientInfo](arkts-securityguard-securityguard-authclientinfo-i-sys.md) | 客户端会话信息。 |
| [AuthClientStatus](arkts-securityguard-securityguard-authclientstatus-i-sys.md) | 客户端会话状态。 |
| [AuthEventInfo](arkts-securityguard-securityguard-autheventinfo-i-sys.md) | 阻断事件信息。 |
| [AuthProvider](arkts-securityguard-securityguard-authprovider-i-sys.md) | AuthProvider 接口，由 createAuthProvider 工厂函数创建。 |
| [AuthProviderCallback](arkts-securityguard-securityguard-authprovidercallback-i-sys.md) | Provider 回调接口，在 createAuthProvider 时传入。 |
| [AuthResult](arkts-securityguard-securityguard-authresult-i-sys.md) | 所有客户端阻断结果。 |
| [ClientAuthResult](arkts-securityguard-securityguard-clientauthresult-i-sys.md) | 单个客户端阻断结果。 |
| [CollectorRule](arkts-securityguard-securityguard-collectorrule-i-sys.md) | Provides the conditions of Collector. |
| [ModelResult](arkts-securityguard-securityguard-modelresult-i-sys.md) | Provides the ModelResult type. |
| [ModelRule](arkts-securityguard-securityguard-modelrule-i-sys.md) | Provides the ModelRule type. |
| [PolicyFile](arkts-securityguard-securityguard-policyfile-i-sys.md) | Provides policy file information. |
| [Querier](arkts-securityguard-securityguard-querier-i-sys.md) | Definition callback of receiving the query data. |
| [SecurityEvent](arkts-securityguard-securityguard-securityevent-i-sys.md) | Provides the SecurityEvent type, including the event id, version info, report content. |
| [SecurityEventInfo](arkts-securityguard-securityguard-securityeventinfo-i-sys.md) | Provides the conditions of on/off. |
| [SecurityEventRule](arkts-securityguard-securityguard-securityeventrule-i-sys.md) | Provides the conditions of querySecurityEvent. |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AuthStrategy](arkts-securityguard-securityguard-authstrategy-e-sys.md) | 阻断策略枚举。 |
<!--DelEnd-->
