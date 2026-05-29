# @ohos.security.CryptoExtensionAbility (密钥扩展能力)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

模块提供外部密钥扩展能力，包括资源管理、PIN码认证管理、密码操作、通用操作等接口能力。

ExtensionAbility实现约束：
1. 设备管理，单个ExtensionAbility实现，最多支持10个UKey接入。
2. 句柄管理，针对同一个UKey资源（例如，容器下的密钥），支持应用维度资源句柄管理。
   - 支持多个OpenHarmony应用，打开同一个UKey密钥资源。例如：OpenHarmony应用1打开容器A后，OpenHarmony应用2也可以再次打开容器A。
   - 支持多个OpenHarmony应用，操作同一个UKey密钥资源。例如：OpenHarmony应用1操作容器A中的私钥签名后，OpenHarmony应用2也验证PIN码后，也可以操作容器A中的私钥进行签名，两者互不影响。
3. 密钥会话管理，支持三段式密钥管理操作，单次签名验签需通过[onInitSession](#cryptoextensionabilityoninitsession)/[onUpdateSession](#cryptoextensionabilityonupdatesession)/[onFinishSession](#cryptoextensionabilityonfinishsession)三个函数三步配合完成，需支持会话管理，缓存密钥会话状态。
   - init操作，初始化密钥会话，并返回会话句柄信息。
   - update操作，传入分组数据，对分组数据进行密码操作，更新密钥会话信息后，将中间数据（如果有）返回。
   - finish操作，对传入最后一段分组数据，进行密钥返回操作，并结束密钥会话，将最终结果返回。
4. 认证状态管理，支持应用维度的认证状态管理。针对同一个UKey中的应用A，OpenHarmony应用1验证UKey应用A的PIN码后，OpenHarmony应用2如果要访问UKey应用A，也需要进行PIN码认证操作。
5. 证书查询，支持根据证书类型，枚举所有证书或查询单个容器中的证书。

> **说明**
>
> 本模块首批接口从API version 22开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { huks, huksExternalCrypto, CryptoExtensionAbility } from '@kit.UniversalKeystoreKit';
```

## HuksCryptoExtensionResultCode

[HuksCryptoExtensionResult](#hukscryptoextensionresult)中的resultCode枚举值。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

| 名称 | 值 | 说明 |
| ------ | ---- | ------ |
| HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL | 34800000 | 密钥扩展错误。可能的原因：<br>1. 输入参数无效。<br>2. 密钥扩展出现无法解决的错误状态。 |
| HUKS_CRYPTO_EXTENSION_ERR_UKEY_NOT_EXIST | 34800001 | UKey不存在。可能的原因：<br>1. UKey已被移除。<br>2. 密钥扩展陷入错误的UKey状态。 |
| HUKS_CRYPTO_EXTENSION_ERR_UKEY_DRIVER_FAIL | 34800002 | UKey驱动出现未知错误。 |
| HUKS_CRYPTO_EXTENSION_ERR_PIN_NO_AUTH | 34800003 | UKey PIN码未认证，需要先认证UKey PIN码。 |
| HUKS_CRYPTO_EXTENSION_ERR_HANDLE_NOT_EXIST | 34800004 | 句柄不存在。可能的原因：<br>1. 句柄无效。<br>2. HUKS服务和密钥扩展的状态不一致。由于异常情况，HUKS服务持有的句柄未能释放。 |
| HUKS_CRYPTO_EXTENSION_ERR_HANDLE_UNAVAILABLE | 34800005 | 句柄不可用。可能的原因：<br>密钥扩展和UKey的状态不一致。 |
| HUKS_CRYPTO_EXTENSION_ERR_PIN_INCORRECT | 34800006 | UKey PIN码错误，需要检查输入的PIN码。 |
| HUKS_CRYPTO_EXTENSION_ERR_PIN_LOCKED | 34800007 | UKey PIN码被锁。可能的原因：<br>PIN码输入错误次数过多。 |

## HuksCryptoExtensionCertInfo

[HuksCryptoExtensionResult](#hukscryptoextensionresult)中的certs数组中的元素。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

| 名称 | 类型    | 只读 | 可选 | 说明  |
| ------ | --------- | ---- | ---- | ------ |
| purpose    | [certificateManager.CertificatePurpose](../apis-device-certificate-kit/js-apis-certManager.md#certificatepurpose22)  | 否   | 否   | 表示证书链对应密钥的使用类型。 |
| resourceId  | string | 否   | 否   | 资源ID。JSON格式，能够映射到UKey中的某个资源。 |
| cert  | Uint8Array | 否   | 否   | 证书。 |

## HuksCryptoExtensionResult

接口返回值的通用类型。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

| 名称 | 类型  | 只读 | 可选 | 说明 |
| ------ | ------ | ---- | ---- | ------ |
| resultCode  | number | 否   | 否   | 返回值的错误码。 |
| handle  | string | 否   | 是   | 资源句柄。 |
| authState  | number | 否   | 是   | 认证状态。 |
| retryCount  | number | 否   | 是   | 重试次数。 |
| certs  | Array<[HuksCryptoExtensionCertInfo](#hukscryptoextensioncertinfo)> | 否   | 是   | 证书。 |
| property  | Array<[huksExternalCrypto.HuksExternalCryptoParam](js-apis-huksExternalCrypto.md#huksexternalcryptoparam)> | 否   | 是   | 属性。 |
| outData  | Uint8Array | 否   | 是   | 返回的数据。 |
| resourceId | string | 否 | 是 | 返回的资源ID。<br>**起始版本：** 26.0.0<br>**模型约束：** 此接口仅可在Stage模型下使用。 |

## CryptoExtensionAbility.onOpenResource

onOpenResource(resourceId: string, params: Array\<huksExternalCrypto.HuksExternalCryptoParam>): Promise\<HuksCryptoExtensionResult>

根据参数中的resourceId，打开UKey的密钥资源。使用Promise异步回调。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型 | 必填 | 说明 |
| -------- | --------- | ---- | -------- |
| resourceId | string | 是   | 资源ID。 |
| params  | Array\<[huksExternalCrypto.HuksExternalCryptoParam](js-apis-huksExternalCrypto.md#huksexternalcryptoparam)> | 是   | 传入的参数，应用身份通过[HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag)参数携带。 |

**返回值：**

| 类型 | 说明 |
| ---------- | ----------- |
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise对象。当调用成功时，resultCode为0，handle携带资源句柄信息。调用失败时，resultCode携带错误码信息。<br>可能返回的错误码值：<br>34800000 密钥扩展错误。<br>34800001 UKey不存在。<br>34800002 UKey驱动错误。<br>34800004 句柄不存在。<br>具体含义可查询[HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode)。 |

**示例：**

```ts
import { huksExternalCrypto, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onOpenResource(resourceId: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
    // 解析resourceId，打开底层句柄，并映射为新的句柄返回。
    let result: HuksCryptoExtensionResult = {
      resultCode: 0,
      handle: "test handle"
    };

    // ...
    return Promise.resolve(result);
  }
}
```

## CryptoExtensionAbility.onCloseResource

onCloseResource(handle: string, params: Array\<huksExternalCrypto.HuksExternalCryptoParam>): Promise\<HuksCryptoExtensionResult>

根据参数中的handle，关闭UKey的密钥资源。使用Promise异步回调。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型 | 必填 | 说明  |
| -------- | ------ | ---- | ------ |
| handle | string | 是   | 会话句柄。  |
| params  | Array\<[huksExternalCrypto.HuksExternalCryptoParam](js-apis-huksExternalCrypto.md#huksexternalcryptoparam)> | 是 | 传入的参数，应用身份通过[HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag)参数携带。 |

**返回值：**

| 类型 | 说明 |
| ----------- | ------------- |
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise对象。当调用成功时，resultCode为0，表示关闭资源成功。调用失败时，resultCode携带错误码信息。<br>可能返回的错误码值：<br>34800000 密钥扩展错误。<br>34800002 UKey驱动错误。<br>34800004 句柄不存在。<br>34800005 句柄不可用。<br>具体含义可查询[HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode)。 |

**示例：**

```ts
import { huksExternalCrypto, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onCloseResource(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
    // 执行句柄关闭操作。如果需要关闭底层句柄，则执行关闭操作。
    const result: HuksCryptoExtensionResult = {
        resultCode: 0,
    };

    // ...
    return Promise.resolve(result);
  }
}
```

## CryptoExtensionAbility.onGetProperty

onGetProperty(handle: string, propertyId: string, params: Array\<huksExternalCrypto.HuksExternalCryptoParam>): Promise\<HuksCryptoExtensionResult>

根据参数中的handle和propertyId获取属性。使用Promise异步回调。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型  | 必填 | 说明  |
| -------- | ----- | ---- | ------|
| handle | string | 是   | 资源句柄。 |
| propertyId | string | 是   | 查找操作的属性名称，是GMT 0016-2023中定义的SKF接口名，要业务针对接口名适配。 |
| params  | Array\<[huksExternalCrypto.HuksExternalCryptoParam](js-apis-huksExternalCrypto.md#huksexternalcryptoparam)> | 是 | 传入的参数，应用身份通过[HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag)参数携带。 |

**返回值：**

| 类型    | 说明   |
| -------- | -----------|
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise对象。当调用成功时，resultCode为0，HuksCryptoExtensionResult的property成员非空，包含获取到的属性，由[HUKS_EXT_CRYPTO_TAG_EXTRA_DATA](js-apis-huksExternalCrypto.md#huksexternalcryptotag)参数携带。调用失败时，resultCode携带错误码信息。<br>可能返回的错误码值：<br>34800000 密钥扩展错误。<br>34800002 UKey驱动错误。<br>34800003 UKey PIN码未认证。<br>34800004 句柄不存在。<br>34800005 句柄不可用。<br>34800007 UKey PIN码被锁。<br>具体含义可查询[HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode)。 |

**示例：**

```ts
import { huksExternalCrypto, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onGetProperty(handle: string, propertyId: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
    // 按照propertyId执行相关函数，函数参数从params中获取。输出数据封装到返回值的property字段中，由HUKS_EXT_CRYPTO_TAG_EXTRA_DATA携带。
    const emptyArray: Array<huksExternalCrypto.HuksExternalCryptoParam> = [];
    const result: HuksCryptoExtensionResult = {
      resultCode: 0,
      property: emptyArray
    };

    // ...
    return Promise.resolve(result);
  }
}
```

## CryptoExtensionAbility.onSetProperty

onSetProperty(handle: string, propertyId: string, params: Array\<huksExternalCrypto.HuksExternalCryptoParam>): Promise\<HuksCryptoExtensionResult>

根据参数中的handle和propertyId设置属性。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型  | 必填 | 说明  |
| -------- | ----- | ---- | ------|
| handle | string | 是   | 资源句柄。 |
| propertyId | string | 是   | 设置操作的属性名称，推荐使用GMT 0016-2023中定义的SKF接口名作为属性ID。 |
| params  | Array\<[huksExternalCrypto.HuksExternalCryptoParam](js-apis-huksExternalCrypto.md#huksexternalcryptoparam)> | 是 | 传入的参数，包含与propertyId相关的操作参数。应用身份通过[HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag)参数携带。 |

**返回值：**

| 类型    | 说明   |
| -------- | -----------|
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise对象。当调用成功时，resultCode为0，表示设置属性成功。调用失败时，resultCode携带错误码信息。<br>可能返回的错误码值：<br>34800000 密钥扩展错误。可能的原因：<br>1. 输入参数无效。<br>2. 密钥扩展出现无法解决的错误状态。<br>34800002 Ukey驱动错误。<br>34800003 Ukey PIN码未认证，需要先认证Ukey PIN码。<br>34800004 句柄不存在。可能的原因：<br>1. 句柄无效。<br>2. HUKS服务和密钥扩展的状态不一致。由于异常情况，HUKS服务持有的句柄未能释放。<br>34800005 句柄不可用。可能的原因：<br>密钥扩展和Ukey的状态不一致。<br>34800007 Ukey PIN码被锁。可能的原因：<br>PIN码输入错误次数过多。<br>具体含义可查询[HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode)。 |

**示例：**

```ts
import { huksExternalCrypto, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onSetProperty(handle: string, propertyId: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
    // 按照propertyId执行相关设置操作，操作参数从params中获取。
    const result: HuksCryptoExtensionResult = {
      resultCode: 0
    };

    // ...
    return Promise.resolve(result);
  }
}
```

## CryptoExtensionAbility.onAuthUkeyPin

onAuthUkeyPin(handle: string, params: Array\<huksExternalCrypto.HuksExternalCryptoParam>): Promise\<HuksCryptoExtensionResult>

请求UKey认证PIN码。使用Promise异步回调。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型   | 必填 | 说明   |
| ------ | ------ | ---- | ------- |
| handle | string  | 是   | 资源句柄。   |
| params  | Array\<[huksExternalCrypto.HuksExternalCryptoParam](js-apis-huksExternalCrypto.md#huksexternalcryptoparam)> | 是   | 传入的参数，应用身份通过[HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag)参数携带。 |

**返回值：**

| 类型 | 说明 |
| -------- | --------|
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise对象。当调用成功时，resultCode为0，authState非0，表示认证请求成功。调用失败时，resultCode携带错误码信息。<br>可能返回的错误码值：<br>34800000 密钥扩展错误。<br>34800002 UKey驱动错误。<br>34800004 句柄不存在。<br>34800005 句柄不可用。<br>34800006 UKey PIN码错误。<br>34800007 UKey PIN码被锁。<br>具体含义可查询[HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode)。 |

**示例：**

```ts
import { huksExternalCrypto, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onAuthUkeyPin(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
    // 执行PIN码认证操作，并且维护应用的PIN码认证状态。
    const result: HuksCryptoExtensionResult = {
      resultCode: 0,
      authState: 1
    };

    // ...
    return Promise.resolve(result);
  }
}
```

## CryptoExtensionAbility.onGetUkeyPinAuthState

onGetUkeyPinAuthState(handle: string, params: Array\<huksExternalCrypto.HuksExternalCryptoParam>): Promise\<HuksCryptoExtensionResult>

获取UKey的PIN码认证状态。使用Promise异步回调。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型  | 必填 | 说明   |
| -------- | ------- | ---- | -------|
| handle | string | 是   | 资源句柄。 |
| params  | Array\<[huksExternalCrypto.HuksExternalCryptoParam](js-apis-huksExternalCrypto.md#huksexternalcryptoparam)> | 是   | 传入的参数，应用身份通过[HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag)参数携带。 |

**返回值：**

| 类型   | 说明  |
| -------- | ------- |
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise对象。当调用成功时，resultCode为0，HuksCryptoExtensionResult的authState成员非空，为获取的PIN码认证状态。调用失败时，resultCode携带错误码信息。<br>可能返回的错误码值：<br>34800000 密钥扩展错误。<br>34800002 UKey驱动错误。<br>34800004 句柄不存在。<br>34800005 句柄不可用。<br>具体含义可查询[HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode)。 |

**示例：**

```ts
import { huksExternalCrypto, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onGetUkeyPinAuthState(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
    // 查询PIN码认证状态。
    const result: HuksCryptoExtensionResult = {
      resultCode: 0,
      authState: 1
    };

    // ...
    return Promise.resolve(result);
  }
}
```

## CryptoExtensionAbility.onClearUkeyPinAuthState

onClearUkeyPinAuthState(handle: string, params: Array\<huksExternalCrypto.HuksExternalCryptoParam>): Promise\<HuksCryptoExtensionResult>

清除应用维度PIN码的认证状态。使用Promise异步回调。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型   | 必填 | 说明 |
| -------- | ----- | ---- | ------|
| handle  | string | 是   | 会话句柄。 |
| params  | Array\<[huksExternalCrypto.HuksExternalCryptoParam](js-apis-huksExternalCrypto.md#huksexternalcryptoparam)> | 是   | 传入的参数，应用身份通过[HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag)参数携带。 |

**返回值：**

| 类型 | 说明 |
| ------------ | ---------|
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise对象。当调用成功时，resultCode为0，表示清除PIN码认证状态成功。调用失败时，resultCode携带错误码信息。<br>可能返回的错误码值：<br>34800000 密钥扩展错误。<br>34800002 UKey驱动错误。<br>34800004 句柄不存在。<br>34800005 句柄不可用。<br>具体含义可查询[HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode)。 |

**示例：**

```ts
import { huksExternalCrypto, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onClearUkeyPinAuthState(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
    const result: HuksCryptoExtensionResult = {
      resultCode: 0
    };

    // ...
    return Promise.resolve(result);
  }
}
```

## CryptoExtensionAbility.onInitSession

onInitSession(handle: string, params: huks.HuksOptions): Promise\<HuksCryptoExtensionResult>

三段式初始化密钥会话操作。使用Promise异步回调。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型 | 必填 | 说明 |
| -------- | ----- | ---- | ------- |
| handle | string                      | 是   | 资源句柄。|
| params  | [huks.HuksOptions](js-apis-huks.md#huksoptions)  | 是   | 传入的参数，应用身份通过[HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag)参数携带。 |

**返回值：**

| 类型 | 说明 |
| --------- | ---------|
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise对象。当调用成功时，resultCode为0，handle成员非空。调用失败时，resultCode携带错误码信息。<br>可能返回的错误码值：<br>34800000 密钥扩展错误。<br>34800002 UKey驱动错误。<br>34800003 UKey PIN码未认证。<br>34800004 句柄不存在。<br>34800005 句柄不可用。<br>34800007 UKey PIN码被锁。<br>具体含义可查询[HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode)。 |

**示例：**

```ts
import { huks, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onInitSession(handle: string, params: huks.HuksOptions): Promise<HuksCryptoExtensionResult> {
    const result: HuksCryptoExtensionResult = {
      resultCode: 0,
      handle: "test handle"
    };

    // ...
    return Promise.resolve(result);
  }
}
```

## CryptoExtensionAbility.onUpdateSession

onUpdateSession(initHandle: string, params: huks.HuksOptions): Promise\<HuksCryptoExtensionResult>

三段式密钥会话更新数据操作。使用Promise异步回调。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型  | 必填 | 说明 |
| -------- | ----- | ---- | ------|
| initHandle | string | 是   | 资源句柄。   |
| params  | [huks.HuksOptions](js-apis-huks.md#huksoptions)  | 是   | 传入的参数，应用身份通过[HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag)参数携带。 |

**返回值：**

| 类型 | 说明 |
| --------- | ---------|
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise对象。当调用成功时，resultCode为0。调用失败时，resultCode携带错误码信息。<br>可能返回的错误码值：<br>34800000 密钥扩展错误。<br>34800002 UKey驱动错误。<br>34800003 UKey PIN码未认证。<br>34800004 句柄不存在。<br>34800005 句柄不可用。<br>34800007 UKey PIN码被锁。<br>具体含义可查询[HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode)。 |

**示例：**

```ts
import { huks, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onUpdateSession(initHandle: string, params: huks.HuksOptions): Promise<HuksCryptoExtensionResult> {
    let outBuffer: Uint8Array = new Uint8Array(1024);
    const result: HuksCryptoExtensionResult = {
      resultCode: 0,
      outData: outBuffer
    };

    // ...
    return Promise.resolve(result);
  }
}
```

## CryptoExtensionAbility.onFinishSession

onFinishSession(initHandle: string, params: huks.HuksOptions): Promise\<HuksCryptoExtensionResult>

三段式密钥会话结束操作。使用Promise异步回调。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型 | 必填 | 说明  |
| -------- | -------- | ---- | --------- |
| initHandle | string  | 是   | 资源句柄。 |
| params  | [huks.HuksOptions](js-apis-huks.md#huksoptions)  | 是   | 传入的参数，应用身份可通过[HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag)参数携带，还包括算法参数（算法类型、填充模式等）。 |

**返回值：**

| 类型 | 说明 |
| ------- | ---------- |
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise对象。当调用成功时，resultCode为0。调用失败时，resultCode携带错误码信息。<br>可能返回的错误码值：<br>34800000 密钥扩展错误。<br>34800002 UKey驱动错误。<br>34800003 UKey PIN码未认证。<br>34800004 句柄不存在。<br>34800005 句柄不可用。<br>34800007 UKey PIN码被锁。<br>具体含义可查询[HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode)。 |

**示例：**

```ts
import { huks, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onFinishSession(initHandle: string, params: huks.HuksOptions): Promise<HuksCryptoExtensionResult> {
    let outBuffer: Uint8Array = new Uint8Array(1024);
    const result: HuksCryptoExtensionResult = {
      resultCode: 0,
      outData: outBuffer
    };

    // ...
    return Promise.resolve(result);
  }
}
```

## CryptoExtensionAbility.onExportCertificate

onExportCertificate(resourceId: string, params?: Array\<huksExternalCrypto.HuksExternalCryptoParam>): Promise\<HuksCryptoExtensionResult>

查询指定resourceId下的证书。使用Promise异步回调。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型  | 必填 | 说明 |
| -------- | ---------- | ---- | --------- |
| resourceId | string | 是   | 资源ID。会附带在[HuksCryptoExtensionCertInfo](#hukscryptoextensioncertinfo)中。 |
| params  | Array\<[huksExternalCrypto.HuksExternalCryptoParam](js-apis-huksExternalCrypto.md#huksexternalcryptoparam)>  | 否   | 操作属性。默认获取签名类型的证书，也可以通过参数[HUKS_EXT_CRYPTO_TAG_PURPOSE](js-apis-huksExternalCrypto.md#huksexternalcryptotag)指定获取证书类型，支持的类型包括签名验签、加解密等。 |

**返回值：**

| 类型  | 说明  |
| ---------- | --------- |
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise对象。当调用成功时，certs成员非空，包含获取的单本证书。调用失败时，resultCode携带错误码信息。<br>可能返回的错误码值：<br>34800000 密钥扩展错误。<br>34800001 UKey不存在。<br>34800002 UKey驱动错误。<br>34800004 句柄不存在。<br>具体含义可查询[HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode)。 |

**示例：**

```ts
import { huksExternalCrypto, CryptoExtensionAbility, HuksCryptoExtensionResult,
  HuksCryptoExtensionCertInfo } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onExportCertificate(resourceId: string, params?: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
    const certInfoSetArray: Array<HuksCryptoExtensionCertInfo> = []
    const result: HuksCryptoExtensionResult = {
      resultCode: 0,
      certs: certInfoSetArray
    };

    // ...
    return Promise.resolve(result);
  }
}
```

## CryptoExtensionAbility.onEnumCertificates

onEnumCertificates(params?: Array\<huksExternalCrypto.HuksExternalCryptoParam>): Promise\<HuksCryptoExtensionResult>

枚举Extension下所有UKey设备的证书信息。使用Promise异步回调。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型 | 必填 | 说明   |
| -------- | -----| ---- | ---------- |
| params  | Array\<[huksExternalCrypto.HuksExternalCryptoParam](js-apis-huksExternalCrypto.md#huksexternalcryptoparam)>  | 否   | 操作属性。默认获取签名类型的[证书](../../security/DeviceCertificateKit/certManager-overview.md)，也可以通过参数[HUKS_EXT_CRYPTO_TAG_PURPOSE](js-apis-huksExternalCrypto.md#huksexternalcryptotag)指定获取证书类型，支持的类型包括签名验签、加解密等。 |

**返回值：**

| 类型 | 说明 |
| ---------- | ---------|
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise对象。当调用成功时，certs成员非空，包含获取的所有证书。调用失败时，resultCode携带错误码信息。<br>可能返回的错误码值：<br>34800000 密钥扩展错误。<br>34800001 UKey不存在。<br>34800002 UKey驱动错误。<br>具体含义可查询[HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode)。 |

**示例：**

```ts
import { huksExternalCrypto, CryptoExtensionAbility, HuksCryptoExtensionResult,
  HuksCryptoExtensionCertInfo } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onEnumCertificates(params?: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
    const certInfoSetArray: Array<HuksCryptoExtensionCertInfo> = []
    const result: HuksCryptoExtensionResult = {
      resultCode: 0,
      certs: certInfoSetArray
    };

    // ...
    return Promise.resolve(result);
  }
}
```

## CryptoExtensionAbility.onGetResourceId

onGetResourceId(params: huksExternalCrypto.HuksExternalCryptoParam[]):Promise&lt;HuksCryptoExtensionResult&gt;

获取外部扩展设备内的资源ID。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型 | 必填 | 说明 |
| -------- | --------- | ---- | -------- |
| params  | [huksExternalCrypto.HuksExternalCryptoParam](js-apis-huksExternalCrypto.md#huksexternalcryptoparam)[] | 是   | 获取资源ID所需的属性参数。必选TAG包括：[HUKS_EXT_CRYPTO_TAG_RESOURCE_INFO](js-apis-huksExternalCrypto.md#huksexternalcryptotag)（厂商自定义的资源信息）、[HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag)（调用方身份）。 |

**返回值：**

| 类型 | 说明 |
| ---------- | ----------- |
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise对象。当调用成功时，resultCode为0，resourceId携带资源ID信息。调用失败时，resultCode携带错误码信息。<br>可能返回的错误码值：<br>34800000 密钥扩展错误。<br>具体含义可查询[HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode)。 |

**示例：**

```ts
import { huksExternalCrypto, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onGetResourceId(params: huksExternalCrypto.HuksExternalCryptoParam[]): Promise<HuksCryptoExtensionResult> {
    const result: HuksCryptoExtensionResult = {
      resultCode: 0,
      resourceId: "test resourceId"
    };

    // ...
    return Promise.resolve(result);
  }
}
```

## CryptoExtensionAbility.onImportCertificate

onImportCertificate(handle: string, params: huksExternalCrypto.HuksExternalCryptoParam[], certInfo: HuksCryptoExtensionCertInfo): Promise&lt;HuksCryptoExtensionResult&gt;

导入指定资源句柄的证书。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型  | 必填 | 说明  |
| -------- | ----- | ---- | ------|
| handle | string | 是   | 导入证书的资源句柄。 |
| params  | [huksExternalCrypto.HuksExternalCryptoParam](js-apis-huksExternalCrypto.md#huksexternalcryptoparam)[] | 是 | 导入证书所需的属性参数。 |
| certInfo | [HuksCryptoExtensionCertInfo](#hukscryptoextensioncertinfo) | 是   | 待导入的证书信息。需指定证书类型（purpose）。 |

**返回值：**

| 类型    | 说明   |
| -------- | -----------|
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise对象。当调用成功时，resultCode为0，表示导入证书成功。调用失败时，resultCode携带错误码信息，errInfo携带详细错误信息。<br>可能返回的错误码值：<br>34800000 密钥扩展错误。<br>34800001 UKey不存在。<br>34800002 UKey驱动错误。<br>34800004 句柄不存在。<br>34800005 句柄不可用。<br>具体含义可查询[HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode)。 |

**示例：**

```ts
import { huksExternalCrypto, CryptoExtensionAbility, HuksCryptoExtensionResult,
  HuksCryptoExtensionCertInfo } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onImportCertificate(handle: string, params: huksExternalCrypto.HuksExternalCryptoParam[],
      certInfo: HuksCryptoExtensionCertInfo): Promise<HuksCryptoExtensionResult> {
    const result: HuksCryptoExtensionResult = {
      resultCode: 0
    };

    // ...
    return Promise.resolve(result);
  }
}
```

## CryptoExtensionAbility.onGenerateKeyItem

onGenerateKeyItem(handle: string, params: huks.HuksParam[]): Promise&lt;HuksCryptoExtensionResult&gt;

用于在扩展设备内生成密钥对。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型  | 必填 | 说明  |
| -------- | ----- | ---- | ------|
| handle | string | 是   | 待生成密钥的资源句柄。 |
| params  | [huks.HuksParam](js-apis-huks.md#huksparam)[] | 是 | 密钥生成操作的属性参数。必选TAG：[HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag)（调用方身份）。 |

**返回值：**

| 类型    | 说明   |
| -------- | -----------|
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise对象。当调用成功时，resultCode为0，表示生成密钥成功。调用失败时，resultCode携带错误码信息。<br>可能返回的错误码值：<br>34800000 密钥扩展错误。<br>34800001 UKey不存在。<br>34800002 UKey驱动错误。<br>34800004 句柄不存在。<br>34800005 句柄不可用。<br>具体含义可查询[HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode)。 |

**示例：**

```ts
import { huks, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onGenerateKeyItem(handle: string, params: huks.HuksParam[]): Promise<HuksCryptoExtensionResult> {
    // 解析可选参数
    let algorithm: huks.HuksKeyAlg | undefined = params.find(
      param => param.tag === huks.HuksTag.HUKS_TAG_ALGORITHM)?.value as huks.HuksKeyAlg;
    let keySize: huks.HuksKeySize | undefined = params.find(
      param => param.tag === huks.HuksTag.HUKS_TAG_KEY_SIZE)?.value as huks.HuksKeySize;
    let purpose: huks.HuksKeyPurpose | undefined = params.find(
      param => param.tag === huks.HuksTag.HUKS_TAG_PURPOSE)?.value as huks.HuksKeyPurpose;

    // 如未传入参数，设置默认值
    if (algorithm === undefined) {
      algorithm = huks.HuksKeyAlg.HUKS_ALG_RSA; // 默认RSA算法
    }
    if (keySize === undefined) {
      keySize = huks.HuksKeySize.HUKS_RSA_KEY_SIZE_2048; // 默认2048位
    }
    if (purpose === undefined) {
      purpose = huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_SIGN; // 默认签名用途
    }

    const result: HuksCryptoExtensionResult = {
      resultCode: 0
    };

    // ...
    return Promise.resolve(result);
  }
}
```

## CryptoExtensionAbility.onExportKeyItem

onExportKeyItem(handle: string, params: huks.HuksParam[]): Promise&lt;HuksCryptoExtensionResult&gt;

用于导出指定密钥的公钥。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型  | 必填 | 说明  |
| -------- | ----- | ---- | ------|
| handle | string | 是   | 待导出公钥的资源句柄。 |
| params  | [huks.HuksParam](js-apis-huks.md#huksparam)[] | 是 | 导出公钥操作的属性参数。必选TAG：[HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag)（调用方身份）。 |

**返回值：**

| 类型    | 说明   |
| -------- | -----------|
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise对象。当调用成功时，resultCode为0，outData携带导出的公钥数据。调用失败时，resultCode携带错误码信息，errInfo携带详细错误信息。<br>可能返回的错误码值：<br>34800000 密钥扩展错误。<br>34800001 UKey不存在。<br>34800002 UKey驱动错误。<br>34800004 句柄不存在。<br>34800005 句柄不可用。<br>具体含义可查询[HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode)。 |

**示例：**

```ts
import { huks, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onExportKeyItem(handle: string, params: huks.HuksParam[]): Promise<HuksCryptoExtensionResult> {
    // 解析可选参数，推荐传入密钥用途
    let purpose: huks.HuksKeyPurpose | undefined = params.find(
      param => param.tag === huks.HuksTag.HUKS_TAG_PURPOSE)?.value as huks.HuksKeyPurpose;

    // 如未传入用途参数，设置默认值（推荐默认签名用途）
    if (purpose === undefined) {
      purpose = huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_SIGN;
    }

    let pubKey: Uint8Array = new Uint8Array(1024);
    const result: HuksCryptoExtensionResult = {
      resultCode: 0,
      outData: pubKey
    };

    // ...
    return Promise.resolve(result);
  }
}
```

## CryptoExtensionAbility.onImportWrappedKeyItem

onImportWrappedKeyItem(handle: string, wrappedHandle: string, params: huks.HuksParam[], wrappedKey: Uint8Array): Promise&lt;HuksCryptoExtensionResult&gt;

用于导入加密封装的密钥对。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型  | 必填 | 说明  |
| -------- | ----- | ---- | ------|
| handle | string | 是   | 待导入密钥的资源句柄。 |
| wrappedHandle | string | 是   | 用于解封导入密钥的密钥资源句柄。 |
| params  | [huks.HuksParam](js-apis-huks.md#huksparam)[] | 是 | 导入封装密钥操作的属性参数。必选TAG：[HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag)（调用方身份）。 |
| wrappedKey | Uint8Array | 是   | 封装密钥数据，格式由密钥扩展定义。 |

**返回值：**

| 类型    | 说明   |
| -------- | -----------|
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise对象。当调用成功时，resultCode为0，表示导入密钥成功。调用失败时，resultCode携带错误码信息，errInfo携带详细错误信息。<br>可能返回的错误码值：<br>34800000 密钥扩展错误。<br>34800001 UKey不存在。<br>34800002 UKey驱动错误。<br>34800004 句柄不存在。<br>34800005 句柄不可用。<br>具体含义可查询[HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode)。 |

**示例：**

```ts
import { huks, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onImportWrappedKeyItem(handle: string, wrappedHandle: string, params: huks.HuksParam[],
      wrappedKey: Uint8Array): Promise<HuksCryptoExtensionResult> {
    // 解析可选参数
    let algorithm: huks.HuksKeyAlg | undefined = params.find(
      param => param.tag === huks.HuksTag.HUKS_TAG_ALGORITHM)?.value as huks.HuksKeyAlg;
    let keySize: huks.HuksKeySize | undefined = params.find(
      param => param.tag === huks.HuksTag.HUKS_TAG_KEY_SIZE)?.value as huks.HuksKeySize;
    let purpose: huks.HuksKeyPurpose | undefined = params.find(
      param => param.tag === huks.HuksTag.HUKS_TAG_PURPOSE)?.value as huks.HuksKeyPurpose;

    // 如未传入参数，设置默认值
    if (algorithm === undefined) {
      algorithm = huks.HuksKeyAlg.HUKS_ALG_RSA;
    }
    if (keySize === undefined) {
      keySize = huks.HuksKeySize.HUKS_RSA_KEY_SIZE_2048;
    }
    if (purpose === undefined) {
      purpose = huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT;
    }

    const result: HuksCryptoExtensionResult = {
      resultCode: 0
    };

    // ...
    return Promise.resolve(result);
  }
}
```
