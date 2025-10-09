# Introduction to Ability Kit

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @ccllee1-->
<!--Designer: @ccllee1-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

Ability Kit provides an application model for application development and running. The application model is the abstraction of capabilities required by an application. It provides components and mechanisms required for running the application. You can develop applications based on a unified set of models, which makes your development simpler and more efficient.

## Use Scenarios

- Multi-module development: You can use different types of modules (HAP, HAR, and HSP) to develop an application. The HAP is used to implement application features, and the HAR and HSP are used to share code and resources.
- Intra-application interaction: Redirection is allowed between components of an application. For example, in a mobile office application, you may need to start a video meeting UIAbility from the entry UIAbility.
- Inter-application interaction: An application can start another application to complete a task or operation. For example, when making a purchase in an e-commerce application, you can be redirected to a payment application to complete the transaction.
- Cross-device hopping: Your application delivers a better user experience through cross-device migration and multi-device collaboration. For example, you migrate a video playback task from a tablet to a smart TV.

## Capability Scope

- Provides APIs to create or destroy an application process, and schedule the application lifecycle.
- Provides an entry to run application components, schedule the application component lifecycle, and enable interaction between components.
- Provides APIs to listen for application context changes, system environment changes, and component lifecycle changes.
- Provides the capabilities of AppStartup. For details, see [AppStartup](./app-startup.md).
- Provides the capabilities of the InsightIntent framework. For details, see [InsightIntent Framework Overview](./insight-intent-overview.md).
- Provides APIs to continue an application on another device.
- Provides capabilities such as multi-package, shared package, and application information configuration. For details, see [Application Package Overview](../quick-start/application-package-overview.md).
- Provides APIs related to shortcuts. For details, see [Shortcuts](../quick-start/typical-scenario-configuration.md).
- Provides access control capabilities. For details, see [Access Control Overview](../security/AccessToken/access-token-overview.md).
<!--RP1-->
<!--RP1End-->

## Highlights

1. **Separation of UI and service logic**
   This architecture enforces a development paradigm where service logic and UI interactions are clearly separated.
   - From service logic to UI: Developers implement core service logic within the ability. Data is then passed to the UI framework through binding mechanisms. Based on declarative syntax, ArkUI automatically renders the view and triggers UI updates when the state changes.
   - From UI to service logic: User inputs captured from UI interactions are synchronized back to the ability framework through event callbacks or state binding mechanisms, reflecting the user's actions in the service logic layer.

2. **Support for cross-device migration and multi-device collaboration at the application component level**

   The [stage model](ability-terminology.md#stage-model) decouples application components from UI.
   - The declarative feature of ArkUI allows the UI to be restored based on the data or status saved in application components, which facilitates cross-device migration.
   - Application components support cross-device interaction over Remote Procedure Calls (RPCs).

3. **Support for multiple device types and window forms**

   Application component management and window management are decoupled at the architecture level. This decoupling makes it easy to:
   - Tailor application components. For example, windows can be tailored for devices without screens.
   - Extend the window forms.
   - Use the same application component lifecycle on multiple devices (such as desktop devices and mobile devices).

4. **Well balanced application capabilities and system management costs**

   The stage model redefines the boundary of application capabilities to well balance application capabilities and system management costs.
   - Diverse application components (such as service widgets and input methods) for specific scenarios.
   - Standardized background process management. To deliver a better user experience, the stage model manages background application processes in a more orderly manner. Applications cannot reside in the background randomly, and their background behavior is strictly managed to minimize malicious behavior.

## Relationship with Related Kits

ArkUI: The UIAbility component of Ability Kit can use the components, events, animations, and status management capabilities provided by ArkUI.

ArkTS: provides language runtime capabilities for Ability Kit.

## Emulator Support

This kit supports development using the Emulator. However, there are some functional differences compared to real devices, as detailed below:

- Launching vertical application panels is not supported.
- Launching atomic services in installation-free mode is not supported.
- Using App Linking for cross-application redirection is not supported.
- Using Deep Linking to trigger the application selection dialog box is not supported. Since the Emulator lacks an application selection dialog box, when multiple applications match a Deep Link, the dialog box cannot be displayed.
