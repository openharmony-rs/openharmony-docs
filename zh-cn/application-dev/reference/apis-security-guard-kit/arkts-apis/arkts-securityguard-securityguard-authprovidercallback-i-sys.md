# AuthProviderCallback（系统接口）

```TypeScript
interface AuthProviderCallback
```

Provider 回调接口，在 createAuthProvider 时传入。

**起始版本：** 26.1.0

<!--Device-securityGuard-interface AuthProviderCallback--><!--Device-securityGuard-interface AuthProviderCallback-End-->

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { securityGuard } from '@kit.SecurityGuardKit';
```

## onClientStatusChanged

```TypeScript
onClientStatusChanged: (clientInfos: AuthClientInfo[]) => void
```

关联的客户端会话状态变更时回调。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AuthProviderCallback-onClientStatusChanged: (clientInfos: AuthClientInfo[]) => void--><!--Device-AuthProviderCallback-onClientStatusChanged: (clientInfos: AuthClientInfo[]) => void-End-->

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| clientInfos | [AuthClientInfo](arkts-securityguard-securityguard-authclientinfo-i-sys.md)[] | 是 | 全部客户端会话信息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Non-system application attempted to use a system API. |
