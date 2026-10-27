# Querier（系统接口）

```TypeScript
interface Querier
```

Definition callback of receiving the query data.

**起始版本：** 12

<!--Device-securityGuard-interface Querier--><!--Device-securityGuard-interface Querier-End-->

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { securityGuard } from '@kit.SecurityGuardKit';
```

## onComplete

```TypeScript
onComplete: () => void
```

Triggered when data is complete.

**起始版本：** 12

<!--Device-Querier-onComplete: () => void--><!--Device-Querier-onComplete: () => void-End-->

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

## onError

```TypeScript
onError: (message: string) => void
```

Triggered when error.

**起始版本：** 12

<!--Device-Querier-onError: (message: string) => void--><!--Device-Querier-onError: (message: string) => void-End-->

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| message | string | 是 |  |

## onQuery

```TypeScript
onQuery: (events: Array<SecurityEvent>) => void
```

Triggered when data is returned.

**起始版本：** 12

<!--Device-Querier-onQuery: (events: Array<SecurityEvent>) => void--><!--Device-Querier-onQuery: (events: Array<SecurityEvent>) => void-End-->

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| events | Array&lt;[SecurityEvent](arkts-securityguard-securityguard-securityevent-i-sys.md)&gt; | 是 |  |
