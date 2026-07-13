# @ohos.scan

该模块为扫描框架的js-api接口文档，提供发现和连接扫描仪的能力。

> **说明：**
> > 当前界面仅包含本模块的公开接口。

**起始版本：** 20

**系统能力：** SystemCapability.Print.PrintFramework

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [cancelScan](arkts-basicservices-cancelscan-f.md#cancelscan-1) | 取消扫描。使用Promise异步回调。 |
| [closeScanner](arkts-basicservices-closescanner-f.md#closescanner-1) | 关闭扫描仪。使用Promise异步回调。 |
| [exit](arkts-basicservices-exit-f.md#exit-1) | 退出扫描服务。使用Promise异步回调。 |
| [getPictureScanProgress](arkts-basicservices-getpicturescanprogress-f.md#getpicturescanprogress-1) | 获取图片扫描进度。使用Promise异步回调。 |
| [getScannerCurrentSetting](arkts-basicservices-getscannercurrentsetting-f.md#getscannercurrentsetting-1) | 获取当前扫描仪设置。使用Promise异步回调。 |
| [getScannerParameter](arkts-basicservices-getscannerparameter-f.md#getscannerparameter-1) | 获取扫描仪参数。使用Promise异步回调。 |
| [init](arkts-basicservices-init-f.md#init-1) | 初始化扫描服务。使用Promise异步回调。 |
| [off](arkts-basicservices-off-f.md#off-1) | 取消注册扫描仪设备发现事件回调。使用callback异步回调。 |
| [off](arkts-basicservices-off-f.md#off-2) | 取消注册扫描仪设备同步事件回调。使用callback异步回调。 |
| [on](arkts-basicservices-on-f.md#on-1) | 注册扫描仪设备发现事件回调。使用callback异步回调。 |
| [on](arkts-basicservices-on-f.md#on-2) | 注册扫描仪设备同步事件回调。使用callback异步回调。 |
| [openScanner](arkts-basicservices-openscanner-f.md#openscanner-1) | 打开扫描仪。使用Promise异步回调。 |
| [setScanAutoOption](arkts-basicservices-setscanautooption-f.md#setscanautooption-1) | 设置扫描选项为自动模式。使用Promise异步回调。 |
| [setScannerParameter](arkts-basicservices-setscannerparameter-f.md#setscannerparameter-1) | 设置扫描仪参数。使用Promise异步回调。 |
| [startScan](arkts-basicservices-startscan-f.md#startscan-1) | 开始扫描。使用Promise异步回调。 |
| [startScannerDiscovery](arkts-basicservices-startscannerdiscovery-f.md#startscannerdiscovery-1) | 开始发现扫描仪。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [addScanner](arkts-basicservices-addscanner-f-sys.md#addscanner-1) | 添加扫描仪（系统API）。使用Promise异步回调。 |
| [deleteScanner](arkts-basicservices-deletescanner-f-sys.md#deletescanner-1) | 删除扫描仪（系统API）。使用Promise异步回调。 |
| [getAddedScanners](arkts-basicservices-getaddedscanners-f-sys.md#getaddedscanners-1) | 获取已添加的扫描仪（系统API）。使用Promise异步回调。 |
| [off](arkts-basicservices-off-f-sys.md#off-3) | 取消注册扫描仪设备添加事件回调（系统API）。使用callback异步回调。 |
| [off](arkts-basicservices-off-f-sys.md#off-4) | 取消注册扫描仪设备删除事件回调（系统API）。使用callback异步回调。 |
| [on](arkts-basicservices-on-f-sys.md#on-3) | 注册扫描仪设备添加事件回调（系统API）。使用callback异步回调。 |
| [on](arkts-basicservices-on-f-sys.md#on-4) | 注册扫描仪设备删除事件回调（系统API）。使用callback异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [PictureScanProgress](arkts-basicservices-picturescanprogress-i.md) | 定义图片扫描进度的接口。 |
| [Range](arkts-basicservices-range-i.md) | 定义范围的接口。 |
| [ScannerDevice](arkts-basicservices-scannerdevice-i.md) | 定义扫描仪设备的接口。 |
| [ScannerOptionValue](arkts-basicservices-scanneroptionvalue-i.md) | 定义扫描仪选项值的接口。 |
| [ScannerParameter](arkts-basicservices-scannerparameter-i.md) | 定义扫描仪参数的接口。 |
| [ScannerSyncDevice](arkts-basicservices-scannersyncdevice-i.md) | 定义扫描仪同步设备的接口。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ConstraintType](arkts-basicservices-constrainttype-e.md) | 定义参数限制类型的枚举。 |
| [OptionValueType](arkts-basicservices-optionvaluetype-e.md) | 定义选项值类型的枚举。 |
| [PhysicalUnit](arkts-basicservices-physicalunit-e.md) | 定义物理单位的枚举。 |
| [ScanErrorCode](arkts-basicservices-scanerrorcode-e.md) | 定义扫描错误码的枚举。 |
| [ScannerDiscoveryMode](arkts-basicservices-scannerdiscoverymode-e.md) | 定义扫描仪发现方式的枚举。 |
| [ScannerSyncMode](arkts-basicservices-scannersyncmode-e.md) | 定义扫描仪同步码的枚举。 |

