# destroyAuthProvider（系统接口）

## 导入模块

```TypeScript
import { securityGuard } from '@kit.SecurityGuardKit';
```

## destroyAuthProvider

```TypeScript
function destroyAuthProvider(provider: AuthProvider): void
```

销毁 AuthProvider 会话。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.AUTH_SERVICE_ACCESS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-securityGuard-function destroyAuthProvider(provider: AuthProvider): void--><!--Device-securityGuard-function destroyAuthProvider(provider: AuthProvider): void-End-->

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

**参见：** [createAuthProvider](arkts-securityguard-securityguard-createauthprovider-f-sys.md) 创建 AuthProvider 会话。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| provider | [AuthProvider](arkts-securityguard-securityguard-authprovider-i-sys.md) | 是 | 要销毁的 AuthProvider 实例，销毁后不可再用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Non-system application attempted to use a system API. |
| 27000001 | Internal system error. <br>The possible causes are as follows: <br>1. The inter-process IPC call fails. <br>2. The system service process is faulty. |
