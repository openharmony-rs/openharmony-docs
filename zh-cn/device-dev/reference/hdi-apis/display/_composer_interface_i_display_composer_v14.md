# IDisplayComposer

## 概述

**相关模块：**  [Display](_composer_display_v14.md)

## 汇总

### Public 成员函数

| 名称 | 描述 |
| -------- | -------- |
| [GetPanelPowerStatus](#getpanelpowerstatus) ([in] unsigned int devId, [out] enum [PanelPowerStatus](_composer_display_v14.md#panelpowerstatus) status) | 获取面板电源状态。 |
| [InitSMQInfo](#initsmqinfo) ([in] unsigned int devId, [in] SharedMemQueue&lt; int &gt; request, [out] SharedMemQueue&lt; int &gt; reply) | 获取命令请求的结果。 |
| [DoCmdRequest](#docmdrequest) ([in] unsigned int devId, [in] unsigned int inEleCnt, [in] struct HdifdInfo[] inFds, [out] unsigned int outEleCnt, [out] struct HdifdInfo[] outFds) | 发送请求命令。 |
| [GetDisplayConnectionType](#getdisplayconnectiontype) ([in] unsigned int devId, [out] enum [DisplayConnectionType](_composer_display_v14.md#displayconnectiontype) outType) | 获取显示连接类型。 |

## 成员函数说明

### DoCmdRequest()

```idl
IDisplayComposer::DoCmdRequest([in] unsigned int devId, [in] unsigned int inEleCnt, [in] struct HdifdInfo[] inFds, [out] unsigned int outEleCnt, [out] struct HdifdInfo[] outFds)
```

**描述**

发送请求命令。

**起始版本：**  6.1

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| devId | 显示设备ID。 |
| inEleCnt | 请求的元素的数量。 |
| inFds | 请求的fds。 |
| outEleCnt | 输出的元素的数量。 |
| outFds | 输出的fds。 |

**返回：**

0表示执行成功。

其他值表示执行失败，具体错误码查看[DispErrCode](_display_v10.md#disperrcode)。

### GetDisplayConnectionType()

```idl
IDisplayComposer::GetDisplayConnectionType([in] unsigned int devId, [out] enum DisplayConnectionType outType)
```

**描述**

获取显示连接类型。

**起始版本：**  6.1

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| devId | 显示设备ID。 |
| outType | 显示器连接类型。 |

**返回：**

0表示执行成功。

其他值表示执行失败，具体错误码查看[DispErrCode](_display_v10.md#disperrcode)。

### GetPanelPowerStatus()

```idl
IDisplayComposer::GetPanelPowerStatus([in] unsigned int devId, [out] enum PanelPowerStatus status)
```

**描述**

获取面板电源状态。

**起始版本：**  6.1

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| devId | 显示设备ID。 |
| status | 面板的电源状态。 |

**返回：**

0表示执行成功。

其他值表示执行失败，具体错误码查看[DispErrCode](_display_v10.md#disperrcode)。

### InitSMQInfo()

```idl
IDisplayComposer::InitSMQInfo([in] unsigned int devId, [in] SharedMemQueue< int > request, [out] SharedMemQueue< int > reply)
```

**描述**

获取命令请求的结果。

**起始版本：**  6.1

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| devId | 显示设备ID。 |
| request | 初始化的共享内存请求队列。 |
| reply | 返回结果。 |

**返回：**

0表示执行成功。

其他值表示执行失败，具体错误码查看[DispErrCode](_display_v10.md#disperrcode)。
