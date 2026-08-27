# AsyncLockState

用于存储异步锁实例上当前执行的所有锁操作的信息的类。

**起始版本：** 12

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { ArkTSUtils } from '@kit.ArkTS';
```

## held

```TypeScript
held: AsyncLockInfo[]
```

持有的锁信息。

**类型：** [AsyncLockInfo](arkts-arkts-locks-asynclockinfo-c.md)[]

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## pending

```TypeScript
pending: AsyncLockInfo[]
```

等待中的锁信息。

**类型：** [AsyncLockInfo](arkts-arkts-locks-asynclockinfo-c.md)[]

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang
