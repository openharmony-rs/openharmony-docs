# Querying DLP File Permission Policies
<!--Kit: Data Protection Kit-->
<!--Subsystem: Security-->
<!--Owner: @winnieHuYu-->
<!--Designer: @QRF-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=b9df51d7071146a150b14ebb45c78377aa8c5fa6 translatedAt=2026-11-20T09:39:59.412Z pushedAt=2026-11-23T08:05:10.918Z nl=1 -->

## When to Use

Data Protection Kit provides applications with the capability to obtain DLP file permission policy information. An application can query the specific policy of a DLP file, including the authorized user list, granted permissions, whether offline opening is allowed, and enterprise-defined policies.

<!--RP1--><!--RP1End-->

## Development Procedure

1. Import the module. 

    <!-- @[dlp_include_dlpPermission](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    import { dlpPermission } from '@kit.DataProtectionKit';
    ```

2. Obtain the permission policy information of the DLP file.

    2.1 Request the permission: ohos.permission.ENTERPRISE_ACCESS_DLP_FILE.

    2.2 Set the file identifier `ciphertextFd` of the DLP file whose policy is to be queried.

    2.3 Call [dlpPermission.queryDlpPolicy](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#dlppermissionquerydlppolicy21) to obtain the DLP plaintext policy.

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
          hilog.info(HILOG_DLP_DOMAIN, HILOG_TAG, 'queryDlpPolicy result: ' + this.result);
        } catch (err) {
          console.error('error message', err.message);
          this.result = 'error message' + err.message;
          hilog.error(HILOG_DLP_DOMAIN, HILOG_TAG, 'error message' + err.message);
        }
      }
    }
    ```
