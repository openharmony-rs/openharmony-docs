# PathSeparatorStrategy

PathSeparatorStrategy作为[Options](arkts-basicservices-zlib-options-i.md)的一个属性，用于指定解压时目标压缩包内文件路径中分隔符的处理策略。

**起始版本：** 21

<!--Device-zlib-export enum PathSeparatorStrategy--><!--Device-zlib-export enum PathSeparatorStrategy-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## PATH_SEPARATOR_STRATEGY_DEFAULT

```TypeScript
PATH_SEPARATOR_STRATEGY_DEFAULT = 0
```

默认值，压缩包内文件路径中的分隔符不做处理。

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

<!--Device-PathSeparatorStrategy-PATH_SEPARATOR_STRATEGY_DEFAULT = 0--><!--Device-PathSeparatorStrategy-PATH_SEPARATOR_STRATEGY_DEFAULT = 0-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## PATH_SEPARATOR_STRATEGY_REPLACE_BACKSLASH

```TypeScript
PATH_SEPARATOR_STRATEGY_REPLACE_BACKSLASH = 1
```

压缩包内文件路径中的反斜杠'\'替换为斜杠'/'。

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

<!--Device-PathSeparatorStrategy-PATH_SEPARATOR_STRATEGY_REPLACE_BACKSLASH = 1--><!--Device-PathSeparatorStrategy-PATH_SEPARATOR_STRATEGY_REPLACE_BACKSLASH = 1-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

