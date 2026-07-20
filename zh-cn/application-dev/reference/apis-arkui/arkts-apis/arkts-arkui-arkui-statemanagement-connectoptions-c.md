# ConnectOptions

globalConnect参数类型。

**起始版本：** 18

<!--Device-unnamed-export class ConnectOptions<T extends object>--><!--Device-unnamed-export class ConnectOptions<T extends object>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { Binding, ComponentReuse, CustomComponentLifecycleState, ComponentInactive, PersistenceV2, ComponentDisappear, MutableBinding, CustomComponentLifecycleObserver, AppStorageV2, Type, ConnectOptionsCollections, CollectionType, CustomComponentContext, IReusePool, ConnectOptions, UIUtils, ComponentActive, CustomComponentLifecycle, ComponentInit, ComponentAppear, ComponentBuilt, ComponentRecycle, IReusableInfo } from '@kit.ArkUI';
```

## areaMode

```TypeScript
areaMode?: contextConstant.AreaMode
```

加密级别：EL1-EL5，详见[加密级别](docroot://application-models/application-context-stage.md#获取和修改加密分区)，对应数值：0-4，不传时默认为EL2，不同加密级别对应不同的加密分区，即不同的存储路径，传入的加密等级数值不在0-4会直接运行crash。

**类型：** contextConstant.AreaMode

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ConnectOptions-areaMode?: contextConstant.AreaMode--><!--Device-ConnectOptions-areaMode?: contextConstant.AreaMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## defaultCreator

```TypeScript
defaultCreator?: StorageDefaultCreator<T>
```

默认数据的构造器，建议传递，如果globalConnect是第一次连接key，不传会报错。

**类型：** StorageDefaultCreator&lt;T&gt;

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ConnectOptions-defaultCreator?: StorageDefaultCreator<T>--><!--Device-ConnectOptions-defaultCreator?: StorageDefaultCreator<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## key

```TypeScript
key?: string
```

传入的key，不传则使用type的名字作为key。

**类型：** string

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ConnectOptions-key?: string--><!--Device-ConnectOptions-key?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: TypeConstructorWithArgs<T>
```

指定的类型。

**类型：** TypeConstructorWithArgs&lt;T&gt;

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ConnectOptions-type: TypeConstructorWithArgs<T>--><!--Device-ConnectOptions-type: TypeConstructorWithArgs<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

