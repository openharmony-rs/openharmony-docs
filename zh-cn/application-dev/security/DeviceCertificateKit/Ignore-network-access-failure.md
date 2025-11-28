# 支持证书链校验时忽略在线证书吊销检查的网络不可达异常

<!--Kit: Device Certificate Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

从API 23开始，支持证书链校验时忽略在线证书吊销检查的网络不可达异常。

## 开发步骤

1. 导入[证书算法库框架模块](../../reference/apis-device-certificate-kit/js-apis-cert.md)。

   ```ts
   import { cert } from '@kit.DeviceCertificateKit';
   ```
2. 调用[cert.createCertChain](../../reference/apis-device-certificate-kit/js-apis-cert.md#certcreatex509certchain11)创建证书链对象。

3. 调用[cert.createX509Cert](../../reference/apis-device-certificate-kit/js-apis-cert.md#certcreatex509cert)创建X509证书对象。

4. 构造[cert.CertChainValidationParameters](../../reference/apis-device-certificate-kit/js-apis-cert.md#certchainvalidationparameters11)证书链校验参数。

5. 调用[cert.validate](../../reference/apis-device-certificate-kit/js-apis-cert.md#validate11)，传入证书链校验参数，进行证书链校验。

在线OCSP检查忽略网络不可达异常示例：

```ts
import { cert } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

let rootCert = '-----BEGIN CERTIFICATE-----\n' +
  'MIIDjjCCAnagAwIBAgIQAzrx5qcRqaC7KGSxHQn65TANBgkqhkiG9w0BAQsFADBh\n' +
  'MQswCQYDVQQGEwJVUzEVMBMGA1UEChMMRGlnaUNlcnQgSW5jMRkwFwYDVQQLExB3\n' +
  'd3cuZGlnaWNlcnQuY29tMSAwHgYDVQQDExdEaWdpQ2VydCBHbG9iYWwgUm9vdCBH\n' +
  'MjAeFw0xMzA4MDExMjAwMDBaFw0zODAxMTUxMjAwMDBaMGExCzAJBgNVBAYTAlVT\n' +
  'MRUwEwYDVQQKEwxEaWdpQ2VydCBJbmMxGTAXBgNVBAsTEHd3dy5kaWdpY2VydC5j\n' +
  'b20xIDAeBgNVBAMTF0RpZ2lDZXJ0IEdsb2JhbCBSb290IEcyMIIBIjANBgkqhkiG\n' +
  '9w0BAQEFAAOCAQ8AMIIBCgKCAQEAuzfNNNx7a8myaJCtSnX/RrohCgiN9RlUyfuI\n' +
  '2/Ou8jqJkTx65qsGGmvPrC3oXgkkRLpimn7Wo6h+4FR1IAWsULecYxpsMNzaHxmx\n' +
  '1x7e/dfgy5SDN67sH0NO3Xss0r0upS/kqbitOtSZpLYl6ZtrAGCSYP9PIUkY92eQ\n' +
  'q2EGnI/yuum06ZIya7XzV+hdG82MHauVBJVJ8zUtluNJbd134/tJS7SsVQepj5Wz\n' +
  'tCO7TG1F8PapspUwtP1MVYwnSlcUfIKdzXOS0xZKBgyMUNGPHgm+F6HmIcr9g+UQ\n' +
  'vIOlCsRnKPZzFBQ9RnbDhxSJITRNrw9FDKZJobq7nMWxM4MphQIDAQABo0IwQDAP\n' +
  'BgNVHRMBAf8EBTADAQH/MA4GA1UdDwEB/wQEAwIBhjAdBgNVHQ4EFgQUTiJUIBiV\n' +
  '5uNu5g/6+rkS7QYXjzkwDQYJKoZIhvcNAQELBQADggEBAGBnKJRvDkhj6zHd6mcY\n' +
  '1Yl9PMWLSn/pvtsrF9+wX3N3KjITOYFnQoQj8kVnNeyIv/iPsGEMNKSuIEyExtv4\n' +
  'NeF22d+mQrvHRAiGfzZ0JFrabA0UWTW98kndth/Jsw1HKj2ZL7tcu7XUIOGZX1NG\n' +
  'Fdtom/DzMNU+MeKNhJ7jitralj41E6Vf8PlwUHBHQRFXGU7Aj64GxJUTFy8bJZ91\n' +
  '8rGOmaFvE7FBcf6IKshPECBV1/MUReXgRPTqh5Uykw7+U0b6LJ3/iyK5S9kJRaTe\n' +
  'pLiaWN0bfVKfjllDiIGknibVb63dDcY3fe0Dkhvld1927jyNxF1WW6LZZm6zNTfl\n' +
  'MrY=\n' +
  '-----END CERTIFICATE-----';

let intermediateCert = '-----BEGIN CERTIFICATE-----\n' +
  'MIIEszCCA5ugAwIBAgIQCyWUIs7ZgSoVoE6ZUooO+jANBgkqhkiG9w0BAQsFADBh\n' +
  'MQswCQYDVQQGEwJVUzEVMBMGA1UEChMMRGlnaUNlcnQgSW5jMRkwFwYDVQQLExB3\n' +
  'd3cuZGlnaWNlcnQuY29tMSAwHgYDVQQDExdEaWdpQ2VydCBHbG9iYWwgUm9vdCBH\n' +
  'MjAeFw0xNzExMDIxMjI0MzNaFw0yNzExMDIxMjI0MzNaMGAxCzAJBgNVBAYTAlVT\n' +
  'MRUwEwYDVQQKEwxEaWdpQ2VydCBJbmMxGTAXBgNVBAsTEHd3dy5kaWdpY2VydC5j\n' +
  'b20xHzAdBgNVBAMTFlJhcGlkU1NMIFRMUyBSU0EgQ0EgRzEwggEiMA0GCSqGSIb3\n' +
  'DQEBAQUAA4IBDwAwggEKAoIBAQC/uVklRBI1FuJdUEkFCuDL/I3aJQiaZ6aibRHj\n' +
  'ap/ap9zy1aYNrphe7YcaNwMoPsZvXDR+hNJOo9gbgOYVTPq8gXc84I75YKOHiVA4\n' +
  'NrJJQZ6p2sJQyqx60HkEIjzIN+1LQLfXTlpuznToOa1hyTD0yyitFyOYwURM+/CI\n' +
  '8FNFMpBhw22hpeAQkOOLmsqT5QZJYeik7qlvn8gfD+XdDnk3kkuuu0eG+vuyrSGr\n' +
  '5uX5LRhFWlv1zFQDch/EKmd163m6z/ycx/qLa9zyvILc7cQpb+k7TLra9WE17YPS\n' +
  'n9ANjG+ECo9PDW3N9lwhKQCNvw1gGoguyCQu7HE7BnW8eSSFAgMBAAGjggFmMIIB\n' +
  'YjAdBgNVHQ4EFgQUDNtsgkkPSmcKuBTuesRIUojrVjgwHwYDVR0jBBgwFoAUTiJU\n' +
  'IBiV5uNu5g/6+rkS7QYXjzkwDgYDVR0PAQH/BAQDAgGGMB0GA1UdJQQWMBQGCCsG\n' +
  'AQUFBwMBBggrBgEFBQcDAjASBgNVHRMBAf8ECDAGAQH/AgEAMDQGCCsGAQUFBwEB\n' +
  'BCgwJjAkBggrBgEFBQcwAYYYaHR0cDovL29jc3AuZGlnaWNlcnQuY29tMEIGA1Ud\n' +
  'HwQ7MDkwN6A1oDOGMWh0dHA6Ly9jcmwzLmRpZ2ljZXJ0LmNvbS9EaWdpQ2VydEds\n' +
  'b2JhbFJvb3RHMi5jcmwwYwYDVR0gBFwwWjA3BglghkgBhv1sAQEwKjAoBggrBgEF\n' +
  'BQcCARYcaHR0cHM6Ly93d3cuZGlnaWNlcnQuY29tL0NQUzALBglghkgBhv1sAQIw\n' +
  'CAYGZ4EMAQIBMAgGBmeBDAECAjANBgkqhkiG9w0BAQsFAAOCAQEAGUSlOb4K3Wtm\n' +
  'SlbmE50UYBHXM0SKXPqHMzk6XQUpCheF/4qU8aOhajsyRQFDV1ih/uPIg7YHRtFi\n' +
  'CTq4G+zb43X1T77nJgSOI9pq/TqCwtukZ7u9VLL3JAq3Wdy2moKLvvC8tVmRzkAe\n' +
  '0xQCkRKIjbBG80MSyDX/R4uYgj6ZiNT/Zg6GI6RofgqgpDdssLc0XIRQEotxIZcK\n' +
  'zP3pGJ9FCbMHmMLLyuBd+uCWvVcF2ogYAawufChS/PT61D9rqzPRS5I2uqa3tmIT\n' +
  '44JhJgWhBnFMb7AGQkvNq9KNS9dd3GWc17H/dXa1enoxzWjE0hBdFjxPhUb0W3wi\n' +
  '8o34/m8Fxw==\n' +
  '-----END CERTIFICATE-----';

let leafCert = '-----BEGIN CERTIFICATE-----\n' +
  'MIIGIzCCBQugAwIBAgIQD8vHwz7g05mDl1F5X17HGzANBgkqhkiG9w0BAQsFADBg\n' +
  'MQswCQYDVQQGEwJVUzEVMBMGA1UEChMMRGlnaUNlcnQgSW5jMRkwFwYDVQQLExB3\n' +
  'd3cuZGlnaWNlcnQuY29tMR8wHQYDVQQDExZSYXBpZFNTTCBUTFMgUlNBIENBIEcx\n' +
  'MB4XDTI1MDMyNDAwMDAwMFoXDTI2MDMyMzIzNTk1OVowFzEVMBMGA1UEAwwMKi5k\n' +
  'b3ViYW8uY29tMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAw6eEA/GD\n' +
  'ShJ0Rtlet3Lf+uYiYzzFJ6J1iJeT/JyvTwDOTKO2VgMjsFHgUcFJBG6QGZT6PXSv\n' +
  'vhkdzzIqqXzJwDsqqowwTwMk0YN/JUB0yr/9aFlmQakLZClu1W5og7uxp4ME+ep6\n' +
  'aJhoQ9MMCCn3/pvDnLoX1hG9z0pgbUsnIrM+1roLpH+D0FwC4jww7+tDr89/kjb4\n' +
  '/+LMqjAbe1fLtXJRuxH5O+kAQNqLL/0ECvq+4KpC/r/0UxTlRTpGZY2M3MPUEXfp\n' +
  'RKMmkRoRSKwDMJ5u2DK0qanvV6mu7ORPoDsC/fTAiqonjh8rClm/zpj5GN9BQKfu\n' +
  'UoaeWIN/XMZSzQIDAQABo4IDIDCCAxwwHwYDVR0jBBgwFoAUDNtsgkkPSmcKuBTu\n' +
  'esRIUojrVjgwHQYDVR0OBBYEFCseEe+vZQ8BzqzkOju1EhGQwoCYMCMGA1UdEQQc\n' +
  'MBqCDCouZG91YmFvLmNvbYIKZG91YmFvLmNvbTA+BgNVHSAENzA1MDMGBmeBDAEC\n' +
  'ATApMCcGCCsGAQUFBwIBFhtodHRwOi8vd3d3LmRpZ2ljZXJ0LmNvbS9DUFMwDgYD\n' +
  'VR0PAQH/BAQDAgWgMB0GA1UdJQQWMBQGCCsGAQUFBwMBBggrBgEFBQcDAjA/BgNV\n' +
  'HR8EODA2MDSgMqAwhi5odHRwOi8vY2RwLnJhcGlkc3NsLmNvbS9SYXBpZFNTTFRM\n' +
  'U1JTQUNBRzEuY3JsMHYGCCsGAQUFBwEBBGowaDAmBggrBgEFBQcwAYYaaHR0cDov\n' +
  'L3N0YXR1cy5yYXBpZHNzbC5jb20wPgYIKwYBBQUHMAKGMmh0dHA6Ly9jYWNlcnRz\n' +
  'LnJhcGlkc3NsLmNvbS9SYXBpZFNTTFRMU1JTQUNBRzEuY3J0MAwGA1UdEwEB/wQC\n' +
  'MAAwggF9BgorBgEEAdZ5AgQCBIIBbQSCAWkBZwB2AA5XlLzzrqk+MxssmQez95Df\n' +
  'm8I9cTIl3SGpJaxhxU4hAAABlcjhhZsAAAQDAEcwRQIhAKfZw1gNPE4sWKi3WL0U\n' +
  'vO4EGn+MD1hScKPMNHex6Ty+AiBv0yYWRuEURh/8ywDMHC+1f3xFaj9kshfv389b\n' +
  'e09MhAB1AGQRxGykEuyniRyiAi4AvKtPKAfUHjUnq+r+1QPJfc3wAAABlcjhhcUA\n' +
  'AAQDAEYwRAIgClXL9SnQFh+6HEqsT/3aBM6jK9NmzG+hrmJGowOKVFYCIEsGPJda\n' +
  'TtsBnc/PrhZSjOHitpzrzKhW02hHOzkrtlR/AHYASZybad4dfOz8Nt7Nh2SmuFuv\n' +
  'CoeAGdFVUvvp6ynd+MMAAAGVyOGF3gAABAMARzBFAiBExgNNV8q5xfdSU+yL6NAJ\n' +
  'l1ze5IYXTetQf04caLUhKgIhALvTCHHHdvokmFbRKQvrY50ihwDoHd4pKbzRtyQ0\n' +
  'H16bMA0GCSqGSIb3DQEBCwUAA4IBAQAsjyQpYDf1JiYBsO4koUcFPeAdvTp9FbRL\n' +
  'yC0PN34rekPHwcjqsEU7mbuUaZ4EMklHqIqkniStPcKyIDCpSwBu17iezM57fwJA\n' +
  'tb9XfzjxZH1vWEFHImcvMEwR0BLRmwXUnnRt3qOeetTV/UpIwH4HGfHldtRNqSnj\n' +
  'xDiM1c2oRjv+4Qs5CTet70NHsaQBjkUWvioCgigE+vuCPnjwVNXJkfSHjC+DWWzf\n' +
  'Nc+rSFEOvO8Fe4d2rvboT7vXigvTciOeQdig9ySCJQCkWxOvB1AcvZc+kw0YhrpM\n' +
  'xUBhDd+DaUWOgmmVS3n6k3GfOqm2EU7iCp8KyfRu2DAsnlsO/YpH\n' +
  '-----END CERTIFICATE-----';

// string转Uint8Array。
function stringToUint8Array(str: string): Uint8Array {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; i++) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

async function createX509Cert(certData: string): Promise<cert.X509Cert> {
  // 证书二进制数据，需业务自行赋值。
  let encodingBlob: cert.EncodingBlob = {
    data: stringToUint8Array(certData),
    // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
    encodingFormat: cert.EncodingFormat.FORMAT_PEM
  };

  let x509Cert: cert.X509Cert = {} as cert.X509Cert;
  try {
    x509Cert = await cert.createX509Cert(encodingBlob);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error('createX509Cert failed, errCode: ' + e.code + ', errMsg: ' + e.message);
  }
  return x509Cert;
}

async function createX509CertChain(): Promise<cert.X509CertChain> {
  const root = await createX509Cert(rootCert);
  const intermediate = await createX509Cert(intermediateCert);
  const leaf = await createX509Cert(leafCert);
  let x509CertChain: cert.X509CertChain = {} as cert.X509CertChain;
  try {
    x509CertChain = cert.createX509CertChain([leaf, intermediate, root]);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error('createX509CertChain failed, errCode: ' + e.code + ', errMsg: ' + e.message);
  }
  return x509CertChain;
}

async function validateOcsp() {
  const certChain = await createX509CertChain();
  console.info('createX509CertChain success.');
  const root = await createX509Cert(rootCert);
  console.info('createX509Cert success.');
  // 证书链校验数据，需业务自行赋值。
  const param: cert.CertChainValidationParameters = {
    trustAnchors: [{ CACert: root }],
    revocationCheckParam: {
      ocspResponderCert: root,
      options: [
        cert.RevocationCheckOptions.REVOCATION_CHECK_OPTION_IGNORE_NETWORK_ERROR,
        cert.RevocationCheckOptions.REVOCATION_CHECK_OPTION_PREFER_OCSP,
        cert.RevocationCheckOptions.REVOCATION_CHECK_OPTION_ACCESS_NETWORK
      ],
    }
  }
  try {
    await certChain.validate(param);
    console.info('validateOcsp success');
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error('validate failed, errCode: ' + e.code + ', errMsg: ' + e.message);
  }
}
```