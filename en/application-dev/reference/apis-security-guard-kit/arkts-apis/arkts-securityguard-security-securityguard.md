# @ohos.security.securityGuard(This module provides the capabilities to security guard.)

Provides security event management and security model management. Based on event information, you will be able to analyze the running status of devices.

@namespace securityGuard

**Since:** 12

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { securityGuard } from '@kit.SecurityGuardKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getModelResult](arkts-securityguard-securityguard-getmodelresult-f-sys.md) | Request security model result from security guard. |
| [off](arkts-securityguard-securityguard-off-f-sys.md#offsecurityeventoccur) | Unsubscribe the security event. |
| [on](arkts-securityguard-securityguard-on-f-sys.md#onsecurityeventoccur) | Subscribe the security event. |
| [querySecurityEvent](arkts-securityguard-securityguard-querysecurityevent-f-sys.md) | Query security event information from security guard. |
| [reportSecurityEvent](arkts-securityguard-securityguard-reportsecurityevent-f-sys.md) | Report security information to the security guard. |
| [startSecurityEventCollector](arkts-securityguard-securityguard-startsecurityeventcollector-f-sys.md) | start the collector to collect data |
| [stopSecurityEventCollector](arkts-securityguard-securityguard-stopsecurityeventcollector-f-sys.md) | stop the collector. |
| [updatePolicyFile](arkts-securityguard-securityguard-updatepolicyfile-f-sys.md) | Update the policy file. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [CollectorRule](arkts-securityguard-securityguard-collectorrule-i-sys.md) | Provides the conditions of Collector. |
| [ModelResult](arkts-securityguard-securityguard-modelresult-i-sys.md) | Provides the ModelResult type. |
| [ModelRule](arkts-securityguard-securityguard-modelrule-i-sys.md) | Provides the ModelRule type. |
| [PolicyFile](arkts-securityguard-securityguard-policyfile-i-sys.md) | Provides policy file information. |
| [Querier](arkts-securityguard-securityguard-querier-i-sys.md) | Definition callback of receiving the query data. |
| [SecurityEvent](arkts-securityguard-securityguard-securityevent-i-sys.md) | Provides the SecurityEvent type, including the event id, version info, report content. |
| [SecurityEventInfo](arkts-securityguard-securityguard-securityeventinfo-i-sys.md) | Provides the conditions of on/off. |
| [SecurityEventRule](arkts-securityguard-securityguard-securityeventrule-i-sys.md) | Provides the conditions of querySecurityEvent. |
<!--DelEnd-->
