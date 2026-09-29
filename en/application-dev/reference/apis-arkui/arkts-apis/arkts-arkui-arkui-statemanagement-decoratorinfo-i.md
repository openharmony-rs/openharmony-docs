# DecoratorInfo

```TypeScript
export interface DecoratorInfo
```

Defines the decorator and component information associated with the observable object.

**Since:** 23

<!--Device-unnamed-export interface DecoratorInfo--><!--Device-unnamed-export interface DecoratorInfo-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AppStorageV2, PersistenceV2, Type, UIUtils, ConnectOptions, Binding, MutableBinding, CustomComponentLifecycle, CustomComponentLifecycleObserver, CustomComponentLifecycleState, ComponentInit, ComponentAppear, ComponentBuilt, ComponentReuse, ComponentActive, ComponentInactive, ComponentRecycle, ComponentDisappear, CollectionType, ConnectOptionsCollections, CustomComponentContext, IReusePool, IReusableInfo, StorageDefaultCreator, TypeConstructorWithArgs, PersistenceErrorCallback, TypeConstructor, TypeDecorator, MonitorCallback, MonitorOptions, GetterCallback, SetterCallback, ObservedResult, DecoratorInfo, ElementInfo } from '@kit.ArkUI';
```

## decoratorName

```TypeScript
decoratorName: string
```

Decorator name. For a V1 object, the value is the name of the decorator associated with the object. <br> If the V1 object uses [@Track](../../../ui/state-management/arkts-track.md), the value is **'@Track'**. <br> If the V2 object uses [@Trace](../../../ui/state-management/arkts-new-observedV2-and-trace.md), the value is **'@Trace'**. <br> If the V2 object uses [makeObserved](arkts-arkui-arkui-statemanagement-uiutils-c.md#makeobserved), the value is **'MakeObserved'**. <br> If the V2 object uses [enableV2Compatibility](arkts-arkui-arkui-statemanagement-uiutils-c.md#enablev2compatibility), the value is **'EnableV2Compatible'**. <br> If the V2 object uses built-in data, the value is **'ProxyObservedV2'**.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-DecoratorInfo-decoratorName: string--><!--Device-DecoratorInfo-decoratorName: string-End-->

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

<!--Device-DecoratorInfo-dependentInfo: Array<ElementInfo>--><!--Device-DecoratorInfo-dependentInfo: Array<ElementInfo>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## owningComponentId

```TypeScript
owningComponentId: number
```

Component ID. For a V1 object, the component ID is returned. <br> **If a V1 object has a property that uses [@Track](../../../ui/state-management/arkts-track.md), no component ID is available, and -1 is returned. In the same case, no component ID is available for a V2 object, and -1 is returned.**

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-DecoratorInfo-owningComponentId: number--><!--Device-DecoratorInfo-owningComponentId: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## owningComponentOrClassName

```TypeScript
owningComponentOrClassName: string
```

Component or object name. For a V1 object, the component name is returned. <br> For a V1 object whose properties are decorated by the [@Track](../../../ui/state-management/arkts-track.md) decorator, the object name is returned. <br> For a V2 object, the object name is returned.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-DecoratorInfo-owningComponentOrClassName: string--><!--Device-DecoratorInfo-owningComponentOrClassName: string-End-->

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

<!--Device-DecoratorInfo-stateVariableName: string--><!--Device-DecoratorInfo-stateVariableName: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
