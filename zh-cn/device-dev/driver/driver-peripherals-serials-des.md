# OpenHarmony Serials HDI 模块设计文档

## 概述

### 文档目的
本文档描述OpenHarmony Serials HDI模块的详细设计方案，包括架构设计、接口定义、模块实现、线程模型、错误处理等内容，从OpenHarmony 7.0版本开始提供了这套串口设计方案

### 模块简介
Serials HDI模块为OpenHarmony系统提供串口通信的硬件驱动接口（HDI），支持：
- 串口设备的查询
- 串口设备的打开、关闭、配置
- 数据的异步读取与同步写入
- 设备热插拔事件通知
- 硬件流控制信号（RTS/CTS）操作

### 适用范围
- 板载硬件串口（ttyHW）
- USB串口设备（ttyUSB）
- 支持波特率范围：50 ~ 4000000 bps

---

## 架构设计

### 整体架构

```text
┌─────────────────────────────────────────────────────────────────┐
│                        Application Layer                        │
├─────────────────────────────────────────────────────────────────┤
│                     ISerials / ISerialDevice                    │
│                     (HDI Interface - IDL Generated)             │
├─────────────────────────────────────────────────────────────────┤
│                    SerialDeviceManager                          │
│    ┌──────────────┐  ┌──────────────┐  ┌──────────────────┐    │
│    │ SerialDevice │  │ UeventQueue  │  │ UeventHandle     │    │
│    │   (Device)   │  │  (Message)   │  │   (Netlink)      │    │
│    └──────────────┘  └──────────────┘  └──────────────────┘    │
├─────────────────────────────────────────────────────────────────┤
│                      Linux Kernel                               │
│                 (tty driver / USB serial driver)                │
└─────────────────────────────────────────────────────────────────┘
```

### 模块层次

| 层次 | 模块 | 职责 |
|------|------|------|
| 接口层 | ISerials / ISerialDevice | 定义标准HDI接口，供上层调用 |
| 管理层 | SerialDeviceManager | 设备管理、uevent处理、生命周期管理 |
| 实现层 | SerialDevice | 具体串口操作实现 |
| 消息层 | SerialUeventQueue | uevent消息队列，中转处理 |
| 事件层 | SerialUeventHandle | netlink socket监听，设备热插拔检测 |

### 目录结构

```text
drivers_peripheral_serial_new/serials/
├── include/
│   ├── serial_device.h            # SerialDevice类定义
│   ├── serial_device_manager.h    # SerialDeviceManager类定义
│   ├── serial_device_callback.h   # 回调实现类
│   ├── serial_uevent_handle.h     # uevent处理类
│   ├── serial_uevent_queue.h      # uevent消息队列
│   ├── serial_consts.h            # 常量定义
│   └── serial_hcb_util.h          # 配置解析工具
├── src/
│   ├── serial_device.cpp          # 串口设备实现
│   ├── serial_device_manager.cpp  # 设备管理实现
│   ├── serial_device_callback.cpp # 回调实现
│   ├── serial_uevent_handle.cpp   # uevent处理实现
│   ├── serial_uevent_queue.cpp    # 消息队列实现
│   ├── serial_service.cpp         # HDI服务入口
│   └── serial_hcb_util.cpp        # 配置解析实现
├── test/
│   ├── unittest/                  # 单元测试
│   ├── sample/                    # 示例程序
│   └── fuzztest/                  # 模糊测试
└── docs/
    └── SERIALS_DESIGN.md          # 设计文档
```

---

## 接口设计

### ISerials（服务接口）

```idl
interface ISerials {
    QueryDevices([out] SerialDeviceInfo[] devices);
    OpenDevice([in] String portName, [in] SerialConfig config, 
               [in] ISerialDeviceCallback cb, [out] ISerialDevice device);
}
```

| 方法 | 描述 |
|------|------|
| QueryDevices | 查询可用串口设备列表 |
| OpenDevice | 打开指定串口设备 |

### ISerialDevice（设备接口）

```idl
interface ISerialDevice {
    StartRead();
    StopRead();
    Close();
    Write([in] unsigned char[] data, [in] int timeout, [out] int bytesWritten);
    Flush();
    Drain();
    SendBrkSignal();
    SetRtsSignal([in] boolean rts);
    GetCtsSignal([out] boolean cts);
}
```

| 方法 | 描述 |
|------|------|
| StartRead | 启动异步读取线程 |
| StopRead | 停止读取线程 |
| Close | 关闭设备 |
| Write | 同步写入数据（支持循环写入） |
| Flush | 刷新缓冲区 |
| Drain | 等待所有写入完成 |
| SendBrkSignal | 发送BRK信号 |
| SetRtsSignal | 设置RTS信号 |
| GetCtsSignal | 获取CTS信号状态 |

### ISerialDeviceCallback（回调接口）

```idl
[callback] interface ISerialDeviceCallback {
    OnDeviceOffline();
    OnReadData([in] byte[] data, [in] unsigned int dataLen);
}
```

| 方法 | 描述 |
|------|------|
| OnDeviceOffline | 设备离线通知（热插拔移除） |
| OnReadData | 接收数据回调 |

### 数据结构

```idl
struct SerialDeviceInfo {
    String portName;       // 设备路径，如 "/dev/ttyUSB0"
    String manufacturer;   // 制造商名称
    String serialNumber;   // 序列号
    int productId;         // 产品ID
    int vendorId;          // 厂商ID
}

struct SerialConfig {
    int baudRate;    // 波特率
    int dataBits;    // 数据位（5/6/7/8）
    int stopBits;    // 停止位（1/2）
    int parity;      // 校验（0/1/2/3/4）
    boolean rtscts;  // 硬件流控
    boolean xon;     // XON软件流控
    boolean xoff;    // XOFF软件流控
    boolean xany;    // XANY软件流控
}
```

### 支持的波特率

| 常量 | 值 | 说明 |
|------|------|------|
| BR50 ~ BR4000000 | 50 ~ 4000000 | 标准波特率范围 |

---

## SerialDeviceManager模块详细设计

### 功能描述
- 单例模式，全局唯一实例
- 管理 `openDevices_`（已打开设备映射）
- 管理 `availableDevices_`（可用设备信息）
- 持有 `SerialUeventQueue` 和 `SerialUeventHandle`

### 核心流程

**设备查询流程：**
```text
QueryDevices()
    │
    ▼
扫描 /dev 目录
    │
    ├─► 匹配 ttyUSB* → AddVirtualUsbDevice()
    │       │
    │       ▼
    |   读取 /sys/class/tty/.../device/../../ 信息
    │   （manufacturer, serialNumber, vendorId, productId）
    │
    └─► 匹配 ttyHW* → AddNormalSerialDevice()
            │
            ▼
        检查supportTtyHws_配置
        添加到availableDevices_
```

**设备打开流程：**
```text
OpenDevice(portName, config, callback)
    │
    ▼
检查openDevices_是否已存在
    │
    ├─► 存在 → 返回HDF_ERR_DEVICE_BUSY
    │
    └─► 不存在 → 创建SerialDevice
            │
            ▼
        调用device->Open()
            │
            ▼
        加入openDevices_ 映射
```

## SerialDevice模块详细设计

### 成员变量

```cpp
class SerialDevice {
private:
    std::unique_ptr<SerialDeviceCallback> cb_;    // 回调对象
    std::string portName_;                         // 设备路径
    int32_t fd_;                                   // 文件描述符
    SerialConfig currentConfig_;                   // 当前配置
    std::atomic<bool> isOpen_;                     // 打开状态
    std::atomic<bool> startRead_;                  // 读取状态
    int stopPipe_[2];                              // StopRead信号pipe
    int closePipe_[2];                             // Close信号pipe
    mutable std::shared_mutex mutex_;              // 读写锁
    std::thread readThread_;                       // 读取线程
};
```

### Open流程

```text
Open()
    │
    ▼
打开设备文件 (O_RDWR | O_NOCTTY | O_NDELAY)
    │
    ▼
获取文件锁 (flock)
    │
    ▼
配置串口参数
    │
    ├─► SetBaudRateInternal()
    ├─► SetDataBitsInternal()
    ├─► SetStopBitsInternal()
    ├─► SetParityInternal()
    ├─► SetRtsCtsInternal()
    └─► SetXonXoffInternal()
    │
    ▼
InitPipes() 创建stopPipe和closePipe
    │
    ▼
isOpen_ = true
```

### Write流程（循环写入）

```text
Write(data, timeout, bytesWritten)
    │
    ▼
DoWriteLoop()
    │
    ▼
while (remaining > 0) {
    │
    ▼
    PollForWrite()
        │
        ├─► poll监听fd(POLLOUT) + closePipe(POLLIN)
        │
        ├─► 收到closePipe信号 → 返回HDF_ERR_DEVICE_BUSY
        │
        └─► fd可写 → 继续
    │
    ▼
    write(fd_, data + offset, remaining)
        │
        ├─► 返回 > 0 → 更新offset, remaining
        ├─► 返回 0 → 继续尝试
        └─► 返回 < 0 (EAGAIN) → 继续等待
}
```

### Read流程（异步读取）

```text
StartRead()
    │
    ▼
启动readThread_

ReadThread()
    │
    ▼
while (startRead_) {
    │
    ▼
    poll监听 [fd, stopPipe, closePipe]
        │
        ├─► 收到closePipe → 退出循环
        ├─► 收到stopPipe → 退出循环
        ├─► fd可读 → HandleReadEvent()
        │       │
        │       ▼
        │   read(fd_, buffer)
        │       │
        │       ▼
        │   cb_->OnReadData(buffer, len)
        │
        └─► POLLHUP → 设备离线
}
```

## SerialUeventHandle模块详细设计

### 功能描述
- 监听Linux netlink uevent事件
- 检测USB设备移除事件
- 通过pipe机制支持优雅退出

### 线程模型

```text
Init()
    │
    ▼
创建pipe（退出信号）
    │
    ▼
启动SerialUeventMain线程

SerialUeventMain()
    │
    ▼
InitUeventSocket() —— 创建netlink socket
    │
    ▼
ProcessEventLoop()
    │
    ▼
poll监听 [socketFd, pipeFd]
        │
        ├─► 收到pipe信号 → 退出
        │
        └─► 收到uevent → SerialHandleUevent()
                │
                ▼
            解析ACTION, DEVNAME, SUBSYSTEM等
                │
                ▼
            queue_->AddTask(info)
```

## SerialUeventQueue模块详细设计

### 功能描述
- 消息队列，中转uevent信息
- 避免直接在uevent线程中回调用户代码
- 使用条件变量实现生产者-消费者模式

### 流程

```text
AddTask(info)
    │
    ▼
加入 queue_，通知 cv_

ProcessThreadMain()
    │
    ▼
cv_.wait() 等待消息
    │
    ▼
取出消息，调用 callback_(info)
    │
    ▼
回调到SerialDeviceManager::OnUeventReceived()
```

---

## 线程模型

### 线程架构图

```text
┌────────────────────────────────────────────────────────────────┐
│                     SerialDeviceManager                        │
│                                                                │
│  ┌──────────────────┐         ┌──────────────────────────┐   │
│  │ UeventHandle     │         │ UeventQueue              │   │
│  │ ───────────────  │  AddTask │ ─────────────────────── │   │
│  │ SerialUeventMain │ ──────► │ ProcessThreadMain        │   │
│  │ (Thread 1)       │         │ (Thread 2)               │   │
│  └──────────────────┘         └──────────────────────────┘   │
│                                        │                      │
│                                        │ callback             │
│                                        ▼                      │
│                              OnUeventReceived()                │
│                                                                │
│  ┌──────────────────────────────────────────────────────────┐│
│  │ SerialDevice                                              ││
│  │ ──────────────────────────────────────────────────────── ││
│  │ ReadThread (Thread 3) - 异步读取                          ││
│  │                                                           ││
│  │ Write() - 同步写入（调用者线程）                           ││
│  └──────────────────────────────────────────────────────────┘│
└────────────────────────────────────────────────────────────────┘
```

### 线程说明

| 线程 | 所属类 | 职责 | 退出机制 |
|------|---------|------|----------|
| SerialUeventMain | SerialUeventHandle | 监听netlink uevent | pipe信号 |
| ProcessThreadMain | SerialUeventQueue | 处理uevent消息 | cv_ + running_标志 |
| ReadThread | SerialDevice | 异步读取串口数据 | stopPipe/closePipe |

### Pipe 信号机制

**SerialDevice 双 Pipe 设计：**

| Pipe | 信号来源 | 监听者 | 目的 |
|------|----------|--------|------|
| stopPipe | StopRead() | ReadThread | 停止读取(不影响Write) |
| closePipe | Close() | ReadThread + Write | 关闭设备（影响所有操作） |

```text
StopRead()                    Write()                      Close()
    │                            │                            │
    ▼                            ▼                            ▼
write 'S' → stopPipe       poll(fd, closePipe)         write 'C' → closePipe
    │                            │                            │
ReadThread:                      │                        ReadThread:
poll(fd, stopPipe, closePipe)    │                        poll检测到 'C'
    │                        检测到 'C' → 退出                │
检测到 'S' → 退出                  │                        Write:
    │                            │                        poll检测到 'C' → 退出
Read线程退出                写完数据后检测                    │
                                 │                        ClosePipes()
```

---

## 同步与并发

### 锁策略

| 类 | 锁类型 | 保护对象 |
|-----|--------|----------|
| SerialDeviceManager | std::mutex | openDevices_, availableDevices_, ueventQueue/Handle |
| SerialDevice | std::shared_mutex | fd_, isOpen_, config_ |
| SerialUeventQueue | std::mutex | queue_, callback_ |
| SerialUeventHandle | std::mutex | running_, socketFd_ |

### 原子变量

| 变量 | 用途 |
|------|------|
| isOpen_ | 设备打开状态 |
| startRead_ | 读取线程状态 |
| running_ | uevent线程状态 |

### 锁使用原则

- Write 使用shared_lock（读锁），允许并发查询状态
- Close 使用unique_lock（写锁），独占修改状态
- 回调执行期间解锁，避免死锁

---

## 错误处理

### 错误码定义

| 错误码 | 含义 |
|--------|------|
| HDF_SUCCESS | 操作成功 |
| HDF_ERR_INVALID_PARAM | 参数无效 |
| HDF_ERR_INVALID_OBJECT | 对象无效（设备未打开） |
| HDF_ERR_DEVICE_BUSY | 设备忙碌（已打开/正在关闭） |
| HDF_ERR_TIMEOUT | 操作超时 |
| HDF_ERR_IO | IO错误 |
| HDF_DEV_ERR_NO_DEVICE | 设备不存在/离线 |

### 错误处理策略

| 场景 | 处理方式 |
|------|----------|
| 设备未打开 | 返回HDF_ERR_INVALID_OBJECT |
| 重复打开 | 返回HDF_ERR_DEVICE_BUSY |
| 写入超时 | 返回HDF_ERR_TIMEOUT |
| 设备离线 | 回调OnDeviceOffline，返回HDF_DEV_ERR_NO_DEVICE |
| Close 信号 | Write/Read 返回HDF_ERR_DEVICE_BUSY |

---

## 设备热插拔

### uevent 监听

```text
Netlink Socket (AF_NETLINK, NETLINK_KOBJECT_UEVENT)
    │
    ▼
监听 "remove" action + "usb_device" devType
    │
    ▼
解析 DEVNAME(如 "ttyUSB0")
    │
    ▼
SerialUeventQueue.AddTask()
    │
    ▼
ProcessThreadMain 处理
    │
    ▼
SerialDeviceManager.OnUeventReceived()
    │
    ▼
查找openDevices_中匹配设备
    │
    ▼
调用device->NotifyDeviceOffline()
    │
    ▼
回调cb_->OnDeviceOffline()
```

### 设备移除流程

```text
USB设备物理移除
    │
    ▼
内核发送uevent (action="remove")
    │
    ▼
SerialUeventHandle接收
    │
    ▼
SerialUeventQueue中转
    │
    ▼
SerialDeviceManager查找已打开设备
    │
    ▼
SerialDevice.NotifyDeviceOffline()
    │
    ▼
ISerialDeviceCallback.OnDeviceOffline()
    │
    ▼
上层应用收到通知，清理资源
```

---

## 测试设计

### 单元测试（unittest）

| 测试用例 | 测试内容 |
|----------|----------|
| QueryDevices_001 | 查询设备列表 |
| OpenDevice_001~005 | 打开设备各种场景 |
| Write_001~003 | 写入数据测试 |
| StartRead_001~002 | 读取线程测试 |
| Close_001 | 关闭设备 |
| Flush/Drain/SendBrkSignal | 辅助功能测试 |
| SetRtsSignal/GetCtsSignal | 硬件流控制测试 |
| CloseBeforeStopRead | Close时自动停止Read |
| OperationAfterClose | 关闭后操作返回错误 |
| DeviceOfflineCallback | 设备离线回调 |
| MultipleDevices | 多设备并发 |

### 模糊测试（fuzztest）

- 使用FuzzedDataProvider生成随机数据
- 函数指针数组随机选择测试函数
- 覆盖所有接口的异常输入场景

### 示例程序（sample）

- 交互式菜单界面
- 支持配置修改、数据读写、Echo测试
- 展示完整使用流程

---

## 使用示例

### 基本使用流程

```cpp
#include "v1_0/iserials.h"
#include "v1_0/iserial_device_callback.h"

using namespace OHOS::HDI::Serials::V1_0;

class MyCallback : public ISerialDeviceCallback {
public:
    int32_t OnDeviceOffline() override {
        // 处理设备离线
        return HDF_SUCCESS;
    }
    
    int32_t OnReadData(const std::vector<int8_t>& data, uint32_t len) override {
        // 处理接收数据
        return HDF_SUCCESS;
    }
};

int main() {
    // 1. 获取服务
    sptr<ISerials> serials = ISerials::Get(true);
    
    // 2. 查询设备
    std::vector<SerialDeviceInfo> devices;
    serials->QueryDevices(devices);
    
    // 3. 配置参数
    SerialConfig config;
    config.baudRate = 115200;
    config.dataBits = 8;
    config.stopBits = 1;
    config.parity = 0;
    
    // 4. 打开设备
    sptr<ISerialDeviceCallback> callback = new MyCallback();
    sptr<ISerialDevice> device;
    serials->OpenDevice(devices[0].portName, config, callback, device);
    
    // 5. 启动读取
    device->StartRead();
    
    // 6. 写入数据
    std::vector<uint8_t> data = {0x01, 0x02, 0x03};
    int bytesWritten;
    device->Write(data, 1000, bytesWritten);
    
    // 7. 关闭设备
    device->StopRead();
    device->Close();
    
    return 0;
}
```

---

## 限制与约束

| 限制 | 说明 |
|------|------|
| 数据大小 | Write单次最大4096字节 |
| 波特率 | 预定义列表（50 ~ 4000000） |
| 设备类型 | 仅支持ttyUSB* 和单独配置的串口设备 |
| 并发写入 | Write同步阻塞，不支持异步写入 |
| 配置修改 | 仅在Open时配置，不支持运行时修改 |

---

## 版本历史

| 版本 | 日期 | 变更 |
|------|------|------|
| 1.0 | 2026-04 | 初始版本 |

---

## 参考资料

- OpenHarmony HDI设计规范
- Linux termios手册
- Linux netlink uevent文档