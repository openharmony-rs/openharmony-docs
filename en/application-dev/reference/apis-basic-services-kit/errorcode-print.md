# Print Service Error Codes

 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @guoshengbang-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=a077482f26289b96749dbeb1a0c6856695ebea0a translatedAt=2026-09-01T03:22:35.148Z pushedAt=2026-09-05T03:44:20.027Z -->

> **NOTE**
>
> The print service provides capabilities such as print job management, printer query and configuration, and print extension management. It is applicable to scenarios where apps need to integrate the printing function, manage print jobs, and configure printers, helping developers easily print documents and images.
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 13100001 General Print Exception

**Error Message**

Generic failure of print.

**Possible Causes**

This error code indicates a general print exception. Possible causes are as follows:
1. Failure to create a task object inside the print service.

**Solution**

Close the print page to release resources and try again. If the error persists, restart the device to reset the print service status. Before calling print-related APIs, ensure that the print service is normal.

## 13100002 RPC Failure

**Error Message**

RPC failure.

**Possible Causes**

The possible causes are as follows:
1. Failed to obtain the SA service object.
2. Inter-process communication failed.

**Solution**

Close the print page to release resources and try again. If the error persists, restart the device to obtain the SA service object again and restore inter-process communication. Before calling print-related APIs, ensure that the SA service object is available and inter-process communication is normal.

## 13100003 Print Service Exception

**Error Message**

Failure of print service.

**Possible Causes**

This error code indicates a print service exception. Possible causes are as follows:
1. Failed to start the print service.
2. Failed to start the cups service.

**Solution**

Close the print page to restart the print service and try again. If the error persists, restart the device to reset the cups service. Before calling print-related APIs, ensure that the print service and cups service are available.

## 13100004 Invalid Print Extension

**Error Message**

Invalid print extension.

**Possible Causes**

The possible causes are as follows:
1. The print extension cannot be found.
2. The print extension parameters are incorrect.
3. The print extension is in an invalid state.

**Solution**

Close the print page to release resources and try again. If the error persists, restart the device to reload the print extension. You are advised to check whether the extension parameters and status are valid before using the print extension.

## 13100005 Invalid Printer

**Error Message**

Invalid printer.

**Possible Causes**

The possible causes are as follows:
1. Incorrect printer ID.
2. The cups failed to query the printer list.
3. The cups failed to query the printer information.

**Solution**

Check whether the printer ID and printer information are correct, and try again. If the query fails, restart the device to reinitialize the cups service. You are advised to verify whether the preceding information is valid before calling print-related APIs.

## 13100006 Invalid Print Job

**Error Message**

Invalid print job.

**Possible Causes**

The possible causes are as follows:
1. Incorrect print job ID.
2. Incorrect print job status.
3. The print job cannot be found.

**Solution**

Check whether the print job ID and status are correct, and try again. If the job cannot be found, cancel the current printing operation and initiate printing again. If the issue persists, restart the device to reset the print service. You are advised to verify that the preceding information is correct before performing operations on the print job.
