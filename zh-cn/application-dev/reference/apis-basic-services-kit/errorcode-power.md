# 系统电源管理错误码

<!--Kit: Basic Services Kit-->
<!--Subsystem: PowerManager-->
<!--Owner: @zhang-yinglie; @volcano_wang-->
<!--Designer: @wangyantian0-->
<!--Tester: @alien0208-->
<!--Adviser: @fang-jinxu-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 4900101 连接服务失败

**错误信息**

Failed to connect to the service.

**错误描述**

操作失败，连接系统服务发生异常。

**可能原因**

1. 电源管理模块依赖的PowerManagerService系统服务停止运行，导致接口调用无法建立服务连接。

2. 电源管理模块与PowerManagerService系统服务之间的服务通信发生异常，导致连接请求无法正常建立或响应。

**处理步骤**

检查系统服务是否正常运行，若服务未运行或运行异常，请重启设备后重新调用接口。

1. 在控制台中输入如下命令，查看当前的系统服务列表。

    ```bash
      hdc shell hidumper -ls
    ```

2. 查看系统服务列表中是否包含PowerManagerService系统服务。

3. 若服务列表中不包含PowerManagerService系统服务，说明系统服务停止运行；若服务列表中包含PowerManagerService系统服务但仍报错，说明系统服务内部通信发生异常。请尝试手动重启设备后重新执行操作。

## 4900102 正在关机中

**错误信息**

Operation failed. The system is shutting down.

**错误描述**

操作失败，系统正在关机。

**可能原因**

系统正处于关机过程中。

**处理步骤**

请在系统正常运行后，重新调用相关接口。

## 4900201 设备活跃状态刷新间隔过短

**错误信息**

The device activity is being refreshed too frequently; the minimum time interval is 100 ms.

**错误描述**

频繁刷新设备活跃状态，刷新设备活跃状态最小时间间隔为100ms。

**可能原因**

频繁刷新设备活跃状态。

**处理步骤**

此错误说明100ms内已经刷新设备活跃状态，无需再次刷新设备活跃状态。如需再次刷新，请在100ms后进行重试。

## 4900301 电源模式设置失败

**错误信息**

Setting the power mode failed.

**错误描述**

设置电源模式失败。

**可能原因**

电源模式管控规则不允许从当前电源模式切换至目标电源模式，导致设置电源模式失败。

**处理步骤**

当前电源模式不可切换至目标电源模式，请使用[getPowerMode](js-apis-power.md#powergetpowermode9)接口查询当前电源模式。

## 4900400 接口入参错误

**错误信息**

The input parameter is invalid.

**错误描述**

接口的入参无效。

**可能原因**

入参超出范围或为空。

**处理步骤**

此错误说明入参值不符合要求，请检查入参的类型和取值范围是否在接口定义的有效范围内，避免传入空值或超出有效范围的参数。

## 4900501 读电源配置值失败

**错误信息**

Failed to read the power configuration value.

**错误描述**

读电源配置值失败。

**可能原因**

设备中配置文件power_config.json的配置节点不存在

**处理步骤**

请参考电源配置接口的参数说明确认有效节点取值，检查入参节点是否在有效范围内。

## 4900601 写电源配置值失败

**错误信息**

Failed to write the power configuration value.

**错误描述**

写电源配置值失败。

**可能原因**

设备中配置文件power_config.json的配置节点不存在

**处理步骤**

请参考电源配置接口的参数说明确认有效节点取值，检查入参节点是否在有效范围内。
