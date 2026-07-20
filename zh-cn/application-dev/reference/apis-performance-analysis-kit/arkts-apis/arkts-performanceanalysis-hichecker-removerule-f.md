# removeRule

## 导入模块

```TypeScript
import { hichecker } from '@kit.PerformanceAnalysisKit';
```

<a id="removerule"></a>
## removeRule

```TypeScript
function removeRule(rule: bigint): void
```

> **˵����**  
>  
> ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��[hichecker.removeCheckRule](arkts-performanceanalysis-hichecker-removecheckrule-f.md#removecheckrule-1)�����

ɾ��һ�����������ɾ���Ĺ��������������Ч��

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [removeCheckRule](arkts-performanceanalysis-hichecker-removecheckrule-f.md#removecheckrule-1)

<!--Device-hichecker-function removeRule(rule: bigint): void--><!--Device-hichecker-function removeRule(rule: bigint): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rule | bigint | 是 | ��Ҫɾ���Ĺ��� |

**示例：**

```TypeScript
// 删除一条规则
hichecker.removeRule(hichecker.RULE_CAUTION_PRINT_LOG);

// 删除多条规则
hichecker.removeRule(
          hichecker.RULE_CAUTION_PRINT_LOG | hichecker.RULE_CAUTION_TRIGGER_CRASH);

```

