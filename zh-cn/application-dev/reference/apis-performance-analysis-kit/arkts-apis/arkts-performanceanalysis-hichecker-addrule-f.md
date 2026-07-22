# addRule

## 导入模块

```TypeScript
import { hichecker } from '@kit.PerformanceAnalysisKit';
```

## addRule

```TypeScript
function addRule(rule: bigint): void
```

> **˵����**  
>  
> ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��[hichecker.addCheckRule](arkts-performanceanalysis-hichecker-addcheckrule-f.md#addcheckrule)�����

����һ�����������ϵͳ��ϵͳ�������ӵĹ�����м�������

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [addCheckRule](arkts-performanceanalysis-hichecker-addcheckrule-f.md#addcheckrule)

<!--Device-hichecker-function addRule(rule: bigint): void--><!--Device-hichecker-function addRule(rule: bigint): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rule | bigint | 是 | ��Ҫ���ӵĹ��� |

**示例：**

```TypeScript
// 添加一条规则
hichecker.addRule(hichecker.RULE_CAUTION_PRINT_LOG);

// 添加多条规则
hichecker.addRule(
          hichecker.RULE_CAUTION_PRINT_LOG | hichecker.RULE_CAUTION_TRIGGER_CRASH);

```

