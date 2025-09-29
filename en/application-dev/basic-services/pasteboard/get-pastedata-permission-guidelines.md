# Requesting Permissions to Access the Pasteboard
<!--Kit: Basic Services Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @yangxiaodong41-->
<!--Designer: @guo867-->
<!--Tester: @maxiaorong-->
<!--Adviser: @fang-jinxu-->

## Overview

In API version 12 and later, permission control is added to the pasteboard reading API to enhance user privacy protection.

Related APIs:

| Name| Description                                                                                                                                       |
| -------- |----------------------------------------------------------------------------------------------------------------------------------------|
| [getData(callback: AsyncCallback&lt;PasteData&gt;): void](../../reference/apis-basic-services-kit/js-apis-pasteboard.md#getdata9) | Reads a **PasteData** object from the pasteboard. This API uses an asynchronous callback to return the result.|
| [getData(): Promise&lt;PasteData&gt;](../../reference/apis-basic-services-kit/js-apis-pasteboard.md#getdata9-1) | Reads a **PasteData** object from the pasteboard. This API uses a promise to return the result.|
| [getDataSync(): PasteData](../../reference/apis-basic-services-kit/js-apis-pasteboard.md#getdatasync11) | Reads data from the system pasteboard. This API returns the result synchronously.|
| [getUnifiedData(): Promise\<unifiedDataChannel.UnifiedData\>](../../reference/apis-basic-services-kit/js-apis-pasteboard.md#getunifieddata12) | Reads the data of a unified data object from the system pasteboard.|
| [getUnifiedDataSync(): unifiedDataChannel.UnifiedData](../../reference/apis-basic-services-kit/js-apis-pasteboard.md#getunifieddatasync12) | Reads the data of a unified data object from the system pasteboard. This API returns the result synchronously.|
| [OH_UdmfData* OH_Pasteboard_GetData (OH_Pasteboard *pasteboard, int *status)](../../reference/apis-basic-services-kit/capi-oh-pasteboard-h.md#oh_pasteboard_getdata) | Obtains data from the pasteboard.|
| [getDataWithProgress(params: GetDataParams): Promise\<PasteData\>](../../reference/apis-basic-services-kit/js-apis-pasteboard.md#getdatawithprogress15) | Obtains the pasteboard data and paste progress. This API uses a promise to return the result. Folders cannot be copied.|
| [OH_UdmfData* OH_Pasteboard_GetDataWithProgress(OH_Pasteboard* pasteboard, Pasteboard_GetDataParams* params, int* status)](../../reference/apis-basic-services-kit/capi-oh-pasteboard-h.md#oh_pasteboard_getdatawithprogress) | Obtains the pasteboard data and paste progress. Folders cannot be copied.|

Note: Before requesting the pasteboard permission, an application needs to check whether the pasteboard contains the required data. For example, use **hasData** to check whether there is data in the pasteboard, **hasDataType** or **getMimeTypes** to check whether required data types are contained, and **getChangeCount** to check whether the data changes. For details, see [Optimizing Pasteboard Dialog Box Adaptation](#optimizing-pasteboard-dialog-box-adaptation).

## Accessing Pasteboard Content

Applications can access the pasteboard content in either of the following ways:

- Using security components

    Applications that use [security components](../../security/AccessToken/pastebutton.md) to access the pasteboard content do not need to request the permission.

    Applications that use the security components can access the pasteboard content without any adaptation.

- Requesting the ohos.permission.READ_PASTEBOARD permission

    ohos.permission.READ_PASTEBOARD is a restricted user_grant permission. Applications that use custom components can request this permission to access the pasteboard content with user authorization.

    How to request permissions:
    <!--RP1-->
    1. Request high-level permissions through [ACL](../../security/AccessToken/declare-permissions-in-acl.md).
    
    2. [Declare permissions](../../security/AccessToken/declare-permissions.md) in the **module.json5** configuration file.
    
    3. [Request user authorization](../../security/AccessToken/request-user-authorization.md) via a dialog box.
    <!--RP1End-->

## Optimizing Pasteboard Dialog Box Adaptation

Before requesting the pasteboard permission, an application needs to check whether the pasteboard contains the required data to avoid invalid dialog boxes.

- Use [hasData](../../reference/apis-basic-services-kit/js-apis-pasteboard.md#hasdata9) to check whether the pasteboard contains data. If no data is contained, the application does not access the pasteboard.

- Use [hasDataType](../../reference/apis-basic-services-kit/js-apis-pasteboard.md#hasdatatype11) or [getMimeTypes](../../reference/apis-basic-services-kit/js-apis-pasteboard.md#getmimetypes14) to check whether the pasteboard contains the data types supported by the application. If no supported data type is contained, the application does not access the pasteboard.

- Use [getChangeCount](../../reference/apis-basic-services-kit/js-apis-pasteboard.md#getchangecount18) to obtain the number of pasteboard content changes and compare it with the number of changes queried when the pasteboard is read last time. If the numbers are the same, the pasteboard content does not change and the application does not access the pasteboard.

- Use [detectPatterns](../../reference/apis-basic-services-kit/js-apis-pasteboard.md#detectpatterns13) to detect patterns on the local pasteboard. If the application password does not match the pattern, the application does not access the pasteboard. If the application password matches the pattern, it is recommended that the application use [cleardata](../../reference/apis-basic-services-kit/js-apis-pasteboard.md#cleardata9) to clear the password in the pasteboard.
