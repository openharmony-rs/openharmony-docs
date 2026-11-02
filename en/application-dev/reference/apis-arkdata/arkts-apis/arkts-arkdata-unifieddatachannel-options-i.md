# Options

```TypeScript
interface Options
```

The data operation APIs provided by UDMF include three optional parameters: intention, key, and visibility. If an API does not require these parameters, they can be left unspecified. For details, see the parameter description of the specific API.

**Since:** 10

<!--Device-unifiedDataChannel-interface Options--><!--Device-unifiedDataChannel-interface Options-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## Modules to Import

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## intention

```TypeScript
intention?: Intention
```

Data channel type related to the data operation. The value is an [Intention](#intention) enum, including DATA_HUB and DRAG. If not specified, the value is empty by default. For details about whether this parameter is mandatory, see the parameter description of the specific API.

**Type:** [Intention](arkts-arkdata-unifieddatachannel-intention-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Options-intention?: Intention--><!--Device-Options-intention?: Intention-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## key

```TypeScript
key?: string
```

Unique identifier of the data object in UDMF. It can be obtained from the return value of [insertData](arkts-arkdata-unifieddatachannel-insertdata-f.md#insertdata-1).

If not specified, the value is empty by default. For details about whether this parameter is mandatory, see the parameter description of the specific API.<br>It consists of four parts: udmf:/, intention, bundleName, and groupId, which are connected by '/', for example, udmf://DataHub/com.ohos.test/0123456789.<br>Among them, udmf:/ is fixed, DataHub is the value of the corresponding enum, com.ohos.test is the bundle name, and 0123456789 is the randomly generated groupId.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Options-key?: string--><!--Device-Options-key?: string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## visibility

```TypeScript
visibility?: Visibility
```

Visibility level of the data. It is available only for public data channels. The value is a [Visibility](#visibility) enum. It takes effect only when specified during data writing. If not specified, the default value is Visibility.ALL.<br>**Atomic service API:** This API is supported in atomic services since API version 20.

**Type:** [Visibility](arkts-arkdata-unifieddatachannel-visibility-e.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-Options-visibility?: Visibility--><!--Device-Options-visibility?: Visibility-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
