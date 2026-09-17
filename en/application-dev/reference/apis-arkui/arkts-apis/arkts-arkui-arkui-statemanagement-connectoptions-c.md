# ConnectOptions

Defines the parameter type for **globalConnect**.

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AppStorageV2, PersistenceV2, Type, UIUtils, ConnectOptions, Binding, MutableBinding, CustomComponentLifecycle, CustomComponentLifecycleObserver, CustomComponentLifecycleState, ComponentInit, ComponentAppear, ComponentBuilt, ComponentReuse, ComponentActive, ComponentInactive, ComponentRecycle, ComponentDisappear, CollectionType, ConnectOptionsCollections, CustomComponentContext, IReusePool, IReusableInfo, StorageDefaultCreator, TypeConstructorWithArgs, PersistenceErrorCallback, TypeConstructor, TypeDecorator, MonitorCallback, MonitorOptions, GetterCallback, SetterCallback, ObservedResult, DecoratorInfo, ElementInfo } from '@kit.ArkUI';
```

## defaultCreator

```TypeScript
defaultCreator?: StorageDefaultCreator<T>
```

Default constructor. You are advised to pass this parameter. If **globalConnect** is connected to the key for the first time, an error is reported if this parameter is not passed in.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## areaMode

```TypeScript
areaMode?: contextConstant.AreaMode
```

Encryption level, ranging from EL1 to EL5 (corresponding to the value from 0 to 4). For details, see [Encryption Levels](../../../application-models/application-context-stage.md#obtaining-and-modifying-encryption-levels). If no value is passed in, EL2 is used by default. Storage paths vary based on the encryption levels. If the input value of encryption level is not in the range of **0** to **4**, a crash occurs.

**Type:** [contextConstant.AreaMode](../../apis-ability-kit/arkts-apis/arkts-ability-contextconstant-areamode-e.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## key

```TypeScript
key?: string
```

Input key. If no value is passed in, the type name is used as the key.

**Type:** string

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: TypeConstructorWithArgs<T>
```

Specified type.

**Type:** [TypeConstructorWithArgs](arkts-arkui-arkui-statemanagement-typeconstructorwithargs-i.md)&lt;T&gt;

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
