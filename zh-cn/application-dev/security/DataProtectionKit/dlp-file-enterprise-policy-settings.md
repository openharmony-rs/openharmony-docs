# 设置DLP文件防护策略
<!--Kit: Data Protection Kit-->
<!--Subsystem: Security-->
<!--Owner: @winnieHuYu-->
<!--Designer: @QRF-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->

## 场景介绍

Data Protection Kit为应用提供了设置动态防护策略的能力，在用户打开DLP文件时，系统会校验设置好的防护策略，并在必要时进行阻断。

目前支持的策略类型包括设备健康状态、网络状态、调试模式状态、高级安全模式状态和文件类型。

使用该能力无需预先注册通信插件。

## 开发步骤

1.  接口所需模块导入。
    <!-- @[dlp_include_dlpPermission](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    import { dlpPermission } from '@kit.DataProtectionKit';
    ```

2. 设置防护策略。

    2.1 申请权限：ohos.permission.ENTERPRISE_ACCESS_DLP_FILE。

    2.2 设置企业应用防护策略[EnterprisePolicy](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#enterprisepolicy21)（包含属性信息、规则和策略等）。

    2.3 调用[dlpPermission.setEnterprisePolicy](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#dlppermissionsetenterprisepolicy21)完成防护策略设置。

    <!-- @[dlp_setEnterprisePolicy](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->

    ``` TypeScript
    setEnterprisePolicy() {
      try {
        if (canIUse('SystemCapability.Security.DataLossPrevention')) {
          let attributeValues: string[] = ['1'];
          let attribute: Attribute = {
            attributeId: 'DeviceHealthyStatus',
            attributeValues: attributeValues,
            valueType: 0,
            opt: 2
          }; // 属性信息。
          let rule: Rule = {
            ruleId: 'ruleId',
            attributes: [attribute]
          }; // 规则。
          let policy: Policy = {
            rules: [rule],
            policyId: 'policyId',
            ruleConflictAlg: 0
          }; // 策略。
          let enterprisePolicy: dlpPermission.EnterprisePolicy = {
            policyString: JSON.stringify(policy)
          };
          dlpPermission.setEnterprisePolicy(enterprisePolicy);
          console.info('set enterprise policy success');
          this.result = 'set enterprise policy success';
          hilog.info(HILOG_DLP_DOMAIN, HILOG_TAG, 'set enterprise policy success');
        }
      } catch (err) {
        console.error('error message', err.message);
        this.result = 'error message' + err.message;
        hilog.error(HILOG_DLP_DOMAIN, HILOG_TAG, 'error message' + err.message);
      }
    }
    ```

## 常见问题

### 企业策略格式错误

**问题描述**：调用setEnterprisePolicy时提示策略格式错误。

**解决方法**：
- policyId和ruleId只允许字母、数字、下划线，长度不超过64字节。
- 规则最多32条，属性最多32条，属性值最多32个。
- 确保valueType与属性值类型匹配。