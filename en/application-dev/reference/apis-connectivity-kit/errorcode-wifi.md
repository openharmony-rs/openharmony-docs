# Wi-Fi Error Codes

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @qq_43802146-->
<!--Designer: @qq_43802146-->
<!--Tester: @furryfurry123-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=8e24f7b49d36b00b7963dc6e73924cf26c9f95fd translatedAt=2026-11-10T05:00:54.214Z pushedAt=2026-11-10T07:22:23.241Z nl=2 -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 2401000 STA Internal Error

**Error Message**

Operation failed.

**Description**

When an API with the SysCap SystemCapability.Communication.WiFi.Core is called, an unknown error occurs inside the Wi-Fi service.

**Possible Causes**

1. Communication with the Wi-Fi service is abnormal.
2. Wi-Fi chip communication is abnormal.

**Solution**

1. Turn off and on the Wi-Fi switch.
2. If the error persists, restart the device.

## 2501000 STA Internal Error

Different error messages are reported depending on the actual cause of the error, as described below.

### Operation Failed

**Error Message**

Operation failed.

**Description**

Communication with the Wi-Fi service is abnormal, and Wi-Fi chip communication is abnormal.

**Possible Causes**

1. The startScan API reports an error. The system-level Wi-Fi scanning service is unavailable, which may be caused by an abnormal service process, an abnormal driver state, or excessively frequent API calls (more than four scans within two minutes).

2. The getScanInfoList API reports an error. An abnormal internal system state prevents the scan result list from being returned, which is usually a temporary fault in the Wi-Fi service or driver layer.

3. The addCandidateConfig API reports an error.
   - The number of candidate configurations already added exceeds the maximum allowed by the system (16).
   - An internal system exception occurs, possibly due to an abnormal Wi-Fi service state or an incorrect configuration format.
   - The current system or firmware does not support candidate configurations of the WEP encryption type.

**Solution**

1. Check the system service status logs to confirm whether the Wi-Fi scanning service is running properly. Turn off and on the Wi-Fi function. If the issue persists, restart the device to recover the scanning service.

2. Turn off and on the Wi-Fi function. If the issue persists, restart the device to recover the scan result query service.

3. addCandidateConfig API error.
   - Reduce the number of configurations passed in to ensure that the upper limit is not exceeded. To update a configuration, remove the old configuration before adding a new one.
   - If an internal system exception occurs, turn off and on the Wi-Fi function. If the issue persists, restart the device to recover the service.
   - If the candidate configuration uses the WEP encryption type, switch to an encryption type supported by the system and add it again.

### Airplane mode is enabled

**Error Message**

Flight mode is enabled.

**Description**

The airplane mode being enabled causes a function exception.

**Possible Causes**

A system service exception occurs. The system service related to airplane mode switching is abnormal and does not correctly respond to Wi-Fi requests.

**Solution**

1. Disable the airplane mode on the device, and then perform the operation again to turn off and on the Wi-Fi switch.
2. If the step 1 does not work, try restarting the device.

### Operation Failed Because the Service Is Being Closed

**Error Message**

Operation failed because the service is being closed.

**Description**

The Wi-Fi service, including P2P or hotspot, is being closed, causing a function exception.

**Possible Causes**

The P2P or hotspot service is being stopped, and the Wi-Fi service is being closed or restarted. System resources are insufficient, memory or CPU resources are strained, and the system reclaims the Wi-Fi service process.

**Solution**

1. Perform the operation again to turn off and on the Wi-Fi switch.
2. If the step 1 does not work, try restarting the device again.

### Scanning service is not enabled

**Error Message**

Scanning service is not enabled.

**Description**

The scanning service is not enabled, causing a function exception.

**Possible Causes**

The scanning function is not initialized. The Wi-Fi scanning module is not properly initialized or started.

**Solution**

1. Perform the operation again to turn off and on the Wi-Fi switch.
2. If the step 1 is ineffective, try restarting the device.

### AP Service Not Enabled

**Error Message**

AP service is not enabled.

**Description**

The AP service is not enabled, causing a function exception.

**Possible Causes**

The hotspot function is not enabled, the Wi-Fi hotspot switch is off, and the AP service is unavailable. Airplane mode restriction: the AP function is disabled when airplane mode is on.

**Solution**

1. Perform the operation again to turn off and on the Wi-Fi switch.
2. If the step 1 does not work, try restarting the device.

### Invalid configuration

**Error Message**

Configuration is invalid.

**Description**

When obtaining or deleting a candidate network, the input netid is invalid, causing the query or deletion to fail.

**Possible Causes**

The configuration parameter is empty. The input configuration parameter is a null pointer or an empty string.

**Solution**

1. Check the input netId to ensure that it is valid and corresponds to an existing candidate network configuration.
2. Correct the parameters and then call the API again.

### P2P MAC Address Not Found

**Error Message**

P2P MAC address not found.

**Description**

The P2P MAC address is not found, causing a function exception.

**Possible Causes**

The P2P function is not enabled or P2P is not initialized.

**Solution**

1. Perform the operation again to turn off and on the Wi-Fi switch.
2. If the step 1 does not work, try again to restart the device.

### P2P MAC Address Format Error

**Error Message**

P2P MAC address format error.

**Description**

A P2P MAC address format error causes a function exception.

**Possible Causes**

The MAC address is empty.

**Solution**

1. Check the input P2P MAC address to ensure that it is not empty and is in the correct format.
2. Correct the parameters and then call the API again.

### P2P Internal Service Exception

**Error Message**

P2P internal service exception.

**Description**

A P2P internal service exception causes a function exception.

**Possible Causes**

The P2P service is abnormal. The Wi-Fi P2P internal service process crashes or does not respond.

**Solution**

1. Perform the operation again to turn off and on the Wi-Fi switch.
2. If the error persists, restart the device.

### P2P wrong parameter size

**Error Message**

P2P wrong parameter size.

**Description**

The P2P wrong parameter size causes a function exception.

**Possible Causes**

The network name is too long, and the SSID length exceeds the maximum limit.

**Solution**

1. Check the input network name and ensure that the SSID length does not exceed the maximum limit allowed by the system.
2. Correct the parameters and then call the API again.

### Stationary Scan Control

**Error Message**

moving freeze scanning control.

**Description**

Wi-Fi scanning is controlled in the stationary state.

**Possible Causes**

When the device is stationary, Wi-Fi scanning is automatically disabled to save power.

**Solution**

1. Move the device so that it leaves the stationary state, and then try scanning again.

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

An unknown error occurs when the Wi-Fi service performs Hotspot-related operations internally.

**Possible Causes**

1. Communication exception when establishing a connection with the Wi-Fi service.
2. Chip communication exception.

**Solution**

1. Disable and then enable the hotspot again.
2. If the error persists, restart the device.

## 2701000 AP Extension Module Error

**Error Message**

Operation failed.

**Description**

An unknown error occurs when the Wi-Fi service performs AP extension-related operations internally.

**Possible Causes**

1. Communication exception with the Wi-Fi service.
2. Chip communication exception.

**Solution**

1. Perform the operation again to turn off and on the AP extension switch.
2. If the error persists, restart the device.

## 2801000 P2P Module Error

**Error Message**

Operation failed.

**Description**

An unknown error occurs when the Wi-Fi service performs P2P-related operations internally.

**Possible Causes**

1. Communication exception with the Wi-Fi service.
2. Chip communication exception.

**Solution**

1. Perform the operation again to turn off and on the Wi-Fi switch.
2. If the error persists, restart the device.

## 2801001 P2P Function Not Enabled

**Error Message**

Wi-Fi P2P disabled.

**Description**

An error occurs when the Wi-Fi service performs a P2P-related operation.

**Possible Causes**

1. Communication between the Wi-Fi service and the STA failed.
2. Failed to enable the P2P service.

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
