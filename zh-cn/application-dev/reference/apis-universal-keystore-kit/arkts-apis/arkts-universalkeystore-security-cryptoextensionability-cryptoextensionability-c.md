# CryptoExtensionAbility

```TypeScript
declare class CryptoExtensionAbility
```

Class to be override for external crypto extension ability.

**起始版本：** 22

<!--Device-unnamed-declare class CryptoExtensionAbility--><!--Device-unnamed-declare class CryptoExtensionAbility-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## ExtensionAbility使用限制

为保障系统安全性和稳定性，防止CryptoExtensionAbility滥用系统资源，系统对其能力进行管控，不支持部分模块的引用，详情请参考[附录](#附录)。

## 导入模块

```TypeScript
import { CryptoExtensionAbility, HuksCryptoExtensionCertInfo, HuksCryptoExtensionResult, HuksCryptoExtensionResultCode, HuksCryptoExtensionParam, HuksCryptoExtensionParams } from '@kit.UniversalKeystoreKit';
```

## onAuthUkeyPin

```TypeScript
onAuthUkeyPin(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |
      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>
```

请求Ukey认证PIN码。使用Promise异步回调。

**起始版本：** 22

<!--Device-CryptoExtensionAbility-onAuthUkeyPin(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>--><!--Device-CryptoExtensionAbility-onAuthUkeyPin(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | string | 是 | 资源句柄。 |
| params | Array&lt;[huksExternalCrypto.HuksExternalCryptoParam](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptoparam-i.md)&gt; &#124; [HuksCryptoExtensionParam](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparam-i.md)[] | 是 | 操作属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise对象。当调用成功时，resultCode为0，authState非0，表示认证请求成功。调用失败时，resultCode携带错误码信息。可能返回的错误码值：0 - 调用成功。34800000 - 密钥扩展错误。34800002 - Ukey驱动错误。34800004 - 句柄不存在。34800005 - 句柄不可用。34800006 - Ukey PIN码错误。34800007 - Ukey PIN码被锁 |

**示例**

```TypeScript
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

## onClearUkeyPinAuthState

```TypeScript
onClearUkeyPinAuthState(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |
      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>
```

清除应用维度PIN码的认证状态。使用Promise异步回调。

**起始版本：** 22

<!--Device-CryptoExtensionAbility-onClearUkeyPinAuthState(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>--><!--Device-CryptoExtensionAbility-onClearUkeyPinAuthState(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | string | 是 | 资源句柄 |
| params | Array&lt;[huksExternalCrypto.HuksExternalCryptoParam](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptoparam-i.md)&gt; &#124; [HuksCryptoExtensionParam](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparam-i.md)[] | 是 | 操作属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise对象。当调用成功时，resultCode为0，表示清除PIN码认证状态成功。调用失败时，resultCode携带错误码信息。可能返回的错误码值：0 - 调用成功。34800000 - 密钥扩展错误。34800002 - Ukey驱动错误。34800004 - 句柄不存在。34800005 - 句柄不可用。 |

**示例**

```TypeScript
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

## onCloseResource

```TypeScript
onCloseResource(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |
      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>
```

根据参数中的handle，关闭Ukey的密钥资源。使用Promise异步回调。

**起始版本：** 22

<!--Device-CryptoExtensionAbility-onCloseResource(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>--><!--Device-CryptoExtensionAbility-onCloseResource(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | string | 是 | 会话句柄。 |
| params | Array&lt;[huksExternalCrypto.HuksExternalCryptoParam](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptoparam-i.md)&gt; &#124; [HuksCryptoExtensionParam](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparam-i.md)[] | 是 | 操作属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | 函数返回的promise。HuksCryptoExtensionResult.resultCode可能具有以下值：0-操作成功34800000 -加密扩展中发生错误。可能原因：1.输入参数非法。2.加密扩展遇到无法解析的错误状态。34800002-UKey驱动程序错误。这意味着UKey驱动程序中发生了未知错误。34800004 -句柄不存在。可能原因：1.输入的句柄无效。2.huks服务和加密扩展的状态不一致。由于异常，huks服务持有的句柄没有被释放。34800005 -句柄不可用，可能是因为状态不一致在加密扩展和UKey之间。 |

**示例**

```TypeScript
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

## onEnumCertificates

```TypeScript
onEnumCertificates(params?: Array<huksExternalCrypto.HuksExternalCryptoParam> | HuksCryptoExtensionParam[]):
      Promise<HuksCryptoExtensionResult>
```

枚举Extension下所有Ukey设备的证书信息。使用Promise异步回调。

**起始版本：** 22

<!--Device-CryptoExtensionAbility-onEnumCertificates(params?: Array<huksExternalCrypto.HuksExternalCryptoParam> | HuksCryptoExtensionParam[]):      Promise<HuksCryptoExtensionResult>--><!--Device-CryptoExtensionAbility-onEnumCertificates(params?: Array<huksExternalCrypto.HuksExternalCryptoParam> | HuksCryptoExtensionParam[]):      Promise<HuksCryptoExtensionResult>-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | Array&lt;[huksExternalCrypto.HuksExternalCryptoParam](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptoparam-i.md)&gt; &#124; [HuksCryptoExtensionParam](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparam-i.md)[] | 否 | 操作属性 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise对象。当调用成功时，certs成员非空，包含获取的所有证书。调用失败时，resultCode携带错误码信息。可能返回的错误码值：0 - 调用成功。34800000 - 密钥扩展错误。34800001 - Ukey不存在。34800002 - Ukey驱动错误。 |

**示例**

```TypeScript
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

## onExportCertificate

```TypeScript
onExportCertificate(resourceId: string, params?: Array<huksExternalCrypto.HuksExternalCryptoParam> |
      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>
```

查询指定resourceId下的证书。使用Promise异步回调。

**起始版本：** 22

<!--Device-CryptoExtensionAbility-onExportCertificate(resourceId: string, params?: Array<huksExternalCrypto.HuksExternalCryptoParam> |      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>--><!--Device-CryptoExtensionAbility-onExportCertificate(resourceId: string, params?: Array<huksExternalCrypto.HuksExternalCryptoParam> |      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resourceId | string | 是 | 资源ID。 |
| params | Array&lt;[huksExternalCrypto.HuksExternalCryptoParam](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptoparam-i.md)&gt; &#124; [HuksCryptoExtensionParam](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparam-i.md)[] | 否 | 操作属性 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise对象。当调用成功时，certs成员非空，包含获取的单本证书。调用失败时，resultCode携带错误码信息。可能返回的错误码值：0 - 调用成功。34800000 - 密钥扩展错误。34800001 - Ukey不存在。34800002 - Ukey驱动错误。34800004 - 句柄不存在。 |

**示例**

```TypeScript
import { huksExternalCrypto, CryptoExtensionAbility, HuksCryptoExtensionResult,
  HuksCryptoExtensionCertInfo, HuksCryptoExtensionParam } from '@kit.UniversalKeystoreKit';

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

## onExportKeyItem

```TypeScript
onExportKeyItem(handle: string, params: HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>
```

用于导出指定密钥的公钥。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CryptoExtensionAbility-onExportKeyItem(handle: string, params: HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>--><!--Device-CryptoExtensionAbility-onExportKeyItem(handle: string, params: HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | string | 是 | 待导出公钥的资源句柄 |
| params | [HuksCryptoExtensionParam](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparam-i.md)[] | 是 | 导出公钥操作的属性参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise对象。当调用成功时，resultCode为0，outData携带导出的公钥数据。调用失败时，resultCode携带错误码信息，errInfo携带详细错误信息。可能返回的错误码值：0 - 调用成功。34800000 - 密钥扩展错误。34800001 - Ukey不存在。34800002 - Ukey驱动错误。34800004 - 句柄不存在。34800005 - 句柄不可用。 |

**示例**

```TypeScript
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

## onFinishSession

```TypeScript
onFinishSession(initHandle: string, params: huks.HuksOptions | HuksCryptoExtensionParams):
      Promise<HuksCryptoExtensionResult>
```

三段式密钥会话结束操作。使用Promise异步回调。

**起始版本：** 22

<!--Device-CryptoExtensionAbility-onFinishSession(initHandle: string, params: huks.HuksOptions | HuksCryptoExtensionParams):      Promise<HuksCryptoExtensionResult>--><!--Device-CryptoExtensionAbility-onFinishSession(initHandle: string, params: huks.HuksOptions | HuksCryptoExtensionParams):      Promise<HuksCryptoExtensionResult>-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| initHandle | string | 是 | 资源句柄。 |
| params | [huks.HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) &#124; [HuksCryptoExtensionParams](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparams-i.md) | 是 | 操作属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise对象。当调用成功时，resultCode为0。调用失败时，resultCode携带错误码信息。可能返回的错误码值：0 - 调用成功。34800000 - 密钥扩展错误。34800002 - Ukey驱动错误。34800003 - Ukey PIN码未认证。34800004 - 句柄不存在。34800005 - 句柄不可用。34800007 - Ukey PIN码被锁。 |

**示例**

```TypeScript
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

## onGenerateKeyItem

```TypeScript
onGenerateKeyItem(handle: string, params:HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>
```

用于在扩展设备内生成密钥对。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CryptoExtensionAbility-onGenerateKeyItem(handle: string, params:HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>--><!--Device-CryptoExtensionAbility-onGenerateKeyItem(handle: string, params:HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | string | 是 | 待生成密钥的资源句柄。 |
| params | [HuksCryptoExtensionParam](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparam-i.md)[] | 是 | 密钥生成操作的属性参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise对象。当调用成功时，resultCode为0，表示生成密钥成功。调用失败时，resultCode携带错误码信息。可能返回的错误码值：0 - 调用成功。34800000 - 密钥扩展错误。34800001 - Ukey不存在。34800002 - Ukey驱动错误。34800004 - 句柄不存在。34800005 - 句柄不可用。 |

**示例**

```TypeScript
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

## onGetProperty

```TypeScript
onGetProperty(handle: string, propertyId: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |
      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>
```

查询操作回调。

**起始版本：** 22

<!--Device-CryptoExtensionAbility-onGetProperty(handle: string, propertyId: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>--><!--Device-CryptoExtensionAbility-onGetProperty(handle: string, propertyId: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | string | 是 | handle表示onOpenResource打开的句柄。 |
| propertyId | string | 是 | propertyId表示属性函数的名称，GMT 0016-2023中定义。 |
| params | Array&lt;[huksExternalCrypto.HuksExternalCryptoParam](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptoparam-i.md)&gt; &#124; [HuksCryptoExtensionParam](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparam-i.md)[] | 是 | 操作属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | 函数返回的promise。HuksCryptoExtensionResult.resultCode可能具有以下值：0-操作成功34800000 -加密扩展中发生错误。可能原因：1.输入参数非法。2.加密扩展遇到无法解析的错误状态。34800002-UKey驱动程序错误。这意味着UKey驱动程序中发生了未知错误。34800003-UKey PIN未鉴权。请先验证UKey PIN码。34800004 -句柄不存在。可能原因：1.输入的句柄无效。2.huks服务和加密扩展的状态不一致。由于异常，huks服务持有的句柄没有被释放。34800005 -句柄不可用，可能是因为状态不一致在加密扩展和UKey之间。34800007-UKey PIN被锁定，因为已超过允许的最大尝试次数。 |

**示例**

```TypeScript
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

## onGetResourceId

```TypeScript
onGetResourceId(params: HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>
```

回调以获取加密扩展的资源ID。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CryptoExtensionAbility-onGetResourceId(params: HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>--><!--Device-CryptoExtensionAbility-onGetResourceId(params: HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [HuksCryptoExtensionParam](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparam-i.md)[] | 是 | 获取资源ID所需的属性参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | params - 获取资源ID所需的属性参数。 |

**示例**

```TypeScript
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

## onGetUkeyPinAuthState

```TypeScript
onGetUkeyPinAuthState(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |
      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>
```

获取Ukey的PIN码认证状态。使用Promise异步回调。

**起始版本：** 22

<!--Device-CryptoExtensionAbility-onGetUkeyPinAuthState(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>--><!--Device-CryptoExtensionAbility-onGetUkeyPinAuthState(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | string | 是 | 资源句柄。 |
| params | Array&lt;[huksExternalCrypto.HuksExternalCryptoParam](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptoparam-i.md)&gt; &#124; [HuksCryptoExtensionParam](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparam-i.md)[] | 是 | 操作属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise对象。当调用成功时，resultCode为0，HuksCryptoExtensionResult的authState成员非空，为获取的PIN码认证状态。调用失败时，resultCode携带错误码信息。可能返回的错误码值：0 - 调用成功。34800000 - 密钥扩展错误。34800002 - Ukey驱动错误。34800004 - 句柄不存在。34800005 - 句柄不可用。 |

**示例**

```TypeScript
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

## onImportCertificate

```TypeScript
onImportCertificate(handle: string, params: HuksCryptoExtensionParam[],
      certInfo: HuksCryptoExtensionCertInfo): Promise<HuksCryptoExtensionResult>
```

导入指定资源句柄的证书。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CryptoExtensionAbility-onImportCertificate(handle: string, params: HuksCryptoExtensionParam[],      certInfo: HuksCryptoExtensionCertInfo): Promise<HuksCryptoExtensionResult>--><!--Device-CryptoExtensionAbility-onImportCertificate(handle: string, params: HuksCryptoExtensionParam[],      certInfo: HuksCryptoExtensionCertInfo): Promise<HuksCryptoExtensionResult>-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | string | 是 | 导入证书的资源句柄。 |
| params | [HuksCryptoExtensionParam](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparam-i.md)[] | 是 | Indicates the needed properties for the import certificate operation. |
| certInfo | [HuksCryptoExtensionCertInfo](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensioncertinfo-i.md) | 是 | 待导入的证书信息。需指定证书类型（purpose） |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise对象。当调用成功时，resultCode为0，表示导入证书成功。调用失败时，resultCode携带错误码信息，errInfo携带详细错误信息。可能返回的错误码值：0 - 调用成功。34800000 - 密钥扩展错误。34800001 - Ukey不存在。34800002 - Ukey驱动错误。34800004 - 句柄不存在。34800005 - 句柄不可用。 |

**示例**

```TypeScript
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

## onImportWrappedKeyItem

```TypeScript
onImportWrappedKeyItem(handle: string, wrappingHandle: string, params: HuksCryptoExtensionParam[],
      wrappedKey: Uint8Array): Promise<HuksCryptoExtensionResult>
```

用于导入加密封装的密钥对。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CryptoExtensionAbility-onImportWrappedKeyItem(handle: string, wrappingHandle: string, params: HuksCryptoExtensionParam[],      wrappedKey: Uint8Array): Promise<HuksCryptoExtensionResult>--><!--Device-CryptoExtensionAbility-onImportWrappedKeyItem(handle: string, wrappingHandle: string, params: HuksCryptoExtensionParam[],      wrappedKey: Uint8Array): Promise<HuksCryptoExtensionResult>-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | string | 是 | 待导入密钥的资源句柄。 |
| wrappingHandle | string | 是 | 待导入密钥的资源句柄。 |
| params | [HuksCryptoExtensionParam](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparam-i.md)[] | 是 | 导入密钥所需的属性 |
| wrappedKey | Uint8Array | 是 | 封装密钥数据，格式由密钥扩展定义。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise对象。当调用成功时，resultCode为0，表示导入密钥成功。调用失败时，resultCode携带错误码信息，errInfo携带详细错误信息。可能返回的错误码值：0 - 调用成功。34800000 - 密钥扩展错误。34800001 - Ukey不存在。34800002 - Ukey驱动错误。34800004 - 句柄不存在。34800005 - 句柄不可用。 |

**示例**

```TypeScript
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

## onInitSession

```TypeScript
onInitSession(handle: string, params: huks.HuksOptions | HuksCryptoExtensionParams):
      Promise<HuksCryptoExtensionResult>
```

三段式初始化密钥会话操作。使用Promise异步回调。

**起始版本：** 22

<!--Device-CryptoExtensionAbility-onInitSession(handle: string, params: huks.HuksOptions | HuksCryptoExtensionParams):      Promise<HuksCryptoExtensionResult>--><!--Device-CryptoExtensionAbility-onInitSession(handle: string, params: huks.HuksOptions | HuksCryptoExtensionParams):      Promise<HuksCryptoExtensionResult>-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | string | 是 | 资源句柄。 |
| params | [huks.HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) &#124; [HuksCryptoExtensionParams](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparams-i.md) | 是 | 操作属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise对象。当调用成功时，resultCode为0，handle成员非空。调用失败时，resultCode携带错误码信息。可能返回的错误码值：0 - 调用成功。34800000 - 密钥扩展错误。34800002 - Ukey驱动错误。34800003 - Ukey PIN码未认证。34800004 - 句柄不存在。34800005 - 句柄不可用。34800007 - Ukey PIN码被锁。 |

**示例**

```TypeScript
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

## onOpenResource

```TypeScript
onOpenResource(resourceId: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |
     HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>
```

打开资源句柄回调，在加密操作之前需打开资源，获取句柄。注意：返回的句柄必须被onCloseResource关闭。

**起始版本：** 22

<!--Device-CryptoExtensionAbility-onOpenResource(resourceId: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |     HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>--><!--Device-CryptoExtensionAbility-onOpenResource(resourceId: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |     HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resourceId | string | 是 | resourceId表示资源ID |
| params | Array&lt;[huksExternalCrypto.HuksExternalCryptoParam](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptoparam-i.md)&gt; &#124; [HuksCryptoExtensionParam](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparam-i.md)[] | 是 | 操作属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | 函数返回的promise。HuksCryptoExtensionResult.resultCode可能具有以下值：0-操作成功34800000 -加密扩展中发生错误。可能原因：1.输入参数非法。2.加密扩展遇到无法解析的错误状态。34800001-UKey不存在。可能原因：1.UKey已经被移除。2.加密扩展维护了一个错误的UKey状态。34800002-UKey驱动程序错误。这意味着UKey驱动程序中发生了未知错误。34800004-resourceId不存在。这说明resourceId、设备名称、应用名称或容器名称错误。 |

**示例**

```TypeScript
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

## onSetProperty

```TypeScript
onSetProperty(handle: string, propertyId: string, params: HuksCryptoExtensionParam[]):
      Promise<HuksCryptoExtensionResult>
```

根据参数中的handle和propertyId设置属性。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CryptoExtensionAbility-onSetProperty(handle: string, propertyId: string, params: HuksCryptoExtensionParam[]):      Promise<HuksCryptoExtensionResult>--><!--Device-CryptoExtensionAbility-onSetProperty(handle: string, propertyId: string, params: HuksCryptoExtensionParam[]):      Promise<HuksCryptoExtensionResult>-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | string | 是 | 资源句柄。 |
| propertyId | string | 是 | 查找操作的属性名称，是GMT 0016-2023中定义的SKF接口名，要业务针对接口名适配。 |
| params | [HuksCryptoExtensionParam](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparam-i.md)[] | 是 | 操作属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise用于返回HuksCryptoExtensionResult。HuksCryptoExtensionResult.resultCode可能具有以下值：0-操作成功。34800000 -加密扩展中发生错误。可能原因：1.输入参数非法。2.加密扩展遇到无法解析的错误状态。34800002 -调用UKey驱动接口失败。请检查UKey连接和驱动程序状态。34800003-UKey PIN未鉴权。请先验证UKey PIN码。34800004 -句柄不存在。可能原因：1.输入的句柄无效。2.HUKS服务和加密扩展的状态不一致。由于异常，HUKS服务持有的句柄没有释放。34800005 -句柄不可用，可能是因为状态不一致在加密扩展和UKey之间。34800007-UKey PIN被锁定，因为已超过允许的最大尝试次数。 |

**示例**

```TypeScript
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

## onUpdateSession

```TypeScript
onUpdateSession(initHandle: string, params: huks.HuksOptions | HuksCryptoExtensionParams):
      Promise<HuksCryptoExtensionResult>
```

三段式密钥会话更新数据操作。使用Promise异步回调。

**起始版本：** 22

<!--Device-CryptoExtensionAbility-onUpdateSession(initHandle: string, params: huks.HuksOptions | HuksCryptoExtensionParams):      Promise<HuksCryptoExtensionResult>--><!--Device-CryptoExtensionAbility-onUpdateSession(initHandle: string, params: huks.HuksOptions | HuksCryptoExtensionParams):      Promise<HuksCryptoExtensionResult>-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| initHandle | string | 是 | 资源句柄。 |
| params | [huks.HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) &#124; [HuksCryptoExtensionParams](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparams-i.md) | 是 | params indicates the properties of the operation<br>**适用版本：** 26.0.0 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[HuksCryptoExtensionResult](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionresult-i.md)&gt; | Promise对象。当调用成功时，resultCode为0。调用失败时，resultCode携带错误码信息。可能返回的错误码值：0 - 调用成功。34800000 - 密钥扩展错误。34800002 - Ukey驱动错误。34800003 - Ukey PIN码未认证。34800004 - 句柄不存在。34800005 - 句柄不可用。34800007 - Ukey PIN码被锁。 |

**示例**

```TypeScript
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

## 附录

CryptoExtensionAbility不支持以下模块的引用。

| Kit | 模块 |
| --- | --- |
| Ads Kit | [@ohos.advertising.AdComponent](../../apis-ads-kit/arkts-apis/arkts-ads-advertising-adcomponent.md) |
| Ads Kit | [@ohos.advertising.AdsServiceExtensionAbility](../../apis-ads-kit/arkts-apis/arkts-ads-advertising-adsserviceextensionability.md) |
| Ads Kit | [@ohos.advertising.AutoAdComponent](../../apis-ads-kit/arkts-apis/arkts-ads-advertising-autoadcomponent.md) |
| Ads Kit | [@ohos.advertising](../../apis-ads-kit/arkts-apis/arkts-ads-advertising.md) |
| Basic Services Kit | [ai.intelligentVoice](../../apis-basic-services-kit/arkts-apis/arkts-ai-intelligentvoice.md) |
| Mind Spore Lite Kit | [ai.mindSporeLite](../../apis-mind-spore-lite-kit/arkts-apis/arkts-ai-mindsporelite.md) |
| Form Kit | [@ohos.app.form.formAgent](../../apis-form-kit/arkts-apis/arkts-form-app-form-formagent.md) |
| Form Kit | [@ohos.app.form.formBindingData](../../apis-form-kit/arkts-apis/arkts-form-app-form-formbindingdata.md) |
| Form Kit | [@ohos.app.form.FormEditExtensionAbility](../../apis-form-kit/arkts-apis/arkts-form-app-form-formeditextensionability.md) |
| Form Kit | [@ohos.app.form.FormExtensionAbility](../../apis-form-kit/arkts-apis/arkts-form-app-form-formextensionability.md) |
| Form Kit | [@ohos.app.form.formHost](../../apis-form-kit/arkts-apis/arkts-form-app-form-formhost.md) |
| Form Kit | [@ohos.app.form.formInfo](../../apis-form-kit/arkts-apis/arkts-form-app-form-forminfo.md) |
| Form Kit | [@ohos.app.form.formObserver](../../apis-form-kit/arkts-apis/arkts-form-app-form-formobserver.md) |
| Form Kit | [@ohos.app.form.formProvider](../../apis-form-kit/arkts-apis/arkts-form-app-form-formprovider.md) |
| Form Kit | [@ohos.app.form.LiveFormExtensionAbility](../../apis-form-kit/arkts-apis/arkts-form-app-form-liveformextensionability.md) |
| ArkUI | [@ohos.atomicservice.AtomicServiceNavigation](../../apis-arkui/arkts-apis/arkts-arkui-atomicservice-atomicservicenavigation.md) |
| ArkUI | [@ohos.atomicservice.AtomicServiceSearch](../../apis-arkui/arkts-apis/arkts-arkui-atomicservice-atomicservicesearch.md) |
| ArkUI | [@ohos.atomicservice.AtomicServiceTabs](../../apis-arkui/arkts-apis/arkts-arkui-atomicservice-atomicservicetabs.md) |
| ArkUI | [@ohos.atomicservice.AtomicServiceWeb](../../apis-arkui/arkts-apis/arkts-arkui-atomicservice-atomicserviceweb.md) |
| ArkUI | [@ohos.atomicservice.HalfScreenLaunchComponent](../../apis-arkui/arkts-apis/arkts-arkui-atomicservice-halfscreenlaunchcomponent.md) |
| ArkUI | [@ohos.atomicservice.InterstitialDialogAction](../../apis-arkui/arkts-apis/arkts-arkui-atomicservice-interstitialdialogaction.md) |
| ArkUI | [@ohos.atomicservice.NavPushPathHelper](../../apis-arkui/arkts-apis/arkts-arkui-atomicservice-navpushpathhelper.md) |
| Connectivity Kit | [@ohos.bluetooth.a2dp](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-a2dp.md) |
| Connectivity Kit | [@ohos.bluetooth.access](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-access.md) |
| Connectivity Kit | [@ohos.bluetooth.baseProfile](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-baseprofile.md) |
| Connectivity Kit | [@ohos.bluetooth.ble](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-ble.md) |
| Connectivity Kit | [@ohos.bluetooth.common](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-common.md) |
| Connectivity Kit | [@ohos.bluetooth.connection](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-connection.md) |
| Connectivity Kit | [@ohos.bluetooth.constant](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-constant.md) |
| Connectivity Kit | [@ohos.bluetooth](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth.md) |
| Connectivity Kit | [@ohos.bluetooth.hfp](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-hfp.md) |
| Connectivity Kit | [@ohos.bluetooth.hid](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-hid.md) |
| Connectivity Kit | [@ohos.bluetoothManager](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetoothmanager.md) |
| Connectivity Kit | [@ohos.bluetooth.map](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-map.md) |
| Connectivity Kit | [@ohos.bluetooth.opp](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-opp.md) |
| Connectivity Kit | [@ohos.bluetooth.pan](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-pan.md) |
| Connectivity Kit | [@ohos.bluetooth.pbap](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-pbap.md) |
| Connectivity Kit | [@ohos.bluetooth.socket](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-socket.md) |
| Connectivity Kit | [@ohos.bluetooth.wearDetection](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-weardetection.md) |
| Calendar Kit | [@ohos.calendarManager](../../apis-calendar-kit/arkts-apis/arkts-calendar-calendarmanager.md) |
| Connectivity Kit | [@ohos.connectedTag](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-connectedtag.md) |
| Contacts Kit | [@ohos.contact](../../apis-contacts-kit/arkts-apis/arkts-contacts-contact.md) |
| Ability Kit | [@ohos.distributedBundle](../../apis-ability-kit/arkts-apis/arkts-ability-distributedbundle.md) |
| Distributed Service Kit | [@ohos.distributedDeviceManager](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager.md) |
| Distributed Service Kit | [@ohos.distributedHardware.deviceManager](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributedhardware-devicemanager.md) |
| Distributed Service Kit | [@ohos.distributedHardware.hardwareManager](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributedhardware-hardwaremanager.md) |
| Mechanic Kit | [@ohos.distributedHardware.mechanicManager](../../apis-mechanic-kit/arkts-apis/arkts-mechanic-distributedhardware-mechanicmanager.md) |
| Ability Kit | [@ohos.distributedMissionManager](../../apis-ability-kit/arkts-apis/arkts-ability-distributedmissionmanager.md) |
| Distributed Service Kit | [@ohos.distributedsched.abilityConnectionManager](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributedsched-abilityconnectionmanager.md) |
| Distributed Service Kit | [@ohos.distributedsched.linkEnhance](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributedsched-linkenhance.md) |
| Distributed Service Kit | [@ohos.distributedsched.proxyChannelManager](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributedsched-proxychannelmanager.md) |
| Data Protection Kit | [@ohos.dlpPermission](../../apis-data-protection-kit/arkts-apis/arkts-dataprotection-dlppermission.md) |
| MDM Kit | [@ohos.enterprise.accountManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-accountmanager.md) |
| MDM Kit | [@ohos.enterprise.adminManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-adminmanager.md) |
| MDM Kit | [@ohos.enterprise.applicationManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-applicationmanager.md) |
| MDM Kit | [@ohos.enterprise.bluetoothManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-bluetoothmanager.md) |
| MDM Kit | [@ohos.enterprise.browser](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-browser.md) |
| MDM Kit | [@ohos.enterprise.bundleManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-bundlemanager.md) |
| MDM Kit | [@ohos.enterprise.common](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-common.md) |
| MDM Kit | [@ohos.enterprise.dateTimeManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-datetimemanager.md) |
| MDM Kit | [@ohos.enterprise.deviceControl](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-devicecontrol.md) |
| MDM Kit | [@ohos.enterprise.deviceInfo](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-deviceinfo.md) |
| MDM Kit | [@ohos.enterprise.deviceSettings](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-devicesettings.md) |
| MDM Kit | [@ohos.enterprise.EnterpriseAdminExtensionAbility](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-enterpriseadminextensionability.md) |
| MDM Kit | [@ohos.enterprise.locationManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-locationmanager.md) |
| MDM Kit | [@ohos.enterprise.networkManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-networkmanager.md) |
| MDM Kit | [@ohos.enterprise.restrictions](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-restrictions.md) |
| MDM Kit | [@ohos.enterprise.securityManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-securitymanager.md) |
| MDM Kit | [@ohos.enterprise.systemManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-systemmanager.md) |
| MDM Kit | [@ohos.enterprise.telephonyManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-telephonymanager.md) |
| MDM Kit | [@ohos.enterprise.usbManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-usbmanager.md) |
| MDM Kit | [@ohos.enterprise.wifiManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-wifimanager.md) |
| Location Kit | [@ohos.geolocation](../../apis-location-kit/arkts-apis/arkts-location-geolocation.md) |
| Location Kit | [@ohos.geoLocationManager](../../apis-location-kit/arkts-apis/arkts-location-geolocationmanager.md) |
| ArkUI | [@ohos.mediaquery](../../apis-arkui/arkts-apis/arkts-arkui-mediaquery.md) |
| arkui | [mediaquery.static](../../apis-arkui/arkts-apis/arkts-mediaquery-static.md) |
| Audio Kit | [@ohos.multimedia.audio](../../apis-audio-kit/arkts-apis/arkts-audio-multimedia-audio.md) |
| Audio Kit | [@ohos.multimedia.audioHaptic](../../apis-audio-kit/arkts-apis/arkts-audio-multimedia-audiohaptic.md) |
| AVSession Kit | [@ohos.multimedia.avCastPicker](../../apis-avsession-kit/arkts-apis/arkts-avsession-multimedia-avcastpicker.md) |
| AVSession Kit | [@ohos.multimedia.avCastPickerParam](../../apis-avsession-kit/arkts-apis/arkts-avsession-multimedia-avcastpickerparam.md) |
| Avsession Kit | [multimedia.avCastPicker.static](../../apis-avsession-kit/arkts-apis/arkts-multimedia-avcastpicker-static.md) |
| AVSession Kit | [@ohos.multimedia.avInputCastPicker](../../apis-avsession-kit/arkts-apis/arkts-avsession-multimedia-avinputcastpicker.md) |
| Avsession Kit | [multimedia.avInputCastPicker.static](../../apis-avsession-kit/arkts-apis/arkts-multimedia-avinputcastpicker-static.md) |
| AVSession Kit | [@ohos.multimedia.avsession](../../apis-avsession-kit/arkts-apis/arkts-avsession-multimedia-avsession.md) |
| Audio Kit | [@ohos.multimedia.avVolumePanel](../../apis-audio-kit/arkts-apis/arkts-audio-multimedia-avvolumepanel.md) |
| Audio Kit | [multimedia.avVolumePanel.static](../../apis-audio-kit/arkts-apis/arkts-multimedia-avvolumepanel-static.md) |
| Camera Kit | [@ohos.multimedia.camera](../../apis-camera-kit/arkts-apis/arkts-camera-multimedia-camera.md) |
| Camera Kit | [@ohos.multimedia.cameraPicker](../../apis-camera-kit/arkts-apis/arkts-camera-multimedia-camerapicker.md) |
| DRM Kit | [@ohos.multimedia.drm](../../apis-drm-kit/arkts-apis/arkts-drm-multimedia-drm.md) |
| Image Kit | [@ohos.multimedia.image](../../apis-image-kit/arkts-apis/arkts-image-multimedia-image.md) |
| Media Kit | [@ohos.multimedia.media](../../apis-media-kit/arkts-apis/arkts-media-multimedia-media.md) |
| Media Library Kit | [multimedia.movingphotoview](../../apis-media-library-kit/arkts-apis/arkts-multimedia-movingphotoview.md) |
| Image Kit | [@ohos.multimedia.sendableImage](../../apis-image-kit/arkts-apis/arkts-image-multimedia-sendableimage.md) |
| Audio Kit | [@ohos.multimedia.systemSoundManager](../../apis-audio-kit/arkts-apis/arkts-audio-multimedia-systemsoundmanager.md) |
| Image Kit | [@ohos.multimedia.videoProcessingEngine](../../apis-image-kit/arkts-apis/arkts-image-multimedia-videoprocessingengine.md) |
| Network Kit | [@ohos.net.connection](../../apis-network-kit/arkts-apis/arkts-network-net-connection.md) |
| Network Kit | [@ohos.net.eap](../../apis-network-kit/arkts-apis/arkts-network-net-eap.md) |
| Network Kit | [@ohos.net.ethernet](../../apis-network-kit/arkts-apis/arkts-network-net-ethernet.md) |
| Network Kit | [@ohos.net.http](../../apis-network-kit/arkts-apis/arkts-network-net-http.md) |
| Network Kit | [@ohos.net.mdns](../../apis-network-kit/arkts-apis/arkts-network-net-mdns.md) |
| Network Kit | [@ohos.net.netFirewall](../../apis-network-kit/arkts-apis/arkts-network-net-netfirewall.md) |
| Network Kit | [@ohos.net.networkSecurity](../../apis-network-kit/arkts-apis/arkts-network-net-networksecurity.md) |
| Network Kit | [@ohos.net.policy](../../apis-network-kit/arkts-apis/arkts-network-net-policy.md) |
| Network Kit | [@ohos.net.sharing](../../apis-network-kit/arkts-apis/arkts-network-net-sharing.md) |
| Network Kit | [@ohos.net.statistics](../../apis-network-kit/arkts-apis/arkts-network-net-statistics.md) |
| Network Kit | [@ohos.net.vpn](../../apis-network-kit/arkts-apis/arkts-network-net-vpn.md) |
| Network Kit | [@ohos.net.vpnExtension](../../apis-network-kit/arkts-apis/arkts-network-net-vpnextension.md) |
| Network Kit | [@ohos.net.webSocket](../../apis-network-kit/arkts-apis/arkts-network-net-websocket.md) |
| Connectivity Kit | [@ohos.nfc.cardEmulation](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-nfc-cardemulation.md) |
| Connectivity Kit | [@ohos.nfc.controller](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-nfc-controller.md) |
| Connectivity Kit | [@ohos.nfc.tag](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-nfc-tag.md) |
| Basic Services Kit | [@ohos.pasteboard](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-pasteboard.md) |
| ArkUI | [@ohos.PiPWindow](../../apis-arkui/arkts-apis/arkts-arkui-pipwindow.md) |
| Basic Services Kit | [@ohos.scan](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-scan.md) |
| Basic Services Kit | [screenLock](../../apis-basic-services-kit/arkts-apis/arkts-screenlock.md) |
| ArkUI | [@ohos.screenshot](../../apis-arkui/arkts-apis/arkts-arkui-screenshot.md) |
| Basic Services Kit | [settings](../../apis-basic-services-kit/arkts-apis/arkts-settings.md) |
| Telephony Kit | [@ohos.telephony.call](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-call.md) |
| Telephony Kit | [@ohos.telephony.data](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-data.md) |
| Telephony Kit | [@ohos.telephony.esim](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-esim.md) |
| Telephony Kit | [@ohos.telephony.observer](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-observer.md) |
| Telephony Kit | [@ohos.telephony.radio](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-radio.md) |
| Telephony Kit | [@ohos.telephony.sim](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-sim.md) |
| Telephony Kit | [@ohos.telephony.sms](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-sms.md) |
| Telephony Kit | [@ohos.telephony.vcard](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-vcard.md) |
| ArkTS | [@ohos.transfer](../../apis-arkts/arkts-apis/arkts-arkts-transfer.md) |
| Basic Services Kit | [@ohos.wallpaper](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-wallpaper.md) |
| Basic Services Kit | [@ohos.WallpaperExtensionAbility](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-wallpaperextensionability.md) |
| Ability Kit | [@ohos.wantAgent](../../apis-ability-kit/arkts-apis/arkts-ability-wantagent.md) |
| ArkWeb | [@ohos.web.netErrorList](../../apis-arkweb/arkts-apis/arkts-arkweb-web-neterrorlist.md) |
| arkweb | [web.netErrorList.static](../../apis-arkweb/arkts-apis/arkts-web-neterrorlist-static.md) |
| ArkWeb | [@ohos.web.WebNativeMessagingExtensionAbility](../../apis-arkweb/arkts-apis/arkts-arkweb-web-webnativemessagingextensionability.md) |
| arkweb | [web.WebNativeMessagingExtensionAbility.static](../../apis-arkweb/arkts-apis/arkts-web-webnativemessagingextensionability-static.md) |
| ArkWeb | [@ohos.web.WebNativeMessagingExtensionContext](../../apis-arkweb/arkts-apis/arkts-arkweb-web-webnativemessagingextensioncontext.md) |
| arkweb | [web.WebNativeMessagingExtensionContext.static](../../apis-arkweb/arkts-apis/arkts-web-webnativemessagingextensioncontext-static.md) |
| ArkWeb | [@ohos.web.webNativeMessagingExtensionManager](../../apis-arkweb/arkts-apis/arkts-arkweb-web-webnativemessagingextensionmanager.md) |
| arkweb | [web.webNativeMessagingExtensionManager.static](../../apis-arkweb/arkts-apis/arkts-web-webnativemessagingextensionmanager-static.md) |
| ArkWeb | [@ohos.web.webview](../../apis-arkweb/arkts-apis/arkts-arkweb-web-webview.md) |
| arkweb | [web.webview.static](../../apis-arkweb/arkts-apis/arkts-web-webview-static.md) |
| Connectivity Kit | [@ohos.wifi](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-wifi.md) |
| Connectivity Kit | [@ohos.wifiext](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-wifiext.md) |
| Connectivity Kit | [@ohos.wifiManager](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-wifimanager.md) |
| Connectivity Kit | [@ohos.wifiManagerExt](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-wifimanagerext.md) |
