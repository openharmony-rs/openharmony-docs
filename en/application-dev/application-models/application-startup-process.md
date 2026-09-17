# Application Startup Process

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @ccllee1-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=071dada0adacb196e25f2947f5b1d2e04d1f3ebe translatedAt=2026-08-31T12:32:00.530Z pushedAt=2026-08-31T13:50:10.555Z -->

## Overview

Application startup refers to the process in which a user triggers the system to launch an application through an entry point (such as an application icon or shortcut). In the application model, a typical application startup sequentially goes through three phases: **process startup**, **AbilityStage startup**, and **UIAbility startup**, during which the corresponding lifecycle callbacks are triggered. Understanding the relationships and timing among the three helps developers complete initialization, resource requests, and UI loading at the correct time.

- **Process startup**: A process is the basic unit for system resource allocation. For details, see Process Model Overview. When the first process of an application is created, it means the application has started. By default, all [UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md) components in an application (with the same bundle name) run in the same independent process (the main process). If the target process has not been created, the system first creates the application process and creates the main thread within the process to enter the message loop; if the process already exists (for example, in a warm startup scenario), the existing process is directly reused.

- **AbilityStage startup**: [AbilityStage](../reference/apis-ability-kit/js-apis-app-ability-abilityStage.md) is a [Module](../quick-start/application-package-overview.md#multi-module-design-mechanism)-level component manager. When the [HAP](../quick-start/hap-package.md) of an application is loaded for the first time, an AbilityStage instance is created, and each HAP corresponds to one AbilityStage instance. Before starting to load the first application component instance of the corresponding Module, the system first creates the AbilityStage and, after the creation is complete, executes its [onCreate()](../reference/apis-ability-kit/js-apis-app-ability-abilityStage.md#oncreate) lifecycle callback to notify developers that the Module can be initialized.

- **UIAbility startup**: The [UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md) component is an application component that contains a UI. A third-party application must contain at least one UIAbility component; otherwise, it has no interface to display to users. After a UIAbility instance is created, the system sequentially triggers the [onCreate()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#oncreate), [onWindowStageCreate()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onwindowstagecreate), and [onForeground()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onforeground) lifecycle callbacks to complete UI loading and display it in the foreground.

The relationship among the process, AbilityStage, and UIAbility lifecycles is shown in the following figure.


| Phase | Trigger Timing | Main Responsibilities |
| :--- | :--- | :--- |
| Process startup | When the first process of the application is created | Allocate system resources, create the main thread, and load the application runtime environment |
| AbilityStage startup | When the HAP is loaded for the first time and before the first application component instance is created | Module-level initialization, such as resource preloading, thread creation, and startup framework task execution |
| UIAbility startup | When a UIAbility instance is created and displayed | Instance-level initialization, UI loading, and foreground/background resource request and release |

## Recommendations for Using Callbacks in Startup Phases

### Module-Level Initialization (AbilityStage.onCreate)

As described in [Overview](#overview), the system first creates the AbilityStage and executes its [onCreate()](../reference/apis-ability-kit/js-apis-app-ability-abilityStage.md#oncreate) callback. This callback is triggered only once in the lifecycle of each HAP, making it suitable for placing Module-level initialization logic.

**Recommended in this callback:**

- Perform resource preloading for the Module, such as reading global configurations and warming up basic data.

- Register an [EnvironmentCallback](../reference/apis-ability-kit/js-apis-app-ability-environmentCallback.md) to listen for changes in system environment variables (language, light/dark mode, etc.).

- If the [application startup framework AppStartup](./app-startup.md) is enabled, startup tasks in automatic mode begin executing during the AbilityStage construction process, so developers do not need to invoke them manually here.

**Not recommended in this callback:**

- Execute business logic strongly tied to a specific UIAbility instance (this should be done in the UIAbility's [onCreate()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#oncreate)).

- Execute a large number of time-consuming synchronous operations that block the main thread. It is recommended to make time-consuming tasks asynchronous or handle them in a subthread.

### Specified Instance Mode Routing (AbilityStage.onAcceptWant)

When a [UIAbility specified instance mode (specified)](uiability-launch-type.md#specified) is started, the system triggers the [onAcceptWant()](../reference/apis-ability-kit/js-apis-app-ability-abilityStage.md#onacceptwant) callback of AbilityStage, and the developer returns an instance key to determine whether to reuse an existing UIAbility instance or create a new one.

**Recommended in this callback:**

- Determine the instance key that this startup should match based on fields such as `bundleName`, `abilityName`, and `parameters` in Want.

- Return a stable string key for instance routing, for example, generated based on business dimensions such as document ID or session ID.

**Not recommended in this callback:**

- Perform time-consuming business logic unrelated to instance matching.

- Return an empty value or null to ignore matching, which causes the system to create a new instance according to the default behavior, defeating the purpose of the specified mode.

### UIAbility Instance Initialization (UIAbility.onCreate)

This callback is triggered only once in the entire lifecycle of a UIAbility instance. Developers can execute startup logic that occurs only once in this callback.

**Recommended in this callback:**

- Read and parse the startup parameters [Want](../reference/apis-ability-kit/js-apis-app-ability-want.md) and [LaunchParam](../reference/apis-ability-kit/js-apis-app-ability-abilityConstant.md#launchparam), and route the business based on the startup reason (such as entry icon, deep linking, or inter-application navigation).

- Perform one-time initialization at the UIAbility instance level, such as global state initialization, permission pre-check, and listener registration.

**Not recommended in this callback:**

- Load and render the UI. UI loading should be completed in [onWindowStageCreate()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onwindowstagecreate) through [loadContent()](../reference/apis-arkui/arkts-apis-window-Window.md#loadcontent9).

- Request resources that are needed only when the UI is visible (such as location and camera). Such resources should be requested in [onForeground()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onforeground) and released in [onBackground()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onbackground).

- Execute time-consuming synchronous tasks that block the main thread and affect startup speed.

## Startup Entry

The startup entry of an application refers to the way a user enters the application (such as the application icon, shortcut, and so on). When different entries trigger UIAbility startup, the [Want](../reference/apis-ability-kit/js-apis-app-ability-want.md) parameters (such as `action`, `uri`, and `parameters`) passed by the system may differ. Developers can distinguish the source based on these parameters in `onCreate()` or `onNewWant()` of UIAbility and execute the corresponding logic.

An application can also be pulled up by other applications through [Want](./want-overview.md) or [application links](./app-uri-config.md), or be scheduled and started by the system through the [intent framework](./insight-intent-overview.md). For details about such cross-application startup scenarios, see [Cross-Application Navigation](./link-between-apps-overview.md).

### Application Icon (Desktop Icon)

The application icon is the most common entry point for application startup, typically displayed on the system desktop. When the user taps the desktop icon, the system initiates startup based on the entry UIAbility declared in the [module.json5 configuration file](../quick-start/module-configuration-file.md) (usually the UIAbility corresponding to `startWindowIcon` and `label` in the entry-type HAP).

### Shortcut

A shortcut is a quick menu item that appears when you press and hold an application icon, allowing users to directly jump to a specific feature page of the application. Developers can declare static shortcuts in the `shortcuts` tag of the [module.json5 configuration file](../quick-start/module-configuration-file.md#shortcuts), or dynamically publish shortcuts through the [shortcutManager](../reference/apis-ability-kit/js-apis-shortcutManager.md) API.

- After a user taps a shortcut, the system starts the corresponding UIAbility with a Want carrying specific `parameters` or `uri`.

- Developers can parse the Want parameters in `onCreate()` or `onNewWant()` of the UIAbility to directly load the target feature page, reducing the user operation hierarchy.

<!--RP1--><!--RP1End-->