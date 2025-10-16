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

4. 调用安装证书对话框接口进行证书安装、调用删除证书对话框接口进行证书删除、调用查看证书详情的对话框接口、展示证书的详情。以上场景仅2in1设备支持。

<!-- @[certificate_management_ca_dialog_development_guide](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DeviceCertificateKit/CertificateManagement/entry/src/main/ets/samples/CertManagerCaDialogSample.ets) -->
