# Application Configuration Files
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @memghaiyang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=850c7d4f71d6bc50d82f299a21bb9cea3a266f3d translatedAt=2026-10-30T06:21:33.935Z pushedAt=2026-10-30T06:21:33.935Z nl=1 -->

Each application project must have configuration files in its code directory. These configuration files provide basic application information for build tools, operating systems, and application markets.


In the code of an application project developed based on the [stage model](../application-models/ability-terminology.md#stage-model), there is an app.json5 configuration file and one or more module.json5 configuration files.

>
> **NOTE**
>
> After the compilation, the contents of **app.json5** and **module.json5** in the build product of a single module will merge into a **module.json** file. For details, see [Package Structure in the Build Phase](application-package-structure-stage.md#package-structure-in-the-build-phase).
>

The [app.json5](app-configuration-file.md) file contains the following information:


- Application-wide configuration, including the bundle name, vendor, and version number

- Device-specific configuration


The [module.json5](module-configuration-file.md) file contains the following information:


- Basic [module](./application-package-overview.md#module-types) configuration, such as the name, type, description, and supported device types of the module

- Application component information, including the descriptions of the [UIAbility](module-configuration-file.md#abilities) and [ExtensionAbility](module-configuration-file.md#extensionabilities) components

- Information about the permissions required during application running
