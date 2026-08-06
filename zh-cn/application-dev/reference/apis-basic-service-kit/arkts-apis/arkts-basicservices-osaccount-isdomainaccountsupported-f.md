# isDomainAccountSupported

## isDomainAccountSupported

```TypeScript
function isDomainAccountSupported(): Promise<boolean>
```

检查是否支持域账号。使用Promise异步回调。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-osAccount-function isDomainAccountSupported(): Promise<boolean>--><!--Device-osAccount-function isDomainAccountSupported(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示支持域账号；返回false表示不支持。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError, osAccount } from '@kit.BasicServicesKit';

try {
  osAccount.isDomainAccountSupported().then((isSupported: boolean) => {
    console.info('isDomainAccountSupported successfully, isSupported: ' + isSupported);
  }).catch((err: BusinessError) => {
    console.error(`isDomainAccountSupported failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`isDomainAccountSupported exception: code is ${err.code}, message is ${err.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError, osAccount } from '@kit.BasicServicesKit';

try {
  osAccount.isDomainAccountSupported().then((isSupported: boolean) => {
    console.info('isDomainAccountSupported successfully, isSupported: ' + isSupported);
  }).catch((e: Error) => {
    const err = e as BusinessError;
    console.error(`isDomainAccountSupported failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e: Error) {
  const err = e as BusinessError;
  console.error(`isDomainAccountSupported exception: code is ${err.code}, message is ${err.message}`);
}
```

