# Power Consumption Statistics Error Codes

<!--Kit: Basic Services Kit-->
<!--Subsystem: PowerManager-->
<!--Owner: @zhang-yinglie; @volcano_wang-->
<!--Designer: @wangyantian0-->
<!--Tester: @alien0208-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=2a67e7451b3dfcc746ff67349e2b0b9474fa54f8 translatedAt=2026-11-06T01:34:12.508Z pushedAt=2026-11-06T10:00:34.413Z nl=1 -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 4600101 Service Connection Failure

**Error Message**

Failed to connect to the service.

**Description**

This error code is reported if a service connection failure occurs.

**Possible causes**

1. The battery statistics service that the power consumption statistics module depends on stops running, causing operations such as power consumption statistics to fail to establish a service connection.

2. An exception occurs in the communication between the power consumption statistics module and the battery statistics service, causing failure to establish a connection or respond to the connection request.

**Solution**

If the service connection fails, perform the following steps to check the system service status:

1. Run the following command on the console to view the current system service list:

    ```bash
      hdc shell hidumper -ls
    ```

2. Check whether the system service list contains the battery statistics service.

3. Try restarting the device manually and then perform the operation again.
