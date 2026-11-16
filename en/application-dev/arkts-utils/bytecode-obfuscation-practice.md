---
kits: ["ArkTS Kit"]
description: "Provides bytecode obfuscation options and trustlist configuration recommendations for HAP, HAR, and HSP package types based on their purposes and build process differences, helping developers correctly enable obfuscation in multi-package projects and ensure normal functionality."
keywords: [obfuscation, bytecode obfuscation, obfuscation recommendations, HAP, HAR, HSP, package type, trustlist, toplevel obfuscation]
doctype: guide
status: active
---

# Package-specific Bytecode Obfuscation Recommendations
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @oatuwwutao-->
<!--Designer: @oatuwwutao-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=17ae88719a2d37a0c07e3b6e33ddb120ebd3dbc5 translatedAt=2026-11-06T10:27:16.989Z pushedAt=2026-11-11T09:26:49.587Z nl=1 -->

Different package types serve various purposes and have distinct build processes. This requires you to consider different aspects when applying obfuscation. This topic provides tailored recommendations for three types of packages: [HAP](../quick-start/hap-package.md), [HAR](../quick-start/har-package.md), and [HSP](../quick-start/in-app-hsp.md), aiming to help you effectively implement obfuscation.

To better understand the obfuscation behavior across different package types, you should familiarize yourself with the principles of obfuscation and the process of enabling it. You are also recommended to read [Application Package Structure in Stage Model](../quick-start/application-package-structure-stage.md) to grasp the differences between package types.

## Recommended Obfuscation Options

In addition to the default obfuscation feature, you are encouraged to configure the following basic obfuscation options in the obfuscation configuration file:
    1. Top-level scope name obfuscation (**-enable-toplevel-obfuscation**)
    2. Property name obfuscation (**-enable-property-obfuscation**)
    3. Imported/Exported name obfuscation (**-enable-export-obfuscation**)
    4. File name obfuscation (**-enable-filename-obfuscation**)

After the option configuration, you must configure the corresponding trustlists to ensure the application functions correctly.

* For new applications, you are advised to configure these options from the start and gradually add trustlist configurations as needed during development.
* For existing applications, configure these options one by one in the suggested order. Compare the obfuscation products to understand the impact of each option, and refer to [Obfuscation Configuration Guidelines](bytecode-obfuscation-guide.md#obfuscation-configuration-guidelines) for troubleshooting.

Once the application functions correctly, you can enable additional features like log removal (**-remove-log**) to prepare the release package.

## HAP Package Obfuscation Recommendations

1. Enable the obfuscation rules. Start with the [recommended options](#recommended-obfuscation-options) and add other options as needed.
2. Familiarize yourself with the [obfuscation rule merging strategies](bytecode-obfuscation.md#obfuscation-rule-merging-strategies) to understand how these rules affect the current module during compilation.
3. Understand which code from dependent packages will be compiled and obfuscated together with the current module. This will affect the newly generated obfuscated names and some globally effective trustlists (such as property names), and consequently affect the final obfuscation effect of the current module. Specifically:
    1. When your HAP depends on a local HAR package, its code is obfuscated together with your HAP. The original and obfuscated names in this code will appear in the `obfuscation/nameCache.json` file.
    2. When your HAP depends on a released source code HAR package, its code in the project-level **oh_modules** directory is obfuscated together with your HAP. The original and obfuscated names in this code will appear in the `obfuscation/nameCache.json` file.
    3. When your HAP depends on a released bytecode HAR package or HSP package, only the binary bytecode and declaration files are used for compilation. Since ArkGuard supports only bytecode obfuscation, these files are not obfuscated. (This also maintains the consistency between the interfaces in the declaration file and those in the binary file.) However, if third-party libraries lack proper interface declarations or trustlist configurations in **consumer-rules**, their interfaces may be accidentally obfuscated. You should manually configure trustlists to ensure runtime correctness.

4. To ensure the correctness of the interaction with third-party libraries in the release state, ArkGuard automatically collects exported names and related properties from dependent modules in **oh_modules** and adds them to a trustlist. Since you can reference files from any path within the dependent modules, this collection includes exported names from both entry files (such as **Index.ets**) and all files of the third-party libraries in **oh_modules**.
5. For local source code HAR packages and local HSP packages, ArkGuard does not automatically collect exported names in all files and add them to a trustlist.

    The table below summarizes the compilation and obfuscation scenarios for common dependent packages.

    | Dependent Module| Files Involved in Compilation| Obfuscated with the Current Module| Passes Retention Configuration to the Current Module| Collects Exported Names into a Trustlist|
    | --- | --- | --- | --- | --- |
    | [Local source code HAR package](#local-source-code-har-package)| Source code directory of the module in the local environment| Yes| Yes| No|
    | [Released source code HAR package](#released-source-code-har-package)| Module directory under project-level oh_modules| Yes| Yes| Yes|
    | [Released bytecode HAR package](#released-bytecode-har-package)| Binary bytecode and declaration files| No| Yes| Yes|
    | [Local source code HSP package](#local-source-code-hsp-package)| NA | No| Yes| No|
    | [Integrated HSP package](#integrated-hsp-package)| Binary bytecode and declaration files| No| Yes| Yes|

6. Identify the [scenarios that require trustlist configurations](bytecode-obfuscation.md#retention-options), and configure a trustlist in **obfuscation-rules.txt**.
7. Build and verify the HAP package. If issues arise, review the trustlist configurations.
8. Once the HAP functions correctly, you can release the package.

## HAR Package Obfuscation Recommendations

### General Recommendations

1. Familiarize yourself with the [three types of obfuscation configuration files](bytecode-obfuscation-guide.md#obfuscation-configuration-files) and the [obfuscation rule merging strategies](bytecode-obfuscation.md#obfuscation-rule-merging-strategies). Understand the precautions provided in [HAP Package Obfuscation Recommendations](#hap-package-obfuscation-recommendations) to ensure that your HAR functions correctly when it is used by HAP packages.

2. Because a HAR package affects the obfuscation process of the main module that uses it, **regardless of whether the HAR package itself has obfuscation enabled, you should configure [consumer-rules.txt](bytecode-obfuscation-guide.md#obfuscation-configuration-files) to ensure that the internal functionality of the HAR package remains normal when the main module enables any obfuscation**.

3. Due to the transitivity of consumer configurations, avoid enabling obfuscation directly in your HAR. Instead, use **-keep-global-name** and **-keep-property-name** to add specific names to a trustlist and minimize impact on dependent modules.

### Local Source Code HAR Package

As unreleased static packages, local source code HAR packages are compiled and obfuscated together with the main module (such as HAP), rather than independently. Therefore, follow the [HAP Package Obfuscation Recommendations](#hap-package-obfuscation-recommendations).

### Released Source Code HAR Package

1. Enable the obfuscation rules. Start with the [recommended options](#recommended-obfuscation-options) and add other options as needed.
2. Understand the [scenarios that require trustlist configurations](bytecode-obfuscation.md#retention-options), and configure a trustlist in the HAR.

    * In **obfuscation-rules.txt**, configure the exported interface names and related property names of your HAR, as well as any names that should not be obfuscated during the build.
    * In **consumer-rules.txt**, configure the names of interfaces and properties that should not be re-obfuscated.

3. Verify the functionality of the HAR package. Note that obfuscation is performed once when building the HAR of this module. When the released HAR package is depended on, if the consumer enables obfuscation, the released code of this HAR package will be obfuscated a second time along with the consumer. Therefore, you need to fully verify that the HAR package functions normally when the consumer enables obfuscation.

4. Release the HAR package.

> **Note:**
>
> When depended on by other modules, note the following two points:
>
> * When the consumer (such as a HAP) enables obfuscation, ArkGuard collects the exported names and related property names of this released HAR package into the non-obfuscation list.
> * When the consumer (such as a HAP) enables obfuscation, ArkGuard collects the trustlist in the obfuscation.txt file of this released HAR package, but does not continue to collect the trustlist in the obfuscation.txt files of the HAR packages (third-party libraries) that this HAR package depends on (this is because the lists of third-party libraries were already collected when the third-party libraries were built). Therefore, **if a released HAR package depends on other HAR packages, you should lock their version numbers and avoid using a dynamic version dependency mechanism.** Otherwise, when a third-party library is upgraded, if its trustlist changes, the changes will not take effect in the HAP, which may cause stability issues.

### Released Bytecode HAR Package

The obfuscation adaptation process for bytecode HAR packages is similar to that for released source code HAR packages. However, since ArkGuard only supports bytecode obfuscation, bytecode HAR packages are not re-obfuscated when used by a dependent module. They are compiled and obfuscated only during the building of the current HAR module.

## HSP Package Obfuscation Recommendations

### General Recommendations

1. Familiarize yourself with the [three types of obfuscation configuration files](bytecode-obfuscation-guide.md#obfuscation-configuration-files) and the [obfuscation rule merging strategies](bytecode-obfuscation.md#obfuscation-rule-merging-strategies). Understand the precautions provided in [HAP Package Obfuscation Recommendations](#hap-package-obfuscation-recommendations) to ensure that your HSP functions correctly when it is used by HAP packages.
2. HSP packages are built independently and are built only once. Therefore, focus on the obfuscation effects within the module and ensure proper interface calls from other modules.
3. Due to the transitivity of consumer configurations, avoid enabling obfuscation directly in your HSP. Instead, use **-keep-global-name** and **-keep-property-name** to add specific names to a trustlist and minimize impact on dependent modules.

### Local Source Code HSP Package

1. Clearly define external interfaces and properties that your source code HSP package provides, and configure these names in **obfuscation-rules.txt** and **consumer-rules.txt**.
2. Follow the [HAP Package Obfuscation Recommendations](#hap-package-obfuscation-recommendations) to ensure the obfuscation effects within the module.
3. Build and verify the HSP package together with the main module to ensure all interfaces provided by the HSP package work correctly.

### Integrated HSP Package

1. Clearly define external interfaces and properties that your integrated HSP package provides, and configure these names in **obfuscation-rules.txt**. There is no need to configure **consumer-rules.txt** because the .tgz file contains both HAR and HSP packages, and the exported interfaces and properties defined in the declaration files of the HAR package are automatically collected into the trustlist.
2. Follow the [HAP Package Obfuscation Recommendations](#hap-package-obfuscation-recommendations) to ensure the obfuscation effects within the module.
3. Ensure that the interfaces that your integrated HSP package provides can be called correctly by dependent modules, especially when obfuscation is enabled.

> **Note**
>
> The rules from which an HSP generates obfuscation.txt come only from the consumer-rules.txt file of the current module, and do not include the consumer-rules.txt files or obfuscation.txt files of dependent modules.
