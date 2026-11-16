# Certificate Management Command-Line Tool Usage Guide

<!--Kit: Device Certificate Kit-->
<!--Subsystem: Security-->
<!--Owner: @chaceli-->
<!--Designer: @chande-->
<!--Tester: @sunzibin001-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=c8093d1c731a16c88278ff4829f8fe5986157773 translatedAt=2026-11-03T05:05:40.072Z pushedAt=2026-11-03T06:48:04.226Z nl=1 -->

Starting from API version 26.0.1, the certificate management command-line tool (certmgr) is provided, mainly for installing user CA certificates on devices through the command line. It supports installing CA certificates at the current user level and the all users level (GlobalUser), supports certificate files in PEM/DER and PKCS#7 (P7B) formats, and also supports inputting certificate data through a pipe.

## Obtaining the Command Line Tool

Tools supported on OpenHarmony PC/2in1 devices: this tool is preinstalled with the system and requires no additional configuration. You can directly execute the certmgr command in a terminal window.

## Command List of the Command-Line Tool

| Command      | Description                                                         |
| ------------- | ------------------------------------------------------------ |
| -h            | Displays the commands supported by the tool.                         |
| installUserCA | Installs a user CA certificate.  |

## Help Command (-h)

```bash
# Query all command information supported by the tool.
certmgr -h

# Query the parameter information of the installUserCA command.
certmgr installUserCA -h
```

## Installing a User CA Certificate (installUserCA)

When installing a user CA certificate, the system triggers user identity authentication (PIN authentication) or administrator authorization authentication. The installation can be completed only after the authentication succeeds<!--RP1--><!--RP1End-->. When the `-g` parameter is specified, the certificate is installed to the all-users (GlobalUser) directory, which requires administrator authorization authentication. When the `-g` parameter is not specified, the certificate is installed to the current user directory, which requires user identity authentication.

**Parameters**

| Parameter        | Description               |
| ---------------- | ------------------------- |
| -h               | Displays help information.    |
| -g               | Installs the certificate to the all-users (GlobalUser) directory. By default, the certificate is installed to the current user directory. Optional. |
| -F certFileFormat | Certificate file format. Supports PEM_DER or P7B. The default value is PEM_DER. Optional. |
| certFile         | Path of the CA certificate file to be installed. Only one file can be specified.<br>Supports pipe input. Required when pipe input is not used. |

**Example**

```bash
# 1. Install a PEM/DER-format CA certificate to the current user.
certmgr installUserCA -F PEM_DER ca_cert.pem

# 2. Install a P7B-format CA certificate to the current user.
certmgr installUserCA -F P7B ca_cert.p7b

# 3. Install a CA certificate to the all-users (GlobalUser) directory.
certmgr installUserCA -g -F PEM_DER ca_cert.pem

# 4. Install a CA certificate through pipe input.
cat ca_cert.pem | certmgr installUserCA -F PEM_DER

# 5. Install a CA certificate to the current user using the default parameters (PEM_DER format).
certmgr installUserCA ca_cert.pem

# Output the certificate URI when the installation succeeds.
```

> **Note:**
>
> - When the `-g` parameter is used to install a certificate to the all-users (GlobalUser) directory, the operation is governed by the device security policy. The device security policy can control whether the current user is allowed to install an all-users CA certificate through the `installGlobalUserCA_defaultConfig`, `enableInstallGlobalUserCA_userList`, and `disableInstallGlobalUserCA_userList` configuration items.
> - When a certificate is installed, the system triggers the authentication UI. The title of the authentication UI is localized based on the device system language.
> - A P7B-format certificate may contain multiple certificates. After the installation succeeds, the URI of each certificate is output.

## Error Message

### CM_CMD_ERR_PARAM_INVALID

A command-line parameter error or invalid parameter occurs, and one of the following error messages is displayed:
- `Missing value for -F parameter`
- `Invalid certFileFormat: <format>`
- `Unknown parameter: <param>`
- `Multiple certificate files specified. Only one certificate file is allowed.`
- `certFile is required when no pipe input`
- `Install failed: Invalid argument`
- `Invalid file size: <size>`
- `No data from pipe input`

**Possible Causes**

1. When the `-F` parameter is used, no value is specified, or the specified value is not PEM_DER or P7B.
2. An unknown parameter is entered (a parameter starting with `-` that is not supported by the tool).
3. Multiple certificate files are specified, but the tool allows only one certificate file.
4. No certificate data is provided through a file path or pipe input.
5. The certificate file size is 0 or exceeds the maximum limit of the corresponding format (8196 bytes for the PEM_DER format and 307200 bytes, that is, 300 KB, for the P7B format).
6. No data is provided when inputting through a pipe.

**Solution**

1. Check whether the value of the `-F` parameter is PEM_DER or P7B.
2. Check whether the command contains parameters not supported by the tool, and remove redundant or incorrect parameters.
3. Ensure that only one certificate file path is specified.
4. If no certificate file path is specified, input the certificate data through a pipe.
5. Check that the certificate file has valid content and that the file size does not exceed the limit for the corresponding format (the PEM_DER format does not exceed 8196 bytes, and the P7B format does not exceed 307200 bytes, that is, 300 KB).
6. When using pipe input, ensure that the pipe contains valid certificate data. For example, pass the certificate file content via `cat ca_cert.pem | certmgr installUserCA`, and avoid an empty pipe or no data being passed, which would cause a read failure.

### CM_CMD_ERR_OPEN_FILE_FAIL

Failed to open the file. Error message: `Failed to open file: <filePath>`

**Possible Causes**

The input certificate file path does not exist or cannot be opened.

**Solution**

Check whether the certificate file path is correct, and ensure that the file exists and is readable.

### CM_CMD_ERR_INVALID_CERT_FORMAT

The certificate format is invalid. Error message: `Install failed: Invalid certificate format`

**Possible Causes**

The input certificate file format is invalid or does not meet the requirements. For example, in PEM_DER format, the input file is not a valid X.509 CA certificate in PEM format (Base64-encoded, containing the `-----BEGIN CERTIFICATE-----` and `-----END CERTIFICATE-----` header and footer markers) or DER format (binary-encoded); or in P7B format, the input file is not a valid PKCS#7 certificate file.

**Solution**

1. Confirm that the certificate file is a valid X.509 CA certificate. The PEM_DER format supports certificate files in PEM encoding (text format) or DER encoding (binary format), and the P7B format supports PKCS#7 certificate files.
2. Confirm that the format specified by the `-F` parameter matches the actual format of the certificate file. For example, use `-F PEM_DER` for PEM-format certificates and `-F P7B` for PKCS#7-format certificates.
3. Use a certificate tool (such as openssl) to verify whether the certificate file is valid, and re-install using a valid certificate file.

### CM_CMD_ERR_MAX_CERT_COUNT_REACHED

The certificate count has reached the maximum limit. Error message: `Install failed: Maximum certificate count reached`

**Possible Causes**

The number of user CA certificates in the system has reached the upper limit, and no further certificates can be installed.

**Solution**

Uninstall the user CA certificates that are no longer in use on the "Certificates & credentials" page in system settings, and then re-install after freeing up the certificate count quota.

### CM_CMD_ERR_DEVICE_ENTER_ADVSECMODE

The device enters advanced security mode. Error message: `Install failed: Device is in advanced security mode`

**Possible Causes**

The device has entered advanced security mode, in which installing user CA certificates is not allowed.

**Solution**

Exit advanced security mode on the device and then re-execute the installation command.

### CM_CMD_ERR_PERMISSION_DENIED

Restricted by the device security policy, error message: `The operation does not comply with the device security policy, the device does not allow users to manage the CA certificate of the global user`

**Possible Causes**

When using the `-g` parameter to install all users-level CA certificates, the current user is prohibited by the device security policy from managing global user CA certificates.

**Solution**

Check whether the device security policy configuration allows the current user to install all user-level CA certificates. The determination logic is as follows:
- `disableInstallGlobalUserCA_userList`: a list of user IDs separated by `|` (for example, `100|101`). If the current user ID is in this list, installation is prohibited.
- `installGlobalUserCA_defaultConfig`: the default policy, with a value of `enable` or `disable`. When the value is `disable`, installation is prohibited for all users by default, unless the current user ID is in `enableInstallGlobalUserCA_userList`.
- `enableInstallGlobalUserCA_userList`: a list of user IDs allowed to install, separated by `|`. It takes effect only when `installGlobalUserCA_defaultConfig` is `disable`.

That is, installation is allowed only when the current user is not in `disableInstallGlobalUserCA_userList`, and when `installGlobalUserCA_defaultConfig` is `disable`, the current user is in `enableInstallGlobalUserCA_userList`.

### CM_CMD_ERR_INTERNAL_ERROR

Internal error. Error message: `Install failed: Permission denied`

**Possible Causes**

The current user does not have the permission to call the API for installing a user CA certificate, which may be caused by an exception in another module.

**Solution**

Re-execute the command. If it fails multiple times, contact the system administrator for troubleshooting.

### CM_CMD_ERR_USER_CANCELLED

The user cancels authentication. Error message: `User cancelled authentication` or `User cancelled admin authorization`

**Possible Causes**

The user cancels the authentication operation on the identity authentication or administrator authorization screen.

**Solution**

Re-execute the command and complete identity authentication or administrator authorization on the authentication screen.
