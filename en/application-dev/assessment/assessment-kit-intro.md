# Introduction to Automatic Scene Configuration Kit

<!--Kit: Automatic Scene Configuration Kit-->
<!--Subsystem: Customization-->
<!--Owner: @weredust-->
<!--Designer: @weredust-->
<!--Tester: @weredust-->
<!--Adviser: @weredust-->
<!-- md-trans-meta sourceCommit=3194fdbc42d6357f420eb498f6d963c04a35b419 translatedAt=2026-11-06T12:37:54.319Z pushedAt=2026-11-09T12:10:24.305Z nl=1 -->

Starting from API version 26.1.0, Automatic Scene Configuration Kit (Scene Configuration Service) provides applications with scenario-based system capability configuration and control. The system implements the configuration and control on the system side, so applications do not need to implement interception logic themselves, nor can they bypass or remove the restrictions on their own. This Kit currently delivers the preceding capabilities through the Assessment Management (assessment) module, targeting business scenarios such as online exams and training assessments that require process fairness. The entire control process requires user confirmation or can be perceived by the user.

## Use Scenarios

- Formal online exams: In formal exam scenarios such as academic proficiency tests and admission exams, restrict some system capabilities of the device during the answering period to prevent cheating and question leakage.
- Professional certification and standardized tests: In standardized test scenarios such as professional qualification certification and language proficiency tests, provide all examinees with a consistent restricted answering environment to ensure score comparability.
- Training assessments: In scenarios such as corporate training and course completion assessments, restrict the running of applications unrelated to the assessment to help participants focus on completing the assessment.

## Capability Scope

- Assessment Management: Provides system capability control such as starting and ending an assessment scenario, querying assessment status and obtaining assessment configuration, callbacks for assessment process events, and notification restrictions during the assessment. For development details, see [Assessment Management Development Guide](assessment-guide.md). For API details, see [@ohos.customization.assessment (Assessment Management)](../reference/apis-assessment-kit/js-apis-customization-assessment.md).

## Highlights

- **Unified system-side control**: System capability restrictions within a scenario are uniformly implemented by the system on the system side, independent of the application's own implementation. Applications cannot bypass them, nor can they remove them on their own.
- **The entire control process requires user confirmation or can be perceived by the user**: Before control takes effect, the system displays a confirmation dialog to obtain user consent. If the user cancels, the control does not take effect. After the control is removed, the device returns to its normal state.
- **Control status and interruption reasons can be perceived through callbacks**: Applications obtain scenario start, interruption, and end events through callbacks. Interruption events carry a reason code and description information.

## Constraints

- The capabilities of this Kit can be used only under the Stage model.
- Supported devices: Phone | PC/2in1 | Tablet.
- Calling the capabilities of this Kit requires applying for restricted permissions. For permission information, approval rules, and module-level specifications, see [Assessment Management Development Guide](assessment-guide.md#constraints-and-limitations).

## Relationship with Related Kits

- [Ability Kit](../application-models/abilitykit-overview.md): This Kit depends on the application model and context capabilities provided by Ability Kit. It supports only Stage model applications, and scene configuration requests must be initiated by applications with UIAbility context.
- [Notification Kit](../notification/notification-overview.md): During scene control, notifications are restricted, including no ringtone, vibration, or banners. These restrictions are enforced uniformly by the system, and this Kit does not separately provide notification-related APIs.

## Relationship with Development Guides

This document describes what Automatic Scene Configuration Kit is, the modules it provides, and the kit-level constraints. The [Assessment Management Development Guide](assessment-guide.md) explains how to use the Assessment Management module, including module-level constraints and limitations, the development process, API descriptions, sample code, debugging and verification, and FAQs. The [Automatic Scene Configuration Kit Glossary](assessment-glossary.md) unifies the terminology used across this document set. For API signatures and error codes, see [@ohos.customization.assessment (Assessment Management)](../reference/apis-assessment-kit/js-apis-customization-assessment.md) and [Assessment Management Error Codes](../reference/apis-assessment-kit/errorcode-assessment.md) under `../reference/apis-assessment-kit/`.
