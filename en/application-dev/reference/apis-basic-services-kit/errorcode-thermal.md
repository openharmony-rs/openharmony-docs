# Thermal Manager Error Codes

<!--Kit: Basic Services Kit-->
<!--Subsystem: PowerManager-->
<!--Owner: @zhang-yinglie; @volcano_wang-->
<!--Designer: @wangyantian0-->
<!--Tester: @alien0208-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=2a67e7451b3dfcc746ff67349e2b0b9474fa54f8 translatedAt=2026-11-06T01:36:04.114Z pushedAt=2026-11-06T10:20:58.896Z nl=1 -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 4800101 Service Connection Failure

**Error Message**

Failed to connect to the service.

**Description**

This error code is reported if a service connection failure occurs.

**Possible Causes**

1. The thermal service that the thermal management module depends on stops running, causing the API call to fail to establish a service connection.

2. An exception occurs in the communication between the thermal management module and the thermal service, causing the API call to fail to establish a service connection.

**Procedure**

Check whether the system service is running properly by following the steps below.

1. Run the following command on the console to view the current system service list:

    ```bash
      hdc shell hidumper -ls
    ```

2. Check whether the thermal system service is included in the system service list.

3. Try manually restarting the device and then perform the operation again.
