# @ohos.security.certManager

The **certManager** module provides system-level certificate management capabilities to implement management and secure use of certificates throughout their lifecycle (installation, storage, use, and destruction).

It can be used to verify the HTTPS certificate chain of the application server , and log in to the website or application server using two-way HTTPS.

**Since:** 11

**System capability:** SystemCapability.Security.CertificateManager

## Modules to Import

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [abort](arkts-devicecertificate-certificatemanager-abort-f.md) | Aborts the signing or signature verification operation. This method is mutually exclusive with the finish method. Only one method can be invoked in a signature verification process. This API uses an asynchronous callback to return the result. |
| [abort](arkts-devicecertificate-certificatemanager-abort-f.md) | Aborts the signing or signature verification operation. This method is mutually exclusive with the finish method. Only one method can be invoked in a signature verification process. This API uses a promise to return the result. |
| [finish](arkts-devicecertificate-certificatemanager-finish-f.md) | Finishes the signing operation. This is the last step in the signature process. The init and update interfaces need to be invoked first. This API uses an asynchronous callback to return the result. |
| [finish](arkts-devicecertificate-certificatemanager-finish-f.md) | Finishes the signature verification operation. This is the last step in the signature verification process. The init and update interfaces need to be invoked first. This API uses an asynchronous callback to return the result. |
| [finish](arkts-devicecertificate-certificatemanager-finish-f.md) | Finishes the signing or signature verification operation. This API uses a promise to return the result. |
| [getAllUserTrustedCertificates](arkts-devicecertificate-certificatemanager-getallusertrustedcertificates-f.md) | Obtains all user trusted root CA certificates of the device. This API uses a promise to return the result. |
| [getAllUserTrustedCertificates](arkts-devicecertificate-certificatemanager-getallusertrustedcertificates-f.md) | Obtains the user root CA certificates based on the certificate scope. This API uses a promise to return the result. |
| [getCertificateStorePath](arkts-devicecertificate-certificatemanager-getcertificatestorepath-f.md) | Obtains the certificate storage path. |
| [getPrivateCertificate](arkts-devicecertificate-certificatemanager-getprivatecertificate-f.md) | Obtains detailed information about a private credential. This API uses an asynchronous callback to return the result. |
| [getPrivateCertificate](arkts-devicecertificate-certificatemanager-getprivatecertificate-f.md) | Obtains detailed information about a private credential. This API uses a promise to return the result. |
| [getPrivateCertificates](arkts-devicecertificate-certificatemanager-getprivatecertificates-f.md) | Obtains the credentials for installing the application. This API uses a promise to return the result asynchronously. |
| [getPublicCertificate](arkts-devicecertificate-certificatemanager-getpubliccertificate-f.md) | Obtains detailed information about a public credential. This API uses a promise to return the result. |
| [getUkeyCertificate](arkts-devicecertificate-certificatemanager-getukeycertificate-f.md) | Obtains the details of a USB Key credential. This API uses a promise to return the result. |
| [getUkeyCertificateList](arkts-devicecertificate-certificatemanager-getukeycertificatelist-f.md) | Obtains the list of USB Key credential . This API uses a promise to return the result. |
| [getUserTrustedCertificate](arkts-devicecertificate-certificatemanager-getusertrustedcertificate-f.md) | Obtains the detailed information about a user root CA certificate. This API uses a promise to return the result. |
| [importUkeyCertificate](arkts-devicecertificate-certificatemanager-importukeycertificate-f.md) | Import the certificate to the USB Key. |
| [init](arkts-devicecertificate-certificatemanager-init-f.md) | Indicates the initialization of signature and signature verification using credentials. This is the first step in the signature verification process. Later, the update and finish interfaces need to be invoked in sequence to complete the operations. Use Callback to return the result asynchronously. |
| [init](arkts-devicecertificate-certificatemanager-init-f.md) | Initializes the signing or signature verification operation using the specified credential. This API uses a promise to return the result. |
| [installPrivateCertificate](arkts-devicecertificate-certificatemanager-installprivatecertificate-f.md) | Installs a private credential. This API uses an asynchronous callback to return the result. |
| [installPrivateCertificate](arkts-devicecertificate-certificatemanager-installprivatecertificate-f.md) | Installs a private credential. This API uses a promise to return the result. |
| [installPrivateCertificate](arkts-devicecertificate-certificatemanager-installprivatecertificate-f.md) | Installs a private credential and specifies its storage level. This API uses a promise to return the result. |
| [installUserTrustedCertificate](arkts-devicecertificate-certificatemanager-installusertrustedcertificate-f.md) | Install the user CA certificate. Use Promise asynchronous callback. |
| [installUserTrustedCertificateSync](arkts-devicecertificate-certificatemanager-installusertrustedcertificatesync-f.md) | Installs a user CA certificate. |
| [isAuthorizedApp](arkts-devicecertificate-certificatemanager-isauthorizedapp-f.md) | Checks whether this application is authorized by the specified user credential. This API uses a promise to return the result. |
| [uninstallPrivateCertificate](arkts-devicecertificate-certificatemanager-uninstallprivatecertificate-f.md) | Uninstalls a private credential. This API uses an asynchronous callback to return the result. |
| [uninstallPrivateCertificate](arkts-devicecertificate-certificatemanager-uninstallprivatecertificate-f.md) | Uninstalls a private credential. This API uses a promise to return the result. |
| [uninstallUserTrustedCertificateSync](arkts-devicecertificate-certificatemanager-uninstallusertrustedcertificatesync-f.md) | Uninstalls a user CA certificate. |
| [update](arkts-devicecertificate-certificatemanager-update-f.md) | Updates the data for the signing or signature verification operation. It needs to be invoked after the init operation to transfer the data to be signed and verified. This API uses an asynchronous callback to return the result. |
| [update](arkts-devicecertificate-certificatemanager-update-f.md) | Updates the data for the signing or signature verification operation. This API uses a promise to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getAllAppPrivateCertificates](arkts-devicecertificate-certificatemanager-getallappprivatecertificates-f-sys.md) | Obtains all private credentials. This API uses an asynchronous callback to return the result. |
| [getAllAppPrivateCertificates](arkts-devicecertificate-certificatemanager-getallappprivatecertificates-f-sys.md) | Obtains all private credentials. This API uses a promise to return the result. |
| [getAllAppPrivateCertificatesByUid](arkts-devicecertificate-certificatemanager-getallappprivatecertificatesbyuid-f-sys.md) | Obtains all private credentials of a specified application. This API is called only by the certificate management application. This API uses a promise to return the result. |
| [getAllPublicCertificates](arkts-devicecertificate-certificatemanager-getallpubliccertificates-f-sys.md) | Obtains the public credentials of all users. This API is called only by the certificate management application. This API uses a promise to return the result. |
| [getAllSystemAppCertificates](arkts-devicecertificate-certificatemanager-getallsystemappcertificates-f-sys.md) | Obtains all system credentials. This API uses a promise to return the result. |
| [getAuthorizedAppList](arkts-devicecertificate-certificatemanager-getauthorizedapplist-f-sys.md) | Obtains the list of authorized applications of a user's public credential. This API is called only by the certificate management application. This API uses a promise to return the result. |
| [getSystemAppCertificate](arkts-devicecertificate-certificatemanager-getsystemappcertificate-f-sys.md) | Obtains the credential details of the system application. This API is called only by the certificate management application. This API uses a promise to return the result. |
| [getSystemTrustedCertificate](arkts-devicecertificate-certificatemanager-getsystemtrustedcertificate-f-sys.md) | Obtains details about a CA certificate trusted by the system. This API is called only by the certificate management application. This API uses a promise to return the result. |
| [getSystemTrustedCertificateList](arkts-devicecertificate-certificatemanager-getsystemtrustedcertificatelist-f-sys.md) | Obtains the list of CA certificates trusted by the system. This API is called only by the certificate management application. This API uses a promise to return the result. |
| [grantPublicCertificate](arkts-devicecertificate-certificatemanager-grantpubliccertificate-f-sys.md) | Grants the permission for an application to use the public credentials of a user. This API is called only by the certificate management application. This API uses a promise to return the result. |
| [installPublicCertificate](arkts-devicecertificate-certificatemanager-installpubliccertificate-f-sys.md) | Installs the public credential of the user. This API is called only by the certificate management application. This API uses a promise to return the result. |
| [installSystemAppCertificate](arkts-devicecertificate-certificatemanager-installsystemappcertificate-f-sys.md) | Installs the system application credential. This API is called only by the certificate management application. This API uses a promise to return the result. |
| [removeGrantedPublicCertificate](arkts-devicecertificate-certificatemanager-removegrantedpubliccertificate-f-sys.md) | Removes the permission for an application to use the public credentials of a user. This API is called only by the certificate management application. This API uses a promise to return the result. |
| [setCertificateStatus](arkts-devicecertificate-certificatemanager-setcertificatestatus-f-sys.md) | Sets the status of a CA certificate. Currently, only the status of a user's CA certificate can be set. This API is called only by the certificate management application. This API uses a promise to return the result. |
| [uninstallAllAppCertificate](arkts-devicecertificate-certificatemanager-uninstallallappcertificate-f-sys.md) | Uninstalls all system application credentials and public user credentials. This API is called only by the certificate management application. This API uses a promise to return the result. |
| [uninstallAllUserTrustedCertificate](arkts-devicecertificate-certificatemanager-uninstallallusertrustedcertificate-f-sys.md) | Uninstalls all CA certificates trusted by the user. This API is called only by the certificate management application. This API uses a promise to return the result. |
| [uninstallPublicCertificate](arkts-devicecertificate-certificatemanager-uninstallpubliccertificate-f-sys.md) | Uninstalls the public credential of the user. This API is called only by the certificate management application. This API uses a promise to return the result. |
| [uninstallSystemAppCertificate](arkts-devicecertificate-certificatemanager-uninstallsystemappcertificate-f-sys.md) | Uninstalls the credential of the system application. This API is called only by the certificate management application. This API uses a promise to return the result. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [CertAbstract](arkts-devicecertificate-certificatemanager-certabstract-i.md) | Represents brief information about a certificate. |
| [CertBlob](arkts-devicecertificate-certificatemanager-certblob-i.md) | Indicates the certificate file data. |
| [CertInfo](arkts-devicecertificate-certificatemanager-certinfo-i.md) | Represents detailed information about a certificate. |
| [CertStoreProperty](arkts-devicecertificate-certificatemanager-certstoreproperty-i.md) | Represents the storage information about a certificate, including the certificate type and location. |
| [CMHandle](arkts-devicecertificate-certificatemanager-cmhandle-i.md) | Represents the handle to a signing or signature verification operation. |
| [CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md) | Represents the result returned. |
| [CMSignatureSpec](arkts-devicecertificate-certificatemanager-cmsignaturespec-i.md) | Represents a set of parameters used for signing or signature verification, including the key usage purpose, padding mode, and digest algorithm. |
| [Credential](arkts-devicecertificate-certificatemanager-credential-i.md) | Represents detailed information about a credential. |
| [CredentialAbstract](arkts-devicecertificate-certificatemanager-credentialabstract-i.md) | Represents brief information about a credential. |
| [UkeyInfo](arkts-devicecertificate-certificatemanager-ukeyinfo-i.md) | Provides USB Key certificate credential attribute information. |

### Enums

| Name | Description |
| --- | --- |
| [AuthStorageLevel](arkts-devicecertificate-certificatemanager-authstoragelevel-e.md) | Enumerates the credential storage levels. |
| [CertAlgorithm](arkts-devicecertificate-certificatemanager-certalgorithm-e.md) | Enumerates the certificate algorithms. |
| [CertFileFormat](arkts-devicecertificate-certificatemanager-certfileformat-e.md) | Represents the certificate file format. |
| [CertificatePurpose](arkts-devicecertificate-certificatemanager-certificatepurpose-e.md) | Enumerates the usage of a credential. |
| [CertScope](arkts-devicecertificate-certificatemanager-certscope-e.md) | Enumerates the certificate scopes. |
| [CertType](arkts-devicecertificate-certificatemanager-certtype-e.md) | Enumerates the certificate types. |
| [CMErrorCode](arkts-devicecertificate-certificatemanager-cmerrorcode-e.md) | Enumerates the error codes used in the certificate management APIs. |
| [CmKeyDigest](arkts-devicecertificate-certificatemanager-cmkeydigest-e.md) | Enumerates the digest algorithms that can be used for signing and signature verification. |
| [CmKeyPadding](arkts-devicecertificate-certificatemanager-cmkeypadding-e.md) | Enumerates the padding modes that can be used for signing and signature verification. |
| [CmKeyPurpose](arkts-devicecertificate-certificatemanager-cmkeypurpose-e.md) | Enumerates the purposes of using the key. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [CMErrorCode](arkts-devicecertificate-certificatemanager-cmerrorcode-e-sys.md) | Enumerates the error codes used in the certificate management APIs. |
<!--DelEnd-->
