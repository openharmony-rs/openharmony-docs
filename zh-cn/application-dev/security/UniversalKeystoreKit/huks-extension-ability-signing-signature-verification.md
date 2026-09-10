# 签名/验签

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

在密钥管理扩展场景下，完成密钥管理扩展PIN认证后，应用可通过resourceId操作对应密钥执行签名/验签操作。该能力通过HUKS提供的三段式接口实现，应用指定相应的算法参数即可（包括算法类型，目的，填充，摘要等）。

## 三段式接口说明

签名/验签操作通过HUKS的三段式接口实现，通过指定[HUKS_TAG_KEY_CLASS](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag)为[HUKS_KEY_CLASS_EXTENSION](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukskeyclasstype22)，表示指定密钥由密钥管理扩展服务中的密钥。

具体使用可参考[签名验签示例](#签名验签示例)。

| 步骤 | 接口 | 说明 |
|------|------|------|
| 1 | [initSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksinitsession9) | 初始化密钥会话，返回会话handle。 |
| 2 | [updateSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksupdatesession9) | （可选）传入分段数据，执行中间密码运算。 |
| 3 | [finishSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksfinishsession9) | 结束会话，返回最终结果（签名/验签结果）。 |

> **说明：**
>
> 1. 通过[HUKS_TAG_KEY_CLASS](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag)指定密钥类别为[HUKS_KEY_CLASS_EXTENSION](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukskeyclasstype22)，表示该密钥由外部密钥管理扩展管理。
> 2. 三段式操作过程中，keyAlias参数需指定为resourceId。
> 3. finishSession完成后会释放会话句柄。
> 4. 签名/验签是否需要PIN认证取决于密钥用途：私钥签名需要PIN认证，公钥验签无需。

## 规格

具体规格与外部硬件密钥管理扩展实现相关，不同厂家实现有差异。

签名/验签操作需要在HuksOptions.properties中指定以下参数：

### 详细参数

| 参数 | 取值 | 必填 | 说明 |
|------|------|------|------|
| [HUKS_TAG_KEY_CLASS](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag) | `HUKS_KEY_CLASS_EXTENSION` | 是 | 表示由密钥管理扩展管理 |
| [HUKS_TAG_PURPOSE](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag) | 用途枚举值 | 否 | 指定用途，未传入则使用密钥管理扩展提供的默认值 |
| [HUKS_TAG_ALGORITHM](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag) | 算法枚举值 | 否 | 指定签名/验签算法 |
| [HUKS_TAG_KEY_SIZE](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag) | 密钥长度 | 否 | 如 2048、3072、4096 |

## 签名/验签示例

以密钥算法为RSA、摘要算法为SHA384、填充模式为PSS的密钥为例，完成签名、验签：

### 开发步骤

**ArkTS接口**

**签名：**

1. 通过[获取资源ID](huks-extension-ability-general-operation.md#获取资源id)操作，得到resourceId，并传入该resourceId进行打开资源，可参考[打开关闭资源](huks-extension-ability-general-operation.md#打开关闭资源)。

2. 参考[PIN码访问控制](huks-extension-ability-pin-authentication-management.md)完成PIN认证。

3. 设置属性参数[HuksOptions](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksoptions)，properties传入算法参数配置。

4. 调用[initSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksinitsession9)初始化密钥会话，不传入inData，获取sessionHandle。

5. （可选）调用[updateSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksupdatesession9)更新密钥会话，inData传入明文数据。

6. 调用[finishSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksfinishsession9)结束会话，inData传入明文数据，从返回值的outData中获取signature。

7. 操作执行完后，关闭资源，可参考[打开关闭资源](huks-extension-ability-general-operation.md#打开关闭资源)。

**验签：**

1. 通过[获取资源ID](huks-extension-ability-general-operation.md#获取资源id)操作，得到resourceId，并传入该resourceId进行打开资源，可参考[打开关闭资源](huks-extension-ability-general-operation.md#打开关闭资源)。

2. 设置属性参数[HuksOptions](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksoptions)，properties传入算法参数配置。

3. 调用[initSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksinitsession9)初始化密钥会话，不传入inData，获取sessionHandle。

4. （可选）调用[updateSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksupdatesession9)更新会话，inData传入明文数据。

5. 调用[finishSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksfinishsession9)结束会话，inData传入签名。

6. 操作执行完后，关闭资源，可参考[打开关闭资源](huks-extension-ability-general-operation.md#打开关闭资源)。

**C++接口**

**签名：**

1. 通过证书管理系统能力提供的[openAuthorizeDialog](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenauthorizedialog22)获取[keyUri](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certreference22)作为resourceId，并作为密钥别名，打开资源后完成PIN码认证，可参考[打开关闭资源](huks-extension-ability-general-operation.md#打开关闭资源)。

2. 指定待签名的明文数据。

3. 调用[OH_Huks_InitParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-param-h.md#oh_huks_initparamset)指定算法参数配置，并指定KeyClass参数，tag为[OH_HUKS_TAG_KEY_CLASS](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_tag)，值为[OH_HUKS_KEY_CLASS_EXTENSION](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_keyclasstype)。

4. 调用[OH_Huks_InitSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_initsession)初始化密钥会话，并获取会话的句柄handle。

5. 调用[OH_Huks_FinishSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_finishsession)结束密钥会话，获取签名signature。

**验签：**

1. 通过证书管理系统能力提供的[openAuthorizeDialog](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenauthorizedialog22)获取[keyUri](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certreference22)作为resourceId，并作为密钥别名，然后打开资源，可参考[打开关闭资源](huks-extension-ability-general-operation.md#打开关闭资源)。

2. 获取待验证的签名。

3. 调用[OH_Huks_InitParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-param-h.md#oh_huks_initparamset)指定算法参数配置，并指定KeyClass参数，tag为[OH_HUKS_TAG_KEY_CLASS](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_tag)，值为[OH_HUKS_KEY_CLASS_EXTENSION](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_keyclasstype)。

4. 调用[OH_Huks_InitSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_initsession)初始化密钥会话，并获取会话的句柄handle。

5. 调用[OH_Huks_UpdateSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_updatesession)更新密钥会话。

6. 调用[OH_Huks_FinishSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_finishsession)结束密钥会话，验证签名。

### 开发示例

**ArkTS接口**

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
    // 进行PIN认证
    await sign(keyAlias);
    await huksExternalCrypto.closeResource(keyAlias);

    // 验签流程（不需要PIN认证）
    await huksExternalCrypto.openResource(keyAlias);
    await verify(keyAlias);
    await huksExternalCrypto.closeResource(keyAlias);
  } catch (error) {
    console.error('signAndVerify input arg invalid.');
  }
}
```

**C++接口**

```c++
#include "huks/native_huks_api.h"
#include "huks/native_huks_param.h"
#include "napi/native_api.h"
#include <string.h>

OH_Huks_Result InitParamSet(
    struct OH_Huks_ParamSet **paramSet,
    const struct OH_Huks_Param *params,
    uint32_t paramCount)
{
    OH_Huks_Result ret = OH_Huks_InitParamSet(paramSet);
    if (ret.errorCode != OH_HUKS_SUCCESS) {
        return ret;
    }
    ret = OH_Huks_AddParams(*paramSet, params, paramCount);
    if (ret.errorCode != OH_HUKS_SUCCESS) {
        OH_Huks_FreeParamSet(paramSet);
        return ret;
    }
    ret = OH_Huks_BuildParamSet(paramSet);
    if (ret.errorCode != OH_HUKS_SUCCESS) {
        OH_Huks_FreeParamSet(paramSet);
        return ret;
    }
    return ret;
}

static struct OH_Huks_Param g_signParamsTest[] = {
    {
        .tag = OH_HUKS_TAG_ALGORITHM,
        .uint32Param = OH_HUKS_ALG_RSA
    }, {
        .tag = OH_HUKS_TAG_PURPOSE,
        .uint32Param = OH_HUKS_KEY_PURPOSE_SIGN
    }, {
        .tag = OH_HUKS_TAG_KEY_SIZE,
        .uint32Param = OH_HUKS_RSA_KEY_SIZE_2048
    }, {
        .tag = OH_HUKS_TAG_PADDING,
        .uint32Param = OH_HUKS_PADDING_PSS
    }, {
        .tag = OH_HUKS_TAG_DIGEST,
        .uint32Param = OH_HUKS_DIGEST_SHA256
    }, {
        .tag = OH_HUKS_TAG_KEY_CLASS,
        .uint32Param = OH_HUKS_KEY_CLASS_EXTENSION
    }
};

static struct OH_Huks_Param g_verifyParamsTest[] = {
    {
        .tag = OH_HUKS_TAG_ALGORITHM,
        .uint32Param = OH_HUKS_ALG_RSA
    }, {
        .tag = OH_HUKS_TAG_PURPOSE,
        .uint32Param = OH_HUKS_KEY_PURPOSE_VERIFY
    }, {
        .tag = OH_HUKS_TAG_KEY_SIZE,
        .uint32Param = OH_HUKS_RSA_KEY_SIZE_2048
    }, {
        .tag = OH_HUKS_TAG_PADDING,
        .uint32Param = OH_HUKS_PADDING_PSS
    }, {
        .tag = OH_HUKS_TAG_DIGEST,
        .uint32Param = OH_HUKS_DIGEST_SHA256
    }, {
        .tag = OH_HUKS_TAG_KEY_CLASS,
        .uint32Param = OH_HUKS_KEY_CLASS_EXTENSION
    }
};

static const uint32_t RSA_COMMON_SIZE = 1024;
static const char *DATA_TO_SIGN = "Hks_RSA_Sign_Verify_Test_0000000000000000000000000000000000000000000000000000000"
                                  "00000000000000000000000000000000000000000000000000000000000000000000000000000000"
                                  "0000000000000000000000000000000000000000000000000000000000000000000000000_string";
static const char *KEY_ALIAS = "{\"providerName\":\"testProviderName\",\"abilityName\":\"CryptoExtension\","
                              "\"bundleName\":\"com.example.cryptoapplication\",\"index\":{\"key\":\"testKey\"}}";

static napi_value SignVerifyKey(napi_env env, napi_callback_info info) 
{
    // 假设keyAlias是获取的resourceId
    struct OH_Huks_Blob keyAlias = {
        (uint32_t)strlen(KEY_ALIAS),
        (uint8_t *)KEY_ALIAS
    };
    struct OH_Huks_Blob inData = {
        (uint32_t)strlen(DATA_TO_SIGN),
        (uint8_t *)DATA_TO_SIGN
    };
    struct OH_Huks_ParamSet *signParamSet = nullptr;
    struct OH_Huks_ParamSet *verifyParamSet = nullptr;
    OH_Huks_Result ohResult;
    do {
        ohResult = InitParamSet(&signParamSet, g_signParamsTest, sizeof(g_signParamsTest) / sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        ohResult = InitParamSet(&verifyParamSet, g_verifyParamsTest,
            sizeof(g_verifyParamsTest) / sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        /* 1. Sign */
        // Init
        uint8_t handleS[sizeof(uint64_t)] = {0};
        struct OH_Huks_Blob handleSign = { (uint32_t)sizeof(uint64_t), handleS };
        ohResult = OH_Huks_InitSession(&keyAlias, signParamSet, &handleSign, nullptr);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        // Finish
        uint8_t outDataS[RSA_COMMON_SIZE] = {0};
        struct OH_Huks_Blob outDataSign = { RSA_COMMON_SIZE, outDataS };
        ohResult = OH_Huks_FinishSession(&handleSign, signParamSet,  &inData, &outDataSign);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        
        /* 2. Verify */
        // Init
        uint8_t handleV[sizeof(uint64_t)] = {0};
        struct OH_Huks_Blob handleVerify = { (uint32_t)sizeof(uint64_t), handleV };
        ohResult = OH_Huks_InitSession(&keyAlias, verifyParamSet, &handleVerify, nullptr);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        // Update loop
        uint8_t temp[] = "out";
        struct OH_Huks_Blob verifyOut = { (uint32_t)sizeof(temp), temp };
        ohResult = OH_Huks_UpdateSession(&handleVerify, verifyParamSet, &inData, &verifyOut);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        // Finish
        ohResult = OH_Huks_FinishSession(&handleVerify, verifyParamSet, &outDataSign, &verifyOut);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
    } while (0);
    OH_Huks_FreeParamSet(&signParamSet);
    OH_Huks_FreeParamSet(&verifyParamSet);
    
    napi_value ret;
    napi_create_int32(env, ohResult.errorCode, &ret);
    return ret;
}
```