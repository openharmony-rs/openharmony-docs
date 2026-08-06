# getAuthenticator

## getAuthenticator

```TypeScript
function getAuthenticator(): Authenticator
```

获取Authenticator对象，用于执行用户身份认证。

**起始版本：** 6

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为6。

**废弃版本：** 8

**替代接口：** [userAuth.getAuthInstance](arkts-userauthentication-userauth-getauthinstance-f.md#getauthinstance)

<!--Device-userAuth-function getAuthenticator(): Authenticator--><!--Device-userAuth-function getAuthenticator(): Authenticator-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 认证器对象。 |

**示例：**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';

let authenticator = userAuth.getAuthenticator();
```

