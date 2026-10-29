# Differences in Configuration Files

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @wkljy-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=e6693c7e3467fc83da37592065a3dc8118ac09a4 translatedAt=2026-10-13T07:14:51.660Z pushedAt=2026-10-13T12:43:19.688Z -->

[FA model](ability-terminology.md#fa-model) applications describe basic application information in the [config.json file](../quick-start/application-configuration-file-overview-fa.md). Multiple Modules can be created in one application project, and each Module has its own config.json file. The config.json file consists of three parts: app, deviceConfig, and module. The app tag is used to configure application-level attributes. If an application has multiple Modules, the developer must ensure that the app tag configuration in each config.json file is consistent.


[Stage model](ability-terminology.md#stage-model) applications describe basic application information in the [app.json5 configuration file](../quick-start/app-configuration-file.md) and the [module.json5 configuration file](../quick-start/module-configuration-file.md). Similar to FA model applications, multiple Modules can also be created in one Stage model application project. However, only one app.json5 file exists in an application project, which is used to configure application-level attributes and takes effect for each Module. Each Module has its own module.json5 configuration file, which is used to configure Module-level attributes and takes effect only for the current Module.

  **Figure 1** Differences in configuration files  
![comparison-of-configuration-file](figures/comparison-of-configuration-file.png)
