# Consistency Verification for Application Installation and Update
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @memghaiyang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=5fd85f6e71e796e351ea0e34fccd8d3898d18093 translatedAt=2026-09-01T02:49:24.351Z pushedAt=2026-09-02T07:19:28.912Z -->

As applications become more and more complex, they are split into multiple modules for development and maintenance. Different teams are responsible for one or more modules. During application installation and update, consistency verification is performed on different fields to ensure application security and validity. This topic describes the consistency verification rules for signing certificates and configuration files during multi-module installation or update.

>
> **NOTE**
>
> If the values of the **versionCode** field in the [app.json5 configuration file](./app-configuration-file.md) are the same, the installed or updated packages are of the same version.
>
> During application packaging, validity verification is performed. For details, see [Packing Tool](../../application-dev/tools/packing-tool.md).

## Consistency Verification for Signing Certificate

|Field|Description|Consistency Verification for Installations|Consistency Verification for Updates|
|--|--|--|--|
|appId|Application ID, which is a unique identifier of the application. For details, see [What is appId](common-problem-of-application.md#what-is-appid).|Yes|Either **appId** or **appIdentifier** is the same.|
|appIdentifier|Unique ID of the application. For details, see [What Is appIdentifier](common-problem-of-application.md#what-is-appidentifier).|Yes|Either **appId** or **appIdentifier** is the same.|
|appDistributionType|<!--RP1-->Application distribution type specified in **app-distribution-type** of the application [profile](../security/app-provision-structure.md).<!--RP1End-->|Yes|No consistency verification is performed when an application is updated to a later version.|
|appProvisionType|Profile type. <!--RP3-->The value comes from **type** defined in the application [profile](../security/app-provision-structure.md). Profiles are classified into two types: debug profiles are used for local debugging and release profiles are used for application release.<!--RP3End-->|Yes|No consistency verification is performed when an application is updated to a later version.|
|apl|Application [APLs](../security/AccessToken/app-permission-mgmt-overview.md#basic-concepts-in-the-permission-mechanism), which are classified into three levels: normal, system_basic, and system_core.|Yes|No consistency verification is performed when an application is updated to a later version.|


## Consistency Verification for Configuration File

|Field Name|Description|Installation Consistency Verification Rule|Update Consistency Verification Rule|
|--|--|--|--|
|bundleName|Identifies the application name. This field comes from the bundleName field in the [app.json5 configuration file](./app-configuration-file.md).|Yes|Yes|
|versionCode|Identifies the application version number. This field comes from the versionCode field in the [app.json5 configuration file](./app-configuration-file.md).|Yes|Yes|
|apiReleaseType|Identifies the type of the API target version required for the application to run. When the application is not installed on the device and contains multiple module packages, consistency is not verified when the modules are installed one by one. This field comes from the apiReleaseType field in the [app.json5 configuration file](./app-configuration-file.md).|No|Yes|
|<!--DelRow--> singleton|Identifies whether the application is installed under user 0.|No|Yes|
|<!--DelRow--> appType|Identifies whether the application is a third-party application or a system application.|Yes|Yes|
|<!--DelRow--> isStage|Identifies whether the application uses the Stage model.|Yes. The FA model and the Stage model cannot be changed within the same version.|No|
|targetBundleName|Identifies the target application specified by the current package. An application configured with this field is an application with the overlay feature. This field comes from the targetBundleName field in the [app.json5 configuration file](./app-configuration-file.md).|Yes|Yes|
|targetPriority|Identifies the priority of the current application. This field comes from the targetPriority field in the [app.json5 configuration file](./app-configuration-file.md).|Yes|Yes|
|bundleType|Identifies the type of the application. This field comes from the bundleType field in the [app.json5 configuration file](./app-configuration-file.md).|Yes|Yes|
|installationFree|Identifies whether installation-free is supported. This field comes from the installationFree field in the [module.json5 configuration file](./module-configuration-file.md).|Yes|Yes|
|debug|Identifies whether the application is debuggable. This field comes from the debug field in the [app.json5 configuration file](./app-configuration-file.md).|Yes|No|
|moduleType|Identifies the type of the module. This field comes from the type field in the [module.json5 configuration file](./module-configuration-file.md).|Yes. The moduleName of the entry type cannot be modified within the same version.|Yes|

