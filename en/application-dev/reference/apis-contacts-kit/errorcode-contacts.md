# Contact Error Codes

<!--Kit: Contacts Kit-->
<!--Subsystem: Applications-->
<!--Owner: @librahCode-->
<!--Designer: @jiayanhong-hw-->
<!--Tester: @shangzhijie-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=4c038a1d5da345aacbf8335a571bab67edf916cc translatedAt=2026-07-29T01:29:40.122Z pushedAt=2026-07-30T03:36:33.456Z -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 16700001 System Internal Error

**Error Message**

General error.

**Description**

This error code is reported if an internal system error occurs.

**Possible Causes**

The internal system processing is abnormal.

**Solution**

A system error has occurred. Try again later.

## 16700002 Parameter Check Failed

**Error Message**

Invalid parameter value.

**Description**

Parameter verification failed.

**Possible Causes**

1. A null parameter is incorrect (Null Argument Error).

2. A parameter format is incorrect (Format Error).

3. A value range is incorrect (Value Range Error).

**Solution**

Please review the parameter specification constraints and perform troubleshooting based on the possible causes.

## 16700003 Background Service Calling Prohibited

**Error Message**

Background usage is prohibited.

**Description**

Background service calling is prohibited.

**Possible Causes**

The service is called in the background.

**Solution**

Ensure that the caller is running in the foreground.

## 16700004 Number of Contacts Exceeds the Limit

**Error Message**

The number of contacts exceeds the upper limit.

**Description**

The number of contacts exceeds the limit.

**Possible Causes**

The number of contacts passed in exceeds the upper limit.

**Solution**

Check the number of contacts.

## 16700101 Database Query Failed

**Error Message**

Failed to get value from contacts data.

**Description**

This error code is reported if database query fails.

**Possible Causes**

Database operation has failed.

**Solution**

Database access has failed. Try again later.

## 16700102 Database Data Addition, Deletion or Modification Failed

**Error Message**

Failed to set value to contacts data.

**Description**

This error is reported if the attempt to add, delete, or modify data in the database fails.

**Possible Causes**

Database operation has failed.

**Solution**

Database access has failed. Try again later.

## 16700103 Operation Canceled

**Error Message**

User cancel.

**Description**

This error code is reported if an operation is canceled by the user.

**Possible Causes**

The user cancels the operation.

**Solution**

The user cancels the operation. Try again later.

## 401 Failed to Open the Contact Portrait File

**Error Message**

Failed to open contact portrait file.

**Description**

The contact portrait file fails to be opened.

**Possible Causes**

The portrait file path is incorrect, the file does not exist, or the disk is damaged.

**Solution**

Check whether the file exists.

## 401 Internal System Error

### Invalid Internal Associated Contact ID

**Error Message**

Internal error. Invalid contact id. Failed to generate contact profile.

**Description**

The ID of the internal associated contact is invalid.

**Possible Causes**

The internal system processing is abnormal.

**Solution**

A system error has occurred. Try again later.

### Failed to Save the Contact Portrait

**Error Message**

Internal error. Failed to save contact portrait.

**Description**

The contact portrait fails to be saved.

**Possible Causes**

The portrait file is abnormal, or the internal system processing is abnormal.

**Solution**

Check the file.

### Database Query Result Set is a Null Pointer

**Error Message**

Internal error. The query resultSet is nullptr.

**Description**

The database query result set is a null pointer.

**Possible Causes**

The internal system processing is abnormal.

**Solution**

A system error has occurred. Try again later.

### Database Query Result Set Exists But Contains No Data

**Error Message**

Internal error. The query resultSet is empty.

**Description**

The database query result set exists but contains no data.

**Possible Causes**

The internal system processing is abnormal.

**Solution**

A system error has occurred. Try again later.

### Invalid Internal Associated Contact rawId

**Error Message**

Internal error. Invalid contact rawId.

**Description**

The **rawId** value of the internal associated contact is invalid.

**Possible Causes**

The internal system processing is abnormal.

**Solution**

A system error has occurred. Try again later.