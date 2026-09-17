# Independent Process Development Guide

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @jsjzju-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=6a098da784d15a95521a34f2fd7e52cc656f398e translatedAt=2026-08-31T12:32:01.062Z pushedAt=2026-08-31T14:04:13.483Z -->

## Overview

In multi-module application development scenarios, developers often face issues such as mutual interference between modules and overall crashes caused by exception propagation. The process isolation mechanism allows developers to configure different functional modules to run in independent processes, achieving process isolation between modules and improving application stability and security. This mechanism is applicable to scenarios that require module isolation, fault isolation, and security isolation.

> **NOTE**
>
> The APIs of this module can be used only in the [Stage model](ability-terminology.md#stage-model).

## Static Specification of Process

### Scenario Introduction

Static specification of process applies to scenarios where process allocation can be determined at compile time, for example, isolating certain functional components into an independent process to improve application stability and security. When multiple UIAbilities or EmbeddedUIExtensionAbilities in the same application need to run in different processes, developers can statically specify the process to run by configuring the process field in the [abilities tag](../quick-start/module-configuration-file.md#abilities) or [extensionAbilities tag](../quick-start/module-configuration-file.md#extensionabilities) of the [module.json5 configuration file](../quick-start/module-configuration-file.md). When starting a UIAbility or EmbeddedUIExtensionAbility, the system allocates the process based on the process field.

Typical scenarios include:

- **Isolating high-risk functional modules**: applicable to functional modules with high stability risks, such as third-party rendering engines, complex codecs, and JNI calls.

- **Reusing the process of associated components**: applicable to multiple UIAbilities with similar responsibilities that need to coexist stably. By specifying the same process field for them, these UIAbilities run in the same process and share resources, such as the Settings, Personal Center, and Help Center pages.

- **Isolating embedded UI extensions**: applicable to scenarios where embedded UI components are provided to other applications through EmbeddedUIExtensionAbility.

### Constraints

- Static specification of process takes effect only for UIAbility and EmbeddedUIExtensionAbility.

- Static specification of process is supported only on PC/2in1 and Tablet device types.

- In the [abilities tag](../quick-start/module-configuration-file.md#abilities) or [extensionAbilities tag](../quick-start/module-configuration-file.md#extensionabilities), a process field starting with ":" indicates an application private process, and the actual process name format is "application bundle name:specified string".

- If the process fields of multiple UIAbilities and EmbeddedUIExtensionAbilities are configured with the same string, they run in the same process.

### How to Develop

This sample code uses UIAbility as an example to describe how to configure static process specification. In the [module.json5 configuration file](../quick-start/module-configuration-file.md) of the UIAbility that needs to run in an independent process, add the process field to the corresponding ability under the [abilities tag](../quick-start/module-configuration-file.md#abilities). The process field value starts with ":", indicating an application private process. Multiple abilities configured with the same process field value will run in the same process. In the following example, EntryAbility does not have the process field configured and runs in the default process. EntryAbility1 and EntryAbility2 both have the process field configured as ":processTag", so they will run in the same independent process, with the process name "application bundle name:processTag":

<!-- @[static_isolation_process_config](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/StaticIsolationProcess/entry/src/main/module.json5) --> 

``` JSON5
{
  "module": {
// ...
    "abilities": [
// ...
      {
        "name": "EntryAbility1",
        "srcEntry": "./ets/entryability1/EntryAbility1.ets",
// ...
        "process": ":processTag"
      },
      {
        "name": "EntryAbility2",
        "srcEntry": "./ets/entryability2/EntryAbility2.ets",
// ...
        "process": ":processTag"
      }
    ],
// ...
  }
}
```

## Dynamic Specification

### Scenario Introduction

Dynamic specification applies to scenarios where the running process is dynamically determined at runtime, for example, dynamically isolating certain components into an independent process to improve application stability and security. For UIAbility instances, developers need to set the isolationProcess field to true in the [abilities tag](../quick-start/module-configuration-file.md#abilities) corresponding to the UIAbility. When the system starts the UIAbility instance, the [Main Control Process](ability-terminology.md#master-process) triggers the [onNewProcessRequest](../reference/apis-ability-kit/js-apis-app-ability-abilityStage.md#onnewprocessrequest11) callback method to return a string that identifies the independent process. The name of the independent process where the UIAbility runs is concatenated as "bundle name:string returned by the onNewProcessRequest callback method". If the returned string has been created by the developer before, the process corresponding to that identifier is reused; otherwise, a new process is created.

<!--Del-->

For UIExtensionAbility of the sys/commonUI type, developers need to set the isolationProcess field to true in the [extensionAbilities tag](../quick-start/module-configuration-file.md#extensionabilities) corresponding to the UIExtensionAbility. Similarly, when the system starts the UIExtensionAbility instance of the sys/commonUI type, the [Main Control Process](ability-terminology.md#master-process) triggers the [onNewProcessRequest](../reference/apis-ability-kit/js-apis-app-ability-abilityStage.md#onnewprocessrequest11) callback method to return a string that identifies the independent process.

<!--DelEnd-->

Typical scenarios include:

- **Multi-account/multi-tenant isolation**: Applies to scenarios where the same application serves multiple accounts, tenants, workspaces, and so on simultaneously.

- **Multi-document/multi-instance dynamic allocation**: Applies to scenarios such as document editing and multi-tab browsing that require managing instances by document or session dimension.

- **Process decision based on runtime context**: Applies to scenarios where process ownership is determined based on startup information such as data security level, content source, and user configuration.

### Constraints

- Dynamic specification takes effect only for UIAbility<!--Del--> and UIExtensionAbility of the sys/commonUI type<!--DelEnd-->.

- Dynamic specification is supported only on PC/2in1 and Tablet device types.

### How to Develop

This sample code uses UIAbility as an example to describe how to develop dynamic specification.

1. Configure dynamic process specification.

    Perform two configurations in the [module.json5 configuration file](../quick-start/module-configuration-file.md): first, specify the AbilityStage source file path through srcEntry under [configuration file tags](../quick-start/module-configuration-file.md#tags-in-the-configuration-file); then, add the isolationProcess field and set it to true for the UIAbility that requires dynamic process specification under the [abilities tag](../quick-start/module-configuration-file.md#abilities).

    In the following example, the UIAbility instance named EntryAbility1 has isolationProcess set to true, and its running process is dynamically specified by the string returned by the onNewProcessRequest callback method of AbilityStage.

    <!-- @[dynamic_isolation_process_config](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/DynamicIsolationProcess/entry/src/main/module.json5) --> 

    ``` JSON5
    {
      "module": {
    // ...
        "srcEntry": "./ets/MyAbilityStage/MyAbilityStage.ets",
    // ...
        "abilities": [
    // ...
          {
            "name": "EntryAbility1",
            "srcEntry": "./ets/entryability1/EntryAbility1.ets",
    // ...
            "isolationProcess": true
          }
        ],
    // ...
      }
    }
    ```

2. Implement the onNewProcessRequest callback method of AbilityStage.

    In the AbilityStage source file specified by srcEntry, implement the [onNewProcessRequest](../reference/apis-ability-kit/js-apis-app-ability-abilityStage.md#onnewprocessrequest11) callback method. When the system starts a UIAbility instance with isolationProcess set to true, it triggers this callback method, and then dynamically specifies the independent process in which the UIAbility instance runs based on the string returned by this method.

    <!-- @[dynamic_isolation_process](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/DynamicIsolationProcess/entry/src/main/ets/MyAbilityStage/MyAbilityStage.ets) --> 

    ``` TypeScript
    import AbilityStage from '@ohos.app.ability.AbilityStage';
    
    export default class MyAbilityStage extends AbilityStage {
    // ...
      onNewProcessRequest(want: Want): string {
        //Return the developer-defined string. The independent process name concatenation rule is: bundle name:developer-defined string.
        return 'testKey';
      }
    }
    ```

## Module Independent Process

### Scenario Introduction

For an application with multiple HAPs, different HAPs may carry different business functions. When the business of each HAP is relatively independent and needs to run in isolation, developers can configure module independent processes so that the UIAbility of different HAPs runs in different processes (the process name format is "application bundle name:module name"), thereby achieving business isolation and preventing exceptions in one module from affecting the running of other modules.

Typical scenarios include:

- **Multi-HAP business isolation**: applicable to applications split into multiple HAPs by business domain, such as instant messaging, audio/video conferencing, and document collaboration business modules.

- **Feature module isolation**: applicable to dynamic feature modules that carry relatively independent functions, decoupling the feature module from the main application.

### Constraints

- It takes effect only for UIAbility.

- It is supported only on PC/2in1 and Tablet device types.

- When isolationMode is set to isolationOnly, the UIAbility in this HAP runs only in the independent process, not in the main process.

### How to Develop

When the UIAbility of the same HAP needs to run in an independent process, add the isolationMode field under the [configuration file tag](../quick-start/module-configuration-file.md#tags-in-the-configuration-file) in the [module.json5 configuration file](../quick-start/module-configuration-file.md) of the HAP module, and set it to "isolationOnly" or "isolationFirst".

The following example uses the entry module configured with isolationOnly mode as an example:

<!-- @[module_isolation_process_config](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ModuleIsolationProcess/entry/src/main/module.json5) --> 

``` JSON5
{
  "module": {
    "name": "entry",
// ...
    "isolationMode": "isolationOnly",
// ...
    "abilities": [
// ...
    ],
    "extensionAbilities": [
// ...
    ]
  }
}
```