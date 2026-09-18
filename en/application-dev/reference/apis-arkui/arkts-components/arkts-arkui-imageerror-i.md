# ImageError

Describes the object returned by the image loading error callback.

This event is not triggered if the parameter type of the component is [AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md).

**Since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## componentHeight

```TypeScript
componentHeight: number
```

Height of the component.

Unit: px

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## componentWidth

```TypeScript
componentWidth: number
```

Width of the component.

Unit: px

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## downloadInfo

```TypeScript
downloadInfo?: RequestDownloadInfo
```

Detailed information about online image download, including download resources, network, and performance. This field is carried when the image source is an online image and the download fails.

Default value: **null**

**Type:** [RequestDownloadInfo](arkts-arkui-requestdownloadinfo-t.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## error

```TypeScript
error?: BusinessError<void>
```

Error information returned when an error occurs during image loading, where **code** represents the error code and **message** indicates the error message. For details, see the error code reference below.

Default value: **{ code : -1, message : "" }**

**Type:** [BusinessError](arkts-arkui-businesserror-t.md)&lt;void&gt;

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## message

```TypeScript
message: string
```

Error information.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
