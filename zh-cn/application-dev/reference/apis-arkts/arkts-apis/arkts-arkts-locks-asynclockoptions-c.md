# AsyncLockOptions

表示锁操作选项的类。

**起始版本：** 12

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { ArkTSUtils } from '@kit.ArkTS';
```

## constructor

```TypeScript
constructor()
```

默认构造函数。创建一个所有属性均具有默认值的异步锁配置项实例。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## isAvailable

```TypeScript
isAvailable: boolean
```

当前锁是否可用。取值为true，则只有在尚未持有锁定请求时才会授予该锁定请求；为false则表示将等待当前锁被释放。默认为 false。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## signal

```TypeScript
signal: AbortSignal<T> | null
```

用于终止异步操作的对象。当signal.aborted为true时，锁请求将被丢弃；当signal.aborted为false时，请求会继续等待获取锁；当signal为null时，请求正常排队运行。默认为 null。

**类型：** [AbortSignal](arkts-arkts-locks-abortsignal-c.md)&lt;T&gt; \| null

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## timeout

```TypeScript
timeout: number
```

锁的超时时间，单位为毫秒。若该值大于零，且操作运行时间超过该时间，lockAsync将返回被拒绝的Promise。默认为 0。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang
