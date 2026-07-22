# Cipher

提供加解密的算法操作功能，按序调用本类中的[init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init)、[update()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#update)、[doFinal()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#dofinal)方法，可以实现对称加密/对称解密/非对称加密/非对称解密。

完整的加解密流程示例可参考[开发指南](../../../security/CryptoArchitectureKit/crypto-encryption-decryption-overview.md)。

一次完整的加/解密流程在对称加密和非对称加密中略有不同：

- 对称加解密：init为必选，update为可选（且允许多次update加/解密大数据），doFinal为必选；doFinal结束后可以重新init开始新一轮加/解密流程。  
- RSA、SM2非对称加解密：init为必选，不支持update操作，doFinal为必选（允许连续多次doFinal加/解密大数据）；RSA不支持重复init，切换加解密模式或填充方式时，需要重新创建Cipher对象。

**起始版本：** 9

<!--Device-cryptoFramework-interface Cipher--><!--Device-cryptoFramework-interface Cipher-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本9-11：SystemCapability.Security.CryptoFramework

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## doFinal

```TypeScript
doFinal(data: DataBlob, callback: AsyncCallback<DataBlob>): void
```

完成加密操作，对输入数据进行加密或解密，然后反馈输出数据。加密操作完成后，数据无法更新。使用Callback异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Cipher-doFinal(data: DataBlob, callback: AsyncCallback<DataBlob>): void--><!--Device-Cipher-doFinal(data: DataBlob, callback: AsyncCallback<DataBlob>): void-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [DataBlob](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-cert-datablob-i.md) | 是 | 表示最终要加密或解密的数据。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;DataBlob&gt; | 是 | 回调函数。当加/解密成功时，err为undefined，data为加/解密结果DataBlob；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。可能的原因：<br>1. 数据过长。<br>**适用版本：** 22+ |

## doFinal

```TypeScript
doFinal(data: DataBlob | null, callback: AsyncCallback<DataBlob>): void
```

（1）在对称加解密中**doFinal**用于处理剩余数据和本次传入的数据，并最终结束加密或解密操作，使用callback异步回调函数获取加密或解密后的数据。如果数据量较小，可以在**doFinal**中一次性传入数据，而不使用**update**；如果在本次加解密流程中已经使用**update**传入过数据，可以在**doFinal**的data参数处传入null。根据对称加解密的模式不同，**doFinal**的输出有以下区别：  
- 在GCM和CCM模式的对称加密中，一次加密流程中，将每次**update**和**doFinal**的结果拼接起来，会得到“密文 + authTag”。GCM模式下，authTag为末尾的16字节；CCM模式下，authTag为末尾的12字节。其余部分均为密文。如果**doFinal**的data参数传入null，则**doFinal**的结果就是authTag。解密时，authTag需要填入[GcmParamsSpec](arkts-cryptoarchitecture-cryptoframework-gcmparamsspec-i.md)或[CcmParamsSpec](arkts-cryptoarchitecture-cryptoframework-ccmparamsspec-i.md)，密文作为解密时的data参数。  
- 对于其他模式的对称加解密及GCM和CCM模式的加解密：每次加/解密流程中，**update**和**doFinal**的结果拼接起来，得到完整的明文或密文。（2）在RSA、SM2非对称加解密中，**doFinal**加密或解密本次传入的数据，使用callback异步回调函数获取加密或者解密数据。如果数据量较大，可以多次调用**doFinal**，拼接结果得到完整的明文/密文。
> **说明：**  
>  
> 1.对称加解密中，调用**doFinal**标志着一次加解密流程已经完成，即[Cipher](arkts-cryptoarchitecture-cryptoframework-cipher-i.md)实例的状态被清除，  
> 因此当后续开启新一轮加解密流程时，需要重新调用**init**并传入完整的参数列表进行初始化。 即使是对同一个Cipher实例，采用同样的对称  
> 密钥，进行加密然后解密，则解密中调用**init**的时候仍需填写params参数，而不能直接省略为null。  
> 如果遇到解密失败，需检查加解密数据和**init**时的参数是否匹配，包括GCM模式下加密得到的authTag是否填入解密时的GcmParamsSpec等。  
> **doFinal**的结果可能为null，因此使用.data字段访问**doFinal**结果的具体数据前，请记得先判断结果是否为null，避免产生异常。  
> 2.对于加密，CFB、OFB和CTR模式，如果**doFinal**传null，则返回结果为null。  
> 3.对于解密，GCM、CCM、CFB、OFB和CTR模式，如果**doFinal**传null，则返回结果为null；对于解密，其他模式，如果明文是加密块大小的  
> 整倍数，调用**update**传入所有密文，调用**doFinal**传null，则返回结果为null。  
> 4.非对称加解密时多次**doFinal**操作的示例代码请参阅  
> [使用RSA非对称密钥对按段加密和解密](../../../security/CryptoArchitectureKit/crypto-rsa-asym-encrypt-decrypt-by-segment.md)。  
> SM2和RSA的操作类似。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Cipher-doFinal(data: DataBlob | null, callback: AsyncCallback<DataBlob>): void--><!--Device-Cipher-doFinal(data: DataBlob | null, callback: AsyncCallback<DataBlob>): void-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本10-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [DataBlob](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-cert-datablob-i.md) \| null | 是 | 要加密或解密的数据。在对称加解密中，这个参数可以是**null**，但是**{data: Uint8Array()}**不能传入。在API版本10之前，仅支持**DataBlob**。从API版本10开始，还支持**null**。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;DataBlob&gt; | 是 | 回调函数。当加/解密成功时，err为undefined，data为加/解密结果DataBlob；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。可能的原因：<br>1. 数据过长。<br>**适用版本：** 22+ |

**示例：**

更多加解密流程的完整示例请参考[加解密开发指导](../../security/CryptoArchitectureKit/crypto-aes-sym-encrypt-decrypt-gcm.md)。

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { buffer } from '@kit.ArkTS';

function generateRandom(len: number) {
  let rand = cryptoFramework.createRandom();
  let generateRandSync = rand.generateRandomSync(len);
  return generateRandSync;
}

function genGcmParamsSpec() {
  let ivBlob = generateRandom(12);
  let arr = [1, 2, 3, 4, 5, 6, 7, 8];
  let dataAad = new Uint8Array(arr);
  let aadBlob: cryptoFramework.DataBlob = { data: dataAad };
  arr = [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0];
  let dataTag = new Uint8Array(arr);
  let tagBlob: cryptoFramework.DataBlob = {
    data: dataTag
  };
  let gcmParamsSpec: cryptoFramework.GcmParamsSpec = {
    iv: ivBlob,
    aad: aadBlob,
    authTag: tagBlob,
    algName: 'GcmParamsSpec'
  };
  return gcmParamsSpec;
}

function cipherByCallback() {
  let gcmParams = genGcmParamsSpec();
  let symKeyGenerator = cryptoFramework.createSymKeyGenerator('AES128');
  let cipher = cryptoFramework.createCipher('AES128|GCM|PKCS7');
  symKeyGenerator.generateSymKey((err, symKey) => {
    cipher.init(cryptoFramework.CryptoMode.ENCRYPT_MODE, symKey, gcmParams, (err) => {
      let message = 'This is a test';
      let plainText: cryptoFramework.DataBlob = { data: new Uint8Array(buffer.from(message, 'utf-8').buffer) };
      cipher.update(plainText, (err, encryptUpdate) => {
        cipher.doFinal(null, (err, tag) => {
          gcmParams.authTag = tag;
          console.info('encryptUpdate plainText：' + encryptUpdate.data);
        });
      });
    });
  });
}

```

## doFinal

```TypeScript
doFinal(data: DataBlob): Promise<DataBlob>
```

完成加密操作，对输入数据进行加密或解密，然后反馈输出数据。加密操作完成后，数据无法更新。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Cipher-doFinal(data: DataBlob): Promise<DataBlob>--><!--Device-Cipher-doFinal(data: DataBlob): Promise<DataBlob>-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [DataBlob](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-cert-datablob-i.md) | 是 | 表示最终要加密或解密的数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;DataBlob&gt; | Promise对象，返回加密或解密的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。可能的原因：<br>1. 数据过长。<br>**适用版本：** 22+ |

## doFinal

```TypeScript
doFinal(data: DataBlob | null): Promise<DataBlob>
```

（1）在对称加解密中，**doFinal**加/解密（分组模式产生的）剩余数据和本次传入的数据，最后结束加密或者解密数据操作，使用Promise异步回调获取加密或者解密数据。如果数据量较小，可以在**doFinal**中一次性传入数据，而不使用**update**；如果在本次加解密流程中，已经使用**update**传入过数据，可以在**doFinal**的data参数处传入null。根据对称加解密的模式不同，**doFinal**的输出有如下区别：  
- 对于GCM和CCM模式的对称加密：一次加密流程中，如果将每一次**update**和**doFinal**的结果拼接起来，会得到“密文+authTag”，即末尾的16字节（GCM模式）或12字节（CCM模式）是authTag，而其余部分均为密文。（也就是说，如果**doFinal**的data参数传入null，则**doFinal**的结果就是authTag）authTag需要填入解密时的[GcmParamsSpec](arkts-cryptoarchitecture-cryptoframework-gcmparamsspec-i.md)或[CcmParamsSpec](arkts-cryptoarchitecture-cryptoframework-ccmparamsspec-i.md)；密文则作为解密时的入参data。  
- 对于其他模式的对称加解密及GCM和CCM模式的对称解密：一次加解密流程中，每次**update**和**doFinal**的结果拼接起来，得到完整的明文或密文。（2）在RSA和SM2非对称加解密中，使用**doFinal**方法加解密传入的数据，并使用Promise异步回调获取加密或解密结果。如果数据量较大，可以多次调用**doFinal**，拼接结果以获得完整的明文或密文。
> **说明：**  
>  
> 1.对称加解密中，调用**doFinal**标志着一次加解密流程已经完成，即[Cipher](arkts-cryptoarchitecture-cryptoframework-cipher-i.md)实例的状态被清除，  
> 因此当后续开启新一轮加解密流程时，需要重新调用**init**并传入完整的参数列表进行初始化。 即使是对同一个Cipher实例，采用同样的对称  
> 密钥，进行加密然后解密，则解密中调用**init**的时候仍需填写params参数，而不能直接省略为null。  
> 如果遇到解密失败，需检查加解密数据和**init**时的参数是否匹配，包括GCM模式下加密得到的authTag是否填入解密时的GcmParamsSpec等。  
> **doFinal**的结果可能为null，因此使用.data字段访问**doFinal**结果的具体数据前，请记得先判断结果是否为null，避免产生异常。  
> 2.对于加密，CFB、OFB和CTR模式，如果**doFinal**传null，则返回结果为null。  
> 3.对于解密，GCM、CCM、CFB、OFB和CTR模式，如果**doFinal**传null，则返回结果为null；对于解密，其他模式，如果明文是加密块大小的  
> 整倍数，调用**update**传入所有密文，调用**doFinal**传null，则返回结果为null。  
> 4.非对称加解密时多次**doFinal**操作的示例代码请参阅  
> [使用RSA非对称密钥对按段加密和解密](../../../security/CryptoArchitectureKit/crypto-rsa-asym-encrypt-decrypt-by-segment.md)。  
> SM2和RSA的操作类似。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Cipher-doFinal(data: DataBlob | null): Promise<DataBlob>--><!--Device-Cipher-doFinal(data: DataBlob | null): Promise<DataBlob>-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本10-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [DataBlob](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-cert-datablob-i.md) \| null | 是 | 要加密或解密的数据。可以为**null**，但不能为{data:Uint8Array(0)}。在API版本10之前的版本中，仅支持**DataBlob**。从API版本10开始，也支持**null**。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;DataBlob&gt; | Promise对象，返回剩余数据的加/解密结果DataBlob。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。可能的原因：<br>1. 数据过长。<br>**适用版本：** 22+ |

**示例：**

此外，更多加解密流程的完整示例可参考[加解密开发指导](../../security/CryptoArchitectureKit/crypto-aes-sym-encrypt-decrypt-gcm.md)。

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { buffer } from '@kit.ArkTS';

function generateRandom(len: number) {
  let rand = cryptoFramework.createRandom();
  let generateRandSync = rand.generateRandomSync(len);
  return generateRandSync;
}

function genGcmParamsSpec() {
  let ivBlob = generateRandom(12);
  let arr = [1, 2, 3, 4, 5, 6, 7, 8];
  let dataAad = new Uint8Array(arr);
  let aadBlob: cryptoFramework.DataBlob = { data: dataAad };
  arr = [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0];
  let dataTag = new Uint8Array(arr);
  let tagBlob: cryptoFramework.DataBlob = {
    data: dataTag
  };
  let gcmParamsSpec: cryptoFramework.GcmParamsSpec = {
    iv: ivBlob,
    aad: aadBlob,
    authTag: tagBlob,
    algName: 'GcmParamsSpec'
  };
  return gcmParamsSpec;
}

async function cipherByPromise() {
  let gcmParams = genGcmParamsSpec();
  let symKeyGenerator = cryptoFramework.createSymKeyGenerator('AES128');
  let cipher = cryptoFramework.createCipher('AES128|GCM|PKCS7');
  let symKey = await symKeyGenerator.generateSymKey();
  await cipher.init(cryptoFramework.CryptoMode.ENCRYPT_MODE, symKey, gcmParams);
  let message = 'This is a test';
  let plainText: cryptoFramework.DataBlob = { data: new Uint8Array(buffer.from(message, 'utf-8').buffer) };
  let encryptUpdate = await cipher.update(plainText);
  gcmParams.authTag = await cipher.doFinal(null);
  console.info('encryptUpdate plainText: ' + encryptUpdate.data);
}

```

## doFinalSync

```TypeScript
doFinalSync(data: DataBlob | null): DataBlob
```

（1）在对称加解密中，**doFinal**加/解密（分组模式产生的）剩余数据和本次传入的数据，最后结束加密或者解密数据操作，使用Promise异步回调获取加密或者解密数据。如果数据量较小，可以在**doFinal**中一次性传入数据，而不使用**update**；如果在本次加解密流程中，已经使用**update**传入过数据，可以在**doFinal**的data参数处传入null。根据对称加解密的模式不同，**doFinal**的输出有如下区别：  
- 对于GCM和CCM模式的对称加密：一次加密流程中，如果将每一次**update**和**doFinal**的结果拼接起来，会得到“密文+authTag”，即末尾的16字节（GCM模式）或12字节（CCM模式）是authTag，而其余部分均为密文。（也就是说，如果**doFinal**的data参数传入null，则**doFinal**的结果就是authTag）authTag需要填入解密时的[GcmParamsSpec](arkts-cryptoarchitecture-cryptoframework-gcmparamsspec-i.md)或[CcmParamsSpec](arkts-cryptoarchitecture-cryptoframework-ccmparamsspec-i.md)；密文则作为解密时的入参data。  
- 对于其他模式的对称加解密及GCM和CCM模式的对称解密：一次加解密流程中，每次**update**和**doFinal**的结果拼接起来，得到完整的明文或密文。（2）在RSA和SM2非对称加解密中，使用**doFinal**方法加解密传入的数据，并使用Promise异步回调获取加密或解密结果。如果数据量较大，可以多次调用**doFinal**，拼接结果以获得完整的明文或密文。

关于其他注意事项，请参见[doFinal()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#dofinal)中的**说明：**。

<br><br>**说明：**<br>建议优先使用异步API{@link doFinal}。同步API可能因系统繁忙、高负载等原因耗时较长而阻塞主线程。因此建议在子线程中调用同步API，以避免阻塞主线程。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Cipher-doFinalSync(data: DataBlob | null): DataBlob--><!--Device-Cipher-doFinalSync(data: DataBlob | null): DataBlob-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Cipher

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [DataBlob](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-cert-datablob-i.md) \| null | 是 | 待加密或解密的数据。在对称加解密中可以为**null**， 但不能传入{data: Uint8Array(0)}。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataBlob](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-cert-datablob-i.md) | 加密或解密后的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。可能的原因：<br>1. 数据过长。<br>**适用版本：** 22+ |

**示例：**

此外，更多加解密流程的完整示例可参考[加解密开发指导](../../security/CryptoArchitectureKit/crypto-aes-sym-encrypt-decrypt-gcm.md)。

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { buffer } from '@kit.ArkTS';

function generateRandom(len: number) {
  let rand = cryptoFramework.createRandom();
  let generateRandSync = rand.generateRandomSync(len);
  return generateRandSync;
}

function genGcmParamsSpec() {
  let ivBlob = generateRandom(12);
  let arr = [1, 2, 3, 4, 5, 6, 7, 8];
  let dataAad = new Uint8Array(arr);
  let aadBlob: cryptoFramework.DataBlob = { data: dataAad };
  arr = [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0];
  let dataTag = new Uint8Array(arr);
  let tagBlob: cryptoFramework.DataBlob = {
    data: dataTag
  };
  let gcmParamsSpec: cryptoFramework.GcmParamsSpec = {
    iv: ivBlob,
    aad: aadBlob,
    authTag: tagBlob,
    algName: 'GcmParamsSpec'
  };
  return gcmParamsSpec;
}

async function cipherBySync() {
  let gcmParams = genGcmParamsSpec();
  let symKeyGenerator = cryptoFramework.createSymKeyGenerator('AES128');
  let cipher = cryptoFramework.createCipher('AES128|GCM|PKCS7');
  let symKey = await symKeyGenerator.generateSymKey();
  await cipher.init(cryptoFramework.CryptoMode.ENCRYPT_MODE, symKey, gcmParams);
  let message = 'This is a test';
  let plainText: cryptoFramework.DataBlob = { data: new Uint8Array(buffer.from(message, 'utf-8').buffer) };
  let encryptUpdate = cipher.updateSync(plainText);
  gcmParams.authTag = cipher.doFinalSync(null);
  console.info('encryptUpdate plainText: ' + encryptUpdate.data);
}

```

## getCipherSpec

```TypeScript
getCipherSpec(itemType: CipherSpecItem): string | Uint8Array
```

获取加解密参数。当前只支持RSA算法和SM2算法，从API version 11开始，支持SM2算法获取加解密参数。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Cipher-getCipherSpec(itemType: CipherSpecItem): string | Uint8Array--><!--Device-Cipher-getCipherSpec(itemType: CipherSpecItem): string | Uint8Array-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本10-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| itemType | [CipherSpecItem](arkts-cryptoarchitecture-cryptoframework-cipherspecitem-e.md) | 是 | 用于指定需要获取的加解密参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回获取的加解密参数值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | 该操作不支持。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。可能的原因：<br>1. 不支持的itemType。<br>**适用版本：** 22+ |

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

function testGetCipherSpec() {
  let cipher = cryptoFramework.createCipher('RSA2048|PKCS1_OAEP|SHA256|MGF1_SHA1');
  let mdName = cipher.getCipherSpec(cryptoFramework.CipherSpecItem.OAEP_MD_NAME_STR);
  console.info('getCipherSpec: mdName =' + mdName);
}

```

## init

```TypeScript
init(opMode: CryptoMode, key: Key, params: ParamsSpec, callback: AsyncCallback<void>): void
```

使用给定的加密模式、密钥和参数初始化加密操作。

init、update和doFinal必须配合使用，其中init和doFinal是必选的，update是可选的。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Cipher-init(opMode: CryptoMode, key: Key, params: ParamsSpec, callback: AsyncCallback<void>): void--><!--Device-Cipher-init(opMode: CryptoMode, key: Key, params: ParamsSpec, callback: AsyncCallback<void>): void-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| opMode | [CryptoMode](arkts-cryptoarchitecture-cryptoframework-cryptomode-e.md) | 是 | 要执行的操作（加密或解密） |
| key | [Key](../../apis-input-kit/arkts-apis/arkts-input-multimodalinput-keyevent-key-i.md) | 是 | 用于加密或解密的密钥 |
| params | [ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md) | 是 | IV等算法参数 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当加解密初始化成功时，err为undefined；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。可能的原因：<br>1. 无效的opMode值；<br>2. 无效的iv长度；<br>3. 无效的密钥长度。<br>**适用版本：** 22+ |

## init

```TypeScript
init(opMode: CryptoMode, key: Key, params: ParamsSpec | null, callback: AsyncCallback<void>): void
```

初始化加解密的[cipher](arkts-cryptoarchitecture-cryptoframework-cipher-i.md)对象，使用callback异步回调获取结果。

init、update、doFinal为三段式接口，需要成组使用。其中init和doFinal必选，update可选。

必须在使用[createCipher](arkts-cryptoarchitecture-cryptoframework-createcipher-f.md#createcipher)创建[Cipher](arkts-cryptoarchitecture-cryptoframework-cipher-i.md)实例后，才能使用本函数。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Cipher-init(opMode: CryptoMode, key: Key, params: ParamsSpec | null, callback: AsyncCallback<void>): void--><!--Device-Cipher-init(opMode: CryptoMode, key: Key, params: ParamsSpec | null, callback: AsyncCallback<void>): void-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本10-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| opMode | [CryptoMode](arkts-cryptoarchitecture-cryptoframework-cryptomode-e.md) | 是 | 加密或者解密模式。 |
| key | [Key](../../apis-input-kit/arkts-apis/arkts-input-multimodalinput-keyevent-key-i.md) | 是 | 指定加密或解密的密钥。 |
| params | [ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md) \| null | 是 | 指定加密或解密的参数，对于ECB等没有参数的算法模式，请传入null。API 10之前只支持ParamsSpec， API 10之后增加支持null。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当加解密初始化成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。可能的原因：<br>1. 无效的opMode值；<br>2. 无效的iv长度；<br>3. 无效的密钥长度。<br>**适用版本：** 22+ |

## init

```TypeScript
init(opMode: CryptoMode, key: Key, params: ParamsSpec): Promise<void>
```

使用给定的加密模式、密钥和参数初始化加密操作。使用Promise异步回调。

init、update和doFinal必须配合使用，其中init和doFinal是必选的，update是可选的。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Cipher-init(opMode: CryptoMode, key: Key, params: ParamsSpec): Promise<void>--><!--Device-Cipher-init(opMode: CryptoMode, key: Key, params: ParamsSpec): Promise<void>-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| opMode | [CryptoMode](arkts-cryptoarchitecture-cryptoframework-cryptomode-e.md) | 是 | 要执行的操作（加密或解密） |
| key | [Key](../../apis-input-kit/arkts-apis/arkts-input-multimodalinput-keyevent-key-i.md) | 是 | 用于加密或解密的密钥 |
| params | [ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md) | 是 | IV等算法参数 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。可能的原因：<br>1. 无效的opMode值；<br>2. 无效的iv长度；<br>3. 无效的密钥长度。<br>**适用版本：** 22+ |

## init

```TypeScript
init(opMode: CryptoMode, key: Key, params: ParamsSpec | null): Promise<void>
```

初始化加解密的cipher对象。使用Promise异步回调。

init、update、doFinal为三段式接口，需要成组使用。其中init和doFinal必选，update可选。

必须在使用[createCipher](arkts-cryptoarchitecture-cryptoframework-createcipher-f.md#createcipher)创建[Cipher](arkts-cryptoarchitecture-cryptoframework-cipher-i.md)实例后，才能使用本函数。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Cipher-init(opMode: CryptoMode, key: Key, params: ParamsSpec | null): Promise<void>--><!--Device-Cipher-init(opMode: CryptoMode, key: Key, params: ParamsSpec | null): Promise<void>-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本10-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| opMode | [CryptoMode](arkts-cryptoarchitecture-cryptoframework-cryptomode-e.md) | 是 | 加密或者解密模式。 |
| key | [Key](../../apis-input-kit/arkts-apis/arkts-input-multimodalinput-keyevent-key-i.md) | 是 | 指定加密或解密的密钥。 |
| params | [ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md) \| null | 是 | 指定加密或解密的参数，对于ECB等没有参数的算法模式，请传入null。API 10之前仅支持ParamsSpec，从API 10开始增加对null的支持。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。可能的原因：<br>1. 无效的opMode值；<br>2. 无效的iv长度；<br>3. 无效的密钥长度。<br>**适用版本：** 22+ |

## initSync

```TypeScript
initSync(opMode: CryptoMode, key: Key, params: ParamsSpec | null): void
```

初始化加解密的[cipher](arkts-cryptoarchitecture-cryptoframework-cipher-i.md)对象，此API以同步方式返回结果。

initSync、updateSync、doFinalSync为三段式接口，需要成组使用。其中initSync和doFinalSync必选，updateSync可选。

必须在使用[createCipher](arkts-cryptoarchitecture-cryptoframework-createcipher-f.md#createcipher)创建[Cipher](arkts-cryptoarchitecture-cryptoframework-cipher-i.md)实例后，才能使用本函数。

<br><br>**说明：**<br>建议优先使用异步API{@link init}。同步API可能因系统繁忙、高负载等原因耗时较长而阻塞主线程。因此建议在子线程中调用同步API，以避免阻塞主线程。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Cipher-initSync(opMode: CryptoMode, key: Key, params: ParamsSpec | null): void--><!--Device-Cipher-initSync(opMode: CryptoMode, key: Key, params: ParamsSpec | null): void-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Cipher

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| opMode | [CryptoMode](arkts-cryptoarchitecture-cryptoframework-cryptomode-e.md) | 是 | 加密或者解密模式。 |
| key | [Key](../../apis-input-kit/arkts-apis/arkts-input-multimodalinput-keyevent-key-i.md) | 是 | 指定加密或解密的密钥。 |
| params | [ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md) \| null | 是 | 指定加密或解密的参数，对于ECB等没有参数的算法模式，请传入null。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。可能的原因：<br>1. 无效的opMode值；<br>2. 无效的iv长度；<br>3. 无效的密钥长度。<br>**适用版本：** 22+ |

## setCipherSpec

```TypeScript
setCipherSpec(itemType: CipherSpecItem, itemValue: Uint8Array): void
```

设置加解密参数。常用的加解密参数直接通过[createCipher](arkts-cryptoarchitecture-cryptoframework-createcipher-f.md#createcipher) 来指定，剩余参数通过本接口指定。当前只支持RSA算法。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Cipher-setCipherSpec(itemType: CipherSpecItem, itemValue: Uint8Array): void--><!--Device-Cipher-setCipherSpec(itemType: CipherSpecItem, itemValue: Uint8Array): void-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本10-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| itemType | [CipherSpecItem](arkts-cryptoarchitecture-cryptoframework-cipherspecitem-e.md) | 是 | 用于指定需要设置的加解密参数。 |
| itemValue | Uint8Array | 是 | 用于指定加解密参数的具体值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | 该操作不支持。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。可能的原因：<br>1. 不支持的itemType。<br>**适用版本：** 22+ |

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

function testsetCipherSpec() {
  let cipher = cryptoFramework.createCipher('RSA2048|PKCS1_OAEP|SHA256|MGF1_SHA1');
  let pSource = new Uint8Array([1, 2, 3, 4]);
  cipher.setCipherSpec(cryptoFramework.CipherSpecItem.OAEP_MGF1_PSRC_UINT8ARR, pSource);
}

```

## update

```TypeScript
update(data: DataBlob, callback: AsyncCallback<DataBlob>): void
```

更新要分段加密或解密的数据。使用Callback异步回调。

必须在对[Cipher](arkts-cryptoarchitecture-cryptoframework-cipher-i.md)实例使用[init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init)初始化后，才能使用本函数。
> **说明：**  
>  
> 1.在进行对称加解密操作时，如果开发者对各分组模式不够熟悉，建议每次调用**update**和**doFinal**后，都判断结果是否为null。如果结果  
> 不为null，则取出其中的数据进行拼接，以形成完整的密文或明文。这是因为选择的分组模式等各项规格可能会影响**update**和**doFinal**的  
> 结果。  
> 例如，对于ECB和CBC模式，不论**update**传入的数据是否为分组长度的整数倍，都会以分组作为基本单位进行加密或解密，并输出本次  
> **update**新产生的加密或解密分组结果。  
> 可以理解为，**update**只要凑满一个新的分组就会有输出，如果没有凑满则此次**update**输出为null，把当前还没被加密或解密的数据留着，  
> 等下一次**update**或**doFinal**传入数据的时候，拼接起来继续凑分组。  
> 最后**doFinal**的时候，会把剩下的还没加/解密的数据，根据[createCipher](arkts-cryptoarchitecture-cryptoframework-createcipher-f.md#createcipher)时设置的  
> padding模式进行填充，补齐到分组的整数倍长度，再输出剩余加解密结果。  
> 而对于可以将分组密码转化为流模式实现的模式，还可能出现密文长度和明文长度相同的情况等。  
> 2.根据数据量，可以不调用**update**（即**init**完成后直接调用**doFinal**）或多次调用**update**。  
> 算法库目前没有对**update**（单次或累计）的数据量设置大小限制，建议对于大数据量的对称加解密，可以采用多次**update**的方式传入数据。  
> 有关在多次**update()**调用中传递数据的示例代码的详细信息，请参见  
> [使用AES对称密钥分段加密和解密（GCM模式）](../../../security/CryptoArchitectureKit/crypto-aes-sym-encrypt-decrypt-gcm-by-segment.md)。  
> 3. RSA或SM2非对称加解密不支持**update()**。  
> 4. 对于CCM模式的对称加解密算法，加密时只能调用1次**update**接口加密数据并调用**doFinal**接口获取tag，或直接调用**doFinal**  
> 接口加密数据并获取tag，解密时只能调用1次**update**接口或调用1次**doFinal**接口解密数据并验证tag。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Cipher-update(data: DataBlob, callback: AsyncCallback<DataBlob>): void--><!--Device-Cipher-update(data: DataBlob, callback: AsyncCallback<DataBlob>): void-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [DataBlob](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-cert-datablob-i.md) | 是 | 需要进行加密或解密的数据。data不能为null。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;DataBlob&gt; | 是 | 回调函数。当更新加/解密数据成功时，err为undefined，data为加密或解密结果DataBlob；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。可能的原因：<br>1. 数据过长。<br>**适用版本：** 22+ |

## update

```TypeScript
update(data: DataBlob): Promise<DataBlob>
```

分段更新加密或者解密数据操作。使用Promise异步回调。

必须在对[Cipher](arkts-cryptoarchitecture-cryptoframework-cipher-i.md)实例使用[init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init)初始化后，才能使用本函数。
> **说明：**  
>  
> 1.在进行对称加解密操作时，如果开发者对各分组模式不够熟悉，建议每次调用**update**和**doFinal**后，都判断结果是否为null。如果结果  
> 不为null，则取出其中的数据进行拼接，以形成完整的密文或明文。这是因为选择的分组模式等各项规格可能会影响**update**和**doFinal**的  
> 结果。  
> 例如，对于ECB和CBC模式，不论**update**传入的数据是否为分组长度的整数倍，都会以分组作为基本单位进行加密或解密，并输出本次  
> **update**新产生的加密或解密分组结果。  
> 可以理解为，**update**只要凑满一个新的分组就会有输出，如果没有凑满则此次**update**输出为null，把当前还没被加密或解密的数据留着，  
> 等下一次**update**或**doFinal**传入数据的时候，拼接起来继续凑分组。  
> 最后**doFinal**的时候，会把剩下的还没加/解密的数据，根据[createCipher](arkts-cryptoarchitecture-cryptoframework-createcipher-f.md#createcipher)时设置的  
> padding模式进行填充，补齐到分组的整数倍长度，再输出剩余加解密结果。  
> 而对于可以将分组密码转化为流模式实现的模式，还可能出现密文长度和明文长度相同的情况等。  
> 2.根据数据量，可以不调用**update**（即**init**完成后直接调用**doFinal**）或多次调用**update**。  
> 算法库目前没有对**update**（单次或累计）的数据量设置大小限制，建议对于大数据量的对称加解密，可以采用多次**update**的方式传入数据。  
> 有关在多次**update()**调用中传递数据的示例代码的详细信息，请参见  
> [使用AES对称密钥分段加密和解密（GCM模式）](../../../security/CryptoArchitectureKit/crypto-aes-sym-encrypt-decrypt-gcm-by-segment.md)。  
> 3. RSA或SM2非对称加解密不支持**update()**。  
> 4. 对于CCM模式的对称加解密算法，加密时只能调用1次**update**接口加密数据并调用**doFinal**接口获取tag，或直接调用**doFinal**  
> 接口加密数据并获取tag，解密时只能调用1次**update**接口或调用1次**doFinal**接口解密数据并验证tag。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Cipher-update(data: DataBlob): Promise<DataBlob>--><!--Device-Cipher-update(data: DataBlob): Promise<DataBlob>-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [DataBlob](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-cert-datablob-i.md) | 是 | 加密或者解密的数据。data不能为null。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;DataBlob&gt; | Promise对象，返回此次更新的加密或解密结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。可能的原因：<br>1. 数据过长。<br>**适用版本：** 22+ |

## updateSync

```TypeScript
updateSync(data: DataBlob): DataBlob
```

分段更新加密或者解密数据操作。

必须在对[Cipher](arkts-cryptoarchitecture-cryptoframework-cipher-i.md)实例使用[initSync()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#initsync)初始化后，才能使用本函数。

其他注意事项同上异步接口说明。

<br><br>**说明：**<br>建议优先使用异步API{@link update}。同步API可能因系统繁忙、高负载等原因耗时较长而阻塞主线程。因此建议在子线程中调用同步API，以避免阻塞主线程。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Cipher-updateSync(data: DataBlob): DataBlob--><!--Device-Cipher-updateSync(data: DataBlob): DataBlob-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Cipher

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [DataBlob](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-cert-datablob-i.md) | 是 | 加密或者解密的数据。data不能为null。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataBlob](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-cert-datablob-i.md) | 返回此次更新的加/解密结果DataBlob。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。可能的原因：<br>1. 数据过长。<br>**适用版本：** 22+ |

## algName

```TypeScript
readonly algName: string
```

加解密生成器指定的算法名称。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Cipher-readonly algName: string--><!--Device-Cipher-readonly algName: string-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本9-11：SystemCapability.Security.CryptoFramework

