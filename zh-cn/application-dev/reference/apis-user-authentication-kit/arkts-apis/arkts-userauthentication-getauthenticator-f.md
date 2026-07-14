# getAuthenticator

## getAuthenticator

```TypeScript
function getAuthenticator(): Authenticator
```

获取Authenticator对象，用于执行用户身份认证。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [getAuthInstance](arkts-userauthentication-getauthinstance-f.md#getauthinstance-1)

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Authenticator | 认证器对象。 |

**示例：**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';

let authenticator = userAuth.getAuthenticator();

```

