# @ohos.boardInfo

本模块提供板级硬件信息查询能力，支持获取CPU、主板、BIOS等硬件信息，适用于设备识别、资产管理、兼容性判断等场景。开发者不可配置这些信息。

> **说明：** 
> 
> 本模块首批接口从API version 26.0.1开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> 本模块接口在执行期间会拉起临时进程，当系统负载较高时，可能引发阻塞风险。
> 为确保应用主线程的响应性能，建议避免在主线程中调用。硬件信息因设备而异且固定不变，
> 可在首次获取后缓存在本地，避免每次使用时重复获取，以提升性能。

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
