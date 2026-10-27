# createAuthProvider（系统接口）

## 导入模块

```TypeScript
import { securityGuard } from '@kit.SecurityGuardKit';
```

## createAuthProvider

```TypeScript
function createAuthProvider(callback: AuthProviderCallback, serviceId: string): AuthProvider
```

创建 AuthProvider 会话。同一进程最多 1 个 Provider 实例，全局最多 16 个。成功后 onClientStatusChanged 回调可收到已有客户端的信息。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.AUTH_SERVICE_ACCESS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-securityGuard-function createAuthProvider(callback: AuthProviderCallback, serviceId: string): AuthProvider--><!--Device-securityGuard-function createAuthProvider(callback: AuthProviderCallback, serviceId: string): AuthProvider-End-->

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

**参见：** [destroyAuthProvider](arkts-securityguard-securityguard-destroyauthprovider-f-sys.md) Destroys an **AuthProvider** session.

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AuthProviderCallback](arkts-securityguard-securityguard-authprovidercallback-i-sys.md) | 是 | Provider 回调接口。 |
| serviceId | string | 是 | 服务标识。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AuthProvider](arkts-securityguard-securityguard-authprovider-i-sys.md) | AuthProvider 实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Non-system application attempted to use a system API. |
| 27000001 | Internal system error. <br>The possible causes are as follows: <br>1. The inter-process IPC call fails. <br>2. The system service process is faulty. |
| 27000002 | Provider count of the current process has reached the upper limit. |
| 27000003 | Global provider count has reached the upper limit. |
