# DataReloadOperation

重载所有数据操作。当onDatasetChange含有DataOperationType.RELOAD操作时，其余操作全部失效，框架会自己调用keyGenerator进行键值比对。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface DataReloadOperation--><!--Device-unnamed-export interface DataReloadOperation-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: DataOperationType
```

数据全部重载类型。

**类型：** DataOperationType

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataReloadOperation-type: DataOperationType--><!--Device-DataReloadOperation-type: DataOperationType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

