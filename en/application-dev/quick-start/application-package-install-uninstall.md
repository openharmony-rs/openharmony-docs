# Application Installation, Uninstall, and Update
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @memghaiyang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=850c7d4f71d6bc50d82f299a21bb9cea3a266f3d translatedAt=2026-10-30T06:21:33.935Z pushedAt=2026-10-30T06:21:33.935Z nl=1 -->

This topic describes application installation, uninstallation, and two update modes.

## Installing or Uninstalling an Application
You can install and uninstall applications using debug commands, for example, the [install](../tools/bm-tool.md#install) and [uninstall](../tools/bm-tool.md#uninstall) commands in the bm tool. For details, see the [compilation, release, and deployment process](./application-package-structure-stage.md#package-structure-in-the-release-phase) flowchart.

**Figure 1** Process of installing and uninstalling an application (applicable to developers)

![hap-install-uninstall](figures/hap-install-uninstall-developer.png)


After an application is released to AppGallery, users can install the application on their devices through the AppGallery.

**Figure 2** Process of installing and uninstalling an application (applicable to consumers)

![hap-install-uninstall](figures/hap-install-uninstall-user.png)

## Updating an Application


To update an application, first update the **versionCode** field in the [app.json5 configuration file](./app-configuration-file.md), package the application using DevEco Studio, and release it on AppGallery using the same process as the initial release. After a new version is released, users can update the application in either of the following ways:

- On AppGallery: AppGallery notifies the user of an available update, and the user can install the update by following the on-screen instructions.
- In the application: <!--RP1-->After the application starts or when the user checks for a new version in the application, an update dialog box is displayed. The user can follow the prompts to update the application.<!--RP1End-->
