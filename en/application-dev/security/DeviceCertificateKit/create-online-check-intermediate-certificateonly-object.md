# Checking the Revocation Status of Intermediate CA Certificates in a Certificate Chain Online

<!--Kit: Device Certificate Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

The revocation status of intermediate CA certificates in a certificate chain can be checked online since API version 22.

## How to Develop

1. Import the [cert](../../reference/apis-device-certificate-kit/js-apis-cert.md) module.

   ```ts
   import { cert } from '@kit.DeviceCertificateKit';
   ```
2. Call [cert.createCertChain](../../reference/apis-device-certificate-kit/js-apis-cert.md#certcreatex509certchain11) to create a certificate chain object.

3. Call [cert.createX509Cert](../../reference/apis-device-certificate-kit/js-apis-cert.md#certcreatex509cert) to create an X.509 certificate object.

4. Construct the [cert.CertChainValidationParameters](../../reference/apis-device-certificate-kit/js-apis-cert.md#certchainvalidationparameters11) certificate chain verification parameters.

5. Call [cert.validate](../../reference/apis-device-certificate-kit/js-apis-cert.md#validate11) and pass the certificate chain verification parameters to check the certificate chain.

> **Description**
>
> The sample code provided in this development guide must be executed with the network configured.

Example:

```ts
import { cert } from '@kit.DeviceCertificateKit';

// Convert the string into a Uint8Array.
function stringToUint8Array(str: string): Uint8Array {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; i++) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

async function createCertChain(certData: string): Promise<cert.X509CertChain> {
  // Certificate binary data, which needs to match your case.
  let encodingBlob: cert.EncodingBlob = {
    data: stringToUint8Array(certData),
    // Assign a value based on the encodingData format. FORMAT_PEM and FORMAT_DER are supported.
    encodingFormat: cert.EncodingFormat.FORMAT_PEM
  };

  let X509CertChain: cert.X509CertChain = {} as cert.X509CertChain;
  try {
    X509CertChain = await cert.createX509CertChain(encodingBlob);
  } catch (err) {
    console.error(`createCertChain failed: errCode: ${err.code}, message: ${err.message}`);
  }
  return X509CertChain;
}
async function createCert(certData: string): Promise<cert.X509Cert> {
  // Certificate binary data, which needs to match your case.
  let encodingBlob: cert.EncodingBlob = {
    data: stringToUint8Array(certData),
    // Assign a value based on the encodingData format. FORMAT_PEM and FORMAT_DER are supported.
    encodingFormat: cert.EncodingFormat.FORMAT_PEM
  };

  let x509Cert: cert.X509Cert = {} as cert.X509Cert;
  try {
    x509Cert = await cert.createX509Cert(encodingBlob);
  } catch (err) {
    console.error(`createCert failed: errCode: ${err.code}, message: ${err.message}`);
  }
  return x509Cert;
}

let caChain =
"-----BEGIN CERTIFICATE-----\n" +
  "MIICezCCAiCgAwIBAgIUDczOyWG59LZLx2kP97vi5y0oL+QwCgYIKoZIzj0EAwIw\n" +
  "fjELMAkGA1UEBhMCQ04xEDAOBgNVBAgMB0JlaWppbmcxEDAOBgNVBAcMB0JlaWpp\n" +
  "bmcxHjAcBgNVBAoMFUVDRFNBIEludGVybWVkaWF0ZSBDQTELMAkGA1UECwwCSVQx\n" +
  "HjAcBgNVBAMMFUVDRFNBIEludGVybWVkaWF0ZSBDQTAeFw0yNTEwMTUwNjI3MzVa\n" +
  "Fw0zMDExMDgwNjI3MzVaMHUxCzAJBgNVBAYTAkNOMRAwDgYDVQQIDAdCZWlqaW5n\n" +
  "MRAwDgYDVQQHDAdCZWlqaW5nMRswGQYDVQQKDBJFQ0RTQSBFeGFtcGxlIENvcnAx\n" +
  "CzAJBgNVBAsMAklUMRgwFgYDVQQDDA93d3cuZXhhbXBsZS5jb20wWTATBgcqhkjO\n" +
  "PQIBBggqhkjOPQMBBwNCAASLR4TL7GQxOngZONYxay8vb5QQ2pDdaFobU2YSUC4m\n" +
  "dYxTsTyujMkTgK9sv/Me3Nf1lDXUz8mUCwVLHJ33hx3Jo4GEMIGBMAkGA1UdEwQC\n" +
  "MAAwCwYDVR0PBAQDAgK0MCcGA1UdEQQgMB6CD3d3dy5leGFtcGxlLmNvbYILZXhh\n" +
  "bXBsZS5jb20wHQYDVR0OBBYEFOp+v71yBI53o1mcrxqLOcZi0BrUMB8GA1UdIwQY\n" +
  "MBaAFDhFnzDg8Ap9glv7qyl8ajigm0OsMAoGCCqGSM49BAMCA0kAMEYCIQDIK8lp\n" +
  "z7+PNk6MxW45Lht9pUj/eAZfHW/692ZeJW1dfAIhAI1f3GEzkTihWd6h139gPXcS\n" +
  "y+Sf6/kfJnN0I3v/O2vI\n" +
  "-----END CERTIFICATE-----\n"                                        +
  "-----BEGIN CERTIFICATE-----\n" +
  "MIIEZjCCBAygAwIBAgIMTT/sw52uhI5Hi8tcMAoGCCqGSM49BAMCMFAxCzAJBgNV\n" +
  "BAYTAkJFMRkwFwYDVQQKDBBHbG9iYWxTaWduIG52LXNhMSYwJAYDVQQDDB1HbG9i\n" +
  "YWxTaWduIEVDQyBPViBTU0wgQ0EgMjAxODAeFw0yNTEwMTUwNjIwMzhaFw0yNTEx\n" +
  "MTQwNjIwMzhaMH4xCzAJBgNVBAYTAkNOMRAwDgYDVQQIDAdCZWlqaW5nMRAwDgYD\n" +
  "VQQHDAdCZWlqaW5nMR4wHAYDVQQKDBVFQ0RTQSBJbnRlcm1lZGlhdGUgQ0ExCzAJ\n" +
  "BgNVBAsMAklUMR4wHAYDVQQDDBVFQ0RTQSBJbnRlcm1lZGlhdGUgQ0EwWTATBgcq\n" +
  "hkjOPQIBBggqhkjOPQMBBwNCAARsa530tupy2vzI0ljPlGdO/QRMnXOv0R7cuQ8P\n" +
  "sTnaaqCBXrHZxrwoISe1c3+eq4CnJZBImvZSTSUUW9DfV31Co4ICnDCCApgwDAYD\n" +
  "VR0TBAUwAwEB/zAOBgNVHQ8BAf8EBAMCAe4wNQYDVR0lAQH/BCswKQYIKwYBBQUH\n" +
  "AwIGCCsGAQUFBwMBBggrBgEFBQcDAwYJKoZIhvcNAQkQMD8GA1UdHwQ4MDYwNKAy\n" +
  "oDCGLmh0dHA6Ly9jcmwuZ2xvYmFsc2lnbi5jb20vZ3NlY2NvdnNzbGNhMjAxOC5j\n" +
  "cmwwggGIBggrBgEFBQcBAQSCAXowggF2MIG4BggrBgEFBQcwAoaBq2h0dHBzOi8v\n" +
  "Z2l0Y29kZS5jb20vbTBfNzI2MTA3NzUvY29tcGF0aWJpbGl0eS9ibG9iL21hc3Rl\n" +
  "ci90ZXN0X3N1aXRlL3Jlc291cmNlL21hc3Rlci9zdGFuZGFyZCUyMHN5c3RlbS9h\n" +
  "Y3RzL3Jlc291cmNlL3NlY3VyaXR5L2NlcnRpZmljYXRlX2ZyYW1ld29yay8yMDI1\n" +
  "MDgxODE3ODgzNC9yb290LmNydDCBuAYIKwYBBQUHMAGGgatodHRwczovL2dpdGNv\n" +
  "ZGUuY29tL20wXzcyNjEwNzc1L2NvbXBhdGliaWxpdHkvYmxvYi9tYXN0ZXIvdGVz\n" +
  "dF9zdWl0ZS9yZXNvdXJjZS9tYXN0ZXIvc3RhbmRhcmQlMjBzeXN0ZW0vYWN0cy9y\n" +
  "ZXNvdXJjZS9zZWN1cml0eS9jZXJ0aWZpY2F0ZV9mcmFtZXdvcmsvMjAyNTA4MTgx\n" +
  "Nzg4MzQvcm9vdE9jc3AwNAYDVR0RBC0wK4IJbG9jYWxob3N0hwR/AAABhwTAqAEB\n" +
  "hhJodHRwOi8vMTkyLjE2OC4wLjIwHQYDVR0OBBYEFDhFnzDg8Ap9glv7qyl8ajig\n" +
  "m0OsMB8GA1UdIwQYMBaAFEYc/aft0QonL8U0/qNsvq3lrA9bMAoGCCqGSM49BAMC\n" +
  "A0gAMEUCIFsgnFqsgzPfzRtxLLqsh1tEQeW6xqp875XqpICR6FO7AiEAnJTGezte\n" +
  "A3uK46isQ2HwlmgwmXTNwgSP1JyWr5t6cVA=\n" +
  "-----END CERTIFICATE-----\n"                                        +
  "-----BEGIN CERTIFICATE-----\n" +
  "MIICGTCCAb6gAwIBAgIULcoKoYK2AQviXl1rlu+m7TH/J5UwCgYIKoZIzj0EAwMw\n" +
  "UDELMAkGA1UEBhMCQkUxGTAXBgNVBAoMEEdsb2JhbFNpZ24gbnYtc2ExJjAkBgNV\n" +
  "BAMMHUdsb2JhbFNpZ24gRUNDIE9WIFNTTCBDQSAyMDE4MB4XDTI1MTAxNTAzNTMw\n" +
  "OFoXDTM1MTAxMzAzNTMwOFowUDELMAkGA1UEBhMCQkUxGTAXBgNVBAoMEEdsb2Jh\n" +
  "bFNpZ24gbnYtc2ExJjAkBgNVBAMMHUdsb2JhbFNpZ24gRUNDIE9WIFNTTCBDQSAy\n" +
  "MDE4MFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAEJgdrEUKaVA8ZPzYD/kLwsn4c\n" +
  "UgkrCkTtMZEtG6l5iGTvpZT4qPTh8h5ILrui9bC+DLPRkEo3YsfHb62EanXqe6N2\n" +
  "MHQwHQYDVR0OBBYEFEYc/aft0QonL8U0/qNsvq3lrA9bMB8GA1UdIwQYMBaAFEYc\n" +
  "/aft0QonL8U0/qNsvq3lrA9bMAsGA1UdDwQEAwIBBjAJBgNVHREEAjAAMAkGA1Ud\n" +
  "EgQCMAAwDwYDVR0TAQH/BAUwAwEB/zAKBggqhkjOPQQDAwNJADBGAiEAz82HL4V2\n" +
  "3zTMVfJVMhHvSf2j+z7mUrRKCc0f21635DkCIQDqxlpMbRjs1bCL4pipCvD+w8v8\n" +
  "i4aEhDebPmxT8WuR7A==\n" +
  "-----END CERTIFICATE-----";
let caTrustCert =
  "-----BEGIN CERTIFICATE-----\n" +
  "MIICGTCCAb6gAwIBAgIULcoKoYK2AQviXl1rlu+m7TH/J5UwCgYIKoZIzj0EAwMw\n" +
  "UDELMAkGA1UEBhMCQkUxGTAXBgNVBAoMEEdsb2JhbFNpZ24gbnYtc2ExJjAkBgNV\n" +
  "BAMMHUdsb2JhbFNpZ24gRUNDIE9WIFNTTCBDQSAyMDE4MB4XDTI1MTAxNTAzNTMw\n" +
  "OFoXDTM1MTAxMzAzNTMwOFowUDELMAkGA1UEBhMCQkUxGTAXBgNVBAoMEEdsb2Jh\n" +
  "bFNpZ24gbnYtc2ExJjAkBgNVBAMMHUdsb2JhbFNpZ24gRUNDIE9WIFNTTCBDQSAy\n" +
  "MDE4MFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAEJgdrEUKaVA8ZPzYD/kLwsn4c\n" +
  "UgkrCkTtMZEtG6l5iGTvpZT4qPTh8h5ILrui9bC+DLPRkEo3YsfHb62EanXqe6N2\n" +
  "MHQwHQYDVR0OBBYEFEYc/aft0QonL8U0/qNsvq3lrA9bMB8GA1UdIwQYMBaAFEYc\n" +
  "/aft0QonL8U0/qNsvq3lrA9bMAsGA1UdDwQEAwIBBjAJBgNVHREEAjAAMAkGA1Ud\n" +
  "EgQCMAAwDwYDVR0TAQH/BAUwAwEB/zAKBggqhkjOPQQDAwNJADBGAiEAz82HL4V2\n" +
  "3zTMVfJVMhHvSf2j+z7mUrRKCc0f21635DkCIQDqxlpMbRjs1bCL4pipCvD+w8v8\n" +
  "i4aEhDebPmxT8WuR7A==\n" +
  "-----END CERTIFICATE-----";

async function doTestCaCheck() {
  try {
      let x509CertChain: cert.X509CertChain = await createCertChain(caChain);
      let x509Cert: cert.X509Cert = await createCert(caTrustCert);
      const param: cert.CertChainValidationParameters = {
        trustAnchors: [{
          CACert: x509Cert
        }],
        revocationCheckParam: {
          options: [
            cert.RevocationCheckOptions.REVOCATION_CHECK_OPTION_ACCESS_NETWORK,
            cert.RevocationCheckOptions.REVOCATION_CHECK_OPTION_CHECK_INTERMEDIATE_CA_ONLINE
          ],
        }
      };
      await x509CertChain.validate(param);
      console.info("validate result is success.");
  } catch (error) {
      console.error("x509CertChain validate failed error code is: " + error.code);
  }
}
```
