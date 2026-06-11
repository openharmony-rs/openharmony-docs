# 传感器错误码
<!--Kit: Sensor Service Kit-->
<!--Subsystem: Sensors-->
<!--Owner: @dilligencer-->
<!--Designer: @andeszhang-->
<!--Tester: @liuhaonan2-->
<!--Adviser: @hu-zhiqiong-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 14500101 传感器服务异常<sup>9+</sup>

**错误信息**

Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3. Sensor data channel exception.

**错误描述**

当调用sensor模块on、once、off接口时，若HDI服务异常，会报此错误码。此错误码表示传感器服务不可用，服务端无法响应传感器相关的操作请求。

**可能原因**

访问HDI服务时服务状态异常，无法正常响应请求。

**处理步骤**

1. 开发者应定时重试操作，建议间隔1s或按照指数增长间隔重试。
2. 连续重试3次仍不可用则停止尝试，期间优先尝试获取器件列表方式进一步确认设备可用性。

## 14500102 设备不支持该传感器

**错误信息**

The sensor is not supported by the device.

**错误描述**

当调用GetSingleSensor接口时，若设备不支持该传感器，会报此错误码。

**可能原因**

底层器件未适配传感器，设备不支持该传感器。

**处理步骤**

使用GetSingleSensor接口，返回14500102则表示设备不支持该传感器。