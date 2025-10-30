# 数据防泄漏服务开发指导
<!--Kit: Data Protection Kit-->
<!--Subsystem: Security-->
<!--Owner: @winnieHuYu-->
<!--Designer: @lucky-jinduo-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->

DLP是系统提供的系统级的数据防泄漏解决方案，提供一种称为DLP的文件格式。后缀格式为“原始文件名（包含原始文件后缀）.dlp”，例如“test.docx.dlp”，文件由授权凭证和原始文件密文组成。

通过端云协同认证（需要联网）来获取文件的访问授权，授权类型包含只读、编辑、文件拥有者三种。

- 只读：能读取文件内容但不能修改。
- 编辑：能够读写文件内容，但不能修改文件权限配置。
- 文件拥有者：可读写文件、修改权限配置、恢复原始文件等。

应用需要访问DLP文件时，系统会自动安装应用的DLP沙箱分身应用，相当于完全独立的应用，数据和配置会继承原应用，但相互之间并不共享。分身应用在运行时会处于DLP沙箱环境中，访问外部的权限会被限制，以防止数据的泄漏。每当打开一个新的DLP文件会生成一个应用沙箱分身，沙箱应用之间也是相互隔离的，当应用关闭后应用分身会自动卸载，沙箱期间产生的临时数据也会丢弃。

正常情况下，应用不会感知到沙箱的存在，访问的也是解密后的明文，和访问普通文件没有区别，但由于DLP沙箱会限制其访问外部的权限（例如网络、剪切板、截屏、录屏、蓝牙等）。为了更好的用户体验，需要应用进行适配，例如文件只读的情况下，不应显示“保存”按钮，不应主动联网等。

## 沙箱限制

当应用进入DLP沙箱状态时，可以申请的权限将受到限制，根据DLP文件授权类型不同，限制也不相同，如下表：

| 权限名 | 说明 | 授权类型：只读 | 授权类型：编辑/文件拥有者 |
| -------- | -------- | -------- | -------- |
| ohos.permission.USE_BLUETOOTH | 允许应用使用蓝牙。 | 禁止 | 禁止 |
| ohos.permission.INTERNET |允许应用访问网络。 |  禁止 | 禁止 |
| ohos.permission.DISTRIBUTED_DATASYNC | 允许应用与远程设备交换用户数据（如图片、音乐、视频、应用数据等）。 | 禁止 | 禁止 |
| ohos.permission.WRITE_MEDIA | 应用读写用户媒体文件，如视频、音频、图片等，需要申请此权限。 | 禁止 | 允许 |
| ohos.permission.NFC_TAG | 允许应用使用NFC。 | 禁止 | 允许 |

## 接口说明

| 接口名 | 描述 |
| -------- | -------- |
| isDLPFile(fd: number): Promise&lt;boolean&gt; <br> isDLPFile(fd: number, callback: AsyncCallback&lt;boolean&gt;): void| 判断是否是dlp文件。 |
| getDLPPermissionInfo(): Promise&lt;DLPPermissionInfo&gt; <br>getDLPPermissionInfo(callback: AsyncCallback&lt;DLPPermissionInfo&gt;): void  | 获取当前沙箱应用的权限类型。 |
| getOriginalFileName(fileName: string): string | 获取dlp文件原始文件名。 |
| getDLPSuffix(): string | 获取dlp文件dlp后缀名。 |
| on(type: 'openDLPFile', listener: Callback&lt;AccessedDLPFileInfo&gt;): void | 注册dlp文件打开事件监听，用于原始应用获取dlp文件打开事件。 |
| off(type: 'openDLPFile', listener?: Callback&lt;AccessedDLPFileInfo&gt;): void | 取消dlp文件打开事件监听。 |
| isInSandbox(): Promise&lt;boolean&gt; <br>isInSandbox(callback: AsyncCallback&lt;boolean&gt;): void | 判断当前是否是dlp沙箱应用。 |
| getDLPSupportedFileTypes(): Promise&lt;Array&lt;string&gt;&gt;<br>getDLPSupportedFileTypes(callback: AsyncCallback&lt;Array&lt;string&gt;&gt;): void | 获取当前系统支持添加权限保护的文件格式类型。 |
| setRetentionState(docUris: Array&lt;string&gt;): Promise&lt;void&gt; <br> setRetentionState(docUris: Array&lt;string&gt;, callback: AsyncCallback&lt;void&gt;): void | 设置dlp分身应用保留状态。 |
| cancelRetentionState(docUris: Array&lt;string&gt;): Promise&lt;void&gt;<br> cancelRetentionState(docUris: Array&lt;string&gt;, callback: AsyncCallback&lt;void&gt;): void | 取消dlp分身应用保留状态。 |
| getRetentionSandboxList(bundleName?: string): Promise&lt;Array&lt;RetentionSandboxInfo&gt;&gt; <br> getRetentionSandboxList(bundleName: string, callback: AsyncCallback&lt;Array&lt;RetentionSandboxInfo&gt;&gt;): void  <br> getRetentionSandboxList(callback: AsyncCallback&lt;Array&lt;RetentionSandboxInfo&gt;&gt;): void| 获取当前保留沙箱列表。 |
| getDLPFileAccessRecords(): Promise&lt;Array&lt;AccessedDLPFileInfo&gt;&gt; <br> getDLPFileAccessRecords(callback: AsyncCallback&lt;Array&lt;AccessedDLPFileInfo&gt;&gt;): void | 获取dlp文件访问记录。 |
|setSandboxAppConfig(configInfo: string): Promise&lt;void&gt;|设置沙箱应用配置信息。|
|getSandboxAppConfig(): Promise&lt;string&gt;|查询沙箱应用配置信息。|
|cleanSandboxAppConfig(): Promise&lt;void&gt;|清理沙箱应用配置信息。|
| startDLPManagerForResult(context: common.UIAbilityContext, want: Want): Promise&lt;DLPManagerResult&gt; <br> | 在当前UIAbility界面以无边框形式打开DLP权限管理应用（只支持Stage模式）。 |
|setEnterprisePolicy(policy: EnterprisePolicy): void|设置企业应用防护策略。|
| scanFile(filePath: string, identifyPolicysies: Array&lt;Policy&gt;):  Promise&lt;Array&lt;MatchResult&gt;&gt;| 识别指定文件中的敏感内容。 <br>从API 21开始支持该接口。 |

## 开发步骤

本文档提供接口示例代码，如需要了解工程项目创建方式，可参考[工程创建](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-project)。
1. 引入[dlpPermission](../../reference/apis-data-protection-kit/js-apis-dlppermission.md)模块。
	<!-- @[dlp_include](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/SystemFeature/Security/DLP/entry/src/main/ets/pages/Index.ets) -->
 
 ``` TypeScript
 import { dlpPermission } from '@kit.DataProtectionKit';
 import { identifySensitiveContent } from '@kit.DataProtectionKit';
 ```

2. 打开DLP文件，系统会自动安装应用的DLP沙箱分身应用。以下代码应在应用页Ability中使用。  
使用该接口的前置条件：链接DLP凭据服务器。  

	<!-- @[dlp_prepareForOpenDlpFile](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/SystemFeature/Security/DLP/entry/src/main/ets/pages/Index.ets) -->
 
 ``` TypeScript
 openDlpFile(dlpUri: string, fileName: string, fd: number) {
   let want:Want = {
     'action': 'ohos.want.action.viewData',
     'uri': dlpUri,
     'parameters' : {
       'fileName': {
         'name': fileName
       },
       'keyFd': {
         'type': 'FD',
         'value': fd
       }
     }
   }
 
   let context = getContext() as common.UIAbilityContext; // 获取当前UIAbilityContext
 
   try {
     console.log('openDLPFile:' + JSON.stringify(want));
     console.log('openDLPFile: delegator:' + JSON.stringify(context));
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

  	以上代码需要在module.json5文件中增加ohos.want.action.viewData：

	<!-- @[dlp_configurationModule](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/SystemFeature/Security/DLP/entry/src/main/module.json5) -->
 
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
  
3. 生成DLP文件。  
使用该接口的前置条件：链接DLP凭据服务器。

   [该功能云端对接模块当前需要开发者自行搭建](../DataProtectionKit/dlp-overview.md)，并且该功能需要配置域账号环境。

    3.1 当前支持生成DLP文件的原文件类型: ".doc", ".docm", ".docx", ".dot", ".dotm", ".dotx", ".odp", ".odt", ".pdf", ".pot", ".potm", ".potx", ".ppa", ".ppam", ".pps", ".ppsm", ".ppsx", ".ppt", ".pptm", ".pptx", ".rtf", ".txt", ".wps", ".xla", ".xlam", ".xls", ".xlsb", ".xlsm", ".xlsx", ".xlt", ".xltm", ".xltx", ".xlw", ".xml", ".xps"。

    3.2 首先要有一个DLP权限应用有读写权限的(比如文件管理的文档目录下)并且属于以上文件类型之一的原文件。

    3.3 以无边框形式打开DLP权限管理应用。此方法只能在UIAbility上下文中调用，只支持Stage模式。调用以下代码，拉起DLP管理应用的设置权限页面，输入相关的授权账号信息，点击保存，在拉起的filepicker中选择DLP文件的保存路径，保存DLP文件。
	<!-- @[dlp_generateDlpFiles](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/SystemFeature/Security/DLP/entry/src/main/ets/pages/Index.ets) -->
 
 ``` TypeScript
 generateDlpFiles() {
   try {
     let fileUri: string = this.uri;
     let fileName: string = this.fileName;
     let context = getContext() as common.UIAbilityContext; // 获取当前UIAbilityContext
     let want: Want = {
       'uri': fileUri,
       'parameters': {
         'displayName': fileName
       }
     };// 请求参数
     dlpPermission.startDLPManagerForResult(context, want).then((res: dlpPermission.DLPManagerResult) => {
       this.result = 'startDLPManagerForResult result.resultCode:' + res.resultCode;
       console.info('startDLPManagerForResult res.resultCode:' + res.resultCode);
       console.info('startDLPManagerForResult res.want:' + JSON.stringify(res.want));
       hilog.info(HILOG_DLP_DOMAIN, HILOG_TAG, 'startDLPManagerForResult res.resultCode:' + res.resultCode);
       hilog.info(HILOG_DLP_DOMAIN, HILOG_TAG, 'startDLPManagerForResult res.want:' + JSON.stringify(res.want));
     });
   } catch (err) {
     this.result = 'startDLPManagerForResult error:' + (err as BusinessError).code + (err as BusinessError).message;
     console.error('startDLPManagerForResult error:' + (err as BusinessError).code + (err as BusinessError).message);
     hilog.error(HILOG_DLP_DOMAIN, HILOG_TAG, 'startDLPManagerForResult error:' + (err as BusinessError).code + (err as BusinessError).message);
   }
 }
 ```

4. 查询当前应用是否在沙箱中。  
使用该接口的前置条件：由demo应用打开DLP文件。

	<!-- @[dlp_isInSandBox](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/SystemFeature/Security/DLP/entry/src/main/ets/pages/Index.ets) -->


5. 查询当前编辑的文件权限，根据文件授权的不同，DLP沙箱被限制的权限有所不同，参考[沙箱限制](#沙箱限制)。  
使用该接口的前置条件：由demo应用打开DLP文件。
	<!-- @[dlp_getDLPPermissionInfo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/SystemFeature/Security/DLP/entry/src/main/ets/pages/Index.ets) -->

6. 获取当前可支持DLP方案的文件扩展名类型列表，用于应用判断能否生成DLP文件，可用在实现类似文件管理器设置DLP权限的场景。

	<!-- @[dlp_getDLPSupportedFileTypes](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/SystemFeature/Security/DLP/entry/src/main/ets/pages/Index.ets) -->

7. 判断当前打开文件是否是DLP文件。  
使用该接口的前置条件：需要dlp文件进行判断。

	<!-- @[dlp_isCurrentDlpFile](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/SystemFeature/Security/DLP/entry/src/main/ets/pages/Index.ets) -->


8. 订阅、取消订阅DLP打开事件。

	<!-- @[dlp_subscribe](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/SystemFeature/Security/DLP/entry/src/main/ets/pages/Index.ets) -->


9. 获取DLP文件打开记录。  
使用该接口的前置条件：由demo应用打开DLP文件。

	<!-- @[dlp_getDLPFileAccessRecords](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/SystemFeature/Security/DLP/entry/src/main/ets/pages/Index.ets) -->

10. 获取DLP文件保留沙箱记录。  
使用该接口的前置条件：由demo应用打开DLP文件。

	<!-- @[dlp_getRetentionSandboxList](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/SystemFeature/Security/DLP/entry/src/main/ets/pages/Index.ets) -->
11. 设置沙箱应用配置信息。

	<!-- @[dlp_setSandboxAppConfig](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/SystemFeature/Security/DLP/entry/src/main/ets/pages/Index.ets) -->


12. 清理沙箱应用配置信息。

	<!-- @[dlp_cleanSandboxAppConfig](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/SystemFeature/Security/DLP/entry/src/main/ets/pages/Index.ets) -->

13. 查询沙箱应用配置信息。

	<!-- @[dlp_getSandboxAppConfig](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/SystemFeature/Security/DLP/entry/src/main/ets/pages/Index.ets) -->

14. 以无边框形式打开DLP权限管理应用。此方法只能在UIAbility上下文中调用，只支持Stage模式。  
使用该接口的前置条件：链接DLP凭据服务器。

	<!-- @[dlp_startDLPManagerForResult](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/SystemFeature/Security/DLP/entry/src/main/ets/pages/Index.ets) -->
15. 查询当前系统是否提供DLP特性。  
使用该接口的前置条件：链接DLP凭据服务器。
	<!-- @[dlp_isDLPFeature](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/SystemFeature/Security/DLP/entry/src/main/ets/pages/Index.ets) -->
16. 设置企业应用防护策略。   
使用该接口的前置条件：链接DLP凭据服务器。
    
    16.1 策略格式。
    | 字段名 | 类型 | 说明 |
    | -------- | -------- | -------- |
    | rules | Array&lt;Rule&gt; | 具体规则列表，一条策略可以设置多条规则，最多32条。 |
    | policyId |string | 策略名称。长度不超过64字节，只允许由字母（包括大写和小写）、数字（0-9）、下划线（_）组成。 |
    | ruleConflictAlg | number | 规则冲突解决算法，0表示首次匹配，1表示完全匹配。 |

    16.2 规则格式。
    | 字段名 | 类型 | 说明 |
    | -------- | -------- | -------- |
      | ruleId |string | 规则名称，长度不超过64字节，只允许由字母（包括大写和小写）、数字（0-9）、下划线（_）组成。 |
    | attributes | Array&lt;Attribute&gt; | 具体属性信息列表，一条规则可以设置多条规则，最多32条。 |

    16.3 属性信息格式。
    | 字段名 | 类型 | 说明 |
    | -------- | -------- | -------- |
      | attributeId |string | 属性信息名称。 |
    | attributeValues | Array&lt;string&gt; | 属性值，一条属性信息可以设置多个属性值，最多32个。 |
    | valueType | number | 属性值类型，0表示整型，1代表字符串。 |
    | opt | number | 判断方法，用于真实属性信息与策略属性信息作比较。 |

    16.4 当前支持的属性信息。
    | 属性信息名称 | 属性值 | 属性值类型 | 场景 |
    | -------- | -------- | -------- | -------- |
     | DeviceHealthyStatus |1 <br> 2 <br> 3 <br> 4 | 整型 | 1：设备健康报告显示正常。 <br>2：设备有健康风险，但风险因子和root无关。 <br> 3：设备有健康风险，且风险因子和root相关。 <br> 4：异常场景。 |
    | NetStatus | InterNet <br> ExtraNet <br> NoNet | 字符串 | InterNet：设备在公司内部使用。<br>ExtraNet：设备在公司外部使用。<br>NoNet：设备处于离线断网状态。 |
    | DebugMode | 1 <br> 2 | 整型 | 1：该设备已开启调试模式。<br>2：该设备未开启调试模式。 |
    | AdvancedSecurityMode | 1 <br> 2 | 整型 | 1：该设备已开启高级安全模式。<br>2：该设备未开启高级安全模式。  |

	<!-- @[dlp_setDLPProtectPolicy](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/SystemFeature/Security/DLP/entry/src/main/ets/pages/Index.ets) -->
17. （API 21开始支持）识别指定文件中的敏感内容。  
使用该接口的前置条件：链接DLP凭据服务器。
	<!-- @[dlp_scanSensitiveInfo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/SystemFeature/Security/DLP/entry/src/main/ets/pages/Index.ets) -->
