# @ohos.app.ability.appMemoryOptimizer

appMemoryOptimizer提供应用内存优化的能力，包括释放指定文件的文件页缓存、释放指定模块的文件页缓存等。

**起始版本：** 26.0.0

<!--Device-unnamed-declare namespace appMemoryOptimizer--><!--Device-unnamed-declare namespace appMemoryOptimizer-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { appMemoryOptimizer } from '@kit.AbilityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [evictFilePages](arkts-ability-appmemoryoptimizer-evictfilepages-f.md#evictfilepages-1) | 向系统发出释放指定文件的文件页缓存请求，系统会根据当前内存状况决定是否真正执行释放，不保证一定释放成功。 |
| [evictModuleFilePages](arkts-ability-appmemoryoptimizer-evictmodulefilepages-f.md#evictmodulefilepages-1) | 向系统发出释放指定模块的文件页缓存请求，系统会根据当前内存状况决定是否真正执行释放，不保证一定释放成功。系统会读取对应模块中的memory_optimizer.json配置文件，获取evictFilePages数组，然后对数组中的文件执行文件页缓存释放操作。配置文件路径：{模块目录}/src/main/resources/rawfile/memory_optimizer.json配置文件中evictFilePages数组里的文件名必须以 .so、.hap 或 .hsp 结尾。 |

