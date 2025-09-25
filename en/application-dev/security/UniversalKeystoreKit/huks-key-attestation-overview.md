# Key Attestation Overview and Algorithm Specifications

HUKS provides attestation for the public keys of asymmetric key pairs.

HUKS issues a certificate for the public key of an asymmetric key pair stored in HUKS using the public key infrastructure (PKI) certificate chain technology. The certificate can prove the validity of the public key. The service can use the root CA certificate provided by the system to verify the key certificates issued by HUKS level by level to ensure that the public key and private key in the certificates are from a trusted hardware device and stored in HUKS. In addition, the output key certificate contains the key owner information in the following format:
| Key Owner| Format| Description| 
| -------- | -------- | -------- |
| HAP| {appId:"xxx", bundleName:"xxx"} | **bundleName** indicates the bundle name of the application.| 
| System Services| {processName:"xxx", APL:"system_basic \| system_core"} | APL is [Ability Privilege Level](../../security/AccessToken/app-permission-mgmt-overview.md#basic-concepts-in-the-permission-mechanism).|

> **NOTE**
> 1. Key attestation is not supported if the caller is a system service with APL of **normal**. In this case, **processName** and **APL** are left empty.
> 2. Key attestation is not supported in Emulator scenarios.
> 3. The mini-system devices do not support key attestation.
> 4. Key attestation is available to both the keys generated and imported. The service side needs to check whether the key source meets the expectation based on the key source field in the service certificate on the server. The object identifier (OID) of the key source field is **1.3.6.1.4.1.2011.2.376.2.1.5**.  

The following table lists the key source and the corresponding value in the OID field.
| Key Source| OID Value|
| -------- | -------- |
| Import| 1 |
| Generation| <!--RP1-->2<!--RP1End--> | 

The key attestation process is as follows:

1. The service transfers the key alias and properties to HUKS.

2. HUKS issues an X.509 certificate chain, which consists of the root CA certificate, device CA certificate, device certificate, and key certificate in sequence, for the application.

3. The certificate chain is sent to a trusted server. The server parses the certificate chain and verifies the certificate chain validity and whether a single certificate is revoked.

<!--RP2-->
Currently, the system provides two key attestation modes.
- Anonymous key attestation: This type of attestation will not disclose the device information, and the caller does not require any permission. Anonymous key attestation is available to all applications. To protect user device information, third-party applications can use anonymous attestation only.
- Non-anonymous key attestation: The device information of the caller can be viewed, and the caller must have the [ohos.permission.ATTEST_KEY](../AccessToken/permissions-for-system-apps.md#ohospermissionattest_key) permission.
<!--RP2End-->

Currently, emulators <!--Del-->and developer boards <!--DelEnd-->support anonymous certificates. The certificate used in the debugging environment is not a real device certificate. You need to note this in cloud scenarios and avoid misuse.

## Supported Algorithms

The following table lists the supported key attestation specifications.
<!--Del-->
The key management service specifications include mandatory specifications and optional specifications. Mandatory specifications are algorithm specifications that must be supported. Optional specifications can be used based on actual situation. Before using the optional specifications, refer to the documents provided by the vendor to ensure that the specifications are supported.

**You are advised to use mandatory specifications in your development for compatibility purposes.**
<!--DelEnd-->

<!--Del-->
**Anonymous key attestation**
<!--DelEnd-->

| Algorithm| Description| API Version| <!--DelCol4-->Mandatory|
| -------- | -------- | -------- | -------- |
| RSA | The padding mode can be PSS or PKCS1_V1_5.| 11+ | Yes|
| ECC | - | 11+ | Yes|
| X25519 | - | 16+ | Yes|
| ED25519 | - | 16+ | Yes|
| SM2 | - | 11+ | Yes|

<!--Del-->
**Non-anonymous key attestation**

| Algorithm| Description| API Version| Mandatory|
| -------- | -------- | -------- | -------- |
| RSA | The padding mode can be PSS or PKCS1_V1_5.| 8+ | Yes|
| ECC | - | 8+ | Yes|
| X25519 | - | 8+ | Yes|
| ED25519 | - | 16+ | Yes|
| SM2 | - | 8+ | Yes|
<!--DelEnd-->
