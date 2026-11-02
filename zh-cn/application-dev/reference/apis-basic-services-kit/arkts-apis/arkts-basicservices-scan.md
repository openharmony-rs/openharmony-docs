# @ohos.scan(扫描)

该模块提供扫描框架的JS API，支持扫描仪的发现与管理、扫描执行、设备事件监听等能力，适用于应用需要集成扫描仪进行文档数字化采集与设备管理的场景。

> **说明：** 
> 
> 当前界面仅包含本模块的公开接口。

**起始版本：** 20

<!--Device-unnamed-declare namespace scan--><!--Device-unnamed-declare namespace scan-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## 导入模块

```TypeScript
import { scan } from '@kit.BasicServicesKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [cancelScan](arkts-basicservices-scan-cancelscan-f.md#cancelscan-1) | 取消扫描。使用Promise异步回调。必须在开始扫描之后才能调用此方法。 |
| [closeScanner](arkts-basicservices-scan-closescanner-f.md#closescanner-1) | 关闭扫描仪。使用Promise异步回调。扫描仪关闭后，将不能再对该扫描仪执行参数获取、设置、扫描等操作。如需再次使用需重新调用openScanner()。 |
| [exit](arkts-basicservices-scan-exit-f.md#exit-1) | 退出扫描服务。使用Promise异步回调。扫描服务退出后，其它扫描方法将不可用，如需再次使用需重新调用init()。 |
| [getPictureScanProgress](arkts-basicservices-scan-getpicturescanprogress-f.md#getpicturescanprogress-1) | 获取图片扫描进度。使用Promise异步回调。必须在开始扫描之后才能调用此方法。 |
| [getScannerCurrentSetting](arkts-basicservices-scan-getscannercurrentsetting-f.md#getscannercurrentsetting-1) | 获取当前扫描仪设置。使用Promise异步回调。必须在调用openScanner()打开扫描仪之后才能调用此方法。 |
| [getScannerParameter](arkts-basicservices-scan-getscannerparameter-f.md#getscannerparameter-1) | 获取扫描仪参数。使用Promise异步回调。必须在调用openScanner()打开扫描仪之后才能调用此方法。应用可通过此方法获取参数索引（optionIndex），用于setScannerParameter、setScanAutoOption和getScannerCurrentSetting等方法的调用。 |
| [init](arkts-basicservices-scan-init-f.md#init-1) | 初始化扫描服务，必须在调用其它扫描接口前完成初始化。使用Promise异步回调。使用完毕后需调用exit()退出扫描服务，释放资源。 |
| [off('scanDeviceFound')](arkts-basicservices-scan-off-f.md#offscandevicefound) | 取消注册扫描仪设备发现事件回调。 |
| [off('scanDeviceSync')](arkts-basicservices-scan-off-f.md#offscandevicesync) | 取消注册扫描仪设备同步事件回调。 |
| [on('scanDeviceFound')](arkts-basicservices-scan-on-f.md#onscandevicefound) | 注册扫描仪设备发现事件回调，当调用startScannerDiscovery发现新的扫描仪设备时会触发此事件。使用callback异步回调。 |
| [on('scanDeviceSync')](arkts-basicservices-scan-on-f.md#onscandevicesync) | 注册扫描仪设备同步事件回调，当扫描仪设备状态发生变化（如扫描仪设备ID变更或掉线）时会触发此事件，通知应用同步维护扫描仪列表。使用callback异步回调。适用于应用需要持续跟踪扫描仪设备状态变化的场景，如扫描仪重新连接时更新本地设备信息。 |
| [openScanner](arkts-basicservices-scan-openscanner-f.md#openscanner-1) | 打开扫描仪。需在调用init()完成初始化后使用。使用Promise异步回调。在使用完毕后，需调用closeScanner()关闭扫描仪，释放资源。 |
| [setScanAutoOption](arkts-basicservices-scan-setscanautooption-f.md#setscanautooption-1) | 设置扫描选项为自动模式，由扫描仪自动确定该选项的取值。使用Promise异步回调。必须在调用openScanner()打开扫描仪之后才能调用此方法。 |
| [setScannerParameter](arkts-basicservices-scan-setscannerparameter-f.md#setscannerparameter-1) | 设置扫描仪参数。使用Promise异步回调。必须在调用openScanner()打开扫描仪之后才能调用此方法。 |
| [startScan](arkts-basicservices-scan-startscan-f.md#startscan-1) | 开始扫描。使用Promise异步回调。必须在调用openScanner()打开扫描仪之后才能调用此方法。扫描过程中可通过getPictureScanProgress()获取扫描进度；需要取消扫描时，可调用cancelScan()。 |
| [startScannerDiscovery](arkts-basicservices-scan-startscannerdiscovery-f.md#startscannerdiscovery-1) | 开始发现扫描仪，发现的扫描仪设备信息通过on('scanDeviceFound')事件回调通知。需在调用init()完成初始化后使用。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [addScanner](arkts-basicservices-scan-addscanner-f-sys.md#addscanner-1) | 添加扫描仪（系统接口）。根据指定的发现模式发现并添加扫描仪设备，添加成功后将触发scanDeviceAdd事件通知，可通过on('scanDeviceAdd')监听设备添加事件。使用Promise异步回调。 |
| [deleteScanner](arkts-basicservices-scan-deletescanner-f-sys.md#deletescanner-1) | 删除扫描仪（系统接口）。适用于扫描仪设备离线或不再需要时移除设备的场景，删除成功后将触发scanDeviceDel事件通知，可通过on('scanDeviceDel')监听设备删除事件。使用Promise异步回调。 |
| [getAddedScanners](arkts-basicservices-scan-getaddedscanners-f-sys.md#getaddedscanners-1) | 获取已添加的扫描仪（系统接口）。适用于需要查询当前可用扫描仪列表以供用户选择设备的场景。使用Promise异步回调。 |
| [off('scanDeviceAdd')](arkts-basicservices-scan-off-f-sys.md#offscandeviceadd) | 取消注册扫描仪设备添加事件回调（系统接口）。 |
| [off('scanDeviceDel')](arkts-basicservices-scan-off-f-sys.md#offscandevicedel) | 取消注册扫描仪设备删除事件回调（系统接口）。 |
| [on('scanDeviceAdd')](arkts-basicservices-scan-on-f-sys.md#onscandeviceadd) | 注册扫描仪设备添加事件回调（系统接口）。当扫描仪设备被成功添加时触发此回调，返回添加的设备信息。使用callback异步回调。 |
| [on('scanDeviceDel')](arkts-basicservices-scan-on-f-sys.md#onscandevicedel) | 注册扫描仪设备删除事件回调（系统接口）。当扫描仪设备被删除时触发此回调，返回删除的设备信息。使用callback异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [PictureScanProgress](arkts-basicservices-scan-picturescanprogress-i.md) | 定义图片扫描进度的接口。 |
| [Range](arkts-basicservices-scan-range-i.md) | 定义范围的接口。 |
| [ScannerDevice](arkts-basicservices-scan-scannerdevice-i.md) | 定义扫描仪设备的接口。 |
| [ScannerOptionValue](arkts-basicservices-scan-scanneroptionvalue-i.md) | 定义扫描仪选项值的接口。当对应选项的约束类型为SCAN_CONSTRAINT_STRING_LIST时，选项取值应为optionConstraintString集合中的字符串。 |
| [ScannerParameter](arkts-basicservices-scan-scannerparameter-i.md) | 定义扫描仪参数的接口。 |
| [ScannerSyncDevice](arkts-basicservices-scan-scannersyncdevice-i.md) | 定义扫描仪同步设备的接口。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ConstraintType](arkts-basicservices-scan-constrainttype-e.md) | 定义参数约束类型的枚举。 |
| [OptionValueType](arkts-basicservices-scan-optionvaluetype-e.md) | 定义选项值类型的枚举。 |
| [PhysicalUnit](arkts-basicservices-scan-physicalunit-e.md) | 定义物理单位的枚举。 |
| [ScanErrorCode](arkts-basicservices-scan-scanerrorcode-e.md) | 定义扫描错误码的枚举。 |
| [ScannerDiscoveryMode](arkts-basicservices-scan-scannerdiscoverymode-e.md) | 定义扫描仪发现模式的枚举。 |
| [ScannerSyncMode](arkts-basicservices-scan-scannersyncmode-e.md) | 定义扫描仪同步模式的枚举。 |
