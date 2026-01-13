# ArkTS卡片适配常见问题
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @cx983299475-->
<!--Designer: @xueyulong-->
<!--Tester: @yangyuecheng-->
<!--Adviser: @HelloShuo-->

## ArkTS卡片开发是否支持V2装饰器？如何从V1迁移？
ArkTS卡片开发支持V2装饰器语法(如[\@ObservedV2](../ui/state-management/arkts-new-observedV2-and-trace.md)、[\@ComponentV2](../ui/state-management/arkts-create-custom-components.md#componentv2))，建议开发者使用V2装饰器替代V1语法进行状态管理，以获得更优的组件渲染性能和状态同步能力。
完整的语法差异对比、迁移步骤及示例代码，请参见官方文档: [V1->V2迁移指导概述](../ui/state-management/arkts-v1-v2-migration.md)。

## ArkTS卡片白屏如何定位？
ArkTS卡片白屏问题定位请参考[服务卡片显示问题定位指导](https://developer.huawei.com/consumer/cn/forum/topic/0202182083369423556)