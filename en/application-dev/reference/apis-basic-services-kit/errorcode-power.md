# Power Manager Error Codes

<!--Kit: Basic Services Kit-->
<!--Subsystem: PowerManager-->
<!--Owner: @zhang-yinglie; @volcano_wang-->
<!--Designer: @wangyantian0-->
<!--Tester: @alien0208-->
<!--Adviser: @w_Machine_cc-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 4900101 Service Connection Failure

**Error Message**

Failed to connect to the service.

**Description**

This error code is reported if a service connection failure occurs.

**Possible Causes**

1. The system service stops running.

2. The internal communication of system services is abnormal.

**Procedure**

Check whether the system services are running properly.

1. Run the following command on the console to view the current system service list:

    ```bash
    > hdc shell hidumper -ls
    ```

2. Check whether **PowerManagerService** is included in the system service list.

## 4900102 System Shutting Down

**Error Message**

Operation failed. The system is shutting down.

**Description**

This error code is reported when an operation failed during system shutting down.

**Possible Causes**

The system is shutting down.

**Procedure**

Make sure that the operation is performed when the system is running properly.

## 4900201 Frequent Status Refreshes

**Error Message**

The device activity is being refreshed too frequently; the minimum timeinterval is 100 ms.

**Description**

This error code is reported if the refresh of the device activity status fails due to short intervals (< 100 ms).

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

The power mode fails to be set due to the power mode control rules.

**Procedure**

The current power mode cannot be switched to the target power mode. You can call the [getPowerMode](js-apis-power.md#powergetpowermode9) API to query the current power mode.
