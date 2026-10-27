# off（系统接口）

## 导入模块

```TypeScript
import { securityGuard } from '@kit.SecurityGuardKit';
```

## off('securityEventOccur')

```TypeScript
function off(type: 'securityEventOccur', securityEventInfo: SecurityEventInfo, callback?: Callback<SecurityEvent>): void
```

Unsubscribe the security event.

**起始版本：** 12

**需要权限：** ohos.permission.QUERY_SECURITY_EVENT

<!--Device-securityGuard-function off(type: 'securityEventOccur', securityEventInfo: SecurityEventInfo, callback?: Callback<SecurityEvent>): void--><!--Device-securityGuard-function off(type: 'securityEventOccur', securityEventInfo: SecurityEventInfo, callback?: Callback<SecurityEvent>): void-End-->

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'securityEventOccur' | 是 |  |
| securityEventInfo | [SecurityEventInfo](arkts-securityguard-securityguard-securityeventinfo-i-sys.md) | 是 | Indicates the subscribed event information. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SecurityEvent](arkts-securityguard-securityguard-securityevent-i-sys.md)&gt; | 否 | Indicates the listener when the security event occurs. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | check permission fail. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | non-system application uses the system API. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | invalid parameters. Possible causes:     1. Mandatory parameters are left unspecified.     2. Incorrect parameter types.     3. Parameter verification failed. |
