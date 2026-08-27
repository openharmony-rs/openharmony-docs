# reportSecurityEvent（系统接口）

## 导入模块

```TypeScript
import { securityGuard } from '@kit.SecurityGuardKit';
```

## reportSecurityEvent

```TypeScript
function reportSecurityEvent(securityEvent: SecurityEvent): void
```

安全事件上报接口。

**起始版本：** 12

**需要权限：** ohos.permission.REPORT_SECURITY_EVENT

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| securityEvent | [SecurityEvent](arkts-securityguard-securityguard-securityevent-i-sys.md) | 是 | 表示要上报的事件信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | check permission fail. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | non-system application uses the system API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
