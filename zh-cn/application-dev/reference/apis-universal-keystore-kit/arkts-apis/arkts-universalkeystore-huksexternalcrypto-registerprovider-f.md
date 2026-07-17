# registerProvider

## 导入模块

```TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
```

## registerProvider

```TypeScript
function registerProvider(providerName: string, params: Array<HuksExternalCryptoParam>): Promise<void>
```

注册指定的外部provider。使用Promise异步回调。

若需使用自定义PIN码弹窗，在注册provider时需要同步注册UIExtensionAbility，注意事项如下：

1. 自定义ability通过UIExtensionAbility扩展实现。2. 注册的UIExtensionAbility可以通过证书管理kit提供的[openUKeyAuthDialog](../../apis-device-certificate-kit/arkts-apis/arkts-security-certmanager.md)接口统一拉起。

3. 系统拉起自定义弹窗时会通过want接口向开发者传递以下参数：  
- Action：string参数类型，在拉起自定义弹窗时want传输的Action为"UkeyPINAuth"。  
- appUid：number参数类型，通过want.parameters传输。"appUid"字段为应用id，开发者可以通过该字段完成应用隔离。  
- keyUri：string参数类型其值为resourceId，通过want.parameters传输，表示Ukey证书的索引。

4. 开发者实现UIExtensionAbility时，应用需根据指定场景返回对应的错误码：  
- 用户取消操作时，返回-1001。  
- keyUri指定的证书/密钥不存在时，返回-1008。  
- 参数格式错误时，返回-1014。  
- 其余失败场景返回错误码-1000，成功时返回0。

**起始版本：** 22

**需要权限：** ohos.permission.CRYPTO_EXTENSION_REGISTER

<!--Device-huksExternalCrypto-function registerProvider(providerName: string, params: Array<HuksExternalCryptoParam>): Promise<void>--><!--Device-huksExternalCrypto-function registerProvider(providerName: string, params: Array<HuksExternalCryptoParam>): Promise<void>-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| providerName | string | 是 | provider名称，最大长度为128。建议包含厂商信息，全局唯一，不要包含个人联系方式等敏感数据。<br>最多支持注册10个provider。 |
| params | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<HuksExternalCryptoParam> | 是 | 操作时需传入的参数，必选TAG：[HUKS_EXT_CRYPTO_TAG_ABILITY_NAME](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptotagtype-e.md)，表示ability的名字，根据业务自己内部定义按照实际填写。<br>从API版本26.0.0开始，可选TAG：[HUKS_EXT_CRYPTO_TAG_ABILITY_INFO](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptotagtype-e.md)，以JSON列表的形式传入PIN码认证自定义弹窗UIExtensionAbility的名字以及包名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | check permission failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | api is not supported. |
| [12000002](../errorcode-huks.md#12000002-缺少密钥算法参数) | the ability name param is missing. |
| [12000005](../errorcode-huks.md#12000005-进程通信错误) | IPC communication failed. |
| [12000014](../errorcode-huks.md#12000014-内存不足) | memory is insufficient. |
| [12000018](../errorcode-huks.md#12000018-输入参数非法) | the input parameter is invalid. |
| [12000019](../errorcode-huks.md#12000019-同名provider已注册) | the provider is already registered. |
| [12000020](../errorcode-huks.md#12000020-依赖的模块报错) | an error occurred in the dependent module. |
| [12000025](../errorcode-huks.md#12000025-资源超过限制) | the number of providers exceeds the limit. |

**示例：**

```TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';

function stringToUint8Array(str: string) {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

const providerName = "testProviderName";
const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [
  {
    tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_ABILITY_NAME,
    value: stringToUint8Array("CryptoExtension")
  }
];
huksExternalCrypto.registerProvider(providerName, extProperties)
    .then(() => {
        console.info('promise: registerProvider success.');
    });

```

