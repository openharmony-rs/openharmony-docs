# Battery Info Error Codes

<!--Kit: Basic Services Kit-->
<!--Subsystem: PowerManager-->
<!--Owner: @zhang-yinglie; @volcano_wang-->
<!--Designer: @wangyantian0-->
<!--Tester: @alien0208-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=2a67e7451b3dfcc746ff67349e2b0b9474fa54f8 translatedAt=2026-11-06T01:34:08.753Z pushedAt=2026-11-06T09:38:57.430Z nl=1 -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 5100101 Service Connection Failure

**Error Message**

Failed to connect to the service.

**Description**

This error code is reported if a service connection failure occurs.

**Possible causes**

1. The battery service that the battery Information module depends on stops running, causing failure to establish a service connection in operations such as battery information query.

2. An exception occurs in the communication between the battery Information module and the battery service, causing failure to establish a connection or respond to the connection request.

**Solution**

Follow the steps below to check whether the system service is running properly:

1. Run the following command on the console to view the current system service list:

    ```bash
      hdc shell hidumper -ls
    ```

2. Check whether the battery service is included in the system service list.

3. Try manually restarting the device and then perform the operation again.
