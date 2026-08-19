# DHKeyUtil

根据素数P的长度和私钥长度（bit位数）生成DH公共密钥参数。

**起始版本：** 23

<!--Device-cryptoFramework-class DHKeyUtil--><!--Device-cryptoFramework-class DHKeyUtil-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本11：SystemCapability.Security.CryptoFramework

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## genDHCommonParamsSpec

```TypeScript
static genDHCommonParamsSpec(pLen: int, skLen?: int): DHCommonParamsSpec
```

根据素数P的长度和私钥长度（单位为bit）生成DH公共密钥参数。详见 [DH密钥生成规格](../../../security/CryptoArchitectureKit/crypto-key-generation-conversion.md#dh)。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DHKeyUtil-static genDHCommonParamsSpec(pLen: int, skLen?: int): DHCommonParamsSpec--><!--Device-DHKeyUtil-static genDHCommonParamsSpec(pLen: int, skLen?: int): DHCommonParamsSpec-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pLen | int | 是 | 用于指定DH公共密钥参数中素数P的长度，单位为bits。 |
| skLen | int | 否 | 用于指定生成DH私钥的最大长度，单位为bits，默认值为0。<br>当参数值设置为0时，生成DH私钥的最大长度为： <br>ffdhe2048：255 bits。<br>ffdhe3072：275 bits。<br>ffdhe4096：325 bits。<br>ffdhe6144：375 bits。 <br>ffdhe8192：400 bits。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DHCommonParamsSpec](arkts-cryptoarchitecture-cryptoframework-dhcommonparamsspec-i.md) | 返回DH公共密钥参数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | This operation is not supported. |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | Crypto operation error. |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | Memory operation failed. |

**示例**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@kit.BasicServicesKit';
try {
  let DHCommonParamsSpec = cryptoFramework.DHKeyUtil.genDHCommonParamsSpec(2048);
  console.info('genDHCommonParamsSpec result: success.');
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error(`genDHCommonParamsSpec failed: errCode: ${e.code}, errMsg: ${e.message}`);
}
```

