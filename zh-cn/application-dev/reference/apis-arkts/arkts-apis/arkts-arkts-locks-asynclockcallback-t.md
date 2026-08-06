# AsyncLockCallback

```TypeScript
type AsyncLockCallback<T> = () => T | Promise<T>
```

这是一个补充类型别名，表示lockAsync函数所有重载中的回调。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-locks-type AsyncLockCallback<T> = () => T | Promise<T>--><!--Device-locks-type AsyncLockCallback<T> = () => T | Promise<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

