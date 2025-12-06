# Wi-Fi Error Codes

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @qq_43802146-->
<!--Designer: @qq_43802146-->
<!--Tester: @furryfurry123-->
<!--Adviser: @zhang_yixin13-->
> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 2401000 STA Internal Error

**Error Message**

Operation failed.

**Description**

An error occurs when the Wi-Fi service performs an operation related to the station (STA).

**Possible Causes**

1. Communication between the Wi-Fi service and the STA failed.
2. The Wi-Fi chip communication is abnormal.
3. An unknown error has occurred.

**Solution**

1. Disable and then enable the Wi-Fi function again.
2. If the error persists, restart the device.

## 2501000 STA Internal Error

**Error Message**

Operation failed.

**Description**

An error occurs when the Wi-Fi service performs an operation related to the station (STA).

**Possible Causes**

1. Communication between the Wi-Fi service and the STA failed.
2. The Wi-Fi chip communication is abnormal.
3. An unknown error has occurred.

**Solution**

1. Disable and then enable the Wi-Fi function again.
2. If the error persists, restart the device.

## 2501001 STA Disabled

**Error Message**

Wi-Fi STA disabled.

**Description**

The Wi-Fi STA function is disabled.

**Possible Causes**

The Wi-Fi function is disabled.

**Solution**

Enable the Wi-Fi function.

## 2501005 No User Response to the Connection Request

**Error Message**

The user does not respond.

**Description**

When an application connects to a candidate network, the application prompts the user whether to trust and establish the connection. The user does not respond to the connection request.

**Possible Causes**

1. The user swipes up to close the dialog box.
2. The user does not click **OK** or **Cancel** within 10 seconds.

**Solution**

The user needs to agree to the request for connecting to the candidate network.

## 2501006 Connection Request Rejected

**Error Message**

The user refused the action.

**Description**

When an application connects to a candidate network, the application prompts the user whether to trust and establish the connection. The user cancels the connection request.

**Possible Causes**

The user clicks **Cancel** to reject the connection.

**Solution**

The user needs to agree to the request for connecting to the candidate network.

## 2501007 Parameter Verification Failed

**Error Message**

Parameter validation failed.

**Description**

An error occurs during parameter verification.

**Possible Causes**

The parameter value range is incorrect.

**Solution**

Rectify the fault according to the parameter restrictions of the API.

## 2601000 Hotspot Module Error

**Error Message**

Operation failed.

**Description**

An error occurs when the Wi-Fi service performs a hotspot-related operation.

**Possible Causes**

1. Communication between the Wi-Fi service and the STA failed.
2. The Wi-Fi chip communication is abnormal.
3. An unknown error has occurred.

**Solution**

1. Disable and then enable the hotspot again.
2. If the error persists, restart the device.

## 2701000 AP Extension Module Error

**Error Message**

Operation failed.

**Description**

An error occurs when the Wi-Fi service performs a hotspot-related operation.

**Possible Causes**

1. Communication between the Wi-Fi service and the STA failed.
2. The Wi-Fi chip communication is abnormal.
3. An unknown error has occurred.

**Solution**

1. Disable and then enable the hotspot again.
2. If the error persists, restart the device.

## 2801000 P2P Module Error

**Error Message**

Operation failed.

**Description**

An error occurs when the Wi-Fi service performs a P2P-related operation.

**Possible Causes**

1. Communication between the Wi-Fi service and the STA failed.
2. The Wi-Fi chip communication is abnormal.
3. An unknown error has occurred.

**Solution**

1. Disable and then enable the Wi-Fi function again.
2. If the error persists, restart the device.

## 2501003 Failed to Open the Service

**Error Message**

Operation failed because the service is being closed.

**Description**

The operation for opening the service failed because the service is being closed.

**Possible Causes**

The service is being closed.

**Solution**

Open the service again later.

## 2501004 Failed to Close the Service

**Error Message**

Operation failed because the service is being opened.

**Description**

The operation for closing the service failed because the service is being opened.

**Possible Causes**

The service is being opened.

**Solution**

Close the service again later.
