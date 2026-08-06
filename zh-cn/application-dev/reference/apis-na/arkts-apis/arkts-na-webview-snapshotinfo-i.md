# SnapshotInfo

Defines the snapshot info.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-webview-interface SnapshotInfo--><!--Device-webview-interface SnapshotInfo-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## id

```TypeScript
id?: string
```

Id of the snapshot.

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-SnapshotInfo-id?: string--><!--Device-SnapshotInfo-id?: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## size

```TypeScript
size?: SizeOptions
```

Size for web rendering. The maximum size is 16000 px × 16000 px. The length unit can be px, vp, or %. The length unit must be the consistent across parameters. The default unit is vp. If the size exceeds the specifications, the maximum size is returned. (Example: width: '100px', height: '200px' or width: '20%', height'30%'. If only digits are written, the unit is vp.)

**类型：** SizeOptions

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-SnapshotInfo-size?: SizeOptions--><!--Device-SnapshotInfo-size?: SizeOptions-End-->

**系统能力：** SystemCapability.Web.Webview.Core

