# PIN码访问控制

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

PIN（Personal Identification Number）码是密钥管理扩展服务中的安全访问凭证，服务实现方可以采用“凭证+PIN码”的双因子认证模式：用户必须同时拥有有效的凭证（如物理设备、虚拟服务会话等）和正确的PIN码，才能访问服务内的密钥材料。

PIN码作用如下：

1. 防暴力破解：连续错误输入达到一定次数（与密钥管理扩展服务实现相关）后自动锁定，通过[onAuthUkeyPin](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#onauthukeypin)返回值中的retryCount字段查询剩余重试次数。

2. 硬件级安全：PIN码验证在密钥管理扩展服务内完成，敏感信息不离开服务。

密钥管理扩展服务使用resourceId标识资源，生态应用打开资源之后，如需要操作resourceId对应的私钥执行签名操作，则需要先验证PIN码。

## PIN码认证状态管理

HUKS提供以下PIN码认证状态管理能力：

- **查询认证状态**：从API版本22开始，可通过[getUkeyPinAuthState](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogetukeypinauthstate)查询当前PIN码认证状态。

- **清除认证状态**：从API版本26.0.0开始，可通过[clearUkeyPinAuthState](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptoclearukeypinauthstate)清除指定资源的PIN码认证状态。
<!--Del-->
      
- **PIN认证**：从API版本22开始，可通过[authUkeyPin](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto-sys.md#huksexternalcryptoauthukeypin)发起验证PIN码请求。
<!--DelEnd-->

> **说明：**
>
> HUKS提供PIN码认证能力和认证状态查询能力。应用PIN码认证之前，可以先查询认证状态。如果需要PIN码认证，则需要拉起[证书管理应用](../DeviceCertificateKit/certManager-overview.md)，完成PIN码认证。

## 查询认证状态

应用可以通过对应接口查询PIN码是否认证通过。

### 开发步骤

**ArkTS接口**

1. 通过[获取资源ID](huks-extension-ability-general-operation.md#获取资源id)操作，得到resourceId，并传入该resourceId进行打开资源，可参考[打开关闭资源](huks-extension-ability-general-operation.md#打开关闭资源)。

2. 调用查询认证状态接口[getUkeyPinAuthState](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogetukeypinauthstate)验证PIN码。

3. 操作执行完后，关闭资源，可参考[打开关闭资源](huks-extension-ability-general-operation.md#打开关闭资源)。

**C++接口**

1. 在CMake脚本中链接相关动态库：
   ```txt
   target_link_libraries(entry PUBLIC libhuks_ndk.z.so libhuks_external_crypto.z.so)
   ```

2. 通过[获取资源ID](huks-extension-ability-general-operation.md#获取资源id)中的证书管理途径获取resourceId，并传入该resourceId进行打开资源，可参考[打开关闭资源](huks-extension-ability-general-operation.md#打开关闭资源)。

3. 调用[OH_Huks_InitExternalCryptoParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_initexternalcryptoparamset)指定参数配置。

4. 调用[OH_Huks_GetUkeyPinAuthState](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_getukeypinauthstate)获取PIN码认证状态。

5. 操作执行完后，关闭资源，可参考[打开关闭资源](huks-extension-ability-general-operation.md#打开关闭资源)。

### 开发示例

**ArkTS接口**

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function getUkeyPinAuthState(): Promise<huksExternalCrypto.HuksExternalPinAuthState> {
  let ret: huksExternalCrypto.HuksExternalPinAuthState = huksExternalCrypto.HuksExternalPinAuthState.HUKS_EXT_CRYPTO_PIN_NO_AUTH;
  try {
    /* 1.构造查询PIN码状态参数 */
    const testResourceId = JSON.stringify({
      providerName: 'testProviderName',
      bundleName: 'com.example.cryptoapplication',
      abilityName: 'CryptoExtension',
      index: {
        key: 'testKey'
      } as ESObject
    });

    const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [];

    /* 2.调用getUkeyPinAuthState */
    await huksExternalCrypto.getUkeyPinAuthState(testResourceId, extProperties)
      .then((data) => {
        console.info(`promise: getUkeyPinAuthState success , data: ${data}`);
      }).catch((error: BusinessError) => {
        console.error(`promise: getUkeyPinAuthState failed, errCode: ${error.code}, errMsg: ${error.message}`);
      });
  } catch (error) {
    console.error('promise: getUkeyPinAuthState input arg invalid.');
  }
  return ret;
}

async function testGetUkeyPinAuthState() {
  let ret: huksExternalCrypto.HuksExternalPinAuthState = await getUkeyPinAuthState();
  if (ret != huksExternalCrypto.HuksExternalPinAuthState.HUKS_EXT_CRYPTO_PIN_AUTH_SUCCEEDED) {
    console.error('getUkeyPinAuthState failed.');
    return;
  }

  console.info('getUkeyPinAuthState success.');
}
```

**C++接口**

```c++
#include "huks/native_huks_external_crypto_api.h"
#include "huks/native_huks_param.h"
#include "napi/native_api.h"
#include <string.h>

OH_Huks_Result InitParamSet(
    struct OH_Huks_ExternalCryptoParamSet **paramSet,
    const struct OH_Huks_ExternalCryptoParam *params,
    uint32_t paramCount)
{
    OH_Huks_Result ret = OH_Huks_InitExternalCryptoParamSet(paramSet);
    if (ret.errorCode != OH_HUKS_SUCCESS) {
        return ret;
    }
    ret = OH_Huks_AddExternalCryptoParams(*paramSet, params, paramCount);
    if (ret.errorCode != OH_HUKS_SUCCESS) {
        OH_Huks_FreeExternalCryptoParamSet(paramSet);
        return ret;
    }
    ret = OH_Huks_BuildExternalCryptoParamSet(paramSet);
    if (ret.errorCode != OH_HUKS_SUCCESS) {
        OH_Huks_FreeExternalCryptoParamSet(paramSet);
        return ret;
    }
    return ret;
}

static const char *resourceId = "{\"providerName\":\"testProviderName\",\"abilityName\":\"CryptoExtension\",\"bundleName\":\"com.example.cryptoapplication\",\"index\":{\"key\":\"testKey\"}}";

static struct OH_Huks_ExternalCryptoParam g_getPinStateParamsTest[] = {};

static napi_value GetUkeyPinAuthState(napi_env env, napi_callback_info info) 
{
    struct OH_Huks_Blob g_resourceId = {
        (uint32_t)strlen(resourceId),
        (uint8_t *)resourceId
    };
    struct OH_Huks_ExternalCryptoParamSet *pinStateParamSet = nullptr;
    OH_Huks_ExternalPinAuthState authState = OH_HUKS_EXT_CRYPTO_PIN_NO_AUTH;
    OH_Huks_Result ohResult;
    do {
        ohResult = InitParamSet(&pinStateParamSet, g_getPinStateParamsTest,
            sizeof(g_getPinStateParamsTest) / sizeof(OH_Huks_ExternalCryptoParam));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        ohResult = OH_Huks_GetUkeyPinAuthState(&g_resourceId, pinStateParamSet, &authState);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
    } while (0);
    OH_Huks_FreeExternalCryptoParamSet(&pinStateParamSet);
    
    napi_value ret;
    napi_create_int32(env, ohResult.errorCode, &ret);
    return ret;
}
```

## 清除认证状态

应用在密钥操作完成后或需要重置认证状态时，可以调用对应接口清除指定资源的PIN码认证状态。

### 使用场景

以下场景可能需要清除PIN码认证状态：

- 密钥操作完成后，主动清除认证状态，避免认证状态残留。
- 应用退出或切换用户时，清除认证状态。
- 认证状态异常时，重置认证状态。

### 开发步骤

1. 通过[获取资源ID](huks-extension-ability-general-operation.md#获取资源id)操作，得到resourceId，并传入该resourceId进行打开资源，可参考[打开关闭资源](huks-extension-ability-general-operation.md#打开关闭资源)。

2. 调用[clearUkeyPinAuthState](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptoclearukeypinauthstate)清除PIN码认证状态。

3. 操作执行完后，关闭资源，可参考[打开关闭资源](huks-extension-ability-general-operation.md#打开关闭资源)。

### 开发示例

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 清除PIN码认证状态
async function clearUkeyPinAuthState(resourceId: string): Promise<void> {
  try {
    await huksExternalCrypto.clearUkeyPinAuthState(resourceId)
      .then(() => {
        console.info('promise: clearUkeyPinAuthState success.');
      }).catch((error: BusinessError) => {
        console.error(`promise: clearUkeyPinAuthState failed, errCode: ${error.code}, errMsg: ${error.message}`);
      });
  } catch (error) {
    console.error('promise: clearUkeyPinAuthState input arg invalid.');
  }
}
```
<!--Del-->
## PIN认证

应用在用户输入PIN码后，可调用对应接口完成PIN码认证。在发起PIN认证流程前，调用方需要先获取密钥管理扩展服务中的公钥用于加密用户输入的PIN码。调用[getProperty](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogetproperty)接口并传入SKF_ExportPublicKey作为propertyId。

### 开发步骤

1. 通过[获取资源ID](huks-extension-ability-general-operation.md#获取资源id)操作，得到resourceId，并传入该resourceId进行打开资源，可参考[打开关闭资源](huks-extension-ability-general-operation.md#打开关闭资源)。

2. 调用[getProperty](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogetproperty)并传入SKF_ExportPublicKey作为propertyId，导出用于PIN码加密传输的公钥。

3. 构造参数，必传[HUKS_EXT_CRYPTO_TAG_UID](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)和[HUKS_EXT_CRYPTO_TAG_UKEY_PIN](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)。

4. 调用接口[authUkeyPin](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto-sys.md#huksexternalcryptoauthukeypin)验证PIN码。

5. 操作执行完后，关闭资源，可参考[打开关闭资源](huks-extension-ability-general-operation.md#打开关闭资源)。

### 开发示例

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';

function StringToUint8Array(str: string) {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

// uid由调用方自己获取
let uid: number = 3511;

async function authUkeyPin(): Promise<void> {
  try {
    /* 1.假设已打开的资源如下 */
    const testResourceId = JSON.stringify({
      providerName: 'testProviderName',
      bundleName: 'com.example.cryptoapplication',
      abilityName: 'CryptoExtension',
      index: {
        key: 'testKey'
      } as ESObject
    });

    /* 2.构造参数 */
    const pin ='123456';
    const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [
      {
        tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_UID,
        value: uid
      }, {
        tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_UKEY_PIN,
        value: StringToUint8Array(pin)
      }
    ];

    /* 3.验证PIN码 */
    await huksExternalCrypto.authUkeyPin(testResourceId, extProperties)
      .then(() => {
        console.info('promise: authUkeyPin success.');
      }).catch((error: BusinessError) => {
        console.error(`promise: authUkeyPin failed, errCode: ${error.code}, errMsg: ${error.message}`);
      });
  } catch (error) {
    console.error('promise: authUkeyPin input arg invalid.');
  }
}

async function TestAuthUkeyPin() {
  await authUkeyPin();
}
```
<!--DelEnd-->