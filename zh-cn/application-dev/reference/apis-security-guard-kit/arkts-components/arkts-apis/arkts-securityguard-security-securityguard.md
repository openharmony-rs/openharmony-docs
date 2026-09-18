# @ohos.security.securityGuard(本模块提供设备风险管理平台能力。)

提供安全事件存取、风险分析等功能。基于事件信息，您将能够分析设备的运行状态。

@namespace securityGuard

**起始版本：** 12

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
| [getModelResult](arkts-securityguard-securityguard-getmodelresult-f-sys.md) | 请求安全模型检测结果。 |
| [off](arkts-securityguard-securityguard-off-f-sys.md#offsecurityeventoccur) | 解订阅安全事件。 |
| [on](arkts-securityguard-securityguard-on-f-sys.md#onsecurityeventoccur) | 订阅安全事件。 |
| [querySecurityEvent](arkts-securityguard-securityguard-querysecurityevent-f-sys.md) | 用于获取安全事件信息。 |
| [reportSecurityEvent](arkts-securityguard-securityguard-reportsecurityevent-f-sys.md) | 安全事件上报接口。 |
| [startSecurityEventCollector](arkts-securityguard-securityguard-startsecurityeventcollector-f-sys.md) | 开始采集事件。 |
| [stopSecurityEventCollector](arkts-securityguard-securityguard-stopsecurityeventcollector-f-sys.md) | 停止采集事件。 |
| [updatePolicyFile](arkts-securityguard-securityguard-updatepolicyfile-f-sys.md) | 更新配置文件。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [CollectorRule](arkts-securityguard-securityguard-collectorrule-i-sys.md) | 安全事件采集规则。 |
| [ModelResult](arkts-securityguard-securityguard-modelresult-i-sys.md) | 安全模型结果。 |
| [ModelRule](arkts-securityguard-securityguard-modelrule-i-sys.md) | 安全模型规则。 |
| [PolicyFile](arkts-securityguard-securityguard-policyfile-i-sys.md) | 配置文件信息。 |
| [Querier](arkts-securityguard-securityguard-querier-i-sys.md) | 用于接收安全数据的回调函数。 |
| [SecurityEvent](arkts-securityguard-securityguard-securityevent-i-sys.md) | 提供SecurityEvent类型，包括事件ID、版本信息和上报内容。 |
| [SecurityEventInfo](arkts-securityguard-securityguard-securityeventinfo-i-sys.md) | 调用订阅接口使用的事件信息。 |
| [SecurityEventRule](arkts-securityguard-securityguard-securityeventrule-i-sys.md) | 用户获取安全数据的规则。 |
<!--DelEnd-->
