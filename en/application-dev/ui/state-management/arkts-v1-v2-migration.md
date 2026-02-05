# V1 to V2 Migration Overview
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @katabanga-->
<!--Designer: @s10021109-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

## Overview
ArkUI state management automatically synchronizes the changes of observable data to the UI, implementing data-driven UI refresh. This allows developers to focus on UI design and implementation.

During the evolution of the state management framework, state management V1 and V2 are released. V1 emphasizes state management of the components, while V2 enhances the in-depth observation and management of data objects. With V2, you can control data and state more flexibly, facilitating a more efficient UI re-render. For details about the differences between V1 and V2, see [State Management Overview](./arkts-state-management-overview.md).

## How to Use
1. V2 represents an enhanced iteration of V1, offering expanded functionality and increased flexibility through ongoing optimization.
2. For new applications, you are advised to use the V2 paradigm for development.
3. For applications that have used V1, if the functions and performance of V1 can meet requirements, you do not need to switch to V2 immediately.
4. For details about the mixed use of V1 and V2, see [Mixing Use of Custom Components](./arkts-custom-component-mixed-scenarios.md). The compiler, toolchain, and DevEco Studio verify some misuse and mixed use scenarios that are not recommended. Although developers can bypass these verifications using special methods, it is strongly recommended that developers follow the instructions in [Mixing Use of Custom Components](./arkts-custom-component-mixed-scenarios.md). Avoid uncertainties caused by problems such as dual agents.

## Purpose
1. Provide systematic templates and guidance for developers who want to migrate their applications from V1 to V2.
2. This document provides reference for developers who want to gradually migrate applications from V1 to V2. This document and [Mixing Use of Custom Components](./arkts-custom-component-mixed-scenarios.md) help developers implement gradual reconstruction.
3. Developers who have not started to develop applications but are familiar with the V1 status management rules can refer to this migration document and V2 documents to start using V2 for development.

## Capability Comparison and Migration Between V1 and V2
| V1 Decorator Name/Scenario               | V2 Decorator Name/API                 | Description|
|------------------------|--------------------------|--------------------------|
| [\@Observed](./arkts-observed-and-objectlink.md)              | [\@ObservedV2](./arkts-new-observedV2-and-trace.md)              | Both mark an object as observable, but with key differences:<br>\@Observed is used to observe the top-level properties and requires [\@ObjectLink](./arkts-observed-and-objectlink.md) to take effect.<br>\@ObservedV2 does not have the observation capability. It only marks a class as observable. To observe the class properties, use it together with \@Trace. For details, see [\@ObjectLink/\@Observed/\@Track -> \@ObservedV2/\@Trace](./arkts-v1-v2-migration-inner-class.md#objectlinkobservedtrack---observedv2trace). |
| [\@Track](./arkts-track.md)                 | [\@Trace](./arkts-new-observedV2-and-trace.md)               | \@Track is used for accurate observation. If it is not used, class properties cannot be accurately observed.<br>\@Trace decorated properties can be accurately traced and observed. For details, see [\@ObjectLink/\@Observed/\@Track -> \@ObservedV2/\@Trace](./arkts-v1-v2-migration-inner-class.md#objectlinkobservedtrack---observedv2trace).|
| [\@Component](./arkts-create-custom-components.md#component)             | [\@ComponentV2](./arkts-create-custom-components.md#componentv2)             | \@Component is the decorator for custom components in V1.<br>@ComponentV2 is the custom component decorator used with the state variables of V2.|
|[\@State](./arkts-state.md)                 | No external initialization: [\@Local](./arkts-new-local.md)<br>One-time external initialization: [\@Param](./arkts-new-param.md) + [\@Once](./arkts-new-once.md)| Similar to \@Local, \@State decorated variables can work as the data source which can be directly migrated without external initialization. If the initialization needs to be transferred from an external system, it can be migrated to \@Param\@Once. For details, see [\@State->\@Local](./arkts-v1-v2-migration-inner-component.md#state-local). If [WaterFlowSections](../../reference/apis-arkui/arkui-ts/ts-container-waterflow.md#waterflowoptions) or [ChildrenMainSize](../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#childrenmainsize12) associated with the scrollable component is used, [makeObserved](./arkts-new-makeObserved.md) must be used. For details, see [Scroll Components](./arkts-v1-v2-migration-application-and-others.md#scroll-components).|
| [\@Prop](./arkts-prop.md)                  | [\@Param](./arkts-new-param.md)                   | \@Prop and \@Param both represent parameters for custom components. For complex input types, \@Prop uses deep copying, while \@Param uses references. For details, see [\@Prop -> \@Param](./arkts-v1-v2-migration-inner-component.md#prop---param).|
| [\@Link](./arkts-link.md)                  | [\@Param](./arkts-new-param.md)[\@Event](./arkts-new-event.md)    | \@Link is a bidirectional synchronization encapsulated by the framework. V2 developers can use @Param and @Event to implement bidirectional synchronization. For details, see [\@Link -> \@Param/\@Event](./arkts-v1-v2-migration-inner-component.md#link---paramevent).|
| [\@ObjectLink](./arkts-observed-and-objectlink.md)           | [\@ObservedV2](./arkts-new-observedV2-and-trace.md)[\@Trace](./arkts-new-observedV2-and-trace.md)                   | Direct compatibility. \@ObjectLink needs to be initialized by the instance of the class decorated by @Observed. It is mainly used to observe nested classes. \@ObservedV2\@Trace can be used in state management V2. For details, see [\@ObjectLink/\@Observed/\@Track -> \@ObservedV2/\@Trace](./arkts-v1-v2-migration-inner-class.md#objectlinkobservedtrack---observedv2trace). |
| [\@Provide](./arkts-provide-and-consume.md)               | [\@Provider](./arkts-new-provider-and-consumer.md)                | Compatible For details, see [\@Provide/\@Consume -> \@Provider/\@Consumer](./arkts-v1-v2-migration-inner-component.md#provideconsume---providerconsumer).|
| [\@Consume](./arkts-provide-and-consume.md)               | [\@Consumer](./arkts-new-provider-and-consumer.md)                | Compatible For details, see [\@Provide/\@Consume -> \@Provider/\@Consumer](./arkts-v1-v2-migration-inner-component.md#provideconsume---providerconsumer).|
| [\@Watch](./arkts-watch.md)               | [\@Monitor](./arkts-new-monitor.md)                | \@Watch is used to listen for the changes of state variables and their top-level properties in V1. Observable changes trigger \@Watch events.<br>\@Monitor is used to listen for the changes of state variables in V2. Used together with \@Trace, it enables deep listening. If a state variable changes multiple times in one event, the final result is used to determine whether to trigger the \@Monitor event. For details, see [\@Watch -> \@Monitor](./arkts-v1-v2-migration-inner-component.md#watch---monitor).|
| Repeated calculation              | [\@Computed](./arkts-new-computed.md)               |State management V1 does not have the capability of calculating attributes. State management V2 can use \@Computed to avoid repeated calculation. For details, see [@Computed](./arkts-v1-v2-migration-inner-component.md#computed).|
| [LocalStorage](./arkts-localstorage.md)               | \@ObservedV2\@Trace   | Compatible For details, see [LocalStorage -> \@ObservedV2/\@Trace](./arkts-v1-v2-migration-application-and-others.md#localstorage-observedv2trace).|
| [AppStorage](./arkts-appstorage.md)               | [AppStorageV2](./arkts-new-appstoragev2.md)   | Compatible For details, see [AppStorage -> AppStorageV2](./arkts-v1-v2-migration-application-and-others.md#appstorage---appstoragev2).|
| [Environment](./arkts-environment.md)       | Direct ability API calls to obtain system environment variables  | **Environment** for obtaining environment variables is coupled with AppStorage. V2 removes AppStorage dependency, enabling direct ability API calls for obtaining environment variables. For details, see [Environment -> Direct API Calls to Obtain System Environment Variables](./arkts-v1-v2-migration-application-and-others.md#environment---direct-api-calls-to-obtain-system-environment-variables).|
| [PersistentStorage](./arkts-persiststorage.md)     | [PersistenceV2](./arkts-new-persistencev2.md)   | PersistentStorage's persistence capability is coupled with AppStorage, while PersistenceV2 can be used independently. For details, see [PersistentStorage -> PersistenceV2](./arkts-v1-v2-migration-application-and-others.md#persistentstorage---persistencev2).|


## V1V2 Migration Scenario
| Scenario               | V2 Decorators and APIs Involved                 | Description|
|------------------------|--------------------------|--------------------------|
| Gradual Migration from V1 to V2     | \@ObservedV2, \@Trace, and \@Monitor|For details about how to gradually migrate applications developed using V1 to V2, see [Gradual Migration from V1 to V2](./arkts-v1-v2-migration-application-and-others.md#gradual-migration-from-v1-to-v2).|
| Scrollable component scenarios     | [makeObserved](./arkts-new-makeObserved.md)|For details, see [Scroll Components](./arkts-v1-v2-migration-application-and-others.md#scroll-components).|
| [Modifier](../arkts-user-defined-modifier.md)    | makeObserved, \@ObservedV2, \@Trace|For details, see [Modifiers](./arkts-v1-v2-migration-application-and-others.md#modifiers).|
