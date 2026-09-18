# @ohos.security.huksExternalCrypto(外部密钥管理)

模块提供外部密钥管理扩展功能的注册与注销，PIN码认证与认证状态获取等。

**起始版本：** 22

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## 导入模块

```TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [clearUkeyPinAuthState](arkts-universalkeystore-huksexternalcrypto-clearukeypinauthstate-f.md) | 清除指定资源ID的PIN码认证状态。使用Promise异步回调。 |
| [closeResource](arkts-universalkeystore-huksexternalcrypto-closeresource-f.md) | 关闭指定资源ID的资源。使用Promise异步回调。 |
| [getErrorInfo](arkts-universalkeystore-huksexternalcrypto-geterrorinfo-f.md) | 查询上次接口调用产生的详细错误信息。 |
| [getProperty](arkts-universalkeystore-huksexternalcrypto-getproperty-f.md) | 调用此接口获取属性值并返回结果。使用Promise异步回调。 |
| [getResourceId](arkts-universalkeystore-huksexternalcrypto-getresourceid-f.md) | 获取密钥扩展能力的资源ID。使用Promise异步回调。 |
| [getUkeyPinAuthState](arkts-universalkeystore-huksexternalcrypto-getukeypinauthstate-f.md) | 获取PIN码认证状态。使用Promise异步回调。 |
| [openResource](arkts-universalkeystore-huksexternalcrypto-openresource-f.md) | 打开指定资源ID的资源。使用Promise异步回调。 |
| [registerProvider](arkts-universalkeystore-huksexternalcrypto-registerprovider-f.md) | 注册指定的外部provider。使用Promise异步回调。 |
| [setProperty](arkts-universalkeystore-huksexternalcrypto-setproperty-f.md) | The set-type operations of the external crypto extension support calling custom interfaces. However, the custom interface must be registered with the provider. |
| [unregisterProvider](arkts-universalkeystore-huksexternalcrypto-unregisterprovider-f.md) | 注销指定的外部provider。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [authUkeyPin](arkts-universalkeystore-huksexternalcrypto-authukeypin-f-sys.md) | PIN码认证。使用Promise异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [HuksExternalCryptoParam](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptoparam-i.md) | 表示调用接口使用的param数组的类型。 |
| [HuksExternalErrorInfo](arkts-universalkeystore-huksexternalcrypto-huksexternalerrorinfo-i.md) | 详细错误信息 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [HuksExternalCryptoTag](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptotag-e.md) | 表示调用参数的Tag。 |
| [HuksExternalCryptoTagType](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptotagtype-e.md) | 表示外部加密数据类型的枚举。 |
| [HuksExternalPinAuthState](arkts-universalkeystore-huksexternalcrypto-huksexternalpinauthstate-e.md) | 枚举PIN认证的状态 |
