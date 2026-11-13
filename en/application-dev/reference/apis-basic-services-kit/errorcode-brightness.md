# Brightness Error Codes

<!--Kit: Basic Services Kit-->
<!--Subsystem: PowerManager-->
<!--Owner: @zhang-yinglie; @volcano_wang-->
<!--Designer: @wangyantian0-->
<!--Tester: @alien0208-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=2a67e7451b3dfcc746ff67349e2b0b9474fa54f8 translatedAt=2026-11-06T01:34:10.554Z pushedAt=2026-11-06T10:00:46.384Z nl=1 -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 4700101 Service Connection Failure

**Error Message**

Failed to connect to the service.

**Description**

This error code is reported if a service connection failure occurs.

**Possible causes**

1. The display power manager service that the brightness module depends on stops running, causing the brightness control operation to fail to establish a service connection.

2. An exception occurs in the service communication between the brightness module and the display power manager service, causing failure to establish a connection or respond to the connection request.

**Solution**

If the service connection fails, perform the following steps to check the system service status:

1. Run the following command on the console to view the current system service list:

    ```bash
      hdc shell hidumper -ls
    ```

2. Check whether the display power manager service is included in the system service list.

3. Try to manually restart the device and then perform the operation again.

