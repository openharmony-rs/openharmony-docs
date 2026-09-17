# Application Quick Start

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SHASAI-->
<!--Designer: @SHASAI-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=77e75fae6d5c2cc1ac0317f040f760f725830586 translatedAt=2026-08-31T12:32:06.296Z pushedAt=2026-08-31T14:34:25.336Z -->

## Overview

As application functions continue to expand, the startup phase often requires a series of operations such as process creation, runtime initialization, module loading, resource parsing, and first-screen construction. When the cold startup path is long or resource and module loading account for a high proportion of the startup phase, users will wait longer on the first screen, which in turn affects application experience and retention performance.

Starting from API version 24, the system provides the application quick start mechanism. This mechanism completes the initialization of reusable processes in the startup phase in advance. When the user starts the application again, the relevant startup initialization results are reused, reducing repeated initialization and loading overhead and shortening the startup path, which helps improve application startup speed and stability.

Features of the application quick start mechanism:

- **System-level startup acceleration**: By reusing startup initialization results, it reduces repeated execution processes in the cold startup phase and significantly improves startup performance.

- **Seamless user experience improvement**: Users can enjoy improved application startup experience without any additional operations.

- **Optimized for startup bottlenecks**: It is particularly suitable for application scenarios with high cold startup latency or a large proportion of resource loading or module loading.

Developers can determine whether an application is suitable for integrating the quick start capability from the following dimensions:

- The application has poor cold startup performance, with a startup latency higher than 1.6s.

- Resource loading and module loading account for more than 25% of the startup process time.

## Basic Concepts

* Application quick start: a startup acceleration capability provided by the system. After an application integrates this capability, the system completes part of the startup initialization work in advance at an appropriate time, and reuses the related initialization results in subsequent startups to reduce repeated startup processes.

* Quick start initialization: the process in which the system completes initialization work in advance for application quick start. This process is only suitable for executing startup logic that is reusable, has no external state dependencies, and does not affect data consistency. When the device is unlocked and the user turns off the screen or locks the screen, the system starts quick start initialization and completes the initialization process subsequently.

* Quick start initialization result: the reusable startup result formed after quick start initialization is completed. When the application, system, or runtime environment changes, the system may clear the existing initialization results and perform quick start initialization again after the conditions are met.

* Quick start initialization result clearing: when an application is uninstalled, installed, or updated, when the system restarts, or when some system environment variables change, the system clears the existing quick start initialization results. After clearing, the application needs to perform quick start initialization again when the conditions are met.

* Quick start point: a timing boundary in the startup process. The startup process before the quick start point is included in the quick start optimization scope and is skipped during application quick start. The startup process after the quick start point is not affected and continues to execute in both normal startup and quick start.

* Quick start: an application reuses part of the startup initialization results through the quick start mechanism to accelerate the next startup. Quick start only affects the process before the quick start point; the business logic after the quick start point still executes according to the normal startup sequence.

* Quick start risky operation: an operation that is not suitable for execution during quick start initialization, such as operations that depend on real-time reading of disk data, registering event listeners that require continuous responses, establishing long-lived network connections, and performing stateful inter-process communication. Such operations need to be deferred beyond the quick start point or re-synchronized in the callback after quick start.

## Constraints

* Currently, only phones are supported.

* In developer mode, applications signed with a debug signature are not subject to system-side control restrictions. Developers can independently integrate, debug, and locally test the quick start feature.

<!--RP1--><!--RP1End-->

* After an application configures quick start, whether quick start is actually performed and the specific quick start timing are comprehensively determined by the system based on information such as user habits. Developers cannot intervene in this process.

## Implementation Principle

The quick start technology completes the initialization of reusable parts in the startup process in advance. When the application starts, it can reuse the relevant initialization results, thereby skipping this part of the startup process and achieving the goal of faster startup. As shown in the following figure, compared with normal startup, quick start can skip some stages in the startup process, thereby reducing the startup latency:


**The processes included in the quick start point are**: AbilityStage module loading, [AbilityStage.onCreate](../reference/apis-ability-kit/js-apis-app-ability-abilityStage.md#oncreate), and UIAbility module loading. During [module loading](../arkts-utils/arkts-module-side-effects.md), some code is executed, including top-level code, so constructors, and class static variable initialization.

## Quick Start Adaptation

### Quick Start Risky Operations

Quick start skips part of the startup process. To ensure data consistency and correct state, developers need to eliminate risky operations in the quick start initialization process to guarantee the correctness of application data after quick start.

Examples of risky operations are as follows:

* Disk data access

    Disk data read operations that occur during quick start initialization are not executed during quick start, which may lead to data inconsistency.

    Example: During quick start initialization, the application business reads the font attribute (SimSun) stored in the database. After the application quick start, the user changes the font to KaiTi, and this attribute is persisted to the database file. The application then exits. The next time the application quick starts, because the database is not read again (this process has been skipped), the font remains SimSun instead of the updated KaiTi.

* Event listener callback registration

    Callback event listeners established during quick start initialization do not continue to respond before quick start, which may lead to event loss.

    Example: During quick start initialization, the application business registers a color mode listener, initially in dark mode. When the application has not been started by the user, the system color mode changes to light mode. Because this listener does not continue to respond before quick start, it cannot receive the broadcast message for the color mode switch. The next time the user starts the application through quick start, the application still displays dark mode.

* Network access

    Network connections established during quick start initialization are uncontrollable and may cause issues such as connection interruption.

    Example: During quick start initialization, a long-lived TCP connection is established to receive cloud information. After quick start initialization completes, the connection stops responding continuously, and a timeout causes the connection to fail.

* Inter-process communication (IPC)

    During quick start initialization, stateful inter-process communication is prohibited, such as saving application state and data persistence (stateless inter-process communication such as parameter retrieval is allowed). Otherwise, the protection mechanism is triggered and quick start initialization fails.

### Postpone Quick Start Risky Operations Beyond the Quick Start Point

The system provides a new callback API [onAboutToCreateAbility()](../reference/apis-ability-kit/js-apis-app-ability-abilityStage.md). This API is triggered after AbilityStage.onCreate() completes, but it does not participate in the quick start initialization process. This callback is invoked regardless of whether the application quick start feature is enabled.

**Example 1:** AbilityStage.onCreate contains quick start risky operations.

```TypeScript
export class AppAbilityStage extends AbilityStage {
    onCreate() {
        this.readFile();
    }
    readFile() {
        // Read a file from the disk.
    }
}
```

Recommendation:

1. Postpone the quick start risky operations to AbilityStage.onAboutToCreateAbility.

    ```TypeScript
    export class AppAbilityStage extends AbilityStage {
        onAboutToCreateAbility() {
            this.readFile();
        }
    }
    ```

2. When adjusting the business logic, consider timing dependencies to ensure the correctness of the business logic.

3. AbilityStage.onCreate() is the first lifecycle callback that contains a large amount of business logic. If the business in this callback is difficult to split, it is recommended that developers move the entire content of AbilityStage.onCreate() to [onAboutToCreateAbility()](../reference/apis-ability-kit/js-apis-app-ability-abilityStage.md) during the initial adaptation. Later, the benefits can be expanded by moving business logic forward.

**Example 2:** Quick start risky operations exist in the top-level code.

The following example instantiates a class in the top-level code, which ultimately leads to file access:

```TypeScript
class ClassA {
    constructor() {
        this.readFile();
    }

    readFile() {
        // Read the file from the disk.
    }
}

let tmp = new ClassA();
```

Recommendation:

1. Top-level code is executed when the module is imported, so its timing is bound to the first caller. This makes it an implicit and uncontrollable invocation, and modifying it can easily disrupt the invocation sequence. Therefore, it is recommended to implement business logic in non-top-level code.

2. Specifically for the quick start feature, the system requires that application modules must not perform quick start risky operations in top-level code. Instead, such operations should be moved to lifecycle callbacks based on the business logic.

**Example 3:** A quick start risky operation exists in a C++ constructor.

```TypeScript
static napi_module OpenPlatformModule = {
    .nm_version = 1,
    .nm_flags = 100,
    .nm_filename = nullptr,
    .nm_register_func = Init,
    .nm_modname = "openplatform",
    .nm_priv = ((void *)0),
    .reserved = {0}
};

void read_file() {
    // Read the file from the disk.
}

extern "C" __attribute__((constructor)) void RegisterOpenPlatformModule(void) {
    napi_module_register(&OpenPlatformModule);
    read_file();
}
```

Recommendation:

1. Check the .so files loaded during the startup process one by one. For .so files whose constructors do not contain quick start risky operations, perform dlopen in AbilityStage.onCreate to expand the quick start benefit.

2. For .so files whose constructors contain risky operations, invoke them in lifecycle callbacks outside the quick start point, such as UIAbility.

**Example 4:** A quick start risky operation exists in the initialization of a class static variable.

The following example contains two types of static initialization: one is static variable initialization, which reads a file; the other is static code block execution, which performs network access.

```TypeScript
export class AppAbilityStage extends AbilityStage {
    private a = 1;
    static data = AppAbilityStage.readFile();
    static {
        AppAbilityStage.netAccess();
    }
    static readFile() {
        // Read the file from the disk.
    }
    static netAccess() {
        // Access the network.
    }
}
```

Recommendation: Adjust the code based on the business logic to move the quick start risky operations out of the quick start point.

### Updating Data in the Update Callback

Considering the difficulty of actually adjusting business logic, some external data interactions are hard to isolate. The quick start mechanism provides developers with a new callback [onLaunchFromHyperSnap()](../reference/apis-ability-kit/js-apis-app-ability-abilityStage.md). This callback is executed only in the quick start process (rather than the quick start initialization process), and is not executed during a normal cold start. Developers can re-request external data for synchronization in this callback to ensure data consistency.

```TypeScript
export class AppAbilityStage extends AbilityStage {
    onCreate() {
        this.initLanguage(language);
    }
    initLanguage(language) {
        readFile(); // A quick start risky operation exists in AbilityStage.onCreate.
    }
    readFile() {
        // Read the file from the disk.
    }
}
```

```TypeScript
export class AppAbilityStage extends AbilityStage {
    onLaunchFromHyperSnap() {
        this.updateLanguage(); // Update in onLaunchFromHyperSnap.
    }
    updateLanguage() {
        readFile();
    }
}
```

## Enabling or Disabling Quick Start Through the Application-Side Cloud Push Switch

The cloud push switch is a mechanism that dynamically enables or disables specific application features through online cloud configuration.

With [setHyperSnapEnabled()](../reference/apis-ability-kit/js-apis-app-ability-hyperSnapManager.md#hypersnapmanagersethypersnapenabled), an application can disable the quick start feature as needed until the cloud push switch re-enables it.

Basic specifications of the cloud push switch:

* The setHyperSnapEnabled configuration value is disabled (false) by default.

* The configuration value set by setHyperSnapEnabled is persisted and remains effective after a device restart.

* Application updates and installations reset the value to the default.

Example of using the cloud push switch:

- After the application is installed, it actively pulls the cloud configuration on first startup and calls setHyperSnapEnabled(true) to apply the setting.

- The application monitors cloud configuration changes, and the cloud actively pushes new configurations (note: the logic for interacting with the cloud must be executed after the quick start point to avoid network interaction within the quick start point and to prevent quick start from skipping the execution of this business logic).

- When the cloud push obtains the settings, a copy of the configuration must also be saved locally in the application (for example, stored in a database).

- Within the quick start point, read the local configuration in AbilityStage.onCreate and call the API again.

With the preceding implementation, the application can continue to use the quick start feature after an update.

```TypeScript
export class LauncherAbility extends UIAbility {
    onCreate() {
        // ...
    }

    onConfigChange(key: string, value: string) {
        if (key == "enable_hyper_snap") {
            if (value == "true") {
                setHyperSnapEnabled(true);
            } else {
                setHyperSnapEnabled(false);
            }
        }
    }
}

export class AppAbilityStage extends AbilityStage {
    onCreate() {
        const hyperSnapConfig = this.readConfigFromDB();
        if (hyperSnapConfig === "true") {
            setHyperSnapEnabled(true);
        } else {
            setHyperSnapEnabled(false);
        }
    }

    readConfigFromDB() {
        // Read the setHyperSnapEnabled parameter from the database.
    }
}
```

## Actively Resetting the Quick Start Initialization Result by the Application

The system provides the [requestRebuildHyperSnap()](../reference/apis-ability-kit/js-apis-app-ability-hyperSnapManager.md#hypersnapmanagerrequestrebuildhypersnap) API, which allows the application to actively call it in its own business logic to clear the current quick start initialization result and re-perform quick start initialization when conditions are met.

```TypeScript
export class LauncherAbility extends UIAbility {
    onCreate() {
        // ...
        try {
            // ...
        } catch (error) {
            // ...
            requestRebuildHyperSnap(); // Regenerate the quick start initialization result when an error is reported based on the business logic.
            // ...
        }
    }
}
```

## Improving Quick Start Acceleration Benefits by Adjusting Business Logic

The more startup logic included in a quick start point, the more obvious the quick start benefits usually are. Developers can sort out and analyze the entire startup process, and move the startup logic suitable for inclusion in the quick start point (that is, logic that does not contain [quick start risky operations](#quick-start-risky-operations)) into the quick start point while ensuring the correctness of business logic, so as to expand the benefits of the application quick start technology in improving startup performance.

* **Move logic that is timing-independent and contains no quick start risky operations during startup into the quick start point**

  If there are tasks that can be moved earlier and have no timing dependencies, it is recommended to evaluate whether to place them in the quick start point to expand the benefits. At the same time, ensure that the tasks do not introduce quick start risky operations.

* **Move the logic of loading dependent libraries during startup into the quick start point**

  Moving import actions earlier has a limited applicable scope. The system recommends moving import actions during the cold startup process into the quick start initialization process as much as possible to expand the benefits. Use the [DevEco Profiler tuning tool](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-profiler) to scan for the keyword "Evaluate" to obtain the import actions during the startup process.

  It is not recommended to move import actions after startup into the startup process or even the quick start initialization process, otherwise the following problems may occur.

  (1) Degrade normal cold startup performance.

  (2) Cause unnecessary increase in resource usage during the startup process.

  It is recommended to use dynamic import to execute import actions in AbilityStage.onCreate.

  ```TypeScript
  export class AppAbilityStage extends AbilityStage {
    onCreate() {
      // ...
      this.preLoadKit();
      // ...
    }

    async preLoadKit() {
      await import('@ohos/common/src/..../1');
      await import('@ohos/common/src/..../2');
      // ...
      await import('@ohos/common/src/..../N');
    }
  }

  ```

<!--RP2--><!--RP2End-->