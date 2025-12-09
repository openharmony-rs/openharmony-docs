# 签名/验签(ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

当前指导提供以下示例，供开发者参考完成签名、验签开发：

- [密钥算法为RSA、摘要算法为SHA256、填充模式为PSS](#rsasha256pss)
<!--RP1--><!--RP1End-->

具体的场景介绍及支持的算法规格，请参考[签名/验签支持的算法](huks-ukey-signing-signature-verification-overview.md#规格)。

## 开发步骤

**签名**

1. 通过[证书管理应用](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenauthorizedialog22)获取resourceId作为密钥别名，并完成PIN码认证后打开资源。

2. 指定待签名的明文数据。

3. 获取属性参数[HuksOptions](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksoptions)，包括两个字段properties和inData。inData传入明文数据，properties传入[算法参数配置](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksparam)。

4. 调用[initSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksinitsession9)初始化密钥会话，并获取会话的句柄handle。

5. 调用[finishSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksfinishsession9)结束密钥会话，获取签名signature。

**验签**

1. 通过[证书管理应用](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenauthorizedialog22)获取resourceId作为密钥别名，并[打开资源](huks-open-close-resource-ndk.md)。

2. 获取待验证的签名。

3. 获取属性参数[HuksOptions](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksoptions)，包括两个字段properties和inData。inData传入签名signature，properties传入[算法参数配置](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksparam)。

4. 调用[initSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksinitsession9)初始化密钥会话，并获取会话的句柄handle。

5. 调用[updateSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksupdatesession9)更新密钥会话。

6. 调用[finishSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksfinishsession9)结束密钥会话，验证签名。

## 开发案例

### RSA/SHA256/PSS
```ts
/*
 * 密钥算法为RSA，摘要算法为SHA256，填充模式为PSS
 */
import { huks } from '@kit.UniversalKeystoreKit';
import { BusinessError } from "@kit.BasicServicesKit";

// 假设keyAlias是已获取的resourceId
let keyAlias = "{\"providerName\":\"testProviderName\",\"abilityName\":\"CryptoExtension\",\"bundleName\":\"com.example.cryptoapplication\",\"index\":{\"key\":\"testKey\"}}";
let handle: number;
let plaintext = '123456';
let signature: Uint8Array;

function StringToUint8Array(str: string) {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

function Uint8ArrayToString(fileData: Uint8Array) {
  let dataString = '';
  for (let i = 0; i < fileData.length; i++) {
    dataString += String.fromCharCode(fileData[i]);
  }
  return dataString;
}

function GetRsaSignProperties() {
  let properties: Array<huks.HuksParam> = [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_RSA
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_RSA_KEY_SIZE_2048
  }, {
    tag: huks.HuksTag.HUKS_TAG_PADDING,
    value: huks.HuksKeyPadding.HUKS_PADDING_PSS
  }, {
    tag: huks.HuksTag.HUKS_TAG_DIGEST,
    value: huks.HuksKeyDigest.HUKS_DIGEST_SHA256
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_SIGN
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_CLASS,
    value: huks.HuksKeyClassType.HUKS_KEY_CLASS_EXTENSION
  }];
  return properties;
}

function GetRsaVerifyProperties() {
  let properties: Array<huks.HuksParam> = [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_RSA
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_RSA_KEY_SIZE_2048
  }, {
    tag: huks.HuksTag.HUKS_TAG_PADDING,
    value: huks.HuksKeyPadding.HUKS_PADDING_PSS
  }, {
    tag: huks.HuksTag.HUKS_TAG_DIGEST,
    value: huks.HuksKeyDigest.HUKS_DIGEST_SHA256
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_VERIFY
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_CLASS,
    value: huks.HuksKeyClassType.HUKS_KEY_CLASS_EXTENSION
  }];
  return properties;
}

async function initSession(keyAlias: string, huksOptions: huks.HuksOptions) {
  console.info(`promise: enter initSession`);
  try {
    await huks.initSession(keyAlias, huksOptions)
      .then((data) => {
        handle = data.handle;
        console.info(`promise: initSession success`);
      }).catch((error: BusinessError) => {
        console.error(`promise: initSession failed, errCode : ${error.code}, errMsg : ${error.message}`);
      })
  } catch (error) {
    console.error(`promise: initSession input arg invalid`);
  }
}

async function updateSession(handle: number, huksOptions: huks.HuksOptions) {
  console.info(`promise: enter updateSession`);
  try {
    await huks.updateSession(handle, huksOptions)
      .then((data) => {
        let outData = data.outData as Uint8Array;
        console.info(`promise: updateSession success, data = ${Uint8ArrayToString(outData)}`);
      }).catch((error: BusinessError) => {
        console.error(`promise: updateSession failed, errCode : ${error.code}, errMsg : ${error.message}`);
      })
  } catch (error) {
    console.error(`promise: updateSession input arg invalid`);
  }
}

async function finishSession(handle: number, huksOptions: huks.HuksOptions) {
  console.info(`promise: enter finishSession`);
  try {
    await huks.finishSession(handle, huksOptions)
      .then((data) => {
        signature = data.outData as Uint8Array;
        console.info(`promise: finishSession success, data = ${Uint8ArrayToString(signature)}`);
      }).catch((error: BusinessError) => {
        console.error(`promise: finishSession failed, errCode : ${error.code}, errMsg : ${error.message}`);
      })
  } catch (error) {
    console.error(`promise: finishSession input arg invalid`);
  }
}

async function Sign(keyAlias: string, plaintext: string) {
  console.info(`enter Sign`);
  let signProperties = GetRsaSignProperties();
  let options: huks.HuksOptions = {
    properties: signProperties,
    inData: StringToUint8Array(plaintext)
  }
  await initSession(keyAlias, options);

  if (handle !== undefined) {
    await finishSession(handle, options);
  }
}

async function Verify(keyAlias: string, plaintext: string, signature: Uint8Array) {
  console.info(`enter Verify`);
  let verifyProperties = GetRsaVerifyProperties();
  let options: huks.HuksOptions = {
    properties: verifyProperties,
    inData: StringToUint8Array(plaintext)
  }

  await initSession(keyAlias, options);

  if (handle !== undefined) {
    await updateSession(handle, options);
    options.inData = signature;
    await finishSession(handle, options);
  }
}

async function testSignVerify() {
  await Sign(keyAlias, plaintext);
  await Verify(keyAlias, plaintext, signature);
}
```