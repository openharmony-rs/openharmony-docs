# @ohos.nearlink.scan

提供扫描和发现附近设备的方法。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Communication.NearLink.Base

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [offDeviceFound](arkts-connectivity-offdevicefound-f.md#offdevicefound-1) | 取消订阅星闪扫描结果。 |
| [onDeviceFound](arkts-connectivity-ondevicefound-f.md#ondevicefound-1) | 订阅NearLink扫描结果。只有授予了ohos.permission.NEARLINK_ACCESS权限的应用程序才能访问此事件。如果应用被赋予了ohos.permission.GET_NEARLINK_PEER_MAC权限。回调返回真实设备地址，否则返回随机设备地址。 |
| [startScan](arkts-connectivity-startscan-f.md#startscan-1) | 开始使用过滤器扫描指定的NearLink设备。如果不想使用过滤器，可以将过滤器参数设置为{@code null}。 |
| [stopScan](arkts-connectivity-stopscan-f.md#stopscan-1) | 停止扫描。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ScanFilters](arkts-connectivity-scanfilters-i.md) | 扫描过滤器。 |
| [ScanOptions](arkts-connectivity-scanoptions-i.md) | 扫描参数。 |
| [ScanResults](arkts-connectivity-scanresults-i.md) | 扫描结果的内容。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ScanMode](arkts-connectivity-scanmode-e.md) | 扫描模式的枚举。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ScanMode](arkts-connectivity-scanmode-e-sys.md) | 扫描模式的枚举。 |
<!--DelEnd-->

