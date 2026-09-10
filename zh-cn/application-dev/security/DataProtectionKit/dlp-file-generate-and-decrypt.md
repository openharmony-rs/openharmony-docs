# 生成、还原DLP加密文件
<!--Kit: Data Protection Kit-->
<!--Subsystem: Security-->
<!--Owner: @winnieHuYu-->
<!--Designer: @QRF-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->

## 场景介绍

Data Protection Kit为应用提供了将明文文件生成DLP文件的能力和将DLP文件解密还原成原始明文文件的能力。应用无需自定义加密文件格式，只需使用OpenHarmony提供的DLP文件生成和解密能力来对敏感文件实现加密保护。

## 开发步骤

1. 接口所需模块导入。 
    <!-- @[dlp_include_dlpPermission](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    import { dlpPermission } from '@kit.DataProtectionKit';
    ```

2. 加密文件。

    2.1 申请权限：ohos.permission.ENTERPRISE_ACCESS_DLP_FILE。

    2.2 需要获取明文文件和加密文件的文件描述符。设置DLP文件通用策略[DLPProperty](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#dlpproperty21)和企业定制策略[CustomProperty](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#customproperty21)。

    2.3 调用[dlpPermission.generateDlpFileForEnterprise](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#dlppermissiongeneratedlpfileforenterprise21)将明文文件加密生成企业账号DLP文件。

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

3. 恢复原始文件。

    3.1 申请权限：ohos.permission.ENTERPRISE_ACCESS_DLP_FILE。

    3.2 需要获取明文文件和加密文件的文件描述符。

    3.3 调用[dlpPermission.decryptDlpFile](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#dlppermissiondecryptdlpfile21)将明文文件加密生成企业账号DLP文件。

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

