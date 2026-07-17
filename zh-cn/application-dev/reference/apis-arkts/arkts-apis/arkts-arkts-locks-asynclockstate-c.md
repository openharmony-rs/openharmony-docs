# AsyncLockState

AsyncLock实例上所有锁操作的信息。

**起始版本：** 12

<!--Device-locks-class AsyncLockState--><!--Device-locks-class AsyncLockState-End-->

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

**类型：** AsyncLockInfo[]

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AsyncLockState-held: AsyncLockInfo[]--><!--Device-AsyncLockState-held: AsyncLockInfo[]-End-->

**系统能力：** SystemCapability.Utils.Lang

## pending

```TypeScript
pending: AsyncLockInfo[]
```

等待中的锁信息。

**类型：** AsyncLockInfo[]

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AsyncLockState-pending: AsyncLockInfo[]--><!--Device-AsyncLockState-pending: AsyncLockInfo[]-End-->

**系统能力：** SystemCapability.Utils.Lang

