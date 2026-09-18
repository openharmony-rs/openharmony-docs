# @ohos.nearlink.scan(星闪扫描能力)

本模块提供了星闪扫描模式的定义。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { scan } from '@kit.ConnectivityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [offDeviceFound](arkts-connectivity-scan-offdevicefound-f.md) | 取消订阅星闪扫描结果。使用callback异步回调。 |
| [onDeviceFound](arkts-connectivity-scan-ondevicefound-f.md) | 订阅星闪扫描结果。使用callback异步回调。 |
| [startScan](arkts-connectivity-scan-startscan-f.md) | 发起星闪扫描。使用Promise异步回调。需先调用[scan.onDeviceFound](arkts-connectivity-scan-ondevicefound-f.md)订阅扫描结果回调，本接口发起扫描后，扫描到的设备信息通过[scan.onDeviceFound](arkts-connectivity-scan-ondevicefound-f.md)回调上报。扫描完成后可调用[scan.stopScan](arkts-connectivity-scan-stopscan-f.md)停止扫描。 |
| [stopScan](arkts-connectivity-scan-stopscan-f.md) | 停止星闪扫描。使用Promise异步回调。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ScanFilters](arkts-connectivity-scan-scanfilters-i.md) | 表示扫描过滤条件。 |
| [ScanOptions](arkts-connectivity-scan-scanoptions-i.md) | 表示扫描选项。 |
| [ScanResults](arkts-connectivity-scan-scanresults-i.md) | 表示扫描结果。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ScanMode](arkts-connectivity-scan-scanmode-e.md) | 表示扫描模式，为枚举值。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ScanMode](arkts-connectivity-scan-scanmode-e-sys.md) | 表示扫描模式，为枚举值。 |
<!--DelEnd-->
