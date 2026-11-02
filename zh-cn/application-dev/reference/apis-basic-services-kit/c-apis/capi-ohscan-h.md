# ohscan.h

## 概述

声明用于发现和连接扫描仪、从扫描仪扫描图片、获取图片扫描进度和设置扫描仪参数等功能的API，适用于需要在应用内集成扫描仪相关操作的场景。

**引用文件：** <ohscan.h>

**库：** libohscan.so

**系统能力：** SystemCapability.Print.PrintFramework

**起始版本：** 12

**相关模块：** [OH_Scan](capi-basic-services-kit-oh-scan.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [Scan_ScannerDevice](capi-oh-scan-scan-scannerdevice.md) | Scan_ScannerDevice | Scan_ScannerDevice表示扫描仪设备信息，包含扫描仪ID、制造商、型号、发现模式和序列号等属性，用于在扫描仪发现流程中获取设备详情， 开发者可通过扫描仪发现相关接口获取该结构体以选择目标扫描仪设备进行扫描操作。相关模块设计逻辑请参见OH_Scan。 |
| [Scan_PictureScanProgress](capi-oh-scan-scan-picturescanprogress.md) | Scan_PictureScanProgress | 表示扫描仪扫描图片的进度。该结构体包含进度值（progress）、文件描述符（fd）及是否为最后扫描的图片（isFinal），适用于需要在应用中实时跟踪图片扫描状态、获取扫描结果文件的场景。详细实现机制请参见 OH_Scan。 |
| [Scan_ScannerOptions](capi-oh-scan-scan-scanneroptions.md) | Scan_ScannerOptions | 表示一个扫描仪的可设置参数选项，用于配置扫描仪的参数，支持配置选项标题、描述、可设置范围及选项数量。每个选项由一组标题（titles）、描述（descriptions）和可设置范围（ranges）组成， 三者以平行数组的形式存储，optionCount表示选项的总数量，开发者可通过索引i（需满足0 ≤ i < optionCount）同时访问titles[i]、descriptions[i] 和ranges[i] 来获取第i个选项的完整信息。需保证titles、descriptions、ranges三者的数组长度一致且等于optionCount，否则可能无法正确获取选项的完整信息。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [Scan_ErrorCode](#scan_errorcode) | Scan_ErrorCode | 定义错误码。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef void (\*Scan_ScannerDiscoveryCallback)(Scan_ScannerDevice** devices, int32_t deviceCount)](#scan_scannerdiscoverycallback) | Scan_ScannerDiscoveryCallback | 扫描仪设备发现回调，通过[OH_Scan_StartScannerDiscovery](capi-ohscan-h.md#oh_scan_startscannerdiscovery)注册。 |
| [int32_t OH_Scan_Init()](#oh_scan_init) | - | 此API检查并拉起扫描服务，初始化扫描客户端，并建立与扫描服务的连接。应先调用此API初始化扫描服务，再调用其他扫描API。在使用完毕后，需调用 [OH_Scan_Exit](capi-ohscan-h.md#oh_scan_exit) 释放资源。 |
| [int32_t OH_Scan_StartScannerDiscovery(Scan_ScannerDiscoveryCallback callback)](#oh_scan_startscannerdiscovery) | - | 此API开始发现扫描仪，注册回调函数处理发现的扫描仪设备。注册的回调将在调用 [OH_Scan_Exit](capi-ohscan-h.md#oh_scan_exit) 时注销。 |
| [int32_t OH_Scan_OpenScanner(const char* scannerId)](#oh_scan_openscanner) | - | 此API连接到扫描仪设备。设备使用完毕后，可调用 [OH_Scan_CloseScanner](capi-ohscan-h.md#oh_scan_closescanner) 关闭。 |
| [int32_t OH_Scan_CloseScanner(const char* scannerId)](#oh_scan_closescanner) | - | 此API用于关闭已连接的扫描仪设备。一般在扫描仪使用完毕后调用此API关闭连接。 |
| [Scan_ScannerOptions* OH_Scan_GetScannerParameter(const char* scannerId, int32_t* errorCode)](#oh_scan_getscannerparameter) | - | 此API可用于获取扫描仪可设置的选项列表。返回的结构体指针指向的内存会在[OH_Scan_Exit](capi-ohscan-h.md#oh_scan_exit)时自动释放，每个扫描仪型号在内存中只会存储一份副本。 |
| [int32_t OH_Scan_SetScannerParameter(const char* scannerId, const int32_t option, const char* value)](#oh_scan_setscannerparameter) | - | 此API可用于设置扫描仪的某个选项参数。传入的选项和值从[OH_Scan_GetScannerParameter](capi-ohscan-h.md#oh_scan_getscannerparameter)获取。 |
| [int32_t OH_Scan_StartScan(const char* scannerId, bool batchMode)](#oh_scan_startscan) | - | 此API用于启动扫描仪的扫描任务。成功初始化扫描服务，并连接扫描仪完成参数设置后，可以调用此API开始扫描。扫描过程中可调用 [OH_Scan_GetPictureScanProgress](capi-ohscan-h.md#oh_scan_getpicturescanprogress) 获取扫描进度， 可调用 [OH_Scan_CancelScan](capi-ohscan-h.md#oh_scan_cancelscan) 取消扫描。 |
| [int32_t OH_Scan_CancelScan(const char* scannerId)](#oh_scan_cancelscan) | - | 此API用于取消扫描仪正在进行的扫描任务。 |
| [int32_t OH_Scan_GetPictureScanProgress(const char* scannerId, Scan_PictureScanProgress* prog)](#oh_scan_getpicturescanprogress) | - | 此API可获取扫描仪扫描图片的进度。 |
| [int32_t OH_Scan_Exit()](#oh_scan_exit) | - | 此API可用于退出扫描服务，释放扫描框架内存，并注销扫描仪设备发现回调。扫描服务退出后，将无法再调用其他扫描API。 |

## 枚举类型说明

### Scan_ErrorCode

```c
enum Scan_ErrorCode
```

**描述：**

定义错误码。

**系统能力：** SystemCapability.Print.PrintFramework

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| SCAN_ERROR_NONE = 0 | 操作成功 |
| SCAN_ERROR_NO_PERMISSION = 201 | 权限验证失败，需申请接口所需权限 |
| SCAN_ERROR_INVALID_PARAMETER = 401 | 参数无效。例如指针为空或字符串为空，请检查传入的参数是否合法 |
| SCAN_ERROR_GENERIC_FAILURE = 24300101 | 通用内部错误，请稍后重试 |
| SCAN_ERROR_RPC_FAILURE = 24300102 | RPC通信错误，请检查扫描服务状态后重试 |
| SCAN_ERROR_SERVER_FAILURE = 24300103 | 表示扫描过程中发生错误，请稍后重试 |
| SCAN_ERROR_UNSUPPORTED = 24300104 | 不支持的操作，请检查当前扫描仪是否支持该操作 |
| SCAN_ERROR_CANCELED = 24300105 | 操作已取消，请重新发起扫描 |
| SCAN_ERROR_DEVICE_BUSY = 24300106 | 扫描仪繁忙，请稍后重试 |
| SCAN_ERROR_INVALID = 24300107 | 数据无效（包括打开时无设备），请检查扫描仪连接状态 |
| SCAN_ERROR_JAMMED = 24300108 | 文档进纸器卡纸，请清除卡纸后重试 |
| SCAN_ERROR_NO_DOCS = 24300109 | 文档进纸器缺纸，请在进纸器中放入文档后重试 |
| SCAN_ERROR_COVER_OPEN = 24300110 | 扫描仪盖板打开，请关闭盖板后重试 |
| SCAN_ERROR_IO_ERROR = 24300111 | 扫描仪I/O错误，请检查扫描仪连接并重试 |
| SCAN_ERROR_NO_MEMORY = 24300112 | 内存不足，请释放资源后重试 |


## 函数说明

### Scan_ScannerDiscoveryCallback()

```c
typedef void (*Scan_ScannerDiscoveryCallback)(Scan_ScannerDevice** devices, int32_t deviceCount)
```

**描述：**

扫描仪设备发现回调，通过[OH_Scan_StartScannerDiscovery](capi-ohscan-h.md#oh_scan_startscannerdiscovery)注册。

**系统能力：** SystemCapability.Print.PrintFramework

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [Scan_ScannerDevice](capi-oh-scan-scan-scannerdevice.md)** devices | 所有发现的扫描仪设备列表，devices指针指向的内存将在回调函数结束时释放 |
| int32_t deviceCount | 发现的扫描仪数量 |

### OH_Scan_Init()

```c
int32_t OH_Scan_Init()
```

**描述：**

此API检查并拉起扫描服务，初始化扫描客户端，并建立与扫描服务的连接。应先调用此API初始化扫描服务，再调用其他扫描API。在使用完毕后，需调用 [OH_Scan_Exit](capi-ohscan-h.md#oh_scan_exit) 释放资源。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** {@code ohos.permission.PRINT}

**起始版本：** 12

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [SCAN_ERROR_NONE](capi-ohscan-h.md#scan_errorcode) 表示扫描服务成功启动<br>[SCAN_ERROR_NO_PERMISSION](capi-ohscan-h.md#scan_errorcode) 表示无权限使用此接口<br>[SCAN_ERROR_RPC_FAILURE](capi-ohscan-h.md#scan_errorcode) 表示RPC通信错误<br>[SCAN_ERROR_SERVER_FAILURE](capi-ohscan-h.md#scan_errorcode) 表示扫描过程中发生错误 |

### OH_Scan_StartScannerDiscovery()

```c
int32_t OH_Scan_StartScannerDiscovery(Scan_ScannerDiscoveryCallback callback)
```

**描述：**

此API开始发现扫描仪，注册回调函数处理发现的扫描仪设备。注册的回调将在调用 [OH_Scan_Exit](capi-ohscan-h.md#oh_scan_exit) 时注销。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** {@code ohos.permission.PRINT}

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [Scan_ScannerDiscoveryCallback](capi-ohscan-h.md#scan_scannerdiscoverycallback) callback | 扫描仪发现事件的[Scan_ScannerDiscoveryCallback](capi-ohscan-h.md#scan_scannerdiscoverycallback)回调函数，不能为NULL |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [SCAN_ERROR_NONE](capi-ohscan-h.md#scan_errorcode) 表示成功开始扫描仪搜索<br>[SCAN_ERROR_NO_PERMISSION](capi-ohscan-h.md#scan_errorcode) 表示无权限使用此接口<br>[SCAN_ERROR_RPC_FAILURE](capi-ohscan-h.md#scan_errorcode) 表示RPC通信错误<br>[SCAN_ERROR_SERVER_FAILURE](capi-ohscan-h.md#scan_errorcode) 表示扫描过程中发生错误 |

### OH_Scan_OpenScanner()

```c
int32_t OH_Scan_OpenScanner(const char* scannerId)
```

**描述：**

此API连接到扫描仪设备。设备使用完毕后，可调用 [OH_Scan_CloseScanner](capi-ohscan-h.md#oh_scan_closescanner) 关闭。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** {@code ohos.permission.PRINT}

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* scannerId | 用于连接扫描仪的ID，取值应为已发现的有效扫描仪设备ID。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [SCAN_ERROR_NONE](capi-ohscan-h.md#scan_errorcode) 表示扫描仪成功连接<br>[SCAN_ERROR_NO_PERMISSION](capi-ohscan-h.md#scan_errorcode) 表示无权限使用此接口<br>[SCAN_ERROR_RPC_FAILURE](capi-ohscan-h.md#scan_errorcode) 表示RPC通信错误<br>[SCAN_ERROR_SERVER_FAILURE](capi-ohscan-h.md#scan_errorcode) 表示扫描过程中发生错误<br>[SCAN_ERROR_DEVICE_BUSY](capi-ohscan-h.md#scan_errorcode) 表示扫描仪繁忙<br>[SCAN_ERROR_INVALID_PARAMETER](capi-ohscan-h.md#scan_errorcode) 表示输入参数无效<br>[SCAN_ERROR_IO_ERROR](capi-ohscan-h.md#scan_errorcode) 表示与扫描仪通信时发生错误<br>[SCAN_ERROR_NO_MEMORY](capi-ohscan-h.md#scan_errorcode) 表示可用内存不足 |

### OH_Scan_CloseScanner()

```c
int32_t OH_Scan_CloseScanner(const char* scannerId)
```

**描述：**

此API用于关闭已连接的扫描仪设备。一般在扫描仪使用完毕后调用此API关闭连接。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** {@code ohos.permission.PRINT}

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* scannerId | 用于断开扫描仪连接的ID，取值应为已连接的有效扫描仪设备ID。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [SCAN_ERROR_NONE](capi-ohscan-h.md#scan_errorcode) 表示扫描仪连接成功关闭<br>[SCAN_ERROR_NO_PERMISSION](capi-ohscan-h.md#scan_errorcode) 表示无权限使用此接口<br>[SCAN_ERROR_RPC_FAILURE](capi-ohscan-h.md#scan_errorcode) 表示RPC通信错误<br>[SCAN_ERROR_SERVER_FAILURE](capi-ohscan-h.md#scan_errorcode) 表示扫描过程中发生错误<br>[SCAN_ERROR_INVALID_PARAMETER](capi-ohscan-h.md#scan_errorcode) 表示输入参数无效 |

### OH_Scan_GetScannerParameter()

```c
Scan_ScannerOptions* OH_Scan_GetScannerParameter(const char* scannerId, int32_t* errorCode)
```

**描述：**

此API可用于获取扫描仪可设置的选项列表。返回的结构体指针指向的内存会在[OH_Scan_Exit](capi-ohscan-h.md#oh_scan_exit)时自动释放，每个扫描仪型号在内存中只会存储一份副本。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** {@code ohos.permission.PRINT}

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* scannerId | 用于获取扫描仪参数的ID，取值应为已连接的有效扫描仪设备ID。 |
| int32_t* errorCode | 不能为NULL。如果执行成功，errorCode返回[SCAN_ERROR_NONE](capi-ohscan-h.md#scan_errorcode)，否则返回特定的错误码，参考[Scan_ErrorCode](capi-ohscan-h.md#scan_errorcode)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [Scan_ScannerOptions*](capi-oh-scan-scan-scanneroptions.md) | 成功时返回扫描仪参数选项结构体指针，可用于获取和设置扫描仪参数选项；失败时返回NULL。 |

### OH_Scan_SetScannerParameter()

```c
int32_t OH_Scan_SetScannerParameter(const char* scannerId, const int32_t option, const char* value)
```

**描述：**

此API可用于设置扫描仪的某个选项参数。传入的选项和值从[OH_Scan_GetScannerParameter](capi-ohscan-h.md#oh_scan_getscannerparameter)获取。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** {@code ohos.permission.PRINT}

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* scannerId | 此ID用于设置特定扫描仪的选项，取值应为已连接的有效扫描仪设备ID。 |
| const int32_t option | 要设置的选项编号。取值范围从0到optionCount - 1，从[Scan_ScannerOptions](capi-oh-scan-scan-scanneroptions.md)获取。 |
| const char* value | 要设置的选项值，有效值从[Scan_ScannerOptions](capi-oh-scan-scan-scanneroptions.md)的ranges中获取。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [SCAN_ERROR_NONE](capi-ohscan-h.md#scan_errorcode) 表示扫描仪参数设置成功<br>[SCAN_ERROR_NO_PERMISSION](capi-ohscan-h.md#scan_errorcode) 表示无权限使用此接口<br>[SCAN_ERROR_RPC_FAILURE](capi-ohscan-h.md#scan_errorcode) 表示RPC通信错误<br>[SCAN_ERROR_SERVER_FAILURE](capi-ohscan-h.md#scan_errorcode) 表示扫描过程中发生错误<br>[SCAN_ERROR_INVALID_PARAMETER](capi-ohscan-h.md#scan_errorcode) 表示输入参数无效 |

### OH_Scan_StartScan()

```c
int32_t OH_Scan_StartScan(const char* scannerId, bool batchMode)
```

**描述：**

此API用于启动扫描仪的扫描任务。成功初始化扫描服务，并连接扫描仪完成参数设置后，可以调用此API开始扫描。扫描过程中可调用 [OH_Scan_GetPictureScanProgress](capi-ohscan-h.md#oh_scan_getpicturescanprogress) 获取扫描进度， 可调用 [OH_Scan_CancelScan](capi-ohscan-h.md#oh_scan_cancelscan) 取消扫描。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** {@code ohos.permission.PRINT}

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* scannerId | 此ID用于启动指定扫描仪的扫描任务，取值应为已连接的有效扫描仪设备ID。 |
| bool batchMode | 是否以批处理模式启动扫描仪。true表示开启批处理模式，扫描仪可连续扫描多页文档（通常经文档进纸器连续进纸）；false表示关闭批处理模式，仅扫描单页。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [SCAN_ERROR_NONE](capi-ohscan-h.md#scan_errorcode) 表示扫描仪成功启动扫描任务<br>[SCAN_ERROR_NO_PERMISSION](capi-ohscan-h.md#scan_errorcode) 表示无权限使用此接口<br>[SCAN_ERROR_RPC_FAILURE](capi-ohscan-h.md#scan_errorcode) 表示RPC通信错误<br>[SCAN_ERROR_SERVER_FAILURE](capi-ohscan-h.md#scan_errorcode) 表示扫描过程中发生错误<br>[SCAN_ERROR_JAMMED](capi-ohscan-h.md#scan_errorcode) 表示文档进纸器卡纸<br>[SCAN_ERROR_NO_DOCS](capi-ohscan-h.md#scan_errorcode) 表示文档进纸器缺纸<br>[SCAN_ERROR_COVER_OPEN](capi-ohscan-h.md#scan_errorcode) 表示扫描仪盖板打开<br>[SCAN_ERROR_IO_ERROR](capi-ohscan-h.md#scan_errorcode) 表示与扫描仪通信时发生错误<br>[SCAN_ERROR_NO_MEMORY](capi-ohscan-h.md#scan_errorcode) 表示可用内存不足<br>[SCAN_ERROR_INVALID_PARAMETER](capi-ohscan-h.md#scan_errorcode) 表示输入参数无效<br>[SCAN_ERROR_DEVICE_BUSY](capi-ohscan-h.md#scan_errorcode) 表示扫描仪繁忙，应稍后重试操作 |

### OH_Scan_CancelScan()

```c
int32_t OH_Scan_CancelScan(const char* scannerId)
```

**描述：**

此API用于取消扫描仪正在进行的扫描任务。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** {@code ohos.permission.PRINT}

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* scannerId | 此ID用于取消指定扫描仪的扫描任务，取值应为已连接的有效扫描仪设备ID。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [SCAN_ERROR_NONE](capi-ohscan-h.md#scan_errorcode) 表示扫描仪成功取消扫描任务<br>[SCAN_ERROR_NO_PERMISSION](capi-ohscan-h.md#scan_errorcode) 表示无权限使用此接口<br>[SCAN_ERROR_INVALID_PARAMETER](capi-ohscan-h.md#scan_errorcode) 表示输入参数无效<br>[SCAN_ERROR_RPC_FAILURE](capi-ohscan-h.md#scan_errorcode) 表示RPC通信错误<br>[SCAN_ERROR_SERVER_FAILURE](capi-ohscan-h.md#scan_errorcode) 表示扫描过程中发生错误 |

### OH_Scan_GetPictureScanProgress()

```c
int32_t OH_Scan_GetPictureScanProgress(const char* scannerId, Scan_PictureScanProgress* prog)
```

**描述：**

此API可获取扫描仪扫描图片的进度。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** {@code ohos.permission.PRINT}

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* scannerId | 用于查询扫描仪图片扫描进度的ID，取值应为已连接的有效扫描仪设备ID。 |
| [Scan_PictureScanProgress](capi-oh-scan-scan-picturescanprogress.md)* prog | 扫描图片的[Scan_PictureScanProgress](capi-oh-scan-scan-picturescanprogress.md)，必须传入非空值，扫描进度将写入prog指针指向的结构体。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [SCAN_ERROR_NONE](capi-ohscan-h.md#scan_errorcode) 表示扫描仪成功查询到扫描图片的进度<br>[SCAN_ERROR_NO_PERMISSION](capi-ohscan-h.md#scan_errorcode) 表示无权限使用此接口<br>[SCAN_ERROR_INVALID_PARAMETER](capi-ohscan-h.md#scan_errorcode) 表示输入参数无效<br>[SCAN_ERROR_RPC_FAILURE](capi-ohscan-h.md#scan_errorcode) 表示RPC通信错误<br>[SCAN_ERROR_SERVER_FAILURE](capi-ohscan-h.md#scan_errorcode) 表示扫描过程中发生错误<br>[SCAN_ERROR_JAMMED](capi-ohscan-h.md#scan_errorcode) 表示文档进纸器卡纸<br>[SCAN_ERROR_NO_DOCS](capi-ohscan-h.md#scan_errorcode) 表示文档进纸器缺纸<br>[SCAN_ERROR_COVER_OPEN](capi-ohscan-h.md#scan_errorcode) 表示扫描仪盖板打开<br>[SCAN_ERROR_IO_ERROR](capi-ohscan-h.md#scan_errorcode) 表示与扫描仪通信时发生错误<br>[SCAN_ERROR_NO_MEMORY](capi-ohscan-h.md#scan_errorcode) 表示可用内存不足<br>[SCAN_ERROR_DEVICE_BUSY](capi-ohscan-h.md#scan_errorcode) 表示扫描仪繁忙，应稍后重试操作 |

### OH_Scan_Exit()

```c
int32_t OH_Scan_Exit()
```

**描述：**

此API可用于退出扫描服务，释放扫描框架内存，并注销扫描仪设备发现回调。扫描服务退出后，将无法再调用其他扫描API。

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** {@code ohos.permission.PRINT}

**起始版本：** 12

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [SCAN_ERROR_NONE](capi-ohscan-h.md#scan_errorcode) 表示扫描服务成功退出<br>[SCAN_ERROR_NO_PERMISSION](capi-ohscan-h.md#scan_errorcode) 表示无权限使用此接口<br>[SCAN_ERROR_RPC_FAILURE](capi-ohscan-h.md#scan_errorcode) 表示RPC通信错误<br>[SCAN_ERROR_SERVER_FAILURE](capi-ohscan-h.md#scan_errorcode) 表示扫描过程中发生错误 |


