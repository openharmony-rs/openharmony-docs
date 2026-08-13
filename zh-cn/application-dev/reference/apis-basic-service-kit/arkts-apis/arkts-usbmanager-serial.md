# @ohos.usbManager.serial

/*
 Copyright (c) 2026 Huawei Device Co., Ltd.
 Licensed under the Apache License, Version 2.0 (the "License"),
 you may not use this file except in compliance with the License.
 You may obtain a copy of the License at
 http://www.apache.org/licenses/LICENSE-2.0
 Unless required by applicable law or agreed to in writing, software
 distributed under the License is distributed on an "AS IS" BASIS,
 WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 See the License for the specific language governing permissions and
 limitations under the License.
 /


**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace serialManager--><!--Device-unnamed-declare namespace serialManager-End-->

**系统能力：** SystemCapability.USB.USBManager.Serial

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [cancelSerialRight](arkts-basicservices-serialmanager-cancelserialright-f.md#cancelSerialRight) | 移除应用程序运行时访问串口设备的权限。此接口会调用close关闭已打开的串口。 |
| [close](arkts-basicservices-serialmanager-close-f.md#close) | 关闭串口。 |
| [getAttribute](arkts-basicservices-serialmanager-getattribute-f.md#getAttribute) | 获取指定串口的配置参数。 |
| [getPortList](arkts-basicservices-serialmanager-getportlist-f.md#getPortList) | 查询串口设备清单，包括设备名称和对应的端口号。 |
| [hasSerialRight](arkts-basicservices-serialmanager-hasserialright-f.md#hasSerialRight) | 检查应用程序是否具有访问串口设备的权限。应用退出后再拉起时，需要重新申请授权。 |
| [open](arkts-basicservices-serialmanager-open-f.md#open) | 打开串口设备。 |
| [read](arkts-basicservices-serialmanager-read-f.md#read) | 从串口设备异步读取数据。使用Promise异步回调。 |
| [readSync](arkts-basicservices-serialmanager-readsync-f.md#readSync) | 从串口设备同步读取数据。 |
| [requestSerialRight](arkts-basicservices-serialmanager-requestserialright-f.md#requestSerialRight) | 请求应用程序访问串口设备的权限。应用退出自动移除对串口设备的访问权限，在应用重启后需要重新申请授权。使用Promise异步回调。 |
| [setAttribute](arkts-basicservices-serialmanager-setattribute-f.md#setAttribute) | 设置串口的配置参数。如果未调用该方法，使用默认配置参数（波特率：9600bps；数据位：8；校验位：0；停止位：1）。 |
| [write](arkts-basicservices-serialmanager-write-f.md#write) | 向串口设备异步写数据，每次写入数据长度不超过4KB，数据过大会导致数据丢失，长数据建议分包写入。使用Promise异步回调。 |
| [writeSync](arkts-basicservices-serialmanager-writesync-f.md#writeSync) | 向串口设备同步写数据，每次写入数据长度不超过4KB，数据过大会导致数据丢失，长数据建议分包写入。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [addSerialRight](arkts-basicservices-serialmanager-addserialright-f-sys.md#addSerialRight) | 为应用程序添加访问串口设备权限。 serialManager.requestSerialRight会触发弹窗请求用户授权；addSerialRight不会触发弹窗，而是直接添加应用程序访问设备的权限。应用退出自动移除对串口设备的访问权限，在应用重启后需要重新申请授 权。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [SerialAttribute](arkts-basicservices-serialmanager-serialattribute-i.md) | 串口的配置参数。 |
| [SerialPort](arkts-basicservices-serialmanager-serialport-i.md) | 串口参数。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [BaudRates](arkts-basicservices-serialmanager-baudrates-e.md) | Enumerates the baud rates. |
| [DataBits](arkts-basicservices-serialmanager-databits-e.md) | Enumerates the number of data bits. |
| [Parity](arkts-basicservices-serialmanager-parity-e.md) | Enumerates the parity check modes. |
| [StopBits](arkts-basicservices-serialmanager-stopbits-e.md) | Enumerates of the number of stop bits. |

