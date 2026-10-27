# AuthProvider（系统接口）

```TypeScript
interface AuthProvider
```

AuthProvider 接口，由 createAuthProvider 工厂函数创建。

**起始版本：** 26.1.0

<!--Device-securityGuard-interface AuthProvider--><!--Device-securityGuard-interface AuthProvider-End-->

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { securityGuard } from '@kit.SecurityGuardKit';
```

## requestAuthResult

```TypeScript
requestAuthResult(event: AuthEventInfo): Promise<AuthResult>
```

请求事件的阻断结果。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.AUTH_SERVICE_ACCESS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AuthProvider-requestAuthResult(event: AuthEventInfo): Promise<AuthResult>--><!--Device-AuthProvider-requestAuthResult(event: AuthEventInfo): Promise<AuthResult>-End-->

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [AuthEventInfo](arkts-securityguard-securityguard-autheventinfo-i-sys.md) | 是 | 阻断事件信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AuthResult](arkts-securityguard-securityguard-authresult-i-sys.md)&gt; | Promise对象，返回事件阻断结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Non-system application attempted to use a system API. |
| 27000001 | Internal system error. <br>The possible causes are as follows: <br>1. The inter-process IPC call fails. <br>2. The system service process is faulty. |
| 27000004 | Concurrent request count has reached the upper limit. |
