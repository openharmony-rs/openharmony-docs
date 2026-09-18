# QueryRule (System API)

Defines event query rules.

**Since:** 9

**System capability:** SystemCapability.HiviewDFX.HiSysEvent

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { hiSysEvent } from '@kit.PerformanceAnalysisKit';
```

## condition

```TypeScript
condition?: string
```

Additional event conditions. The value of this parameter is in the format of **{"version":"V1","condition":{"and":[{"param":"*Parameter*","op":"*Operator*","value":"*Comparison value*"}]}}**.

Parameter: key value of the specified event parameter.

Supported operators: **=**, **!=**, **&lt;**, **<=**, **>** and **&gt;=**.

Multiple conditions can be configured in the **"and"** array, and the intersection of the query results is used.

**Type:** string

**Since:** 10

**System capability:** SystemCapability.HiviewDFX.HiSysEvent

**System API:** This is a system API.

## domain

```TypeScript
domain: string
```

Event domain.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.HiviewDFX.HiSysEvent

**System API:** This is a system API.

## names

```TypeScript
names: string[]
```

Array of event names. A **QueryRule** object contains multiple system event names.

**Type:** string[]

**Since:** 9

**System capability:** SystemCapability.HiviewDFX.HiSysEvent

**System API:** This is a system API.
