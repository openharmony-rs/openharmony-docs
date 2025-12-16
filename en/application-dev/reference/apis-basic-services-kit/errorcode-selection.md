# Word Selection Service Error Codes

<!--Kit: Basic Services Kit-->
<!--Subsystem: SelectionInput-->
<!--Owner: @no86-->
<!--Designer: @mmwwbb-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @fang-jinxu-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 33600001 Word Selection Service Error

**Error Message**

Selection service exception.

**Description**

This error code is reported when the word selection service is abnormal.

**Possible Causes**

An error is thrown when an application calls the word selection service or its dependent services.

**Solution**

Restart the device and try again.

## 33600002 Word Selection Panel Has Been Destroyed

**Error Message**

This selection window has been destroyed.

**Description**

This error code is reported when the word selection panel has been destroyed.

**Possible Causes**

1. The word selection panel object is invalid.
2. The word selection panel is not created.

**Solution**

1. Ensure the word selection panel object is valid before operating the panel.
2. Do not operate the destroyed word selection panel object.

## 33600003 Invalid Application for Word Selection

**Error Message**

Invalid operation. The selection app is not valid.

**Description**

This error code is reported when an invalid application calls the word selection API.

**Possible Causes**

An invalid application calls the word selection API.

**Solution**

Ensure the current application is valid for using word selection.

## 33600004 The API Is Called Too Frequently

**Error Message**

The interface is called too frequently.

**Description**

This error code is reported when the API is called too frequently.

**Possible Causes**

The API is called more than 50 times within 500 ms.

**Solution**

Call this API only after receiving the word selection notification.

## 33600005 Incorrect API Call Timing

**Error Message**

The interface is called at the wrong time.

**Description**

This error code is reported when the API is called at an incorrect time.

**Possible Causes**

The user may not have selected words.

**Solution**

Call this API only after receiving the word selection notification.

## 33600006 Word Selection Prohibited in the Current Application

**Error Message**

The current application is prohibited from accessing content.

**Description**

This error code is reported when the current application does not allow word selection.

**Possible Causes**

The text content cannot be shared with other applications.

**Solution**

Switch to an application that allows word selection and call this API again.

## 33600007 Selected Text Is Out of Range

**Error Message**

The length of selected content is out of range.

**Description**

This error code is reported when the selected text is out of range.

**Possible Causes**

The selected text contains more than 2000 characters.

**Solution**

Select text within 2000 characters and call this API again.

## 33600008 Content Acquisition Timed Out

**Error Message**

Getting the selected content times out.

**Description**

This error code is reported when the selected text fails to be obtained within a specified period.

**Possible Causes**

The application cannot return the selected text within a specified period.

**Solution**

Call this API again.
