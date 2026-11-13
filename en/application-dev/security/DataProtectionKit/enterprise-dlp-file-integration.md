# Enterprise DLP File Adaptation
<!--Kit: Data Protection Kit-->
<!--Subsystem: Security-->
<!--Owner: @winnieHuYu-->
<!--Designer: @QRF-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=57bfdae40c212841223c0901c52730bcefb3354e translatedAt=2026-10-31T07:12:03.545Z pushedAt=2026-11-02T07:16:40.576Z nl=1 -->

## When to Use

Data Protection Kit provides applications with the capability to query or close a specific type of DLP files based on file tags. An application can set custom file tags when generating or opening files. When the device state changes, if the application determines that the device is currently in a risky scenario, it can use the custom file tags to query whether any DLP files are currently open, and close these files to prevent sensitive data from being leaked in the risky scenario.

In addition, Data Protection Kit provides applications with the capability to register a communication plugin with the SA (System Ability) side. After the application registers the communication plugin, the system SA can initiate communication with the application through the plugin. Capabilities related to the generation and restoration of DLP files all depend on the enterprise registering this communication plugin in advance, through which the system SA can obtain required information from the application in real time.

## Development Procedure

1. Import the module.
    <!-- @[dlp_include_dlpPermission](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    import { dlpPermission } from '@kit.DataProtectionKit';
    ```

2. Enter the specified file tag to query the DLP files that have been opened and carry this tag.

    2.1 Request the permission: ohos.permission.ENTERPRISE_ACCESS_DLP_FILE.

    2.2 Set the query options for enterprise DLP files in [DlpFileQueryOptions](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#dlpfilequeryoptions). Pass this parameter when you need to filter and query specific enterprise DLP files by classification tag. You can omit this parameter when you need to query all enterprise DLP files.

    2.3 Call [dlpPermission.queryOpenedEnterpriseDlpFiles](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#dlppermissionqueryopenedenterprisedlpfiles) to query the URI list of the opened enterprise DLP files that meet the specified options.

    <!-- @[dlp_queryOpenedEnterpriseDlpFiles](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    queryOpenedEnterpriseDlpFiles() {
      if (canIUse('SystemCapability.Security.DataLossPrevention')) {
        let options: dlpPermission.DlpFileQueryOptions = {
          classificationLabel: 'label1'
        };
        dlpPermission.queryOpenedEnterpriseDlpFiles(options).then((uris: Array<string>) => {
          console.info('try to query opened enterprise dlp files, result: ', JSON.stringify(uris));
          this.result = 'try to query opened enterprise dlp files, result: ' + JSON.stringify(uris);
          hilog.info(HILOG_DLP_DOMAIN, HILOG_TAG, 'try to query opened enterprise dlp files, result: ',
            JSON.stringify(uris));
        }).catch((err: BusinessError) => {
          console.error('error message', err.message);
          this.result = 'error message' + err.message;
          hilog.error(HILOG_DLP_DOMAIN, HILOG_TAG, 'error message' + err.message);
        }).finally(() => {
          console.info('after querying opened enterprise dlp files');
          hilog.info(HILOG_DLP_DOMAIN, HILOG_TAG, 'after querying opened enterprise dlp files');
        });
      }
    }
    ```


3. Enter the specified file tag to close the DLP files that are currently open and carry this tag.

    3.1 Request the permission: ohos.permission.ENTERPRISE_ACCESS_DLP_FILE.

    3.2 Set the query options for enterprise DLP files in [DlpFileQueryOptions](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#dlpfilequeryoptions). Pass this parameter when you need to filter and close specific enterprise DLP files by classification tag. You can omit this parameter when you need to close all enterprise DLP files.

    3.3 Call [dlpPermission.closeOpenedEnterpriseDlpFiles](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#dlppermissioncloseopenedenterprisedlpfiles) to close all currently opened enterprise DLP files that match the specified options.

    <!-- @[dlp_closeOpenedEnterpriseDlpFiles](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    closeOpenedEnterpriseDlpFiles() {
      if (canIUse('SystemCapability.Security.DataLossPrevention')) {
        let options: dlpPermission.DlpFileQueryOptions = {
          classificationLabel: 'label1'
        };
        dlpPermission.closeOpenedEnterpriseDlpFiles(options).then(() => {
          console.info('try to close opened enterprise dlp files');
          this.result = 'try to close opened enterprise dlp files';
          hilog.info(HILOG_DLP_DOMAIN, HILOG_TAG, 'try to close opened enterprise dlp files');
        }).catch((err: BusinessError) => {
          console.error('error message', err.message);
          this.result = 'error message' + err.message;
          hilog.error(HILOG_DLP_DOMAIN, HILOG_TAG, 'error message' + err.message);
        }).finally(() => {
          console.info('after closing opened enterprise dlp files');
          hilog.info(HILOG_DLP_DOMAIN, HILOG_TAG, 'after closing opened enterprise dlp files');
        });
      }
    }
    ```

4. Implement the API for SA calls.

    4.1 Request permission: Starting from API version 26.0.0, request the ohos.permission.ENTERPRISE_ACCESS_DLP_FILE or ohos.permission.ACCESS_DLP_SERVICE permission; for API versions 21 - 24, request the ohos.permission.ENTERPRISE_ACCESS_DLP_FILE permission.

    4.2 [DlpConnPlugin](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#dlpconnplugin21) is used in the registerPlugin API to register callback capabilities with the SA (System Ability).

    4.3 [connectServer](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#connectserver21) is provided for the SA to call. After processing the request to connect to the cloud service, it returns the result to the SA through the callback.

    <!-- @[dlp_DlpConnPlugin](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    export default class DataCapsulePlugin implements dlpPermission.DlpConnPlugin {
      connectServer(requestId: string, requestData: string, callback: Callback<string>): void {
        let callbackJson = JSON.stringify({
          'requestId': requestId,
        });
        callback(callbackJson);
      }
    }
    ```

5. Register the communication plugin.

    5.1 Request permission: Starting from API version 26.0.0, request the ohos.permission.ENTERPRISE_ACCESS_DLP_FILE or ohos.permission.ACCESS_DLP_SERVICE permission; for API versions 21 - 24, request the ohos.permission.ENTERPRISE_ACCESS_DLP_FILE permission.

    5.2 [DlpConnPlugin](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#dlpconnplugin21) is used in the registerPlugin API to register callback capabilities with the SA.

    5.3 [registerPlugin](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#registerplugin21) registers the plugin with the SA, waiting to be called by the SA.

    <!-- @[dlp_registerPlugin](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    registerPlugin() {
      try {
        if (canIUse('SystemCapability.Security.DataLossPrevention')) {
          let pluginId: number = dlpPermission.DlpConnManager.registerPlugin(new DataCapsulePlugin());
          console.info('registerPlugin pluginId:', JSON.stringify(pluginId));
          this.result = 'registerPlugin pluginId:' + JSON.stringify(pluginId);
          hilog.info(HILOG_DLP_DOMAIN, HILOG_TAG, 'registerPlugin pluginId:', JSON.stringify(pluginId));
        }
      } catch (err) {
        console.error('error message', err.message);
        this.result = 'error message' + err.message;
        hilog.error(HILOG_DLP_DOMAIN, HILOG_TAG, 'error message' + err.message);
      }
    }
    ```

6. Obtain DLP file events
 
    Data Protection Kit provides applications with the capability to obtain information about user operations on DLP file events. An application can subscribe to DLP file events in advance, and when a user operates on a DLP file, the system sends the event information to the application through the security audit service.
 
    Currently supported event types include creating, opening, modifying (content), and copying (content) DLP files. The specific development steps are as follows:
 
    6.1 For the specific development steps, see [Single-Client Subscription](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/devicesecurity-audit-subscribe-arkts-suevent).

    6.2 The eventId of DLP file events is 0x00F000006.
