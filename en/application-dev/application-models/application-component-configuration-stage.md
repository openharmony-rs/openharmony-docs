# Application- or Component-Level Configuration
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @memghaiyang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=0ea90699c22c82153d76e42b42b6354680202a52 translatedAt=2026-10-13T07:12:59.376Z pushedAt=2026-10-15T13:16:22.273Z -->

During application development, you must configure tags to identify an application, such as the bundle name and application icon. This topic describes some critical tags.

## Configuring the Bundle Name

The bundle name is specified by the **bundleName** field in the [app.json5 file](../quick-start/app-configuration-file.md) in the **AppScope** directory of the project. This field identifies an application and must be globally unique. You are advised to use the reverse domain name notation, for example, *com.example.demo*, where the first part is the domain suffix **com**, the second part is the vendor/individual name, and the third part is the application name, which can be of multiple levels.

## Configuring the Application Icon and Label

Application icons and labels are usually configured together. They correspond to the **icon** and **label** fields in the [app.json5 file](../quick-start/app-configuration-file.md) and [module.json5 file](../quick-start/module-configuration-file.md). Starting from DevEco Studio 5.0.3.800 and later, the **icon** and **label** fields in the **module.json5** file are no longer mandatory. However, they are mandatory in the **app.json5** file. Therefore, they can be omitted in the **module.json5** file. There is a priority and effectiveness strategy for the **icon** and **label** fields in both the **app.json5** and **module.json5** files. For details, please refer to [Configuration Priority and Build Policy](../quick-start/layered-image.md#configuration-priority-and-build-policy).

## Configuring Application Version Declaration

To declare the application version, configure the versionCode and versionName fields in the [app.json5 configuration file](../quick-start/app-configuration-file.md) under the AppScope directory of the project. versionCode identifies the version number of the application. The value of this tag ranges from [0, 2147483647] and must be an integer. This number is used only to determine whether one version is newer than another; a larger value indicates a newer version. The versionName tag provides a text description of the version number.

## Configuring Device Types Supported by the Module

To configure the device types supported by the module, set the [deviceTypes](../quick-start/module-configuration-file.md#devicetypes) field in the [module.json5 file](../quick-start/module-configuration-file.md). If a certain device type is added to **deviceTypes**, the module can run on that device.

## Configuring the Module Permission

The [requestPermissions](../security/AccessToken/declare-permissions.md) field in the [module.json5 file](../quick-start/module-configuration-file.md) is used to configure the permission information required by the module to access the protected part of the system or other applications. This field declares the name of the permission to request, the reason for requesting the permission, and the scenario where the permission is used.

## Configuring the Launch Mode

Since API version 20, applications can configure the startMode field in app.json5 to set different launch modes. For usage constraints and supported values, see the description of the startMode field in the app.json5 [configuration file tags](../quick-start/app-configuration-file.md#tags-in-the-configuration-file).
