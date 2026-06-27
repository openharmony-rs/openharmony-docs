# WIFI错误码

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @qq_43802146-->
<!--Designer: @qq_43802146-->
<!--Tester: @furryfurry123-->
<!--Adviser: @zhang_yixin13-->
> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 2401000 STA内部异常

**错误信息**

Operation failed.

**错误描述**

调用syscap为SystemCapability.Communication.WiFi.Core的接口时，Wi-Fi服务内部出现未知错误。

**可能原因**

1. 和WIFI服务建立通信异常。
2. WIFI芯片通信异常。
3. 其他未知错误。

**处理步骤**

1. 重新执行关闭及打开WIFI开关的操作。
2. 如果步骤1无效，请尝试重启设备。

## 2501000 STA内部异常

**错误描述**

通常与WIFI服务建立通信异常，WIFI芯片通信异常，且该错误码在不同接口中表示不同的状态错误：

1. startScan接口报错可能原因及解决方案：
**可能原因**：系统级Wi-Fi扫描服务处于不可用状态，可能由服务进程异常或驱动状态异常引起。
**处理步骤**：查看系统服务状态日志。建议先关闭再重新开启 Wi-Fi 功能，若无效则执行系统重启以恢复扫描服务。

2. getScanInfoList接口报错可能原因及解决方案：
**可能原因**：系统内部状态异常导致无法返回扫描结果列表，通常为Wi-Fi服务或驱动层临时故障。
**处理步骤**：首先尝试开关Wi-Fi，若问题未能解决，则重启设备恢复系统状态。

3. addCandidateConfig接口报错可能原因及解决方案：
**可能原因**：当前已添加的候选配置数量超过系统允许的最大值（16 个）
**处理步骤**：减少传入的配置数量，确保不超过上限；若需更新配置，建议先移除旧配置再添加新配置。
**可能原因**：系统内部异常，可能为Wi-Fi服务状态异常或配置格式错误。
**处理步骤**：执行开关Wi-Fi或重启设备以恢复服务。
**可能原因**：当前系统或固件不支持WEP加密类型的候选配置。
**处理步骤**：移除WEP加密配置，改用受支持的加密方式（如 WPA2/WPA3）。

**错误信息**

Operation failed.

### 飞行模式开启导致功能异常

**错误信息**

Flight mode is enabled.

### 省电模式开启导致功能异常

**错误信息**

Power saving mode is enabled.

### 服务正在关闭导致功能异常

**错误信息**

Operation failed because the service is being closed.

### 扫描服务未开启导致功能异常

**错误信息**

Ap service is not enabled.

### AP服务未开启导致功能异常

**错误信息**

Ap service is not enabled.

### 配置无效导致功能异常

**错误信息**

Configuration is invalid.

### P2P MAC地址未找到导致功能异常

**错误信息**

P2P MAC address not found.

### P2P MAC地址格式错误导致功能异常

**错误信息**

P2P MAC address format error.

### P2P内部服务异常导致功能异常

**错误信息**

P2P Internal service exception.

### P2P参数大小错误导致功能异常

**错误信息**

P2P wrong parameter size.

### 移动冻结扫描控制导致功能异常

**错误信息**

moving freeze scanning control.

**处理步骤**

1. 重新执行关闭及打开WIFI开关的操作。
2. 如果步骤1无效，请尝试重启设备。

## 2501001 STA功能未打开

**错误信息**

Wi-Fi STA disabled.

**错误描述**

WIFI STA功能被关闭。

**可能原因**

WIFI功能被关闭。

**处理步骤**

打开WIFI功能。

## 2501005 用户未响应连接请求

**错误信息**

The user does not respond.

**错误描述**

应用连接候选网络，提示是否信任并建立连接，用户未响应此连接请求。

**可能原因**

1. 用户通过上滑操作关闭提示对话框。
2. 10s内，用户未点击连接或者取消。

**处理步骤**

应用连接候选网络的请求，需要用户同意。

## 2501006 用户拒绝连接请求

**错误信息**

The user refused the action.

**错误描述**

应用连接候选网络，提示是否信任并建立连接，用户取消此连接请求。

**可能原因**

用户点击取消，拒绝连接。

**处理步骤**

应用连接候选网络的请求，需要用户同意。

## 2501007 参数校验失败

**错误信息**

Parameter validation failed.

**错误描述**

参数检查失败。

**可能原因**

参数值范围错误。

**处理步骤**

阅读接口入参约束，进行排查。

## 2601000 Hotspot模块异常

**错误信息**

Operation failed.

**错误描述**

WIFI服务内部执行Hotspot相关操作时出现未知错误。

**可能原因**

1. 和WIFI服务建立通信异常。
2. WIFI芯片通信异常。
3. 其他未知错误。

**处理步骤**

1. 重新执行关闭及打开Hotspot开关的操作。
2. 如果步骤1无效，请尝试重启设备。

## 2701000 AP扩展模块异常

**错误信息**

Operation failed.

**错误描述**

WIFI服务内部执行Hotspot相关操作时出现未知错误。

**可能原因**

1. 和WIFI服务建立通信异常。
2. WIFI芯片通信异常。
3. 其他未知错误。

**处理步骤**

1. 重新执行关闭及打开Hotspot开关的操作。
2. 如果步骤1无效，请尝试重启设备。

## 2801000 P2P模块异常

**错误信息**

Operation failed.

**错误描述**

WIFI服务内部执行P2P相关操作时出现未知错误。

**可能原因**

1. 和WIFI服务建立通信异常。
2. WIFI芯片通信异常。
3. 其他未知错误。

**处理步骤**

1. 重新执行关闭及打开WIFI开关的操作。
2. 如果步骤1无效，请尝试重启设备。

## 2801001 P2P模块异常

**错误信息**

Wi-Fi P2P disabled.

**错误描述**

Wi-Fi服务内部执行P2P相关操作时出现错误。

**可能原因**

1. 和Wi-Fi服务建立通信异常。
2. 打开P2P服务失败。
3. 其他未知错误。

**处理步骤**

1. 重新执行关闭及打开Wi-Fi开关的操作。
2. 如果步骤1无效，请尝试重启设备。

## 2501003 服务打开失败

**错误信息**

Operation failed because the service is being closed.

**错误描述**

打开服务操作失败，服务正在关闭。

**可能原因**

服务功能正在关闭。

**处理步骤**

重新执行打开服务操作。

## 2501004 服务关闭失败

**错误信息**

Operation failed because the service is being opened.

**错误描述**

关闭服务操作失败，服务正在打开。

**可能原因**

服务功能正在打开。

**处理步骤**

重新执行关闭服务操作。
