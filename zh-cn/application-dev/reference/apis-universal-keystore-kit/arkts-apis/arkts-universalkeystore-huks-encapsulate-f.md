# encapsulate

## 导入模块

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

## encapsulate

```TypeScript
function encapsulate(keyAlias: string, params: HuksParam[],
      sharedKeyAlias?: string, sharedKeyParams?: HuksParam[]): Promise<HuksReturnResult>
```

后量子加密密钥封装操作，支持HUKS密钥管理或由应用程序本身决定。如果应用程序选择管理密钥，对称密钥携带在HuksReturnResult的outData字段中。

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-huks-function encapsulate(keyAlias: string, params: HuksParam[],      sharedKeyAlias?: string, sharedKeyParams?: HuksParam[]): Promise<HuksReturnResult>--><!--Device-huks-function encapsulate(keyAlias: string, params: HuksParam[],      sharedKeyAlias?: string, sharedKeyParams?: HuksParam[]): Promise<HuksReturnResult>-End-->

**系统能力：** SystemCapability.Security.Huks.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | 后量子加密算法的密钥名称 |
| params | [HuksParam](arkts-universalkeystore-huks-huksparam-i.md)[] | 是 | 表示封装属性 |
| sharedKeyAlias | string | 否 | 封装密钥的密钥别名。如果使用HUKS进行密钥管理，则必须指定该参数。如果应用程序自己管理密钥，则忽略此参数 |
| sharedKeyParams | [HuksParam](arkts-universalkeystore-huks-huksparam-i.md)[] | 否 | 表示封装的密钥的属性。如果使用HUKS进行密钥管理，则必须指定该参数。如果应用程序自己管理密钥，则忽略此参数 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksReturnResult&gt; | 函数返回的promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | API is not supported. |
| [12000001](../errorcode-huks.md#12000001-该子功能不支持特性) | Algorithm mode is not supported |
| [12000002](../errorcode-huks.md#12000002-缺少密钥算法参数) | Algorithm parameters are missing, please check the algorithm parameters. |
| [12000003](../errorcode-huks.md#12000003-无效的密钥算法参数) | The algorithm parameters are invalid, please check the algorithm parameters. |
| [12000004](../errorcode-huks.md#12000004-文件错误) | File operation failed. |
| [12000005](../errorcode-huks.md#12000005-进程通信错误) | IPC communication failed. |
| [12000006](../errorcode-huks.md#12000006-算法库操作失败) | The algorithm engine reported an error, please check the input parameters. |
| [12000011](../errorcode-huks.md#12000011-目标对象不存在) | The queried key does not exist, please check the key-related parameters. |
| [12000012](../errorcode-huks.md#12000012-外部错误) | Device environment or input parameters are abnormal. |
| [12000013](../errorcode-huks.md#12000013-密钥设置生物访问控制时待绑定的凭据不存在) | Queried credential does not exist |
| [12000014](../errorcode-huks.md#12000014-内存不足) | Memory is insufficient. |
| [12000015](../errorcode-huks.md#12000015-调用其他系统服务失败) | Failed to obtain the security information via UserIAM. |
| [12000016](../errorcode-huks.md#12000016-设备密码未设置) | The screen lock password is not set. |
| [12000017](../errorcode-huks.md#12000017-同名密钥已存在) | The key with the same alias already exists. |
| [12000018](../errorcode-huks.md#12000018-输入参数非法) | The input parameter is invalid. |

**示例：**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';

let keyAlias = 'ml_kem_pub_key_b';
let params: huks.HuksParam[] = [{
  tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
  value: huks.HuksKeyAlg.HUKS_ALG_ML_KEM,
}, {
  tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
  value: huks.HuksKeySize.HUKS_ML_KEM_KEY_PARAM_SET_768,
}, {
  tag: huks.HuksTag.HUKS_TAG_PURPOSE,
  value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_WRAP,
}];

try {
  huks.encapsulate(keyAlias, params).then((data: huks.HuksReturnResult) => {
    console.info(`encapsulate success, encapsulatedData length: ${(data.outData as Uint8Array).length}`);
    console.info(`sharedSecret length: ${(data.sharedSecret as Uint8Array).length}`);
  }).catch((error: BusinessError) => {
    console.error(`encapsulate failed, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`encapsulate input arg invalid`);
}

```

