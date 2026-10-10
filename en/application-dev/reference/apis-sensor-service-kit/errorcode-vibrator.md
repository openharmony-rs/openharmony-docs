# Vibrator Error Codes
<!--Kit: Sensor Service Kit-->
<!--Subsystem: Sensors-->
<!--Owner: @dilligencer-->
<!--Designer: @butterls-->
<!--Tester: @zhaofangyuan-->
<!--Adviser: @hu-zhiqiong-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 14600101 Device operation failed.

**Error Message**

Device operation failed.

**Description**

This error code is reported if the HDI service is abnormal or the device is occupied when the **startVibration** interface of the vibrator module is called.

**Possible Causes**

<!--RP1-->
1. The HDI service is abnormal.
2. The device is occupied.
<!--RP1End-->

**Solution**

<!--RP2-->
1. Retry the operation at an interval of 1 to 2 seconds or at an exponential increase interval (for example, 1 second, 2 seconds, and 4 seconds). If the operation fails for three consecutive times, stop the retry. During this period, obtain the device list to further check the device availability.
2. Try again after the current vibration task is complete.
<!--RP2End-->
