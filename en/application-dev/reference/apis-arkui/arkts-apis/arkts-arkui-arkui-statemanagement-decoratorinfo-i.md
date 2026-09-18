# DecoratorInfo

Defines the decorator and component information associated with the observable object.

**Since:** 23

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AppStorageV2, PersistenceV2, Type, UIUtils, ConnectOptions, Binding, MutableBinding, CustomComponentLifecycle, CustomComponentLifecycleObserver, CustomComponentLifecycleState, ComponentInit, ComponentAppear, ComponentBuilt, ComponentReuse, ComponentActive, ComponentInactive, ComponentRecycle, ComponentDisappear, CollectionType, ConnectOptionsCollections, CustomComponentContext, IReusePool, IReusableInfo, StorageDefaultCreator, TypeConstructorWithArgs, PersistenceErrorCallback, TypeConstructor, TypeDecorator, MonitorCallback, MonitorOptions, GetterCallback, SetterCallback, ObservedResult, DecoratorInfo, ElementInfo } from '@kit.ArkUI';
```

## decoratorName

```TypeScript
decoratorName: string
```

Decorator name.

For a V1 object, the value is the name of the decorator associated with the object.

If the V1 object uses [@Track](../../../ui/state-management/arkts-track.md), the value is **'@Track'**.

If the V2 object uses [@Trace](../../../ui/state-management/arkts-new-observedV2-and-trace.md), the value is **'@Trace'**.

If the V2 object uses [makeObserved](arkts-arkui-arkui-statemanagement-uiutils-c.md#makeobserved), the value is **'MakeObserved'**.

If the V2 object uses [enableV2Compatibility](arkts-arkui-arkui-statemanagement-uiutils-c.md#enablev2compatibility), the value is **'EnableV2Compatible'**.

If the V2 object uses built-in data, the value is **'ProxyObservedV2'**.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## dependentInfo

```TypeScript
dependentInfo: Array<ElementInfo>
```

Information about the component that uses the observable object. If the object is not used in any UI, an empty array is returned.

**Type:** Array&lt;[ElementInfo](arkts-arkui-arkui-statemanagement-elementinfo-i.md)&gt;

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## owningComponentId

```TypeScript
owningComponentId: number
```

Component ID.

For a V1 object, the component ID is returned.

For the V1 object whose properties are decorated by the [@Track](../../../ui/state-management/arkts-track.md) decorator or for the V2 object, **-1** is returned instead of the component ID.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## owningComponentOrClassName

```TypeScript
owningComponentOrClassName: string
```

Component or object name.

For a V1 object, the component name is returned.

For a V1 object whose properties are decorated by the [@Track](../../../ui/state-management/arkts-track.md) decorator, the object name is returned.

For a V2 object, the object name is returned.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## stateVariableName

```TypeScript
stateVariableName: string
```

Name of the attribute decorated by the decorator.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
