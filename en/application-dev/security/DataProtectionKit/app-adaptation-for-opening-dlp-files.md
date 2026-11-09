# Adapting an Application to Open DLP Files (ArkTS)
<!--Kit: Data Protection Kit-->
<!--Subsystem: Security-->
<!--Owner: @winnieHuYu-->
<!--Designer: @QRF-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=80e62758ad85d40a8c9e90c904f456b1974d772a translatedAt=2026-10-31T07:05:36.018Z pushedAt=2026-11-02T07:22:22.022Z nl=1 -->

## How to Develop

The following figure shows the important modules involved in DLP files and their interactions. Through the DLP permission management application module, a file owner or file authorizer calls the corresponding APIs to complete operations such as generating and opening DLP files.

![](figures/dlp-intro.png)

### DLP File Generation and Sending

There are two main ways for users to share files with encryption:

- Method 1 (system sharing): Starting from a file, the user directly performs file selection and shares the file to an application with encryption.

- Method 2 (third-party application sharing): Starting from an application, the user performs file selection in-app through the file picker ([@ohos.file.picker (Picker)](../../reference/apis-core-file-kit/js-apis-file-picker.md)) and enables encrypted sharing.

**System sharing:**

The user directly performs file selection and shares the file to an application with encryption. The user's operation process on the device is as follows:

1. In system applications such as Files and Gallery, select the file to be shared with encryption.

2. Tap Share, select **Encrypted sharing** in the bottom function area, enter the encrypted sharing authorization screen, and add the HUAWEI ID of the access party to specify the users who can view the file.

3. Use **System sharing** to send the encrypted file to a third-party application, for example, share it to a chat application and then send it to others.

To support the user in completing the preceding process, the application must meet the following requirements:

- Support sharing and sending encrypted files with the `.dlp` extension to the application through system sharing, without filtering out `.dlp` files.

- Ensure that the DLP file content is not corrupted and that the `.dlp` file extension remains unchanged.

**Third-party application sharing:**

In-app, select a file through the file Picker and configure encrypted sharing. The user operation flow on the device is as follows:

1. In-app, select a file through the file Picker.

2. Tap the **Encrypted Sharing** button at the bottom of the file Picker to enter the encrypted sharing authorization screen, and add the Huawei account of the access party to specify the users who can view the file.

3. After adding, share the encrypted file with others directly within the third-party application.

To support users in completing the preceding flow, the application must meet the following requirements:

- Configure the `DocumentSelectOptions` parameter to display the **Encrypted Sharing** button at the bottom of the file Picker.

- Obtain the file URI through `DocumentViewPicker`.

- After the application obtains the file URI, it can send the DLP file.

### Viewing Encrypted Files

There are two ways for users to view encrypted files:

- Method 1: Preview the DLP file in-app.

- Method 2: Save the DLP file in the application to the local system file management for viewing.

**Preview the DLP file in-app:**

When the user taps the DLP file to view in the application, the application directly launches the file preview to view the file.

To support users in completing the preceding steps, the application must be adapted as follows:

- When opening a DLP file, obtain the URI of the DLP file to be opened first.

- Construct the `want` parameter.

- Pass the `want` parameter through `startAbility` to open the file using the system unified open capability.

**Save the DLP file to local file management for viewing:**

The user operation flow on the device is as follows:

1. Select a DLP file in-app.

2. Save the file to local system file management.

3. Tap the DLP file in system file management to preview it through the system file preview.

To support the user in completing the preceding steps, the application must be adapted as follows:

- The application supports downloading or saving encrypted files to system file management.

- Do not change the .dlp file extension when downloading or saving encrypted files.

## Development Procedure

This document provides API sample code. For details about how to create a project, see [Creating a Project](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-project).

1. Import the [dlpPermission](../../reference/apis-data-protection-kit/js-apis-dlppermission.md) module.

    <!-- @[dlp_include_dlpPermission](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    import { dlpPermission } from '@kit.DataProtectionKit';
    ```

2. Support opening the selected DLP file in-app.

    Prerequisites for using This API: The DLP credential server has been connected.

    The application can support selecting a DLP file from the recently opened list or the file picker and opening it. Adapt the application as follows:

     2.1 Set the [Want](../../reference/apis-ability-kit/js-apis-inner-ability-want.md) parameters, specify `action` as `"ohos.want.action.viewData"`, `uri` as the URI of the DLP file to open, and set the `name` value of `fileName` in `parameters` to the file name of the DLP file.

    2.2 Obtain the `context` of [UIAbilityContext](../../reference/apis-ability-kit/js-apis-app-ability-common.md#uiabilitycontext).

    2.3 Call the [startAbility](../../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startability) method of `context` and pass the `want` parameter to open the DLP file.

    <!-- @[dlp_prepareForOpenDlpFile](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    openDlpFile(dlpUri: string, fileName: string, fd: number) {
      let want: Want = {
        'action': 'ohos.want.action.viewData',
        'uri': dlpUri,
        'parameters': {
          'fileName': {
            'name': fileName
          },
          'keyFd': {
            'type': 'FD',
            'value': fd
          }
        }
      }
    
      let context = new UIContext().getHostContext() as common.UIAbilityContext; // Obtain the current UIAbilityContext.
    
      try {
        console.info('openDLPFile:' + JSON.stringify(want));
        console.info('openDLPFile: delegator:' + JSON.stringify(context));
        hilog.info(HILOG_DLP_DOMAIN, HILOG_TAG, 'openDLPFile:' + JSON.stringify(want));
        hilog.info(HILOG_DLP_DOMAIN, HILOG_TAG, 'openDLPFile: delegator:' + JSON.stringify(context));
        context.startAbility(want);
      } catch (err) {
        console.error('openDLPFile startAbility failed' + (err as BusinessError).code);
        hilog.error(HILOG_DLP_DOMAIN, HILOG_TAG, 'openDLPFile startAbility failed' + (err as BusinessError).code);
        this.result = 'openDLPFile startAbility failed' + (err as BusinessError).code;
        return;
      }
    }
    
    prepareForOpenDlpFile() {
      let file = this.openFile(this.uri);
      if (!file) {
        return;
      }
      this.openDlpFile(this.uri, this.fileName, file.fd);
    
    }
    ```

    Add **ohos.want.action.viewData** to the **module.json5** file.
   
    <!-- @[dlp_configurationModule](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/module.json5) -->
    
    ``` JSON5
    "skills": [
      {
        "entities": [
          "entity.system.home"
        ],
        "actions": [
          "action.system.home",
          "ohos.want.action.viewData"
        ]
      }
    ]
    ```
    
    2.4 Use the file Picker in-app for encrypted sharing of files.
    <!-- @[dlp_callFilePicker](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    async callFilePicker(): Promise<void> {
      try {
        let context = this.getUIContext()?.getHostContext() as common.UIAbilityContext;
        let documentSelectOptions = new picker.DocumentSelectOptions();
        documentSelectOptions.isEncryptionSupported = true; // Display the encrypted sharing button.
        let documentPicker = new picker.DocumentViewPicker(context);
        const documentSelectResult: string[] = await documentPicker.select(documentSelectOptions); // Obtain the file URI.
      } catch (err) {
        console.error('CallFilePickerSelectFile failed');
      }
    }
    ```
  
3. Support permission settings for DLP files in-app.

    Prerequisites for using this API: The DLP credential server has been connected.
   
    You can integrate a permission setting button in-app. After a normal file is opened, tap the permission setting button to launch the modal permission setting page of the DLP management application and generate a DLP file. You can also view the operation permissions of the currently open DLP file in the DLP sandbox clone.

    The cloud integration module of this feature currently needs to be built by you, and this feature requires a domain account environment to be configured.

    3.1 Permission settings in a normal application.

    3.1.1 First, there must be a file that the DLP permission application has read and write access to (for example, under the document directory of File Manager).

    3.1.2 Open the DLP permission management application in borderless mode. This method can be called only in the UIAbility context. Call [startDLPManagerForResult](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#dlppermissionstartdlpmanagerforresult11) to launch the permission settings page of the DLP management application, enter the relevant authorized account information, tap Save, select the save path of the DLP file in the launched file picker, and save the DLP file.

    <!-- @[dlp_generateDlpFiles](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    generateDlpFiles() {
      try {
        let fileUri: string = this.uri;
        let fileName: string = this.fileName;
        let context = new UIContext().getHostContext() as common.UIAbilityContext; // Obtain the current UIAbilityContext.
        let want: Want = {
          'uri': fileUri,
          'parameters': {
            'displayName': fileName
          }
        }; // Request parameters.
        if (canIUse('SystemCapability.Security.DataLossPrevention')) {
          dlpPermission.startDLPManagerForResult(context, want).then((res: dlpPermission.DLPManagerResult) => {
            this.result = 'startDLPManagerForResult result.resultCode:' + res.resultCode;
            console.info('startDLPManagerForResult res.resultCode:' + res.resultCode);
            console.info('startDLPManagerForResult res.want:' + JSON.stringify(res.want));
            hilog.info(HILOG_DLP_DOMAIN, HILOG_TAG, 'startDLPManagerForResult res.resultCode:' + res.resultCode);
            hilog.info(HILOG_DLP_DOMAIN, HILOG_TAG, 'startDLPManagerForResult res.want:' + JSON.stringify(res.want));
          });
        }
      } catch (err) {
        this.result = 'startDLPManagerForResult error:' + (err as BusinessError).code + (err as BusinessError).message;
        console.error('startDLPManagerForResult error:' + (err as BusinessError).code + (err as BusinessError).message);
        hilog.error(HILOG_DLP_DOMAIN, HILOG_TAG,
          'startDLPManagerForResult error:' + (err as BusinessError).code + (err as BusinessError).message);
      }
    }
    ```
    
    3.2. Permission modification, viewing, and removal in the DLP sandbox clone.
    
    Prerequisites for using this API: The DLP credential server has been connected.

    3.2.1 If the current account is the creator of the DLP document, the user has the ability to modify the permissions of this DLP file or remove the permissions of this DLP document to restore it to a normal file. Call [startDLPManagerForResult](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#dlppermissionstartdlpmanagerforresult11) to launch the permission settings page of the DLP management application, and select Change encryption on this page to modify permissions or remove encryption. If the current account has read-only or edit permissions on the DLP document, call the following code to view the permission content of the current user.

    <!-- @[dlp_startDLPManagerForResult](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    startDLPManagerForResult() {
      if (canIUse('SystemCapability.Security.DataLossPrevention')) {
        try {
          let context = new UIContext().getHostContext() as common.UIAbilityContext; // Obtain the current UIAbilityContext.
          let want: Want = {
            'uri': this.uri,
            'parameters': {
              'displayName': this.fileName
            }
          }; // Request parameters.
          dlpPermission.startDLPManagerForResult(context, want).then((res) => {
            this.result = 'startDLPManagerForResult resultCode: ' + res.resultCode;
            console.info('res.resultCode', res.resultCode);
            console.info('res.want', JSON.stringify(res.want));
            hilog.info(HILOG_DLP_DOMAIN, HILOG_TAG, 'res.resultCode' + res.resultCode);
            hilog.info(HILOG_DLP_DOMAIN, HILOG_TAG, 'res.want' + JSON.stringify(res.want));
          }); // Open the DLP permission management application.
        } catch (err) {
          this.result = 'startDLPManagerForResult error' + err.code + err.message;
          console.error('error', err.code, err.message); // Report the error on failure.
          hilog.error(HILOG_DLP_DOMAIN, HILOG_TAG,
            'error' + (err as BusinessError).code + (err as BusinessError).message);
        }
      }
    }
    ```

4. Check whether the application is running in a sandbox.

    Prerequisites for using this API: The DLP file has been opened by the demo application.
   
    In the application, call [isInSandbox](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#dlppermissionisinsandbox) to check whether the current environment is a DLP sandbox clone. If it is, you can gray out or hide the corresponding function buttons based on the permission query result. For example, if only read-only permission is available, the edit and save entry can be grayed out; if only read-only or edit permission is available, the permission modification entry can be grayed out.

    <!-- @[dlp_isInSandBox](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    isInSandbox() {
      if (canIUse('SystemCapability.Security.DataLossPrevention')) {
        dlpPermission.isInSandbox().then((data) => {
          this.result = 'isInSandbox result: ' + JSON.stringify(data);
          console.info('isInSandbox result: ' + JSON.stringify(data));
          hilog.info(HILOG_DLP_DOMAIN, HILOG_TAG, 'isInSandbox result: ' + JSON.stringify(data));
        }).catch((err: BusinessError) => {
          this.result = 'isInSandbox error: ' + JSON.stringify(err);
          console.error('isInSandbox error: ' + JSON.stringify(err));
          hilog.error(HILOG_DLP_DOMAIN, HILOG_TAG, 'isInSandbox error: ' + JSON.stringify(err));
        });
      }
    }
    ```

5. Adapt the UI based on the DLP file permissions.

    In the DLP sandbox clone, you can call [getDLPPermissionInfo](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#dlppermissiongetdlppermissioninfo) to query the user permission and operation permission of the domain account currently signed in to the system for this DLP file. Different user permissions can correspond to different operation permissions on the document. For sandbox restrictions, see [Data Loss Prevention (DLP) Overview](dlp-guidelines.md).
   
     Prerequisites for using this API: The DLP file has been opened by the demo application.

    <!-- @[dlp_getDLPPermissionInfo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    getDLPPermissionInfo() {
      if (canIUse('SystemCapability.Security.DataLossPrevention')) {
        dlpPermission.getDLPPermissionInfo().then((data) => {
          this.result = 'getDLPPermissionInfo result: ' + JSON.stringify(data);
          console.info('getDLPPermissionInfo, result: ' + JSON.stringify(data));
          hilog.info(HILOG_DLP_DOMAIN, HILOG_TAG, 'getDLPPermissionInfo result: ' + JSON.stringify(data));
        }).catch((err: BusinessError) => {
          this.result = 'getDLPPermissionInfo error: ' + JSON.stringify(err);
          console.error('getDLPPermissionInfo: ' + JSON.stringify(err));
          hilog.error(HILOG_DLP_DOMAIN, HILOG_TAG, 'getDLPPermissionInfo error: ' + JSON.stringify(err));
        });
      }
    }
    ```

    The `data` returned by `getDLPPermissionInfo` is of the [DLPPermissionInfo](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#dlppermissioninfo) type, where `dlpFileAccess` indicates the user permission and `flags` indicates the bitwise combination result of operation permissions. You can compare the returned `flags` field with [ActionFlagType](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#actionflagtype) to determine whether the DLP sandbox clone has the corresponding operation permission, which can be used for operations such as graying out UI buttons.

6. Obtain the list of file extension types that currently support the DLP solution.

    [getDLPSupportedFileTypes](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#dlppermissiongetdlpsupportedfiletypes) is used for the application to determine whether the current file can be generated and encrypted.

    <!-- @[dlp_getDLPSupportedFileTypes](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    getDLPSupportedFileTypes() {
      if (canIUse('SystemCapability.Security.DataLossPrevention')) {
        dlpPermission.getDLPSupportedFileTypes((err, result) => {
          console.error('getDLPSupportedFileTypes: ' + JSON.stringify(err));
          console.info('getDLPSupportedFileTypes: ' + JSON.stringify(result));
          hilog.error(HILOG_DLP_DOMAIN, HILOG_TAG, 'getDLPSupportedFileTypes: ' + JSON.stringify(err));
          hilog.info(HILOG_DLP_DOMAIN, HILOG_TAG, 'getDLPSupportedFileTypes: ' + JSON.stringify(result));
          this.result = 'getDLPSupportedFileTypes result: ' + JSON.stringify(result);
        });
      }
    }
    ```

7. Check whether the opened file is a DLP file.

    Prerequisites for using this API: A DLP file is required for the judgment.

    [isDLPFile](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#dlppermissionisdlpfile) is used to determine whether the currently opened file is a DLP file.

    <!-- @[dlp_isCurrentDlpFile](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    isCurrentDlpFile() {
      let file = this.openFile(this.uri);
      if (!file) {
        this.result = 'Please open a file!';
        return;
      }
      if (canIUse('SystemCapability.Security.DataLossPrevention')) {
        dlpPermission.isDLPFile(file.fd).then((res) => {
          if (res.valueOf()) {
            this.result = 'isDLPFile result: ' + JSON.stringify(res);
          } else {
            this.result = getResourceString(this.context, $r('app.string.open_dlp_file_prompt'));
          }
          console.info('res', res);
          hilog.info(HILOG_DLP_DOMAIN, HILOG_TAG, 'res' + res);
        }).catch((err: BusinessError) => {
          this.result = 'isDLPFile error: ' + (err as BusinessError).code + (err as BusinessError).message;
          console.error('error', (err as BusinessError).code, (err as BusinessError).message); // Report the error.
          hilog.error(HILOG_DLP_DOMAIN, HILOG_TAG,
            'error' + (err as BusinessError).code + (err as BusinessError).message);
        }).finally(() => {
          try {
            fileIo.closeSync(file);
          } catch (e) {
            console.error('closeSync failed', e);
          }
        });
      }
    }
    ```

8. The application supports updating the recent open records.

    When the application has a scenario involving recent open records, you can use the APIs provided by the DLP framework to adapt the recent open records. You can adapt in the following scenarios:
    
    8.1 The normal application is not started and cannot perceive the DLP files opened by the DLP sandbox clone.

    Scenario where only the DLP sandbox clone opens DLP files: when the normal application starts, you can call [getDLPFileAccessRecords](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#dlppermissiongetdlpfileaccessrecords) to obtain the DLP files that were historically opened through the DLP sandbox clone of this application.

    Prerequisites for using this API: The DLP file has been opened by the demo application.

    <!-- @[dlp_getDLPFileAccessRecords](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    getDLPFileAccessRecords() {
      if (canIUse('SystemCapability.Security.DataLossPrevention')) {
        dlpPermission.getDLPFileAccessRecords().then((res) => {
          this.result = 'getDLPFileAccessRecords result: ' + JSON.stringify(res);
          console.info('res', JSON.stringify(res));
          hilog.info(HILOG_DLP_DOMAIN, HILOG_TAG, 'res' + JSON.stringify(res));
        }).catch((err: BusinessError) => {
          this.result = 'getDLPFileAccessRecords error: ' + (err as BusinessError).code + (err as BusinessError).message;
          console.error('error: ', (err as BusinessError).code, (err as BusinessError).message); // Report the error.
          hilog.error(HILOG_DLP_DOMAIN, HILOG_TAG,
            'error' + (err as BusinessError).code + (err as BusinessError).message);
        });
      }
    }
    ```

    8.2 The normal application is already started and can perceive the DLP files opened by the DLP sandbox clone.

    Scenario where the DLP sandbox clone opens DLP files: The normal application can subscribe to the event of the DLP sandbox clone of this application opening DLP files by calling [on](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#dlppermissiononopendlpfile), or unsubscribe from it by calling [off](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#dlppermissionoffopendlpfile).

    <!-- @[dlp_subscribe](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    event(info: dlpPermission.AccessedDLPFileInfo) {
      console.info('openDlpFile event');
      hilog.info(HILOG_DLP_DOMAIN, HILOG_TAG, 'openDlpFile event');
    }
    
    unSubscribe() {
      if (canIUse('SystemCapability.Security.DataLossPrevention')) {
        try {
          dlpPermission.off('openDLPFile', this.event); // Unsubscribe.
          this.result = 'unSubscribe result: unsubscribed';
          hilog.info(HILOG_DLP_DOMAIN, HILOG_TAG, 'unSubscribe result: unsubscribed');
        } catch (err) {
          console.error('error', (err as BusinessError).code, (err as BusinessError).message); // Report the error on failure.
          hilog.error(HILOG_DLP_DOMAIN, HILOG_TAG,
            'error' + (err as BusinessError).code + (err as BusinessError).message);
          this.result = 'unSubscribe error: failed to unsubscribe';
        }
      }
    }
    
    subscribe() {
      if (canIUse('SystemCapability.Security.DataLossPrevention')) {
        try {
          dlpPermission.on('openDLPFile', this.event); // Subscribe.
          this.result = 'subscribe result: subscribed';
          hilog.info(HILOG_DLP_DOMAIN, HILOG_TAG, 'subscribe result: subscribed');
        } catch (err) {
          console.error('error', (err as BusinessError).code, (err as BusinessError).message); // Report the error on failure.
          hilog.error(HILOG_DLP_DOMAIN, HILOG_TAG,
            'error' + (err as BusinessError).code + (err as BusinessError).message);
          this.result = 'subscribe error: failed to subscribe';
        }
      }
    }
    ```

9. Retain the sandbox.

    After a DLP sandbox clone is closed, the sandbox is uninstalled. If you do not want the sandbox to be uninstalled when the DLP sandbox clone is closed, call
  
    the API for retaining the sandbox in the sandbox. The sandbox is uninstalled only when the API for canceling sandbox retention is called again and the DLP sandbox clone is closed.

    9.1 Call [setRetentionState](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#dlppermissionsetretentionstate) to retain the sandbox. Pass the URI list of the DLP files opened in this sandbox. This API can be called only in the sandbox.

    <!-- @[dlp_setRetentionState](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    async setRetentionState() {
      let docUris: string[]= ['file://docs/storage/Users/currentUser/Desktop/test.txt.dlp']
      try {
        if (canIUse('SystemCapability.Security.DataLossPrevention')) {
          await dlpPermission.setRetentionState(docUris); // Retain the sandbox.
          console.info('set RetentionState successful');
          this.result = 'set RetentionState successful';
          hilog.info(HILOG_DLP_DOMAIN, HILOG_TAG, 'set RetentionState successful');
        }
      } catch (err) {
        console.error('error message', err.message);
        this.result = 'error message' + err.message;
        hilog.error(HILOG_DLP_DOMAIN, HILOG_TAG, 'error message' + err.message);
      }
    }
    ```

   9.2 Call [cancelRetentionState](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#dlppermissioncancelretentionstate) to cancel sandbox retention.

    <!-- @[dlp_cancelRetentionState](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    async cancelRetentionState() {
      let docUris: string[] = ['file://docs/storage/Users/currentUser/Desktop/test.txt.dlp']
      try {
        if (canIUse('SystemCapability.Security.DataLossPrevention')) {
          await dlpPermission.cancelRetentionState(docUris); // Cancel sandbox retention.
          console.info('cancel RetentionState successful');
          this.result = 'cancel RetentionState successful';
          hilog.info(HILOG_DLP_DOMAIN, HILOG_TAG, 'cancel RetentionState successful');
        }
      } catch (err) {
        console.error('error message', err.message);
        this.result = 'error message' + err.message;
        hilog.error(HILOG_DLP_DOMAIN, HILOG_TAG, 'error message' + err.message);
      }
    }
    ```

    9.3. Call [getRetentionSandboxList](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#dlppermissiongetretentionsandboxlist) to obtain the retained sandbox records.

    Prerequisites for using this API: The DLP file has been opened by the demo application.

    <!-- @[dlp_getRetentionSandboxList](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    getRetentionSandboxList() {
      if (canIUse('SystemCapability.Security.DataLossPrevention')) {
        dlpPermission.getRetentionSandboxList().then((res) => {
          this.result = 'getRetentionSandboxList result: ' + JSON.stringify(res);
          console.info('res', JSON.stringify(res));
          hilog.info(HILOG_DLP_DOMAIN, HILOG_TAG, 'res' + JSON.stringify(res));
        }).catch((err: BusinessError) => {
          this.result = 'getRetentionSandboxList error' + (err as BusinessError).code + (err as BusinessError).message;
          console.error('error', (err as BusinessError).code, (err as BusinessError).message); // Report the error on failure.
          hilog.error(HILOG_DLP_DOMAIN, HILOG_TAG,
            'error' + (err as BusinessError).code + (err as BusinessError).message);
        });
      }
    }
    ```

10. Share data between the application and the DLP sandbox clone.

    A DLP sandbox clone is a clone of a normal application, and all its data is brand new. If some data needs to be shared between the two, you can use the data sharing mechanism between the application and the DLP sandbox clone provided by the DLP framework. A typical use case is sharing the configuration information about whether the privacy statement dialog has been displayed between the original application and the DLP sandbox clone.

    Generally, the following four read/write sequences of configuration information are involved:

    - The original application writes the configuration, and the original application reads the configuration.

    - The original application writes the configuration, and the DLP sandbox clone reads the configuration.

    **Data Sharing Between the Application and the DLP Sandbox Clone**

    - Each call to the API for setting configuration information overwrites the content set by the previous call.

    - For data loss prevention, the DLP sandbox clone must write the configuration before reading the FUSE file content.
    
    **Specific Steps**

    10.1 Set the configuration information.

    Convert the configuration information to be saved into the string type, and call [setSandboxAppConfig](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#dlppermissionsetsandboxappconfig11) to set the configuration information.

    <!-- @[dlp_setSandboxAppConfig](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    setSandboxAppConfig() {
      if (canIUse('SystemCapability.Security.DataLossPrevention')) {
        dlpPermission.setSandboxAppConfig('configInfo').then(() => {
          this.result = 'setSandboxAppConfig result: Sandbox application configuration information set successfully';
          console.info('res', 'Sandbox application configuration information set successfully');
          hilog.info(HILOG_DLP_DOMAIN, HILOG_TAG, 'setSandboxAppConfig result: Sandbox application configuration information set successfully');
        }).catch((err: BusinessError) => {
          this.result = 'setSandboxAppConfig error: ' + (err as BusinessError).code + (err as BusinessError).message;
          console.error('error', (err as BusinessError).code, (err as BusinessError).message); // Report the error on failure.
          hilog.error(HILOG_DLP_DOMAIN, HILOG_TAG,
            'error' + (err as BusinessError).code + (err as BusinessError).message);
        });
      }
    }
    ```

    10.2 Clean up the configuration information.

    Call the [cleanSandboxAppConfig](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#dlppermissioncleansandboxappconfig11) API to clean up all configuration information of the application.

    This API can be called only in a normal application.

    <!-- @[dlp_cleanSandboxAppConfig](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    cleanSandboxAppConfig() {
      if (canIUse('SystemCapability.Security.DataLossPrevention')) {
        dlpPermission.cleanSandboxAppConfig().then(() => {
          this.result = 'cleanSandboxAppConfig result: Sandbox cleaned up successfully';
          console.info('res', 'Sandbox cleaned up successfully');
          hilog.info(HILOG_DLP_DOMAIN, HILOG_TAG, 'cleanSandboxAppConfig result: Sandbox cleaned up successfully');
        }).catch((err: BusinessError) => {
          this.result = 'cleanSandboxAppConfig error: ' + (err as BusinessError).code + (err as BusinessError).message;
          console.error('error', (err as BusinessError).code, (err as BusinessError).message); // Report the error on failure.
          hilog.error(HILOG_DLP_DOMAIN, HILOG_TAG,
            'error' + (err as BusinessError).code + (err as BusinessError).message);
        });
      }
    }
    ```


    10.3. Obtain the configuration information.

    Call [getSandboxAppConfig](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#dlppermissiongetsandboxappconfig11) to query all configuration information of the application.

    Both normal applications and DLP sandbox clones can call this API.

    <!-- @[dlp_getSandboxAppConfig](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    getSandboxAppConfig() {
      if (canIUse('SystemCapability.Security.DataLossPrevention')) {
        dlpPermission.getSandboxAppConfig().then((res) => {
          this.result = 'getSandboxAppConfig result: ' + JSON.stringify(res);
          console.info('res', JSON.stringify(res));
          hilog.info(HILOG_DLP_DOMAIN, HILOG_TAG, 'getSandboxAppConfig result: ' + JSON.stringify(res));
        }).catch((err: BusinessError) => {
          this.result = 'getSandboxAppConfig error: ' + (err as BusinessError).code + (err as BusinessError).message;
          console.error('error', (err as BusinessError).code, (err as BusinessError).message); // Report the error on failure.
          hilog.error(HILOG_DLP_DOMAIN, HILOG_TAG,
            'error' + (err as BusinessError).code + (err as BusinessError).message);
        });
      }
    }
    ```

11. Check whether the current system provides the DLP feature.

    Prerequisites for using this API: The DLP credential server has been connected.

    [isDLPFeatureProvided](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#dlppermissionisdlpfeatureprovided12) is used to query whether the current system provides the DLP feature.
    
    <!-- @[dlp_isDLPFeature](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    isDLPFeature() {
      if (canIUse('SystemCapability.Security.DataLossPrevention')) {
        dlpPermission.isDLPFeatureProvided().then((res) => {
          this.result = 'isDLPFeatureProvided result: ' + JSON.stringify(res.valueOf());
          console.info('res', JSON.stringify(res.valueOf()));
          hilog.info(HILOG_DLP_DOMAIN, HILOG_TAG, 'isDLPFeatureProvided result: ' + JSON.stringify(res.valueOf()));
        }).catch((err: BusinessError) => {
          this.result = 'isDLPFeatureProvided error: ' + (err as BusinessError).code + (err as BusinessError).message;
          console.error('error: ', (err as BusinessError).code, (err as BusinessError).message); // Report the error on failure.
          hilog.error(HILOG_DLP_DOMAIN, HILOG_TAG,
            'error' + (err as BusinessError).code + (err as BusinessError).message);
        });
      }
    }
    ```
    
12. The application supports opening the FUSE file bound to the DLP file.

    Generally, if an application supports opening files of the file type specified in the preset operation and does not impose specific restrictions on the incoming Want, it can open the FUSE file without adaptation.

    12.1 When opening a DLP file, the application is installed as a DLP sandbox clone application (hereinafter referred to as the clone). The clone receives a want request and can parse some of its fields:

    <!-- @[dlp_PrepareOpenFuseFile](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->

    ``` TypeScript
    interface DLPUriObj {
      name: string
    };
    
    interface DLPWriteable {
      name: boolean
    };
    
    interface DLPNameObj {
      dateModified: string,
      displayName: string,
      relativePath: string,
    };
    
    interface DLPLinkNameObj {
      name: string
    };
    
    function getParams(want: Want) {
      // Receive the parameters passed when opening the DLP file.
      let dlpFuseUri: string = want.uri ? want.uri : ''; // URI of the FUSE file, which stores the decrypted plaintext.
      let dlpFuseWriteable: boolean = (want.parameters?.linkFileWriteable as DLPWriteable).name; // Whether the FUSE file is writable.
      let dlpUri: string = (want.parameters?.dlpUri as DLPUriObj).name; // URI of the DLP file.
      let dlpName: string = (want.parameters?.fileAsset as DLPNameObj).displayName; // File name of the DLP file.
      let dlpFuseName: string = (want.parameters?.linkFileName as DLPLinkNameObj).name; // File name of the FUSE file.
    }
    ```

    12.2 The clone can open `want.uri` as an fd to obtain the content of the FUSE file:

    <!-- @[dlp_OpenFuseFile](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    function readFileContent(dlpFuseUri: string): string {
      let content: string = '';
      let file: fileIo.File | undefined = undefined;
      try {
        file = fileIo.openSync(dlpFuseUri, fileIo.OpenMode.READ_ONLY);
      } catch (err) {
        console.error('error message', err.message);
        if (file) {
          try {
            fileIo.closeSync(file);
          } catch (e) {
            console.error('closeSync failed');
          }
        }
        return content;
      }
    
      try {
        let buffer = new ArrayBuffer(4096);
        let bytesRead = fileIo.readSync(file.fd, buffer);
        let actualBuffer = buffer.slice(0, bytesRead);
        content = bufferToString(actualBuffer);
      } catch (err) {
        console.error('error message', err.message);
      } finally {
        if (file) {
          try {
            fileIo.closeSync(file);
          } catch (e) {
            console.error('closeSync failed');
          }
        }
      }
      return content;
    }
    
    function bufferToString(buffer: ArrayBuffer): string {
      let textDecoder = util.TextDecoder.create('utf-8', {
        ignoreBOM: true
      });
      return textDecoder.decodeToString(new Uint8Array(buffer), {
        stream: true
      });
    }
    ```
 
    12.3 If the clone has read/write permission on the FUSE file, it can also update the content of the FUSE file:
 
    <!-- @[dlp_WriteFuseFile](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    function writeFileContent(dlpFuseUri: string, content: string): void {
      let file: fileIo.File | undefined = undefined;
    
      try {
        file = fileIo.openSync(dlpFuseUri, fileIo.OpenMode.CREATE | fileIo.OpenMode.READ_WRITE);
        // O_RDWR: read/write mode, O_CREAT: create the file if it does not exist.
        let writeLen: number = fileIo.writeSync(file.fd, content);
    
      } catch (err) {
        console.error('error message', err.message);
      } finally {
        if (file) {
          try {
            fileIo.closeSync(file);
          } catch (e) {
            console.error('closeSync failed');
          }
        }
      }
    }
    ```

13. Obtain the original name of the DLP file.

    [getOriginalFileName](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#dlppermissiongetoriginalfilename) is used to obtain the original name of the DLP file.

    <!-- @[dlp_getOriginalFileName](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    getOriginalFileName() {
      if (canIUse('SystemCapability.Security.DataLossPrevention')) {
        try {
          this.result = dlpPermission.getOriginalFileName('test.txt.dlp');
          console.info('res', JSON.stringify(this.result));
          hilog.info(HILOG_DLP_DOMAIN, HILOG_TAG, 'getOriginalFileName result: ' + JSON.stringify(this.result));
        } catch (err) {
          console.error('error message', err.message);
          this.result = 'error message' + err.message;
          hilog.error(HILOG_DLP_DOMAIN, HILOG_TAG, 'error message' + err.message);
        }
      }
    }
    ```

14. Obtain the suffix of the DLP file.

    [getDLPSuffix](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#dlppermissiongetdlpsuffix) is used to obtain the suffix of the DLP file.

    <!-- @[dlp_getDLPSuffix](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    getDLPSuffix() {
      if (canIUse('SystemCapability.Security.DataLossPrevention')) {
        try {
          this.result = dlpPermission.getDLPSuffix();
          console.info('res', JSON.stringify(this.result));
          hilog.info(HILOG_DLP_DOMAIN, HILOG_TAG, 'getDLPSuffix result: ' + JSON.stringify(this.result));
        } catch (err) {
          console.error('error message', err.message);
          this.result = 'error message' + err.message;
          hilog.error(HILOG_DLP_DOMAIN, HILOG_TAG, 'error message' + err.message);
        }
      }
    }
    ```
## FAQs

### FUSE File Cannot Be Opened

**Symptom**: The application can open normal files but cannot open FUSE files.

**Solution**:
- Check whether specific restrictions are imposed on `want`, which prevents the DLP sandbox clone from obtaining the FUSE file.
- Check whether a read-only FUSE file is opened with read/write permissions.
