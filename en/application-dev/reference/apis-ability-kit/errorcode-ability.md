# Ability Error Codes

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @dsz2025; @Luobniz21-->
<!--Designer: @ccllee1-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 16000001 Ability Name Does Not Exist

**Error Message**

The specified ability does not exist.

**Description**

This error code is reported when the specified ability name does not exist.

**Possible Causes**

The ability to query does not exist.

**Solution**

1. Check whether the values of **bundleName**, **moduleName**, and **abilityName** in **want** are correct.
2. Check whether the application corresponding to **bundleName** in **want** is installed. You can run the following command to query the list of installed applications. If **bundleName** is not in the query result, the application is not installed.
    ```
    hdc shell bm dump -a
    ```
3. For a multi-HAP application, check whether the HAP to which the ability belongs is installed. You can run the following command to query the bundle information. If the installed application does not contain the corresponding HAP and ability, the HAP to which the ability belongs is not installed.
    ```
    hdc shell bm dump -n bundleName
    ```

## 16000002 Incorrect Ability Type

**Error Message**

Incorrect ability type.

**Description**

This error code is reported when the ability type for the API call is incorrect.

**Possible Causes**

The ability with the specified type does not support the API call.

**Solution**

1. Check whether the values of **bundleName**, **moduleName**, and **abilityName** in **want** are correct.
2. Call APIs based on the ability type. For example, call <!--Del-->[startServiceExtensionAbility](js-apis-inner-application-uiAbilityContext-sys.md#startserviceextensionability) to start the ServiceExtensionAbility, or call <!--DelEnd-->[connectServiceExtensionAbility()](js-apis-inner-application-uiAbilityContext.md#connectserviceextensionability) to connect to the ServiceExtensionAbility. Additionally, ensure that the value of **type** under **extensionAbilities** in the [module.json5](../../quick-start/module-configuration-file.md) file matches the service you are using.

## 16000003 ID Does Not Exist

**Error Message**

The specified ID does not exist.

**Description**

This error code is reported when the specified ID does not exist.

**Possible Causes**

The target with the specified ID does not exist.

**Solution**

Use the correct ID.

## 16000004 Visibility Verification Failure

**Error Message**

Cannot start an invisible component.

**Description**

This error code is reported when the application fails visibility verification.

**Possible Causes**

Visibility verification fails.

**Solution**

1. Check whether [exported](../../quick-start/module-configuration-file.md#abilities) under the **Ability** field in the **module.json5** file of the ability is set to **true**. If this parameter is set to **true**, the ability can be started by other applications. If this parameter is set to **false**, the ability cannot be started by other applications.
2. To start the ability for which **exported** is set to **false**, the caller must request the ohos.permission.START_INVISIBLE_ABILITY permission, which is available only for system applications.

## 16000005 Process Permission Verification Failure

**Error Message**

The specified process does not have the permission.

**Description**

This error code is reported when the specified process fails permission verification.

**Possible Causes**

Permission verification for the specified process fails.

**Solution**

Check whether the caller has the permission required by the target component.

## 16000006 Cross-User Operation Is Not Allowed

**Error Message**

Cross-user operations are not allowed.

**Description**

This error code is reported when an application tries to perform a cross-user operation.

**Possible Causes**

The application initiates a cross-user operation.

**Solution**

Check whether a cross-user operation is being attempted by checking whether the user ID passed during the API call matches the current userID.

## 16000007 Service Unresponsive

**Error Message**

Service busy. There are concurrent tasks. Try again later.

**Description**

This error code is reported when the system service is not responding.

**Possible Causes**

The application tries to access the system service before it is fully started.

**Solution**

Wait until the system service is started and then try again.

## 16000008 Crowdtesting Application Expires

**Error Message**

The crowdtesting application expires.

**Description**

This error code is reported when users try to open a crowdtesting application that has expired.

**Possible Causes**

The crowdtesting application has expired.

**Solution**

Check whether the application has expired. A crowdtesting application that has passed its validity period cannot be started.

## 16000009 Ability Start or Stop Failure in Wukong Mode

**Error Message**

An ability cannot be started or stopped in Wukong mode.

**Description**

This error code is returned when the application tries to start or stop an ability in Wukong mode.

**Possible Causes**

An ability cannot be started or stopped in Wukong mode.

**Solution**

Exit Wukong mode, and then start or stop the ability.  

## 16000010 Continuation Flag Is Forbidden

**Error Message**

The call with the continuation and prepare continuation flag is forbidden.

**Description**

This error code is reported when the API call carries the continuation flag.

**Possible Causes**

The continuation flag is not allowed for the API call.

**Solution**

Remove the continuation flag.

## 16000011 Context Does Not Exist

**Error Message**

The context does not exist.

**Description**

This error code is reported when the specified context does not exist.

**Possible Causes**

The context passed in the API does not exist.

**Solution**

Use the correct context.

## 16000012 Application Under Control

**Error Message**

The application is controlled.

**Description**

This error code is reported when the application is under control.

**Possible Causes**

The application is controlled by the system control module and is not allowed to start.

**Solution**

The target application is prohibited from being started. Try the call again later.

## 16000013 Application Controlled by EDM

**Error Message**

The application is controlled by EDM.

**Description**

This error code is reported when an application is controlled by [Enterprise Device Manager (EDM)](../../mdm/mdm-kit-admin.md).

**Possible Causes**

The application is controlled by EDM.

**Solution**

Contact the enterprise device management personnel.

## 16000015 Service Timeout

**Error Message**

Service timeout.

**Description**

This error code is reported when the service requested times out.

**Possible Causes**

The service times out.

**Solution**

Try again later.

## 16000018 Restricting Redirection to Third-Party Applications of API Version 11 or Later

**Error Message**

Redirection to a third-party application is not allowed in API version greater than 11.

**Description**

For applications with an API version later than 11, explicit redirection to other third-party applications is not allowed.

**Possible Causes**

The application uses an API version later than 11 and attempts to explicitly redirect to a third-party application.

**Solution**

Use implicit startup or [openLink](js-apis-inner-application-uiAbilityContext.md#openlink12) for redirection.

## 16000019 No Matching Ability Is Found During Implicit Startup

**Error Message**

No matching ability is found.

**Description**

This error code is reported when a matching ability is not found during implicit startup.

**Possible Causes**

1. The parameter settings for implicit startup are incorrect.
2. The specified HAP is not installed.

**Solution**

1. Correct the parameter settings for implicit startup. For details about the matching rules, see [Matching Rules of Explicit Want and Implicit Want](../../application-models/explicit-implicit-want-mappings.md).
2. Install the specified HAP.

<!--Del-->
## 16000020 Context Is Not an Ability-level Context

**Error Message**

The context is not ability context.

**Description**

This error code is reported when the passed Context object is not an ability-level context.

**Possible Causes**

The passed Context object is not UIAbilityContext or ExtensionContext, and does not inherit from UIAbilityContext or ExtensionContext.

**Solution**

Use a UIAbilityContext object or an ExtensionContext object as the input parameter, or use the object that inherits from UIAbilityContext or ExtensionContext as the input parameter.
<!--DelEnd-->

## 16000050 Internal Error

**Error Message**

Internal error.

**Description**

This error code is reported when an internal exception occurs that the developer cannot resolve, such as memory allocation failure, multithreading exceptions, or IPC failure.

**Possible Causes**

This is a generic system error code and can be triggered by various issues depending on the API. Common causes include: null pointer exceptions for internal objects, processing timeouts, IPC failures, failure in obtaining application information, failure in obtaining system services, and reaching the upper limit of ability instances launched.

**Solution**

1. Internal errors are system exceptions that developers cannot handle. You can try the operation again.
2. For failures in launching an ability, check whether the data passed in Want is too large.

## 16000053 Ability Is Not on Top of UI

**Error Message**

The ability is not on the top of the UI.

**Description**

This error code is reported when the ability is not displayed on the top of the UI.

**Possible Causes**

During the installation-free startup process, it is necessary to ensure that the ability is in the foreground, but the ability is not displayed at the top of the UI.

**Solution**

1. Ensure that the ability is started and running in the foreground.
2. Ensure that the ability UI is fully displayed and not obscured or minimized by other application windows.
3. If the split-screen or multi-window mode is enabled on the device, ensure that the ability is the focused window.

## 16000055 Installation-Free Timeout

**Error Message**

Installation-free timed out.

**Description**

This error code is reported when the installation-free task times out.

**Possible Causes**

Installation-free times out.

**Solution**

Try again later.

<!--Del-->
## 16000058 Specified URI Flag Is Invalid

**Error Message**

Invalid URI flag.

**Description**

This error code is reported when the specified URI flag is invalid.

**Possible Causes**

An incorrect parameter is passed in.

**Solution**

Pass in a valid URI flag.

## 16000059 Specified URI Type Is Invalid

**Error Message**

Invalid URI type.

**Description**

This error code is reported when the specified URI type is invalid.

**Possible Causes**

An incorrect parameter is passed in. Currently, URI authorization management supports only URIs of the file type.

**Solution**

Ensure that the input parameter is of the supported URI type.

## 16000060 Sandbox Applications Cannot Grant URI Permission

**Error Message**

A sandbox application cannot grant URI permission.

**Description**

This error code is reported when a sandbox application attempts to grant URI permission.

**Possible Causes**

Sandbox applications are not allowed to grant URI permissions.

**Solution**

Use a non-sandbox application.
<!--DelEnd-->

## 16000061 Unsupported Operation

**Error Message**

Operation not supported.

**Description**

This error code is reported when the operation is not supported.

**Possible Causes**

The operation is not supported.

**Solution**

Perform a supported operation.

## 16000062 Too Many Child Processes

**Error Message**

The number of child processes exceeds the upper limit.

**Description**

This error code is reported when the number of created child processes reaches the upper limit.

**Possible Causes**

The number of created child processes has reached the upper limit.

**Solution**

Limit the number of created child processes. The upper limit is 512.

## 16000063 Invalid Ability During Application Restart

**Error Message**

The target to restart does not belong to the current application or is not a UIAbility.

**Description**

This error code is reported when the specified ability name or type is invalid during application restart.

**Possible Causes**

The specified ability name or type is invalid.

**Solution**

Ensure that the specified ability name belongs to the current application and the ability type is UIAbility.

## 16000064 Frequent Application Restart

**Error Message**

Restart too frequently. Try again at least 3s later.

**Description**

This error code is reported when the API used to restart the application with a specified component is called again within 3 seconds.

**Possible Causes**

The API is frequently called.

**Solution**

Wait for at least 3s and try again.

## 16000065 API Can Be Called Only for a Foreground Ability

**Error Message**

The API can be called only when the ability is running in the foreground.

**Description**

This error code is reported when the API is called while the ability is not running in the foreground.

**Possible Causes**

The ability is not in the foreground when the API is called.

**Solution**

Before calling the API, ensure that the ability is running in the foreground and the UI is visible.

## 16000066 Ability Cannot Be Switched to the Foreground or Background in Wukong Mode

**Error Message**

An ability cannot switch to the foreground or background in Wukong mode.

**Description**

This error code is reported when the API used to switch the ability to the foreground or background is called in Wukong mode.

**Possible Causes**

In Wukong mode, it is not allowed to switch the ability to the foreground or background.

**Solution**

Exit wukong mode, and then call the API to switch the ability to the foreground or background.  

## 16000067 Ability Startup Parameter Verification Failure

**Error Message**

The StartOptions check failed.

**Description**

This error code is reported when verification on **StartOptions** fails.

**Possible Causes**

1. **startAbility()**, with **processMode** set to **NEW_PROCESS_ATTACH_TO_STATUS_BAR_ITEM** or **ATTACH_TO_STATUS_BAR_ITEM**, is called, but the application icon is not displayed in the status bar.
2. **showAbility()** or **hideAbility()** is called, but the caller is not started in **NEW_PROCESS_ATTACH_TO_STATUS_BAR_ITEM** or **ATTACH_TO_STATUS_BAR_ITEM** mode.

**Solution**

Check whether the constraints for **StartOptions** are met.

## 16000068 Ability Is Already Running

**Error Message**

The ability is already running.

**Description**

This error code is reported when the target ability is already running.

**Possible Causes**

**startAbility()** is called, with **processMode** and **startupVisibility** specified. **launchType** of the target ability is singleton or specified, and the target ability is running.

**Solution**

When **launchType** of the target ability is singleton or specified, do not specify **processMode** or **startupVisibility** in **startAbility()**.

## 16000069 ExtensionAbility Fails to Start a Third-Party Application in Strict Mode

**Error Message**

The extension cannot start the third party application.

**Description**

In strict mode, the ExtensionAbility is not allowed to start third-party applications.

**Possible Causes**

The ExtensionAbility is in strict mode, and this type of ExtensionAbility is forbidden to start third-party applications in strict mode.

**Solution**

1. Check the strict mode activation conditions for this [type of ExtensionAbility](../../application-models/extensionability-overview.md).
2. Start the ExtensionAbility in non-strict mode.

## 16000070 ExtensionAbility Fails to Start a ServiceExtensionAbility in Strict Mode

**Error Message**

The extension cannot start the service.

**Description**

In strict mode, the ExtensionAbility is not allowed to start the specified ServiceExtensionAbility.

**Possible Causes**

The ExtensionAbility is in strict mode, and this type of ExtensionAbility is forbidden to start the specified ServiceExtensionAbility in strict mode.

**Solution**

1. Check the strict mode activation conditions for this [type of ExtensionAbility](../../application-models/extensionability-overview.md).
2. Start the ExtensionAbility in non-strict mode.

## 16000071 Application Clone Is Not Supported

**Error Message**

App clone is not supported.

**Description**

This error code is reported when the application does not support clones.

**Possible Causes**

The [getCurrentAppCloneIndex](./js-apis-inner-application-applicationContext.md#applicationcontextgetcurrentappcloneindex12) API is called while the [multiAppMode](../../quick-start/app-configuration-file.md#multiappmode) field in the **app.json5** file is not set to **appClone** (meaning that the application does not support app clone mode).

**Solution**

Configure the **multiAppMode** field in the **app.json5** file by referring to [Creating an Application Multi-Instance](../../quick-start/multiInstance.md). After app clone mode is enabled, call the [getCurrentAppCloneIndex](./js-apis-inner-application-applicationContext.md#applicationcontextgetcurrentappcloneindex12) API.

<!--Del-->
## 16000072 Multi-App Mode Is Not Supported

**Error Message**

App clone or multi-instance is not supported.

**Description**

This error code is reported when the application does not support multi-app mode.

**Possible Causes**

The **getRunningMultiAppInfo()** API is called to query the information about an application that does not support multi-app mode.

**Solution**

When calling **getCurrentAppCloneIndex()**, ensure that the application supports multi-app mode.
<!--DelEnd-->

## 16000073 appCloneIndex Is Invalid

**Error Message**

The app clone index is invalid.

**Description**

This error code is reported when an invalid value of **appCloneIndex** is passed in.

**Possible Causes**

1. **startAbility()** is called, with **appCloneIndex** carried in **ohos.extra.param.key.appCloneIndex** set to an invalid value.
2. **isAppRunning()** is called, with **appCloneIndex** set to an invalid value.

**Solution**

Check whether the constraints of **appCloneIndex** are met.

## 16000074 Caller Corresponding to requestCode Does Not Exist When the Result Is Returned

**Error Message**

The caller does not exist.

**Description**

This error code is reported when the **backToCallerAbilityWithResult** API attempts to return the result to the caller but fails to find the caller based on **requestCode**.

**Possible Causes**

1. **requestCode** is not obtained from the **CALLER_REQUEST_CODE** field in **want**.

2. The caller corresponding to **requestCode** has been destroyed or the result has been returned.

**Solution**

1. Check whether **requestCode** is obtained from **CALLER_REQUEST_CODE** in **want**.

2. Check whether the caller has been destroyed or the result has been returned.

## 16000075 Caller Cannot Be Started When the Result Is Returned

**Error Message**

BackToCaller is not supported.

**Description**

This error code is reported when the **backToCallerAbilityWithResult** API fails to return the result to the caller.

**Possible Causes**

The link feature is not configured for the application or the configuration is not approved by the system.

**Solution**

1. Ensure that the **linkFeature** field is configured in the **module.json5** file of the application.
2. Ensure that the **linkFeature** field value of the application is correct, the functionality it describes matches the actual capability of the application link, and the configuration has been approved by the system.

## 16000076 APP_INSTANCE_KEY Does Not Exist

**Error Message**

The app instance key is invalid.

**Description**

This error code is reported when the specified [APP_INSTANCE_KEY](js-apis-app-ability-wantConstant.md#params) does not exist.

**Possible Causes**

The instance specified by [APP_INSTANCE_KEY](js-apis-app-ability-wantConstant.md#params) does not exist.

**Solution**

Ensure that the value of [APP_INSTANCE_KEY](js-apis-app-ability-wantConstant.md#params) is valid.

## 16000077 Number of Application Instances Reaches the Upper Limit

**Error Message**

The number of app instances reaches the limit.

**Description**

This error code is reported when the number of application instances reaches the upper limit and more application instances try to be created.

**Possible Causes**

Before creating an application instance, the application does not check whether the number of application instances reaches the upper limit.

**Solution**

To create a new instance when the number of application instances has reached the upper limit, prompt the user to close existing instances via a dialog box.

## 16000078 Multi-Instance Mode Is Not Supported

**Error Message**

The multi-instance is not supported.

**Description**

This error code is reported when the application does not support multi-instance mode.

**Possible Causes**

1. Multi-instance mode is not configured for the application.
2. The current device type does not support multi-instance mode.

**Solution**

1. Configure multi-instance mode for the application.
2. Call the API to create multiple instances on a 2-in-1 device.

## 16000079 APP_INSTANCE_KEY Cannot Be Specified

**Error Message**

The APP_INSTANCE_KEY cannot be specified.

**Description**

[APP_INSTANCE_KEY](js-apis-app-ability-wantConstant.md#params) and [CREATE_APP_INSTANCE_KEY](js-apis-app-ability-wantConstant.md#params) cannot be specified at the same time. This error code is reported when both of them are specified.

**Possible Causes**

Too many parameters are passed.

**Solution**

Specify either [APP_INSTANCE_KEY](js-apis-app-ability-wantConstant.md#params) or [CREATE_APP_INSTANCE_KEY](js-apis-app-ability-wantConstant.md#params).

## 16000080 New Instances Cannot Be Created

**Error Message**

Creating a new instance is not supported.

**Description**

Applications can use [CREATE_APP_INSTANCE_KEY](js-apis-app-ability-wantConstant.md#params) to create their own instances, but not for other applications. Otherwise, this error code is reported.

**Possible Causes**

The parameter use scenario is incorrect.

**Solution**

Delete the [CREATE_APP_INSTANCE_KEY](js-apis-app-ability-wantConstant.md#params) parameter.

<!--Del-->
## 16000081 Failed to Obtain the Target Application Information

**Error Message**

Failed to obtain the target application information.

**Description**

In the call of an [API related to URI authorization](js-apis-uripermissionmanager-sys.md), the information about the target application cannot be obtained based on the bundle name and clone index.

**Possible Causes**

1. The target application is not installed.
2. The clone index is out of range.
3. The target application does not have a clone of the specified index.

**Solution**

1. Check whether the application has been installed.
2. Check whether the index is within the allowed range.
3. Check whether the target application has created a clone of the specified index.
<!--DelEnd-->

## 16000083 Specified Ability Cannot Be Started by This Type of ExtensionAbility

**Error Message**

The ExtensionAbility cannot start the ability due to system control.

**Description**

Different types of ExtensionAbility components require different capabilities. The system does not allow this type of ExtensionAbility to start the specified ability.

**Possible Causes**

The current type of ExtensionAbility is under system control and is not allowed to start the specified ability.

**Solution**

Check the usage constraints for this type of ExtensionAbility, and ensure that the API is used as required.

## 16000084 Only One DelegatorAbility Is Allowed to Call the API

**Error Message**

Only DelegatorAbility is allowed to call this API, and only once.

**Description**

The system allows the DelegatorAbility to call this API only once.

**Possible Causes**

1. The caller is not a DelegatorAbility.
2. The caller is a DelegatorAbility, but it calls the API repeatedly.

**Solution**

1. Check whether the caller is a DelegatorAbility.
2. Check whether the API is being called repeatedly.

## 16000085 Error Occurs During the Interaction Between the Ability and Window

**Error Message**

An error occurred during the interaction between the ability and window.

**Description**

An error occurs during the interaction between the ability and the window.

**Possible Causes**

The window service process is abnormal.

**Solution**

This is a system error. Try calling the API again.

## 16000086 Context Is Not a UIAbilityContext

**Error Message**

The context is not UIAbilityContext.

**Description**

This error code is reported when the passed Context object is not a UIAbilityContext.

**Possible Causes**

The passed Context object is not a UIAbilityContext or does not inherit from the UIAbilityContext class.

**Solution**

Ensure that the passed parameter is a UIAbilityContext object or its child class object.

## 16000090 Caller Is Not an Atomic Service

**Error Message**

The caller is not an atomic service.

**Description**

This error code is reported when the caller is not an atomic service.

**Possible Causes**

The API caller is not an atomic service.

**Solution**

Ensure that the caller is an atomic service.

<!--Del-->
## 16000091 Failed to Obtain a File URI by Key

**Error Message**

Failed to get the file URI from the key.

**Description**

This error code is reported when attempting to obtain a file URI based on the key fails.

**Possible Causes**

1. The key is empty.
2. The key does not belong to the current caller.
3. The key is not a data path of a specific service.
4. The data corresponding to the key in the UDMF is not entirely composed of file URIs.

**Solution**

1. Ensure that the key is created by the caller.
2. Ensure that the key is a data path of a specific service. For details, see [UDMF Data Path](../apis-arkdata/js-apis-data-unifiedDataChannel.md#intention).
3. Ensure that the data written in the UDMF when creating the key is entirely composed of file URIs.

## 16000092 No Permission to Authorize URI

**Error Message**

No permission to authorize the URI.

**Description**

This error code is reported when the caller does not have the permission to authorize the URI.

**Possible Causes**

The URIs written when the key is created include URIs that cannot be authorized.

**Solution**

Ensure that all URIs written when the key is created are authorized.

## 16000093 Invalid Caller Token ID

**Error Message**

The caller token ID is invalid.

**Description**

This error code is reported when the token ID of the caller is invalid.

**Possible Causes**

The system does not find the application corresponding to **callerTokenId**.

**Solution**

Check whether the application corresponding to **callerTokenId** is installed.

## 16000094 Invalid Target Token ID

**Error Message**

The target token ID is invalid.

**Description**

This error code is reported when the token ID of the target application is invalid.

**Possible Causes**

1. The system does not find the application corresponding to **targetTokenId**.
2. **targetTokenId** and **callerTokenId** are the same application.

**Solution**

1. Ensure that the application corresponding to **targetTokenId** is installed.
2. Ensure that **callerTokenId** and **targetTokenId** are not the same application.
<!--DelEnd-->

## 16000100 Failed to Call AbilityMonitor APIs to Listen for Ability Lifecycle Changes

**Error Message**

 - Calling AddAbilityMonitor failed.

 - Calling AddAbilityMonitorSync failed.

 - Calling RemoveAbilityMonitor failed.

 - Calling RemoveAbilityMonitorSync failed.

 - Calling WaitAbilityMonitor failed.

 - Calling GetCurrentTopAbility failed.

 - Calling DoAbilityForeground failed.

 - Calling DoAbilityBackground failed.

 - Calling FinishTest failed.

 - Calling AddAbilityStageMonitor failed.

 - Calling AddAbilityStageMonitorSync failed.

 - Calling RemoveAbilityStageMonitor failed.

 - Calling RemoveAbilityStageMonitorSync failed.

 - Calling WaitAbilityStageMonitor failed.

**Description**

This error code is reported when an AbilityMonitor API for monitoring the lifecycle change of a specified ability fails to be executed.

**Possible Causes**

Creating an AbilityDelegatorRegistry instance fails.

**Solution**

Check whether an AbilityDelegatorRegistry instance is created.

## 16000110 Application Is Not in the Kiosk Mode List

**Error Message**

The current application is not in Kiosk app list and cannot enter Kiosk mode.

**Description**

This error code is reported when the current application is not in the kiosk mode list and cannot enter kiosk mode.

**Possible Causes**

The application is not in the kiosk mode list and cannot enter kiosk mode.

**Solution**

Add the application to the kiosk application list on the EDM.

## 16000111 Application Is Already in Kiosk Mode

**Error Message**

The system is already in Kiosk mode and cannot enter Kiosk mode again.

**Description**

This error code is reported when the system is already in kiosk mode.

**Possible Causes**

Only one application can enter Kiosk mode at a time.

**Solution**

Exit the application that is in Kiosk mode.

## 16000112 No Application Is in Kiosk Mode

**Error Message**

The current application is not in Kiosk mode and cannot exit Kiosk mode.

**Description**

This error code is reported when the current application is not in Kiosk mode and cannot exit Kiosk mode.

**Possible Causes**

The application is not in Kiosk mode and cannot exit Kiosk mode.

**Solution**

Check whether any application in the system is in Kiosk mode.

## 16000113 Ability Is Not in the Foreground

**Error Message**

Current ability is not in foreground.

**Description**

When the ability is not in the foreground, attempting to perform operations that require the foreground will return this error code.

**Possible Causes**

The current ability is not in the foreground.

**Solution**

Check whether the ability is in the foreground.

<!--Del-->
## 16000120 Number of Elements in wantList Exceeds 4 or Is Less Than 1

**Error Message**

A maximum of four UIAbility instances can be started simultaneously.The current parameter exceeds the maximum number or is less than 1.

**Description**

The input parameter is incorrect. The **wantList** parameter must contain 1 to 4 Want objects.

**Possible Causes**

The **wantList** parameter contains more than four or less than one element.

**Solution**

Ensure that the **wantList** parameter contains 1 to 4 Want objects.

## 16000121 Target Component Is Not a UIAbility

**Error Message**

The target component type is not a UIAbility.

**Description**

The target component is not a UIAbility.

**Possible Causes**

**startUIAbilities** can start only UIAbility components. This error code is reported when the target component is not a UIAbility.

**Solution**

Check the component type passed in the Want and ensure that the component is a UIAbility.

## 16000122 Target Component Is Intercepted by the System Control Module

**Error Message**

The target component is blocked by the system module and does not support startup.

**Description**

The target component is intercepted by the system control module and cannot be started.

**Possible Causes**

The system control module has blocked the startup of the target application.

**Solution**

If the target UIAbility cannot be started, try to start another UIAbility.

## 16000123 Implicit Startup Is Not Supported

**Error Message**

Implicit startup is not supported.

**Description**

Implicit startup is not supported.

**Possible Causes**

The **wantList** parameter contains an implicit Want.

**Solution**

Check the **wantList** parameter and ensure that no implicit Want exists. If implicit Want exists, change it to explicit Want.

## 16000124 Starting a Distributed UIAbility Is Not Supported

**Error Message**

Starting a remote UIAbility is not supported.

**Description**

This error code is reported when you attempt to start a remote UIAbility.

**Possible Causes**

The **deviceId** field in the Want is not empty and is not the local device ID.

**Solution**

Set the **deviceId** field in the Want to an empty string or the local device ID.

## 16000125 Starting a Plugin Is Not Supported

**Error Message**

Starting a plugin UIAbility is not supported.

**Description**

This error code is reported when you attempt to start a plugin.

**Possible Causes**

The **parameters** field in the Want is set to start the UIAbility of the plugin.

**Solution**

Check the **parameters** field in the Want and do not set **ohos.params.pluginAbility** to **true**.

## 16000126 DLP Files Cannot Be Started

**Error Message**

Starting DLP files is not supported.

**Description**

This error code is reported when you attempt to start a DLP file.

**Possible Causes**

A DLP file is passed in the Want.

**Solution**

Check whether the Want carries a DLP file.
<!--DelEnd-->

## 16000130 UIAbility Does Not Belong to the Caller

**Error Message**

The UIAbility not belong to caller.

**Description**

This error code is reported when target UIAbility does not belong to the caller.

**Possible Causes**

Attempting to launch a UIAbility that belongs to another application.

**Solution**

Verify that the target UIAbility belongs to the caller.

## 16000131 UIAbility Already Started

**Error Message**

The UIAbility is already exist, can not start again.

**Description**

This error code is reported when the UIAbility is already running and cannot be started again.

**Possible Causes**

**startSelfUIAbilityInCurrentProcess** is designed for cold-starting a new UIAbility instance. This error occurs when attempting to launch a UIAbility instance that has already been started.

**Solution**

Check whether the UIAbility has already been launched.

## 16000135 UIAbility Main Window Does Not Exist

**Error Message**

The main window of this ability of this context does not exits.

**Description**

This error code is reported when the main window for this UIAbility does not exist.

**Possible Causes**

The API is called when the window has not yet been created or has already been destroyed.

**Solution**

Do not call this API before the window stage is created or after it is destroyed.

## 16000151 Invalid wantAgent Object

**Error Message**

Invalid wantAgent object.

**Description**

This error code is reported when the wantAgent object passed in the API is invalid.

**Possible Causes**

1. The wantAgent object is invalid.
2. A third-party application attempts to set the ability of another application.
3. An internal communication error occurs.

**Solution**

1. Ensure that the wantAgent object passed in the API exists.
2. Check whether the caller is a third-party application. Third-party applications cannot set the ability components of other applications.

<!--Del-->
## 16000153 wantAgent Object Is Canceled

**Error Message**

The WantAgent has been canceled.

**Description**

This error code is reported when the wantAgent object passed in the API has been canceled.

**Possible Causes**

The wantAgent object passed to the API has been canceled.

**Solution**

Use the wantAgent object that is not canceled.
<!--DelEnd-->

## 16000200 Caller Is Not Allowed to Start a Background Service of the Application

**Error Message**

The caller is not in the appIdentifierAllowList of the target application.

**Description**

This error code is reported when the caller is not in the [appIdentifierAllowList](../../quick-start/module-configuration-file.md#extensionabilities) of the target application.

**Possible Causes**

The **app-identifier** of the caller of [startAppServiceExtensionAbility](js-apis-inner-application-uiAbilityContext.md#startappserviceextensionability20) or [stopAppServiceExtensionAbility](js-apis-inner-application-uiAbilityContext.md#stopappserviceextensionability20) is not in the [appIdentifierAllowList](../../quick-start/module-configuration-file.md#extensionabilities) of the target [AppServiceExtensionAbility](js-apis-app-ability-appServiceExtensionAbility.md).

**Solution**

Configure the **app-identifier** of the API caller in the [appIdentifierAllowList](../../quick-start/module-configuration-file.md#extensionabilities) of the target [AppServiceExtensionAbility](js-apis-app-ability-appServiceExtensionAbility.md).

## 16000201 Target Service Is Not Started

**Error Message**

The target service has not been started yet.

**Description**

This error code is reported when the target service is not started.

**Possible Causes**

When the [connectAppServiceExtensionAbility](js-apis-inner-application-uiAbilityContext.md#connectappserviceextensionability20) API is used, the server is not started, and the current application does not have the permission to start the target service.

**Solution**

1. Wait until the service is started and then reconnect to it.
2. When the current application starts the target service, the **app-identifier** of the API caller must be configured in the [appIdentifierAllowList](../../quick-start/module-configuration-file.md#extensionabilities) of the target [AppServiceExtensionAbility](js-apis-app-ability-appServiceExtensionAbility.md).

## 16200001 Caller Released

**Error Message**

The caller has been released.

**Description**

This error code is reported when the caller has been released.

**Possible Causes**

The caller has been released.

**Solution**

1. Register a valid caller again.
2. Check whether the ability corresponding to the context is still running when **context.startAbility** is called. This error code is thrown when the ability has been destructed.
3. If **startAbility()** and **terminateSelf()** are called consecutively, ensure that a success or failure callback for **startAbility()** is received before calling **terminateSelf()**.

## 16200002 Invalid Callee

**Error Message**

The callee does not exist.

**Description**

This error code is reported when the callee is invalid.

**Possible Causes**

The callee does not exist.

**Solution**

Use a valid callee.

## 16200004 Method Registered

**Error Message**

The method has been registered.

**Description**

This error code is reported when the method has been registered.

**Possible Causes**

The method has been registered by the callee.

**Solution**

Check whether the method has been registered. If the method has been registered, do not register it again.

## 16200005 Method Not Registered

**Error Message**

The method has not been registered.

**Description**

This error code is reported when the method has not been registered.

**Possible Causes**

The method has not been registered by the callee.

**Solution**

Register the method on the callee side and then call it.

<!--Del-->
## 16200006 No Permission to Enable or Disable the Resident Process

**Error Message**

The caller application can only set the resident status of the configured process.

**Description**

This error code is reported when the caller does not have the permission to enable or disable the resident process.

**Possible Causes**

The caller does not have the permission to enable or disable the resident process.

**Solution**

Ensure that the caller has the required permission before calling this API.

## 16300001 Nonexistent Mission

**Error Message**

Mission not found.

**Description**

This error code is reported when the specified mission does not exist.

**Possible Causes**

The mission does not exist.

**Solution**

Check the mission ID.

## 16300002 Nonexistent Mission Listener

**Error Message**

The specified mission listener does not exist.

**Description**

This error code is reported when the specified mission listener does not exist.

**Possible Causes**

The mission listener does not exist.

**Solution**

Check the mission listener ID.
<!--DelEnd-->

## 16300003 Target Application Is Not the Invoker Application

**Error Message**

The target application is not the current application.

**Description**

This error code is reported when the application to start is not the application that calls the API.

**Possible Causes**

The application to start and the invoker application are not the same application.

**Solution**

Ensure that the application to start is the invoker application.

<!--Del-->
## 18500001 Invalid Bundle Name

**Error Message**

The bundle does not exist or no patch has been applied.

**Description**

This error code is reported when the specified bundle name is invalid.

**Possible Causes**

The bundle does not exist or is not installed.

**Solution**

Check whether the bundle has been installed.

## 18500002 Invalid Patch Package

**Error Message**

Invalid patch package.

**Description**

This error code is returned when the specified patch package is invalid.

**Possible Causes**

The patch package does not exist or is inaccessible.

**Solution**

1. Check whether the path of the patch package is valid.
2. Check whether the application has the permission to access the patch package.

## 18500008 Internal Error

**Error Message**

Internal error.

**Description**

This error code is reported when an error occurs during internal processing, such as memory application or multithreading processing.

**Possible Causes**

Common kernel errors such as memory application and multithreading processing errors occur.

**Solution**

Ensure sufficient system memory.

## 18500009 Application Has a Quick Fix Task Being Processed

**Error Message**

The application has an ongoing quick fix task.

**Description**

This error code is reported when the application has a quick fix task that is under processing.

**Possible Causes**

When you try to cancel a quick fix task for an application, the application has a quick repair task that is under processing.

**Solution**

Wait until the quick fix task is complete.
<!--DelEnd-->

## 16300004 Observer Does Not Exist

**Error Message**

The observer does not exist.

**Description**

This error code is reported when the specified observer does not exist.

**Possible Causes**

The observer does not exist or has been unregistered.

**Solution**

Check whether the observer exists.

<!--Del-->
## 16300005 Bundle Information Does Not Exist

**Error Message**

The target bundle does not exist.

**Description**

This error code is reported when the bundle information of the preinstalled application does not exist.

**Possible Causes**

The value of **bundleName**, **userId**, or **appIndex** is incorrect, leading to the query failure.

**Solution**

Pass in correct values for **bundleName**, **userId**, and **appIndex**.

## 16300008 Specified Package Does Not Have a Main UIAbility

**Error Message**

The target bundle has no MainAbility.

**Description**

This error code is reported when the application does not have a main UIAbility.

**Possible Causes**

The ability configured for **mainElement** is not a UIAbility.

**Solution**

Check whether the ability configured for **mainElement** in the **module.json** file is a UIAbility.

## 16300009 Specified Package Does Not Have a Status Bar

**Error Message**

The target bundle has no status-bar ability.

**Description**

This error code is reported when the application does not have a status bar.

**Possible Causes**

The application does not have a status bar.

**Solution**

Check whether the application has a status bar.

## 16300010 Running Application Is Not Attached to a Status Bar

**Error Message**

The target application is not attached to the status bar.

**Description**

This error code is reported when the application is not attached to a status bar after running.

**Possible Causes**

The application has a status bar, but it is not attached to the status bar during running.

**Solution**

Check whether the application is attached to a status bar.
<!--DelEnd-->

## 29600001 Internal Error During Image Editing

**Error Message**

Internal error.

**Description**

This error code is reported when an internal error such as memory allocation or multithreaded processing exception occurs during image saving.

**Possible Causes**

Common kernel errors such as memory application and multithreading processing errors occur. The possible causes are as follows: The internal object is empty, and the processing times out.

**Solution**

1. Ensure sufficient system memory. Ensure that the system version used by the device is normal.
2. Restart the device.

## 29600002 Internal Error During Image Editing

**Error Message**

Image input error.

**Description**

This error code is reported when the image URI does not exist or the image cannot be parsed.

**Possible Causes**

The URI does not exist or the URI does not point to an image file.

**Solution**

Check whether the file exists and whether the file type is image.

## 29600003 Image Too Large

**Error Message**

Image too big.

**Description**

The image is too large.

**Possible Causes**

This error code is reported when the size of the image exceeds 50 MB.

**Solution**

1. Limit the size of the edited image to less than 50 MB.
2. Verify the image size in advance.

<!--Del-->
## 16300007 Download and Installation Task Information of the Atomic Service Does Not Exist

**Error Message**

The target free-installation task does not exist.

**Description**

This error code is reported when the download and installation task of the specified atomic service does not exist while the atomic service window is opened.

**Possible Causes**

The value of **bundleName**, **moduleName**, **abilityName**, or **startTime** is incorrect, leading to the query failure.

**Solution**

Pass in correct values for **bundleName**, **moduleName**, **abilityName**, and **startTime**.
<!--DelEnd-->

## 28800001 Startup Task or Dependency Not Found

**Error Message**

Startup task or its dependency not found.

**Description**

This error code is reported if the startup task or its dependency is not found during task startup.

**Possible Causes**

The startup task or dependency is not correctly configured.

**Solution**

Check whether the AppStartup configuration file is correctly compiled, and ensure that all configured startup tasks are implemented.

## 28800002 Circular Dependencies Between Startup Tasks

**Error Message**

The startup tasks have circular dependencies.

**Description**

This error code is reported if circular dependencies are detected between startup tasks during startup task loading.

**Possible Causes**

There are circular dependencies between startup tasks.

**Solution**

Check the AppStartup configuration file, and ensure that no circular dependency exists between startup tasks.

## 28800003 Error Occurs During Task Startup

**Error Message**

An error occurred while running the startup tasks.

**Description**

This error code is reported when an error occurs during task startup.

**Possible Causes**

The code logic for starting the task is incorrect, or no exception handling is available.

**Solution**

Check whether the startup task has logic errors, and ensure that each startup task contains the exception handling logic.

## 28800004 Executing the Startup Task Times Out

**Error Message**

Running startup tasks timeout.

**Description**

This error code is reported if the execution time of a task exceeds the timeout interval (10000 ms by default).

**Possible Causes**

The startup task contains a large number of time-consuming operations, or the configured timeout interval is too short.

**Solution**

Adjust the timeout interval as required. For details about how to set the timeout interval, see [Setting Startup Parameters](../../application-models/app-startup.md#setting-startup-parameters).

<!--Del-->
## 16400001 Target Application Type Is Not a System HSP

**Error Message**

The input bundleName is not a system HSP.

**Description**

When the [createSystemHspModuleResourceManager](js-apis-inner-application-context-sys.md#createsystemhspmoduleresourcemanager12) API is used to create a [ResourceManager](../apis-localization-kit/js-apis-resource-manager.md#resourcemanager), if the passed **bundleName** does not belong to a module of a [system HSP](../../quick-start/application-package-glossary.md#system-level-hsp), this error code is reported.

**Possible Causes**

The **bundleName** parameter passed to **createSystemHspModuleResourceManager** is not the bundle name of the HSP preconfigured in the system by the OEM.

**Solution**

Check whether the value of **bundleName** is correct.

## 16000202 Keep-Alive Can Be Set Only for an ExtensionAbility of the appService Type

**Error Message**

Invalid main element type.

**Description**

This error code is reported when the object to be kept alive is not an ExtensionAbility of the appService type.

**Possible Causes**

The **mainElement** field in the **module.json5** file of the entry HAP is not an ExtensionAbility of the appService type.

**Solution**

Change the **mainElement** field of the entry HAP in the **module.json5** file to an ExtensionAbility of the appService type.

## 16000203 Cannot Change the Keep-alive Status of an AppServiceExtensionAbility

**Error Message**

Cannot change the keep-alive status.

**Description**

This error code is reported when the keep-alive status of an AppServiceExtensionAbility cannot be changed.

**Possible Causes**

The keep-alive policy of the AppServiceExtensionAbility is set by the MDM to be uncancelable by users or is set to keep-alive by other users.

**Solution**

Cancel the keep-alive setting on the MDM server, or set the keep-alive policy to allow users to cancel the keep-alive. Cancel the keep-alive of the AppServiceExtensionAbility for the user who has the keep-alive permission.

## 16000204 Application Is Not Installed for the User with userId of 1

**Error Message**

The target bundle is not in u1.

**Description**

This error code is reported when the specified application is not installed under the user with **userId** of 1.

**Possible Causes**

The specified application is not installed under the user with **userId** of 1.

**Solution**

Install the specified application under the user with **userId** of 1.
<!--DelEnd-->

## 16000115 Current Process Cannot Be Set as Candidate Master Process

**Error Message**

The current process cannot be set as a candidate master process.

**Description**

The current process does not meet the requirements to be configured as a candidate master process.

**Possible Causes**

The process fails to satisfy at least one of the following conditions:

1. It is running a component with **isolationProcess** set to **true**.
2. It has previously served as the master process.

**Solution**

No workaround is available. A process can only be set as a candidate master process if it is currently running a component with **isolationProcess** set to **true**, or if it has previously functioned as the master process.

## 16000116 Process Is Already a Master Process

**Error Message**

The current process is already a master process and does not support cancellation.

**Description**

This error code is reported when you attempt to cancel the current process, which is already the master process, as a candidate master process.

**Possible Causes**

The current process is already the main process.

**Solution**

No action can be taken. Cancellation is not supported since the current process is already the master process.

## 16000117 Process Is Not a Candidate Master Process

**Error Message**

The current process is not a candidate master process and does not support cancellation.

**Description**

This error code is reported when you attempt to cancel the current process, which is not a candidate master process , as a candidate master process.

**Possible Causes**

The current process is not a candidate master process and cannot be canceled.

**Solution**

No action can be taken. Cancellation is not supported since the current process is not a candidate master process.

## 16000118 Process Is Not the Master Process

**Error Message**

Not a master process.

**Description**

This error code is reported when you attempt to relinquish the master-process role of the current process, which is not the master process.

**Possible Causes**

The current process is not the master process and cannot relinquish its master-process role.

**Solution**

No action can be taken. The current process is not the master process and cannot relinquish its master-process role.

## 16000119 Pending Request Exists

**Error Message**

Cannot exit because there is an unfinished request.

**Description**

The attempt to relinquish the current process's master process status has failed due to pending requests.

**Possible Causes**

The current process contains unfinished requests:

1. There are pending [onNewProcessRequest](js-apis-app-ability-abilityStage.md#onnewprocessrequest11) calls in the process
2. When a UIAbility with [specified](../../application-models/uiability-launch-type.md#specified) launch mode runs in an isolated process, there are pending [onAcceptWant](js-apis-app-ability-abilityStage.md#onacceptwant) requests

**Solution**

Wait for all current requests in the process to complete before attempting to relinquish master process status.

## 16000205 API Not Called in Main Thread

**Error Message**

The API is not called in the main thread.

**Description**

This error code is reported when the API is not called in the main thread.

**Possible Causes**

The current API is called in a Worker or TaskPool thread, which is not supported.

**Solution**

Move the API call logic to the main thread.

## 10110000 Incorrect Declaration for Decorator Parameters

**Error Message**

Decorator parameters must be compile-time constants.

**Description**

This error code is reported when variables are used as decorator parameters in the code. Compile-time constants (such as string literals) are required.

**Possible Causes**

Decorator parameters use variables.

**Solution**

Change the decorator parameters from variables to fixed values.

## 10110001 Incorrect Decorator Usage Location

**Error Message**

The intent decorator can only be used in .ets files. 

**Description**

This error code is reported when the intent decorator is used in a non-.ets file.

**Possible Causes**

The intent decorator is used in a non-.ets file.

**Solution**

Use the intent decorator in an .ets file.

## 10110002 Incorrect Decorator Call Form

**Error Message**

Decorators must be called as functions. 

**Description**

This error code is reported when the decorator is not invoked in function call form.

**Possible Causes**

The decorator is not invoked in function call form.

**Solution**

Add parentheses to ensure that the decorator is invoked as a function.

## 10110003 Decorator Missing Required Parameters

**Error Message**

Required parameters are missing for the decorator.

**Description**

This error code is reported when the decorator is missing required parameters.

**Possible Causes**

The decorator is missing required parameters.

**Solution**

Add the required parameters based on the error message.

## 10110004 Parameter Type Does Not Match Decorator Requirements

**Error Message**

The parameter type does not match the decorator's requirement.

**Description**

This error code is reported when the parameter type does not match the decorator's requirements.

**Possible Causes**

The parameter type does not match the decorator's requirements.

**Solution**

Adjust the parameter type based on the error message.

## 10110005 Unsupported Parameters in Decorator

**Error Message**

Unsupported parameters found in the decorator.

**Description**

This error code is reported when unsupported parameters are found in the decorator.

**Possible Causes**

Unsupported parameters are written in the decorator.

**Solution**

Remove unsupported parameters based on the error message. (Only the string, number, boolean, object, and array types are supported.)

## 10110006 Circular Dependency Detected in Decorator Parameters

**Error Message**

Circular dependencies detected in decorator parameters.

**Description**

This error code is reported when circular dependencies are detected in decorator parameters.

**Possible Causes**

Circular dependencies are written in the decorator parameters.

**Solution**

Refactor the data structure by extracting common variables or using ID references to avoid nesting.

## 10110007 Root Type of JSON Schema for Parameters is Not Object

**Error Message**

The root type of the JSON Schema for Parameters must be object. 

**Description**

This error code is reported when the root type of the JSON schema for **Parameters** is not object.

**Possible Causes**

The root type of the JSON schema for **Parameters** is not object.

**Solution**

Ensure that the top-level definition of the JSON schema for parameters is {"type": "object"}.

## 10110008 Class Property Missing Required Field

**Error Message**

A required field in the class property is missing.

**Description**

This error code is reported when a required field in the class property is missing.

**Possible Causes**

A required field in the class property is missing.

**Solution**

Add the required field as specified by the JSON Schema.

## 10110009 Class Property Field Type Does Not Match JSON Schema

**Error Message**

The field type of the class property does not match the JSON Schema.

**Description**

This error code is reported when the field type of the class property does not match the JSON schema.

**Possible Causes**

The field type of the class property does not match the JSON schema.

**Solution**

Correct the type to match the requirement.

## 10110010 Class Property Parameter Violates oneOf/anyOf Validation Rules

**Error Message**

The class property parameter violates the oneOf/anyOf validation rules in the JSON Schema.

**Description**

This error code is reported when the class property parameter violates the oneOf/anyOf validation rules in the JSON schema.

**Possible Causes**

The class property parameter violates the oneOf/anyOf validation rules in the JSON Schema.

**Solution**

Modify the parameter to meet the validation rules.

## 10110011 Class Property Includes Parameters Not Defined in JSON Schema

**Error Message**

The class property includes parameters not defined in the JSON Schema.

**Description**

This error code is reported when the class property includes parameters not defined in the JSON schema.

**Possible Causes**

The class property includes parameters not defined in the JSON schema.

**Solution**

Remove any extra parameters.

## 10110012 Duplicate intentName Definitions Found

**Error Message**

Duplicate intentName definitions found.

**Description**

This error code is reported when duplicate intentName definitions are found.

**Possible Causes**

The same intentName is declared in the module.

**Solution**

Find the duplicate intentName in the module and rename it.

## 10110013 Incorrect Location for Methods Decorated with @InsightIntentFunctionMethod

**Error Message**

Methods decorated with @InsightIntentFunctionMethod must be in a class decorated with @InsightIntentFunction.

**Description**

This error code is reported when the method decorated with @InsightIntentFunctionMethod is not in the class decorated with @InsightIntentFunction.

**Possible Causes**

The method decorated with @InsightIntentFunctionMethod is not in the class decorated with @InsightIntentFunction.

**Solution**

Move the method to the class decorated with @InsightIntentFunction, or add the @InsightIntentFunction decorator to the class.

## 10110014 Class Decorated with @InsightIntentFunction Is Not Exported

**Error Message**

The class decorated with @InsightIntentFunction must be exported.

**Description**

This error code is reported when the class decorated with @InsightIntentFunction is not exported using **export**.

**Possible Causes**

The class decorated with @InsightIntentFunction is not exported using **export**.

**Solution**

Add an **export** statement to the class.

## 10110015 Incorrect Method Decorated with @InsightIntentFunctionMethod

**Error Message**

Methods decorated with @InsightIntentFunctionMethod must be static. 

**Description**

This error code is reported when the method decorated with @InsightIntentFunctionMethod is not a static method.

**Possible Causes**

The method decorated with @InsightIntentFunctionMethod is not modified with static.

**Solution**

Modify the method decorated with @InsightIntentFunctionMethod with **static**.

## 10110016 Incorrect Location for @InsightIntentPage

**Error Message**

@InsightIntentPage must be applied to a struct page.

**Description**

This error code is reported when the @InsightIntentPage decorator is not applied to a struct page.

**Possible Causes**

The @InsightIntentPage decorator is applied to a regular class.

**Solution**

Move the @InsightIntentPage decorator to a struct page.

## 10110017 @InsightIntentPage pagePath Does Not Match Actual Page Path

**Error Message**

pagePath in @InsightIntentPage does not match the actual page path. 

**Description**

This error code is reported when **pagePath** in @InsightIntentPage does not match the actual page path.

**Possible Causes**

The value of **pagePath** in @InsightIntentPage is incorrect.

**Solution**

Ensure that the file paths in the directory are consistent.

## 10110018 Incorrect Inheritance for Class Decorated with @InsightIntentEntry

**Error Message**

Classes decorated with @InsightIntentEntry must inherit from InsightIntentEntryExecutor. 

**Description**

This error code is reported when the class decorated with @InsightIntentEntry does not inherit from the base class InsightIntentEntryExecutor.

**Possible Causes**

The class decorated with @InsightIntentEntry does not inherit from the base class InsightIntentEntryExecutor.

**Solution**

Add base class the InsightIntentEntryExecutor to the class.

## 10110019 Class Decorated with @InsightIntentEntry Not Exported as Default

**Error Message**

The class decorated with @InsightIntentEntry must be exported as default. 

**Description**

This error code is reported when the class decorated with @InsightIntentEntry is not exported using **export default**.

**Possible Causes**

The class decorated with @InsightIntentEntry is not exported using **export default**.

**Solution**

Add an **export default** statement to the class.

## 10110020 Multiple @InsightIntentEntity Decorators Applied to the Same Class

**Error Message**

Multiple @InsightIntentEntity decorators applied to the same class. 

**Description**

This error code is reported when the same class is decorated with multiple @InsightIntentEntity decorators.

**Possible Causes**

Multiple @InsightIntentEntity decorators are applied to the same class.

**Solution**

Remove the extra @InsightIntentEntity decorators.

## 10110021 Class Decorated with @InsightIntentEntity Does Not Implement InsightIntent.IntentEntity

**Error Message**

Classes decorated with @InsightIntentEntity must implement InsightIntent.IntentEntity.

**Description**

This error code is reported when the class decorated with @InsightIntentEntity does not implement **InsightIntent.IntentEntity**.

**Possible Causes**

The class decorated with @InsightIntentEntity does not implement **InsightIntent.IntentEntity**.

**Solution**

Ensure that the class implements **InsightIntent.IntentEntity** or inherits from another intent entity.

## 10110022 Incorrect Location for @InsightIntentForm

**Error Message**

@InsightIntentForm must be applied to formExtensionAbility. 

**Description**

This error code is reported when the @InsightIntentForm decorator is not applied to formExtensionAbility.

**Possible Causes**

The @InsightIntentForm decorator is not applied to formExtensionAbility.

**Solution**

Move the @InsightIntentForm decorator to the formExtensionAbility class.

## 10110023 @InsightIntentForm Decorator formName Parameter Mismatch

**Error Message**

formName in @InsightIntentForm must match the widget name registered in formExtensionAbility.

**Description**

This error code is reported when the **formName** parameter in @InsightIntentForm does not match the widget name registered in formExtensionAbility.

**Possible Causes**

The formName parameter in @InsightIntentForm is declared incorrectly.

**Solution**

Update **formName** to match the registered widget name.

## 10110024 module.json5 File Missing

**Error Message**

The module.json5 file is missing. 

**Description**

This error code is reported when the **module.json5** file is not found in the project.

**Possible Causes**

The **module.json5** file has been deleted or moved.

**Solution**

Check the file path (usually in **entry/src/main/config.json** or **module.json5**) and confirm whether the file has been accidentally deleted or moved.

## 10110025 Failed to Write to Intent Configuration File

**Error Message**

Failed to write to the intent configuration file.

**Description**

This error code is reported when the intent configuration file cannot be written.

**Possible Causes**

The permission is insufficient or the disk space is full.

**Solution**

Check file permissions, free disk space, or restart DevEco Studio.

## 10110027 Failed to Generate OHMUrl

**Error Message**

Generating standard OHMUrl failed with useNormalizedOHMUrl configuration not set to true.

**Description**

This error code is reported when the standard OHM URL fails to be generated because **useNormalizedOHMUrl** is not set to **true**.

**Possible Causes**

**useNormalizedOHMUrl** is not set or is set to **false**.

**Solution**

Set **useNormalizedOHMUrl** to **true** in the application-level file **build-profile.json5**.
