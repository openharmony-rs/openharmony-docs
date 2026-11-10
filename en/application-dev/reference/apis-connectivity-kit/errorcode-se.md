# SecureElement Error Codes

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @yh1719-->
<!--Designer: @wenxiaolin-->
<!--Tester: @zs_111-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=67487829468179127107f74c0916ca5ae8660edf translatedAt=2026-11-10T05:00:28.544Z pushedAt=2026-11-10T07:22:14.698Z nl=1 -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 3300101 Abnormal SE Service Status

**Error Message**

IllegalStateError, an attempt is made to use an SE session that has been closed.

**Description**

The SecureElement (SE) service is abnormal.

**Possible Causes**

1. The SE service is disconnected.
2. If the application accesses a SIM card or SIM2 card, check whether the corresponding card is inserted into the card slot.

**Solution**

1. Close the SE service.
2. Set up a connection with the SE service again.

## 3300102 Failed to Find the Desired SE

**Error Message**

NoSuchElementError, the AID on the SE is not available or cannot be selected.

**Description**

The desired SE is not found.

**Possible Causes**

1. The **aid** value of the parameter is incorrect.
2. The SE channel is occupied.

**Solution**

1. Enter a correct **aid** value.
2. Close the SE channel and then re-establish a connection.
3. Restart the device and try again.

## 3300103 Failed to Obtain the Access Rule

**Error Message**

SecurityError, the calling application cannot be granted access to this AID or the default applet on this session.

**Description**

The access rule cannot be obtained.

**Possible Causes**

The Secure Element does not contain the access control rule that the application depends on.

**Solution**

1. Write the correct access control rule to the Secure Element.
2. Close the SE service and set up a connection with the SE service again.

## 3300104 SE Chip I/O Exception

**Error Message**

IOError, there is a communication problem to the reader or the SE.

**Description**

The I/O of the SE chip is abnormal.

**Possible Causes**

1. The communication with the SE chip is abnormal.
2. The SE chip is abnormal.

**Solution**

1. Close the SE service and set up a connection with the SE service again.
2. Restart the device.
