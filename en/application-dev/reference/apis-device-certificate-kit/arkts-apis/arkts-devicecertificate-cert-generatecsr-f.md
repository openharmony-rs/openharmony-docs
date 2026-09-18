# generateCsr

## Modules to Import

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## generateCsr

```TypeScript
function generateCsr(keyInfo: PrivateKeyInfo, config: CsrGenerationConfig): string | Uint8Array
```

Generates a CSR.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Security.Cert

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyInfo | [PrivateKeyInfo](arkts-devicecertificate-cert-privatekeyinfo-i.md) | Yes | Private key information. |
| config | [CsrGenerationConfig](arkts-devicecertificate-cert-csrgenerationconfig-i.md) | Yes | Configuration for generating the CSR. |

**Return value:**

| Type | Description |
| --- | --- |
| string &#124; Uint8Array | CSR generated. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [19020001](../errorcode-cert.md#19020001-memory-error) | Memory malloc failed. |
| [19020002](../errorcode-cert.md#19020002-runtime-error) | Runtime error. Possible causes:<br>1. Memory copy failed; <br>2. A null pointer occurs inside the system; <br>3. Failed to obtain the native object or convert parameters. |
| [19030001](../errorcode-cert.md#19030001-failed-to-invoke-the-third-party-cryptographic-api) | Crypto operation error. |
| [19030008](../errorcode-cert.md#19030008-incorrect-private-key-password) | Maybe wrong password. |

**Examples**

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
