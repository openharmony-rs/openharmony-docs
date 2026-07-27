# Font Management Error Codes

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=cc8fe8b0f1b2859346994908b98ebf9b3df1ff9d translatedAt=2026-07-17T00:22:39.717Z pushedAt=2026-07-17T03:07:15.093Z -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 31100101 Font File Not Exist

**Error Message**

The font does not exist.

**Description**

This error code is reported if the input font file path does not exist.

**Possible Causes**

The font file path is incorrect.

**Solution**

Ensure that the input file is in **.ttf** or **.ttc** format and the path is correct.

## 31100102 Failed to Install Font File

**Error Message**

The font is not supported.

**Description**

This error code is reported if the input file is not a font file, leading to an installation failure.

**Possible Causes**

1. The input file is not in **.ttf** or **.ttc** format.

2. The file content does not comply with the font file specifications.

**Solution**

Ensure that the input file is in **.ttf** or **.ttc** format.

## 31100103 Failed to Copy Font File

**Error Message**

Failed to copy the font file.

**Description**

This error code is reported if copying the font file fails during installation.

**Possible Causes**

An exception occurs during font file copying.

**Solution**

Try again, or restart the device and try again.

## 31100104 Font File Already Installed

**Error Message**

The font file is installed.

**Description**

This error code is reported if the input font file has been installed.

**Possible Causes**

The input font file has been installed, and the font name is duplicate.

**Solution**

Uninstall the existing font with the same name and reinstall the font file.

## 31100105 Number of Installed Font Files Reaching the Maximum

**Error Message**

Exceeded the maximum number of installed files.

**Description**

This error code is reported if the number of installed font files reaches the maximum.

**Possible Causes**

The number of installed font files reaches the maximum (200).

**Solution**

Uninstall unnecessary font files and try again.

## 31100106 Font File Installation Failed Due to Other Errors

**Error Message**

The system ability works abnormally.

**Description**

This error code is reported if the font file installation fails because of a system error. 

**Possible Causes**

An exception occurs during font installation.

**Solution**

Try again, or restart the device and try again.

## 31100107 Uninstalled Font File Not Exist

**Error Message**

The font file does not exist.

**Description**

This error code is reported if the font file to be uninstalled does not exist.

**Possible Causes**

The font file to be uninstalled has not been installed, or the input font file name is incorrect.

**Solution**

Check whether the input font name is correct. If not, correct it and try again.

## 31100108 Failed to Delete Font File

**Error Message**

Failed to delete the font file.

**Description**

This error code is reported if deleting the font file fails during uninstallation.

**Possible Causes**

An exception occurs during uninstallation.

**Solution**

Try again, or restart the device and try again.

## 31100109 Uninstallation Failed Due to Other Errors

**Error Message**

The system ability works abnormally.

**Description**

This error code is reported if the font file uninstallation fails because of a system error. 

**Possible Causes**

An exception occurs during uninstallation.

**Solution**

Try again, or restart the device and try again.

## 31100110 Failed to Call the API Due to System Errors

**Error Message**

Call failed due to system error.

**Description**

The system service is abnormal, and the API fails to be called.

**Possible Causes**

A system exception occurred when the data migration task is started.

**Solution**

Perform the operation again or restart the device and then perform the operation again.

## 31100111 Migration Task Being Executed

**Error Message**

Data migration is in progress.

**Description**

The data migration task is in execution and cannot be started again.

**Possible Causes**

The data migration task is being executed.

**Solution**

Do not start the migration task repeatedly. Wait until the current task is completed.