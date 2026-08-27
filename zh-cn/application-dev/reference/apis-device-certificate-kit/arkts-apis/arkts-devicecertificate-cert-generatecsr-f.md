# generateCsr

## 导入模块

```TypeScript
```

## generateCsr

```TypeScript
function generateCsr(keyInfo: PrivateKeyInfo, config: CsrGenerationConfig): string | Uint8Array
```

表示使用指定的私钥，传入主体、扩展、摘要算法、输出格式等配置参数去生成CSR。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyInfo | [PrivateKeyInfo](arkts-devicecertificate-cert-privatekeyinfo-i.md) | 是 | 包含私钥跟口令的配置参数。 |
| config | [CsrGenerationConfig](arkts-devicecertificate-cert-csrgenerationconfig-i.md) | 是 | 包含生成CSR的配置参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string \| Uint8Array | 生成的CSR。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types;  3. Parameter verification failed. |
| [19020001](../errorcode-cert.md#19020001-内存错误) | Memory malloc failed. |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | Runtime error. Possible causes:  1. Memory copy failed;  2. A null pointer occurs inside the system;  3. Failed to obtain the native object or convert parameters. |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | Crypto operation error. |
| [19030008](../errorcode-cert.md#19030008-私钥密码错误) | Maybe wrong password. |

**示例**

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function createCsrTest() {
  let nameStr = '/CN=John Doe/OU=IT Department/O=ACME Inc./L=San Francisco/ST=California/C=US/CN=ALN C/CN=XTS';
  let priKeyEnstr: string =
    '-----BEGIN RSA PRIVATE KEY-----\n' +
      'Proc-Type: 4,ENCRYPTED\n' +
      'DEK-Info: AES-128-CBC,B5FFA3AEEE7176106FDDB0988B532F07\n\n' +
      't3zNRGKp5X4BNkcsYATad/Le+94yMIX9CoNAGsBIDzQw+773UMGIoeGEYVlXWc8x\n' +
      'N1XWDinn4ytWw9x9OfUYgmNnrdkWRSaIuw+SpQfBgJip+MsNERYOHZ5TYWTR8n3k\n' +
      '7/jHY8eCgTsP3hbNtyaePIrtbTLZGZAHG1YWY5UmLaYoI1O6/Vvobx72lx3b43Tx\n' +
      '4j5lkknpLl85fcs1s4TYMOd8vEwhdpouR4VY8kfRSm44WQLtGXrce0An3MG3pXyZ\n' +
      'GhpmJyTcg0epTEYVzglENlBJrBVDL+bJ8uvHGH4tmeQb77e6ILXoxZntM7zQMMFo\n' +
      'A7dilqO6FBxu20n2TidVGCa0Yn+DZLpry2OdwVUC2nXyCHCehr3jAZz6k20FWg5B\n' +
      'EsU16yOIB+bp9BUKdTpJVtc/pmZJtnlA9pSCUVmWdltOsjjxkE94wfAUOYhO3Mvz\n' +
      'gF9KR1/bdAbLw4t7bGeuyV4N2iYr83FodLLXpupM6Qfb51+HVgHvm2aaHv2Q4sf3\n' +
      'poCVTNlegoVV9x3+7HqXY6MjlG8aU6LcWqH34ySqRBQrKL1PuDzQSY5/RmP7PUhG\n' +
      'ym4l6KbEaRC2H/XS2qKa4VCMgBCgA0hoiw4s48Xd4h2GUTuxLM9wGyW89OEaHky7\n' +
      'VE7t3O9a2zhkRTYDDYQ8QCycKhNrsKySyItRUWn/w2lXvuKM7PpAzYH7Ey3W1eZG\n' +
      'PyyeGG9exjpdIvD3tx5Hl/OWwBkW1DAzO40gT6sdD5FXzRv4fCHuCrIow5QMLF4T\n' +
      'd5Y4a6q13V4O5b73T5INmKl8rEbPGIw7WLR7BNj05QuzNcn5kA1aBFIJqsxQv46l\n' +
      '-----END RSA PRIVATE KEY-----\n';
  let priKeyInfo: cert.PrivateKeyInfo = {
    key: priKeyEnstr,
    password: '123abc'
  };
  let keyUsage: cert.CsrAttribute = {
    type: 'keyUsage',
    value: 'digitalSignature, keyEncipherment'
  };

  let challengePassword: cert.CsrAttribute = {
    type: 'challengePassword',
    value: '123456'
  };
  let attribute: cert.CsrAttribute[] = [
    keyUsage, challengePassword
  ];
  try {
    let data = await cert.createX500DistinguishedName(nameStr);
    console.info('createX500DistinguishedName result: success. ' + data.getName('CN').toString());
    let conf: cert.CsrGenerationConfig = {
      subject: data,
      mdName: 'SHA256',
      outFormat: cert.EncodingBaseFormat.PEM,
      attributes: attribute
    };
    try {
      let csrStr = cert.generateCsr(priKeyInfo, conf);
      console.info('generateCsr result: success, return str is ' + csrStr.toString());
    } catch (error) {
      let e: BusinessError = error as BusinessError;
      console.error(`generateCsr failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`createX500DistinguishedName failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}
```
