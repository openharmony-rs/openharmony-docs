# Signature Tool Error Codes

<!--Kit: Common-->
<!--Subsystem: Security-->
<!--Owner: @scuteehuangjun-->
<!--Designer: @scuteehuangjun; @liuchibin-->
<!--Tester: @wwrongs-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=7874ed5a9b27c4f8bf820de615e2cfd32359db29 translatedAt=2026-10-31T02:20:53.229Z pushedAt=2026-10-31T02:35:38.236Z nl=1 -->

## 11010001 Unknown Error

**Error Message**

Unknown error.

**Error Description**

A system internal error occurs during the signing process.

**Possible Causes**

1. An error occurred during the signing process. Check the signature verification failure details in the log.
2. The size of the signed application package exceeds 4 GB. The error message is "uint32 value out of range: xxx".

**Solution**

1. Analyze the error log information output by the console together with the application package.
2. Reduce the software package size and repack it for signing.

<!--Del-->
## 11011001 Current Command Unsupported

**Error Message**

Unsupported command method.

**Error Description**

The current command is not supported.

**Possible Causes**

A parameter that is not supported by the signing tool is entered during the signing process.

**Solution**

Verify that the command line parameters are correct by referring to [hapsigner Guide](hapsigntool-guidelines.md#how-to-develop).

## 11011002 Parameter Check Error

**Error Message**

xxx param is incorrect.

**Error Description**

Failed to verify the signing parameter.

**Possible Causes**

1. The parameter value of the enum type is out of the allowed range.
2. The input file does not exist or cannot be read.

**Solution**

1. Verify that the command line parameters are correct by referring to [hapsigner Guide](hapsigntool-guidelines.md#how-to-develop).
2. Verify that the file specified by the **inFile** parameter is readable.

## 11011003 Incorrect Number of Parameters

**Error Message**

Check param num failed.

**Error Description**

The number of signing parameters is incorrect.

**Possible Causes**

The number of parameters required for signing is different from the actual number of parameters provided.

**Solution**

Verify that the command line parameters are correct by referring to [hapsigner Guide](hapsigntool-guidelines.md#how-to-develop).

## 11011004 Empty Parameter

**Error Message**

Check param failed.

**Error Description**

The parameter value is left empty.

**Possible Causes**

The parameter value is an empty string.

**Solution**

Verify that the parameter value in the signing command contains an empty string.

## 11011005 Untrusted Parameter

**Error Message**

Param is not trusted.

**Error Description**

The parameter is untrusted.

**Possible Causes**

An untrusted parameter is used during the signing process.

**Solution**

Verify that the command line parameters are correct by referring to [hapsigner Guide](hapsigntool-guidelines.md#how-to-develop).

## 11011006 Unpaired Parameter Name and Value

**Error Message**

Param {-key value} must in pairs.

**Error Description**

The parameter name and value are not paired.

**Possible Causes**

A parameter name is entered during the signing process, but the parameter value is not specified.

**Solution**

Verify that the command line parameters are correct by referring to [hapsigner Guide](hapsigntool-guidelines.md#how-to-develop).

## 11011007 Duplicate Parameters

**Error Message**

Param xxx is duplicated.

**Error Description**

The parameters are duplicate.

**Possible Causes**

Duplicate parameter names are entered during the signing process.

**Solution**

Verify that the command line parameters are correct by referring to [hapsigner Guide](hapsigntool-guidelines.md#how-to-develop).

## 11011008 Mandatory Parameters Missing

**Error Message**

Check param failed.

**Error Description**

Mandatory parameters are missing.

**Possible Causes**

Mandatory parameters (such as **inFile** and **keyAlias**) are not entered during the signing process.

**Solution**

Verify that the command line parameters are correct by referring to [hapsigner Guide](hapsigntool-guidelines.md#how-to-develop).

## 11012001 Failure to Load the Remote Signing Plugin

**Error Message**

Load remote sign plugin failed.

**Error Description**

Failed to load the remote signing plugin.

**Possible Causes**

When **mode** is set to **remoteSign**, a connection error occurs or the plugin fails to be loaded during the loading of the remote signing plugin.

**Solution**

The remoteSign mode is an extended mode reserved for the signing tool. Currently, this mode is not supported. You are advised to use the localSign mode.
<!--DelEnd-->

## 11012002 Input File Does Not Exist

**Error Message**

File not exist.

**Error Description**

The input file does not exist.

**Possible Causes**

1. The input file specified by the **inFile** parameter does not exist.
2. The certificate file specified by the **appCertFile** parameter does not exist.
3. The profile file specified by the **profileFile** parameter does not exist.

**Solution**

1. Verify that the input file specified by **inFile** exists.
2. Verify that the certificate file specified by **appCertFile** exists.
3. Verify that the profile file specified by **profileFile** exists.

## 11012003 File Writing Error

**Error Message**

Write file failed.

**Error Description**

An error occurs when writing data to the file.

**Possible Causes**

The user does not have the write permission on the output file specified by **outFile**.

**Solution**

Verify that the user has the write permission on the output file specified by **outFile**.

## 11012004 File Reading Error

**Error Message**

Read file failed.

**Error Description**

An error occurs when reading data from the file.

**Possible Causes**

The file specified by **profileFile** does not exist, or the user does not have the read permission on the file.

**Solution**

Verify that the file specified by **profileFile** exists and whether the user has the read permission on the file.

## 11012005 Unsupported File Format

**Error Message**

Not support file.

**Error Description**

The file format is not supported.

**Possible Causes**

An unsupported file name extension is entered during the signing process.

**Solution**

Enter a file in the correct format. The specific formats are as follows:
1. The file name extension of a signed profile file is .p7b.
2. The file name extension of an unsigned profile file is .json.
3. The file name extension of a certificate or certificate chain file is .cer.
4. The file name extension of a keystore file is .jks or .p12.

## 11012006 File I/O Error

**Error Message**

File IO failed.

**Error Description**

A file reading or writing error occurs during the signing process.

**Possible Causes**

1. The file specified by **inFile**, **keystoreFile**, **profileFile**, or **appCertFile** does not exist, or the current user does not have the read permission.
2. The user does not have the write permission on the output file specified by **outFile**.

**Solution**

1. Verify that the file specified by **inFile**, **keystoreFile**, **profileFile**, or **appCertFile** exists and whether the current user has the read permission.
2. Verify that the user has the write permission on the output file specified by **outFile**.

<!--Del-->
## 11013001 Incorrect Certificate Subject or Issuer Format

**Error Message**

Check DN format failed.

**Error Description**

The format of the certificate subject or issuer does not comply with RFC 2253.

**Possible Causes**

The format of the issuer or subject parameter is incorrect.

**Solution**

Check the format of the issuer or subject parameter.

The following format of the issuer or subject parameter is supported: *X*=*xx*, *XX*=*xxx*. Example: C=CN, O=OpenHarmony, CN=hapsigntool.
<!--DelEnd-->

## 11013002 Incorrect Certificate Chain File

**Error Message**

Certificate format is incorrect, please check your appCertFile parameter.

**Error Description**

The certificate chain file is incorrect.

**Possible Causes**

1. The certificate chain file specified by **appCertFile** is not a standard X.509 certificate or the file content has been modified.
2. The certificate in the certificate chain file specified by **appCertFile** has expired.

**Solution**

1. Verify that the certificate chain file specified by **appCertFile** is a standard X.509 certificate.
2. Update the certificate chain file.

<!--Del-->
## 11013003 Failure to Generate a CA Certificate

**Error Message**

Generate CA failed.

**Error Description**

Failed to generate a CA certificate.

**Possible Causes**

When a root CA certificate is generated, the certificate store file specified by **keystoreFile** is different from that specified by **issuerKeystoreFile**, or the certificate store password specified by **keystorePwd** is different from that specified by **issuerKeystorePwd**.

**Solution**

Verify that the command line parameters are correct by referring to [hapsigner Guide](hapsigntool-guidelines.md#how-to-develop).

## 11013004 Incorrect Number of Certificates in the Certificate Chain File

**Error Message**

Profile cert must a cert chain.

**Error Description**

The number of certificates in the certificate chain file is incorrect.

**Possible Causes**

The certificate chain file specified by **appCertFile** or **profileCertFile** must contain two or three certificates.

**Solution**

Check the number of certificates in the certificate chain file specified by **appCertFile** or **profileCertFile**.

## 11013005 Unsupported Algorithm

**Error Message**

No such algorithm.

**Error Description**

The signature algorithm is not supported.

**Possible Causes**

The signature algorithm specified by the **signAlg** parameter is not supported by the signing tool. The supported signature algorithms are SHA256withECDSA and SHA384withECDSA.

**Solution**

The signing tool supports only the following signature algorithms: SHA256withECDSA and SHA384withECDSA.

## 11013006 Certificate I/O Error

**Error Message**

Certificate IO failed.

**Error Description**

A file read/write exception occurs during CA certificate generation.

**Possible Causes**

The user does not have the write permission on the output file specified by **outFile**.

**Solution**

Verify that the user has the write permission on the output file specified by **outFile**.

## 11013007 Incorrect Certificate Subject

**Error Message**

Certificate check failed.

**Error Description**

Certificate subject check failed.

**Possible Causes**

The certificate subject specified by **distribution-certificate** or **development-certificate** in the profile file does not contain the **common name** field.

**Solution**

Check the certificate content of **distribution-certificate** or **development-certificate** in the profile file.

## 11013008 Failure to Generate a CSR

**Error Message**

generate csr failed.

**Error Description**

Failed to generate a CSR.

**Possible Causes**

A file read/write exception occurs during CSR generation.

**Solution**

Analyze the error based on the error log and command parameters.
<!--DelEnd-->

## 11014001 Key Not Found

**Error Message**

Key alias not found.

**Error Description**

The key with the specified alias does not exist in the keystore.

**Possible Causes**

The key specified by **keyAlias** does not exist in the keystore.

**Solution**

Verify that the key specified by **keyAlias** exists in the keystore.

<!--Del-->
## 11014002 Key Alias Exists

**Error Message**

Key alias is exist.

**Error Description**

The key alias already exists.

**Possible Causes**

When a key pair is generated, the keystore file specified by **keystoreFile** already contains a key whose name is the same as the value of **keyAlias**.

**Solution**

Check the entry information about the keystore file specified by **keystoreFile**.
<!--DelEnd-->

## 11014003 Keystore Initialization Failure

**Error Message**

Init keystore failed.

**Error Description**

Failed to initialize the keystore.

**Possible Causes**

1. The keystore file does not exist.
2. The password of the keystore file is incorrect.
3. The JDK version in the current running environment is earlier than that used for generating the keystore file.

**Solution**

1. Verify that the keystore file exists.
2. Verify that the password of the keystore file is correct.
3. Check the JDK version in the current running environment.

<!--Del-->
## 11014004 Incorrect Signature Key

**Error Message**

Invalid Key.

**Error Description**

The signature key is incorrect.

**Possible Causes**

The key algorithm specified by **keyAlias** does not match the signature algorithm specified by **signAlg**. For example, the key specified by **keyAlias** is an RSA key, while the signature algorithm specified by **signAlg** is SHA256withECDSA.

**Solution**

Verify that the key algorithm specified by **keyAlias** matches the signature algorithm specified by **signAlg**.

## 11014005 Incorrect Signature Parameter

**Error Message**

Not support algorithm.

**Error Description**

The signing parameter is invalid or the format is incorrect.

**Possible Causes**

1. The signing tool does not support the algorithm specified by **signAlg**.
2. The algorithm specified by **signAlg** does not match the key algorithm.

**Solution**

1. Verify that the value of **signAlg** is correct by referring to [hapsigner Guide](hapsigntool-guidelines.md#how-to-develop).
2. Verify that the algorithm specified by **signAlg** matches the key algorithm.

## 11014006 Keystore Error

**Error Message**

Keystore exception.

**Error Description**

The keystore file cannot be accessed or read.

**Possible Causes**

The keystore file cannot be accessed or read.

**Solution**

Analyze the error based on the fault log and keystore file output by the console.
<!--DelEnd-->

## 11014007 Incorrect Key Password

**Error Message**

Key alias xxx password error.

**Error Description**

The key password is incorrect.

**Possible Causes**

The key password is incorrect.

**Solution**

Check the key password specified by **keyAlias**.

## 11014008 No Available Certificate

**Error Message**

No usable cert found in xxx.

**Error Description**

No available certificate is found.

**Possible Causes**

The certificate corresponding to the key entry specified by **keyAlias** in the keystore file has expired.

**Solution**

Verify that the certificate corresponding to the key entry specified by **keyAlias** in the keystore file has expired.

## 11015001 Signature Exception

**Error Message**

Signature failed.

**Error Description**

The signature verification fails, and an invalid signature is returned.

**Possible Causes**

The signature verification or generation fails.

**Solution**

Analyze the error based on the error log and command line parameters output by the console.

## 11015002 Unmatched Certificate and Private Key

**Error Message**

Signature not matched.

**Error Description**

The certificate does not match the private key.

**Possible Causes**

The key used for signing the profile file does not match the corresponding certificate.

**Solution**

Verify that the key specified by **keyAlias** matches the certificate specified by **profileCertFile**.

## 11015003 Signature Verification Error

**Error Message**

Verify signature failed.

**Error Description**

Signature verification failed during the signing process.

**Possible Causes**

1. The key specified by **keyAlias** does not match the certificate specified by **appCertFile** during the signing process.
2. The certificate specified by **appCertFile** has expired.

**Solution**

1. Verify that the key specified by **keyAlias** matches the certificate specified by **appCertFile** during the signing process.
2. Update the certificate chain file.

<!--Del-->
## 11015004 Profile File Content Verification Error

**Error Message**

Verify profile failed.

**Error Description**

The content of the profile file is incorrect.

**Possible Causes**

The content of the profile file does not comply with the format requirements of the **HarmonyAppProvision** configuration file.

**Solution**

Check the content of the profile file by referring to [HarmonyAppProvision Configuration File](app-provision-structure.md#configuration-file-structure).

## 11015005 Profile File Integrity Check Error

**Error Message**

Verify profile failed.

**Error Description**

The profile file integrity check fails.

**Possible Causes**

The content of the signed profile file has been modified without authorization.

**Solution**

Generate a signed profile file again. For details, see [hapsigner Guide](hapsigntool-guidelines.md#when-to-use).
<!--DelEnd-->

## 11017001 Incorrect Software Package Format

**Error Message**

Read zip file failed.

**Error Description**

The format of the software package to be signed is incorrect.

**Possible Causes**

The HAP/HSP/HNP package to be signed does not comply with the ZIP specifications.

1. The file size exceeds 4 GB.

2. The number of entries (files and directories) exceeds 65,535.

**Solution**

1. Reduce the size of the software package and the number of files and directories in the software package.
2. Repack the software package and ensure that the package is in ZIP format.

## 11017002 Software Package Replication Exception

**Error Message**

Write zip file failed.

**Error Description**

Failed to copy the HAP, HSP, or HNP package to be signed.

**Possible Causes**

The user does not have the write permission on the output file specified by **outFile**.

**Solution**

Verify that the user has the write permission on the output file specified by **outFile**.

## 11017003 Incorrect Byte Alignment of the HAP Package

**Error Message**

Alignment zip file failed

**Error Description**

The byte alignment of the HAP package is incorrect.

**Possible Causes**

The byte alignment of the HAP package is incorrect.

**Solution**

Analyze the error based on the fault log and output by the console and the application package.

## 11017004 Incorrect Format of the Software Package to Be Signed

**Error Message**

Zip format failed

**Error Description**

The format of the software package to be signed is incorrect.

**Possible Causes**

The HAP, HSP, or HNP package to be signed does not comply with the ZIP specifications (such as the compression mode and file structure).

**Solution**

Repack the package and sign it again.

## 11017005 Signed Package Size Exceeds 4 GB

**Error Message**

The size of signed application is out of range

**Description**

The size of the signed HAP/HSP/HNP package exceeds 4 GB.

**Possible Causes**

The size of the HAP/HSP/HNP package to be signed is close to 4 GB, and after the signing block is written, the package size exceeds 4 GB.

**Solution**

Reduce the package size and repack and sign it.

## 11018001 Application Package Integrity Verification Failed

**Error Message**

Verify input HAP failed

**Description**

Failed to verify the enterprise application package to be re-signed.

**Possible Causes**

The enterprise application package to be re-signed is not signed or its integrity is compromised.

**Solution**

Repackage and sign the package.

## 11018002 Unsupported Application Distribution Type

**Error Message**

Unsupported application distribution type: xxx

**Description**

Unsupported application distribution type.

**Possible Causes**

The distribution type of the application to be re-signed specified by the inFile parameter is not an enterprise application.

**Solution**

Replace the application to be re-signed specified by the inFile parameter with an enterprise application whose distribution type is enterprise, enterprise_normal, or enterprise_mdm.

## 11106001 Invalid File Format

**Error Message**

Invalid file format.

**Error Description**

The input file format is incorrect.

**Possible Causes**

The input file format is not supported for code signing.

**Solution**

The following file formats are supported for code signing: HAP, HSP, and HQF.

## 11110001 Failure to Read the File Stream

**Error Message**

Input stream read error.

**Error Description**

Failed to read the file.

**Possible Causes**

Failed to read the file.

**Solution**

Try again or analyze the error based on the fault log and application package.

## 11111002 Certificate Error

**Error Message**

Certificates error.

**Error Description**

Failed to verify the certificate.

**Possible Causes**

1. The certificate is incorrect.

2. The value of the signing parameter **keyAlias** is incorrect.

**Solution**

1. Verify that the certificate format and content are correct.

2. Verify that the value of **keyAlias** is correct.

## 11112001 Incorrect Profile Content

**Error Message**

Profile content error.

**Error Description**

The profile content is incorrect.

**Possible Causes**

1. The content in JSON format in profile does not comply with the specifications.

2. **type** is missing or the value is invalid.

3. **bundle-info** is missing.

4. The value of **app-identifier** is of the incorrect type or the length is invalid.

**Solution**

1. Verify that the content in JSON format complies with the specifications.

2. Verify that the value of **type** is correct.

3. Add the content of **bundle-info**.

4. Ensure that the value of **app-identifier** is of the string type and contains 1 to 32 characters.

## 11112002 Incorrect module.json Content

**Error Message**

module.json content error.

**Error Description**

The content of the **module.json** file is incorrect.

**Possible Causes**

1. The content format of the **module.json** file does not comply with the specifications.

2. The HNP file in the application package is not described in the **module.json** file.

**Solution**

1. Verify that the content in JSON format complies with the specifications.

2. Add the HNP file description to the **module.json** file. For details, see [module.json5 Configuration File](../quick-start/module-configuration-file.md#hnppackages).

## 11112003 ELF File Error

**Error Message**

ELF is incorrect.

**Error Description**

Failed to parse the ELF file.

**Possible Causes**

The header information of the ELF file is incorrect.

**Solution**

Verify that the header information of the ELF file complies with the specifications.

## 11112004 HNP File Error

**Error Message**

Extract hnp file error.

**Error Description**

Failed to decompress the HNP file.

**Possible Causes**

Failed to extract or decompress the HNP file.

**Solution**

1. Perform signing again.

2. Verify that the HNP file is correctly packaged.

## 11113001 Algorithm Error

**Error Message**

Invalid algorithm.

**Error Description**

The signature algorithm is incorrect.

**Possible Causes**

The installed Java version does not support this digest algorithm.

**Solution**

The SHA-256 and SHA-512 algorithms are supported for code signing. Verify that the Java version is correct. Currently, Java 8 or a later version is supported.

## 11114001 Internal Signature Error

**Error Message**

Code sign internal error.

**Error Description**

An internal error of code signing occurs.

**Possible Causes**

An internal error occurs during the tool signing process.

**Solution**

Analyze the error based on the fault log and application package.