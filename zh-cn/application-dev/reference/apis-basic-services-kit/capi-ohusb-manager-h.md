# ohusb_manager.h

<!--Kit: Basic Services Kit-->
<!--Subsystem: USB-->

## 概述

声明用于USB设备管理的C API。

**库：** libohusb_manager.so

**系统能力：** SystemCapability.USB.USBManager

**起始版本：** 26.1.0

**相关模块：** [UsbManager](capi-usbmanager.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_UsbManager_UsbEndpoint](capi-usbmanager-oh-usbmanager-usbendpoint.md) | OH_UsbManager_UsbEndpoint | 定义用于发送或接收数据的USB端点。端点从[OH_UsbManager_UsbInterface](capi-usbmanager-oh-usbmanager-usbinterface.md)获取。 |
| [OH_UsbManager_UsbInterface](capi-usbmanager-oh-usbmanager-usbinterface.md) | OH_UsbManager_UsbInterface | 定义USB接口。一个[OH_UsbManager_UsbConfig](capi-usbmanager-oh-usbmanager-usbconfig.md)可以包含多个<br>OH_UsbManager_UsbInterface实例，每个实例提供特定功能。 |
| [OH_UsbManager_UsbConfig](capi-usbmanager-oh-usbmanager-usbconfig.md) | OH_UsbManager_UsbConfig | 定义USB配置。一个[OH_UsbManager_UsbDevice](capi-usbmanager-oh-usbmanager-usbdevice.md)可以包含多个<br>**OH_UsbManager_UsbConfig**实例。 |
| [OH_UsbManager_UsbDevice](capi-usbmanager-oh-usbmanager-usbdevice.md) | OH_UsbManager_UsbDevice | 定义USB设备的扁平化表示。 |
| [OH_UsbManager_UsbPipe](capi-usbmanager-oh-usbmanager-usbpipe.md) | OH_UsbManager_UsbPipe | 定义用于与已打开设备通信的USB设备管道。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_UsbManager_ErrorCode](#oh_usbmanager_errorcode) | OH_UsbManager_ErrorCode | 枚举USB管理器的错误码。 |
| [OH_UsbManager_RequestDirection](#oh_usbmanager_requestdirection) | OH_UsbManager_RequestDirection | 枚举USB请求方向。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_UsbManager_ErrorCode OH_UsbManager_GetUsbDeviceList(OH_UsbManager_UsbDevice **devices, uint32_t *deviceCount)](#oh_usbmanager_getusbdevicelist) | - | 获取所有已连接USB设备的列表。调用者必须调用[OH_UsbManager_FreeUsbDeviceList](capi-ohusb-manager-h.md#oh_usbmanager_freeusbdevicelist)<br>释放返回的数组。 |
| [void OH_UsbManager_FreeUsbDeviceList(OH_UsbManager_UsbDevice *devices, uint32_t deviceCount)](#oh_usbmanager_freeusbdevicelist) | - | 释放之前由[OH_UsbManager_GetUsbDeviceList](capi-ohusb-manager-h.md#oh_usbmanager_getusbdevicelist)返回的设备数组。<br>调用后该指针失效，不得再使用。传入null或数量为0是安全的空操作。 |
| [OH_UsbManager_ErrorCode OH_UsbManager_ConnectDevice(const OH_UsbManager_UsbDevice *device, OH_UsbManager_UsbPipe *pipe)](#oh_usbmanager_connectdevice) | - | 连接USB设备并打开用于通信的管道。返回的管道必须通过调用<br>[OH_UsbManager_ClosePipe](capi-ohusb-manager-h.md#oh_usbmanager_closepipe)关闭，以避免资源泄漏。<br>仅需要设备结构体中的**busNum**和**devAddress**字段；其他字段将被忽略。 |
| [OH_UsbManager_ErrorCode OH_UsbManager_HasPermission(const char *deviceName, bool *result)](#oh_usbmanager_haspermission) | - | 检查应用是否有权限访问指定设备。 |
| [typedef void (\*OH_UsbManager_PermissionCallback)(OH_UsbManager_ErrorCode errorCode, bool result, void *userContext)](#oh_usbmanager_permissioncallback) | OH_UsbManager_PermissionCallback | 定义用于返回[OH_UsbManager_RequestPermission](capi-ohusb-manager-h.md#oh_usbmanager_requestpermission)结果的<br>回调类型。 |
| [OH_UsbManager_ErrorCode OH_UsbManager_RequestPermission(const char *deviceName, OH_UsbManager_PermissionCallback callback, void *userContext)](#oh_usbmanager_requestpermission) | - | 异步请求访问指定USB设备的权限。这可能触发系统弹窗询问用户是否授权。<br>函数立即返回，结果通过回调传递。 |
| [OH_UsbManager_ErrorCode OH_UsbManager_GetFileDescriptor(const OH_UsbManager_UsbPipe *pipe, int32_t *fd)](#oh_usbmanager_getfiledescriptor) | - | 获取已打开USB设备管道的文件描述符。该fd可用于基于ioctl的<br>低层USB传输。 |
| [OH_UsbManager_ErrorCode OH_UsbManager_ClosePipe(const OH_UsbManager_UsbPipe *pipe)](#oh_usbmanager_closepipe) | - | 关闭USB设备管道并释放底层资源。该管道必须从[OH_UsbManager_ConnectDevice](capi-ohusb-manager-h.md#oh_usbmanager_connectdevice)<br>获取。 |

## 枚举类型说明

### OH_UsbManager_ErrorCode

```c
enum OH_UsbManager_ErrorCode
```

**描述：**

枚举USB管理器的错误码。

**起始版本：** 26.1.0

| 枚举项 | 描述 |
| -- | -- |
| OH_USBMANAGER_SUCCESS = 0 | 操作成功。<br>**起始版本：** 26.1.0 |
| OH_USBMANAGER_ERROR_PERMISSION_DENIED = 14400001 | 权限被拒绝。<br>**起始版本：** 26.1.0 |
| OH_USBMANAGER_ERROR_SERVICE_EXCEPTION = 14400004 | 服务异常。<br>**起始版本：** 26.1.0 |
| OH_USBMANAGER_ERROR_NO_DEVICE = 14400008 | 不存在该设备（可能已被断开连接）。<br>**起始版本：** 26.1.0 |
| OH_USBMANAGER_ERROR_NO_MEMORY = 14400009 | 内存不足。<br>**起始版本：** 26.1.0 |
| OH_USBMANAGER_ERROR_IO_ERROR = 14400012 | 传输I/O错误。<br>**起始版本：** 26.1.0 |
| OH_USBMANAGER_ERROR_INVALID_PARAMETER = 14400014 | 无效参数。对不可为空的参数传入了空指针。<br>**起始版本：** 26.1.0 |

### OH_UsbManager_RequestDirection

```c
enum OH_UsbManager_RequestDirection
```

**描述：**

枚举USB请求方向。

**起始版本：** 26.1.0

| 枚举项 | 描述 |
| -- | -- |
| OH_USBMANAGER_REQUEST_DIR_TO_DEVICE = 0 | 用于从主机向设备写入数据的请求。<br>**起始版本：** 26.1.0 |
| OH_USBMANAGER_REQUEST_DIR_FROM_DEVICE = 0x80 | 用于从设备向主机读取数据的请求。<br>**起始版本：** 26.1.0 |


## 函数说明

### OH_UsbManager_GetUsbDeviceList()

```c
OH_UsbManager_ErrorCode OH_UsbManager_GetUsbDeviceList(OH_UsbManager_UsbDevice **devices, uint32_t *deviceCount)
```

**描述：**

获取所有已连接USB设备的列表。调用者必须调用[OH_UsbManager_FreeUsbDeviceList](capi-ohusb-manager-h.md#oh_usbmanager_freeusbdevicelist)<br>释放返回的数组。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_UsbManager_UsbDevice](capi-usbmanager-oh-usbmanager-usbdevice.md) **devices | [出参] 指向[OH_UsbManager_UsbDevice](capi-usbmanager-oh-usbmanager-usbdevice.md)数组的二级指针。成功时，<br>函数会分配该数组及所有内部字符串缓冲区。调用者不得单独释放各个字段；<br>请改用[OH_UsbManager_FreeUsbDeviceList](capi-ohusb-manager-h.md#oh_usbmanager_freeusbdevicelist)。不得为空。 |
| uint32_t *deviceCount | [出参] 指向返回设备数量的指针。成功时，该值被设置为数组中的<br>元素个数。为0表示当前没有设备。不得为空。 |

**释放资源：** 调用[OH_UsbManager_FreeUsbDeviceList](capi-ohusb-manager-h.md#oh_usbmanager_freeusbdevicelist)释放devices。

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_UsbManager_ErrorCode](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) | [OH_USBMANAGER_SUCCESS](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) 表示操作成功。      <br>[OH_USBMANAGER_ERROR_SERVICE_EXCEPTION](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) 表示USB服务不可用。可能原因：USB服务故障，例如服务未运行或意外停止。      <br>[OH_USBMANAGER_ERROR_NO_MEMORY](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) 表示设备数组或字符串的内存分配失败。可能原因：系统内存不足或连接的设备过多。处理建议：释放未使用的内存后重试。      <br>[OH_USBMANAGER_ERROR_INVALID_PARAMETER](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) 表示devices或deviceCount为NULL。可能原因：未提供必需的参数。处理建议：传入有效的非空指针。 |

### OH_UsbManager_FreeUsbDeviceList()

```c
void OH_UsbManager_FreeUsbDeviceList(OH_UsbManager_UsbDevice *devices, uint32_t deviceCount)
```

**描述：**

释放之前由[OH_UsbManager_GetUsbDeviceList](capi-ohusb-manager-h.md#oh_usbmanager_getusbdevicelist)返回的设备数组。<br>调用后该指针失效，不得再使用。传入null或数量为0是安全的空操作。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_UsbManager_UsbDevice](capi-usbmanager-oh-usbmanager-usbdevice.md) *devices | [入参] 指向由[OH_UsbManager_GetUsbDeviceList](capi-ohusb-manager-h.md#oh_usbmanager_getusbdevicelist)返回的数组的指针。 |
| uint32_t deviceCount | [入参] 数组中的元素个数，由[OH_UsbManager_GetUsbDeviceList](capi-ohusb-manager-h.md#oh_usbmanager_getusbdevicelist)<br>返回。 |

### OH_UsbManager_ConnectDevice()

```c
OH_UsbManager_ErrorCode OH_UsbManager_ConnectDevice(const OH_UsbManager_UsbDevice *device, OH_UsbManager_UsbPipe *pipe)
```

**描述：**

连接USB设备并打开用于通信的管道。返回的管道必须通过调用<br>[OH_UsbManager_ClosePipe](capi-ohusb-manager-h.md#oh_usbmanager_closepipe)关闭，以避免资源泄漏。<br>仅需要设备结构体中的**busNum**和**devAddress**字段；其他字段将被忽略。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_UsbManager_UsbDevice](capi-usbmanager-oh-usbmanager-usbdevice.md) *device | [入参] 指向要连接的[OH_UsbManager_UsbDevice](capi-usbmanager-oh-usbmanager-usbdevice.md)的指针。不得为空。 |
| [OH_UsbManager_UsbPipe](capi-usbmanager-oh-usbmanager-usbpipe.md) *pipe | [出参] 指向[OH_UsbManager_UsbPipe](capi-usbmanager-oh-usbmanager-usbpipe.md)的指针，成功时用于接收<br>句柄。不得为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_UsbManager_ErrorCode](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) | [OH_USBMANAGER_SUCCESS](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) 表示连接成功。      <br>[OH_USBMANAGER_ERROR_PERMISSION_DENIED](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) 表示应用缺少设备访问权限。      <br>可能原因：尚未请求访问权限、权限已被撤销，或用户拒绝了请求。      <br>处理建议：调用[OH_UsbManager_RequestPermission](capi-ohusb-manager-h.md#oh_usbmanager_requestpermission)请求访问权限。      <br>[OH_USBMANAGER_ERROR_SERVICE_EXCEPTION](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) 表示USB服务打开设备失败。      <br>可能原因：USB服务故障（例如服务未运行或意外停止），或传入的device无效。      <br>处理建议：如果device无效，请先通过[OH_UsbManager_GetUsbDeviceList](capi-ohusb-manager-h.md#oh_usbmanager_getusbdevicelist)      <br>获取有效的设备数据后重试。      <br>[OH_USBMANAGER_ERROR_IO_ERROR](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) 表示无法打开设备（如已断开连接或发生I/O失败）。      <br>可能原因：设备已断开连接或USB总线发生I/O错误。      <br>处理建议：检查物理连接和设备状态后重试。      <br>[OH_USBMANAGER_ERROR_INVALID_PARAMETER](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) 表示device或pipe为NULL。      <br>可能原因：未提供必需的参数。处理建议：传入有效的非空指针。 |

### OH_UsbManager_HasPermission()

```c
OH_UsbManager_ErrorCode OH_UsbManager_HasPermission(const char *deviceName, bool *result)
```

**描述：**

检查应用是否有权限访问指定设备。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *deviceName | [入参] 设备名称，格式为<总线编号>-<设备地址>。不得为空。 |
| bool *result | [出参] 用于接收结果的指针。如果应用已被授予访问设备的权限<br>则为true；如果权限未被授予或未被请求则为false。不得为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_UsbManager_ErrorCode](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) | [OH_USBMANAGER_SUCCESS](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) 表示操作成功。      <br>[OH_USBMANAGER_ERROR_SERVICE_EXCEPTION](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) 表示USB服务不可用。      <br>可能原因：USB服务故障（例如服务未运行或意外停止），或传入的deviceName无效。      <br>处理建议：如果deviceName无效，请先通过[OH_UsbManager_GetUsbDeviceList](capi-ohusb-manager-h.md#oh_usbmanager_getusbdevicelist)      <br>获取有效的设备名称后重试。      <br>[OH_USBMANAGER_ERROR_INVALID_PARAMETER](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) 表示deviceName或result为NULL。      <br>可能原因：未提供必需的参数。处理建议：传入有效的非空指针。 |

### OH_UsbManager_PermissionCallback()

```c
typedef void (*OH_UsbManager_PermissionCallback)(OH_UsbManager_ErrorCode errorCode, bool result, void *userContext)
```

**描述：**

定义用于返回[OH_UsbManager_RequestPermission](capi-ohusb-manager-h.md#oh_usbmanager_requestpermission)结果的<br>回调类型。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_UsbManager_ErrorCode](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) errorCode | [出参] 请求的错误码。[OH_USBMANAGER_SUCCESS](capi-ohusb-manager-h.md#oh_usbmanager_errorcode)表示请求<br>正常完成；其他值表示服务异常。 |
| bool result | [出参] 如果权限被授予则为true；如果用户拒绝请求则为false。<br>该参数仅在errorCode为[OH_USBMANAGER_SUCCESS](capi-ohusb-manager-h.md#oh_usbmanager_errorcode)时有意义。 |
| void \*userContext | [出参] 从[OH_UsbManager_RequestPermission](capi-ohusb-manager-h.md#oh_usbmanager_requestpermission)透传的用户上下文。 |

### OH_UsbManager_RequestPermission()

```c
OH_UsbManager_ErrorCode OH_UsbManager_RequestPermission(const char *deviceName, OH_UsbManager_PermissionCallback callback, void *userContext)
```

**描述：**

异步请求访问指定USB设备的权限。这可能触发系统弹窗询问用户是否授权。<br>函数立即返回，结果通过回调传递。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *deviceName | [入参] 设备名称，格式为<总线编号>-<设备地址>。不得为空。 |
| [OH_UsbManager_PermissionCallback](capi-ohusb-manager-h.md#oh_usbmanager_permissioncallback) callback | [入参] 请求完成时调用的[OH_UsbManager_PermissionCallback](capi-ohusb-manager-h.md#oh_usbmanager_permissioncallback)。<br>不得为空。 |
| void *userContext | [入参] 传递给回调的用户上下文指针。可以为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_UsbManager_ErrorCode](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) | [OH_USBMANAGER_SUCCESS](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) 表示请求成功发起。      <br>[OH_USBMANAGER_ERROR_SERVICE_EXCEPTION](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) 表示服务启动请求失败。      <br>可能原因：USB服务故障（例如服务未运行或意外停止），或传入的deviceName无效。      <br>处理建议：如果deviceName无效，请先通过[OH_UsbManager_GetUsbDeviceList](capi-ohusb-manager-h.md#oh_usbmanager_getusbdevicelist)      <br>获取有效的设备名称后重试。      <br>[OH_USBMANAGER_ERROR_INVALID_PARAMETER](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) 表示deviceName或callback为NULL。      <br>可能原因：未提供必需的参数。处理建议：传入有效的非空指针。 |

### OH_UsbManager_GetFileDescriptor()

```c
OH_UsbManager_ErrorCode OH_UsbManager_GetFileDescriptor(const OH_UsbManager_UsbPipe *pipe, int32_t *fd)
```

**描述：**

获取已打开USB设备管道的文件描述符。该fd可用于基于ioctl的<br>低层USB传输。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_UsbManager_UsbPipe](capi-usbmanager-oh-usbmanager-usbpipe.md) *pipe | [入参] 指向从[OH_UsbManager_ConnectDevice](capi-ohusb-manager-h.md#oh_usbmanager_connectdevice)获取的<br>[OH_UsbManager_UsbPipe](capi-usbmanager-oh-usbmanager-usbpipe.md)的指针。不得为空。 |
| int32_t *fd | [出参] 用于在成功时接收文件描述符的指针。不得为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_UsbManager_ErrorCode](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) | [OH_USBMANAGER_SUCCESS](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) 表示操作成功。      <br>[OH_USBMANAGER_ERROR_PERMISSION_DENIED](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) 表示应用缺少设备访问权限。      <br>可能原因：尚未请求访问权限、权限已被撤销，或用户拒绝了请求。      <br>处理建议：调用[OH_UsbManager_RequestPermission](capi-ohusb-manager-h.md#oh_usbmanager_requestpermission)请求访问权限。      <br>[OH_USBMANAGER_ERROR_SERVICE_EXCEPTION](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) 表示管道无效或服务失败。      <br>可能原因：USB服务故障，或管道并非通过[OH_UsbManager_ConnectDevice](capi-ohusb-manager-h.md#oh_usbmanager_connectdevice)获取、      <br>或管道已被关闭。处理建议：如果管道无效或已关闭，请通过      <br>[OH_UsbManager_ConnectDevice](capi-ohusb-manager-h.md#oh_usbmanager_connectdevice)获取有效的打开管道后重试。      <br>[OH_USBMANAGER_ERROR_NO_DEVICE](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) 表示设备不存在或已断开连接。      <br>可能原因：设备已被拔出。处理建议：使用[OH_UsbManager_GetUsbDeviceList](capi-ohusb-manager-h.md#oh_usbmanager_getusbdevicelist)      <br>重新枚举设备并重新连接。      <br>[OH_USBMANAGER_ERROR_INVALID_PARAMETER](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) 表示pipe或fd为NULL。      <br>可能原因：未提供必需的参数。处理建议：传入有效的非空指针。 |

### OH_UsbManager_ClosePipe()

```c
OH_UsbManager_ErrorCode OH_UsbManager_ClosePipe(const OH_UsbManager_UsbPipe *pipe)
```

**描述：**

关闭USB设备管道并释放底层资源。该管道必须从[OH_UsbManager_ConnectDevice](capi-ohusb-manager-h.md#oh_usbmanager_connectdevice)<br>获取。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_UsbManager_UsbPipe](capi-usbmanager-oh-usbmanager-usbpipe.md) *pipe | [入参] 指向要关闭的、从[OH_UsbManager_ConnectDevice](capi-ohusb-manager-h.md#oh_usbmanager_connectdevice)获取的<br>[OH_UsbManager_UsbPipe](capi-usbmanager-oh-usbmanager-usbpipe.md)的指针。不得为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_UsbManager_ErrorCode](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) | [OH_USBMANAGER_SUCCESS](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) 表示管道关闭成功。      <br>[OH_USBMANAGER_ERROR_PERMISSION_DENIED](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) 表示应用缺少设备访问权限。      <br>可能原因：尚未请求访问权限、权限已被撤销，或用户拒绝了请求。      <br>处理建议：调用[OH_UsbManager_RequestPermission](capi-ohusb-manager-h.md#oh_usbmanager_requestpermission)请求访问权限。      <br>[OH_USBMANAGER_ERROR_SERVICE_EXCEPTION](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) 表示关闭操作失败。      <br>可能原因：USB服务故障，或管道无效或已被关闭。处理建议：如果管道无效或已关闭，      <br>请通过[OH_UsbManager_ConnectDevice](capi-ohusb-manager-h.md#oh_usbmanager_connectdevice)获取有效的打开管道后重试。      <br>[OH_USBMANAGER_ERROR_INVALID_PARAMETER](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) 表示pipe为NULL。      <br>可能原因：未提供必需的参数。处理建议：传入有效的非空指针。 |


