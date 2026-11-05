# Generating and Restoring DLP Encrypted Files
<!--Kit: Data Protection Kit-->
<!--Subsystem: Security-->
<!--Owner: @winnieHuYu-->
<!--Designer: @QRF-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=eef9add48dd77c504f78fa94f4924cac143a2e1a translatedAt=2026-10-31T07:07:35.298Z pushedAt=2026-10-31T09:17:30.467Z nl=1 -->

## When to Use

Data Protection Kit provides applications with the capability to generate DLP files from plaintext files and to decrypt DLP files back into the original plaintext files. Applications do not need to define a custom encrypted file format; they only need to use the DLP file generation and decryption capabilities provided by OpenHarmony to protect sensitive files through encryption.

## Development Procedure

1. Import the modules required by the APIs. 
    <!-- @[dlp_include_dlpPermission](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    import { dlpPermission } from '@kit.DataProtectionKit';
    ```

2. Encrypt the file.

    2.1 Request the permission: `ohos.permission.ENTERPRISE_ACCESS_DLP_FILE`.

    2.2 Obtain the file descriptors of the plaintext file and the encrypted file. Set the general DLP file policy [DLPProperty](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#dlpproperty21) and the enterprise-customized policy [CustomProperty](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#customproperty21).

    2.3 Call [dlpPermission.generateDlpFileForEnterprise](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#dlppermissiongeneratedlpfileforenterprise21) to encrypt the plaintext file and generate an enterprise-account DLP file.

    <!-- @[dlp_generateDlpFileForEnterprise](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    async generateDlpFileForEnterprise() {
      let fileName: string = 'test.txt';
      try {
        if (canIUse('SystemCapability.Security.DataLossPrevention')) {
          let property: dlpPermission.DLPProperty = {
            ownerAccount: 'accountInfo.accountName',
            ownerAccountType: dlpPermission.AccountType.ENTERPRISE_ACCOUNT,
            authUserList: [{
              authAccount: 'a012345678',
              authAccountType: 1,
              dlpFileAccess: 2,
              permExpiryTime: 3,
            }],
    
            contactAccount: 'b012345678',
            offlineAccess: true,
            ownerAccountID: 'accountInfo.ownerAccountID',
            everyoneAccessList: [],
            expireTime: 666666666666666,
            actionUponExpiry: dlpPermission.ActionType.NOT_OPEN,
            fileId: 'abc123456789123456789',
          };
    
          let customProperty: dlpPermission.CustomProperty = {
            enterprise: 'testString'
          };
          let context = this.context as common.UIAbilityContext;
          let fileDir = context.getApplicationContext().filesDir;
          let plaintextFd = fileIo.openSync(fileDir + '/' + fileName, fileIo.OpenMode.READ_ONLY).fd;
          let ciphertextFd =
            fileIo.openSync(fileDir + '/' + fileName + '.dlp', fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE).fd;
          await dlpPermission.generateDlpFileForEnterprise(plaintextFd, ciphertextFd, property, customProperty);
          this.result = 'generate DLP file for enterprise successful'
          console.info('generate DLP file for enterprise successful');
          hilog.info(HILOG_DLP_DOMAIN, HILOG_TAG, 'generate DLP file for enterprise successful');
        }
      } catch (err) {
        console.error('error message', err.message);
        this.result = 'error message' + err.message;
        hilog.error(HILOG_DLP_DOMAIN, HILOG_TAG, 'error message' + err.message);
      }
    }
    ```

3. Restore the original file.

    3.1 Request the permission: `ohos.permission.ENTERPRISE_ACCESS_DLP_FILE`.

    3.2 Obtain the file descriptors of the plaintext file and the encrypted file.

    3.3 Call [dlpPermission.decryptDlpFile](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#dlppermissiondecryptdlpfile21) to restore the original file.

    <!-- @[dlp_decryptDlpFile](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    async decryptDlpFile() {
      let fileName = 'test.pptx.dlp';
    
      try {
        if (canIUse('SystemCapability.Security.DataLossPrevention')) {
          let context = this.context as common.UIAbilityContext;
          let fileDir = context.getApplicationContext().filesDir;
          let oriFileName: string = fileName.split('.dlp')[0];
          let plaintextFd =
            fileIo.openSync(fileDir + '/' + oriFileName, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE).fd;
          let ciphertextFd = fileIo.openSync(fileDir + '/' + fileName, fileIo.OpenMode.READ_ONLY).fd;
          await dlpPermission.decryptDlpFile(ciphertextFd, plaintextFd);
        }
        this.result = 'decrypt DLP file for enterprise successful'
        console.info('decrypt DLP file for enterprise successful');
        hilog.info(HILOG_DLP_DOMAIN, HILOG_TAG, 'decrypt DLP file for enterprise successful');
      } catch (err) {
        console.error('error message', err.message);
        this.result = 'error message' + err.message;
        hilog.error(HILOG_DLP_DOMAIN, HILOG_TAG, 'error message' + err.message);
      }
    }
    ```

