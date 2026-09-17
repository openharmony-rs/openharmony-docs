# TagInfo

Before a card with tags is read or written, **[TagInfo](arkts-connectivity-tag-taginfo-i.md)** must be obtained to determine the tag technologies supported by the card. In this way, the application can invoke the correct API to communicate with the card.

**Since:** 7

**System capability:** SystemCapability.Communication.NFC.Tag

## Modules to Import

```TypeScript
import { tag } from '@kit.ConnectivityKit';
```

## extrasData

```TypeScript
extrasData: PacMap[]
```

Extended attribute value of the tag technology.

**Type:** [PacMap](../../apis-ability-kit/arkts-apis/arkts-ability-dataabilityhelper-pacmap-i.md)[]

**Since:** 9

**Required permissions:** ohos.permission.NFC_TAG

**System capability:** SystemCapability.Communication.NFC.Tag

**System API:** This is a system API.

## remoteTagService

```TypeScript
remoteTagService: rpc.RemoteObject
```

Remote object of the NFC service process used for interface communication between the client and the service.

**Type:** [rpc.RemoteObject](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-remoteobject-c.md)

**Since:** 9

**Required permissions:** ohos.permission.NFC_TAG

**System capability:** SystemCapability.Communication.NFC.Tag

**System API:** This is a system API.

## tagRfDiscId

```TypeScript
tagRfDiscId: number
```

ID allocated when the tag is discovered.

**Type:** number

**Since:** 9

**Required permissions:** ohos.permission.NFC_TAG

**System capability:** SystemCapability.Communication.NFC.Tag

**System API:** This is a system API.
