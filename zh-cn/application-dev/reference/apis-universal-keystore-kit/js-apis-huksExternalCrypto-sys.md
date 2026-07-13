# @ohos.security.huksExternalCrypto (外部密钥管理)(系统接口)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

模块提供外部密钥管理扩展功能的注册与注销，PIN码认证与认证状态获取等。

> **说明**
>
> 本模块首批接口从API version 22开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
```

## huksExternalCrypto.authUkeyPin

authUkeyPin(resourceId: string, params: Array\<HuksExternalCryptoParam>): Promise\<void>

PIN码认证。使用Promise异步回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------|
| resourceId | string | 是   | Ukey中某容器的资源ID，可通过[导出证书的接口](../apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenauthorizedialog22)获取，其结果中附带resourceId。 |
| params  | Array\<[HuksExternalCryptoParam](js-apis-huksExternalCrypto.md#huksexternalcryptoparam)> | 是   | 操作时需传入的参数，必选TAG：[HUKS_EXT_CRYPTO_TAG_UKEY_PIN](js-apis-huksExternalCrypto.md#huksexternalcryptotag)。 |

**返回值：**

| 类型     | 说明   |
| -------- | ---------- |
| Promise\<void> | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[HUKS错误码](errorcode-huks.md)。

| 错误码ID | 错误信息      |
| -------- | ------------- |
| 202 | The caller is not a system application and is not allowed to use system applications. |
| 801 | api is not supported. |
| 12000005 | IPC communication failed. |
| 12000006 | the Ukey driver operation failed. |
| 12000011 | queried entity does not exist. |
| 12000012 | Device environment or input parameter abnormal. This error may occur if the process function is not found, or due to other issues. |
| 12000014 | memory is insufficient. |
| 12000018 | the input parameter is invalid. |
| 12000020 | the provider operation failed. |
| 12000021 | the Ukey PIN is locked. |
| 12000022 | the Ukey PIN is incorrect. |
| 12000024 | the provider or Ukey is busy. |

**示例：**

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';

function StringToUint8Array(str: string) {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

let uid: number = 3511;
const testResourceId = "{\"providerName\":\"testProviderName\", \"bundleName\":\"com.example.cryptoapplication\", \"abilityName\":\"CryptoExtension\",\"index\":{\"key\":\"testKey\"}}";
const pin = "123456";
const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [
  {
    tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_UID,
    value: uid
  }, {
    tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_UKEY_PIN,
    value: StringToUint8Array(pin)
  }
];
huksExternalCrypto.authUkeyPin(testResourceId, extProperties)
    .then((data) => {
        console.info(`promise: authUkeyPin success`);
    });
```
