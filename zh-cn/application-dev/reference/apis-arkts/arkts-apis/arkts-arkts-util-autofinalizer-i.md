# AutoFinalizer

提供一个可通过开发者自定义回调释放由开发者管理的资源的接口。 > **说明：** > > AutoFinalizer&lt;T&gt;需要和AutoFinalizerCleaner&lt;T&gt;一起使用，只实现该接口类没有任何功能。

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

<!--Device-util-interface AutoFinalizer--><!--Device-util-interface AutoFinalizer-End-->

**系统能力：** SystemCapability.Utils.Lang

## onFinalization

```TypeScript
onFinalization(heldValue: T): void
```

开发者自定义的用于释放资源的回调。

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-AutoFinalizer-onFinalization(heldValue: T): void--><!--Device-AutoFinalizer-onFinalization(heldValue: T): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| heldValue | T | 是 | 传递给 finalizer 的值。 |

