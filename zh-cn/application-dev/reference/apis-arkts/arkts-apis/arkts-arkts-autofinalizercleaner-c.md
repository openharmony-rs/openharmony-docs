# AutoFinalizerCleaner

用于通过开发者自定义回调释放由开发者管理的资源的 cleaner。

**起始版本：** 22

**系统能力：** SystemCapability.Utils.Lang

## register

```TypeScript
static register<T>(obj: AutoFinalizer<T>, heldValue: T): void
```

注册释放由开发者管理的资源的对象。

**起始版本：** 22

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| obj | AutoFinalizer&lt;T&gt; | 是 | 注册到 cleaner 的对象。 |
| heldValue | T | 是 | 传递给 finalizer 的值。 |

