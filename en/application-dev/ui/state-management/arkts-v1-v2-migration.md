# V1 to V2 Migration Overview
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @katabanga-->
<!--Designer: @s10021109-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

## Overview
ArkUI state management automatically synchronizes observable data changes to the UI to implement data-driven UI re-render, enabling you to focus on UI implementation and design.

During the evolution of the state management framework, state management V1 and V2 are released. V1 emphasizes state management of the components, while V2 enhances the in-depth observation and management of data objects. With V2, you can control data and state more flexibly, facilitating a more efficient UI re-render. For details about the differences between V1 and V2, see [State Management Overview](./arkts-state-management-overview.md).

## How to Use
1. V2 represents an enhanced iteration of V1, offering expanded functionality and increased flexibility through ongoing optimization.
2. For new applications, you are advised to use the V2 paradigm for development.
3. For applications that have used V1, if the functions and performance of V1 can meet the requirements, you do not need to switch to V2 immediately.
4. For details about the mixed use of V1 and V2, see [Mixing Use of Custom Components](./arkts-custom-component-mixed-scenarios.md). The compiler, toolchain, and DevEco Studio can verify some misuse and mixed use scenarios that are not recommended. Although you may bypass these verifications using special methods, you are still advised to follow the guidelines in [Mixing Use of Custom Components](./arkts-custom-component-mixed-scenarios.md) to avoid uncertainty caused by dual proxies.

## Purpose
1. For developers who want to migrate applications from V1 to V2, this document provides systematic templates and guidance.
2. For developers who want to gradually transition applications from V1 to V2, this document together with [Mixing Use of Custom Components](./arkts-custom-component-mixed-scenarios.md) provide guidelines and reference.
3. For developers who have not started to develop applications but are familiar with the state management of V1, this document and documents about V2 provide reference for application development in V2.

## Capability Comparison and Migration Between V1 and V2
| V1 Decorator Name/Scenario               | V2 Decorator Name/API                 | Description|
|------------------------|--------------------------|--------------------------|
| [\@Observed](./arkts-observed-and-objectlink.md)              | [\@ObservedV2](./arkts-new-observedV2-and-trace.md)              | Both mark an object as observable, but with key differences:<br>\@Observed is used to observe the top-level properties and requires [\@ObjectLink](./arkts-observed-and-objectlink.md) to take effect.<br>\@ObservedV2 does not have the observation capability. It only marks a class as observable. To observe the class properties, use it together with \@Trace. For details, see [\@ObjectLink/\@Observed/\@Track -> \@ObservedV2/\@Trace](./arkts-v1-v2-migration-inner-class.md#objectlinkobservedtrack---observedv2trace). |
| [\@Track](./arkts-track.md)                 | [\@Trace](./arkts-new-observedV2-and-trace.md)               | \@Track is used for accurate observation. If it is not used, class properties cannot be accurately observed.<br>\@Trace decorated properties can be accurately traced and observed. For details, see [\@ObjectLink/\@Observed/\@Track -> \@ObservedV2/\@Trace](./arkts-v1-v2-migration-inner-class.md#objectlinkobservedtrack---observedv2trace).|
| [\@Component](./arkts-create-custom-components.md#component)             | [\@ComponentV2](./arkts-new-componentV2.md)             | \@Component is the custom component decorator used with the state variables of V1.<br>@ComponentV2 is the custom component decorator used with the state variables of V2.|
|[\@State](./arkts-state.md)                 | No external initialization: [\@Local](./arkts-new-local.md)<br>One-time external initialization: [\@Param](./arkts-new-param.md) + [\@Once](./arkts-new-once.md)| Similar to \@Local, \@State decorated variables can work as the data source which can be directly migrated without external initialization. If external input is required for initialization, you can migrate it to \@Param\@Once. For details, see [\@State->\@Local](./arkts-v1-v2-migration-inner-component.md#state-local).|
| [\@Prop](./arkts-prop.md)                  | [\@Param](./arkts-new-param.md)                   | Similar to \@Param, \@Prop is used to decorate custom component variables. When the input parameter is of the complex type, \@Prop is used to deep copy and \@Param is used to import the parameter. For details, see [\@Prop -> \@Param](./arkts-v1-v2-migration-inner-component.md#prop---param).|
| [\@Link](./arkts-link.md)                  | [\@Param](./arkts-new-param.md)[\@Event](./arkts-new-event.md)    | \@Link implements a two-way synchronization encapsulated by the framework of V1. Developers using V2 can implement the two-way synchronization through @Param and @Event. For details, see [\@Link -> \@Param/\@Event](./arkts-v1-v2-migration-inner-component.md#link---paramevent).|
| [\@ObjectLink](./arkts-observed-and-objectlink.md)           | [\@ObservedV2](./arkts-new-observedV2-and-trace.md)[\@Trace](./arkts-new-observedV2-and-trace.md)                   | Compatible. \@ObjectLink needs to be initialized by the instance of the class decorated by @Observed. It is mainly used in the observation nested class scenario. In V2 state management, \@ObservedV2\@Trace can be used. For details, see [\@ObjectLink/\@Observed/\@Track -> \@ObservedV2/\@Trace](./arkts-v1-v2-migration-inner-class.md#objectlinkobservedtrack---observedv2trace). |
| [\@Provide](./arkts-provide-and-consume.md)               | [\@Provider](./arkts-new-Provider-and-Consumer.md)                | Compatible. For details, see [Provide-Consume Migration Scenario](./arkts-v1-v2-migration-inner-component.md#provideconsume---providerconsumer).|
| [\@Consume](./arkts-provide-and-consume.md)               | [\@Consumer](./arkts-new-Provider-and-Consumer.md)                | Compatible. For details, see [\@Provide/\@Consume -> \@Provider/\@Consumer](./arkts-v1-v2-migration-inner-component.md#provideconsume---providerconsumer).|
| [\@Watch](./arkts-watch.md)               | [\@Monitor](./arkts-new-monitor.md)                | \@Watch is used to listen for the changes of state variables and their top-level properties in V1. Observable changes of state variables can trigger the \@Watch listening event.<br>\@Monitor is used to listen for the changes of state variables in V2. Used together with \@Trace, in-depth changes can be listened. When a state variable changes frequently in an event, only the final result is used to determine whether to trigger the \@Monitor listening event. For details, see [\@Watch -> \@Monitor](./arkts-v1-v2-migration-inner-component.md#watch---monitor).|
| Repeated calculation              | [\@Computed](./arkts-new-Computed.md)               |State management V1 does not have the capability of computing attributes. State management V2 can use \@Computed to avoid repeated calculation. For details, see [@Computed](./arkts-v1-v2-migration-inner-component.md#computed).|
| [LocalStorage](./arkts-localstorage.md)               | \@ObservedV2\@Trace   | Compatible. For details, see [LocalStorage -> \@ObservedV2/\@Trace](./arkts-v1-v2-migration-application-and-others.md#localstorage---observedv2trace).|
| [AppStorage](./arkts-appstorage.md)               | [AppStorageV2](./arkts-new-appstoragev2.md)   | Compatible. For details, see [AppStorage -> AppStorageV2](./arkts-v1-v2-migration-application-and-others.md#appstorage---appstoragev2).|
| [Environment](./arkts-environment.md)       | Calls the ability APIs to obtain system environment variables.  | This capability is coupled with the AppStorage. In V2, you can directly call the ability APIs to obtain system environment variables. For details, see [Environment -> Direct API Calls to Obtain System Environment Variables](./arkts-v1-v2-migration-application-and-others.md#environment---direct-api-calls-to-obtain-system-environment-variables).|
| [PersistentStorage](./arkts-persiststorage.md)     | [PersistenceV2](./arkts-new-persistencev2.md)   | The persistence capability of PersistentStorage is coupled with the AppStorage, while that of PersistenceV2 can be used independently. For details, see [PersistentStorage -> PersistenceV2](./arkts-v1-v2-migration-application-and-others.md#persistentstorage---persistencev2).|


## V1V2 Migration Scenario
| Scenario               | V2 Decorators and APIs Involved                 | Description|
|------------------------|--------------------------|--------------------------|
| Gradual migration of existing V1 functions to V2     | \@ObservedV2, \@Trace, and \@Monitor|For details about how to gradually migrate applications that have been developed using V1 to V2, see [Gradual Migration from V1 to V2](./arkts-v1-v2-migration-application-and-others.md#gradual-migration-from-v1-to-v2).|
| Scrollable component scenarios     | [makeObserved](./arkts-new-makeObserved.md)|For details, see [Scrollable Components](./arkts-v1-v2-migration-application-and-others.md#scrollable-components).|
| [Modifier](../arkts-user-defined-modifier.md) scenario    | makeObserved, \@ObservedV2, \@Trace|For details, see [Modifiers](./arkts-v1-v2-migration-application-and-others.md#modifiers).|
