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

> **NOTE**
>
> Before requesting the pasteboard permission, an application needs to check whether the pasteboard contains the required data. For example, use **hasData** to check whether there is data in the pasteboard, **hasDataType** or **getMimeTypes** to check whether required data types are contained, and **getChangeCount** to check whether the data changes. For details, see [Optimizing Pasteboard Dialog Box Adaptation](#optimizing-pasteboard-dialog-box-adaptation).

## Accessing Pasteboard Content

Applications can access the pasteboard content in either of the following ways:

- Using security components

    Applications that use [security components](../../security/AccessToken/pastebutton.md) to access the pasteboard content do not need to request the permission.

    Applications that use the security components can access the pasteboard content without any adaptation.

- Requesting the ohos.permission.READ_PASTEBOARD permission

    This is a restricted user_grant permission. After an application that uses custom components requests this permission, the application can access the pasteboard content with user authorization.

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

## Sample Code

<!-- @[pasteboard_permission](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/pasteboard/pasteboard_arkts_sample/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { BusinessError, pasteboard } from '@kit.BasicServicesKit';
import { abilityAccessCtrl, common, Permissions } from '@kit.AbilityKit';
import { preferences } from '@kit.ArkData';
import { hilog } from '@kit.PerformanceAnalysisKit';

const permissions: Permissions[] = ['ohos.permission.READ_PASTEBOARD'];
const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
const patterns: pasteboard.Pattern[] = [pasteboard.Pattern.URL, pasteboard.Pattern.EMAIL_ADDRESS];
let dataPreferences: preferences.Preferences | null = null;
// ...
async function isNeedGetPermissionFromUser(): Promise<boolean> {
  try {
    let hasData: boolean = await systemPasteboard.hasData();
    if (!hasData) {
      // Pasteboard does not have data. No permission is required.
      return false;
    }
    // Obtain the number of content changes in the pasteboard.
    let result: number = systemPasteboard.getChangeCount();
    hilog.info(0xFF00, '[Sample_pasteboard]', 'Succeeded in getting the ChangeCount. Result: ${result}');
    // Read the value of changeCount stored last time from Preferences.
    let storedChangeCount: number = dataPreferences ? Number(dataPreferences.getSync('pasteboardChangeCount', 0)) : 0;
    if (result === storedChangeCount) {
      // The pasteboard data does not change. No permission is required.
      return false;
    }
  } catch (err) {
    hilog.error(0xFF00, '[Sample_pasteboard]', 'Failed to get the ChangeCount. Cause: ${err.message}');
    return false;
  };

  // Check whether the pasteboard contains the data type required by the application.
  try {
    // (Optional) Check whether the data type required by the application exists.
    let result: boolean = systemPasteboard.hasDataType(pasteboard.MIMETYPE_TEXT_PLAIN);
    hilog.info(0xFF00, '[Sample_pasteboard]', 'Succeeded in checking the DataType. Result: ${result}');
    if (!result) {
      // The pasteboard does not contain the data type required by the application. No permission is required.
      return false;
    }
    // (Optional) If the copied contents contain passwords or other special contents, use detectPatterns to filter out the unwanted contents.
    let data: pasteboard.Pattern[] = await systemPasteboard.detectPatterns(patterns);
    if (patterns.sort().join('') != data.sort().join('')) {
      hilog.info(0xFF00, '[Sample_pasteboard]', 'Not all needed patterns detected, no need to get data.');
      return false;
    }
  } catch (err) {
    hilog.error(0xFF00, '[Sample_pasteboard]', 'Failed to check the DataType. Cause:' + err.message);
    return false;
  };
  return true;
}

@Entry
@Component
struct Index {
  // ...

  build() {
    Row() {
      Column() {
        // ...
        Button('Paste')
          // ...
          .onClick(() => {
            const context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
            if (!isNeedGetPermissionFromUser()) {
              hilog.info(0xFF00, '[Sample_pasteboard]', 'No neded to bring up the permission pop-up window');
              return;
            }
            let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
            // Determine whether to display a user authorization dialog box based on the return value of requestPermissionsFromUser.
            atManager.requestPermissionsFromUser(context, permissions).then((data) => {
              let grantStatus: number[] = data.authResults;
              for (const status of grantStatus) {
                if (status === 0) {
                  // Use the get operation to read the pasteboard content after user authorization.
                  // ...
                  // Determine whether the password is of the current application and use the cleardata API to clear the password in the pasteboard after obtaining the data.
                  systemPasteboard.clearData().then((data: void) => {
                    hilog.info(0xFF00, '[Sample_pasteboard]', 'Succeeded in clearing the pasteboard.');
                  }).catch((err: BusinessError) => {
                    hilog.error(0xFF00, '[Sample_pasteboard]', 'Failed to clear the pasteboard. Cause: ${err.message}');
                  });
                  // Obtain the value of current ChangeCount.
                  let currentChangeCount: number = systemPasteboard.getChangeCount();
                  hilog.info(0xFF00, '[Sample_pasteboard]', 'Current ChangeCount: ' + currentChangeCount);
                  // Update the value of ChangeCount in Preferences.
                  if (dataPreferences) {
                    dataPreferences.putSync('pasteboardChangeCount', currentChangeCount);
                    dataPreferences.flushSync(); // Flush data to Preferences for persistent storage.
                    hilog.info(0xFF00, '[Sample_pasteboard]', 'ChangeCount has been updated to: ' + currentChangeCount);
                  }
                } else {
                  // If the user denies the permission, display a message indicating that user authorization is required, and direct the user to set the permission in Settings.
                  return;
                }
              }
              // Authorization is successful.
            }).catch((err: BusinessError) => {
              hilog.error(0xFF00, '[Sample_pasteboard]', 'Failed to request permissions from user. ');
            })
          })
        // ...
      }
      // ...
    }
    // ...
  }
}
```
