# Screen Hopping Error Codes (To Be Deprecated)

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=574e1b97c419a831e3ff5b620b1254fe667a5306 translatedAt=2026-06-12T02:21:15.018Z pushedAt=2026-06-12T06:18:19.556Z -->

> **NOTE**
>
> - This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 20900001 Service Exception

**Error Message**

Service exception. Possible causes:

1. A system error, such as null pointer, container-related exception, or IPC exception.

2. N-API invocation exception or invalid N-API status.

**Description**

This error code is reported when a system exception occurs during the call to the screen hopping API.

**Possible Causes**

1. A system error occurs, such as null pointer, container-related exception, or IPC exception.

2. The N-API call is abnormal or the N-API status is invalid.

**Solution**

1. Ensure that the system service is running properly and try the operation again.

2. If the fault persists, contact technical support.

## 4400001 Incorrect Target Device Descriptor

**Error Message**

Incorrect descriptor for the target device.

**Description**

This error code is reported if an invalid device descriptor is passed to the screen hopping API.

**Possible Causes**

1. The target device does not exist (the device is not networked).

2. The target device descriptor is empty.

**Solution**

1. Ensure that the target device for screen hopping is correctly networked with the local device.

2. Set the target device descriptor correctly.

## 4400002 Input Device Operation Failed

**Error Message**

Screen hop failed.

**Description**

This error code is reported if the screen hopping status is abnormal when the screen hopping API is called.

**Possible Causes**

1. When screen hopping is initiated, the current device is in the hopped state.

2. When screen hopping is disabled, the current device is in the free state.

3. When screen hopping is disabled, the current device is in the hopping state.

**Solution**

1. When initiating screen hopping, ensure that the current device is not in the hopped state.

2. When disabling screen hopping, ensure that the current device is not in the free state.

3. When disabling screen hopping, ensure that the current device is not in the hopping state.