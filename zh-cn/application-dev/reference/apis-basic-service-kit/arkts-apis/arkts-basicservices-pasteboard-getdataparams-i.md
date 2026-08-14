# GetDataParams

应用在使用剪贴板提供的文件拷贝能力的情况下需要的参数，包含目标路径、文件冲突选项、进度条类型等。调用本接口前，需确保无其他拷贝或粘贴操作正在进行。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-pasteboard-interface GetDataParams--><!--Device-pasteboard-interface GetDataParams-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

## destUri

```TypeScript
destUri?: string
```

拷贝文件的目标路径对应的URI。 若不支持文件处理，则不需要设置此参数；若应用涉及复杂文件处理策略或需要区分文件多路径存储，建议不设置此参数，由应用自行完成文件copy处理，默认为空。

**类型：** string

**默认值：** -

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-GetDataParams-destUri?: string--><!--Device-GetDataParams-destUri?: string-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

## fileConflictOptions

```TypeScript
fileConflictOptions?: FileConflictOptions
```

定义文件拷贝冲突时的选项。 OVERWRITE（覆盖）适合需要确保目标路径使用最新文件内容的场景；SKIP（跳过）适合需要保留目标路径原有文件、避免意外覆盖的场景。默认为OVERWRITE。

**类型：** FileConflictOptions

**默认值：** FileConflictOptions.OVERWRITE

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-GetDataParams-fileConflictOptions?: FileConflictOptions--><!--Device-GetDataParams-fileConflictOptions?: FileConflictOptions-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

## progressIndicator

```TypeScript
progressIndicator: ProgressIndicator
```

定义进度条指示选项，可选择是否采用系统默认进度显示。设置为DEFAULT时采用系统默认进度显示；设置为NONE时需应用自行处理进度， 此时progressListener和progressSignal参数才有效。

**类型：** ProgressIndicator

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-GetDataParams-progressIndicator: ProgressIndicator--><!--Device-GetDataParams-progressIndicator: ProgressIndicator-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

## progressListener

```TypeScript
progressListener?: ProgressListener
```

定义进度数据变化的订阅函数，用于获取粘贴过程的进度。仅当progressIndicator设置为NONE时此参数才生效，可设置该项自行处理进度显示； 当progressIndicator设置为DEFAULT时此参数无效。默认为空（不监听进度）。

**类型：** ProgressListener

**默认值：** -

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-GetDataParams-progressListener?: ProgressListener--><!--Device-GetDataParams-progressListener?: ProgressListener-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

## progressSignal

```TypeScript
progressSignal?: ProgressSignal
```

定义进度取消的函数，在粘贴过程中可选择取消任务，且仅当进度指示选项[ProgressIndicator](arkts-basicservices-pasteboard-progressindicator-e.md#ProgressIndicator)设置为NONE时此参数才有意义，默认为空。

**类型：** [ProgressSignal](arkts-basicservices-pasteboard-progresssignal-c.md)

**默认值：** -

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-GetDataParams-progressSignal?: ProgressSignal--><!--Device-GetDataParams-progressSignal?: ProgressSignal-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

