# Address Data Donation Error Codes
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @weixin_40768329-->
<!--Designer: @CynthiaYeh-->
<!--Tester: @logic42; @zhaofangyuan-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=2dce00494a531365f1539a0b35b0f7ad3001bd09 translatedAt=2026-11-03T04:20:31.234Z pushedAt=2026-11-03T12:08:25.476Z nl=1 -->

> **NOTE**
>
> The following describes only the error codes specific to this module. For details about the universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 36900001 Internal Error in the API

**Error Message**

Internal error in the API.

**Description**

An internal error occurs in the system service.

**Possible Causes**

The internal state of the system service is abnormal, or a system error occurs (for example, null pointer, insufficient memory, abnormal restart of the system service, or IPC exception).

**Solution**

Try calling the interface again. If the problem persists, prompt the user to restart the application, upgrade the application, or upgrade the device version.

## 36900002 Subscription Failed

**Error Message**

Subscription failed.

**Description**

This error code is reported when the system fails to subscribe to address data update events by calling [onDataFabricAddress](js-apis-data-dataFabricAddress-sys.md#datafabricaddressondatafabricaddress).

**Possible Causes**

The subscription API is called again after a successful subscription without unsubscribing first.

**Solution**

If the service needs to subscribe again, call [offDataFabricAddress](js-apis-data-dataFabricAddress-sys.md#datafabricaddressoffdatafabricaddress) to unsubscribe first, and then call [onDataFabricAddress](js-apis-data-dataFabricAddress-sys.md#datafabricaddressondatafabricaddress) to subscribe. Otherwise, ignore this error, as the successfully subscribed service is not affected.

## 36900003 Unsubscription Failed

**Error Message**

Unsubscription failed.

**Description**

This error code is reported when the [offDataFabricAddress](js-apis-data-dataFabricAddress-sys.md#datafabricaddressoffdatafabricaddress) API fails to unsubscribe from the address data update event.

**Possible Causes**

The unsubscribe API is called directly without a successful subscription.

**Solution**

Call [onDataFabricAddress](js-apis-data-dataFabricAddress-sys.md#datafabricaddressondatafabricaddress) to subscribe successfully, and then call [offDataFabricAddress](js-apis-data-dataFabricAddress-sys.md#datafabricaddressoffdatafabricaddress) to unsubscribe.

## 36900004 Operation Not Supported

**Error Message**

Operation not supported.

**Description**

This error code is reported when the parameters passed in are in the correct format but the conditions are not met during API calling.

**Possible Causes**

1. Currently, only the commute navigation scenario is supported. This error code is reported when the passed scenario type is not the commute navigation scenario.

2. During subscription or update, this error code is reported when the scenario type is the commute navigation scenario and the distance between the passed home and company is less than the minimum distance supported by the configuration.

3. During update, this error code is reported when no subscription has been made yet.

**Solution**

1. Configure the scenario type as the commuting navigation scenario (currently only this scenario is supported).

2. Ensure that the distance between the home and the company is not less than the minimum supported distance. The default value of this distance is 1000 meters, and it can be adjusted to other values through cloud-pushed configuration.

3. If performing an update operation, first call the subscribe interface to subscribe successfully, and then perform the update.

## 36900005 Invalid Parameter

**Error Message**

Invalid parameter.

**Description**

This error code is reported when an invalid parameter is passed in while calling an interface.

**Possible Causes**

1. An enum parameter is out of the enum range.

2. The longitude or latitude of a coordinate is out of range.

3. The number of reference points exceeds the limit or does not meet the service scenario requirements.

**Solution**

1. Check whether the enum type parameter exceeds the enum range.

2. Check whether the coordinate longitude and latitude are valid: the longitude is within the range of -180° to 180°, and the latitude is within the range of -90° to 90°.

3. Check whether the number of reference points is within the range of [0, 128] and meets the business scenario requirements: the commuting navigation scenario must have 2 reference points.
