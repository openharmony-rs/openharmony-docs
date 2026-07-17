# Options

Options用于指定在压缩或解压Zip文件时的选项。

**起始版本：** 7

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

**类型：** CompressLevel

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Options-level?: CompressLevel--><!--Device-Options-level?: CompressLevel-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## memLevel

```TypeScript
memLevel?: MemLevel
```

压缩时指定的使用内存等级。

**类型：** MemLevel

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Options-memLevel?: MemLevel--><!--Device-Options-memLevel?: MemLevel-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## parallel

```TypeScript
parallel?: ParallelStrategy
```

压缩策略。

**类型：** ParallelStrategy

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-Options-parallel?: ParallelStrategy--><!--Device-Options-parallel?: ParallelStrategy-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## pathSeparatorStrategy

```TypeScript
pathSeparatorStrategy?: PathSeparatorStrategy
```

并行策略。

**类型：** PathSeparatorStrategy

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

<!--Device-Options-pathSeparatorStrategy?: PathSeparatorStrategy--><!--Device-Options-pathSeparatorStrategy?: PathSeparatorStrategy-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## strategy

```TypeScript
strategy?: CompressStrategy
```

压缩时指定的压缩策略。

**类型：** CompressStrategy

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Options-strategy?: CompressStrategy--><!--Device-Options-strategy?: CompressStrategy-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

