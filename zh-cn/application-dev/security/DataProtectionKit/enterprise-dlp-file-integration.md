# 企业接入DLP文件适配
<!--Kit: Data Protection Kit-->
<!--Subsystem: Security-->
<!--Owner: @winnieHuYu-->
<!--Designer: @QRF-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->

## 场景介绍

Data Protection Kit为应用提供了根据文件标签查询或关闭某一类DLP文件的能力，应用可在生成/打开文件时设置自定义的文件标签，在设备的状态发生变化时，如果应用判断当前设备处于风险场景，则可以通过自定义的文件标签，查询当前是否存在打开的DLP文件，并可关闭这些文件从而防止敏感数据在风险场景泄露。

除此之外，Data Protection Kit为应用提供向SA（System Ability）侧注册通信插件的能力，应用注册通信插件后，系统SA可通过该插件向应用发起通信。涉及DLP文件的生成、还原等相关能力，均依赖企业预先注册该通信插件，系统SA通过该插件可实时向应用获取需要的信息。

## 开发步骤

1. 导入模块。
    <!-- @[dlp_include_dlpPermission](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    import { dlpPermission } from '@kit.DataProtectionKit';
    ```

2. 输入指定的文件标签，查询当前已打开过的拥有该标签的DLP文件。

    2.1 申请权限：ohos.permission.ENTERPRISE_ACCESS_DLP_FILE。

    2.2 设置企业DLP文件的查询选项[DlpFileQueryOptions](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#dlpfilequeryoptions)。当需要按分类标签筛选查询特定企业DLP文件时传入此参数，当需要查询所有企业DLP文件时可不传此参数。

    2.3 调用[dlpPermission.queryOpenedEnterpriseDlpFiles](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#dlppermissionqueryopenedenterprisedlpfiles)查询已打开且符合指定选项的企业DLP文件的URI列表。

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


3. 输入指定的文件标签，关闭当前正打开的拥有该标签的DLP文件。

    3.1 申请权限：ohos.permission.ENTERPRISE_ACCESS_DLP_FILE。

    3.2 设置企业DLP文件的查询选项[DlpFileQueryOptions](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#dlpfilequeryoptions)。当需要按分类标签筛选关闭特定企业DLP文件时传入此参数，当需要关闭所有企业DLP文件时可不传此参数。

    3.3 调用[dlpPermission.closeOpenedEnterpriseDlpFiles](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#dlppermissioncloseopenedenterprisedlpfiles)关闭当前打开的所有符合指定选项的企业DLP文件。

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

4. 实现SA调用的API。

    4.1 申请权限：从API版本26.0.0开始，需要申请权限ohos.permission.ENTERPRISE_ACCESS_DLP_FILE或ohos.permission.ACCESS_DLP_SERVICE；对于API版本21 - 24，需要申请权限ohos.permission.ENTERPRISE_ACCESS_DLP_FILE。

    4.2 [DlpConnPlugin](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#dlpconnplugin21)被用于registerPlugin接口中，将回调能力注册到SA（System Ability）中。

    4.3 [connectServer](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#connectserver21)提供给SA侧调用，处理完连接云端服务的请求后，通过callback将结果返回给SA。

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

5. 注册通信插件。

    5.1 申请权限：从API版本26.0.0开始，需要申请权限ohos.permission.ENTERPRISE_ACCESS_DLP_FILE或ohos.permission.ACCESS_DLP_SERVICE；对于API版本21 - 24，需要申请权限ohos.permission.ENTERPRISE_ACCESS_DLP_FILE。

    5.2 [DlpConnPlugin](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#dlpconnplugin21)被用于registerPlugin接口中，将回调能力注册到SA中。

    5.3 [registerPlugin](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#registerplugin21)将plugin注册到SA侧，待SA调用。

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

6. 获取DLP文件事件
 
    Data Protection Kit为应用提供了获取用户操作DLP文件事件信息的能力，应用可以预先订阅DLP文件事件，在用户操作DLP文件时，系统会通过安全审计服务将事件信息发送给应用。
 
    目前支持的事件类型包括DLP文件的创建、打开、修改（内容）、复制（内容）。具体开发步骤如下：
 
    6.1 具体开发步骤可以参考[单客户端订阅场景](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/devicesecurity-audit-subscribe-arkts-suevent)。 

    6.2. DLP文件事件的eventId为0x00F000006。
