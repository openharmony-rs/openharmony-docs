# ValueType

```TypeScript
type ValueType = number | number | string | boolean | image.PixelMap | Want | ArrayBuffer | object | null | undefined
```

Enumerates the data field types allowed in a unified data record.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

| Type | Description |
| --- | --- |
| int | Int. |
| long | Long. |
| double | Double. |
| string | String. |
| boolean | Boolean. |
| [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) | The value is of the [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-multimedia-image.md) type. |
| [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md). |
| ArrayBuffer | ArrayBuffer. |
| object | Object. |
| null | Null. |
| undefined | Undefined. |
