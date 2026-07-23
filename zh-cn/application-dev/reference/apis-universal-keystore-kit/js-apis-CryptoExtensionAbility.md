# @ohos.security.CryptoExtensionAbility (密钥扩展能力)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

模块提供外部密钥扩展能力，包括资源管理、PIN码认证管理、密码操作、通用操作等接口能力。

ExtensionAbility功能与约束：
1. 设备管理，单个ExtensionAbility实现，最多支持10个UKey接入。
2. 句柄管理，针对同一个UKey资源（例如，容器下的密钥），支持应用维度资源句柄管理。
   - 支持多个OpenHarmony应用，打开同一个UKey密钥资源。例如：OpenHarmony应用1打开容器A后，OpenHarmony应用2也可以再次打开容器A。
   - 支持多个OpenHarmony应用，操作同一个UKey密钥资源。例如：OpenHarmony应用1操作容器A中的私钥签名后，OpenHarmony应用2也验证PIN码后，也可以操作容器A中的私钥进行签名，两者互不影响。
3. 密钥会话管理，支持三段式密钥管理操作，单次签名验签需通过[onInitSession](#oninitsession)/[onUpdateSession](#onupdatesession)/[onFinishSession](#onfinishsession)三个函数三步配合完成，需支持会话管理，缓存密钥会话状态。
   - init操作，初始化密钥会话，并返回会话句柄信息。
   - update操作，传入分组数据，对分组数据进行密码操作，更新密钥会话信息后，将中间数据（如果有）返回。
   - finish操作，对传入最后一段分组数据，进行密钥返回操作，并结束密钥会话，将最终结果返回。
4. 认证状态管理，支持应用维度的认证状态管理。针对同一个UKey中的应用A，OpenHarmony应用1验证UKey应用A的PIN码后，OpenHarmony应用2如果要访问UKey应用A，也需要进行PIN码认证操作。
5. 证书查询，支持根据证书类型，枚举所有证书或查询单个容器中的证书。

> **说明**
>
> 本模块首批接口从API version 22开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 约束限制

CryptoExtensionAbility作为密钥管理扩展能力，为减少安全攻击面，保障CryptoExtensionAbility合理实现，系统对网络、蓝牙、位置等能力进行管控，不支持部分模块的引用，详情请参考[附录](#附录)。

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
| HUKS_CRYPTO_EXTENSION_ERR_PIN_NO_AUTH | 34800003 | UKey PIN码未认证，需要先通过[onAuthUkeyPin](#onauthukeypin)认证UKey PIN码。 |
| HUKS_CRYPTO_EXTENSION_ERR_HANDLE_NOT_EXIST | 34800004 | 句柄不存在。可能的原因：<br>1. 句柄无效。<br>2. HUKS服务和密钥扩展的状态不一致。由于异常情况，HUKS服务持有的句柄未能释放。 |
| HUKS_CRYPTO_EXTENSION_ERR_HANDLE_UNAVAILABLE | 34800005 | 句柄不可用。可能的原因：<br>密钥扩展和UKey的状态不一致。 |
| HUKS_CRYPTO_EXTENSION_ERR_PIN_INCORRECT | 34800006 | UKey PIN码错误，需要检查输入的PIN码。 |
| HUKS_CRYPTO_EXTENSION_ERR_PIN_LOCKED | 34800007 | UKey PIN码被锁定。可能的原因：<br>PIN码输入错误次数过多。 |

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
| retryCount  | number | 否   | 是   | 重试次数，表示PIN码认证剩余可用次数，为0时表示无剩余重试机会。 |
| certs  | Array<[HuksCryptoExtensionCertInfo](#hukscryptoextensioncertinfo)> | 否   | 是   | 证书。 |
| property  | Array<[huksExternalCrypto.HuksExternalCryptoParam](js-apis-huksExternalCrypto.md#huksexternalcryptoparam)> | 否   | 是   | 属性。 |
| outData  | Uint8Array | 否   | 是   | 返回的数据。 |
| resourceId | string | 否 | 是 | 返回的资源ID。默认值为空。<br>**起始版本：** 26.0.0<br>**模型约束：** 此接口仅可在Stage模型下使用。 |
| errInfo | [huksExternalCrypto.HuksExternalErrorInfo](js-apis-huksExternalCrypto.md#huksexternalerrorinfo) | 否 | 是 | 返回的详细错误信息。默认值为{0,""}。<br>**起始版本：** 26.0.0<br>**模型约束：** 此接口仅可在Stage模型下使用。 |

## HuksCryptoExtensionParam

密钥扩展操作参数，用于指定操作的属性标签和对应值。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称 | 类型  | 只读 | 可选 | 说明 |
| ------ | ------ | ---- | ---- | ------ |
| tag  | [huksExternalCrypto.HuksExternalCryptoTag](js-apis-huksExternalCrypto.md#huksexternalcryptotag) \| [huks.HuksTag](js-apis-huks.md#hukstag) \| number | 否   | 否   | 标签。 |
| value  | boolean \| number \| bigint \| Uint8Array | 否   | 否   | 标签对应值。 |

## HuksCryptoExtensionParams

密钥扩展操作参数集合，用于传递操作所需的属性和输入数据。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称 | 类型                                | 只读 | 可选 | 说明         |
| ------ | ----------------------------------- | ---- | ---- | ------------ |
| properties | [HuksCryptoExtensionParam](#hukscryptoextensionparam)[] | 否   | 否   | 属性，用于存储HuksCryptoExtensionParam的数组。默认为undefined。 |
| inData     | Uint8Array        | 否   | 是   | 输入数据。默认为undefined。 |

## CryptoExtensionAbility

密钥扩展能力类，提供外部密钥管理扩展所需接口定义，包括打开/关闭资源、PIN码认证管理、密钥会话操作、证书管理、密钥生成与导入、通用操作等接口能力。驱动厂商需继承CryptoExtensionAbility并实现相关接口，通过[registerProvider](js-apis-huksExternalCrypto.md#huksexternalcryptoregisterprovider)完成能力注册后，由HUKS和证书管理将对应的密钥管理扩展能力开放给应用使用。

CryptoExtensionAbility可以隔离不同的UKey驱动厂商实现的差异。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

### onOpenResource

onOpenResource(resourceId: string, params: Array\<huksExternalCrypto.HuksExternalCryptoParam> | HuksCryptoExtensionParam[]): Promise\<HuksCryptoExtensionResult>

根据参数中的resourceId，打开UKey的密钥资源。使用Promise异步回调。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型 | 必填 | 说明 |
| -------- | --------- | ---- | -------- |
| resourceId | string | 是   | 资源ID。 |
| params  | Array\<[huksExternalCrypto.HuksExternalCryptoParam](js-apis-huksExternalCrypto.md#huksexternalcryptoparam)> \| [HuksCryptoExtensionParam](#hukscryptoextensionparam)[] | 是   | 传入的参数，应用身份通过[HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag)参数携带。 |

**返回值：**

| 类型 | 说明 |
| ---------- | ----------- |
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise对象。当调用成功时，resultCode为0，handle携带资源句柄信息。调用失败时，resultCode携带错误码信息。<br>可能返回的错误码值：<br>34800000 密钥扩展错误。<br>34800001 UKey不存在。<br>34800002 UKey驱动错误。<br>34800004 句柄不存在。<br>具体含义可查询[HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode)。 |

**示例：**

```ts
import { huksExternalCrypto, HuksCryptoExtensionParam, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onOpenResource(resourceId: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> | HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult> {
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

### onCloseResource

onCloseResource(handle: string, params: Array\<huksExternalCrypto.HuksExternalCryptoParam> | HuksCryptoExtensionParam[]): Promise\<HuksCryptoExtensionResult>

根据参数中的handle，关闭UKey的密钥资源。使用Promise异步回调。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型 | 必填 | 说明  |
| -------- | ------ | ---- | ------ |
| handle | string | 是   | 会话句柄。  |
| params  | Array\<[huksExternalCrypto.HuksExternalCryptoParam](js-apis-huksExternalCrypto.md#huksexternalcryptoparam)> \| [HuksCryptoExtensionParam](#hukscryptoextensionparam)[] | 是 | 传入的参数，应用身份通过[HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag)参数携带。 |

**返回值：**

| 类型 | 说明 |
| ----------- | ------------- |
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise对象。当调用成功时，resultCode为0，表示关闭资源成功。调用失败时，resultCode携带错误码信息。<br>可能返回的错误码值：<br>34800000 密钥扩展错误。<br>34800002 UKey驱动错误。<br>34800004 句柄不存在。<br>34800005 句柄不可用。<br>具体含义可查询[HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode)。 |

**示例：**

```ts
import { huksExternalCrypto, HuksCryptoExtensionParam, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onCloseResource(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> | HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult> {
    // 执行句柄关闭操作。如果需要关闭底层句柄，则执行关闭操作。
    const result: HuksCryptoExtensionResult = {
        resultCode: 0,
    };

    // ...
    return Promise.resolve(result);
  }
}
```

### onGetProperty

onGetProperty(handle: string, propertyId: string, params: Array\<huksExternalCrypto.HuksExternalCryptoParam> | HuksCryptoExtensionParam[]): Promise\<HuksCryptoExtensionResult>

根据参数中的handle和propertyId获取属性。使用Promise异步回调。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型  | 必填 | 说明  |
| -------- | ----- | ---- | ------|
| handle | string | 是   | 资源句柄。 |
| propertyId | string | 是   | 查找操作的属性名称，是GMT 0016-2023中定义的SKF接口名，要业务针对接口名适配。 |
| params  | Array\<[huksExternalCrypto.HuksExternalCryptoParam](js-apis-huksExternalCrypto.md#huksexternalcryptoparam)> \| [HuksCryptoExtensionParam](#hukscryptoextensionparam)[] | 是 | 传入的参数，应用身份通过[HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag)参数携带。 |

**返回值：**

| 类型    | 说明   |
| -------- | -----------|
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise对象。当调用成功时，resultCode为0，HuksCryptoExtensionResult的property成员非空，包含获取到的属性，由[HUKS_EXT_CRYPTO_TAG_EXTRA_DATA](js-apis-huksExternalCrypto.md#huksexternalcryptotag)参数携带。调用失败时，resultCode携带错误码信息。<br>可能返回的错误码值：<br>34800000 密钥扩展错误。<br>34800002 UKey驱动错误。<br>34800003 UKey PIN码未认证。<br>34800004 句柄不存在。<br>34800005 句柄不可用。<br>34800007 UKey PIN码被锁定。<br>具体含义可查询[HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode)。 |

**示例：**

```ts
import { huksExternalCrypto, HuksCryptoExtensionParam, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onGetProperty(handle: string, propertyId: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> | HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult> {
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

### onSetProperty

onSetProperty(handle: string, propertyId: string, params: HuksCryptoExtensionParam[]): Promise\<HuksCryptoExtensionResult>

根据参数中的handle和propertyId设置属性。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型  | 必填 | 说明  |
| -------- | ----- | ---- | ------|
| handle | string | 是   | 资源句柄。 |
| propertyId | string | 是   | 设置操作的属性名称，推荐使用GMT 0016-2023中定义的SKF接口名作为属性ID。 |
| params  | [HuksCryptoExtensionParam](#hukscryptoextensionparam)[] | 是 | 传入的参数，包含与propertyId相关的操作参数。应用身份通过[HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag)参数携带。 |

**返回值：**

| 类型    | 说明   |
| -------- | -----------|
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise对象。当调用成功时，resultCode为0，表示设置属性成功。调用失败时，resultCode携带错误码信息。<br>可能返回的错误码值：<br>34800000 密钥扩展错误。可能的原因：<br>1. 输入参数无效。<br>2. 密钥扩展出现无法解决的错误状态。<br>34800002 UKey驱动错误。<br>34800003 UKey PIN码未认证，需要先认证UKey PIN码。<br>34800004 句柄不存在。可能的原因：<br>1. 句柄无效。<br>2. HUKS服务和密钥扩展的状态不一致。由于异常情况，HUKS服务持有的句柄未能释放。<br>34800005 句柄不可用。可能的原因：<br>密钥扩展和UKey的状态不一致。<br>34800007 UKey PIN码被锁定。可能的原因：<br>PIN码输入错误次数过多。<br>具体含义可查询[HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode)。 |

**示例：**

```ts
import { HuksCryptoExtensionParam, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onSetProperty(handle: string, propertyId: string, params: HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult> {
    // 按照propertyId执行相关设置操作，操作参数从params中获取。
    const result: HuksCryptoExtensionResult = {
      resultCode: 0
    };

    // ...
    return Promise.resolve(result);
  }
}
```

### onAuthUkeyPin

onAuthUkeyPin(handle: string, params: Array\<huksExternalCrypto.HuksExternalCryptoParam> | HuksCryptoExtensionParam[]): Promise\<HuksCryptoExtensionResult>

请求UKey认证PIN码。使用Promise异步回调。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型   | 必填 | 说明   |
| ------ | ------ | ---- | ------- |
| handle | string  | 是   | 资源句柄。   |
| params  | Array\<[huksExternalCrypto.HuksExternalCryptoParam](js-apis-huksExternalCrypto.md#huksexternalcryptoparam)> \| [HuksCryptoExtensionParam](#hukscryptoextensionparam)[] | 是   | 传入的参数，应用身份通过[HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag)参数携带。 |

**返回值：**

| 类型 | 说明 |
| -------- | --------|
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise对象。当调用成功时，resultCode为0，authState非0，表示认证请求成功。调用失败时，resultCode携带错误码信息。<br>可能返回的错误码值：<br>34800000 密钥扩展错误。<br>34800002 UKey驱动错误。<br>34800004 句柄不存在。<br>34800005 句柄不可用。<br>34800006 UKey PIN码错误。<br>34800007 UKey PIN码被锁定。<br>具体含义可查询[HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode)。 |

**示例：**

```ts
import { huksExternalCrypto, HuksCryptoExtensionParam, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onAuthUkeyPin(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> | HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult> {
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

### onGetUkeyPinAuthState

onGetUkeyPinAuthState(handle: string, params: Array\<huksExternalCrypto.HuksExternalCryptoParam> | HuksCryptoExtensionParam[]): Promise\<HuksCryptoExtensionResult>

获取UKey的PIN码认证状态。使用Promise异步回调。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型  | 必填 | 说明   |
| -------- | ------- | ---- | -------|
| handle | string | 是   | 资源句柄。 |
| params  | Array\<[huksExternalCrypto.HuksExternalCryptoParam](js-apis-huksExternalCrypto.md#huksexternalcryptoparam)> \| [HuksCryptoExtensionParam](#hukscryptoextensionparam)[] | 是   | 传入的参数，应用身份通过[HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag)参数携带。 |

**返回值：**

| 类型   | 说明  |
| -------- | ------- |
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise对象。当调用成功时，resultCode为0，HuksCryptoExtensionResult的authState成员非空，为获取的PIN码认证状态。调用失败时，resultCode携带错误码信息。<br>可能返回的错误码值：<br>34800000 密钥扩展错误。<br>34800002 UKey驱动错误。<br>34800004 句柄不存在。<br>34800005 句柄不可用。<br>具体含义可查询[HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode)。 |

**示例：**

```ts
import { huksExternalCrypto, HuksCryptoExtensionParam, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onGetUkeyPinAuthState(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> | HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult> {
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

### onClearUkeyPinAuthState

onClearUkeyPinAuthState(handle: string, params: Array\<huksExternalCrypto.HuksExternalCryptoParam> | HuksCryptoExtensionParam[]): Promise\<HuksCryptoExtensionResult>

清除应用维度PIN码的认证状态。使用Promise异步回调。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型   | 必填 | 说明 |
| -------- | ----- | ---- | ------|
| handle  | string | 是   | 会话句柄。 |
| params  | Array\<[huksExternalCrypto.HuksExternalCryptoParam](js-apis-huksExternalCrypto.md#huksexternalcryptoparam)> \| [HuksCryptoExtensionParam](#hukscryptoextensionparam)[] | 是   | 传入的参数，应用身份通过[HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag)参数携带。 |

**返回值：**

| 类型 | 说明 |
| ------------ | ---------|
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise对象。当调用成功时，resultCode为0，表示清除PIN码认证状态成功。调用失败时，resultCode携带错误码信息。<br>可能返回的错误码值：<br>34800000 密钥扩展错误。<br>34800002 UKey驱动错误。<br>34800004 句柄不存在。<br>34800005 句柄不可用。<br>具体含义可查询[HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode)。 |

**示例：**

```ts
import { huksExternalCrypto, HuksCryptoExtensionParam, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onClearUkeyPinAuthState(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> | HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult> {
    const result: HuksCryptoExtensionResult = {
      resultCode: 0
    };

    // ...
    return Promise.resolve(result);
  }
}
```

### onInitSession

onInitSession(handle: string, params: huks.HuksOptions | HuksCryptoExtensionParams): Promise\<HuksCryptoExtensionResult>

三段式初始化密钥会话操作。使用Promise异步回调。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型 | 必填 | 说明 |
| -------- | ----- | ---- | ------- |
| handle | string                      | 是   | 资源句柄。|
| params  | [huks.HuksOptions](js-apis-huks.md#huksoptions) \| [HuksCryptoExtensionParams](#hukscryptoextensionparams)  | 是   | 传入的参数，应用身份通过[HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag)参数携带。 |

**返回值：**

| 类型 | 说明 |
| --------- | ---------|
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise对象。当调用成功时，resultCode为0，handle成员非空。调用失败时，resultCode携带错误码信息。<br>可能返回的错误码值：<br>34800000 密钥扩展错误。<br>34800002 UKey驱动错误。<br>34800003 UKey PIN码未认证。<br>34800004 句柄不存在。<br>34800005 句柄不可用。<br>34800007 UKey PIN码被锁定。<br>具体含义可查询[HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode)。 |

**示例：**

```ts
import { huks, HuksCryptoExtensionParams, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onInitSession(handle: string, params: huks.HuksOptions | HuksCryptoExtensionParams): Promise<HuksCryptoExtensionResult> {
    const result: HuksCryptoExtensionResult = {
      resultCode: 0,
      handle: "test handle"
    };

    // ...
    return Promise.resolve(result);
  }
}
```

### onUpdateSession

onUpdateSession(initHandle: string, params: huks.HuksOptions | HuksCryptoExtensionParams): Promise\<HuksCryptoExtensionResult>

三段式密钥会话更新数据操作。使用Promise异步回调。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型  | 必填 | 说明 |
| -------- | ----- | ---- | ------|
| initHandle | string | 是   | 资源句柄。   |
| params  | [huks.HuksOptions](js-apis-huks.md#huksoptions) \| [HuksCryptoExtensionParams](#hukscryptoextensionparams)  | 是   | 传入的参数，应用身份通过[HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag)参数携带。 |

**返回值：**

| 类型 | 说明 |
| --------- | ---------|
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise对象。当调用成功时，resultCode为0。调用失败时，resultCode携带错误码信息。<br>可能返回的错误码值：<br>34800000 密钥扩展错误。<br>34800002 UKey驱动错误。<br>34800003 UKey PIN码未认证。<br>34800004 句柄不存在。<br>34800005 句柄不可用。<br>34800007 UKey PIN码被锁定。<br>具体含义可查询[HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode)。 |

**示例：**

```ts
import { huks, HuksCryptoExtensionParams, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onUpdateSession(initHandle: string, params: huks.HuksOptions | HuksCryptoExtensionParams): Promise<HuksCryptoExtensionResult> {
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

### onFinishSession

onFinishSession(initHandle: string, params: huks.HuksOptions | HuksCryptoExtensionParams): Promise\<HuksCryptoExtensionResult>

三段式密钥会话结束操作。使用Promise异步回调。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型 | 必填 | 说明  |
| -------- | -------- | ---- | --------- |
| initHandle | string  | 是   | 资源句柄。 |
| params  | [huks.HuksOptions](js-apis-huks.md#huksoptions) \| [HuksCryptoExtensionParams](#hukscryptoextensionparams)  | 是   | 传入的参数，应用身份可通过[HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag)参数携带，还包括算法参数（算法类型、填充模式等）。 |

**返回值：**

| 类型 | 说明 |
| ------- | ---------- |
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise对象。当调用成功时，resultCode为0。调用失败时，resultCode携带错误码信息。<br>可能返回的错误码值：<br>34800000 密钥扩展错误。<br>34800002 UKey驱动错误。<br>34800003 UKey PIN码未认证。<br>34800004 句柄不存在。<br>34800005 句柄不可用。<br>34800007 UKey PIN码被锁定。<br>具体含义可查询[HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode)。 |

**示例：**

```ts
import { huks, HuksCryptoExtensionParams, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onFinishSession(initHandle: string, params: huks.HuksOptions | HuksCryptoExtensionParams): Promise<HuksCryptoExtensionResult> {
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

### onExportCertificate

onExportCertificate(resourceId: string, params?: Array\<huksExternalCrypto.HuksExternalCryptoParam> | HuksCryptoExtensionParam[]): Promise\<HuksCryptoExtensionResult>

查询指定resourceId下的证书。使用Promise异步回调。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型  | 必填 | 说明 |
| -------- | ---------- | ---- | --------- |
| resourceId | string | 是   | 资源ID。会附带在[HuksCryptoExtensionCertInfo](#hukscryptoextensioncertinfo)中。 |
| params  | Array\<[huksExternalCrypto.HuksExternalCryptoParam](js-apis-huksExternalCrypto.md#huksexternalcryptoparam)> \| [HuksCryptoExtensionParam](#hukscryptoextensionparam)[]  | 否   | 操作属性。默认获取签名类型的证书，也可以通过参数[HUKS_EXT_CRYPTO_TAG_PURPOSE](js-apis-huksExternalCrypto.md#huksexternalcryptotag)指定获取证书类型，支持的类型包括签名验签、加解密等。 |

**返回值：**

| 类型  | 说明  |
| ---------- | --------- |
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise对象。当调用成功时，certs成员非空，包含获取的单本证书。调用失败时，resultCode携带错误码信息。<br>可能返回的错误码值：<br>34800000 密钥扩展错误。<br>34800001 UKey不存在。<br>34800002 UKey驱动错误。<br>34800004 句柄不存在。<br>具体含义可查询[HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode)。 |

**示例：**

```ts
import { huksExternalCrypto, CryptoExtensionAbility, HuksCryptoExtensionResult,
  HuksCryptoExtensionCertInfo } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onExportCertificate(resourceId: string, params?: Array<huksExternalCrypto.HuksExternalCryptoParam> | HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult> {
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

### onEnumCertificates

onEnumCertificates(params?: Array\<huksExternalCrypto.HuksExternalCryptoParam> | HuksCryptoExtensionParam[]): Promise\<HuksCryptoExtensionResult>

枚举Extension下所有UKey设备的证书信息。使用Promise异步回调。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型 | 必填 | 说明   |
| -------- | -----| ---- | ---------- |
| params  | Array\<[huksExternalCrypto.HuksExternalCryptoParam](js-apis-huksExternalCrypto.md#huksexternalcryptoparam)> \| [HuksCryptoExtensionParam](#hukscryptoextensionparam)[]  | 否   | 操作属性。默认获取签名类型的[证书](../../security/DeviceCertificateKit/certManager-overview.md)，也可以通过参数[HUKS_EXT_CRYPTO_TAG_PURPOSE](js-apis-huksExternalCrypto.md#huksexternalcryptotag)指定获取证书类型，支持的类型包括签名验签、加解密等。 |

**返回值：**

| 类型 | 说明 |
| ---------- | ---------|
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise对象。当调用成功时，certs成员非空，包含获取的所有证书。调用失败时，resultCode携带错误码信息。<br>可能返回的错误码值：<br>34800000 密钥扩展错误。<br>34800001 UKey不存在。<br>34800002 UKey驱动错误。<br>具体含义可查询[HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode)。 |

**示例：**

```ts
import { huksExternalCrypto, HuksCryptoExtensionParam, CryptoExtensionAbility, HuksCryptoExtensionResult, HuksCryptoExtensionCertInfo } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onEnumCertificates(params?: Array<huksExternalCrypto.HuksExternalCryptoParam> | HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult> {
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

### onGetResourceId

onGetResourceId(params: HuksCryptoExtensionParam[]):Promise&lt;HuksCryptoExtensionResult&gt;

获取外部扩展设备内的资源ID。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型 | 必填 | 说明 |
| -------- | --------- | ---- | -------- |
| params  | [HuksCryptoExtensionParam](#hukscryptoextensionparam)[] | 是   | 获取资源ID所需的属性参数。必选TAG包括：[HUKS_EXT_CRYPTO_TAG_RESOURCE_INFO](js-apis-huksExternalCrypto.md#huksexternalcryptotag)（厂商自定义的资源信息）、[HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag)（调用方身份）。 |

**返回值：**

| 类型 | 说明 |
| ---------- | ----------- |
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise对象。当调用成功时，resultCode为0，resourceId携带资源ID信息。调用失败时，resultCode携带错误码信息。<br>可能返回的错误码值：<br>34800000 密钥扩展错误。<br>具体含义可查询[HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode)。 |

**示例：**

```ts
import { HuksCryptoExtensionParam, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onGetResourceId(params: HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult> {
    const result: HuksCryptoExtensionResult = {
      resultCode: 0,
      resourceId: "test resourceId"
    };

    // ...
    return Promise.resolve(result);
  }
}
```

### onImportCertificate

onImportCertificate(handle: string, params: HuksCryptoExtensionParam[], certInfo: HuksCryptoExtensionCertInfo): Promise&lt;HuksCryptoExtensionResult&gt;

导入指定资源句柄的证书。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型  | 必填 | 说明  |
| -------- | ----- | ---- | ------|
| handle | string | 是   | 导入证书的资源句柄。 |
| params  | [HuksCryptoExtensionParam](#hukscryptoextensionparam)[] | 是 | 导入证书所需的属性参数。 |
| certInfo | [HuksCryptoExtensionCertInfo](#hukscryptoextensioncertinfo) | 是   | 待导入的证书信息。需指定证书类型（purpose）。 |

**返回值：**

| 类型    | 说明   |
| -------- | -----------|
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise对象。当调用成功时，resultCode为0，表示导入证书成功。调用失败时，resultCode携带错误码信息，errInfo携带详细错误信息。<br>可能返回的错误码值：<br>34800000 密钥扩展错误。<br>34800001 UKey不存在。<br>34800002 UKey驱动错误。<br>34800004 句柄不存在。<br>34800005 句柄不可用。<br>具体含义可查询[HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode)。 |

**示例：**

```ts
import { CryptoExtensionAbility, HuksCryptoExtensionParam, HuksCryptoExtensionResult,
  HuksCryptoExtensionCertInfo } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onImportCertificate(handle: string, params: HuksCryptoExtensionParam[],
      certInfo: HuksCryptoExtensionCertInfo): Promise<HuksCryptoExtensionResult> {
    const result: HuksCryptoExtensionResult = {
      resultCode: 0
    };

    // ...
    return Promise.resolve(result);
  }
}
```

### onGenerateKeyItem

onGenerateKeyItem(handle: string, params: HuksCryptoExtensionParam[]): Promise&lt;HuksCryptoExtensionResult&gt;

用于在扩展设备内生成密钥对。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型  | 必填 | 说明  |
| -------- | ----- | ---- | ------|
| handle | string | 是   | 待生成密钥的资源句柄。 |
| params  | [HuksCryptoExtensionParam](#hukscryptoextensionparam)[] | 是 | 密钥生成操作的属性参数。必选TAG：[HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag)（调用方身份）。 |

**返回值：**

| 类型    | 说明   |
| -------- | -----------|
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise对象。当调用成功时，resultCode为0，表示生成密钥成功。调用失败时，resultCode携带错误码信息。<br>可能返回的错误码值：<br>34800000 密钥扩展错误。<br>34800002 UKey驱动错误。<br>34800004 句柄不存在。<br>34800005 句柄不可用。<br>具体含义可查询[HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode)。 |

**示例：**

```ts
import { huks, CryptoExtensionAbility, HuksCryptoExtensionResult, HuksCryptoExtensionParam } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onGenerateKeyItem(handle: string, params: HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult> {
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

### onExportKeyItem

onExportKeyItem(handle: string, params: HuksCryptoExtensionParam[]): Promise&lt;HuksCryptoExtensionResult&gt;

用于导出指定密钥的公钥。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型  | 必填 | 说明  |
| -------- | ----- | ---- | ------|
| handle | string | 是   | 待导出公钥的资源句柄。 |
| params  | [HuksCryptoExtensionParam](#hukscryptoextensionparam)[] | 是 | 导出公钥操作的属性参数。必选TAG：[HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag)（调用方身份）。 |

**返回值：**

| 类型    | 说明   |
| -------- | -----------|
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise对象。当调用成功时，resultCode为0，outData携带导出的公钥数据。调用失败时，resultCode携带错误码信息，errInfo携带详细错误信息。<br>可能返回的错误码值：<br>34800000 密钥扩展错误。<br>34800002 UKey驱动错误。<br>34800004 句柄不存在。<br>34800005 句柄不可用。<br>具体含义可查询[HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode)。 |

**示例：**

```ts
import { huks, CryptoExtensionAbility, HuksCryptoExtensionResult, HuksCryptoExtensionParam } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onExportKeyItem(handle: string, params: HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult> {
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

### onImportWrappedKeyItem

onImportWrappedKeyItem(handle: string, wrappingHandle: string, params: HuksCryptoExtensionParam[], wrappedKey: Uint8Array): Promise&lt;HuksCryptoExtensionResult&gt;

用于导入加密封装的密钥对。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型  | 必填 | 说明  |
| -------- | ----- | ---- | ------|
| handle | string | 是   | 待导入密钥的资源句柄。 |
| wrappingHandle | string | 是   | 用于解封导入密钥的密钥资源句柄。 |
| params  | [HuksCryptoExtensionParam](#hukscryptoextensionparam)[] | 是 | 导入封装密钥操作的属性参数。必选TAG：[HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag)（调用方身份）。 |
| wrappedKey | Uint8Array | 是   | 封装密钥数据，格式由密钥扩展定义。 |

**返回值：**

| 类型    | 说明   |
| -------- | -----------|
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise对象。当调用成功时，resultCode为0，表示导入密钥成功。调用失败时，resultCode携带错误码信息，errInfo携带详细错误信息。<br>可能返回的错误码值：<br>34800000 密钥扩展错误。<br>34800002 UKey驱动错误。<br>34800004 句柄不存在。<br>34800005 句柄不可用。<br>具体含义可查询[HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode)。 |

**示例：**

```ts
import { huks, CryptoExtensionAbility, HuksCryptoExtensionResult, HuksCryptoExtensionParam } from '@kit.UniversalKeystoreKit';
export default class CryptoExtension extends CryptoExtensionAbility {
  onImportWrappedKeyItem(handle: string, wrappingHandle: string, params: HuksCryptoExtensionParam[], wrappedKey: Uint8Array): Promise<HuksCryptoExtensionResult> {
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

## 附录

CryptoExtensionAbility不支持以下模块的引用。
<!--RP1-->
| Kit | 模块 |
| ------ | ------ |
| Ability Kit | [@ohos.distributedBundle (分布式包管理)(系统接口)](../../reference/apis-ability-kit/js-apis-Bundle-distributedBundle-sys.md) |
| Ability Kit | [@ohos.distributedMissionManager (分布式任务管理)(系统接口)](../../reference/apis-ability-kit/js-apis-distributedMissionManager-sys.md) |
| Ability Kit | [@ohos.wantAgent (WantAgent模块)](../../reference/apis-ability-kit/js-apis-wantAgent.md) |
| Ads Kit | [@ohos.advertising.AdComponent (广告展示组件)](../../reference/apis-ads-kit/js-apis-adcomponent.md) |
| Ads Kit | [@ohos.advertising.AdsServiceExtensionAbility (广告扩展服务)](../../reference/apis-ads-kit/js-apis-adsserviceextensionability.md) |
| Ads Kit | [@ohos.advertising.AutoAdComponent (轮播广告展示组件)](../../reference/apis-ads-kit/js-apis-autoadcomponent.md) |
| Ads Kit | [@ohos.advertising (广告服务框架)](../../reference/apis-ads-kit/js-apis-advertising.md) |
| ArkUI | [@ohos.atomicservice.AtomicServiceNavigation (AtomicServiceNavigation)](../../reference/apis-arkui/arkui-ts/ohos-atomicservice-AtomicServiceNavigation.md) |
| ArkUI | [@ohos.atomicservice.AtomicServiceSearch (AtomicServiceSearch)](../../reference/apis-arkui/arkui-ts/ohos-atomicservice-AtomicServiceSearch.md) |
| ArkUI | [@ohos.atomicservice.AtomicServiceTabs (AtomicServiceTabs)](../../reference/apis-arkui/arkui-ts/ohos-atomicservice-AtomicServiceTabs.md) |
| ArkUI | [@ohos.atomicservice.AtomicServiceWeb (AtomicServiceWeb)](../../reference/apis-arkui/arkui-ts/ohos-atomicservice-AtomicServiceWeb.md) |
| ArkUI | [@ohos.atomicservice.HalfScreenLaunchComponent (HalfScreenLaunchComponent)](../../reference/apis-arkui/arkui-ts/ohos-atomicservice-HalfScreenLaunchComponent.md) |
| ArkUI | [@ohos.atomicservice.InterstitialDialogAction (InterstitialDialogAction)](../../reference/apis-arkui/arkui-ts/ohos-atomicservice-InterstitialDialogAction.md) |
| ArkUI | [@ohos.atomicservice.NavPushPathHelper (NavPushPathHelper)](../../reference/apis-arkui/arkui-ts/ohos-atomicservice-NavPushPathHelper.md) |
| ArkUI | [@ohos.mediaquery (媒体查询)](../../reference/apis-arkui/js-apis-mediaquery.md) |
| ArkUI | [@ohos.PiPWindow (画中画窗口)](../../reference/apis-arkui/js-apis-pipWindow.md) |
| ArkUI | [@ohos.screenshot (屏幕截图)](../../reference/apis-arkui/js-apis-screenshot.md) |
| ArkWeb | [@ohos.web.netErrorList (ArkWeb网络协议栈错误列表)](../../reference/apis-arkweb/arkts-apis-netErrorList.md) |
| ArkWeb | [@ohos.web.WebNativeMessagingExtensionAbility (Web Native Messaging Extension Ability)](../../reference/apis-arkweb/arkts-apis-web-webNativeMessagingExtensionAbility.md) |
| ArkWeb | [@ohos.web.WebNativeMessagingExtensionContext (Web Native Messaging Extension Context)](../../reference/apis-arkweb/arkts-apis-web-webNativeMessagingExtensionContext.md) |
| ArkWeb | [@ohos.web.webNativeMessagingExtensionManager (Web Native Messaging Extension Manager)](../../reference/apis-arkweb/arkts-apis-web-webNativeMessagingExtensionManager.md) |
| ArkWeb | [@ohos.web.webview](../../reference/apis-arkweb/arkts-apis-webview.md) |
| Audio Kit | [@ohos.multimedia.audio (音频管理)(系统接口)](../../reference/apis-audio-kit/js-apis-audio-sys.md) |
| Audio Kit | [@ohos.multimedia.audioHaptic (音振协同)](../../reference/apis-audio-kit/js-apis-audioHaptic.md) |
| Audio Kit | [@ohos.multimedia.avVolumePanel (音量面板)](../../reference/apis-audio-kit/ohos-multimedia-avvolumepanel.md) |
| Audio Kit | [@ohos.multimedia.systemSoundManager (系统声音管理)](../../reference/apis-audio-kit/js-apis-systemSoundManager.md) |
| AVSession Kit | [@ohos.multimedia.avCastPicker (投播组件)](../../reference/apis-avsession-kit/ohos-multimedia-avcastpicker.md) |
| AVSession Kit | [@ohos.multimedia.avCastPickerParam (投播组件参数)](../../reference/apis-avsession-kit/js-apis-avCastPickerParam.md) |
| AVSession Kit | [@ohos.multimedia.avInputCastPicker (录音设备选择组件)](../../reference/apis-avsession-kit/ohos-multimedia-avinputcastpicker.md) |
| AVSession Kit | [@ohos.multimedia.avsession (媒体会话管理)(系统接口)](../../reference/apis-avsession-kit/js-apis-avsession-sys.md) |
| Basic Service Kit | [@ohos.ai.intelligentVoice (智能语音)(系统接口)](../../reference/apis-basic-services-kit/js-apis-intelligentVoice-sys.md) |
| Basic Service Kit | [@ohos.pasteboard (剪贴板)](../../reference/apis-basic-services-kit/js-apis-pasteboard.md) |
| Basic Service Kit | [@ohos.scan (扫描)](../../reference/apis-basic-services-kit/js-apis-scan.md) |
| Basic Service Kit | [@ohos.screenLock (锁屏管理)](../../reference/apis-basic-services-kit/js-apis-screen-lock.md) |
| Basic Service Kit | [@ohos.settings (设置数据项名称)](../../reference/apis-basic-services-kit/js-apis-settings.md) |
| Basic Service Kit | [@ohos.wallpaper (壁纸)](../../reference/apis-basic-services-kit/js-apis-wallpaper.md) |
| Basic Service Kit | [@ohos.WallpaperExtensionAbility (WallpaperExtensionAbility)(系统接口)](../../reference/apis-basic-services-kit/js-apis-WallpaperExtensionAbility-sys.md) |
| Calendar Kit | [@ohos.calendarManager (日程管理能力)](../../reference/apis-calendar-kit/js-apis-calendarManager.md) |
| Camera Kit | [@ohos.multimedia.camera (相机管理)(系统接口)](../../reference/apis-camera-kit/js-apis-camera-sys.md) |
| Camera Kit | [@ohos.multimedia.cameraPicker (相机选择器)](../../reference/apis-camera-kit/js-apis-cameraPicker.md) |
| Connectivity Kit | [@ohos.bluetooth.a2dp (蓝牙a2dp模块)](../../reference/apis-connectivity-kit/js-apis-bluetooth-a2dp.md) |
| Connectivity Kit | [@ohos.bluetooth.access (蓝牙access模块)](../../reference/apis-connectivity-kit/js-apis-bluetooth-access.md) |
| Connectivity Kit | [@ohos.bluetooth.baseProfile (蓝牙baseProfile模块)](../../reference/apis-connectivity-kit/js-apis-bluetooth-baseProfile.md) |
| Connectivity Kit | [@ohos.bluetooth.ble (蓝牙ble模块)](../../reference/apis-connectivity-kit/js-apis-bluetooth-ble.md) |
| Connectivity Kit | [@ohos.bluetooth.common (蓝牙common模块)](../../reference/apis-connectivity-kit/js-apis-bluetooth-common.md) |
| Connectivity Kit | [@ohos.bluetooth.connection (蓝牙connection模块)](../../reference/apis-connectivity-kit/js-apis-bluetooth-connection.md) |
| Connectivity Kit | [@ohos.bluetooth.constant (蓝牙constant模块)](../../reference/apis-connectivity-kit/js-apis-bluetooth-constant.md) |
| Connectivity Kit | [@ohos.bluetooth (蓝牙)](../../reference/apis-connectivity-kit/js-apis-bluetooth.md) |
| Connectivity Kit | [@ohos.bluetooth.hfp (蓝牙hfp模块)](../../reference/apis-connectivity-kit/js-apis-bluetooth-hfp.md) |
| Connectivity Kit | [@ohos.bluetooth.hid (蓝牙hid模块)](../../reference/apis-connectivity-kit/js-apis-bluetooth-hid.md) |
| Connectivity Kit | [@ohos.bluetoothManager (蓝牙)](../../reference/apis-connectivity-kit/js-apis-bluetoothManager.md) |
| Connectivity Kit | [@ohos.bluetooth.map (蓝牙map模块)](../../reference/apis-connectivity-kit/js-apis-bluetooth-map.md) |
| Connectivity Kit | [@ohos.bluetooth.opp (蓝牙opp模块)(系统接口)](../../reference/apis-connectivity-kit/js-apis-bluetooth-opp-sys.md) |
| Connectivity Kit | [@ohos.bluetooth.pan (蓝牙pan模块)](../../reference/apis-connectivity-kit/js-apis-bluetooth-pan.md) |
| Connectivity Kit | [@ohos.bluetooth.pbap (蓝牙pbap模块)](../../reference/apis-connectivity-kit/js-apis-bluetooth-pbap.md) |
| Connectivity Kit | [@ohos.bluetooth.socket (蓝牙socket模块)](../../reference/apis-connectivity-kit/js-apis-bluetooth-socket.md) |
| Connectivity Kit | [@ohos.bluetooth.wearDetection(蓝牙佩戴检测模块)(系统接口)](../../reference/apis-connectivity-kit/js-apis-bluetooth-wearDetection-sys.md) |
| Connectivity Kit | [@ohos.connectedTag (有源标签)](../../reference/apis-connectivity-kit/js-apis-connectedTag.md) |
| Connectivity Kit | [@ohos.nfc.cardEmulation (标准NFC-cardEmulation)](../../reference/apis-connectivity-kit/js-apis-cardEmulation.md) |
| Connectivity Kit | [@ohos.nfc.controller (标准NFC)](../../reference/apis-connectivity-kit/js-apis-nfcController.md) |
| Connectivity Kit | [@ohos.nfc.tag (标准NFC-Tag)](../../reference/apis-connectivity-kit/js-apis-nfcTag.md) |
| Connectivity Kit | [@ohos.wifi (WLAN)](../../reference/apis-connectivity-kit/js-apis-wifi.md) |
| Connectivity Kit | [@ohos.wifiext (WLAN扩展接口)](../../reference/apis-connectivity-kit/js-apis-wifiext.md) |
| Connectivity Kit | [@ohos.wifiManager (WLAN)](../../reference/apis-connectivity-kit/js-apis-wifiManager.md) |
| Connectivity Kit | [@ohos.wifiManagerExt (WLAN扩展接口)](../../reference/apis-connectivity-kit/js-apis-wifiManagerExt.md) |
| Contacts Kit | [@ohos.contact (联系人)](../../reference/apis-contacts-kit/js-apis-contact.md) |
| Data Protection Kit | [@ohos.dlpPermission (数据防泄漏)](../../reference/apis-data-protection-kit/js-apis-dlppermission.md) |
| Distributed Service Kit | [@ohos.distributedDeviceManager (设备管理)](../../reference/apis-distributedservice-kit/js-apis-distributedDeviceManager.md) |
| Distributed Service Kit | [@ohos.distributedHardware.deviceManager (设备管理)(系统接口)](../../reference/apis-distributedservice-kit/js-apis-device-manager-sys.md) |
| Distributed Service Kit | [@ohos.distributedHardware.hardwareManager (分布式硬件管理)(系统接口)](../../reference/apis-distributedservice-kit/js-apis-distributedHardwareManager-sys.md) |
| Distributed Service Kit | [@ohos.distributedsched.abilityConnectionManager (应用多端协同管理)](../../reference/apis-distributedservice-kit/js-apis-distributed-abilityConnectionManager.md) |
| Distributed Service Kit | [@ohos.distributedsched.linkEnhance (增强连接)](../../reference/apis-distributedservice-kit/js-apis-link-enhance.md) |
| Distributed Service Kit | [@ohos.distributedsched.proxyChannelManager (代理通道管理)](../../reference/apis-distributedservice-kit/js-apis-proxyChannelManager.md) |
| DRM Kit | [@ohos.multimedia.drm](../../reference/apis-drm-kit/arkts-apis-drm.md) |
| Form Kit | [@ohos.app.form.formAgent (FormAgent)(系统接口)](../../reference/apis-form-kit/js-apis-app-form-formAgent-sys.md) |
| Form Kit | [@ohos.app.form.formBindingData (卡片数据绑定类)](../../reference/apis-form-kit/js-apis-app-form-formBindingData.md) |
| Form Kit | [@ohos.app.form.FormEditExtensionAbility (FormEditExtensionAbility)](../../reference/apis-form-kit/js-apis-app-form-formEditExtensionAbility.md) |
| Form Kit | [@ohos.app.form.FormExtensionAbility (FormExtensionAbility)](../../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md) |
| Form Kit | [@ohos.app.form.formHost (formHost)(系统接口)](../../reference/apis-form-kit/js-apis-app-form-formHost-sys.md) |
| Form Kit | [@ohos.app.form.formInfo (formInfo)](../../reference/apis-form-kit/js-apis-app-form-formInfo.md) |
| Form Kit | [@ohos.app.form.formObserver (formObserver)(系统接口)](../../reference/apis-form-kit/js-apis-app-form-formObserver-sys.md) |
| Form Kit | [@ohos.app.form.formProvider (formProvider)](../../reference/apis-form-kit/js-apis-app-form-formProvider.md) |
| Form Kit | [@ohos.app.form.LiveFormExtensionAbility (LiveFormExtensionAbility)](../../reference/apis-form-kit/js-apis-app-form-LiveFormExtensionAbility.md) |
| Image Kit | [@ohos.multimedia.image (图片处理)(系统接口)](../../reference/apis-image-kit/js-apis-image-sys.md) |
| Image Kit | [@ohos.multimedia.sendableImage (基于Sendable对象的图片处理)](../../reference/apis-image-kit/js-apis-sendableImage.md) |
| Image Kit | [@ohos.multimedia.videoProcessingEngine (视频处理引擎)](../../reference/apis-image-kit/js-apis-videoProcessingEngine.md) |
| Location Kit | [@ohos.geolocation (位置服务)](../../reference/apis-location-kit/js-apis-geolocation.md) |
| Location Kit | [@ohos.geoLocationManager (位置服务)](../../reference/apis-location-kit/js-apis-geoLocationManager.md) |
| MDM Kit | [@ohos.enterprise.accountManager（账号管理）](../../reference/apis-mdm-kit/js-apis-enterprise-accountManager.md) |
| MDM Kit | [@ohos.enterprise.adminManager（admin权限管理）](../../reference/apis-mdm-kit/js-apis-enterprise-adminManager.md) |
| MDM Kit | [@ohos.enterprise.applicationManager（应用管理）](../../reference/apis-mdm-kit/js-apis-enterprise-applicationManager.md) |
| MDM Kit | [@ohos.enterprise.bluetoothManager（蓝牙管理）](../../reference/apis-mdm-kit/js-apis-enterprise-bluetoothManager.md) |
| MDM Kit | [@ohos.enterprise.browser（浏览器管理）](../../reference/apis-mdm-kit/js-apis-enterprise-browser.md) |
| MDM Kit | [@ohos.enterprise.bundleManager（包管理）](../../reference/apis-mdm-kit/js-apis-enterprise-bundleManager.md) |
| MDM Kit | [@ohos.enterprise.common（Enterprise公共模块）](../../reference/apis-mdm-kit/js-apis-enterprise-common.md) |
| MDM Kit | [@ohos.enterprise.dateTimeManager （系统时间管理）(系统接口)](../../reference/apis-mdm-kit/js-apis-enterprise-dateTimeManager-sys.md) |
| MDM Kit | [@ohos.enterprise.deviceControl（设备控制管理）](../../reference/apis-mdm-kit/js-apis-enterprise-deviceControl.md) |
| MDM Kit | [@ohos.enterprise.deviceInfo（设备信息管理）](../../reference/apis-mdm-kit/js-apis-enterprise-deviceInfo.md) |
| MDM Kit | [@ohos.enterprise.deviceSettings （设备设置管理）](../../reference/apis-mdm-kit/js-apis-enterprise-deviceSettings.md) |
| MDM Kit | [@ohos.enterprise.EnterpriseAdminExtensionAbility（企业设备管理扩展能力）](../../reference/apis-mdm-kit/js-apis-EnterpriseAdminExtensionAbility.md) |
| MDM Kit | [@ohos.enterprise.locationManager（位置服务管理）](../../reference/apis-mdm-kit/js-apis-enterprise-locationManager.md) |
| MDM Kit | [@ohos.enterprise.networkManager（网络管理）](../../reference/apis-mdm-kit/js-apis-enterprise-networkManager.md) |
| MDM Kit | [@ohos.enterprise.restrictions （限制类策略）](../../reference/apis-mdm-kit/js-apis-enterprise-restrictions.md) |
| MDM Kit | [@ohos.enterprise.securityManager（安全管理）](../../reference/apis-mdm-kit/js-apis-enterprise-securityManager.md) |
| MDM Kit | [@ohos.enterprise.systemManager （系统管理）](../../reference/apis-mdm-kit/js-apis-enterprise-systemManager.md) |
| MDM Kit | [@ohos.enterprise.telephonyManager（通话管理）](../../reference/apis-mdm-kit/js-apis-enterprise-telephonyManager.md) |
| MDM Kit | [@ohos.enterprise.usbManager（USB管理）](../../reference/apis-mdm-kit/js-apis-enterprise-usbManager.md) |
| MDM Kit | [@ohos.enterprise.wifiManager（Wi-Fi管理）](../../reference/apis-mdm-kit/js-apis-enterprise-wifiManager.md) |
| Mechanic Kit | [@ohos.distributedHardware.mechanicManager (机械体控制模块)](../../reference/apis-mechanic-kit/js-apis-mechanicManager.md) |
| Media Kit | [@ohos.multimedia.media (媒体服务)(系统接口)](../../reference/apis-media-kit/js-apis-media-sys.md) |
| Media Library Kit | [@ohos.multimedia.movingphotoview (动态照片)](../../reference/apis-media-library-kit/ohos-multimedia-movingphotoview.md) |
| MindSpore Lite Kit | [@ohos.ai.mindSporeLite (端侧AI框架)](../../reference/apis-mindspore-lite-kit/js-apis-mindSporeLite.md) |
| Network Kit | [@ohos.net.connection (网络连接管理)](../../reference/apis-network-kit/js-apis-net-connection.md) |
| Network Kit | [@ohos.net.eap (扩展认证)](../../reference/apis-network-kit/js-apis-net-eap.md) |
| Network Kit | [@ohos.net.ethernet (以太网连接管理)](../../reference/apis-network-kit/js-apis-net-ethernet.md) |
| Network Kit | [@ohos.net.http (数据请求)](../../reference/apis-network-kit/js-apis-http.md) |
| Network Kit | [@ohos.net.mdns (MDNS管理)](../../reference/apis-network-kit/js-apis-net-mdns.md) |
| Network Kit | [@ohos.net.netFirewall (网络防火墙)](../../reference/apis-network-kit/js-apis-net-netfirewall.md) |
| Network Kit | [@ohos.net.networkSecurity (网络安全校验)](../../reference/apis-network-kit/js-apis-networkSecurity.md) |
| Network Kit | [@ohos.net.policy (网络策略管理)](../../reference/apis-network-kit/js-apis-net-policy.md) |
| Network Kit | [@ohos.net.sharing (网络共享管理)](../../reference/apis-network-kit/js-apis-net-sharing.md) |
| Network Kit | [@ohos.net.socket (Socket连接)](../../reference/apis-network-kit/js-apis-socket.md) |
| Network Kit | [@ohos.net.statistics (流量管理)](../../reference/apis-network-kit/js-apis-net-statistics.md) |
| Network Kit | [@ohos.net.vpn (VPN管理)](../../reference/apis-network-kit/js-apis-net-vpn.md) |
| Network Kit | [@ohos.net.vpnExtension (VPN增强管理)](../../reference/apis-network-kit/js-apis-net-vpnExtension.md) |
| Network Kit | [@ohos.net.webSocket (WebSocket连接)](../../reference/apis-network-kit/js-apis-webSocket.md) |
| Telephony Kit | [@ohos.telephony.call (拨打电话)](../../reference/apis-telephony-kit/js-apis-call.md) |
| Telephony Kit | [@ohos.telephony.data (蜂窝数据)](../../reference/apis-telephony-kit/js-apis-telephony-data.md) |
| Telephony Kit | [@ohos.telephony.esim (eSIM卡管理)](../../reference/apis-telephony-kit/js-apis-esim.md) |
| Telephony Kit | [@ohos.telephony.observer (observer)](../../reference/apis-telephony-kit/js-apis-observer.md) |
| Telephony Kit | [@ohos.telephony.radio (网络搜索)](../../reference/apis-telephony-kit/js-apis-radio.md) |
| Telephony Kit | [@ohos.telephony.sim (SIM卡管理)](../../reference/apis-telephony-kit/js-apis-sim.md) |
| Telephony Kit | [@ohos.telephony.sms (短信服务)](../../reference/apis-telephony-kit/js-apis-sms.md) |
| Telephony Kit | [@ohos.telephony.vcard (VCard模块)](../../reference/apis-telephony-kit/js-apis-vcard.md) |
<!--RP1End-->