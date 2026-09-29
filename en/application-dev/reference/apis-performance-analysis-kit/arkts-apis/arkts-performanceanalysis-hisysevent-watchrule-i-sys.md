# WatchRule (System API)

```TypeScript
interface WatchRule
```

Defines event subscription rules.

**Since:** 9

<!--Device-hiSysEvent-interface WatchRule--><!--Device-hiSysEvent-interface WatchRule-End-->

**System capability:** SystemCapability.HiviewDFX.HiSysEvent

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { hiSysEvent } from '@kit.PerformanceAnalysisKit';
```

## domain

```TypeScript
domain: string
```

Event domain.

**Type:** string

**Since:** 9

<!--Device-WatchRule-domain: string--><!--Device-WatchRule-domain: string-End-->

**System capability:** SystemCapability.HiviewDFX.HiSysEvent

**System API:** This is a system API.

## name

```TypeScript
name: string
```

Event name.

**Type:** string

**Since:** 9

<!--Device-WatchRule-name: string--><!--Device-WatchRule-name: string-End-->

**System capability:** SystemCapability.HiviewDFX.HiSysEvent

**System API:** This is a system API.

## ruleType

```TypeScript
ruleType: RuleType
```

Matching rule type.

**Type:** [RuleType](arkts-performanceanalysis-hisysevent-ruletype-e-sys.md)

**Since:** 9

<!--Device-WatchRule-ruleType: RuleType--><!--Device-WatchRule-ruleType: RuleType-End-->

**System capability:** SystemCapability.HiviewDFX.HiSysEvent

**System API:** This is a system API.

## tag

```TypeScript
tag?: string
```

Event tag.

**Type:** string

**Since:** 9

<!--Device-WatchRule-tag?: string--><!--Device-WatchRule-tag?: string-End-->

**System capability:** SystemCapability.HiviewDFX.HiSysEvent

**System API:** This is a system API.
