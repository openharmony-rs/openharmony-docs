# 证书管理对话框开发指导

<!--Kit: Device Certificate Kit-->
<!--Subsystem: Security-->
<!--Owner: @chaceli-->
<!--Designer: @chande-->
<!--Tester: @zhangzhi1995-->
<!--Adviser: @zengyawen-->

> **说明**
>
> 本开发指导需使用API version 13及以上版本SDK。

证书管理对话框，可用于拉起证书管理页面并管理证书，如安装、存储、使用、销毁证书。

## 接口说明

详细接口说明可参考[API参考](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md)。

以上场景涉及的常用接口如下表所示。

| 实例名          | 接口名                                                       | 描述                                         |
| --------------- | ------------------------------------------------------------ | -------------------------------------------- |
| certificateManagerDialog        | openCertificateManagerDialog(context: common.Context, pageType: CertificateDialogPageType): Promise\<void> | 拉起证书管理对话框，显示相应的页面，使用Promise方式异步返回结果。 |
| certificateManagerDialog | openInstallCertificateDialog(context: common.Context, certType: CertificateType, certScope: CertificateScope, cert: Uint8Array): Promise\<string><sup>14+</sup> | 调用安装证书对话框接口进行证书安装，使用Promise方式异步返回安装证书的唯一标识符。<br/>仅2in1设备支持。 |
| certificateManagerDialog | openUninstallCertificateDialog(context: common.Context, certType: CertificateType, certUri: string): Promise\<void><sup>18+</sup> | 调用删除证书对话框接口删除指定的证书，使用Promise方式异步返回结果。<br/>仅2in1设备支持。 |
| certificateManagerDialog | openCertificateDetailDialog(context: common.Context, cert: Uint8Array, property: CertificateDialogProperty): Promise\<void><sup>18+</sup> | 调用查看证书详情的对话框接口，展示证书的详情。使用Promise方式异步返回结果。<br/>仅2in1设备支持。 |

## 开发步骤

1. 权限申请和声明。

   需要申请的权限：ohos.permission.ACCESS_CERT_MANAGER

   申请流程请参考：[申请应用权限](../AccessToken/determine-application-mode.md)

   声明权限请参考：[声明权限](../AccessToken/declare-permissions.md)

2. 导入相关模块。

   ```ts
   import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   import { common } from '@kit.AbilityKit';
   import { UIContext } from '@kit.ArkUI';
   ```

3. 拉起证书管理界面。

   <!-- @[certificate_management_dialog_box_development_guide](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DeviceCertificateKit/CertificateManagement/entry/src/main/ets/samples/CertManagerDialogSample.ets) -->
   
   ``` TypeScript
   import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   import { common } from '@kit.AbilityKit';
   
   async function certificateManagerDialogSample() {
     /* context为应用的上下文信息，由调用方自行获取，此处仅为示例 */
     let context: common.Context = new UIContext().getHostContext() as common.Context;
     /* pageType为页面类型，此处赋值PAGE_MAIN，即拉起证书管理主界面 */
     let pageType: certificateManagerDialog.CertificateDialogPageType =
       certificateManagerDialog.CertificateDialogPageType.PAGE_MAIN;
     try {
       certificateManagerDialog.openCertificateManagerDialog(context, pageType).then(() => {
         console.info('Succeeded in opening certificate manager dialog.');
       }).catch((err: BusinessError) => {
         console.error(`Failed to open certificate manager dialog. Code: ${err.code}, message: ${err.message}`);
       })
     } catch (error) {
       console.error(`Failed to open certificate manager dialog. Code: ${error.code}, message: ${error.message}`);
     }
   }
   ```


4. 调用安装证书对话框接口进行证书安装、调用删除证书对话框接口进行证书删除、调用查看证书详情的对话框接口、展示证书的详情。以上场景仅2in1设备支持。

   <!-- @[certificate_management_ca_dialog_development_guide](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DeviceCertificateKit/CertificateManagement/entry/src/main/ets/samples/CertManagerCaDialogSample.ets) -->
   
   ``` TypeScript
   import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   import { common } from '@kit.AbilityKit';
   import { UIContext } from '@kit.ArkUI';
   import { util } from '@kit.ArkTS';
   
   let certType = certificateManagerDialog.CertificateType.CA_CERT;
   let certUri: string = '';
   /* 用户CA证书数据需要业务赋值。 */
   let cert: Uint8Array = new util.TextEncoder().encodeInto(`-----BEGIN CERTIFICATE-----
   MIIDSTCCAjECFFRZKkiBuiZ+zqfjJOg05yeTePM9MA0GCSqGSIb3DQEBCwUAMGEx
   CzAJBgNVBAYTAmNuMQ0wCwYDVQQIDARvaG9zMQswCQYDVQQHDAJjbTEhMB8GA1UE
   CgwYSW50ZXJuZXQgV2lkZ2l0cyBQdHkgTHRkMRMwEQYDVQQDDApUZXN0Um9vdENB
   MB4XDTI1MTAxNTA3MzE0MloXDTI2MTAxNTA3MzE0MlowYTELMAkGA1UEBhMCY24x
   DTALBgNVBAgMBG9ob3MxCzAJBgNVBAcMAmNtMSEwHwYDVQQKDBhJbnRlcm5ldCBX
   aWRnaXRzIFB0eSBMdGQxEzARBgNVBAMMClRlc3RSb290Q0EwggEiMA0GCSqGSIb3
   DQEBAQUAA4IBDwAwggEKAoIBAQC5p4eoQJyTBvn01M8SwEi8dguTIPGmD3a8SGIj
   KXaB6ltv742H5EBjgk+zC8+Gis0ehEqwk3pVnnmByeYvrERxsUqDt69/FndlfTxI
   C2/2MxWVk97g/6TpJ5Lt2mTrH+rSOgUDyU27aPn12ZnDF1mLsT+U+CBmfj4+J4tW
   yzdFNj7kcKMQQok+L1dtFlDNMNpMA1UqADzoC3XgFl49CpDtoFId9DVsgUPkPfX1
   89cCunomgJe1b17FzxfNu2yhbl5cnUEjeHGbmBgBIB7uG8tjGstnDPx7fl3Xrj+Q
   fRrwCpVKD9RxoyUBFbHttixxY5bHFUdvHRB251sxD+JfxxxLAgMBAAEwDQYJKoZI
   hvcNAQELBQADggEBAEGbNqcMU7C/lrIytI/OTtzYbkWDsfnRSPxlCUoZ2Xh3S83A
   SNQ9Ze5tDwWdW9Hlde9May6hzvuQSYeMLLnyM8WGResXCs7UbnSQe7fGfUu+xDGb
   h4tamnRFtZydxCCgDT9lIdHeutlPwOuxlR4HXpeowGeGJX0iFrdo6D0iXAY34hic
   yLQzuBqE/1s3PLA83Fi4EOOOV7P/ahmOLtBFlHbySHV68i9PNeNr9SDykH9/RgI9
   5G8ZTZj8oSmbTGGtfNuVXybMyJMRlz6BkxG++kYcg7STRBqHGX7RrWHiupguNreO
   4sJBdSpWBq172ZEyOvTqC4xX9lLYqwwBQ++TFoo=
   -----END CERTIFICATE-----`);
   
   async function installUserCADialogSample() {
     /* context为应用的上下文信息，由调用方自行获取，此处仅为示例。 */
     let context: common.Context = new UIContext().getHostContext() as common.Context;
     let certScope = certificateManagerDialog.CertificateScope.CURRENT_USER; /* 安装在当前用户下。 */
     try {
       /* 安装证书。 */
       certificateManagerDialog.openInstallCertificateDialog(context, certType, certScope, cert).then((result) => {
         console.info('Succeeded in opening install ca dialog.');
         certUri = result;
       }).catch((err: BusinessError) => {
         console.error(`Failed to open install ca dialog. Code: ${err.code}, message: ${err.message}`);
       })
     } catch (error) {
       console.error(`Failed to open install ca dialog. Code: ${error.code}, message: ${error.message}`);
     }
   }
   
   async function uninstallUserCADialogSample() {
     /* context为应用的上下文信息，由调用方自行获取，此处仅为示例。 */
     let context: common.Context = new UIContext().getHostContext() as common.Context;
     try {
       /* 删除证书。 */
       certificateManagerDialog.openUninstallCertificateDialog(context, certType, certUri).then(() => {
         console.info('Succeeded in opening uninstall ca dialog.');
       }).catch((err: BusinessError) => {
         console.error(`Failed to open uninstall ca dialog. Code: ${err.code}, message: ${err.message}`);
       })
     } catch (error) {
       console.error(`Failed to open uninstall ca dialog. Code: ${error.code}, message: ${error.message}`);
     }
   }
   
   async function certDetailDialogSample() {
     /* context为应用的上下文信息，由调用方自行获取，此处仅为示例。 */
     let context: common.Context = new UIContext().getHostContext() as common.Context;
     try {
       let property: certificateManagerDialog.CertificateDialogProperty = {
         showInstallButton: false    /* 不显示安装按钮。 */
       };
       /* 显示证书详情。 */
       certificateManagerDialog.openCertificateDetailDialog(context, cert, property).then(() => {
         console.info('Succeeded in opening show ca detail dialog.');
       }).catch((err: BusinessError) => {
         console.error(`Failed to open show ca detail dialog. Code: ${err.code}, message: ${err.message}`);
       })
     } catch (error) {
       console.error(`Failed to open show ca detail dialog. Code: ${error.code}, message: ${error.message}`);
     }
   }
   ```

