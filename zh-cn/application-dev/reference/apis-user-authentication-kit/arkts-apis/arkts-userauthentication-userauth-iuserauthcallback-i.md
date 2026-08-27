# IUserAuthCallback

返回认证结果的回调对象。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [AuthEvent](arkts-userauthentication-userauth-authevent-i.md)

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## 导入模块

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## onAcquireInfo

```TypeScript
onAcquireInfo?: (module: number, acquire: number, extraInfo: any) => void
```

回调函数，返回认证过程中的提示信息，非必须实现。  
- **module**: 发送提示信息的模块标识。  
- **acquire**: 认证执过程中的提示信息。  
- **extraInfo**: 预留字段。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [callback](arkts-userauthentication-userauth-authevent-i.md#callback)

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| module | number | 是 |  |
| acquire | number | 是 |  |
| extraInfo | any | 是 |  |

**示例**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';

let auth = new userAuth.UserAuth();
let challenge = new Uint8Array([]);
auth.auth(challenge, userAuth.UserAuthType.FACE, userAuth.AuthTrustLevel.ATL1, {
  onResult: (result, extraInfo) => {
    try {
      console.info(`auth onResult result = ${result}`);
      if (result == userAuth.ResultCode.SUCCESS) {
        // 此处添加认证成功逻辑。
      }  else {
        // 此处添加认证失败逻辑。
      }
    } catch (error) {
      console.error(`Failed to auth onResult. Code: ${error?.code}, message: ${error?.message}`);
    }
  },
  onAcquireInfo: (module, acquire, extraInfo: userAuth.AuthResult) => {
    try {
      console.info('auth onAcquireInfo successfully.');
    } catch (error) {
      console.error(`Failed to auth onAcquireInfo. Code: ${error?.code}, message: ${error?.message}`);
    }
  }
});
```

## onResult

```TypeScript
onResult: (result: number, extraInfo: AuthResult) => void
```

回调函数，返回认证结果。  
- **result**: 认证结果，参见[ResultCode](arkts-userauthentication-userauth-resultcode-e.md)。  
- **extraInfo**: 扩展信息，不同情况下的具体信息。如果身份验证通过，则在extraInfo中返回用户认证令牌；如果身份验证失败，则在extraInfo中返回剩余的用户认证次数；如果身份验证执行器被锁定，则在  
extraInfo中返回冻结时间，类型为[AuthResult](arkts-userauthentication-userauth-authresult-i.md)。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [callback](arkts-userauthentication-userauth-authevent-i.md#callback)

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | number | 是 |  |
| extraInfo | AuthResult | 是 |  |

**示例**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';

let auth = new userAuth.UserAuth();
let challenge = new Uint8Array([]);
auth.auth(challenge, userAuth.UserAuthType.FACE, userAuth.AuthTrustLevel.ATL1, {
  onResult: (result, extraInfo) => {
    try {
      console.info(`auth onResult result = ${result}`);
      if (result == userAuth.ResultCode.SUCCESS) {
        // 此处添加认证成功逻辑。
      }  else {
        // 此处添加认证失败逻辑。
      }
    } catch (error) {
      console.error(`Failed to auth onResult. Code: ${error?.code}, message: ${error?.message}`);
    }
  }
});
```
