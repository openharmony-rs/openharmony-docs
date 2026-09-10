# 识别敏感内容
<!--Kit: Data Protection Kit-->
<!--Subsystem: Security-->
<!--Owner: @Yuan_bys-->
<!--Designer: @zhengdu_628-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->
 
## 场景介绍
 
Data Protection Kit为应用提供了识别文件中是否存在敏感内容的能力，方便应用判断文件是否属于敏感文件，从而对该文件实行进一步的管控。

## 约束与限制

1. 识别敏感内容支持的文件格式：txt、doc、docx、xls、xlsx、ppt、pptx。
2. 识别敏感内容支持文件最大80MB。
 
## 开发步骤
 
1. 导入模块。 
    <!-- @[dlp_include_identifySensitiveContent](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    import { identifySensitiveContent } from '@kit.DataProtectionKit';
    ```
 
2. 根据设置的策略，识别指定文件中的敏感内容。
 
    2.1 申请权限：ohos.permission.ENTERPRISE_DATA_IDENTIFY_FILE。
 
    2.2 设置待识别的文件物理路径和用于识别敏感内容的策略数组。
 
    2.3 调用[identifySensitiveContent.scanFile](../../reference/apis-data-protection-kit/js-apis-identifySensitiveContent.md#identifysensitivecontentscanfile)，根据设置的策略，识别指定文件中的敏感内容，返回识别的结果数组，包含匹配的敏感标签、匹配内容及匹配数量。
 
    <!-- @[dlp_scanSensitiveInfo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    scanSensitiveInfo() {
      let filepath = this.uri;
      let policies: identifySensitiveContent.Policy[] = [
        { 'sensitiveLabel': '1', 'keywords': [], 'regex': '' }
      ];
      if (canIUse('SystemCapability.Security.DataLossPrevention')) {
        try {
          identifySensitiveContent.scanFile(filepath, policies).then(records => {
            console.info('scanFile finish');
            this.result = 'scanFile finish';
            hilog.info(HILOG_DLP_DOMAIN, HILOG_TAG, 'scanFile finish');
          }).catch((err: Error) => {
            console.error('error message', err.message);
            this.result = 'error message' + err.message;
            hilog.error(HILOG_DLP_DOMAIN, HILOG_TAG, 'error message' + err.message);
          })
        } catch (err) {
          console.error('error message', err.message);
          this.result = 'error message' + err.message;
          hilog.error(HILOG_DLP_DOMAIN, HILOG_TAG, 'error message' + err.message);
        }
      }
    }
    ```
 
 
 
## 常见问题
 
### 敏感内容扫描失败
**问题描述**：调用scanFile扫描敏感内容时报错。
 
**解决方法**：
- 确认文件路径是否正确，例如：路径是否存在、路径是否是物理路径。
- 确认策略配置格式是否正确，例如：正则表达式是否正确、策略内容长度是否超上限。