---
kits: ["ArkTS Kit / Ark Programming Language"]
description: "Guides you through enabling ArkGuard source code obfuscation in DevEco Studio and configuring obfuscation-rules.txt rules, and introduces scenario adaptation, effect viewing, and error stack restoration methods."
keywords: [obfuscation, source code obfuscation, enable obfuscation, ArkGuard, obfuscation-rules.txt, obfuscation rule, view obfuscation effect, error stack restoration, DevEco Studio]
doctype: guide
status: active
---

# Using ArkGuard for Source Code Obfuscation
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @oatuwwutao-->
<!--Designer: @oatuwwutao-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=17ae88719a2d37a0c07e3b6e33ddb120ebd3dbc5 translatedAt=2026-11-06T10:46:03.561Z pushedAt=2026-11-12T11:34:57.224Z nl=1 -->

This guide aims to help developers understand and use the ArkGuard source code obfuscation feature to protect application code security. By enabling source code obfuscation, developers can obfuscate variable names, property names, file names, and other elements in ArkTS code, increasing the difficulty of code reverse engineering and improving application security. This document details how to enable obfuscation in DevEco Studio, configure obfuscation rules, adapt to different obfuscation scenarios, and how to view the obfuscation effect and restore obfuscated error stacks.

## Steps for Enabling Source Code Obfuscation

The source code obfuscation feature is integrated into the system and can be enabled in DevEco Studio.

* Enabling the obfuscation switch  

    To enable obfuscation, set the **enable** field to **true** under **arkOptions.obfuscation.ruleOptions** in the **build-profile.json5** file of your module.
    <!-- @[set_openObfuscation1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/build-profile.json5) -->   
    
    ``` JSON5
    "arkOptions": {
      "obfuscation": {
        "ruleOptions": {
          "enable": true, // Enable the obfuscation switch.
          "files": ["./obfuscation-rules.txt"] // Specify the obfuscation rule file, which takes effect when the current module is compiled.
        },
        // ...
      }
    },
    ```

* Configuring obfuscation rules  

    Enabling the obfuscation switch activates the default settings, which include obfuscation of local variables and parameters. To enable additional obfuscation features, customize the **obfuscation-rules.txt** file specified in the **files** field. Note that the default values in this file may vary across different versions of DevEco Studio.

    For example, in DevEco Studio of version 5.0.3.600 and later, the obfuscation configuration file is as follows, which indicates that property name obfuscation, top-level scope name obfuscation, file name obfuscation, and imported/exported name obfuscation are enabled.
    ```text
    -enable-property-obfuscation
    -enable-toplevel-obfuscation
    -enable-filename-obfuscation
    -enable-export-obfuscation
    ```

    You can also add comments to the obfuscation rule file by prefixing lines with the `#` symbol. The sample code is as follows:
    ```text
    # options:
    -enable-property-obfuscation
    -enable-toplevel-obfuscation
    -enable-filename-obfuscation
    # -enable-export-obfuscation
    -keep-property-name # trustlist for dynamic property names
    ```

    For details about all configuration files involved in the obfuscation process, see [Obfuscation Configuration Files](#obfuscation-configuration-files). When adapting obfuscation for the first time, you are advised to configure and perform obfuscation by referring to the [Configuring Obfuscation Options](#configuring-obfuscation-options) section.

    > **NOTE**
    >
    > 1. In DevEco Studio versions prior to 5.0.3.600, source code obfuscation is enabled by default for new projects, and code developed on the stage model using API version 10 or later is automatically obfuscated.
    > 2. In DevEco Studio 5.0.3.600 and later versions, source code obfuscation is disabled by default for new projects. To enable obfuscation, set the `ruleOptions.enable` field in the `build-profile.json5` file of the module to **true**. The `obfuscation-rules.txt` file has the following options enabled by default: `-enable-property-obfuscation`, `-enable-toplevel-obfuscation`, `-enable-filename-obfuscation`, and `-enable-export-obfuscation`. You can customize the obfuscation settings as needed.

* Configuring obfuscation retention options

    After obfuscation is enabled, methods, properties, or paths in the code are obfuscated. However, at runtime, if unobfuscated methods, properties, or paths are accessed, functions may become unavailable. Therefore, you need to configure retention options based on different scenarios. For the troubleshooting scenarios and configuration methods of retention options, see [ArkGuard Obfuscation Retention Options](./source-obfuscation-keep-options.md).

    When checking the scenarios and configuration fields, you are advised to [use obfuscation for code hardening](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-build-obfuscation#section19439175917123) to quickly identify the retention options and trustlist fields to be configured.

* Specifying release compilation  

    Source code obfuscation is supported only for release builds, not for debug builds. This means that obfuscation will only be applied when a module is compiled in release mode, not in debug mode. You can view and modify the build mode by referring to [Specifying a Build Mode](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-hvigor-compilation-options-customizing-guide#section192461528194916).

    > **NOTE**
    >
    > Release compilation supports obfuscation, while debug compilation does not. To determine whether a difference in application behavior is caused by obfuscation, troubleshoot by enabling or disabling the obfuscation switch rather than by merely switching the compilation mode.

### Obfuscation Configuration Files

The following table briefly summarizes the differences among the three obfuscation configuration files:

| Configuration File (Example) | Configuration Type | Whether the Configuration Is Modifiable | Whether It Affects the Obfuscation of This Module | Whether It Affects the Obfuscation of Other Modules |
| --- | --- | --- | --- | --- |
| obfuscation-rules.txt | Custom | Yes | Yes | No |
| consumer-rules.txt    | Custom | Yes | No | Yes |
| obfuscation.txt       | Compilation artifact | Not applicable. It is automatically generated when building a HAR or HSP. | Not applicable | Yes |

* `obfuscation-rules.txt`  

    For HAP, HAR, and HSP modules, the **arkOptions.obfuscation.ruleOptions.files** field in the **build-profile.json5** file specifies obfuscation rules applied during module compilation. A default obfuscation rule file, named **obfuscation-rules.txt**, is created when a new project is set up.

* `consumer-rules.txt`  

    For HAR and HSP modules, an additional **arkOptions.obfuscation.consumerFiles** field is available in the **build-profile.json5** file. This field specifies obfuscation rules that should be applied when this package is depended upon in the current compilation process. A default **consumer-rules.txt** file is created when a new HAR or HSP module is set up. The key difference between **consumer-rules.txt** and **obfuscation-rules.txt** is as follows: **obfuscation-rules.txt** applies to the compilation of the current module, whereas **consumer-rules.txt** applies to the compilation of other modules that depend on the current module.

  Example of the build-profile.json5 configuration:
    <!-- @[set_openObfuscation2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/build-profile.json5) -->    
    
    ``` JSON5
    "arkOptions": {
      "obfuscation": {
        "ruleOptions": {
          "enable": true, // Enable the obfuscation switch.
          "files": ["./obfuscation-rules.txt"] // Specify the obfuscation rule file, which takes effect when the current module is compiled.
        },
        "consumerFiles": ["./consumer-rules.txt"] // Specify the obfuscation rule file, which takes effect when other modules that depend on the current module are compiled.
      }
    },
    ```

  > **Description**:
  >
  > If [ArkGuard obfuscation configuration options](./source-obfuscation-rule-options.md) are configured in the `consumer-rules.txt` file, they may affect the main module that depends on the HAR or HSP. Therefore, it is recommended that only [ArkGuard obfuscation retention options](./source-obfuscation-keep-options.md) be configured in this file.

* `obfuscation.txt`  

    Unlike the preceding two configuration files that developers can modify, `obfuscation.txt` is a file automatically generated based on `consumer-rules.txt` and the obfuscation rule files of dependent modules when compiling and building a HAR or HSP. As a compilation artifact, it exists in the released HAR or HSP package. When other applications depend on the released package, the obfuscation rules in it are merged and applied to the current compilation process. For details about the generation and merging logic of the `obfuscation.txt` content, see [Obfuscation Rule Merging Policy](./source-obfuscation.md#obfuscation-rule-merging-strategies).

  > **NOTE**
  >
  > For third-party libraries, the **obfuscation.txt** file takes effect only when the third-party library is depended upon in the **oh-package.json5** file of the module. If the dependency is specified in the **oh-package.json5** file of the project, the **obfuscation.txt** file of the third-party library does not take effect.

### Configuring Obfuscation Options
1. When `-enable-toplevel-obfuscation` is configured, access to global variables using `globalThis` fails. To rectify the fault, use `-keep-global-name` to retain the global variable name.
2. After the preceding adaptation is successful, configure **-enable-property-obfuscation**, and perform adaptation in the following scenarios:
    1. If the code has static definition with dynamic access, or dynamic definition with static access, use `-keep-property-name` to retain the property name.
       <!-- @[example_openObfuscation1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ts) -->   
       
       ``` TypeScript
       // Static definition, dynamic access: the property name is static when the object is defined, but is accessed by dynamically constructing the property name (usually through string concatenation).
       // ArkGuardAbility.ts
       const obj001 = {
         staticName: 'value'  // Statically defined property.
       };
       const fieldName = 'static' + 'Name';  // Dynamically construct the property name. Use -keep-property-name staticName to retain this property name.
       console.info(obj001[fieldName]);  // Dynamically access the property using bracket syntax.
       ```

       <!-- @[example_openObfuscation2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ts) -->   
       
       ``` TypeScript
       // Dynamic definition, static access: the property name is determined by a dynamic expression when the object is defined, but dot syntax is used directly for access (assuming the developer knows the result of the property name)
       // ArkGuardAbility.ts
       const dynamicExpression = 'dynamicPropertyName';
       const obj002 = {
         [dynamicExpression]: 'value'  // Dynamically define the property
       };
       console.info(obj002.dynamicPropertyName);// Use dot syntax to statically access the property. Use -keep-property-name dynamicPropertyName to retain the property name
       ```
    2. If the code uses dot notation to access fields not defined in ArkTS/TS/JS code (for example, native so libraries, fixed JSON files, or database fields):
        1. If the code references APIs of an so library, for example, `import testNapi from 'library.so';testNapi.foo();`, use [-keep-property-name](./source-obfuscation-keep-options.md#-keep-property-name) foo to retain the property name.
        2. For fields in JSON files, use **-keep-property-name** to retain the JSON field names.
        3. For database-related fields, use **-keep-property-name** to retain the database field names.
    3. When building a HAR module for use by other modules, use **-keep-property-name** in the **consumer-rules.txt** file of the HAR module to retain properties that should not be re-obfuscated. The **consumer-rules.txt** file generates the **obfuscation.txt** file during HAR compilation. When the HAR module is depended upon by other modules, DevEco Studio parses the **obfuscation.txt** file to read the trustlist.
    4. Verify application functionality and identify any missed scenarios. If the application functionality is abnormal, find the code of the error line in the corresponding [intermediate products](#viewing-obfuscation-effects) based on the obfuscated error stack, identify the necessary trustlist configurations, and use **-keep-property-name** to retain them.
3. After the preceding adaptations are successful, configure **-enable-export-obfuscation**, and perform adaptation in the following scenarios:
    1. For HSP modules that provide interfaces and properties to other modules, use **-keep-global-name** to retain the interface names and **-keep-property-name** to retain the property names in exposed classes/interfaces.
    2. When building HAR modules for use by other modules, use **-keep-global-name** to retain interface names and **-keep-property-name** to retain the property names in exposed classes/interfaces in the **obfuscation-rules.txt** file.
    3. If the code references APIs of an so library, for example, `import { napiA } from 'library.so'`, use `-keep-global-name napiA` to retain the so interface name.
    4. Verify application functionality and interface call functionality when the module is depended upon, and identify any missed scenarios. If the application functionality is abnormal, find the code of the error line in the corresponding [intermediate products](#viewing-obfuscation-effects) based on the obfuscated error stack, identify the necessary trustlist configurations, and retain them.
4. After the preceding adaptations are successful, configure **-enable-filename-obfuscation**, and perform adaptation in the following scenarios:
    1. If the code contains dynamic import statements, for example, `const path = './filePath'; import(path)`, file reference failures may occur. Use `-keep-file-name filePath` to retain this file name.
    2. If the application has a [routerMap configuration](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/module-configuration-file#routermap) that describes routing information, use **-keep-file-name** to retain the page source file path, which is specified by **pageSourceFile** field in the routing information.
    3. If the code passes ohmUrl for page navigation, for example, `router.pushUrl({url: '@bundle:com.example.routerPage/Library/Index'})`, use `-keep-file-name` to retain the file name portion in the path (such as Library and Index).
    4. Verify application functionality and identify any missed scenarios. If the application function is abnormal and the error stack contains obfuscated paths, you can query the original path in the **build/default/[...]/release/obfuscation/nameCache.json** file within the module and then locate the source code file. You can also use the [hstack plugin](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-command-line-hstack) to trigger automatic deobfuscation of error stacks. After locating the paths to retain, use **-keep-file-name** to retain them.

### Precautions
* Currently, custom obfuscation plugins are not supported in the hvigor build process.
* If a module that depends on an obfuscated HAR enables obfuscation, the HAR will be obfuscated again.

## Viewing Obfuscation Effects

After obfuscation is complete, the obfuscated intermediate products are generated in the `build` directory of the compilation product. You can view the intermediate products to check the obfuscation effect. In addition, the name mapping file and system API trustlist file are generated in this directory.

* Obfuscated file directory: `build/default/[...]/release/moduleName`.
* Directory of the name mapping file and system API trustlist file: `build/default/[...]/release/obfuscation`.
  * The name mapping file, named **nameCache.json**, records the mappings between source code names and names after obfuscation.
  * The system API trustlist file, named **systemApiCache.json**, records the APIs and property names that will not be obfuscated in the source code.

  ![build-product](figures/build-product.png)

## Deobfuscating Error Stacks

For an obfuscated application, code names are changed, making the error stack printed during a crash difficult to understand. You can use the [hstack plugin](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-command-line-hstack) in Command Line Tools of DevEco Studio to deobfuscate the source code stack and then analyze the issue.

Back up the `sourceMaps.map` file and the obfuscation name mapping file nameCache.json generated during application compilation. The deobfuscation tool requires these files.

If you use a self-built online platform or pipeline to build the application, the sourceMaps.map file and the obfuscation name mapping file nameCache.json generated during compilation cannot be obtained. You can use the corresponding files generated by local compilation as substitutes.

Source code mapping information file: sourceMaps.map. This file records the mapping relationship between the compressed/transformed code and the original source code.

![obfuscation-product](figures/obfuscation-product.png)
