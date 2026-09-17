# Querier（系统接口）

用于接收安全数据的回调函数。

@interface Querier

**起始版本：** 12

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

获取数据结束时触发。

**起始版本：** 12

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

## onError

```TypeScript
onError: (message: string) => void
```

查询存在失败时触发。

**起始版本：** 12

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

返回数据时触发。

**起始版本：** 12

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| events | Array&lt;[SecurityEvent](arkts-securityguard-securityguard-securityevent-i-sys.md)&gt; | 是 |  |
