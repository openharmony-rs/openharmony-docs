# @ohos.boardInfo

boardInfo模块用于查询硬件设备信息。

> **说明：** 
> 
> 本模块首批接口从API version 26开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> 本模块接口返回设备常量信息，建议应用只调用一次，不需要频繁调用。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace boardInfo--><!--Device-unnamed-declare namespace boardInfo-End-->

**系统能力：** SystemCapability.Startup.BoardInfo

## 导入模块

```TypeScript
import { boardInfo } from '@kit.BasicServicesKit';
```

## 汇总

### 常量

| 名称 | 说明 |
| --- | --- |
| [biosDate](arkts-basicservices-boardinfo-con.md#biosdate) | BIOS发布日期。 |
| [biosVendor](arkts-basicservices-boardinfo-con.md#biosvendor) | BIOS厂商。 |
| [biosVersion](arkts-basicservices-boardinfo-con.md#biosversion) | BIOS版本。 |
| [boardName](arkts-basicservices-boardinfo-con.md#boardname) | 主板产品名称。 |
| [boardSn](arkts-basicservices-boardinfo-con.md#boardsn) | 主板序列号。 |
| [boardVendor](arkts-basicservices-boardinfo-con.md#boardvendor) | 主板厂商。 |
| [cpuArch](arkts-basicservices-boardinfo-con.md#cpuarch) | CPU架构。 |
| [cpuId](arkts-basicservices-boardinfo-con.md#cpuid) | CPU ID。 |
| [cpuVendor](arkts-basicservices-boardinfo-con.md#cpuvendor) | CPU厂商信息。 |
