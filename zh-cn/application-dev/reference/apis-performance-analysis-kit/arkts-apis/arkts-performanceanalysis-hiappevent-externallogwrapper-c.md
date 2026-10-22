# ExternalLogWrapper

```TypeScript
class ExternalLogWrapper
```

外部日志的包装器，提供各种信息。

**起始版本：** 26.0.1

<!--Device-hiAppEvent-class ExternalLogWrapper--><!--Device-hiAppEvent-class ExternalLogWrapper-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## 导入模块

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## getFilePath

```TypeScript
getFilePath(): string
```

获取文件路径

**起始版本：** 26.0.1

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-ExternalLogWrapper-getFilePath(): string--><!--Device-ExternalLogWrapper-getFilePath(): string-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 文件路径 |

## getGenerationTime

```TypeScript
getGenerationTime(): number
```

获取文件的生成时间点（毫秒）

**起始版本：** 26.0.1

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-ExternalLogWrapper-getGenerationTime(): long--><!--Device-ExternalLogWrapper-getGenerationTime(): long-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 生成时间 |

## getSizeInKb

```TypeScript
getSizeInKb(): number
```

以kb为单位获取文件大小

**起始版本：** 26.0.1

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-ExternalLogWrapper-getSizeInKb(): long--><!--Device-ExternalLogWrapper-getSizeInKb(): long-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 文件大小，单位为kb |

## getSysEvent

```TypeScript
getSysEvent(): string
```

获取文件的系统事件

**起始版本：** 26.0.1

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-ExternalLogWrapper-getSysEvent(): string--><!--Device-ExternalLogWrapper-getSysEvent(): string-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 系统事件的字符串形式 |
