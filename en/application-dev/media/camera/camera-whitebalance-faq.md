# White Balance Issues

<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=45526eba67080b876eb51af31a33be43ae26f701 translatedAt=2026-07-13T13:21:09.830Z pushedAt=2026-07-21T07:41:26.063Z -->

## Symptom

White balance does not work properly, manually setting the white balance value does not take effect, or switching between white balance modes and manually configured color temperature values does not work as expected.

## Possible Causes

The issue is related to the call sequence of white balance APIs. An incorrect white balance mode may cause manual color temperature settings to fail. Possible causes include:

1. Incorrect call sequence when switching between white balance modes and manually setting the white balance color temperature.

2. Failure when manually setting the white balance value.

**Troubleshooting Steps**

Step 1: The white balance mode and manual white balance value can be configured independently. If the white balance mode is configured first, switch the mode to [WhiteBalanceMode.MANUAL](../../reference/apis-camera-kit/arkts-apis-camera-e.md#whitebalancemode20) before setting the manual white balance value. If the manual white balance value is configured first, you can directly set the white balance mode.

Step 2: If setting the manual white balance color temperature fails, check logs related to `SetManualWhiteBalance` to identify the cause. The logs can help determine whether the session has been committed. If a white balance mode has been configured previously, verify that the mode has been switched to [WhiteBalanceMode.MANUAL](../../reference/apis-camera-kit/arkts-apis-camera-e.md#whitebalancemode20) before setting the color temperature value.

Log keyword: `whiteBalance`

## Solution

Use `setWhiteBalance` correctly as follows:

1. Call sequence: Ensure that `setWhiteBalance` is called after `commitConfig`.

2. Color temperature range: Call `getWhiteBalanceRange` to obtain the supported color temperature range for the current device, and select a value within this range. If the call fails, the device model or API version may not support this API.

3. White balance mode: If a white balance mode has been configured before setting the color temperature value, switch the white balance mode to `WhiteBalanceMode.MANUAL` before setting the color temperature value.

For white balance sample code, see [White Balance Settings (ArkTS)](camera-whitebalance.md).