# Extensible Authentication Error Codes

<!-- md-trans-meta sourceCommit=c8d611da517c0df9bbfb2e4952764bf8397e713e translatedAt=2026-11-04T06:36:00.776Z pushedAt=2026-11-04T08:04:44.867Z nl=1 -->

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 33200001 Invalid netId

**Error Message**

Invalid netId.

**Description**

Invalid **netId** value.

**Possible causes**

The **netId** value does not exist.

**Solution**

Enter a valid **netId** value.

## 33200002 Failed to Exit Extended Authentication of the Specified NIC

**Error Message**

log off fail.

**Description**

Failed to exit extended authentication of the specified **netId**.

**Possible causes**

The **netId** value does not exist.

**Solution**

Enter a valid **netId** value.

## 33200003 Invalid eth eap Configuration

**Error Message**

Invalid profile.

**Description**

This error code is reported if the **eth eap** configuration in **profile** is invalid.

**Possible causes**

The **profile** field value is incorrect.

**Solution**

Configure the **profile** field correctly.

## 33200004 Invalid eap Result Value

**Error Message**

Invalid result.

**Description**

This error code is reported if the **result** value is invalid.

**Possible causes**

The input **result** value is not within the range of **CustomResult**.

**Solution**

Set **result** to a value within the range of **CustomResult**.

## 33200005 Invalid Data Length

**Error Message**

Invalid size of eap data.

**Description**

Invalid EAP data length value.

**Possible causes**

The input EAP data length is different from the value of **bufferLen** in **EapData**.

**Solution**

Ensure that the value of **bufferLen** is the same as the EAP data length.

## 33200006 Invalid Network Type

**Error Message**

Invalid net type.

**Description**

This error code is reported if the network type is invalid.

**Possible causes**

The input network type is not supported.

**Solution**

Pass in a supported valid network type: **WLAN: 1**; **ETH: 2**.


## 33200007 Invalid eapCode Value

**Error Message**

Invalid eap code.

**Description**

The **eapCode** value is invalid.

**Possible causes**

The input **eapCode** is not within the valid value range.

**Solution**

The valid values of **eapCode** are **1**, **2**, **3**, and **4**.

## 33200008 Invalid eapType Value

**Error Message**

Invalid eap type.

**Description**

The **eapType** is invalid.

**Possible causes**

The input **eapCode** is not within the valid value range.

**Solution**

Pass in a valid **eapType**, with a value range of [1, 255].

## 33200009 netmanager Not Exist

**Error Message**

netmanager stop.

**Description**

The netmanager process does not exist.

**Possible causes**

This error code is reported if the netmanager process is abnormal.

**Solution**

Reboot the system.

## 33200010 Invalid eth State

**Error Message**

Invalid eth state.

**Description**

This error code is reported if the eth state is invalid.

**Possible causes**

The Ethernet adapter is not working properly.

**Solution**

Remove and insert the network cable and try again.

## 33200099 Internal Program Error

**Error Message**

internal error.

**Description**

This error code is reported if a program fails to operate properly.

**Possible causes**

1. EAP packet processing exception, such as packet parsing failure or incorrect data format. Locate the issue by filtering logs with the keyword wpa_supplicant:EAP.

2. Authentication process exception, such as state machine error or authentication timeout without response. Locate the issue by filtering logs with the keyword entering state.

3. Certificate processing failure, such as certificate loading failure, certificate parsing error, or key operation failure. Locate the issue by filtering logs with the keyword wpa_supplicant:SSL.

4. Callback function exception, such as the callback not being correctly implemented or throwing an uncaught exception. Locate the issue by filtering logs with the keyword replyCustomEapData.

5. Communication failure, such as socket communication exception or connection disconnection. This cause is common for the [startEthEap](js-apis-net-eap.md#eapstartetheap) and [logOffEthEap](js-apis-net-eap.md#eaplogoffetheap) APIs. You can filter log keywords **startEap** or **stopEap** to check whether the command is delivered properly.

**Solution**

1. Check the system logs to locate the specific cause. Filter logs with the keyword supplicant to locate EAP packet processing exceptions, and filter logs with the keyword replyCustomEapData to locate callback function exceptions. For communication exceptions triggered by the [startEthEap](js-apis-net-eap.md#eapstartetheap) and [logOffEthEap](js-apis-net-eap.md#eaplogoffetheap) APIs, filter logs with the keyword startEap or stopEap to locate the issue.

2. Ensure that the EAP authentication process is invoked in the correct order, and avoid proceeding to the next step before the previous step is completed.

3. Check that the certificate and key configurations are correct and that the certificate format meets the requirements.

4. Ensure that the callback function is not unregistered repeatedly before being unregistered, and that it is used normally after registration.

5. If the problem persists, restart the device and try again.

