# Power Manager Error Codes

<!--Kit: Basic Services Kit-->
<!--Subsystem: PowerManager-->
<!--Owner: @zhang-yinglie; @volcano_wang-->
<!--Designer: @wangyantian0-->
<!--Tester: @alien0208-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=b42d2f19b4147ca317f040c00ccc3c0d556652e1 translatedAt=2026-11-06T01:34:19.693Z pushedAt=2026-11-06T10:13:57.956Z nl=1 -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 4900101 Service Connection Failure

**Error Message**

Failed to connect to the service.

**Description**

This error code is reported if a service connection failure occurs.

**Possible Causes**

1. The power manager service that the power management module depends on stops running, causing the API call to fail to establish a service connection.

2. An exception occurs in the communication between the power management module and the power manager service, causing failure to establish a connection or respond to the connection request.

**Procedure**

Check whether the system service is running properly. If the service is not running or is running abnormally, restart the device and call the API again.

1. Run the following command on the console to view the current system service list:

    ```bash
      hdc shell hidumper -ls
    ```

2. Check whether the power manager service is included in the system service list.

3. Manually restart the device and perform the operation again.

## 4900102 System Shutting Down

**Error Message**

Operation failed. The system is shutting down.

**Description**

This error code is reported when an operation failed during system shutting down.

**Possible Causes**

The system is shutting down.

**Procedure**

Call the related API again after the system runs normally.

## 4900201 Short Refresh Interval of the Device Active Status

**Error Message**

The device activity is being refreshed too frequently; the minimum time interval is 100 ms.

**Description**

The device active status is refreshed too frequently. The minimum interval for refreshing the device active status is 100 ms.

**Possible Causes**

The device activity status is frequently refreshed.

**Procedure**

No more refresh is needed if the device activity status has been refreshed within 100 ms. Try another refresh 100 ms later.

## 4900301 Power Mode Setting Failed

**Error Message**

Setting the power mode failed.

**Description**

This error code is reported if the power mode fails to be set.

**Possible Causes**

The power mode control rules do not allow switching from the current power mode to the target power mode, causing the power mode setting to fail.

**Procedure**

The current power mode cannot be switched to the target power mode. Use the [getPowerMode](js-apis-power.md#powergetpowermode9) API to query the current power mode.

## 4900400 Invalid Input Parameter

**Error Message**

The input parameter is invalid.

**Description**

The input parameter of the API is invalid.

**Possible Causes**

The parameter is a null pointer or the parameter value is out of range.

**Procedure**

This error indicates that the input parameter value does not meet the requirements. Check whether the type and value range of the input parameter fall within the valid range defined by the API, and do not pass in null values or parameters that exceed the valid range.

## 4900501 Failed to Read the Power Configuration Value

**Error Message**

Failed to read the power configuration value.

**Description**

The power configuration value fails to be read.

**Possible Causes**

The configuration node in the **power_config.json** file on the device does not exist.

**Procedure**

Refer to the parameter description of the power configuration API to confirm the valid node values, and check whether the input node is within the valid range.

## 4900601 Failed to Write the Power Configuration Value

**Error Message**

Failed to write the power configuration value.

**Description**

The power configuration value fails to be written.

**Possible Causes**

The configuration node in the **power_config.json** file on the device does not exist.

**Procedure**

Refer to the parameter description of the power configuration API to confirm the valid node values, and check whether the input node is within the valid range.

## 4900701 Failed to Suspend the Device

**Error Message**

Failed to suspend the device.

**Description**

The device fails to be suspended.

**Possible Causes**

The device is not allowed to be suspended during an exam.

**Solution**

The device is not allowed to be suspended during an exam based on system specification. It is recommended that the caller record a log when this error code is received.
