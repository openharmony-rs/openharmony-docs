# getAppRunningUniqueId

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## getAppRunningUniqueId

```TypeScript
function getAppRunningUniqueId(): string
```

获取应用程序的运行唯一标识符。

**起始版本：** 26.1.0

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回运行唯一标识ID字符串。失败时返回空字符串。 |
