# Extended Authentication Error Codes


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

This error code is reported if **netId** is invalid.

**Possible causes**

The specified **netId** does not exist.

**Solution**

Enter a valid **netId**.

## 33200002 Failed to Exit Extended Authentication of the Specified NIC

**Error Message**

log off fail.

**Description**

This error code is reported if the attempt to exit extended authentication of the NIC identified by the specified **netId** fails.

**Possible causes**

The specified **netId** does not exist.

**Solution**

Enter a valid **netId**.

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

This error code is reported if the EAP data length is invalid.

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

Set the input network type to **1** (WLAN) or **2** (ETH).


## 33200007 Invalid eapCode Value

**Error Message**

Invalid eap code.

**Description**

This error code is reported if **eapCode** is invalid.

**Possible causes**

The input **eapCode** is not within the valid value range.

**Solution**

Enter a valid **eapCode** value, which can be **1**, **2**, **3**, or **4**.

## 33200008 Invalid eapType Value

**Error Message**

Invalid eap type.

**Description**

This error code is reported if **eapType** is invalid.

**Possible causes**

The input **eapCode** is not within the valid value range.

**Solution**

Set **eapType** to a value within the range of [1, 255].

## 33200009 netmanager Not Exist

**Error Message**

netmanager stop.

**Description**

The netmanager process does not exist.

**Possible causes**

This error code is reported if the netmanager process is abnormal.

**Solution**

Reboot the system.

## 33200010 Invalid eap Status

**Error Message**

Invalid eth state.

**Description**

This error code is reported if the eth status is invalid.

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

1. If EAP packets fail to be processed, for example, packets fail to be parsed or the data format is incorrect, filter the logs by the keyword "wpa_supplicant:EAP" to locate and analyze the fault.

2. If the authentication process is abnormal, for example, the state machine is incorrect or the authentication times out and no response is returned, filter the logs by the keyword "entering state" to locate and analyze the fault.

3. If the certificate fails to be processed, for example, the certificate fails to be loaded or parsed, or the key operation fails, filter the logs by the keyword "wpa_supplicant:SSL" to locate and analyze the fault.

4. If the callback function is abnormal, for example, the callback function is not correctly implemented or an exception that is not captured is thrown, filter the logs by the keyword "replyCustomEapData" to locate and analyze the fault.

5. If the communication fails, for example, the socket communication is abnormal or the connection is disconnected, check the logs. This cause is commonly seen on the [startEthEap](js-apis-net-eap.md#eapstartetheap) and [logOffEthEap](js-apis-net-eap.md#eaplogoffetheap) interfaces. You can filter logs by the keyword startEap or stopEap to check whether the command is delivered properly.

**Solution**

1. View system logs to locate the fault. You can filter logs by the keyword supplicant to locate the EAP packet processing exception, and filter logs by the keyword replyCustomEapData to locate the callback function exception. For communication exceptions triggered by the [startEthEap](js-apis-net-eap.md#eapstartetheap) and [logOffEthEap](js-apis-net-eap.md#eaplogoffetheap) interfaces, you can filter logs by the keyword startEap or stopEap to locate the fault.

2. Ensure that the EAP authentication process is correctly invoked. Do not perform the next step before the previous step is complete.

3. Check whether the certificate and key are correctly configured and whether the certificate format meets the requirements.

4. Ensure that the callback function is not deregistered repeatedly before being deregistered and is working properly after being registered.

5. If the fault persists, restart the device and try again.
