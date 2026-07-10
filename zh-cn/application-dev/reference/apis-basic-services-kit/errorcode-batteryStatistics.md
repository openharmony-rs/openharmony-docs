# 耗电统计错误码

<!--Kit: Basic Services Kit-->
<!--Subsystem: PowerManager-->
<!--Owner: @zhang-yinglie; @volcano_wang-->
<!--Designer: @wangyantian0-->
<!--Tester: @alien0208-->
<!--Adviser: @fang-jinxu-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 4600101 连接服务失败

**错误信息**

Failed to connect to the service.

**错误描述**

操作失败，连接系统服务发生异常。

**可能原因**

1. 耗电统计模块依赖的BatteryStatisticsService系统服务停止运行，导致耗电统计等操作无法建立服务连接。

2. 耗电统计模块与BatteryStatisticsService系统服务之间的服务通信发生异常，导致请求无法正常建立或响应。

**处理步骤**

若连接服务失败，请按以下步骤排查系统服务状态：

1. 在控制台中输入如下命令，查看当前的系统服务列表。

    ```bash
      hdc shell hidumper -ls
    ```

2. 查看系统服务列表中是否包含BatteryStatisticsService系统服务。

3. 若服务列表中不包含BatteryStatisticsService系统服务，说明系统服务停止运行；若服务列表中包含BatteryStatisticsService系统服务但仍报错，说明系统服务内部通信发生异常。请尝试手动重启设备后重新执行操作。
