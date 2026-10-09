# Settings Error Codes

<!--Kit: Basic Services Kit-->
<!--Subsystem: Applications-->
<!--Owner: @YingCong-->
<!--Designer: @Kun_Wu-->
<!--Tester: @dyx118186878-->
<!--Adviser: @fang-jinxu-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 14800000 Parameter Check Failed

**Error Message**

Parameter error. Possible causes: 1. Parameter verification failed.

**Description**

1. This error code is reported when the null parameter is incorrect.

2. This error code is reported when the parameter parsing fails.

**Possible Causes**

1. A null parameter is incorrect (Null Argument Error).

2. A value range is incorrect (Value Range Error).

**Solution**

Make sure all the mandatory parameters are passed. If parameter verification fails, read the parameter specifications and locate the fault based on the possible causes.

## 14800010 UIAbility Required

**Error Message**

Original service error.

**Description**

This error code is reported when the original service throws an error.

**Possible Causes**

The current context is not the UIAbility.

**Solution**

Perform the operation on UIAbility.

## 16900010 Parameter Check Failed

**Error Message**

Parameter error.

**Description**

This error code is reported when the type or format of the parameter is incorrect.

**Possible Causes**

1. A null parameter is incorrect (Null Argument Error).

2. A value range is incorrect (Value Range Error).

**Solution**

Make sure all the mandatory parameters are passed. If parameter verification fails, read the parameter specifications and locate the fault based on the possible causes.

## 16900020 Failed to Open the Settings Page

**Error Message**

Failed to open the settings page via redirection.

**Description**

This error code is reported when the settings page fails to be opened.

**Possible Causes**

An internal error occurs.

**Solution**

Restart the application or device and try again.
