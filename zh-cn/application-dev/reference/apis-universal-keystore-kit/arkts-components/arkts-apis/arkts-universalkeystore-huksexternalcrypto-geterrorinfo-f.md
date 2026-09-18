# getErrorInfo

## 导入模块

```TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
```

## getErrorInfo

```TypeScript
function getErrorInfo(): HuksExternalErrorInfo
```

查询上次接口调用产生的详细错误信息。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [HuksExternalErrorInfo](arkts-universalkeystore-huksexternalcrypto-huksexternalerrorinfo-i.md) | 返回的详细错误信息。 |

**示例**

```TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';

const resourceId = JSON.stringify({
  providerName: "testProviderName",
  bundleName: "com.example.cryptoapplication",
  abilityName: "CryptoExtension",
  index: {
    key: "testKey"
  } as ESObject
});

async function testFunction() : Promise<void>
{
  try {
    await huksExternalCrypto.openResource(resourceId);
  } catch (error) {
    const errorInfo = huksExternalCrypto.getErrorInfo();
    console.error(`errno: ${errorInfo.errno}`);
    console.error(`errorDesc: ${errorInfo.errorDesc}`);
  }
}
```
