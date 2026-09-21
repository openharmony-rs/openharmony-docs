# LocalizedBarrierDirection

```TypeScript
declare enum LocalizedBarrierDirection
```

Enumerates the directions of barriers with mirror mode support.

| Name| Value | Description |  
| ------ | -- | ----------------------------- |  
| [START](arkts-arkui-relativecontainer-comp-localizedbarrierdirection-e.md) | 0 |The barrier is on the start side of all its |
| | |[referencedId](arkts-arkui-relativecontainer-comp-localizedbarrierstyle-i.md), that is, the |
| | |leftmost side in LTR mode and the rightmost side in RTL mode.|
| [END](arkts-arkui-relativecontainer-comp-localizedbarrierdirection-e.md) | 1 | The barrier is on the end side of all its [referencedId](arkts-arkui-relativecontainer-comp-localizedbarrierstyle-i.md), that is, the |
| | |rightmost side in LTR mode and the leftmost side in RTL mode.|
| TOP | 2 | The barrier is at the top of all the referenced components specified by |
| | |[referencedId](arkts-arkui-relativecontainer-comp-localizedbarrierstyle-i.md).|
| BOTTOM | 3 | The barrier is at the bottom of all the referenced components specified by |
| | |[referencedId](arkts-arkui-relativecontainer-comp-localizedbarrierstyle-i.md).|

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## START

```TypeScript
START = 0
```

The barrier is on the start side of all its [referencedId](arkts-arkui-relativecontainer-comp-localizedbarrierstyle-i.md), that is, the leftmost side in LTR mode and the rightmost side in RTL mode.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## END

```TypeScript
END = 1
```

The barrier is on the end side of all its [referencedId](arkts-arkui-relativecontainer-comp-localizedbarrierstyle-i.md), that is, the rightmost side in LTR mode and the leftmost side in RTL mode.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## TOP

```TypeScript
TOP = 2
```

The barrier is at the top of all the referenced components specified by [referencedId](arkts-arkui-relativecontainer-comp-localizedbarrierstyle-i.md).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## BOTTOM

```TypeScript
BOTTOM = 3
```

The barrier is at the bottom of all the referenced components specified by [referencedId](arkts-arkui-relativecontainer-comp-localizedbarrierstyle-i.md).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
