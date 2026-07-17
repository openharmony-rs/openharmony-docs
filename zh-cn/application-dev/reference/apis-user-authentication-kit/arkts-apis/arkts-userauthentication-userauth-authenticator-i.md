# Authenticator

认证器对象。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [AuthInstance](arkts-userauthentication-userauth-authinstance-i.md)

<!--Device-userAuth-interface Authenticator--><!--Device-userAuth-interface Authenticator-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## 导入模块

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## execute

```TypeScript
execute(type: AuthType, level: SecureLevel, callback: AsyncCallback<number>): void
```

执行用户认证，使用callback方式作为异步方法。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [start](arkts-userauthentication-userauth-authinstance-i.md#start)

**需要权限：** ohos.permission.ACCESS_BIOMETRIC

<!--Device-Authenticator-execute(type: AuthType, level: SecureLevel, callback: AsyncCallback<number>): void--><!--Device-Authenticator-execute(type: AuthType, level: SecureLevel, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [AuthType](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-authtype-e-sys.md) | 是 | 认证类型，当前只支持"FACE_ONLY"。<br/>ALL为预留参数。当前版本暂不支持ALL类型的认证。 |
| level | [SecureLevel](arkts-userauthentication-userauth-securelevel-t.md) | 是 | 安全级别，对应认证的安全级别，有效值为"S1"（最低）、"S2"、"S3"、"S4"（最高）。<br/>具备3D人脸识别能力的设备支持"S3"及以下安全级别的认证。<br/>具备2D人脸识别能力的设备支持"S2"及以下安全级别的认证。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<number> | 是 | 回调函数。number表示认证结果，参见[AuthenticationResult](arkts-userauthentication-userauth-authenticationresult-e.md)。 |

**示例：**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';

let authenticator = userAuth.getAuthenticator();
authenticator.execute('FACE_ONLY', 'S2', (error, code) => {
  if (code === userAuth.ResultCode.SUCCESS) {
    console.info('auth successfully.');
    return;
  }
  console.error(`auth failed, code = ${code}`);
});

```

## execute

```TypeScript
execute(type: AuthType, level: SecureLevel): Promise<number>
```

执行用户认证，使用promise方式作为异步方法。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [start](arkts-userauthentication-userauth-authinstance-i.md#start)

**需要权限：** ohos.permission.ACCESS_BIOMETRIC

<!--Device-Authenticator-execute(type: AuthType, level: SecureLevel): Promise<number>--><!--Device-Authenticator-execute(type: AuthType, level: SecureLevel): Promise<number>-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [AuthType](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-authtype-e-sys.md) | 是 | 认证类型，当前只支持"FACE_ONLY"。<br/>ALL为预留参数。当前版本暂不支持ALL类型的认证。 |
| level | [SecureLevel](arkts-userauthentication-userauth-securelevel-t.md) | 是 | 安全级别，对应认证的安全级别，有效值为"S1"（最低）、"S2"、"S3"、"S4"（最高）。<br/>具备3D人脸识别能力的设备支持"S3"及以下安全级别的认证。<br/>具备2D人脸识别能力的设备支持"S2"及以下安全级别的认证。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | 返回携带一个number的Promise。number 为认证结果，参见[AuthenticationResult](arkts-userauthentication-userauth-authenticationresult-e.md)。 |

**示例：**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';

try {
  let authenticator = userAuth.getAuthenticator();
  authenticator.execute('FACE_ONLY', 'S2').then((code) => {
    console.info('auth successfully.');
  })
} catch (error) {
  console.error(`auth failed, Code: ${error?.code}, message: ${error?.message}`);
}

```

