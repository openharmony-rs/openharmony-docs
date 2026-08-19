# Options

Options用于指定在压缩或解压Zip文件时的选项。

**起始版本：** 23

<!--Device-zlib-interface Options--><!--Device-zlib-interface Options-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## 导入模块

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
```

## level

```TypeScript
level?: CompressLevel
```

压缩或解压时指定的压缩等级。

**类型：** [CompressLevel](arkts-basicservices-zlib-compresslevel-e.md)

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Options-level?: CompressLevel--><!--Device-Options-level?: CompressLevel-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## memLevel

```TypeScript
memLevel?: MemLevel
```

压缩时指定的使用内存等级。

**类型：** [MemLevel](arkts-basicservices-zlib-memlevel-e.md)

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Options-memLevel?: MemLevel--><!--Device-Options-memLevel?: MemLevel-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## parallel

```TypeScript
parallel?: ParallelStrategy
```

压缩策略。

**类型：** [ParallelStrategy](arkts-basicservices-zlib-parallelstrategy-e.md)

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Options-parallel?: ParallelStrategy--><!--Device-Options-parallel?: ParallelStrategy-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## pathSeparatorStrategy

```TypeScript
pathSeparatorStrategy?: PathSeparatorStrategy
```

并行策略。

**类型：** [PathSeparatorStrategy](arkts-basicservices-zlib-pathseparatorstrategy-e.md)

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Options-pathSeparatorStrategy?: PathSeparatorStrategy--><!--Device-Options-pathSeparatorStrategy?: PathSeparatorStrategy-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## strategy

```TypeScript
strategy?: CompressStrategy
```

压缩时指定的压缩策略。

**类型：** [CompressStrategy](arkts-basicservices-zlib-compressstrategy-e.md)

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Options-strategy?: CompressStrategy--><!--Device-Options-strategy?: CompressStrategy-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

