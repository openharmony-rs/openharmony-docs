# RequestTraceConfig

提供trace采集的参数选项。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

<!--Device-hidebug-interface RequestTraceConfig--><!--Device-hidebug-interface RequestTraceConfig-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## bufferSizeKb

```TypeScript
bufferSizeKb: int
```

trace文件的缓存大小，以KB为单位。数值为32位无符号整型数字，超出有效范围将导致数值溢出。取值范围为[1024, 15360]，传入参数超过取值范围，参数将被设置为最近的边界值。

**类型：** int

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-RequestTraceConfig-bufferSizeKb: int--><!--Device-RequestTraceConfig-bufferSizeKb: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## durationMs

```TypeScript
durationMs: int
```

trace采集时长，以ms为单位。数值为32位无符号整型数字，超出有效范围将导致数值溢出。取值范围为[1000, 15000]，传入参数超过取值范围，参数将被设置为最近的边界值。

**类型：** int

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-RequestTraceConfig-durationMs: int--><!--Device-RequestTraceConfig-durationMs: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## identifier

```TypeScript
identifier: string
```

采集trace输出的文件名前缀。文件名前缀只取字符串前20个字符，超过部分将抛弃。前20个字符只包含大小写字母和下划线，若不符合则默认为空字符串。

**类型：** string

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-RequestTraceConfig-identifier: string--><!--Device-RequestTraceConfig-identifier: string-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## reserved

```TypeScript
reserved: int
```

预留字段，可以设置为0。

**类型：** int

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-RequestTraceConfig-reserved: int--><!--Device-RequestTraceConfig-reserved: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

