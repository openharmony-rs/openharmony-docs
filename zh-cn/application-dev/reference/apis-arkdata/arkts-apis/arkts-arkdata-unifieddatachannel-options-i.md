# Options

UDMF提供的数据操作接口包含三个可选参数：intention、key和visibility。如果接口不需要这些参数，可以不填，具体要求请参阅该接口的参数说明。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unifiedDataChannel-interface Options--><!--Device-unifiedDataChannel-interface Options-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## intention

```TypeScript
intention?: Intention
```

表示数据操作相关的数据通路类型，取值为[Intention](arkts-arkdata-unifieddatachannel-intention-e.md#Intention)枚举类型，包括DATA_HUB、DRAG等。不填写时默认无值，具体是否必填请参阅具体接口的参数 说明。

**类型：** [Intention](arkts-arkdata-unifieddatachannel-intention-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Options-intention?: Intention--><!--Device-Options-intention?: Intention-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## key

```TypeScript
key?: string
```

UDMF中数据对象的唯一标识符，可通过[insertData](arkts-arkdata-unifieddatachannel-insertdata-f.md#insertData)接口的返回值获取。不填写时默认无值，具体是否必填请参阅具体接口的参数说明。 由udmf:/、intention、bundleName和groupId四部分组成，以'/'连接，比如：udmf://DataHub/com.ohos.test/0123456789。 其中udmf:/固定，DataHub为对应枚举的取值，com.ohos.test为包名，0123456789为随机生成的groupId。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Options-key?: string--><!--Device-Options-key?: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## visibility

```TypeScript
visibility?: Visibility
```

表示数据的可见性等级，仅公共数据通路可使用，取值为[Visibility](arkts-arkdata-unifieddatachannel-visibility-e.md#Visibility)枚举类型。只在写入数据的时候填写才生效，若不填写默认是 Visibility.ALL。

**类型：** Visibility

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Options-visibility?: Visibility--><!--Device-Options-visibility?: Visibility-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

