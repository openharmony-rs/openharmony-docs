# JsLeakWatcher Error Codes

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @Lutao98-->
<!--Designer: @martin_duan-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=2f737406ac68f4723c8c6f76a0b33412cdf44738 translatedAt=2026-09-16T11:09:45.587Z pushedAt=2026-09-20T09:01:52.270Z -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 10801001 Invalid isEnabled Parameter

**Error Message**

The parameter isEnabled is invalid.

**Description**

When the **enableLeakWatcher** function is called, the invalid parameter **isEnabled** is input.

**Possible Causes**

1. The type of **isEnabled** is incorrect.

2. Mandatory parameters are not specified.


**Solution**

Ensure that the type of **isEnabled** is correct.

## 10801002 Invalid config Parameter

**Error Message**

The parameter config is invalid.

**Description**

When the **enableLeakWatcher** function is called, the invalid parameter **config** is input.

**Possible Causes**

1. The type of **config** is incorrect.

2. Mandatory parameters are not specified.

3. Parameter verification failed. This parameter is an array of strings. The array must contain one or more of **XComponent**, **NodeContainer**, **Window**, **CustomComponent**, and **Ability**.

**Solution**

Ensure that the type of **config** is correct.

## 10801003 Invalid callback Parameter

**Error Message**

The parameter callback is invalid.

**Description**

When the **enableLeakWatcher** function is called, the invalid parameter **callback** is input.

**Possible Causes**

1. The type of the input parameter **callback** is incorrect.

2. Required parameters are not specified.

3. Parameter verification failed. The input parameter of the **callback** function is an array of two string elements.

**Solution**

Ensure that the type of **callback** is correct. The input parameter of the **callback** function is an array of two strings.

Index 0 is the leak list file name with the suffix .jsleaklist; index 1 is the virtual machine memory snapshot file name with the suffix .rawheap.

