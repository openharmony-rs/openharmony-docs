# Router Error Codes

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @huangxiaolinabc-->
<!--Designer: @fangzhiyuan1-->
<!--Tester: @Giacinta-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=66d449f865d808c2ab2228de4384c97bf7b4883d translatedAt=2026-08-19T08:37:41.144Z pushedAt=2026-08-19T08:50:51.767Z -->

Page routing error codes are used to identify common errors in scenarios such as page redirection, page replacement, and Navigation-based redirection, helping you quickly locate issues in route configuration, page stack, and parameter passing.

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 100002 Incorrect URI During Page Redirection

**Error Message**

Uri error. The URI of the page to redirect is incorrect or does not exist.

**Description**

This error code is reported when the URI of the page to redirect is incorrect or does not exist. This error code is represented as a string type.

**Possible Causes**

The entered URI is incorrect or does not exist.

**Solution**

Ensure that the URI is correct.

## 100003 Too Many Pages Are Pushed into the Page Stack

**Error Message**

Page stack error. Too many pages are pushed.

**Description**

This error code is reported when more than 32 pages are pushed into the page stack. This error code is represented as a string type.

**Possible Causes**

More than 32 pages are pushed.

**Solution**

Delete unnecessary or invalid pages.

## 100004 Incorrect Route Name

**Error Message**

Named route error. The named route does not exist.

**Description**

This error code is reported when the specified route name for redirection is incorrect or does not exist. This error code is represented as a string type.

**Possible Causes**

The specified route name for redirection is incorrect or does not exist.

**Solution**

Verify that the specified route name for redirection is correct and exists.

## 100005 Builder Function Not Registered During Navigation

**Error Message**

Builder function not registered.

**Description**

This error code is reported during navigation when the builder function for creating the **NavDestination** component is not registered.

**Possible Causes**

- The builder function for creating the **NavDestination** component is not registered during navigation.

- The target page for navigation does not contain the **Navigation** component.

- The route table is not configured.

**Solution**

Perform the following:

1. Check whether **Navigation** provides the builder function for creating **NavDestination**.

2. Ensure that the route table is correctly configured.

3. Ensure that the target page for navigation contains the **Navigation** component.

## 100006 NavDestination Not Found

**Error Message**

NavDestination not found.

**Description**

This error code is reported when no **NavDestination** component is found for navigation.

**Possible Causes**

No **NavDestination** component is available for navigation.

**Solution**

Make sure there is a **NavDestination** component for navigation.

## 106200 Invalid Index Value

**Error Message**

index value is invalid.

**Description**

This error code is reported when an invalid index value is passed when a route-related API is called.

**Possible Causes**

The passed index value is invalid, for example, less than 0 or beyond the valid range of the page stack.

**Solution**

Ensure that the passed index value is a valid integer within the valid range of the current page stack.

## 106201 Failed to Obtain Route Navigation Information

**Error Message**

Failed to query route navigation information.

**Description**

This error code is reported when the system fails to query route navigation information because the current node is not mounted under a page.

**Possible Causes**

The current node may not be mounted under the page.

**Solution**

Check whether the current node is on the page.

## 106202 Buffer Size Not Sufficient to Hold the Target Data

**Error Message**

buffer size is not large enough.

**Description**

This error code is reported when the input buffer size is not large enough to hold the target data.

**Possible Causes**

The provided buffer size is smaller than the minimum required to accommodate the target data.

**Solution**

Ensure that the provided buffer size meets the minimum buffer size requirement.

## 200002 Incorrect URI During Page Replacement

**Error Message**

Uri error. The URI of the page to be used for replacement is incorrect or does not exist.

**Description**

This error code is reported when the URI of the page to be used for replacement is incorrect or does not exist. This error code is represented as a string type.

**Possible Causes**

The entered URI is incorrect or does not exist.

**Solution**

Ensure that the URI is correct.

## 300001 Silent Installation of the HSP Failed Before Navigation

**Error Message**

hsp silent install fail.

**Description**

This error code is reported when the silent installation of the HSP containing the target page fails before **Navigation** performs the redirection.

**Possible Causes**

The target HSP to be downloaded does not exist.

**Solution**

Verify that the HSP for the target navigation page actually exists. Make sure the value of **moduleName** passed in is correct.