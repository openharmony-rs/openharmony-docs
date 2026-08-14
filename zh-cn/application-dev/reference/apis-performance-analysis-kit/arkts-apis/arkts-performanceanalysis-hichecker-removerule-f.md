# removeRule

## removeRule

```TypeScript
function removeRule(rule: bigint): void
```

> **说明：** > > 从API version 8开始支持，从API version 9开始废弃，建议使用[hichecker.removeCheckRule](arkts-performanceanalysis-hichecker-removecheckrule-f.md#removeCheckRule)替代。 删除一条或多条规则，删除的规则后续将不再生效。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [removeCheckRule](arkts-performanceanalysis-hichecker-removecheckrule-f.md#removeCheckRule)

<!--Device-hichecker-function removeRule(rule: bigint): void--><!--Device-hichecker-function removeRule(rule: bigint): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rule | bigint | 是 | 需要删除的规则。 |

## 示例

```TypeScript
// 删除一条规则
hichecker.removeRule(hichecker.RULE_CAUTION_PRINT_LOG);

// 删除多条规则
hichecker.removeRule(
          hichecker.RULE_CAUTION_PRINT_LOG | hichecker.RULE_CAUTION_TRIGGER_CRASH);
```

