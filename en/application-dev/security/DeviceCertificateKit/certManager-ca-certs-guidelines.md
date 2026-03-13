# CA Certificate Development

<!--Kit: Device Certificate Kit-->
<!--Subsystem: Security-->
<!--Owner: @chaceli-->
<!--Designer: @chande-->
<!--Tester: @zhangzhi1995-->
<!--Adviser: @zengyawen-->

> **NOTE**
>
> This guide applies to the SDK of API version 12 or later.

## Scenarios

Typical scenarios:

- Install a user CA certificate. The caller can install the user CA certificate in the current user or device public directory.
  - If the certificate is installed in the current user directory, only the services of the current user can access the certificate.
  - If the certificate is installed in the device public directory, services of all users can access the certificate.
- Obtain the list of user CA certificates from the current user or device public directory.
- Obtain the details of a user CA certificate.
- Delete a user CA certificate.
- Obtain the storage path of a CA certificate.

## Available APIs

For details about the APIs, see [Certificate Management](../../reference/apis-device-certificate-kit/js-apis-certManager.md).

The following table describes the commonly used APIs.

| Instance         | API                                                      | Description                                        |
| --------------- | ------------------------------------------------------------ | -------------------------------------------- |
| certificateManager        | installUserTrustedCertificateSync(cert: Uint8Array, certScope: CertScope) : CMResult<sup>18+</sup> | Installs a user CA certificate.       |
| certificateManager        | uninstallUserTrustedCertificateSync(certUri: string) : void<sup>18+</sup> | Deletes a user CA certificate.      |
| certificateManager        | getAllUserTrustedCertificates(): Promise\<CMResult> | Obtains the list of all user root CA certificates in the current user and device public directories.|
| certificateManager        | getAllUserTrustedCertificates(scope: CertScope): Promise\<CMResult><sup>18+</sup> | Obtains the list of user root CA certificates based on the certificate storage path.|
| certificateManager        | getUserTrustedCertificate(certUri: string): Promise\<CMResult> | Obtains the details about a user root CA certificate.|
| certificateManager | getCertificateStorePath(property: CertStoreProperty): string<sup>18+</sup> | Obtains the storage path of a certificate.|

## How to Develop

1. Request and declare permissions.

   To use the API for installing or deleting a certificate, request the **ohos.permission.ACCESS_ENTERPRISE_USER_TRUSTED_CERT** or **ohos.permission.ACCESS_USER_TRUSTED_CERT** permission.

   To use the API for obtaining the certificate list or details, request the **ohos.permission.ACCESS_CERT_MANAGER** permission.

   For details about how to request permissions, see [Workflow for Requesting Permissions](../AccessToken/determine-application-mode.md).

   For details about how to declare permissions, see [Declaring Permissions](../AccessToken/declare-permissions.md).

2. Import the required module.

   ```ts
   import { certificateManager } from '@kit.DeviceCertificateKit';
   ```

3. Install a user CA certificate, obtain the list of user CA certificates, obtain the details of the user certificate, and delete the user CA certificate.

   <!-- @[certificate_management_user_ca](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DeviceCertificateKit/CertificateManagement/entry/src/main/ets/samples/CertManagerUserCASample.ets) -->
   
   ``` TypeScript
   import { certificateManager } from '@kit.DeviceCertificateKit';
   import { util } from '@kit.ArkTS';
   
   async function userCASample() {
     /* The user CA certificate data to be installed must be assigned based on the service. */
     let userCAData: Uint8Array = new util.TextEncoder().encodeInto('-----BEGIN CERTIFICATE-----\n' +
       'MIIDSTCCAjECFFRZKkiBuiZ+zqfjJOg05yeTePM9MA0GCSqGSIb3DQEBCwUAMGEx\n' +
       'CzAJBgNVBAYTAmNuMQ0wCwYDVQQIDARvaG9zMQswCQYDVQQHDAJjbTEhMB8GA1UE\n' +
       'CgwYSW50ZXJuZXQgV2lkZ2l0cyBQdHkgTHRkMRMwEQYDVQQDDApUZXN0Um9vdENB\n' +
       'MB4XDTI1MTAxNTA3MzE0MloXDTI2MTAxNTA3MzE0MlowYTELMAkGA1UEBhMCY24x\n' +
       'DTALBgNVBAgMBG9ob3MxCzAJBgNVBAcMAmNtMSEwHwYDVQQKDBhJbnRlcm5ldCBX\n' +
       'aWRnaXRzIFB0eSBMdGQxEzARBgNVBAMMClRlc3RSb290Q0EwggEiMA0GCSqGSIb3\n' +
       'DQEBAQUAA4IBDwAwggEKAoIBAQC5p4eoQJyTBvn01M8SwEi8dguTIPGmD3a8SGIj\n' +
       'KXaB6ltv742H5EBjgk+zC8+Gis0ehEqwk3pVnnmByeYvrERxsUqDt69/FndlfTxI\n' +
       'C2/2MxWVk97g/6TpJ5Lt2mTrH+rSOgUDyU27aPn12ZnDF1mLsT+U+CBmfj4+J4tW\n' +
       'yzdFNj7kcKMQQok+L1dtFlDNMNpMA1UqADzoC3XgFl49CpDtoFId9DVsgUPkPfX1\n' +
       '89cCunomgJe1b17FzxfNu2yhbl5cnUEjeHGbmBgBIB7uG8tjGstnDPx7fl3Xrj+Q\n' +
       'fRrwCpVKD9RxoyUBFbHttixxY5bHFUdvHRB251sxD+JfxxxLAgMBAAEwDQYJKoZI\n' +
       'hvcNAQELBQADggEBAEGbNqcMU7C/lrIytI/OTtzYbkWDsfnRSPxlCUoZ2Xh3S83A\n' +
       'SNQ9Ze5tDwWdW9Hlde9May6hzvuQSYeMLLnyM8WGResXCs7UbnSQe7fGfUu+xDGb\n' +
       'h4tamnRFtZydxCCgDT9lIdHeutlPwOuxlR4HXpeowGeGJX0iFrdo6D0iXAY34hic\n' +
       'yLQzuBqE/1s3PLA83Fi4EOOOV7P/ahmOLtBFlHbySHV68i9PNeNr9SDykH9/RgI9\n' +
       '5G8ZTZj8oSmbTGGtfNuVXybMyJMRlz6BkxG++kYcg7STRBqHGX7RrWHiupguNreO\n' +
       '4sJBdSpWBq172ZEyOvTqC4xX9lLYqwwBQ++TFoo=\n' +
       '-----END CERTIFICATE-----');
   
     let certUri: string = '';
     let certScope = certificateManager.CertScope.CURRENT_USER;
     try {
       /* Install the user CA certificate in the current user directory. */
       let result = certificateManager.installUserTrustedCertificateSync(userCAData, certScope);
       certUri = (result.uri != undefined) ? result.uri : '';
       console.info(`Succeeded in install user ca cert, certUri is ${certUri}`);
     } catch (err) {
       console.error(`Failed to install user ca cert. Code: ${err.code}, message: ${err.message}`);
     }
   
     try {
       /* Obtain the details of the user CA certificate. */
       let result = await certificateManager.getUserTrustedCertificate(certUri);
       if (result === undefined || result.certInfo == undefined) {
         console.error('The result of getting user ca cert is undefined.');
       } else {
         let certInfo = result.certInfo;
         console.info('Succeeded in getting user ca cert.');
       }
     } catch (err) {
       console.error(`Failed to get user ca certificate. Code: ${err.code}, message: ${err.message}`);
     }
   
     try {
       /* Obtain the list of user CA certificates in the current user directory. */
       let result = await certificateManager.getAllUserTrustedCertificates(certScope);
       if (result == undefined) { /* If the number of root CA certificates is 0, the returned result is undefined. */
         console.info('the count of the user trusted certificates is 0');
       } else if (result.certList == undefined) {
         console.error('The result of getting current user trusted certificates is undefined.');
       } else {
         let list = result.certList;
         console.info('Succeeded in getting user ca cert list.');
       }
     } catch (err) {
       console.error(`Failed to get user ca certificate. Code: ${err.code}, message: ${err.message}`);
     }
   
     try {
       /* Delete the installed user CA certificate. */
       certificateManager.uninstallUserTrustedCertificateSync(certUri);
     } catch (err) {
       console.error(`Failed to uninstall user ca certificate. Code: ${err.code}, message: ${err.message}`);
     }
   }
   ```


4. Obtain the paths of system CA certificates and user CA certificates so applications can access them.

   <!-- @[certificate_management_get_ca_path](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DeviceCertificateKit/CertificateManagement/entry/src/main/ets/samples/CertManagerGetCAPathSample.ets) -->
   
   ``` TypeScript
   import { certificateManager } from '@kit.DeviceCertificateKit';
   
   function getUserCaPathSample() {
     try {
       /* Obtain the storage path of the system CA certificates. */
       let property1: certificateManager.CertStoreProperty = {
         certType: certificateManager.CertType.CA_CERT_SYSTEM,
       }
       let systemCAPath = certificateManager.getCertificateStorePath(property1);
       console.info(`Success to get system ca path: ${systemCAPath}`);
   
       /* Obtain the storage path of the CA certificates for the current user. */
       let property2: certificateManager.CertStoreProperty = {
         certType: certificateManager.CertType.CA_CERT_USER,
         certScope: certificateManager.CertScope.CURRENT_USER,
       }
       let userCACurrentPath = certificateManager.getCertificateStorePath(property2);
       console.info(`Success to get current user's user ca path: ${userCACurrentPath}`);
   
       /* Obtain the storage path of the CA certificates for all users. */
       let property3: certificateManager.CertStoreProperty = {
         certType: certificateManager.CertType.CA_CERT_USER,
         certScope: certificateManager.CertScope.GLOBAL_USER,
       }
       let globalCACurrentPath = certificateManager.getCertificateStorePath(property3);
       console.info(`Success to get global user's user ca path: ${globalCACurrentPath}`);
     } catch (error) {
       console.error(`Failed to get store path. Code: ${error.code}, message: ${error.message}`);
     }
   }
   ```
