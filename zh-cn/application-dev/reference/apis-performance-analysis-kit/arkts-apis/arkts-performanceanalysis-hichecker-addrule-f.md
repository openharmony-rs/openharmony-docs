# addRule

## 导入模块

```TypeScript
import { hichecker } from '@kit.PerformanceAnalysisKit';
```

## addRule

```TypeScript
function addRule(rule: bigint): void
```

> **说明：** > > 从API version 8开始支持，从API version 9开始废弃，建议使用[hichecker.addCheckRule](arkts-performanceanalysis-hichecker-addcheckrule-f.md)替代。 添加一条或多条规则到系统，系统根据添加的规则进行检测或反馈。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [addCheckRule](arkts-performanceanalysis-hichecker-addcheckrule-f.md)

<!--Device-hichecker-function addRule(rule: bigint): void--><!--Device-hichecker-function addRule(rule: bigint): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rule | bigint | 是 | 需要添加的规则。 |

**示例**

```TypeScript
// 添加一条规则
hichecker.addRule(hichecker.RULE_CAUTION_PRINT_LOG);

// 添加多条规则
hichecker.addRule(
          hichecker.RULE_CAUTION_PRINT_LOG | hichecker.RULE_CAUTION_TRIGGER_CRASH);
```

