# AbortSignal

用于终止异步操作的对象。该类的实例必须在其创建的同一线程中访问。从其他线程访问此类的字段会导致未定义的行为。

**起始版本：** 12

**系统能力：** SystemCapability.Utils.Lang

## aborted

```TypeScript
aborted: boolean
```

设置为true以终止操作。

**类型：** boolean

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## reason

```TypeScript
reason: T
```

终止的原因。此值将用于拒绝lockAsync返回的Promise。

**类型：** T

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

