# Md

```TypeScript
interface Md
```

Message digest interface, defining methods for calculating message digests. Before use, you must create an **Md** instance by using [createMd](arkts-cryptoarchitecture-cryptoframework-createmd-f.md).

**Since:** 9

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.MessageDigest
- API versions 9 to 11: SystemCapability.Security.CryptoFramework

## Modules to Import

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## digest

```TypeScript
digest(callback: AsyncCallback<DataBlob>): void
```

Generates a message digest. This API uses an asynchronous callback to return the result.

**Since:** 9

**Model restriction:** 
- API version 12 and later: This API can be used in both the stage model and FA model.
- API versions 9 to 11: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.MessageDigest
- API versions 9 to 11: SystemCapability.Security.CryptoFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**, and **data** is the message digest obtained. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |
| [17620004](../errorcode-crypto-framework.md#17620004-invalid-function-call) | Invalid function call. XOF(Extendable-Output Function) digest algorithms, such as SHAKE128 and SHAKE256, do not support this API.<br>**Applicable version:** 26.2.0 and later |
| [17630001](../errorcode-crypto-framework.md#17630001-cryptographic-operation-error) | Crypto operation error. |

**Examples**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { buffer } from '@kit.ArkTS';

function mdByCallback() {
  let md = cryptoFramework.createMd('SHA256');
  md.update({ data: new Uint8Array(buffer.from('mdTestMessage', 'utf-8').buffer) }, (err) => {
    md.digest((err, digestOutput) => {
      console.info('[Callback]: MD result: ' + digestOutput.data);
      console.info('[Callback]: MD len: ' + md.getMdLength());
    });
  });
}
```

<a id="digest-1"></a>

## digest

```TypeScript
digest(): Promise<DataBlob>
```

Generates a message digest. This API uses a promise to return the result.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.MessageDigest
- API versions 9 to 11: SystemCapability.Security.CryptoFramework

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md)&gt; | Promise used to return the message digest generated. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |
| [17630001](../errorcode-crypto-framework.md#17630001-cryptographic-operation-error) | Crypto operation error. |
| [17620004](../errorcode-crypto-framework.md#17620004-invalid-function-call) | Invalid function call. XOF digest algorithms, such as SHAKE128 and SHAKE256, do not support this API.<br>**Applicable version:** 26.2.0 and later |

**Examples**

ArkTS example:

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { buffer } from '@kit.ArkTS';

async function mdByPromise() {
  let md = cryptoFramework.createMd('SHA256');
  await md.update({ data: new Uint8Array(buffer.from('mdTestMessage', 'utf-8').buffer) });
  let mdOutput = await md.digest();
  console.info('[Promise]: MD result: ' + mdOutput.data);
  console.info('[Promise]: MD len: ' + md.getMdLength());
}
```

JS example:

```TypeScript
<div class="container">
    <text class="TestTitle">Crypto test</text>
    <input class="btn" @click="MdTest">Md asynchronous test</input>
</div>
```

```TypeScript
.container {
  width: 100%;
  height: 2000px;
  align-items: center;
  background-color: #fffefcfc;
  flex-direction: column;
  display: flex;
}

.TestTitle {
  width: 300px;
  height: 80px;
  text-align: center;
  background-color: white;
  color: #fff61515;
  font-size: 15fp;
}

.btn {
  width: 90%;
  height: 80px;
  text-align: center;
  background-color: #fff17f04;
  margin-top: 3px;
  color: white;
  font-size: 20fp;
}
```

```TypeScript
import cryptoFramework from '@ohos.security.cryptoFramework';

function StringToUint8Array(str) {
    let arr = [];
    for (let i = 0, j = str.length; i < j; ++i) {
        arr.push(str.charCodeAt(i));
    }
    return new Uint8Array(arr);
}

let plainText = "123456";

function mdTest() {
    let inData = StringToUint8Array(plainText);
    let md = cryptoFramework.createMd('SHA256');
    console.info('createMd ' + typeof md);

    md.update({data: inData}, function (finishErr) {
        if (finishErr) {
            console.error('Digest update failed. Code: ' + finishErr.code + " : " + finishErr.message);
        } else {
            console.info('Digest update successfully.');
        }
    })

    md.digest(function (finishErr, digestOutput){
        if (finishErr) {
            console.error('Digest failed. Code: ' + finishErr.code + " : " + finishErr.message);
        } else {
            console.info('Digest successfully:' + digestOutput);
        }
    })
}

export default {
    data: {
        result: ''
    },
    MdTest() {
        mdTest();
    }
};
```

## digestSync

```TypeScript
digestSync(): DataBlob
```

Generates a message digest. This API returns the result synchronously.

<br><br>**NOTE:** <br>It is recommended to prioritize the use of asynchronous API, [digest](#digest). Synchronous API may take a long time and block the main thread due to system busyness, high load, and other reasons. Therefore, it is advised to invoke synchronous API within a child thread to avoid blocking the main thread.

**Since:** 12

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.CryptoFramework.MessageDigest

**Return value:**

| Type | Description |
| --- | --- |
| [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md) | Message digest generated. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |
| [17620002](../errorcode-crypto-framework.md#17620002-failed-to-obtain-the-native-object-or-convert-parameters) | Failed to obtain the native object or convert parameters. |
| [17620004](../errorcode-crypto-framework.md#17620004-invalid-function-call) | Invalid function call. XOF digest algorithms, such as SHAKE128 and SHAKE256, do not support this API.<br>**Applicable version:** 26.2.0 and later |
| [17630001](../errorcode-crypto-framework.md#17630001-cryptographic-operation-error) | Crypto operation error. |

**Examples**

ArkTS example:

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { buffer } from '@kit.ArkTS';

function mdBySync() {
  let md = cryptoFramework.createMd('SHA256');
  md.updateSync({ data: new Uint8Array(buffer.from('mdTestMessage', 'utf-8').buffer) });
  let mdOutput = md.digestSync();
  console.info('[Sync]: MD result: ' + mdOutput.data);
  console.info('[Sync]: MD len: ' + md.getMdLength());
}
```

JS example:

```TypeScript
<div class="container">
    <text class="TestTitle">Crypto test</text>
    <input class="btn" @click="MdTestSync">Md synchronous test</input>
</div>
```

```TypeScript
.container {
  width: 100%;
  height: 2000px;
  align-items: center;
  background-color: #fffefcfc;
  flex-direction: column;
  display: flex;
}

.TestTitle {
  width: 300px;
  height: 80px;
  text-align: center;
  background-color: white;
  color: #fff61515;
  font-size: 15fp;
}

.btn {
  width: 90%;
  height: 80px;
  text-align: center;
  background-color: #fff17f04;
  margin-top: 3px;
  color: white;
  font-size: 20fp;
}
```

```TypeScript
import cryptoFramework from '@ohos.security.cryptoFramework';

function StringToUint8Array(str) {
    let arr = [];
    for (let i = 0, j = str.length; i < j; ++i) {
        arr.push(str.charCodeAt(i));
    }
    return new Uint8Array(arr);
}

function mdTestSync() {
    let mdAlgName = 'SHA256';
    let message = 'mdTestMessage';
    let md = cryptoFramework.createMd(mdAlgName);
    md.updateSync({ data: StringToUint8Array(message) });
    let mdResult = md.digestSync();
    console.info('Digest successfully. result:' + mdResult.data);
    let mdLen = md.getMdLength();
    console.info('Digest successfully. md len: ' + mdLen);
}

export default {
    data: {
        result: ''
    },
    MdTestSync() {
        mdTestSync();
    }
};
```

## getMdLength

```TypeScript
getMdLength(): number
```

Obtains the message digest length, in bytes.

**Since:** 9

**Model restriction:** 
- API version 12 and later: This API can be used in both the stage model and FA model.
- API versions 9 to 11: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.MessageDigest
- API versions 9 to 11: SystemCapability.Security.CryptoFramework

**Return value:**

| Type | Description |
| --- | --- |
| number | Message digest length obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17620004](../errorcode-crypto-framework.md#17620004-invalid-function-call) | Invalid function call. XOF digest algorithms, such as SHAKE128 and SHAKE256, do not support this API.<br>**Applicable version:** 26.2.0 and later |
| [17630001](../errorcode-crypto-framework.md#17630001-cryptographic-operation-error) | Crypto operation error. |

**Examples**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

function getLength() {
  let md = cryptoFramework.createMd('SHA256');
  console.info('[Promise]: MD len: ' + md.getMdLength());
}
```

## squeeze

```TypeScript
squeeze(len: number): Promise<DataBlob>
```

Squeezes the output for XOF algorithms such as SHAKE128 and SHAKE256. This API uses a promise to return the result.

> **NOTE:** 
> 
> Currently, this API and [squeezeSync](#squeezesync) can be called only once in total per **Md** instance.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

**System capability:** SystemCapability.Security.CryptoFramework.MessageDigest

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| len | number | Yes | Length of the output digest in bytes.<br>For the SHAKE128 algorithm, the supported length ranges from 32 to 65536. <br>For the SHAKE256 algorithm, the supported length ranges from 64 to 65536. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md)&gt; | Promise used to return the message digest generated. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |
| [17620002](../errorcode-crypto-framework.md#17620002-failed-to-obtain-the-native-object-or-convert-parameters) | Failed to obtain the native object or convert parameters. |
| [17620003](../errorcode-crypto-framework.md#17620003-parameter-check-failed) | Parameter check failed. Possible causes:<br>1. Invalid len value; |
| [17620004](../errorcode-crypto-framework.md#17620004-invalid-function-call) | Invalid function call. The fixed-length digest algorithm, such as SHA256, does not support this API. |

## squeezeSync

```TypeScript
squeezeSync(len: number): DataBlob
```

Squeezes the output for XOF algorithms such as SHAKE128 and SHAKE256. This API returns the result synchronously.

> **NOTE:** 
> 
> Currently, this API and [squeeze](#squeeze) can be called only once in total per **Md** instance.

<br><br>**NOTE:** <br>It is recommended to prioritize the use of asynchronous API, [squeeze](#squeeze). Synchronous API may take a long time and block the main thread due to system busyness, high load, and other reasons. Therefore, it is advised to invoke synchronous API within a child thread to avoid blocking the main thread.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

**System capability:** SystemCapability.Security.CryptoFramework.MessageDigest

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| len | number | Yes | Length of the output digest in bytes.<br>For the SHAKE128 algorithm, the supported length ranges from 32 to 65536. <br>For the SHAKE256 algorithm, the supported length ranges from 64 to 65536. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md) | Message digest generated. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |
| [17620002](../errorcode-crypto-framework.md#17620002-failed-to-obtain-the-native-object-or-convert-parameters) | Failed to obtain the native object or convert parameters. |
| [17620003](../errorcode-crypto-framework.md#17620003-parameter-check-failed) | Parameter check failed. Possible causes:<br>1. Invalid len value; |
| [17620004](../errorcode-crypto-framework.md#17620004-invalid-function-call) | Invalid function call. The fixed-length digest algorithm, such as SHA256, does not support this API. |

## update

```TypeScript
update(input: DataBlob, callback: AsyncCallback<void>): void
```

Updates the message digest status. This API uses an asynchronous callback to return the result. **update** must be used with **digest** together. **digest** is mandatory, and **update** is optional.

> **NOTE:** 
> 
> For details about the code for calling **update** multiple times in a message digest operation, see
> [Generating an MD by Passing In Data by Segment](../../../security/CryptoArchitectureKit/crypto-generate-message-digest.md#generating-an-md-by-passing-in-data-by-segment)
> .

**Since:** 9

**Model restriction:** 
- API version 12 and later: This API can be used in both the stage model and FA model.
- API versions 9 to 11: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.MessageDigest
- API versions 9 to 11: SystemCapability.Security.CryptoFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| input | [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md) | Yes | Data to pass in. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |
| [17630001](../errorcode-crypto-framework.md#17630001-cryptographic-operation-error) | Crypto operation error. |

<a id="update-1"></a>

## update

```TypeScript
update(input: DataBlob): Promise<void>
```

Updates the message digest status. This API uses a promise to return the result. **update** must be used with **digest** together. **digest** is mandatory, and **update** is optional.

> **NOTE:** 
> 
> For details about the code for calling **update** multiple times in a message digest operation, see
> [Generating an MD by Passing In Data by Segment](../../../security/CryptoArchitectureKit/crypto-generate-message-digest.md#generating-an-md-by-passing-in-data-by-segment)
> .

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.MessageDigest
- API versions 9 to 11: SystemCapability.Security.CryptoFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| input | [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md) | Yes | Data to pass in. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |
| [17630001](../errorcode-crypto-framework.md#17630001-cryptographic-operation-error) | Crypto operation error. |

## updateSync

```TypeScript
updateSync(input: DataBlob): void
```

Updates the message digest status. This API returns the result synchronously. **updateSync** must be used with **digestSync** together. **digestSync** is mandatory, and **updateSync** is optional.

> **NOTE:** 
> 
> For details about the code for calling **updateSync** multiple times in a message digest operation, see
> [Generating an MD by Passing In Data by Segment](../../../security/CryptoArchitectureKit/crypto-generate-message-digest.md#generating-an-md-by-passing-in-data-by-segment)
> .

<br><br>**NOTE:** <br>It is recommended to prioritize the use of asynchronous API, update. Synchronous API may take a long time and block the main thread due to system busyness, high load, and other reasons. Therefore, it is advised to invoke synchronous API within a child thread to avoid blocking the main thread.

**Since:** 12

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.CryptoFramework.MessageDigest

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| input | [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md) | Yes | Data to pass in. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |
| [17630001](../errorcode-crypto-framework.md#17630001-cryptographic-operation-error) | Crypto operation error. |

## algName

```TypeScript
readonly algName: string
```

Indicates the algorithm name.

**Type:** string

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.MessageDigest
- API versions 9 to 11: SystemCapability.Security.CryptoFramework
