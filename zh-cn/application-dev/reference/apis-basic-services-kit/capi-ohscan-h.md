# ohscan.h
<!--Kit: Basic Services Kit-->	
<!--Subsystem: Print-->	
<!--Owner: @guoshengbang-->	
<!--Designer: @Q-haosu-->	
<!--Tester: @Q-haosu-->	
<!--Adviser: @fang-jinxu-->

## 概述

声明用于发现和连接扫描仪、从扫描仪扫描图像、获取页面扫描进度和设置扫描图像参数等功能的API

**库：** libohscan.so

**系统能力：** SystemCapability.Print.PrintFramework

**起始版本：** 12

**相关模块：** [OH_Scan](capi-oh-scan.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [Scan_ScannerDevice](capi-oh-scan-scan-scannerdevice.md) | Scan_ScannerDevice | 表示扫描仪设备信息 |
| [Scan_PictureScanProgress](capi-oh-scan-scan-picturescanprogress.md) | Scan_PictureScanProgress | 表示扫描仪扫描图片的进度 |
| [Scan_ScannerOptions](capi-oh-scan-scan-scanneroptions.md) | Scan_ScannerOptions | 表示一个扫描仪的所有参数选项 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [Scan_ErrorCode](#scan_errorcode) | Scan_ErrorCode | 定义错误码 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef void (\*Scan_ScannerDiscoveryCallback)(Scan_ScannerDevice** devices, int32_t deviceCount)](#scan_scannerdiscoverycallback) | Scan_ScannerDiscoveryCallback | 扫描仪设备发现回调，通过[OH_Scan_StartScannerDiscovery](capi-ohscan-h.md#oh_scan_startscannerdiscovery)注册指针指向的内存将在回调函数结束时释放 |
| [int32_t OH_Scan_Init()](#oh_scan_init) | - | 此API检查并拉起扫描服务，初始化扫描客户端，并建立与扫描服务的连接 |
| [int32_t OH_Scan_StartScannerDiscovery(Scan_ScannerDiscoveryCallback callback)](#oh_scan_startscannerdiscovery) | - | 此API开始发现扫描仪，注册回调函数处理发现的扫描仪设备 |
| [int32_t OH_Scan_OpenScanner(const char* scannerId)](#oh_scan_openscanner) | - | 此API连接到扫描仪设备 |
| [int32_t OH_Scan_CloseScanner(const char* scannerId)](#oh_scan_closescanner) | - | 此API用于关闭已连接的扫描仪设备 |
| [Scan_ScannerOptions* OH_Scan_GetScannerParameter(const char* scannerId, int32_t* errorCode)](#oh_scan_getscannerparameter) | - | 此API可用于获取扫描仪可设置的选项列表返回的结构体指针指向的内存会在[OH_Scan_Exit](capi-ohscan-h.md#oh_scan_exit)时自动释放，每个型号在内存中只会存储一份副本 |
| [int32_t OH_Scan_SetScannerParameter(const char* scannerId, const int32_t option, const char* value)](#oh_scan_setscannerparameter) | - | 此API可用于设置扫描仪的某个选项参数传入的选项和值从[OH_Scan_GetScannerParameter](capi-ohscan-h.md#oh_scan_getscannerparameter)获取 |
| [int32_t OH_Scan_StartScan(const char* scannerId, bool batchMode)](#oh_scan_startscan) | - | 此API允许扫描仪开始扫描 |
| [int32_t OH_Scan_CancelScan(const char* scannerId)](#oh_scan_cancelscan) | - | 此API允许扫描仪取消扫描 |
| [int32_t OH_Scan_GetPictureScanProgress(const char* scannerId, Scan_PictureScanProgress* prog)](#oh_scan_getpicturescanprogress) | - | 此API可获取扫描仪扫描图片的进度。必须传入非空值，扫描进度将写入指针指向的结构体 |
| [int32_t OH_Scan_Exit()](#oh_scan_exit) | - | 此API可用于退出扫描服务，释放扫描框架内存，并注销扫描仪发现回调 |

## 枚举类型说明

### Scan_ErrorCode

```
enum Scan_ErrorCode
```

**描述**

定义错误码

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| SCAN_ERROR_NONE = 0 | 操作成功 |
| SCAN_ERROR_NO_PERMISSION = 201 | 权限验证失败 |
| SCAN_ERROR_INVALID_PARAMETER = 401 | 参数无效。例如指针为空或字符串为空 |
| SCAN_ERROR_GENERIC_FAILURE = 24300101 | 通用内部错误 |
| SCAN_ERROR_RPC_FAILURE = 24300102 | RPC通信错误 |
| SCAN_ERROR_SERVER_FAILURE = 24300103 | 服务器错误 |
| SCAN_ERROR_UNSUPPORTED = 24300104 | 不支持的操作 |
| SCAN_ERROR_CANCELED = 24300105 | 操作已取消 |
| SCAN_ERROR_DEVICE_BUSY = 24300106 | 设备繁忙，请稍后重试 |
| SCAN_ERROR_INVALID = 24300107 | 数据无效（包括打开时无设备） |
| SCAN_ERROR_JAMMED = 24300108 | 文档进纸器卡纸 |
| SCAN_ERROR_NO_DOCS = 24300109 | 文档进纸器缺纸 |
| SCAN_ERROR_COVER_OPEN = 24300110 | 扫描仪盖板打开 |
| SCAN_ERROR_IO_ERROR = 24300111 | 设备I/O错误 |
| SCAN_ERROR_NO_MEMORY = 24300112 | 内存不足 |


## 函数说明

### Scan_ScannerDiscoveryCallback()

```
typedef void (*Scan_ScannerDiscoveryCallback)(Scan_ScannerDevice** devices, int32_t deviceCount)
```

**描述**

扫描仪设备发现回调，通过[OH_Scan_StartScannerDiscovery](capi-ohscan-h.md#oh_scan_startscannerdiscovery)注册指针指向的内存将在回调函数结束时释放

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [Scan_ScannerDevice](capi-oh-scan-scan-scannerdevice.md)** devices | 所有发现的扫描仪设备列表 |
|  int32_t deviceCount | 发现的扫描仪数量 |

### OH_Scan_Init()

```
int32_t OH_Scan_Init()
```

**描述**

此API检查并拉起扫描服务，初始化扫描客户端，并建立与扫描服务的连接

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** ohos.permission.PRINT

**起始版本：** 12

**返回：**

| 类型 | 说明                                                                                                                                                                                                                                                                                                    |
| -- |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| int32_t | [Scan_ERROR_NONE](#scan_errorcode) 表示扫描服务成功启动<br>         [SCAN_ERROR_NO_PERMISSION](capi-ohscan-h.md#scan_errorcode) 表示无权限使用此接口<br>         [SCAN_ERROR_RPC_FAILURE](capi-ohscan-h.md#scan_errorcode) 表示RPC通信错误<br>         [SCAN_ERROR_SERVER_FAILURE](capi-ohscan-h.md#scan_errorcode) 表示扫描过程中发生错误 |

### OH_Scan_StartScannerDiscovery()

```
int32_t OH_Scan_StartScannerDiscovery(Scan_ScannerDiscoveryCallback callback)
```

**描述**

此API开始发现扫描仪，注册回调函数处理发现的扫描仪设备

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** ohos.permission.PRINT

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [Scan_ScannerDiscoveryCallback](capi-ohscan-h.md#scan_scannerdiscoverycallback) callback | 扫描仪发现事件的[Scan_ScannerDiscoveryCallback](capi-ohscan-h.md#scan_scannerdiscoverycallback)回调函数 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [Scan_ERROR_NONE](#scan_errorcode) 表示成功开始扫描仪搜索<br>         [SCAN_ERROR_NO_PERMISSION](capi-ohscan-h.md#scan_errorcode) 表示无权限使用此接口<br>         [SCAN_ERROR_RPC_FAILURE](capi-ohscan-h.md#scan_errorcode) 表示RPC通信错误<br>         [SCAN_ERROR_SERVER_FAILURE](capi-ohscan-h.md#scan_errorcode) 表示扫描过程中发生错误 |

### OH_Scan_OpenScanner()

```
int32_t OH_Scan_OpenScanner(const char* scannerId)
```

**描述**

此API连接到扫描仪设备

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** ohos.permission.PRINT

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* scannerId | 用于连接扫描仪的ID |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [Scan_ERROR_NONE](#scan_errorcode) 表示扫描仪成功连接<br>         [SCAN_ERROR_NO_PERMISSION](capi-ohscan-h.md#scan_errorcode) 表示无权限使用此接口<br>         [SCAN_ERROR_RPC_FAILURE](capi-ohscan-h.md#scan_errorcode) 表示RPC通信错误<br>         [SCAN_ERROR_SERVER_FAILURE](capi-ohscan-h.md#scan_errorcode) 表示扫描过程中发生错误<br>         [SCAN_ERROR_DEVICE_BUSY](capi-ohscan-h.md#scan_errorcode) 表示扫描仪繁忙<br>         [SCAN_ERROR_INVALID_PARAMETER](capi-ohscan-h.md#scan_errorcode) 表示输入参数无效<br>         [SCAN_ERROR_IO_ERROR](capi-ohscan-h.md#scan_errorcode) 表示与设备通信时发生错误<br>         [SCAN_ERROR_NO_MEMORY](capi-ohscan-h.md#scan_errorcode) 表示可用内存不足 |

### OH_Scan_CloseScanner()

```
int32_t OH_Scan_CloseScanner(const char* scannerId)
```

**描述**

此API用于关闭已连接的扫描仪设备

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** ohos.permission.PRINT

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* scannerId | 用于断开扫描仪连接的ID |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [Scan_ERROR_NONE](#scan_errorcode) 表示扫描仪连接成功关闭<br>         [SCAN_ERROR_NO_PERMISSION](capi-ohscan-h.md#scan_errorcode) 表示无权限使用此接口<br>         [SCAN_ERROR_RPC_FAILURE](capi-ohscan-h.md#scan_errorcode) 表示RPC通信错误<br>         [SCAN_ERROR_SERVER_FAILURE](capi-ohscan-h.md#scan_errorcode) 表示扫描过程中发生错误<br>         [SCAN_ERROR_INVALID_PARAMETER](capi-ohscan-h.md#scan_errorcode) 表示输入参数无效 |

### OH_Scan_GetScannerParameter()

```
Scan_ScannerOptions* OH_Scan_GetScannerParameter(const char* scannerId, int32_t* errorCode)
```

**描述**

此API可用于获取扫描仪可设置的选项列表返回的结构体指针指向的内存会在[OH_Scan_Exit](capi-ohscan-h.md#oh_scan_exit)时自动释放，每个型号在内存中只会存储一份副本

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** ohos.permission.PRINT

**起始版本：** 12

**参数：**

| 参数项 | 描述                                                                                                    |
| -- |-------------------------------------------------------------------------------------------------------|
| const char* scannerId | 用于获取扫描仪参数的ID                                                                                          |
| int32_t* errorCode | 如果执行成功，errorCode返回[Scan_ERROR_NONE](#scan_errorcode)，否则返回特定的错误码，参考[Print_ErrorCode](capi-ohprint-h.md#print_errorcode) |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Scan_ScannerOptions*](capi-oh-scan-scan-scanneroptions.md) | [Scan_ERROR_NONE](#scan_errorcode) 表示成功获取扫描仪参数选项<br>         [SCAN_ERROR_NO_PERMISSION](capi-ohscan-h.md#scan_errorcode) 表示无权限使用此接口<br>         [SCAN_ERROR_RPC_FAILURE](capi-ohscan-h.md#scan_errorcode) 表示RPC通信错误<br>         [SCAN_ERROR_SERVER_FAILURE](capi-ohscan-h.md#scan_errorcode) 表示扫描过程中发生错误<br>         [SCAN_ERROR_INVALID_PARAMETER](capi-ohscan-h.md#scan_errorcode) 表示参数无效 |

### OH_Scan_SetScannerParameter()

```
int32_t OH_Scan_SetScannerParameter(const char* scannerId, const int32_t option, const char* value)
```

**描述**

此API可用于设置扫描仪的某个选项参数传入的选项和值从[OH_Scan_GetScannerParameter](capi-ohscan-h.md#oh_scan_getscannerparameter)获取

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** ohos.permission.PRINT

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* scannerId | 此ID用于设置特定扫描仪的选项 |
| const int32_t option | 要设置的选项编号。取值范围从0到 optionCount - 1，从[Scan_ScannerOptions](capi-oh-scan-scan-scanneroptions.md)获取 |
| const char* value | 要设置的选项值，有效值从ranges获取，从[Scan_ScannerOptions](capi-oh-scan-scan-scanneroptions.md)获取 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [Scan_ERROR_NONE](#scan_errorcode) 表示扫描仪参数设置成功<br>         [SCAN_ERROR_NO_PERMISSION](capi-ohscan-h.md#scan_errorcode) 表示无权限使用此接口<br>         [SCAN_ERROR_RPC_FAILURE](capi-ohscan-h.md#scan_errorcode) 表示RPC通信错误<br>         [SCAN_ERROR_SERVER_FAILURE](capi-ohscan-h.md#scan_errorcode) 表示扫描过程中发生错误<br>         [SCAN_ERROR_INVALID_PARAMETER](capi-ohscan-h.md#scan_errorcode) 表示参数无效 |

### OH_Scan_StartScan()

```
int32_t OH_Scan_StartScan(const char* scannerId, bool batchMode)
```

**描述**

此API允许扫描仪开始扫描

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** code ohos.permission.PRINT

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* scannerId | 此ID用于启动指定扫描仪的扫描任务 |
| bool batchMode | 是否以批处理模式启动扫描仪 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [Scan_ERROR_NONE](#scan_errorcode) 表示扫描仪成功启动扫描任务<br>         [SCAN_ERROR_NO_PERMISSION](capi-ohscan-h.md#scan_errorcode) 表示无权限使用此接口<br>         [SCAN_ERROR_RPC_FAILURE](capi-ohscan-h.md#scan_errorcode) 表示RPC通信错误<br>         [SCAN_ERROR_SERVER_FAILURE](capi-ohscan-h.md#scan_errorcode) 表示扫描过程中发生错误<br>         [SCAN_ERROR_JAMMED](capi-ohscan-h.md#scan_errorcode) 表示文档进纸器卡纸<br>         [SCAN_ERROR_NO_DOCS](capi-ohscan-h.md#scan_errorcode) 表示文档进纸器缺纸<br>         [SCAN_ERROR_COVER_OPEN](capi-ohscan-h.md#scan_errorcode) 表示扫描仪盖板打开<br>         [SCAN_ERROR_IO_ERROR](capi-ohscan-h.md#scan_errorcode) 表示与设备通信时发生错误<br>         [SCAN_ERROR_NO_MEMORY](capi-ohscan-h.md#scan_errorcode) 表示可用内存不足<br>         [SCAN_ERROR_INVALID_PARAMETER](capi-ohscan-h.md#scan_errorcode) 表示输入参数无效<br>         [SCAN_ERROR_DEVICE_BUSY](capi-ohscan-h.md#scan_errorcode) 表示设备繁忙，应稍后重试操作 |

### OH_Scan_CancelScan()

```
int32_t OH_Scan_CancelScan(const char* scannerId)
```

**描述**

此API允许扫描仪取消扫描

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** ohos.permission.PRINT

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* scannerId | 此ID用于取消指定扫描仪的扫描任务 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [Scan_ERROR_NONE](#scan_errorcode) 表示扫描仪成功取消扫描任务<br>         [SCAN_ERROR_NO_PERMISSION](capi-ohscan-h.md#scan_errorcode) 表示无权限使用此接口<br>         [SCAN_ERROR_INVALID_PARAMETER](capi-ohscan-h.md#scan_errorcode) 表示指针为空或字符串为空<br>         [SCAN_ERROR_RPC_FAILURE](capi-ohscan-h.md#scan_errorcode) 表示RPC通信错误<br>         [SCAN_ERROR_SERVER_FAILURE](capi-ohscan-h.md#scan_errorcode) 表示扫描过程中发生错误 |

### OH_Scan_GetPictureScanProgress()

```
int32_t OH_Scan_GetPictureScanProgress(const char* scannerId, Scan_PictureScanProgress* prog)
```

**描述**

此API可获取扫描仪扫描图片的进度。必须传入非空值，扫描进度将写入指针指向的结构体

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** ohos.permission.PRINT

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* scannerId | 用于查询扫描仪图像扫描进度的ID |
| [Scan_PictureScanProgress](capi-oh-scan-scan-picturescanprogress.md)* prog | 扫描图片的[Scan_PictureScanProgress](capi-oh-scan-scan-picturescanprogress.md)，必须为非空值 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [Scan_ERROR_NONE](#scan_errorcode) 表示扫描仪成功查询到扫描图像的进度<br>         [SCAN_ERROR_NO_PERMISSION](capi-ohscan-h.md#scan_errorcode) 表示无权限使用此接口<br>         [SCAN_ERROR_INVALID_PARAMETER](capi-ohscan-h.md#scan_errorcode) 表示指针为空或字符串为空<br>         [SCAN_ERROR_RPC_FAILURE](capi-ohscan-h.md#scan_errorcode) 表示RPC通信错误<br>         [SCAN_ERROR_SERVER_FAILURE](capi-ohscan-h.md#scan_errorcode) 表示扫描过程中发生错误<br>         [SCAN_ERROR_JAMMED](capi-ohscan-h.md#scan_errorcode) 表示文档进纸器卡纸<br>         [SCAN_ERROR_NO_DOCS](capi-ohscan-h.md#scan_errorcode) 表示文档进纸器缺纸<br>         [SCAN_ERROR_COVER_OPEN](capi-ohscan-h.md#scan_errorcode) 表示扫描仪盖板打开<br>         [SCAN_ERROR_IO_ERROR](capi-ohscan-h.md#scan_errorcode) 表示与扫描仪通信时发生错误<br>         [SCAN_ERROR_NO_MEMORY](capi-ohscan-h.md#scan_errorcode) 表示可用内存不足<br>         [SCAN_ERROR_DEVICE_BUSY](capi-ohscan-h.md#scan_errorcode) 表示设备繁忙，应稍后重试操作 |

### OH_Scan_Exit()

```
int32_t OH_Scan_Exit()
```

**描述**

此API可用于退出扫描服务，释放扫描框架内存，并注销扫描仪发现回调

**系统能力：** SystemCapability.Print.PrintFramework

**需要权限：** ohos.permission.PRINT

**起始版本：** 12

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [Scan_ERROR_NONE](#scan_errorcode) 表示扫描服务成功退出<br>         [SCAN_ERROR_NO_PERMISSION](capi-ohscan-h.md#scan_errorcode) 表示无权限使用此接口<br>         [SCAN_ERROR_RPC_FAILURE](capi-ohscan-h.md#scan_errorcode) 表示RPC通信错误<br>         [SCAN_ERROR_SERVER_FAILURE](capi-ohscan-h.md#scan_errorcode) 表示扫描过程中发生错误 |


