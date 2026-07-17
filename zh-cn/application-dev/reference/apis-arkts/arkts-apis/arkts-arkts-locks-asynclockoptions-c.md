# AsyncLockOptions

锁操作的选项。

**起始版本：** 12

<!--Device-locks-class AsyncLockOptions<T>--><!--Device-locks-class AsyncLockOptions<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { ArkTSUtils } from '@kit.ArkTS';
```

## constructor

```TypeScript
constructor()
```

默认构造函数。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AsyncLockOptions-constructor()--><!--Device-AsyncLockOptions-constructor()-End-->

**系统能力：** SystemCapability.Utils.Lang

## isAvailable

```TypeScript
isAvailable: boolean
```

如果值为true且lockAsync无法立即获取锁，则操作将被取消。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AsyncLockOptions-isAvailable: boolean--><!--Device-AsyncLockOptions-isAvailable: boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

## signal

```TypeScript
signal: AbortSignal<T> | null
```

用于终止异步操作的对象。如果signal.aborted为true，回调将不会被调用。

**类型：** AbortSignal<T> | null

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AsyncLockOptions-signal: AbortSignal<T> | null--><!--Device-AsyncLockOptions-signal: AbortSignal<T> | null-End-->

**系统能力：** SystemCapability.Utils.Lang

## timeout

```TypeScript
timeout: number
```

锁操作的超时时间，单位为毫秒。如果该值大于零，当超时到达时，lockAsync将拒绝返回的Promise。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AsyncLockOptions-timeout: number--><!--Device-AsyncLockOptions-timeout: number-End-->

**系统能力：** SystemCapability.Utils.Lang

