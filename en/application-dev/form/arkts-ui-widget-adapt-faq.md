# ArkTS Widget Adaptation FAQs
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @Qian-Win-->
<!--Designer: @cx983299475-->
<!--Tester: @mahailong123456-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=25ffb887f2919e16c03fcbf1b003b994b365d387 translatedAt=2026-08-26T04:43:24.528Z pushedAt=2026-08-28T08:20:16.850Z -->

## Using V2 Decorators for State Management in ArkTS Widgets

ArkTS widget development supports the V2 decorator syntax (such as [\@ObservedV2](../ui/state-management/arkts-new-observedV2-and-trace.md) and [\@ComponentV2](../ui/state-management/arkts-create-custom-components.md#componentv2)). You are advised to use V2 decorators to replace the V1 syntax for state management, so as to achieve better component rendering performance and state synchronization capabilities.

For details about the syntax differences, migration procedure, and sample code, see [V1 to V2 Migration Overview](../ui/state-management/arkts-v1-v2-migration.md).

<!--RP1--><!--RP1End-->

## Adapting ArkTS Widgets to Dark Mode
The system offers dark and light modes. ArkTS widgets should adapt to both modes to enhance visual consistency between widgets and pages, delivering a better user experience. For details, see [Implementing Dark and Light Mode Adaptation](../ui/ui-dark-light-color-adaptation.md).

## App Crash Caused by Importing particleAbility, audio, camera, media, or backgroundTaskManager Modules

### Symptom
After importing `particleAbility`, `audio`, `camera`, `media`, or `backgroundTaskManager`, the app crashes, and the `FaultLog` points to the relevant call line.<br>
![Screenshot of the crash code line](figures/CrashCode.png)<br>
The code line corresponding to the error is as follows:<br>
![Screenshot of the crash error message](figures/CrashInfo.png)

### Possible Causes
The `FormExtensionAbility` of ArkTS widgets does not support loading the above modules. For details, see [@ohos.app.form.FormExtensionAbility](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md). Forcibly loading these modules results in an `undefined` object, which causes a JS crash when used.

### Solution
Check the import chain of `FormExtensionAbility`, and separate the files that involve the above modules from the files used by the ArkTS widget to prevent them from being loaded by `FormExtensionAbility`.

