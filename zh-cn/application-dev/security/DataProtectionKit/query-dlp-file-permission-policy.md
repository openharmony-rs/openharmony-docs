# 查询DLP文件权限策略
<!--Kit: Data Protection Kit-->
<!--Subsystem: Security-->
<!--Owner: @winnieHuYu-->
<!--Designer: @QRF-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->

## 场景介绍

Data Protection Kit为应用提供了获取DLP文件权限策略信息的能力，应用可查询某个DLP文件的具体策略，包括授权用户列表、授予权限、是否允许离线打开、企业自定义策略等。

## 开发步骤

1. 导入模块。 

    <!-- @[dlp_include_dlpPermission](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    import { dlpPermission } from '@kit.DataProtectionKit';
    ```

2. 获取 DLP 文件的权限策略信息。

    2.1 申请权限：ohos.permission.ENTERPRISE_ACCESS_DLP_FILE。

    2.2 设置待查询策略的DLP文件的文件标识符ciphertextFd。

    2.3 调用[dlpPermission.queryDlpPolicy](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#dlppermissionquerydlppolicy21)获取DLP明文策略。

    <!-- @[dlp_queryDlpPolicy](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    async queryDlpPolicy() {
      if (canIUse('SystemCapability.Security.DataLossPrevention')) {
        let fileName = 'test.pptx.dlp';
        try {
          let context = this.context as common.UIAbilityContext;
          let fileDir = context.getApplicationContext().filesDir;
          let ciphertextFd = fileIo.openSync(fileDir + '/' + fileName, fileIo.OpenMode.READ_ONLY).fd;
          this.result = await dlpPermission.queryDlpPolicy(ciphertextFd);
          console.info('res', this.result);
          hilog.info(HILOG_DLP_DOMAIN, HILOG_TAG, 'getDLPSuffix result: ' + this.result);
        } catch (err) {
          console.error('error message', err.message);
          this.result = 'error message' + err.message;
          hilog.error(HILOG_DLP_DOMAIN, HILOG_TAG, 'error message' + err.message);
        }
      }
    }
    ```
