# Calendar Kit Error Codes

<!--Kit: Calendar Kit-->
<!--Subsystem: Applications-->
<!--Owner: @qq_42718467-->
<!--Designer: @huangxinwei-->
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

**Solution**

1. Check whether the length of the parameter value (string) exceeds the valid range.

2. Check whether the parameter value is out of range.

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

Internal processing exception.

**Solution**

An internal exception has occurred. Try again later.
