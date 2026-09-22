# Cross-Device Wakeup and Message Transfer Error Codes

<!--Kit: Distributed Service Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wangrui7-->
<!--Designer: @yangyang2-->
<!--Tester: @Ytt-test-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=f44fb7f8070e1cb97778b3fca79dffbcf4e0c7e9 translatedAt=2026-08-07T09:45:20.823Z pushedAt=2026-08-07T11:30:43.562Z -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 2000001 Internal Error

**Error Message**

Internal error.

**Description**

An internal error occurs.

**Possible Causes**

A DSoftBus error occurs, such as failure to start the peer ability or memory allocation failure.

**Solution**

Verify whether the peer device has the ability installed, and whether the DSoftBus is running properly.

## 2004001 Peer Device System Version Outdated

**Error Message**

Remote system version is too low.

**Description**

The peer device system version is outdated.

**Possible Causes**

The peer device system version is outdated.

**Solution**

Update the peer device system version.

## 2004002 Failed to Start the Peer Ability

**Error Message**

Failed to start ability on the remote side.

**Description**

The peer ability fails to be started.

**Possible Causes**

The passed **abilityName** is incorrect, or the peer device does not have the ability.

**Solution**

Verify whether the **abilityName** value is correct.

## 2004003 Failure to Send Data

**Error Message**

Failed to send data.

**Description**

This error code is reported if data fails to be sent.

**Possible Causes**

Data fails to be sent.

**Solution**

Ensure that the same account is used on the peer device, the **deviceId** of the peer device is correct, and the local network status is normal.

## 2004004 Peer Confirmation Timeout

**Error Message**

Timeout while waiting for acknowledgement from the remote side.

**Description**

Peer confirmation times out.

**Possible Causes**

Peer confirmation times out, or the peer device is powered off.

**Solution**

Ensure that the peer network is normal.