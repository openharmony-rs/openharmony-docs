# Universal Error Codes

<!--Kit: Common-->
<!--Subsystem: Common-->
<!--Owner: @zengyawen-->
<!--Designer: @lingminghw-->
<!--Tester: @RayShih-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=100e5b11e9eb72bea7c4221b30191424eac1d556 translatedAt=2026-11-02T14:35:59.867Z pushedAt=2026-11-03T03:29:38.703Z nl=1 -->

## 201 API Permission Verification Failed

**Error Message**

Permission verification failed. The application does not have the permission required to call the API.

**Description**

This error code is reported when permission verification fails.

**Possible Causes**

1. The application configuration file does not declare the required permission.

2. The sensitive permission has not been dynamically requested, and the user has not granted the permission.

3. The application identity does not meet the permission invocation constraints of the API.

**Solution**

1. Add the permission required by the API to the configuration file. For details, see [Declaring Permissions](../security/AccessToken/declare-permissions.md).

2. Add the dynamic request logic for sensitive permissions. For details, see [Requesting User Authorization](../security/AccessToken/request-user-authorization.md).

3. Ensure that the identity of the calling application meets the permission requirements of the API.

## 202 Non-System Application Calls System API

**Error Message**

Permission verification failed. A non-system application calls a system API.

**Description**

This error code is reported when a non-system application failed the permission verification.

**Possible Causes**

The API called by the application is a system API.

**Solution**

Check whether any system API is called. Delete it if any.

## 203 System Function Prohibited by Enterprise Management Policies

**Error Message**

This function is prohibited by enterprise management policies.

**Description**

The enterprise management policies do not allow the use of this system function.

**Possible Causes**

You attempted to operate a system function that has been disabled by the device management application.

**Solution**

Use [getDisallowedPolicy](./apis-mdm-kit/js-apis-enterprise-restrictions.md#restrictionsgetdisallowedpolicydeprecated) to check whether the system function is disabled, and use [setDisallowedPolicy](./apis-mdm-kit/js-apis-enterprise-restrictions.md#restrictionssetdisallowedpolicydeprecated) to remove the disabled state.

<!--Del-->
## 204 User Access Control Policy Interception, Access Denied

**Error Message**

Access denied due to user access control policy. Possible causes:
1. The operation is prohibited by OS-account constraints.
2. The required privilege for the operation has expired or has not been granted.

**Description**

Access is denied because it is intercepted by the user access control policy.

**Possible Causes**

1. OS-account constraints prohibit this operation.
2. The privilege required for this operation has expired or has not been granted.

**Solution**

1. Confirm the user constraints and user privileges involved in the target operation.
2. If the target operation is subject to constraint control, call [isOsAccountConstraintEnabled](./apis-basic-services-kit/js-apis-osAccount.md#isosaccountconstraintenabled11) to check whether the related constraint is enabled. If it is enabled, stop the operation.
3. If the target operation is subject to privilege control, call [acquireAuthorization](./apis-basic-services-kit/js-apis-osAccount-sys.md#acquireauthorization24) to request the required privilege. If the request succeeds, continue the target operation. Otherwise, stop the operation.
<!--DelEnd-->

## 401 Function Parameter Quantity or Type Mismatch

**Error Message**

Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.

**Description**

1. A mandatory parameter is left unspecified.

2. A parameter type is incorrect.

3. Parameter verification failed. Regardless of whether the API is synchronous or asynchronous, this type of error is generally thrown in synchronous mode.

**Possible Causes**

1. A mandatory parameter is not passed.

2. A parameter type is incorrect (Type Error).

3. The number of parameters is incorrect (Argument Count Error).

4. A null parameter is incorrect (Null Argument Error).

5. A parameter format is incorrect (Format Error).

6. A value range is incorrect (Value Range Error).

**Solution**

Make sure all the mandatory parameters are passed in and the types of the passed-in parameter are valid. If parameter verification fails, read the parameter specifications and locate the fault based on the possible causes.

## 501 Resource Occupied by Another Thread, Access Denied

**Error Message**

Access denied because the resource is occupied by another thread.

**Symptom**

The resource is occupied and locked by another thread, so this access request is denied.

**Possible Cause**

The resource is currently being used by another thread, so the operation cannot be completed.

**Solution**

Ensure that the same component/resource is used in only one thread.

## 801 API Not Supported on Some Devices

**Error Message**

Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported.

**Description**

The function is not supported.

**Possible Causes**

This error code may occur in the following scenarios: the hardware does not support the capability, or a dependent service feature is not supported.

**Solution**

1. Avoid using this API on the device.

2. If the API has a preceding isxxxsupported interface, call isxxxsupported first to check whether the API function is supported, and then call this API.

## 803 Service Unavailable in the Current Country or Region

**Error Message**

The service is unavailable in the current country or region.

**Symptom**

The service is unavailable in the current country or region.

**Possible Cause**

The service is not available in the current country.

**Solution**

The application should catch the error and isolate the functions provided by the service to avoid affecting user experience. You can further query the developer documentation for the countries and regions supported by the Kit.

<!--RP1--><!--RP1End-->