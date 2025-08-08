# 申请访问剪贴板权限

## 概述

API version 12及之后，系统为提升用户隐私安全保护能力，剪贴板读取接口增加权限管控。

涉及接口如下：

| 名称 | 说明                                                                                                                                        |
| -------- |----------------------------------------------------------------------------------------------------------------------------------------|
| getData(callback: AsyncCallback&lt;PasteData&gt;): void | 读取系统剪贴板内容，使用callback异步回调。 |
| getData(): Promise&lt;PasteData&gt; | 读取系统剪贴板内容，使用Promise异步回调。 |
| getDataSync(): PasteData | 读取系统剪贴板内容, 此接口为同步接口。 |
| getUnifiedData(): Promise\<unifiedDataChannel.UnifiedData\> | 从系统剪贴板中读取统一数据对象的数据。 |
| getUnifiedDataSync(): unifiedDataChannel.UnifiedData | 从系统剪贴板中读取统一数据对象的数据，此接口为同步接口。 |
| OH_UdmfData * OH_Pasteboard_GetData (OH_Pasteboard *pasteboard, int *status) | 获取剪贴板中的数据。 |
| getDataWithProgress(params: GetDataParams): Promise\<PasteData\> | 获取剪贴板的内容和进度，使用Promise异步回调，不支持对文件夹的拷贝。 |
| OH_UdmfData* OH_Pasteboard_GetDataWithProgress(OH_Pasteboard* pasteboard, Pasteboard_GetDataParams* params, int* status) | 获取剪贴板的数据以及粘贴进度，不支持对文件夹的拷贝。 |

## 访问剪贴板内容

剪贴板为应用提供如下两种访问内容的方式。

- 使用安全控件

    使用[安全控件](../../security/AccessToken/pastebutton.md)访问剪贴板内容的应用，可以无需申请权限。

    已经使用了安全控件的应用无需做任何适配就可以访问剪贴板内容。

- 申请ohos.permission.READ_PASTEBOARD权限

    ohos.permission.READ_PASTEBOARD是受限的user_grant（用户授权）权限，使用自定义控件的应用可以通过申请ohos.permission.READ_PASTEBOARD权限，在用户授权的场景下访问剪贴板内容。

    权限申请步骤：
    <!--RP1-->
    1.通过[ACL方式](../../security/AccessToken/declare-permissions-in-acl.md)，申请高级别权限。
    
    2.在module.json5配置文件中[声明权限](../../security/AccessToken/declare-permissions.md)。
    
    3.通过弹窗[向用户申请权限](../../security/AccessToken/request-user-authorization.md)。
    <!--RP1End-->

## 剪贴板弹窗适配优化指南

应用申请剪贴板权限需要提前判断剪贴板内容是否包含所需数据，避免频繁弹窗。

- 使用[hasData](../../reference/apis-basic-services-kit/js-apis-pasteboard.md/#hasdata9)判断是否有数据，无数据则不访问剪贴板

- 使用[hasDataType](../../reference/apis-basic-services-kit/js-apis-pasteboard.md/#hasdatatype11)/[getMimeTypes](../../reference/apis-basic-services-kit/js-apis-pasteboard.md/#getmimetypes14)判断是否包含应用自身支持的数据类型，如果没有则不访问剪贴板

- 使用[getChangeCount](../../reference/apis-basic-services-kit/js-apis-pasteboard.md/#getchangecount18)记录每次访问剪贴板，下次访问前比较上次记录和本次查询的记录是否一致，一致则不访问剪贴板

- 使用[detectPatterns](../../reference/apis-basic-services-kit/js-apis-pasteboard.md/#detectpatterns13)判断是否为口令场景，如果不是则不访问剪贴板
