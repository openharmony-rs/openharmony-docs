# NFC Error Codes

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @amunra03-->
<!--Designer: @wenxiaolin-->
<!--Tester: @zs_111-->
<!--Adviser: @zhang_yixin13-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 3100101 NFC Switch Error

**Error Message**

The NFC state is abnormal in the service.

**Description**

The NFC service fails to enable or disable NFC.

**Possible Causes**

1. Communication with the NFC service failed.
2. The NFC chip communication is abnormal.

**Solution**

Enable or disable NFC again or restart the device, and try again.

## 3100201 Tag Read/Write Error

**Error Message**

The tag running state is abnormal in the service.

**Description**

An error occurs when the NFC service executes the tag service logic.

**Possible Causes**
1. The tag parameters do not match the API to invoke.
2. The NFC is disabled.
3. The tag is disconnected before the tag operation.
4. The tag chip returns an error status or response timeout.
5. Binding with the NFC service has not been established.

**Solution**
1. Check whether the NFC parameters match the API to call.
2. Instruct the user to enable NFC if it is disabled.
3. Connect to the tag and then perform the read and write operations.
4. Touch and read the card again.
5. Exit the app and read the card again.

## 3100202 Application Status Error

**Error Message**

The element state is invalid.

**Description**

When the API is called, the application of the card read page is not running in the foreground.

**Possible Causes**
The card read page is not in the foreground.

**Solution**
The API can be called only by the page in the foreground.

## 3100203 Incorrect API Call Sequence

**Error Message**

The off() API can be called only when the on() has been called.

**Description**

The off() API can be called only after on() is called.

**Possible Causes**
The foreground page of the application calls **off()** without invoking **on()**.

**Solution**
Call **on()** first, and call **off()** before the page exits.

## 3100204 NFC Chip I/O Exception

**Error Message**

The tag I/O operation failed.

**Description**

The NFC tag I/O operation fails.

**Possible Causes**
The NFC tag does not support the read/write operation.

**Solution**
Implement error handling and display error messages based on service scenarios.

## 3100205 Abnormal NFC Tag Status

**Error Message**

The tag leaves the field.

**Description**

The NFC tag has been removed.

**Possible Causes**
The NFC tag is out of the NFC device's sensing range.

**Solution**
Place the NFC tag close to the NFC card reader.

## 3100301 Abnormal NFC Card Emulation Status

**Error Message**

Card emulation running state is abnormal in service.

**Description**

An error occurs when the NFC service executes the card emulation service logic.

**Possible Causes**
1. NFC is disabled during card emulation.
2. The NFC chip returns an error status or response timeout.

**Solution**
1. Instruct the user to enable NFC if it is disabled.
2. Instruct the user to disable and enable NFC to initialize the hardware again.

## 3200101 Abnormal Active NFC Tag Status

**Error Message**

Connected NFC tag running state is abnormal in service.

**Description**

An error occurs when the service logic of the active NFC tag is executed.

**Possible Causes**
1. The parameter values of the active NFC tag do not match the API called.
2. The active NFC tag chip does not respond within the specified time or returns an error status.

**Solution**
1. Check that the active NFC tag parameters match the API called.
2. Touch and read the card again.
