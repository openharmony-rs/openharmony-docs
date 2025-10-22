# Binary Sign Tool

Binary Sign Tool is used to sign code of binary files on OpenHarmony PCs/2-in-1 devices. It supports code signing of standard ELF files or printing of signed ELF certificate information using commands.
You can find the tool in **toolchains/lib** of the OpenHarmony SDK library downloaded locally. The file name is **binary-sign-tool**.

## Environment
Before using this tool, you need to obtain [hdc](../dfx/hdc.md) and run the **hdc shell** command.

## Commands

| Command         | Description                                                        |
| ------------- | ------------------------------------------------------------ |
| help          | Displays the commands supported by the tool.                        |
| sign          | Signs a binary file.                  |
| display-sign  | Prints the certificate information of the file signature.            |

## help

```bash
# Display the help information.
binary-sign-tool -help
```

## sign

**Parameters**

| Parameter            | Description              |
| ---------------- | ---------------------- |
| -keyAlias        | Key alias, which is mandatory and case-insensitive.   |
| -keyPwd          | Key password, which is optional.|
| -appCertFile     | Signing certificate file (certificate chain, with entity certificate first, then intermediate CA, and root CA last), which is mandatory. |
| -profileFile     | Signed provision profile file name, in p7b format, which is optional.|
| -profileSigned   | Whether the profile is signed. The value **1** means signed, and value **0** means unsigned. The default value is **1**. This parameter is optional.  |
| -signAlg         | Signing algorithm, which can be **SHA256withECDSA** or **SHA384withECDSA**. This parameter is mandatory.|
| -keystoreFile    | Keystore file, which is mandatory in non-self-signed mode.    |
| -keystorePwd     | Keystore password, which is optional.|
| -inFile          | Original ELF file, which is mandatory.   |
| -outFile         | Signed file, which is mandatory.|
| -moduleFile      | Permission **module.json** file, which is optional.    |
| -selfSign        | Whether the local self-signed mode is used. The value **1** indicates that the local self-signed mode is used, and the value **0** indicates that the certificate signature mode is used. The default value is **0**. This parameter is optional.|

**Example**

```bash
# Sign a binary file.
binary-sign-tool sign -keyAlias "oh-app1-key-v1" -signAlg "SHA256withECDSA" -appCertFile "app1.pem" -profileFile "app1-profile.p7b" -profileSigned "1" -inFile "unsigned-elf" -keystoreFile "ohtest.p12" -outFile "signed-elf" -keyPwd "123456" -keystorePwd "123456" -moduleFile "module.json"
# Command output:
write code sign data success.
```

## display-sign

**Parameters**

| Parameter            | Description              |
| ---------------- | ---------------------- |
| -inFile          | ELF file, which is mandatory.   |

**Example**

```bash
# Print the certificate information of the binary file signature.
binary-sign-tool display-sign -inFile "signed-elf"
# Command output:
# 1. No code signature.
code signature is not found
# 2. Self-signed mode.
code signature is self-sign
# 3. Output the signing certificate.
```

## Error Message

### FILE_NOT_FOUND

**Description**

When the command is executed, the error message "ERROR - FILE_NOT_FOUND, code: -102. Details: The'OpenHarmony.p12' file does not exist or the path is invalid, parameter name'-keystoreFile'" is displayed.

**Possible Causes**

The input file does not exist or the path is incorrect.

**Solution**

Check whether the input file path or file name is correct.

### COMMAND_PARAM_ERROR

**Description**

When the command is executed, the error message "ERROR - COMMAND_PARAM_ERROR, code: -107. Details: 'generate-cert' Parameters error, Param key - value must in pairs" is displayed.

**Possible Causes**

1. An unnecessary part is pasted in the command.
2. The **value** of the last parameter is not entered.

**Solution**

Check and correct the unnecessary or incorrect part in the command.

### KEY_PASSWORD_ERROR

**Description**

When the command is executed, the error message "ERROR - KEY_PASSWORD_ERROR, code: -114. Details: 'oh-app1-key-v1' keypair password error" is displayed.

**Possible Causes**

If the key pair password is incorrect, the **KEY_PASSWORD_ERROR** error occurs.

**Solution**

Check whether the password parameter in the command is correct. Ensure that the key pair password is correct when accessing different keystores.

### NOT_SUPPORT_ERROR

**Description**

When the command is executed, the error message "ERROR - NOT_SUPPORT_ERROR, code: -104. Details: Not support file: ./OpenHarmony.p12" is displayed.

**Possible Causes**

The keystore file type is incorrect.

**Solution**

Ensure that the keystore file name extension is **.p12**.

### KEY_ALIAS_ERROR

**Description**

When the command is executed, the error message "ERROR - KEY_ALIAS_ERROR, code: -109. Details: 'XXX' key alias already exists and cannot be generated repeatedly" is displayed.

**Possible Causes**

The key pair with the same alias already exists in the keystore.

**Solution**

Rename the alias of the key pair.

### SIGN_ERROR

**Description**

After the command is executed, the error message "ERROR - SIGN_ERROR, code: -105. Details: No certificates configured for sign" is displayed.

**Possible Causes**

The signing key does not match the entity certificate.

**Solution**

1. Check whether the **keyAlias** key is correct.
2. Check whether the **appCertFile** is correct. Ensure that the key matches the certificate.
