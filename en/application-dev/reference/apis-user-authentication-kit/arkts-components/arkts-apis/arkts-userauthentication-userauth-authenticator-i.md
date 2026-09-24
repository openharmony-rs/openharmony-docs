# Authenticator

```TypeScript
interface Authenticator
```

Provides APIs for managing the **Authenticator** object.

**Since:** 6

**Deprecated since:** 8

**Substitutes:** [AuthInstance](arkts-userauthentication-userauth-authinstance-i.md)

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## Modules to Import

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## execute

```TypeScript
execute(type: AuthType, level: SecureLevel, callback: AsyncCallback<number>): void
```

Starts user authentication. This API uses an asynchronous callback to return the result.

**Since:** 6

**Deprecated since:** 8

**Substitutes:** [start](arkts-userauthentication-userauth-authinstance-i.md#start)

**Required permissions:** ohos.permission.ACCESS_BIOMETRIC

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [AuthType](arkts-userauthentication-userauth-authtype-t.md) | Yes | Authentication type. Currently, only **FACE_ONLY** is supported.<br>**ALL** is reserved and not supported by the current version. |
| level | [SecureLevel](arkts-userauthentication-userauth-securelevel-t.md) | Yes | Security level of the authentication. It can be **S1** (lowest), **S2**, **S3**, or **S4** (highest).<br>Devices capable of 3D facial recognition support S3 and lower-level authentication. <br>Devices capable of 2D facial recognition support S2 and lower-level authentication. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. **number** indicates the [AuthenticationResult](arkts-userauthentication-userauth-authenticationresult-e.md). |

**Examples**

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

<a id="execute-1"></a>

## execute

```TypeScript
execute(type: AuthType, level: SecureLevel): Promise<number>
```

Starts user authentication. This API uses a promise to return the result.

**Since:** 6

**Deprecated since:** 8

**Substitutes:** [start](arkts-userauthentication-userauth-authinstance-i.md#start)

**Required permissions:** ohos.permission.ACCESS_BIOMETRIC

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [AuthType](arkts-userauthentication-userauth-authtype-t.md) | Yes | Authentication type. Currently, only **FACE_ONLY** is supported.<br>**ALL** is reserved and not supported by the current version. |
| level | [SecureLevel](arkts-userauthentication-userauth-securelevel-t.md) | Yes | Security level of the authentication. It can be **S1** (lowest), **S2**, **S3**, or **S4** (highest).<br>Devices capable of 3D facial recognition support S3 and lower-level authentication. <br>Devices capable of 2D facial recognition support S2 and lower-level authentication. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the authentication result, which is a number. For details, see [AuthenticationResult](arkts-userauthentication-userauth-authenticationresult-e.md). |

**Examples**

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
