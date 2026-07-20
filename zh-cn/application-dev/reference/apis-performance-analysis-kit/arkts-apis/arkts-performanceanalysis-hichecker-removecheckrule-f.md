# removeCheckRule

## 导入模块

```TypeScript
import { hichecker } from '@kit.PerformanceAnalysisKit';
```

<a id="removecheckrule"></a>
## removeCheckRule

```TypeScript
function removeCheckRule(rule: bigint) : void
```

ɾ��һ�����������ɾ���Ĺ��������������Ч��

**起始版本：** 9

<!--Device-hichecker-function removeCheckRule(rule: bigint) : void--><!--Device-hichecker-function removeCheckRule(rule: bigint) : void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rule | bigint | 是 | ��Ҫɾ���Ĺ��� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | the parameter check failed, only one bigint type parameter is needed |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    // 删除一条规则
    hichecker.removeCheckRule(hichecker.RULE_CAUTION_PRINT_LOG);
    // 删除多条规则
    // hichecker.removeCheckRule(
    //     hichecker.RULE_CAUTION_PRINT_LOG | hichecker.RULE_CAUTION_TRIGGER_CRASH);
} catch (err) {
    console.error(`code: ${(err as BusinessError).code}, message: ${(err as BusinessError).message}`);
}

```

