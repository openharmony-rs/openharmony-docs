# ArkTS Widget Adaptation FAQs
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @cx983299475-->
<!--Designer: @xueyulong-->
<!--Tester: @yangyuecheng-->
<!--Adviser: @HelloShuo-->

## Does ArkTS widget development support V2 decorators? How do I migrate from V1 to V2?
ArkTS widget development supports the V2 decorator syntax (such as [\@ObservedV2](../ui/state-management/arkts-new-observedV2-and-trace.md) and [\@ComponentV2](../ui/state-management/arkts-create-custom-components.md#componentv2)). You are advised to use V2 decorators to replace the V1 syntax for state management, so as to achieve better component rendering performance and state synchronization capabilities.
For details about the syntax differences, migration procedure, and sample code, see [V1 to V2 Migration Overview](../ui/state-management/arkts-v1-v2-migration.md).
