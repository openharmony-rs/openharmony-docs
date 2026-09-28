# Persisting Temporary Permissions
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @lvzhenjie; @hongjin-li_admin-->
<!--Designer: @chenxi0605; @JerryH1011-->
<!--Tester: @leiyuqian; @zsyztt; @yue-ye2-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=8bb3e2585de6843c7a6b6958a78ae198c6cbfd8c translatedAt=2026-09-16T02:50:38.399Z pushedAt=2026-09-16T06:59:30.854Z -->

## When to Use

An app can obtain temporary authorization through Picker by [selecting a file](select-user-file.md) or [saving a file](save-user-file.md). The temporary authorization is cleared after the app exits or the device restarts. If the app needs to directly access previously accessed files after restarting or after a device restart, persistent authorization is required for the files.

## Persisting a Temporary Permission Granted by Picker

When you select a file or folder through Picker for temporary authorization, the URI obtained has only **temporary read/write permission**. The app can subsequently persist the authorization through the file sharing API ([ohos.fileshare](../reference/apis-core-file-kit/js-apis-fileShare.md)) as needed.

1. When an app only temporarily needs to access data in a public directory, for example, a communication app needs to send a user file or image, the app calls the Picker's [select()](../reference/apis-core-file-kit/js-apis-file-picker.md#select-3) API to select the file or image to send. In this case, the app obtains temporary access permission to the file. After the app restarts or the device restarts, the app must use Picker again to select the file for access.

2. If an app needs long-term access to a file or directory, it can use a Picker to select the file or directory and obtain temporary access, and then call persistPermission ([ohos.fileshare.persistPermission](../reference/apis-core-file-kit/js-apis-fileShare.md#filesharepersistpermission11)) to persist the permission, provided that the grantor allows the permission to be persisted. For example, when a file is selected using a Picker, the Picker grants the permission to the current app, allowing the app to persist the permission. This is useful for scenarios such as a document editing app that needs to reopen a previously edited file directly from the history list without invoking the Picker again for authorization.

    You can use canIUse to check whether the device supports the following system capability: SystemCapability.FileManagement.AppFileService.FolderAuthorization.

    ```ts
    if (!canIUse('SystemCapability.FileManagement.AppFileService.FolderAuthorization')) {
        console.error('this api is not supported on this device');
        return;
    }
    ```

    **Required Permissions**<br>
    ohos.permission.FILE_ACCESS_PERSIST. For details about how to request the permission, see [Workflow for Requesting Permissions](../security/AccessToken/determine-application-mode.md).

    **Example**

    <!-- @[persist_permission_example](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/PersistPermission/entry/src/main/ets/persistpermission/PersistPermission.ets) -->    

    ``` TypeScript
    import { BusinessError } from '@kit.BasicServicesKit';
    import { picker } from '@kit.CoreFileKit';
    import { fileShare } from '@kit.CoreFileKit';

    export async function persistPermissionExample() {
      try {
        // ...
        let documentSelectOptions = new picker.DocumentSelectOptions();
        let documentPicker = new picker.DocumentViewPicker();
        let uris = await documentPicker.select(documentSelectOptions);
        // You can combine multiple permissions. For example, for read and write permissions, use fileShare.OperationMode.READ_MODE | fileShare.OperationMode.WRITE_MODE. 
        // Note: You can perform persistent authorization only on the obtained temporary permission. Otherwise, an error is reported.
        let policyInfo: fileShare.PolicyInfo = {
          uri: uris[0],
          operationMode: fileShare.OperationMode.READ_MODE,
        };
        let policies: fileShare.PolicyInfo[] = [policyInfo];
        fileShare.persistPermission(policies).then(() => {
          console.info('persistPermission successfully');
        }).catch((err: BusinessError<Array<fileShare.PolicyErrorResult>>) => {
          console.error('persistPermission failed with error message: ' + err.message + ', error code: ' + err.code);
          if (err.code == 13900001 && err.data) {
            for (let i = 0; i < err.data.length; i++) {
              console.error('error code : ' + JSON.stringify(err.data[i].code));
              console.error('error uri : ' + JSON.stringify(err.data[i].uri));
              console.error('error reason : ' + JSON.stringify(err.data[i].message));
            }
          }
        });
      } catch (error) {
        let err: BusinessError = error as BusinessError;
        console.error(`persistPermission failed with err, Error code: ${err.code}, message: ${err.message}`);
      }
    }
    ```

    > **NOTE**
    >
    > 1. It is recommended that the app store the persisted authorization file information locally for later activation of the persisted file as needed.
    > 2. The persisted authorization data is stored in the system database. After the app or device restarts, you must activate the persisted authorization before you can use it normally. For details, see [Activating a Persisted Permission](#activating-a-persistent-permission-for-accessing-a-file-or-folder).
    > 3. For the persistent permission API, you can use the **canIUse** API to check whether the capability is available, and you need to request the corresponding permission.
    > 4. When the app is uninstalled, all previous authorization data is cleared. After the app is reinstalled, you need to request authorization again.
    > 5. You can only persist a temporary permission that has already been obtained. Otherwise, an error is reported.

    For details about how to persist a temporary permission using C/C++ APIs, see [OH_FileShare_PersistPermission](native-fileshare-guidelines.md).

3. You can use [ohos.fileshare.revokePermission](../reference/apis-core-file-kit/js-apis-fileShare.md#filesharerevokepermission11) to revoke the persistent permission from a file, and update the data stored in the application to remove the corresponding recent access record.

    **Required Permissions**<br>
    ohos.permission.FILE_ACCESS_PERSIST. For details about how to request the permission, see [Workflow for Requesting Permissions](../security/AccessToken/determine-application-mode.md).

    **Example**

    <!-- @[revoke_permission_example](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/PersistPermission/entry/src/main/ets/persistpermission/PersistPermission.ets) -->    

    ``` TypeScript
    import { BusinessError } from '@kit.BasicServicesKit';
    import { picker } from '@kit.CoreFileKit';
    import { fileShare } from '@kit.CoreFileKit';

    // ...
    export async function revokePermissionExample() {
      try {
        let uri = 'file://docs/storage/Users/username/tmp.txt';
        // You can combine multiple permissions to cancel, for example, read/write permissions can use fileShare.OperationMode.READ_MODE | fileShare.OperationMode.WRITE_MODE.
        // Note: You can only cancel persistent authorization for persistent permissions that have been obtained; otherwise, an error is reported.
        let policyInfo: fileShare.PolicyInfo = {
          uri: uri,
          operationMode: fileShare.OperationMode.READ_MODE,
        };
        let policies: fileShare.PolicyInfo[] = [policyInfo];
        fileShare.revokePermission(policies).then(() => {
          console.info('revokePermission successfully');
        }).catch((err: BusinessError<Array<fileShare.PolicyErrorResult>>) => {
          console.error('revokePermission failed with error message: ' + err.message + ', error code: ' + err.code);
          if (err.code == 13900001 && err.data) {
            for (let i = 0; i < err.data.length; i++) {
              console.error('error code : ' + JSON.stringify(err.data[i].code));
              console.error('error uri : ' + JSON.stringify(err.data[i].uri));
              console.error('error reason : ' + JSON.stringify(err.data[i].message));
            }
          }
        });
      } catch (error) {
        let err: BusinessError = error as BusinessError;
        console.error(`revokePermission failed with err, Error code: ${err.code}, message: ${err.message}`);
      }
    }
    ```

    > **NOTE**
    >
    > 1. The URI in the example comes from the persistent data stored by the app.
    > 2. You can only revoke a persistent permission that has already been obtained. It is recommended that you revoke the corresponding persistent permission based on your usage requirements.
    > 3. For the persistent permission API, you can use the **canIUse** API to check whether the capability is available, and you need to request the corresponding permission.

    **Note:** For details about how to revoke a persistent permission using C/C++ APIs, see [OH_FileShare_RevokePermission](native-fileshare-guidelines.md).

## Activating a Persistent Permission for Accessing a File or Folder

Each time an application is started, its persistent permissions have not been loaded to the memory. To make a persistent permission still valid after the application is restarted, use [ohos.fileshare.activatePermission](../reference/apis-core-file-kit/js-apis-fileShare.md#fileshareactivatepermission11) to activate the permission.

**Required Permissions**<br>
ohos.permission.FILE_ACCESS_PERSIST. For details about how to request the permission, see [Workflow for Requesting Permissions](../security/AccessToken/determine-application-mode.md).

**Example**

<!-- @[activate_permission_example](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/PersistPermission/entry/src/main/ets/persistpermission/PersistPermission.ets) -->    

``` TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { picker } from '@kit.CoreFileKit';
import { fileShare } from '@kit.CoreFileKit';

// ...
export async function activatePermissionExample() {
  try {
    let uri = 'file://docs/storage/Users/username/tmp.txt';
    // Multiple permissions can be activated in combination. For example, for read and write permissions, use fileShare.OperationMode.READ_MODE | fileShare.OperationMode.WRITE_MODE.
    // Note: Activation of persistent authorization can only be performed on permissions that have already been persisted. Otherwise, an error will be reported.
    let policyInfo: fileShare.PolicyInfo = {
      uri: uri,
      operationMode: fileShare.OperationMode.READ_MODE,
    };
    let policies: fileShare.PolicyInfo[] = [policyInfo];
    fileShare.activatePermission(policies).then(() => {
      console.info('activatePermission successfully');
    }).catch((err: BusinessError<Array<fileShare.PolicyErrorResult>>) => {
      console.error('activatePermission failed with error message: ' + err.message + ', error code: ' + err.code);
      if (err.code == 13900001 && err.data) {
        for (let i = 0; i < err.data.length; i++) {
          console.error('error code : ' + JSON.stringify(err.data[i].code));
          console.error('error uri : ' + JSON.stringify(err.data[i].uri));
          console.error('error reason : ' + JSON.stringify(err.data[i].message));
          if (err.data[i].code == fileShare.PolicyErrorCode.PERMISSION_NOT_PERSISTED) {
          // You can choose to persist first and then activate.
          }
        }
      }
    });
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`activatePermission failed with err, Error code: ${err.code}, message: ${err.message}`);
  }
}
```

> **NOTE**
>
> 1. The URI in the example comes from the persistent data stored by the app.
> 2. It is recommended that you activate the corresponding persistent permissions based on your usage requirements. Do not blindly activate all of them.
> 3. If activation fails and indicates that the permission is not persisted, you can persist it by following the example.
> 4. For the persistent permission API, you can use the **canIUse** API to check whether the capability is available, and you need to request the corresponding permission.

For details about how to activate a persistent permission using C/C++ APIs, see [OH_FileShare_ActivatePermission](native-fileshare-guidelines.md).

## Persistent Permission Retention Configuration

Starting from API version 24, the system supports the persistent permission retention capability. When the app is uninstalled, the persistent permissions are retained based on the **ohos.fileshare.supportPreservePersistentPermission** tag. When the app is reinstalled, the previously retained persistent permissions are restored.

### Configuration Method

You can configure the ohos.fileshare.supportPreservePersistentPermission tag in the metadata under the module tag in the app module-level configuration file [src/main/module.json5](../quick-start/module-configuration-file.md) to enable the persistent permission retention capability.

**metadata Tag Configuration Example**

``` JSON5
{
  "module": {
    // ...
    "metadata": [
      {
        "name": "ohos.fileshare.supportPreservePersistentPermission"
      }
    ],
    // ...
  }
}
```
**Description of the ohos.fileshare.supportPreservePersistentPermission Tag**

| Name | Description | Type | Mandatory |
| -------- | -------- | -------- | -------- |
| name | Identifies the metadata name. The value is fixed as **ohos.fileshare.supportPreservePersistentPermission**. | String | Yes |
