# @ohos.security.identifySensitiveContent

识别敏感内容通过输入的[Policy](arkts-dataprotection-policy-i.md)来检测指定文件中的敏感信息。
系统根据提供的[Policy](arkts-dataprotection-policy-i.md)策略（包括敏感标签、关键字集合和正则表达式），
对文件内容进行关键字匹配和正则表达式匹配，返回匹配到的敏感内容结果。

**起始版本：** 21

**系统能力：** SystemCapability.Security.DataLossPrevention

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [scanFile](arkts-dataprotection-scanfile-f.md#scanfile-1) | 根据设置的策略，识别指定文件中的敏感内容，返回识别的结果数组，包含匹配的敏感标签、匹配内容及匹配数量。使用Promise异步回调。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [MatchResult](arkts-dataprotection-matchresult-i.md) | 表示敏感内容的识别结果。 |
| [Policy](arkts-dataprotection-policy-i.md) | 定义敏感内容识别策略。单个策略内，关键字与正则表达式为顺序组合关系，实行两级匹配：首先进行关键字匹配，若命中，则仅在该关键字匹配位置的前后50字节窗口内，进行正则表达式匹配。多个Policy策略之间独立，扫描时会分别应用每个策略。sensitiveLabel用于标记匹配结果，便于识别具体匹配的策略。 |

