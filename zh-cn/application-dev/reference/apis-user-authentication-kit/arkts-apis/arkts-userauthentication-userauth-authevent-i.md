# AuthEvent

认证接口的异步回调对象。

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [IAuthCallback](arkts-userauthentication-userauth-iauthcallback-i.md)

<!--Device-userAuth-interface AuthEvent--><!--Device-userAuth-interface AuthEvent-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## 导入模块

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## callback

```TypeScript
callback(result: EventInfo): void
```

通过该回调获取认证结果信息或认证过程中的提示信息。

**起始版本：** 9

**废弃版本：** 11

**替代接口：** onResult(result:

<!--Device-AuthEvent-callback(result: EventInfo): void--><!--Device-AuthEvent-callback(result: EventInfo): void-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | [EventInfo](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-update-eventinfo-i-sys.md) | 是 | 返回的认证结果信息或提示信息。 |

**示例：**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';

let challenge = new Uint8Array([1, 2, 3, 4, 5, 6, 7, 8]);
let authType = userAuth.UserAuthType.FACE;
let authTrustLevel = userAuth.AuthTrustLevel.ATL1;
// 通过callback获取认证结果。
try {
  let auth = userAuth.getAuthInstance(challenge, authType, authTrustLevel);
  auth.on('result', {
    callback: (result: userAuth.AuthResultInfo) => {
      console.info(`result: ${result.result}`);
    }
  } as userAuth.AuthEvent);
  auth.start();
  console.info('auth start successfully.');
} catch (error) {
  console.error(`auth failed. Code: ${error?.code}, message: ${error?.message}`);
  // do error.
}
// 通过callback获取认证过程中的提示信息。
try {
  let auth = userAuth.getAuthInstance(challenge, authType, authTrustLevel);
  auth.on('tip', {
    callback : (result : userAuth.TipInfo) => {
      switch (result.tip) {
        case userAuth.FaceTips.FACE_AUTH_TIP_TOO_BRIGHT:
          // do something;
          break;
        case userAuth.FaceTips.FACE_AUTH_TIP_TOO_DARK:
          // do something;
          break;
        default:
          // do others.
      }
    }
  } as userAuth.AuthEvent);
  auth.start();
  console.info('auth start successfully.');
} catch (error) {
  console.error(`auth failed. Code: ${error?.code}, message: ${error?.message}`);
  // do error.
}

```

