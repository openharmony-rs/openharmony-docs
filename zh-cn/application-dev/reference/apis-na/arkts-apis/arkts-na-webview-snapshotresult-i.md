# SnapshotResult

Represents a full drawing result.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-webview-interface SnapshotResult--><!--Device-webview-interface SnapshotResult-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## id

```TypeScript
id?: string
```

Id of the snapshot.

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-SnapshotResult-id?: string--><!--Device-SnapshotResult-id?: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## imagePixelMap

```TypeScript
imagePixelMap?: image.PixelMap
```

Full drawing result in image.PixelMap format.

**类型：** image.PixelMap

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-SnapshotResult-imagePixelMap?: image.PixelMap--><!--Device-SnapshotResult-imagePixelMap?: image.PixelMap-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## size

```TypeScript
size?: SizeOptions
```

Actual size drawn on the web page. The value is of the number type, and the unit is vp.

**类型：** SizeOptions

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-SnapshotResult-size?: SizeOptions--><!--Device-SnapshotResult-size?: SizeOptions-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## status

```TypeScript
status?: boolean
```

The status of the snapshot. The value can be true (normal) or false (failure). If the full drawing result fails to be obtained, the width and height of the returned size are both 0, and the map is empty.

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-SnapshotResult-status?: boolean--><!--Device-SnapshotResult-status?: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

