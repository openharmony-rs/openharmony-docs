# Ability Kit<!--ability-kit-->

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @jayleehw-->
<!--Designer: @jayleehw-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=f513c81199f72302f41dc822fad2997ee23361fd translatedAt=2026-11-02T13:26:41.174Z pushedAt=2026-11-03T04:24:22.521Z nl=1 -->


- [About This Kit](abilitykit-overview.md)
- Application Model<!--application-models-->
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
      - [Multi-Device Collaboration Through Call](uiability-cross-device-interaction.md)
      - [UIAbility Backup and Restore](ability-recover-guideline.md)
    - [ExtensionAbility Component](extensionability-overview.md)
      <!--Del-->
      - [Agent Service Provided by the AgentExtensionAbility Component (System Applications Only)](agent-manager-sys.md)
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
    - Component Startup Rules<!--component-startup-rules-->
      - [Intra-Device Component Startup Rules](component-startup-rules-inner-device.md)
      <!--Del-->
      - [Intra-Device Component Startup Rules (System Applications Only)](component-startup-rules-inner-device-sys.md)
      <!--DelEnd-->
      - [Cross-Device Component Startup Rules](component-startup-rules-cross-device.md)
      <!--Del-->
      - [Cross-Device Component Startup Rules (System Applications Only)](component-startup-rules-cross-device-sys.md)
      <!--DelEnd-->
> ⚠️ [翻译失败]此段需用户自行翻译
    <!--Del-->
    - Inter-Device Application Component Interaction (Hopping)<!--hop-->
      - [Hopping Overview](inter-device-interaction-hop-overview.md)
      - [Cross-Device Migration](hop-cross-device-migration.md)
      - [Multi-device Collaboration](hop-multi-device-collaboration.md)
    <!--DelEnd-->  
> ⚠️ [翻译失败]此段需用户自行翻译
    - [Process Model Overview](process-model-overview.md)
    - Extension process development guide<!--extended-process-development-->
      - [Child process development guide (ArkTS)](arkts-child-process-development-guideline.md)
      - [Child Process Development Guide (C/C++)](capi-nativechildprocess-development-guideline.md)
    - [Isolation Process Development Guide](isolation-process-development-guideline.md)
  - [Thread Model](thread-model-stage.md)
  <!--Del-->
  - Mission Management (system-only) <!--mission-management-->
    - [Mission Management Scenario Introduction (system-only)](mission-management-overview-sys.md)
    - [Task (Mission) and Launch Mode (system-only)](mission-management-launch-type-sys.md)
    - [Page Stack and Task Chain (system-only)](page-mission-stack-sys.md)
    - [Set Icon and Name for Task Snapshot (system-only)](mission-set-icon-name-for-task-snapshot-sys.md)
  <!--DelEnd-->
  - [App Configuration File](config-file-stage.md)
- App Lifecycle<!--app-lifecycle-->
  - [App Lifecycle Overview](application-lifecycle.md)
  - App Startup<!--app-start-->
    - [App Startup Process](application-startup-process.md)
    - [App Startup Settings](application-startup-options.md)
    - [App Startup Framework AppStartup](app-startup.md)
    - [App Preloading](preload-application.md)
    - [App Quick Startup](hyperstartup-application.md)
  - [App Exit](app-stop.md)<!--RP2--><!--RP2End-->
  - [App Restart](app-restart.md)
  - [Obtaining the Cause of Abnormal App Exit](ability-exit-info-record.md)
- Cross-App Navigation<!--inter-app-redirection-->
  - [Cross-App Navigation Overview](link-between-apps-overview.md)
  - Launching a Specified App<!--directional-redirection-->
    - [Launching a Specified App Overview](app-startup-overview.md)
    - [(Optional) Using canOpenLink to Determine Whether an App Is Accessible](canopenlink.md)
    - [Obtain URL Information of the Target App](obtaining-target-app-url-info.md)
    - [Use Deep Linking to Implement App-to-App Redirection](deep-linking-startup.md)
    - [Use App Linking to Implement App-to-App Redirection](app-linking-startup.md)
    - [Adaptation Guide for Switching from Explicit Want Redirection to App Linking Redirection](uiability-startup-adjust.md)
    - [App Linking Description](app-uri-config.md)
  - Launch a specified type of app<!--specified-type-app-redirection-->
    - [Overview of Launching a Specified Type of App](start-intent-panel.md)
    - [Launch a Navigation Type of App (startAbilityByType)](start-navigation-apps.md)
    - [Launch an Email Type of App (startAbilityByType)](start-email-apps.md)
    - [Launch an Email Type of App (mailto)](start-email-apps-by-mailto.md)
    - [Launching Finance Apps (startAbilityByType)](start-finance-apps.md)
    - [Launching Flight Apps (startAbilityByType)](start-flight-apps.md)
    - [Launching Express Apps (startAbilityByType)](start-express-apps.md)
    - [Launching Image Editing Apps (startAbilityByType)](photoEditorExtensionAbility.md)
    - [Launching File Processing Apps (startAbility)](file-processing-apps-startup.md)
  - [Launching System Apps](system-app-startup.md)<!--RP1--><!--RP1End-->
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
    - Developing On-Device Agents<!--agent-development-->
      - [Using the AgentExtensionAbility Component to Implement Agent Services](agent-extension-ability.md)
      - [AgentExtensionAbility Configuration File Description](agent-extension-configuration.md)
      <!--Del-->
      - [Using Agent Services Provided by the AgentExtensionAbility Component (System-Only)](agent-manager-sys.md)
      <!--DelEnd-->
- Modular Object Development Guide Based on ModularObjectExtensionAbility (C/C++)<!--modular-object-extension-ability-->
  - [Modular Object Model Overview (C/C++)](modular-object-extension-overview.md)
  - [Using ModularObjectExtensionAbility to Implement Modular Objects (C/C++)](modular-object-extension-development.md)
  - [Using Taihe to Implement IPC Communication for ModularObjectExtensionAbility (C/C++)](modular-object-extension-ability-taihe.md)
  - [Using ModularObjectDispatcher to Implement Dynamic Interface Invocation (C/C++)](modular-object-dispatcher-development.md)
- [Ability Kit Terminology](ability-terminology.md)