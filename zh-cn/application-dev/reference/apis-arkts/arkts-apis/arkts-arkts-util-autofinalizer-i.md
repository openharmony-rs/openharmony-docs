# AutoFinalizer

提供一个可通过开发者自定义回调释放由开发者管理的资源的接口。

**起始版本：** 22

<!--Device-util-interface AutoFinalizer<T>--><!--Device-util-interface AutoFinalizer<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { util } from '@kit.ArkTS';
```

## onFinalization

```TypeScript
onFinalization(heldValue: T): void
```

开发者自定义的用于释放资源的回调。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-AutoFinalizer-onFinalization(heldValue: T): void--><!--Device-AutoFinalizer-onFinalization(heldValue: T): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| heldValue | T | 是 | 传递给 finalizer 的值。 |

