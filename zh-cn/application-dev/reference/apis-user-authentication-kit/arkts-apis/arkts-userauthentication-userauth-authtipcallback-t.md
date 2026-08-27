# AuthTipCallback

```TypeScript
type AuthTipCallback = (authTipInfo: AuthTipInfo) => void
```

回调函数，返回认证中间状态。该回调用于在认证过程中获取各种中间状态信息，包括每次认证不通过、冻结状态、界面加载和释放等。通过订阅这些中间状态，应用可以在认证过程中提供更精细的用户交互和状态管理。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| authTipInfo | [AuthTipInfo](arkts-userauthentication-userauth-authtipinfo-i.md) | 是 | 认证中间状态。包含认证类型(tipType)和状态码(tipCode)。应用应根据tipCode执行相应处理：  - COMPARE_FAILURE(1)：提示用户重新尝试。  - TIMEOUT(2)：提示用户操作超时。  - TEMPORARILY_LOCKED(3)：提示用户等待冻结解除。  - PERMANENTLY_LOCKED(4)：提示用户需PIN解锁。  - WIDGET_LOADED(5)：认证界面已加载，可执行初始化。  - WIDGET_RELEASED(6)：认证界面已释放，可执行后续操作。  - COMPARE_FAILURE_WITH_FROZEN(7)：提示用户认证不通过且已冻结。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { userAuth } from '@kit.UserAuthenticationKit';

try {
  const rand = cryptoFramework.createRandom();
  const len: number = 16;
  let randData: Uint8Array | null = null;
  let retryCount = 0;
  while (retryCount < 3) {
    randData = rand?.generateRandomSync(len)?.data;
    if (randData) {
      break;
    }
    retryCount++;
  }
  if (!randData) {
    return;
  }
  const authParam: userAuth.AuthParam = {
    challenge: randData,
    authType: [userAuth.UserAuthType.PIN],
    authTrustLevel: userAuth.AuthTrustLevel.ATL3,
  };
  const widgetParam: userAuth.WidgetParam = {
    title: '请输入密码',
  };

  const userAuthInstance = userAuth.getUserAuthInstance(authParam, widgetParam);
  console.info('get userAuth instance successfully.');
  // 需要调用UserAuthInstance的start()接口，启动认证后，才能通过onAuthTip获取到认证中间状态。
  userAuthInstance.on('authTip', (authTipInfo: userAuth.AuthTipInfo) => {
    console.info('userAuthInstance callback');
  });
  console.info('auth on successfully.');
  userAuthInstance.start();
  console.info('auth start successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`Failed to auth. Code: ${err?.code}, message: ${err?.message}`);
}
```
