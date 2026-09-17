# Process Model Overview

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=2f4b89223ea807a0581c60a9a81b8de70ba28fa9 translatedAt=2026-08-31T12:32:15.849Z pushedAt=2026-08-31T14:22:55.039Z -->

A process is the basic unit for the system to allocate resources and an important foundation of the operating system's runtime structure. The following describes the system's process model from the global perspective of an application.

After an application process is started, the system creates a main thread by default and enters a message loop, with application components running on the main thread. If an application needs to handle complex or time-consuming tasks, developers can create a [Worker](../reference/apis-arkts/js-apis-worker.md) thread or submit tasks to [Taskpool](../reference/apis-arkts/js-apis-taskpool.md) for execution. For details about the thread model, see [Thread Model](thread-model-stage.md).

## Component-Driven Process Model

In traditional desktop operating systems (such as Windows), the process model is application-centric. Applications explicitly create processes through system APIs, and within the created processes they create windows, message loops, and other components on their own. Developers need to directly manage the creation, scheduling, and termination of processes.

The OpenHarmony process model, by contrast, is component-centric. In most cases, applications do not directly participate in process creation and management. Instead, they develop and configure various components (such as UIAbility and ExtensionAbility), and the system automatically creates and assigns processes based on the component type and configuration. Developers generally only need to focus on the components themselves. Only in the child process scenario does an application need to actively create a process (for details, see [Extended Process Type](#extended-process-type)).

## Process Types

### Basic Process Types

When developing an application with complex functions, a developer may include multiple [UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md) components and multiple ExtensionAbility components. The ExtensionAbility components include [FormExtensionAbility](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md) and [ShareExtensionAbility](../reference/apis-ability-kit/js-apis-app-ability-shareExtensionAbility.md), as shown in Figure 1. In the application runtime, the possible process types are as follows:

- **Main process**: By default, all UIAbility<!--Del-->, ServiceExtensionAbility, and DataShareExtensionAbility<!--DelEnd--> components in an application (with the same bundle name) run in the same independent process (main process), that is, "Main Process1" in Figure 1.

- **ExtensionAbility process**: All ExtensionAbility<!--Del--> components of the same type (except ServiceExtensionAbility and DataShareExtensionAbility)<!--DelEnd--> in an application (with the same bundle name) run in an independent process, such as "FormExtensionAbility Process" and "Other ExtensionAbility Process" (for ExtensionAbility components of other types) in Figure 1.

  In particular, for an ExtensionAbility inherited from [UIExtensionAbility](../reference/apis-ability-kit/js-apis-app-ability-uiExtensionAbility.md), an independent process can be configured for each instance. For example, ShareExtensionAbility can specify that each ShareExtensionAbility instance runs in a separate independent process. For details, see [UIExtensionAbility](../reference/apis-ability-kit/js-apis-app-ability-uiExtensionAbility.md). For [AppServiceExtensionAbility](../reference/apis-ability-kit/js-apis-app-ability-appServiceExtensionAbility.md), you can set the [extensionProcessMode](../quick-start/module-configuration-file.md#extensionabilities) field in the module.json5 file to type to specify that AppServiceExtensionAbility components with different names each run in an independent process.

- **Render process**: When the Web component in an application runs, the system allocates a Render process for it to perform rendering, such as "Render Process" in Figure 1.

**Figure 1** Basic process types


>**NOTE**
>
> - There are no fixed rules for naming process names, and process names are not directly associated with process types. Therefore, they cannot be used to determine business logic. For example, a developer develops an application com.example.myapplication that contains an input method component [InputMethodExtensionAbility](../reference/apis-ime-kit/js-apis-inputmethod-extension-ability.md). The input method component runs in an independent process, and its process name is usually "com.example.myapplication:input". However, this is not fixed. The process corresponding to this process name is not necessarily the input method process, and the input method process does not necessarily use this process name.
> - A process can contain multiple AbilityStages, and an AbilityStage can contain multiple Abilities. The lifecycle of a process is closely related to the lifecycle of Abilities. Only after all Abilities in the process exit does the process enter the destruction process. In other words, to exit a process, you must first exit all Abilities in the process.

### Extended Process Type

**Child process**: On PC/2-in-1 and tablet devices, if developers need to create multiple processes to execute background tasks, they can call the APIs in [childProcessManager](../reference/apis-ability-kit/js-apis-app-ability-childProcessManager.md) to create child processes. The lifecycle of a child process follows its parent process. When the parent process terminates, the child process terminates accordingly. As shown in Figure 2, "ArkTS Child Process" and "Native Child Process" are child processes created by the main process. A child process does not support creating further child processes. For details about child process development, see [Child Process Development Guide (C/C++)](./capi-nativechildprocess-development-guideline.md) and [Child Process Development Guide (ArkTS)](./arkts-child-process-development-guideline.md).

## Independent Process Configuration

The first independent process created when an application starts is the **main process**, in which core components run by default. On PC/2in1 and tablet devices, you can also configure specified components to run in other **independent processes** (which have independent resources and lifecycles, are isolated from each other, and communicate through IPC) outside the main process in the following ways, to achieve service isolation or fault isolation:

- **Module independent process**: For an application with multiple HAPs, the services of each HAP are relatively independent. If you want UIAbilities of different HAPs to run in different processes, you can set the isolationMode field to isolationOnly (run only in an independent process; the application cannot be installed on non-PC/2in1 devices) or isolationFirst (run in an independent process first; run in an independent process on PC/2in1 devices and in a non-independent process on other devices) in the [module.json5 configuration file](../quick-start/module-configuration-file.md#tags-in-the-configuration-file). Then all UIAbilities under the HAP run in a unified independent process. As shown in Figure 2, UIAbilityC runs in "Main Process2" instead of "Main Process1". For details about the configuration method, see Module Independent Process.

- **Dynamic process specification**: When UIAbility instances in the same HAP need to be dynamically allocated to different processes based on runtime states (for example, each process supports a maximum of five instances), you can set the isolationProcess field of the UIAbility to true in the module.json5 configuration file, as shown by UIAbilityD in Figure 2. When the system starts a UIAbilityD instance, it calls back [onNewProcessRequest](../reference/apis-ability-kit/js-apis-app-ability-abilityStage.md#onnewprocessrequest11) of the [master process](ability-terminology.md#master-process). In this callback, you return a custom process identifier string. If the string is the same as one returned by a previous onNewProcessRequest callback, the process where that identifier resides is reused; otherwise, a new process is created. As shown in Figure 2, "Main Process3" and "Main Process4" are multiple processes where UIAbilityD runs. For details about the configuration method, see Dynamic Process Specification.

- **Static process specification**: When UIAbility or EmbeddedUIExtensionAbility in the same application needs to run in different processes, you can configure the process field in the [abilities label](../quick-start/module-configuration-file.md#abilities) or the process field in the [extensionAbilities label](../quick-start/module-configuration-file.md#extensionabilities) of the module.json5 configuration file with different strings. When the system starts UIAbility or EmbeddedUIExtensionAbility, it allocates a process based on this string. If the process fields of multiple UIAbilities and multiple EmbeddedUIExtensionAbilities in the same application are configured with the same string, these UIAbilities and EmbeddedUIExtensionAbilities all run in the same process, as shown by "Main Process5" in Figure 2. For details about the configuration method, see Static Process Specification.

**Figure 2** Independent process configuration and child process


<!--Del-->

Based on the preceding model, system applications often provide different external system capabilities, and each capability or multiple capabilities need to run in the same process, relying on a more flexible process model. A system application can apply for the allowAppMultiProcess multi-process privilege to configure a custom process name for a specified HAP. Then UIAbility, DataShareExtensionAbility, and ServiceExtensionAbility in the HAP run in the custom process (as shown in Figure 3). For details about how to apply, see [Application Privilege Configuration Guide](../../device-dev/subsystems/subsys-app-privilege-config-guide.md). Different HAPs can customize process names by configuring the process attribute in the [module.json5 configuration file](../quick-start/module-configuration-file.md#tags-in-the-configuration-file).

**Figure 3** Multi-process diagram


<!--DelEnd-->