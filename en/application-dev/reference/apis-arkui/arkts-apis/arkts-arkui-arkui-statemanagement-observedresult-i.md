# ObservedResult

```TypeScript
export interface ObservedResult
```

Provides the result of whether the object can be observed.

**Since:** 23

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AppStorageV2, PersistenceV2, Type, UIUtils, ConnectOptions, Binding, MutableBinding, CustomComponentLifecycle, CustomComponentLifecycleObserver, CustomComponentLifecycleState, ComponentInit, ComponentAppear, ComponentBuilt, ComponentReuse, ComponentActive, ComponentInactive, ComponentRecycle, ComponentDisappear, CollectionType, ConnectOptionsCollections, CustomComponentContext, IReusePool, IReusableInfo, StorageDefaultCreator, TypeConstructorWithArgs, PersistenceErrorCallback, TypeConstructor, TypeDecorator, MonitorCallback, MonitorOptions, GetterCallback, SetterCallback, ObservedResult, DecoratorInfo, ElementInfo } from '@kit.ArkUI';
```

## decoratorInfo

```TypeScript
decoratorInfo: Array<DecoratorInfo>
```

Decorator and component information associated with the observable object. If the object cannot be observed, the array is empty.

**Type:** Array&lt;[DecoratorInfo](arkts-arkui-arkui-statemanagement-decoratorinfo-i.md)&gt;

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isObserved

```TypeScript
isObserved: boolean
```

Whether an object can be observed.

**true**: The object can be observed.

**false**: The object cannot be observed.

**Type:** boolean

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## reason

```TypeScript
reason: string
```

Reason for the object's observability.

For the object that cannot be observed: The object itself cannot be observed.

For the object that can be observed:

1. The V1 object is decorated by the [@Observed](../../../ui/state-management/arkts-observed-and-objectlink.md)
decorator or the object is converted by the [makeV1Observed](arkts-arkui-arkui-statemanagement-uiutils-c.md#makev1observed) method.
2. The V1 object is decorated by the [@Observed](../../../ui/state-management/arkts-observed-and-objectlink.md)
decorator or the object is converted by the [makeV1Observed](arkts-arkui-arkui-statemanagement-uiutils-c.md#makev1observed) method, but the object is not used by the UI component.
3. The V1 object is converted by the [enableV2Compatibility](arkts-arkui-arkui-statemanagement-uiutils-c.md#enablev2compatibility) method
and then passed to the V2 component.
4. The V1 object is converted by the [enableV2Compatibility](arkts-arkui-arkui-statemanagement-uiutils-c.md#enablev2compatibility) method
and then passed to the V2 component, but is not used by the V2 component.
5. The V2 object is decorated by the
[@ObservedV2 or @Trace](../../../ui/state-management/arkts-new-observedV2-and-trace.md) decorator.
6. The V2 object is converted by the [makeObserved](arkts-arkui-arkui-statemanagement-uiutils-c.md#makeobserved) method.
7. The V2 object is of the Array, Map, Set, or Date type.
8. The V2 object is decorated by the
[@ObservedV2 or @Trace](../../../ui/state-management/arkts-new-observedV2-and-trace.md) decorator, but is not used by the UI component.
9. The V2 object is converted by the [makeObserved](arkts-arkui-arkui-statemanagement-uiutils-c.md#makeobserved) method, but the object is not
used by the UI component.
10. The V2 object is of the Array, Map, Set, or Date type, but is not used by the UI component.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
