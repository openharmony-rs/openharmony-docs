# AsyncLockInfo

关于锁的信息。

**起始版本：** 12

<!--Device-locks-class AsyncLockInfo--><!--Device-locks-class AsyncLockInfo-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { ArkTSUtils } from '@kit.ArkTS';
```

## contextId

```TypeScript
contextId: number
```

lockAsync调用者的执行上下文标识符。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AsyncLockInfo-contextId: number--><!--Device-AsyncLockInfo-contextId: number-End-->

**系统能力：** SystemCapability.Utils.Lang

## mode

```TypeScript
mode: AsyncLockMode
```

锁操作的模式。

**类型：** AsyncLockMode

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AsyncLockInfo-mode: AsyncLockMode--><!--Device-AsyncLockInfo-mode: AsyncLockMode-End-->

**系统能力：** SystemCapability.Utils.Lang

## name

```TypeScript
name: string
```

锁的名称。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AsyncLockInfo-name: string--><!--Device-AsyncLockInfo-name: string-End-->

**系统能力：** SystemCapability.Utils.Lang

