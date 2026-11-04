# Ethernet Connection Error Codes

<!-- md-trans-meta sourceCommit=ede2473bcfdd173278c84f213a25b67a0910ea5b translatedAt=2026-11-04T06:36:28.635Z pushedAt=2026-11-04T08:04:44.870Z nl=1 -->

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 2200001 Invalid Parameter Value

**Error Message**

Invalid parameter value.

**Description**

This error code is reported if the parameter value is invalid.

**Cause**

The input parameter value is not within the valid value range.

**Procedure**

Check whether the input parameter value is within the valid value range.

## 2200002 Service Connection Failure

**Error Message**

Failed to connect to the service.

**Description**

This error code is reported if a service connection failure occurs.

**Cause**

The service is abnormal.

**Procedure**

Check whether system services are running properly.

## 2200003 System Internal Error

**Error Message**

System internal error.

**Description**

This error code is reported if a system internal error occurs.

**Possible Causes**

1. Memory exception.

2. Null pointer.

**Solution**

1. Check whether the memory space is sufficient, and clear the memory and try again.

2. The system is abnormal. Try again later or restart the device.

<!--Del-->

## 2201004 Invalid Ethernet Profile

**Error Message**

Invalid Ethernet profile.

**Description**

The Ethernet interface configuration passed in when calling the setIfaceConfig API is invalid.

**Cause**

1. The InterfaceConfiguration passed in is invalid. For example, when mode is set to IPSetMode.STATIC (value 0), a static network configuration is used, which requires manually specifying the IP address (ipAddr), subnet mask (netMask), gateway, route, and DNS server addresses (dnsServers), instead of obtaining the network configuration automatically through DHCP. If the manually configured parameters are empty or in an incorrect format, the Ethernet configuration may become invalid.

2. The value of mode does not match the passed configuration items. For example, a static IP configuration is passed in DHCP mode.

**Procedure**

Check whether the value of each field in the InterfaceConfiguration passed in meets the requirements in the description of the setIfaceConfig API.

<!--DelEnd-->

## 2201005 Device Information Not Exist

**Error Message**

The device information does not exist.

**Description**

This error code is reported if the device information does not exist.

**Cause**

The device to set or obtain does not exist.

**Procedure**

```shell
> hdc shell ifconfig
```
Check whether the device, for example, **eth0** or **eth1**, exists.

## 2201006 Device Not Connected

**Error Message**

Device disconnected.

**Description**

This error code is reported if the device is not connected.

**Cause**

The network interface card (NIC) is faulty.

**Procedure**

View the Ethernet service and netsys logs to check for the connection status information reported by the kernel.

## 2201007 Failed to Write the User Configuration

**Error Message**

Failed to write the user configuration.

**Description**

This error code is reported if an error occurs while writing data to the user configuration file.

**Cause**

The system reports an error.

**Procedure**

A system internal error occurs. You are advised to locate the fault based on logs.
