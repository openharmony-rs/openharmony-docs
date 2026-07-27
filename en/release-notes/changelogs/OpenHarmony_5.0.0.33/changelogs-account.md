# Account Subsystem Changelog

## cl.account_os_account.1. queryDistributedVirtualDeviceld Error Code Is Changed

**Access Level**

Public API

**Reason for Change**

According to the JS error code specifications, error code 201 is returned when access is denied due to insufficient permission. However, error code 12300001 (system error) is also returned when access is denied due to insufficient permission. Developers cannot determine the error based on the error code returned.

**Impact of the Change**

This change is a non-compatible change.

Before change: If the caller does not have the permission when calling **queryDistributedVirtualDeviceld**, error code 12300001 is returned.

After change: If the caller does not have the permission when calling **queryDistributedVirtualDeviceld**, error code 201 is returned.

**Start API Level**

9

**Change Since**

OpenHarmony SDK 5.0.0.33

**Key API/Component Changes**

queryDistributedVirtualDeviceld

**Adaptation Guide**

No adaptation is required because the problem can be detected during development.
