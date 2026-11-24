# Ads Service Framework Error Codes

<!--Kit: Ads Kit-->
<!--Subsystem: Advertising-->
<!--Owner: @ctssss-->
<!--Designer: @zhansf1988-->
<!--Tester: @hongmei_may-->
<!--Adviser: @RayShih-->
<!-- md-trans-meta sourceCommit=6493b14494a6c6b34e36a2da0a181b6e9e0f901d translatedAt=2026-11-23T09:09:45.719Z pushedAt=2026-11-24T11:34:44.640Z nl=1 -->


> **NOTE**
> 
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).


## 21800001 Internal System Error

**Error Message**

System internal error.

**Description**

An internal system error occurs (for example, failure to register or delete a JavaScript object of a Web component).

**Possible Causes**

Failed to connect to the OAID service.

**Procedure**

1. Restart the device and try again.

2. If your issue remains unresolved, please prioritize using Qidian QQ: 800183590 or the [Manual Transfer Link](https://webpage.qidian.qq.com/qidian/chatv3/pc.html?linkType=1&env=ol&kfuin=2885820057&fid=365&key=646c4489e237ea477e85483a1791dfaa&cate=1&type=16&ftype=1&_type=wpa&qidian=true&waitTime=10005&clickid=ad71nq.wg8a2n.l1fu39si&callImType=1&delayTime=10&roleValue=1&roleData=474&translateSwitch=0&source=0&isLBS=0&isSsc=0&isCustomEntry=0&im_jump_from=v2_1) to contact technical personnel for troubleshooting. If the above methods fail to resolve the issue, submit the issue via <!--RP1-->Online Ticket Submission<!--RP1End-->.


## 21800003 Ad Loading Failure

**Error Message**

Failed to load the ad request.

**Description**

This error code is reported if loading the ad fails.

**Possible Causes**

1. The server does not have proper ad filling. Whether a device returns an ad depends on factors such as the ad floor price setting, user negative feedback blocking, or algorithm decisions. Therefore, it cannot be guaranteed that every request is filled.

**Procedure**

1. Check the network status.

2. Check whether the ad request parameters meet the requirements based on the API reference.

3. If a single device still cannot request advertisements after multiple requests, it is recommended to test with multiple devices. If your issue remains unresolved, please prioritize using Qidian QQ: 800183590 or the [Manual Transfer Link](https://webpage.qidian.qq.com/qidian/chatv3/pc.html?linkType=1&env=ol&kfuin=2885820057&fid=365&key=646c4489e237ea477e85483a1791dfaa&cate=1&type=16&ftype=1&_type=wpa&qidian=true&waitTime=10005&clickid=ad71nq.wg8a2n.l1fu39si&callImType=1&delayTime=10&roleValue=1&roleData=474&translateSwitch=0&source=0&isLBS=0&isSsc=0&isCustomEntry=0&im_jump_from=v2_1) to contact technical personnel for troubleshooting. If the above methods fail to resolve the issue, submit the issue via <!--RP2-->Online Ticket Submission<!--RP2End-->.


## 21800004 Ad Display Failure

**Error Message**

Failed to display the ad.

**Description**

This error code is reported if displaying the ad fails.

**Possible Causes**

The network connection is abnormal.

**Procedure**

Check the network status.


## 21800005 Ad Data Parsing Failure

**Error Message**

Failed to parse the ad response.

**Description**

This error code is reported if ad data is failed to be parsed.

**Possible Causes**

Key attributes are missing or the structure of the ad response data is incorrect.

**Procedure**

Check the ad response data.