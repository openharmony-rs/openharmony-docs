# UserAuthType

表示身份认证的凭据类型枚举。该枚举定义了系统支持的认证类型，包括锁屏密码认证（PIN）、生物特征认证（人脸、指纹）等。应用在发起认证时需指定认证类型列表，用户可选择其中任意一种完成认证。不同认证类型具有不同的安全强度和用户体验特 点，应用应根据业务场景选择合适的认证类型。

**起始版本：** 8

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## PRIVATE_PIN

```TypeScript
PRIVATE_PIN = 16
```

隐私密码。一种特殊的PIN认证类型，一般用于解锁后的用户二次访问控制（即在设备解锁后，用户访问特定应用或内容前需再次进行身份验证）。例如用户可以选择使用隐私密码保护应用锁（应用锁是一种对应用启动进行二次验证的功能，可防止他人打 开用户的应用），从而阻止知道锁屏密码的家人访问自己的某些应用。

**起始版本：** 14

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**系统接口：** 此接口为系统接口。

**示例**

发起用户认证，采用认证可信等级≥ATL3的隐私密码认证，获取认证结果。

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { userAuth } from '@kit.UserAuthenticationKit';

try {
  const rand = cryptoFramework.createRandom();
  const len: number = 16;
  const randData: Uint8Array = rand?.generateRandomSync(len)?.data;
  const authParam: userAuth.AuthParam = {
    challenge: randData,
    authType: [userAuth.UserAuthType.PRIVATE_PIN],
    authTrustLevel: userAuth.AuthTrustLevel.ATL3,
  };
  const widgetParam: userAuth.WidgetParam = {
    title: '请输入密码',
  };

  const userAuthInstance = userAuth.getUserAuthInstance(authParam, widgetParam);
  console.info('get userAuth instance successfully.');
  // 需要调用UserAuthInstance的start()接口，启动认证后，才能通过onResult获取到认证结果。
  userAuthInstance.on('result', {
    onResult: (result) => {
      console.info(`userAuthInstance callback result = ${result.result}`);
    }
  });
  console.info('auth on successfully.');
  userAuthInstance.start();
  console.info('auth start successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`Failed to auth. Code: ${err?.code}, message: ${err?.message}`);
}
```
