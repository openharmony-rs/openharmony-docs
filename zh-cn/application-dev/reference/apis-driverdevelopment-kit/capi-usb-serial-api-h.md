# usb_serial_api.h
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @lixinsheng2-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @w_Machine_cc-->

## 概述

声明用于主机侧访问串口设备的USB Serial DDK接口。

**引用文件：** <usb_serial/usb_serial_api.h>

**库：** libusb_serial.z.so

**系统能力：** SystemCapability.Driver.UsbSerial.Extension

**起始版本：** 18

**相关模块：** [SerialDdk](capi-serialddk.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [int32_t OH_UsbSerial_Init(void)](#oh_usbserial_init) | 初始化USB Serial DDK。 |
| [int32_t OH_UsbSerial_Release(void)](#oh_usbserial_release) | 释放USB Serial DDK。 |
| [int32_t OH_UsbSerial_Open(uint64_t deviceId, uint8_t interfaceIndex, UsbSerial_DeviceHandle **dev)](#oh_usbserial_open) | 通过deviceId和interfaceIndex打开USB串口设备。 |
| [int32_t OH_UsbSerial_Close(UsbSerial_DeviceHandle *dev)](#oh_usbserial_close) | 关闭USB串口设备。 |
| [int32_t OH_UsbSerial_Read(UsbSerial_DeviceHandle *dev, uint8_t *buff, uint32_t bufferSize, uint32_t *bytesRead)](#oh_usbserial_read) | 从USB串口设备读入数据到缓冲区。 |
| [int32_t OH_UsbSerial_Write(UsbSerial_DeviceHandle *dev, uint8_t *buff, uint32_t bufferSize, uint32_t *bytesWritten)](#oh_usbserial_write) | 将buff中的数据写入USB串口设备。 |
| [int32_t OH_UsbSerial_SetBaudRate(UsbSerial_DeviceHandle *dev, uint32_t baudRate)](#oh_usbserial_setbaudrate) | 设置USB串口设备的波特率。如果USB串口设备的参数为默认值（数据位为8，停止位为1，数据传输无校验），则只需要调用该接口设置波特率。 |
| [int32_t OH_UsbSerial_SetParams(UsbSerial_DeviceHandle *dev, UsbSerial_Params *params)](#oh_usbserial_setparams) | 设置USB串口设备的参数。如果USB串口设备的参数不为默认值（数据位默认为8，停止位默认为1，数据传输默认无校验），则需要调用该接口进行参数设置。 |
| [int32_t OH_UsbSerial_SetTimeout(UsbSerial_DeviceHandle *dev, int timeout)](#oh_usbserial_settimeout) | 设置读取USB串口设备上报数据的超时时间（毫秒）。在不调用此函数的情况下，超时值默认为0，表示不管是否读取到数据都立即返回。如果需要等待一定的时间或者必须读取到数据，则调用该接口。 |
| [int32_t OH_UsbSerial_SetFlowControl(UsbSerial_DeviceHandle *dev, UsbSerial_FlowControl flowControl)](#oh_usbserial_setflowcontrol) | 设置流控参数。USB串口设备通信中的流控用于管理数据传输的速率，以确保发送方不会发送超过接收方处理能力的数据量。<br> 如果USB串口设备实现了流控处理，则需要调用此接口。如果不调用此接口，默认为无流控。 |
| [int32_t OH_UsbSerial_Flush(UsbSerial_DeviceHandle *dev)](#oh_usbserial_flush) | 写入完成后清空输入和输出缓冲区。在向USB串口设备发送数据时，可能会有大量数据缓冲在内核中等待发送。如果应用程序关闭文件描述符或者退出之前<br> 没有等待这些数据被实际发送出去，那么部分数据可能会丢失。调用该接口可以确保所有的数据都被发送完毕再继续执行后续操作。 |
| [int32_t OH_UsbSerial_FlushInput(UsbSerial_DeviceHandle *dev)](#oh_usbserial_flushinput) | 刷新输入缓冲区，缓冲区中的数据会被立刻清空。在和USB串口设备通信过程中，特别是在调试阶段，有时会遇到乱序的数据包或者其他异常情况。<br> 调用该接口可以帮助清理这些异常状况，使通信恢复正常。 |
| [int32_t OH_UsbSerial_FlushOutput(UsbSerial_DeviceHandle *dev)](#oh_usbserial_flushoutput) | 刷新输出缓冲区，缓冲区中的数据会被立刻清空。在和USB串口设备通信过程中，特别是在调试阶段，有时会遇到乱序的数据包或者其他异常情况。<br> 调用该接口可以帮助清理这些异常状况，使通信恢复正常。 |

## 函数说明

### OH_UsbSerial_Init()

```
int32_t OH_UsbSerial_Init(void)
```

**描述**

初始化USB Serial DDK。

**需要权限：** ohos.permission.ACCESS_DDK_USB_SERIAL

**起始版本：** 18

**返回：**

| 类型 | 说明                                                                                                                                                                                                                                |
| -- |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| int32_t | [USB_SERIAL_DDK_SUCCESS](capi-usb-serial-types-h.md#usbserial_ddkretcode) 调用接口成功。<br>         [USB_SERIAL_DDK_NO_PERM](capi-usb-serial-types-h.md#usbserial_ddkretcode) 权限校验失败。<br>         [USB_SERIAL_DDK_INIT_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) 初始化DDK失败。 |

### OH_UsbSerial_Release()

```
int32_t OH_UsbSerial_Release(void)
```

**描述**

释放USB Serial DDK。

**需要权限：** ohos.permission.ACCESS_DDK_USB_SERIAL

**起始版本：** 18

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [USB_SERIAL_DDK_SUCCESS](capi-usb-serial-types-h.md#usbserial_ddkretcode) 调用接口成功。<br>         [USB_SERIAL_DDK_NO_PERM](capi-usb-serial-types-h.md#usbserial_ddkretcode) 权限校验失败。<br>         [USB_SERIAL_DDK_INIT_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) 未初始化DDK。<br>         [USB_SERIAL_DDK_SERVICE_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) DDK服务通信失败。 |

### OH_UsbSerial_Open()

```
int32_t OH_UsbSerial_Open(uint64_t deviceId, uint8_t interfaceIndex, UsbSerial_DeviceHandle **dev)
```

**描述**

通过deviceId和interfaceIndex打开USB串口设备。

**需要权限：** ohos.permission.ACCESS_DDK_USB_SERIAL

**起始版本：** 18


**参数：**

| 参数项                              | 描述                                         |
|----------------------------------|--------------------------------------------|
| uint64_t deviceId                | 设备ID，代表要操作的设备。                             |
| uint8_t interfaceIndex           | 接口索引，对应USB协议中的[bInterfaceNumber](capi-usbddk-usbinterfacedescriptor.md)。 |
| [UsbSerial_DeviceHandle](capi-serialddk-usbserial-devicehandle.md) **dev | 设备句柄。                                      |

**返回：**

| 类型 | 说明                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| -- |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| int32_t | [USB_SERIAL_DDK_SUCCESS](capi-usb-serial-types-h.md#usbserial_ddkretcode) 调用接口成功。<br>         [USB_SERIAL_DDK_NO_PERM](capi-usb-serial-types-h.md#usbserial_ddkretcode) 权限校验失败。<br>         [USB_SERIAL_DDK_INVALID_PARAMETER](capi-usb-serial-types-h.md#usbserial_ddkretcode) 参数检查失败。可能原因为：dev为空指针。<br>         [USB_SERIAL_DDK_INIT_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) 未初始化DDK。<br>         [USB_SERIAL_DDK_SERVICE_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) DDK服务通信失败。<br>         [USB_SERIAL_DDK_MEMORY_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) 内存不足。<br>         [USB_SERIAL_DDK_IO_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) DDK发生I/O错误。<br>         [USB_SERIAL_DDK_DEVICE_NOT_FOUND](capi-usb-serial-types-h.md#usbserial_ddkretcode) 找不到设备或接口。 |

### OH_UsbSerial_Close()

```
int32_t OH_UsbSerial_Close(UsbSerial_DeviceHandle *dev)
```

**描述**

关闭USB串口设备。

**需要权限：** ohos.permission.ACCESS_DDK_USB_SERIAL

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [UsbSerial_DeviceHandle](capi-serialddk-usbserial-devicehandle.md) *dev | 设备句柄。 |

**返回：**

| 类型 | 说明                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| -- |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| int32_t | [USB_SERIAL_DDK_SUCCESS](capi-usb-serial-types-h.md#usbserial_ddkretcode) 调用接口成功。<br>         [USB_SERIAL_DDK_NO_PERM](capi-usb-serial-types-h.md#usbserial_ddkretcode) 权限校验失败。<br>         [USB_SERIAL_DDK_INVALID_PARAMETER](capi-usb-serial-types-h.md#usbserial_ddkretcode) 参数检查失败。可能原因：dev为空指针。<br>         [USB_SERIAL_DDK_INIT_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) 未初始化DDK。<br>         [USB_SERIAL_DDK_SERVICE_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) DDK服务通信失败。<br>         [USB_SERIAL_DDK_IO_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) DDK发生I/O错误。<br>         [USB_SERIAL_DDK_INVALID_OPERATION](capi-usb-serial-types-h.md#usbserial_ddkretcode) 无效操作。 |

### OH_UsbSerial_Read()

```
int32_t OH_UsbSerial_Read(UsbSerial_DeviceHandle *dev, uint8_t *buff, uint32_t bufferSize, uint32_t *bytesRead)
```

**描述**

从USB串口设备读入数据到缓冲区。

**需要权限：** ohos.permission.ACCESS_DDK_USB_SERIAL

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [UsbSerial_DeviceHandle](capi-serialddk-usbserial-devicehandle.md) *dev | 设备句柄。 |
| uint8_t *buff | 保存从USB串口设备读取数据的缓冲区。 |
| uint32_t bufferSize | 缓冲区的大小。 |
| uint32_t *bytesRead | 实际读取的字节数，如果设置了阻塞模式，则实际读取到的数据等于bufferSize后才会返回，<br>                  详见[OH_UsbSerial_SetTimeout](capi-usb-serial-api-h.md#oh_usbserial_settimeout)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [USB_SERIAL_DDK_SUCCESS](capi-usb-serial-types-h.md#usbserial_ddkretcode) 调用接口成功。<br>         [USB_SERIAL_DDK_NO_PERM](capi-usb-serial-types-h.md#usbserial_ddkretcode) 权限校验失败。<br>         [USB_SERIAL_DDK_INVALID_PARAMETER](capi-usb-serial-types-h.md#usbserial_ddkretcode) 参数检查失败。可能原因：1. dev为空指针;<br>         2. buff为空指针; 3. bufferSize等于0; 4. bytesRead为空指针。<br>         [USB_SERIAL_DDK_INIT_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) 未初始化DDK。<br>         [USB_SERIAL_DDK_SERVICE_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) DDK服务通信失败。<br>         [USB_SERIAL_DDK_MEMORY_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) buff地址无效。<br>         [USB_SERIAL_DDK_IO_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) DDK发生I/O错误。<br>         [USB_SERIAL_DDK_INVALID_OPERATION](capi-usb-serial-types-h.md#usbserial_ddkretcode) 无效操作。 |

### OH_UsbSerial_Write()

```
int32_t OH_UsbSerial_Write(UsbSerial_DeviceHandle *dev, uint8_t *buff, uint32_t bufferSize, uint32_t *bytesWritten)
```

**描述**

将buff中的数据写入USB串口设备。

**需要权限：** ohos.permission.ACCESS_DDK_USB_SERIAL

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [UsbSerial_DeviceHandle](capi-serialddk-usbserial-devicehandle.md) *dev | 设备句柄。 |
| uint8_t *buff | 写入USB串口设备数据的缓冲区。 |
| uint32_t bufferSize | 缓冲区的大小。 |
| uint32_t *bytesWritten | 实际写入的字节数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [USB_SERIAL_DDK_SUCCESS](capi-usb-serial-types-h.md#usbserial_ddkretcode) 调用接口成功。<br>         [USB_SERIAL_DDK_NO_PERM](capi-usb-serial-types-h.md#usbserial_ddkretcode) 权限校验失败。<br>         [USB_SERIAL_DDK_INVALID_PARAMETER](capi-usb-serial-types-h.md#usbserial_ddkretcode) 参数检查失败。可能原因：1. dev为空指针;<br>         2. buff为空指针; 3. bufferSize等于0; 4. bytesWritten为空指针。<br>         [USB_SERIAL_DDK_INIT_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) 未初始化DDK。<br>         [USB_SERIAL_DDK_SERVICE_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) DDK服务通信失败。<br>         [USB_SERIAL_DDK_MEMORY_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) buff地址无效。<br>         [USB_SERIAL_DDK_IO_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) DDK发生I/O错误。<br>         [USB_SERIAL_DDK_INVALID_OPERATION](capi-usb-serial-types-h.md#usbserial_ddkretcode) 无效操作。 |

### OH_UsbSerial_SetBaudRate()

```
int32_t OH_UsbSerial_SetBaudRate(UsbSerial_DeviceHandle *dev, uint32_t baudRate)
```

**描述**

设置USB串口设备的波特率。如果USB串口设备的参数为默认值（数据位为8，停止位为1，数据传输无校验），则只需要调用该接口设置波特率。

**需要权限：** ohos.permission.ACCESS_DDK_USB_SERIAL

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [UsbSerial_DeviceHandle](capi-serialddk-usbserial-devicehandle.md) *dev | 设备句柄。 |
| uint32_t baudRate | USB串口设备的波特率。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [USB_SERIAL_DDK_SUCCESS](capi-usb-serial-types-h.md#usbserial_ddkretcode) 调用接口成功。<br>         [USB_SERIAL_DDK_NO_PERM](capi-usb-serial-types-h.md#usbserial_ddkretcode) 权限校验失败。<br>         [USB_SERIAL_DDK_INVALID_PARAMETER](capi-usb-serial-types-h.md#usbserial_ddkretcode)参数检查失败。可能原因：dev为空指针。<br>         [USB_SERIAL_DDK_INIT_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) 未初始化DDK。<br>         [USB_SERIAL_DDK_SERVICE_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) DDK服务通信失败。<br>         [USB_SERIAL_DDK_IO_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) DDK发生I/O错误。<br>         [USB_SERIAL_DDK_INVALID_OPERATION](capi-usb-serial-types-h.md#usbserial_ddkretcode) 无效操作。 |

### OH_UsbSerial_SetParams()

```
int32_t OH_UsbSerial_SetParams(UsbSerial_DeviceHandle *dev, UsbSerial_Params *params)
```

**描述**

设置USB串口设备的参数。如果USB串口设备的参数不为默认值（数据位默认为8，停止位默认为1，数据传输默认无校验），则需要调用该接口进行参数设置。

**需要权限：** ohos.permission.ACCESS_DDK_USB_SERIAL

**起始版本：** 18


**参数：**

| 参数项                                                                     | 描述 |
|-------------------------------------------------------------------------| -- |
| [UsbSerial_DeviceHandle](capi-serialddk-usbserial-devicehandle.md) *dev | 设备句柄。 |
| [UsbSerial_Params](capi-serialddk-usbserial-params.md) *params                                            | 待设置的USB串口设备参数，详见[UsbSerial_Params](capi-serialddk-usbserial-params.md)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [USB_SERIAL_DDK_SUCCESS](capi-usb-serial-types-h.md#usbserial_ddkretcode) 调用接口成功。<br>         [USB_SERIAL_DDK_NO_PERM](capi-usb-serial-types-h.md#usbserial_ddkretcode) 权限校验失败。<br>         [USB_SERIAL_DDK_INVALID_PARAMETER](capi-usb-serial-types-h.md#usbserial_ddkretcode) 参数检查失败。可能原因：1. dev为空指针;<br>         2. params为空指针。<br>         [USB_SERIAL_DDK_INIT_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) 未初始化DDK。<br>         [USB_SERIAL_DDK_SERVICE_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) DDK服务通信失败。<br>         [USB_SERIAL_DDK_IO_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) DDK发生I/O错误。<br>         [USB_SERIAL_DDK_INVALID_OPERATION](capi-usb-serial-types-h.md#usbserial_ddkretcode) 无效操作。 |

### OH_UsbSerial_SetTimeout()

```
int32_t OH_UsbSerial_SetTimeout(UsbSerial_DeviceHandle *dev, int timeout)
```

**描述**

设置读取USB串口设备上报数据的超时时间（毫秒）。在不调用此函数的情况下，超时值默认为0，表示不管是否读取到数据都立即返回。如果需要等待一定的时间或者必须读取到数据，则调用该接口。

**需要权限：** ohos.permission.ACCESS_DDK_USB_SERIAL

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [UsbSerial_DeviceHandle](capi-serialddk-usbserial-devicehandle.md) *dev | 设备句柄。 |
| int timeout | 读取USB串口设备的超时时间，其取值范围为：- (0, 25500]：以毫秒为单位的时间值，将其四舍五入为最接近的100毫秒后，作为实际的超时时间。例如，输入12321，实际生效的超时时间为12300。- 0：表示立即返回数据，不等待。- -1：表示以阻塞方式读取数据，即读取数据时，只有读到指定长度的数据后才返回，详见[OH_UsbSerial_Read](capi-usb-serial-api-h.md#oh_usbserial_read)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [USB_SERIAL_DDK_SUCCESS](capi-usb-serial-types-h.md#usbserial_ddkretcode) 调用接口成功。<br>         [USB_SERIAL_DDK_NO_PERM](capi-usb-serial-types-h.md#usbserial_ddkretcode) 权限校验失败。<br>         [USB_SERIAL_DDK_INVALID_PARAMETER](capi-usb-serial-types-h.md#usbserial_ddkretcode) 参数检查失败。可能原因：1. dev为空指针;<br>         2. timeout < -1 or timeout > 25500.<br>         [USB_SERIAL_DDK_INIT_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) 未初始化DDK。<br>         [USB_SERIAL_DDK_SERVICE_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) DDK服务通信失败。<br>         [USB_SERIAL_DDK_IO_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) DDK发生I/O错误。<br>         [USB_SERIAL_DDK_INVALID_OPERATION](capi-usb-serial-types-h.md#usbserial_ddkretcode) 无效操作。 |

### OH_UsbSerial_SetFlowControl()

```
int32_t OH_UsbSerial_SetFlowControl(UsbSerial_DeviceHandle *dev, UsbSerial_FlowControl flowControl)
```

**描述**

设置流控参数。USB串口设备通信中的流控用于管理数据传输的速率，以确保发送方不会发送超过接收方处理能力的数据量。<br> 如果USB串口设备实现了流控处理，则需要调用此接口。如果不调用此接口，默认为无流控。

**需要权限：** ohos.permission.ACCESS_DDK_USB_SERIAL

**起始版本：** 18


**参数：**

| 参数项                                                                                   | 描述 |
|---------------------------------------------------------------------------------------| -- |
| [UsbSerial_DeviceHandle](capi-serialddk-usbserial-devicehandle.md) *dev               | 设备句柄。 |
| [UsbSerial_FlowControl](capi-usb-serial-types-h.md#usbserial_flowcontrol) flowControl | 流控方式，详见[UsbSerial_FlowControl](capi-usb-serial-types-h.md#usbserial_flowcontrol)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [USB_SERIAL_DDK_SUCCESS](capi-usb-serial-types-h.md#usbserial_ddkretcode) 调用接口成功。<br>         [USB_SERIAL_DDK_NO_PERM](capi-usb-serial-types-h.md#usbserial_ddkretcode) 权限校验失败。<br>         [USB_SERIAL_DDK_INVALID_PARAMETER](capi-usb-serial-types-h.md#usbserial_ddkretcode) 参数检查失败。可能原因：dev为空指针。<br>         [USB_SERIAL_DDK_INIT_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) 未初始化DDK。<br>         [USB_SERIAL_DDK_SERVICE_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) DDK服务通信失败。<br>         [USB_SERIAL_DDK_IO_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) DDK发生I/O错误。<br>         [USB_SERIAL_DDK_INVALID_OPERATION](capi-usb-serial-types-h.md#usbserial_ddkretcode) 无效操作。 |

### OH_UsbSerial_Flush()

```
int32_t OH_UsbSerial_Flush(UsbSerial_DeviceHandle *dev)
```

**描述**

写入完成后清空输入和输出缓冲区。在向USB串口设备发送数据时，可能会有大量数据缓冲在内核中等待发送。如果应用程序关闭文件描述符或者退出之前<br> 没有等待这些数据被实际发送出去，那么部分数据可能会丢失。调用该接口可以确保所有的数据都被发送完毕再继续执行后续操作。

**需要权限：** ohos.permission.ACCESS_DDK_USB_SERIAL

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [UsbSerial_DeviceHandle](capi-serialddk-usbserial-devicehandle.md) *dev | 设备句柄。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [USB_SERIAL_DDK_SUCCESS](capi-usb-serial-types-h.md#usbserial_ddkretcode) 调用接口成功。<br>         [USB_SERIAL_DDK_NO_PERM](capi-usb-serial-types-h.md#usbserial_ddkretcode) 权限校验失败。<br>         [USB_SERIAL_DDK_INVALID_PARAMETER](capi-usb-serial-types-h.md#usbserial_ddkretcode) 参数检查失败。可能原因：dev为空指针。<br>         [USB_SERIAL_DDK_INIT_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) 未初始化DDK。<br>         [USB_SERIAL_DDK_SERVICE_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) DDK服务通信失败。<br>         [USB_SERIAL_DDK_IO_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) DDK发生I/O错误。<br>         [USB_SERIAL_DDK_INVALID_OPERATION](capi-usb-serial-types-h.md#usbserial_ddkretcode) 无效操作。 |

### OH_UsbSerial_FlushInput()

```
int32_t OH_UsbSerial_FlushInput(UsbSerial_DeviceHandle *dev)
```

**描述**

刷新输入缓冲区，缓冲区中的数据会被立刻清空。在和USB串口设备通信过程中，特别是在调试阶段，有时会遇到乱序的数据包或者其他异常情况。<br> 调用该接口可以帮助清理这些异常状况，使通信恢复正常。

**需要权限：** ohos.permission.ACCESS_DDK_USB_SERIAL

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [UsbSerial_DeviceHandle](capi-serialddk-usbserial-devicehandle.md) *dev | 设备句柄。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [USB_SERIAL_DDK_SUCCESS](capi-usb-serial-types-h.md#usbserial_ddkretcode) 调用接口成功。<br>         [USB_SERIAL_DDK_NO_PERM](capi-usb-serial-types-h.md#usbserial_ddkretcode) 权限校验失败。<br>         [USB_SERIAL_DDK_INVALID_PARAMETER](capi-usb-serial-types-h.md#usbserial_ddkretcode) 参数检查失败。可能原因：dev为空指针。<br>         [USB_SERIAL_DDK_INIT_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) 未初始化DDK。<br>         [USB_SERIAL_DDK_SERVICE_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) DDK服务通信失败。<br>         [USB_SERIAL_DDK_IO_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) DDK发生I/O错误。<br>         [USB_SERIAL_DDK_INVALID_OPERATION](capi-usb-serial-types-h.md#usbserial_ddkretcode) 无效操作。 |

### OH_UsbSerial_FlushOutput()

```
int32_t OH_UsbSerial_FlushOutput(UsbSerial_DeviceHandle *dev)
```

**描述**

刷新输出缓冲区，缓冲区中的数据会被立刻清空。在和USB串口设备通信过程中，特别是在调试阶段，有时会遇到乱序的数据包或者其他异常情况。<br> 调用该接口可以帮助清理这些异常状况，使通信恢复正常。

**需要权限：** ohos.permission.ACCESS_DDK_USB_SERIAL

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [UsbSerial_DeviceHandle](capi-serialddk-usbserial-devicehandle.md) *dev | 设备句柄。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [USB_SERIAL_DDK_SUCCESS](capi-usb-serial-types-h.md#usbserial_ddkretcode) 调用接口成功。<br>         [USB_SERIAL_DDK_NO_PERM](capi-usb-serial-types-h.md#usbserial_ddkretcode) 权限校验失败。<br>         [USB_SERIAL_DDK_INVALID_PARAMETER](capi-usb-serial-types-h.md#usbserial_ddkretcode) 参数检查失败。可能原因：dev为空指针。<br>         [USB_SERIAL_DDK_INIT_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) 未初始化DDK。<br>         [USB_SERIAL_DDK_SERVICE_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) DDK服务通信失败。<br>         [USB_SERIAL_DDK_IO_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) DDK发生I/O错误。<br>         [USB_SERIAL_DDK_INVALID_OPERATION](capi-usb-serial-types-h.md#usbserial_ddkretcode) 无效操作。 |


