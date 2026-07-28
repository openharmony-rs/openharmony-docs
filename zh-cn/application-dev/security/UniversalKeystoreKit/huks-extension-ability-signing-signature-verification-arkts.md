# 签名/验签(ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

当前指导提供以下示例，供开发者参考完成签名、验签开发：

- [密钥算法为RSA、摘要算法为SHA256、填充模式为PSS](#rsasha256pss)

具体的场景介绍及支持的算法规格，请参考[签名/验签介绍及算法规格](huks-extension-ability-signing-signature-verification-overview.md)。

## 开发步骤

### 签名

1. 通过[获取资源ID(ArkTS)](huks-extension-get-resource-id-arkts.md)获取resourceId，并通过[打开资源](huks-open-close-resource-arkts.md#打开资源)。

2. 参考[PIN码认证介绍及规格](huks-extension-ability-pin-authentication-management-overview.md)完成PIN认证。

3. 设置属性参数[HuksOptions](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksoptions)，properties传入算法参数配置。

4. 调用[initSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksinitsession9)初始化密钥会话，不传入inData，获取sessionHandle。

5. （可选）调用[updateSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksupdatesession9)更新密钥会话，inData传入明文数据。

6. 调用[finishSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksfinishsession9)结束会话，inData传入明文数据，从返回值的outData中获取signature。

7. 执行[关闭资源](huks-open-close-resource-arkts.md#关闭资源)。

### 验签

1. 通过[获取资源ID(ArkTS)](huks-extension-get-resource-id-arkts.md)获取resourceId，并通过[打开资源](huks-open-close-resource-arkts.md#打开资源)。

2. 设置属性参数[HuksOptions](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksoptions)，properties传入算法参数配置。

3. 调用[initSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksinitsession9)初始化密钥会话，不传入inData，获取sessionHandle。

4. （可选）调用[updateSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksupdatesession9)更新会话，inData传入明文数据。

5. 调用[finishSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksfinishsession9)结束会话，inData传入签名。

6. 执行[关闭资源](huks-open-close-resource-arkts.md#关闭资源)。

## 开发案例

### RSA/SHA256/PSS
```ts
/*
 * 密钥算法为RSA，摘要算法为SHA256，填充模式为PSS
 */
import { huks, huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { util } from '@kit.ArkTS';

let handle: number;
let plaintext = '123456';
let signature: Uint8Array;

function StringToUint8Array(str: string): Uint8Array {
  return new util.TextEncoder().encodeInto(str);
}

function Uint8ArrayToString(data: Uint8Array) {
  let s = '';
  for (let i = 0; i < data.length; i++) s += String.fromCharCode(data[i]);
  return s;
}

function getRsaSignProperties() {
  return [
    { tag: huks.HuksTag.HUKS_TAG_ALGORITHM, value: huks.HuksKeyAlg.HUKS_ALG_RSA },
    { tag: huks.HuksTag.HUKS_TAG_KEY_SIZE, value: huks.HuksKeySize.HUKS_RSA_KEY_SIZE_2048 },
    { tag: huks.HuksTag.HUKS_TAG_PADDING, value: huks.HuksKeyPadding.HUKS_PADDING_PSS },
    { tag: huks.HuksTag.HUKS_TAG_DIGEST, value: huks.HuksKeyDigest.HUKS_DIGEST_SHA256 },
    { tag: huks.HuksTag.HUKS_TAG_PURPOSE, value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_SIGN },
    { tag: huks.HuksTag.HUKS_TAG_KEY_CLASS, value: huks.HuksKeyClassType.HUKS_KEY_CLASS_EXTENSION }
  ];
}

function getRsaVerifyProperties() {
  return [
    { tag: huks.HuksTag.HUKS_TAG_ALGORITHM, value: huks.HuksKeyAlg.HUKS_ALG_RSA },
    { tag: huks.HuksTag.HUKS_TAG_KEY_SIZE, value: huks.HuksKeySize.HUKS_RSA_KEY_SIZE_2048 },
    { tag: huks.HuksTag.HUKS_TAG_PADDING, value: huks.HuksKeyPadding.HUKS_PADDING_PSS },
    { tag: huks.HuksTag.HUKS_TAG_DIGEST, value: huks.HuksKeyDigest.HUKS_DIGEST_SHA256 },
    { tag: huks.HuksTag.HUKS_TAG_PURPOSE, value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_VERIFY },
    { tag: huks.HuksTag.HUKS_TAG_KEY_CLASS, value: huks.HuksKeyClassType.HUKS_KEY_CLASS_EXTENSION }
  ];
}

async function initSession(keyAlias: string, options: huks.HuksOptions) {
  await huks.initSession(keyAlias, options)
    .then((data) => { handle = data.handle; })
    .catch((error: BusinessError) => console.error(`initSession failed: ${error.code}`));
}

async function finishSession(options: huks.HuksOptions) {
  await huks.finishSession(handle, options)
    .then((data) => { signature = data.outData as Uint8Array; });
}

async function sign(keyAlias: string) {
  const options: huks.HuksOptions = { properties: getRsaSignProperties() };
  await initSession(keyAlias, options);
  if (handle !== undefined) {
    options.inData = StringToUint8Array(plaintext);
    await finishSession(options);
  }
}

async function verify(keyAlias: string) {
  const options: huks.HuksOptions = { properties: getRsaVerifyProperties() };
  await initSession(keyAlias, options);
  if (handle !== undefined) {
    options.inData = StringToUint8Array(plaintext);
    await huks.updateSession(handle, options);
    options.inData = signature;
    await huks.finishSession(handle, options);
  }
}

async function signAndVerify() {
  const keyAlias = JSON.stringify({
    providerName: "testProviderName",
    bundleName: "com.example.cryptoapplication",
    abilityName: "CryptoExtension",
    index: { key: "testKey" } as ESObject
  });
  try {
    // 签名流程
    await huksExternalCrypto.openResource(keyAlias);
    // ... 进行 PIN 认证 ...
    await sign(keyAlias);
    await huksExternalCrypto.closeResource(keyAlias);

    // 验签流程（不需要 PIN 认证）
    await huksExternalCrypto.openResource(keyAlias);
    await verify(keyAlias);
    await huksExternalCrypto.closeResource(keyAlias);
  } catch (error) {
    console.error('signAndVerify input arg invalid.');
  }
}
```