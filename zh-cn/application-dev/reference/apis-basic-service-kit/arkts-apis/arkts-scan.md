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
| <!--DelRow-->[addScanner](arkts-basicservices-scan-addscanner-f-sys.md#addScanner-1) | 添加扫描仪（系统API）。使用Promise异步回调。<br/> |
| [cancelScan](arkts-basicservices-scan-cancelscan-f.md#cancelScan-1) | 取消扫描。使用Promise异步回调。<br/> |
| [closeScanner](arkts-basicservices-scan-closescanner-f.md#closeScanner-1) | 关闭扫描仪。使用Promise异步回调。<br/> |
| <!--DelRow-->[deleteScanner](arkts-basicservices-scan-deletescanner-f-sys.md#deleteScanner-1) | 删除扫描仪（系统API）。使用Promise异步回调。<br/> |
| [exit](arkts-basicservices-scan-exit-f.md#exit-1) | 退出扫描服务。使用Promise异步回调。<br/> |
| <!--DelRow-->[getAddedScanners](arkts-basicservices-scan-getaddedscanners-f-sys.md#getAddedScanners-1) | 获取已添加的扫描仪（系统API）。使用Promise异步回调。<br/> |
| [getPictureScanProgress](arkts-basicservices-scan-getpicturescanprogress-f.md#getPictureScanProgress-1) | 获取图片扫描进度。使用Promise异步回调。<br/> |
| [getScannerCurrentSetting](arkts-basicservices-scan-getscannercurrentsetting-f.md#getScannerCurrentSetting-1) | 获取当前扫描仪设置。使用Promise异步回调。<br/> |
| [getScannerParameter](arkts-basicservices-scan-getscannerparameter-f.md#getScannerParameter-1) | 获取扫描仪参数。使用Promise异步回调。<br/> |
| [init](arkts-basicservices-scan-init-f.md#init-1) | 初始化扫描服务。使用Promise异步回调。<br/> |
| [off](arkts-basicservices-scan-off-f.md#off-1) | 取消注册扫描仪设备发现事件回调。使用callback异步回调。<br/> |
| [off](arkts-basicservices-scan-off-f.md#off-2) | 取消注册扫描仪设备同步事件回调。使用callback异步回调。<br/> |
| <!--DelRow-->[off](arkts-basicservices-scan-off-f-sys.md#off-3) | 取消注册扫描仪设备添加事件回调（系统API）。使用callback异步回调。<br/> |
| <!--DelRow-->[off](arkts-basicservices-scan-off-f-sys.md#off-4) | 取消注册扫描仪设备删除事件回调（系统API）。使用callback异步回调。<br/> |
| [on](arkts-basicservices-scan-on-f.md#on-1) | 注册扫描仪设备发现事件回调。使用callback异步回调。<br/> |
| [on](arkts-basicservices-scan-on-f.md#on-2) | 注册扫描仪设备同步事件回调。使用callback异步回调。<br/> |
| <!--DelRow-->[on](arkts-basicservices-scan-on-f-sys.md#on-3) | 注册扫描仪设备添加事件回调（系统API）。使用callback异步回调。<br/> |
| <!--DelRow-->[on](arkts-basicservices-scan-on-f-sys.md#on-4) | 注册扫描仪设备删除事件回调（系统API）。使用callback异步回调。<br/> |
| [openScanner](arkts-basicservices-scan-openscanner-f.md#openScanner-1) | 打开扫描仪。使用Promise异步回调。<br/> |
| [setScanAutoOption](arkts-basicservices-scan-setscanautooption-f.md#setScanAutoOption-1) | 设置扫描选项为自动模式。使用Promise异步回调。<br/> |
| [setScannerParameter](arkts-basicservices-scan-setscannerparameter-f.md#setScannerParameter-1) | 设置扫描仪参数。使用Promise异步回调。<br/> |
| [startScan](arkts-basicservices-scan-startscan-f.md#startScan-1) | 开始扫描。使用Promise异步回调。<br/> |
| [startScannerDiscovery](arkts-basicservices-scan-startscannerdiscovery-f.md#startScannerDiscovery-1) | 开始发现扫描仪。使用Promise异步回调。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [PictureScanProgress](arkts-basicservices-scan-picturescanprogress-i.md) | 定义图片扫描进度的接口。<br/> |
| [Range](arkts-basicservices-scan-range-i.md) | 定义范围的接口。<br/> |
| [ScannerDevice](arkts-basicservices-scan-scannerdevice-i.md) | 定义扫描仪设备的接口。<br/> |
| [ScannerOptionValue](arkts-basicservices-scan-scanneroptionvalue-i.md) | 定义扫描仪选项值的接口。<br/> |
| [ScannerParameter](arkts-basicservices-scan-scannerparameter-i.md) | 定义扫描仪参数的接口。<br/> |
| [ScannerSyncDevice](arkts-basicservices-scan-scannersyncdevice-i.md) | 定义扫描仪同步设备的接口。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ConstraintType](arkts-basicservices-scan-constrainttype-e.md) | 定义参数限制类型的枚举。<br/> |
| [OptionValueType](arkts-basicservices-scan-optionvaluetype-e.md) | 定义选项值类型的枚举。<br/> |
| [PhysicalUnit](arkts-basicservices-scan-physicalunit-e.md) | 定义物理单位的枚举。<br/> |
| [ScanErrorCode](arkts-basicservices-scan-scanerrorcode-e.md) | 定义扫描错误码的枚举。<br/> |
| [ScannerDiscoveryMode](arkts-basicservices-scan-scannerdiscoverymode-e.md) | 定义扫描仪发现方式的枚举。<br/> |
| [ScannerSyncMode](arkts-basicservices-scan-scannersyncmode-e.md) | 定义扫描仪同步码的枚举。<br/> |

