# UI Decorator Overview
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @s10021109-->
<!--Designer: @s10021109-->
<!--Tester: @zhangwenhan-->
<!--Adviser: @zhang_yixin13-->

The following table lists the common decorators in ArkUI.

| Common Decorators                                        | Decorator Description         |
| -------------------------------------------------- | ------------------- |
| [\@Require](./arkts-require.md)                    | Validates constructor input parameters.     |
| [\@Builder](./arkts-builder.md)                    | Customizes builder function.   |
| [\@LocalBuilder](./arkts-localBuilder.md)          | Maintains the component relationship.     |
| [\@BuilderParam](./arkts-builderparam.md)          | References the \@Builder function.|
| [\@Styles](./arkts-style.md)                       | Defines the component reuse style. |
| [\@Extend](./arkts-extend.md)                      | Defines the extension component style. |
| [\@AnimatableExtend](./arkts-animatable-extend.md) | Defines nimatable attributes.   |
| [\@Env](../arkts-env-system-property.md)           | Environment variables.         |

The following table lists the V1 state management decorators in ArkUI.

| V1 State Management Decorator                                            | Decorator Description                                  |
| ------------------------------------------------------------ | -------------------------------------------- |
| [\@State](./arkts-state.md)                                  | Basic state variable.                              |
| [\@Prop](./arkts-prop.md)                                    | Establishes one-way synchronization between the parent and child states.                      |
| [\@Link](./arkts-link.md)                                    | Establishes two-way synchronization between the parent and child states.                      |
| [\@ObjectLink](./arkts-observed-and-objectlink.md)           | Observes the changes of nested class object attributes.                    |
| [\@Provide](./arkts-provide-and-consume.md)                  | Establishes two-way synchronization with the child states.                        |
| [\@Consume](./arkts-provide-and-consume.md)                  | Establishes two-way synchronization with the ancestor state.                        |
| [\@Watch](./arkts-watch.md)                                  | Observes state variable changes.                          |
| [\@StorageLink](./arkts-appstorage.md#storagelink)           | Establishes two-way data synchronization with the corresponding attribute in the AppStorage.  |
| [\@StorageProp](./arkts-appstorage.md#storageprop)            | Establishes two-way data synchronization with the corresponding attribute in the AppStorage.  |
| [\@LocalStorageLink](./arkts-localstorage.md#localstoragelink) | Establishes two-way data synchronization with the corresponding attribute in the LocalStorage.|
| [\@LocalStorageProp](./arkts-localstorage.md#localstorageprop) | Establishes one-way data synchronization with the corresponding attribute in the LocalStorage.|
| [\@Observed](./arkts-observed-and-objectlink.md)             | Marks the class observable.                              |
| [\@Track](./arkts-track.md)                                  | Class object attribute update.                          |
| [\@Reusable](./arkts-reusable.md)                            | The tag component can be reused.                            |

The following table lists the V2 state management decorators in ArkUI.

| V2 State Management Decorator                                   | Decorator Description          |
| --------------------------------------------------- | -------------------- |
| [\@Local](./arkts-new-local.md)                     | Internal status of a component.      |
| [\@Param](./arkts-new-param.md)                     | External input of the component.      |
| [\@Once](./arkts-new-once.md)                       | The initialization is synchronized once.    |
| [\@Event](./arkts-new-event.md)                     | Standardizes the component output.      |
| [\@Provider](./arkts-new-provider-and-consumer.md)  | Establishes two-way synchronization with the child states.|
| [\@Consumer](./arkts-new-provider-and-consumer.md)  | Establishes two-way synchronization with the ancestor state.|
| [\@Monitor](./arkts-new-monitor.md)                 | Observes state variable changes.  |
| [\@Computed](./arkts-new-computed.md)               | Computed attributes.          |
| [\@ObservedV2](./arkts-new-observedV2-and-trace.md) | Marks the class observable.        |
| [\@Trace](./arkts-new-observedV2-and-trace.md)      | Marks the class attribute observable.  |
| [\@Type](./arkts-new-type.md)                       | Marks the types of the class attributes.  |
| [\@ReusableV2](./arkts-new-reusableV2.md)           | Marks the component reusable.    |
