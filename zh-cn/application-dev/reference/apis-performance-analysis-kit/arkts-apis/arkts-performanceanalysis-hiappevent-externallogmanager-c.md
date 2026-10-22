# ExternalLogManager

```TypeScript
class ExternalLogManager
```

定义外部日志管理者，用于外部日志管理

**起始版本：** 26.0.1

<!--Device-hiAppEvent-class ExternalLogManager--><!--Device-hiAppEvent-class ExternalLogManager-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## 导入模块

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## onCapacityReached

```TypeScript
onCapacityReached(container: ExternalLogContainer): void
```

当外部日志目录容量达到时调用此函数

**起始版本：** 26.0.1

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-ExternalLogManager-onCapacityReached(container: ExternalLogContainer): void--><!--Device-ExternalLogManager-onCapacityReached(container: ExternalLogContainer): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| container | [ExternalLogContainer](arkts-performanceanalysis-hiappevent-externallogcontainer-c.md) | 是 | 包含所有外部日志文件的容器 |
