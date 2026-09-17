# Ability Kit<!--ability-kit-->

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @jayleehw-->
<!--Designer: @jayleehw-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=c6807ccd3e6322f13c08345e517071d1cd3c3fa5 translatedAt=2026-09-09T02:58:17.726Z pushedAt=2026-09-09T03:11:34.926Z -->


- [About This Kit](abilitykit-overview.md)
- Application Models<!--application-models-->
  - [Application Model Overview](stage-model-development-overview.md)
  - Application Components<!--stage-model-application-components-->
    - [Application- or Component-Level Configuration](application-component-configuration-stage.md)
    - UIAbility Component<!--uiability-->
      - [UIAbility Overview](uiability-overview.md)
      - [UIAbility Lifecycle](uiability-lifecycle.md)
      - [UIAbility Launch Type](uiability-launch-type.md)
      - [UIAbility Usage](uiability-usage.md)
      - [Data Synchronization Between UIAbility and UI Page](uiability-data-sync-with-ui.md)
      - [Starting UIAbility Within the Same Application](uiability-intra-device-interaction.md)
      - [Multi-device Collaboration Through Call Invocation](uiability-cross-device-interaction.md)
      - [UIAbility Backup and Restore](ability-recover-guideline.md)
    - [ExtensionAbility Component](extensionability-overview.md)
      <!--Del-->
      - [Using the Agent Service Provided by the AgentExtensionAbility Component (Available Only to System Applications)](agent-manager-sys.md)
      - [ServiceExtensionAbility (for System Applications Only)](serviceextensionability-sys.md)
      - [UIServiceExtensionAbility (for System Applications Only)](uiserviceextension-sys.md)
      - [UIExtensionAbility (for System Applications Only)](uiextensionability-sys.md)
      - [Using AutoFillExtensionAbility for Auto-Fill (for System Applications Only)](autofillextensionability-guide-sys.md)
      - [Using UIServiceExtensionAbility for System Floating Windows](uiserviceextension.md)
      <!--DelEnd-->
      - [EmbeddedUIExtensionAbility](embeddeduiextensionability.md)
      - [Using AppServiceExtensionAbility for Background Services](app-service-extension-ability.md)
    - [AbilityStage Component Manager](abilitystage.md)
    - [Context](application-context-stage.md)
    - Want<!--want-->
      - [Want Overview](want-overview.md)
      - [Matching Rules of Explicit Want and Implicit Want](explicit-implicit-want-mappings.md)
      - [Using Explicit Want to Start an Application Component](ability-startup-with-explicit-want.md)
      - [Common action and entities Values (Not Recommended)](actions-entities.md)
    - [Component Startup Rules](component-startup-rules.md)
    - [Obtaining/Setting Environment Variables](subscribe-system-environment-variable-changes.md)
    <!--Del-->
    - Inter-Device Application Component Interaction (Hopping)<!--hop-->
      - [Hopping Overview](inter-device-interaction-hop-overview.md)
      - [Cross-Device Migration](hop-cross-device-migration.md)
      - [Multi-device Collaboration](hop-multi-device-collaboration.md)
    <!--DelEnd-->  
  - Process Model<!--process-model-stage-->
    - [Process Model Overview](process-model-overview.md)
    - Extended Process Development Guide<!--extended-process-development-->
      - [Child Process Development Guide (ArkTS)](arkts-child-process-development-guideline.md)
      - [Child Process Development Guide (C/C++)](capi-nativechildprocess-development-guideline.md)
    - [Isolation Process Development Guide](isolation-process-development-guideline.md)
  - [Thread Model](thread-model-stage.md)
  <!--Del-->
  - Mission Management (available only to system applications)<!--mission-management-->
    - [Mission Management Scenario Overview (available only to system applications)](mission-management-overview-sys.md)
    - [Mission and Launch Type (available only to system applications)](mission-management-launch-type-sys.md)
    - [Page Stack and Mission Chain (available only to system applications)](page-mission-stack-sys.md)
    - [Setting the Icon and Name of a Task Snapshot (available only to system applications)](mission-set-icon-name-for-task-snapshot-sys.md)
  <!--DelEnd-->
  - [Application Configuration File](config-file-stage.md)
- Application Lifecycle<!--app-lifecycle-->
  - [Application Lifecycle Overview](application-lifecycle.md)
  - Application Startup<!--app-start-->
    - [Application Startup Process](application-startup-process.md)
    - [Application Startup Settings](application-startup-options.md)
    - [Application Startup Framework AppStartup](app-startup.md)
    - [Application Preloading](preload-application.md)
    - [Application Quick Startup](hyperstartup-application.md)
  - [Application Exit](app-stop.md)<!--RP2--><!--RP2End-->
  - [Application Restart](app-restart.md)
  - [Obtaining the Cause of Abnormal Application Exit](ability-exit-info-record.md)
- Application Redirection<!--inter-app-redirection-->
  - [Application Redirection Overview](link-between-apps-overview.md)
  - Launch the Specified Application<!--directional-redirection-->
    - [Launch the Specified Application Overview](app-startup-overview.md)
    - [(Optional) Using canOpenLink to Check Whether an Application Is Accessible](canopenlink.md)
    - [Obtaining the URL Information of the Target Application](obtaining-target-app-url-info.md)
    - [Using Deep Linking for Application Redirection](deep-linking-startup.md)
    - [Using App Linking for Application Redirection](app-linking-startup.md)
    - [Explicit Want Redirection to App Linking Redirection Adaptation Guide](uiability-startup-adjust.md)
    - [Application Link Description](app-uri-config.md)
  - Launch the specified type of applications<!--specified-type-app-redirection-->
    - [Overview of Launching the Specified Type of Applications](start-intent-panel.md)
    - [Launching Navigation Applications (startAbilityByType)](start-navigation-apps.md)
    - [Launching Email Applications (startAbilityByType)](start-email-apps.md)
    - [Launching Email Applications (mailto)](start-email-apps-by-mailto.md)
    - [Launching Finance Applications (startAbilityByType)](start-finance-apps.md)
    - [Launching Flight Applications (startAbilityByType)](start-flight-apps.md)
    - [Launching Express Delivery Applications (startAbilityByType)](start-express-apps.md)
    - [Launching Image Editing Applications (startAbilityByType)](photoEditorExtensionAbility.md)
    - [Launch File-Processing Applications (startAbility)](file-processing-apps-startup.md)
  - [Launch System Applications](system-app-startup.md)<!--RP1--><!--RP1End-->
- Ark Intelligent Development Framework Development Guide<!--ark-agentic-framework-->
  - [Ark Intelligent Development Framework Overview](arkaf-overview.md)
  - InsightIntent Framework Development<!--insight-intent-->
    - [InsightIntent Framework Overview](insight-intent-overview.md)
    - Intent Development<!--insight-intent-development-->
      - [Intent Development Overview](insight-intent-definition.md)
      - [Developing Intents Using Configuration Files](insight-intent-config-development.md)
      - [Developing Intents Using Decorators](insight-intent-decorator-development.md)
      - [Appendix: Standard Intent Access Specifications](insight-intent-access-specifications.md)
    - [Debugging Intents](insight-intent-debug.md)
  - [Application Skill Development Guide Based on ArkTS Scripts](arkts-skill-development-guide.md)
  - On-Device A2A Framework Development Guide<!--agent-guideline-->
    - [On-Device A2A Framework Overview](agent-overview.md)
    - Develop On-Device Agents<!--agent-development-->
      - [Implement Agent Services Using the AgentExtensionAbility Component](agent-extension-ability.md)
      - [AgentExtensionAbility Configuration File Description](agent-extension-configuration.md)
      <!--Del-->
      - [Using the Agent Service Provided by the AgentExtensionAbility Component (available only to system applications)](agent-manager-sys.md)
      <!--DelEnd-->
- Modular Object Development Guide Based on ModularObjectExtensionAbility (C/C++)<!--modular-object-extension-ability-->
  - [Modular Object Model Overview (C/C++)](modular-object-extension-overview.md)
  - [Using ModularObjectExtensionAbility to Implement Modular Objects (C/C++)](modular-object-extension-development.md)
  - [Using Taihe to Implement IPC Communication for ModularObjectExtensionAbility (C/C++)](modular-object-extension-ability-taihe.md)
  - [Using ModularObjectDispatcher to Implement Dynamic Interface Invocation (C/C++)](modular-object-dispatcher-development.md)
- [Ability Kit Terminology](ability-terminology.md)