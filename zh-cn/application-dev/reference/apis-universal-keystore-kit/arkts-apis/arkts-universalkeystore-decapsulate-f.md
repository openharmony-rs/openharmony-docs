# decapsulate

## decapsulate

```TypeScript
function decapsulate(keyAlias: string, params: HuksParam[], encapData: Uint8Array,
      sharedKeyAlias?: string, sharedKeyParams?:  HuksParam[]): Promise<HuksReturnResult>
```

Post-Quantum Cryptography密钥解封装操作，支持HUKS密钥管理
或由应用程序本身决定。如果应用程序选择管理密钥，
对称密钥包含在HuksReturnResult的outData字段中。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Security.Huks.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | 后量子加密算法的密钥名称。 |
| params | HuksParam[] | 是 | 表示解封装属性。 |
| encapData | Uint8Array | 是 | 表示封装后的共享密钥。 |
| sharedKeyAlias | string | 否 | 表示解封装密钥的密钥别名。如果使用HUKS进行密钥管理，则必须指定该参数。如果应用程序自己管理密钥，则忽略此参数。 |
| sharedKeyParams | HuksParam[] | 否 | 表示解封装后的key的属性。如果使用HUKS进行密钥管理，则必须指定该参数。如果应用程序自己管理密钥，则忽略此参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksReturnResult&gt; | 返回值 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | API is not supported. |
| [12000001](../errorcode-huks.md#12000001-该子功能不支持特性) | Algorithm mode is not supported |
| [12000002](../errorcode-huks.md#12000002-缺少密钥算法参数) | The algorithm parameter is missing. Check the algorithm parameter. |
| [12000003](../errorcode-huks.md#12000003-无效的密钥算法参数) | The algorithm parameter is invalid. Check the algorithm parameter. |
| [12000004](../errorcode-huks.md#12000004-文件错误) | The file operation failed. |
| [12000005](../errorcode-huks.md#12000005-进程通信错误) | IPC communication failed. |
| [12000006](../errorcode-huks.md#12000006-算法库操作失败) | The algorithm engine reports an error. Check the input parameters. |
| [12000011](../errorcode-huks.md#12000011-目标对象不存在) | The queried key does not exist. Check the key-related parameters. |
| [12000012](../errorcode-huks.md#12000012-外部错误) | The device environment or input parameter is abnormal. |
| [12000013](../errorcode-huks.md#12000013-密钥设置生物访问控制时待绑定的凭据不存在) | Queried credential does not exist |
| [12000014](../errorcode-huks.md#12000014-内存不足) | Insufficient memory. |
| [12000015](../errorcode-huks.md#12000015-调用其他系统服务失败) | Failed to obtain the security information using UserIAM. |
| 12000016 | The lock screen password is not set. |
| [12000017](../errorcode-huks.md#12000017-同名密钥已存在) | A key with the same alias already exists. |
| [12000018](../errorcode-huks.md#12000018-输入参数非法) | Invalid input parameter. |

**示例：**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';

let keyAlias = 'ml_kem_key_b';
let params: huks.HuksParam[] = [{
  tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
  value: huks.HuksKeyAlg.HUKS_ALG_ML_KEM,
}, {
  tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
  value: huks.HuksKeySize.HUKS_ML_KEM_KEY_PARAM_SET_768,
}, {
  tag: huks.HuksTag.HUKS_TAG_PURPOSE,
  value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_UNWRAP,
}];

let encapData = new Uint8Array(784);

try {
  huks.decapsulate(keyAlias, params, encapData).then((data: huks.HuksReturnResult) => {
    console.info(`decapsulate success, sharedSecret length: ${(data.sharedSecret as Uint8Array).length}`);
  }).catch((error: BusinessError) => {
    console.error(`decapsulate failed, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`decapsulate input arg invalid`);
}

```

