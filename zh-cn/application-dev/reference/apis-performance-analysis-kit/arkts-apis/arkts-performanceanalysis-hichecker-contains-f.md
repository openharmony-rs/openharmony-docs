# contains

## 导入模块

```TypeScript
```

## contains

```TypeScript
function contains(rule: bigint): boolean
```


> **说明：**
> 
> 从API version 8开始支持，从API version 9开始废弃，建议使用[hichecker.containsCheckRule](arkts-performanceanalysis-hichecker-containscheckrule-f.md)替代。
当前已添加的规则集中是否包含了某一个特定的规则。如果传入的规则级别为线程级别，则仅在当前线程中进行查询。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [containsCheckRule](arkts-performanceanalysis-hichecker-containscheckrule-f.md)

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rule | bigint | 是 | 需要查询的规则。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 查询结果。true 表示规则已添加；false 表示规则未添加。 |

**示例**

```TypeScript
// 添加一条规则
hichecker.addRule(hichecker.RULE_THREAD_CHECK_SLOW_PROCESS);

// 查询是否包含
hichecker.contains(hichecker.RULE_THREAD_CHECK_SLOW_PROCESS); // return true;
hichecker.contains(hichecker.RULE_CAUTION_PRINT_LOG); // return false;
```
