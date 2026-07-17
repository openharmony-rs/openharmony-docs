# ConfigOption

提供对应用事件打点功能的配置选项。

**起始版本：** 9

<!--Device-hiAppEvent-interface ConfigOption--><!--Device-hiAppEvent-interface ConfigOption-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## 导入模块

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## disable

```TypeScript
disable?: boolean
```

打点功能开关，默认值为false。true：关闭打点功能，false：开启打点功能。

**类型：** boolean

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ConfigOption-disable?: boolean--><!--Device-ConfigOption-disable?: boolean-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## maxStorage

```TypeScript
maxStorage?: string
```

打点数据存放目录的配额大小，默认值为“10MB”。建议配额大小不超过10MB，配额过大可能会影响接口效率。

在目录大小超出配额后，下次打点会触发对目录的清理操作：按从旧到新的顺序逐个删除打点数据文件，直到目录大小不超出配额时结束。

配额值字符串规格如下：

- 配额值字符串只由数字字符和大小单位字符（单位字符支持[b|k|kb|m|mb|g|gb|t|tb]，不区分大小写）构成。  
- 配额值字符串必须以数字开头，后面可以选择不传单位字符（默认使用byte作为单位），或者以单位字符结尾。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ConfigOption-maxStorage?: string--><!--Device-ConfigOption-maxStorage?: string-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

