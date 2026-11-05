# Font Management Error Codes

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @OningO-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=a04b9be3bedef1b09b05f9b1b2ad2d7c971b4692 translatedAt=2026-11-04T04:11:24.467Z pushedAt=2026-11-04T10:13:14.918Z nl=1 -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 31100101 Font File Not Exist

**Error Message**

The font does not exist.

**Symptom**

This error code is reported input font file path does not exist.

**Possible Causes**

The font file path is incorrect.
 
**Solution**

Ensure that the input file is in **.ttf** or **.ttc** format and the path is correct.

## 31100102 Failed to Install Font File

**Error Message**

The font is not supported.

**Symptom**

This error code is reported if the input file is not a font file, leading to an installation failure.

**Possible Causes**

1. The input file is not in **.ttf** or **.ttc** format.
2. The file content does not comply with the font file specifications.
 
**Solution**

Ensure that the input file is in **.ttf** or **.ttc** format.

## 31100103 Failed to Copy Font File

**Error Message**

Failed to copy the font file.

**Symptom**

This error code is reported if copying the font file fails during installation.

**Possible Causes**

An exception occurs during font file copying.
 
**Solution**

Try again, or restart the device and try again.

## 31100104 Font File Already Installed

**Error Message**

The font file is installed.

**Symptom**

This error code is reported if the input font file has been installed.

**Possible Causes**

The input font file has been installed, and the font name is duplicate.
 
**Solution**

Uninstall the existing font with the same name and reinstall the font file.

## 31100105 Number of Installed Font Files Reaching the Maximum

**Error Message**

Exceeded the maximum number of installed files.

**Symptom**

This error code is reported if the number of installed font files reaches the maximum.

**Possible Causes**

The number of installed font files exceeds the maximum limit.
 
**Solution**

Uninstall unnecessary font files and try again.

## 31100106 Font File Installation Failed Due to Other Errors

**Error Message**

The system ability works abnormally.

**Symptom**

This error code is reported if the font file installation fails because of a system error.

**Possible Causes**

An exception occurs during font installation.
 
**Solution**

Try again, or restart the device and try again.

## 31100107 Uninstalled Font File Not Exist

**Error Message**

The font file does not exist.

**Symptom**

This error code is reported if the font file to be uninstalled does not exist.

**Possible Causes**

The font file to be uninstalled has not been installed, or the input font file name is incorrect.
 
**Solution**

Check whether the input font name is correct. If not, correct it and try again.

## 31100108 Failed to Delete Font File

**Error Message**

Failed to delete the font file.

**Symptom**

This error code is reported if deleting the font file fails during uninstallation.

**Possible Causes**

An exception occurs during uninstallation.
 
**Solution**

Try again, or restart the device and try again.

## 31100109 Uninstallation Failed Due to Other Errors

**Error Message**

The system ability works abnormally.

**Symptom**

This error code is reported if the font file uninstallation fails because of a system error.

**Possible Causes**

An exception occurs during uninstallation.
 
**Solution**

Try again, or restart the device and try again.

## 31100110 Failed to Call the API Due to System Errors

**Error Message**

Call failed due to system error.

**Symptom**

The system service is abnormal, and the API fails to be called.

**Possible Causes**

A system exception occurs when starting a data migration task.
 
**Solution**

Perform the operation again or restart the device and then perform the operation again.

## 31100111 Migration Task Being Executed

**Error Message**

Data migration is in progress.

**Symptom**

A data migration task is in progress and cannot be started again.

**Possible Causes**

The data migration task is being executed.
 
**Solution**

Do not start the migration task again. Wait until the current task is complete.

## 31100112 Scope Font Not Found

**Error Message**

The scope font is not found.

**Description**

When uninstalling or querying a font, the font record corresponding to the specified font path (url) is not found.

**Possible Causes**

The font is not installed, or the font path (url) is entered incorrectly.
 
**Solution**

Check whether the application has installed this font and whether the font path (url) is correct.

## 31100113 Font Service State Listener Already Registered

**Error Message**

The font observer is already registered.

**Description**

The font service state listener is already registered and cannot be registered again.

**Possible Causes**

The same application repeatedly calls [fontManager.onFontObserver](js-apis-font-manager.md#fontmanageronfontobserver) to register the font service state listener.

**Solution**

No repeated registration is required. To update the font service state listener, call [fontManager.offFontObserver](js-apis-font-manager.md#fontmanagerofffontobserver) to unregister it first, and then register it again.

## 31100114 Maximum Number of Font Service State Listeners Exceeded

**Error Message**

The maximum number of font observers has been reached.

**Description**

The number of font service state change listeners registered by the same user exceeds the maximum limit (5).

**Possible Causes**

Five different applications have registered font service state change listeners for the same user.

**Solution**

Wait until other applications unregister their font service state change listeners, and then try again.

## 31100115 Font Service State Change Listener Not Registered

**Error Message**

The font observer is not registered.

**Description**

The font service state change listener is not registered when installing an application-level font or unregistering the font service state change listener.

**Possible Causes**

1. When calling [fontManager.installScopeFont](js-apis-font-manager.md#fontmanagerinstallscopefont) to install an application-level font, [fontManager.onFontObserver](js-apis-font-manager.md#fontmanageronfontobserver) is not called first to register the font service state change listener.
2. When calling [fontManager.offFontObserver](js-apis-font-manager.md#fontmanagerofffontobserver) to unregister the font service state change listener, the listener is not registered or has already been unregistered.

**Solution**

1. Before calling [fontManager.installScopeFont](js-apis-font-manager.md#fontmanagerinstallscopefont) to install an application-level font, call [fontManager.onFontObserver](js-apis-font-manager.md#fontmanageronfontobserver) to register the font service state change listener.
2. Before calling [fontManager.offFontObserver](js-apis-font-manager.md#fontmanagerofffontobserver) to unregister the font service state change listener, ensure that the listener is registered and has not been unregistered.