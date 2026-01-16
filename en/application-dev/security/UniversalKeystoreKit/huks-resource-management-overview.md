# Resource Management Overview and Specifications

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

It is agreed that **resourceId** is used to uniquely identify a resource in external key management extensions (such as Ukey). Currently, **resourceId** can be returned through [certification query](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenauthorizedialog22). Each certificate chain corresponds to one **resourceId**. After obtaining **resourceId**, the application need to [open the resource](huks-open-close-resource-ndk.md#opening-resources) before performing subsequent key operations. After the operations are complete, the application [closes the resource](huks-open-close-resource-ndk.md#closing-resources).

> **NOTE**
>
> 1. Before operating a key, the resource must be opened. To perform high-permission operations such as private key signing, you must complete the PIN verification. Otherwise, the resource status is abnormal.
> 2. After user operations are complete, the application must close the resource to avoid resource leakage.
