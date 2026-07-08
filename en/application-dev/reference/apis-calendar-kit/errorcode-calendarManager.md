# Calendar Kit Error Codes

<!--Kit: Calendar Kit-->
<!--Subsystem: Applications-->
<!--Owner: @qq_42718467-->
<!--Designer: @windsky6-->
<!--Tester: @z30055209-->
<!--Adviser: @ge-yafang-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 23900001 Parameter Value Error

**Error Message**

Parameter value error.

**Description**

Invalid parameter value.

**Possible causes**

1. The length of the parameter value (string) exceeds the valid range.

2. The parameter value is out of the valid range.

3. The input ID does not exist.

4. The permission is restricted.

**Solution**

1. Check whether the length of the parameter value (string) exceeds the valid range.

2. Check whether the parameter value is out of range.

3. Call the **getEvents** API to obtain the event with the corresponding ID and check whether the passed ID exists.

4. Check whether the permission is restricted.

## 23900003 Specified Account Not Found

**Error Message**

The specified account was not found.

**Description**

The specified account does not exist.

**Possible causes**

The entered account does not match the created account, so the queried account does not exist.

**Solution**

Use the created account instead of a non-created one.

## 23900004 Internal Program Error

**Error Message**

Internal program error.

**Description**

An internal program error occurred.

**Possible causes**

1. **dataShare** database execution error.

2. Null pointer error.

3. Data parsing error.

**Solution**

An internal exception has occurred. Try again later.

## 23900005 Event Not Editable

**Error Message**

This event cannot be edited.

**Description**

The event cannot be edited.

**Possible causes**

The event with the corresponding ID cannot be edited.

**Solution**

1. Check the type of the account to which the event belongs. Only local accounts can view and edit events.

2. Check the event type. Important events cannot be viewed or edited.
