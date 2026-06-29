# MDNS Error Codes

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=66333f405b8ba85b102d9221d24e54901f6cfbf8 translatedAt=2026-06-25T01:49:56.324Z pushedAt=2026-06-26T03:00:41.282Z -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 2100002 Service Connection Failure

**Error Message**

Failed to connect to the service.

**Description**

This error code is reported if a service connection failure occurs.

**Possible Causes**

The service is abnormal.

**Solution**

Check the system service running status and try again. If the problem persists, collect complete logs and contact technical support for assistance.

## 2100003 System Internal Error

**Error Message**

System internal error.

**Description**

This error code is reported if a system internal error occurs.

**Possible Causes**

1. The memory is abnormal.

2. A null pointer is present.

**Solution**

1. Check whether the memory space is sufficient. If not, clear the memory and try again.

2. The system is abnormal. Try again later or restart the device. If the problem persists, collect complete logs and contact technical support for assistance.

## 2204002 Target Service Not Found

**Error Message**

Callback not found.

**Description**

The target service is not found.

**Possible Causes**

An unregistered mDNS service is being unregistered, or the search for an mDNS service not being searched is being cancelled.

**Solution**

Check whether the input parameters for the APIs to unregister mDNS and cancel mDNS search are correct.

## 2204003 Repeated Registration

**Error Message**

Callback duplicated.

**Description**

This error code is reported if a callback already exists.

**Possible Causes**

An MDNS service with the same name and type is repeatedly registered.

**Solution**

Check whether the MDNS service to be registered already exists.

## 2204007 Service Already Exists

**Error Message**

Service instance duplicated.

**Description**

This error code is reported if an MDNS service already exists.

**Possible Causes**

The previously registered MDNS service is still running.

**Solution**

Check whether the MDNS service already exists.

## 2204008 Service Deletion Failure

**Error Message**

Failed to delete the service instance.

**Description**

This error code is reported if the MDNS service to be removed does not exist.

**Possible Causes**

The service has been deleted.

**Solution**

Check whether the MDNS service to be registered already exists.

## 2204009 Data Packet Sending Failure

**Error Message**

Failed to send packet.

**Description**

Data packets fail to be sent.

**Possible Causes**

No network is available.

**Solution**

Check whether the device is connected to an available network.

## 2204010 Message Sending Failure

**Error Message**

Failed to send the message.

**Description**

This error code is reported if messages fail to be sent through an MDNS service.

**Possible Causes**

The MDNS service does not exist on the LAN.

**Solution**

Check whether the target MDNS service exists on the LAN.

## 2204006 Service Resolution Timeout

**Error Message**

Request timeout.

**Description**

This error code is reported if MDNS services of the specified type fail to be resolved.

**Possible Causes**

MDNS services of the specified type do not exist on the LAN.

**Solution**

Check whether MDNS services of the specified type exist on the LAN.