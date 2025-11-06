# 数据对象状态变量的迁移指导
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiyujia926-->
<!--Designer: @s10021109-->
<!--Tester: @TerryTsao-->
<!--Adviser: @Brilliantry_Rui-->

本文档主要介绍数据对象内的状态变量的迁移场景，包含以下场景。
| V1装饰器名                | V2装饰器名                  |
|------------------------|--------------------------|
|[\@ObjectLink](./arkts-observed-and-objectlink.md)/[\@Observed](./arkts-observed-and-objectlink.md) /[\@Track](./arkts-track.md)|[\@ObservedV2](./arkts-new-observedV2-and-trace.md)/[\@Trace](./arkts-new-observedV2-and-trace.md)|

## 各装饰器迁移示例

### \@ObjectLink/\@Observed/\@Track -> \@ObservedV2/\@Trace
**迁移规则**

在V1中，\@Observed与\@ObjectLink装饰器用于观察类对象及其嵌套属性的变化，但V1只能观察对象的第一层属性。嵌套对象的属性需要通过自定义组件和\@ObjectLink观察。此外，V1中提供了\@Track装饰器实现对属性级别变化的精确控制。

在V2中，结合使用\@ObservedV2和\@Trace，可以高效实现类对象及其嵌套属性的深度观察，省去对自定义组件的依赖，简化开发流程。同时，\@Trace装饰器具备精确更新能力，替代V1中的\@Track，实现更高效的UI刷新控制。根据不同场景，有以下迁移策略：

- 嵌套对象的属性观察：V1中需要通过自定义组件和\@ObjectLink观察嵌套属性，V2中则可以使用\@ObservedV2和\@Trace直接观察嵌套对象，简化了代码结构。
- 类属性的精确更新：V1中的\@Track可以用V2中的\@Trace取代，\@Trace可以同时观察和精确更新属性变化，使代码更简洁高效。

**示例**

**嵌套对象属性观察方法**

在V1中，无法直接观察嵌套对象的属性变化，只能观察到第一层属性的变化。必须通过创建自定义组件并使用\@ObjectLink来实现对嵌套属性的观察。V2中使用\@ObservedV2和\@Trace，可以直接对嵌套对象的属性进行深度观察，减少复杂度。

V1实现：
<!-- @[Migration_Nested_Object_Properties_V1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/migrationDataObjectVariables/MigrationNestedObjectPropertiesV1.ets) -->

V2迁移策略：使用\@ObservedV2和\@Trace。
<!-- @[Migration_Nested_Object_Properties_V2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/migrationDataObjectVariables/MigrationNestedObjectPropertiesV2.ets) -->

**类属性变化观测**

在V1中，\@Observed用于观察类实例及其属性的变化，\@Track用于类对象的属性级的观察。在V2中，\@Trace实现了观察和更新属性级别变化的能力，搭配\@ObservedV2实现高效的UI更新。

V1实现：
<!-- @[Migration_Class_Attribute_V1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/migrationDataObjectVariables/MigrationClassAttributeV1.ets) -->

V2迁移策略：使用\@ObservedV2和\@Trace。
<!-- @[Migration_Class_Attribute_V2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/migrationDataObjectVariables/MigrationClassAttributeV2.ets) -->

