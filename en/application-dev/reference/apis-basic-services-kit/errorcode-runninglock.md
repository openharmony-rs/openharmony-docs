# Running Lock Error Codes

<!--Kit: Basic Services Kit-->
<!--Subsystem: PowerManager-->
<!--Owner: @zhang-yinglie; @volcano_wang-->
<!--Designer: @wangyantian0-->
<!--Tester: @alien0208-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=2a67e7451b3dfcc746ff67349e2b0b9474fa54f8 translatedAt=2026-11-06T01:35:14.821Z pushedAt=2026-11-06T10:17:50.289Z nl=1 -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 4900101 Service Connection Failure

**Error Message**

Failed to connect to the service.

**Description**

The operation failed because the system service could not be connected.

**Possible causes**

1. The power manager service that the **RunningLock** module depends on stopped running, causing the API call to fail to establish a service connection.

2. An exception occurred in the communication between the **RunningLock** module and the power manager service, causing failure to establish a connection or respond to the connection request.

**Solution**

Perform the following steps to check whether the system service is running properly.

1. Run the following command on the console to view the current system service list:

    ```bash
      hdc shell hidumper -ls
    ```

2. Check whether the power manager service is included in the system service list.

3. Try to manually restart the device and then perform the operation again.
