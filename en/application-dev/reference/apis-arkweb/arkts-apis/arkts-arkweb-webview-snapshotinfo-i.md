# SnapshotInfo

Provides information used to obtain a full drawing result.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## id

```TypeScript
id?: string
```

ID of the snapshot, used to identify this full rendering request so that the corresponding full rendering data can be matched in the callback result. If not passed, no ID is specified and the system handles it automatically.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## size

```TypeScript
size?: SizeOptions
```

Size of the Web rendering. The maximum supported size is 16000px * 16000px. The supported length units are px, vp, and %. The length units passed in different parameters must be consistent; otherwise, the rendering size may not meet expectations. The default unit is vp. If the specified size exceeds the specification, the maximum specification is returned. If not passed, the rendering is performed at the actual size of the screenshot area. (Example: width:'100px', height:'200px'. Or width:'20%', height:'30%'. If only a number is specified, the unit is vp.)

**Type:** [SizeOptions](../../apis-arkui/arkts-apis/arkts-arkui-sizeoptions-i.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core
