# Ability Kit Management Class Overview

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @ccllee1-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=9a0d9265a7a9000715929485766676ca3996041c translatedAt=2026-11-23T08:27:02.991Z pushedAt=2026-11-24T13:09:01.025Z nl=1 -->

Ability Kit (application framework service) provides multiple management class modules named with "Manager" and similar suffixes, targeting different functional domains such as application component runtime, application package management, startup acceleration, task management, cross-device migration, process management, permission and privacy, and intelligent agents. This document classifies these management class interfaces by functional hierarchy to help developers quickly locate the required capabilities and jump to the corresponding API reference.

## Application Component and Runtime Management

The interfaces in this class are used to query and manage the running status and process information of application components.

| Modules | Description |
| -------- | -------- |
| [abilityManager](../reference/apis-ability-kit/js-apis-app-ability-abilityManager.md) | Provides Ability information management functions, including obtaining the Ability running status, restarting atomic services, and determining device capability support. |
| [appManager](../reference/apis-ability-kit/js-apis-app-ability-appManager.md) | Provides application management capabilities, including querying whether the device is RAM-constrained, obtaining the maximum available memory, and obtaining running process information. |
| [errorManager](../reference/apis-ability-kit/js-apis-app-ability-errorManager.md) | Provides global observation capabilities for various exceptions during application runtime, supporting listening for application crashes (JS_CRASH), application freezes (APP_FREEZE), uncaught Promise exceptions, and resource usage exceeding preset baselines. |

## Application Package Management
 
The interfaces in this class are used to query application package information, and to manage default applications, desktop applications (Launcher), plugins, shortcuts, and so on.
 
| Modules | Description |
| -------- | -------- |
| [bundleManager](../reference/apis-ability-kit/js-apis-bundleManager.md) | Provides the query capability for application information, supporting information queries such as BundleInfo, ApplicationInfo, AbilityInfo, and ExtensionAbilityInfo. |
| [defaultAppManager](../reference/apis-ability-kit/js-apis-defaultAppManager.md) | Provides the capability to query default applications, supporting querying whether the current application is the default application. |
| [launcherBundleManager](../reference/apis-ability-kit/js-apis-launcherBundleManager.md) | Provides the query capability required by launcher applications (applications with icons on the desktop). |
| [pluginBundleManager](../reference/apis-ability-kit/js-apis-pluginBundleManager.md) | Provides the capability of managing self-distributed plugins for an application, including installing and uninstalling local plugins. |
| [shortcutManager](../reference/apis-ability-kit/js-apis-shortcutManager.md) | Provides application shortcut management capabilities, including setting whether a shortcut is displayed. |
|<!--DelRow-->[bundleMonitor](../reference/apis-ability-kit/js-apis-bundleMonitor-sys.md) (system interface) | Provides the capability to listen for application installation, uninstallation, and updates. |
|<!--DelRow-->[bundleResourceManager](../reference/apis-ability-kit/js-apis-bundleResourceManager-sys.md) (system interface) | Provides the application resource data query capability, supporting information queries such as BundleResourceInfo and LauncherAbilityResourceInfo. |
|<!--DelRow-->[distributedBundleManager](../reference/apis-ability-kit/js-apis-distributedBundleManager-sys.md) (system interface) | Provides the management capability for distributed applications. |

## Application Startup Management

The interfaces in this class are used to manage the application startup process, including startup framework task scheduling, application quick start, and auto-start on boot.

| Modules | Description |
| -------- | -------- |
| [startupManager](../reference/apis-ability-kit/js-apis-app-appstartup-startupManager.md) | Provides application startup framework management capabilities, supporting startup task dependency scheduling, parallel execution, so preloading, and task result management. |
| [hyperSnapManager](../reference/apis-ability-kit/js-apis-app-ability-hyperSnapManager.md) | Provides application quick start management capabilities, including enabling or disabling the quick start function and requesting re-initialization of quick start. |
| [autoStartupManager](../reference/apis-ability-kit/js-apis-app-ability-autoStartupManager.md) | Provides the capability to obtain the auto-start on boot status of the application itself and to check whether the device supports auto-start on boot. |

## Process and Context Management

The interfaces in this class are used to manage the creation and startup of child processes, as well as context transfer between ArkTS concurrent instances.

| Modules | Description |
| -------- | -------- |
| [childProcessManager](../reference/apis-ability-kit/js-apis-app-ability-childProcessManager.md) | Provides child process management capabilities, supporting child process creation and startup operations. The created child process exits along with the parent process. |
| [sendableContextManager](../reference/apis-ability-kit/js-apis-app-ability-sendableContextManager.md) | Provides the capability to convert between Context and SendableContext, used for data transfer between ArkTS concurrent instances (main thread, TaskPool worker thread, and Worker worker thread). |

## Ark Intelligent Development Framework

The interfaces in this class are used for on-device intelligent agent (Agent) management, Function invocation, CLI tool interaction, Skill query, and ArkTS script management, supporting the Ark intelligent development framework.

| Modules | Description |
| -------- | -------- |
|<!--DelRow-->[agentManager](../reference/apis-ability-kit/js-apis-app-agent-agentManager-sys.md) (system interface) | Provides Agent management capabilities, supporting connecting to and disconnecting from AgentExtensionAbility, managing the lifecycle, and obtaining AgentCard information. |
|<!--DelRow-->[functionManager](../reference/apis-ability-kit/js-apis-app-function-functionManager-sys.md) (system interface) | Provides Function management and invocation capabilities, allowing querying of available Function information and invoking a specified Function to execute business logic. |
|<!--DelRow-->[taskManager](../reference/apis-ability-kit/js-apis-app-agent-taskManager-sys.md) (system interface) | Provides task (Task) lifecycle management capabilities. A task is the attribution unit for user intent execution. During the task's lifetime, the system controls the processes attributed to the task according to task priority. |
| [skillManager](../reference/apis-ability-kit/js-apis-skillManager.md) | Provides the Skill information query capability, supporting querying the skill information of the application itself, a specified application, or all applications, used for AI agent task scheduling. |
| [cliManager](../reference/apis-ability-kit/js-apis-app-cli-cliManager.md) | Provides the interaction capability with system command-line tools (CLI), allowing querying of tool information, execution of CLI commands, and session management. |
| [scriptManager](../reference/apis-ability-kit/js-apis-app-ability-scriptManager.md) | Provides the management and organization capability for ArkTS script information, supporting the reporting of application ArkTS script execution results. |

<!--Del-->
## Task Management

The interfaces in this class are system interfaces that can be called only by system applications, and are used to manage tasks (Mission) within a device and across devices.

| Modules | Description |
| -------- | -------- |
| [missionManager](../reference/apis-ability-kit/js-apis-app-ability-missionManager-sys.md) (system interface) | Provides system task management capabilities, including operations such as locking, unlocking, cleaning, and switching tasks to the foreground. |
| [distributedMissionManager](../reference/apis-ability-kit/js-apis-distributedMissionManager-sys.md) (system interface) | Provides cross-device task management capabilities, including registering and unregistering task status listeners, synchronizing remote task lists, and migrating tasks by task ID and package name. |
<!--DelEnd-->

## Cross-Device Migration and Flow

The interfaces in this class are used for application continuation (cross-device migration) and flow/collaboration management.

| Modules | Description |
| -------- | -------- |
| [continueManager](../reference/apis-ability-kit/js-apis-app-ability-continueManager.md) | Provides the management capability for application cross-device migration, for example, obtaining the result of quickly launching the target application during application continuation. |

## Permission and Privacy Management

The interfaces in this class are used to manage the usage records of sensitive permissions, URI permission authorization, and sensitive data protection under lock screen.

| Modules | Description |
| -------- | -------- |
| [screenLockFileManager](../reference/apis-ability-kit/js-apis-screenLockFileManager.md) | Provides the sensitive data protection capability for applications under lock screen, supporting applying for and releasing sensitive data access permissions under lock screen and querying the sensitive data key status. |
|<!--DelRow-->[privacyManager](../reference/apis-ability-kit/js-apis-privacyManager-sys.md) (system interface) | Provides privacy management interfaces such as permission usage records, supporting recording, querying, listening for, and controlling the use of sensitive permissions. |
|<!--DelRow-->[uriPermissionManager](../reference/apis-ability-kit/js-apis-uripermissionmanager-sys.md) (system interface) | Provides URI permission management capabilities, used for authorizing/revoking URI permissions between applications, supporting secure sharing of file access permissions. |

## Other Capabilities

The interfaces in this class provide capabilities such as auto-fill, Kiosk mode, quick fix, vertical domain panel, and business routing.

| Modules | Description |
| -------- | -------- |
| [autoFillManager](../reference/apis-ability-kit/js-apis-app-ability-autoFillManager.md) | Provides the auto-fill capability for user information such as accounts, passwords, addresses, and phone numbers. |
| [kioskManager](../reference/apis-ability-kit/js-apis-app-ability-kioskManager.md) | Provides Kiosk mode management capabilities, including operations to enter or exit Kiosk mode. |
|<!--DelRow-->[quickFixManager](../reference/apis-ability-kit/js-apis-app-ability-quickFixManager-sys.md) (system interface) | Provides the quick fix capability, supporting defect repair through rapid patch delivery. |
|<!--DelRow-->[verticalPanelManager](../reference/apis-ability-kit/js-apis-app-ability-verticalpanelmanager-sys.md) (system interface) | Provides vertical domain panel management capabilities, currently supporting launching the vertical domain application panel selector. |
|<!--DelRow-->[businessAbilityRouter](../reference/apis-ability-kit/js-apis-businessAbilityRouter-sys.md) (system interface) | Provides the business routing capability, used to query the routing Ability information of applications installed on the device, supporting standardized business registration and jump control. |
