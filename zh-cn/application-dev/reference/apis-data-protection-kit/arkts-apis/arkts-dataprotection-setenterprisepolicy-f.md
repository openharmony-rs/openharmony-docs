# setEnterprisePolicy

## setEnterprisePolicy

```TypeScript
function setEnterprisePolicy(policy: EnterprisePolicy): void
```

设置企业应用防护策略。调用成功后，企业应用的DLP防护将按照设置的策略执行。

该接口可用于企业管理员配置DLP安全策略，以统一管理企业数据安全防护规则。

> **说明：**
>
> 该接口仅支持企业账号调用。

**起始版本：** 21

**需要权限：** ohos.permission.ENTERPRISE_ACCESS_DLP_FILE

**系统能力：** SystemCapability.Security.DataLossPrevention

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| policy | EnterprisePolicy | 是 | 待设置的企业应用防护策略，设置后将按策略对企业DLP文件进行访问控制和行为限制。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [19100001](../errorcode-dlp.md#19100001-入参错误) | Invalid parameter value. |
| [19100011](../errorcode-dlp.md#19100011-系统服务工作异常) | The system ability works abnormally. |
| [19100021](../errorcode-dlp.md#19100021-设置企业应用策略失败) | Failed to set the enterprise policy. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

interface Attribute {
  attributeId: string;
  attributeValues: Array<string>;
  valueType: number;
  opt: number;
}

interface Rule {
  ruleId: string;
  attributes: Array<Attribute>;
}

interface Policy {
  rules: Array<Rule>;
  policyId: string;
  ruleConflictAlg: number;
}

try {
    let attributeValues: Array<string> = [ '1' ];
    let attribute: Attribute = {
        attributeId: 'DeviceHealthyStatus',
        attributeValues: attributeValues,
        valueType: 0,
        opt: 2
    }; // 属性信息。
    let rule: Rule = {
        ruleId: 'ruleId',
        attributes: [ attribute ]
    }; // 规则。
    let policy: Policy = {
        rules: [ rule ],
        policyId: 'policyId',
        ruleConflictAlg: 0
    }; // 策略。
    let enterprisePolicy: dlpPermission.EnterprisePolicy = {
        policyString: JSON.stringify(policy)
    };
    dlpPermission.setEnterprisePolicy(enterprisePolicy);
    console.info('set enterprise policy success'); 
} catch (err) { 
    console.error('error:' + err.code + err.message); // 失败报错。 
}

```

