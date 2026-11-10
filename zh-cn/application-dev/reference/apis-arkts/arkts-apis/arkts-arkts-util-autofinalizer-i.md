# AutoFinalizer

```TypeScript
interface AutoFinalizer<T>
```

提供一个可通过开发者自定义回调释放由开发者管理的资源的接口。

> **说明：** 
> 
> AutoFinalizer<T>需要和AutoFinalizerCleaner<T>一起使用，只实现该接口类没有任何功能。

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

开发者需要实现该接口，定义对象被回收时自动触发的资源清理回调。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

<!--Device-AutoFinalizer-onFinalization(heldValue: T): void--><!--Device-AutoFinalizer-onFinalization(heldValue: T): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| heldValue | T | 是 | 当监听的对象被回收时，该值会被传递给`onFinalization`回调方法。 |
