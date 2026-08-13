# @ohos.scan

该模块为扫描框架的js-api接口文档，提供发现和连接扫描仪的能力。 > **说明：** > > 当前界面仅包含本模块的公开接口。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace scan--><!--Device-unnamed-declare namespace scan-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [cancelScan](arkts-basicservices-scan-cancelscan-f.md#cancelScan) | 取消扫描。使用Promise异步回调。 |
| [closeScanner](arkts-basicservices-scan-closescanner-f.md#closeScanner) | 关闭扫描仪。使用Promise异步回调。 |
| [exit](arkts-basicservices-scan-exit-f.md#exit) | 退出扫描服务。使用Promise异步回调。 |
| [getPictureScanProgress](arkts-basicservices-scan-getpicturescanprogress-f.md#getPictureScanProgress) | 获取图片扫描进度。使用Promise异步回调。 |
| [getScannerCurrentSetting](arkts-basicservices-scan-getscannercurrentsetting-f.md#getScannerCurrentSetting) | 获取当前扫描仪设置。使用Promise异步回调。 |
| [getScannerParameter](arkts-basicservices-scan-getscannerparameter-f.md#getScannerParameter) | 获取扫描仪参数。使用Promise异步回调。 |
| [init](arkts-basicservices-scan-init-f.md#init) | 初始化扫描服务。使用Promise异步回调。 |
| [offScanDeviceFound](arkts-basicservices-scan-offscandevicefound-f.md#offScanDeviceFound) | Unregister event callback for scanner device found. |
| [offScanDeviceSync](arkts-basicservices-scan-offscandevicesync-f.md#offScanDeviceSync) | Unregister event callback for scanner device sync. |
| off_scanDeviceFound | 取消注册扫描仪设备发现事件回调。使用callback异步回调。 |
| off_scanDeviceSync | 取消注册扫描仪设备同步事件回调。使用callback异步回调。 |
| [onScanDeviceFound](arkts-basicservices-scan-onscandevicefound-f.md#onScanDeviceFound) | Register event callback for scanner device found. |
| [onScanDeviceSync](arkts-basicservices-scan-onscandevicesync-f.md#onScanDeviceSync) | Register event callback for scanner device sync. |
| on_scanDeviceFound | 注册扫描仪设备发现事件回调。使用callback异步回调。 |
| on_scanDeviceSync | 注册扫描仪设备同步事件回调。使用callback异步回调。 |
| [openScanner](arkts-basicservices-scan-openscanner-f.md#openScanner) | 打开扫描仪。使用Promise异步回调。 |
| [setScanAutoOption](arkts-basicservices-scan-setscanautooption-f.md#setScanAutoOption) | 设置扫描选项为自动模式。使用Promise异步回调。 |
| [setScannerParameter](arkts-basicservices-scan-setscannerparameter-f.md#setScannerParameter) | 设置扫描仪参数。使用Promise异步回调。 |
| [startScan](arkts-basicservices-scan-startscan-f.md#startScan) | 开始扫描。使用Promise异步回调。 |
| [startScannerDiscovery](arkts-basicservices-scan-startscannerdiscovery-f.md#startScannerDiscovery) | 开始发现扫描仪。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [addScanner](arkts-basicservices-scan-addscanner-f-sys.md#addScanner) | 添加扫描仪（系统API）。使用Promise异步回调。 |
| [deleteScanner](arkts-basicservices-scan-deletescanner-f-sys.md#deleteScanner) | 删除扫描仪（系统API）。使用Promise异步回调。 |
| [getAddedScanners](arkts-basicservices-scan-getaddedscanners-f-sys.md#getAddedScanners) | 获取已添加的扫描仪（系统API）。使用Promise异步回调。 |
| [offScanDeviceAdd](arkts-basicservices-scan-offscandeviceadd-f-sys.md#offScanDeviceAdd) | Unregister event callback for scanner device add (system API). |
| [offScanDeviceDel](arkts-basicservices-scan-offscandevicedel-f-sys.md#offScanDeviceDel) | Unregister event callback for scanner device delete (system API). |
| off_scanDeviceAdd | 取消注册扫描仪设备添加事件回调（系统API）。使用callback异步回调。 |
| off_scanDeviceDel | 取消注册扫描仪设备删除事件回调（系统API）。使用callback异步回调。 |
| [onScanDeviceAdd](arkts-basicservices-scan-onscandeviceadd-f-sys.md#onScanDeviceAdd) | Register event callback for scanner device add (system API). |
| [onScanDeviceDel](arkts-basicservices-scan-onscandevicedel-f-sys.md#onScanDeviceDel) | Register event callback for scanner device delete (system API). |
| on_scanDeviceAdd | 注册扫描仪设备添加事件回调（系统API）。使用callback异步回调。 |
| on_scanDeviceDel | 注册扫描仪设备删除事件回调（系统API）。使用callback异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [PictureScanProgress](arkts-basicservices-scan-picturescanprogress-i.md) | 定义图片扫描进度的接口。 |
| [Range](arkts-basicservices-scan-range-i.md) | 定义范围的接口。 |
| [ScannerDevice](arkts-basicservices-scan-scannerdevice-i.md) | 定义扫描仪设备的接口。 |
| [ScannerOptionValue](arkts-basicservices-scan-scanneroptionvalue-i.md) | 定义扫描仪选项值的接口。 |
| [ScannerParameter](arkts-basicservices-scan-scannerparameter-i.md) | 定义扫描仪参数的接口。 |
| [ScannerSyncDevice](arkts-basicservices-scan-scannersyncdevice-i.md) | 定义扫描仪同步设备的接口。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ConstraintType](arkts-basicservices-scan-constrainttype-e.md) | 定义参数限制类型的枚举。 |
| [OptionValueType](arkts-basicservices-scan-optionvaluetype-e.md) | 定义选项值类型的枚举。 |
| [PhysicalUnit](arkts-basicservices-scan-physicalunit-e.md) | 定义物理单位的枚举。 |
| [ScanErrorCode](arkts-basicservices-scan-scanerrorcode-e.md) | 定义扫描错误码的枚举。 |
| [ScannerDiscoveryMode](arkts-basicservices-scan-scannerdiscoverymode-e.md) | 定义扫描仪发现方式的枚举。 |
| [ScannerSyncMode](arkts-basicservices-scan-scannersyncmode-e.md) | 定义扫描仪同步码的枚举。 |

