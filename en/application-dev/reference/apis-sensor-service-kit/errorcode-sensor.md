# Sensor Error Codes
<!--Kit: Sensor Service Kit-->
<!--Subsystem: Sensors-->
<!--Owner: @dilligencer-->
<!--Designer: @andeszhang-->
<!--Tester: @liuhaonan2-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=7b96ce2cdc47279f6264c88642e4fd07a8682bf6 translatedAt=2026-06-18T03:35:54.947Z pushedAt=2026-06-18T07:24:16.913Z -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 14500101 Service Exception

**Error Message**

Service exception.Possible causes:1. Sensor hdf service exception;2. Sensor service ipc exception;3. Sensor data channel exception.

**Description**

This error code is reported if the HDI service is abnormal when the **on**, **once**, or **off** API of the sensor module is called.

**Possible Causes**

The HDI service is abnormal.

**Solution**

1. Retry the operation at a specified interval (for example, 1s) or at an exponential increase interval.
2. If the operation fails for three consecutive times, stop the retry. You can also attempt to obtain the sensor list to check for device availability.

## 14500102 Sensor Not Supported by the Device

**Error Message**

The sensor is not supported by the device.

**Description**

This error code is reported if the **GetSingleSensor** API is called to obtain a sensor that is not supported by the device.

**Possible Causes**

The device does not support the sensor because the underlying components are not adaptable to the sensor.

**Solution**

Adapt the underlying components to the sensor.