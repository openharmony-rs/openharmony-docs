# CompressFlushMode

压缩刷新模式。

**起始版本：** 12

<!--Device-zlib-export enum CompressFlushMode--><!--Device-zlib-export enum CompressFlushMode-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## NO_FLUSH

```TypeScript
NO_FLUSH = 0
```

默认值，表示正常操作。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CompressFlushMode-NO_FLUSH = 0--><!--Device-CompressFlushMode-NO_FLUSH = 0-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## PARTIAL_FLUSH

```TypeScript
PARTIAL_FLUSH = 1
```

在流中生成部分刷新点。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CompressFlushMode-PARTIAL_FLUSH = 1--><!--Device-CompressFlushMode-PARTIAL_FLUSH = 1-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## SYNC_FLUSH

```TypeScript
SYNC_FLUSH = 2
```

在保持压缩流状态的同时强制输出所有压缩数据。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CompressFlushMode-SYNC_FLUSH = 2--><!--Device-CompressFlushMode-SYNC_FLUSH = 2-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## FULL_FLUSH

```TypeScript
FULL_FLUSH = 3
```

重置压缩状态。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CompressFlushMode-FULL_FLUSH = 3--><!--Device-CompressFlushMode-FULL_FLUSH = 3-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## FINISH

```TypeScript
FINISH = 4
```

压缩或解压缩过程结束。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CompressFlushMode-FINISH = 4--><!--Device-CompressFlushMode-FINISH = 4-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## BLOCK

```TypeScript
BLOCK = 5
```

允许更精确的控制。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CompressFlushMode-BLOCK = 5--><!--Device-CompressFlushMode-BLOCK = 5-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## TREES

```TypeScript
TREES = 6
```

实施过程中有特殊目的。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CompressFlushMode-TREES = 6--><!--Device-CompressFlushMode-TREES = 6-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

