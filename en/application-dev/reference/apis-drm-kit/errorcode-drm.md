# DRM Error Codes

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 24700101 Unknown Error

**Error Message**

Unknown error.

**Description**

An unknown error occurs.

**Possible Causes**

The parameter format or data type is incorrect, causing data retrieval or conversion failures.

**Procedure**

Check the exception description for details, review system error logs for additional context, and address the issue based on the error information found.

## 24700103 Too Many MediaKeySystem Instances

**Error Message**

Too many MediaKeySystem instances.

**Description**

The maximum number of MediaKeySystem instances (64) has been reached.

**Possible Causes**

Unused MediaKeySystem instances are not properly released.

**Procedure**

Release any MediaKeySystem instances that are no longer needed.

## 24700104 Too Many MediaKeySession Instances

**Error Message**

Too many MediaKeySession instances.

**Description**

The maximum number of MediaKeySession instances (64) has been reached.

**Possible Causes**

Unused MediaKeySession instances are not properly released.

**Procedure**

Release any MediaKeySession instances that are no longer needed.

## 24700201 Service Exception

**Error Message**

Service error. For example, the service crashed.

**Description**

The DRM service encountered a fatal error.

**Possible Causes**

1. An error occurs during the DRM plugin execution.

2. The DRM service process is terminated.

**Procedure**

Check the exception description for details, review system error logs for additional context, and address the issue based on the error information found.
