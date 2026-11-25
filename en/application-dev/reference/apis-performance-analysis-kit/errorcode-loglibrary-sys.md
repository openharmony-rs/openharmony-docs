# Log Library Error Codes

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @BruceZong-->
<!--Designer: @tangyyan-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=f00a13769ab903f0badf660649729d0cd8470528 translatedAt=2026-09-16T11:11:08.629Z pushedAt=2026-09-20T09:01:52.271Z -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 21300001 Specified File Not Exist

**Error Message**

The specified file does not exist.

**Description**

The specified log file does not exist when the copy, move, or delete API of the log file is called for file operations.

**Possible Causes**

- The input file name is incorrect.

- The file with the input file name does not exist in the device storage.

**Procedure**

- Check whether the input file name is correct, including the file name spelling and path format.
- Check whether the file exists in the device storage, and verify that the file path and log directory configuration are correct.
