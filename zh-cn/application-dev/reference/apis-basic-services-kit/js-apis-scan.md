# @ohos.scan (扫描)

<!--Kit: Basic Services Kit-->
<!--Subsystem: Print-->
<!--Owner: @guoshengbang-->
<!--Designer: @baozewei-->
<!--Tester:@baozewei-->
<!--Adviser: @fang-jinxu-->

该模块提供扫描框架的 JS API，支持扫描仪的发现与管理、扫描执行、设备事件监听等能力，适用于应用需要集成扫描仪进行文档数字化采集与设备管理的场景，可帮助开发者实现扫描相关功能。

> **说明：**
> 本模块首批接口从API version 20开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> 当前界面仅包含本模块的公开接口。

## 导入模块

```ts
import { scan } from '@kit.BasicServicesKit';
```

## ScanErrorCode

定义扫描错误码的枚举。

**系统能力：** SystemCapability.Print.PrintFramework

| **名称** | **值** | **说明** |
| -------- | ------ | -------- |
| SCAN_ERROR_NO_PERMISSION | 201 | 无权限，请根据对应接口的权限要求申请所需权限，并在配置文件中声明。 |
| SCAN_ERROR_NOT_SYSTEM_APPLICATION | 202 | 非系统应用，请检查应用类型是否为系统应用。 |
| SCAN_ERROR_INVALID_PARAMETER | 401 | 无效参数，请检查参数类型和取值范围。 |
| SCAN_ERROR_GENERIC_FAILURE | 13100001 | 通用失败，请检查扫描服务运行状态并重试。 |
| SCAN_ERROR_RPC_FAILURE | 13100002 | RPC失败，请检查RPC通信状态并重试。 |
| SCAN_ERROR_SERVER_FAILURE | 13100003 | 服务失败，请检查扫描服务是否正常运行并重试。 |
| SCAN_ERROR_UNSUPPORTED | 13100004 | 不支持的操作，请检查当前操作是否被扫描仪支持。 |
| SCAN_ERROR_CANCELED | 13100005 | 操作取消，请检查是否调用了cancelScan或操作被系统中断。 |
| SCAN_ERROR_DEVICE_BUSY | 13100006 | 设备忙，请等待设备空闲后重试。 |
| SCAN_ERROR_INVALID | 13100007 | 无效操作，请检查当前操作在扫描仪状态下是否有效。 |
| SCAN_ERROR_JAMMED | 13100008 | 卡纸，请清除扫描仪中的卡纸后重试。 |
| SCAN_ERROR_NO_DOCS | 13100009 | 缺纸，请在扫描仪中放入文档后重试。 |
| SCAN_ERROR_COVER_OPEN | 13100010 | 盖子打开，请关闭扫描仪盖子后重试。 |
| SCAN_ERROR_IO_ERROR | 13100011 | I/O错误，请检查设备I/O连接状态并重试。 |
| SCAN_ERROR_NO_MEMORY | 13100012 | 内存不足，请释放系统内存后重试。 |

## ConstraintType

定义参数约束类型的枚举。

**系统能力：** SystemCapability.Print.PrintFramework

| **名称** | **值** | **说明** |
| -------- | ------ | -------- |
| SCAN_CONSTRAINT_NONE | 0 | 无限制。 |
| SCAN_CONSTRAINT_RANGE | 1 | 范围限制。 |
| SCAN_CONSTRAINT_WORD_LIST | 2 | 数字列表。 |
| SCAN_CONSTRAINT_STRING_LIST | 3 | 字符串列表。 |

## PhysicalUnit

定义物理单位的枚举。

**系统能力：** SystemCapability.Print.PrintFramework

| **名称** | **值** | **说明** |
| -------- | ------ | -------- |
| SCAN_UNIT_NONE | 0 | 无单位。 |
| SCAN_UNIT_PIXEL | 1 | 像素单位。 |
| SCAN_UNIT_BIT | 2 | 位单位。 |
| SCAN_UNIT_MM | 3 | 毫米单位。 |
| SCAN_UNIT_DPI | 4 | DPI单位。 |
| SCAN_UNIT_PERCENT | 5 | 百分比单位。 |
| SCAN_UNIT_MICROSECOND | 6 | 微秒单位。 |

## OptionValueType

定义选项值类型的枚举。

**系统能力：** SystemCapability.Print.PrintFramework

| **名称** | **值** | **说明** |
| -------- | ------ | -------- |
| SCAN_TYPE_BOOL | 0 | 布尔类型。 |
| SCAN_TYPE_INT | 1 | 整数类型。 |
| SCAN_TYPE_FIXED | 2 | 定点数类型。 |
| SCAN_TYPE_STRING | 3 | 字符串类型。 |

## ScannerSyncMode

定义扫描仪同步模式的枚举。

**系统能力：** SystemCapability.Print.PrintFramework

| **名称** | **值** | **说明** |
| -------- | ------ | -------- |
| UPDATE_STR | 'update' | 更新模式，表示扫描仪ID的变化。 |
| DELETE_STR | 'delete' | 删除模式，表示扫描仪掉线。 |

## ScannerDiscoveryMode

定义扫描仪发现模式的枚举。

**系统能力：** SystemCapability.Print.PrintFramework

| **名称** | **值** | **说明** |
| -------- | ------ | -------- |
| TCP_STR | 'TCP' | 网络扫描仪的发现模式。 |
| USB_STR | 'USB' | USB扫描仪的发现模式。 |

## Range

定义范围的接口。

**系统能力：** SystemCapability.Print.PrintFramework

**属性：**
| **名称** | **类型** | **只读** | **可选** | **说明** |
| -------- | -------- | -------- | -------- | -------- |
| minValue | number | 否 | 否 | 范围的最小值。 |
| maxValue | number | 否 | 否 | 范围的最大值。 |
| quantValue | number | 否 | 否 | 范围的量化值，表示范围内有效值之间的步长。 |

## ScannerParameter

定义扫描仪参数的接口。

**系统能力：** SystemCapability.Print.PrintFramework

**属性：**
| **名称** | **类型** | **只读** | **可选** | **说明** |
| -------- | -------- | -------- | -------- | -------- |
| optionName | string | 否 | 否 | 选项名称。 |
| optionIndex | number | 否 | 否 | 选项索引。 |
| optionTitle | string | 否 | 否 | 选项标题。 |
| optionDesc | string | 否 | 否 | 选项描述。 |
| optionType | [OptionValueType](#optionvaluetype) | 否 | 否 | 选项值类型。 |
| optionUnit | [PhysicalUnit](#physicalunit) | 否 | 否 | 选项物理单位。 |
| optionConstraintType | [ConstraintType](#constrainttype) | 否 | 否 | 选项约束类型，决定有效的约束字段。当类型为SCAN_CONSTRAINT_NONE时无约束。 |
| optionConstraintString | string[] | 否 | 是 | 选项字符串约束，仅在optionConstraintType为SCAN_CONSTRAINT_STRING_LIST时有效。 |
| optionConstraintInt | number[] | 否 | 是 | 选项整数约束，仅在optionConstraintType为SCAN_CONSTRAINT_WORD_LIST时有效。 |
| optionConstraintRange | [Range](#range) | 否 | 是 | 选项范围约束，仅在optionConstraintType为SCAN_CONSTRAINT_RANGE时有效。 |

## ScannerOptionValue

定义扫描仪选项值的接口。

**系统能力：** SystemCapability.Print.PrintFramework

**属性：**
| **名称** | **类型** | **只读** | **可选** | **说明** |
| -------- | -------- | -------- | -------- | -------- |
| valueType | [OptionValueType](#optionvaluetype) | 否 | 否 | 值类型，决定应使用的值字段。 |
| numValue | number | 否 | 是 | 数值，仅在valueType为SCAN_TYPE_INT或SCAN_TYPE_FIXED时有效。 |
| strValue | string | 否 | 是 | 字符串值，仅在valueType为SCAN_TYPE_STRING时有效。 |
| boolValue | boolean | 否 | 是 | 布尔值，仅在valueType为SCAN_TYPE_BOOL时有效。 |

## PictureScanProgress

定义图片扫描进度的接口。

**系统能力：** SystemCapability.Print.PrintFramework

**属性：**
| **名称** | **类型** | **只读** | **可选** | **说明** |
| -------- | -------- | -------- | -------- | -------- |
| progress | number | 否 | 否 | 当前进度百分比，范围从0~100。单位：百分比。 |
| pictureFd | number | 否 | 否 | 扫描图片的文件描述符。 |
| isFinal | boolean | 否 | 否 | 是否是本次扫描的最后一张图片。true表示是最后一张图片，false表示不是最后一张图片。 |

## ScannerDevice

定义扫描仪设备的接口。

**系统能力：** SystemCapability.Print.PrintFramework

**属性：**
| **名称** | **类型** | **只读** | **可选** | **说明** |
| -------- | -------- | -------- | -------- | -------- |
| scannerId | string | 否 | 否 | 扫描仪的ID。 |
| discoveryMode | [ScannerDiscoveryMode](#scannerdiscoverymode) | 否 | 否 | 扫描仪的发现模式，用于指定发现扫描仪的方式。 |
| uniqueId | string | 否 | 否 | 扫描仪的唯一ID。 |
| manufacturer | string | 否 | 否 | 扫描仪的制造商。 |
| model | string | 否 | 否 | 扫描仪的型号。 |
| deviceName | string | 否 | 否 | 扫描仪的设备名称。 |

## ScannerSyncDevice

定义扫描仪同步设备的接口。

**系统能力：** SystemCapability.Print.PrintFramework

**属性：**
| **名称** | **类型** | **只读** | **可选** | **说明** |
| -------- | -------- | -------- | -------- | -------- |
| scannerId | string | 否 | 否 | 扫描仪的ID。 |
| discoveryMode | [ScannerDiscoveryMode](#scannerdiscoverymode) | 否 | 否 | 扫描仪的发现模式，用于指定发现扫描仪的方式。 |
| uniqueId | string | 否 | 否 | 扫描仪的唯一ID。 |
| syncMode | [ScannerSyncMode](#scannersyncmode) | 否 | 否 | 同步模式，决定oldScannerId是否有效：当syncMode为"update"时oldScannerId有效，为"delete"时oldScannerId无效。 |
| oldScannerId | string | 否 | 是 | 旧的扫描仪ID，仅在syncMode为"update"时有效，默认值为空字符串。 |

## scan.init

init(): Promise&lt;void&gt;

初始化扫描服务，必须在调用其它扫描接口前完成初始化。使用Promise异步回调。使用完毕后需调用exit()退出扫描服务，释放资源。

**需要权限：** ohos.permission.PRINT

**系统能力：** SystemCapability.Print.PrintFramework

**返回值：**
| **类型** | **说明** |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，初始化扫描服务成功时resolve，失败时reject。 |

**错误码：**

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denied. |

**示例：**

```ts
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

scan.init().then(() => {
    console.info('scan init success');
}).catch((error: BusinessError) => {
    console.error(`Failed to init scan. Code: ${error.code}, message: ${error.message}`);
});
```

## scan.exit

exit(): Promise&lt;void&gt;

退出扫描服务。使用Promise异步回调。扫描服务退出后，其它扫描方法将不可用，如需再次使用需重新调用init()。

**需要权限：** ohos.permission.PRINT

**系统能力：** SystemCapability.Print.PrintFramework

**返回值：**
| **类型** | **说明** |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，退出扫描服务成功时resolve，失败时reject。 |

**错误码：**

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denied. |

**示例：**

```ts
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

scan.exit().then(() => {
    console.info('scan exit success');
}).catch((error: BusinessError) => {
    console.error(`Failed to exit scan. Code: ${error.code}, message: ${error.message}`);
});
```

## scan.startScannerDiscovery

startScannerDiscovery(): Promise&lt;void&gt;

开始发现扫描仪，发现的扫描仪设备信息通过on('scanDeviceFound')事件回调通知。需在调用init()完成初始化后使用。使用Promise异步回调。

**需要权限：** ohos.permission.PRINT

**系统能力：** SystemCapability.Print.PrintFramework

**返回值：**
| **类型** | **说明** |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，开始发现扫描仪成功时resolve，失败时reject。 |

**错误码：**

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denied. |

**示例：**

```ts
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

scan.startScannerDiscovery().then(() => {
    console.info('start scanner discovery success');
}).catch((error: BusinessError) => {
    console.error(`Failed to start scanner discovery. Code: ${error.code}, message: ${error.message}`);
});
```

## scan.openScanner

openScanner(scannerId: string): Promise&lt;void&gt;

打开扫描仪。需在调用init()完成初始化后使用。使用Promise异步回调。在使用完毕后，需调用closeScanner()关闭扫描仪，释放资源。

**需要权限：** ohos.permission.PRINT

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**
| **参数名** | **类型** | **必填** | **说明** |
| -------- | -------- | -------- | -------- |
| scannerId | string | 是 | 要打开的扫描仪的ID，可以在startScannerDiscovery后通过scanDeviceFound回调获取。 |

**返回值：**
| **类型** | **说明** |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，打开扫描仪成功时resolve，失败时reject。 |

**错误码：**

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denied. |

**示例：**

```ts
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let scannerId: string = 'scanner_001';
scan.openScanner(scannerId).then(() => {
    console.info('open scanner success');
}).catch((error: BusinessError) => {
    console.error(`Failed to open scanner. Code: ${error.code}, message: ${error.message}`);
});
```

## scan.closeScanner

closeScanner(scannerId: string): Promise&lt;void&gt;

关闭扫描仪。使用Promise异步回调。扫描仪关闭后，将不能再对该扫描仪执行参数获取、设置、扫描等操作。如需再次使用需重新调用openScanner()。

**需要权限：** ohos.permission.PRINT

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**
| **参数名** | **类型** | **必填** | **说明** |
| -------- | -------- | -------- | -------- |
| scannerId | string | 是 | 要关闭的扫描仪的ID，可以在startScannerDiscovery后通过scanDeviceFound回调获取。 |

**返回值：**
| **类型** | **说明** |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，关闭扫描仪成功时resolve，失败时reject。 |

**错误码：**

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denied. |

**示例：**

```ts
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let scannerId: string = 'scanner_001';
scan.closeScanner(scannerId).then(() => {
    console.info('close scanner success');
}).catch((error: BusinessError) => {
    console.error(`Failed to close scanner. Code: ${error.code}, message: ${error.message}`);
});
```

## scan.getScannerParameter

getScannerParameter(scannerId: string): Promise&lt;ScannerParameter[]&gt;

获取扫描仪参数。使用Promise异步回调。必须在调用openScanner()打开扫描仪之后才能调用此方法。应用可通过此方法获取参数索引（optionIndex），用于其它扫描方法的调用。

**需要权限：** ohos.permission.PRINT

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**
| **参数名** | **类型** | **必填** | **说明** |
| -------- | -------- | -------- | -------- |
| scannerId | string | 是 | 扫描仪的ID，可以在startScannerDiscovery后通过scanDeviceFound回调获取。 |

**返回值：**
| **类型** | **说明** |
| -------- | -------- |
| Promise&lt;[ScannerParameter](#scannerparameter)[]&gt; | Promise对象，获取扫描仪参数成功时resolve并返回扫描仪参数数组，失败时reject。 |

**错误码：**

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denied. |

**示例：**

```ts
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let scannerId: string = 'scanner_001';
scan.getScannerParameter(scannerId).then((parameters: scan.ScannerParameter[]) => {
    console.info('get scanner parameters success: ' + JSON.stringify(parameters));
}).catch((error: BusinessError) => {
    console.error(`Failed to get scanner parameters. Code: ${error.code}, message: ${error.message}`);
});
```

## scan.setScannerParameter

setScannerParameter(scannerId: string, optionIndex: number, value: ScannerOptionValue): Promise&lt;void&gt;

设置扫描仪参数。使用Promise异步回调。必须在调用openScanner()打开扫描仪之后才能调用此方法。

**需要权限：** ohos.permission.PRINT

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**
| **参数名** | **类型** | **必填** | **说明** |
| -------- | -------- | -------- | -------- |
| scannerId | string | 是 | 要设置参数的扫描仪的ID，可以在startScannerDiscovery后通过scanDeviceFound回调获取。 |
| optionIndex | number | 是 | 要设置的选项的索引，可通过getScannerParameter()获取。 |
| value | [ScannerOptionValue](#scanneroptionvalue) | 是 | 要设置的扫描仪选项值，包含值类型（valueType）及对应的数值（numValue）、字符串值（strValue）或布尔值（boolValue）。 |

**返回值：**
| **类型** | **说明** |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，设置扫描仪参数成功时resolve，失败时reject。 |

**错误码：**

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denied. |

**示例：**

```ts
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let scannerId: string = 'scanner_001';
let optionIndex: number = 1;
let value: scan.ScannerOptionValue = {
    valueType: scan.OptionValueType.SCAN_TYPE_INT,
    numValue: 100
};
scan.setScannerParameter(scannerId, optionIndex, value).then(() => {
    console.info('set scanner parameter success');
}).catch((error: BusinessError) => {
    console.error(`Failed to set scanner parameter. Code: ${error.code}, message: ${error.message}`);
});
```

## scan.setScanAutoOption

setScanAutoOption(scannerId: string, optionIndex: number): Promise&lt;void&gt;

设置扫描选项为自动模式，由扫描仪自动确定该选项的取值。使用Promise异步回调。必须在调用openScanner()打开扫描仪之后才能调用此方法。

**需要权限：** ohos.permission.PRINT

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**
| **参数名** | **类型** | **必填** | **说明** |
| -------- | -------- | -------- | -------- |
| scannerId | string | 是 | 扫描仪的ID，可以在startScannerDiscovery后通过scanDeviceFound回调获取。 |
| optionIndex | number | 是 | 要设置为自动的选项的索引，可通过getScannerParameter()获取。 |

**返回值：**
| **类型** | **说明** |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，设置扫描选项为自动模式成功时resolve，失败时reject。 |

**错误码：**

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denied. |

**示例：**

```ts
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let scannerId: string = 'scanner_001';
let optionIndex: number = 1;
scan.setScanAutoOption(scannerId, optionIndex).then(() => {
    console.info('set scan auto option success');
}).catch((error: BusinessError) => {
    console.error(`Failed to set scan auto option. Code: ${error.code}, message: ${error.message}`);
});
```

## scan.getScannerCurrentSetting

getScannerCurrentSetting(scannerId: string, optionIndex: number): Promise&lt;ScannerOptionValue&gt;

获取当前扫描仪设置。使用Promise异步回调。必须在调用openScanner()打开扫描仪之后才能调用此方法。

**需要权限：** ohos.permission.PRINT

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**
| **参数名** | **类型** | **必填** | **说明** |
| -------- | -------- | -------- | -------- |
| scannerId | string | 是 | 要获取当前设置的扫描仪的ID，可以在startScannerDiscovery后通过scanDeviceFound回调获取。 |
| optionIndex | number | 是 | 要获取的选项的索引，可通过getScannerParameter()获取。 |

**返回值：**
| **类型** | **说明** |
| -------- | -------- |
| Promise&lt;[ScannerOptionValue](#scanneroptionvalue)&gt; | Promise对象，获取当前扫描仪设置成功时resolve并返回扫描仪选项值，失败时reject。 |

**错误码：**

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denied. |

**示例：**

```ts
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let scannerId: string = 'scanner_001';
let optionIndex: number = 1;
scan.getScannerCurrentSetting(scannerId, optionIndex).then((value: scan.ScannerOptionValue) => {
    console.info('get scanner current setting success: ' + JSON.stringify(value));
}).catch((error: BusinessError) => {
    console.error(`Failed to get scanner current setting. Code: ${error.code}, message: ${error.message}`);
});
```

## scan.startScan

startScan(scannerId: string, batchMode: boolean): Promise&lt;void&gt;

开始扫描。使用Promise异步回调。必须在调用openScanner()打开扫描仪之后才能调用此方法。扫描过程中可通过getPictureScanProgress()获取扫描进度；需要取消扫描时，可调用cancelScan()。

**需要权限：** ohos.permission.PRINT

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**
| **参数名** | **类型** | **必填** | **说明** |
| -------- | -------- | -------- | -------- |
| scannerId | string | 是 | 扫描仪的ID，可以在startScannerDiscovery后通过scanDeviceFound回调获取。 |
| batchMode | boolean | 是 | 是否使用批处理模式。true表示使用批处理模式，可连续扫描多页文档；false表示不使用批处理模式，仅扫描单页。 |

**返回值：**
| **类型** | **说明** |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，开始扫描成功时resolve，失败时reject。 |

**错误码：**

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denied. |

**示例：**

```ts
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let scannerId: string = 'scanner_001';
let batchMode: boolean = true;
scan.startScan(scannerId, batchMode).then(() => {
    console.info('start scan success');
}).catch((error: BusinessError) => {
    console.error(`Failed to start scan. Code: ${error.code}, message: ${error.message}`);
});
```

## scan.cancelScan

cancelScan(scannerId: string): Promise&lt;void&gt;

取消扫描。使用Promise异步回调。必须在开始扫描之后才能调用此方法。

**需要权限：** ohos.permission.PRINT

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**
| **参数名** | **类型** | **必填** | **说明** |
| -------- | -------- | -------- | -------- |
| scannerId | string | 是 | 扫描仪的ID，可以在startScannerDiscovery后通过scanDeviceFound回调获取。 |

**返回值：**
| **类型** | **说明** |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，取消扫描成功时resolve，失败时reject。 |

**错误码：**

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denied. |

**示例：**

```ts
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let scannerId: string = 'scanner_001';
scan.cancelScan(scannerId).then(() => {
    console.info('cancel scan success');
}).catch((error: BusinessError) => {
    console.error(`Failed to cancel scan. Code: ${error.code}, message: ${error.message}`);
});
```

## scan.getPictureScanProgress

getPictureScanProgress(scannerId: string): Promise&lt;PictureScanProgress&gt;

获取图片扫描进度。使用Promise异步回调。必须在开始扫描后才能调用此方法。

**需要权限：** ohos.permission.PRINT

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**
| **参数名** | **类型** | **必填** | **说明** |
| -------- | -------- | -------- | -------- |
| scannerId | string | 是 | 扫描仪的ID，可以在startScannerDiscovery后通过scanDeviceFound回调获取。 |

**返回值：**
| **类型** | **说明** |
| -------- | -------- |
| Promise&lt;[PictureScanProgress](#picturescanprogress)&gt; | Promise对象，获取图片扫描进度成功时resolve并返回图片扫描进度信息，失败时reject。 |

**错误码：**

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denied. |

**示例：**

```ts
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let scannerId: string = 'scanner_001';
scan.getPictureScanProgress(scannerId).then((progress: scan.PictureScanProgress) => {
    console.info('get picture scan progress success: ' + JSON.stringify(progress));
}).catch((error: BusinessError) => {
    console.error(`Failed to get picture scan progress. Code: ${error.code}, message: ${error.message}`);
});
```

## scan.on

on(type: 'scanDeviceFound', callback: Callback&lt;ScannerDevice&gt;): void

注册扫描仪设备发现事件回调，当调用startScannerDiscovery发现新的扫描仪设备时会触发此事件。使用callback异步回调。

**需要权限：** ohos.permission.PRINT

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**
| **参数名** | **类型** | **必填** | **说明** |
| -------- | -------- | -------- | -------- |
| type | 'scanDeviceFound' | 是 | 事件类型。 |
| callback | Callback&lt;[ScannerDevice](#scannerdevice)&gt; | 是 | 回调函数，返回扫描仪设备发现信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denied. |

**示例：**

```ts
import { scan } from '@kit.BasicServicesKit';

scan.on('scanDeviceFound', (device: scan.ScannerDevice) => {
    console.info('scan device found: ' + JSON.stringify(device));
});
```

## scan.off

off(type: 'scanDeviceFound', callback?: Callback&lt;ScannerDevice&gt;): void

取消注册扫描仪设备发现事件回调。

**需要权限：** ohos.permission.PRINT

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**
| **参数名** | **类型** | **必填** | **说明** |
| -------- | -------- | -------- | -------- |
| type | 'scanDeviceFound' | 是 | 事件类型。 |
| callback | Callback&lt;[ScannerDevice](#scannerdevice)&gt; | 否 | 需要取消注册的回调函数。若不传入，则取消调用方所有已注册的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denied. |

**示例：**

```ts
import { scan } from '@kit.BasicServicesKit';

let callback = (device: scan.ScannerDevice) => {
    console.info('scan device found: ' + JSON.stringify(device));
};
scan.on('scanDeviceFound', callback);
// 取消注册
scan.off('scanDeviceFound', callback);
```

## scan.on

on(type: 'scanDeviceSync', callback: Callback&lt;ScannerSyncDevice&gt;): void

注册扫描仪设备同步事件回调，当扫描仪设备状态发生变化（如扫描仪设备ID变更或掉线）时会触发此事件，通知应用同步维护扫描仪列表。使用callback异步回调。适用于应用需要持续跟踪扫描仪设备状态变化的场景，如扫描仪重新连接时更新本地设备信息。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**
| **参数名** | **类型** | **必填** | **说明** |
| -------- | -------- | -------- | -------- |
| type | 'scanDeviceSync' | 是 | 事件类型。 |
| callback | Callback&lt;[ScannerSyncDevice](#scannersyncdevice)&gt; | 是 | 回调函数，返回扫描仪设备同步信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denied. |

**示例：**

```ts
import { scan } from '@kit.BasicServicesKit';

scan.on('scanDeviceSync', (device: scan.ScannerSyncDevice) => {
    console.info('scan device sync: ' + JSON.stringify(device));
});
```

## scan.off

off(type: 'scanDeviceSync', callback?: Callback&lt;ScannerSyncDevice&gt;): void

取消注册扫描仪设备同步事件回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**
| **参数名** | **类型** | **必填** | **说明** |
| -------- | -------- | -------- | -------- |
| type | 'scanDeviceSync' | 是 | 事件类型。 |
| callback | Callback&lt;[ScannerSyncDevice](#scannersyncdevice)&gt; | 否 | 需要取消注册的回调函数。若不传入，则取消调用方所有已注册的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denied. |

**示例：**

```ts
import { scan } from '@kit.BasicServicesKit';

let callback = (device: scan.ScannerSyncDevice) => {
    console.info('scan device sync: ' + JSON.stringify(device));
};
scan.on('scanDeviceSync', callback);
// 取消注册
scan.off('scanDeviceSync', callback);
```
