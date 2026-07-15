# @ohos.nearlink.scan (星闪扫描能力)(系统接口)
<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @CCCZKing-->
<!--Designer: @lilong32; @CCCZKing-->
<!--Tester: @zhangjiaji111-->
<!--Adviser: @zhang_yixin13-->


本模块提供了星闪扫描相关功能。


**起始版本：** 26.0.0

> **说明：**
>
> 当前页面仅包含本模块的系统接口，其他公开接口参见[@ohos.nearlink.scan(星闪扫描能力)](js-apis-nearlink-scan.md)。

## 导入模块

```typescript
import { scan } from '@kit.ConnectivityKit';
```

## ScanMode

表示扫描模式，为枚举值。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

| 名称 | 值 | 说明 |
| -------- | -------- | -------- |
| SCAN_MODE_LOW_LATENCY | 2 | 表示高功率扫描模式，具有更高的扫描频率，功耗较高。 |
