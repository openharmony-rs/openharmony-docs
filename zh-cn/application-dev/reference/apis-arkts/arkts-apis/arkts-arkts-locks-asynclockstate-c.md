# AsyncLockState

用于存储异步锁实例上当前执行的所有锁操作的信息的类。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

<!--Device-locks-class AsyncLockState--><!--Device-locks-class AsyncLockState-End-->

**系统能力：** SystemCapability.Utils.Lang

## held

```TypeScript
held: AsyncLockInfo[]
```

持有的锁信息。

**类型：** AsyncLockInfo[]

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

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

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AsyncLockState-pending: AsyncLockInfo[]--><!--Device-AsyncLockState-pending: AsyncLockInfo[]-End-->

**系统能力：** SystemCapability.Utils.Lang

