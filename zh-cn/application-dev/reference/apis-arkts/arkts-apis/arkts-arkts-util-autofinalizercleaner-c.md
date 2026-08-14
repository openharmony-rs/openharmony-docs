# AutoFinalizerCleaner

用于通过开发者自定义回调释放由开发者管理的资源的 cleaner。

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

<!--Device-util-class AutoFinalizerCleaner--><!--Device-util-class AutoFinalizerCleaner-End-->

**系统能力：** SystemCapability.Utils.Lang

## register

```TypeScript
static register<T>(obj: AutoFinalizer<T>, heldValue: T): void
```

注册释放由开发者管理的资源的对象。

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-AutoFinalizerCleaner-static register<T>(obj: AutoFinalizer<T>, heldValue: T): void--><!--Device-AutoFinalizerCleaner-static register<T>(obj: AutoFinalizer<T>, heldValue: T): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| obj | [AutoFinalizer](arkts-arkts-util-autofinalizer-i.md)&lt;T&gt; | 是 | 注册到 cleaner 的对象。 |
| heldValue | T | 是 | 传递给 finalizer 的值。 |

